---
title: "TS Models — Governors (Part 4 of 4)"
part: "Transient Models"
chapter_file: "40-ts-models-governors-part4.md"
topics: 32
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Governors (Part 4 of 4)

Turbine-governor models (GGOV, IEEEG, GAST, HYGOV, WT*T, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (32)**

- [WNDTGE](#wndtge)
- [WNDTRB](#wndtrb)
- [WPIDHY](#wpidhy)
- [WSHYDD](#wshydd)
- [WSHYGP](#wshygp)
- [WSIEG1](#wsieg1)
- [WT12T1](#wt12t1)
- [WT1T](#wt1t)
- [WT2T](#wt2t)
- [WT3T](#wt3t)
- [WT3T1](#wt3t1)
- [WT4T](#wt4t)
- [WTDTA1](#wtdta1)
- [WTGT_A](#wtgt-a)
- [WTGT_B](#wtgt-b)
- [Gas](#gas)
- [General](#general)
- [Hydro](#hydro)
- [PlayIn](#playin)
- [Steam](#steam)
- [Wind Turbines](#wind-turbines)
- [BPA Governors](#bpa-governors)
- [BPA_GG](#bpa-gg)
- [BPA_GH](#bpa-gh)
- [BPA_GIGATB](#bpa-gigatb)
- [BPA_GJGATB](#bpa-gjgatb)
- [BPA_GKGATB](#bpa-gkgatb)
- [BPA_GLTB](#bpa-gltb)
- [BPA_GSTA](#bpa-gsta)
- [BPA_GSTB](#bpa-gstb)
- [BPA_GSTC](#bpa-gstc)
- [BPA_GWTW](#bpa-gwtw)

---

<a id="wndtge"></a>

## WNDTGE

*Source: [`Content/TransientModels_HTML/Governor WNDTGE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WNDTGE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpc \< Mult\*TimeStep then Tpc = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If 0.0 \< Tpav \< Mult\*TimeStep then Tpav = Mult\*TimeStep
  - If 0.0 \< Tplwi \< 0.5\*Mult\*TimeStep then Tplwi = 0, ElseIf 0.5\*Mult\*TimeStep \< Tplwi \< Mult\*TimeStep then Tplwi = Mult\*TimeStep
  - If 0.0 \< Twowi \< 0.5\*Mult\*TimeStep then Twowi = 0, ElseIf 0.5\*Mult\*TimeStep \< Twowi \< Mult\*TimeStep then Twowi = Mult\*TimeStep
  - If Pmxwi \< Pmnwi then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Power Control \> PImax , then PImax = Power Control or if Power Control \< PImin, then PImin= Power Control

Model Equations and/or Block Diagrams

![Governor WNDTGE 0001](images/Governor_WNDTGE_0001.svg)   

![Governor WNDTGE 0002](images/Governor_WNDTGE_0002.svg)

**Parameters:**

|        |                                                           |
| ------ | --------------------------------------------------------- |
| Trate  | Turbine rating, MW                                        |
| Usize  | WTG unit size (1.5 or 3.6)                                |
| Spdwl  | Initial wind speed, m/s                                   |
| Tp     | Pitch control constant, sec                               |
| Tpc    | Power control time constant, sec                          |
| Kpp    | Pitch control proportional gain                           |
| Kip    | Pitch control integral gain                               |
| Kptrq  | Torque control proportional gain                          |
| Kitrq  | Torque control integral gain                              |
| Kpc    | Pitch compensation proportional gain                      |
| Kic    | Pitch compensation integral gain                          |
| PIMax  | Maximum blade pitch, deg                                  |
| PIMin  | Minimum blade pitch, deg                                  |
| PIRat  | Blade pitch rate limit, deg/sec                           |
| PWmax  | Maximum power order, pu                                   |
| PWmin  | Minimum power order, pu                                   |
| PWrat  | Power order rate limit, pu/sec                            |
| H      | Rotor inertia constant, p.u. (on turbine MW base)         |
| Nmass  | 2 for 2 mass model                                        |
| Hg     | Generator rotor inertia constant, p.u. (on turb. MW base) |
| Ktg    | Shaft stiffness (p.u. torque / rad)                       |
| Dtg    | Shaft damping (p.u. torque / p.u. speed)                  |
| Wbase  | Base mechanical speed (rad./sec.)                         |
| Tw     | Rate limit washout time constant, sec.                    |
| Apcflg | Active power control enable flag                          |
| Tpav   | Filter time constant on Pavail, sec.                      |
| Pa     | Active power point in frequency response curve, p.u.      |
| Pbc    | Active power point in frequency response curve, p.u.      |
| Pd     | Active power point in frequency response curve, p.u.      |
| Fa     | Frequency value for Pa frequency response curve, p.u.     |
| Fb     | Frequency value for Pbc frequency response curve, p.u.    |
| Fc     | Frequency value for Pbc frequency response curve, p.u.    |
| Fd     | Frequency value for Pd frequency response curve, p.u.     |
| Pmax   | Maximum wind plant power, p.u.                            |
| Pmin   | Minimum wind plant power, p.u.                            |
| Kwi    | WINENERTIA gain; default=0; typical non-default is 10     |
| dbwi   | Deadband, pu                                              |
| Tlpwi  | Low pass filter time constant, sec                        |
| Twowi  | Washout time constant, sec                                |
| urlwi  | Up rate limit                                             |
| drlwi  | Down rate limit                                           |
| Pmxwi  | Maximum power output, pu                                  |
| Pmnwi  | Minimum power output, pu                                  |
| wfflg  | WindFREE reactive power function flag (1=enabled)         |
| Td1    | Time delay in APC output, sec                             |
| Tpset  | Filter time constant on Pset, sec                         |

---

<a id="wndtrb"></a>

## WNDTRB

*Source: [`Content/TransientModels_HTML/Governor WNDTRB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WNDTRB.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WNDTRB 0001](images/Governor_WNDTRB_0001.svg)   

**Parameters:**

|       |                                                    |
| ----- | -------------------------------------------------- |
| Trate | Turbine rating, MW                                 |
| Ta    | Actuator time constant, sec                        |
| Kp    | Speed regulator gain                               |
| T1    | Speed regulator TGR numerator time constant, sec   |
| T2    | Speed regulator TGR denominator time constant, sec |
| BPRmx | Blade pitch maximum rate, deg/sec                  |
| Pwo   | Initial wind power, pu                             |

---

<a id="wpidhy"></a>

## WPIDHY

*Source: [`Content/TransientModels_HTML/Governor WPIDHY and WPIDHYD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WPIDHY and WPIDHYD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Treg \< 0.5\*Mult\*TimeStep then Treg = 0, ElseIf 0.5\*Mult\*TimeStep \< Treg \< Mult\*TimeStep then Treg = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Velmax \< Velmin then swap the values. If Velmax \< 0 then Velmax change sign to positive. If Velmin\> 0 then change sign to negative.
  - If Gmax \< Gmin then swap the values.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Gmax , then Gmax = Gate or if Gate \< Gmin , then Gmin = Gate
  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor WPIDHY 0001](images/Governor_WPIDHY_0001.svg)

**Parameters for WPIDHY:**

|        |                                              |
| ------ | -------------------------------------------- |
| Treg   | Input time constant of governor, sec         |
| Reg    | Reg Gain                                     |
| Kp     | Proportional gain, pu                        |
| Ki     | Integral gain, pu                            |
| Kd     | Derivative gain, pu                          |
| Ta     | Governor high frequency cutoff time constant |
| Tb     | Gate servo time constant                     |
| Velmax | Max gate opening velocity, pu/sec            |
| Velmin | Min gate opening velocity, pu/sec            |
| Gmax   | Maximum gate velocity, pu of mwcap           |
| Gmin   | Minimum gate velocity, pu of mwcap           |
| Tw     | Water inertia time constant, sec             |
| Pmax   | Maximum gate opening, pu of mwcap            |
| Pmin   | Minimum gate opening, pu of mwcap            |
| D      | Turbine damping coefficient                  |
| G0     | Gate opening at speed no load, pu            |
| G1     | Intermediate gate opening                    |
| P1     | Power at gate opening G1, pu                 |
| G2     | Intermediate gate opening                    |
| P2     | Power at gate opening G2, pu                 |
| P3     | Power at full opened gate, pu                |

**Parameters for WPIDHYD:**

|        |                                              |
| ------ | -------------------------------------------- |
| Treg   | Input time constant of governor, sec         |
| Reg    | Reg Gain                                     |
| Kp     | Proportional gain, pu                        |
| Ki     | Integral gain, pu                            |
| Kd     | Derivative gain, pu                          |
| Ta     | Governor high frequency cutoff time constant |
| Tb     | Gate servo time constant                     |
| Velmax | Max gate opening velocity, pu/sec            |
| Velmin | Min gate opening velocity, pu/sec            |
| Gmax   | Maximum gate velocity, pu of mwcap           |
| Gmin   | Minimum gate velocity, pu of mwcap           |
| Tw     | Water inertia time constant, sec             |
| Pmax   | Maximum gate opening, pu of mwcap            |
| Pmin   | Minimum gate opening, pu of mwcap            |
| D      | Turbine damping coefficient                  |
| G0     | Gate opening at speed no load, pu            |
| G1     | Intermediate gate opening                    |
| P1     | Power at gate opening G1, pu                 |
| G2     | Intermediate gate opening                    |
| P2     | Power at gate opening G2, pu                 |
| P3     | Power at full opened gate, pu                |
| dbH    | Deadband High (pu)                           |
| dbL    | Deadband Low (pu)                            |
| Trate  | Turbine rating, MW                           |

---

<a id="wshydd"></a>

## WSHYDD

*Source: [`Content/TransientModels_HTML/Governor WSHYDD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WSHYDD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Bturb\< Mult\*TimeStep then Bturb= Mult\*TimeStep
  - If 0.0 \< Tturb\< Mult\*TimeStep then Tturb= Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor WSHYDD 0001](images/Governor_WSHYDD_0001.svg)   

**Parameters:**

|          |                                           |
| -------- | ----------------------------------------- |
| Trate    | Turbine rating, MW                        |
| db1pu    | Intentional deadband width, pu            |
| Err      | Intentional db hysteresis, pu             |
| Td       | Input filter time constant, sec           |
| K1       | Double derivative gain, pu                |
| Tf       | Filter time constant, sec                 |
| K2       | Double derivative gain, pu, if Cflag = -1 |
| Ki       | Integral gain, pu                         |
| R        | Permanent droop, pu                       |
| Tt       | Power feedback time constant, sec         |
| Kg       | Gate servo gain, pu                       |
| Tp       | Lead time constant, sec                   |
| Velopen  | Maximum gate opening velocity, pu/sec     |
| Velclose | Maximum gate closing velocity, pu/sec     |
| Pmax     | Maximum gate opening, pu of mwcap         |
| Pmin     | Minimum gate opening, pu of mwcap         |
| db2pu    | Unintentional deadband, pu                |
| Gv1      | Nonlinear gain point 1, pu gv             |
| Pgv1     | Nonlinear gain point 1, pu power          |
| Gv2      | Nonlinear gain point 2, pu gv             |
| Pgv2     | Nonlinear gain point 2, pu power          |
| Gv3      | Nonlinear gain point 3, pu gv             |
| Pgv3     | Nonlinear gain point 3, pu power          |
| Gv4      | Nonlinear gain point 4, pu gv             |
| Pgv4     | Nonlinear gain point 4, pu power          |
| Gv5      | Nonlinear gain point 5, pu gv             |
| Pgv5     | Nonlinear gain point 5, pu power          |
| Aturb    | Turbine numerator multiplier              |
| Bturb    | Turbine denominator multiplier            |
| Tturb    | Turbine time constant, sec                |

---

<a id="wshygp"></a>

## WSHYGP

*Source: [`Content/TransientModels_HTML/Governor WSHYGP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WSHYGP.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Bturb \< Mult\*TimeStep then Bturb = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Pmax , then Pmax = Gate or if Gate \< Pmin , then Pmin = Gate

Model Equations and/or Block Diagrams

![Governor WSHYGP 0001](images/Governor_WSHYGP_0001.svg)   

**Parameters:**

|          |                                       |
| -------- | ------------------------------------- |
| Trate    | Turbine rating, MW                    |
| db1pu    | Intentional deadband width, pu        |
| Err      | Intentional db hysteresis, pu         |
| Td       | Input filter time constant, sec       |
| Ki       | Integral gain, pu                     |
| Tf       | Filter time constant, sec             |
| Kd       | Derivative gain, pu                   |
| Kp       | Proportional gain, pu                 |
| R        | Permanent droop, pu                   |
| Tt       | Power feedback time constant, sec     |
| Kg       | Gate servo gain, pu                   |
| Tp       | Lead time constant, sec               |
| Velopen  | Maximum gate opening velocity, pu/sec |
| Velclose | Maximum gate closing velocity, pu/sec |
| Pmax     | Maximum gate opening, pu of mwcap     |
| Pmin     | Minimum gate opening, pu of mwcap     |
| db2pu    | Unintentional deadband, pu            |
| Gv1      | Nonlinear gain point 1, pu gv         |
| Pgv1     | Nonlinear gain point 1, pu power      |
| Gv2      | Nonlinear gain point 2, pu gv         |
| Pgv2     | Nonlinear gain point 2, pu power      |
| Gv3      | Nonlinear gain point 3, pu gv         |
| Pgv3     | Nonlinear gain point 3, pu power      |
| Gv4      | Nonlinear gain point 4, pu gv         |
| Pgv4     | Nonlinear gain point 4, pu power      |
| Gv5      | Nonlinear gain point 5, pu gv         |
| Pgv5     | Nonlinear gain point 5, pu power      |
| Aturb    | Turbine numerator multiplier          |
| Bturb    | Turbine denominator multiplier        |
| Tturb    | Turbine time constant, sec            |

---

<a id="wsieg1"></a>

## WSIEG1

*Source: [`Content/TransientModels_HTML/Governor WSIEG1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WSIEG1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< 0.25\*Mult\*TimeStep then T3 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T3 \< 0.5\*Mult\*TimeStep then T3 = 0.5\*Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.
  - K1 to K8: Check K1+K3+K5+K7 and K2+K4+K6+K8 \<= 1.0 and if not normalized values to 1.0.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Pmax , then Pmax = Gate or if Gate \< Pmin , then Pmin = Gate

Model Equations and/or Block Diagrams

![Governor WSIEG1 0001](images/Governor_WSIEG1_0001.svg)

**Parameters:**

|        |                                                     |
| ------ | --------------------------------------------------- |
| K      | Governor gain (recirpocal of droop), pu             |
| T1     | Governor mechanism time constant, sec               |
| T2     | Turbine power time constant, sec                    |
| T3     | Turbine exhaust temperature time constant, sec      |
| Uo     | Maximum valve opening velocity, pu/sec              |
| Uc     | Maximum valve closing velocity, pu/sec              |
| Pmax   | Maximum gate opening, pu of mwcap                   |
| Pmin   | Minimum gate opening, pu of mwcap                   |
| T4     | Governor lead time constant, sec                    |
| K1     | Fraction of hp shaft power after first boiler pass  |
| K2     | Fraction of lp shaft power after first boiler pass  |
| T5     | Governor lag time constant, sec                     |
| K3     | Fraction of hp shaft power after second boiler pass |
| K4     | Fraction of lp shaft power after second boiler pass |
| T6     | T, sec                                              |
| K5     | Fraction of hp shaft power after third boiler pass  |
| K6     | Fraction of lp shaft power after third boiler pass  |
| T7     | T, sec                                              |
| K7     | Fraction of hp shaft power after fourth boiler pass |
| K8     | Fraction of lp shaft power after fourth boiler pass |
| db1pu  | Intentional deadband width, pu                      |
| Err    | Intentional db hysteresis, pu                       |
| db2pu  | Unintentional deadband, pu                          |
| Gv1    | Nonlinear gain point 1, pu gv                       |
| Pgv1   | Nonlinear gain point 1, pu power                    |
| Gv2    | Nonlinear gain point 2, pu gv                       |
| Pgv2   | Nonlinear gain point 2, pu power                    |
| Gv3    | Nonlinear gain point 3, pu gv                       |
| Pgv3   | Nonlinear gain point 3, pu power                    |
| Gv4    | Nonlinear gain point 4, pu gv                       |
| Pgv4   | Nonlinear gain point 4, pu power                    |
| Gv5    | Nonlinear gain point 5, pu gv                       |
| Pgv5   | Nonlinear gain point 5, pu power                    |
| Iblock | Pmin and Pmax initialization.                       |

---

<a id="wt12t1"></a>

## WT12T1

*Source: [`Content/TransientModels_HTML/Governor WT12T1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT12T1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Governor WT12T1 0001](images/Governor_WT12T1_0001.svg)

**Parameters:**

|        |                                              |
| ------ | -------------------------------------------- |
| H      | Rotor inertia constant, pu                   |
| Damp   | Damping factor, pu P/pu speed                |
| Htfrac | Turbine inertia fraction (Ht/H)              |
| Freq1  | First shaft torsional resonant frequency, Hz |
| DShaft | Shaft damping factor, pu P/pu speed          |

---

<a id="wt1t"></a>

## WT1T

*Source: [`Content/TransientModels_HTML/Governor WT1T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT1T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< H \< Mult\*TimeStep then H = Mult\*TimeStep
  - Freq1: If 1/Freq1 \< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WT1T 0001](images/Governor_WT1T_0001.svg)   

**Parameters:**

|        |                                              |
| ------ | -------------------------------------------- |
| Trate  | Turbine rating, MW                           |
| H      | Rotor inertia constant, pu                   |
| Damp   | Damping factor, pu P/pu speed                |
| Htfrac | Turbine inertia fraction (Ht/H)              |
| Freq1  | First shaft torsional resonant frequency, Hz |
| DShaft | Shaft damping factor, pu P/pu speed          |

---

<a id="wt2t"></a>

## WT2T

*Source: [`Content/TransientModels_HTML/Governor WT2T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT2T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< H \< Mult\*TimeStep then H = Mult\*TimeStep
  - Freq1: If 1/Freq1 \< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WT2T 0001](images/Governor_WT2T_0001.svg)   

**Parameters:**

|        |                                 |
| ------ | ------------------------------- |
| H      | Inertia                         |
| Damp   | Damping factor                  |
| Htfrac | Turbine inertia fraction        |
| Freq1  | First shaft torsional frequency |
| DShaft | Shaft damping factor            |

---

<a id="wt3t"></a>

## WT3T

*Source: [`Content/TransientModels_HTML/Governor WT3T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT3T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< H \< Mult\*TimeStep then H = Mult\*TimeStep
  - Freq1: If 1/Freq1 \< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WT3T 0001](images/Governor_WT3T_0001.svg)   

**Parameters:**

|        |                                              |
| ------ | -------------------------------------------- |
| VW     | Initial wind speed, pu of rated wind speed   |
| H      | Total inertia constant, sec                  |
| Damp   | Damping factor, pu P/pu speed                |
| Kaero  | Aerodynamic gain factor                      |
| Theta2 | Blade pitch at twice rated wind speed, deg   |
| Htfrac | Turbine inertia fraction (Ht/H)              |
| Freq1  | First shaft torsional resonant frequency, Hz |
| DShaft | Shaft damping factor, pu P/pu speed          |

---

<a id="wt3t1"></a>

## WT3T1

*Source: [`Content/TransientModels_HTML/Governor WT3T1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT3T1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< H \< Mult\*TimeStep then H = Mult\*TimeStep
  - Freq1: If 1/Freq1 \< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WT3T1 0001](images/Governor_WT3T1_0001.svg)   

**Parameters:**

|        |                                              |
| ------ | -------------------------------------------- |
| VW     | Initial wind speed, pu of rated wind speed   |
| H      | Total inertia constant, sec                  |
| Damp   | Damping factor, pu P/pu speed                |
| Kaero  | Aerodynamic gain factor                      |
| Theta2 | Blade pitch at twice rated wind speed, deg   |
| Htfrac | Turbine inertia fraction (Ht/H)              |
| Freq1  | First shaft torsional resonant frequency, Hz |
| DShaft | Shaft damping factor, pu P/pu speed          |

---

<a id="wt4t"></a>

## WT4T

*Source: [`Content/TransientModels_HTML/Governor WT4T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WT4T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If dPmx \< Pmnthen swap the values. If dPmx \< 0 then dPmx change sign to positive. If Pmn\> 0 then change sign to negative.
  - If 0.0 \< Tpw \< 0.5\*Mult\*TimeStep then Tpw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpw \< Mult\*TimeStep then Tpw = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Kip \> 1/(Mult\*TimeStep) then Kip = 1/Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

Model Equations and/or Block Diagrams

![Governor WT4T 0001](images/Governor_WT4T_0001.svg)

**Parameters:**

|       |                                 |
| ----- | ------------------------------- |
| MWCap | Turbine Rating, MW              |
| Tpw   | Pelec time constant, sec        |
| Kpp   | Pitch control proportional gain |
| Kip   | Pitch control integral gain     |
| Tf    | Washout time constant, sec      |
| Kf    | Model Parameters\\Kf            |
| dPmx  | Maximum PI limit, pu            |
| dPmn  | Minimum PI limit, pu            |

---

<a id="wtdta1"></a>

## WTDTA1

*Source: [`Content/TransientModels_HTML/Governor WTDTA1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WTDTA1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KShaft: If 1/(KShaft/(2\*Pi\*NominalFrequency) \* ( (Ht + Hg) \* 2\*Pi \* 60) / ( 2\*sqr(2\*Pi) \* Ht\*Hg ))\< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead with H = (Ht + Hg).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WTDTA1 0001](images/Governor_WTDTA1_0001.svg)   

**Parameters:**

|        |                                               |
| ------ | --------------------------------------------- |
| H      | Total Inertia Constant (s)                    |
| Damp   | Machine Damping Factor (pu)                   |
| Htfrac | Turbine Inertia Fraction (Ht/H)               |
| Freq1  | First Shaft Torsional Resonant Frequency (Hz) |
| Dshaft | Shaft Damping Factor (pu)                     |

---

<a id="wtgt-a"></a>

## WTGT_A

*Source: [`Content/TransientModels_HTML/Governor WTGT_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WTGT_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KShaft: If 1/(KShaft/(2\*Pi\*NominalFrequency) \* ( (Ht + Hg) \* 2\*Pi \* 60) / ( 2\*sqr(2\*Pi) \* Ht\*Hg ))\< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead with H = (Ht + Hg).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WTGT A 0001](images/Governor_WTGT_A_0001.svg)   

**Parameters:**

|        |                                                         |
| ------ | ------------------------------------------------------- |
| Ht     | Turbine inertia, MW-sec/MVA                             |
| Hg     | Generator inertia, MW-sec/MVA                           |
| DShaft | Shaft damping coefficient p.u.                          |
| KShaft | Spring constant, p.u.                                   |
| MWCap  | Model MVA Base, If \<= 0 then use base of machine model |
| W0     | Initial speed, pu                                       |

---

<a id="wtgt-b"></a>

## WTGT_B

*Source: [`Content/TransientModels_HTML/Governor WTGT_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WTGT_B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KShaft: If 1/(KShaft/(2\*Pi\*NominalFrequency) \* ( (Ht + Hg) \* 2\*Pi \* 60) / ( 2\*sqr(2\*Pi) \* Ht\*Hg ))\< TwoMassMassFrequencyMultiplier\*TimeStep. We will treat as a one-mass model instead with H = (Ht + Hg).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WTGT B 0001](images/Governor_WTGT_B_0001.svg)   

**Parameters:**

|        |                                                           |
| ------ | --------------------------------------------------------- |
| Ht     | Turbine inertia, MW-sec/MVA                               |
| Hg     | Generator inertia, MW-sec/MVA                             |
| DShaft | Shaft damping coefficient p.u.                            |
| KShaft | Spring constant, p.u.                                     |
| MWCap  | Model MVA Base, If \<= 0 then use base of machine model   |
| W0     | Initial speed, pu                                         |
| Tp     | Time constant for electrical to mechanical power, seconds |
| Damp   | Machine damping coefficient, pu Power/pu speed            |

---

<a id="gas"></a>

## Gas

*Source: [`Content/TransientModels_HTML/GovernorFolder Gas.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder Gas.htm)*

_This topic has no body text in the source help file._

---

<a id="general"></a>

## General

*Source: [`Content/TransientModels_HTML/GovernorFolder General.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder General.htm)*

_This topic has no body text in the source help file._

---

<a id="hydro"></a>

## Hydro

*Source: [`Content/TransientModels_HTML/GovernorFolder Hydro.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder Hydro.htm)*

_This topic has no body text in the source help file._

---

<a id="playin"></a>

## PlayIn

*Source: [`Content/TransientModels_HTML/GovernorFolder PlayIn.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder PlayIn.htm)*

_This topic has no body text in the source help file._

---

<a id="steam"></a>

## Steam

*Source: [`Content/TransientModels_HTML/GovernorFolder Steam.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder Steam.htm)*

_This topic has no body text in the source help file._

---

<a id="wind-turbines"></a>

## Wind Turbines

*Source: [`Content/TransientModels_HTML/GovernorFolder Wind Turbines.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder Wind Turbines.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-governors"></a>

## BPA Governors

*Source: [`Content/TransientModels_HTML/BPA Governors.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BPA Governors.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-gg"></a>

## BPA_GG

*Source: [`Content/TransientModels_HTML/Governor BPA_GG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GG.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-gh"></a>

## BPA_GH

*Source: [`Content/TransientModels_HTML/Governor BPA_GH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GH.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-gigatb"></a>

## BPA_GIGATB

*Source: [`Content/TransientModels_HTML/Governor BPA_GIGATB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GIGATB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-gjgatb"></a>

## BPA_GJGATB

*Source: [`Content/TransientModels_HTML/Governor BPA_GJGATB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GJGATB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-gkgatb"></a>

## BPA_GKGATB

*Source: [`Content/TransientModels_HTML/Governor BPA_GKGATB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GKGATB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-gltb"></a>

## BPA_GLTB

*Source: [`Content/TransientModels_HTML/Governor BPA_GLTB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GLTB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.

---

<a id="bpa-gsta"></a>

## BPA_GSTA

*Source: [`Content/TransientModels_HTML/Governor BPA_GSTA.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GSTA.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-gstb"></a>

## BPA_GSTB

*Source: [`Content/TransientModels_HTML/Governor BPA_GSTB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GSTB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-gstc"></a>

## BPA_GSTC

*Source: [`Content/TransientModels_HTML/Governor BPA_GSTC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GSTC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-gwtw"></a>

## BPA_GWTW

*Source: [`Content/TransientModels_HTML/Governor BPA_GWTW.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BPA_GWTW.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen
