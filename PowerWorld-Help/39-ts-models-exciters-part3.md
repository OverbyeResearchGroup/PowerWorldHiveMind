---
title: "TS Models — Exciters (Part 3 of 5)"
part: "Transient Models"
chapter_file: "39-ts-models-exciters-part3.md"
topics: 33
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Exciters (Part 3 of 5)

Excitation system models (IEEE types, ESST/ESAC/EXST families, REEC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (33)**

- [EXDC2_PTI](#exdc2-pti)
- [EXDC2A](#exdc2a)
- [EXDC4](#exdc4)
- [EXELI](#exeli)
- [EXIVO](#exivo)
- [EXPIC1](#expic1)
- [EXST1_GE](#exst1-ge)
- [EXST1_PTI](#exst1-pti)
- [EXST2](#exst2)
- [EXST2A](#exst2a)
- [EXST3](#exst3)
- [EXST3A](#exst3a)
- [EXST4B](#exst4b)
- [EXWTG1](#exwtg1)
- [EXWTGE](#exwtge)
- [IEEET1](#ieeet1)
- [IEEET2](#ieeet2)
- [IEEET3](#ieeet3)
- [IEEET4](#ieeet4)
- [IEEET5](#ieeet5)
- [IEEEX1](#ieeex1)
- [IEEEX2](#ieeex2)
- [IEEEX3](#ieeex3)
- [IEEEX4](#ieeex4)
- [IEET1A](#ieet1a)
- [IEET1B](#ieet1b)
- [IEET5A](#ieet5a)
- [IEEX2A](#ieex2a)
- [IVOEX](#ivoex)
- [MEXS](#mexs)
- [PLAYINEX](#playinex)
- [PV1E](#pv1e)
- [REEC_A](#reec-a)

---

<a id="exdc2-pti"></a>

## EXDC2_PTI

*Source: [`Content/TransientModels_HTML/Exciter EXDC2_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXDC2_PTI.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXDC2 PTI 0001](images/Exciter_EXDC2_PTI_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Tr     | Filter time constant, sec                      |
| Ka     | Voltage regulator gain                         |
| Ta     | Time constant, sec                             |
| Tb     | Lag time constant, sec                         |
| Tc     | Lead time constant, sec                        |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Ke     | Exciter field resistance line slope margin, pu |
| Te     | Exciter time constant, sec                     |
| Kf     | Rate feedback gain, pu                         |
| Tf1    | Rate feedback time constant, sec               |
| Switch | Parameter not used in PowerWorld               |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| E2     | Field voltage value, 2                         |
| SE2    | Saturation factor at E2                        |

---

<a id="exdc2a"></a>

## EXDC2A

*Source: [`Content/TransientModels_HTML/Exciter EXDC2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXDC2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXDC2A 0001](images/Exciter_EXDC2A_0001.svg)

**Parameters:**

|       |                                                                            |
| ----- | -------------------------------------------------------------------------- |
| Tr    | Filter time constant, sec                                                  |
| Ka    | Voltage regulator gain                                                     |
| Ta    | Time constant, sec                                                         |
| Tb    | Lag time constant, sec                                                     |
| Tc    | Lead time constant, sec                                                    |
| Vrmax | Maximum control element output, pu                                         |
| Vrmin | Minimum control element output, pu                                         |
| Ke    | Exciter field resistance line slope margin, pu                             |
| Te    | Exciter time constant, sec                                                 |
| Kf    | Rate feedback gain, pu                                                     |
| Tf1   | Rate feedback time constant, sec                                           |
| Tf2   | Second rate feedback time constant, zero for a pure IEEE EX DC2 model, sec |
| E1    | Field voltage value, 1                                                     |
| SE1   | Saturation factor at E1                                                    |
| E2    | Field voltage value, 2                                                     |
| SE2   | Saturation factor at E2                                                    |

---

<a id="exdc4"></a>

## EXDC4

*Source: [`Content/TransientModels_HTML/Exciter EXDC4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXDC4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Kv = 0 then Kv = 0.02
  - If Kr = 0 then Kr = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXDC4 0001](images/Exciter_EXDC4_0001.svg)

**Parameters:**

|       |                                                                                                                                                                                                   |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kr    | Verr deadband. If Kr is not zero, the voltage regulator input changes at a constant rate if Verr \> Kr or Verr \< -Kr. If Kr is zero, the error signal drives the voltage regulator continuously. |
| Trh   | Rheostat time constant, sec                                                                                                                                                                       |
| Kv    | Fast raise/lower contact setting                                                                                                                                                                  |
| Vrmax | Maximum control element output, pu                                                                                                                                                                |
| Vrmin | Minimum control element output, pu                                                                                                                                                                |
| Te    | Exciter time constant, sec                                                                                                                                                                        |
| Ke    | Exciter field resistance line slope margin, pu                                                                                                                                                    |
| E1    | Field voltage value, 1                                                                                                                                                                            |
| SE1   | Saturation factor at E1                                                                                                                                                                           |
| E2    | Field voltage value, 2                                                                                                                                                                            |
| SE2   | Saturation factor at E2                                                                                                                                                                           |

---

<a id="exeli"></a>

## EXELI

*Source: [`Content/TransientModels_HTML/Exciter EXELI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXELI.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tfv \< 0.5\*Mult\*TimeStep then Tfv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfv \< Mult\*TimeStep then Tfv = Mult\*TimeStep
  - If 0.0 \< Tfi \< 0.5\*Mult\*TimeStep then Tfi = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfi \< Mult\*TimeStep then Tfi = Mult\*TimeStep
  - If 0.0 \< Ts1 \< 0.5\*Mult\*TimeStep then Ts1 = 0,ElseIf 0.5\*Mult\*TimeStep \< Ts1 \< Mult\*TimeStep then Ts1 = Mult\*TimeStep
  - If 0.0 \< Ts2 \< 0.5\*Mult\*TimeStep then Ts2 =0, ElseIf 0.5\*Mult\*TimeStep \< Ts2 \< Mult\*TimeStep then Ts2 = Mult\*TimeStep
  - If 0.0 \< Tw \< 0.5\*Mult\*TimeStep then Tw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If 0 \< Tnu \< Mult\*TimeStep then Tnu = Mult\*TimeStep
  - If Vpi \> 0 then Vpi = Mult\*TimeStep
  - If Vpu \> 0 then Vpu = Mult\*TimeStep
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> Efdmax, then Efdmax = Efd or if Efd \< Efdmin, then Efdmin = Efd

Model Equations and/or Block Diagrams

![Exciter EXELI 0001](images/Exciter_EXELI_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tfv   | Voltage transducer time contant, sec           |
| Tfi   | Current transducer time constant, sec          |
| Tnu   | Controller reset time constant, sec            |
| Vpu   | Voltage controller proportional gain           |
| Vpi   | Current controller gain                        |
| Vpnf  | Controller followup gain                       |
| Dpnf  | Controller followup deadband, pu               |
| Efmin | Minimum open circuit excitation voltage, pu    |
| Efmax | Maximum open circuit excitation voltage, pu    |
| Xe    | Excitation transformer effective reactance, pu |
| Tw    | Stabilizer time constant, sec                  |
| Ks1   | Stabilizer gain 1                              |
| Ks2   | Stabilizer gain 2                              |
| Ts1   | Stabilizer phase lag time constant             |
| Ts2   | Stabilizer filter time constant                |
| Smax  | Stabilizer output limit                        |

---

<a id="exivo"></a>

## EXIVO

*Source: [`Content/TransientModels_HTML/Exciter EXIVO.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXIVO.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If V5 \> Efdmax, then Efdmax = V5 or if V5 \< Efdmin, then Efdmin = V5
  - If V3 \> Vmax3, then Vmax3 = V3 or if V3 \< Vmin3, then Vmin3 = V3
  - If V1 \> Vmax1, then Vmax1 = V1 or if V1 \< Vmin1, then Vmin1 = V1

Model Equations and/or Block Diagrams

![Exciter EXIVO 0001](images/Exciter_EXIVO_0001.svg)

**Parameters:**

|       |                               |
| ----- | ----------------------------- |
| Tr    | Transducer time constant, sec |
| K1    | Voltage regulator gain, pu    |
| A1    | Lead coefficient, pu          |
| A2    | Lag coefficient, pu           |
| T1    | Lead time constant, sec       |
| T2    | Lag time constant, sec        |
| VMax1 | Lead-lag maxmimum limit, pu   |
| VMin1 | Lead-lag minimum limit, pu    |
| K3    | Voltage regulator gain, pu    |
| A3    | Lead coefficient, pu          |
| A4    | Lag coefficient, pu           |
| T3    | Lead time constant, sec       |
| T4    | Lag time constant, sec        |
| VMax3 | Lead-lag maxmimum limit, pu   |
| VMin3 | Lead-lag minimum limit, pu    |
| K5    | Voltage regulator gain, pu    |
| A5    | Lead coefficient, pu          |
| A6    | Lag coefficient, pu           |
| T5    | Lead time constant, sec       |
| T6    | Lag time constant, sec        |
| VMax5 | Lead-lag maxmimum limit, pu   |
| VMin5 | Lead-lag minimum limit, pu    |

---

<a id="expic1"></a>

## EXPIC1

*Source: [`Content/TransientModels_HTML/Exciter EXPIC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXPIC1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Ta2 \< 0.5\*Mult\*TimeStep then Ta2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta2 \< Mult\*TimeStep then Ta2 = Mult\*TimeStep
  - If 0.0 \< Ta4 \< 0.5\*Mult\*TimeStep then Ta4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta4 \< Mult\*TimeStep then Ta4 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vr1 \< Vr2 then swap the values
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> Efdmax, then Efdmax = Efd limits or if Efd \< Efdmin, then Efdmin = Efd
  - If Vr \> Vrmax , then Vrmax = Vr limits or if Vr limits \< Vrmin, then Vrmin = Vr limits
  - If Va \> Vr1, then Vr1 = Va or if Va \< Vr2, then Vr2 = Va

Model Equations and/or Block Diagrams

![Exciter EXPIC1 0001](images/Exciter_EXPIC1_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Tr     | Transducer time constant, sec                  |
| Ka     | Voltage regulator gain                         |
| Ta1    | Voltage regulator time constant, sec           |
| Vr1    | PI maximum limit, pu                           |
| Vr2    | PI minimum limit, pu                           |
| Ta2    | Voltage regulator time constant, sec           |
| Ta3    | Voltage regulator time constant, sec           |
| Ta4    | Voltage regulator time constant, sec           |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Kf     | Rate feedback gain, pu                         |
| Tf1    | Feedback lead time constant, sec               |
| Tf2    | Feedback lag time constant, sec                |
| Efdmax | Maximum excitation output, pu                  |
| Efdmin | Minimum excitation output, pu                  |
| Ke     | Exciter field resistance line slope margin, pu |
| Te     | Exciter field time constant, sec               |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| E2     | Field voltage value, 2                         |
| SE2    | Saturation factor at E2                        |
| Kp     | Potential source gain, pu                      |
| Ki     | Current source gain, pu                        |
| Kc     | Rectifier regulation factor, pu                |

---

<a id="exst1-ge"></a>

## EXST1_GE

*Source: [`Content/TransientModels_HTML/Exciter EXST1_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST1_GE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.3\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.3\*Mult\*TimeStep \< Tf \< 0.6\*Mult\*TimeStep then Tf = 0.6\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.05\*Mult\*TimeStep then Tb = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< Tb \< 0.1\*Mult\*TimeStep then Tb = 0.1\*Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.05\*Mult\*TimeStep then Tb1 = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< Tb1 \< 0.1\*Mult\*TimeStep then Tb1 = 0.1\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va
  - If Vi \> Vimax, then Vimax = Vi limits or if Vi \< Vimin, then Vimin = Vi

Model Equations and/or Block Diagrams

![Exciter EXST1 GE 0001](images/Exciter_EXST1_GE_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Filter time constant, sec                      |
| ViMax | Maximum error, pu                              |
| ViMin | Minimum error, pu                              |
| Tc    | Lag time constant, sec                         |
| Tb    | Lead time constant, sec                        |
| Ka    | Gain, pu                                       |
| Ta    | Voltage regulator time constant, sec           |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Kc    | Rectifier regulation factor, pu                |
| Kf    | Rate feedback gain, pu                         |
| Tf    | Rate feedback constant, sec                    |
| Tc1   | Lag time constant, sec                         |
| Tb1   | Lead time constant, sec                        |
| VaMax | Maximum control element output, pu             |
| VaMin | Minimum control element output, pu             |
| Xe    | Excitation transformer effective reactance, pu |
| Ilr   | Maximum field current, pu                      |
| Klr   | Gain on field current limit                    |

---

<a id="exst1-pti"></a>

## EXST1_PTI

*Source: [`Content/TransientModels_HTML/Exciter EXST1_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST1_PTI.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.3\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.3\*Mult\*TimeStep \< fb \< 0.6\*Mult\*TimeStep then Tf = 0.6\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.05\*Mult\*TimeStep then Tb = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< Tb \< 0.1\*Mult\*TimeStep then Tb = 0.1\*Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.05\*Mult\*TimeStep then Tb1 = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< Tb1 \< 0.1\*Mult\*TimeStep then Tb1 = 0.1\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi

Model Equations and/or Block Diagrams

![Exciter EXST1 PTI 0001](images/Exciter_EXST1_PTI_0001.svg)

**Parameters:**

|       |                                      |
| ----- | ------------------------------------ |
| Tr    | Filter time constant, sec            |
| ViMax | Maximum error, pu                    |
| ViMin | Minimum error, pu                    |
| Tc    | Lag time constant, sec               |
| Tb    | Lead time constant, sec              |
| Ka    | Gain, pu                             |
| Ta    | Voltage regulator time constant, sec |
| Vrmax | Maximum control element output, pu   |
| Vrmin | Minimum control element output, pu   |
| Kc    | Rectifier regulation factor, pu      |
| Kf    | Rate feedback gain, pu               |
| Tf    | Rate feedback constant, sec          |

---

<a id="exst2"></a>

## EXST2

*Source: [`Content/TransientModels_HTML/Exciter EXST2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep, but if Tr \> 0.5 then Tr = 0.5
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Efd \> Efdmax, then Efdmax = Efd

Model Equations and/or Block Diagrams

![Exciter EXST2 0001](images/Exciter_EXST2_0001.svg)

**Parameters:**

|        |                                            |
| ------ | ------------------------------------------ |
| Tr     | Filter time constant, sec                  |
| Ka     | Gain, pu                                   |
| Ta     | Voltage regulator time constant, sec       |
| Vrmax  | Maximum control element output, pu         |
| Vrmin  | Minimum control element output, pu         |
| Ke     | Exciter field resistance time constant, pu |
| Te     | Exciter field time constant, sec           |
| Kf     | Rate feedback gain, pu                     |
| Tf     | Rate feedback constant, sec                |
| Kp     | Potential source gain, pu                  |
| Ki     | Current source gain, pu                    |
| Kc     | Rectifier regulation factor, pu            |
| Efdmax | Maximum excitation output, pu              |
| Tb     | Lead time constant, sec                    |
| Tc     | Lag time constant, sec                     |

---

<a id="exst2a"></a>

## EXST2A

*Source: [`Content/TransientModels_HTML/Exciter EXST2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep, but if Tr \> 0.5 then Tr = 0.5
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Efd \> Efdmax, then Efdmax = Efd

Model Equations and/or Block Diagrams

![Exciter EXST2A 0001](images/Exciter_EXST2A_0001.svg)

**Parameters:**

|        |                                            |
| ------ | ------------------------------------------ |
| Tr     | Filter time constant, sec                  |
| Ka     | Gain, pu                                   |
| Ta     | Voltage regulator time constant, sec       |
| Vrmax  | Maximum control element output, pu         |
| Vrmin  | Minimum control element output, pu         |
| Ke     | Exciter field resistance time constant, pu |
| Te     | Exciter field time constant, sec           |
| Kf     | Rate feedback gain, pu                     |
| Tf     | Rate feedback constant, sec                |
| Kp     | Potential source gain, pu                  |
| Ki     | Current source gain, pu                    |
| Kc     | Rectifier regulation factor, pu            |
| Efdmax | Maximum excitation output, pu              |
| Tb     | Lead time constant, sec                    |
| Tc     | Lag time constant, sec                     |

---

<a id="exst3"></a>

## EXST3

*Source: [`Content/TransientModels_HTML/Exciter EXST3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep, but if Tr \> 0.5 then Tr = 0.5
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kj = 0 then Kj = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi
  - If Efd \> Efdmax, then Efdmax = Efd

Model Equations and/or Block Diagrams

![Exciter EXST3 0001](images/Exciter_EXST3_0001.svg)

**Parameters:**

|           |                                                       |
| --------- | ----------------------------------------------------- |
| Tr        | Filter time constant, sec                             |
| ViMax     | Maximum error, pu                                     |
| ViMin     | Minimum error, pu                                     |
| Kj        | Gain, pu                                              |
| Tc        | Lag time constant, sec                                |
| Tb        | Lead time constant, sec                               |
| Ka        | Gain, pu                                              |
| Ta        | Voltage regulator time constant, sec                  |
| Vrmax     | Maximum control element output, pu                    |
| Vrmin     | Minimum control element output, pu                    |
| Kg        | Excitation limiter gain, pu                           |
| Kp        | Potential source gain, pu                             |
| Ki        | Current source gain, pu                               |
| Efdmax    | Maximum excitation output, pu                         |
| Kc        | Rectifier regulation factor, pu                       |
| Xl        | P-bar leakage reactance, pu                           |
| VgMax     | Maximum excitation voltage                            |
| ThetaPDeg | Phase angle of potential source, degrees              |
| Spdmlt    | If not zero, multiply output (Efd) by generator speed |

---

<a id="exst3a"></a>

## EXST3A

*Source: [`Content/TransientModels_HTML/Exciter EXST3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kj = 0 then Kj = Mult\*TimeStep
  - If Kp = 0 then Kp = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi
  - If Vb \> Efdmax, then Efdmax = Vb

Model Equations and/or Block Diagrams

![Exciter EXST3A 0001](images/Exciter_EXST3A_0001.svg)

**Parameters:**

|           |                                          |
| --------- | ---------------------------------------- |
| Tr        | Filter time constant, sec                |
| ViMax     | Maximum error, pu                        |
| ViMin     | Minimum error, pu                        |
| Kj        | Gain, pu                                 |
| Tc        | Lag time constant, sec                   |
| Tb        | Lead time constant, sec                  |
| Ka        | Gain, pu                                 |
| Ta        | Voltage regulator time constant, sec     |
| Vrmax     | Maximum control element output, pu       |
| Vrmin     | Minimum control element output, pu       |
| Kg        | Excitation limiter gain, pu              |
| Kp        | Potential source gain, pu                |
| Ki        | Current source gain, pu                  |
| VbMax     | Maximum excitation voltage, pu           |
| Kc        | Rectifier regulation factor, pu          |
| Xl        | P-bar leakage reactance, pu              |
| VgMax     | Maximum excitation voltage               |
| ThetaPDeg | Phase angle of potential source, degrees |

---

<a id="exst4b"></a>

## EXST4B

*Source: [`Content/TransientModels_HTML/Exciter EXST4B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXST4B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Kpm = 0 then Kpm = 1
  - If Vrmax \< Vrmin then swap the values
  - If Vmmax \< Vmmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vm \> Vmmax, then Vmmax = Vm or if Vm \< Vmmin, then Vmmin = Vm

Model Equations and/or Block Diagrams

![Exciter EXST4B 0001](images/Exciter_EXST4B_0001.svg)

**Parameters:**

Tr Filter time constant, sec

Kpr Proportional gain, pu

Kir Integral gain, pu

Ta Voltage regulator time constant, sec

Vrmax Maximum control element output, pu

Vrmin Minimum control element output, pu

Kpm Proportional gain of field voltage regulator, pu

Kim Integral gain of field voltage regulator, pu

VmMax Model Parameters\\VmMax

VmMin Model Parameters\\VmMin

Kg Excitation limiter gain, pu

Kp Potential source gain, pu

ThetaPDeg Phase angle of potential source, degrees

Ki Current source gain, pu

Kc Rectifier regulation factor, pu

Xl P-bar leakage reactance, pu

VbMax Maximum excitation voltage, pu

---

<a id="exwtg1"></a>

## EXWTG1

*Source: [`Content/TransientModels_HTML/Exciter EXWTG1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXWTG1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tw2 \< 0.5\*Mult\*TimeStep then Tw2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Tdp \< Mult\*TimeStep then Tdp = Mult\*TimeStep
  - If Rmax \< Rmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Rexternal \> Rmax, then Rmax = Rexternal or if Rexternal \< Rmin, then Rmin = Rexternal

Model Equations and/or Block Diagrams

![Exciter EXWTG1 0001](images/Exciter_EXWTG1_0001.svg)

**Parameters:**

|      |                                                    |
| ---- | -------------------------------------------------- |
| Ta   | Voltage regulator time constant, sec               |
| Kdp  | Power derivative gain                              |
| Tdp  | Power derivative washout time constant, sec        |
| Kw   | Speed regulator gain                               |
| Tw1  | Speed regulator TGR numerator time constant, sec   |
| Tw2  | Speed regulator TGR denominator time constant, sec |
| Rmax | Maximum external rotor resistance, pu              |
| Rmin | Minimum external rotor resistance, pu              |

---

<a id="exwtge"></a>

## EXWTGE

*Source: [`Content/TransientModels_HTML/Exciter EXWTGE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXWTGE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tlpdq \< 0.5\*Mult\*TimeStep then Tlpdq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tlpdq \< Mult\*TimeStep then Tlpdq = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tc \< 0.5\*Mult\*TimeStep then Tc = 0, ElseIf 0.5\*Mult\*TimeStep \< Tc \< Mult\*TimeStep then Tc = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Xiqmax \< Xiqmin then swap the values
  - If Vermx \< Vermn then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If EqppCMD \> Xiqmax, then Xiqmax = EqppCMD or if EqppCMD \< Xiqmin, then Xiqmin = EqppCMD
  - If QCord \> Qmax , then Qmax = QCord or if QCord \< Qmin , then Qmin = QCord
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef

Model Equations and/or Block Diagrams

![Exciter EXWTGE 0001](images/Exciter_EXWTGE_0001.svg)

**Parameters:**

|        |                                                                                         |
| ------ | --------------------------------------------------------------------------------------- |
| varflg | 1=Qord from WindVar emulation; -1=Qord from vref; 0=constant                            |
| Kqi    | Q control integral gain                                                                 |
| Kvi    | V control integral gain                                                                 |
| Vmax   | Max. V at regulated bus, pu                                                             |
| Vmin   | Min. V at regulated bus, pu                                                             |
| Qmax   | Max. Q command, pu                                                                      |
| Qmin   | Min. Q command, pu                                                                      |
| XIqmax | (+Vterm)=max. Eq"(flux) command, pu                                                     |
| XIqmin | (+Vterm)=min. Eq"(flux) command, pu                                                     |
| Tr     | WindVar voltage measurement lag, sec                                                    |
| Tc     | Lag between WindVar output and wind turbine, sec                                        |
| Kpv    | WindVar regulator proportional gain                                                     |
| Kiv    | WindVar regulator integral gain                                                         |
| Vl1    | Open loop control: low voltage limit, pu                                                |
| Vh1    | Open loop control: high voltage limit, pu                                               |
| Tl1    | Open loop control: first low voltage time, sec                                          |
| Tl2    | Open loop control: second low voltage time, sec                                         |
| Th1    | Open loop control: first high voltage time, sec                                         |
| Th2    | Open loop control: second high voltage time, sec                                        |
| Ql1    | Open loop control: first low voltage Q command, pu                                      |
| Ql2    | Open loop control: second low voltage Q command, pu                                     |
| Ql3    | Open loop control: third low voltage Q command, pu                                      |
| Qh1    | Open loop control: first high voltage Q command, pu                                     |
| Qh2    | Open loop control: second high voltage Q command, pu                                    |
| Qh3    | Open loop control: third high voltage Q command, pu                                     |
| pfaflg | Model Parameters\\pfaflg                                                                |
| Fn     | Fraction of WTGs in wind farm that are on-line                                          |
| Tv     | Time constant in proportional path of WindVAR emulator, sec                             |
| Tp     | Time constant in power measurement for PFA control, sec                                 |
| Ipmax  | Max. Ip command, pu                                                                     |
| Xc     | Compensating reactance for voltage control, pu                                          |
| Kqd    | Gain on Q droop function; default is zero (not implmented); typical value would be 0.04 |
| Tlpqd  | Time constant in Q droop function, sec; if implemented typical value would be 5.0       |
| Xqd    | Compensating reactance for Q droop function                                             |
| VerMn  | Minimum limit on WindControl regulated bus voltage error, pu                            |
| VerMx  | Maximum limit on WindControl regulated bus voltage error, pu                            |
| Vfrz   | Voltage threshold to freeze integrators in WindControl voltage regulator, pu            |

---

<a id="ieeet1"></a>

## IEEET1

*Source: [`Content/TransientModels_HTML/Exciter IEEET1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEET1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEET1 0001](images/Exciter_IEEET1_0001.svg)

**Parameters:**

|        |                                                       |
| ------ | ----------------------------------------------------- |
| Tr     | Transducer time constant, sec                         |
| Ka     | Voltage regulator gain                                |
| Ta     | Voltage regulator time constant, sec                  |
| Vrmax  | Maximum control element output, pu                    |
| Vrmin  | Minimum control element output, pu                    |
| Ke     | Exciter field resistance line slope margin, pu        |
| Te     | Exciter field time constant, sec                      |
| Kf     | Rate feedback gain, pu                                |
| Tf     | Rate feedback constant, sec                           |
| Switch | Parameter not used in PowerWorld                      |
| E1     | Field voltage value, 1                                |
| SE1    | Saturation factor at E1                               |
| E2     | Field voltage value, 2                                |
| SE2    | Saturation factor at E2                               |
| Spdmlt | If not zero, multiply output (Efd) by generator speed |

---

<a id="ieeet2"></a>

## IEEET2

*Source: [`Content/TransientModels_HTML/Exciter IEEET2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEET2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If 0 \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEET2 0001](images/Exciter_IEEET2_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Ka    | Voltage regulator gain                         |
| Ta    | Voltage regulator time constant, sec           |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Ke    | Exciter field resistance line slope margin, pu |
| Te    | Exciter field time constant, sec               |
| Kf    | Rate feedback gain, pu                         |
| Tf1   | Feedback lead time constant, sec               |
| Tf2   | Feedback lag time constant, sec                |
| E1    | Field voltage value, 1                         |
| SE1   | Saturation factor at E1                        |
| E2    | Field voltage value, 2                         |
| SE2   | Saturation factor at E2                        |

---

<a id="ieeet3"></a>

## IEEET3

*Source: [`Content/TransientModels_HTML/Exciter IEEET3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEET3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Kp \< 1 then Kp = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vb \<= 0 then Vb = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vbmax \> Vb, then Vbmax = Vb

Model Equations and/or Block Diagrams

![Exciter IEEET3 0001](images/Exciter_IEEET3_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Ka    | Voltage regulator gain                         |
| Ta    | Voltage regulator time constant, sec           |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Te    | Exciter field time constant, sec               |
| Kf    | Rate feedback gain, pu                         |
| Tf    | Rate feedback constant, sec                    |
| Kp    | Potential source gain, pu                      |
| Ki    | Current source gain, pu                        |
| VbMax | Maximum excitation voltage, pu                 |
| Ke    | Exciter field resistance line slope margin, pu |

---

<a id="ieeet4"></a>

## IEEET4

*Source: [`Content/TransientModels_HTML/Exciter IEEET4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEET4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Trh \< Mult\*TimeStep then Trh = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEET4 0001](images/Exciter_IEEET4_0001.svg)

**Parameters:**

|       |                                                                                                                                                                                                   |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kr    | Verr deadband. If Kr is not zero, the voltage regulator input changes at a constant rate if Verr \> Kr or Verr \< -Kr. If Kr is zero, the error signal drives the voltage regulator continuously. |
| Trh   | Rheostat time constant, sec                                                                                                                                                                       |
| Kv    | Fast raise/lower contact setting                                                                                                                                                                  |
| Vrmax | Maximum control element output, pu                                                                                                                                                                |
| Vrmin | Minimum control element output, pu                                                                                                                                                                |
| Te    | Exciter field time constant, sec                                                                                                                                                                  |
| Ke    | Exciter field resistance line slope margin, pu                                                                                                                                                    |
| E1    | Field voltage value, 1                                                                                                                                                                            |
| SE1   | Saturation factor at E1                                                                                                                                                                           |
| E2    | Field voltage value, 2                                                                                                                                                                            |
| SE2   | Saturation factor at E2                                                                                                                                                                           |

---

<a id="ieeet5"></a>

## IEEET5

*Source: [`Content/TransientModels_HTML/Exciter IEEET5.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEET5.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Trh \< Mult\*TimeStep then Trh = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEET5 0001](images/Exciter_IEEET5_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Trh   | Rheostat time constant, sec                    |
| Kv    | Fast raise/lower contact setting               |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Te    | Exciter field time constant, sec               |
| Ke    | Exciter field resistance line slope margin, pu |
| E1    | Field voltage value, 1                         |
| SE1   | Saturation factor at E1                        |
| E2    | Field voltage value, 2                         |
| SE2   | Saturation factor at E2                        |

---

<a id="ieeex1"></a>

## IEEEX1

*Source: [`Content/TransientModels_HTML/Exciter IEEEX1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEEX1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEEX1 0001](images/Exciter_IEEEX1_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Tr     | Transducer time constant, sec                  |
| Ka     | Voltage regulator gain                         |
| Ta     | Voltage regulator time constant, sec           |
| Tb     | Time constant, sec                             |
| Tc     | Time constant, sec                             |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Ke     | Exciter field resistance line slope margin, pu |
| Te     | Exciter field time constant, sec               |
| Kf     | Rate feedback gain, pu                         |
| Tf1    | Feedback lead time constant, sec               |
| Switch | Parameter not used in PowerWorld               |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| E2     | Field voltage value, 2                         |
| SE2    | Saturation factor at E2                        |

---

<a id="ieeex2"></a>

## IEEEX2

*Source: [`Content/TransientModels_HTML/Exciter IEEEX2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEEX2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If 0 \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEEX2 0001](images/Exciter_IEEEX2_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Ka    | Voltage regulator gain                         |
| Ta    | Voltage regulator time constant, sec           |
| Tb    | Time constant, sec                             |
| Tc    | Time constant, sec                             |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Ke    | Exciter field resistance line slope margin, pu |
| Te    | Exciter field time constant, sec               |
| Kf    | Rate feedback gain, pu                         |
| Tf1   | Feedback lead time constant, sec               |
| Tf2   | Feedback lag time constant, sec                |
| E1    | Field voltage value, 1                         |
| SE1   | Saturation factor at E1                        |
| E2    | Field voltage value, 2                         |
| SE2   | Saturation factor at E2                        |

---

<a id="ieeex3"></a>

## IEEEX3

*Source: [`Content/TransientModels_HTML/Exciter IEEEX3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEEX3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Kp = 0 then Kp = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEEX3 0001](images/Exciter_IEEEX3_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Ka    | Voltage regulator gain                         |
| Ta    | Voltage regulator time constant, sec           |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Te    | Exciter field time constant, sec               |
| Kf    | Rate feedback gain, pu                         |
| Tf    | Rate feedback constant, sec                    |
| Kp    | Potential source gain, pu                      |
| Ki    | Current source gain, pu                        |
| VbMax | Maximum excitation voltage, pu                 |
| Ke    | Exciter field resistance line slope margin, pu |

---

<a id="ieeex4"></a>

## IEEEX4

*Source: [`Content/TransientModels_HTML/Exciter IEEEX4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEEX4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then T1 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Trh \< Mult\*TimeStep then Trh = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEEX4 0001](images/Exciter_IEEEX4_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Trh   | Rheostat time constant, sec                    |
| Kv    | Fast raise/lower contact setting               |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Te    | Exciter field time constant, sec               |
| Ke    | Exciter field resistance line slope margin, pu |
| E1    | Field voltage value, 1                         |
| SE1   | Saturation factor at E1                        |
| E2    | Field voltage value, 2                         |
| SE2   | Saturation factor at E2                        |

---

<a id="ieet1a"></a>

## IEET1A

*Source: [`Content/TransientModels_HTML/Exciter IEET1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEET1A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEET1A 0001](images/Exciter_IEET1A_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Ka     | Voltage regulator gain                         |
| Ta     | Voltage regulator time constant, sec           |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Ke     | Exciter field resistance line slope margin, pu |
| Te     | Exciter field time constant, sec               |
| Kf     | Rate feedback gain, pu                         |
| Tf     | Rate feedback constant, sec                    |
| Efdmin | Minimum excitation output, pu                  |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| Efdmax | Maximum excitation output, pu                  |
| SE2    | Saturation factor at E2                        |

---

<a id="ieet1b"></a>

## IEET1B

*Source: [`Content/TransientModels_HTML/Exciter IEET1B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEET1B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Ta1 \< 0.5\*Mult\*TimeStep then Ta1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta1 \< Mult\*TimeStep then Ta1 = Mult\*TimeStep
  - If 0.0 \< Ta2 \< 0.5\*Mult\*TimeStep then Ta2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta1 \< Mult\*TimeStep then Ta1 = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vsmax \< Vsmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Exciter IEET1B 0001](images/Exciter_IEET1B_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Tr     | Transducer time constant, sec                  |
| Vsmax  | Vsmax                                          |
| Vsmin  | Vsmin                                          |
| Ka     | Voltage regulator gain                         |
| Ta1    | Voltage regulator time constant, sec           |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Ta2    | Voltage regulator time constant, sec           |
| KF1    | KF1                                            |
| Tf1    | Feedback lead time constant, sec               |
| Ke     | Exciter field resistance line slope margin, pu |
| Te     | Exciter field time constant, sec               |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| E2     | Field voltage value, 2                         |
| SE2    | Saturation factor at E2                        |
| Switch | 0: Feedback is Efd; 1: Feedback is Vreg        |
| Xe     | Excitation transformer effective reactance, pu |

---

<a id="ieet5a"></a>

## IEET5A

*Source: [`Content/TransientModels_HTML/Exciter IEET5A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEET5A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Trh \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Trh \< Mult\*TimeStep then Trh = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Efd \> Efdmax, then Efdmax = Efd or if Efd \< Efdmin, then Efdmin = Efd

Model Equations and/or Block Diagrams

![Exciter IEET5A 0001](images/Exciter_IEET5A_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Ka     | Voltage regulator gain                         |
| Trh    | Rheostat time constant, sec                    |
| Kv     | Fast raise/lower contact setting               |
| Vrmax  | Maximum control element output, pu             |
| Vrmin  | Minimum control element output, pu             |
| Te     | Exciter field time constant, sec               |
| Ke     | Exciter field resistance line slope margin, pu |
| E1     | Field voltage value, 1                         |
| SE1    | Saturation factor at E1                        |
| E2     | Field voltage value, 2                         |
| SE2    | Saturation factor at E2                        |
| Efdmax | Maximum excitation output, pu                  |
| Efdmin | Minimum excitation output, pu                  |

---

<a id="ieex2a"></a>

## IEEX2A

*Source: [`Content/TransientModels_HTML/Exciter IEEX2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IEEX2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter IEEX2A 0001](images/Exciter_IEEX2A_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Tr    | Transducer time constant, sec                  |
| Ka    | Voltage regulator gain                         |
| Ta    | Voltage regulator time constant, sec           |
| Tb    | Time constant, sec                             |
| Tc    | Time constant, sec                             |
| Vrmax | Maximum control element output, pu             |
| Vrmin | Minimum control element output, pu             |
| Ke    | Exciter field resistance line slope margin, pu |
| Te    | Exciter field time constant, sec               |
| Kf    | Rate feedback gain, pu                         |
| Tf1   | Feedback lead time constant, sec               |
| E1    | Field voltage value, 1                         |
| SE1   | Saturation factor at E1                        |
| E2    | Field voltage value, 2                         |
| SE2   | Saturation factor at E2                        |

---

<a id="ivoex"></a>

## IVOEX

*Source: [`Content/TransientModels_HTML/Exciter IVOEX.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter IVOEX.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If V5 \> Efdmax, then Efdmax = V5 or if V5 \< Efdmin, then Efdmin = V5
  - If V3 \> Vmax3, then Vmax3 = V3 or if V3 \< Vmin3, then Vmin3 = V3
  - If V1 \> Vmax1, then Vmax1 = V1 or if V1 \< Vmin1, then Vmin1 = V1

Model Equations and/or Block Diagrams

![Exciter IVOEX 0001](images/Exciter_IVOEX_0001.svg)

**Parameters:**

|      |                             |
| ---- | --------------------------- |
| K1   | Voltage regulator gain, pu  |
| A1   | Lead coefficient, pu        |
| A2   | Lag coefficient, pu         |
| T1   | Lead time constant, sec     |
| T2   | Lag time constant, sec      |
| Max1 | Lead-lag maxmimum limit, pu |
| Min1 | Lead-lag minimum limit, pu  |
| K3   | Voltage regulator gain, pu  |
| A3   | Lead coefficient, pu        |
| A4   | Lag coefficient, pu         |
| T3   | Lead time constant, sec     |
| T4   | Lag time constant, sec      |
| Max3 | Lead-lag maxmimum limit, pu |
| Min3 | Lead-lag minimum limit, pu  |
| K5   | Voltage regulator gain, pu  |
| A5   | Lead coefficient, pu        |
| A6   | Lag coefficient, pu         |
| T5   | Lead time constant, sec     |
| T6   | Lag time constant, sec      |
| Max5 | Lead-lag maxmimum limit, pu |
| Min5 | Lead-lag minimum limit, pu  |

---

<a id="mexs"></a>

## MEXS

*Source: [`Content/TransientModels_HTML/Exciter MEXS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter MEXS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Ka \< 0 then Ka = 1
  - If Ta \< 0 then Ta = 10

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Exciter MEXS 0001](images/Exciter_MEXS_0001.svg)

**Parameters:**

|     |                             |
| --- | --------------------------- |
| Ka  | Gain, pu                    |
| Ta  | Time Constant, sec          |
| Rex | Effective Output Resistance |

---

<a id="playinex"></a>

## PLAYINEX

*Source: [`Content/TransientModels_HTML/Exciter PLAYINEX.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter PLAYINEX.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="pv1e"></a>

## PV1E

*Source: [`Content/TransientModels_HTML/Exciter PV1E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter PV1E.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Exciter PV1E 0001](images/Exciter_PV1E_0001.svg)

**Parameters:**

|        |                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------- |
| varflg | 1 = Qord from PV plant Var controller emulator; -1 = Qord from vref; 0 = constant                 |
| Kqi    | Q control integral gain                                                                           |
| Kvi    | V control integral gain                                                                           |
| Vmax   | Maximum V at regulated bus, pu                                                                    |
| Vmin   | Minimum V at regulated bus, pu                                                                    |
| Qmax   | Maximum Q command, pu                                                                             |
| Qmin   | Minimum Q command, pu                                                                             |
| Tr     | Voltage measuremant lag, sec                                                                      |
| Tc     | Lag time constant, sec                                                                            |
| Kpv    | Regulator proportional gain                                                                       |
| Kiv    | Regulator integral gain                                                                           |
| pfaflg | 1 = regulate power factor angle; 0 = regulate Q                                                   |
| Fn     | Scaling gain                                                                                      |
| Tv     | Time constant in proportional path, sec                                                           |
| Tpwr   | Time constant in power measurment for PFA control (tp), sec                                       |
| Iphl   | Hard limit on real current, pu                                                                    |
| Iqhl   | Hard limit on reactive current, pu                                                                |
| Pqflag | 0 = Q priority; 1 = P priority                                                                    |
| Xc     | Compensating reactance for voltage control, pu                                                    |
| Kqd    | Gain on Q Droop function                                                                          |
| Tlpqd  | Time constant in Q Droop function                                                                 |
| Xqd    | Compensating reactance for Q Droop function                                                       |
| VerMn  | Minimum limit on regulated bus voltage error, pu                                                  |
| VerMx  | Maximum limit on regulated bus voltage error, pu                                                  |
| Vfrz   | Voltage threshold to freeze integrators in PV plant Var controller emulator voltage regulator, pu |
| ImaxTD | Maximum temperature dependent converter current, pu                                               |
| Viqlim | Maximum voltage dependent reactive current limit, pu                                              |

---

<a id="reec-a"></a>

## REEC_A

*Source: [`Content/TransientModels_HTML/Exciter REEC_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REEC_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Iqh \< Iql then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Q limits \> Qmax , then Qmax = Q limits or if Q limits \< Qmin , then Qmin = Q limits
  - If PIq limits \> Vmax , then Vmax = PIq limits or if PIq limits \< Vmin, then Vmin = PIq limits
  - If Pord \> Pmax , then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Model Equations and/or Block Diagrams

![Exciter REEC A 0001](images/Exciter_REEC_A_0001.svg)

**Parameters:**

|         |                                                                                                                                                                                                          |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PfFlag  | Power factor flag (1 – power factor control, 0 – Q control, which can be commanded by an external signal)                                                                                                |
| VFlag   | Voltage control flag (1 – Q control, 0 – voltage control)                                                                                                                                                |
| QFlag   | Reactive power control flag ( 1 – voltage/Q control, 0 – constant pf or Q control)                                                                                                                       |
| Pqflag  | P/Q priority selection on current limit flag. 0 = Q priority; 1 = P priority                                                                                                                             |
| Pflag   | Power Flag (1 - multiply Pref signal by gen speed wg, 0 - do not multiply)                                                                                                                               |
| Vdip    | The voltage below which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                |
| Vup     | The voltage above which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                |
| Trv     | Filter time constant for voltage measurement                                                                                                                                                             |
| dbd1    | Deadband in voltage error when voltage dip logic is activated (for overvoltage – thus overvoltage response can be disabled by setting this to a large number e.g. 999)                                   |
| dbd2    | Deadband in voltage error when voltage dip logic is activated (for undervoltage)                                                                                                                         |
| kqv     | Gain for reactive current injection during voltage dip (and overvoltage) conditions                                                                                                                      |
| Iqh1    | Maximum limit of reactive current injection (Iqinj)                                                                                                                                                      |
| Iql1    | Minimum limit of reactive current injection (Iqinj)                                                                                                                                                      |
| Vref0   | The reference voltage from which the voltage error is calculated. This is set by the user. If the user does not specify a value it is initialized by the model to equal to the initial terminal voltage. |
| Iqfrz   | Value at which Iqinj is held for Thld seconds following a voltage dip if Thld \> 0                                                                                                                       |
| Thld    | Time delay for which the state of the reactive current injection is held after voltage\_dip returns to zero.                                                                                             |
| Thld2   | Time delay for which the active current limit (Ipmax) is held after voltage\_dip returns to zero for Thld2 seconds at its value during the voltage dip.                                                  |
| Tp      | Filter time constant for electrical power measurement                                                                                                                                                    |
| Qmax    | Reactive power limit maximum                                                                                                                                                                             |
| Qmin    | Reactive power limit minimum                                                                                                                                                                             |
| Vmax    | Voltage control maximum                                                                                                                                                                                  |
| Vmin    | Voltage control minimum                                                                                                                                                                                  |
| Kqp     | Proportional gain on Q control                                                                                                                                                                           |
| Kqi     | Integral gain on Q control                                                                                                                                                                               |
| Kvp     | Proportional gain on V control                                                                                                                                                                           |
| Kvi     | Integral gain on V control                                                                                                                                                                               |
| Vref1   | User-define reference/bias on the inner-loop voltage control (default value is zero)                                                                                                                     |
| Tiq     | Time constant on lag delay                                                                                                                                                                               |
| dPmax   | Positive Ramp rate on power reference                                                                                                                                                                    |
| dPmin   | Negative Ramp rate on power reference                                                                                                                                                                    |
| Pmax    | Maximum power reference                                                                                                                                                                                  |
| Pmin    | Minimum power reference                                                                                                                                                                                  |
| Tpord   | Filter time constant on Pord                                                                                                                                                                             |
| Imax    | Maximum allowable total converter current limit                                                                                                                                                          |
| vq1     | VDL1: Voltage Point1                                                                                                                                                                                     |
| lq1     | VDL1: Iqmax Point1                                                                                                                                                                                       |
| vq2     | VDL1: Voltage Point2                                                                                                                                                                                     |
| lq2     | VDL1: Iqmax Point2                                                                                                                                                                                       |
| vq3     | VDL1: Voltage Point3                                                                                                                                                                                     |
| lq3     | VDL1: Iqmax Point3                                                                                                                                                                                       |
| vq4     | VDL1: Voltage Point4                                                                                                                                                                                     |
| lq4     | VDL1: Iqmax Point4                                                                                                                                                                                       |
| vp1     | VDL2: Voltage Point1                                                                                                                                                                                     |
| lp1     | VDL2: Ipmax Point1                                                                                                                                                                                       |
| vp2     | VDL2: Voltage Point2                                                                                                                                                                                     |
| lp2     | VDL2: Ipmax Point2                                                                                                                                                                                       |
| vp3     | VDL2: Voltage Point3                                                                                                                                                                                     |
| lp3     | VDL2: Ipmax Point3                                                                                                                                                                                       |
| vp4     | VDL2: Voltage Point4                                                                                                                                                                                     |
| lp4     | VDL2: Ipmax Point4                                                                                                                                                                                       |
| MVABase | MVABase                                                                                                                                                                                                  |

**Current Limit Logic Psuedo Code**

The following pseudo-code describes how the values for Ipmax, Ipmin, Iqmax, and Iqmin are updated.

  Voltage\_Thld2TimerActive = special boolean related to timer

  local\_V = StateVtfilter // Vt State 1

  **if** VDL1 table is empty **then** Iqmax = **1E10**

  **else** Iqmax = lookup from VL1 table using local\_V

  **if** not Voltage\_Thld2TimerActive **then begin**

   **if** VDL2 table is empty **then** Ipmax = **1E10**

   **else** Ipmax = lookup from VDL2 table using local\_V

  **end**

  **if** PQFlag = **0** **then begin** // Q priority \[default\]

    **If** Imax \< Iqmax **Then** Iqmax = IMax

      Iqmin = -Iqmax

    **if** not Voltage\_Thld2TimerActive **then begin**

      local\_I = Sqr(Imax) - Sqr(Iqcmd)

      **if** local\_I \< **0** **then** local\_I = **0**

      **else** local\_I = sqrt( local\_I )

      **if** local\_I \< Ipmax **Then** Ipmax = local\_I

    **end**

    Ipmin = **0**

  **end**

  **else** **Begin** // P priority

    **if** not Voltage\_Thld2TimerActive **then begin**

      **if** IMax \< Ipmax **Then** Ipmax = Imax

    **end**

    Ipmin = **0**

    local\_I = Sqr(Imax) - Sqr(Ipcmd)

    **if** local\_I \< 0 **then** local\_I = **0**

    **else** local\_I = sqrt( local\_I )

    **if** local\_I \< Iqmax **Then** Iqmax = local\_I

    Iqmin = -Iqmax

  **end**
