---
title: "TS Models — Stabilizers"
part: "Transient Models"
chapter_file: "41-ts-models-stabilizers.md"
topics: 40
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Stabilizers

Power system stabilizer models (IEEEST, PSS2A/PSS4B, STAB*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (40)**

- [Stabilizer](#stabilizer)
- [All](#all)
- [IEE2ST](#iee2st)
- [IEEEST](#ieeest)
- [IVOST](#ivost)
- [PFQRG](#pfqrg)
- [PSS1A](#pss1a)
- [PSS2A](#pss2a)
- [PSS2B](#pss2b)
- [PSS2C](#pss2c)
- [PSS3B](#pss3b)
- [PSS3C](#pss3c)
- [PSS4B](#pss4b)
- [PSS4C](#pss4c)
- [PSS5C](#pss5c)
- [PSS6C](#pss6c)
- [PSS7C](#pss7c)
- [PSSSB](#psssb)
- [PSSSH](#psssh)
- [PTIST1](#ptist1)
- [PTIST3](#ptist3)
- [ST2CUT](#st2cut)
- [STAB1](#stab1)
- [STAB2A](#stab2a)
- [STAB3](#stab3)
- [STAB4](#stab4)
- [STBSVC](#stbsvc)
- [WSCCST](#wsccst)
- [WT12A1](#wt12a1)
- [WT1P_B](#wt1p-b)
- [WT2P](#wt2p)
- [WT3P](#wt3p)
- [WTGPT_A](#wtgpt-a)
- [WTGPT_B](#wtgpt-b)
- [Reactive Control](#reactive-control)
- [Stabilizers](#stabilizers)
- [Wind](#wind)
- [BPA Stabilizers](#bpa-stabilizers)
- [BPA_SF](#bpa-sf)
- [BPA_SH](#bpa-sh)

---

<a id="stabilizer"></a>

## Stabilizer

*Source: [`Content/TransientModels_HTML/Stabilizer.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/StabilizerFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/StabilizerFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="iee2st"></a>

## IEE2ST

*Source: [`Content/TransientModels_HTML/Stabilizer IEE2ST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer IEE2ST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< Mult\*TimeStep then T2 = , else T2 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.125\*Mult\*TimeStep then T6 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T6 \< 0.25\*Mult\*TimeStep then T6 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T8 \< 0.125\*Mult\*TimeStep then T8 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep T8 Tr \< 0.25\*Mult\*TimeStep then T8 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T10 \< 0.125\*Mult\*TimeStep then T10 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T10 \< 0.25\*Mult\*TimeStep then T10 = 0.25\*Mult\*TimeStep
  - If Vcl \< Vcu then swap the values
  - If Lsmax \< Lsmin then swap the values. If Lsmax \< 0 then Lsmax change sign to positive. If Lsmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer IEE2ST 0001](images/Stabilizer_IEE2ST_0001.svg)

**Parameters:**

|       |                                       |
| ----- | ------------------------------------- |
| Ics1  | First stabilizer input code           |
| Ics2  | Second stabilizer input code          |
| K1    | Gain 1                                |
| K2    | Gain 2                                |
| T1    | Lead/lag time constant, sec           |
| T2    | Lead/lag time constant, sec           |
| T3    | Lead/lag time constant, sec           |
| T4    | Lead/lag time constant, sec           |
| T5    | Lead/lag time constant, sec           |
| T6    | Lead/lag time constant, sec           |
| T7    | Lead/lag time constant, sec           |
| T8    | Lead/lag time constant, sec           |
| T9    | Lead/lag time constant, sec           |
| T10   | Lead/lag time constant, sec           |
| Lsmax | Maximum stabilizer output, pu         |
| Lsmin | Minimum stabilizer output, pu         |
| Vcu   | Stabilizer input cutoff threshold, pu |
| Vcl   | Stabilizer input cutoff threshold, pu |

---

<a id="ieeest"></a>

## IEEEST

*Source: [`Content/TransientModels_HTML/Stabilizer IEEEST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer IEEEST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T2 \< 0.125\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T2 \< 0.25\*Mult\*TimeStep then T2 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If 0 \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If Vcl \< Vcu then swap the values
  - If Lsmax \< Lsmin then swap the values. If Lsmax \< 0 then Lsmax change sign to positive. If Lsmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer IEEEST 0001](images/Stabilizer_IEEEST_0001.svg)

**Parameters:**

|        |                                        |
| ------ | -------------------------------------- |
| Ics    | Stabilizer input code                  |
| A1     | Notch filter parameters                |
| A2     | Notch filter parameters                |
| A3     | Notch filter parameters                |
| A4     | Notch filter parameters                |
| A5     | Notch filter parameters                |
| A6     | Notch filter parameters                |
| T1     | Lead/lag time constant, sec            |
| T2     | Lead/lag time constant, sec            |
| T3     | Lead/lag time constant, sec            |
| T4     | Lead/lag time constant, sec            |
| T5     | Wahsout numerator time constant, sec   |
| T6     | Washout denominator time constant, sec |
| Ks     | Stabilizer gains                       |
| Lsmax  | Maximum stabilizer output, pu          |
| Lsmin  | Minimum stabilizer output, pu          |
| Vcu    | Stabilizer input cutoff threshold, pu  |
| Vcl    | Stabilizer input cutoff threshold, pu  |
| Tdelay | Time delay, sec                        |

---

<a id="ivost"></a>

## IVOST

*Source: [`Content/TransientModels_HTML/Stabilizer IVOST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer IVOST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer IVOST 0001](images/Stabilizer_IVOST_0001.svg)

**Parameters:**

|       |                                        |
| ----- | -------------------------------------- |
| K1    | Gain 1                                 |
| A1    | Notch filter parameters                |
| A2    | Notch filter parameters                |
| T1    | Lead/lag time constant, sec            |
| T2    | Lead/lag time constant, sec            |
| VMax1 | Maximum 1                              |
| VMin1 | Minimum 1                              |
| K3    | Gain 3                                 |
| A3    | Notch filter parameters                |
| A4    | Notch filter parameters                |
| T3    | Lead/lag time constant, sec            |
| T4    | Lead/lag time constant, sec            |
| VMax3 | Maximum 3                              |
| VMin3 | Minimum 3                              |
| K5    | Gain 5                                 |
| A5    | Notch filter parameters                |
| A6    | Notch filter parameters                |
| T5    | Wahsout numerator time constant, sec   |
| T6    | Washout denominator time constant, sec |
| VMax5 | Maximum 5                              |
| VMin5 | Minimum 5                              |

---

<a id="pfqrg"></a>

## PFQRG

*Source: [`Content/TransientModels_HTML/Stabilizer PFQRG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PFQRG.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If MAX = 0 then MAX = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PFQRG 0001](images/Stabilizer_PFQRG_0001.svg)

**Parameters:**

|     |                                                        |
| --- | ------------------------------------------------------ |
| J   | Control mode: 0 for power factor; 1 for reactive power |
| Kp  | Proportional gain                                      |
| Ki  | Reset Gain                                             |
| Max | Output limit                                           |
| Ref | Reference value of reactive power or power factor      |

---

<a id="pss1a"></a>

## PSS1A

*Source: [`Content/TransientModels_HTML/Stabilizer PSS1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS1A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T2 \< 0.125\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T2 \< 0.25\*Mult\*TimeStep then T2 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If 0 \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If Vcl \< Vcu then swap the values
  - If Lsmax \< Lsmin then swap the values. If Lsmax \< 0 then Lsmax change sign to positive. If Lsmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS1A 0001](images/Stabilizer_PSS1A_0001.svg)

**Parameters:**

|       |                                        |
| ----- | -------------------------------------- |
| Ics   | Stabilizer input code                  |
| A1    | Notch filter parameters                |
| A2    | Notch filter parameters                |
| T1    | Lead/lag time constant, sec            |
| T2    | Lead/lag time constant, sec            |
| T3    | Lead/lag time constant, sec            |
| T4    | Lead/lag time constant, sec            |
| T5    | Wahsout numerator time constant, sec   |
| T6    | Washout denominator time constant, sec |
| Ks    | Stabilizer gains                       |
| Lsmax | Maximum stabilizer output, pu          |
| Lsmin | Minimum stabilizer output, pu          |
| Vcu   | Stabilizer input cutoff threshold, pu  |
| Vcl   | Stabilizer input cutoff threshold, pu  |

---

<a id="pss2a"></a>

## PSS2A

*Source: [`Content/TransientModels_HTML/Stabilizer PSS2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If 0.0 \< Tw2 \< 0.5\*Mult\*TimeStep then Tw2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0.0 \< Tw4 \< 0.5\*Mult\*TimeStep then Tw4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw4 \< Mult\*TimeStep then Tw4 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.125\*Mult\*TimeStep then T6 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T6 \< 0.25\*Mult\*TimeStep then T6 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T9 \< 0.125\*Mult\*TimeStep then T9 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T9 \< 0.25\*Mult\*TimeStep then T9 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T7 \< 0.5\*Mult\*TimeStep then T7 = 0, ElseIf 0.5\*Mult\*TimeStep \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.05\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< T2 \< 0.1\*Mult\*TimeStep then T2 = 0.1\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.05\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.05\*Mult\*TimeStep \< T4 \< 0.1\*Mult\*TimeStep then T4 = 0.1\*Mult\*TimeStep
  - If 0.0 \< Tb \< 0.125\*Mult\*TimeStep then Tb = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tb \< 0.25\*Mult\*TimeStep then Tb = 0.25\*Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS2A 0001](images/Stabilizer_PSS2A_0001.svg)

**Parameters:**

|        |                                                  |
| ------ | ------------------------------------------------ |
| Ics1   | First stabilizer input code                      |
| Ics2   | Second stabilizer input code                     |
| M      | Ramp tracking filter                             |
| N      | Ramp tracking filter                             |
| Tw1    | First washout on first remote bus, sec           |
| Tw2    | Second washout on first remote bus, sec          |
| T6     | Time constant on first remote bus, sec           |
| Tw3    | First washout on second remote bus, sec          |
| Tw4    | Second washout on second remote bus, sec         |
| T7     | Time constant on second remote bus, sec          |
| Ks2    | Gain on second remote bus                        |
| Ks3    | Gain on second remote bus                        |
| T8     | Lead of ramp tracking filter                     |
| T9     | Lag of ramp tracking filter                      |
| Ks1    | Stabilizer gain                                  |
| T1     | Lead/lag time constant, sec                      |
| T2     | Lead/lag time constant, sec                      |
| T3     | Lead/lag time constant, sec                      |
| T4     | Lead/lag time constant, sec                      |
| Vstmax | Stabilizer output maximum limit, pu              |
| Vstmin | Stabilizer output minimum limit, pu              |
| A      | Lead/lag time numerical gain (Not in IEEE model) |
| Ta     | Lead/lag time constant, sec (Not in IEEE model)  |
| Tb     | Lead/lag time constant, sec (Not in IEEE model)  |
| Ks4    | Gain on second remote bus                        |

---

<a id="pss2b"></a>

## PSS2B

*Source: [`Content/TransientModels_HTML/Stabilizer PSS2B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS2B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If 0.0 \< Tw2 \< 0.5\*Mult\*TimeStep then Tw2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0.0 \< Tw4 \< 0.5\*Mult\*TimeStep then Tw4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw4 \< Mult\*TimeStep then Tw4 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.125\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T2 \< 0.25\*Mult\*TimeStep then T2 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T11 \< 0.125\*Mult\*TimeStep then T11 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T11 \< 0.25\*Mult\*TimeStep then T11 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0.0 \< T7 \< 0.5\*Mult\*TimeStep then T7 = 0, ElseIf 0.5\*Mult\*TimeStep \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If 0.0 \< T9 \< 0.5\*Mult\*TimeStep then T9 = 0, ElseIf 0.5\*Mult\*TimeStep \< T9 \< Mult\*TimeStep then T9 = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.
  - If Vsi1max \< Vsi1min then swap the values.
  - If Vsi2max \< Vsi2min then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS2B 0001](images/Stabilizer_PSS2B_0001.svg)

**Parameters:**

|         |                                                  |
| ------- | ------------------------------------------------ |
| Ics1    | First stabilizer input code                      |
| Ics2    | Second stabilizer input code                     |
| M       | Ramp tracking filter                             |
| N       | Ramp tracking filter                             |
| Tw1     | First washout on first remote bus, sec           |
| Tw2     | Second washout on first remote bus, sec          |
| T6      | Time constant on first remote bus, sec           |
| Tw3     | First washout on second remote bus, sec          |
| Tw4     | Second washout on second remote bus, sec         |
| T7      | Time constant on second remote bus, sec          |
| Ks2     | Gain on second remote bus                        |
| Ks3     | Gain on second remote bus                        |
| T8      | Lead of ramp tracking filter                     |
| T9      | Lag of ramp tracking filter                      |
| Ks1     | Stabilizer gain                                  |
| T1      | Lead/lag time constant, sec                      |
| T2      | Lead/lag time constant, sec                      |
| T3      | Lead/lag time constant, sec                      |
| T4      | Lead/lag time constant, sec                      |
| T10     | Lead/lag time constant, sec                      |
| T11     | Lead/lag time constant, sec                      |
| Vsi1max | Stabilizer input 1 maximum limit, pu             |
| Vsi1min | Stabilizer input 1 minimum limit, pu             |
| Vsi2max | Stabilizer input 2 maximum limit, pu             |
| Vsi2min | Stabilizer input 2 minimum limit, pu             |
| Vstmax  | Stabilizer output maximum limit, pu              |
| Vstmin  | Stabilizer output minimum limit, pu              |
| A       | Lead/lag time numerical gain (Not in IEEE model) |
| Ta      | Lead/lag time constant, sec (Not in IEEE model)  |
| Tb      | Lead/lag time constant, sec (Not in IEEE model)  |
| Ks4     | Gain on second remote bus                        |

---

<a id="pss2c"></a>

## PSS2C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0 \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If 0.0 \< Tw4 \< 0.5\*Mult\*TimeStep then Tw4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw4 \< Mult\*TimeStep then Tw4 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.125\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T2 \< 0.25\*Mult\*TimeStep then T2 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T11 \< 0.125\*Mult\*TimeStep then T11 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T11 \< 0.25\*Mult\*TimeStep then T11 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T13 \< 0.125\*Mult\*TimeStep then T13 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T13 \< 0.25\*Mult\*TimeStep then T13 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0.0 \< T7 \< 0.5\*Mult\*TimeStep then T7 = 0, ElseIf 0.5\*Mult\*TimeStep \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If 0.0 \< T9 \< 0.5\*Mult\*TimeStep then T9 = 0, ElseIf 0.5\*Mult\*TimeStep \< T9 \< Mult\*TimeStep then T9 = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.
  - If Vsi1max \< Vsi1min then swap the values.
  - If Vsi2max \< Vsi2min then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS2C 0001](images/Stabilizer_PSS2C_0001.svg)

**Parameters:**

|                 |                                                                                                                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ics1            | First stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu); 7=Compensated Frequency Signal (pu) |
| Ics2            | Second stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu)                                       |
| M               | Ramp tracking filter                                                                                                                                                                                                                             |
| N               | Ramp tracking filter                                                                                                                                                                                                                             |
| Tw1             | First washout on first remote bus, sec                                                                                                                                                                                                           |
| Tw2             | Second washout on first remote bus, sec                                                                                                                                                                                                          |
| T6              | Time constant on first remote bus, sec                                                                                                                                                                                                           |
| Tw3             | First washout on second remote bus, sec                                                                                                                                                                                                          |
| Tw4             | Second washout on second remote bus, sec                                                                                                                                                                                                         |
| T7              | Time constant on second remote bus, sec                                                                                                                                                                                                          |
| Ks2             | Gain on second remote bus                                                                                                                                                                                                                        |
| Ks3             | Gain on second remote bus                                                                                                                                                                                                                        |
| T8              | Lead of ramp tracking filter                                                                                                                                                                                                                     |
| T9              | Lag of ramp tracking filter                                                                                                                                                                                                                      |
| Ks1             | Stabilizer gain                                                                                                                                                                                                                                  |
| T1              | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T2              | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T3              | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T4              | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T10             | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T11             | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| Vsi1max         | Stabilizer input 1 maximum limit, pu                                                                                                                                                                                                             |
| Vsi1min         | Stabilizer input 1 minimum limit, pu                                                                                                                                                                                                             |
| Vsi2max         | Stabilizer input 2 maximum limit, pu                                                                                                                                                                                                             |
| Vsi2min         | Stabilizer input 2 minimum limit, pu                                                                                                                                                                                                             |
| Vstmax          | Stabilizer output maximum limit, pu                                                                                                                                                                                                              |
| Vstmin          | Stabilizer output minimum limit, pu                                                                                                                                                                                                              |
| T12             | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| T13             | Lead/lag time constant, sec                                                                                                                                                                                                                      |
| PSSActivation   | Generator MW threshold for PSS activation                                                                                                                                                                                                        |
| PSSDeactivation | Generator MW threshold for PSS da-activation                                                                                                                                                                                                     |
| Tpgfilt         | Filter time constant for Pgen used in PSS output logic                                                                                                                                                                                           |
| Xcomp           | Reactance for compensated frequency calculation                                                                                                                                                                                                  |
| Tcomp           | Time constant for compensated frequency calculation                                                                                                                                                                                              |

---

<a id="pss3b"></a>

## PSS3B

*Source: [`Content/TransientModels_HTML/Stabilizer PSS3B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS3B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0.0 \< Tw3 \< 0.5\*Mult\*TimeStep then Tw3 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS3B 0001](images/Stabilizer_PSS3B_0001.svg)

**Parameters:**

|        |                                |
| ------ | ------------------------------ |
| Ics1   | First stabilizer input code    |
| Ics2   | Second stabilizer input code   |
| K1     | Signal gain                    |
| T1     | Transducter time constant, sec |
| Tw1    | Washout time constant, sec     |
| K2     | Signal gain                    |
| T2     | Transducter time constant, sec |
| Tw2    | Washout time constant, sec     |
| Tw3    | Washout time constant, sec     |
| A1     | Notch filter parameter         |
| A2     | Notch filter parameter         |
| A3     | Notch filter parameter         |
| A4     | Notch filter parameter         |
| A5     | Notch filter parameter         |
| A6     | Notch filter parameter         |
| A7     | Notch filter parameter         |
| A8     | Notch filter parameter         |
| Vstmax | Output limit, maximum          |
| Vstmin | Output limit, minimum          |

---

<a id="pss3c"></a>

## PSS3C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS3C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS3C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw2 \< Mult\*TimeStep then Tw2 = Mult\*TimeStep
  - If 0.0 \< Tw3 \< 0.5\*Mult\*TimeStep then Tw3 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS3C 0001](images/Stabilizer_PSS3C_0001.svg)

**Parameters:**

|                 |                                                                                                                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ics1            | First stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu); 7=Compensated Frequency Signal (pu) |
| Ics2            | Second stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu)                                     |
| K1              | Signal gain                                                                                                                                                                                                                                      |
| T1              | Transducter time constant, sec                                                                                                                                                                                                                   |
| Tw1             | Washout time constant, sec                                                                                                                                                                                                                       |
| K2              | Signal gain                                                                                                                                                                                                                                      |
| T2              | Transducter time constant, sec                                                                                                                                                                                                                   |
| Tw2             | Washout time constant, sec                                                                                                                                                                                                                       |
| Tw3             | Washout time constant, sec                                                                                                                                                                                                                       |
| A1              | Notch filter parameter                                                                                                                                                                                                                           |
| A2              | Notch filter parameter                                                                                                                                                                                                                           |
| A3              | Notch filter parameter                                                                                                                                                                                                                           |
| A4              | Notch filter parameter                                                                                                                                                                                                                           |
| A5              | Notch filter parameter                                                                                                                                                                                                                           |
| A6              | Notch filter parameter                                                                                                                                                                                                                           |
| A7              | Notch filter parameter                                                                                                                                                                                                                           |
| A8              | Notch filter parameter                                                                                                                                                                                                                           |
| Vstmax          | Output limit, maximum                                                                                                                                                                                                                            |
| Vstmin          | Output limit, minimum                                                                                                                                                                                                                            |
| PSSActivation   | Generator MW threshold for PSS activation                                                                                                                                                                                                        |
| PSSDeactivation | Generator MW threshold for PSS deactivation                                                                                                                                                                                                      |
| Tpgfilt         | Filter time constant for Pgen used in PSS output logic                                                                                                                                                                                           |
| Xcomp           | Reactance for compensated frequency calculation                                                                                                                                                                                                  |
| Tcomp           | Time constant for compensated frequency calculation                                                                                                                                                                                              |

---

<a id="pss4b"></a>

## PSS4B

*Source: [`Content/TransientModels_HTML/Stabilizer PSS4B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS4B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If TH \<= 0 then TH = Mult\*TimeStep

  - If A \<= 0 then A = Mult\*TimeStep

  - If KL1 \<= 0 then KL1 = Mult\*TimeStep

  - If KL2 \<= 0 then KL2 = Mult\*TimeStep

  - If KI1 \<= 0 then KI1 = Mult\*TimeStep

  - If KI2 \<= 0 then KI2 = Mult\*TimeStep

  - If KH1 \<= 0 then KH1 = Mult\*TimeStep

  - If KH2 \<= 0 then KH2 = Mult\*TimeStep

  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

  - If VLmax \< VLmin then swap the values. If VLmax \< 0 then VLmax change sign to positive. If VLmin \> 0 then change sign to negative.

  - If VImax \< VImin then swap the values. If VImax \< 0 then VImax change sign to positive. If VImin \> 0 then change sign to negative.

  - If VHmax \< VHmin then swap the values. If VHmax \< 0 then VHmax change sign to positive. If VHmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS4B 0001](images/Stabilizer_PSS4B_0001.svg)

![Stabilizer PSS4B 0002](images/Stabilizer_PSS4B_0002.svg)

**Parameters:**

|        |                                                           |
| ------ | --------------------------------------------------------- |
| CLI    | Filter parameter                                          |
| DLI    | Filter parameter                                          |
| ALI    | Filter parameter                                          |
| BLI    | Filter parameter                                          |
| BWLI1  | Notch filter parameter                                    |
| WLI1   | Notch filter parameter                                    |
| BWLI2  | Notch filter parameter                                    |
| WLI2   | Notch filter parameter                                    |
| TH     | Notch filter parameter                                    |
| AH     | Notch filter parameter                                    |
| BH     | Notch filter parameter                                    |
| M      | Ramp tracking filter                                      |
| BWH1   | Notch filter parameter                                    |
| WH1    | Notch filter parameter                                    |
| BWH2   | Notch filter parameter                                    |
| WH2    | Notch filter parameter                                    |
| KL1    | Low band differential filter gain (p.u.)                  |
| KL11   | Low band first lead-lag block coefficient (p.u.)          |
| TL1    | Low band numerator time constant (sec.)                   |
| TL2    | Low band denominator time constant (sec.)                 |
| TL3    | Low band numerator time constant (sec.)                   |
| TL4    | Low band denominator time constant (sec.)                 |
| TL5    | Low band numerator time constant (sec.)                   |
| TL6    | Low band denominator time constant (sec.)                 |
| KL2    | Low band differential filter gain (p.u.)                  |
| KL17   | Low band first lead-lag block coefficient (p.u.)          |
| TL7    | Low band numerator time constant (sec.)                   |
| TL8    | Low band denominator time constant (sec.)                 |
| TL9    | Low band numerator time constant (sec.)                   |
| TL10   | Low band denominator time constant (sec.)                 |
| TL11   | Low band numerator time constant (sec.)                   |
| TL12   | Low band denominator time constant (sec.)                 |
| KL     | Low band gain (p.u.)                                      |
| VLmax  | Low band upper limit                                      |
| VLmin  | Low band lower limit                                      |
| KI1    | Intermediate band differential filter gain (p.u.)         |
| KI11   | Intermediate band first lead-lag block coefficient (p.u.) |
| TI1    | Intermediate band numerator time constant (sec.)          |
| TI2    | Intermediate band denominator time constant (sec.)        |
| TI3    | Intermediate band numerator time constant (sec.)          |
| TI4    | Intermediate band denominator time constant (sec.)        |
| TI5    | Intermediate band numerator time constant (sec.)          |
| TI6    | Intermediate band denominator time constant (sec.)        |
| KI2    | Intermediate band differential filter gain (p.u.)         |
| KI17   | Intermediate band first lead-lag block coefficient (p.u.) |
| TI7    | Intermediate band numerator time constant (sec.)          |
| TI8    | Intermediate band denominator time constant (sec.)        |
| TI9    | Intermediate band numerator time constant (sec.)          |
| TI10   | Intermediate band denominator time constant (sec.)        |
| TI11   | Intermediate band numerator time constant (sec.)          |
| TI12   | Intermediate band denominator time constant (sec.)        |
| KI     | Intermediate band gain (p.u.)                             |
| VImax  | Intermediate band upper limit                             |
| VImin  | Intermediate band lower limit                             |
| KH1    | High band differential filter gain (p.u.)                 |
| KH11   | High band first lead-lag block coefficient (p.u.)         |
| TH1    | High band numerator time constant (sec.)                  |
| TH2    | High band denominator time constant (sec.)                |
| TH3    | High band numerator time constant (sec.)                  |
| TH4    | High band denominator time constant (sec.)                |
| TH5    | High band numerator time constant (sec.)                  |
| TH6    | High band denominator time constant (sec.)                |
| KH2    | High band differential filter gain (p.u.)                 |
| KH17   | High band first lead-lag block coefficient (p.u.)         |
| TH7    | High band numerator time constant (sec.)                  |
| TH8    | High band denominator time constant (sec.)                |
| TH9    | High band numerator time constant (sec.)                  |
| TH10   | High band denominator time constant (sec.)                |
| TH11   | High band numerator time constant (sec.)                  |
| TH12   | High band denominator time constant (sec.)                |
| KH     | High band limit                                           |
| VHmax  | High band upper limit                                     |
| VHmin  | High band lower limit                                     |
| VSTmax | Output limit, maximum                                     |
| VSTmin | Output limit, minimum                                     |

---

<a id="pss4c"></a>

## PSS4C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS4C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS4C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If TH \<= 0 then TH = Mult\*TimeStep

  - If A \<= 0 then A = Mult\*TimeStep

  - If KVL1 \<= 0 then KVL1 = Mult\*TimeStep

  - If KVL2 \<= 0 then KVL2 = Mult\*TimeStep

  - If KL1 \<= 0 then KL1 = Mult\*TimeStep

  - If KL2 \<= 0 then KL2 = Mult\*TimeStep

  - If KI1 \<= 0 then KI1 = Mult\*TimeStep

  - If KI2 \<= 0 then KI2 = Mult\*TimeStep

  - If KH1 \<= 0 then KH1 = Mult\*TimeStep

  - If KH2 \<= 0 then KH2 = Mult\*TimeStep

  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

  - If VVLmax \< VVLmin then swap the values. If VVLmax \< 0 then VVLmax change sign to positive. If VVLmin \> 0 then change sign to negative.

  - If VLmax \< VLmin then swap the values. If VLmax \< 0 then VLmax change sign to positive. If VLmin \> 0 then change sign to negative.

  - If VImax \< VImin then swap the values. If VImax \< 0 then VImax change sign to positive. If VImin \> 0 then change sign to negative.

  - If VHmax \< VHmin then swap the values. If VHmax \< 0 then VHmax change sign to positive. If VHmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS4C 0001](images/Stabilizer_PSS4C_0001.svg)

![Stabilizer PSS4C 0002](images/Stabilizer_PSS4C_0002.svg)

**Parameters:**

|        |                                                                                                |
| ------ | ---------------------------------------------------------------------------------------------- |
| CLI    | Equation parameter                                                                             |
| DLI    | Equation parameter                                                                             |
| ALI    | Equation parameter                                                                             |
| BLI    | Equation parameter                                                                             |
| BWLI1  | Notch filter parameter                                                                         |
| WLI1   | Notch filter parameter                                                                         |
| BWLI2  | Notch filter parameter                                                                         |
| WLI2   | Notch filter parameter                                                                         |
| TH     | Digital transducer parameter                                                                   |
| AH     | Digital transducer parameter                                                                   |
| BH     | Digital transducer parameter                                                                   |
| H      | H (Inertia in pu. If zero then it will take the generator transient model H and multiply by 2) |
| BWH1   | Notch filter parameter                                                                         |
| WH1    | Notch filter parameter                                                                         |
| BWH2   | Notch filter parameter                                                                         |
| WH2    | Notch filter parameter                                                                         |
| KL1    | Low band differential filter gain (p.u.)                                                       |
| KL11   | Low band first lead-lag block coefficient (p.u.)                                               |
| TL1    | Low band numerator time constant (sec.)                                                        |
| TL2    | Low band denominator time constant (sec.)                                                      |
| TL3    | Low band numerator time constant (sec.)                                                        |
| TL4    | Low band denominator time constant (sec.)                                                      |
| TL5    | Low band numerator time constant (sec.)                                                        |
| TL6    | Low band denominator time constant (sec.)                                                      |
| KL2    | Low band differential filter gain (p.u.)                                                       |
| KL17   | Low band first lead-lag block coefficient (p.u.)                                               |
| TL7    | Low band numerator time constant (sec.)                                                        |
| TL8    | Low band denominator time constant (sec.)                                                      |
| TL9    | Low band numerator time constant (sec.)                                                        |
| TL10   | Low band denominator time constant (sec.)                                                      |
| TL11   | Low band numerator time constant (sec.)                                                        |
| TL12   | Low band denominator time constant (sec.)                                                      |
| KL     | Low band gain (p.u.)                                                                           |
| VLmax  | Low band upper limit                                                                           |
| VLmin  | Low band lower limit                                                                           |
| KI1    | Intermediate band differential filter gain (p.u.)                                              |
| KI11   | Intermediate band first lead-lag block coefficient (p.u.)                                      |
| TI1    | Intermediate band numerator time constant (sec.)                                               |
| TI2    | Intermediate band denominator time constant (sec.)                                             |
| TI3    | Intermediate band numerator time constant (sec.)                                               |
| TI4    | Intermediate band denominator time constant (sec.)                                             |
| TI5    | Intermediate band numerator time constant (sec.)                                               |
| TI6    | Intermediate band denominator time constant (sec.)                                             |
| KI2    | Intermediate band differential filter gain (p.u.)                                              |
| KI17   | Intermediate band first lead-lag block coefficient (p.u.)                                      |
| TI7    | Intermediate band numerator time constant (sec.)                                               |
| TI8    | Intermediate band denominator time constant (sec.)                                             |
| TI9    | Intermediate band numerator time constant (sec.)                                               |
| TI10   | Intermediate band denominator time constant (sec.)                                             |
| TI11   | Intermediate band numerator time constant (sec.)                                               |
| TI12   | Intermediate band denominator time constant (sec.)                                             |
| KI     | Intermediate band gain (p.u.)                                                                  |
| VImax  | Intermediate band upper limit                                                                  |
| VImin  | Intermediate band lower limit                                                                  |
| KH1    | High band differential filter gain (p.u.)                                                      |
| KH11   | High band first lead-lag block coefficient (p.u.)                                              |
| TH1    | High band numerator time constant (sec.)                                                       |
| TH2    | High band denominator time constant (sec.)                                                     |
| TH3    | High band numerator time constant (sec.)                                                       |
| TH4    | High band denominator time constant (sec.)                                                     |
| TH5    | High band numerator time constant (sec.)                                                       |
| TH6    | High band denominator time constant (sec.)                                                     |
| KH2    | High band differential filter gain (p.u.)                                                      |
| KH17   | High band first lead-lag block coefficient (p.u.)                                              |
| TH7    | High band numerator time constant (sec.)                                                       |
| TH8    | High band denominator time constant (sec.)                                                     |
| TH9    | High band numerator time constant (sec.)                                                       |
| TH10   | High band denominator time constant (sec.)                                                     |
| TH11   | High band numerator time constant (sec.)                                                       |
| TH12   | High band denominator time constant (sec.)                                                     |
| KH     | High band limit                                                                                |
| VHmax  | High band upper limit                                                                          |
| VHmin  | High band lower limit                                                                          |
| VSTmax | Output limit, maximum                                                                          |
| VSTmin | Output limit, minimum                                                                          |
| KVL1   | Very Low band differential filter gain (p.u.)                                                  |
| KVL11  | Very Low band first lead-lag block coefficient (p.u.)                                          |
| TVL1   | Very Low band numerator time constant (sec.)                                                   |
| TVL2   | Very Low band denominator time constant (sec.)                                                 |
| TVL3   | Very Low band numerator time constant (sec.)                                                   |
| TVL4   | Very Low band denominator time constant (sec.)                                                 |
| TVL5   | Very Low band numerator time constant (sec.)                                                   |
| TVL6   | Very Low band denominator time constant (sec.)                                                 |
| KVL2   | Very Low band differential filter gain (p.u.)                                                  |
| KVL17  | Very Low band first lead-lag block coefficient (p.u.)                                          |
| TVL7   | Very Low band numerator time constant (sec.)                                                   |
| TVL8   | Very Low band denominator time constant (sec.)                                                 |
| TVL9   | Very Low band numerator time constant (sec.)                                                   |
| TVL10  | Very Low band denominator time constant (sec.)                                                 |
| TVL11  | Very Low band numerator time constant (sec.)                                                   |
| TVL12  | Very Low band denominator time constant (sec.)                                                 |
| KVL    | Very Low band gain (p.u.)                                                                      |
| VVLmax | Very low band upper limit                                                                      |
| VVLmin | Very low band lower limit                                                                      |

---

<a id="pss5c"></a>

## PSS5C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS5C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS5C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If FVL \<= 0 then FVL = Mult\*TimeStep

  - If FL \<= 0 then FL = Mult\*TimeStep

  - If FI \<= 0 then FI = Mult\*TimeStep

  - If FH \<= 0 then FH = Mult\*TimeStep

  - If KVL \<= 0 then KVL = Mult\*TimeStep

  - If K1 \<= 0 then K1 = Mult\*TimeStep

  - If K2 \<= 0 then K2 = Mult\*TimeStep

  - If K3 \<= 0 then K3 = Mult\*TimeStep

  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

  - If VVLmax \< VVLmin then swap the values. If VVLmax \< 0 then VVLmax change sign to positive. If VVLmin \> 0 then change sign to negative.

  - If VLmax \< VLmin then swap the values. If VLmax \< 0 then VLmax change sign to positive. If VLmin \> 0 then change sign to negative.

  - If VImax \< VImin then swap the values. If VImax \< 0 then VImax change sign to positive. If VImin \> 0 then change sign to negative.

  - If VHmax \< VHmin then swap the values. If VHmax \< 0 then VHmax change sign to positive. If VHmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS5C 0001](images/Stabilizer_PSS5C_0001.svg)

**Parameters:**

|         |                                          |
| ------- | ---------------------------------------- |
| KVL     | Very Low band gain (p.u.)                |
| FVL     | Very Low band central frequency (Hz)     |
| VVVLmax | Very Low band upper limit (p.u.)         |
| VVVLmin | Very Low band lower limit (p.u.)         |
| KL      | Low band gain (p.u.)                     |
| FL      | Low band central frequency (Hz)          |
| VLmax   | Low band upper limit                     |
| VLmin   | Low band lower limit                     |
| KI      | Intermediate band gain (p.u.)            |
| FI      | Intermediate band central frequency (Hz) |
| VImax   | Intermediate band upper limit            |
| VImin   | Intermediate band lower limit            |
| KH      | High band limit                          |
| FH      | High band central frequency (Hz)         |
| VHmax   | High band upper limit                    |
| VHmin   | High band lower limit                    |
| k1      | Gain 1                                   |
| k2      | Gain 2                                   |
| k3      | Gain 3                                   |
| Vstmax  | Maximum PSS output                       |
| Vstmin  | Minimum PSS output                       |

---

<a id="pss6c"></a>

## PSS6C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS6C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS6C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Ks \<= 0 then Ks = Mult\*TimeStep

  - If K0 \<= 0 then K0 = Mult\*TimeStep

  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

  - If Vsi1max \< Vsi1min then swap the values. If Vsi1max \< 0 then Vsi1max change sign to positive. If Vsi1min \> 0 then change sign to negative.

  - If Vsi2max \< Vsi2min then swap the values. If Vsi2max \< 0 then Vsi2max change sign to positive. If Vsi2min \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vpss \> Vstmax, then Vstmax = Vpss limits or if Vpss \< Vstmin , then Vstmin = Vpss

Model Equations and/or Block Diagrams

![Stabilizer PSS6C 0001](images/Stabilizer_PSS6C_0001.svg)

**Parameters:**

|                 |                                                                                                                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ics1            | First stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu); 7=Compensated Frequency Signal (pu) |
| Ics2            | Second stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu)                                     |
| Ks1             | PSS gain for input channel 1                                                                                                                                                                                                                     |
| T1              | PSS transducer time constant for input channel 1                                                                                                                                                                                                 |
| T3              | PSS time constant for input channel 1                                                                                                                                                                                                            |
| Ks2             | PSS gain for input channel 2                                                                                                                                                                                                                     |
| Macc            | PSS washout time constant for input channel 2                                                                                                                                                                                                    |
| T2              | PSS transducer time constant for input channel 2                                                                                                                                                                                                 |
| T4              | PSS time constant for input channel 2                                                                                                                                                                                                            |
| Td              | PSS washout time constant                                                                                                                                                                                                                        |
| K0              | PSS canoniocal gain 0                                                                                                                                                                                                                            |
| K1              | PSS canoniocal gain 1                                                                                                                                                                                                                            |
| K2              | PSS canoniocal gain 2                                                                                                                                                                                                                            |
| K3              | PSS canoniocal gain 3                                                                                                                                                                                                                            |
| K4              | PSS canoniocal gain 4                                                                                                                                                                                                                            |
| Ki3             | PSS third block gain                                                                                                                                                                                                                             |
| Ki4             | PSS fourth block gain                                                                                                                                                                                                                            |
| Ks              | PSS main gain                                                                                                                                                                                                                                    |
| Ti1             | PSS time constant in first block                                                                                                                                                                                                                 |
| Ti2             | PSS time constant in second block                                                                                                                                                                                                                |
| Ti3             | PSS time constant in third block                                                                                                                                                                                                                 |
| Ti4             | PSS time constant in fourth block                                                                                                                                                                                                                |
| Vsi1max         | Input Signal 1 maximum limit                                                                                                                                                                                                                     |
| Vsi1min         | Input Signal 1 minimum limit                                                                                                                                                                                                                     |
| Vsi2max         | Input Signal 2 maximum limit                                                                                                                                                                                                                     |
| Vsi2min         | Input Signal 2 minimum limit                                                                                                                                                                                                                     |
| VSTmax          | Maximum PSS output                                                                                                                                                                                                                               |
| VSTmin          | Minimum PSS output                                                                                                                                                                                                                               |
| PSSActivation   | Generator MW threshold for PSS activation                                                                                                                                                                                                        |
| PSSDeactivation | Generator MW threshold for PSS da-activation                                                                                                                                                                                                     |
| Tpgfilt         | Filter time constant for Pgen used in PSS output logic                                                                                                                                                                                           |
| Xcomp           | Reactance for compensated frequency calculation                                                                                                                                                                                                  |
| Tcomp           | Time constant for compensated frequency calculation                                                                                                                                                                                              |

---

<a id="pss7c"></a>

## PSS7C

*Source: [`Content/TransientModels_HTML/Stabilizer PSS7C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSS7C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Tw1 \<= 0 then Tw1 = Mult\*TimeStep
  - If Tw2 \<= 0 then Tw2 = Mult\*TimeStep
  - If Tw3 \<= 0 then Tw3 = Mult\*TimeStep
  - If Tw4 \<= 0 then Tw4 = Mult\*TimeStep
  - If Ti1 \<= 0 then Ti1 = Mult\*TimeStep
  - If Ti2 \<= 0 then Ti2 = Mult\*TimeStep
  - If Ti3 \<= 0 then Ti3 = Mult\*TimeStep
  - If Ti4 \<= 0 then Ti4 = Mult\*TimeStep
  - If K0 \<= 0 then K0 = Mult\*TimeStep
  - If Ks1 \<= 0 then Ks1 = Mult\*TimeStep
  - If Ks2 \<= 0 then Ks2 = Mult\*TimeStep
  - If 0.0 \< T9 \< 0.5\*Mult\*TimeStep then T9 = 0, ElseIf 0.5\*Mult\*TimeStep \< T9 \< Mult\*TimeStep then T9 = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.
  - If Vsi1max \< Vsi1min then swap the values.
  - If Vsi2max \< Vsi2min then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSS7C 0001](images/Stabilizer_PSS7C_0001.svg)

**Parameters:**

|                 |                                                                                                                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Ics1            | First stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu); 7=Compensated Frequency Signal (pu) |
| Ics2            | Second stabilizer input code; 1=Rotor speed deviation (pu); 2=Bus Freq Deviation (pu); 3=Gen Pelec on Machine Base (pu); 4=Gen accelerating power (pu); 5=Bus voltage (pu); 6=Derivative of Bus voltage (pu)                                     |
| M               | PSS ramp tracking filter denominator exponent                                                                                                                                                                                                    |
| N               | PSS ramp tracking filter overal exponent                                                                                                                                                                                                         |
| Ks1             | PSS main gain                                                                                                                                                                                                                                    |
| Ks2             | PSS gain                                                                                                                                                                                                                                         |
| Ks3             | PSS gain                                                                                                                                                                                                                                         |
| T6              | PSS transducer time constant for input channel 1                                                                                                                                                                                                 |
| T7              | PSS transducer time constant for input channel 2                                                                                                                                                                                                 |
| Tw1             | First washout on first remote bus, sec                                                                                                                                                                                                           |
| Tw2             | Second washout on first remote bus, sec                                                                                                                                                                                                          |
| Tw3             | First washout on second remote bus, sec                                                                                                                                                                                                          |
| Tw4             | Second washout on second remote bus, sec                                                                                                                                                                                                         |
| T8              | PSS ramp tracking filter numerator time constant                                                                                                                                                                                                 |
| T9              | PSS ramp tracking filter denominator time constant                                                                                                                                                                                               |
| K0              | PSS canoniocal gain 0                                                                                                                                                                                                                            |
| K1              | PSS canoniocal gain 1                                                                                                                                                                                                                            |
| K2              | PSS canoniocal gain 2                                                                                                                                                                                                                            |
| K3              | PSS canoniocal gain 3                                                                                                                                                                                                                            |
| K4              | PSS canoniocal gain 4                                                                                                                                                                                                                            |
| Ki3             | PSS third block gain                                                                                                                                                                                                                             |
| Ki4             | PSS fourth block gain                                                                                                                                                                                                                            |
| Ti1             | PSS time constant in first block                                                                                                                                                                                                                 |
| Ti2             | PSS time constant in second block                                                                                                                                                                                                                |
| Ti3             | PSS time constant in third block                                                                                                                                                                                                                 |
| Ti4             | PSS time constant in fourth block                                                                                                                                                                                                                |
| Vsi1max         | Input Signal 1 maximum limit                                                                                                                                                                                                                     |
| Vsi1min         | Input Signal 1 minimum limit                                                                                                                                                                                                                     |
| Vsi2max         | Input Signal 2 maximum limit                                                                                                                                                                                                                     |
| Vsi2min         | Input Signal 2 minimum limit                                                                                                                                                                                                                     |
| VSTmax          | Maximum PSS output                                                                                                                                                                                                                               |
| VSTmin          | Minimum PSS output                                                                                                                                                                                                                               |
| PSSActivation   | Generator MW threshold for PSS activation                                                                                                                                                                                                        |
| PSSDeactivation | Generator MW threshold for PSS da-activation                                                                                                                                                                                                     |
| Tpgfilt         | Filter time constant for Pgen used in PSS output logic                                                                                                                                                                                           |
| Xcomp           | Reactance for compensated frequency calculation                                                                                                                                                                                                  |
| Tcomp           | Time constant for compensated frequency calculation                                                                                                                                                                                              |

---

<a id="psssb"></a>

## PSSSB

*Source: [`Content/TransientModels_HTML/Stabilizer PSSSB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSSSB.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tw1 \< Mult\*TimeStep then Tw1 = Mult\*TimeStep
  - If 0 \< Tw3 \< Mult\*TimeStep then Tw3 = Mult\*TimeStep
  - If Vstmax \< Vstmin then swap the values. If Vstmax \< 0 then Vstmax change sign to positive. If Vstmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSSSB 0001](images/Stabilizer_PSSSB_0001.svg)

**Parameters:**

|         |                                                                      |
| ------- | -------------------------------------------------------------------- |
| Ics1    | First stabilizer input code                                          |
| Ics2    | Second stabilizer input code                                         |
| M       | Ramp tracking filter                                                 |
| N       | Ramp tracking filter                                                 |
| Tw1     | First washout on first remote bus, sec                               |
| Tw2     | Second washout on first remote bus, sec                              |
| Tw3     | First washout on second remote bus, sec                              |
| Tw4     | Second washout on second remote bus, sec                             |
| T6      | Time constant on signal 1, sec                                       |
| T7      | Time constant on signal 2, sec                                       |
| Ks2     | Gain on second remote bus                                            |
| Ks3     | Gain on second remote bus                                            |
| Ks4     | Gain on second remote bus                                            |
| T8      | Lead of ramp tracking filter, sec                                    |
| T9      | Lag of ramp tracking filter, sec                                     |
| Ks1     | Stabilizer gain                                                      |
| T1      | Lead/lag time constant, sec                                          |
| T2      | Lead/lag time constant, sec                                          |
| T3      | Lead/lag time constant, sec                                          |
| T4      | Lead/lag time constant, sec                                          |
| Vstmax  | Stabilizer output maximum limit, pu                                  |
| Vstmin  | Stabilizer output minimum limit, pu                                  |
| Sw1     | Voltage boost signal transient stabilizer manual switch              |
| Td1     | Voltage boost signal transient stabilizer lag, sec                   |
| Td2     | Voltage boost signal transient stabilizer washout time constant, sec |
| Vtl     | Voltage boost signal transient stabilizer terminal voltage limit.    |
| Vk      | Voltage boost signal transient stabilizer boost signal magnitude, pu |
| Vcutoff | Voltage deviation level for stabilizer cutout, pu                    |

---

<a id="psssh"></a>

## PSSSH

*Source: [`Content/TransientModels_HTML/Stabilizer PSSSH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PSSSH.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0 \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If Vsmax \< Vsmin then swap the values. If Vsmax \< 0 then Vsmax change sign to positive. If Vsmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PSSSH 0001](images/Stabilizer_PSSSH_0001.svg)

**Parameters:**

|       |                           |
| ----- | ------------------------- |
| K     | Main gain                 |
| K0    | Gain 0                    |
| K1    | Gain 1                    |
| K2    | Gain 2                    |
| K3    | Gain 3                    |
| K4    | Gain 4                    |
| Td    | Input time constant, sec  |
| T1    | Time constant 1, sec      |
| T2    | Time constant 2, sec      |
| T3    | Time constant 3, sec      |
| T4    | Time constant 4, sec      |
| Vsmax | Maximum output signal, pu |
| Vsmin | Minimum output signal, pu |

---

<a id="ptist1"></a>

## PTIST1

*Source: [`Content/TransientModels_HTML/Stabilizer PTIST1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PTIST1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PTIST1 0001](images/Stabilizer_PTIST1_0001.svg)

**Parameters:**

|         |                                                                                                                                                                                                                                                                     |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DeltaTf | Delta time constant, sec                                                                                                                                                                                                                                            |
| DeltaTp | Delta time constant, sec                                                                                                                                                                                                                                            |
| DeltaTc | Delta time constant, sec                                                                                                                                                                                                                                            |
| Xq      | Terminal Voltage and Current of the generator along with the parameter Xq are used to estimate the complex internal voltage of the generator. The angle of this internal voltage is then taken, and a derivative of this angle is used to estimate the rotor speed. |
| M       | Time constant, sec                                                                                                                                                                                                                                                  |
| Tp      | Time constant, sec                                                                                                                                                                                                                                                  |
| Tf      | Time constant, sec                                                                                                                                                                                                                                                  |
| K       | Gain                                                                                                                                                                                                                                                                |
| T1      | Time constant 1, sec                                                                                                                                                                                                                                                |
| T2      | Time constant 2, sec                                                                                                                                                                                                                                                |
| T3      | Time constant 3, sec                                                                                                                                                                                                                                                |
| T4      | Time constant 4, sec                                                                                                                                                                                                                                                |

---

<a id="ptist3"></a>

## PTIST3

*Source: [`Content/TransientModels_HTML/Stabilizer PTIST3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer PTIST3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - NCL: Warning because PowerWorld has not implemented the Limit Function of this stabilizer. The limit function will be ignored.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer PTIST3 0001](images/Stabilizer_PTIST3_0001.svg)

**Parameters:**

|         |                                                                |
| ------- | -------------------------------------------------------------- |
| ISW     | Digital/analog output switch (ISW = 0 or 1)                    |
| NAV     | Number of control outputs to average (1 ≤ NAV ≤ 16)            |
| NCL     | Number of counts at limit to active limit function (NCL \> 0)  |
| NCR     | Number of counts until reset after limit function is triggered |
| DeltaTf | Delta time constant, sec                                       |
| DeltaTp | Delta time constant, sec                                       |
| DeltaTc | Delta time constant, sec                                       |
| Xqp     | Parameter Xqp                                                  |
| M       | Ramp tracking filter                                           |
| Tp      | Time constant, sec                                             |
| Tf      | Time constant, sec                                             |
| K       | Gain                                                           |
| T1      | Lead/lag time constant, sec                                    |
| T2      | Lead/lag time constant, sec                                    |
| T3      | Lead/lag time constant, sec                                    |
| T4      | Lead/lag time constant, sec                                    |
| T5      | Wahsout numerator time constant, sec                           |
| T6      | Washout denominator time constant, sec                         |
| A0      | Lead/lag time numerical gain (Not in IEEE model)               |
| A1      | Notch filter parameters                                        |
| A2      | Notch filter parameters                                        |
| B0      | Lead/lag time numerical gain (Not in IEEE model)               |
| B1      | Notch filter parameters                                        |
| B2      | Notch filter parameters                                        |
| A3      | Notch filter parameters                                        |
| A4      | Notch filter parameters                                        |
| A5      | Notch filter parameters                                        |
| B3      | Notch filter parameters                                        |
| B4      | Notch filter parameters                                        |
| B5      | Notch filter parameters                                        |
| Athres  | Average threshold                                              |
| DL      | Signal limit                                                   |
| AL      | Signal limit                                                   |
| Lthres  | Linit threshold                                                |
| Pmin    | Minimum Power                                                  |

---

<a id="st2cut"></a>

## ST2CUT

*Source: [`Content/TransientModels_HTML/Stabilizer ST2CUT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer ST2CUT.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T6 \< 0.5\*Mult\*TimeStep then T6 = 0, ElseIf 0.5\*Mult\*TimeStep \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0.0 \< T8 \< 0.5\*Mult\*TimeStep then T8 = 0, ElseIf 0.5\*Mult\*TimeStep \< T8 \< Mult\*TimeStep then T8 = Mult\*TimeStep
  - If 0.0 \< T10 \< 0.5\*Mult\*TimeStep then T10 = 0, ElseIf 0.5\*Mult\*TimeStep \< T10 \< Mult\*TimeStep then T10 = Mult\*TimeStep
  - If Lsmax \< Lsmin then swap the values. If Lsmax \< 0 then Lsmax change sign to positive. If Lsmin \> 0 then change sign to negative.
  - If Vcu \< Vcl then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer ST2CUT 0001](images/Stabilizer_ST2CUT_0001.svg)

**Parameters:**

|       |                                                                                                                                                                                                                                                               |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IC1   | First stabilizer input code (for Remote Input); 1 - Rotor speed diviation (pu); 2 - Bus frequency deviation (pu); 3 - Generator electrical power on MBASE base (pu); 4 - Generator accelerating power (pu); 5 - Bus voltage; 6 - Derivative of pu bus voltage |
| IC2   | Second stabilizer input code                                                                                                                                                                                                                                  |
| K1    | Gain 1                                                                                                                                                                                                                                                        |
| K2    | Gain 2                                                                                                                                                                                                                                                        |
| T1    | Time constant, sec                                                                                                                                                                                                                                            |
| T2    | Time constant, sec                                                                                                                                                                                                                                            |
| T3    | Time constant, sec                                                                                                                                                                                                                                            |
| T4    | Time constant, sec                                                                                                                                                                                                                                            |
| T5    | Time constant, sec                                                                                                                                                                                                                                            |
| T6    | Time constant, sec                                                                                                                                                                                                                                            |
| T7    | Time constant, sec                                                                                                                                                                                                                                            |
| T8    | Time constant, sec                                                                                                                                                                                                                                            |
| T9    | Time constant, sec                                                                                                                                                                                                                                            |
| T10   | Time constant, sec                                                                                                                                                                                                                                            |
| Lsmax | Maximum stabilizer output, pu                                                                                                                                                                                                                                 |
| Lsmin | Minimum stabilizer output, pu                                                                                                                                                                                                                                 |
| Vcu   | Stabilizer input cutoff threshold, pu                                                                                                                                                                                                                         |
| Vcl   | Stabilizer input cutoff threshold, pu                                                                                                                                                                                                                         |

---

<a id="stab1"></a>

## STAB1

*Source: [`Content/TransientModels_HTML/Stabilizer STAB1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer STAB1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - If 0.0 \< T3 \< 0.125\*Mult\*TimeStep then T3 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T3 \< 0.25\*Mult\*TimeStep then T3 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If HLim \< 0 then HLim change sign to positive.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer STAB1 0001](images/Stabilizer_STAB1_0001.svg)

**Parameters:**

|        |                             |
| ------ | --------------------------- |
| K\_T   | K/T ratio                   |
| T      | Time constant, sec          |
| T1\_T3 | T1/T3 ratio                 |
| T3     | Lead/lag time constant, sec |
| T2\_T4 | T2/T4 ratio                 |
| T4     | Lead/lag time constant, sec |
| Hlim   | Limit                       |

---

<a id="stab2a"></a>

## STAB2A

*Source: [`Content/TransientModels_HTML/Stabilizer STAB2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer STAB2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If HLim \< 0 then HLim change sign to positive.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer STAB2A 0001](images/Stabilizer_STAB2A_0001.svg)

**Parameters:**

|      |                    |
| ---- | ------------------ |
| K2   | Gain 2             |
| T2   | Time constant, sec |
| K3   | Gain 3             |
| T3   | Time constant, sec |
| K4   | Gain 4             |
| K5   | Gain 5             |
| T5   | Time constant, sec |
| Hlim | Limit              |

---

<a id="stab3"></a>

## STAB3

*Source: [`Content/TransientModels_HTML/Stabilizer STAB3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer STAB3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tx1 \< Mult\*TimeStep then Tx1 = Mult\*TimeStep
  - If 0 \< Tx2 \< Mult\*TimeStep then Tx2 = Mult\*TimeStep
  - If 0.0 \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0, ElseIf 0.5\*Mult\*TimeStep \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If Kx = 0 then Kx = Mult\*TimeStep
  - If VLim \< 0 then VLim change sign to positive.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer STAB3 0001](images/Stabilizer_STAB3_0001.svg)

**Parameters:**

|      |                    |
| ---- | ------------------ |
| Tt   | Time constant, sec |
| Tx1  | Time constant, sec |
| Tx2  | Time constant, sec |
| Kx   | Gain               |
| Vlim | Limit              |

---

<a id="stab4"></a>

## STAB4

*Source: [`Content/TransientModels_HTML/Stabilizer STAB4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer STAB4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tx1 \< Mult\*TimeStep then Tx1 = Mult\*TimeStep
  - If 0 \< Tx2 \< Mult\*TimeStep then Tx2 = Mult\*TimeStep
  - If 0.0 \< Tc \< 0.125\*Mult\*TimeStep then Tc = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tc \< 0.25\*Mult\*TimeStep then Tc = 0.25\*Mult\*TimeStep
  - If 0.0 \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0, ElseIf 0.5\*Mult\*TimeStep \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If 0.0 \< Td \< 0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Te \< 0.5\*Mult\*TimeStep then Te = 0, ElseIf 0.5\*Mult\*TimeStep \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If L2 \< L1 then swap the values. If L2 \< 0 then L2 change sign to positive. If L1 \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer STAB4 0001](images/Stabilizer_STAB4_0001.svg)

**Parameters:**

|     |                                    |
| --- | ---------------------------------- |
| Kx  | Gain                               |
| Tt  | Watt transducer time constant, sec |
| Tx1 | Time constant, sec                 |
| Tx2 | Time constant, sec                 |
| Ta  | Time constant, sec                 |
| Tb  | Time constant, sec                 |
| Tc  | Time constant, sec                 |
| Td  | Time constant, sec                 |
| Te  | Time constant, sec                 |
| L1  | L1 (pu) low limit                  |
| L2  | L2 (pu) high limit                 |

---

<a id="stbsvc"></a>

## STBSVC

*Source: [`Content/TransientModels_HTML/Stabilizer STBSVC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer STBSVC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Ks1 \< Mult\*TimeStep then Ks1 = Mult\*TimeStep
  - If 0 \< Ks2 \< Mult\*TimeStep then Ks2 = Mult\*TimeStep
  - If 0 \< T9 \< Mult\*TimeStep then T9 = Mult\*TimeStep
  - If 0 \< T12 \< Mult\*TimeStep then T12 = Mult\*TimeStep
  - If 0 \< T14 \< Mult\*TimeStep then T14 = Mult\*TimeStep
  - If 0.0 \< T7 \< 0.5\*Mult\*TimeStep then T7 = 0, ElseIf 0.5\*Mult\*TimeStep \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If 0.0 \< T10 \< 0.5\*Mult\*TimeStep then T10 = 0, ElseIf 0.5\*Mult\*TimeStep \< T10 \< Mult\*TimeStep then T10 = Mult\*TimeStep
  - If Vscs = 0 then Vscs = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer STBSVC 0001](images/Stabilizer_STBSVC_0001.svg)

**Parameters:**

|      |                                                                                                                                                                   |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IC1  | First stabilizer input code; 1 - Accelerating power from remote machine (pu); 2 - Electrical power from branch (pu); 3 - Frequency deviation from remote bus (pu) |
| IC2  | Second stabilizer input code; 0 - No signal bus; 1 - Bus voltage (pu); 2 - VARS from SVC to system (pu); 3 - Current from SVC to system (pu)                      |
| Ks1  | Gain 1                                                                                                                                                            |
| Ts7  | Time constant, sec                                                                                                                                                |
| Ts8  | Time constant, sec                                                                                                                                                |
| Ts9  | Time constant, sec                                                                                                                                                |
| Ts13 | Time constant, sec                                                                                                                                                |
| Ts14 | Time constant, sec                                                                                                                                                |
| Ks3  | Gain 3                                                                                                                                                            |
| Vscs | Limit                                                                                                                                                             |
| Ks2  | Gain 2                                                                                                                                                            |
| Ts10 | Time constant, sec                                                                                                                                                |
| Ts11 | Time constant, sec                                                                                                                                                |
| Ts12 | Time constant, sec                                                                                                                                                |

---

<a id="wsccst"></a>

## WSCCST

*Source: [`Content/TransientModels_HTML/Stabilizer WSCCST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WSCCST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tq \< 0.5\*Mult\*TimeStep then Tq = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tq1 \< 0.5\*Mult\*TimeStep then Tq1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tq1 \< Mult\*TimeStep then Tq1 = Mult\*TimeStep
  - If 0.0 \< Tq2 \< 0.5\*Mult\*TimeStep then Tq2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tq2 \< Mult\*TimeStep then Tq2 = Mult\*TimeStep
  - If 0.0 \< Tq3 \< 0.5\*Mult\*TimeStep then Tq3 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tq3 \< Mult\*TimeStep then Tq3 = Mult\*TimeStep
  - If 0.0 \< Tqs \< 0.125\*Mult\*TimeStep then Tqs = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tqs \< 0.25\*Mult\*TimeStep then Tqs = 0.25\*Mult\*TimeStep
  - If 0.0 \< Tqv \< Mult\*TimeStep then Tqv = 0, else Tqv = Mult\*TimeStep
  - If Vsmax \< Vslow then swap the values. If Vsmax \< 0 then Vsmax change sign to positive. If Vslow \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer WSCCST 0001](images/Stabilizer_WSCCST_0001.svg)

**Parameters:**

|         |                                                                                     |
| ------- | ----------------------------------------------------------------------------------- |
| Ics     | Input signal code; 1 for shaft speed; 2 for accelerating power; 3 for bus frequency |
| Kqv     | Voltage deviation gain                                                              |
| Tqv     | Voltage transducer time constan, sec                                                |
| Kqs     | Main input signal gain                                                              |
| Tqs     | Main input signal transducer time constant, sec                                     |
| Tq      | Stabilizer washout time constant, sec                                               |
| Tq1     | Lag time constant, sec                                                              |
| Tpq1    | Lead time constant, sec                                                             |
| Tq2     | Lag time constant, sec                                                              |
| Tpq2    | Lead time constant, sec                                                             |
| Tq3     | Lag time constant, sec                                                              |
| Tpq3    | Lead time constant, sec                                                             |
| Vsmax   | Maximum output signal, pu                                                           |
| Vcutoff | Voltage deviation level for stabilizer cutout, pu                                   |
| Vslow   | Minimum output signal, sec                                                          |
| T1      | Frequency boost signal transient stabilizer lag, sec                                |
| T2      | Frequency boost signal transient stabilizer washout time constant, sec              |
| T3      | Frequency boost signal transient stabilizer trigger washout time constant, sec      |
| Kboost  | Transient stabilizer boost signal, pu                                               |
| Dw1     | Speed deviation 1 for trigger, pu                                                   |
| Dw2     | Speed deviation 2 for trigger, pu                                                   |
| Ddwt    | Acceleration value for trigger, pu                                                  |
| Tdelay  | Trigger delay, sec                                                                  |
| T4      | Frequency boost signal transient stabilizer trigger circuit lag, sec                |
| Sw1     | Voltage boost signal transient stabilizer manual switch                             |
| Td1     | Voltage boost signal transient stabilizer lag, sec                                  |
| Td2     | Voltage boost signal transient stabilizer washout time constant, sec                |
| Vtl     | Voltage boost signal transient stabilizer terminal voltage limit                    |
| Vk      | Voltage boost signal transient stabilizer boost signal magnitude, pu                |

---

<a id="wt12a1"></a>

## WT12A1

*Source: [`Content/TransientModels_HTML/Stabilizer WT12A1 and WT1P.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WT12A1 and WT1P.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tpe \< 0.5\*Mult\*TimeStep then Tpe = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpe \< Mult\*TimeStep then Tpe = Mult\*TimeStep
  - If 0.0 \< T1 \< 0.5\*Mult\*TimeStep then T1 = 0, ElseIf 0.5\*Mult\*TimeStep \< T1 \< Mult\*TimeStep then T1 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - For WT12A1: If 0 \< Ti \< 0.5\*Mult\*TimeStep then Ti = 0.5\*Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer WT12A1 and WT1P 0001](images/Stabilizer_WT12A1_and_WT1P_0001.svg)

**Parameters for WT12A1:**

|        |                             |
| ------ | --------------------------- |
| Kdroop | Droop gain                  |
| Kp     | PI proportional gain        |
| Ti     | Integrator time constant    |
| T1     | Lead/lag time constant, sec |
| T2     | Lead/lag time constant, sec |
| Tpe    | Time constant, sec          |
| Pimax  | Maximum pitch, deg          |
| Pimin  | Minimum pitch, deg          |

**Parametersfor WT1P:**

|        |                             |
| ------ | --------------------------- |
| Tpe    | Time constant, sec          |
| Kdroop | Droop gain                  |
| Kp     | PI proportional gain        |
| Ki     | PI integral gain            |
| Pimax  | Maximum pitch, deg          |
| Pimin  | Minimum pitch, deg          |
| T1     | Lead/lag time constant, sec |
| T2     | Lead/lag time constant, sec |
| Kw     | Speed gain, pu              |

---

<a id="wt1p-b"></a>

## WT1P_B

*Source: [`Content/TransientModels_HTML/Stabilizer WT1P_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WT1P_B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer WT1P B 0001](images/Stabilizer_WT1P_B_0001.svg)

**Parameters:**

|      |                                        |
| ---- | -------------------------------------- |
| Tr   | Voltage transducer time constant, sec. |
| Rmax | Rate limit for increasing power pu/sec |
| Rmin | Rate limit for decreasing power pu/sec |
| T    | lag time constant, sec                 |
| Pmin | Minimum power setting, pu              |
| Pset | Power setpoint, pu                     |
| Vt1  | Voltage point 1, pu                    |
| T1   | Time point 1, sec                      |
| Vt2  | Voltage point 2, pu                    |
| T2   | Time point 2, sec                      |
| Vt3  | Voltage point 3, pu                    |
| T3   | Time point 3, sec                      |
| Vt4  | Voltage point 4, pu                    |
| T4   | Time point 4, sec                      |

---

<a id="wt2p"></a>

## WT2P

*Source: [`Content/TransientModels_HTML/Stabilizer WT2P.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WT2P.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Stabilizer WT2P 0001](images/Stabilizer_WT2P_0001.svg)

**Parameters:**

|        |                             |
| ------ | --------------------------- |
| Tpe    | Time constant, sec          |
| Kdroop | Droop gain                  |
| Kp     | PI proportional gain        |
| Ki     | PI integral gain            |
| Pimax  | Maximum pitch, deg          |
| Pimin  | Minimum pitch, deg          |
| T1     | Lead/lag time constant, sec |
| T2     | Lead/lag time constant, sec |
| Kw     | Speed gain, pu              |

---

<a id="wt3p"></a>

## WT3P

*Source: [`Content/TransientModels_HTML/Stabilizer WT3P and WT3P1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WT3P and WT3P1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Stabilizer WT3P and WT3P1 0001](images/Stabilizer_WT3P_and_WT3P1_0001.svg)

**Parameters for WT3P:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Kpp   | Pitch control porportional gain, deg/pu-speed  |
| Kip   | Pitch control integral gain, deg/pu speed-sec  |
| Kpc   | Pitch compensator proportional gain, deg./pu P |
| Kic   | Pitch compensator integral gain, deg/pu P-sec  |
| Pimax | Maximum pitch, deg                             |
| Pimin | Minimum pitch, deg                             |
| Pirat | Pitch rate limit, deg/sec                      |
| Tpi   | Blade response time constant, sec              |
| Pset  | Power setpoint, pu                             |

**Parametersfor WT3P1:**

|           |                                                |
| --------- | ---------------------------------------------- |
| Tp        | Blade response time constant, sec              |
| Kpp       | Pitch control porportional gain, deg/pu-speed  |
| Kip       | Pitch control integral gain, deg/pu speed-sec  |
| Kpc       | Pitch compensator proportional gain, deg./pu P |
| Kic       | Pitch compensator integral gain, deg/pu P-sec  |
| ThetaMin  | Minimum pitch, deg                             |
| ThetaMax  | Maximum pitch, deg                             |
| RThetaMax | Pitch rate limit, deg/sec                      |
| Pset      | Power setpoint, pu                             |

---

<a id="wtgpt-a"></a>

## WTGPT_A

*Source: [`Content/TransientModels_HTML/Stabilizer WTGPT_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WTGPT_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If RThetaMax \< RThetaMin then swap the values. If RThetaMax \< 0 then RThetaMax change sign to positive. If RThetaMin \> 0 then change sign to negative.
  - If ThetaMax \< ThetaMin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer WTGPT A 0001](images/Stabilizer_WTGPT_A_0001.svg)

**Parameters for WTGPT\_A:**

|           |                                                |
| --------- | ---------------------------------------------- |
| Tp        | Blade response time constant, sec              |
| Kpp       | Pitch control porportional gain, deg/pu-speed  |
| Kip       | Pitch control integral gain, deg/pu speed-sec  |
| Kpc       | Pitch compensator proportional gain, deg./pu P |
| Kic       | Pitch compensator integral gain, deg/pu P-sec  |
| ThetaMin  | Minimum pitch, deg                             |
| ThetaMax  | Maximum pitch, deg                             |
| RThetaMin | Pitch rate limit negative, deg/sec             |
| RThetaMax | Pitch rate limit, deg/sec                      |
| Kcc       | Cross Proportional Gain                        |
| MVABase   | MVABase: MVABase for the object parameters     |

**Parameters for WTPTA1:**

|           |                                                |
| --------- | ---------------------------------------------- |
| Kiw       | Pitch control integral gain, deg/pu speed-sec  |
| Kpw       | Pitch control porportional gain, deg/pu-speed  |
| Kic       | Pitch compensator integral gain, deg/pu P-sec  |
| Kpc       | Pitch compensator proportional gain, deg./pu P |
| Kcc       | Cross Proportional Gain                        |
| Tp        | Blade response time constant, sec              |
| ThetaMax  | Maximum pitch, deg                             |
| ThetaMin  | Minimum pitch, deg                             |
| RThetaMax | Pitch rate limit, deg/sec                      |
| RThetaMin | Pitch rate limit negative, deg/sec             |

---

<a id="wtgpt-b"></a>

## WTGPT_B

*Source: [`Content/TransientModels_HTML/Stabilizer WTGPT_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer WTGPT_B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If RThetaMax \< RThetaMin then swap the values. If RThetaMax \< 0 then RThetaMax change sign to positive. If RThetaMin \> 0 then change sign to negative.
  - If ThetaMax \< ThetaMin then swap the values.
  - If ThetaWMax \< ThetaWMin then swap the values.
  - If ThetaCMax \< ThetaCMin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Stabilizer WTGPT B 0001](images/Stabilizer_WTGPT_B_0001.svg)

**Parameters:**

|           |                                                          |
| --------- | -------------------------------------------------------- |
| Tp        | Blade response time constant, sec                        |
| Kpp       | Pitch control porportional gain, deg/pu-speed            |
| Kip       | Pitch control integral gain, deg/pu speed-sec            |
| Kpc       | Pitch compensator proportional gain, deg./pu P           |
| Kic       | Pitch compensator integral gain, deg/pu P-sec            |
| ThetaMin  | Minimum pitch, deg                                       |
| ThetaMax  | Maximum pitch, deg                                       |
| RThetaMin | Pitch rate limit negative, deg/sec                       |
| RThetaMax | Pitch rate limit, deg/sec                                |
| Kcc       | Cross Proportional Gain                                  |
| MVABase   | MVABase: MVABase for the object parameters               |
| ThetaWMin | Minimum output of the speed error controller, deg        |
| ThetaWMax | Maximum output of the speed error controller, deg        |
| ThetaCMin | Minimum output of the pitch compensation controller, deg |
| ThetaCMax | Maximum output of the pitch compensation controller, deg |

---

<a id="reactive-control"></a>

## Reactive Control

*Source: [`Content/TransientModels_HTML/StabilizerFolder ReactiveControl.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/StabilizerFolder ReactiveControl.htm)*

_This topic has no body text in the source help file._

---

<a id="stabilizers"></a>

## Stabilizers

*Source: [`Content/TransientModels_HTML/StabilizerFolder Stabilizer.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/StabilizerFolder Stabilizer.htm)*

_This topic has no body text in the source help file._

---

<a id="wind"></a>

## Wind

*Source: [`Content/TransientModels_HTML/StabilizerFolder Wind.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/StabilizerFolder Wind.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-stabilizers"></a>

## BPA Stabilizers

*Source: [`Content/TransientModels_HTML/BPA Stabilizers.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BPA Stabilizers.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-sf"></a>

## BPA_SF

*Source: [`Content/TransientModels_HTML/Stabilizer BPA SF, BPA SP, BPA SS, and BPA SG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer BPA SF, BPA SP, BPA SS, and BPA SG.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-sh"></a>

## BPA_SH

*Source: [`Content/TransientModels_HTML/Stabilizer BPA SH, BPA SHPLUS, and BPA SI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stabilizer BPA SH, BPA SHPLUS, and BPA SI.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This is a legacy model, which we do not have documentation.
