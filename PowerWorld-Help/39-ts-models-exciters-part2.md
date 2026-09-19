---
title: "TS Models — Exciters (Part 2 of 5)"
part: "Transient Models"
chapter_file: "39-ts-models-exciters-part2.md"
topics: 30
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Exciters (Part 2 of 5)

Excitation system models (IEEE types, ESST/ESAC/EXST families, REEC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (30)**

- [ESAC4A](#esac4a)
- [ESAC5A](#esac5a)
- [ESAC6A](#esac6a)
- [ESAC8B_GE](#esac8b-ge)
- [ESAC8B_PTI](#esac8b-pti)
- [ESDC1A](#esdc1a)
- [ESDC2A](#esdc2a)
- [ESDC3A](#esdc3a)
- [ESST1A](#esst1a)
- [ESST2A](#esst2a)
- [ESST3A](#esst3a)
- [ESST4B](#esst4b)
- [ESST5B](#esst5b)
- [ESST6B](#esst6b)
- [ESST7B](#esst7b)
- [ESURRY](#esurry)
- [EWTGFC](#ewtgfc)
- [EX2000](#ex2000)
- [EXAC1](#exac1)
- [EXAC1A](#exac1a)
- [EXAC2](#exac2)
- [EXAC3](#exac3)
- [EXAC3A](#exac3a)
- [EXAC4](#exac4)
- [EXAC6A](#exac6a)
- [EXAC8B](#exac8b)
- [EXBAS](#exbas)
- [EXBBC](#exbbc)
- [EXDC1](#exdc1)
- [EXDC2_GE](#exdc2-ge)

---

<a id="esac4a"></a>

## ESAC4A

*Source: [`Content/TransientModels_HTML/Exciter ESAC4A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC4A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi
  - If Vr \> (Vr-Kc\*Ifd), then Vrmax = (Vr-Kc\*Ifd) or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESAC4A 0001](images/Exciter_ESAC4A_0001.svg)

**Parameters:**

|       |                                                                |
| ----- | -------------------------------------------------------------- |
| Tr    | Filter time constant, sec                                      |
| ViMax | Maximum error, pu                                              |
| ViMin | Minimum error, pu                                              |
| Tc    | Time constant, sec                                             |
| Tb    | Time constant, sec                                             |
| Ka    | Voltage regulator gain                                         |
| Ta    | Voltage regulator time constant, sec                           |
| Vrmax | Maximum exciter control signal, pu                             |
| Vrmin | Minimum exciter control signal, pu                             |
| Kc    | Rectifier loading factor proportional to commutating reactance |

---

<a id="esac5a"></a>

## ESAC5A

*Source: [`Content/TransientModels_HTML/Exciter ESAC5A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC5A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESAC5A 0001](images/Exciter_ESAC5A_0001.svg)

**Parameters:**

|        |                                                       |
| ------ | ----------------------------------------------------- |
| Tr     | Filter time constant, sec                             |
| Ka     | Voltage regulator gain                                |
| Ta     | Voltage regulator time constant, sec                  |
| Vrmax  | Maximum exciter control signal, pu                    |
| Vrmin  | Minimum exciter control signal, pu                    |
| Ke     | Exciter field resistance constant, pu                 |
| Te     | Exciter field time constant, sec                      |
| Kf     | Rate feedback gain, pu                                |
| Tf1    | Feedback lead time constant, sec                      |
| Tf2    | Feedback lag time constant, sec                       |
| Tf3    | Feedback time constant, sec                           |
| E1     | Field voltage value, 1                                |
| SE1    | Saturation factor at E1                               |
| E2     | Field voltage value, 2                                |
| SE2    | Saturation factor at E2                               |
| Spdmlt | If not zero, multiply output (Efd) by generator speed |

---

<a id="esac6a"></a>

## ESAC6A

*Source: [`Content/TransientModels_HTML/Exciter ESAC6A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC6A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter ESAC6A 0001](images/Exciter_ESAC6A_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| Tk     | Voltage regulator time constant, sec                           |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Te     | Exciter field time constant, sec                               |
| Vfelim | Model Parameters\\Vfelim                                       |
| Kh     | Exciter field current feedback gain, pu                        |
| Vhmax  | Model Parameters\\Vhmax                                        |
| Th     | VH time constant, sec                                          |
| Tj     | VH time constant, sec                                          |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="esac8b-ge"></a>

## ESAC8B_GE

*Source: [`Content/TransientModels_HTML/Exciter ESAC8B_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC8B_GE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.
  - If Vrmax \< Vrmin then swap the values
  - If Vfedmax \< Vfedmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESAC8B GE 0001](images/Exciter_ESAC8B_GE_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Kpr    | Proportional gain, pu                                          |
| Kir    | Integral gain, pu                                              |
| Kdr    | Regulator derivative gain, pu                                  |
| Tdr    | Regulator derivative washout time constant, sec                |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| Te     | Exciter field time constant, sec                               |
| Vfemax | Exciter field current limit parameter, pu                      |
| Vemin  | Minimimum exciter output voltage, pu                           |
| Ke     | Exciter field resistance constant, pu                          |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| VTMult | If non-zero, multiply Vrmax and Vrmin by terminal voltage      |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="esac8b-pti"></a>

## ESAC8B_PTI

*Source: [`Content/TransientModels_HTML/Exciter ESAC8B_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC8B_PTI.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESAC8B PTI 0001](images/Exciter_ESAC8B_PTI_0001.svg)

**Parameters:**

|       |                                         |
| ----- | --------------------------------------- |
| Tr    | Filter time constant, sec               |
| Kpr   | Proportional gain, pu                   |
| Kir   | Integral gain, pu                       |
| Kdr   | Regulator derivative gain, pu           |
| Td    | Regulator derivative time constant, sec |
| Ka    | Voltage regulator gain                  |
| Ta    | Voltage regulator time constant, sec    |
| Vrmax | Maximum exciter control signal, pu      |
| Vrmin | Minimum exciter control signal, pu      |
| Te    | Exciter field time constant, sec        |
| Ke    | Exciter field resistance constant, pu   |
| E1    | Field voltage value, 1                  |
| SE1   | Saturation factor at E1                 |
| E2    | Field voltage value, 2                  |
| SE2   | Saturation factor at E2                 |

---

<a id="esdc1a"></a>

## ESDC1A

*Source: [`Content/TransientModels_HTML/Exciter ESDC1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESDC1A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep, elseif Tf 1\<= 0 then Tf1 = 0
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESDC1A 0001](images/Exciter_ESDC1A_0001.svg)

**Parameters:**

|        |                                                       |
| ------ | ----------------------------------------------------- |
| Tr     | Transducer time constant, sec                         |
| Ka     | Voltage regulator gain                                |
| Ta     | Voltage regulator time constant, sec                  |
| Tb     | Time constant, sec                                    |
| Tc     | Time constant, sec                                    |
| Vrmax  | Maximum control element output, pu                    |
| Vrmin  | Minimum control element output, pu                    |
| Ke     | Exciter field resistance line slope margin, pu        |
| Te     | Exciter field time constant, sec                      |
| Kf     | Rate feedback gain, pu                                |
| Tf1    | Feedback lead time constant, sec                      |
| Spdmlt | If not zero, multiply output (Efd) by generator speed |
| E1     | Field voltage value, 1                                |
| SE1    | Saturation factor at E1                               |
| E2     | Field voltage value, 2                                |
| SE2    | Saturation factor at E2                               |
| UEL    | UEL (1,2,3)                                           |
| exclim | Exciter Limitaion                                     |

---

<a id="esdc2a"></a>

## ESDC2A

*Source: [`Content/TransientModels_HTML/Exciter ESDC2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESDC2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tf1 \< Mult\*TimeStep then Tf1 = 0, else Tf1 = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESDC2A 0001](images/Exciter_ESDC2A_0001.svg)

**Parameters:**

|        |                                                       |
| ------ | ----------------------------------------------------- |
| Tr     | Transducer time constant, sec                         |
| Ka     | Voltage regulator gain                                |
| Ta     | Voltage regulator time constant, sec                  |
| Tb     | Time constant, sec                                    |
| Tc     | Time constant, sec                                    |
| Vrmax  | Maximum control element output, pu                    |
| Vrmin  | Minimum control element output, pu                    |
| Ke     | Exciter field resistance line slope margin, pu        |
| Te     | Exciter field time constant, sec                      |
| Kf     | Rate feedback gain, pu                                |
| Tf1    | Feedback lead time constant, sec                      |
| Spdmlt | If not zero, multiply output (Efd) by generator speed |
| E1     | Field voltage value, 1                                |
| SE1    | Saturation factor at E1                               |
| E2     | Field voltage value, 2                                |
| SE2    | Saturation factor at E2                               |
| UEL    | UEL (1,2,3)                                           |
| exclim | Exciter Limitaion                                     |

---

<a id="esdc3a"></a>

## ESDC3A

*Source: [`Content/TransientModels_HTML/Exciter ESDC3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESDC3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Trh \<= 0 then Trh = 0
  - If Kv \<= 0 then Kv = 0

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESDC3A 0001](images/Exciter_ESDC3A_0001.svg)

**Parameters:**

|        |                                                              |
| ------ | ------------------------------------------------------------ |
| Tr     | Filter time constant, sec.                                   |
| Trh    | Rheostat full range travel time, sec. (\> 0.)                |
| Kv     | Voltage error threshold min/max control action, p.u. (\> 0.) |
| Vrmax  | Maximum control element output, p.u.                         |
| Vrmin  | Minimum control element output, p.u.                         |
| Te     | Exciter field time constant, sec. (\> 0.)                    |
| Ke     | Exciter field resistance line slope margin p.u.              |
| E1     | Field voltage value, 1                                       |
| SE1    | Saturation factor at E1                                      |
| E2     | Field voltage value, 2                                       |
| SE2    | Saturation factor at E2                                      |
| Spdmlt | If = 1, multiply output (Efd) by generator speed             |
| exclim | If not 0, apply lower limit of 0. to exciter output          |

---

<a id="esst1a"></a>

## ESST1A

*Source: [`Content/TransientModels_HTML/Exciter ESST1A and ESST1A_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST1A and ESST1A_GE.htm)*

**AutoCorrection Properties**

**ESST1A**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If Vimax \< Vimin then swap the values

**ESST1A\_GE**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.3\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.3\*Mult\*TimeStep \< Tf \< 0.6\*Mult\*TimeStep then Tf = 0.6\*Mult\*TimeStep
  - If 0.0 \< Tb \< 0.3\*Mult\*TimeStep then Tb = 0.0  
    ElseIf 0.3\*Mult\*TimeStep \< Tb \< 0.6\*Mult\*TimeStep then Tb = 0.6\*Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.3\*Mult\*TimeStep then Tb1 = 0.0  
    ElseIf 0.3\*Mult\*TimeStep \< Tb1 \< 0.6\*Mult\*TimeStep then Tb1 = 0.6\*Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> (Vrmax- Kc\*Ifd), then Efd = (Vrmax- Kc\*Ifd) limits or if Efd\< Vrmin, then Vrmin = Efd
  - If Va \> Vamax, then Vamax = Va or if Va\< Vamin, then Vamin = Va
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi

Model Equations and/or Block Diagrams

![Exciter ESST1A and ESST1A GE 0001](images/Exciter_ESST1A_and_ESST1A_GE_0001.svg)

**Parameters for ESST1A:**

|       |                                                                               |
| ----- | ----------------------------------------------------------------------------- |
| UEL   | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| VOS   | PSS input: if = 1, add to error signal; if = 2, add after HV gate 1           |
| Tr    | Filter time constant, sec                                                     |
| ViMax | Maximum error, pu                                                             |
| ViMin | Minimum error, pu                                                             |
| Tc    | Lag time constant, sec                                                        |
| Tb    | Lead time constant, sec                                                       |
| Tc1   | Lag time constant, sec                                                        |
| Tb1   | Lead time constant, sec                                                       |
| Ka    | Gain, pu                                                                      |
| Ta    | Voltage regulator time constant, sec                                          |
| VaMax | Maximum control element output, pu                                            |
| VaMin | Minimum control element output, pu                                            |
| Vrmax | Maximum control element output, pu                                            |
| Vrmin | Minimum control element output, pu                                            |
| Kc    | Rectifier regulation factor, pu                                               |
| Kf    | Rate feedback gain, pu                                                        |
| Tf    | Rate feedback constant, sec                                                   |
| Klr   | Gain on field current limit                                                   |
| Ilr   | Maximum field current, pu                                                     |

**Parameters for ESST1A\_GE:**

|       |                                                                                  |
| ----- | -------------------------------------------------------------------------------- |
| UELin | UEL location: 0=ignore, 1=HV gate with error, 2=error; -1=HV gate with Vr output |
| PSSin | Stabilizer input location (0=voltage error, 1=regulator output)                  |
| Tr    | Filter time constant, sec                                                        |
| ViMax | Maximum error, pu                                                                |
| ViMin | Minimum error, pu                                                                |
| Tc    | Lag time constant, sec                                                           |
| Tb    | Lead time constant, sec                                                          |
| Ka    | Gain, pu                                                                         |
| Ta    | Voltage regulator time constant, sec                                             |
| Vrmax | Maximum control element output, pu                                               |
| Vrmin | Minimum control element output, pu                                               |
| Kc    | Rectifier regulation factor, pu                                                  |
| Kf    | Rate feedback gain, pu                                                           |
| Tf    | Rate feedback constant, sec                                                      |
| Tc1   | Lag time constant, sec                                                           |
| Tb1   | Lead time constant, sec                                                          |
| VaMax | Maximum control element output, pu                                               |
| VaMin | Minimum control element output, pu                                               |
| Ilr   | Maximum field current, pu                                                        |
| Klr   | Gain on field current limit                                                      |

---

<a id="esst2a"></a>

## ESST2A

*Source: [`Content/TransientModels_HTML/Exciter ESST2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Te \< 0.5\*Mult\*TimeStep then Te = 0, ElseIf 0.5\*Mult\*TimeStep \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Efd \> Efdmax, then Efdmax= Efd

Model Equations and/or Block Diagrams

![Exciter ESST2A 0001](images/Exciter_ESST2A_0001.svg)

**Parameters:**

|        |                                                                               |
| ------ | ----------------------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                                     |
| Ka     | Gain, pu                                                                      |
| Ta     | Voltage regulator time constant, sec                                          |
| Vrmax  | Maximum control element output, pu                                            |
| Vrmin  | Minimum control element output, pu                                            |
| Ke     | Exciter field resistance time constant, pu                                    |
| Te     | Exciter field time constant, sec                                              |
| Kf     | Rate feedback gain, pu                                                        |
| Tf     | Rate feedback constant, sec                                                   |
| Kp     | Potential source gain, pu                                                     |
| Ki     | Current source gain, pu                                                       |
| Kc     | Rectifier regulation factor, pu                                               |
| Efdmax | Maximum excitation output, pu                                                 |
| UEL    | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| Tb     | Lead time constant, sec                                                       |
| Tc     | Lag time constant, sec                                                        |

---

<a id="esst3a"></a>

## ESST3A

*Source: [`Content/TransientModels_HTML/Exciter ESST3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tm \< 0.5\*Mult\*TimeStep then Tm = 0, ElseIf 0.5\*Mult\*TimeStep \< Tm \< Mult\*TimeStep then Tm = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Km = 0 then Km = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values
  - If Vmmax \< Vmmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi
  - If Vm \> Vmmax, then Vmmax = Vm or if Vm \< Vmmin, then Vmmin = Vm

Model Equations and/or Block Diagrams

![Exciter ESST3A 0001](images/Exciter_ESST3A_0001.svg)

**Parameters:**

|           |                                          |
| --------- | ---------------------------------------- |
| Tr        | Filter time constant, sec                |
| ViMax     | Maximum error, pu                        |
| ViMin     | Minimum error, pu                        |
| Km        | DC converter gain                        |
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
| VgMax     | Maximum inner loop feedback voltage,, pu |
| ThetaPDeg | Phase angle of potential source, degrees |
| Tm        | Tm, sec                                  |
| VmMax     | Maximum inner loop regulator output, pu  |
| VmMin     | Minimum inner loop regulator output, pu  |

---

<a id="esst4b"></a>

## ESST4B

*Source: [`Content/TransientModels_HTML/Exciter ESST4B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST4B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - Kpm and Kim: Kpm can't be 0 if Kim = 0, if true then Kpm changed to 1.
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.
  - If Vrmax \< Vrmin then swap the values
  - If Vmmax \< Vmmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vm \> Vmmax, then Vmmax = Vm or if Vm \< Vmmin, then Vmmin = Vm

Model Equations and/or Block Diagrams

![Exciter ESST4B 0001](images/Exciter_ESST4B_0001.svg)

**Parameters:**

|           |                                                  |
| --------- | ------------------------------------------------ |
| Tr        | Filter time constant, sec                        |
| Kpr       | Proportional gain, pu                            |
| Kir       | Integral gain, pu                                |
| Vrmax     | Maximum control element output, pu               |
| Vrmin     | Minimum control element output, pu               |
| Ta        | Voltage regulator time constant, sec             |
| Kpm       | Proportional gain of field voltage regulator, pu |
| Kim       | Integral gain of field voltage regulator, pu     |
| VmMax     | Maximum inner loop regulator output, pu          |
| VmMin     | Minimum inner loop regulator output, pu          |
| Kg        | Excitation limiter gain, pu                      |
| Kp        | Potential source gain, pu                        |
| Ki        | Current source gain, pu                          |
| VbMax     | Maximum excitation voltage, pu                   |
| Kc        | Rectifier regulation factor, pu                  |
| Xl        | P-bar leakage reactance, pu                      |
| ThetaPDeg | Phase angle of potential source, degrees         |
| VgMax     | Maximum inner loop feedback gain, pu             |

---

<a id="esst5b"></a>

## ESST5B

*Source: [`Content/TransientModels_HTML/Exciter ESST5B and ST5B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST5B and ST5B.htm)*

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

![Exciter ESST5B and ST5B 0001](images/Exciter_ESST5B_and_ST5B_0001.svg)

**Parameters for ESST5B:**

|       |                                      |
| ----- | ------------------------------------ |
| Tr    | Filter time constant, sec            |
| Kr    | Regulator gain, pu                   |
| T1    | Inverse timing current constant, sec |
| Kc    | Rectifier regulation factor, pu      |
| Vrmax | Maximum control element output, pu   |
| Vrmin | Minimum control element output, pu   |
| Tc1   | Regulator lead time constant, sec    |
| Tb1   | Regulator lag time constant, sec     |
| Tc2   | Regulator lead time constant, sec    |
| Tb2   | Regulator lag time constant, sec     |
| Toc1  | OEL lead time constnat, sec.         |
| Tob1  | OEL lag time constant, sec.          |
| Toc2  | OEL lead time constnat, sec.         |
| Tob2  | OEL lag time constant, sec.          |
| Tuc1  | OEL lead time constant, sec.         |
| Tub1  | UEL lag time constant, sec.          |
| Tuc2  | OEL lead time constant, sec.         |
| Tub2  | UEL lag time constant, sec.          |

**Parameters for ST5B:**

|       |                                      |
| ----- | ------------------------------------ |
| Tr    | Filter time constant, sec            |
| Tc1   | Regulator lead time constant, sec    |
| Tb1   | Regulator lag time constant, sec     |
| Tc2   | Regulator lead time constant, sec    |
| Tb2   | Regulator lag time constant, sec     |
| Kr    | Regulator gain, pu                   |
| Vrmax | Maximum control element output, pu   |
| Vrmin | Minimum control element output, pu   |
| T1    | Inverse timing current constant, sec |
| Kc    | Rectifier regulation factor, pu      |
| Tuc1  | OEL lead time constant, sec.         |
| Tub1  | UEL lag time constant, sec.          |
| Tuc2  | OEL lead time constant, sec.         |
| Tub2  | UEL lag time constant, sec.          |
| Toc1  | OEL lead time constnat, sec.         |
| Tob1  | OEL lag time constant, sec.          |
| Toc2  | OEL lead time constnat, sec.         |
| Tob2  | OEL lag time constant, sec.          |

---

<a id="esst6b"></a>

## ESST6B

*Source: [`Content/TransientModels_HTML/Exciter ESST6B and ST6B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST6B and ST6B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tg \< 0.5\*Mult\*TimeStep then Tg = 0, ElseIf 0.5\*Mult\*TimeStep \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Ts \< 0.5\*Mult\*TimeStep then Ts = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts \< Mult\*TimeStep then Ts = Mult\*TimeStep
  - Kff and Km: (Kff + Km) can not be zero. Must be fixed.
  - If Kpa = 0 then Kpa = 1
  - If Kia = 0 then Kia = 1
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESST6B and ST6B 0001](images/Exciter_ESST6B_and_ST6B_0001.svg)

**Parameters for ESST6B:**

|        |                                                                     |
| ------ | ------------------------------------------------------------------- |
| Tr     | Filter time constant, sec.                                          |
| Kpa    | Regulator proportional gain, p.u. (\> 0.)                           |
| Kia    | Regulator integral gain, sec-1(\> 0.)                               |
| VaMax  | PI maximum output, p.u.                                             |
| VaMin  | PI minimum output, p.u.                                             |
| Kff    | Feedforward gain, p.u.                                              |
| Km     | Main gain, p.u.                                                     |
| Kg     | Feedback gain p.u.                                                  |
| Tg     | Feedback time constant, sec.                                        |
| Vrmax  | Maximum regulator output, p.u.                                      |
| Vrmin  | Minimum regulator output, p.u.                                      |
| VRMult | If non-zero, multiply regulator output by terminal voltage          |
| OEL    | OEL input selector: 1 – before UEL, 2 – after UEL, 0 – no OEL input |
| Ilr    | Field current limiter setpoint, p.u.                                |
| Kcl    | Field current limiter conversion factor                             |
| Klr    | Field current limiter gain, p.u.                                    |
| Ts     | Rectifier firing time constant, sec.                                |

**Parameters for ST6B:**

|       |                                                                     |
| ----- | ------------------------------------------------------------------- |
| OEL   | OEL input selector: 1 – before UEL, 2 – after UEL, 0 – no OEL input |
| Tr    | Filter time constant, sec.                                          |
| Kpa   | Regulator proportional gain, p.u. (\> 0.)                           |
| Kia   | Regulator integral gain, sec-1(\> 0.)                               |
| Kda   | Regulator derivative gain                                           |
| Tda   | Regulator derivative channel time constant                          |
| VaMax | PI maximum output, p.u.                                             |
| VaMin | PI minimum output, p.u.                                             |
| Kff   | Feedforward gain, p.u.                                              |
| Km    | Main gain, p.u.                                                     |
| Kcl   | Field current limiter conversion factor                             |
| Klr   | Field current limiter gain, p.u.                                    |
| Ilr   | Field current limiter setpoint, p.u.                                |
| Vrmax | Maximum regulator output, p.u.                                      |
| Vrmin | Minimum regulator output, p.u.                                      |
| Kg    | Feedback gain p.u.                                                  |
| Tg    | Feedback time constant, sec.                                        |

---

<a id="esst7b"></a>

## ESST7B

*Source: [`Content/TransientModels_HTML/Exciter ESST7B and ST7B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESST7B and ST7B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Ts \< 0.5\*Mult\*TimeStep then Ts = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts \< Mult\*TimeStep then Ts = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vmax \< Vmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vref \> Vmax, then Vmax = Vref or if Vref \< Vmin, then Vmin = Vref

Model Equations and/or Block Diagrams

![Exciter ESST7B and ST7B 0001](images/Exciter_ESST7B_and_ST7B_0001.svg)

**Parameters for ESST7B:**

|       |                                                                                              |
| ----- | -------------------------------------------------------------------------------------------- |
| Tr    | Filter time constant, sec.                                                                   |
| Kpa   | Regulator proportional gain, p.u. (\> 0.)                                                    |
| Kia   | Feedback gain, p.u.. (\> 0.)                                                                 |
| Tia   | Feedback time constant, sec..                                                                |
| Tb    | Lead-lag denominator time constant, sec.                                                     |
| Tc    | Lead-lag numerator time constant, sec.                                                       |
| Tf    | Input lead-lag denominator time constant, sec.                                               |
| Tg    | Input lead-lag numerator time constant, sec.                                                 |
| Kl    | Low-value gate feedback gain, p.u.                                                           |
| Kh    | High-value gate feedback gain, p.u.                                                          |
| Vrmax | Maximum field voltage output, p.u.                                                           |
| Vrmin | Minimum field voltage output, p.u.                                                           |
| Vmax  | Maximum voltage reference signal, p.u.                                                       |
| Vmin  | Minimum voltage reference signal, p.u.                                                       |
| UEL   | UEL input selector: 1 – add to Vref, 2 – input HV gate, 3 – output HV gate, 0 – no UEL input |
| OEL   | OEL input selector: 1 – add to Vref, 2 – input LV gate, 3 – output LV gate, 0 – no OEL input |
| Ts    | Rectifier firing time constant, sec. (not in IEEE model)                                     |

**Parameters for ST7B:**

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
| Tia   | Feedback time constant, sec.                                                                 |

---

<a id="esurry"></a>

## ESURRY

*Source: [`Content/TransientModels_HTML/Exciter ESURRY and EXAC1M.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESURRY and EXAC1M.htm)*

**AutoCorrection Properties**

**ESURRY**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If Kc \<= 0 then Kc = 0.01, if Kc \> 1 then Kc = 1
  - If Vrmax \< Vrmin then swap the values

**EXAC1M**:

Following checks and corrections are applied during Validation and AutoCorrection.

  - Same as ESURRY
  - Parameter K10 in the block diagram is K1
  - Parameter K16 in the block diagram is K2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ESURRY and EXAC1M 0001](images/Exciter_ESURRY_and_EXAC1M_0001.svg)

**Parameters for ESSURRY:**

|        |                                                       |
| ------ | ----------------------------------------------------- |
| Tr     | Transducer time constant, sec.                        |
| Ta     | Lead-lag numerator time constant, sec.                |
| Tb     | Lead-lag denominator time constant, sec.              |
| Tc     | Lead-lag numerator time constant, sec.                |
| Td     | Lead-lag denominator time constant, sec.              |
| K10    | Gain, pu                                              |
| T1     | Time constant, pu                                     |
| K16    | Gain, pu                                              |
| Kf     | Rate feedback gain, pu                                |
| Tf     | Rate feedback time constant, sec.                     |
| Vrmax  | Voltage regulator maximum output, pu                  |
| Vrmin  | Voltage regulator minimum output, pu                  |
| Te     | Exciter time constant, sec.                           |
| E1     | Field voltage value, 1                                |
| SE1    | Saturation factor at E1                               |
| E2     | Field voltage value, 2                                |
| SE2    | Saturation factor at E2                               |
| Kc     | Rectifier regulation factor, pu                       |
| Kd     | Exciter internal reactance, pu                        |
| Ke     | Exciter field resistance constant, pu                 |
| Spdmlt | If not zero, multiply output (Efd) by generator speed |

---

<a id="ewtgfc"></a>

## EWTGFC

*Source: [`Content/TransientModels_HTML/Exciter EWTGFC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EWTGFC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5Mult\*TimeStep then Tr = 0.5Mult\*TimeStep
  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tc \< 0.5\*Mult\*TimeStep then Tc = 0, ElseIf 0.5\*Mult\*TimeStep \< Tc \< Mult\*TimeStep then Tc = Mult\*TimeStep
  - If 0.0 \< Tlpdq \< Mult\*TimeStep then Tlpdq = 0, else Tlpdq = Mult\*TimeStep
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Vermx \< Vermn then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If QCord \> Qmax , then Qmax = QCord or if QCord \< Qmin , then Qmin = QCord
  - If VRef \> Vmax , then Vmax = VRef or if VRef \< Vmin, then Vmin = VRef

Model Equations and/or Block Diagrams

![Exciter EWTGFC 0001](images/Exciter_EWTGFC_0001.svg)

**Parameters:**

|        |                                                                                               |
| ------ | --------------------------------------------------------------------------------------------- |
| varflg | 1 = Qord from WindCONTROL emulation; -1 = Qord from vref (i.e., separate model); 0 = constant |
| Kqi    | Q control integral gain                                                                       |
| Kvi    | Voltage regulator integral gain                                                               |
| Vmax   | Maximum V at regulated bus, pu                                                                |
| Vmin   | Minimum V at regulated bus, pu                                                                |
| Qmax   | Maximum Q at regulated bus, pu                                                                |
| Qmin   | Minimum Q at regulated bus, pu                                                                |
| Tr     | Wind CONTROL voltage measurement lag, sec                                                     |
| Tc     | Lag between Wind CONTROL output and wind turbine, sec                                         |
| Kpv    | Wind CONTROL regulator proportional gain                                                      |
| Kiv    | Wind CONTROL regulator integral gain                                                          |
| pfaflg | 1 = regulate power factor angle; 0 = regulate Q                                               |
| Fn     | Fraction of WTGs in wind farm that are on-line                                                |
| Tv     | Time constant in proportional path of WindCONTROL emulator, sec                               |
| Tp     | Time constant in power measurement for PFA control (Tp), sec                                  |
| Iphl   | Hard limit on real current, pu                                                                |
| Iqhl   | Hard limit on rective current, pu                                                             |
| Pqflag | 0 = Q priority; 1 = P priority                                                                |
| Kdbr   | Dynamic breaking resistor gain, pu                                                            |
| Ebst   | Dynamic breaking resistor energy threshold, pu sec                                            |
| Xc     | Compensating reactance for voltage control, pu                                                |
| Kqd    | Gain on Q droop function; default is zero (not implmented); typical value would be 0.04       |
| Tlpqd  | Time constant in Q droop function, sec; if implemented typical value would be 5.0             |
| Xqd    | Compensating reactance for Q droop function                                                   |
| VerMn  | Minimum limit on Wind Control regulated bus voltage error, pu                                 |
| VerMx  | Maximum limit on Wind Control regulated bus voltage error, pu                                 |
| Vfrz   | Voltage threshold to freeze integrators in Wind Control voltage regulator, pu                 |

---

<a id="ex2000"></a>

## EX2000

*Source: [`Content/TransientModels_HTML/Exciter EX2000.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EX2000.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va
  - If RefLimP \> Vref, then RefLimP = Vref
  - If Vfemax \> Vemax, then Vfemax = Vemax

Model Equations and/or Block Diagrams

![Exciter EX2000 0001](images/Exciter_EX2000_0001.svg)

![Exciter EX2000 0002](images/Exciter_EX2000_0002.svg)

![Exciter EX2000 0003](images/Exciter_EX2000_0003.svg)

**Parameters:**

|           |                                                                |
| --------- | -------------------------------------------------------------- |
| FCL       | Field Current Limit: 0=excluded, 1=included                    |
| MinGate2  | Minimum gate 2: 0=excluded, 1=included                         |
| Kpr       | Proportional gain, pu                                          |
| Kir       | Integral gain, pu                                              |
| Vrmax     | Maximum exciter control signal, pu                             |
| Vrmin     | Minimum exciter control signal, pu                             |
| Kpa       | Amplifier proportional gain, pu                                |
| Kia       | Amplifier integral gain, pu                                    |
| VaMax     | Maximum control element output, pu                             |
| VaMin     | Minimum control element output, pu                             |
| Kp        | Potential source gain, pu                                      |
| Kl        | Exciter field current limiter gain, pu                         |
| Te        | Exciter field time constant, sec                               |
| Vfemax    | Exciter field current limit parameter, pu                      |
| Ke        | Exciter field resistance constant, pu                          |
| Kc        | Rectifier loading factor proportional to commutating reactance |
| Kd        | Exciter internal reactance, pu                                 |
| KF1       | Feedback gain KF1                                              |
| KF2       | Feedback gain KF2                                              |
| E1        | Field voltage value, 1                                         |
| SE1       | Saturation factor at E1                                        |
| E2        | Field voltage value, 2                                         |
| SE2       | Saturation factor at E2                                        |
| Kvhz      | Volt/hz gain                                                   |
| Krcc      | Volt/reactive current gain                                     |
| Tr        | Filter time constant, sec                                      |
| Ifdref1   | Field current first reference                                  |
| Ifdref2   | Field current second reference                                 |
| Ifdref3   | Field current third reference                                  |
| Ifdref4   | Field current fourth reference                                 |
| I1        | Inverse timing constant                                        |
| T1        | Inverse timing current constant, sec                           |
| I2        | Inverse timing constant                                        |
| T2        | Inverse timing current constant, sec                           |
| I3        | Inverse timing constant                                        |
| T3        | Inverse timing current constant, sec                           |
| I4        | Inverse timing constant                                        |
| T4        | Inverse timing current constant, sec                           |
| Tlead     | Field current limiter time constant                            |
| Tlag      | Field current limiter time constant                            |
| Kpifd     | Proportional gain                                              |
| Kiifd     | Integral gain                                                  |
| IfdLimP   | Maximum output                                                 |
| IfdLimN   | Minimum output                                                 |
| IfdadVlim | Advance field current limit                                    |
| Vemin     | Minimimum exciter output voltage, pu                           |
| Reflimp   | Voltage reference signal limit                                 |

---

<a id="exac1"></a>

## EXAC1

*Source: [`Content/TransientModels_HTML/Exciter EXAC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXAC1 0001](images/Exciter_EXAC1_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Te     | Exciter field time constant, sec                               |
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="exac1a"></a>

## EXAC1A

*Source: [`Content/TransientModels_HTML/Exciter EXAC1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC1A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXAC1A 0001](images/Exciter_EXAC1A_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Te     | Exciter field time constant, sec                               |
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="exac2"></a>

## EXAC2

*Source: [`Content/TransientModels_HTML/Exciter EXAC2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter EXAC2 0001](images/Exciter_EXAC2_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Kb     | Exciter field current controller gain, pu                      |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Te     | Exciter field time constant, sec                               |
| Kl     | Exciter field current limiter gain, pu                         |
| Kh     | Exciter field current feedback gain, pu                        |
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| VLr    | Maximum exciter field current, pu                              |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="exac3"></a>

## EXAC3

*Source: [`Content/TransientModels_HTML/Exciter EXAC3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Kr = 0 then Kr = Mult\*TimeStep
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter EXAC3 0001](images/Exciter_EXAC3_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Te     | Exciter field time constant, sec                               |
| Klv    | Minimum field voltage limiter gain, pu                         |
| Kr     | Field voltage feedback gain, pu                                |
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kn     | High level rate feedback gain, pu                              |
| Efdn   | Rate feedback gain break level, pu                             |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| Vlv    | Minimum excitation limit, pu                                   |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Vfemax | Exciter field current limit parameter, pu                      |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="exac3a"></a>

## EXAC3A

*Source: [`Content/TransientModels_HTML/Exciter EXAC3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Kr = 0 then Kr = Mult\*TimeStep
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter EXAC3A 0001](images/Exciter_EXAC3A_0001.svg)

**Parameters:**

Tr Filter time constant, sec

Tb Time constant, sec

Tc Time constant, sec

Ka Voltage regulator gain

Ta Voltage regulator time constant, sec

VaMax Maximum control element output, pu

VaMin Minimum control element output, pu

Te Exciter field time constant, sec

Klv Minimum field voltage limiter gain, pu

Kr Field voltage feedback gain, pu

Kf Rate feedback gain, pu

Tf Rate feedback constant, sec

Kn High level rate feedback gain, pu

Efdn Rate feedback gain break level, pu

Kc Rectifier loading factor proportional to commutating reactance

Kd Exciter internal reactance, pu

Ke Exciter field resistance constant, pu

Vlv Minimum excitation limit, pu

E1 Field voltage value, 1

SE1 Saturation factor at E1

E2 Field voltage value, 2

SE2 Saturation factor at E2

Kl1 Field current limit parameter

Kfa Field current limit parameter

---

<a id="exac4"></a>

## EXAC4

*Source: [`Content/TransientModels_HTML/Exciter EXAC4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi

Model Equations and/or Block Diagrams

![Exciter EXAC4 0001](images/Exciter_EXAC4_0001.svg)

**Parameters:**

|       |                                                                |
| ----- | -------------------------------------------------------------- |
| Tr    | Filter time constant, sec                                      |
| ViMax | Maximum error, pu                                              |
| ViMin | Minimum error, pu                                              |
| Tc    | Time constant, sec                                             |
| Tb    | Time constant, sec                                             |
| Ka    | Voltage regulator gain                                         |
| Ta    | Voltage regulator time constant, sec                           |
| Vrmax | Maximum exciter control signal, pu                             |
| Vrmin | Minimum exciter control signal, pu                             |
| Kc    | Rectifier loading factor proportional to commutating reactance |

---

<a id="exac6a"></a>

## EXAC6A

*Source: [`Content/TransientModels_HTML/Exciter EXAC6A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC6A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Th \< Mult\*TimeStep then Th = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter EXAC6A 0001](images/Exciter_EXAC6A_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Ka     | Voltage regulator gain                                         |
| Ta     | Voltage regulator time constant, sec                           |
| Tk     | Tk                                                             |
| Tb     | Time constant, sec                                             |
| Tc     | Time constant, sec                                             |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Te     | Exciter field time constant, sec                               |
| Kh     | Exciter field current feedback gain, pu                        |
| Tj     | Field current limiter time constant, sec                       |
| Th     | Field current limiter time constant, sec                       |
| Vfelim | Model Parameters\\Vfelim                                       |
| Vhmax  | Model Parameters\\Vhmax                                        |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |

---

<a id="exac8b"></a>

## EXAC8B

*Source: [`Content/TransientModels_HTML/Exciter EXAC8B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXAC8B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tvd \< 0.5\*Mult\*TimeStep then Tvd = 0, ElseIf 0.5\*Mult\*TimeStep \< Tvd \< Mult\*TimeStep then Tvd = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXAC8B 0001](images/Exciter_EXAC8B_0001.svg)

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Kvp    | Voltage regulator proportional gain                            |
| Kvi    | Voltage regulator integral gain                                |
| Kvd    | Voltage regulator derivative gain                              |
| Tvd    | Voltage regulator derivative time constant, sec                |
| ViMax  | Maximum error, pu                                              |
| Ta     | Voltage regulator time constant, sec                           |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Ke     | Exciter field resistance constant, pu                          |
| Te     | Exciter field time constant, sec                               |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Limflg | Limit flag                                                     |

---

<a id="exbas"></a>

## EXBAS

*Source: [`Content/TransientModels_HTML/Exciter EXBAS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXBAS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXBAS 0001](images/Exciter_EXBAS_0001.svg)

**Parameters:**

|       |                                     |
| ----- | ----------------------------------- |
| Tr    | Filter time constant, sec           |
| Kp    | Integral (reset) gain               |
| Ki    | Proportional gain                   |
| Ka    | Gain                                |
| Ta    | Bridge time constant, sec           |
| Tb    | Lag time constant, sec              |
| Tc    | Lead time constant, sec             |
| Vrmax | Maximum exciter control signal, pu  |
| Vrmin | Minimum exciter control signal, pu  |
| Kf    | Rate feedback gain, pu              |
| Tf    | Rate feedback constant, sec         |
| Tf1   | Feedback lead time constant, sec    |
| Tf2   | Feedback lag time constant, sec     |
| Ke    | Exciter field proportional constant |
| Te    | Exciter field time constant, sec    |
| Kc    | Rectifier regulation factor, pu     |
| Kd    | Exciter regulation factor, pu       |
| E1    | Field voltage value, 1              |
| SE1   | Saturation factor at E1             |
| E2    | Field voltage value, 2              |
| SE2   | Saturation factor at E2             |

---

<a id="exbbc"></a>

## EXBBC

*Source: [`Content/TransientModels_HTML/Exciter EXBBC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXBBC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXBBC 0001](images/Exciter_EXBBC_0001.svg)

**Parameters:**

|        |                                                |
| ------ | ---------------------------------------------- |
| Tf     | Rate feedback constant, sec                    |
| T1     | Inverse timing current constant, sec           |
| T2     | Inverse timing current constant, sec           |
| T3     | Inverse timing current constant, sec           |
| T4     | Inverse timing current constant, sec           |
| K      | Voltage regulator gain                         |
| Vrmin  | Minimum exciter control signal, pu             |
| Vrmax  | Maximum exciter control signal, pu             |
| Eefmin | Minimum exciter field voltage, pi              |
| Eefmax | Maximum exciter field voltage, pi              |
| Xe     | Excitation transformer effective reactance, pu |
| Sisig  | Supplementary signal routing switch            |

---

<a id="exdc1"></a>

## EXDC1

*Source: [`Content/TransientModels_HTML/Exciter EXDC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXDC1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXDC1 0001](images/Exciter_EXDC1_0001.svg)

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

<a id="exdc2-ge"></a>

## EXDC2_GE

*Source: [`Content/TransientModels_HTML/Exciter EXDC2_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EXDC2_GE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf1 = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Ka = 0 then Ka = 1
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EXDC2 GE 0001](images/Exciter_EXDC2_GE_0001.svg)

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
