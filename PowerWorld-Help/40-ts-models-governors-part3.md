---
title: "TS Models — Governors (Part 3 of 4)"
part: "Transient Models"
chapter_file: "40-ts-models-governors-part3.md"
topics: 25
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Governors (Part 3 of 4)

Turbine-governor models (GGOV, IEEEG, GAST, HYGOV, WT*T, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (25)**

- [HYGOVRU](#hygovru)
- [HYPID](#hypid)
- [HYST1](#hyst1)
- [IEEEG1](#ieeeg1)
- [IEEEG1PID](#ieeeg1pid)
- [IEEEG2](#ieeeg2)
- [IEEEG3_GE](#ieeeg3-ge)
- [IEEEG3_PTI](#ieeeg3-pti)
- [IEESGO](#ieesgo)
- [ISOGOV1](#isogov1)
- [PIDGOV](#pidgov)
- [PLAYINGOV](#playingov)
- [SHAF25](#shaf25)
- [TGOV1](#tgov1)
- [TGOV2](#tgov2)
- [TGOV3](#tgov3)
- [TGOV5](#tgov5)
- [TURCZT](#turczt)
- [URGS3T](#urgs3t)
- [UCBGT](#ucbgt)
- [UCCPSS](#uccpss)
- [UHRSG](#uhrsg)
- [W2301](#w2301)
- [WEHGOV](#wehgov)
- [WESGOV](#wesgov)

---

<a id="hygovru"></a>

## HYGOVRU

*Source: [`Content/TransientModels_HTML/Governor HYGOVRU.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYGOVRU.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If At \<= 0 then At = Mult\*TimeStep
  - If 0.0 \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0, ElseIf 0.5\*Mult\*TimeStep \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Gmax , then Gmax = GV or if GV \< Gmin , then Gmin = GV

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="hypid"></a>

## HYPID

*Source: [`Content/TransientModels_HTML/Governor HYPID.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYPID.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Gmax , then Gmax = Gate or if Gate \< Gmin , then Gmin = Gate

Model Equations and/or Block Diagrams

   ![Governor HYPID 0001](images/Governor_HYPID_0001.svg)

**Parameters:**

|        |                                                     |
| ------ | --------------------------------------------------- |
| MWCap  | Turbine Rating, MW                                  |
| Relec  | Steady-state droop, pu, for electric power feedback |
| Tpelec | Electrical power transducer time constant, sec      |
| Kp     | Proportional gain, pu                               |
| Ki     | Integral gain, pu                                   |
| Kd     | Derivative gain, pu                                 |
| Td     | Input filter time constant, sec                     |
| Tg     | Gate servo time constant, sec                       |
| Velm   | Maximum gate velocity, pu/sec                       |
| Gmax   | Maximum gate velocity, pu of mwcap                  |
| Gmin   | Minimum gate velocity, pu of mwcap                  |
| Tw     | Water inertia time constant, sec                    |
| At     | Turbine gain, pu                                    |
| Dturb  | Turbine damping coefficient, pu                     |
| Qnl    | No-load flow at nominal head, pu                    |
| Gsp    | Speed input gain                                    |
| db1    | Intentional deadband width, Hz                      |
| Eps    | Intentional db hysteresis, Hz                       |
| db2    | Unintentional deadband, MW                          |
| Gv0    | Nonlinear gain point 0, pu gv                       |
| Pgv0   | Nonlinear gain point 0, pu power                    |
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
| Hdam   | Head available at dam, pu                           |
| Bgv0   | Kaplan blade servo point 0, pu                      |
| Bgv1   | Kaplan blade servo point 1, pu                      |
| Bgv2   | Kaplan blade servo point 2, pu                      |
| Bgv3   | Kaplan blade servo point 3, pu                      |
| Bgv4   | Kaplan blade servo point 4, pu                      |
| Bgv5   | Kaplan blade servo point 5, pu                      |
| Bmax   | Maximum blade adjustment factor                     |
| Tblade | Blade servo time constant, sec                      |

---

<a id="hyst1"></a>

## HYST1

*Source: [`Content/TransientModels_HTML/Governor HYST1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYST1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Velmax \< Velminthen swap the values. If Velmax \< 0 then Velmax change sign to positive. If Velmin\> 0 then change sign to negative.
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Gmax , then Gmax = Gate or if Gate \< Gmin , then Gmin = Gate

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="ieeeg1"></a>

## IEEEG1

*Source: [`Content/TransientModels_HTML/Governor IEEEG1, IEEEG1D and IEEEG1_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEEEG1, IEEEG1D and IEEEG1_GE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0, ElseIf 0.5\*Mult\*TimeStep \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0.0 \< T7 \< 0.5\*Mult\*TimeStep then T7 = 0, ElseIf 0.5\*Mult\*TimeStep \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.
  - K1 to K8: Check K1+K3+K5+K7 and K2+K4+K6+K8 \<= 1.0 and if not normalized values to 1.0.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor IEEEG1 and IEEEG1 GE 0001](images/Governor_IEEEG1_and_IEEEG1_GE_0001.svg)

**Parameters for IEEEG1:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| K     | Governor gain (recirpocal of droop), pu             |
| T1    | Governor lag time constant, sec                     |
| T2    | governor lead time constant, sec                    |
| T3    | Valve positioner time constant, sec                 |
| Uo    | Maximum valve opening velocity, pu/sec              |
| Uc    | Maximum valve closing velocity, pu/sec              |
| Pmax  | Maximum valve opening, pu of mwcap                  |
| Pmin  | Minimum valve opening, pu of mwcap                  |
| T4    | High pressure turbine bowl time constant, sec       |
| K1    | Fraction of hp shaft power after first boiler pass  |
| K2    | Fraction of lp shaft power after first boiler pass  |
| T5    | Reheater time constant, sec                         |
| K3    | Fraction of hp shaft power after second boiler pass |
| K4    | Fraction of lp shaft power after second boiler pass |
| T6    | Crossover time constant, sec                        |
| K5    | Fraction of hp shaft power after third boiler pass  |
| K6    | Fraction of lp shaft power after third boiler pass  |
| T7    | Double reheat time constant, sec                    |
| K7    | Fraction of hp shaft power after fourth boiler pass |
| K8    | Fraction of lp shaft power after fourth boiler pass |
| db1   | Intentional deadband width, Hz                      |
| Eps   | Intentional db hysteresis, Hz                       |
| db2   | Unintentional deadband, MW                          |
| Gv1   | Nonlinear gain point 1, pu gv                       |
| Pgv1  | Nonlinear gain point 1, pu power                    |
| Gv2   | Nonlinear gain point 2, pu gv                       |
| Pgv2  | Nonlinear gain point 2, pu power                    |
| Gv3   | Nonlinear gain point 3, pu gv                       |
| Pgv3  | Nonlinear gain point 3, pu power                    |
| Gv4   | Nonlinear gain point 4, pu gv                       |
| Pgv4  | Nonlinear gain point 4, pu power                    |
| Gv5   | Nonlinear gain point 5, pu gv                       |
| Pgv5  | Nonlinear gain point 5, pu power                    |
| Gv6   | Nonlinear gain point 6, pu gv                       |
| Pgv6  | Nonlinear gain point 6, pu power                    |
| Trate | Turbine rating, MW                                  |

**Parameters for IEEEG1D:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| K     | Governor gain (recirpocal of droop), pu             |
| T1    | Governor lag time constant, sec                     |
| T2    | governor lead time constant, sec                    |
| T3    | Valve positioner time constant, sec                 |
| Uo    | Maximum valve opening velocity, pu/sec              |
| Uc    | Maximum valve closing velocity, pu/sec              |
| Pmax  | Maximum valve opening, pu of mwcap                  |
| Pmin  | Minimum valve opening, pu of mwcap                  |
| T4    | High pressure turbine bowl time constant, sec       |
| K1    | Fraction of hp shaft power after first boiler pass  |
| K2    | Fraction of lp shaft power after first boiler pass  |
| T5    | Reheater time constant, sec                         |
| K3    | Fraction of hp shaft power after second boiler pass |
| K4    | Fraction of lp shaft power after second boiler pass |
| T6    | Crossover time constant, sec                        |
| K5    | Fraction of hp shaft power after third boiler pass  |
| K6    | Fraction of lp shaft power after third boiler pass  |
| T7    | Double reheat time constant, sec                    |
| K7    | Fraction of hp shaft power after fourth boiler pass |
| K8    | Fraction of lp shaft power after fourth boiler pass |
| dbH   | Deadband High (pu)                                  |
| dbL   | Deadband Low (pu)                                   |
| Trate | Turbine rating, MW                                  |

**Parameters for IEEEG1\_GE:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| Trate | Turbine rating, MW                                  |
| K     | Governor gain (recirpocal of droop), pu             |
| T1    | Governor lag time constant, sec                     |
| T2    | governor lead time constant, sec                    |
| T3    | Valve positioner time constant, sec                 |
| Uo    | Maximum valve opening velocity, pu/sec              |
| Uc    | Maximum valve closing velocity, pu/sec              |
| Pmax  | Maximum valve opening, pu of mwcap                  |
| Pmin  | Minimum valve opening, pu of mwcap                  |
| T4    | High pressure turbine bowl time constant, sec       |
| K1    | Fraction of hp shaft power after first boiler pass  |
| K2    | Fraction of lp shaft power after first boiler pass  |
| T5    | Reheater time constant, sec                         |
| K3    | Fraction of hp shaft power after second boiler pass |
| K4    | Fraction of lp shaft power after second boiler pass |
| T6    | Crossover time constant, sec                        |
| K5    | Fraction of hp shaft power after third boiler pass  |
| K6    | Fraction of lp shaft power after third boiler pass  |
| T7    | Double reheat time constant, sec                    |
| K7    | Fraction of hp shaft power after fourth boiler pass |
| K8    | Fraction of lp shaft power after fourth boiler pass |
| db1   | Intentional deadband width, Hz                      |
| Eps   | Intentional db hysteresis, Hz                       |
| db2   | Unintentional deadband, MW                          |
| Gv1   | Nonlinear gain point 1, pu gv                       |
| Pgv1  | Nonlinear gain point 1, pu power                    |
| Gv2   | Nonlinear gain point 2, pu gv                       |
| Pgv2  | Nonlinear gain point 2, pu power                    |
| Gv3   | Nonlinear gain point 3, pu gv                       |
| Pgv3  | Nonlinear gain point 3, pu power                    |
| Gv4   | Nonlinear gain point 4, pu gv                       |
| Pgv4  | Nonlinear gain point 4, pu power                    |
| Gv5   | Nonlinear gain point 5, pu gv                       |
| Pgv5  | Nonlinear gain point 5, pu power                    |
| Gv6   | Nonlinear gain point 6, pu gv                       |
| Pgv6  | Nonlinear gain point 6, pu power                    |

---

<a id="ieeeg1pid"></a>

## IEEEG1PID

*Source: [`Content/TransientModels_HTML/Governor IEEEG1PID.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEEEG1PID.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tcv \< Mult\*TimeStep then T3 = Mult\*TimeStep.
  - If 0.0 \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep.
  - For Tdc, Tb, Trh, Tco, and Trhd, if value is less than 0.5\*Mult\*TimeStep it is set to 0.0.  
    If Value is between 0.5\*Mult\*TimeStep and Mult\*TimStep it is set to Mult\*TimeStep
  - If Droop \> 0.0001, then Droop set to 0.0001 (can't set this to zero)
  - abs(K1 + K3 + K5 + K7) \> 0.000001 or this is treated as a validation error
  - If a second generator is references, abs(K2 + K4 + K6 + K8) \> 0.000001 or this is treated as a validation error
  - Pthrot \> 0.0001 or this is treated as a validation error
  - Values should be entered with Pmax \>= Pmin. If Pmax \< Pmin then swap the values.
  - Values should be entered with Uo \> 0 and Uc \< 0.  
    If (Uo \> 0) AND (Uc \> 0), then set Uc = -Uc  
    If (Uo \< 0) AND (Uc \< 0), then set Uo = -Uo  
    If (Uo \< 0) AND (Uc \> 0), the values of Uc and Uo are swapped

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor IEEEG1PID 0001](images/Governor_IEEEG1PID_0001.svg)

**Parameters:**

|         |                                                                                    |
| ------- | ---------------------------------------------------------------------------------- |
| Droop   | Droop: Droop setting, pu                                                           |
| Tdc     | Tdc: Droop Delay, seconds                                                          |
| Kp      | Kp: Proportional gain, pu                                                          |
| Ki      | Ki: Integral gain, pu                                                              |
| Kd      | Kd: Derivative gain, pu                                                            |
| Td      | Td: Derivative delay, seconds                                                      |
| Tcv     | Tcv: Valve positioner time constant, sec                                           |
| Uo      | Uo: Maximum valve opening velocity, pu/sec                                         |
| Uc      | Uc: Maximum valve closing velocity, pu/sec                                         |
| Pmax    | Pmax: Maximum valve opening, pu                                                    |
| Pmin    | Pmin: Minimum valve opening, pu                                                    |
| Pthrot  | Pthrot: Power Throttle, pu                                                         |
| Tb      | Tb: High pressure turbine bowl time constant, sec                                  |
| K1      | K1: Fraction of hp shaft power after first boiler pass                             |
| K2      | K2: Fraction of lp shaft power after first boiler pass                             |
| Trh     | Trh: Reheater time constant, sec                                                   |
| K3      | K3: Fraction of hp shaft power after reheater                                      |
| K4      | K4: Fraction of lp shaft power after reheater                                      |
| Tco     | Tco: Crossover time constant, sec                                                  |
| K5      | K5: Fraction of hp shaft power after crossover                                     |
| K6      | K6: Fraction of lp shaft power after crossover                                     |
| Trhd    | Trhd: Double reheat time constant, sec                                             |
| K7      | K7: Fraction of hp shaft power after double reheater                               |
| K8      | K8: Fraction of lp shaft power after double reheater                               |
| Plosshp | Plosshp: Power Loss on hp turbine, per unit on hp gen MVABase                      |
| Plosslp | Plosslp: Power Loss on lp turbine, per unit on lp gen MVABase                      |
| Dlim    | Dlim: Dlim, pu                                                                     |
| dbH     | dbH: Deadband High (pu)                                                            |
| dbL     | dbL: Deadband Low (pu)                                                             |
| Trate   | Trate: Model Rating, MW. (If 0, then treated as summation of hp and lp gen MVABase |

---

<a id="ieeeg2"></a>

## IEEEG2

*Source: [`Content/TransientModels_HTML/Governor IEEEG2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEEEG2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor IEEEG2 0001](images/Governor_IEEEG2_0001.svg)   

**Parameters:**

|      |                                                |
| ---- | ---------------------------------------------- |
| K    | Governor gain (recirpocal of droop), pu        |
| T1   | Governor mechanism time constant, sec          |
| T2   | Turbine power time constant, sec               |
| T3   | Turbine exhaust temperature time constant, sec |
| Pmax | Maximum gate opening, pu of mwcap              |
| Pmin | Minimum gate opening, pu of mwcap              |
| T4   | Governor lead time constant, sec               |

---

<a id="ieeeg3-ge"></a>

## IEEEG3_GE

*Source: [`Content/TransientModels_HTML/Governor IEEEG3_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEEEG3_GE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.25\*Mult\*TimeStep then Tp = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If 0.0 \< Kturb\< Mult\*TimeStep then Kturb= Mult\*TimeStep
  - If 0.0 \< Bturb\< Mult\*TimeStep then Bturb= Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor IEEEG3 GE 0001](images/Governor_IEEEG3_GE_0001.svg)

**Parameters:**

|       |                                        |
| ----- | -------------------------------------- |
| Trate | Turbine rating, MW                     |
| Tg    | Gate servo time constant, sec          |
| Tp    | Pilot servo valve time constant, sec   |
| Uo    | Maximum valve opening velocity, pu/sec |
| Uc    | Maximum valve closing velocity, pu/sec |
| Pmax  | Maximum gate opening, pu of mwcap      |
| Pmin  | Minimum gate opening, pu of mwcap      |
| Rperm | Permanent droop, pu                    |
| Rtemp | Temporary droop, pu                    |
| Tr    | Dashpot time constant, sec             |
| Tw    | Water inertia time constant, sec       |
| Kturb | Turbine gain                           |
| Aturb | Turbine numerator multiplier           |
| Bturb | Turbine denominator multiplier         |
| Spare | Unused parameter                       |
| db1   | Intentional deadband width, Hz         |
| Eps   | Intentional db hysteresis, Hz          |
| db2   | Unintentional deadband, MW             |
| Gv1   | Nonlinear gain point 1, pu gv          |
| Pgv1  | Nonlinear gain point 1, pu power       |
| Gv2   | Nonlinear gain point 2, pu gv          |
| Pgv2  | Nonlinear gain point 2, pu power       |
| Gv3   | Nonlinear gain point 3, pu gv          |
| Pgv3  | Nonlinear gain point 3, pu power       |
| Gv4   | Nonlinear gain point 4, pu gv          |
| Pgv4  | Nonlinear gain point 4, pu power       |
| Gv5   | Nonlinear gain point 5, pu gv          |
| Pgv5  | Nonlinear gain point 5, pu power       |
| Gv6   | Nonlinear gain point 6, pu gv          |
| Pgv6  | Nonlinear gain point 6, pu power       |

---

<a id="ieeeg3-pti"></a>

## IEEEG3_PTI

*Source: [`Content/TransientModels_HTML/Governor IEEEG3_PTI and IEEEG3D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEEEG3_PTI and IEEEG3D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.25\*Mult\*TimeStep then Tp = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - From A11 to A23:
      - If 0.0 \< A \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor IEEEG3 PTI 0001](images/Governor_IEEEG3_PTI_0001.svg)

**Parameters for IEEEG3\_PTI:**

|       |                                        |
| ----- | -------------------------------------- |
| Tg    | Gate servo time constant, sec          |
| Tp    | Pilot servo valve time constant, sec   |
| Uo    | Maximum valve opening velocity, pu/sec |
| Uc    | Maximum valve closing velocity, pu/sec |
| Pmax  | Maximum gate opening, pu of mwcap      |
| Pmin  | Minimum gate opening, pu of mwcap      |
| Rperm | Permanent droop, pu                    |
| Rtemp | Temporary droop, pu                    |
| Tr    | Dashpot time constant, sec             |
| Tw    | Water inertia time constant, sec       |
| A11   | Equation variable A11                  |
| A13   | Equation variable A13                  |
| A21   | Equation variable A21                  |
| A23   | Equation variable A23                  |

**Parameters for IEEEG3D:**

|       |                                        |
| ----- | -------------------------------------- |
| Tg    | Gate servo time constant, sec          |
| Tp    | Pilot servo valve time constant, sec   |
| Uo    | Maximum valve opening velocity, pu/sec |
| Uc    | Maximum valve closing velocity, pu/sec |
| Pmax  | Maximum gate opening, pu of mwcap      |
| Pmin  | Minimum gate opening, pu of mwcap      |
| Rperm | Permanent droop, pu                    |
| Rtemp | Temporary droop, pu                    |
| Tr    | Dashpot time constant, sec             |
| Tw    | Water inertia time constant, sec       |
| A11   | Equation variable A11                  |
| A13   | Equation variable A13                  |
| A21   | Equation variable A21                  |
| A23   | Equation variable A23                  |
| dbH   | Deadband High (pu)                     |
| dbL   | Deadband Low (pu)                      |
| Trate | Turbine rating, MW                     |

---

<a id="ieesgo"></a>

## IEESGO

*Source: [`Content/TransientModels_HTML/Governor IEESGO and IEESGOD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor IEESGO and IEESGOD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0, ElseIf 0.5\*Mult\*TimeStep \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

![Governor IEESGO 0001](images/Governor_IEESGO_0001.svg)

**Parameters for IEESGO:**

|      |                                                                                    |
| ---- | ---------------------------------------------------------------------------------- |
| T1   | Controller lag time constant, sec                                                  |
| T2   | Controller lead time compensation, sec                                             |
| T3   | Governor lag time constant, sec                                                    |
| T4   | Delay due to steam inlet volumes associated with steam chest and inlet piping, sec |
| T5   | Reheater delay including hot and cold leads, sec                                   |
| T6   | Delay due to IP-LP turbine, crossover pipes, and LP end hoods, sec                 |
| K1   | 1/pu unit regulation                                                               |
| K2   | Fraction                                                                           |
| K3   | Fraction                                                                           |
| Pmax | Upper power limit (pu)                                                             |
| Pmin | Lower power unit (pu)                                                              |

**Parameters for IEESGOD:**

|       |                                                                                    |
| ----- | ---------------------------------------------------------------------------------- |
| T1    | Controller lag time constant, sec                                                  |
| T2    | Controller lead time compensation, sec                                             |
| T3    | Governor lag time constant, sec                                                    |
| T4    | Delay due to steam inlet volumes associated with steam chest and inlet piping, sec |
| T5    | Reheater delay including hot and cold leads, sec                                   |
| T6    | Delay due to IP-LP turbine, crossover pipes, and LP end hoods, sec                 |
| K1    | 1/pu unit regulation                                                               |
| K2    | Fraction                                                                           |
| K3    | Fraction                                                                           |
| Pmax  | Upper power limit (pu)                                                             |
| Pmin  | Lower power unit (pu)                                                              |
| dbH   | Deadband High (pu)                                                                 |
| dbL   | Deadband Low (pu)                                                                  |
| Trate | Turbine rating, MW                                                                 |

---

<a id="isogov1"></a>

## ISOGOV1

*Source: [`Content/TransientModels_HTML/Governor ISOGOV1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor ISOGOV1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T3 \< 0.5\*Mult\*TimeStep then T3 = 0, ElseIf 0.5\*Mult\*TimeStep \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Vmax , then Vmax = Valveor if Valve \< Vmin , then Vmin = Valve

Model Equations and/or Block Diagrams

![Governor ISOGOV1 0001](images/Governor_ISOGOV1_0001.svg)

**Parameters:**

|       |                                              |
| ----- | -------------------------------------------- |
| R     | Permanent droop, pu                          |
| Ki    | Integrator gain                              |
| T1    | Steam bowl time constant, sec                |
| Vmax  | Maximum valve position limit, pu of Trate    |
| Vmin  | Minimum valve position limit, pu of Trate    |
| T2    | Numerator time constant of T2, T3 block, sec |
| T3    | Reheater time constant, sec                  |
| Dt    | Turbine damping coefficient, pu              |
| Trate | Turbine rating, MW                           |

---

<a id="pidgov"></a>

## PIDGOV

*Source: [`Content/TransientModels_HTML/Governor PIDGOV and PIDGOVD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor PIDGOV and PIDGOVD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Velmax \< Velmin then swap the values. If Velmax \< 0 then Velmax change sign to positive. If Velmin\> 0 then change sign to negative.
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Gmax , then Gmax = Gate or if Gate \< Gmin , then Gmin = Gate

Model Equations and/or Block Diagrams

   ![Governor PIDGOV 0001](images/Governor_PIDGOV_0001.svg)

**Parameters for PIDGOV:**

|          |                                                             |
| -------- | ----------------------------------------------------------- |
| Trate    | Turbine rating, MW                                          |
| Feedback | Feedback signal: 0=electric power feedback, 1=gate position |
| Rperm    | Permanent droop, pu                                         |
| Treg     | Input time constant of governor, sec                        |
| Kp       | Proportional gain, pu                                       |
| Ki       | Integral gain, pu                                           |
| Kd       | Derivative gain, pu                                         |
| Ta       | Governor high frequency cutoff time constant                |
| Tb       | Gate servo time constant                                    |
| Dturb    | Turbine damping coefficient, pu                             |
| G0       | Gate opening at speed no load, pu                           |
| G1       | Intermediate gate opening                                   |
| P1       | Power at gate opening G1, pu                                |
| G2       | Intermediate gate opening                                   |
| P2       | Power at gate opening G2, pu                                |
| P3       | Power at full opened gate, pu                               |
| Gmax     | Maximum gate velocity, pu of mwcap                          |
| Gmin     | Minimum gate velocity, pu of mwcap                          |
| Atw      | Model Parameters\\Atw                                       |
| Tw       | Water inertia time constant, sec                            |
| Velmax   | Max gate opening velocity, pu/sec                           |
| Velmin   | Min gate opening velocity, pu/sec                           |

**Parameters for PIDGOVD:**

|          |                                                             |
| -------- | ----------------------------------------------------------- |
| Feedback | Feedback signal: 0=electric power feedback, 1=gate position |
| Rperm    | Permanent droop, pu                                         |
| Treg     | Input time constant of governor, sec                        |
| Kp       | Proportional gain, pu                                       |
| Ki       | Integral gain, pu                                           |
| Kd       | Derivative gain, pu                                         |
| Ta       | Governor high frequency cutoff time constant                |
| Tb       | Gate servo time constant                                    |
| Dturb    | Turbine damping coefficient, pu                             |
| G0       | Gate opening at speed no load, pu                           |
| G1       | Intermediate gate opening                                   |
| P1       | Power at gate opening G1, pu                                |
| G2       | Intermediate gate opening                                   |
| P2       | Power at gate opening G2, pu                                |
| P3       | Power at full opened gate, pu                               |
| Gmax     | Maximum gate velocity, pu of mwcap                          |
| Gmin     | Minimum gate velocity, pu of mwcap                          |
| Atw      | Model Parameters\\Atw                                       |
| Tw       | Water inertia time constant, sec                            |
| Velmax   | Max gate opening velocity, pu/sec                           |
| Velmin   | Min gate opening velocity, pu/sec                           |
| dbH      | Deadband High (pu)                                          |
| dbL      | Deadband Low (pu)                                           |
| Trate    | Turbine rating, MW                                          |

---

<a id="playingov"></a>

## PLAYINGOV

*Source: [`Content/TransientModels_HTML/Governor PLAYINGOV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor PLAYINGOV.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="shaf25"></a>

## SHAF25

*Source: [`Content/TransientModels_HTML/Governor SHAF25.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor SHAF25.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="tgov1"></a>

## TGOV1

*Source: [`Content/TransientModels_HTML/Governor TGOV1 and TGOV1D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor TGOV1 and TGOV1D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< 0.25\*Mult\*TimeStep then T1 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0.5\*Mult\*TimeStep
  - If 0.0 \< T3 \< 0.25\*Mult\*TimeStep then \< = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T3 \< 0.5\*Mult\*TimeStep then T3 = 0.5\*Mult\*TimeStep
  - If Vmax \< Vmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Vmax , then Vmax = Valve or if Valve \< Vmin , then Vmin = Valve

Model Equations and/or Block Diagrams

   ![Governor TGOV1 0001](images/Governor_TGOV1_0001.svg)

**Parameters for TGOV1:**

|       |                                              |
| ----- | -------------------------------------------- |
| Trate | Turbine rating, MW                           |
| R     | Permanent droop, pu                          |
| T1    | Steam bowl time constant, sec                |
| Vmax  | Maximum valve position limit                 |
| Vmin  | Minimum valve position limit                 |
| T2    | Numerator time constant of T2, T3 block, sec |
| T3    | Reheater time constant, sec                  |
| Dt    | Turbine damping coefficient, pu              |

**Parameters for TGOV1D:**

|       |                                              |
| ----- | -------------------------------------------- |
| R     | Permanent droop, pu                          |
| T1    | Steam bowl time constant, sec                |
| Vmax  | Maximum valve position limit                 |
| Vmin  | Minimum valve position limit                 |
| T2    | Numerator time constant of T2, T3 block, sec |
| T3    | Reheater time constant, sec                  |
| Dt    | Turbine damping coefficient, pu              |
| dbH   | Deadband High (pu)                           |
| dbL   | Deadband Low (pu)                            |
| Trate | Turbine rating, MW                           |

---

<a id="tgov2"></a>

## TGOV2

*Source: [`Content/TransientModels_HTML/Governor TGOV2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor TGOV2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T1 \< 0.25\*Mult\*TimeStep then T1 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0.5\*Mult\*TimeStep
  - If 0.0 \< T3 \< 0.25\*Mult\*TimeStep then \< = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T3 \< 0.5\*Mult\*TimeStep then T3 \< = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If R \<= 0 then R = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Vmax , then Vmax = Valve or if Valve \< Vmin , then Vmin = Valve

Model Equations and/or Block Diagrams

   ![Governor TGOV2 0001](images/Governor_TGOV2_0001.svg)

**Parameters:**

|      |                                                  |
| ---- | ------------------------------------------------ |
| R    | Permanent droop, pu                              |
| T1   | Governor mechanism time constant, sec            |
| Vmax | Maximum turbine power, pu of mwcap               |
| Vmin | Minimum turbine power, pu of mwcap               |
| K    | Governor gain (recirpocal of droop), pu          |
| T3   | Turbine exhaust temperature time constant, sec   |
| Dt   | Turbine damping coefficient, pu                  |
| Tt   | Time constant Intercept Valve, sec               |
| Ta   | Time to close Intercept Valve (IV), sec          |
| Tb   | Time until Intercept Valve starts to reopen, sec |
| Tc   | Time until Intercept Valve is fully open, sec    |

---

<a id="tgov3"></a>

## TGOV3

*Source: [`Content/TransientModels_HTML/Governor TGOV3 and TGOV3D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor TGOV3 and TGOV3D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T5 \< 0.25\*Mult\*TimeStep then T5 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0.5\*Mult\*TimeStep
  - If 0.0 \< T3 \< 0.25\*Mult\*TimeStep then \< = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< T3 \< 0.5\*Mult\*TimeStep then T3 \< = 0.5\*Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams

   ![Governor TGOV3 0001](images/Governor_TGOV3_0001.svg)

**Parameters for TGOV3:**

|       |                                                           |
| ----- | --------------------------------------------------------- |
| Trate | Turbine rating, MW                                        |
| K     | Governor gain (recirpocal of droop), pu                   |
| T1    | Governor lead time constant, sec                          |
| T2    | Governor lag time constant, sec                           |
| T3    | Valve positioner time constant, sec                       |
| Uo    | Maximum valve opening velocity, pu/sec                    |
| Uc    | Maximum valve closing velocity, pu/sec                    |
| Pmax  | Maximum valve opening, pu of mwcap                        |
| Pmin  | Minimum valve opening, pu of mwcap                        |
| T4    | Inlet piping/steam bowl time constant, sec                |
| K1    | Fraction of hp shaft power after first boiler pass        |
| T5    | Time constant of second boiler pass (i.e. reaheater), sec |
| K2    | Fraction of lp shaft power after first boiler pass        |
| T6    | Time constant of crossover of third boiler pass, sec      |
| K3    | Fraction of hp shaft power after second boiler pass       |
| Ta    | Time to close Intercept Valve (IV), sec                   |
| Tb    | Time until Intercept Valve starts to reopen, sec          |
| Tc    | Time until Intercept Valve is fully open, sec             |
| Prmax | Maximum pressure in reheater, pu                          |
| Gv1   | Nonlinear gain point 1, pu gv                             |
| Pgv1  | Nonlinear gain point 1, pu power                          |
| Gv2   | Nonlinear gain point 2, pu gv                             |
| Pgv2  | Nonlinear gain point 2, pu power                          |
| Gv3   | Nonlinear gain point 3, pu gv                             |
| Pgv3  | Nonlinear gain point 3, pu power                          |
| Gv4   | Nonlinear gain point 4, pu gv                             |
| Pgv4  | Nonlinear gain point 4, pu power                          |
| Gv5   | Nonlinear gain point 5, pu gv                             |
| Pgv5  | Nonlinear gain point 5, pu power                          |
| Gv6   | Nonlinear gain point 6, pu gv                             |
| Pgv6  | Nonlinear gain point 6, pu power                          |

**Parameters for TGOV3D:**

|       |                                                           |
| ----- | --------------------------------------------------------- |
| K     | Governor gain (recirpocal of droop), pu                   |
| T1    | Governor lead time constant, sec                          |
| T2    | Governor lag time constant, sec                           |
| T3    | Valve positioner time constant, sec                       |
| Uo    | Maximum valve opening velocity, pu/sec                    |
| Uc    | Maximum valve closing velocity, pu/sec                    |
| Pmax  | Maximum valve opening, pu of mwcap                        |
| Pmin  | Minimum valve opening, pu of mwcap                        |
| T4    | Inlet piping/steam bowl time constant, sec                |
| K1    | Fraction of hp shaft power after first boiler pass        |
| T5    | Time constant of second boiler pass (i.e. reaheater), sec |
| K2    | Fraction of lp shaft power after first boiler pass        |
| T6    | Time constant of crossover of third boiler pass, sec      |
| K3    | Fraction of hp shaft power after second boiler pass       |
| Ta    | Time to close Intercept Valve (IV), sec                   |
| Tb    | Time until Intercept Valve starts to reopen, sec          |
| Tc    | Time until Intercept Valve is fully open, sec             |
| Prmax | Maximum pressure in reheater, pu                          |
| dbH   | Deadband High (pu)                                        |
| dbL   | Deadband Low (pu)                                         |
| Trate | Turbine rating, MW                                        |

---

<a id="tgov5"></a>

## TGOV5

*Source: [`Content/TransientModels_HTML/Governor TGOV5.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor TGOV5.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< Cb \< Mult\*TimeStep then Cb = Mult\*TimeStep
  - If 0.0 \< Psp \< Mult\*TimeStep then Psp = Mult\*TimeStep
  - If Uo \< Uc then swap the values. If Uo \< 0 then Uo change sign to positive. If Uc \> 0 then change sign to negative.
  - If Vmax \< Vmin then swap the values.
  - If Rmax \< Rmin then swap the values.
  - If Lmax \< Lmin then swap the values.
  - If Cmax \< Cmin then swap the values.
  - If DeltaPe \< 0 then change the sign to positive.
  - K1 to K8: Check K1+K3+K5+K7 and K2+K4+K6+K8 \<= 1.0 and if not normalized values to 1.0.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Vmax , then Vmax = Valve or if Valve \< Vmin , then Vmin = Valve
  - If Load Reference \> Lmax , then Lmax = Load Reference or if Load Reference \< Lmin , then Lmin = Load Reference

Model Equations and/or Block Diagrams

   ![Governor TGOV5 0001](images/Governor_TGOV5_0001.svg)

![Governor TGOV5 0002](images/Governor_TGOV5_0002.svg)

**Parameters:**

|         |                                                      |
| ------- | ---------------------------------------------------- |
| K       | Governor gain (recirpocal of droop), pu              |
| T1      | Governor mechanism time constant, sec                |
| T2      | Turbine power time constant, sec                     |
| T3      | Turbine exhaust temperature time constant, sec       |
| Uo      | Maximum valve opening velocity, pu/sec               |
| Uc      | Maximum valve closing velocity, pu/sec               |
| Vmax    | Maximum turbine power, pu of mwcap                   |
| Vmin    | Minimum turbine power, pu of mwcap                   |
| T4      | Governor lead time constant, sec                     |
| K1      | Fraction of hp shaft power after first boiler pass   |
| K2      | Fraction of lp shaft power after first boiler pass   |
| T5      | Governor lag time constant, sec                      |
| K3      | Fraction of hp shaft power after second boiler pass  |
| K4      | Fraction of lp shaft power after second boiler pass  |
| T6      | Time constant, sec                                   |
| K5      | Fraction of hp shaft power after third boiler pass   |
| K6      | Fraction of lp shaft power after third boiler pass   |
| T7      | Time constant, sec                                   |
| K7      | Fraction of hp shaft power after fourth boiler pass  |
| K8      | Fraction of lp shaft power after fourth boiler pass  |
| K9      | Gain                                                 |
| K10     | Gain                                                 |
| K11     | Gain                                                 |
| K12     | Gain                                                 |
| K13     | Gain                                                 |
| K14     | Gain                                                 |
| Rmax    | Maximum fuel valve opening rate, pu/sec              |
| Rmin    | Minimum fuel valve opening rate, pu/sec              |
| Lmax    | Po Maxmum                                            |
| Lmin    | Po Minimum                                           |
| C1      | Inputs                                               |
| C2      | Inputs                                               |
| C3      | Inputs                                               |
| B       | Turbine power time constant denominator scale factor |
| Cb      | Integrator time constant, sec                        |
| Ki      | Integral gain, pu                                    |
| Ti      | Time constant, sec                                   |
| Tr      | Washout time constant, sec                           |
| Tr1     | Washout time constant, sec                           |
| Cmax    | Controller maximum                                   |
| Cmin    | Controller minimum                                   |
| Td      | Input filter time constant, sec                      |
| Tf      | Washout time constant, sec                           |
| Tw      | Water inertia time constant, sec                     |
| Psp     | Pressure setpoint                                    |
| Tmw     | Pelec time constant, sec                             |
| Kl      | Controller gain                                      |
| Kmw     | Pelec gain                                           |
| DeltaPe | Deadband                                             |

---

<a id="turczt"></a>

## TURCZT

*Source: [`Content/TransientModels_HTML/Governor TURCZT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor TURCZT.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KP and TI: K3 can't be 0 if TI = 0, if true then KP changed to 10.
  - fDEAD must be greater than 0. If true, deadband will be ignored.
  - SDEAD must be greater than 0. If true, deadband will be ignored.
  - For Param TC, TI, TEHP, TR and TW then If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0, ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - For Param KM and TV then If 0 \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - If fMax\< fMin then swap the values.
  - If NTmax\< NTmin then swap the values.
  - If Gmax\< Gmin then swap the values.
  - If Vmax\< Vmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If PI Integrator\> NTmax, then NTmax = PI Integrator limits or if PI Integrator \< NTmin, then NTmin = PI Integrator
  - If Integrator\> Gmax, then Gmax = Integrator limits or if PI Integrator \< Gmin, then Gmin = Integrator

Model Equations and/or Block Diagrams

   ![Governor TURCZT 0001](images/Governor_TURCZT_0001.svg)

**Parameters:**

|        |        |
| ------ | ------ |
| SWITCH | SWITCH |
| fDEAD  | fDEAD  |
| fMin   | fMin   |
| fMax   | fMax   |
| KKOR   | KKOR   |
| KM     | KM     |
| KP     | KP     |
| SDEAD  | SDEAD  |
| KSTAT  | KSTAT  |
| KHP    | KHP    |
| TC     | TC     |
| TI     | TI     |
| TEHP   | TEHP   |
| TV     | TV     |
| THP    | THP    |
| TR     | TR     |
| TW     | TW     |
| NTmax  | NTmax  |
| NTmin  | NTmin  |
| Gmax   | Gmax   |
| Gmin   | Gmin   |
| Vmin   | Vmin   |
| Vmax   | Vmax   |

---

<a id="urgs3t"></a>

## URGS3T

*Source: [`Content/TransientModels_HTML/Governor URGS3T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor URGS3T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Linc \< 0.25\*Mult\*TimeStep then Linc = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Linc \< 0.5\*Mult\*TimeStep then Linc = 0.5\*Mult\*TimeStep
  - If 0.0 \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< Tltr \< Mult\*TimeStep then Tltr = Mult\*TimeStep
  - If B \<= 0 then B = 0.1
  - If Lmax \<= 0 then Lmax = 0.1
  - If Vmax \< Vmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Vmax, then Vmax = Valve or if Valve \< Vmin, then Vmin = Valve

Model Equations and/or Block Diagrams

   ![Governor URGS3T 0001](images/Governor_URGS3T_0001.svg)

**Parameters:**

|       |                                                      |
| ----- | ---------------------------------------------------- |
| MWCap | Turbine Rating, MW                                   |
| R     | Permanent droop, pu                                  |
| T1    | Governor mechanism time constant, sec                |
| T2    | Turbine power time constant, sec                     |
| T3    | Turbine exhaust temperature time constant, sec       |
| Lmax  | Ambient Temperature load limit, pu                   |
| Kt    | Temperature limiter gain                             |
| Vmax  | Maximum turbine power, pu of mwcap                   |
| Vmin  | Minimum turbine power, pu of mwcap                   |
| Dturb | Turbine damping coefficient, pu                      |
| Fidle | Fuel flow at zero power output, pu                   |
| Rmax  | Maximum fuel valve opening rate, pu/sec              |
| Linc  | Valve opening limit, pu                              |
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
| Ka    | Governor gain                                        |
| T4    | Governor lead time constant, sec                     |
| T5    | Governor lag time constant, sec                      |

---

<a id="ucbgt"></a>

## UCBGT

*Source: [`Content/TransientModels_HTML/Governor UCBGT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor UCBGT.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - For the parameters Tp, Tdg, Tthcp, Td, and Tv, the following check is done  
    If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - rfmax and rfmin are flipped if rfmax \< rfmin
  - Fmax and Fmin are flipped in Fmax \< Fmin
  - Vmax and Vmin are flipped in Vmax \< Vmin

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

The following parameters interpretations are applied when running transient stability

  - The absolute value of Dbd and Err are used.

Model Equations and/or Block Diagrams

   ![Governor UCBGT 0001](images/Governor_UCBGT_0001.svg)

**Parameters:**

|        |                                                                                                                                        |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Rp     | Electrical power feedback droop                                                                                                        |
| Tp     | Electrical power feedback time constant                                                                                                |
| Rv     | Governor feedback droop                                                                                                                |
| Kmwp   | Proportional gain for outer loop MW control                                                                                            |
| Kmwi   | Integral gain for outer loop MW control                                                                                                |
| rfmax  | Maximum limit on outer loop MW control loop                                                                                            |
| rfmin  | Minimum limit on outer loop MW control loop                                                                                            |
| Dbd    | Intentional deadband                                                                                                                   |
| Err    | Intentional error limit                                                                                                                |
| Ta     | Acceleration control differentiator time constant                                                                                      |
| aset   | Acceleration limit set-point                                                                                                           |
| Kpg    | Speed governor proportional gain                                                                                                       |
| Kig    | Speed governor integral gain                                                                                                           |
| Kdg    | Speed governor derivative gain                                                                                                         |
| Tdg    | Speed governor derivative time constant                                                                                                |
| Kpa    | Acceleration control proportional gain                                                                                                 |
| Kia    | Acceleration control integral gain                                                                                                     |
| Kpt    | Temperature control proportional gain                                                                                                  |
| Kit    | Temperature control integral gain                                                                                                      |
| Fmax   | Maximum fuel flow command                                                                                                              |
| FMin   | Minimum fuel flow command                                                                                                              |
| Tlimit | Temperature limit (in pu corresponds to fuel flow required for 1 pu turbine power i.e. = 1/Kt + Wfo) (4)                               |
| Tthcp  | Thermocouple time constant                                                                                                             |
| Tn     | Heat transfer lead time constant                                                                                                       |
| Td     | Heat transfer lag time constant                                                                                                        |
| Tv     | Fuel system time constant                                                                                                              |
| Vmax   | Maximum valve opening                                                                                                                  |
| Vmin   | Minimum valve opening                                                                                                                  |
| Fm     | Fuel flow multiplier; typically set to 1.0. In some cases this is equal to speed (e.g. liquid fuel system with shaft driven fuel pump) |
| Wfo    | Full-speed no-load fuel flow                                                                                                           |
| Kt     | Turbine gain                                                                                                                           |
| Ttn1   | Turbine transfer function numerator time constant 1                                                                                    |
| Ttn2   | Turbine transfer function numerator time constant 2                                                                                    |
| Ttd1   | Turbine transfer function denominator time constant 1                                                                                  |
| Ttd2   | Turbine transfer function denominator time constant 2                                                                                  |
| x1     | Turbine characteristic curve speed 1                                                                                                   |
| Fx1    | Turbine characteristic curve output for speed 1                                                                                        |
| x2     | Turbine characteristic curve speed 2                                                                                                   |
| Fx2    | Turbine characteristic curve output for speed 2                                                                                        |
| x3     | Turbine characteristic curve speed 3                                                                                                   |
| Fx3    | Turbine characteristic curve output for speed 3                                                                                        |
| Trate  | Turbine rating in MW                                                                                                                   |

---

<a id="uccpss"></a>

## UCCPSS

*Source: [`Content/TransientModels_HTML/Governor UCCPSS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor UCCPSS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - For the parameters Tp, Tdg, Tthcp, TdGT, TvGT, TdST, and TvST the following check is done  
    If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - For the parameters Tdrum, the following check is done  
    If Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - rfmax and rfmin are flipped if rfmax \< rfmin
  - Fmax and Fmin are flipped in Fmax \< Fmin
  - Vmax and Vmin are flipped in Vmax \< Vmin

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

The following parameters interpretations are applied when running transient stability

  - The absolute value of Dbd and Err are used.

Model Equations and/or Block Diagrams

![Governor UCCPSS 0001](images/Governor_UCCPSS_0001.svg)

![Governor UCCPSS 0002](images/Governor_UCCPSS_0002.svg)

**Parameters:**

|         |                                                                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Rp      | Electrical power feedback droop                                                                                                                        |
| Tp      | Electrical power feedback time constant                                                                                                                |
| Rv      | Governor feedback droop                                                                                                                                |
| Kmwp    | Proportional gain for outer loop MW control                                                                                                            |
| Kmwi    | Integral gain for outer loop MW control                                                                                                                |
| rfmax   | Maximum limit on outer loop MW control loop                                                                                                            |
| rfmin   | Minimum limit on outer loop MW control loop                                                                                                            |
| Dbd     | Intentional deadband                                                                                                                                   |
| Err     | Intentional error limit                                                                                                                                |
| Ta      | Acceleration control differentiator time constant                                                                                                      |
| aset    | Acceleration limit set-point                                                                                                                           |
| Kpg     | Speed governor proportional gain                                                                                                                       |
| Kig     | Speed governor integral gain                                                                                                                           |
| Kdg     | Speed governor derivative gain                                                                                                                         |
| Tdg     | Speed governor derivative time constant                                                                                                                |
| Kpa     | Acceleration control proportional gain                                                                                                                 |
| Kia     | Acceleration control integral gain                                                                                                                     |
| Kpt     | Temperature control proportional gain                                                                                                                  |
| Kit     | Temperature control integral gain                                                                                                                      |
| Fmax    | Maximum fuel flow command                                                                                                                              |
| FMin    | Minimum fuel flow command                                                                                                                              |
| Tlimit  | Temperature limit (in pu corresponds to fuel flow required for 1 pu turbine power i.e. = 1/Kt + Wfo) (4)                                               |
| Tthcp   | Thermocouple time constant                                                                                                                             |
| TnGT    | Heat transfer lead time constant                                                                                                                       |
| TdGT    | Heat transfer lag time constant                                                                                                                        |
| TvGT    | Fuel system time constant                                                                                                                              |
| Vmax    | Maximum valve opening                                                                                                                                  |
| Vmin    | Minimum valve opening                                                                                                                                  |
| Fm      | Fuel flow multiplier; typically set to 1.0. In some cases this is equal to speed (e.g. liquid fuel system with shaft driven fuel pump)                 |
| Wfo     | Full-speed no-load fuel flow                                                                                                                           |
| Kt      | Turbine gain                                                                                                                                           |
| Ttn1    | Turbine transfer function numerator time constant 1                                                                                                    |
| Ttn2    | Turbine transfer function numerator time constant 2                                                                                                    |
| Ttd1    | Turbine transfer function denominator time constant 1                                                                                                  |
| Ttd2    | Turbine transfer function denominator time constant 2                                                                                                  |
| x1      | Turbine characteristic curve speed 1                                                                                                                   |
| Fx1     | Turbine characteristic curve output for speed 1                                                                                                        |
| x2      | Turbine characteristic curve speed 2                                                                                                                   |
| Fx2     | Turbine characteristic curve output for speed 2                                                                                                        |
| x3      | Turbine characteristic curve speed 3                                                                                                                   |
| Fx3     | Turbine characteristic curve output for speed 3                                                                                                        |
| TrateGT | Gas Turbine rating in MW                                                                                                                               |
| Pgt1    | Power Point \#1 for Heat versus gas turbine power function                                                                                             |
| Qgt1    | Heat at Power Point \#1 for Heat versus gas turbine power function                                                                                     |
| Pgt2    | Power Point \#2 for Heat versus gas turbine power function                                                                                             |
| Qgt2    | Heat at Power Point \#2 for Heat versus gas turbine power function                                                                                     |
| Pgt3    | Power Point \#3 for Heat versus gas turbine power function                                                                                             |
| Qgt3    | Heat at Power Point \#3 for Heat versus gas turbine power function                                                                                     |
| Pgt4    | Power Point \#4 for Heat versus gas turbine power function                                                                                             |
| Qgt4    | Heat at Power Point \#4 for Heat versus gas turbine power function                                                                                     |
| Pgt5    | Power Point \#5 for Heat versus gas turbine power function                                                                                             |
| Qgt5    | Heat at Power Point \#5 for Heat versus gas turbine power function                                                                                     |
| Pgt6    | Power Point \#6 for Heat versus gas turbine power function                                                                                             |
| Qgt6    | Heat at Power Point \#6 for Heat versus gas turbine power function                                                                                     |
| Pgt7    | Power Point \#7 for Heat versus gas turbine power function                                                                                             |
| Qgt7    | Heat at Power Point \#7 for Heat versus gas turbine power function                                                                                     |
| Tdrum   | Drum time constant                                                                                                                                     |
| Km      | Pressure loss due to flow friction in the boiler tubes                                                                                                 |
| TvST    | Actuator time constant for main steam                                                                                                                  |
| Kp      | Governor proportional gain                                                                                                                             |
| Ki      | Governor integral gain                                                                                                                                 |
| TnST    | Turbine lead time constant                                                                                                                             |
| TdST    | Turbine lag time constant                                                                                                                              |
| Qs      | Amount of supplemental firing, in per unit, applied to the boiler; it is to be defined by the user or by the program upon initialization of the model. |
| Bv      | Fixed position of the bypass valve defined by the user to simulate a fixed amount of steam extraction.                                                 |
| Pref    | Minimum steam pressure reference                                                                                                                       |
| TrateST | Steam Turbine rating in MW                                                                                                                             |

---

<a id="uhrsg"></a>

## UHRSG

*Source: [`Content/TransientModels_HTML/Governor UHRSG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor UHRSG.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - For the parameters Td and Tv, the following check is done  
    If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - For the parameters Tdrum, the following check is done  
    If Param \< Mult\*TimeStep then Param = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor UHRSG 0001](images/Governor_UHRSG_0001.svg)

**Parameters:**

|       |                                                                                                                                                        |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Pgt1  | Power Point \#1 for Heat versus gas turbine power function                                                                                             |
| Qgt1  | Heat at Power Point \#1 for Heat versus gas turbine power function                                                                                     |
| Pgt2  | Power Point \#2 for Heat versus gas turbine power function                                                                                             |
| Qgt2  | Heat at Power Point \#2 for Heat versus gas turbine power function                                                                                     |
| Pgt3  | Power Point \#3 for Heat versus gas turbine power function                                                                                             |
| Qgt3  | Heat at Power Point \#3 for Heat versus gas turbine power function                                                                                     |
| Pgt4  | Power Point \#4 for Heat versus gas turbine power function                                                                                             |
| Qgt4  | Heat at Power Point \#4 for Heat versus gas turbine power function                                                                                     |
| Pgt5  | Power Point \#5 for Heat versus gas turbine power function                                                                                             |
| Qgt5  | Heat at Power Point \#5 for Heat versus gas turbine power function                                                                                     |
| Pgt6  | Power Point \#6 for Heat versus gas turbine power function                                                                                             |
| Qgt6  | Heat at Power Point \#6 for Heat versus gas turbine power function                                                                                     |
| Pgt7  | Power Point \#7 for Heat versus gas turbine power function                                                                                             |
| Qgt7  | Heat at Power Point \#7 for Heat versus gas turbine power function                                                                                     |
| Tdrum | Drum time constant                                                                                                                                     |
| Km    | Pressure loss due to flow friction in the boiler tubes                                                                                                 |
| Tv    | Actuator time constant for main steam                                                                                                                  |
| Kp    | Governor proportional gain                                                                                                                             |
| Ki    | Governor integral gain                                                                                                                                 |
| Tn    | Turbine lead time constant                                                                                                                             |
| Td    | Turbine lag time constant                                                                                                                              |
| Qs    | Amount of supplemental firing, in per unit, applied to the boiler; it is to be defined by the user or by the program upon initialization of the model. |
| Bv    | Fixed position of the bypass valve defined by the user to simulate a fixed amount of steam extraction.                                                 |
| Pref  | Minimum steam pressure reference                                                                                                                       |
| Trate | Turbine rating for the Steam Turbine in MW                                                                                                             |

---

<a id="w2301"></a>

## W2301

*Source: [`Content/TransientModels_HTML/Governor W2301.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor W2301.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Turb \< 0.5\*Mult\*TimeStep then Turb = 0, ElseIf 0.5\*Mult\*TimeStep \< Turb \< Mult\*TimeStep then Turb = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tv \< 0.25\*Mult\*TimeStep then Tv = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0.5\*Mult\*TimeStep
  - If Gmax \< Gmin then swap the values.
  - Alpha: Alpha can not be 1.05. Error will be created.
  - Beta: Beta can not be 0.0. Error will be created.
  - Gamma: Gamma can not be 0.0. Error will be created.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Valve \> Gmax , then Gmax = Valve or if Valve \< Gmin , then Gmin = Valve

Model Equations and/or Block Diagrams

![Governor W2301 0001](images/Governor_W2301_0001.svg)

**Parameters:**

|        |                                   |
| ------ | --------------------------------- |
| Tp     | Power transducer time constant    |
| Alpha  | Gain setting                      |
| Beta   | Reset setting                     |
| Rho    | Compensation                      |
| Gamma  | Droop setting, pu                 |
| Gain   | Turbine gain                      |
| TV     | Valve actuator time constant, sec |
| Velamx | Maximum valve velocity, psec      |
| Gmax   | Maximum valve opening, pu         |
| Gmin   | Minimum valve opening, pu         |
| Gnl    | Valve opening at no load, pu      |
| Tturb  | Turbine time constant, sec        |
| D      | Turbine damping coefficient       |
| Kt     | Turbine lead-lag ratio            |

---

<a id="wehgov"></a>

## WEHGOV

*Source: [`Content/TransientModels_HTML/Governor WEHGOV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WEHGOV.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tpe \< 0.5\*Mult\*TimeStep then Tpe = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpe \< Mult\*TimeStep then Tpe = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tdv \< Mult\*TimeStep then Tdv = Mult\*TimeStep
  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Gtmxop \< Gtmxcl then swap the values. If Gtmxop \< 0 then Gtmxop change sign to positive. If Gtmxcl \> 0 then change sign to negative.
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WEHGOV 0001](images/Governor_WEHGOV_0001.svg)

**Parameters:**

|               |                                                             |
| ------------- | ----------------------------------------------------------- |
| Feedback      | Feedback signal: 0=electric power feedback, 1=gate position |
| RpermGate     | Rperm Gate                                                  |
| RpermPE       | Rperm PE                                                    |
| Tpe           | Tpe                                                         |
| Kp            | Proportional gain, pu                                       |
| Ki            | Integral gain, pu                                           |
| Kd            | Derivative gain, pu                                         |
| Td            | Input filter time constant, sec                             |
| Tp            | Lead time constant, sec                                     |
| Tdv           | Tdv                                                         |
| Tg            | Gate servo time constant, sec                               |
| GTMXOP        | GTMXOP                                                      |
| GTMXCL        | GTMXCL                                                      |
| Gmax          | Maximum gate velocity, pu of mwcap                          |
| Gmin          | Minimum gate velocity, pu of mwcap                          |
| Dturb         | Turbine damping coefficient, pu                             |
| Tw            | Water inertia time constant, sec                            |
| SpeedDeadband | Speed deadband                                              |
| DPV           | DPV                                                         |
| DICN          | DICN                                                        |
| Gate1         | Gate 1                                                      |
| Gate2         | Gate 2                                                      |
| Gate3         | Gate 3                                                      |
| Gate4         | Gate 4                                                      |
| Gate5         | Gate 5                                                      |
| FlowG1        | Flow G1                                                     |
| FlowG2        | Flow G2                                                     |
| FlowG3        | Flow G3                                                     |
| FlowG4        | Flow G4                                                     |
| FlowG5        | Flow G5                                                     |
| FlowP1        | Flow P1                                                     |
| FlowP2        | Flow P2                                                     |
| FlowP3        | Flow P3                                                     |
| FlowP4        | Flow P4                                                     |
| FlowP5        | Flow P5                                                     |
| FlowP6        | Flow P6                                                     |
| FlowP7        | Flow P7                                                     |
| FlowP8        | Flow P8                                                     |
| FlowP9        | Flow P9                                                     |
| FlowP10       | Flow P10                                                    |
| PMECH1        | PMECH 1                                                     |
| PMECH2        | PMECH 2                                                     |
| PMECH3        | PMECH 3                                                     |
| PMECH4        | PMECH 4                                                     |
| PMECH5        | PMECH 5                                                     |
| PMECH6        | PMECH 6                                                     |
| PMECH7        | PMECH 7                                                     |
| PMECH8        | PMECH 8                                                     |
| PMECH9        | PMECH 9                                                     |
| PMECH10       | PMECH 10                                                    |

---

<a id="wesgov"></a>

## WESGOV

*Source: [`Content/TransientModels_HTML/Governor WESGOV and WESGOVD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor WESGOV and WESGOVD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ti \< Mult\*TimeStep then Ti = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor WESGOV 0001](images/Governor_WESGOV_0001.svg)

**Parameters for WESGOV:**

|         |                                                                |
| ------- | -------------------------------------------------------------- |
| DeltaTC | Delta t sample for controls, sec                               |
| DeltaTP | Delta t sample for PE, sec                                     |
| Droop   | Droop                                                          |
| Kp      | Proportional gain, pu                                          |
| Ti      | Integrator Time constant, sec                                  |
| T1      | Pmech time constant 1, sec                                     |
| T2      | Pmech time constant 2, sec                                     |
| Alim    | Maximum change is limited by this value between sampling times |
| Tpe     | Pelec time constant, sec                                       |

**Parameters for WESGOVD:**

|         |                                                                |
| ------- | -------------------------------------------------------------- |
| DeltaTC | Delta t sample for controls, sec                               |
| DeltaTP | Delta t sample for PE, sec                                     |
| Droop   | Droop                                                          |
| Kp      | Proportional gain, pu                                          |
| Ti      | Integrator Time constant, sec                                  |
| T1      | Pmech time constant 1, sec                                     |
| T2      | Pmech time constant 2, sec                                     |
| Alim    | Maximum change is limited by this value between sampling times |
| Tpe     | Pelec time constant, sec                                       |
| dbH     | Deadband High (pu)                                             |
| dbL     | Deadband Low (pu)                                              |
| Trate   | Turbine rating, MW                                             |
