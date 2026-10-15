---
type: method
domain: tooling
aliases: [finding-field-names, field-name-lookup, which-field, gen-mvar-field, genmvr, genmvar,
  generator-mvar, generator-reactive-power, case-object-fields, concise-name, variable-name]
tags: [powerworld, simauto, esapp, esa, fields, schema, getparametersmultipleelement, gen, load, bus]
---

# Finding the PowerWorld field name for a quantity

## Abstract

SimAuto calls (`GetParametersMultipleElement`, `ChangeParametersMultipleElement`, esapp's
`pw[Gen, [...]]`) take a field's **variable name**, not its concise name or column header. The
generator's present Mvar output is **`GenMVR`** (concise name `Mvar`, dialog path
`Mvar Output\Mvar`); its MW output is `GenMW`. Searching `Case Object Fields.txt` for the obvious
guess `GenMvar` finds the wrong fields: `GenMvar` is the *concise* name of 25 aggregate fields on
Area, Zone, Bus, Substation and others (`BGGenMVR`, `BusGenMVR`), while on the `Gen` object itself
the concise name is just `Mvar`. Two rules prevent this: PowerWorld writes Mvar as **MVR** in
variable names, and you look a field up *inside its object's block* by concise name or dialog path,
never across the whole file. The `schema-lookup` skill does both for you. Also note that `GenMW`
and `GenMVR` read **0.0 for an open generator**; `GenMWSetPoint` and `GenMvrSetPoint` keep the
setpoint.

## Connections

- **Up:** [Home](../index.md) · [esapp-overview](esapp-overview.md)
- **Tool:** the `schema-lookup` skill (`skills/schema-lookup/SKILL.md`), and the
  `schema-librarian` agent that runs it
- **Across:** [esapp](../concepts/esapp.md) · [powerworld-simauto](../concepts/powerworld-simauto.md) · [esapp-script-command-wrappers](../concepts/esapp-script-command-wrappers.md)
- **Deeper:** [esapp-schema-reference](../references/esapp-schema-reference.md) · [powerworld-study-options](../references/powerworld-study-options.md)

## Content

### Look it up with the skill (fastest)

```
python skills/schema-lookup/engine/lookup.py field Gen GenMvar
python skills/schema-lookup/engine/lookup.py search "generator reactive power output"
python skills/schema-lookup/engine/lookup.py object Gen
```

`field` accepts a variable name, a concise name, a Python spelling (`MaxItr__1`), or a name with
the unit spelled another way (`GenMvar`, `GenMegaVar` both resolve to `GenMVR`, with a note saying
so). `search` reads plain English: "reactive power", "megavars" and "mvar" all mean Mvar; "real
power" and "active power" mean MW; "per unit" means pu. Run from the kit root; it needs `openpyxl`.

### Look it up by hand in Case Object Fields.txt

The export has one block per object. The object name sits alone in column 1; the field rows under
it have column 4 = variable name, column 5 = concise name, column 7 = description, column 8 =
dialog path (`Mvar Output\Mvar`). Filter to the object first, then match the concise name:

```bash
awk -F'\t' '$1!=""{obj=$1} obj=="Gen" && $5=="Mvar" {print $4" | "$5" | "$7}' "Case Object Fields.txt"
# GenMVR | Mvar | 'Generator's present Mvar ouput'
```

To browse every Mvar field on the object, match the dialog path instead: `$8 ~ /Mvar Output/`.

The same search across the whole file without the object filter is how `GenMvar` leads you to
`Area.BGGenMVR` instead of `Gen.GenMVR`.

### How PowerWorld spells variable names

| Pattern | Example | Meaning |
|---|---|---|
| `MVR` for Mvar | `GenMVR`, `LoadMVR`, `LineMVR` | Variable names abbreviate Mvar; concise names and dialog paths spell `Mvar` |
| `BG` prefix | `Area.BGGenMVR` | An aggregate ("sum of generator Mvars in the area"), not a device value |
| `:n` suffix | `AreaNum:1`, `GenMVRPercent:1` | A variant of the base field; in esapp attributes it is `__1` |
| `PU`, `KV` | `BusPUVolt`, `BusKVVolt` | Per-unit and kV versions of one quantity |
| `SetPoint` | `GenMWSetPoint`, `GenMvrSetPoint` | Same as the output field while in service; keeps its value when the unit is open |

### Fields used most often (checked against the Simulator 25 export)

| Object | Quantity | Variable name | Concise name |
|---|---|---|---|
| Gen | MW output | `GenMW` | `MW` |
| Gen | Mvar output | `GenMVR` | `Mvar` |
| Gen | MW / Mvar setpoint (kept when open) | `GenMWSetPoint` / `GenMvrSetPoint` | `MWSetPoint` / `MvarSetPoint` |
| Gen | Mvar limits | `GenMVRMax` / `GenMVRMin` | `MvarMax` / `MvarMin` |
| Gen | Status (`Open`/`Closed`) | `GenStatus` | `Status` |
| Load | MW / Mvar | `LoadMW` / `LoadMVR` | `MW` / `Mvar` |
| Load | Status | `LoadStatus` | `Status` |
| Bus | Voltage pu / kV / angle (deg) | `BusPUVolt` / `BusKVVolt` / `BusAngle` | `Vpu` / `kV` / `Vangle` |
| Branch | MW / Mvar at the from bus | `LineMW` / `LineMVR` | `MWFrom` / `MvarFrom` |
| Branch | Status | `LineStatus` | `Status` |
| Shunt | Nominal / actual Mvar | `SSNMVR` / `SSAMVR` | `MvarNom` / `Mvar` |

Example, with ESA or esapp's `SAW`:

```python
gens = saw.GetParametersMultipleElement("Gen", ["BusNum", "GenID", "GenMW", "GenMVR", "GenStatus"])
```

### Open generators read zero

Per the export's description of `GenMWSetPoint`: when a generator is out of service, the MW field
returns 0.0 while the setpoint field still returns the setpoint. The same holds for `GenMVR` and
`GenMvrSetPoint`. Sum `GenMW`/`GenMVR` for what the case is actually producing; sum the setpoint
fields for what the fleet is set to produce, open units included.

### Writing GenMVR

`GenMVR` is writable only with a condition: normally enterable, but with AVR = YES only from an AUX
file or copy/paste. esapp also marks it not settable (see
[esapp-script-command-wrappers](../concepts/esapp-script-command-wrappers.md)). To change a
generator's reactive output, change its voltage setpoint (`GenVoltSet`) or turn AVR off first.
