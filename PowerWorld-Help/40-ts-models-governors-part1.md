---
title: "TS Models — Governors (Part 1 of 4)"
part: "Transient Models"
chapter_file: "40-ts-models-governors-part1.md"
topics: 19
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Governors (Part 1 of 4)

Turbine-governor models (GGOV, IEEEG, GAST, HYGOV, WT*T, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (19)**

- [Governors (Mechanical Controls)](#governors-mechanical-controls)
- [All](#all)
- [BBGOV1](#bbgov1)
- [CCBT1](#ccbt1)
- [CRCMGV](#crcmgv)
- [DEGOV](#degov)
- [DEGOV1](#degov1)
- [G2WSCC](#g2wscc)
- [GAST_GE](#gast-ge)
- [GAST_PTI](#gast-pti)
- [GAST2A](#gast2a)
- [GAST2A_AIR](#gast2a-air)
- [GASTWD](#gastwd)
- [GASTWD_AIR](#gastwd-air)
- [GGOV1](#ggov1)
- [GGOV2](#ggov2)
- [GGOV3](#ggov3)
- [GPWSCC](#gpwscc)
- [H6B and H6BD](#h6b-and-h6bd)

---

<a id="governors-mechanical-controls"></a>

## Governors (Mechanical Controls)

*Source: [`Content/TransientModels_HTML/Governor.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/GovernorFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/GovernorFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="bbgov1"></a>

## BBGOV1

*Source: [`Content/TransientModels_HTML/Governor BBGOV1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor BBGOV1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - f\_cut must be greater than 0. If true, deadband will be ignored.
  - For Param T4, T5, T6 and T1 then If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0, ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - For Param Kls, Kp, Tn, Kd and Td then If 0 \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - If Pmax\< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If P \> Pmax, then Pmax = P limits or if P \< Pmin, then Pmin = P

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="ccbt1"></a>

## CCBT1

*Source: [`Content/TransientModels_HTML/Governor CCBT1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor CCBT1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tpelec \< 0.5\*Mult\*TimeStep then Tpelec = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpelec \< Mult\*TimeStep then Tpelec = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tw \< 0.5\*Mult\*TimeStep then Tw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If 0.0 \< Trh \< 0.5\*Mult\*TimeStep then Trh = 0, ElseIf 0.5\*Mult\*TimeStep \< Trh \< Mult\*TimeStep then Trh = Mult\*TimeStep
  - If Kd7 \<\> 0 the:
      - If 0.0 \< Td7 \< Mult\*TimeStep then Td7 = Mult\*TimeStep
  - Rmax1 and Rmin1 to Rmax6 and Rmin6:
      - If Rmax \< Rmin then swap the values.
  - Max1 and Min1 to Max7 and Min7:
      - If Max \< Min then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If PD7 \> Pmax , then Pmax = Gate or if Gate \< Pmin , then Pmin = Gate
  - If PI1 \> Max1, then Max1 = PI1 or if PI1 \< Min1, then Min1 = PI1
  - If PI2 \> Max2, then Max2 = PI2 or if PI2 \< Min2, then Min2 = PI2
  - If PI3 \> Max3, then Max3 = PI3 or if PI3 \< Min3, then Min3 = PI3
  - If PI4 \> Max4, then Max4 = PI4 or if PI4 \< Min4, then Min4 = PI4
  - If PI5 \> Max5, then Max5 = PI5 or if PI5 \< Min5, then Min5 = PI5
  - If PI6 \> Max6, then Max6 = PI6 or if PI6 \< Min6, then Min6 = PI6
  - If Valve \> Vmax, then Vmax = Valve or if Valve \< Vmin, then Vmin = Valve

Model Equations and/or Block Diagrams 

![Governor CCBT1 0001](images/Governor_CCBT1_0001.svg)

**Parameters:**

|        |                                                                                                    |
| ------ | -------------------------------------------------------------------------------------------------- |
| Trate  | Turbine rating, MW                                                                                 |
| data   | Type of data input 0=User Entries; 1=Boiler Follows Unit; 2=Coordinate Unit; 3=Turbine Follow Unit |
| rvalve | Governor Permanent droop, valve position feedback, p.u.                                            |
| rpelec | Governor Permanent droop, electrical power feedback, p.u.                                          |
| tpelec | Electrical Power Transducer time constant, sec.                                                    |
| tg     | Governor time constant, sec.                                                                       |
| kpgov  | Governor control proportional gain, p.u.                                                           |
| kigov  | Governor control integral gain, p.u.                                                               |
| vmax   | Maximum governor control output, p.u.                                                              |
| vmin   | Minimum governor control output, p.u.                                                              |
| ah     | Turbine high pressure power fraction                                                               |
| trh    | Reheater time constant, sec.                                                                       |
| ref    | Boiler or turbine controller reference                                                             |
| kp1    | Turbine/pressure controller proportional gain                                                      |
| ki1    | Turbine/pressure controller reset gain                                                             |
| max1   | Turbine/pressure controller maximum output, p.u.                                                   |
| min1   | Turbine/pressure controller minimum output, p.u.                                                   |
| rmax1  | Turbine/pressure controller rate limit, p.u.                                                       |
| rmin1  | Turbine/pressure controller rate limit, p.u.                                                       |
| kp2    | Boiler/pressure controller proportional gain                                                       |
| ki2    | Boiler/pressure controller reset gain                                                              |
| max2   | Boiler/pressure controller maximum output, p.u.                                                    |
| min2   | Boiler/pressure controller minimum output, p.u.                                                    |
| rmax2  | Boiler/pressure controller rate limit, p.u.                                                        |
| rmin2  | Boiler/pressure controller rate limit, p.u.                                                        |
| kp3    | Boiler/load controller proportional gain                                                           |
| ki3    | Boiler/load controller reset gain                                                                  |
| max3   | Boiler/load controller maximum output, p.u.                                                        |
| min3   | Boiler/load controller minimum output, p.u.                                                        |
| rmax3  | Boiler/load controller rate limit, pu                                                              |
| rmin3  | Boiler/load controller rate limit, pu                                                              |
| kp4    | Boiler/fuel controller proportional gain                                                           |
| ki4    | Boiler/fuel controller reset gain                                                                  |
| max4   | Boiler/fuel controller maximum output, p.u.                                                        |
| min4   | Boiler/fuel controller minimum output, p.u.                                                        |
| rmax4  | Boiler/fuel controller rate limit, p.u.                                                            |
| rmin4  | Boiler/fuel controller rate limit, p.u.                                                            |
| kp5    | Turbine/load controller proportional gain                                                          |
| ki5    | Turbine/load controller reset gain                                                                 |
| max5   | Turbine/load controller maximum output, p.u.                                                       |
| min5   | Turbine/load controller minimum output, p.u.                                                       |
| rmax5  | Turbine/load controller rate limit, p.u.                                                           |
| rmin5  | Turbine/load controller rate limit, p.u.                                                           |
| kp6    | Load/turbine controller proportional gain                                                          |
| ki6    | Load/turbine controller reset gain                                                                 |
| max6   | Load/turbine controller maximum output, p.u.                                                       |
| min6   | Load/turbine controller minimum output, p.u.                                                       |
| rmax6  | Load/turbine controller rate limit, p.u.                                                           |
| rmin6  | Load/turbine controller rate limit, p.u.                                                           |
| kp7    | Steam flow feedforward controller proportional gain                                                |
| kd7    | Steam flow feedforward controller reset gain                                                       |
| max7   | Steam flow feedforward controller maximum output, p.u.                                             |
| min7   | Steam flow feedforward controller minimum output, p.u.                                             |
| td7    | Steam flow feedforward controller rate limit, p.u.                                                 |
| kplm   | Low steam pressure limiter gain, p.u.                                                              |
| plmref | Low steam pressure limiter reference, p.u.                                                         |
| tf     | Fuel system time constant, sec.                                                                    |
| tw     | Boiler steam generation time constant, sec.                                                        |
| td     | Boiler drum time constant, sec.                                                                    |
| kp     | Superheater pressure drop factor, p.u./p.u.                                                        |
| kb     | Frequency error gain, p.u./p.u.                                                                    |
| dbd    | Frequency dead-band, p.u.                                                                          |
| flag   | Control input flag                                                                                 |
| dref   | Required change in MW load for load ramp, MW                                                       |
| t1     | Starting time for the load ramp, sec.                                                              |
| t2     | Finishing time for the load ramp, sec.                                                             |
| gv1    | Break point for governor valve characteristic, p.u.                                                |
| gvb1   | Break point for governor value characteristic, p.u./p.u.                                           |
| p0     | Pressure reference at zero load, p.u.                                                              |
| h1     | First break point for pressure reference characteristic, p.u.                                      |
| p1     | First break point for pressure reference characteristic, p.u.                                      |
| h2     | Second break point for pressure reference characteristic, p.u.                                     |
| p2     | Second break point for pressure reference characteristic, p.u                                      |

.

---

<a id="crcmgv"></a>

## CRCMGV

*Source: [`Content/TransientModels_HTML/Governor CRCMGV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor CRCMGV.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T1HP \< Mult\*TimeStep then T1HP = Mult\*TimeStep
  - If 0 \< T2HP \< Mult\*TimeStep then T2HP = Mult\*TimeStep
  - If 0 \< T3HP \< Mult\*TimeStep then T3HP = Mult\*TimeStep
  - If 0 \< T4HP \< Mult\*TimeStep then T4HP = Mult\*TimeStep
  - If 0 \< T5HP \< Mult\*TimeStep then T5HP = Mult\*TimeStep
  - If 0 \< T1LP \< Mult\*TimeStep then T1LP = Mult\*TimeStep
  - If 0 \< T2LP \< Mult\*TimeStep then T2LP = Mult\*TimeStep
  - If 0 \< T3LP \< Mult\*TimeStep then T3LP = Mult\*TimeStep
  - If 0 \< T4LP \< Mult\*TimeStep then T4LP = Mult\*TimeStep
  - If 0 \< T5LP \< Mult\*TimeStep then T5LP = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If PHP \> PmaxHP, then Pmax = PHP or if PHP \< Pref, then Pref = PHP
  - If PLP \> PmaxLP, then PmaxLP = PLP or if PLP \< PrefLP, then PrefLP = PLP

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="degov"></a>

## DEGOV

*Source: [`Content/TransientModels_HTML/Governor DEGOV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor DEGOV.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T3 \< 0.5\*Mult\*TimeStep then T3 = 0, ElseIf 0.5\*Mult\*TimeStep \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0, ElseIf 0.5\*Mult\*TimeStep \< T5 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< Td \< 0.25\*Mult\*TimeStep then Td = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Td \< 0.5\*Mult\*TimeStep then Td = 0.5\*Mult\*TimeStep
  - If Tmax \< Tmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If T5 = 0, then we also assume T4 = 0
  - If Pmech \> Tmax, then Tmax = Pmech or if Pmech \< Tmin, then Tmin = Pmech

Model Equations and/or Block Diagrams

![Governor DEGOV 0001](images/Governor_DEGOV_0001.svg)

**Parameters:**

|      |                                                |
| ---- | ---------------------------------------------- |
| T1   | Governor mechanism time constant, sec          |
| T2   | Turbine power time constant, sec               |
| T3   | Turbine exhaust temperature time constant, sec |
| K    | Governor gain (reciprocal of droop), pu        |
| T4   | Governor lead time constant, sec               |
| T5   | Governor lag time constant, sec                |
| T6   | Actuator time constant, sec                    |
| Td   | Engine time delay, sec                         |
| Tmax | Upper Limit, pu                                |
| Tmin | Lower Limit, pu                                |

---

<a id="degov1"></a>

## DEGOV1

*Source: [`Content/TransientModels_HTML/Governor DEGOV1 and DEGOV1D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor DEGOV1 and DEGOV1D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0, ElseIf 0.5\*Mult\*TimeStep \< T5 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< Te \< 0.5\*Mult\*TimeStep then Te = 0, ElseIf 0.5\*Mult\*TimeStep \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If Td \> 12\*TimeStep then Td = 12\*TimeStep AND If 0.0 \< Td \< 0.25\*Mult\*TimeStep then Td = 0, ElseIf 0.25\*Mult\*TimeStep \< Td \< 0.5\*Mult\*TimeStep then Td = 0.5\*Mult\*TimeStep
  - If Tmax \< Tmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If T5 = 0, then we also assume T4 = 0
  - If Pmech \> Tmax, then Tmax = Pmech or if Pmech \< Tmin, then Tmin = Pmech

Model Equations and/or Block Diagrams

![Governor DEGOV1 0001](images/Governor_DEGOV1_0001.svg)   

**Parameters for DEGOV1:**

|              |                                                                      |
| ------------ | -------------------------------------------------------------------- |
| DroopControl | Droop control flag (0: Throttle feedback; 1 Electric power feedback) |
| T1           | Governor mechanism time constant, sec                                |
| T2           | Turbine power time constant, sec                                     |
| T3           | Turbine exhaust temperature time constant, sec                       |
| K            | Governor gain (recirpocal of droop), pu                              |
| T4           | Governor lead time constant, sec                                     |
| T5           | Governor lag time constant, sec                                      |
| T6           | Actuator time constant, sec                                          |
| Td           | Engine time delay, sec                                               |
| Tmax         | Upper Limit, pu                                                      |
| Tmin         | Lower Limit, pu                                                      |
| Droop        | Steady state droop, pu                                               |
| Te           | Power transducer time constant, pu                                   |

**Parameters for DEGOV1D:**

|              |                                                                      |
| ------------ | -------------------------------------------------------------------- |
| DroopControl | Droop control flag (0: Throttle feedback; 1 Electric power feedback) |
| T1           | Governor mechanism time constant, sec                                |
| T2           | Turbine power time constant, sec                                     |
| T3           | Turbine exhaust temperature time constant, sec                       |
| K            | Governor gain (recirpocal of droop), pu                              |
| T4           | Governor lead time constant, sec                                     |
| T5           | Governor lag time constant, sec                                      |
| T6           | T, sec                                                               |
| Td           | Engine time delay, sec                                               |
| Tmax         | Upper Limit, pu                                                      |
| Tmin         | Lower Limit, pu                                                      |
| Droop        | Steady state droop, pu                                               |
| Te           | Power transducer time constant, pu                                   |
| dbH          | Deadband High (pu)                                                   |
| dbL          | Deadband Low (pu)                                                    |
| Trate        | Turbine rating, MW                                                   |

---

<a id="g2wscc"></a>

## G2WSCC

*Source: [`Content/TransientModels_HTML/Governor G2WSCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor G2WSCC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tturb \*Bturb \< Mult\*TimeStep then Tturb = 0
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tt \< 0.25\*Mult\*TimeStep then Tt = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tf \< 0.25\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tp \< 0.25\*Mult\*TimeStep then Tp = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0.5\*Mult\*TimeStep
  - If Velopen \< Velclose then swap the values. If Velopen \< 0 then Velopen change sign to positive. If Velclose \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Pmax , then Pmax = GV or if GV \< Pmin , then Pmin = GV

Model Equations and/or Block Diagrams

![Governor G2WSCC 0001](images/Governor_G2WSCC_0001.svg)   

**Parameters:**

|          |                                                    |
| -------- | -------------------------------------------------- |
| MWCap    | Turbine Rating, MW                                 |
| Pmax     | Maximum gate opening, pu of mwcap                  |
| Pmin     | Minimum gate opening, pu of mwcap                  |
| R        | Governor control flag                              |
| Td       | Input filter time constant, sec                    |
| Tf       | Washout time constant, sec                         |
| Tp       | Gate servo time constant, sec                      |
| Velopen  | Maximum gate opening velocity, pu/sec              |
| Velclose | Maximum gate closing velocity, pu/sec              |
| K1       | Fraction of hp shaft power after first boiler pass |
| K2       | Fraction of lp shaft power after first boiler pass |
| Ki       | Integral gain, pu                                  |
| Kg       | Gate servo gain, pu                                |
| Tturb    | Turbine time constant, sec                         |
| Aturb    | Turbine numerator multiplier                       |
| Bturb    | Turbine denominator multiplier                     |
| Tt       | Power feedback time constant, sec                  |
| db1      | Intentional deadband width, Hz                     |
| Eps      | Unintentional db hysteresis, Hz                    |
| db2      | Unintentional deadband, MW                         |
| Gv1      | Nonlinear gain point 1, pu gv                      |
| Pgv1     | Nonlinear gain point 1, pu power                   |
| Gv2      | Nonlinear gain point 2, pu gv                      |
| Pgv2     | Nonlinear gain point 2, pu power                   |
| Gv3      | Nonlinear gain point 3, pu gv                      |
| Pgv3     | Nonlinear gain point 3, pu power                   |
| Gv4      | Nonlinear gain point 4, pu gv                      |
| Pgv4     | Nonlinear gain point 4, pu power                   |
| Gv5      | Nonlinear gain point 5, pu gv                      |
| Pgv5     | Nonlinear gain point 5, pu power                   |
| Gv6      | Nonlinear gain point 6, pu gv                      |
| Pgv6     | Nonlinear gain point 6, pu power                   |

---

<a id="gast-ge"></a>

## GAST_GE

*Source: [`Content/TransientModels_HTML/Governor GAST_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GAST_GE.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Governor GAST GE 0001](images/Governor_GAST_GE_0001.svg)

**Parameters:**

|       |                                                      |
| ----- | ---------------------------------------------------- |
| MWCap | Turbine Rating, MW                                   |
| R     | Permanent droop, pu                                  |
| T1    | Governor mechanism time constant, sec                |
| T2    | Turbine power time constant, sec                     |
| T3    | Turbine exhaust temperature time constant, sec       |
| Lmax  | Model Parameters\\Lmax                               |
| Kt    | Temperature limiter gain                             |
| Vmax  | Maximum turbine power, pu of mwcap                   |
| Vmin  | Minimum turbine power, pu of mwcap                   |
| Dturb | Turbine damping coefficient, pu                      |
| Fidle | Fuel flow at zero power output, pu                   |
| Rmax  | Maximum fuel valve opening rate, pu/sec              |
| Linc  | Valve position change allowed at fast rate, pu       |
| Tltr  | Valve position averaging time constant, sec          |
| Ltrat | Maximum long term fuel valve opening rate, pu/sec    |
| A     | Turbine power time constant numerator scale factor   |
| B     | Turbine power time constant denominator scale factor |
| db1pu | Intentional deadband width, pu                       |
| Err   | Intentional db hysteresis, pu                        |
| db2pu | Unintentional deadband, pu                           |
| Gv1   | Nonlinear gain point 1, pu gv                        |
| Pgv1  | Nonlinear gain point 1, pu power                     |
| Gv2   | Nonlinear gain point 2, pu gv                        |
| Pgv2  | Nonlinear gain point 2, pu power                     |
| Gv3   | Nonlinear gain point 3, pu gv                        |
| Pgv3  | Nonlinear gain point 3, pu power                     |
| Gv4   | Nonlinear gain point 4, pu gv                        |
| Pgv4  | Nonlinear gain point 4, pu power                     |
| Gv5   | Nonlinear gain point 5, pu gv                        |
| Pgv5  | Nonlinear gain point 5, pu power                     |
| Gv6   | Nonlinear gain point 6, pu gv                        |
| Pgv6  | Nonlinear gain point 6, pu power                     |
| Ka    | Governor gain                                        |
| T4    | Governor lead time constant, sec                     |
| T5    | Governor lag time constant, sec                      |

---

<a id="gast-pti"></a>

## GAST_PTI

*Source: [`Content/TransientModels_HTML/Governor GAST_PTI and GASTD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GAST_PTI and GASTD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T3 \< 0.5\*Mult\*TimeStep then T3 = 0, ElseIf 0.5\*Mult\*TimeStep \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pref \> At, then Pref = At
  - If Pmech \> Vmax, then Vmax = Pmech or if Pmech \< Vmin, then Vmin = Pmech

Model Equations and/or Block Diagrams

![Governor GAST PTI 0001](images/Governor_GAST_PTI_0001.svg)  

**Parameters for GAST\_PTI:**

|       |                                    |
| ----- | ---------------------------------- |
| R     | Permanent droop, pu                |
| T1    | Time in sec                        |
| T2    | Time in sec                        |
| T3    | Time in sec                        |
| At    | Ambient temperature load limit     |
| Kt    | Temperature limiter gain           |
| Vmax  | Maximum turbine power, pu of mwcap |
| Vmin  | Minimum turbine power, pu of mwcap |
| Dturb | Turbine damping coefficient, pu    |

**Parameters for GASTD:**

|       |                                    |
| ----- | ---------------------------------- |
| R     | Permanent droop, pu                |
| T1    | Time in sec                        |
| T2    | Time in sec                        |
| T3    | Time in sec                        |
| At    | Ambient temperature load limit     |
| Kt    | Temperature limiter gain           |
| Vmax  | Maximum turbine power, pu of mwcap |
| Vmin  | Minimum turbine power, pu of mwcap |
| Dturb | Turbine damping coefficient, pu    |
| dbH   | Deadband High (pu)                 |
| dbL   | Deadband Low (pu)                  |
| Trate | Turbine rating, MW                 |

---

<a id="gast2a"></a>

## GAST2A

*Source: [`Content/TransientModels_HTML/Governor GAST2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GAST2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Y \< Mult\*TimeStep then Y = Mult\*TimeStep
  - If 0.0 \< A \< Mult\*TimeStep then A = Mult\*TimeStep
  - If 0.0 \< B \< Mult\*TimeStep then B = Mult\*TimeStep
  - If 0.0 \< TauF \< Mult\*TimeStep then TauF = Mult\*TimeStep
  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - If 0 \< Bf2 \< Mult\*TimeStep then Bf2 = Mult\*TimeStep
  - If 0.0 \< K3 \< Mult\*TimeStep then K3 = Mult\*TimeStep
  - If 0.0 \< TauT \< Mult\*TimeStep then TauT = Mult\*TimeStep
  - If 0.0 \< Tcd \< 0.5\*Mult\*TimeStep then Tcd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tcd \< Mult\*TimeStep then Tcd = Mult\*TimeStep
  - If 0.0 \< Etd \< 0.5\*Mult\*TimeStep then Etd = 0, ElseIf 0.5\*Mult\*TimeStep \< Etd \< Mult\*TimeStep then Etd = Mult\*TimeStep
  - If MaxLimit \< MinLimit then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \> Max, then Max = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 or if ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \< Min, then Min = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3

Model Equations and/or Block Diagrams

![Governor GAST2A 0001](images/Governor_GAST2A_0001.svg)

**Parameters for GAST2A:**

|          |                                          |
| -------- | ---------------------------------------- |
| W        | W - governor gain (1/droop)              |
| X        | Governor lead time constant, sec         |
| Y        | Governor lag time constant, sec          |
| Z        | Governor mode: 0=ISO, 1=Droop            |
| Etd      | Etd, sec                                 |
| Tcd      | Tcd, sec                                 |
| Trate    | Turbine rating, MW                       |
| T        | Time in sec                              |
| MaxLimit | Max limit on turbine rating              |
| MinLimit | Min limit on turbine rating              |
| Ecr      | Ecr, sec                                 |
| K3       | Gain                                     |
| A        | Valve positioner                         |
| B        | Valve positioner                         |
| C        | Valve positioner                         |
| TauF     | Time in sec                              |
| Kf       | Feedback Gain                            |
| K5       | Gain                                     |
| K4       | Gain                                     |
| T3       | Time in sec                              |
| T4       | Time in sec                              |
| TauT     | Time in sec                              |
| T5       | Time in sec                              |
| Af1      | Af1: coefficient of the Turbine f1 block |
| Bf1      | Bf1: coefficient of the Turbine f1 block |
| Af2      | Af2: coefficient of the Turbine f2 block |
| Bf2      | Bf2: coefficient of the Turbine f2 block |
| Cf2      | Cf2: coefficient of the Turbine f2 block |
| Tr       | Rated temperature                        |
| K6       | Minimum fuel flow, pu                    |
| Tc       | Temperature control                      |

**Parameters for GAST2AD**:

|          |                                          |
| -------- | ---------------------------------------- |
| W        | W - governor gain (1/droop)              |
| X        | Governor lead time constant, sec         |
| Y        | Governor lag time constant, sec          |
| Z        | Governor mode: 0=ISO, 1=Droop            |
| Etd      | Etd, sec                                 |
| Tcd      | Tcd, sec                                 |
| Trate    | Turbine rating, MW                       |
| T        | Time in sec                              |
| MaxLimit | Max limit on turbine rating              |
| MinLimit | Min limit on turbine rating              |
| Ecr      | Ecr, sec                                 |
| K3       | Gain                                     |
| A        | Valve positioner                         |
| B        | Valve positioner                         |
| C        | Valve positioner                         |
| TauF     | Time in sec                              |
| Kf       | Feedback Gain                            |
| K5       | Gain                                     |
| K4       | Gain                                     |
| T3       | Time in sec                              |
| T4       | Time in sec                              |
| TauT     | Time in sec                              |
| T5       | Time in sec                              |
| Af1      | Af1: coefficient of the Turbine f1 block |
| Bf1      | Bf1: coefficient of the Turbine f1 block |
| Af2      | Af2: coefficient of the Turbine f2 block |
| Bf2      | Bf2: coefficient of the Turbine f2 block |
| Cf2      | Cf2: coefficient of the Turbine f2 block |
| Tr       | Rated temperature                        |
| K6       | Minimum fuel flow, pu                    |
| Tc       | Temperature control                      |
| dbH      | Deadband High (pu)                       |
| dbL      | Deadband Low (pu)                        |

---

<a id="gast2a-air"></a>

## GAST2A_AIR

*Source: [`Content/TransientModels_HTML/Governor GAST2A_AIR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GAST2A_AIR.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Y \< Mult\*TimeStep then Y = Mult\*TimeStep
  - If 0.0 \< A \< Mult\*TimeStep then A = Mult\*TimeStep
  - If 0.0 \< B \< Mult\*TimeStep then B = Mult\*TimeStep
  - If 0.0 \< TauF \< Mult\*TimeStep then TauF = Mult\*TimeStep
  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - If 0 \< Bf2 \< Mult\*TimeStep then Bf2 = Mult\*TimeStep
  - If 0.0 \< K3 \< Mult\*TimeStep then K3 = Mult\*TimeStep
  - If 0.0 \< TauT \< Mult\*TimeStep then TauT = Mult\*TimeStep
  - If 0.0 \< Tcd \< 0.5\*Mult\*TimeStep then Tcd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tcd \< Mult\*TimeStep then Tcd = Mult\*TimeStep
  - If 0.0 \< Etd \< 0.5\*Mult\*TimeStep then Etd = 0, ElseIf 0.5\*Mult\*TimeStep \< Etd \< Mult\*TimeStep then Etd = Mult\*TimeStep
  - If MaxLimit \< MinLimit then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \> Max, then Max = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 or if ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \< Min, then Min = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3

Model Equations and/or Block Diagrams

![Governor GAST2A AIR 0001](images/Governor_GAST2A_AIR_0001.svg)   

**Parameters:**

|            |                                          |
| ---------- | ---------------------------------------- |
| W          | W - governor gain (1/droop)              |
| X          | Governor lead time constant, sec         |
| Y          | Governor lag time constant, sec          |
| Z          | Governor mode: 0=ISO, 1=Droop            |
| Etd        | Etd, sec                                 |
| Tcd        | Tcd, sec                                 |
| Trate      | Turbine rating, MW                       |
| T          | Time in sec                              |
| MaxLimit   | Max limit on turbine rating              |
| MinLimit   | Min limit on turbine rating              |
| Ecr        | Ecr, sec                                 |
| K3         | Gain                                     |
| A          | Valve positioner                         |
| B          | Valve positioner                         |
| C          | Valve positioner                         |
| TauF       | Time in sec                              |
| Kf         | Feedback Gain                            |
| K5         | Gain                                     |
| K4         | Gain                                     |
| T3         | Time in sec                              |
| T4         | Time in sec                              |
| TauT       | Time in sec                              |
| T5         | Time in sec                              |
| Af1        | Af1: coefficient of the Turbine f1 block |
| Bf1        | Bf1: coefficient of the Turbine f1 block |
| Af2        | Af2: coefficient of the Turbine f2 block |
| Bf2        | Bf2: coefficient of the Turbine f2 block |
| Cf2        | Cf2: coefficient of the Turbine f2 block |
| Tr         | Rated temperature                        |
| K6         | Minimum fuel flow, pu                    |
| Tc         | Temperature control                      |
| Cf1        | Cf1: coefficient of the Turbine f1 block |
| AirTemp    | Ambient Air Temperature                  |
| AirTempNom | Nominal Ambient Air Temperature          |

---

<a id="gastwd"></a>

## GASTWD

*Source: [`Content/TransientModels_HTML/Governor GASTWD and GASTWDD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GASTWD and GASTWDD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< A \< Mult\*TimeStep then A = Mult\*TimeStep
  - If 0.0 \< B \< Mult\*TimeStep then B = Mult\*TimeStep
  - If 0.0 \< TauF \< Mult\*TimeStep then TauF = Mult\*TimeStep
  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - If 0 \< Bf2 \< Mult\*TimeStep then Bf2 = Mult\*TimeStep
  - If 0.0 \< TauT \< Mult\*TimeStep then TauT = Mult\*TimeStep
  - If 0.0 \< Tcd \< 0.5\*Mult\*TimeStep then Tcd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tcd \< Mult\*TimeStep then Tcd = Mult\*TimeStep
  - If 0.0 \< Ecr \< 0.5\*Mult\*TimeStep then Ecr = 0, ElseIf 0.5\*Mult\*TimeStep \< Ecr \< Mult\*TimeStep then Ecr = Mult\*TimeStep
  - If MaxLimit \< MinLimit then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \> Max, then Max = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 or if ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \< Min, then Min = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3

Model Equations and/or Block Diagrams

![Governor GASTWD 0001](images/Governor_GASTWD_0001.svg)   

**Parameters for GASTWD:**

|          |                                          |
| -------- | ---------------------------------------- |
| Kdroop   | Gain in turbine rating                   |
| Kp       | Proportional gain, pu                    |
| Ki       | Integral gain, pu                        |
| Kd       | Derivative gain, pu                      |
| Etd      | Etd, sec                                 |
| Tcd      | Tcd, sec                                 |
| Trate    | Turbine rating, MW                       |
| T        | Time in sec                              |
| MaxLimit | Max limit on turbine rating              |
| MinLimit | Min limit on turbine rating              |
| Ecr      | Ecr, sec                                 |
| K3       | Gain                                     |
| A        | Valve positioner                         |
| B        | Valve positioner                         |
| C        | Valve positioner                         |
| TauF     | Time in sec                              |
| Kf       | Feedback Gain                            |
| K5       | Gain                                     |
| K4       | Gain                                     |
| T3       | Time in sec                              |
| T4       | Time in sec                              |
| TauT     | Time in sec                              |
| T5       | Time in sec                              |
| Af1      | Af1: coefficient of the Turbine f1 block |
| Bf1      | Bf1: coefficient of the Turbine f1 block |
| Af2      | Af2: coefficient of the Turbine f2 block |
| Bf2      | Bf2: coefficient of the Turbine f2 block |
| Cf2      | Cf2: coefficient of the Turbine f2 block |
| Tr       | Rated temperature                        |
| K6       | Minimum fuel flow, pu                    |
| Tc       | Temperature control                      |
| Td       | Power transducer, sec                    |

**Parameters for GASTWDD:**

|          |                                          |
| -------- | ---------------------------------------- |
| Kdroop   | Gain in turbine rating                   |
| Kp       | Proportional gain, pu                    |
| Ki       | Integral gain, pu                        |
| Kd       | Derivative gain, pu                      |
| Etd      | Etd, sec                                 |
| Tcd      | Tcd, sec                                 |
| Trate    | Turbine rating, MW                       |
| T        | Time in sec                              |
| MaxLimit | Max limit on turbine rating              |
| MinLimit | Min limit on turbine rating              |
| Ecr      | Ecr, sec                                 |
| K3       | Gain                                     |
| A        | Valve positioner                         |
| B        | Valve positioner                         |
| C        | Valve positioner                         |
| TauF     | Time in sec                              |
| Kf       | Feedback Gain                            |
| K5       | Gain                                     |
| K4       | Gain                                     |
| T3       | Time in sec                              |
| T4       | Time in sec                              |
| TauT     | Time in sec                              |
| T5       | Time in sec                              |
| Af1      | Af1: coefficient of the Turbine f1 block |
| Bf1      | Bf1: coefficient of the Turbine f1 block |
| Af2      | Af2: coefficient of the Turbine f2 block |
| Bf2      | Bf2: coefficient of the Turbine f2 block |
| Cf2      | Cf2: coefficient of the Turbine f2 block |
| Tr       | Rated temperature                        |
| K6       | Minimum fuel flow, pu                    |
| Tc       | Temperature control                      |
| Td       | Power transducer, sec                    |
| dbH      | Deadband High (pu)                       |
| dbL      | Deadband Low (pu)                        |

---

<a id="gastwd-air"></a>

## GASTWD_AIR

*Source: [`Content/TransientModels_HTML/Governor GASTWD_AIR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GASTWD_AIR.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< A \< Mult\*TimeStep then A = Mult\*TimeStep
  - If 0.0 \< B \< Mult\*TimeStep then B = Mult\*TimeStep
  - If 0.0 \< TauF \< Mult\*TimeStep then TauF = Mult\*TimeStep
  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - If 0 \< Bf2 \< Mult\*TimeStep then Bf2 = Mult\*TimeStep
  - If 0.0 \< TauT \< Mult\*TimeStep then TauT = Mult\*TimeStep
  - If 0.0 \< Tcd \< 0.5\*Mult\*TimeStep then Tcd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tcd \< Mult\*TimeStep then Tcd = Mult\*TimeStep
  - If 0.0 \< Ecr \< 0.5\*Mult\*TimeStep then Ecr = 0, ElseIf 0.5\*Mult\*TimeStep \< Ecr \< Mult\*TimeStep then Ecr = Mult\*TimeStep
  - If MaxLimit \< MinLimit then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \> Max, then Max = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 or if ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3 \< Min, then Min = ((C/A + Kf)\*((Pmech - AF2)/Bf2)- K6)/K3

Model Equations and/or Block Diagrams

![Governor GASTWD AIR 0001](images/Governor_GASTWD_AIR_0001.svg)

**Parameters:**

|            |                                          |
| ---------- | ---------------------------------------- |
| Kdroop     | Gain in turbine rating                   |
| Kp         | Proportional gain, pu                    |
| Ki         | Integral gain, pu                        |
| Kd         | Derivative gain, pu                      |
| Etd        | Etd, sec                                 |
| Tcd        | Tcd, sec                                 |
| Trate      | Turbine rating, MW                       |
| T          | Time in sec                              |
| MaxLimit   | Max limit on turbine rating              |
| MinLimit   | Min limit on turbine rating              |
| Ecr        | Ecr, sec                                 |
| K3         | Gain                                     |
| A          | Valve positioner                         |
| B          | Valve positioner                         |
| C          | Valve positioner                         |
| TauF       | Time in sec                              |
| Kf         | Feedback Gain                            |
| K5         | Gain                                     |
| K4         | Gain                                     |
| T3         | Time in sec                              |
| T4         | Time in sec                              |
| TauT       | Time in sec                              |
| T5         | Time in sec                              |
| Af1        | Af1: coefficient of the Turbine f1 block |
| Bf1        | Bf1: coefficient of the Turbine f1 block |
| Af2        | Af2: coefficient of the Turbine f2 block |
| Bf2        | Bf2: coefficient of the Turbine f2 block |
| Cf2        | Cf2: coefficient of the Turbine f2 block |
| Tr         | Rated temperature                        |
| K6         | Minimum fuel flow, pu                    |
| Tc         | Temperature control                      |
| Td         | Power transducer, sec                    |
| Cf1        | Cf1: coefficient of the Turbine f1 block |
| AirTemp    | Ambient Air Temperature                  |
| AirTempNom | Nominal Ambient Air Temperature          |

---

<a id="ggov1"></a>

## GGOV1

*Source: [`Content/TransientModels_HTML/Governor GGOV1 and GGOV1D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GGOV1 and GGOV1D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Kturb\< Mult\*TimeStep then Kturb= Mult\*TimeStep
  - If 0.0 \< TPelec \< 0.5\*Mult\*TimeStep then TPelec = 0, ElseIf 0.5\*Mult\*TimeStep \< TPelec \< Mult\*TimeStep then TPelec = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tsb \< 0.5\*Mult\*TimeStep then Tsb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tsb \< Mult\*TimeStep then Tsb = Mult\*TimeStep
  - If 0.0 \< Tfload \< 0.5\*Mult\*TimeStep then Tfload = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfload \< Mult\*TimeStep then Tfload = Mult\*TimeStep
  - If Maxerr \< Minerr then swap the values. If Maxerr \< 0 then Maxerr change sign to positive. If Minerr \> 0 then change sign to negative.
  - If Vmax \< Vmin then swap the values. If Vmax \> 1 then Vmax = 1. If Vmin \< 0 then Vmin = 0.
  - If ROpen \> 0.1 then ROpen = 0.1
  - If RClose \> -0.1 then RClose = -0.1
  - If Rup \> 99 then Rup = 99
  - If Rdown \> -99 then Rdown = -99
  - If Kpgov/Kigov \< Mult\*TimeStep then Kpgov = 0

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Low Value Select \> Vmax, then Vmax = Low Value Select or if Low Value Select \< Vmin, then Vmin = Low Value Select
  - If Err \> Maxerr, then Maxerr = Err or if Err \< Minerr, then Minerr = Err

Model Equations and/or Block Diagrams

![Governor GGOV1 0001](images/Governor_GGOV1_0001.svg)

**Parameters for GGOV1:**

|         |                                                  |
| ------- | ------------------------------------------------ |
| Trate   | Turbine rating, MW                               |
| Rselect | Feedback signal for droop                        |
| Flag    | Switch for fuel source characteristic            |
| R       | Permanent droop, pu                              |
| Tpelec  | Electrical power transducer time constant, sec   |
| Maxerr  | Maximum value for speed error signal             |
| Minerr  | Minimum value for speed error signal             |
| Kpgov   | Governor proportional gain                       |
| Kigov   | Governor integral gain                           |
| Kdgov   | Governor derivative gain                         |
| Tdgov   | Governor derivative controller time constant     |
| Vmax    | Maximum valve position limit                     |
| Vmin    | Minimum valve position limit                     |
| Tact    | Actuator time constant                           |
| Kturb   | Turbine gain                                     |
| Wfnl    | No load fuel flow, pu                            |
| Tb      | Turbine lag time constant                        |
| Tc      | Turbine lead time constant                       |
| Teng    | Transport lag time constant for diesel engine    |
| Tfload  | Load limiter time constant                       |
| Kpload  | Load limiter proportional gain for PI controller |
| Kiload  | Load limiter integral gain for PI controller     |
| Ldref   | Load limiter reference value, pu                 |
| Dm      | Speed sensistivity coefficient, pu               |
| Ropen   | Largest (\>0) valve opening rate, pu/sec         |
| Rclose  | Largest (\<0) valve closing rate, pu/sec         |
| Kimw    | Power controller (reset) gain                    |
| Aset    | Acceleration limiter setpoint, pu/sec            |
| Ka      | Acceleration limiter gain                        |
| Ta      | Acceleration limiter time constant, sec          |
| Db      | Speed governor dead band, pu                     |
| Tsa     | Temperature detection lead time constant, sec    |
| Tsb     | Temperature detection lag time constant, sec     |
| Rup     | Maximum rate of load limit increase              |
| Rdown   | Maximum rate of load limit decrease              |

**Parameters for GGOV1D:**

|         |                                                  |
| ------- | ------------------------------------------------ |
| Trate   | Turbine rating, MW                               |
| Rselect | Feedback signal for droop                        |
| Flag    | Switch for fuel source characteristic            |
| R       | Permanent droop, pu                              |
| Tpelec  | Electrical power transducer time constant, sec   |
| Maxerr  | Maximum value for speed error signal             |
| Minerr  | Minimum value for speed error signal             |
| Kpgov   | Governor proportional gain                       |
| Kigov   | Governor integral gain                           |
| Kdgov   | Governor derivative gain                         |
| Tdgov   | Governor derivative controller time constant     |
| Vmax    | Maximum valve position limit                     |
| Vmin    | Minimum valve position limit                     |
| Tact    | Actuator time constant                           |
| Kturb   | Turbine gain                                     |
| Wfnl    | No load fuel flow, pu                            |
| Tb      | Turbine lag time constant                        |
| Tc      | Turbine lead time constant                       |
| Teng    | Transport lag time constant for diesel engine    |
| Tfload  | Load limiter time constant                       |
| Kpload  | Load limiter proportional gain for PI controller |
| Kiload  | Load limiter integral gain for PI controller     |
| Ldref   | Load limiter reference value, pu                 |
| Dm      | Speed sensistivity coefficient, pu               |
| Ropen   | Largest (\>0) valve opening rate, pu/sec         |
| Rclose  | Largest (\<0) valve closing rate, pu/sec         |
| Kimw    | Power controller (reset) gain                    |
| Aset    | Acceleration limiter setpoint, pu/sec            |
| Ka      | Acceleration limiter gain                        |
| Ta      | Acceleration limiter time constant, sec          |
| Db      | Speed governor dead band, pu                     |
| Tsa     | Temperature detection lead time constant, sec    |
| Tsb     | Temperature detection lag time constant, sec     |
| Rup     | Maximum rate of load limit increase              |
| Rdown   | Maximum rate of load limit decrease              |
| DbH     | Deadband High (pu)                               |
| DbL     | Deadband Low (pu)                                |

---

<a id="ggov2"></a>

## GGOV2

*Source: [`Content/TransientModels_HTML/Governor GGOV2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GGOV2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Kturb\< Mult\*TimeStep then Kturb= Mult\*TimeStep
  - If 0.0 \< TPelec \< 0.5\*Mult\*TimeStep then TPelec = 0, ElseIf 0.5\*Mult\*TimeStep \< TPelec \< Mult\*TimeStep then TPelec = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tsb \< 0.5\*Mult\*TimeStep then Tsb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tsb \< Mult\*TimeStep then Tsb = Mult\*TimeStep
  - If 0.0 \< Tfload \< 0.5\*Mult\*TimeStep then Tfload = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfload \< Mult\*TimeStep then Tfload = Mult\*TimeStep
  - If Maxerr \< Minerr then swap the values. If Maxerr \< 0 then Maxerr change sign to positive. If Minerr \> 0 then change sign to negative.
  - If Vmax \< Vmin then swap the values. If Vmax \> 1 then Vmax = 1. If Vmin \< 0 then Vmin = 0.
  - If ROpen \> 0.1 then ROpen = 0.1
  - If RClose \> -0.1 then RClose = -0.1
  - If Rup \> 99 then Rup = 99
  - If Rdown \> -99 then Rdown = -99
  - If Kpgov/Kigov \< Mult\*TimeStep then Kpgov = 0

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Low Value Select \> Vmax, then Vmax = Low Value Select or if Low Value Select \< Vmin, then Vmin = Low Value Select
  - If Err \> Maxerr, then Maxerr = Err or if Err \< Minerr, then Minerr = Err

Model Equations and/or Block Diagram

![Governor GGOV2 0001](images/Governor_GGOV2_0001.svg)

**Parameters:**

|         |                                                           |
| ------- | --------------------------------------------------------- |
| Trate   | Turbine rating, MW                                        |
| Rselect | Feedback signal for droop                                 |
| Flag    | Switch for fuel source characteristic                     |
| R       | Permanent droop, pu                                       |
| Tpelec  | Electrical power transducer time constant, sec            |
| Maxerr  | Maximum value for speed error signal                      |
| Minerr  | Minimum value for speed error signal                      |
| Kpgov   | Governor proportional gain                                |
| Kigov   | Governor integral gain                                    |
| Kdgov   | Governor derivative gain                                  |
| Tdgov   | Governor derivative controller time constant              |
| Vmax    | Maximum valve position limit                              |
| Vmin    | Minimum valve position limit                              |
| Tact    | Actuator time constant                                    |
| Kturb   | Turbine gain                                              |
| Wfnl    | No load fuel flow, pu                                     |
| Tb      | Turbine lag time constant                                 |
| Tc      | Turbine lead time constant                                |
| Teng    | Transport lag time constant for diesel engine             |
| Tfload  | Load limiter time constant                                |
| Kpload  | Load limiter propoertional gain for PI controller         |
| Kiload  | Load limiter integral gain for PI controller              |
| Ldref   | Load limiter reference value, pu                          |
| Dm      | Speed sensistivity coefficient, pu                        |
| Ropen   | Largest (\>0) valve opening rate, pu/sec                  |
| Rclose  | Largest (\<0) valve closing rate, pu/sec                  |
| Kimw    | Power controller (reset) gain                             |
| Aset    | Acceleration limiter setpoint, pu/sec                     |
| Ka      | Acceleration limiter gain                                 |
| Ta      | Acceleration limiter time constant, sec                   |
| Db      | Speed governor dead band, pu                              |
| Tsa     | Temperature detection lead time constant, sec             |
| Tsb     | Temperature detection lag time constant, sec              |
| Rup     | Maximum rate of load limit increase                       |
| Rdown   | Maximum rate of load limit decrease                       |
| Prate   | Ramp rate for frequency-dependent power limit, p.u. P/sec |
| Flim1   | Frequency Threshold 1, Hz                                 |
| Plim1   | Power limit 1, pu                                         |
| Flim2   | Frequency Threshold 2, Hz                                 |
| Plim2   | Power limit 2, pu                                         |
| Flim3   | Frequency Threshold 3, Hz                                 |
| Plim3   | Power limit 3, pu                                         |
| Flim4   | Frequency Threshold 4, Hz                                 |
| Plim4   | Power limit 4, pu                                         |
| Flim5   | Frequency Threshold 5, Hz                                 |
| Plim5   | Power limit 5, pu                                         |
| Flim6   | Frequency Threshold 6, Hz                                 |
| Plim6   | Power limit 6, pu                                         |
| Flim7   | Frequency Threshold 7, Hz                                 |
| Plim7   | Power limit 7, pu                                         |
| Flim8   | Frequency Threshold 8, Hz                                 |
| Plim8   | Power limit 8, pu                                         |
| Flim9   | Frequency Threshold 9, Hz                                 |
| Plim9   | Power limit 9, pu                                         |
| Flim10  | Frequency Threshold 10, Hz                                |
| Plim10  | Power limit 10, pu                                        |

---

<a id="ggov3"></a>

## GGOV3

*Source: [`Content/TransientModels_HTML/Governor GGOV3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GGOV3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Kturb\< Mult\*TimeStep then Kturb= Mult\*TimeStep
  - If 0.0 \< TPelec \< 0.5\*Mult\*TimeStep then TPelec = 0, ElseIf 0.5\*Mult\*TimeStep \< TPelec \< Mult\*TimeStep then TPelec = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tsb \< 0.5\*Mult\*TimeStep then Tsb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tsb \< Mult\*TimeStep then Tsb = Mult\*TimeStep
  - If 0.0 \< Tfload \< 0.5\*Mult\*TimeStep then Tfload = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfload \< Mult\*TimeStep then Tfload = Mult\*TimeStep
  - If Maxerr \< Minerr then swap the values. If Maxerr \< 0 then Maxerr change sign to positive. If Minerr \> 0 then change sign to negative.
  - If Vmax \< Vmin then swap the values. If Vmax \> 1 then Vmax = 1. If Vmin \< 0 then Vmin = 0.
  - If ROpen \> 0.1 then ROpen = 0.1
  - If RClose \> -0.1 then RClose = -0.1
  - If Rup \> 99 then Rup = 99
  - If Rdown \> -99 then Rdown = -99
  - If Kpgov/Kigov \< Mult\*TimeStep then Kpgov = 0

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Low Value Select \> Vmax, then Vmax = Low Value Select or if Low Value Select \< Vmin, then Vmin = Low Value Select
  - If Err \> Maxerr, then Maxerr = Err or if Err \< Minerr, then Minerr = Err

Model Equations and/or Block Diagrams   

![Governor GGOV3 0001](images/Governor_GGOV3_0001.svg)

**Parameters:**

|         |                                                   |
| ------- | ------------------------------------------------- |
| Trate   | Turbine rating, MW                                |
| Rselect | Feedback signal for droop                         |
| Flag    | Switch for fuel source characteristic             |
| R       | Permanent droop, pu                               |
| Tpelec  | Electrical power transducer time constant, sec    |
| Maxerr  | Maximum value for speed error signal              |
| Minerr  | Minimum value for speed error signal              |
| Kpgov   | Governor proportional gain                        |
| Kigov   | Governor integral gain                            |
| Kdgov   | Governor derivative gain                          |
| Tdgov   | Governor derivative controller time constant      |
| Vmax    | Maximum valve position limit                      |
| Vmin    | Minimum valve position limit                      |
| Tact    | Actuator time constant                            |
| Kturb   | Turbine gain                                      |
| Wfnl    | No load fuel flow, pu                             |
| Tb      | Turbine lag time constant                         |
| Tc      | Turbine lead time constant                        |
| Teng    | Transport lag time constant for diesel engine     |
| Tfload  | Load limiter time constant                        |
| Kpload  | Load limiter propoertional gain for PI controller |
| Kiload  | Load limiter integral gain for PI controller      |
| Ldref   | Load limiter reference value, pu                  |
| Dm      | Speed sensistivity coefficient, pu                |
| Ropen   | Largest (\>0) valve opening rate, pu/sec          |
| Rclose  | Largest (\<0) valve closing rate, pu/sec          |
| Kimw    | Power controller (reset) gain                     |
| Aset    | Acceleration limiter setpoint, pu/sec             |
| Ka      | Acceleration limiter gain                         |
| Ta      | Acceleration limiter time constant, sec           |
| Db      | Speed governor dead band, pu                      |
| Tsa     | Temperature detection lead time constant, sec     |
| Tsb     | Temperature detection lag time constant, sec      |
| Rup     | Maximum rate of load limit increase               |
| Rdown   | Maximum rate of load limit decrease               |
| Tbd     | Model Parameters\\Tbd                             |
| Tcd     | Tcd, sec                                          |
| ffa     | Model Parameters\\ffa                             |
| ffb     | Model Parameters\\ffb                             |
| ffc     | Model Parameters\\ffc                             |
| dnrate  | Model Parameters\\dnrate                          |
| dnhi    | Model Parameters\\dnhi                            |
| dnlo    | Model Parameters\\dnlo                            |
| t1      | Perceived speed deviation input breakpoint, sec   |
| t2      | Perceived speed deviation input breakpoint, sec   |
| t3      | Perceived speed deviation input breakpoint, sec   |
| t4      | Perceived speed deviation input breakpoint, sec   |
| t5      | Perceived speed deviation input breakpoint, sec   |
| n1      | Perceived speed deviation at breakpoint time, pu  |
| n2      | Perceived speed deviation at breakpoint time, pu  |
| n3      | Perceived speed deviation at breakpoint time, pu  |
| n4      | Perceived speed deviation at breakpoint time, pu  |
| n5      | Perceived speed deviation at breakpoint time, pu  |

---

<a id="gpwscc"></a>

## GPWSCC

*Source: [`Content/TransientModels_HTML/Governor GPWSCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor GPWSCC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Bturb \< Mult\*TimeStep then Bturb = 0
  - If 0.0 \< Tturb \< Mult\*TimeStep then Tturb = 0
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0, ElseIf 0.5\*Mult\*TimeStep \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If Velopen \< Velclose then swap the values. If Velopen \< 0 then Velopen change sign to positive. If Velclose \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Pmax , then Pmax = GV or if GV \< Pmin , then Pmin = GV

Model Equations and/or Block Diagrams

![Governor GPWSCC 0001](images/Governor_GPWSCC_0001.svg)   

**Parameters:**

|          |                                       |
| -------- | ------------------------------------- |
| MWCap    | Turbine Rating, MW                    |
| Pmax     | Maximum gate opening, pu of mwcap     |
| Pmin     | Minimum gate opening, pu of mwcap     |
| R        | Governor control flag                 |
| Td       | Input filter time constant, sec       |
| Tf       | Washout time constant, sec            |
| Tp       | Gate servo time constant, sec         |
| Velopen  | Maximum gate opening velocity, pu/sec |
| Velclose | Maximum gate closing velocity, pu/sec |
| Kp       | Proportional gain, pu                 |
| Kd       | Derivative gain, pu                   |
| Ki       | Integral gain, pu                     |
| Kg       | Gate servo gain, pu                   |
| Tturb    | Turbine time constant, sec            |
| Aturb    | Turbine numerator multiplier          |
| Bturb    | Turbine denominator multiplier        |
| Tt       | Power feedback time constant, sec     |
| db1      | Intentional deadband width, Hz        |
| Eps      | Unintentional db hysteresis, Hz       |
| db2      | Unintentional deadband, MW            |
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
| Gv6      | Nonlinear gain point 6, pu gv         |
| Pgv6     | Nonlinear gain point 6, pu power      |

---

<a id="h6b-and-h6bd"></a>

## H6B and H6BD

*Source: [`Content/TransientModels_HTML/Governor H6B and H6BD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor H6B and H6BD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Trate: Verify that associated H6BD family model not found. This must be fixed.
  - If Ki = 0 then Ki = Mult\*TimeStep
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tpe \< 0.5\*Mult\*TimeStep then Tpe = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpe \< Mult\*TimeStep then Tpe = Mult\*TimeStep
  - If 0.0 \< Tg \< 0.5\*Mult\*TimeStep then Tg = 0, ElseIf 0.5\*Mult\*TimeStep \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tbf \< 0.5\*Mult\*TimeStep then Tbf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tbf \< Mult\*TimeStep then Tbf = Mult\*TimeStep
  - If 0.0 \< Tbs \< 0.5\*Mult\*TimeStep then Tbs = 0, ElseIf 0.5\*Mult\*TimeStep \< Tbs \< Mult\*TimeStep then Tbs = Mult\*TimeStep
  - If 0.0 \< Tsp \< 0.5\*Mult\*TimeStep then Tsp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tsp \< Mult\*TimeStep then Tsp = Mult\*TimeStep
  - If 0.0 \< Tff \< 0.5\*Mult\*TimeStep then Tff = 0, ElseIf 0.5\*Mult\*TimeStep \< Tff \< Mult\*TimeStep then Tff = Mult\*TimeStep
  - If 0.0 \< Tpw \< 0.5\*Mult\*TimeStep then Tpw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpw \< Mult\*TimeStep then Tpw = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Gmax, then Gmax = Gate or if Gate \< Gmin, then Gmin = Gate

Model Equations and/or Block Diagrams   View in fullscreen
