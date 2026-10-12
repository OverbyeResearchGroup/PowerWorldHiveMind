---
title: "TS Models — Exciters (Part 1 of 5)"
part: "Transient Models"
chapter_file: "39-ts-models-exciters-part1.md"
topics: 26
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Exciters (Part 1 of 5)

Excitation system models (IEEE types, ESST/ESAC/EXST families, REEC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (26)**

- [Exciters (Electrical Controls)](#exciters-electrical-controls)
- [All](#all)
- [AC1C](#ac1c)
- [AC2C](#ac2c)
- [AC3C](#ac3c)
- [AC4C](#ac4c)
- [AC5C](#ac5c)
- [AC6C](#ac6c)
- [AC7B](#ac7b)
- [AC7C](#ac7c)
- [AC8B](#ac8b)
- [AC8C](#ac8c)
- [AC9C](#ac9c)
- [AC10C](#ac10c)
- [AC11C](#ac11c)
- [BBSEX1](#bbsex1)
- [CELIN](#celin)
- [DC1C](#dc1c)
- [DC2C](#dc2c)
- [DC3A](#dc3a)
- [DC4B](#dc4b)
- [DC4C](#dc4c)
- [EMAC1T](#emac1t)
- [ESAC1A](#esac1a)
- [ESAC2A](#esac2a)
- [ESAC3A](#esac3a)

---

<a id="exciters-electrical-controls"></a>

## Exciters (Electrical Controls)

*Source: [`Content/TransientModels_HTML/Exciter.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/ExciterFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/ExciterFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="ac1c"></a>

## AC1C

*Source: [`Content/TransientModels_HTML/Exciter AC1C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC1C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If EFEmax \< EFEmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va
  - If EFE \> EFEmax, then EFEmax = EFE limits or if EFE limits \< EFEmin, then EFEmin = EFE limits

Model Equations and/or Block Diagrams   

![Exciter AC1C 0001](images/Exciter_AC1C_0001.svg)

![Exciter AC1C 0002](images/Exciter_AC1C_0002.svg)

---

<a id="ac2c"></a>

## AC2C

*Source: [`Content/TransientModels_HTML/Exciter AC2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kb = 0 then Kb = Mult\*TimeStep
  - If EFEmax \< EFEmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va
  - If EFE \> EFEmax, then EFEmax = EFE limits or if EFE limits \< EFEmin, then EFEmin = EFE limits

Model Equations and/or Block Diagrams

![Exciter AC2C 0001](images/Exciter_AC2C_0001.svg)

![Exciter AC2C 0002](images/Exciter_AC2C_0002.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr     | Filter time constant, sec                                       |
| Tb     | Time constant, sec                                              |
| Tc     | Time constant, sec                                              |
| Ka     | Voltage regulator gain                                          |
| Ta     | Voltage regulator time constant, sec                            |
| VaMax  | Maximum control element output, pu                              |
| VaMin  | Minimum control element output, pu                              |
| Kb     | Exciter field current controller gain, pu                       |
| Eefmax | Maximum exciter field voltage, pi                               |
| Eefmin | Minimum exciter field voltage, pi                               |
| Te     | Exciter field time constant, sec                                |
| Vfemax | Exciter field current limit parameter, pu                       |
| Kh     | Exciter field current feedback gain, pu                         |
| Kf     | Rate feedback gain, pu                                          |
| Tf     | Rate feedback constant, sec                                     |
| Kc     | Rectifier loading factor proportional to commutating reactance  |
| Kd     | Exciter internal reactance, pu                                  |
| Ke     | Exciter field resistance constant, pu                           |
| E1     | Field voltage value, 1                                          |
| SE1    | Saturation factor at E1                                         |
| E2     | Field voltage value, 2                                          |
| SE2    | Saturation factor at E2                                         |
| Vemin  | Minimimum exciter output voltage, pu                            |
| Spdmlt | If not zero, multiply output (Efd) by generator speed           |

---

<a id="ac3c"></a>

## AC3C

*Source: [`Content/TransientModels_HTML/Exciter AC3C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC3C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kr = 0 then Kr = Mult\*TimeStep
  - If Vamax \< Vamin then swap the values
  - If VPIDmax \< VPIDmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va \< Vamin, then Vamin = Va
  - If Ve \< Vfemin, then Vfemin = Ve limits

Model Equations and/or Block Diagrams

![Exciter AC3C 0001](images/Exciter_AC3C_0001.svg)

![Exciter AC3C 0002](images/Exciter_AC3C_0002.svg)

**Parameters:**

|         |                                                                 |
| ------- | --------------------------------------------------------------- |
| OEL     | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL     | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL     | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr      | Filter time constant, sec                                       |
| Tb      | Time constant, sec                                              |
| Tc      | Time constant, sec                                              |
| Ka      | Voltage regulator gain                                          |
| Ta      | Voltage regulator time constant, sec                            |
| VaMax   | Maximum control element output, pu                              |
| VaMin   | Minimum control element output, pu                              |
| Te      | Exciter field time constant, sec                                |
| Vemin   | Minimimum exciter output voltage, pu                            |
| Kr      | Field voltage feedback gain, pu                                 |
| Kf      | Rate feedback gain, pu                                          |
| Tf      | Rate feedback constant, sec                                     |
| Kn      | High level rate feedback gain, pu                               |
| Efdn    | Rate feedback gain break level, pu                              |
| Kc      | Rectifier loading factor proportional to commutating reactance  |
| Kd      | Exciter internal reactance, pu                                  |
| Ke      | Exciter field resistance constant, pu                           |
| Vfemax  | Exciter field current limit parameter, pu                       |
| E1      | Field voltage value, 1                                          |
| SE1     | Saturation factor at E1                                         |
| E2      | Field voltage value, 2                                          |
| SE2     | Saturation factor at E2                                         |
| Kpr     | Proportional gain, pu                                           |
| Kir     | Integral gain, pu                                               |
| Kdr     | Regulator derivative gain, pu                                   |
| Tdr     | Derivative gain washout time constant, sec                      |
| Vpidmax | PID maximum limit                                               |
| Vpidmin | PID minimum limit                                               |
| Spdmlt  | If not zero, multiply output (Efd) by generator speed           |

---

<a id="ac4c"></a>

## AC4C

*Source: [`Content/TransientModels_HTML/Exciter AC4C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC4C.htm)*

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

![Exciter AC4C 0001](images/Exciter_AC4C_0001.svg)

**Parameters:**

|       |                                                                 |
| ----- | --------------------------------------------------------------- |
| OEL   | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL   | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL   | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr    | Filter time constant, sec                                       |
| ViMax | Maximum error, pu                                               |
| ViMin | Minimum error, pu                                               |
| Tc    | Time constant, sec                                              |
| Tb    | Time constant, sec                                              |
| Ka    | Voltage regulator gain                                          |
| Ta    | Voltage regulator time constant, sec                            |
| Vrmax | Maximum exciter control signal, pu                              |
| Vrmin | Minimum exciter control signal, pu                              |
| Kc    | Rectifier loading factor proportional to commutating reactance  |

---

<a id="ac5c"></a>

## AC5C

*Source: [`Content/TransientModels_HTML/Exciter AC5C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC5C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf1 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter AC5C 0001](images/Exciter_AC5C_0001.svg)

![Exciter AC5C 0002](images/Exciter_AC5C_0002.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr     | Filter time constant, sec                                       |
| Ka     | Voltage regulator gain                                          |
| Ta     | Voltage regulator time constant, sec                            |
| VaMax  | Maximum control element output, pu                              |
| VaMin  | Minimum control element output, pu                              |
| Ke     | Exciter field resistance constant, pu                           |
| Te     | Exciter field time constant, sec                                |
| Kf     | Rate feedback gain, pu                                          |
| Tf1    | Feedback lag time constant, sec                                 |
| Tf2    | Feedback lag time constant, sec                                 |
| Tf3    | Feedback lead time constant, sec                                |
| E1     | Field voltage value, 1                                          |
| SE1    | Saturation factor at E1                                         |
| E2     | Field voltage value, 2                                          |
| SE2    | Saturation factor at E2                                         |
| Kc     | Rectifier loading factor proportional to commutating reactance  |
| Kd     | Exciter internal reactance, pu                                  |
| Vfemax | Exciter field current limit parameter, pu                       |
| Vemin  | Minimimum exciter output voltage, pu                            |
| Spdmlt | If not zero, multiply output (Efd) by generator speed           |

---

<a id="ac6c"></a>

## AC6C

*Source: [`Content/TransientModels_HTML/Exciter AC6C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC6C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If EFEmax \< EFEmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If EFE \> VT\*EFEmax, then EFEmax = EFE/VT limits or if EFE\< VT\*EFEmin, then EFEmin = EFE/VT
  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter AC6C 0001](images/Exciter_AC6C_0001.svg)

![Exciter AC6C 0002](images/Exciter_AC6C_0002.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr     | Filter time constant, sec                                       |
| Ka     | Voltage regulator gain                                          |
| Ta     | Voltage regulator time constant, sec                            |
| Tk     | Time constant, sec                                              |
| Tb     | Time lag constant, sec                                          |
| Tc     | Time lead constant, sec                                         |
| VaMax  | Maximum control element output, pu                              |
| VaMin  | Minimum control element output, pu                              |
| Eefmax | Maximum exciter field voltage, pi                               |
| Eefmin | Minimum exciter field voltage, pi                               |
| Te     | Exciter field time constant, sec                                |
| Vfelim | Model Parameters\\Vfelim                                        |
| Kh     | Exciter field current feedback gain, pu                         |
| Vhmax  | Model Parameters\\Vhmax                                         |
| Th     | Time lag constant, sec                                          |
| Tj     | Time lead constant, sec                                         |
| Kc     | Rectifier loading factor proportional to commutating reactance  |
| Kd     | Exciter internal reactance, pu                                  |
| Ke     | Exciter field resistance constant, pu                           |
| E1     | Field voltage value, 1                                          |
| SE1    | Saturation factor at E1                                         |
| E2     | Field voltage value, 2                                          |
| SE2    | Saturation factor at E2                                         |
| Vfemax | Exciter field current limit parameter, pu                       |
| Vemin  | Minimimum exciter output voltage, pu                            |
| Spdmlt | If not zero, multiply output (Efd) by generator speed           |

---

<a id="ac7b"></a>

## AC7B

*Source: [`Content/TransientModels_HTML/Exciter AC7B and ESAC7B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC7B and ESAC7B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va
  - If Ve \> ((VFemax-Kd\*Ifd)/(Ke + Se(Ve)), then VFemax = ((VFemax-Kd\*Ifd)/(Ke + Se(Ve)) or if Ve \< Vemin, then Vemin = Ve

Model Equations and/or Block Diagrams

![Exciter AC7B and ESAC7B 0001](images/Exciter_AC7B_and_ESAC7B_0001.svg)   

**Parameters for AC7B:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Kpr    | Proportional gain, pu                                          |
| Kir    | Integral gain, pu                                              |
| Kdr    | Regulator derivative gain, pu                                  |
| Tdr    | Regulator derivative washout time constant, sec                |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Kpa    | Amplifier proportional gain, pu                                |
| Kia    | Amplifier integral gain, pu                                    |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Kp     | Potential source gain, pu                                      |
| Kl     | Exciter field current limiter gain, pu                         |
| KF1    | KF1                                                            |
| KF2    | KF2                                                            |
| KF3    | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| Te     | Exciter field time constant, sec                               |
| Vfemax | Exciter field current limit parameter, pu                      |
| Vemin  | Minimimum exciter output voltage, pu                           |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |

**Parameters for ESAC7B:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Kpr    | Proportional gain, pu                                          |
| Kir    | Integral gain, pu                                              |
| Kdr    | Regulator derivative gain, pu                                  |
| Tdr    | Derivative gain washout time constant, sec                     |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Kpa    | Amplifier proportional gain, pu                                |
| Kia    | Amplifier integral gain, pu                                    |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Kp     | Potential source gain, pu                                      |
| Kl     | Exciter field current limiter gain, pu                         |
| Te     | Exciter field time constant, sec                               |
| Vfemax | Exciter field current limit parameter, pu                      |
| Vemin  | Minimimum exciter output voltage, pu                           |
| Ke     | Exciter field resistance constant, pu                          |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| KF1    | KF1                                                            |
| KF2    | KF2                                                            |
| KF3    | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="ac7c"></a>

## AC7C

*Source: [`Content/TransientModels_HTML/Exciter AC7C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC7C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va
  - If Ve \> ((VFemax-Kd\*Ifd)/(Ke + Se(Ve)), then VFemax = ((VFemax-Kd\*Ifd)/(Ke + Se(Ve)) or if Ve \< Vemin, then Vemin = Ve

Model Equations and/or Block Diagrams

![Exciter AC7C 0001](images/Exciter_AC7C_0001.svg)

![Exciter AC7C 0002](images/Exciter_AC7C_0002.svg)

**Parameters:**

|        |                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------- |
| OEL    | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2; if = 4, LV gate 3; |
| UEL    | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2;                    |
| SCL    | SCL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2;                    |
| VOS    | PSS input: if = 1, add to error signal; if = 2, add after HV gate 1                               |
| SW1    | Logical switch 1 (1 = Position A, 2 = Position B)                                                 |
| SW2    | Logical switch 2 (1 = Position A, 2 = Position B)                                                 |
| Tr     | Filter time constant, sec                                                                         |
| Kpr    | Proportional gain, pu                                                                             |
| Kir    | Integral gain, pu                                                                                 |
| Kdr    | Regulator derivative gain, pu                                                                     |
| Tdr    | Derivative gain washout time constant, sec                                                        |
| Vrmax  | Maximum exciter control signal, pu                                                                |
| Vrmin  | Minimum exciter control signal, pu                                                                |
| Kpa    | Amplifier proportional gain, pu                                                                   |
| Kia    | Amplifier integral gain, pu                                                                       |
| VaMax  | Maximum control element output, pu                                                                |
| VaMin  | Minimum control element output, pu                                                                |
| Kp     | Potential source gain, pu                                                                         |
| Kl     | Exciter field current limiter gain, pu                                                            |
| KF1    | Generator field voltage feedback gain, pu                                                         |
| KF2    | Exciter field current feedback gain, pu                                                           |
| KF3    | Rate feedback gain, pu                                                                            |
| Tf     | Rate feedback constant, sec                                                                       |
| KC     | Rectifier loading factor proportional to commutating reactance                                    |
| Kd     | Exciter internal reactance, pu                                                                    |
| Ke     | Exciter field resistance constant, pu                                                             |
| Te     | Exciter field time constant, sec                                                                  |
| Vfemax | Exciter field current limit parameter, pu                                                         |
| Vemin  | Minimimum exciter output voltage, pu                                                              |
| E1     | Field voltage value, 1                                                                            |
| SE1    | Saturation factor at E1                                                                           |
| E2     | Field voltage value, 2                                                                            |
| SE2    | Saturation factor at E2                                                                           |
| Ki     | Potential circuit (current) gain coefficient                                                      |
| XL     | Reactance associated with potential source                                                        |
| ThetaP | Potencial circuit phase angle, degrees                                                            |
| KC1    | Rectifier loading factor proportional to commutating reactance                                    |
| Vbmax  | Maximum available exciter field voltage                                                           |
| Kr     | Field voltage feedback gain, pu                                                                   |
| Spdmlt | If not zero, multiply output (Efd) by generator speed                                             |

---

<a id="ac8b"></a>

## AC8B

*Source: [`Content/TransientModels_HTML/Exciter AC8B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC8B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vpidmax \< Vpidmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter AC8B 0001](images/Exciter_AC8B_0001.svg)   

**Parameters:**

|        |                                                                |
| ------ | -------------------------------------------------------------- |
| Tr     | Filter time constant, sec                                      |
| Kpr    | Proportional gain, pu                                          |
| Kir    | Integral gain, pu                                              |
| Kdr    | Regulator derivative gain, pu                                  |
| Tdr    | Derivative gain washout time constant, sec                     |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Kpa    | Amplifier proportional gain, pu                                |
| Kia    | Amplifier integral gain, pu                                    |
| VaMax  | Maximum control element output, pu                             |
| VaMin  | Minimum control element output, pu                             |
| Kp     | Potential source gain, pu                                      |
| Kl     | Exciter field current limiter gain, pu                         |
| KF1    | KF1                                                            |
| KF2    | KF2                                                            |
| KF3    | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| Te     | Exciter field time constant, sec                               |
| Vfemax | Exciter field current limit parameter, pu                      |
| Vemin  | Minimimum exciter output voltage, pu                           |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |

---

<a id="ac8c"></a>

## AC8C

*Source: [`Content/TransientModels_HTML/Exciter AC8C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC8C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vpidmax \< Vpidmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter AC8C 0001](images/Exciter_AC8C_0001.svg)

![Exciter AC8C 0002](images/Exciter_AC8C_0002.svg)

**Parameters:**

|         |                                                                               |
| ------- | ----------------------------------------------------------------------------- |
| OEL     | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| UEL     | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| SCL     | SCL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| VOS     | PSS input: if = 1, add to error signal; if = 2, add after HV gate 1           |
| SW1     | Logical switch 1 (1 = Position A, 2 = Position B)                             |
| Tr      | Filter time constant, sec                                                     |
| Kpr     | Proportional gain, pu                                                         |
| Kir     | Integral gain, pu                                                             |
| Kdr     | Regulator derivative gain, pu                                                 |
| Tdr     | Derivative gain washout time constant, sec                                    |
| Vpidmax | PID maximum limit                                                             |
| Vpidmin | PID minimum limit                                                             |
| Ka      | Voltage regulator gain                                                        |
| Ta      | Voltage regulator time constant, sec                                          |
| Vrmax   | Maximum exciter control signal, pu                                            |
| Vrmin   | Minimum exciter control signal, pu                                            |
| KC      | Rectifier loading factor proportional to commutating reactance                |
| Kd      | Exciter internal reactance, pu                                                |
| Ke      | Exciter field resistance constant, pu                                         |
| Te      | Exciter field time constant, sec                                              |
| Vfemax  | Exciter field current limit parameter, pu                                     |
| Vemin   | Minimimum exciter output voltage, pu                                          |
| E1      | Field voltage value, 1                                                        |
| SE1     | Saturation factor at E1                                                       |
| E2      | Field voltage value, 2                                                        |
| SE2     | Saturation factor at E2                                                       |
| Kp      | Potential source gain, pu                                                     |
| Ki      | Potential circuit (current) gain coefficient                                  |
| XL      | Reactance associated with potential source                                    |
| ThetaP  | Potencial circuit phase angle, degrees                                        |
| KC1     | Rectifier loading factor proportional to commutating reactance                |
| Vbmax   | Maximum available exciter field voltage                                       |
| Spdmlt  | If not zero, multiply output (Efd) by generator speed                         |

---

<a id="ac9c"></a>

## AC9C

*Source: [`Content/TransientModels_HTML/Exciter AC9C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC9C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tdr \< 0.5\*Mult\*TimeStep then Tdr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdr \< Mult\*TimeStep then Tdr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If Vpidmax \< Vpidmin then swap the values
  - If VFWmax \< VFWmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If VFW \> VFWmax, then VFWmax = VFW limits or if VFW \< VFWmin, then VFWmin = VFW
  - If Va \> Vamax, then Vamax = Va limits or if Va \< Vamin, then Vamin = Va
  - If IFDref \> VPIDmax, then VPIDmax = IFDref limits or if IFDref \< VPIDmin, then VPIDmin = IFDref

Model Equations and/or Block Diagrams

![Exciter AC9C 0001](images/Exciter_AC9C_0001.svg)

![Exciter AC9C 0002](images/Exciter_AC9C_0002.svg)

**Parameters:**

|         |                                                                                                   |
| ------- | ------------------------------------------------------------------------------------------------- |
| OEL     | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2                     |
| UEL     | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2                     |
| SCL     | SCL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2                     |
| SW1     | Logical switch 1 (1 = Position A, 2 = Position B)                                                 |
| Tr      | Filter time constant, sec                                                                         |
| Kpr     | Proportional gain, pu                                                                             |
| Kir     | Integral gain, pu                                                                                 |
| Kdr     | Regulator derivative gain, pu                                                                     |
| Tdr     | Derivative gain washout time constant, sec                                                        |
| Vpidmax | PID maximum limit                                                                                 |
| Vpidmin | PID minimum limit                                                                                 |
| KPA     | Potential source gain, pu                                                                         |
| KIA     | Potential circuit (current) gain coefficient                                                      |
| VaMax   | Maximum control element output, pu                                                                |
| VaMin   | Minimum control element output, pu                                                                |
| Ka      | Voltage regulator gain                                                                            |
| Ta      | Voltage regulator time constant, sec                                                              |
| Vrmax   | Maximum exciter control signal, pu                                                                |
| Vrmin   | Minimum exciter control signal, pu                                                                |
| KF      | Rate feedback gain, pu                                                                            |
| Tf      | Rate feedback constant, sec                                                                       |
| KFW     | Gain for VFW                                                                                      |
| VFWmax  | VFW Maximum                                                                                       |
| VFWmin  | VFW Minimum                                                                                       |
| SCT     | User select parameter: SCT not 0 - Represent thyristor bridge; 1 - Represents a chopper converter |
| KC      | Rectifier loading factor proportional to commutating reactance                                    |
| Kd      | Exciter internal reactance, pu                                                                    |
| Ke      | Exciter field resistance constant, pu                                                             |
| Te      | Exciter field time constant, sec                                                                  |
| Vfemax  | Exciter field current limit parameter, pu                                                         |
| Vemin   | Minimimum exciter output voltage, pu                                                              |
| E1      | Field voltage value, 1                                                                            |
| SE1     | Saturation factor at E1                                                                           |
| E2      | Field voltage value, 2                                                                            |
| SE2     | Saturation factor at E2                                                                           |
| KP      | Potential source gain, pu                                                                         |
| KI1     | Potential circuit (current) gain coefficient                                                      |
| KI2     | Potential circuit (current) gain coefficient                                                      |
| KC1     | Rectifier loading factor proportional to commutating reactance                                    |
| KC2     | Rectifier loading factor proportional to commutating reactance                                    |
| XL      | Reactance associated with potential source                                                        |
| ThetaP  | Potencial circuit phase angle, degrees                                                            |
| VbMax1  | Maximum available exciter field voltage                                                           |
| VbMax2  | Maximum available exciter field voltage                                                           |
| Vlim1   | Power type stage selector vlim1                                                                   |
| Vlim2   | Power type stage selector vlim2                                                                   |
| Spdmlt  | If not zero, multiply output (Efd) by generator speed                                             |

---

<a id="ac10c"></a>

## AC10C

*Source: [`Content/TransientModels_HTML/Exciter AC10C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC10C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If Kr \<= 0 then Kr = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vrsmax \< Vrsmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If Vrs \> Vrsmax, then Vrsmax = Vrs limits or if Vrs \< Vrsmin, then Vrsmin = Vrs

Model Equations and/or Block Diagrams

![Exciter AC10C 0001](images/Exciter_AC10C_0001.svg)

![Exciter AC10C 0002](images/Exciter_AC10C_0002.svg)

![Exciter AC10C 0003](images/Exciter_AC10C_0003.svg)

![Exciter AC10C 0004](images/Exciter_AC10C_0004.svg)

**Parameters:**

|        |                                                                                            |
| ------ | ------------------------------------------------------------------------------------------ |
| OEL    | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2              |
| UEL    | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2              |
| VOS    | PSS input: if = 1, add to error signal; if = 2, add in SWLim Logic; if = 3, add to VS2 Sum |
| SCL    | SCL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2              |
| Tr     | Filter time constant, sec                                                                  |
| Kr     | Field voltage feedback gain, pu                                                            |
| TB1    | Voltage Regulator Time constant 1, sec                                                     |
| TC1    | Voltage Regulator Time constant 1, sec                                                     |
| TB2    | Voltage Regulator Lag time constant 2, sec                                                 |
| TC2    | Voltage Regulator Lead time constant 2, sec                                                |
| TUB1   | UEL Regulator Lag time constant 1, sec                                                     |
| TUC1   | UEL Regulator Lead time constant 1, sec                                                    |
| TUB2   | UEL Regulator Lag time constant 2, sec                                                     |
| TUC2   | UEL Regulator Lead time constant 2, sec                                                    |
| TOB1   | OEL Regulator Lag time constant 1, sec                                                     |
| TOC1   | OEL Regulator Lead time constan 1t, sec                                                    |
| TOB2   | OEL Regulator Lag time constant 2, sec                                                     |
| TOC2   | OEL Regulator Lead time constant 2, sec                                                    |
| VRmax  | Maximum exciter control signal, pu                                                         |
| VRmin  | Minimum exciter control signal, pu                                                         |
| VRSmax | Maximum exciter control signal, pu                                                         |
| VRSmin | Minimum exciter control signal, pu                                                         |
| TE     | Exciter field time constant, sec                                                           |
| KC     | Rectifier loading factor proportional to commutating reactance                             |
| Kd     | Exciter internal reactance, pu                                                             |
| Ke     | Exciter field resistance constant, pu                                                      |
| Vfemax | Exciter field current limit parameter, pu                                                  |
| E1     | Field voltage value, 1                                                                     |
| SE1    | Saturation factor at E1                                                                    |
| E2     | Field voltage value, 2                                                                     |
| SE2    | Saturation factor at E2                                                                    |
| SW1    | Logical switch 1 (1 = Position A, 2 = Position B)                                          |
| Kp     | Potential source gain, pu                                                                  |
| ThetaP | Potencial circuit phase angle, degrees                                                     |
| KI     | Potential circuit (current) gain coefficient                                               |
| XL     | Reactance associated with potential source                                                 |
| KC1    | Rectifier loading factor proportional to commutating reactance                             |
| VbMax1 | Maximum available exciter field voltage                                                    |
| KI2    | Potential circuit (current) gain coefficient                                               |
| KC2    | Rectifier loading factor proportional to commutating reactance                             |
| VbMax2 | Maximum available exciter field voltage                                                    |
| SWEXC  | Logical switch 1 (1 = Position A, 2 = Position B)                                          |
| TEXC   | Exciter field time constant, sec                                                           |
| KEXC   | Exciter field resistance constant, pu                                                      |
| KCR    | Rectifier loading factor proportional to commutating reactance                             |
| Tf1    | Rate feedback constant, sec                                                                |
| Tf2    | Feedback lead time constant, sec                                                           |
| KVFE   | Fast raise/lower contact setting                                                           |
| KLIM   | Exciter field current limiter gain, pu                                                     |
| Vfelim | Model Parameters\\Vfelim                                                                   |
| Vemin  | Minimimum exciter output voltage, pu                                                       |
| Spdmlt | If not zero, multiply output (Efd) by generator speed                                      |

---

<a id="ac11c"></a>

## AC11C

*Source: [`Content/TransientModels_HTML/Exciter AC11C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter AC11C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tia \< Mult\*TimeStep then Tia = Mult\*TimeStep
  - If 0 \< Tio \< Mult\*TimeStep then Tio = Mult\*TimeStep
  - If 0 \< Tiu \< Mult\*TimeStep then Tiu = Mult\*TimeStep
  - If Kpa \<= 0 then Kpa = Mult\*TimeStep
  - If Kpu \<= 0 then Kpu = Mult\*TimeStep
  - If Kpo \<= 0 then Kpo = Mult\*TimeStep
  - If Kb \<= 0 then Kb = Mult\*TimeStep
  - If Tb \<= 0 then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vrsmax \< Vrsmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr limits or if Vr \< Vrmin, then Vrmin = Vr
  - If Vrs \> Vrsmax, then Vrsmax = Vrs limits or if Vrs \< Vrsmin, then Vrsmin = Vrs
  - If Va \> Vamax, then Vamax = Va limits or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter AC11C 0001](images/Exciter_AC11C_0001.svg)

![Exciter AC11C 0002](images/Exciter_AC11C_0002.svg)

![Exciter AC11C 0003](images/Exciter_AC11C_0003.svg)

**Parameters:**

|        |                                                                                              |
| ------ | -------------------------------------------------------------------------------------------- |
| VOS    | PSS input: if \<= 1, add to error signal; if = 2, add in SWLim Logic; if = 3, add to VS2 Sum |
| OEL    | OEL input: if \<= 1, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2               |
| UEL    | UEL input: if \<= 1, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2               |
| SCL    | SCL input: if \<= 1, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2               |
| SW1    | SW1 Logical switch 1 (1 = Position A, 2 = Position B)                                        |
| Tr     | Filter time constant, sec                                                                    |
| Kpa    | Amplifier proportional gain, pu                                                              |
| Tia    | Integrator time constant, sec                                                                |
| KPU    | Potential source gain, pu                                                                    |
| TIU    | Integrator time constant, sec                                                                |
| Kb     | Exciter field current controller gain, pu                                                    |
| Tb     | Time constant, sec                                                                           |
| KPO    | Potential source gain, pu                                                                    |
| TIO    | Integrator time constant, sec                                                                |
| VRSmax | Maximum exciter control signal, pu                                                           |
| VRSmin | Minimum exciter control signal, pu                                                           |
| VRmax  | Maximum exciter control signal, pu                                                           |
| VRmin  | Minimum exciter control signal, pu                                                           |
| VaMax  | Maximum control element output, pu                                                           |
| VaMin  | Minimum control element output, pu                                                           |
| Te     | Exciter field time constant, sec                                                             |
| KC     | Rectifier loading factor proportional to commutating reactance                               |
| Kd     | Exciter internal reactance, pu                                                               |
| Ke     | Exciter field resistance constant, pu                                                        |
| Vfemax | Exciter field current limit parameter, pu                                                    |
| Vemin  | Minimimum exciter output voltage, pu                                                         |
| E1     | Field voltage value, 1                                                                       |
| SE1    | Saturation factor at E1                                                                      |
| E2     | Field voltage value, 2                                                                       |
| SE2    | Saturation factor at E2                                                                      |
| KP     | Potential source gain, pu                                                                    |
| KI     | Potential circuit (current) gain coefficient                                                 |
| XL     | Reactance associated with potential source                                                   |
| ThetaP | Potencial circuit phase angle, degrees                                                       |
| KC1    | Rectifier loading factor proportional to commutating reactance                               |
| VbMax1 | Maximum available exciter field voltage                                                      |
| KI2    | Potential circuit (current) gain coefficient                                                 |
| KC2    | Rectifier loading factor proportional to commutating reactance                               |
| VbMax2 | Maximum available exciter field voltage                                                      |
| KBOOST | Exciter field current controller gain, pu                                                    |
| VBOOST | Model Parameters\\VBOOST                                                                     |

---

<a id="bbsex1"></a>

## BBSEX1

*Source: [`Content/TransientModels_HTML/Exciter BBSEX1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter BBSEX1.htm)*

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

![Exciter BBSEX1 0001](images/Exciter_BBSEX1_0001.svg)   

**Parameters:**

|        |                                      |
| ------ | ------------------------------------ |
| Tf     | Rate feedback constant, sec          |
| K      | Voltage regulator gain               |
| T1     | Inverse timing current constant, sec |
| T2     | Inverse timing current constant, sec |
| T3     | Inverse timing current constant, sec |
| T4     | Inverse timing current constant, sec |
| Vrmax  | Maximum exciter control signal, pu   |
| Vrmin  | Minimum exciter control signal, pu   |
| Eefmax | Maximum exciter field voltage, pi    |
| Eefmin | Minimum exciter field voltage, pi    |
| Switch | Supplementary signal routing switch  |

---

<a id="celin"></a>

## CELIN

*Source: [`Content/TransientModels_HTML/Exciter CELIN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter CELIN.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - p\_PSS must be between than 0 and 4, if true then p\_PSS changed to 0.
  - K3 and T13: K3 can't be 0 if T13 = 0, if true then K3 changed to 10.
  - K4 and T14: K3 can't be 0 if T14 = 0, if true then K4 changed to 10.
  - For Param TR1, TR2, TR3, TR4, T1, T2, T3, T4, T5, T6, T11 and TE then If 0.0 \< Param \< 0.5\*Mult\*TimeStep then Param = 0, ElseIf 0.5\*Mult\*TimeStep \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - For Param TE2, TB1, K21, KETB and Xp then If 0 \< Param \< Mult\*TimeStep then Param = Mult\*TimeStep
  - If LIMMAX\_PID1\< LIMMIN\_PID1 then swap the values
  - If Up+\< Up- then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Up+, then Up+= Vr limits or if Vr \< Up-, then Up-= Vr
  - If Ieref \> LIMMAX\_PID1, then LIMMAX\_PID1= Ieref limits or if Ieref \< LIMMIN\_PID1, then LIMMIN\_PID1= Ieref
  - If Vss \> Psslim, then Psslim = Vss or if Vss \< -Psslim then Psslim := abs(Vss)
  - If State TE\> Vt\*Up+, then Vt\*Up+= State TE limits or if State TE\< Vt\*Up-, then Vt\*Up-= State TE

Model Equations and/or Block Diagrams

![Exciter CELIN 0001](images/Exciter_CELIN_0001.svg)  

![Exciter CELIN 0002](images/Exciter_CELIN_0002.svg)

**Parameters:**

|              |                                       |
| ------------ | ------------------------------------- |
| TR1          | Vt filter time constant, sec          |
| TR2          | Vw filter time constant, sec          |
| TR3          | Vb filter time constant, sec          |
| alpha        | alpha                                 |
| Beta         | Beta                                  |
| TE2          | Exciter field time constant, sec      |
| NomEFD       | EFD normalization parameter, pu       |
| KE2          | Exciter field resistance constant, pu |
| TR4          | Ief filter time constant, sec         |
| T1           | Filter time constant 1, sec           |
| T2           | Filter time constant 2, sec           |
| T3           | Derivative time constant 3, sec       |
| T4           | Derivative time constant 4, sec       |
| T5           | Derivative time constant 5, sec       |
| T6           | Vs time constant, sec                 |
| K12          | Vs gain                               |
| K2           | Gain K2                               |
| p\_PSS       | p\_PSS                                |
| A\_PSS       | A\_PSS                                |
| Psslim       | Vss limit                             |
| K1           | Gain 1                                |
| KIEC         | KIEC limit                            |
| KD1          | Derivative D1 parameter               |
| TB1          | Derivative D1 time constant, sec      |
| T11          | Integrator 11 time constant, sec      |
| LIMMAX\_PID1 | PID max limit                         |
| LIMMIN\_PID1 | PID min limit                         |
| K21          | Gain 21                               |
| Spare        | Spare                                 |
| Up+          | Up+ max limit                         |
| Up-          | Up- min limit                         |
| K3           | Gain 3                                |
| T13          | Integrator 12 time constant, sec      |
| K4           | Gain 4                                |
| T14          | Integrator 14 time constat, sec       |
| KETB         | Vr gain                               |
| TE           | Vr filter time constant, sec          |
| Xp           | Xp                                    |
| Iefmax1      | Ief max1                              |
| Iefmax2      | Ief max2                              |
| Iefmin       | Ief min                               |
| E1           | Field voltage value, 1                |
| SE1          | Saturation factor at E1               |
| E2           | Field voltage value, 2                |
| SE2          | Saturation factor at E2               |

---

<a id="dc1c"></a>

## DC1C

*Source: [`Content/TransientModels_HTML/Exciter DC1C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter DC1C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep, elseif Tf \<= 0 then Tf = 0
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter DC1C 0001](images/Exciter_DC1C_0001.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr     | Regulator input filter time constant, s                         |
| Ka     | Regulator ouput gain, pu                                        |
| Ta     | Regulator time constant, s                                      |
| Tb     | Regulator denominator lag time constant, s                      |
| Tc     | Regulator numerator lead time constant, s                       |
| Vrmax  | Maximum controller output, pu                                   |
| Vrmin  | Minimum controller output, pu                                   |
| Ke     | Exciter field proportional constant, pu                         |
| Te     | Exciter field time constant, s                                  |
| Kf     | Rate Feedback gain, pu                                          |
| Tf1    | Rate feedback time constant, s                                  |
| E1     | Exciter outout voltage for saturation factor SeE1, pu           |
| SE1    | Exciter saturation factor at exciter output voltage E1          |
| E2     | Exciter outout voltage for saturation factor SeE2, pu           |
| SE2    | Exciter saturation factor at exciter output voltage E2          |
| Vemax  | Exciter output maximum limit                                    |
| Vemin  | Exciter output minimum limit                                    |
| Spdmlt | If not zero, multiply output (Efd) by generator speed           |

---

<a id="dc2c"></a>

## DC2C

*Source: [`Content/TransientModels_HTML/Exciter DC2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter DC2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep, elseif Tf \<= 0 then Tf = 0
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter DC2C 0001](images/Exciter_DC2C_0001.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, LV gate; if \< 2, subtract from error signal |
| Tr     | Regulator input filter time constant, s                         |
| Ka     | Regulator ouput gain, pu                                        |
| Ta     | Regulator time constant, s                                      |
| Tb     | Regulator denominator lag time constant, s                      |
| Tc     | Regulator numerator lead time constant, s                       |
| Vrmax  | Maximum controller output, pu                                   |
| Vrmin  | Minimum controller output, pu                                   |
| Ke     | Exciter field proportional constant, pu                         |
| Te     | Exciter field time constant, s                                  |
| Kf     | Rate Feedback gain, pu                                          |
| Tf1    | Rate feedback time constant, s                                  |
| E1     | Exciter outout voltage for saturation factor SeE1, pu           |
| SE1    | Exciter saturation factor at exciter output voltage E1          |
| E2     | Exciter outout voltage for saturation factor SeE2, pu           |
| SE2    | Exciter saturation factor at exciter output voltage E2          |
| Vemax  | Exciter output maximum limit                                    |
| Vemin  | Exciter output minimum limit                                    |
| Spdmlt | If not zero, multiply output (Efd) by generator speed           |

---

<a id="dc3a"></a>

## DC3A

*Source: [`Content/TransientModels_HTML/Exciter DC3A and ESDC3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter DC3A and ESDC3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Trh \<= 0 then Trh = 0
  - If Kv \<= 0 then Kv = 0

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter DC3A and ESDC3A 0001](images/Exciter_DC3A_and_ESDC3A_0001.svg)   

**Parameters for DC3A:**

|       |                                                              |
| ----- | ------------------------------------------------------------ |
| Tr    | Filter time constant, sec.                                   |
| Kv    | Voltage error threshold min/max control action, p.u. (\> 0.) |
| VrMax | Maximum control element output, p.u.                         |
| VrMin | Minimum control element output, p.u.                         |
| Trh   | Rheostat full range travel time, sec. (\> 0.)                |
| Te    | Exciter field time constant, sec. (\> 0.)                    |
| Ke    | Exciter field resistance line slope margin p.u.              |
| Vemin | Exciter minimum limit                                        |
| E1    | Field voltage value, 1                                       |
| SE1   | Saturation factor at E1                                      |
| E2    | Field voltage value, 2                                       |
| SE2   | Saturation factor at E2                                      |

**Parameters for ESDC3A:**

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

<a id="dc4b"></a>

## DC4B

*Source: [`Content/TransientModels_HTML/Exciter DC4B and ESDC4B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter DC4B and ESDC4B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Td \<0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter DC4B and ESDC4B 0001](images/Exciter_DC4B_and_ESDC4B_0001.svg)  

**Parameters for DC4B:**

|       |                                                                 |
| ----- | --------------------------------------------------------------- |
| OEL   | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL   | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| Tr    | Filter time constant, sec.                                      |
| Kp    | Proportional gain                                               |
| Ki    | Integral gain                                                   |
| Kd    | Derivative gain                                                 |
| Td    | Derivative time constant, sec.                                  |
| Vrmax | Maximum controller output, p.u.                                 |
| Vrmin | Minimum controller output, p.u.                                 |
| Ka    | Gain, p.u.                                                      |
| Ta    | Time constant, sec. (\> 0.)                                     |
| Ke    | Exciter field resistance line slope margin, p.u.                |
| Te    | Exciter time constant, sec. (\> 0.)                             |
| Kf    | Rate feedback gain                                              |
| Tf    | Rate feedback time constant, sec.                               |
| Vemin | Exciter minimum output                                          |
| E1    | Field voltage value, 1                                          |
| SE1   | Saturation factor at E1                                         |
| E2    | Field voltage value, 2                                          |
| SE2   | Saturation factor at E2                                         |

**Parameters for ESDC4B:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| Tr     | Filter time constant, sec.                                      |
| Ka     | Gain, p.u.                                                      |
| Ta     | Time constant, sec. (\> 0.)                                     |
| Kp     | Proportional gain                                               |
| Ki     | Integral gain                                                   |
| Kd     | Derivative gain                                                 |
| Td     | Derivative time constant, sec.                                  |
| Vrmax  | Maximum controller output, p.u.                                 |
| Vrmin  | Minimum controller output, p.u.                                 |
| Ke     | Exciter field resistance line slope margin, p.u.                |
| Te     | Exciter time constant, sec. (\> 0.)                             |
| Kf     | Rate feedback gain                                              |
| Tf     | Rate feedback time constant, sec.                               |
| E1     | Field voltage value, 1                                          |
| SE1    | Saturation factor at E1                                         |
| E2     | Field voltage value, 2                                          |
| SE2    | Saturation factor at E2                                         |
| Vemin  | Exciter minimum output                                          |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| Spdmlt | If = 1, multiply output (Efd) by generator speed                |

---

<a id="dc4c"></a>

## DC4C

*Source: [`Content/TransientModels_HTML/Exciter DC4C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter DC4C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Td \<0.5\*Mult\*TimeStep then Td = 0, ElseIf 0.5\*Mult\*TimeStep \< Td \< Mult\*TimeStep then Td = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter DC4C 0001](images/Exciter_DC4C_0001.svg)

**Parameters:**

|        |                                                                 |
| ------ | --------------------------------------------------------------- |
| OEL    | OEL input: if = 2, LV gate; if \< 2, subtract from error signal |
| UEL    | UEL input: if = 2, HV gate; if \< 2, add to error signal        |
| SCL    | SCL input: if = 2, HV gate; if \< 2, add to error signal        |
| SW1    | Logical switch 1 (1 = Position A, 2 = Position B)               |
| Tr     | Filter time constant, sec.                                      |
| Kpr    | Proportional gain                                               |
| Kir    | Integral gain                                                   |
| KDR    | Derivative gain                                                 |
| TDR    | Derivative time constant, sec.                                  |
| Vrmax  | Maximum controller output, p.u.                                 |
| Vrmin  | Minimum controller output, p.u.                                 |
| Ka     | Gain, p.u.                                                      |
| Ta     | Time constant, sec. (\> 0.)                                     |
| Ke     | Exciter field resistance line slope margin, p.u.                |
| Te     | Exciter time constant, sec. (\> 0.)                             |
| Kf     | Rate feedback gain                                              |
| Tf     | Rate feedback time constant, sec.                               |
| Vemin  | Exciter minimum output                                          |
| E1     | Field voltage value, 1                                          |
| SE1    | Saturation factor at E1                                         |
| E2     | Field voltage value, 2                                          |
| SE2    | Saturation factor at E2                                         |
| Kp     | Potential circuit gain coefficient                              |
| Ki     | Potential circuit current gain coefficient                      |
| XL     | Reactance associated with potential source                      |
| ThetaP | Potencial circuit phase angle, degrees                          |
| KC1    | Rectifier loading factor proportional to commutating reactance  |
| Vbmax  | Maximum available exciter field voltage                         |
| Spdmlt | If = 1, multiply output (Efd) by generator speed                |

---

<a id="emac1t"></a>

## EMAC1T

*Source: [`Content/TransientModels_HTML/Exciter EMAC1T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter EMAC1T.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter EMAC1T 0001](images/Exciter_EMAC1T_0001.svg)

**Parameters:**

|       |                                                                |
| ----- | -------------------------------------------------------------- |
| Tr    | Filter time constant, sec                                      |
| T4    | Inverse timing current constant, sec                           |
| T3    | Inverse timing current constant, sec                           |
| Ka    | Voltage regulator gain                                         |
| Ta    | Voltage regulator time constant, sec                           |
| Vrmax | Maximum exciter control signal, pu                             |
| Vrmin | Minimum exciter control signal, pu                             |
| Te    | Exciter field time constant, sec                               |
| Kf    | Rate feedback gain, pu                                         |
| Tf    | Rate feedback constant, sec                                    |
| Kc    | Rectifier loading factor proportional to commutating reactance |
| Kd    | Exciter internal reactance, pu                                 |
| Ke    | Exciter field resistance constant, pu                          |
| E1    | Field voltage value, 1                                         |
| SE1   | Saturation factor at E1                                        |
| E2    | Field voltage value, 2                                         |
| SE2   | Saturation factor at E2                                        |
| T6    | Inverse timing current constant, sec                           |
| T5    | Inverse timing current constant, sec                           |
| T2    | Inverse timing current constant, sec                           |
| T1    | Inverse timing current constant, sec                           |
| Kfe   | Derivative gain                                                |
| Tfe   | Derivative time constant, sec                                  |

---

<a id="esac1a"></a>

## ESAC1A

*Source: [`Content/TransientModels_HTML/Exciter ESAC1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC1A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va
  - If Vr \> Vrmax , then Vrmax = Vr limits or if Vr limits \< Vrmin, then Vrmin = Vr limits

Model Equations and/or Block Diagrams

![Exciter ESAC1A 0001](images/Exciter_ESAC1A_0001.svg)

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
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Vrmax  | Maximum exciter control signal, pu                             |
| Vrmin  | Minimum exciter control signal, pu                             |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |

---

<a id="esac2a"></a>

## ESAC2A

*Source: [`Content/TransientModels_HTML/Exciter ESAC2A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC2A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kb = 0 then Kb = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va\< Vamin, then Vamin = Va
  - If Vr \> Vrmax , then Vrmax = Vr limits or if Vr limits \< Vrmin, then Vrmin = Vr limits

Model Equations and/or Block Diagrams

![Exciter ESAC2A 0001](images/Exciter_ESAC2A_0001.svg)

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
| Vfemax | Exciter field current limit parameter, pu                      |
| Kh     | Exciter field current feedback gain, pu                        |
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

<a id="esac3a"></a>

## ESAC3A

*Source: [`Content/TransientModels_HTML/Exciter ESAC3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ESAC3A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Kr = 0 then Kr = Mult\*TimeStep
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Va \> Vamax, then Vamax = Va limits or if Va \< Vamin, then Vamin = Va
  - If Ve \< Vfemin, then Vfemin = Ve limits

Model Equations and/or Block Diagrams

![Exciter ESAC3A 0001](images/Exciter_ESAC3A_0001.svg)

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
| Vfemin | Model Parameters\\Vfemin                                       |
| Kr     | Field voltage feedback gain, pu                                |
| Kf     | Rate feedback gain, pu                                         |
| Tf     | Rate feedback constant, sec                                    |
| Kn     | High level rate feedback gain, pu                              |
| Efdn   | Rate feedback gain break level, pu                             |
| Kc     | Rectifier loading factor proportional to commutating reactance |
| Kd     | Exciter internal reactance, pu                                 |
| Ke     | Exciter field resistance constant, pu                          |
| Vfemax | Exciter field current limit parameter, pu                      |
| E1     | Field voltage value, 1                                         |
| SE1    | Saturation factor at E1                                        |
| E2     | Field voltage value, 2                                         |
| SE2    | Saturation factor at E2                                        |
| Spdmlt | If not zero, multiply output (Efd) by generator speed          |
