---
title: "TS Models — Exciters (Part 5 of 5)"
part: "Transient Models"
chapter_file: "39-ts-models-exciters-part5.md"
topics: 50
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Exciters (Part 5 of 5)

Excitation system models (IEEE types, ESST/ESAC/EXST families, REEC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (50)**

- [ST6C](#st6c)
- [ST6C_PTI](#st6c-pti)
- [ST7C](#st7c)
- [ST8C](#st8c)
- [ST9C](#st9c)
- [ST10C](#st10c)
- [TEXS](#texs)
- [URST5T](#urst5t)
- [WT2E](#wt2e)
- [WT2E1](#wt2e1)
- [WT3E](#wt3e)
- [WT4E](#wt4e)
- [WT4E1](#wt4e1)
- [Converter/Renewable](#converterrenewable)
- [Excitation AC](#excitation-ac)
- [Excitation DC](#excitation-dc)
- [Excitation Static](#excitation-static)
- [Other](#other)
- [PlayIn](#playin)
- [BPA Exciters](#bpa-exciters)
- [BPA_EA](#bpa-ea)
- [BPA_EB](#bpa-eb)
- [BPA_EC](#bpa-ec)
- [BPA_ED](#bpa-ed)
- [BPA_EE](#bpa-ee)
- [BPA_EF](#bpa-ef)
- [BPA_EG](#bpa-eg)
- [BPA_EJ](#bpa-ej)
- [BPA_EK](#bpa-ek)
- [BPA_FA](#bpa-fa)
- [BPA_FB](#bpa-fb)
- [BPA_FC](#bpa-fc)
- [BPA_FD](#bpa-fd)
- [BPA_FE](#bpa-fe)
- [BPA_FF](#bpa-ff)
- [BPA_FG](#bpa-fg)
- [BPA_FH](#bpa-fh)
- [BPA_FJ](#bpa-fj)
- [BPA_FK](#bpa-fk)
- [BPA_FL](#bpa-fl)
- [BPA_FM](#bpa-fm)
- [BPA_FN](#bpa-fn)
- [BPA_FO](#bpa-fo)
- [BPA_FP](#bpa-fp)
- [BPA_FQ](#bpa-fq)
- [BPA_FR](#bpa-fr)
- [BPA_FS](#bpa-fs)
- [BPA_FT](#bpa-ft)
- [BPA_FU](#bpa-fu)
- [BPA_FV](#bpa-fv)

---

<a id="st6c"></a>

## ST6C

*Source: [`Content/TransientModels_HTML/Exciter ST6C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST6C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tg \< 0.5\*Mult\*TimeStep then Tg = 0, ElseIf 0.5\*Mult\*TimeStep \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ts = Mult\*TimeStep
  - Kff and Km: (Kff + Km) can not be zero. Must be fixed.
  - Kpa and Kia: Kpa can't be 0 if Kia = 0, if true then Kpa changed to 40.
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If VMmax \< VMmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If VM \> VMmax, then VMmax = VM or if VM \< VMmin, then VMmin = VM
  - If VA \> VAmax, then VAmax = VA or if VA \< VAmin, then VAmin = VA

Model Equations and/or Block Diagrams

![Exciter ST6C 0001](images/Exciter_ST6C_0001.svg)

![Exciter ST6C 0002](images/Exciter_ST6C_0002.svg)

**Parameters:**

|           |                                                                                                            |
| --------- | ---------------------------------------------------------------------------------------------------------- |
| OEL       | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, Sum after LV gate 1; if = 4, LV gate 2 |
| UEL       | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, Sum after LV gate 1; if = 4, HV gate 2 |
| Tr        | Filter time constant, sec.                                                                                 |
| Kpa       | Regulator proportional gain, p.u. (\> 0.)                                                                  |
| Kia       | Regulator integral gain, sec-1(\> 0.)                                                                      |
| VaMax     | PI maximum output, p.u.                                                                                    |
| VaMin     | PI minimum output, p.u.                                                                                    |
| Kff       | Feedforward gain, p.u.                                                                                     |
| Km        | Main gain, p.u.                                                                                            |
| Kcl       | Field current limiter conversion factor                                                                    |
| Klr       | Field current limiter gain, p.u.                                                                           |
| Ilr       | Field current limiter setpoint, p.u.                                                                       |
| Vrmax     | Maximum regulator output, p.u.                                                                             |
| Vrmin     | Minimum regulator output, p.u.                                                                             |
| Kg        | Feedback gain p.u.                                                                                         |
| Tg        | Feedback time constant, sec.                                                                               |
| VmMax     | Vm Maximum                                                                                                 |
| VmMin     | Vm Minimum                                                                                                 |
| Ta        | Voltage regulator time constant, sec                                                                       |
| Kc        | Rectifier regulation factor, pu                                                                            |
| Kp        | Potential source gain, pu                                                                                  |
| Ki        | Current source gain, pu                                                                                    |
| Xl        | P-bar leakage reactance, pu                                                                                |
| ThetaPDeg | Phase angle of potential source, degrees                                                                   |
| VbMax     | Maximum excitation voltage, pu                                                                             |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)                                                          |

---

<a id="st6c-pti"></a>

## ST6C_PTI

*Source: [`Content/TransientModels_HTML/Exciter ST6C_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST6C_PTI.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tg \< 0.5\*Mult\*TimeStep then Tg = 0, ElseIf 0.5\*Mult\*TimeStep \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ts = Mult\*TimeStep
  - If 0.0 \< Tda \< 0.5\*Mult\*TimeStep then Tda = 0, ElseIf 0.5\*Mult\*TimeStep \< Tda \< Mult\*TimeStep then Tda = Mult\*TimeStep
  - Kff and Km: (Kff + Km) can not be zero. Must be fixed.
  - Kpa and Kia: Kpa can't be 0 if Kia = 0, if true then Kpa changed to 40.
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If VMmax \< VMmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If VM \> VMmax, then VMmax = VM or if VM \< VMmin, then VMmin = VM
  - If VA \> VAmax, then VAmax = VA or if VA \< VAmin, then VAmin = VA

Model Equations and/or Block Diagrams

![Exciter ST6C PTI 0001](images/Exciter_ST6C_PTI_0001.svg)

![Exciter ST6C PTI 0002](images/Exciter_ST6C_PTI_0002.svg)

**Parameters:**

|           |                                                                                                                |
| --------- | -------------------------------------------------------------------------------------------------------------- |
| OEL       | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, Sum after LV gate 1; if = 4, LV gate 2     |
| UEL       | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, Sum after LV gate 1; if = 4, HV gate 2     |
| SCL       | SCL input: if \< 2, add to error signal; if = 2, Take Over 1; if = 3, Sum after LV gate 1; if = 4, Take Over 2 |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)                                                              |
| Tr        | Filter time constant, sec.                                                                                     |
| Kpa       | Regulator proportional gain, p.u. (\> 0.)                                                                      |
| Kia       | Regulator integral gain, sec-1(\> 0.)                                                                          |
| Kda       | Regulator derivative gain                                                                                      |
| Tda       | Regulator derivative channel time constant                                                                     |
| VaMax     | PI maximum output, p.u.                                                                                        |
| VaMin     | PI minimum output, p.u.                                                                                        |
| Kff       | Feedforward gain, p.u.                                                                                         |
| Km        | Main gain, p.u.                                                                                                |
| Kcl       | Field current limiter conversion factor                                                                        |
| Klr       | Field current limiter gain, p.u.                                                                               |
| Ilr       | Field current limiter setpoint, p.u.                                                                           |
| Vrmax     | Maximum regulator output, p.u.                                                                                 |
| Vrmin     | Minimum regulator output, p.u.                                                                                 |
| Kg        | Feedback gain p.u.                                                                                             |
| Tg        | Feedback time constant, sec.                                                                                   |
| VmMax     | Model Parameters\\VmMax                                                                                        |
| VmMin     | Model Parameters\\VmMin                                                                                        |
| Ta        | Voltage regulator time constant, sec                                                                           |
| Kp        | Potential source gain, pu                                                                                      |
| Ki        | Current source gain, pu                                                                                        |
| Xl        | P-bar leakage reactance, pu                                                                                    |
| ThetaPDeg | Phase angle of potential source, degrees                                                                       |
| Kc        | Rectifier regulation factor, pu                                                                                |
| VbMax     | Maximum excitation voltage, pu                                                                                 |

---

<a id="st7c"></a>

## ST7C

*Source: [`Content/TransientModels_HTML/Exciter ST7C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST7C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vmax \< Vmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> Vrmax, then Vrmax = Efd or if Efd \< Vrmin, then Vrmin = Efd
  - If Vfb \> Vmax, then Vmax = Vfb or if Vfb \< Vmin, then Vmin = Vfb

Model Equations and/or Block Diagrams

![Exciter ST7C 0001](images/Exciter_ST7C_0001.svg)

**Parameters:**

|       |                                                                                              |
| ----- | -------------------------------------------------------------------------------------------- |
| OEL   | OEL input selector: 1 – add to Vref, 2 – input LV gate, 3 – output LV gate, 0 – no OEL input |
| UEL   | UEL input selector: 1 – add to Vref, 2 – input HV gate, 3 – output HV gate, 0 – no UEL input |
| Tr    | Filter time constant, sec.                                                                   |
| Tg    | Input lead-lag numerator time constant, sec.                                                 |
| Tf    | Input lead-lag denominator time constant, sec.                                               |
| Vmax  | Maximum voltage reference signal, p.u.                                                       |
| Vmin  | Minimum voltage reference signal, p.u.                                                       |
| Kpa   | Regulator proportional gain, p.u. (\> 0.)                                                    |
| Vrmax | Maximum field voltage output, p.u.                                                           |
| Vrmin | Minimum field voltage output, p.u.                                                           |
| Kh    | High-value gate feedback gain, p.u.                                                          |
| Kl    | Low-value gate feedback gain, p.u.                                                           |
| Tc    | Lead-lag numerator time constant, sec.                                                       |
| Tb    | Lead-lag denominator time constant, sec.                                                     |
| Kia   | Feedback gain, p.u.. (\> 0.)                                                                 |
| Tia   | Feedback time constant, sec..                                                                |
| Ta    | Thyristor bridge firing control equivalent time constant                                     |

---

<a id="st8c"></a>

## ST8C

*Source: [`Content/TransientModels_HTML/Exciter ST8C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST8C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - Kpa and Kia: Kpa can't be 0 if Kia = 0, if true then Kpa changed to 1.
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kf = 0 then Kf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If VAmax \< VAmin then swap the values
  - If VPImax \< VPImin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va
  - If IFDref \> VPImax, then VPImax = IFDref or if IFDref \< VPImin, then VPImin = IFDref

Model Equations and/or Block Diagrams

![Exciter ST8C 0001](images/Exciter_ST8C_0001.svg)

**Parameters:**

|           |                                                                 |
| --------- | --------------------------------------------------------------- |
| OEL       | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL       | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL       | SCL input: if = 2, Take Over; if \< 2, add to error signal      |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)               |
| Tr        | Filter time constant, sec.                                      |
| Kpr       | Voltage regulator proportional gain, p.u.                       |
| Kir       | Voltage regulator integral gain, p.u.                           |
| VPImax    | Model Parameters\\VPImax                                        |
| VPImin    | Model Parameters\\VPImin                                        |
| Kpa       | Field current regulator proportional gain, p.u. (\> 0.)         |
| Kia       | Field current regulator integral gain, sec-1(\> 0.)             |
| VaMax     | Maximum field current regulator output, p.u.                    |
| VaMin     | Minimum field current regulator output, p.u.                    |
| Ka        | Voltage regulator gain                                          |
| Ta        | Voltage regulator time constant, sec                            |
| Vrmax     | Maximum field current regulator output, p.u.                    |
| Vrmin     | Minimum field current regulator output, p.u.                    |
| Kf        | Rate feedback gain, pu                                          |
| Tf        | Rate feedback constant, sec                                     |
| KC1       | Rectifier loading factor proportional to commutating reactance  |
| Kp        | Potential source gain, pu                                       |
| KI1       | Current source gain, pu                                         |
| Xl        | P-bar leakage reactance, pu                                     |
| ThetaPDeg | Phase angle of potential source, degrees                        |
| VB1max    | Maximum excitation voltage, pu                                  |
| KC2       | Rectifier loading factor proportional to commutating reactance  |
| KI2       | Current source gain, pu                                         |
| VB2max    | Maximum excitation voltage, pu                                  |

---

<a id="st9c"></a>

## ST9C

*Source: [`Content/TransientModels_HTML/Exciter ST9C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST9C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tas \< 0.5\*Mult\*TimeStep then Tas = 0, ElseIf 0.5\*Mult\*TimeStep \< Tas \< Mult\*TimeStep then Tas = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tbd \< 0.5\*Mult\*TimeStep then Tbd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tbd \< Mult\*TimeStep then Tbd = Mult\*TimeStep
  - If Ta = 0 then Ta = Mult\*TimeStep
  - If KA = 0 then KA = Mult\*TimeStep
  - If TAUEL= 0 then TAUEL= Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ST9C 0001](images/Exciter_ST9C_0001.svg)

**Parameters:**

|           |                                                                  |
| --------- | ---------------------------------------------------------------- |
| OEL       | OEL input: if = 2, LV gate; if \< 2, add to error signal         |
| UEL       | UEL input: if = 2, HV gate; if \< 2, add to error signal         |
| SCL       | SCL input: if = 2, Take Over; if \< 2, add to error signal       |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)                |
| Tr        | Filter time constant, sec.                                       |
| Tcd       | Time constant of differential part of AVR, sec.                  |
| Tbd       | Filter time constant of differential part of AVR, sec.           |
| Za        | Dead-band for differential part influence on AVR, sec.           |
| Ka        | AVR gain                                                         |
| Ku        | Gain associated with activation of takeover UEL                  |
| Ta        | Time constant of AVR, sec.                                       |
| Tauel     | Time coonstant of underexcitation limiter, sec.                  |
| Vrmax     | Maximum regulator output, p.u.                                   |
| Vrmin     | Minimum regulator output, p.u.                                   |
| Kas       | Power converter gain, proportional to supply voltage, p.u.       |
| Tas       | Equivalent time constant of power converter firing control, sec. |
| Kp        | Potential circuit voltage gain coefficient                       |
| ThetaPDeg | Potential circuit phase angle, degrees                           |
| Ki        | Potential circuit current gain coefficient                       |
| Xl        | Reactance associated with compound source, p.u.                  |
| Kc        | Rectifier loading factor proportional to commutating reactance   |
| VbMax     | Maximum limit on exciter voltage based on supply condition, p.u. |

---

<a id="st10c"></a>

## ST10C

*Source: [`Content/TransientModels_HTML/Exciter ST10C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST10C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Kr \<= 0 then Kr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vrsmax \< Vrsmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If Vrs \> Vrsmax, then Vrsmax = Vrs limits or if Vrs \< Vrsmin, then Vrsmin = Vrs

Model Equations and/or Block Diagrams

![Exciter ST10C 0001](images/Exciter_ST10C_0001.svg)

![Exciter ST10C 0002](images/Exciter_ST10C_0002.svg)

**Parameters:**

|        |                                                                                            |
| ------ | ------------------------------------------------------------------------------------------ |
| VOS    | PSS input: if = 1, add to error signal; if = 2, add in SWLim Logic; if = 3, add to VS2 Sum |
| OEL    | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2              |
| UEL    | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2              |
| SCL    | SCL input: if \< 2, add to error signal; if = 2, Take Over 2; if = 3, Take Over 3          |
| SW1    | Logical switch 1 (1 = Position A, 2 = Position B)                                          |
| Tr     | Filter time constant, sec                                                                  |
| Kr     | Field voltage feedback gain, pu                                                            |
| TC1    | Lead time constant 1, sec                                                                  |
| TB1    | Lag time constant 1, sec                                                                   |
| TC2    | Lead time constant 2, sec                                                                  |
| TB2    | Lag time constant 2, sec                                                                   |
| TUC1   | UEL lead time constant 1, sec.                                                             |
| TUB1   | UEL lag time constant 1, sec.                                                              |
| TUC2   | UEL lead time constant 2, sec.                                                             |
| TUB2   | UEL lag time constant 2, sec.                                                              |
| TOC1   | OEL lead time constant 1, sec.                                                             |
| TOB1   | OEL lag time constant 1, sec.                                                              |
| TOC2   | OEL lead time constant 2, sec.                                                             |
| TOB2   | OEL lag time constant 2, sec.                                                              |
| VRSmax | Maximum exciter control signal, pu                                                         |
| VRSmin | Minimum exciter control signal, pu                                                         |
| VRmax  | Maximum exciter control signal, pu                                                         |
| VRmin  | Minimum exciter control signal, pu                                                         |
| T1     | Inverse timing current constant, sec                                                       |
| Kp     | Potential source gain, pu                                                                  |
| KC     | Rectifier loading factor proportional to commutating reactance                             |
| KI     | Potential circuit (current) gain coefficient                                               |
| XL     | Reactance associated with potential source                                                 |
| ThetaP | Potencial circuit phase angle, degrees                                                     |
| VbMax  | Maximum available exciter field voltage                                                    |

---

<a id="texs"></a>

## TEXS

*Source: [`Content/TransientModels_HTML/Exciter TEXS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter TEXS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tvd \< Mult\*TimeStep then Tvd = Mult\*TimeStep
  - If 0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Ilr \> (Vr/Klr + Ifd)/Kcl, then Ilr = (Vr/Klr + Ifd)/Kcl

(local\_Vr/fKlr + local\_Ifd)/fKcl,fIlr,'Ilr'

Model Equations and/or Block Diagrams

![Exciter TEXS 0001](images/Exciter_TEXS_0001.svg)

**Parameters:**

|       |                                                 |
| ----- | ----------------------------------------------- |
| Tr    | Transducer time constant, sec                   |
| Kvp   | Voltage regulator proportional gain             |
| Kvi   | Voltage regulator integral gain                 |
| Kvd   | Voltage regulator derivative gain               |
| Tvd   | Voltage regulator derivative time constant, sec |
| ViMax | Voltage regulator input limit, pu               |
| Kff   | Feedforward gain                                |
| Km    | DC converter gain                               |
| Vrmax | Maximum control element output, pu              |
| Vrmin | Minimum control element output, pu              |
| Kg    | Field current regulator feedback gain           |
| Tg    | Field current feedback time constant, sec       |
| Kcl   | Field current limit setpoint gain               |
| Klr   | Gain on field current limit                     |
| Ilr   | Maximum field current, pu                       |
| Xc    | Exciter compounding reactance, pu               |
| Flag  | Excitation power source flag                    |

---

<a id="urst5t"></a>

## URST5T

*Source: [`Content/TransientModels_HTML/Exciter URST5T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter URST5T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If 0.0 \< Tob1 \< 0.5\*Mult\*TimeStep then Tob1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tob1 \< Mult\*TimeStep then Tob1 = Mult\*TimeStep
  - If 0.0 \< Tob2 \< 0.5\*Mult\*TimeStep then Tob2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tob2 \< Mult\*TimeStep then Tob2 = Mult\*TimeStep
  - If 0.0 \< Tub2 \< 0.5\*Mult\*TimeStep then Tob2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tub2 \< Mult\*TimeStep then Tub2 = Mult\*TimeStep
  - If 0.0 \< Tub1 \< 0.5\*Mult\*TimeStep then Tub1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tub1 \< Mult\*TimeStep then Tub1 = Mult\*TimeStep
  - T1: If Mult\*TimeStep \> 4 then T1 = 0.25\*Mult\*TimeStep, else 1 \< T1 \< Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter URST5T 0001](images/Exciter_URST5T_0001.svg)

**Parameters:**

|       |                                      |
| ----- | ------------------------------------ |
| Tr    | Filter time constant, sec            |
| Tc1   | Lead time constant, sec              |
| Tb1   | Lag time constant, sec               |
| Tc2   | Lead time constant, sec              |
| Tb2   | Lag time constant, sec               |
| Kr    | Gain                                 |
| Vrmax | Maximum control element output, pu   |
| Vrmin | Minimum control element output, pu   |
| T1    | Inverse timing current constant, sec |
| Kc    | Rectifier regulation factor, pu      |

---

<a id="wt2e"></a>

## WT2E

*Source: [`Content/TransientModels_HTML/Exciter WT2E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter WT2E.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tw \< 0.5\*Mult\*TimeStep then Tw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If Rmax \< Rmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Rexternal \> Rmax, then Rmax = Rexternal or if Rexternal \< Rmin, then Rmin = Rexternal

Model Equations and/or Block Diagrams

![Exciter WT2E 0001](images/Exciter_WT2E_0001.svg)

**Parameters:**

|               |                                           |
| ------------- | ----------------------------------------- |
| Tw            | Speed time constant, sec                  |
| Kw            | Speed regulator gain                      |
| Tp            | P time constant, sec                      |
| Kp            | Potential source gain, pu                 |
| Kpp           | Proportional gain, pu                     |
| Kip           | Field current regulator proportional gain |
| Rmax          | Maximum external rotor resistance, pu     |
| Rmin          | Minimum external rotor resistance, pu     |
| Slip\_1       | Slip point 1 in Power vs Slip curve, pu   |
| Slip\_2       | Slip point 2 in Power vs Slip curve, pu   |
| Slip\_3       | Slip point 3 in Power vs Slip curve, pu   |
| Slip\_4       | Slip point 4 in Power vs Slip curve, pu   |
| Slip\_5       | Slip point 5 in Power vs Slip curve, pu   |
| Power\_Ref\_1 | Power point 1 in Power vs Slip curve, pu  |
| Power\_Ref\_2 | Power point 2 in Power vs Slip curve, pu  |
| Power\_Ref\_3 | Power point 3 in Power vs Slip curve, pu  |
| Power\_Ref\_4 | Power point 4 in Power vs Slip curve, pu  |
| Power\_Ref\_5 | Power point 5 in Power vs Slip curve, pu  |

---

<a id="wt2e1"></a>

## WT2E1

*Source: [`Content/TransientModels_HTML/Exciter WT2E1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter WT2E1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tsp \< 0.5\*Mult\*TimeStep then Tsp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tsp \< Mult\*TimeStep then Tsp = Mult\*TimeStep
  - If 0.0 \< Tpe \< 0.5\*Mult\*TimeStep then Tpe = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpe \< Mult\*TimeStep then Tpe = Mult\*TimeStep
  - If 0 \< Ti \< Mult\*TimeStep then Ti = Mult\*TimeStep
  - If Rmax \< Rmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Rexternal \> Rmax, then Rmax = Rexternal or if Rexternal \< Rmin, then Rmin = Rexternal

Model Equations and/or Block Diagrams

![Exciter WT2E1 0001](images/Exciter_WT2E1_0001.svg)

**Parameters:**

|      |                                       |
| ---- | ------------------------------------- |
| Tsp  | Speed time constant, sec              |
| Tpe  | P time constant, sec                  |
| Ti   | Integrator gain, sec                  |
| Kp   | Potential source gain, pu             |
| Rmax | Maximum external rotor resistance, pu |
| Rmin | Minimum external rotor resistance, pu |

---

<a id="wt3e"></a>

## WT3E

*Source: [`Content/TransientModels_HTML/Exciter WT3E and WT3E1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter WT3E and WT3E1.htm)*

**AutoCorrection Properties**

**WT3E**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tc \< 0.5\*Mult\*TimeStep then Tc = 0, ElseIf 0.5\*Mult\*TimeStep \< Tc \< Mult\*TimeStep then Tc = Mult\*TimeStep
  - If 0.0 \< Tpwr \< 0.5\*Mult\*TimeStep then Tpwr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpwr \< Mult\*TimeStep then Tpwr = Mult\*TimeStep
  - If 0 \< Tfp \< Mult\*TimeStep then Tfp = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If Xiqmax \< Xiqmin then swap the values

Following treatment is handled during the transient numerical simulation

  - If QCmd \> Qmax , then Qmax = QCmd or if QCmd \< Qmin , then Qmin = QCmd
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef
  - If EqppCMD \> Xiqmax, then Xiqmax = EqppCMD or if EqppCMD \< Xiqmin, then Xiqmin = EqppCMD
  - If Pord \> Pmax , then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

**WT3E1**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tfv \< 0.5\*Mult\*TimeStep then Tfv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfv \< Mult\*TimeStep then Tfv = Mult\*TimeStep
  - If 0.0 \< Tpwr \< 0.5\*Mult\*TimeStep then Tpwr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpwr \< Mult\*TimeStep then Tpwr = Mult\*TimeStep
  - If 0 \< Tfp \< Mult\*TimeStep then Tfp = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Xiqmax \< Xiqmin then swap the values

Following treatment is handled during the transient numerical simulation

  - If QCmd \> Qmax , then Qmax = QCmd or if QCmd \< Qmin , then Qmin = QCmd
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef
  - If EqppCMD \> Xiqmax, then Xiqmax = EqppCMD or if EqppCMD \< Xiqmin, then Xiqmin = EqppCMD
  - If Pord \> Pmax , then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Exciter WT3E and WT3E1 0001](images/Exciter_WT3E_and_WT3E1_0001.svg)

**Parameters for WT3E:**

|        |                                                                                                  |
| ------ | ------------------------------------------------------------------------------------------------ |
| varflg | 0 = Constant Q cntl; 1 = Use Wind Plant reactive power cntrl; -1 = Constant power factor control |
| vltflg | 1 = Use closed loop terminal voltage control; 0 = Bypass closed loop terminal voltage control    |
| Tfp    | Speed reference lag, sec                                                                         |
| Kpp    | Torque control proportional gain, pu P                                                           |
| Kip    | Torque control integral gain, pu P/sec                                                           |
| Tpwr   | Power control lag, sec                                                                           |
| Pmax   | Maximum power ord, pu                                                                            |
| Pmin   | Minimum power order, pu                                                                          |
| RPMax  | Power order rate limit, pu/sec                                                                   |
| Ipmax  | Maximum reactive current order, pu of rated current                                              |
| Wpmin  | Shaft speed at Pmin, pu                                                                          |
| WP20   | Shaft speed at 20% rated power, pu                                                               |
| WP40   | Shaft speed at 40% rated power, pu                                                               |
| WP60   | Shaft speed at 60% rated power, pu                                                               |
| PWP    | Minimum power for operating at wp100 speed, pu                                                   |
| WP100  | Shaft speed at rated power, pu                                                                   |
| Kqi    | Reactive control gain, pu V/pu Q sec                                                             |
| Kqv    | Terminal voltage control gain, pu V/pu V)                                                        |
| Qmax   | Maximum reactive power limit, pu                                                                 |
| Qmin   | Minimum reactive power limit, pu                                                                 |
| Vmax   | Maximum voltage limit, pu                                                                        |
| Vmin   | Minimum voltage limit, pu                                                                        |
| XIqmax | Terminal voltage regulator maximum limit, pu                                                     |
| XIqmin | Terminal voltage regulator minimum limit, pu                                                     |
| Tp     | Power factor control filter time constant, sec                                                   |
| Xc     | Compensating reactance for voltage control, pu                                                   |
| Tr     | Voltage transducer time constant, sec                                                            |
| Fn     | Fraction of WTG in Wind Plant that are on-line                                                   |
| Kiv    | Integral gain, pu Q/pu V sec                                                                     |
| Kpv    | Proportional gain, pu Q/pu V                                                                     |
| Tv     | Proportional path time constant, sec                                                             |
| Tc     | Communication lag, sec                                                                           |

**Parameters for WT3E1:**

|        |                                                                                                                                                                                                               |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| varflg | 0 = Constant Q cntl; 1 = Use Wind Plant reactive power cntrl; -1 = Constant power factor control                                                                                                              |
| vltflg | 0 : Bypass terminal voltage control; 1 : Eqcmd limits are calculated as VTerm and +XIQmin and VTerm and +XIQmax i.e limits are functions of terminal voltage; 2 : Eqcmd limits are equal to XIQmin and XIQmax |
| Tfv    | Filter time constant in voltage regulator, sec                                                                                                                                                                |
| Kpv    | Proportional gain in voltage regulator, pu                                                                                                                                                                    |
| Kiv    | Integrator gain in voltage regulator, pu                                                                                                                                                                      |
| Xc     | Line drop compensation reactance, pu                                                                                                                                                                          |
| Tfp    | Filter time constant in torque regulator, sec                                                                                                                                                                 |
| Kpp    | Proportional gain in torque regulator, pu                                                                                                                                                                     |
| Kip    | Integrator gain in torque regulator, pu                                                                                                                                                                       |
| Pmax   | Max limit in torque regulator, pu                                                                                                                                                                             |
| Pmin   | Min limit in torque regulator, pu                                                                                                                                                                             |
| Qmax   | Max limit in voltage regulator, pu                                                                                                                                                                            |
| Qmin   | Min limit in voltage regulator, pu                                                                                                                                                                            |
| Ipmax  | Max active current limit                                                                                                                                                                                      |
| Tr     | Voltage sensor time constant                                                                                                                                                                                  |
| RPMax  | Max power order derivative                                                                                                                                                                                    |
| RPMin  | Min power order derivative                                                                                                                                                                                    |
| Tpwr   | Power filter time constant                                                                                                                                                                                    |
| Kqi    | MVAR/Voltage gain                                                                                                                                                                                             |
| Vmin   | Min voltage limit                                                                                                                                                                                             |
| Vmax   | Max voltage limit                                                                                                                                                                                             |
| Kqv    | Voltage/MVAR gain                                                                                                                                                                                             |
| XIqmin | Minimum reactive power, pu                                                                                                                                                                                    |
| XIqmax | Maximum reactive power, pu                                                                                                                                                                                    |
| Tv     | Lag time constant in WindVar controller                                                                                                                                                                       |
| Tp     | Pelec filter in fast PF controller                                                                                                                                                                            |
| Fn     | A portion of online wind turbines                                                                                                                                                                             |
| Wpmin  | Shaft speed at Pmin, pu                                                                                                                                                                                       |
| WP20   | Shaft speed at 20% rated power, pu                                                                                                                                                                            |
| WP40   | Shaft speed at 40% rated power, pu                                                                                                                                                                            |
| WP60   | Shaft speed at 60% rated power, pu                                                                                                                                                                            |
| PWP    | Minimum power for operating at ωP100 speed, pu                                                                                                                                                                |
| WP100  | Shaft speed at 100% rated power, pu                                                                                                                                                                           |

---

<a id="wt4e"></a>

## WT4E

*Source: [`Content/TransientModels_HTML/Exciter WT4E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter WT4E.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpwr \< 0.5\*Mult\*TimeStep then Tpwr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpwr \< Mult\*TimeStep then Tpwr = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If QCmd \> Qmax , then Qmax = QCmd or if QCmd \< Qmin , then Qmin = QCmd
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef

Model Equations and/or Block Diagrams

![Exciter WT4E 0001](images/Exciter_WT4E_0001.svg)

**Parameters:**

|        |                                                                                                                      |
| ------ | -------------------------------------------------------------------------------------------------------------------- |
| varflg | 1 = Qord from WindCONTROL emulation; -1 = Qord from vref (i.e., separate model); 0 = Power factor control (pfaflg=1) |
| Kqi    | Q cointreoglr al gain                                                                                                |
| Kvi    | V cointreoglr al gain                                                                                                |
| Vmax   | Maximum V at regulated bus, pu                                                                                       |
| Vmin   | Minimum V at regulated bus, pu                                                                                       |
| Qmax   | Maximum Q command, pu                                                                                                |
| Qmin   | Minimum Q command, pu                                                                                                |
| Tr     | WindCONTROL ge vmoeltaasurement lag, sec                                                                             |
| Tc     | Lag between WindCONTROL output and wind turbine, sec                                                                 |
| Kpv    | WindCONTROL gularteor proportional gain                                                                              |
| Kiv    | WindCONTROLregulator integral gain                                                                                   |
| pfaflg | 1 = regulate power factor angle; 0 = regulate Q                                                                      |
| Fn     | Fraction of WTGs in wind farm that are on-line                                                                       |
| Tv     | Time constant in proportional path of WindCONTROL emulator, sec                                                      |
| Tpwr   | Time constant in power measurement for PFA control (Tp), sec                                                         |
| Iphl   | Hard limit on real current, pu                                                                                       |
| Iqhl   | Hard limit on reactive current, pu                                                                                   |
| Pqflag | 0 = Q priority ; 1 = P priority                                                                                      |
| ImaxTD | Maximum temperature dependent converter current, pu                                                                  |
| Viqlim | Max. voltage dependent reactive current limit, pu                                                                    |

---

<a id="wt4e1"></a>

## WT4E1

*Source: [`Content/TransientModels_HTML/Exciter WT4E1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter WT4E1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tfv \< 0.5\*Mult\*TimeStep then Tfv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfv \< Mult\*TimeStep then Tfv = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tpwr \< 0.5\*Mult\*TimeStep then Tpwr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpwr \< Mult\*TimeStep then Tpwr = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If dPmax \< dPmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If QCmd \> Qmax , then Qmax = QCmd or if QCmd \< Qmin , then Qmin = QCmd
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef

Model Equations and/or Block Diagrams

![Exciter WT4E1 0001](images/Exciter_WT4E1_0001.svg)

**Parameters:**

|        |                                                                                                                                        |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| pfaflg | 0 if PF fast control disabled; 1 if PF fast control enabled                                                                            |
| varflg | 0 if Qord is not provided by WindVar, if VARFLG = PFAFLG = 0 then Qord is provided as a Qref = const; 1 if Qord is provided by WindVar |
| Pqflag | 0 for Q priority; 1 for P priority                                                                                                     |
| Tfv    | Filter time constant in Voltage regulator, sec                                                                                         |
| Kpv    | Proportional gain in Voltage regulator, pu                                                                                             |
| Kiv    | Integrator gain in Voltage regulator, pu                                                                                               |
| Kpp    | Proportional gain in Active Power regulator, pu                                                                                        |
| Kip    | Integrator gain in Active Power regulator, pu                                                                                          |
| Kf     | Rate feedback gain, pu                                                                                                                 |
| Tf     | Rate feedback time constant, sec                                                                                                       |
| Qmax   | Max limit in Voltage regulator, pu                                                                                                     |
| Qmin   | Min limit in Voltage regulator, pu                                                                                                     |
| Ipmax  | Max active current limit                                                                                                               |
| Tr     | Voltage sensor time constant                                                                                                           |
| dPmax  | Max limit in power PI controller, pu                                                                                                   |
| dPmin  | Min limit in power PI controller, pu                                                                                                   |
| Tpwr   | Power filter time constant                                                                                                             |
| Kqi    | MVAR/Voltage gain                                                                                                                      |
| Vmin   | Min. voltage limit                                                                                                                     |
| Vmax   | Max. voltage limit                                                                                                                     |
| Kvi    | Voltage/MVAR Gain                                                                                                                      |
| Tv     | Lag time constant in WindVar controller                                                                                                |
| Tp     | Pelec filter in fast PF controller                                                                                                     |
| ImaxTD | Converter current limit                                                                                                                |
| Iphl   | Hard active current limit                                                                                                              |
| Iqhl   | Hard reactive current limit                                                                                                            |

---

<a id="converterrenewable"></a>

## Converter/Renewable

*Source: [`Content/TransientModels_HTML/ExciterFolder Converter.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder Converter.htm)*

_This topic has no body text in the source help file._

---

<a id="excitation-ac"></a>

## Excitation AC

*Source: [`Content/TransientModels_HTML/ExciterFolder ExcitationAC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder ExcitationAC.htm)*

_This topic has no body text in the source help file._

---

<a id="excitation-dc"></a>

## Excitation DC

*Source: [`Content/TransientModels_HTML/ExciterFolder ExcitationDC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder ExcitationDC.htm)*

_This topic has no body text in the source help file._

---

<a id="excitation-static"></a>

## Excitation Static

*Source: [`Content/TransientModels_HTML/ExciterFolder ExcitationStatic.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder ExcitationStatic.htm)*

_This topic has no body text in the source help file._

---

<a id="other"></a>

## Other

*Source: [`Content/TransientModels_HTML/ExciterFolder Other.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder Other.htm)*

_This topic has no body text in the source help file._

---

<a id="playin"></a>

## PlayIn

*Source: [`Content/TransientModels_HTML/ExciterFolder PlayIn.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder PlayIn.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-exciters"></a>

## BPA Exciters

*Source: [`Content/TransientModels_HTML/BPA Exciters.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BPA Exciters.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-ea"></a>

## BPA_EA

*Source: [`Content/TransientModels_HTML/Exciter BPA EA.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EA.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-eb"></a>

## BPA_EB

*Source: [`Content/TransientModels_HTML/Exciter BPA EB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ec"></a>

## BPA_EC

*Source: [`Content/TransientModels_HTML/Exciter BPA EC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ed"></a>

## BPA_ED

*Source: [`Content/TransientModels_HTML/Exciter BPA ED.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA ED.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ee"></a>

## BPA_EE

*Source: [`Content/TransientModels_HTML/Exciter BPA EE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EE.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ef"></a>

## BPA_EF

*Source: [`Content/TransientModels_HTML/Exciter BPA EF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EF.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-eg"></a>

## BPA_EG

*Source: [`Content/TransientModels_HTML/Exciter BPA EG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EG.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ej"></a>

## BPA_EJ

*Source: [`Content/TransientModels_HTML/Exciter BPA EJ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EJ.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ek"></a>

## BPA_EK

*Source: [`Content/TransientModels_HTML/Exciter BPA EK.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA EK.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fa"></a>

## BPA_FA

*Source: [`Content/TransientModels_HTML/Exciter BPA FA.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FA.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fb"></a>

## BPA_FB

*Source: [`Content/TransientModels_HTML/Exciter BPA FB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fc"></a>

## BPA_FC

*Source: [`Content/TransientModels_HTML/Exciter BPA FC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fd"></a>

## BPA_FD

*Source: [`Content/TransientModels_HTML/Exciter BPA FD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FD.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fe"></a>

## BPA_FE

*Source: [`Content/TransientModels_HTML/Exciter BPA FE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FE.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-ff"></a>

## BPA_FF

*Source: [`Content/TransientModels_HTML/Exciter BPA FF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FF.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fg"></a>

## BPA_FG

*Source: [`Content/TransientModels_HTML/Exciter BPA FG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FG.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fh"></a>

## BPA_FH

*Source: [`Content/TransientModels_HTML/Exciter BPA FH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FH.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fj"></a>

## BPA_FJ

*Source: [`Content/TransientModels_HTML/Exciter BPA FJ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FJ.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fk"></a>

## BPA_FK

*Source: [`Content/TransientModels_HTML/Exciter BPA FK.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FK.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fl"></a>

## BPA_FL

*Source: [`Content/TransientModels_HTML/Exciter BPA FL.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA FL.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-fm"></a>

## BPA_FM

*Source: [`Content/TransientModels_HTML/Exciter BPA_FM.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FM.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fn"></a>

## BPA_FN

*Source: [`Content/TransientModels_HTML/Exciter BPA_FN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FN.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fo"></a>

## BPA_FO

*Source: [`Content/TransientModels_HTML/Exciter BPA_FO.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FO.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fp"></a>

## BPA_FP

*Source: [`Content/TransientModels_HTML/Exciter BPA_FP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FP.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fq"></a>

## BPA_FQ

*Source: [`Content/TransientModels_HTML/Exciter BPA_FQ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FQ.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fr"></a>

## BPA_FR

*Source: [`Content/TransientModels_HTML/Exciter BPA_FR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FR.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fs"></a>

## BPA_FS

*Source: [`Content/TransientModels_HTML/Exciter BPA_FS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FS.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-ft"></a>

## BPA_FT

*Source: [`Content/TransientModels_HTML/Exciter BPA_FT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fu"></a>

## BPA_FU

*Source: [`Content/TransientModels_HTML/Exciter BPA_FU.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FU.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-fv"></a>

## BPA_FV

*Source: [`Content/TransientModels_HTML/Exciter BPA_FV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BPA_FV.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.
