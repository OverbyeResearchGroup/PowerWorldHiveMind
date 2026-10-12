---
title: "TS Models — Machines and Converters"
part: "Transient Models"
chapter_file: "38-ts-models-machine.md"
topics: 64
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Machines and Converters

Synchronous and converter machine models (GENROU, GENSAL, REGC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (64)**

- [Machine (Converters)](#machine-converters)
- [All](#all)
- [CBattery](#cbattery)
- [CBEST](#cbest)
- [CIMTR1](#cimtr1)
- [CIMTR2](#cimtr2)
- [CIMTR3](#cimtr3)
- [CIMTR4](#cimtr4)
- [CSTATT](#cstatt)
- [CSVGN1](#csvgn1)
- [CSVGN3](#csvgn3)
- [CSVGN4](#csvgn4)
- [CSVGN5](#csvgn5)
- [CSVGN6](#csvgn6)
- [DER_A](#der-a)
- [GENCC](#gencc)
- [GENCLS](#gencls)
- [GENCLS_PLAYBACK](#gencls-playback)
- [GENDCO](#gendco)
- [GENIND](#genind)
- [GENFluxDecay](#genfluxdecay)
- [GENPWTwoAxis](#genpwtwoaxis)
- [GENQEC](#genqec)
- [GENQEJ](#genqej)
- [GENROE](#genroe)
- [GENROU](#genrou)
- [GENSAE](#gensae)
- [GENSAL](#gensal)
- [GENTPF](#gentpf)
- [GENTPJ](#gentpj)
- [GENTRA](#gentra)
- [GENWRI](#genwri)
- [GEWTG](#gewtg)
- [InfiniteBusSignalGen](#infinitebussignalgen)
- [MOTOR1](#motor1)
- [PLAYINGEN](#playingen)
- [PV1G](#pv1g)
- [PVD1](#pvd1)
- [REGC_A](#regc-a)
- [REGC_B](#regc-b)
- [REGC_C](#regc-c)
- [REGFM_A1](#regfm-a1)
- [REGFM_B1](#regfm-b1)
- [REGFM_C1](#regfm-c1)
- [STCON](#stcon)
- [SVCWSC](#svcwsc)
- [VWSCC](#vwscc)
- [WT1G](#wt1g)
- [WT1G1](#wt1g1)
- [WT2G](#wt2g)
- [WT2G1](#wt2g1)
- [WT3G](#wt3g)
- [WT3G1](#wt3g1)
- [WT3G2](#wt3g2)
- [WT4G](#wt4g)
- [WT4G1](#wt4g1)
- [Converter/Renewable](#converterrenewable)
- [Induction](#induction)
- [PlayIn](#playin)
- [Static Var Compensator](#static-var-compensator)
- [Synchronous](#synchronous)
- [BPA Machines](#bpa-machines)
- [GEN_BPA_MMG2](#gen-bpa-mmg2)
- [BPASVC](#bpasvc)

---

<a id="machine-converters"></a>

## Machine (Converters)

*Source: [`Content/TransientModels_HTML/Machine.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/MachineFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="cbattery"></a>

## CBattery

*Source: [`Content/TransientModels_HTML/Machine Model CBattery.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CBattery.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - S1 to S20 and Time1 to Time20: Invalid Time-Apparent Power Curve. Time values must be increasing.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="cbest"></a>

## CBEST

*Source: [`Content/TransientModels_HTML/Machine Model CBEST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CBEST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - T1, T3 and T4:
      - If T1 = T3 for model, T1 and T3 will be ignored (T1=0 and T3=small value).
      - Ff T1 = T4 for model, T1 and T4 will be ignored (T1=0 and T4=0).
  - T2, T3 and T4
      - T2 = T4 for model, T2 and T4 will be ignored (T2=0 and T4=0).
      - T2 = T3 for model, T2 and T3 will be ignored (T2=0 and T3=small value).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CBEST 0001](images/Machine_Model_CBEST_0001.svg)

**Parameters:**

|          |                                     |
| -------- | ----------------------------------- |
| Pmax     | Maximum power, pu                   |
| OutEff   | Output efficiency ( ≥ 1 )           |
| InEff    | Input efficiency ( ≤1 )             |
| Iacmaxpu | IACMAX (pu)                         |
| Kavr     | AVR gain                            |
| T1       | AVR time constant, sec              |
| T2       | AVR time constant, sec              |
| T3       | AVR time constant, sec ( \>0 )      |
| T4       | AVR time constant, sec              |
| Vmax     | Maximum AVR speed limit, pu         |
| Vmin     | Minimum AVR speed limit, pu ( \<0 ) |
| Droop    | DROOP, pu                           |

---

<a id="cimtr1"></a>

## CIMTR1

*Source: [`Content/TransientModels_HTML/Machine Model CIMTR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CIMTR1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpp \< 0.5\*Mult\*TimeStep then Tpp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpp \< Mult\*TimeStep then Tpp = Mult\*TimeStep
  - Xl, Xp, Xpp and Tpp:
      - If Xpp \> 0 and Tpp \> 0 and Xl \>= Xpp then Xl := 0.8\*Xpp
      - If Xl \>= Xp then Xl := 0.5\*Xp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|        |                                                 |
| ------ | ----------------------------------------------- |
| Tp     | T' - Transient rotor time constant              |
| Tpp    | T'' – Sub-transient rotor time constant in sec. |
| H      | Inertia constant in sec.                        |
| X      | Synchronous reactance                           |
| Xp     | X' – Transient Reactance                        |
| Xpp    | X'' – Sub-transient Reactance                   |
| Xl     | Stator leakage reactance in p.u.                |
| E1     | Field voltage value E1                          |
| SE1    | Saturation value at E1                          |
| E2     | Field voltage value E2                          |
| SE2    | Saturation value at E2                          |
| Switch | Switch                                          |
| Ra     | Stator resistance in p.u.                       |

**States:**

1 – Epr

2 – Epi

3 – Ekr

4 – Eki

5 – Speed wr

---

<a id="cimtr2"></a>

## CIMTR2

*Source: [`Content/TransientModels_HTML/Machine Model CIMTR2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CIMTR2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpp \< 0.5\*Mult\*TimeStep then Tpp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpp \< Mult\*TimeStep then Tpp = Mult\*TimeStep
  - Xl, Xp, Xpp and Tpp:
      - If Xpp \> 0 and Tpp \> 0 and Xl \>= Xpp then Xl := 0.8\*Xpp
      - If Xl \>= Xp then Xl := 0.5\*Xp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|     |                                                 |
| --- | ----------------------------------------------- |
| Tp  | T' - Transient rotor time constant              |
| Tpp | T'' – Sub-transient rotor time constant in sec. |
| H   | Inertia constant in sec.                        |
| X   | Synchronous reactance                           |
| Xp  | X' – Transient Reactance                        |
| Xpp | X'' – Sub-transient Reactance                   |
| Xl  | Stator leakage reactance in p.u.                |
| E1  | Field voltage value E1                          |
| SE1 | Saturation value at E1                          |
| E2  | Field voltage value E2                          |
| SE2 | Saturation value at E2                          |
| D   | Damping                                         |

**States:**

1 – Epr

2 – Epi

3 – Ekr

4 – Eki

5 – Speed wr

---

<a id="cimtr3"></a>

## CIMTR3

*Source: [`Content/TransientModels_HTML/Machine Model CIMTR3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CIMTR3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpp \< 0.5\*Mult\*TimeStep then Tpp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpp \< Mult\*TimeStep then Tpp = Mult\*TimeStep
  - Xl, Xp, Xpp and Tpp:
      - If Xpp \> 0 and Tpp \> 0 and Xl \>= Xpp then Xl := 0.8\*Xpp
      - If Xl \>= Xp then Xl := 0.5\*Xp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|         |                                                   |
| ------- | ------------------------------------------------- |
| Tp      | T' - Transient rotor time constant                |
| Tpp     | T'' – Sub-transient rotor time constant in sec.   |
| H       | Inertia constant in sec.                          |
| X       | Synchronous reactance                             |
| Xp      | X' – Transient Reactance                          |
| Xpp     | X'' – Sub-transient Reactance                     |
| Xl      | Stator leakage reactance in p.u.                  |
| E1      | Field voltage value E1                            |
| SE1     | Saturation value at E1                            |
| E2      | Field voltage value E2                            |
| Switch  | Switch                                            |
| SYN-POW | Mechanical power at synchronous speed (p.u. \> 0) |

**States:**

1 – Epr

2 – Epi

3 – Ekr

4 – Eki

5 – Speed wr

---

<a id="cimtr4"></a>

## CIMTR4

*Source: [`Content/TransientModels_HTML/Machine Model CIMTR4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CIMTR4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tpp \< 0.5\*Mult\*TimeStep then Tpp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpp \< Mult\*TimeStep then Tpp = Mult\*TimeStep
  - Xl, Xp, Xpp and Tpp:
      - If Xpp \> 0 and Tpp \> 0 and Xl \>= Xpp then Xl := 0.8\*Xpp
      - If Xl \>= Xp then Xl := 0.5\*Xp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|         |                                                 |
| ------- | ----------------------------------------------- |
| Tp      | T' - Transient rotor time constant              |
| Tpp     | T'' – Sub-transient rotor time constant in sec. |
| H       | Inertia constant in sec.                        |
| X       | Synchronous reactance                           |
| Xp      | X' – Transient Reactance                        |
| Xpp     | X'' – Sub-transient Reactance                   |
| Xl      | Stator leakage reactance in p.u.                |
| E1      | Field voltage value E1                          |
| SE1     | Saturation value at E1                          |
| E2      | Field voltage value E2                          |
| D       | Damping                                         |
| SYN-TOR | Synchronous torque (p.u. \< 0)                  |

**States:**

1 – Epr

2 – Epi

3 – Ekr

4 – Eki

5 – Speed wr

---

<a id="cstatt"></a>

## CSTATT

*Source: [`Content/TransientModels_HTML/Machine Model CSTATT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSTATT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model CSTATT 0001](images/Machine_Model_CSTATT_0001.svg)

**Parameters:**

|         |                                               |
| ------- | --------------------------------------------- |
| T1      | First Lead time constant, sec.                |
| T2      | Second Lead time constant, sec.               |
| T3      | First Lag time constant, sec.                 |
| T4      | Second Lag time constant, sec.                |
| K       | Integrator Multiplier                         |
| DROOP   | Current droop, p.u.                           |
| Vmax    | Lead/Lag Max                                  |
| Vmin    | Lead/Lag Min                                  |
| ICMAX   | ICMAX                                         |
| ILMAX   | ILMAX                                         |
| VCutOff | VCutoff                                       |
| Elimit  | ELimit                                        |
| Xt      | Internal (transformer) reactance, pu on mbase |
| Accel   | Solution acceleration factor                  |

---

<a id="csvgn1"></a>

## CSVGN1

*Source: [`Content/TransientModels_HTML/Machine Model CSVGN1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSVGN1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - Rmin: Generator MVA Base should be approximately equal to the difference between Max Mvar and Min Mvar, if not then Generator MVA Base has been changed to a value which is a difference between Max Mvar and Min Mvar.
  - CBase: CBase should be approximately equal to the Generator Max Mvar value, if not then CBase has been change to a value which is the Generator Max Mvar value.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CSVGN1 0001](images/Machine_Model_CSVGN1_0001.svg)

**Parameters:**

|       |                    |
| ----- | ------------------ |
| K     | Gain, pu           |
| T1    | Time constant, sec |
| T2    | Time constant, sec |
| T3    | Time constant, sec |
| T4    | Time constant, sec |
| T5    | Time constant, sec |
| Rmin  | Reactor min Mvar   |
| Vmax  | Vmax, pu           |
| Vmin  | Vmin, pu           |
| CBase | Capacitor Mvar     |

---

<a id="csvgn3"></a>

## CSVGN3

*Source: [`Content/TransientModels_HTML/Machine Model CSVGN3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSVGN3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - Rmin: Generator MVA Base should be approximately equal to the difference between Max Mvar and Min Mvar, if not then Generator MVA Base has been changed to a value which is a difference between Max Mvar and Min Mvar.
  - CBase: CBase should be approximately equal to the Generator Max Mvar value, if not then CBase has been change to a value which is the Generator Max Mvar value.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CSVGN3 0001](images/Machine_Model_CSVGN3_0001.svg)

**Parameters:**

|       |                      |
| ----- | -------------------- |
| K     | Gain, pu             |
| T1    | Time constant, sec   |
| T2    | Time constant, sec   |
| T3    | Time constant, sec   |
| T4    | Time constant, sec   |
| T5    | Time constant, sec   |
| Rmin  | Reactor min Mvar     |
| Vmax  | Vmax, pu             |
| Vmin  | Vmin, pu             |
| CBase | Capacitor Mvar       |
| Vov   | Override Voltage, pu |

---

<a id="csvgn4"></a>

## CSVGN4

*Source: [`Content/TransientModels_HTML/Machine Model CSVGN4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSVGN4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - Rmin: Generator MVA Base should be approximately equal to the difference between Max Mvar and Min Mvar, if not then Generator MVA Base has been changed to a value which is a difference between Max Mvar and Min Mvar.
  - CBase: CBase should be approximately equal to the Generator Max Mvar value, if not then CBase has been change to a value which is the Generator Max Mvar value.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CSVGN4 0001](images/Machine_Model_CSVGN4_0001.svg)

**Parameters:**

|       |                      |
| ----- | -------------------- |
| K     | Gain, pu             |
| T1    | Time constant, sec   |
| T2    | Time constant, sec   |
| T3    | Time constant, sec   |
| T4    | Time constant, sec   |
| T5    | Time constant, sec   |
| Rmin  | Reactor min Mvar     |
| Vmax  | Vmax, pu             |
| Vmin  | Vmin, pu             |
| CBase | Capacitor Mvar       |
| Vov   | Override Voltage, pu |

---

<a id="csvgn5"></a>

## CSVGN5

*Source: [`Content/TransientModels_HTML/Machine Model CSVGN5.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSVGN5.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Ts3 \< Mult\*TimeStep then Ts3 = Mult\*TimeStep
  - If 0.0 \< Ts1 \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ts5 \< 0.5\*Mult\*TimeStep then Ts5 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts5 \< Mult\*TimeStep then Ts5 = Mult\*TimeStep
  - If 0.0 \< Ts6 \< 0.5\*Mult\*TimeStep then Ts6 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts6 \< Mult\*TimeStep then Ts6 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CSVGN5 0001](images/Machine_Model_CSVGN5_0001.svg)

**Parameters:**

|       |                         |
| ----- | ----------------------- |
| Ts1   | Time constant, sec      |
| Vemax | Vemax, pu               |
| Ts2   | Lead time constant, sec |
| Ts3   | Lag time constant, sec  |
| Ts4   | Lead time constant, sec |
| Ts5   | Lag time constant, sec  |
| Ksvs  | Gain, pu                |
| Ksd   | Gain, pu                |
| Bmax  | Bmax, pu                |
| Bpmax | Bpmax, pu               |
| Bpmin | Bpmin, pu               |
| Bmin  | Bmin, pu                |
| Ts6   | Time constant, sec      |
| DV    | DV                      |

---

<a id="csvgn6"></a>

## CSVGN6

*Source: [`Content/TransientModels_HTML/Machine Model CSVGN6.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model CSVGN6.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Ts3 \< Mult\*TimeStep then Ts3 = Mult\*TimeStep
  - If 0.0 \< Ts1 \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Ts5 \< 0.5\*Mult\*TimeStep then Ts5 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts5 \< Mult\*TimeStep then Ts5 = Mult\*TimeStep
  - If 0.0 \< Ts6 \< 0.5\*Mult\*TimeStep then Ts6 = 0, ElseIf 0.5\*Mult\*TimeStep \< Ts6 \< Mult\*TimeStep then Ts6 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model CSVGN6 0001](images/Machine_Model_CSVGN6_0001.svg)

**Parameters:**

|        |                         |
| ------ | ----------------------- |
| Ts1    | Time constant, sec      |
| Vemax  | Vemax, pu               |
| Ts2    | Lead time constant, sec |
| Ts3    | Lag time constant, sec  |
| Ts4    | Lead time constant, sec |
| Ts5    | Lag time constant, sec  |
| Ksvs   | Gain, pu                |
| Ksd    | Gain, pu                |
| Bmax   | Bmax, pu                |
| Bpmax  | Bpmax, pu               |
| Bpmin  | Bpmin, pu               |
| Bmin   | Bmin, pu                |
| Ts6    | Time constant, sec      |
| DV     | DV                      |
| Vemin  | Vemin, pu               |
| Vmax   | Vmax, pu                |
| Vmin   | Vmin, pu                |
| Bias   | Bias                    |
| DV2    | DV2                     |
| Bshunt | Bshunt                  |
| Tdelay | Tdelay, sec             |

---

<a id="der-a"></a>

## DER_A

*Source: [`Content/TransientModels_HTML/Machine Model DER_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model DER_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Trv \< 0.5\*Mult\*TimeStep then Trv = 0, ElseIf 0.5\*Mult\*TimeStep \< Trv \< Mult\*TimeStep then Trv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - Only the absolute value of the deadband values are used (dbd1, dbd2, fdbd1, and fdbd2)
  - Only the absolute value of the droop values Ddn and Dup will be used
  - If Vl0 \< Vl1 then the parameters Vl0 and Vl1 will be treated as though they are 0.0 (we'll ignore the low voltage tripping)
  - If Vh1 \< Vh0 then the parameters Vh0 and Vh1 will be treated as though they are infinite (we'll ignore the high voltage tripping)
  - If Vrfrac \< 0 it will be treated as 0. If Vrfac \> 1.0 it will be treated as 1.0
  - If Tg \< 4\*TimeStep then Tg will use 4\*TimeStep, and if Tg \> 0.2 then Tg = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model DER A 0001](images/Machine_Model_DER_A_0001.svg)

**Parameters:**

|           |                                                                                                                                                                                                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PfFlag    | PfFlag: 0 means for constant Q control; 1 means constant power factor control (any number which is not 0 is treated as 1)                                                                                                                                                       |
| FreqFlag  | FreqFlag: 0 means frequency control disabled; 1 means frequency control enabled (any number which is not 0 is treated as 1)                                                                                                                                                     |
| PQFlag    | PQFlag: 0 means Q priority; 1 means P priority for current limit (any number which is not 0 is treated as 1)                                                                                                                                                                    |
| TypeFlag  | TypeFlag: 0 means the unit is a storage device and Ipmin = - Ipmax; 1 means the unit is a generator Ipmin = 0 (any number which is not 0 is treated as 1)                                                                                                                       |
| VtripFlag | VtripFlag: 0 means disable the voltage trip logic; 1 means enable the voltage trip logic (any number which is not 0 is treated as 1)                                                                                                                                            |
| FtripFlag | FtripFlag: 0 means disable the frequency trip logic; 1 means enable the frequency trip logic (any number which is not 0 is treated as 1)                                                                                                                                        |
| Trv       | Trv: transducer time constant (seconds) for voltage measurement (can be zero)                                                                                                                                                                                                   |
| Trf       | Trf: transducer time constant (seconds) for frequency measurement (\> 0)                                                                                                                                                                                                        |
| dbd1      | dbd1: lower voltage deadband \<= 0 (pu)                                                                                                                                                                                                                                         |
| dbd2      | dbd2: upper voltage deadband \>= 0 (pu)                                                                                                                                                                                                                                         |
| Kqv       | Kqv: proportional voltage control gain (pu/pu)                                                                                                                                                                                                                                  |
| Vref0     | Vref0: voltage reference set-point (pu)                                                                                                                                                                                                                                         |
| Tp        | Tp: transducer time constant (seconds)                                                                                                                                                                                                                                          |
| Tiq       | Tiq: Q control time constant (seconds)                                                                                                                                                                                                                                          |
| Ddn       | Ddn: frequency control droop gain \>= 0 (down-side)                                                                                                                                                                                                                             |
| Dup       | Dup: frequency control droop gain \>= 0 (up-side)                                                                                                                                                                                                                               |
| fdbd1     | fdbd1: lower frequency control deadband \<= 0 (pu)                                                                                                                                                                                                                              |
| fdbd2     | fdbd2: upper frequency control deadband \>= 0 (pu)                                                                                                                                                                                                                              |
| femax     | femax: frequency control maximum error (pu) \>= 0                                                                                                                                                                                                                               |
| femin     | femin: frequency control minimum error (pu) \<= 0                                                                                                                                                                                                                               |
| Pmax      | Pmax: Maximum power (pu)                                                                                                                                                                                                                                                        |
| Pmin      | Pmin: Minimum power (pu)                                                                                                                                                                                                                                                        |
| dPmax     | dPmax: Power ramp rate up \>= 0 (pu/s)                                                                                                                                                                                                                                          |
| dPmin     | dPmin: Power ramp rate down \<= 0 (pu/s)                                                                                                                                                                                                                                        |
| Tpord     | Tpord: Power order time constant (seconds)                                                                                                                                                                                                                                      |
| Kpg       | Kpg: active power control proportional gain                                                                                                                                                                                                                                     |
| Kig       | Kig: active power control integral gain                                                                                                                                                                                                                                         |
| Imax      | Imax: Maximum converter current (pu)                                                                                                                                                                                                                                            |
| Vl0       | Vl0: voltage break-point for low voltage cut-out of the inverter (Multiplier = 0.0 at this voltage)                                                                                                                                                                             |
| Vl1       | Vl1: voltage break-point for low voltage cut-out of the inverter (Multiplier = 1.0 at this voltage)                                                                                                                                                                             |
| Vh0       | Vh0: voltage break-point for high voltage cut-out of the inverter (Multiplier = 0.0 at this voltage)                                                                                                                                                                            |
| Vh1       | Vh1: voltage break-point for high voltage cut-out of the inverter (Multiplier = 1.0 at this voltage)                                                                                                                                                                            |
| Tvl0      | Tvl0: voltage break-point for low voltage cut-out timer (If voltage stays below vl0 for more than tvl0 seconds, then the multiplier will remain zero for the simulation)                                                                                                        |
| Tvl1      | Tvl1: voltage break-point for low voltage cut-out timer (If voltage stays below vl1 for more than tvl1 seconds, then the multiplier will track a depressed curve according to Vrfrac and an internally tracked value of the minimum voltage experienced during the simulation)  |
| Tvh0      | Tvh0: voltage break-point for high voltage cut-out timer (If voltage stays above vl0 for more than tvl0 seconds, then the multiplier will remain zero for the simulation)                                                                                                       |
| Tvh1      | Tvh1: voltage break-point for high voltage cut-out timer (If voltage stays above vl1 for more than tvl1 seconds, then the multiplier will track a depressed curve according to Vrfrac and an internally tracked value of the maximum voltage experienced during the simulation) |
| Vrfrac    | Vrfrac: fraction of device that recovers after voltage comes back to within vl1 \< V \< vh1 (Note that the timers Tvl1 and Tvh1 also impact when this fraction is used)                                                                                                         |
| Tv        | Tv: time constant on the output of the voltage cut-out                                                                                                                                                                                                                          |
| fl        | fl: frequency break-point for low frequency cut-out of the inverter (Hertz)                                                                                                                                                                                                     |
| fh        | fh: frequency break-point for high frequency cut-out of the inverter (Hertz)                                                                                                                                                                                                    |
| Tfl       | Tfl: frequency break-point for low frequency cut-out timer (seconds) (highly recommend that Tfl \> Trf)                                                                                                                                                                         |
| Tfh       | Tfh: frequency break-point for high frequency cut-out timer (seconds) (highly recommend that Tfh \> Trf)                                                                                                                                                                        |
| Vpr       | Vpr: voltage below which frequency tripping is disabled (pu)                                                                                                                                                                                                                    |
| Tg        | Tg: Current control time constant                                                                                                                                                                                                                                               |
| rrpwr     | rrpwr: Power rise ramp rate following a fault \>= 0 (pu/s)                                                                                                                                                                                                                      |
| Xe        | Xe: Generator effective reactive (pu) \> 0                                                                                                                                                                                                                                      |
| Iqh1      | Iqh1: Maximum limit of reactive current injection, p.u.                                                                                                                                                                                                                         |
| Iql1      | Iql1: Minimum limit of reactive current injection, p.u.                                                                                                                                                                                                                         |

![Machine Model DER A 0002](images/Machine_Model_DER_A_0002.svg)

![Machine Model DER A 0003](images/Machine_Model_DER_A_0003.svg)

---

<a id="gencc"></a>

## GENCC

*Source: [`Content/TransientModels_HTML/Machine Model GENCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENCC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp (not done if Tdopp = 0)
  - If Xdpp \< 0.05 then Xdpp = 0.05 (not done if Tdopp = 0)
  - If Xqp \> Xq then Xqp = Xq
  - If Xqpp \> Xqp then Xqpp = 0.8\*Xqp
  - If (Tdopp \> 0) and (Tqop = 0) and (Xqpp \> 0.25\*Xq) then Xqpp = 0.25\*Xq
  - If Xqpp \> 1.5\*Xdpp then Xqpp = 1.5\*Xdpp
  - If Xqpp \< 0.01\*Xdpp then Xqpp = Xdpp (*assume near zero value was a mistake and set equal*)  
    Else if Xqpp \< 0.5\*Xdpp then Xqpp = 0.5\*Xdpp (*don't allow them to be wildly different*)
  - Xqp: Check if Xqp = 0 which means that Xqp = Xq, then Xqp is changed to Xq. Also if Xqp = 0, but Tqop = 0 which indicates that you must have Xqp = Xq. Xqp will be treated as though it is equal to Xq.
  - if XComp \> = 0 then XComp = -0.01.

Model Equations and/or Block Diagrams

![Machine Model GENCC 0001](images/Machine_Model_GENCC_0001.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xqpp  | Quadrature axis subtransient reactance              |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |
| Accel | Acceleration factor                                 |
| Pfac  | Real power participation faction                    |
| Qfac  | Reactive power participation faction                |

---

<a id="gencls"></a>

## GENCLS

*Source: [`Content/TransientModels_HTML/Machine Model GENCLS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENCLS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \< 0.00001 then Xdp = 0.00001, and if Xdp \> 999 then Xdp = 999

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model GENCLS PLAYBACK 0001](images/Machine_Model_GENCLS_PLAYBACK_0001.svg)

**Parameters:**

|       |                                                 |
| ----- | ----------------------------------------------- |
| H     | Inertia constant, sec                           |
| D     | Damping factor, pu                              |
| Ra    | Stator resistance, pu                           |
| Xdp   | Direct axis transient reactance                 |
| RComp | Compensating resistance for voltage control, pu |
| XComp | Compensating reactance for voltage control, pu  |

---

<a id="gencls-playback"></a>

## GENCLS_PLAYBACK

*Source: [`Content/TransientModels_HTML/Machine Model GENCLS_PLAYBACK.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENCLS_PLAYBACK.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model GENCLS PLAYBACK 0001](images/Machine_Model_GENCLS_PLAYBACK_0001.svg)

**Parameters:**

|                |                                                                               |
| -------------- | ----------------------------------------------------------------------------- |
| TSPlayBackFile | Playback Filename                                                             |
| H              | Inertia constant, sec                                                         |
| D              | Damping factor, pu                                                            |
| Ra             | Stator resistance, pu                                                         |
| Xdp            | Direct axis transient reactance                                               |
| RComp\_VBias   | Compensating resistance (pu) or voltage bias (pu) if model has playback file  |
| XComp\_FBias   | Compensating reactance (pu) or frequency bias (pu) if model has playback file |
| t0             | Starting time for playback, sec                                               |
| tf0            | Filtering time constant for playback channel 0                                |
| tf1            | Filtering time constant for playback channel 1                                |
| tf2            | Filtering time constant for playback channel 2                                |
| tf3            | Filtering time constant for playback channel 3                                |
| tf4            | Filtering time constant for playback channel 4                                |

---

<a id="gendco"></a>

## GENDCO

*Source: [`Content/TransientModels_HTML/Machine Model GENDCO.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENDCO.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Minimum(Xdp, Xqp) then Xdpp = 0.8\*Minimum(Xdp, Xqp)
  - If Xdpp \< 0.05 then Xdpp = 0.05
  - If Xqp \> Xq then Xqp = Xq
  - If Xl \>Xdpp then Xl = 0.8\*Xdpp
  - Ta: Warning message - GENDCO models presently are treated the same as GENROU models in Simulator. The DC offset is ignored and the Ta term ignored.

Model Equations and/or Block Diagrams

![Machine Model GENDCO 0001](images/Machine_Model_GENDCO_0001.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| Ta    | Time constant, sec (Not used in PowerWorld)         |

---

<a id="genind"></a>

## GENIND

*Source: [`Content/TransientModels_HTML/Machine Model GENIND.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENIND.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model GENIND 0001](images/Machine_Model_GENIND_0001.svg)

**Parameters:**

|       |                                        |
| ----- | -------------------------------------- |
| Ls    | Synchrounous reactance, (pu \> 0)      |
| Lp    | Transient reactance (pu, \> 0)         |
| Ra    | Stator resistance, pu                  |
| Tpo   | Transient rotor time constant, sec     |
| H     | Inertia constant, sec                  |
| D     | Damping factor, pu                     |
| SE1   | Saturation factor at E1                |
| SE2   | Saturation factor at E2                |
| Acc   | Acceleration factor for initialization |
| Lpp   | Sub-transient reactance (pu, \> 0)     |
| Ll    | Stator leakage reactance (pu, \> 0)    |
| Tppo  | Sub-transient rotor time constant, sec |
| ndelt | Model Parameters\\ndelt                |
| wdelt | Model Parameters\\wdelt                |
| VT    | Voltage threshold for tripping, pu     |
| TV    | Voltage trip pickup time, sec          |

---

<a id="genfluxdecay"></a>

## GENFluxDecay

*Source: [`Content/TransientModels_HTML/Machine Model GENPWFluxDecay.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENPWFluxDecay.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tdop \< 0.5\*Mult\*TimeStep then Tdop = 0.5\*Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|                          |                                                             |
| ------------------------ | ----------------------------------------------------------- |
| H                        | Inertia constant, sec                                       |
| D                        | Damping factor, pu                                          |
| Ra                       | Stator resistance, pu                                       |
| Xd                       | Open circuit direct axis transient time constant            |
| Xq                       | Quadrature axis synchronous reactance                       |
| Xdp                      | Direct axis transient reactance                             |
| Tdop                     | Open circuit direct axis transient time constant            |
| S1                       | Saturation factor at 1.0 pu flux                            |
| S12                      | Saturation factor at 1.2 pu flux                            |
| IgnoreStatorVoltageSpeed | If 1 ignore stator voltage speed effects; otherwise include |

---

<a id="genpwtwoaxis"></a>

## GENPWTwoAxis

*Source: [`Content/TransientModels_HTML/Machine Model GENPWTwoAxis.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENPWTwoAxis.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tdop \< 0.5\*Mult\*TimeStep then Tdop = 0.5\*Mult\*TimeStep
  - If 0 \< Tqop \< 0.5\*Mult\*TimeStep then Tqop = 0.5\*Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model GENPWTwoAxis 0001](images/Machine_Model_GENPWTwoAxis_0001.svg)

**Parameters:**

|      |                                                  |
| ---- | ------------------------------------------------ |
| H    | Inertia constant, sec                            |
| D    | Damping factor, pu                               |
| Ra   | Stator resistance, pu                            |
| Xd   | Direct axis synchronous reactance                |
| Xq   | Quadrature axis synchronous reactance            |
| Xdp  | Direct axis transient reactance                  |
| Xqp  | Quadrature axis transient reactance              |
| Tdop | Open circuit direct axis transient time constant |
| Tqop | Quadrature axis transient time constant          |

---

<a id="genqec"></a>

## GENQEC

*Source: [`Content/TransientModels_HTML/Machine Model GENQEC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENQEC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp (not done if Tdopp = 0)
  - If Xdpp \< 0.05 then Xdpp = 0.05 (not done if Tdopp = 0)
  - If Xqp \> Xq then Xqp = Xq
  - If Xqpp \> Xqp then Xqpp = 0.8\*Xqp
  - If (Tdopp \> 0) and (Tqop = 0) and (Xqpp \> 0.25\*Xq) then Xqpp = 0.25\*Xq
  - If Xqpp \> 1.5\*Xdpp then Xqpp = 1.5\*Xdpp
  - If Xqpp \< 0.01\*Xdpp then Xqpp = Xdpp (*assume near zero value was a mistake and set equal*)  
    Else if Xqpp \< 0.5\*Xdpp then Xqpp = 0.5\*Xdpp (*don't allow them to be wildly different*)
  - If Xl \>Minimum(Xdpp, Xqpp) then Xl = 0.8\*Minimum(Xdpp, Xqpp)
  - Xqp: Check if Xqp = 0 which means that Xqp = Xq, then Xqp is changed to Xq. Also if Xqp = 0, but Tqop = 0 which indicates that you must have Xqp = Xq. Xqp will be treated as though it is equal to Xq.

Model Equations and/or Block Diagrams

![Machine Model GENQEC 0001](images/Machine_Model_GENQEC_0001.svg)

**Parameters:**

|         |                                                               |
| ------- | ------------------------------------------------------------- |
| H       | Inertia constant, sec                                         |
| D       | Damping factor, pu                                            |
| Ra      | Stator resistance, pu                                         |
| Xd      | Direct axis synchronous reactance                             |
| Xq      | Quadrature axis synchronous reactance                         |
| Xdp     | Direct axis transient reactance                               |
| Xqp     | Quadrature axis transient reactance                           |
| Xdpp    | Direct axis subtransient reactance                            |
| Xqpp    | Quadrature axis subtransient reactance                        |
| Xl      | Stator leakage reactance                                      |
| Tdop    | Open circuit direct axis transient time constant              |
| Tqop    | Quadrature axis transient time constant                       |
| Tdopp   | Open circuit direct axis subtransient time constant           |
| Tqopp   | Quadrature axis subtransient time constant                    |
| S1      | Saturation factor at 1.0 pu flux                              |
| S12     | Saturation factor at 1.2 pu flux                              |
| RComp   | Compensating resistance for voltage control, pu               |
| XComp   | Compensating reactance for voltage control, pu                |
| Accel   | Acceleration factor                                           |
| Kw      | Current multiplier on Idw for additional saturation on d-axis |
| SatFunc | SatFunc; 0 = exponential; 1 = Scaled Quadratic; 2 = Quadratic |

![Machine Model GENQEC 0002](images/Machine_Model_GENQEC_0002.svg)

![Machine Model GENQEC 0003](images/Machine_Model_GENQEC_0003.svg)

![Machine Model GENQEC 0004](images/Machine_Model_GENQEC_0004.svg)

![Machine Model GENQEC 0005](images/Machine_Model_GENQEC_0005.svg)

![Machine Model GENQEC 0006](images/Machine_Model_GENQEC_0006.svg)

![Machine Model GENQEC 0007](images/Machine_Model_GENQEC_0007.svg)

![Machine Model GENQEC 0008](images/Machine_Model_GENQEC_0008.svg)

![Machine Model GENQEC 0009](images/Machine_Model_GENQEC_0009.svg)

---

<a id="genqej"></a>

## GENQEJ

*Source: [`Content/TransientModels_HTML/Machine Model GENQEJ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENQEJ.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp (not done if Tdopp = 0)
  - If Xdpp \< 0.05 then Xdpp = 0.05 (not done if Tdopp = 0)
  - If Xqp \> Xq then Xqp = Xq
  - If Xqpp \> Xqp then Xqpp = 0.8\*Xqp
  - If (Tdopp \> 0) and (Tqop = 0) and (Xqpp \> 0.25\*Xq) then Xqpp = 0.25\*Xq
  - If Xqpp \> 1.5\*Xdpp then Xqpp = 1.5\*Xdpp
  - If Xqpp \< 0.01\*Xdpp then Xqpp = Xdpp (*assume near zero value was a mistake and set equal*)  
    Else if Xqpp \< 0.5\*Xdpp then Xqpp = 0.5\*Xdpp (*don't allow them to be wildly different*)
  - If Xl \>Minimum(Xdpp, Xqpp) then Xl = 0.8\*Minimum(Xdpp, Xqpp)
  - Xqp: Check if Xqp = 0 which means that Xqp = Xq, then Xqp is changed to Xq. Also if Xqp = 0, but Tqop = 0 which indicates that you must have Xqp = Xq. Xqp will be treated as though it is equal to Xq.

Model Equations and/or Block Diagrams

![Machine Model GENQEJ 0001](images/Machine_Model_GENQEJ_0001.svg)

**Parameters:**

|         |                                                               |
| ------- | ------------------------------------------------------------- |
| H       | Inertia constant, sec                                         |
| D       | Damping factor, pu                                            |
| Ra      | Stator resistance, pu                                         |
| Xd      | Direct axis synchronous reactance                             |
| Xq      | Quadrature axis synchronous reactance                         |
| Xdp     | Direct axis transient reactance                               |
| Xqp     | Quadrature axis transient reactance                           |
| Xdpp    | Direct axis subtransient reactance                            |
| Xqpp    | Quadrature axis subtransient reactance                        |
| Xl      | Stator leakage reactance                                      |
| Tdop    | Open circuit direct axis transient time constant              |
| Tqop    | Quadrature axis transient time constant                       |
| Tdopp   | Open circuit direct axis subtransient time constant           |
| Tqopp   | Quadrature axis subtransient time constant                    |
| S1      | Saturation factor at 1.0 pu flux                              |
| S12     | Saturation factor at 1.2 pu flux                              |
| RComp   | Compensating resistance for voltage control, pu               |
| XComp   | Compensating reactance for voltage control, pu                |
| Accel   | Acceleration factor                                           |
| Kis     | Current multiplier for saturation calculation                 |
| SatFunc | SatFunc; 0 = exponential; 1 = Scaled Quadratic; 2 = Quadratic |

![Machine Model GENQEJ 0002](images/Machine_Model_GENQEJ_0002.svg)

![Machine Model GENQEJ 0003](images/Machine_Model_GENQEJ_0003.svg)

![Machine Model GENQEJ 0004](images/Machine_Model_GENQEJ_0004.svg)

![Machine Model GENQEJ 0005](images/Machine_Model_GENQEJ_0005.svg)

![Machine Model GENQEJ 0006](images/Machine_Model_GENQEJ_0006.svg)

![Machine Model GENQEJ 0007](images/Machine_Model_GENQEJ_0007.svg)

![Machine Model GENQEJ 0008](images/Machine_Model_GENQEJ_0008.svg)

![Machine Model GENQEJ 0009](images/Machine_Model_GENQEJ_0009.svg)

---

<a id="genroe"></a>

## GENROE

*Source: [`Content/TransientModels_HTML/Machine Model GENROE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENROE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Minimum(Xdp, Xqp) then Xdpp = 0.8\*Minimum(Xdp, Xqp)
  - If Xdpp \< 0.05 then Xdpp = 0.05
  - If Xqp \> Xq then Xqp = Xq
  - If Xl \>Xdpp then Xl = 0.8\*Xdpp

Model Equations and/or Block Diagrams

**Round Rotor Generator Model GENROEInduction Generator Model CIMTR1**

Same as the GENROU model, except that an exponential function is used for saturation.

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |

---

<a id="genrou"></a>

## GENROU

*Source: [`Content/TransientModels_HTML/Machine Model GENROU.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENROU.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Minimum(Xdp, Xqp) then Xdpp = 0.8\*Minimum(Xdp, Xqp)
  - If Xdpp \< 0.05 then Xdpp = 0.05
  - If Xqp \> Xq then Xqp = Xq
  - If Xl \>Xdpp then Xl = 0.8\*Xdpp

Model Equations and/or Block Diagrams

![Machine Model GENROU 0001](images/Machine_Model_GENROU_0001.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |

![Machine Model GENROU 0002](images/Machine_Model_GENROU_0002.svg)

---

<a id="gensae"></a>

## GENSAE

*Source: [`Content/TransientModels_HTML/Machine Model GENSAE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENSAE.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp
  - If Xdpp \< 0.05 then Xdpp = 0.05
  - If Xl \>Xdpp then Xl = 0.8\*Xdpp

Model Equations and/or Block Diagrams

**Machine Model GENSAE**

Same as the GENSAL model, except that an exponential function is used for saturation.

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xdpp  | Direct axis subtransient reactance                  |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |

---

<a id="gensal"></a>

## GENSAL

*Source: [`Content/TransientModels_HTML/Machine Model GENSAL.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENSAL.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp
  - If Xdpp \< 0.05 then Xdpp = 0.05
  - If Xl \>Xdpp then Xl = 0.8\*Xdpp

Model Equations and/or Block Diagrams

![Machine Model GENSAL 0001](images/Machine_Model_GENSAL_0001.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xdpp  | Direct axis subtransient reactance                  |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |

![Machine Model GENSAL 0002](images/Machine_Model_GENSAL_0002.svg)

---

<a id="gentpf"></a>

## GENTPF

*Source: [`Content/TransientModels_HTML/Machine Model GENTPF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENTPF.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp (not done if Tdopp = 0)
  - If Xdpp \< 0.05 then Xdpp = 0.05 (not done if Tdopp = 0)
  - If Xqp \> Xq then Xqp = Xq
  - If Xqpp \> Xqp then Xqpp = 0.8\*Xqp
  - If (Tdopp \> 0) and (Tqop = 0) and (Xqpp \> 0.25\*Xq) then Xqpp = 0.25\*Xq
  - If Xqpp \> 1.5\*Xdpp then Xqpp = 1.5\*Xdpp
  - If Xqpp \< 0.01\*Xdpp then Xqpp = Xdpp (*assume near zero value was a mistake and set equal*)  
    Else if Xqpp \< 0.5\*Xdpp then Xqpp = 0.5\*Xdpp (*don't allow them to be wildly different*)
  - Xqp: Check if Xqp = 0 which means that Xqp = Xq, then Xqp is changed to Xq. Also if Xqp = 0, but Tqop = 0 which indicates that you must have Xqp = Xq. Xqp will be treated as though it is equal to Xq.

Model Equations and/or Block Diagrams

![Machine Model GENTPF 0001](images/Machine_Model_GENTPF_0001.svg)

![Machine Model GENTPF 0002](images/Machine_Model_GENTPF_0002.svg)

![Machine Model GENTPF 0003](images/Machine_Model_GENTPF_0003.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xqpp  | Quadrature axis subtransient reactance              |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |
| Accel | Acceleration factor                                 |

---

<a id="gentpj"></a>

## GENTPJ

*Source: [`Content/TransientModels_HTML/Machine Model GENTPJ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENTPJ.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Xdp \> Xd then Xdp = 0.8\*Xd
  - If Xdpp \> Xdp then Xdpp = 0.8\*Xdp (not done if Tdopp = 0)
  - If Xdpp \< 0.05 then Xdpp = 0.05 (not done if Tdopp = 0)
  - If Xqp \> Xq then Xqp = Xq
  - If Xqpp \> Xqp then Xqpp = 0.8\*Xqp
  - If (Tdopp \> 0) and (Tqop = 0) and (Xqpp \> 0.25\*Xq) then Xqpp = 0.25\*Xq
  - If Xqpp \> 1.5\*Xdpp then Xqpp = 1.5\*Xdpp
  - If Xqpp \< 0.01\*Xdpp then Xqpp = Xdpp (*assume near zero value was a mistake and set equal*)  
    Else if Xqpp \< 0.5\*Xdpp then Xqpp = 0.5\*Xdpp (*don't allow them to be wildly different*)
  - Xqp: Check if Xqp = 0 which means that Xqp = Xq, then Xqp is changed to Xq. Also if Xqp = 0, but Tqop = 0 which indicates that you must have Xqp = Xq. Xqp will be treated as though it is equal to Xq.

Model Equations and/or Block Diagrams

![Machine Model GENTPJ 0001](images/Machine_Model_GENTPJ_0001.svg)

**Parameters:**

|       |                                                     |
| ----- | --------------------------------------------------- |
| H     | Inertia constant, sec                               |
| D     | Damping factor, pu                                  |
| Ra    | Stator resistance, pu                               |
| Xd    | Direct axis synchronous reactance                   |
| Xq    | Quadrature axis synchronous reactance               |
| Xdp   | Direct axis transient reactance                     |
| Xqp   | Quadrature axis transient reactance                 |
| Xdpp  | Direct axis subtransient reactance                  |
| Xqpp  | Quadrature axis subtransient reactance              |
| Xl    | Stator leakage reactance                            |
| Tdop  | Open circuit direct axis transient time constant    |
| Tqop  | Quadrature axis transient time constant             |
| Tdopp | Open circuit direct axis subtransient time constant |
| Tqopp | Quadrature axis subtransient time constant          |
| S1    | Saturation factor at 1.0 pu flux                    |
| S12   | Saturation factor at 1.2 pu flux                    |
| RComp | Compensating resistance for voltage control, pu     |
| XComp | Compensating reactance for voltage control, pu      |
| Accel | Acceleration factor                                 |
| Kis   | Current multiplier for saturation calculation       |

---

<a id="gentra"></a>

## GENTRA

*Source: [`Content/TransientModels_HTML/Machine Model GENTRA.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENTRA.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model GENTRA 0001](images/Machine_Model_GENTRA_0001.svg)

**Parameters:**

|      |                                                  |
| ---- | ------------------------------------------------ |
| Ra   | Stator resistance, pu                            |
| Tdop | Open circuit direct axis transient time constant |
| H    | Inertia constant, sec                            |
| D    | Damping factor, pu                               |
| Xd   | Direct axis synchronous reactance                |
| Xq   | Quadrature axis synchronous reactance            |
| Xdp  | Direct axis transient reactance                  |
| S1   | Saturation factor at 1.0 pu flux                 |
| S12  | Saturation factor at 1.2 pu flux                 |
| Af   | Af                                               |

---

<a id="genwri"></a>

## GENWRI

*Source: [`Content/TransientModels_HTML/Machine Model GENWRI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GENWRI.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model GENWRI 0001](images/Machine_Model_GENWRI_0001.svg)

**Parameters:**

|        |                                                          |
| ------ | -------------------------------------------------------- |
| Ls     | Synchrounous reactance, (pu \> 0)                        |
| Lp     | Transient reactance (pu, \> 0)                           |
| Ll     | Stator leakage reactance (pu, \> 0)                      |
| Ra     | Stator resistance, pu                                    |
| Tpo    | Transient rotor time constant, sec                       |
| H      | Inertia constant, sec                                    |
| D      | Not used                                                 |
| S1     | Saturation factor at 1.0 pu flux                         |
| S12    | Saturation factor at 1.2 pu flux                         |
| spdrot | Initial electrical rotor speed, p.u. of system frequency |
| Acc    | Acceleration factor for initialization                   |

---

<a id="gewtg"></a>

## GEWTG

*Source: [`Content/TransientModels_HTML/Machine Model GEWTG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GEWTG.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - fcflg:
      - If exciter is EWTGFC and model has (fcflg = 1) indicating it is a full converter model, however it is using the DFAG electrical model EXWTGE instead. Parameter fcflag changed to 0 to match this.
      - If exciter is EXWTGE and model has (fcflg = 0) indicating it is a DFAG model, however it is using the full converter electrical model EXWTG instead. Parameter fcflag changed to 1 to match this.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model GEWTG 0001](images/Machine_Model_GEWTG_0001.svg)

![Machine Model GEWTG 0002](images/Machine_Model_GEWTG_0002.svg)

**Parameters:**

|        |                                                                             |
| ------ | --------------------------------------------------------------------------- |
| Lpp    | Generator effective reactive, p.u.                                          |
| dVtrp1 | Delta Voltage Trip Level 1, p.u.                                            |
| dVtrp2 | Delta Voltage Trip Level 2, p.u.                                            |
| dVtrp3 | Delta Voltage Trip Level 3, p.u.                                            |
| dVtrp4 | Delta Voltage Trip Level 4, p.u.                                            |
| dVtrp5 | Delta Voltage Trip Level 5, p.u.                                            |
| dVtrp6 | Delta Voltage Trip Level 6, p.u.                                            |
| dTtrp1 | Voltage Trip Time 1, sec.                                                   |
| dTtrp2 | Voltage Trip Time 2, sec.                                                   |
| dTtrp3 | Voltage Trip Time 3, sec.                                                   |
| dTtrp4 | Voltage Trip Time 4, sec.                                                   |
| dTtrp5 | Voltage Trip Time 5, sec.                                                   |
| dTtrp6 | Voltage Trip Time 6, sec.                                                   |
| fcflg  | Flag: 0 = Doubly Fed Asynchronous Generator (DFAG); 1 = Full Converter (FC) |
| rrpwr  | LVPL ramprate limit, p.u.                                                   |
| brkpt  | LVPL characteristic breakpoint voltage, p.u.                                |
| zerox  | LVPL characteristic zero crossing voltage, p.u.                             |

---

<a id="infinitebussignalgen"></a>

## InfiniteBusSignalGen

*Source: [`Content/TransientModels_HTML/Machine Model InfiniteBusSignalGen.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model InfiniteBusSignalGen.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model InfiniteBusSignalGen 0001](images/Machine_Model_InfiniteBusSignalGen_0001.svg)

![Machine Model InfiniteBusSignalGen 0002](images/Machine_Model_InfiniteBusSignalGen_0002.svg)

![Machine Model InfiniteBusSignalGen 0003](images/Machine_Model_InfiniteBusSignalGen_0003.svg)

---

<a id="motor1"></a>

## MOTOR1

*Source: [`Content/TransientModels_HTML/Machine Model MOTOR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model MOTOR1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If H \< 0.1, then H = 0.1

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model MOTOR1 0001](images/Machine_Model_MOTOR1_0001.svg)

**Parameters:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Ls    | Synchrounous reactance, (pu \> 0)              |
| Lp    | Transient reactance (pu, \> 0)                 |
| Ra    | Stator resistance, pu                          |
| Tpo   | Transient rotor time constant, sec             |
| H     | Inertia constant, sec                          |
| D     | Damping factor, pu                             |
| SE1   | Saturation factor at E1                        |
| SE2   | Saturation factor at E2                        |
| VT    | Voltage threshold for tripping, pu             |
| TV    | Voltage trip pickup time, sec                  |
| FT    | Frequency deviation threshold for tripping, Hz |
| Tf    | Frequency trip pickup time, sec                |
| Vr    | Voltage at which reconnection is permitted, pu |
| Tvr   | Time delay for reconnection, sec               |
| Acc   | Acceleration factor for initialization         |
| Lpp   | Sub-transient reactance (pu, \> 0)             |
| Ll    | Stator leakage reactance (pu, \> 0)            |
| Tppo  | Sub-transient rotor time constant, sec         |
| ndelt | Time step subdivision factor.                  |
| wdelt | Speed threshold for subdividing time step, pu  |

---

<a id="playingen"></a>

## PLAYINGEN

*Source: [`Content/TransientModels_HTML/Machine Model PLAYINGEN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model PLAYINGEN.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model PLAYINGEN 0001](images/Machine_Model_PLAYINGEN_0001.svg)

**Parameters:**

|        |                                    |
| ------ | ---------------------------------- |
| Vindex | Voltage signal index               |
| Findex | Frequency signal index             |
| Rth    | Thevenin equivalent resistance, pu |
| Xth    | Thevenin equivalent reactance, pu  |

---

<a id="pv1g"></a>

## PV1G

*Source: [`Content/TransientModels_HTML/Machine Model PV1G.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model PV1G.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model PV1G 0001](images/Machine_Model_PV1G_0001.svg)

**Parameters:**

|        |                                                                                           |
| ------ | ----------------------------------------------------------------------------------------- |
| LVPLSW | LVPL Switch (enabled=1)                                                                   |
| rrpwr  | LVPL ramprate limit, p.u.                                                                 |
| brkpt  | LVPL characteristic breakpoint voltage, p.u.                                              |
| zerox  | LVPL characteristic zero crossing voltage, p.u.                                           |
| LVPL1  | LVPL Maximum Current Breakpoint                                                           |
| VLim   | Voltage limit used in the high voltage reactive current management function, p.u.         |
| LVPnt1 | Voltage in per unit at which the low voltage active current management scalar goes to 1.0 |
| LVPnt0 | Voltage in per unit at which the low voltage active current management scalar goes to 0.0 |
| Iolim  | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |
| Khv    | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |

---

<a id="pvd1"></a>

## PVD1

*Source: [`Content/TransientModels_HTML/Machine Model PVD1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model PVD1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If Tg \< 4\*TimeStep then Tg = 4\*TimeStep, and if Tg \> 0.2 then Tg = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model PVD1 0001](images/Machine_Model_PVD1_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                 |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pqflag | Priority to reactive current (0) or active current (1)                                                                                                                                                          |
| Xc     | Line drop compensation reactance (pu on mbase)                                                                                                                                                                  |
| Qmx    | Maximum change in reactive power due to voltage droop response (in pu on mbase)                                                                                                                                 |
| Qmn    | Minimum change in reactive power due to voltage droop response (in pu on mbase)                                                                                                                                 |
| V0     | Lower limit of deadband for voltage droop response (pu)                                                                                                                                                         |
| V1     | Upper limit of deadband for voltage droop response (pu)                                                                                                                                                         |
| Dqdv   | Voltage droop response characteristic                                                                                                                                                                           |
| fdbd   | Overfrequency deadband for governor response (pu deviation)                                                                                                                                                     |
| Ddn    | Down regulation droop gain (pu on mbase)                                                                                                                                                                        |
| Imax   | Apparent current limit (pu on mbase)                                                                                                                                                                            |
| Vt0    | Voltage below which all generation is tripped (pu)                                                                                                                                                              |
| Vt1    | Voltage below which generation starts to trip (pu)                                                                                                                                                              |
| Vt2    | Voltage above which generation starts to trip (pu)                                                                                                                                                              |
| Vt3    | Voltage above which all generation is tripped (pu)                                                                                                                                                              |
| Vrflag | Fraction of generation that can reconnect after low or high voltage tripping. 0.0 means voltage tripping is permanent; 1.0 means all generation can reconnect; Between 0 and 1 for partially self-resetting     |
| Ft0    | Frequency below which all generation is tripped (pu)                                                                                                                                                            |
| Ft1    | Frequency below which generation starts to trip (pu)                                                                                                                                                            |
| Ft2    | Frequency above which generation starts to trip (pu)                                                                                                                                                            |
| Ft3    | Frequency above which all generation is tripped (pu)                                                                                                                                                            |
| Frflag | Fraction of generation that can reconnect after low or high frequency tripping. 0.0 means frequency tripping is permanent; 1.0 means all generation can reconnect; Between 0 and 1 for partially self-resetting |
| Tg     | Inverter current lag time constant (seconds)                                                                                                                                                                    |
| Tf     | Frequency measurement lag time constant (seconds)                                                                                                                                                               |
| Vtmax  | Voltage limit for high voltage clamp logic (pu)                                                                                                                                                                 |
| Lvpnt1 | Low voltage active current management breakpoint 1 (pu)                                                                                                                                                         |
| lvpnt0 | Low voltage active current management breakpoint 0 (pu)                                                                                                                                                         |
| qmin   | High Voltage reactive current management term for PSLF (not used by PowerWorld)                                                                                                                                 |
| accel  | High Voltage reactive current management term for PSLF (not used by PowerWorld)                                                                                                                                 |

---

<a id="regc-a"></a>

## REGC_A

*Source: [`Content/TransientModels_HTML/Machine Model REGC_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGC_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If LVPL1 \< 0 then LVPL1 = 0.0 per unit. We will ignore all low voltage power logic and treat model as though Lvplsw = 0.
  - If Td \< 4\*TimeStep then Td = 4\*TimeStep, and if Td \> 0.2 then Td = 0.2

Model Equations and/or Block Diagrams

![Machine Model REGC A 0001](images/Machine_Model_REGC_A_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LVPLSW | LVPL Switch (enabled=1)                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| rrpwr  | Real power current ramp rate limit, p.u.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| brkpt  | LVPL characteristic breakpoint voltage, p.u.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| zerox  | LVPL characteristic zero crossing voltage, p.u.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| LVPL1  | LVPL Maximum Current Breakpoint                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| VLim   | Inside the network boundary equations, as voltages increases and reaches this threshold, additional reactive current is modeled to maintain an algebraic solution voltage at this threshold. This is intended to model very fast control that prevents over-voltage in this device.                                                                                                                                                                                                             |
| LVPnt1 | Inside the network boundary equations this is the voltage at which the real power current begins dropping from the controlled Ip value in the block diagram. LVPnt1 and LVpnt0 do not represent any control, but instead are part of the numerical calculation of the network boundary equations. Use LVPLSW=1 and parameters LVPL1, Xerox, Brkpt, and Tfltr to model low voltage current control. Or for more precision use the REEC\_\* models with appropriate piece-wise linear VDL curves. |
| LVPnt0 | Inside the network boundary equations this is the voltage at which the real power current will fall to zero. LVPnt1 and LVpnt0 do not represent any control, but instead are part of the numerical calculation of the network boundary equations. Use LVPLSW=1 and parameters LVPL1, Xerox, Brkpt, and Tfltr to model low voltage current control. Or for more precision use the REEC\_\* models with appropriate piece-wise linear VDL curves.                                                 |
| Tg     | Time Delay to represent how long it takes the renewable controller to achieve the desired current                                                                                                                                                                                                                                                                                                                                                                                               |
| Tfltr  | LVPL Voltage sensor time constant                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Iqrmax | Reactive current recovery positive rate limit (set to zero or negative value to disable)                                                                                                                                                                                                                                                                                                                                                                                                        |
| Iqrmin | Reactive current recovery negative rate limit (set to zero or positive value to disable)                                                                                                                                                                                                                                                                                                                                                                                                        |
| Qmin   | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.                                                                                                                                                                                                                                                                                                                                                                                                          |
| Khv    | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.                                                                                                                                                                                                                                                                                                                                                                                                          |
| Xe     | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.                                                                                                                                                                                                                                                                                                                                                                                                          |

---

<a id="regc-b"></a>

## REGC_B

*Source: [`Content/TransientModels_HTML/Machine Model REGC_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGC_B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Tfltr \< 4\*TimeStep then Tfltr will use 0.0
  - If Tg \< 4\*TimeStep then Tg will use 4\*TimeStep, and if Tg \> 0.2 then Tg = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model REGC B 0001](images/Machine_Model_REGC_B_0001.svg)

![Machine Model REGC B 0002](images/Machine_Model_REGC_B_0002.svg)

**Parameters:**

|          |                                                                                          |
| -------- | ---------------------------------------------------------------------------------------- |
| Tfltr    | Voltage sensor time constant                                                             |
| Tg       | Ip and Iq command time constant, seconds                                                 |
| Te       | Generator network impedance time constant, seconds                                       |
| rrpwr    | LVPL ramprate limit, p.u.                                                                |
| Re       | Generator effective resistance, p.u.                                                     |
| Xe       | Generator effective reactive, p.u.                                                       |
| Iqrmax   | Reactive current recovery positive rate limit (set to zero or negative value to disable) |
| Iqrmin   | Reactive current recovery negative rate limit (set to zero or positive value to disable) |
| Rateflag | RateFlag; 0 means active current ramp rate, otherwise active power ramp rate             |
| Imax     | Maximum curring rating of the converter, p.u.                                            |
| DQFlag   | PQ priority Flag; 0 = Q priority, otherwise P priority                                   |

---

<a id="regc-c"></a>

## REGC_C

*Source: [`Content/TransientModels_HTML/Machine Model REGC_C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGC_C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Tfltr \< 4\*TimeStep then Tfltr will use 0.0
  - If Tg \< 4\*TimeStep then Tg will use 4\*TimeStep, and if Tg \> 0.2 then Tg = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model REGC C 0001](images/Machine_Model_REGC_C_0001.svg)

![Machine Model REGC C 0002](images/Machine_Model_REGC_C_0002.svg)

**Parameters:**

|          |                                                                                          |
| -------- | ---------------------------------------------------------------------------------------- |
| Tfltr    | Voltage sensor time constant                                                             |
| Te       | Generator network impedance time constant, seconds                                       |
| rrpwr    | LVPL ramprate limit, p.u.                                                                |
| Re       | Generator effective resistance, p.u.                                                     |
| Xe       | Generator effective reactive, p.u.                                                       |
| Iqrmax   | Reactive current recovery positive rate limit (set to zero or negative value to disable) |
| Iqrmin   | Reactive current recovery negative rate limit (set to zero or positive value to disable) |
| Rateflag | RateFlag; 0 means active current ramp rate, otherwise active power ramp rate             |
| Imax     | Maximum curring rating of the converter, p.u.                                            |
| DQFlag   | PQ priority Flag; 0 = Q priority, otherwise P priority                                   |
| Kip      | Proportional-gain of the inner-current control loop \[pu/pu\]                            |
| Kii      | Integral-gain of the inner-current control loop \[pu/pu.s-1\]                            |
| Kppll    | Proportional-gain of the PLL \[rad.s-1/pu\]                                              |
| Kipll    | Integral-gain of the PLL \[rad.s-1/pu.s-1\]                                              |
| wmax     | Upper limit on the PLL \[rad.s-1\]                                                       |
| wmin     | Lower limit on the PLL \[rad.s-1\]                                                       |
| Vdip     | Vdip \[pu\], Voltage below which PLL integrator state is frozen                          |

---

<a id="regfm-a1"></a>

## REGFM_A1

*Source: [`Content/TransientModels_HTML/Machine Model REGFM_A1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGFM_A1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Xe \< 0.0001 is not allowed, and a value of 0.0001 will be used if a smaller one is entered.
  - For TPf, TQf, TVf time constant, any value less than Mult\*TimeStep will be modified. If less than 0.5\*Mult\*TimeStep will be set to 0.0, otherwise it will be increased to Mult\*TimeStep.
  - Parameters Emax/Emin, Pmax/Pmin, and Qmax/Qmin will be checked for consistency and flipped if entered backwards.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model REGFM A1 0001](images/Machine_Model_REGFM_A1_0001.svg)

![Machine Model REGFM A1 0002](images/Machine_Model_REGFM_A1_0002.svg)

**Parameters:**

|        |                                                                                                 |
| ------ | ----------------------------------------------------------------------------------------------- |
| TPf    | Filter time constant for P measurement (s)                                                      |
| TQf    | Filter time constant for Q measurement (s)                                                      |
| TVf    | Filter time constant for V measurement (s)                                                      |
| Re     | Inverter coupling resistance (pu)                                                               |
| Xe     | Inverter coupling reactance (pu), must be greater than zero                                     |
| Imax   | Inverter maximum output current (pu), Zero means ignore Imax                                    |
| Emax   | Upper limit of the output of voltage controller                                                 |
| Emin   | Lower limit of the output of voltage controller                                                 |
| Pmax   | Upper limit of the inverter active power control                                                |
| Pmin   | Lower limit of the inverter active power control                                                |
| Qmax   | Upper limit of the inverter reactive power control                                              |
| Qmin   | Lower limit of the inverter reactive power control                                              |
| Mp     | P-Freq Droop gain                                                                               |
| Mq     | Q-V Droop gain                                                                                  |
| Kpv    | Proportional gain for voltage controller                                                        |
| Kiv    | Integral gain for voltage controller (\>0)                                                      |
| Kppmax | Proportional gain of the Pmax and Pmin controller                                               |
| Kipmax | Integral gain of the Pmax and Pmin controller                                                   |
| Kpqmax | Proportional gain of the Qmax and Qmin controller                                               |
| Kiqmax | Integral gain of the Qmax and Qmin controller                                                   |
| Vflag  | Voltage Control Mode Selection. \<\>0 to use PI controller; =0 to directly set internal voltage |
| QVflag | Input Mode Selection. \<\>0 to use Voltage as a input; =0 to use Reactive Power Q as an input   |

---

<a id="regfm-b1"></a>

## REGFM_B1

*Source: [`Content/TransientModels_HTML/Machine Model REGFM_B1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGFM_B1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - For TPf, TQf, TVf time constant, any value less than Mult\*TimeStep will be modified. If less than 0.5\*Mult\*TimeStep will be set to 0.0, otherwise it will be increased to Mult\*TimeStep.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model REGFM B1 0001](images/Machine_Model_REGFM_B1_0001.svg)

![Machine Model REGFM B1 0002](images/Machine_Model_REGFM_B1_0002.svg)

**Parameters:**

<table>
<tbody>
<tr class="odd">
<td>wFlag</td>
<td>Flag to select which speed deviation to use for Power-Frequency droop.<br />
=0 to use Dwm; &lt;&gt;0 to use DwPLL</td>
</tr>
<tr class="even">
<td>VdrpFlag</td>
<td>Flag to select either Current or Reactive Power Droop. If QVFlag=0 then VdrpFlag will be ignored and treated as 0 regardless.<br />
=0 for Power; &lt;&gt;0 for Current.</td>
</tr>
<tr class="odd">
<td>QVflag</td>
<td>Input Mode Selection determines whether input value is Qref or Vref.<br />
=0 to use Reactive Power Q as an input; &lt;&gt;0 to use Voltage as an input</td>
</tr>
<tr class="even">
<td>PQflag</td>
<td>PQ priority flag specifies a priority used for the steady state current limitation.<br />
=0 to use Q priority; &lt;&gt;0 to use P priority</td>
</tr>
<tr class="odd">
<td>FFlag</td>
<td>Flag determine if the Power-Frequency droop is enabled.<br />
=0 to disable Power-Frequency Droop; &lt;&gt; 0 to enable Power-Frequency Droop</td>
</tr>
<tr class="even">
<td>ESFlag</td>
<td>Flag determines if the model supports energy storage (negative real power or current).<br />
=0 to prevent negative angle; &lt;&gt; 0 to enabled negative angles for energy storage</td>
</tr>
<tr class="odd">
<td>Re</td>
<td>Inverter coupling resistance [pu] (0.00 &lt;= Re &lt;= 0.25*Xe)</td>
</tr>
<tr class="even">
<td>Xe</td>
<td>Inverter coupling reactance [pu] (0.04 &lt;= Xe &lt;= 0.40)</td>
</tr>
<tr class="odd">
<td>mq</td>
<td>Q-V droop gain. When Vdrpflag&lt;&gt;0, mq represents a per unit virtual impedance [pu]</td>
</tr>
<tr class="even">
<td>kpv</td>
<td>Proportional gain of the voltage controller [pu]</td>
</tr>
<tr class="odd">
<td>kiv</td>
<td>Integral gain of the voltage controller (&gt;0) [pu/s]</td>
</tr>
<tr class="even">
<td>mp</td>
<td>Power-Frequency Droop gain [pu]</td>
</tr>
<tr class="odd">
<td>Dwmax</td>
<td>Upper limit of Dwm (&gt;=0) [pu]</td>
</tr>
<tr class="even">
<td>Dwmin</td>
<td>Lower limit of Dwm (&lt;=0) [pu]</td>
</tr>
<tr class="odd">
<td>kpPLL</td>
<td>Proportional gain of PLL [pu]</td>
</tr>
<tr class="even">
<td>kiPLL</td>
<td>Integral gain of PLL (&gt;0) [pu/s]</td>
</tr>
<tr class="odd">
<td>DwPLLmax</td>
<td>Upper limit of the PLL output (&gt;=0) [pu]</td>
</tr>
<tr class="even">
<td>DwPLLmin</td>
<td>Lower limit of the PLL output (&lt;=0) [pu]</td>
</tr>
<tr class="odd">
<td>Tp</td>
<td>Time constant of the low-pass filter in the VSM control block (&gt;=0) [seconds]</td>
</tr>
<tr class="even">
<td>H</td>
<td>Inertia time constant [seconds]</td>
</tr>
<tr class="odd">
<td>D1</td>
<td>Damping [pu]</td>
</tr>
<tr class="even">
<td>D2</td>
<td>Transient damping [pu]</td>
</tr>
<tr class="odd">
<td>wD</td>
<td>Angular frequency of the washout block [1/seconds]</td>
</tr>
<tr class="even">
<td>Issmax</td>
<td>Steady state current limit [pu] (Issmax &lt;= 0 is treated as 1/Xe) (Issmax &lt;= 1/Xe) (Issmax &lt;= Ifaultmax)</td>
</tr>
<tr class="odd">
<td>Kf</td>
<td>PQFlag determines if Idmax = Kf*Issmax or Iqmax = Kf*Issmax (Kf&lt;=0 is treated 1.0)</td>
</tr>
<tr class="even">
<td>kI</td>
<td>Integral gain for the active current limiting loop [pu/s]</td>
</tr>
<tr class="odd">
<td>Ifaultmax</td>
<td>Transient fault current limit [pu]. (If Ifaultmax &lt;= 0 then limit is ignored, but this is not recommended)</td>
</tr>
<tr class="even">
<td>Tpf</td>
<td>Time constant of the low-pass filter for active power measurement (&gt;=0) [seconds]</td>
</tr>
<tr class="odd">
<td>TQf</td>
<td>Time constant of the low-pass filter for reactive power measurement (&gt;=0) [seconds]</td>
</tr>
<tr class="even">
<td>TVf</td>
<td>Time constant of the low-pass filter for voltage measurement (&gt;=0) [seconds]</td>
</tr>
<tr class="odd">
<td>TIf</td>
<td>Time constant of the low-pass filter for current measurement (&gt;=0) [seconds]</td>
</tr>
<tr class="even">
<td>Ke</td>
<td>Scalar on Idmax for negative real steady state current limitation (0 &lt;= Ke &lt;= 1.0)</td>
</tr>
<tr class="odd">
<td>Vpllfrz</td>
<td>Terminal voltage below which special PLL state freezing is implemented (Vpllfrz &lt;= 0.10) [pu]</td>
</tr>
</tbody>
</table>

---

<a id="regfm-c1"></a>

## REGFM_C1

*Source: [`Content/TransientModels_HTML/Machine Model REGFM_C1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model REGFM_C1.htm)*

Model was added in Version 24, build on May 1, 2025

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - The following parameter pairs should have a maximum value that is positive and a minimum value that is negative:  
    DEmax/DEmin, DPDmax, DPDmin, Dwmax/Dwmin, DPGFMmax/DPGFMmin  
    If both values are positive, then we will assume the minimum value should have had a negative sign.  
    If both values are negative, then we will assume the maximum value should have had a positive sign.  
    If the Max \< 0 AND Min \> 0, then we will assume the numbers have been entered backwards and we will swap the values.
  - The following parameter pairs should have a maximum value that is greater or equal to than the minimum value:  
    PcmdGFLmax/PcmdGFLmin, QcmdGFLmax/QcmdGFLmin  
    If the Max \< Min then the values will be swapped by the Auto Correction.  
  - 0.04 \<= Xe \<= 0.40. Any value outside this range will be set to the edge of this range
  - 0.0 \<= Re \<= 0.25\*Xe. Any value outside this range will be set to the edge of this range
  - H \>= 0.1. Any value less than 0.1 will be treated as 0.1
  - dbVL1 represent low side deadbands which should always be negative. We will assume a parameter equal to the negative of the absolute value entered.
  - dbVH1 represent high side deadbands which should always be positive. We will assume a parameter equal to the positive of the absolute value entered.
  - Kf \> 0, so value that is negative or zero will be treated as 1.0
  - A zero or negative Ifaultmax is interpreted as ignoring the limit
  - For TVr, TVSM, Twr, Twm, TVf, TPf, and TIf time constant, any value less than Mult\*TimeStep will be modified. If less than 0.5\*Mult\*TimeStep will be set to 0.0, otherwise it will be increased to Mult\*TimeStep.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model REGFM C1 0001](images/Machine_Model_REGFM_C1_0001.svg)

![Machine Model REGFM C1 0002](images/Machine_Model_REGFM_C1_0002.svg)

**Parameters:**

|            |                                                                                                     |
| ---------- | --------------------------------------------------------------------------------------------------- |
| FFlag      | A flag to determine whether the power-frequency droop is enabled (Fflag\<\>0) or disabled (FFlag=0) |
| Vflag      | A flag to determine whether the voltage droop is enabled (Vflag \<\> 0) or disabled (Vflag = 0)     |
| PQFlag     | A flag to determine whether P priority (PQFlag\<\>0) or Q priority (PQFlag=0) is selected           |
| Re         | Virtual resistance (0 pu \<= Rs \<= 0.25Xs) \[pu\]                                                  |
| Xe         | Virtual reactance (0.04 pu \<= Xs \<= 0.4 pu) \[pu\]                                                |
| Mq         | Q-V droop gain of the GFM branch \[pu\]                                                             |
| KpE        | Proportional gain of the voltage PI loop of the GFM branch \[pu\]                                   |
| KiE        | Integral gain of the voltage PI loop of the GFM branch \[pu/s\]                                     |
| DEmax      | Upper limit of the volage PI loop of the GFM branch \[pu\]                                          |
| DEmin      | Lower limit of the volage PI loop of the GFM branch \[pu\]                                          |
| DPDmax     | Upper limit of the VSM damping output \[pu\]                                                        |
| DPDmin     | Lower limit of the VSM damping output \[pu\]                                                        |
| TVr        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| TVSM       | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| DPGFMmax   | Upper limit of the VSM droop output \[pu\]                                                          |
| DPGFMmin   | Lower limit of the VSM droop output \[pu\]                                                          |
| Twr        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| Twm        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| Mp         | P-f droop gain of the GFM branch \[pu\]                                                             |
| Dwmax      | Upper limit of the VSM integrator of the GFM branch \[pu\]                                          |
| Dwmin      | Lower limit of the VSM integrator of the GFM branch \[pu\]                                          |
| H          | Inertia time constant of the GFM branch \[s\]                                                       |
| D1         | Damping of the GFM branch \[pu\]                                                                    |
| D2         | Transient damping of the GFM branch \[pu\]                                                          |
| wD         | Angular frequency of the washout block of the GFM branch \[pu\]                                     |
| TVf        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| TPf        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| TIf        | Time constant of low-pass filter of the GFM branch \[s\]                                            |
| Vmin       | Lower voltage limit of the GFL branch \[pu\]                                                        |
| Vref0      | Voltage reference of the GFL branch \[pu\]                                                          |
| dbVL1      | Lower threshold of the deadband of the GFL branch (\<=0) \[pu\]                                     |
| dbVH1      | Upper threshold of the deadband of the GFL branch (\>=0) \[pu\]                                     |
| Kqv        | Voltage control factor of the GFL branch \[pu\]                                                     |
| Imax       | Maximum output current \[pu\]                                                                       |
| Kf         | A factor to determine Iqmax (PQFlag=0) or Idmax (PQFlag\<\>0) of the GFL branch. (0 \< Kf \<= 1.0)  |
| PcmdGFLmax | Upper limit of the active power reference for the GFL branch \[pu\]                                 |
| PcmdGFLmin | Lower limit of the active power reference for the GFL branch \[pu\]                                 |
| QcmdGFLmax | Upper limit of the reactive power reference for the GFL branch \[pu\]                               |
| QcmdGFLmin | Lower limit of the reactive power reference for the GFL branch \[pu\]                               |

---

<a id="stcon"></a>

## STCON

*Source: [`Content/TransientModels_HTML/Machine Model STCON.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model STCON.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model STCON 0001](images/Machine_Model_STCON_0001.svg)

**Parameters:**

|         |                                                                  |
| ------- | ---------------------------------------------------------------- |
| R       | Current droop, p.u.                                              |
| Tf      | Voltage transducer time constant, sec.                           |
| Kp      | Proportional gain                                                |
| Ki      | Reset gain gain                                                  |
| Ta      | Lead time constant, sec. ( unused )                              |
| Tb      | Lag time constant, sec. ( unused )                               |
| Xt      | Internal (transformer) reactance, pu on mbase                    |
| Vmin    | Minimum inverter voltage, p.u.                                   |
| Vmax    | Maximum inverter voltage, p.u.                                   |
| Kil     | Current limiter gain                                             |
| Imax    | Current limit setting, p.u. on mbase                             |
| Kqi     | Reactive controller gain                                         |
| Qset    | Reactive power output set-point, MVAR                            |
| Accel   | Solution acceleration factor                                     |
| Imxeps  | A delta p.u. current used in umax and umin calculation           |
| vthresh | Voltage threshold above which vmax and vmin limits become active |

---

<a id="svcwsc"></a>

## SVCWSC

*Source: [`Content/TransientModels_HTML/Machine Model SVCWSC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model SVCWSC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model SVCWSC 0001](images/Machine_Model_SVCWSC_0001.svg)

**Parameters:**

|         |                                              |
| ------- | -------------------------------------------- |
| J1      | First stabilizer input signal code           |
| J2      | Second stabilizer input signal code          |
| Ts1     | Voltage transducer time constant, sec.       |
| Vemax   | Maximum error signal, p.u.                   |
| Vemin   | Maximum error signal, p.u.                   |
| Ts2     | Lead time constant, sec.                     |
| Ts3     | Lag time constant, sec.                      |
| Ts4     | Lead time constant, sec.                     |
| Ts5     | Lag time constant, sec.                      |
| Ksvs    | Gain, per unit b/per unit v                  |
| Ksd     | Discontinuous control gain, p.u.             |
| Bmax    | Maximum admittance, p.u.                     |
| Bpmax   | Maximum controlled admittance, p.u.          |
| Bpmin   | Minimum controlled admittance, p.u.          |
| Bmin    | Minimum admittance, p.u.                     |
| Ts6     | Firing control time constant, sec.           |
| Dv      | Threshold for switched control, p.u.         |
| V1max   | Maximum limit on first lead/lag, p.u.        |
| V1min   | Minimum limit on first lead/lag, p.u.        |
| V2max   | Maximum limit on second lead/lag, p.u.       |
| V2min   | Minimum limit on second lead/lag, p.u.       |
| Xc      | Line drop compensating reactance, p.u.       |
| Tc      | Transducer lead time constant, sec.          |
| Dv2     | Threshold for added shunt switching, p.u.    |
| Bshunt  | Additional switched shunt admittance, p.u.   |
| Tdelay  | Time delay for switching added shunt, sec.   |
| Bias    | Constant "bias" shunt admittance, p.u.       |
| Ks1     | Stabilizer gain                              |
| Ts7     | Stabilizer time constant, sec.               |
| Ts8     | Stabilizer time constant, sec.               |
| Ts9     | Stabilizer time constant, sec.               |
| Ts13    | Stabilizer time constant, sec.               |
| Ts14    | Stabilizer time constant, sec.               |
| Ks3     | Stabilizer gain                              |
| Vscsmax | Maximum stabilizer output, p.u.              |
| Ks2     | Stabilizer gain                              |
| Ts10    | Stabilizer time constant, sec.               |
| Ts11    | Stabilizer time constant, sec.               |
| Ts12    | Stabilizer time constant, sec.               |
| b       | 0 integral control, = 1 proportional control |
| V1vcl   | Voltage Clamp initiation voltage, pu         |
| V2vcl   | Voltage Clamp release voltage, pu            |
| Tdvcl   | Voltage Clamp release time, sec.             |

---

<a id="vwscc"></a>

## VWSCC

*Source: [`Content/TransientModels_HTML/Machine Model VWSCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model VWSCC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model VWSCC 0001](images/Machine_Model_VWSCC_0001.svg)

**Parameters:**

|        |                                                   |
| ------ | ------------------------------------------------- |
| Ts1    | Voltage transducer time constant, sec.            |
| Vemax  | Maximum error signal, p.u.                        |
| Ts2    | Lead time constant, sec.                          |
| Ts3    | Lag time constant, sec.                           |
| a      | Lead gain, must be 1.0                            |
| b      | Lag gain, must be 1.0                             |
| Ts4    | Lead time constant, sec.                          |
| Ts5    | Lag time constant, sec.                           |
| Ksvs   | Gain, per unit b/per unit v                       |
| Ksd    | Discontinuous control gain, p.u.                  |
| Bmax   | Maximum admittance, p.u.                          |
| Bpmax  | Maximum admittance under continuous control, p.u. |
| Bpmin  | Minimum admittance under continuous control, p.u. |
| Bmin   | Minimum admittance, p.u.                          |
| Ts6    | Firing control time constant, sec.                |
| Dv     | Error threshold for discontinuous control, p.u.   |
| Xc     | Line drop compensating reactance, p.u.            |
| Tc     | Transducer lead time constant, sec.               |
| Tdelay | Controller delay, sec.                            |

---

<a id="wt1g"></a>

## WT1G

*Source: [`Content/TransientModels_HTML/Machine Model WT1G.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT1G.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tpo \< 0.5\*Mult\*TimeStep then Tpo = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
  - If 0.0 \< Tppo \< 0.5\*Mult\*TimeStep then Tppo = 0, ElseIf 0.5\*Mult\*TimeStep \< Tppo \< Mult\*TimeStep then Tppo = Mult\*TimeStep
  - If Lp \> 0.4\*Ls is not possible then Lp = 0.4\*Ls.
  - If Lpp \> Lp is not possible then Lpp = Lp.
  - If Ll \> 0.8\*Lpp is not possible then Ll = 0.8\*Lpp.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model WT1G 0001](images/Machine_Model_WT1G_0001.svg)

**Parameters:**

|       |                                               |
| ----- | --------------------------------------------- |
| Ls    | Synchrounous reactance, (pu \> 0)             |
| Lp    | Transient reactance (pu, \> 0)                |
| Ra    | Stator resistance, pu                         |
| Tpo   | Transient rotor time constant, sec            |
| SE1   | Saturation factor at E1                       |
| SE2   | Saturation factor at E2                       |
| Acc   | Acceleration factor for initialization        |
| Lpp   | Sub-transient reactance (pu, \> 0)            |
| Ll    | Stator leakage reactance (pu, \> 0)           |
| Tppo  | Sub-transient rotor time constant, sec        |
| ndelt | Time step subdivision factor.                 |
| wdelt | Speed threshold for subdividing time step, pu |

---

<a id="wt1g1"></a>

## WT1G1

*Source: [`Content/TransientModels_HTML/Machine Model WT1G1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT1G1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|      |                                        |
| ---- | -------------------------------------- |
| Tpo  | Transient rotor time constant, sec     |
| Tppo | Sub-transient rotor time constant, sec |
| Ls   | Synchrounous reactance, (pu \> 0)      |
| Lp   | Transient reactance (pu, \> 0)         |
| Lpp  | Sub-transient reactance (pu, \> 0)     |
| Ll   | Stator leakage reactance (pu, \> 0)    |
| E1   | Field voltage value, E1                |
| SE1  | Saturation factor at E1                |
| E2   | Field voltage value, E2                |
| SE2  | Saturation factor at E2                |

---

<a id="wt2g"></a>

## WT2G

*Source: [`Content/TransientModels_HTML/Machine Model WT2G.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT2G.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Lp \> 0.5\*Ls is not possible then Lp = 0.5\*Ls.
  - If Ll \> 0.8\*Lpp is not possible then Ll = 0.8\*Lpp.
  - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

**Parameters:**

|        |                                                          |
| ------ | -------------------------------------------------------- |
| Ls     | Synchrounous reactance, (pu \> 0)                        |
| Lp     | Transient reactance (pu, \> 0)                           |
| Ll     | Stator leakage reactance (pu, \> 0)                      |
| Ra     | Stator resistance, pu                                    |
| Tpo    | Transient rotor time constant, sec                       |
| S1     | Saturation factor at 1.0 pu flux                         |
| S12    | Saturation factor at 1.2 pu flux                         |
| spdrot | Initial electrical rotor speed, p.u. of system frequency |
| Accel  | Acceleration factor for initialization                   |

---

<a id="wt2g1"></a>

## WT2G1

*Source: [`Content/TransientModels_HTML/Machine Model WT2G1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT2G1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|                              |                                                   |
| ---------------------------- | ------------------------------------------------- |
| Xa                           | Stator reactance                                  |
| Xm                           | Magnetizing reactance                             |
| X1                           | Rotor reactance                                   |
| R\_Rot\_Mach                 | Rotor resistance                                  |
| R\_Rot\_Max                  | Sum of R\_Rot\_Mach and total external resistance |
| E1                           | Field voltage value E1                            |
| SE1                          | Saturation value at E1                            |
| E2                           | Field voltage value E2                            |
| SE2                          | Saturation value at E2                            |
| Power\_Ref1 to Power\_Ref\_5 | Coordinate pairs of the power-slip curve          |
| Slip\_1 to Slip\_5           | Power-Slip                                        |

---

<a id="wt3g"></a>

## WT3G

*Source: [`Content/TransientModels_HTML/Machine Model WT3G.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT3G.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If LVPL1 \< 0 then LVPL1 = 0.0 per unit. We will ignore all low voltage power logic and treat model as though Lvplsw = 0.
  - If Td \< 4\*TimeStep then Td = 4\*TimeStep, and if Td \> 0.2 then Td = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model WT3G 0001](images/Machine_Model_WT3G_0001.svg)

**Parameters:**

|         |                                                                                           |
| ------- | ----------------------------------------------------------------------------------------- |
| Lpp     | Generator effective reactive, p.u.                                                        |
| LVPLSW  | LVPL Switch (enabled=1)                                                                   |
| rrpwr   | LVPL ramprate limit, p.u.                                                                 |
| brkpt   | LVPL characteristic breakpoint voltage, p.u.                                              |
| zerox   | LVPL characteristic zero crossing voltage, p.u.                                           |
| LVPL1   | LVPL Maximum Current Breakpoint                                                           |
| VLim    | Model Parameters\\VLim                                                                    |
| LVPnt1  | Voltage in per unit at which the low voltage active current management scalar goes to 1.0 |
| LVPnt0  | Voltage in per unit at which the low voltage active current management scalar goes to 0.0 |
| Iolim   | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |
| Khv     | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |
| Td      | Time constant, sec                                                                        |
| T\_LVPL | Voltage sensor time constant                                                              |

---

<a id="wt3g1"></a>

## WT3G1

*Source: [`Content/TransientModels_HTML/Machine Model WT3G1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT3G1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Machine Model WT3G1 0001](images/Machine_Model_WT3G1_0001.svg)

**Parameters:**

|        |                                    |
| ------ | ---------------------------------- |
| Lpp    | Generator effective reactive, p.u. |
| Kpll   | PLL first integrator gain          |
| Kipll  | PLL second integrator gain         |
| Pllmax | PLL maximum limit                  |
| Prated | Turbine MW rating                  |

---

<a id="wt3g2"></a>

## WT3G2

*Source: [`Content/TransientModels_HTML/Machine Model WT3G2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT3G2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If GLVPL \< 0 then GLVPL = 0.0 per unit. We will ignore all low voltage power logic.
  - If Tipcmd \< 4\*TimeStep then Tipcmd = 4\*TimeStep, and if Tipcmd \> 0.2 then Tipcmd = 0.2
  - If Tiqcmd \< 4\*TimeStep then Tiqcmd = 4\*TimeStep, and if Tiqcmd \> 0.2 then Tiqcmd = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model WT3G2 0001](images/Machine_Model_WT3G2_0001.svg)

**Parameters:**

|           |                                     |
| --------- | ----------------------------------- |
| Number    | Number of turbines                  |
| Tiqcmd    | Q command time constant             |
| Tipcmd    | P command time constant             |
| Kpll      | PLL gain                            |
| Kipll     | PLL integrator gain                 |
| Pllmax    | PLL max. limit                      |
| Prated    | Turbine MW rating                   |
| VLVPL1    | Low voltage regulation breakpoints  |
| VLVPL2    | Low voltage regulation breakpoints  |
| GLVLP     | Low voltage regulation breakpoints  |
| VHVRCR    | High voltage limit, pu              |
| CurHVRCR  | High voltage reactive current limit |
| RIP\_LVPL | Maximum Ip rate, pu                 |
| T\_LVPL   | Voltage sensor time constant        |

---

<a id="wt4g"></a>

## WT4G

*Source: [`Content/TransientModels_HTML/Machine Model WT4G.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT4G.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If LVPL1 \< 0 then LVPL1 = 0.0 per unit. We will ignore all low voltage power logic and treat model as though Lvplsw = 0.
  - If Td \< 4\*TimeStep then Td = 4\*TimeStep, and if Td \> 0.2 then Td = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model WT4G 0001](images/Machine_Model_WT4G_0001.svg)

**Parameters:**

|         |                                                                                           |
| ------- | ----------------------------------------------------------------------------------------- |
| LVPLSW  | LVPL Switch (enabled=1)                                                                   |
| rrpwr   | LVPL ramprate limit, p.u.                                                                 |
| brkpt   | LVPL characteristic breakpoint voltage, p.u.                                              |
| zerox   | LVPL characteristic zero crossing voltage, p.u.                                           |
| LVPL1   | LVPL Maximum Current Breakpoint                                                           |
| VLim    | Voltage limit used in the high voltage reactive current management function, pu           |
| LVPnt1  | Voltage in per unit at which the low voltage active current management scalar goes to 1.0 |
| LVPnt0  | Voltage in per unit at which the low voltage active current management scalar goes to 0.0 |
| Iolim   | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |
| Khv     | Parameter not used by PowerWorld Simulator. Included only to support DYD file formats.    |
| Td      | Time constant, sec                                                                        |
| T\_LVPL | Voltage sensor time constant                                                              |

---

<a id="wt4g1"></a>

## WT4G1

*Source: [`Content/TransientModels_HTML/Machine Model WT4G1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model WT4G1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If GLVPL \< 0 then GLVPL = 0.0 per unit. We will ignore all low voltage power logic.
  - If Tipcmd \< 4\*TimeStep then Tipcmd = 4\*TimeStep, and if Tipcmd \> 0.2 then Tipcmd = 0.2
  - If Tiqcmd \< 4\*TimeStep then Tiqcmd = 4\*TimeStep, and if Tiqcmd \> 0.2 then Tiqcmd = 0.2

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Machine Model WT4G1 0001](images/Machine_Model_WT4G1_0001.svg)

**Parameters:**

|           |                                     |
| --------- | ----------------------------------- |
| Tiqcmd    | Q command time constant             |
| Tipcmd    | P command time constant             |
| VLVPL1    | Low voltage regulation breakpoints  |
| VLVPL2    | Low voltage regulation breakpoints  |
| GLVLP     | Low voltage regulation breakpoints  |
| VHVRCR    | High voltage limit, pu              |
| CurHVRCR  | High voltage reactive current limit |
| RIP\_LVPL | Maximum Ip rate, pu                 |
| T\_LVPL   | Voltage sensor time constant        |

---

<a id="converterrenewable"></a>

## Converter/Renewable

*Source: [`Content/TransientModels_HTML/MachineFolder Converter.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder Converter.htm)*

_This topic has no body text in the source help file._

---

<a id="induction"></a>

## Induction

*Source: [`Content/TransientModels_HTML/MachineFolder Induction.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder Induction.htm)*

_This topic has no body text in the source help file._

---

<a id="playin"></a>

## PlayIn

*Source: [`Content/TransientModels_HTML/MachineFolder PlayIn.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder PlayIn.htm)*

_This topic has no body text in the source help file._

---

<a id="static-var-compensator"></a>

## Static Var Compensator

*Source: [`Content/TransientModels_HTML/MachineFolder StaticVarCompensator.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder StaticVarCompensator.htm)*

_This topic has no body text in the source help file._

---

<a id="synchronous"></a>

## Synchronous

*Source: [`Content/TransientModels_HTML/MachineFolder Synchronous.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MachineFolder Synchronous.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-machines"></a>

## BPA Machines

*Source: [`Content/TransientModels_HTML/BPA Machines.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BPA Machines.htm)*

_This topic has no body text in the source help file._

---

<a id="gen-bpa-mmg2"></a>

## GEN_BPA_MMG2

*Source: [`Content/TransientModels_HTML/Machine Model GEN_BPA_MMG2 - MMG6.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model GEN_BPA_MMG2 - MMG6.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpasvc"></a>

## BPASVC

*Source: [`Content/TransientModels_HTML/Machine Model BPASVC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Machine Model BPASVC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.
