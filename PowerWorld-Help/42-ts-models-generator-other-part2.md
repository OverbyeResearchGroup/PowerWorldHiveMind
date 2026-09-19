---
title: "TS Models — Other Generator Models (Part 2 of 2)"
part: "Transient Models"
chapter_file: "42-ts-models-generator-other-part2.md"
topics: 37
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Other Generator Models (Part 2 of 2)

Remaining generator-attached models: plant controllers, relays, limiters and auxiliary devices.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (37)**

- [PAUXSS1A](#pauxss1a)
- [PROBOOST](#proboost)
- [WTGIBFFR_A](#wtgibffr-a)
- [Pref Controller](#pref-controller)
- [LCFB1](#lcfb1)
- [LCFB1_PTI](#lcfb1-pti)
- [WTGTRQ_A](#wtgtrq-a)
- [WTGWGO_A](#wtgwgo-a)
- [Relay](#relay)
- [ATRRELAY](#atrrelay)
- [FRQDCAT](#frqdcat)
- [GENOF](#genof)
- [GP1](#gp1)
- [GP2](#gp2)
- [GP3](#gp3)
- [GVPHZFT](#gvphzft)
- [GVPHZIT](#gvphzit)
- [LHFRT](#lhfrt)
- [LHSRT](#lhsrt)
- [LHVRT](#lhvrt)
- [VTGDCAT](#vtgdcat)
- [Stator Current Limiter](#stator-current-limiter)
- [SCL1C](#scl1c)
- [SCL2C](#scl2c)
- [MNLEX1](#mnlex1)
- [MNLEX2](#mnlex2)
- [MNLEX3](#mnlex3)
- [UEL1](#uel1)
- [UEL2](#uel2)
- [UEL2C](#uel2c)
- [Voltage Compensator](#voltage-compensator)
- [CCOMP](#ccomp)
- [CCOMP4](#ccomp4)
- [COMP](#comp)
- [COMPCC](#compcc)
- [IEEEVC](#ieeevc)
- [REMCMP](#remcmp)

---

<a id="pauxss1a"></a>

## PAUXSS1A

*Source: [`Content/TransientModels_HTML/Paux Controller PAUXSS1A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Paux Controller PAUXSS1A.htm)*

**AutoCorrection Properties**

  - If 0.0 \< T2 \< 0.125\*Mult\*TimeStep then T2 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T2 \< 0.25\*Mult\*TimeStep then T2 = 0.25\*Mult\*TimeStep
  - If 0.0 \< T4 \< 0.125\*Mult\*TimeStep then T4 = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< T4 \< 0.25\*Mult\*TimeStep then T4 = 0.25\*Mult\*TimeStep
  - If 0 \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0 \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep
  - If Lsmax \< Lsmin then swap the values. If Lsmax \< 0 then Lsmax change sign to positive. If Lsmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)  

Model Equations and/or Block Diagrams

![Paux Controller PAUXSS1A 0001](images/Paux_Controller_PAUXSS1A_0001.svg)

**Parameters:**

|         |                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------ |
| FlowDir | \>=0 means a flow into the branch. \<0 means a flow out of the branch                                  |
| Ics     | 1= Bus Frequency in per unit ; 2 = Generator electric MW output in per unit; 3 = Branch MW in per unit |
| A1      | Notch filter parameters                                                                                |
| A2      | Notch filter parameters                                                                                |
| T1      | Lead/lag time constant, sec                                                                            |
| T2      | Lead/lag time constant, sec                                                                            |
| T3      | Lead/lag time constant, sec                                                                            |
| T4      | Lead/lag time constant, sec                                                                            |
| T5      | Wahsout numerator time constant, sec                                                                   |
| T6      | Washout denominator time constant, sec                                                                 |
| Ks      | Stabilizer gains                                                                                       |
| Lsmax   | Maximum stabilizer output, pu                                                                          |
| Lsmin   | Minimum stabilizer output, pu                                                                          |

---

<a id="proboost"></a>

## PROBOOST

*Source: [`Content/TransientModels_HTML/Paux Controller PROBOOST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Paux Controller PROBOOST.htm)*

**AutoCorrection Properties**

  - None  

Model Equations and/or Block Diagrams

![Paux Controller PROBOOST 0001](images/Paux_Controller_PROBOOST_0001.svg)

**Parameters:**

|               |                                  |
| ------------- | -------------------------------- |
| FrequencyDrop | Frequency value specified \[HZ\] |
| TimeDelay     | Time Delay \[Sec.\]              |
| BoostMW       | Boost Power \[MW\]               |

---

<a id="wtgibffr-a"></a>

## WTGIBFFR_A

*Source: [`Content/TransientModels_HTML/Paux Controller WTGIBFFR_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Paux Controller WTGIBFFR_A.htm)*

**AutoCorrection Properties**

Following treatment of these values are used during the simulation

  - All values of db, Trise, Tpeak, Tfall, dP, and dPmin are used with an absolute value. Negative values do not make sense for these.  

Model Equations and/or Block Diagrams

![Paux Controller WTGIBFFR A 0001](images/Paux_Controller_WTGIBFFR_A_0001.svg)

![Paux Controller WTGIBFFR A 0002](images/Paux_Controller_WTGIBFFR_A_0002.svg)

**Parameters:**

|        |                                                                                                                        |
| ------ | ---------------------------------------------------------------------------------------------------------------------- |
| mvab   | MVABase of the model. If 0 then assume same as machine base                                                            |
| db     | Deadband below which IBFFR is initiated (1-frequency) \>= dbd (pu)                                                     |
| p1     | Power Point 1                                                                                                          |
| p2     | Power Point 2                                                                                                          |
| p3     | Power Point 3                                                                                                          |
| p4     | Power Point 4                                                                                                          |
| p5     | Power Point 5                                                                                                          |
| p6     | Power Point 6                                                                                                          |
| dP1    | dP 1 Point                                                                                                             |
| dPmin1 | dPmin 1 Point                                                                                                          |
| Trise1 | Rise Time 1 Point                                                                                                      |
| Tpeak1 | Peak Time 1 Point                                                                                                      |
| Tfall1 | Fall Time 1 Point                                                                                                      |
| Trec1  | Recovery Time 1 Point                                                                                                  |
| dP2    | dP 2 Point                                                                                                             |
| dPmin2 | dPmin 2 Point                                                                                                          |
| Trise2 | Rise Time 2 Point                                                                                                      |
| Tpeak2 | Peak Time 2 Point                                                                                                      |
| Tfall2 | Fall Time 2 Point                                                                                                      |
| Trec2  | Recovery Time 2 Point                                                                                                  |
| dP3    | dP 3 Point                                                                                                             |
| dPmin3 | dPmin 3 Point                                                                                                          |
| Trise3 | Rise Time 3 Point                                                                                                      |
| Tpeak3 | Peak Time 3 Point                                                                                                      |
| Tfall3 | Fall Time 3 Point                                                                                                      |
| Trec3  | Recovery Time 3 Point                                                                                                  |
| dP4    | dP 4 Point                                                                                                             |
| dPmin4 | dPmin 4 Point                                                                                                          |
| Trise4 | Rise Time 4 Point                                                                                                      |
| Tpeak4 | Peak Time 4 Point                                                                                                      |
| Tfall4 | Fall Time 4 Point                                                                                                      |
| Trec4  | Recovery Time 4 Point                                                                                                  |
| dP5    | dP 5 Point                                                                                                             |
| dPmin5 | dPmin 5 Point                                                                                                          |
| Trise5 | Rise Time 5 Point                                                                                                      |
| Tpeak5 | Peak Time 5 Point                                                                                                      |
| Tfall5 | Fall Time 5 Point                                                                                                      |
| Trec5  | Recovery Time 5 Point                                                                                                  |
| dP6    | dP 6 Point                                                                                                             |
| dPmin6 | dPmin 6 Point                                                                                                          |
| Trise6 | Rise Time 6 Point                                                                                                      |
| Tpeak6 | Peak Time 6 Point                                                                                                      |
| Tfall6 | Fall Time 6 Point                                                                                                      |
| Trec6  | Recovery Time 6 Point                                                                                                  |
| Tflt   | Filter time constant for frequency measurement \[seconds\]                                                             |
| Tlapse | Time in seconds that the IBFFR can reinitiate. Time is measured after the Recovery Time has elapsed on previous IBFFR. |

---

<a id="pref-controller"></a>

## Pref Controller

*Source: [`Content/TransientModels_HTML/Pref Controller.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Pref Controller.htm)*

_This topic has no body text in the source help file._

---

<a id="lcfb1"></a>

## LCFB1

*Source: [`Content/TransientModels_HTML/Pref Controller LCFB1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Pref Controller LCFB1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Pref Controller LCFB1 0001](images/Pref_Controller_LCFB1_0001.svg)

**Parameters:**

|                   |                                                                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Type              | Flag indicating type of turbine governor reference (not used)                                                                                 |
| FrequencyBiasFlag | 1 to enable, 0 to disable                                                                                                                     |
| PowerControlFlag  | 1 to enable, 0 to disable                                                                                                                     |
| db                | Controller dead band                                                                                                                          |
| emax              | Maximum control error                                                                                                                         |
| Fb                | Frequency bias gain                                                                                                                           |
| Kp                | Proportional gain                                                                                                                             |
| Ki                | Integral gain                                                                                                                                 |
| Tpelec            | Power transducer time constant (seconds)                                                                                                      |
| Irmax             | Maximum turbine speed/load reference bias                                                                                                     |
| Pmwset            | Power controller setpoint, MW                                                                                                                 |
| Kdrp              | Output scaling; if value is \<= 0 then is it automatically set to either 1 for a speed reference governor or 25 for a load reference governor |

---

<a id="lcfb1-pti"></a>

## LCFB1_PTI

*Source: [`Content/TransientModels_HTML/Pref Controller LCFB1_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Pref Controller LCFB1_PTI.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Pref Controller LCFB1 PTI 0001](images/Pref_Controller_LCFB1_PTI_0001.svg)

**Parameters:**

|                   |                                                               |
| ----------------- | ------------------------------------------------------------- |
| Type              | Flag indicating type of turbine governor reference (not used) |
| FrequencyBiasFlag | 1 to enable, 0 to disable                                     |
| PowerControlFlag  | 1 to enable, 0 to disable                                     |
| db                | Controller dead band                                          |
| emax              | Maximum control error                                         |
| Fb                | Frequency bias gain                                           |
| Kp                | Proportional gain                                             |
| Ki                | Integral gain                                                 |
| Tpelec            | Power transducer time constant (seconds)                      |
| Irmax             | Maximum turbine speed/load reference bias                     |

---

<a id="wtgtrq-a"></a>

## WTGTRQ_A

*Source: [`Content/TransientModels_HTML/Pref Controller WTGTRQ_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Pref Controller WTGTRQ_A.htm)*

In PTI: **WTTQA1** is the same as **WTGTRQ\_A** model.

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tp \< 0.125\*Mult\*TimeStep then Tp = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tp \< 0.25\*Mult\*TimeStep then Tp = 0.25\*Mult\*TimeStep
  - If 0.0 \< Twref \< 0.125\*Mult\*TimeStep then Twref = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Twref \< 0.25\*Mult\*TimeStep then Twref = 0.25\*Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Pref Controller WTGTRQ A 0001](images/Pref_Controller_WTGTRQ_A_0001.svg)

**Parameters for WTGTRQ\_A:**

|         |                                                                                    |
| ------- | ---------------------------------------------------------------------------------- |
| Flag    | 0=Torque Control; 1=Speed control; 2=Alternative with Pref0 feeding to Temax value |
| Kip     | Integral Gain                                                                      |
| Kpp     | Proportional Gain                                                                  |
| Tp      | Power measurement lag time constant                                                |
| Twref   | Speed measurement time constant                                                    |
| Temax   | Maximum torque                                                                     |
| Temin   | Minimum torque                                                                     |
| P1      | Power Point 1 for mapping of Pelec to speed function                               |
| Speed1  | Speed Point 1 for mapping of Pelec to speed function                               |
| P2      | Power Point 2 for mapping of Pelec to speed function                               |
| Speed2  | Speed Point 2 for mapping of Pelec to speed function                               |
| P3      | Power Point 3 for mapping of Pelec to speed function                               |
| Speed3  | Speed Point 3 for mapping of Pelec to speed function                               |
| P4      | Power Point 4 for mapping of Pelec to speed function                               |
| Speed4  | Speed Point 4 for mapping of Pelec to speed function                               |
| MVABase | MVA Base for model                                                                 |

**Parameters for WTTQA1:**

|         |                                                                                    |
| ------- | ---------------------------------------------------------------------------------- |
| Flag    | 0=Torque Control; 1=Speed control; 2=Alternative with Pref0 feeding to Temax value |
| Kpp     | Proportional Gain                                                                  |
| Kip     | Integral Gain                                                                      |
| Tp      | Power measurement lag time constant                                                |
| Twref   | Speed measurement time constant                                                    |
| Temax   | Maximum torque                                                                     |
| Temin   | Minimum torque                                                                     |
| P1      | Power Point 1 for mapping of Pelec to speed function                               |
| Speed1  | Speed Point 1 for mapping of Pelec to speed function                               |
| P2      | Power Point 2 for mapping of Pelec to speed function                               |
| Speed2  | Speed Point 2 for mapping of Pelec to speed function                               |
| P3      | Power Point 3 for mapping of Pelec to speed function                               |
| Speed3  | Speed Point 3 for mapping of Pelec to speed function                               |
| P4      | Power Point 4 for mapping of Pelec to speed function                               |
| Speed4  | Speed Point 4 for mapping of Pelec to speed function                               |
| MVABase | MVA Base for model                                                                 |

---

<a id="wtgwgo-a"></a>

## WTGWGO_A

*Source: [`Content/TransientModels_HTML/Pref Controller WTGWGO_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Pref Controller WTGWGO_A.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tfltr \< 0.5\*Mult\*TimeStep then Tfltr = 0.0  
    ElseIf 0.55\*Mult\*TimeStep \< Tfltr \< Mult\*TimeStep then Tfltr = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Pref Controller WTGWGO A 0001](images/Pref_Controller_WTGWGO_A_0001.svg)

**Parameters:**

|       |                                                                          |
| ----- | ------------------------------------------------------------------------ |
| Vwgo  | Voltage threshold below with the WGO function is initiated \[pu\]        |
| Pwgo1 | Power reference held during a fault when WGO is initiated \[pu\]         |
| rpw1  | Ramp rate at which power is increased from Pwgo1 to Pwgo2 \[pu/s\]       |
| Pwgo2 | Power reference held for Thold seconds after the fault \[pu\]            |
| rpw2  | Ramp rate at which power is increased from Pwgo2 back to normal \[pu/s\] |
| Thold | Time for which the power reference is held at Pwgo2 \[s\]                |
| eps   | Small hysteresis on voltage recovery to start the first ramp \[pu\]      |
| Tfltr | Voltage filter time constant \[s\]                                       |

---

<a id="relay"></a>

## Relay

*Source: [`Content/TransientModels_HTML/Generator Relay.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Generator Relay.htm)*

_This topic has no body text in the source help file._

---

<a id="atrrelay"></a>

## ATRRELAY

*Source: [`Content/TransientModels_HTML/Relay Model ATRRELAY.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model ATRRELAY.htm)*

Added in version 19

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|            |                                                                                                                                                                                                                            |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| u1vsu2     | Unit 1 (0) vs Unit 2 (1) preferences switch selection                                                                                                                                                                      |
| u3vsu4     | Unit 3 (0) vs Unit 4 (1) preferences switch selection                                                                                                                                                                      |
| smvslg     | Small unit (0) vs large unit (1) preference switch selection                                                                                                                                                               |
| lgvs2sm    | Large unit (0) vs 2 small unit (1) preference switch selection                                                                                                                                                             |
| Monitor    | Mute mode enabled (1) or disabled (0)                                                                                                                                                                                      |
| u1delay    | Unit 1 relay and breaker time delay (sec)                                                                                                                                                                                  |
| u2delay    | Unit 2 relay and breaker time delay (sec)                                                                                                                                                                                  |
| u3delay    | Unit 3 relay and breaker time delay (sec)                                                                                                                                                                                  |
| u4delay    | Unit 4 relay and breaker time delay (sec)                                                                                                                                                                                  |
| auxdelay   | Auxiliary load trip time delay (sec)                                                                                                                                                                                       |
| GenNum     | If GenNum = 2 then generator to which model is assigned is unit 2 and then Gen2 would represent unit 1, and so on. Also NOTE that the results of the gens are now going to be in a different order if the GenNum is not 1. |
| LeaveOneOn | LeaveOneOn: Set to a non-zero value to force at least one generator in this to remain online when a tripping command is sent. The generator with the smallest initial MW output will remain on.                            |

---

<a id="frqdcat"></a>

## FRQDCAT

*Source: [`Content/TransientModels_HTML/Relay Model FRQDCAT and FRQTPAT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model FRQDCAT and FRQTPAT.htm)*

**AutoCorrection Properties**

\-None

**Parameters for FRQDCAT:**

|             |                                     |
| ----------- | ----------------------------------- |
| FreqPickLow | Frequency Low-Pick, Hertz           |
| FreqPickUp  | Frequency High-Pick, Hertz          |
| RelayTP     | Relay Pickup Time, Seconds          |
| BreakerTB   | Breaker Opening Time Delay, Seconds |

**Parameters for FRQTPAT:**

|             |                                     |
| ----------- | ----------------------------------- |
| FreqPickLow | Frequency Low-Pick, Hertz           |
| FreqPickUp  | Frequency High-Pick, Hertz          |
| RelayTP     | Relay Pickup Time, Seconds          |
| BreakerTB   | Breaker Opening Time Delay, Seconds |

**footnotes:** FRQDCAT disconnects all the devices connected to the generator bus, and FRQTPAT only disconnects the generator.

Model support by PSSE

---

<a id="genof"></a>

## GENOF

*Source: [`Content/TransientModels_HTML/Relay Model GENOF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GENOF.htm)*

**AutoCorrection Properties**

To be documented.

**Parameters:**

|            |                                          |
| ---------- | ---------------------------------------- |
| Monitor    | Monitor. 0 = Alarm; 1 = Trip             |
| FreqPickUp | Frequency Pick-up, Hertz                 |
| RelayTD    | Over-Frequency Relay Time Delay, Seconds |
| BreakerTD  | Breaker Opening Time Delay, Seconds      |

Model supported by PowerWorld

---

<a id="gp1"></a>

## GP1

*Source: [`Content/TransientModels_HTML/Relay Model GP1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GP1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Relay Model GP1 0001](images/Relay_Model_GP1_0001.svg)

**Parameters:**

|      |                                             |
| ---- | ------------------------------------------- |
| vuv  | under-voltage relay pickup setting, p.u.    |
| tuv  | under-voltage relay time setting, seconds   |
| vov  | over-voltage relay pickup setting, p.u.     |
| tov  | over-voltage relay time setting, seconds    |
| ifoc | over-excitation relay pickup setting, p.u.  |
| kfoc | over-excitation relay timer coefficient,    |
| afoc | over-excitation relay timer coefficient,    |
| fof  | over-frequency relay pickup setting, p.u.   |
| tof  | over-frequency relay time setting, seconds  |
| fuf  | under-frequency relay pickup setting, p.u.  |
| tuf  | under-frequency relay time setting, seconds |
| isoc | over-current relay pickup setting, p.u.     |
| ksoc | over-current relay timer coefficient,       |
| asoc | over-current relay timer coefficient,       |
| pmtr | reverse-power relay pickup setting, p.u.    |
| tmtr | reverse-power relay time setting, seconds   |

---

<a id="gp2"></a>

## GP2

*Source: [`Content/TransientModels_HTML/Relay Model GP2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GP2.htm)*

**AutoCorrection Properties**

To be documented.

This model is the same as GP1 but have a flag parameter:

\-**flag**: \<=0 means alarm only, \>0 means trip

Model Equations and/or Block Diagrams

![Relay Model GP1 0001](images/Relay_Model_GP1_0001.svg)

**Parameters:**

|      |                                             |
| ---- | ------------------------------------------- |
| flag | \<=0 means alarm only, \>0 means trip       |
| vuv  | under-voltage relay pickup setting, p.u.    |
| tuv  | under-voltage relay time setting, seconds   |
| vov  | over-voltage relay pickup setting, p.u.     |
| tov  | over-voltage relay time setting, seconds    |
| ifoc | over-excitation relay pickup setting, p.u.  |
| kfoc | over-excitation relay timer coefficient,    |
| afoc | over-excitation relay timer coefficient,    |
| fof  | over-frequency relay pickup setting, p.u.   |
| tof  | over-frequency relay time setting, seconds  |
| fuf  | under-frequency relay pickup setting, p.u.  |
| tuf  | under-frequency relay time setting, seconds |
| isoc | over-current relay pickup setting, p.u.     |
| ksoc | over-current relay timer coefficient,       |
| asoc | over-current relay timer coefficient,       |
| pmtr | reverse-power relay pickup setting, p.u.    |
| tmtr | reverse-power relay time setting, seconds   |

---

<a id="gp3"></a>

## GP3

*Source: [`Content/TransientModels_HTML/Relay Model GP3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GP3.htm)*

**AutoCorrection Properties**

\-None

This model represents a combination of the generic generator protection relay models GP1 and GP2. This model represent the generator protection for over and under voltage, over and under frequency, reverse power and stator and field over current.

The model followed the specifications develop by NERC and the attached pdf present the NERC GP3 Generic Protection Model for Generator specification. The model is coded exactly as presented in the NERC specificqations.

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|       |                                                                                                                                              |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| flag1 | 0 = alarm only, 1 = trip generator                                                                                                           |
| flag2 | 1 = monitor generator, 2 = monitor all generators in areas, 3 = monitor all generator in zone, 4 = monitor all generators in the entire case |
| vhz   | V/Hz trip setting (pu)                                                                                                                       |
| tvhz  | Definite time trip for V/Hz (s)                                                                                                              |
| vuv   | Under-voltage trip setting (pu)                                                                                                              |
| tvuv  | Definite time trip for UV (s)                                                                                                                |
| vov   | Over-voltage trip setting (pu)                                                                                                               |
| tvov  | Definite time trip for OV (s)                                                                                                                |
| pmtr  | Reverse power trip setting (pu)                                                                                                              |
| tpmr  | Definite time trip on reverse power (s)                                                                                                      |
| Xz1   | Loss of field Zone 1 impedance (pu)                                                                                                          |
| Xz2   | Loss of field Zone 2 impedance (pu))                                                                                                         |
| Xoff  | Loss of field impedance off set (pu))                                                                                                        |
| tz1   | Definite time trip for Zone 1 of LOF (s)                                                                                                     |
| tz2   | Definite time trip for Zone 2 of LOF (s)                                                                                                     |
| ioc   | Stator Over current trip pickup setting (pu)                                                                                                 |
| koc   | Time factor for over current trip (s)                                                                                                        |
| boc   | Time coefficient for over current trip (s)                                                                                                   |
| poc   | Exponent for inverse time                                                                                                                    |
| troc  | Reset time for over current relay (s)                                                                                                        |
| fof   | Over speed trip setting (pu)                                                                                                                 |
| tof   | Definite time trip for OF (s)                                                                                                                |
| fuf   | Under speed trip setting (pu)                                                                                                                |
| tuf   | Definite time trip for UF (s)                                                                                                                |
| delp  | Delta power imbalance for Power/Load Unbalance Relay (pu)                                                                                    |
| tdelp | Definite time trip for Power/Load Unbalance Relay (s)                                                                                        |
| ifoc  | Over excitation trip setting (pu)                                                                                                            |
| tfoc  | Definite time trip for over excitation (s)                                                                                                   |

---

<a id="gvphzft"></a>

## GVPHZFT

*Source: [`Content/TransientModels_HTML/Relay Model GVPHZFT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GVPHZFT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

**Parameters:**

|            |                       |
| ---------- | --------------------- |
| VHZpickup1 | Pickup1 (p.u. - V/Hz) |
| tdelay1    | Time Delay1           |
| VHZpickup2 | Pickup2 (p.u. - V/Hz) |
| tdelay2    | Time Delay2           |
| bdelay     | Breaker Delay         |

---

<a id="gvphzit"></a>

## GVPHZIT

*Source: [`Content/TransientModels_HTML/Relay Model GVPHZIT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model GVPHZIT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

**Parameters:**

|           |                      |
| --------- | -------------------- |
| curvef    | Curve Family         |
| curvet    | Curve Type           |
| VHZpickup | Pickup (p.u. - V/Hz) |
| tdial     | Time Dial            |
| bdelay    | Breaker Delay        |

---

<a id="lhfrt"></a>

## LHFRT

*Source: [`Content/TransientModels_HTML/Relay Model LHFRT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model LHFRT.htm)*

**AutoCorrection Properties**

If Fref \<= 0 then assumption is made that Fref = 60.0

The units of the dftrp1, dftrp2, … dftrp10 are based on the value of Fref. The test for determining whether the relay will trip is as follows.

Value = (Monitored Frequency in pu – 1.0)\*Fref

If (dftrp1 \> 0) and (Value \> dftrp1) then activate timer for dttrp1 else Reset the timer

If (dftrp1 \< 0) and (Value \< dftrp1) then activate timer for dttrp1 else Reset the timer

Each timer acts independently of other timers. If a time remains active for longer than the respective dttrpX value, then it will trip the generator.

As an example, if the nominal frequency of your system in 60 Hz and you have trip levels of frequency at 65.0, 60.5, 59.3, 57.0, 50.0 Hz, then the following Fref and dftrpX values would be equivalent.

|      |         |         |            |        |            |
| ---- | ------- | ------- | ---------- | ------ | ---------- |
| Fref | dftrp1  | dftrp2  | dftrp3     | dftrp4 | dftrp5     |
| 60.0 | 5.0     | 0.5     | \-0.7      | \-3.0  | \-10.0     |
| 1.0  | 0.08333 | 0.00833 | \-0.011667 | \-0.05 | \-0.166667 |

**Parameters:**

|         |                                                                                                           |
| ------- | --------------------------------------------------------------------------------------------------------- |
| Fref    | Frequency ref., Hz                                                                                        |
| dftrp1  | Delta frequency trip level, Hz                                                                            |
| dftrp2  | Delta frequency trip level, Hz                                                                            |
| dftrp3  | Delta frequency trip level, Hz                                                                            |
| dftrp4  | Delta frequency trip level, Hz                                                                            |
| dftrp5  | Delta frequency trip level, Hz                                                                            |
| dftrp6  | Delta frequency trip level, Hz                                                                            |
| dftrp7  | Delta frequency trip level, Hz                                                                            |
| dftrp8  | Delta frequency trip level, Hz                                                                            |
| dftrp9  | Delta frequency trip level, Hz                                                                            |
| dftrp10 | Delta frequency trip level, Hz                                                                            |
| dttrp1  | Frequency trip time, sec.                                                                                 |
| dttrp2  | Frequency trip time, sec.                                                                                 |
| dttrp3  | Frequency trip time, sec.                                                                                 |
| dttrp4  | Frequency trip time, sec.                                                                                 |
| dttrp5  | Frequency trip time, sec.                                                                                 |
| dttrp6  | Frequency trip time, sec.                                                                                 |
| dttrp7  | Frequency trip time, sec.                                                                                 |
| dttrp8  | Frequency trip time, sec.                                                                                 |
| dttrp9  | Frequency trip time, sec.                                                                                 |
| dttrp10 | Frequency trip time, sec.                                                                                 |
| Alarm   | If greater than zero, no tripping action is enforced; a message is printed when a trip level is exceeded. |

Model supported by PSLF

---

<a id="lhsrt"></a>

## LHSRT

*Source: [`Content/TransientModels_HTML/Relay Model LHSRT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model LHSRT.htm)*

**AutoCorrection Properties**

To be documented.

The values of dstrp1, dstrp2, … dstrp10 represent deviations from synchronous speed in per unitThe test for determining whether the relay will trip is as follows.

Value = generator speed deviation from synchronous speed in per unit

If (dstrp1 \> 0) and (Value \> dstrp1) then activate timer for dttrp1 else Reset the timer

If (dstrp1 \< 0) and (Value \< dstrp1) then activate timer for dttrp1 else Reset the timer

Each timer acts independently of other timers. If a time remains active for longer than the respective dttrpX value, then it will trip the generator.

**Parameters:**

|         |                                                                                                           |
| ------- | --------------------------------------------------------------------------------------------------------- |
| dstrp1  | Delta speed trip level, pu                                                                                |
| dstrp2  | Delta speed trip level, pu                                                                                |
| dstrp3  | Delta speed trip level, pu                                                                                |
| dstrp4  | Delta speed trip level, pu                                                                                |
| dstrp5  | Delta speed trip level, pu                                                                                |
| dstrp6  | Delta speed trip level, pu                                                                                |
| dstrp7  | Delta speed trip level, pu                                                                                |
| dstrp8  | Delta speed trip level, pu                                                                                |
| dstrp9  | Delta speed trip level, pu                                                                                |
| dstrp10 | Delta speed trip level, pu                                                                                |
| dttrp1  | Speed trip time, sec.                                                                                     |
| dttrp2  | Speed trip time, sec.                                                                                     |
| dttrp3  | Speed trip time, sec.                                                                                     |
| dttrp4  | Speed trip time, sec.                                                                                     |
| dttrp5  | Speed trip time, sec.                                                                                     |
| dttrp6  | Speed trip time, sec.                                                                                     |
| dttrp7  | Speed trip time, sec.                                                                                     |
| dttrp8  | Speed trip time, sec.                                                                                     |
| dttrp9  | Speed trip time, sec.                                                                                     |
| dttrp10 | Speed trip time, sec.                                                                                     |
| Alarm   | If greater than zero, no tripping action is enforced; a message is printed when a trip level is exceeded. |

Model supported by PSLF

---

<a id="lhvrt"></a>

## LHVRT

*Source: [`Content/TransientModels_HTML/Relay Model LHVRT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model LHVRT.htm)*

**AutoCorrection Properties**

To be documented.

Treatment of Model in Power Flow Contingency Analysis

When a transient stability model is used in the power flow contingency analysis using the [special option for the power flow contingency solution](22-contingency-analysis-options.md#transient-models), then the model determines how to report violation for the Monitor Only option as well as specifying a TimeDelay and Trip/Act action. The following table describes this and uses the following text conventions.

  - **Green**ext are parameters of a stability model.
  - **Blue** text are a parameter of the contingency options.
  - Other **bold** text are “local variables” used in this description.

<table>
<tbody>
<tr class="odd">
<td><p>Model Evaluation</p></td>
<td><p>Description</p></td>
<td><p>Specific Implementation for this model</p></td>
</tr>
<tr class="even">
<td><p><strong>Monitor Only</strong></p></td>
<td><p>Determine a Boolean result to indicate whether the stability model is “violated” and ready to do something?</p></td>
<td><p>Find the <span class="underline">highest</span> low voltage value specified (for all <strong>dvtrpX</strong> values which are negative these are the <strong>vref+dvtrpX</strong> values) which has a time-delay associated with it which is less than the <strong>TSModelMaxDelay</strong> specified as part of dynamic model input data (call this <strong>UseLowVolt</strong>). For the value found for <strong>UseLowVolt</strong>, take the corresponding Voltage Trip Time (<strong>dttrpX</strong> values) and call this <strong>UseLowVoltTime</strong>.</p>
<p> </p>
<p>Find the <span class="underline">lowest</span> high voltage value specified (for all <strong>dvtrpX</strong> values which are positive these are the <strong>vref+dvtrpX</strong> values) which has a time-delay associated with it which is less than the <strong>TSModelMaxDelay</strong> specified as part of dynamic model input data (call this <strong>UseHighVolt</strong>). For the value found for <strong>UseHighVolt</strong>, take the corresponding Voltage Trip Time (<strong>dttrpX</strong> values) and call this <strong>UseHighVoltTime</strong>.</p>
<p> </p>
<p>Evaluate whether</p>
<p>“Present Voltage PU &gt; <strong>UseHighVolt</strong>” or</p>
<p>“Present Voltage PU &lt; <strong>UseLowVolt</strong>”</p></td>
</tr>
<tr class="odd">
<td><p>TimeDelay used in <strong>Trip/Act</strong></p></td>
<td><p>Time in seconds that the model needs to remain “violated” before it will actually apply an action.</p></td>
<td><p>If Violated because of exceeding <strong>UseHighVolt</strong>, then TimeDelay is <strong>UseHighVoltTime</strong></p>
<p>If Violated because of exceeding <strong>UseLowVolt</strong>, then TimeDelay is <strong>UseLowVoltTime</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Trip/Act</strong> Action</p></td>
<td><p>If violated for the particular time, then this procedure must be written to actually implement the action.</p></td>
<td><p>Model will open the generator</p></td>
</tr>
</tbody>
</table>

Model Equations and/or Block Diagrams

The values of dvtrp1, dvtrp2, … dvtrp10 represent deviations from the value of Vref. The test for determining whether the relay will trip is as follows.

Value = Monitored Voltage in pu – Vref

If (dvtrp1 \> 0) and (Value \> dvtrp1) then activate timer for dttrp1 else Reset the timer

If (dvtrp1 \< 0) and (Value \< dvtrp1) then activate timer for dttrp1 else Reset the timer

Each timer acts independently of other timers. If a time remains active for longer than the respective dttrpX value, then it will trip the generator.

As an example, if the low voltage trip levels are at 0.70, 0.45 and 0.15 and the high voltage trip levels are at 1.10 and 1.23 then both of the following would result in the same behavior (although specifying Vref as 1.0 seems the easier choice)

As an example, if the low voltage trip levels are at 0.70, 0.45 and 0.15 and the high voltage trip levels are at 1.10 and 1.23 then both of the following would result in the same behavior (although specifying Vref as 1.0 seems the easier choice)

|      |        |        |        |        |        |
| ---- | ------ | ------ | ------ | ------ | ------ |
| Vref | dvtrp1 | dvtrp2 | dvtrp3 | dvtrp4 | dvtrp5 |
| 1.0  | \-0.30 | \-0.55 | \-0.85 | 0.10   | 0.23   |
| 1.05 | \-0.35 | \-0.60 | \-0.90 | 0.05   | 0.18   |

**Parameters:**

|         |                                                                                                           |
| ------- | --------------------------------------------------------------------------------------------------------- |
| Vref    | Voltage ref., Hz                                                                                          |
| dvtrp1  | Delta voltage trip level, pu                                                                              |
| dvtrp2  | Delta voltage trip level, pu                                                                              |
| dvtrp3  | Delta voltage trip level, pu                                                                              |
| dvtrp4  | Delta voltage trip level, pu                                                                              |
| dvtrp5  | Delta voltage trip level, pu                                                                              |
| dvtrp6  | Delta voltage trip level, pu                                                                              |
| dvtrp7  | Delta voltage trip level, pu                                                                              |
| dvtrp8  | Delta voltage trip level, pu                                                                              |
| dvtrp9  | Delta voltage trip level, pu                                                                              |
| dvtrp10 | Delta voltage trip level, pu                                                                              |
| dttrp1  | Voltage trip time, sec.                                                                                   |
| dttrp2  | Voltage trip time, sec.                                                                                   |
| dttrp3  | Voltage trip time, sec.                                                                                   |
| dttrp4  | Voltage trip time, sec.                                                                                   |
| dttrp5  | Voltage trip time, sec.                                                                                   |
| dttrp6  | Voltage trip time, sec.                                                                                   |
| dttrp7  | Voltage trip time, sec.                                                                                   |
| dttrp8  | Voltage trip time, sec.                                                                                   |
| dttrp9  | Voltage trip time, sec.                                                                                   |
| dttrp10 | Voltage trip time, sec.                                                                                   |
| Alarm   | If greater than zero, no tripping action is enforced; a message is printed when a trip level is exceeded. |

Model supported by PSLF

---

<a id="vtgdcat"></a>

## VTGDCAT

*Source: [`Content/TransientModels_HTML/Relay Model VTGDCAT and VTGTPAT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Relay Model VTGDCAT and VTGTPAT.htm)*

**AutoCorrection Properties**

\-None

**Parameters for VTGDCAT:**

|              |                                     |
| ------------ | ----------------------------------- |
| VoltThresLow | Voltage Low-threshold, p.u.         |
| VoltThresUp  | Voltage High-threshold, p.u.        |
| RelayTP      | Relay Pickup Time, Seconds          |
| BreakerTB    | Breaker Opening Time Delay, Seconds |

**Parameters for VTGTPAT:**

|              |                                     |
| ------------ | ----------------------------------- |
| VoltThresLow | Voltage Low-threshold, p.u.         |
| VoltThresUp  | Voltage High-threshold, p.u.        |
| RelayTP      | Relay Pickup Time, Seconds          |
| BreakerTB    | Breaker Opening Time Delay, Seconds |

**footnotes:** VTGDCAT disconnects all the devices connected to the generator bus, and VTGTPAT only disconnects the generator.

Model supported by PSSE

---

<a id="stator-current-limiter"></a>

## Stator Current Limiter

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter.htm)*

_This topic has no body text in the source help file._

---

<a id="scl1c"></a>

## SCL1C

*Source: [`Content/TransientModels_HTML/Stator Current Limiter SCL1C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stator Current Limiter SCL1C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< TIT \< 0.5\*Mult\*TimeStep then TIT = 0, ElseIf 0.5\*Mult\*TimeStep \< TIT \< Mult\*TimeStep then TIT = Mult\*TimeStep

  - If 0.0 \< TQSCL \< 0.5\*Mult\*TimeStep then TQSCL = 0, ElseIf 0.5\*Mult\*TimeStep \< TQSCL \< Mult\*TimeStep then TQSCL = Mult\*TimeStep

  - If 0.0 \< TINV \< 0.5\*Mult\*TimeStep then TINV = 0, ElseIf 0.5\*Mult\*TimeStep \< TINV \< Mult\*TimeStep then TINV = Mult\*TimeStep

  - KPoex and KIoex: KPoex can't be 0 if KIoex = 0, if true then KPoex changed to 1.

  - KPuex and KIuex: KPoex can't be 0 if KIuex = 0, if true then KPuex changed to 1.

  - If VSCLmax \< VSCLmin then swap the values. If VSCLmax\< 0 then VSCLmax change sign to positive. If VSCLmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VSCL \> VSCLmax, then VSCLmax = VSCL limits or if VSCL \< VSCLmin, then VSCLmin = VSCL

Model Equations and/or Block Diagrams

![Stator Current Limiter SCL1C 0001](images/Stator_Current_Limiter_SCL1C_0001.svg)

**Parameters:**

|          |                                                                                       |
| -------- | ------------------------------------------------------------------------------------- |
| TB1oel   | Overexcited regulator denominator lag time constant 1 (s)                             |
| TC1oel   | Overexcited regulator numerator lead time constant 1 (s)                              |
| TB2oel   | Overexcited regulator denominator lag time constant 2 (s)                             |
| TC2oel   | Overexcited regulator numerator lead time constant 2 (s)                              |
| KPoel    | Overexcited PID regulator proportional gain (pu)                                      |
| KIoel    | Overexcited PID regulator integral gain (pu)                                          |
| KDoel    | Overexcited PID regulator differential gain (pu)                                      |
| TDoel    | Overexcited PID regulator differential time constant (s)                              |
| VOELmax3 | Maximum OEL PID output limit (pu)                                                     |
| VOELmin3 | Minimum OEL PID output limit (pu)                                                     |
| VOELmax2 | Maximum OEL lead lag 1 output limit (pu)                                              |
| VOELmin2 | Minimum OEL lead lag 1 output limit (pu)                                              |
| VOELmax1 | Maximum OEL output limit (pu)                                                         |
| VOELmin1 | Minimum OEL output limit (pu)                                                         |
| TB1uel   | Underexcited regulator denominator lag time constant 1 (s)                            |
| TC1uel   | Underexcited regulator numerator lead time constant 1 (s)                             |
| TB2uel   | Underexcited regulator denominator lag time constant 2 (s)                            |
| TC2uel   | Underexcited regulator numerator lead time constant 2 (s)                             |
| KPuel    | Underexcited PID regulator proportional gain (pu)                                     |
| KIuel    | Underexcited PID regulator integral gain (pu)                                         |
| KDuel    | Underexcited PID regulator differential gain (pu)                                     |
| TDuel    | Underexcited PID regulator differential time constant (s)                             |
| VUELmax3 | Maximum UEL PID output limit (pu)                                                     |
| VUELmin3 | Minimum UEL PID output limit (pu)                                                     |
| VUELmax2 | Maximum UEL lead lag 1 output limit (pu)                                              |
| VUELmin2 | Minimum UEL lead lag 1 output limit (pu)                                              |
| VUELmax1 | Maximum UEL output limit (pu                                                          |
| VUELmin1 | Minimum UEL output limit (pu)                                                         |
| Ireset   | SCL reset reference, if inactive (pu)                                                 |
| TenOEL   | Overexcited activation delay time (s)                                                 |
| TenUEL   | Underexcited activation delay time (s)                                                |
| Toff     | SCL reset delay time (s)                                                              |
| ITHoff   | SCL reset threshold value (pu)                                                        |
| TIQoel   | Overexcited reactive current time constant (s)                                        |
| KIQoel   | Overexcited reactive current scaling factor (pu/pu)                                   |
| TIPoel   | Overexcited active current time constant (s)                                          |
| KIPoel   | Overexcited active current scaling factor (pu/pu)                                     |
| TIQuel   | Underexcited reactive current time constant (s)                                       |
| KIQuel   | Underexcited reactive current scaling factor (pu/pu)                                  |
| TIPuel   | Underexcited active current time constant (s)                                         |
| KIPuel   | Underexcited active current scaling factor (pu/pu)                                    |
| TITscl   | Stator current transducer time constant (s)                                           |
| ITFpu    | SCL thermal reference for inverse time calculations (pu)                              |
| Iinst    | SCL instantaneous stator current limit (pu)                                           |
| IinstUEL | Underexcited region instantaneous stator current limit (pu)                           |
| Ilim     | SCL thermal stator current limit (pu)                                                 |
| TAoel    | SCL reference filter time constant (s)                                                |
| c1       | SCL exponent for calculation of IERRinv1 (pu)                                         |
| K1       | SCL gain for calculation of IERRinv1 (pu/pu)                                          |
| c2       | SCL exponent for calculation of IERRinv2 (pu)                                         |
| K2       | SCL gain for calculation of IERRinv2 (pu/pu)                                          |
| VINVmax  | SCL maximum inverse time output (pu)                                                  |
| VINVmin  | SCL minimum inverse time output (pu)                                                  |
| Fixedru  | SCL fixed delay time output (pu)                                                      |
| Fixedrd  | SCL fixed cooling down time output (pu)                                               |
| TSCL     | SCL timer reference (pu)                                                              |
| Tmax     | SCL timer maximum level (pu)                                                          |
| Tmin     | SCL timer minimum level (pu)                                                          |
| KFB      | SCL timer feedback gain (pu)                                                          |
| SW1      | OEL reference ramp logic selection (0 = fixed ramp rates - Kru and Krd, 1 = IERRinv1) |
| Krd      | SCL reference ramp down rate (pu/s)                                                   |
| Kru      | SCL reference ramp up rate (pu/s)                                                     |
| KZRU     | SCL thermal reference release threshold (pu)                                          |
| TVTscl   | Terminal voltage transducer time constant (s)                                         |
| VTmin    | SCLoel minimum voltage reference value (pu)                                           |
| VTreset  | SCLoel voltage reset value (pu)                                                       |
| IQminOEL | SCLoel minimum reactive current reference value (pu)                                  |
| IQmaxUEL | SCLoel maximum reactive current reference value (pu)                                  |
| KPref    | SCL reference scaling factor based on active current (pu)                             |

---

<a id="scl2c"></a>

## SCL2C

*Source: [`Content/TransientModels_HTML/Stator Current Limiter SCL2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Stator Current Limiter SCL2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If KIQoel \<= 0.0001 then KIQoel = 0.0001

  - If KIPoel \<= 0.0001 then KIPoel = 0.0001

  - If KIQuel \<= 0.0001 then KIQuel = 0.0001

  - If KIPuel \<= 0.0001 then KIPuel = 0.0001

  - If ITFpu \<= 0.0001 then ITFpu = 0.0001

  - If 0.0 \< TB1oel \< 0.5\*Mult\*TimeStep then TB1oel = 0, ElseIf 0.5\*Mult\*TimeStep \< TB1oel \< Mult\*TimeStep then TB1oel = Mult\*TimeStep

  - If 0.0 \< TB2oel \< 0.5\*Mult\*TimeStep then TB2oel = 0, ElseIf 0.5\*Mult\*TimeStep \< TB2oel \< Mult\*TimeStep then TB2oel = Mult\*TimeStep

  - If 0.0 \< TB1uel \< 0.5\*Mult\*TimeStep then TB1uel = 0, ElseIf 0.5\*Mult\*TimeStep \< TB1uel \< Mult\*TimeStep then TB1uel = Mult\*TimeStep

  - If 0.0 \< TB2uel \< 0.5\*Mult\*TimeStep then TB2uel = 0, ElseIf 0.5\*Mult\*TimeStep \< TB2uel \< Mult\*TimeStep then TB2uel = Mult\*TimeStep

  - If 0.0 \< TIQoel \< 0.5\*Mult\*TimeStep then TIQoel = 0, ElseIf 0.5\*Mult\*TimeStep \< TIQoel \< Mult\*TimeStep then TIQoel = Mult\*TimeStep

  - If 0.0 \< TIPoel \< 0.5\*Mult\*TimeStep then TIPoel = 0, ElseIf 0.5\*Mult\*TimeStep \< TIPoel \< Mult\*TimeStep then TIPoel = Mult\*TimeStep

  - If 0.0 \< TIQuel \< 0.5\*Mult\*TimeStep then TIQuel = 0, ElseIf 0.5\*Mult\*TimeStep \< TIQuel \< Mult\*TimeStep then TIQuel = Mult\*TimeStep

  - If 0.0 \< TIPuel \< 0.5\*Mult\*TimeStep then TIPuel = 0, ElseIf 0.5\*Mult\*TimeStep \< TIPuel \< Mult\*TimeStep then TIPuel = Mult\*TimeStep

  - If 0.0 \< TITscl \< 0.5\*Mult\*TimeStep then TITscl = 0, ElseIf 0.5\*Mult\*TimeStep \< TITscl \< Mult\*TimeStep then TITscl = Mult\*TimeStep

  - If 0.0 \< TAoel \< 0.5\*Mult\*TimeStep then TAoel = 0, ElseIf 0.5\*Mult\*TimeStep \< TAoel \< Mult\*TimeStep then TAoel = Mult\*TimeStep

  - If 0.0 \< TVTscl \< 0.5\*Mult\*TimeStep then TVTscl = 0, ElseIf 0.5\*Mult\*TimeStep \< TVTscl \< Mult\*TimeStep then TVTscl = Mult\*TimeStep

  - KPoel and KIoel: KPoel can't be 0 if KIoel = 0, if true then KPoel changed to 1.

  - KPuel and KIuex: KPoel can't be 0 if KIuel = 0, if true then KPuel changed to 1.

  - If VOELmax1 \< VOELmin1 then swap the values. If VOELmax1 \< 0 then VOELmax1 change sign to positive. If VOELmin1 \> 0 then change sign to negative.

  - If VOELmax2 \< VOELmin2 then swap the values. If VOELmax2 \< 0 then VOELmax2 change sign to positive. If VOELmin2 \> 0 then change sign to negative.

  - If VOELmax3 \< VOELmin3 then swap the values. If VOELmax3 \< 0 then VOELmax3 change sign to positive. If VOELmin3 \> 0 then change sign to negative.

  - If VUELmax1 \< VUELmin1 then swap the values. If VUELmax1 \< 0 then VUELmax1 change sign to positive. If VUELmin1 \> 0 then change sign to negative.

  - If VUELmax2 \< VUELmin2 then swap the values. If VUELmax2 \< 0 then VUELmax2 change sign to positive. If VUELmin1 \> 0 then change sign to negative.

  - If VUELmax3 \< VUELmin3 then swap the values. If VUELmax3 \< 0 then VUELmax3 change sign to positive. If VUELmin1 \> 0 then change sign to negative.

  - If VINVmax \< VINVmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VSCLoel \> VOELmax1, then VOELmax1 = VSCLoel limits or if VSCLoel \< VOELmin1, then VOELmin1 = VSCLoel

  - If OELLeadLag2 \> VOELmax2, then VOELmax2 = OELLeadLag2 limits or if OELLeadLag2 \< VOELmin2, then VOELmin2 = OELLeadLag2

  - If OELLeadLag2\_Input \> VOELmax3, then VOELmax3 = OELLeadLag2\_Input limits or if OELLeadLag2\_Input \< VOELmin3 , then VOELmin3 = OELLeadLag2\_Input

  - If VSCLuel \> VUELmax1 , then VUELmax1 = VSCLuel limits or if VSCLuel \< VUELmin1, then VUELmin1 = VSCLuel

  - If UELLeadLag2 \> VUELmax2, then VUELmax2 = UELLeadLag2 limits or if UELLeadLag2 \< VUELmin2, then VUELmin2 = UELLeadLag2

  - If UELLeadLag2\_Input \> VUELmax3, then VUELmax3 = UELLeadLag2\_Input limits or if UELLeadLag2\_Input \< VUELmin3, then VUELmin3 = UELLeadLag2\_Input

  - if IERRinv2 \> VINVmax , then VINVmax = IERRinv2 limits or if IERRinv2 \< VINVmin, then VINVmin = IERRinv2

Model Equations and/or Block Diagrams

![Stator Current Limiter SCL2C 0001](images/Stator_Current_Limiter_SCL2C_0001.svg)

![Stator Current Limiter SCL2C 0002](images/Stator_Current_Limiter_SCL2C_0002.svg)

**Parameters:**

|         |                                                                           |
| ------- | ------------------------------------------------------------------------- |
| ISCLim  | SCL terminal current pick up level (pu)                                   |
| TIT     | Terminal current transducer equivalent time constant (s)                  |
| K       | SCL timing characteristic factor                                          |
| TQSL    | Reactive current transducer equivalent time constant (s)                  |
| IQmin   | Dead band for reactive current (pu)                                       |
| VSCLdb  | Dead band for reactive power or power factor (pu)                         |
| TINV    | Inverse time delay after pickup (s)                                       |
| TDSCL   | Fixed time delay after pickup (s)                                         |
| SW1     | Reactive current/reactive power selector (1 = Position A, 2 = Position B) |
| SW2     | Fixed time or inverse time selector                                       |
| KPoex   | SCL proportional gain overexcited range (pu)                              |
| KIoex   | SCL integral gain overexcited gain (pu/s)                                 |
| KPuex   | SCL proportional gain underexcited range (pu)                             |
| KIuex   | SCL integral gain underexcited gain (pu/s)                                |
| VSCLmax | SCL upper integrator limit (pu)                                           |
| VSCLmin | SCL lower integrator limit (pu)                                           |

---

<a id="mnlex1"></a>

## MNLEX1

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter MNLEX1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter MNLEX1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tm \< 0.5\*Mult\*TimeStep then Tm = 0, ElseIf 0.5\*Mult\*TimeStep \< Tm \< Mult\*TimeStep then Tm = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Under Excitation Limiter MNLEX1 0001](images/Under_Excitation_Limiter_MNLEX1_0001.svg)

**Parameters:**

|        |                              |
| ------ | ---------------------------- |
| Kf2    | Kf2 Time constant            |
| Tf2    | Tf2 (\> 0)                   |
| Km     | Km (gain)                    |
| Tm     | Tm (gain time constant, sec) |
| Melmax | Maximum limit                |
| K      | K,mel                        |

---

<a id="mnlex2"></a>

## MNLEX2

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter MNLEX2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter MNLEX2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tm \< 0.5\*Mult\*TimeStep then Tm = 0, ElseIf 0.5\*Mult\*TimeStep \< Tm \< Mult\*TimeStep then Tm = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Under Excitation Limiter MNLEX2 0001](images/Under_Excitation_Limiter_MNLEX2_0001.svg)

**Parameters:**

|        |                              |
| ------ | ---------------------------- |
| Kf2    | Kf2 Time constant            |
| Tf2    | Tf2 (\> 0)                   |
| Km     | Km (gain)                    |
| Tm     | Tm (gain time constant, sec) |
| Melmax | Maximum limit                |
| Qo     | Qo (machine MVA base)        |
| Radius | Radius                       |

---

<a id="mnlex3"></a>

## MNLEX3

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter MNLEX3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter MNLEX3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tm \< 0.5\*Mult\*TimeStep then Tm = 0, ElseIf 0.5\*Mult\*TimeStep \< Tm \< Mult\*TimeStep then Tm = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Under Excitation Limiter MNLEX3 0001](images/Under_Excitation_Limiter_MNLEX3_0001.svg)

**Parameters:**

|        |                              |
| ------ | ---------------------------- |
| Kf2    | Kf2 Time constant            |
| Tf2    | Tf2 (\> 0)                   |
| Km     | Km (gain)                    |
| Tm     | Tm (gain time constant, sec) |
| Melmax | Maximum limit                |
| Qo     | Qo (machine MVA base)        |
| B      | B (slope)                    |

---

<a id="uel1"></a>

## UEL1

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter UEL1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter UEL1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tu2 \< 0.5\*Mult\*TimeStep then Tu2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu2 \< Mult\*TimeStep then Tu2 = Mult\*TimeStep

  - If 0.0 \< Tu4 \< 0.5\*Mult\*TimeStep then Tu4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu4 \< Mult\*TimeStep then Tu4 = Mult\*TimeStep

  - Kul and Kui: Kul can't be 0 if Kui = 0, if true then Kul changed to 40.

  - If VUImax \< VUImin then swap the values. If VUImax \< 0 then VUImax change sign to positive. If VUImin \> 0 then change sign to negative.

  - If VULmax \< VULmin then swap the values. If VULmax \< 0 then VULmax change sign to positive. If VULmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Under Excitation Limiter UEL1 0001](images/Under_Excitation_Limiter_UEL1_0001.svg)

**Parameters:**

|        |                                         |
| ------ | --------------------------------------- |
| Kur    | Radius setting, p.u.                    |
| Kuc    | Center setting, p.u.                    |
| Kuf    | Excitation system stabilizer gain, p.u. |
| Vurmax | Limit, p.u.                             |
| Vucmax | Limit, p.u.                             |
| Kui    | Integral gain, p.u.                     |
| Kul    | Proportional gain, p.u.                 |
| Vuimax | PI control maximum output, p.u.         |
| Vuimin | PI control minimum output, p.u.         |
| Tu1    | Lead time constant, sec.                |
| Tu2    | Lag time constant, sec.                 |
| Tu3    | Lead time constant, sec.                |
| Tu4    | Lag time constant, sec.                 |
| Vulmax | UEL maximum output, p.u.                |
| Vulmin | UEL minimum output, p.u.                |

---

<a id="uel2"></a>

## UEL2

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter UEL2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter UEL2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tuv \< 0.5\*Mult\*TimeStep then Tuv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tuv \< Mult\*TimeStep then Tuv = Mult\*TimeStep

  - If 0.0 \< Tup \< 0.5\*Mult\*TimeStep then Tup = 0, ElseIf 0.5\*Mult\*TimeStep \< Tup \< Mult\*TimeStep then Tup = Mult\*TimeStep

  - If 0.0 \< Tuq \< 0.5\*Mult\*TimeStep then Tuq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tuq \< Mult\*TimeStep then Tuq = Mult\*TimeStep

  - If 0.0 \< TuL \< 0.5\*Mult\*TimeStep then TuL = 0, ElseIf 0.5\*Mult\*TimeStep \< TuL \< Mult\*TimeStep then TuL = Mult\*TimeStep

  - If 0.0 \< Tu2 \< 0.5\*Mult\*TimeStep then Tu2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu2 \< Mult\*TimeStep then Tu2 = Mult\*TimeStep

  - If 0.0 \< Tu4 \< 0.5\*Mult\*TimeStep then Tu4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu4 \< Mult\*TimeStep then Tu4 = Mult\*TimeStep

  - Kul and Kui: Kul can't be 0 if Kui = 0, if true then Kul changed to 40.

  - If VUImax \< VUImin then swap the values. If VUImax \< 0 then VUImax change sign to positive. If VUImin \> 0 then change sign to negative.

  - If VULmax \< VULmin then swap the values. If VULmax \< 0 then VULmax change sign to positive. If VULmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Under Excitation Limiter UEL2 0001](images/Under_Excitation_Limiter_UEL2_0001.svg)

**Parameters for UEL2 and UEL2\_PTI:**

|        |                                           |
| ------ | ----------------------------------------- |
| K1     | Voltage exponent                          |
| K2     | Voltage exponent                          |
| Qquad  | 0: Mirror image around MVAR axix          |
| Tuv    | Voltage filter time constant, sec.        |
| Tup    | Real power filter time constant, sec.     |
| Tuq    | Reactive power filter time constant, sec. |
| Kui    | Integral gain, p.u./sec                   |
| Kul    | Proportional gain, p.u.                   |
| Vuimax | PI control block maximum output, p.u.     |
| Vuimin | PI control block minimum output, p.u.     |
| Kuf    | Excitation system stabilizer gain, p.u.   |
| Kfb    | Gain                                      |
| TuL    | Time constant, sec.                       |
| Tu1    | Lead time constant, sec.                  |
| Tu2    | Lag time constant, sec.                   |
| Tu3    | Lead time constant, sec.                  |
| Tu4    | Lag time constant, sec.                   |
| P0     | Point 0 real power, p.u.                  |
| Q0     | Point 0 reactive power, p.u.              |
| P1     | Point 1 real power, p.u.                  |
| Q1     | Point 1 reactive power, p.u.              |
| P2     | Point 2 real power, p.u.                  |
| Q2     | Point 2 reactive power, p.u.              |
| P3     | Point 3 real power, p.u.                  |
| Q3     | Point 3 reactive power, p.u.              |
| P4     | Point 4 real power, p.u.                  |
| Q4     | Point 4 reactive power, p.u.              |
| P5     | Point 5 real power, p.u.                  |
| Q5     | Point 5 reactive power, p.u.              |
| P6     | Point 6 real power, p.u.                  |
| Q6     | Point 6 reactive power, p.u.              |
| P7     | Point 7 real power, p.u.                  |
| Q7     | Point 7 reactive power, p.u.              |
| P8     | Point 8 real power, p.u.                  |
| Q8     | Point 8 reactive power, p.u.              |
| P9     | Point 9 real power, p.u.                  |
| Q9     | Point 9 reactive power, p.u.              |
| P10    | Point 10 real power, p.u.                 |
| Q10    | Point 10 reactive power, p.u.             |
| VULmax | Maximum limit, p.u.                       |
| VULmin | Minimum limit, p.u.                       |

---

<a id="uel2c"></a>

## UEL2C

*Source: [`Content/TransientModels_HTML/Under Excitation Limiter UEL2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Under Excitation Limiter UEL2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Kfix \<= 0.0001 then Kfix = 0.0001

  - If 0.0 \< Tuv \< 0.5\*Mult\*TimeStep then Tuv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tuv \< Mult\*TimeStep then Tuv = Mult\*TimeStep

  - If 0.0 \< Tup \< 0.5\*Mult\*TimeStep then Tup = 0, ElseIf 0.5\*Mult\*TimeStep \< Tup \< Mult\*TimeStep then Tup = Mult\*TimeStep

  - If 0.0 \< Tuq \< 0.5\*Mult\*TimeStep then Tuq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tuq \< Mult\*TimeStep then Tuq = Mult\*TimeStep

  - If 0.0 \< TuL \< 0.5\*Mult\*TimeStep then TuL = 0, ElseIf 0.5\*Mult\*TimeStep \< TuL \< Mult\*TimeStep then TuL = Mult\*TimeStep

  - If 0.0 \< Tu2 \< 0.5\*Mult\*TimeStep then Tu2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu2 \< Mult\*TimeStep then Tu2 = Mult\*TimeStep

  - If 0.0 \< Tu4 \< 0.5\*Mult\*TimeStep then Tu4 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tu4 \< Mult\*TimeStep then Tu4 = Mult\*TimeStep

  - If 0.0 \< TQref \< 0.5\*Mult\*TimeStep then TQref = 0, ElseIf 0.5\*Mult\*TimeStep \< TQref \< Mult\*TimeStep then TQref = Mult\*TimeStep

  - If 0.0 \< Tadj \< 0.5\*Mult\*TimeStep then Tadj = 0, ElseIf 0.5\*Mult\*TimeStep \< Tadj \< Mult\*TimeStep then Tu4 = Mult\*TimeStep

  - Kul and Kui: Kul can't be 0 if Kui = 0, if true then Kul changed to 40.

  - If VUImax \< VUImin then swap the values. If VUImax \< 0 then VUImax change sign to positive. If VUImin \> 0 then change sign to negative.

  - If VUELmax1 \< VUELmin1 then swap the values. If VUELmax1 \< 0 then VUELmax1 change sign to positive. If VUELmin1 \> 0 then change sign to negative.

  - If VUELmax2 \< VUELmin2 then swap the values. If VUELmax2 \< 0 then VUELmax2 change sign to positive. If VUELmin2 \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VUEL \> VUELmax1 , then VUELmax1 = VUEL limits or if VUEL \< VUELmin1 , then VUELmin1 = VUEL
  - If LeadLagU1U2 \> VUELmax2, then VUELmax2 = LeadLagU1U2 limits or if LeadLagU1U2 \< VUELmin2 , then VUELmin2 = LeadLagU1U2
  - If PIIntegrator \> VUImax, then VUImax = PIIntegrator limits or if PIIntegrator \< VUImin, then VUImin = PIIntegrator

Model Equations and/or Block Diagrams

![Under Excitation Limiter UEL2C 0001](images/Under_Excitation_Limiter_UEL2C_0001.svg)

**Parameters:**

|          |                                                                                 |
| -------- | ------------------------------------------------------------------------------- |
| Tup      | UEL real power filter time constant (s)                                         |
| Tuq      | UEL reactive power filter time constant (s)                                     |
| Tuv      | UEL voltage filter time constant (s)                                            |
| Vbias    | UEL voltage bias (pu)                                                           |
| K1       | Voltage exponent for real power input to UEL table                              |
| K2       | Voltage exponent for reactive power output to UEL table                         |
| Kuf      | UEL excitation system stabilizer gain (pu)                                      |
| TQref    | UEL reactive power reference time constant (s)                                  |
| Kfix     | UEL fixed gain reduction factor (pu)                                            |
| Tadj     | UEL adjustable gain reduction time constant (s)                                 |
| SW1      | UEL logic switch for adjustable gain reduction (1 = Position A, 2 = Position B) |
| Kui      | UEL integral gain (pu/s)                                                        |
| Kul      | UEL proportional gain (pu)                                                      |
| Vuimax   | Vuimax: UEL PI control maximum output (pu)                                      |
| Vuimin   | Vuimin: UEL PI control minimum output (pu)                                      |
| Tu1      | UEL numerator lead time constant in first block (s)                             |
| Tu2      | UEL denominator lag time constant in first block (s)                            |
| Tu3      | UEL numerator lead time constant in second block (s)                            |
| Tu4      | UEL denominator lag time constant in second block (s)                           |
| VUELmax1 | VUELmax1: UEL maximum output 1 (pu)                                             |
| VUELmin1 | VUELmin1: UEL minimum output 1 (pu)                                             |
| VUELmax2 | VUELmax2: UEL maximum output 2 (pu)                                             |
| VUELmin2 | VUELmin2: UEL minimum output 2 (pu)                                             |
| Kfb      | UEL FB Gain                                                                     |
| TuL      | UEL FB time constant (s)                                                        |
| Xq       | The Q-axis synchronous reactance of the generator (pu)                          |
| P0       | UEL lookup table real power (first point)                                       |
| Q0       | UEL lookup table reactive power (first point)                                   |
| P1       | UEL lookup table real power (second point)                                      |
| Q1       | UEL lookup table reactive power (second point)                                  |
| P2       | UEL lookup table real power (third point)                                       |
| Q2       | UEL lookup table reactive power (third point)                                   |
| P3       | UEL lookup table real power (fourth point)                                      |
| Q3       | UEL lookup table reactive power (fourth point)                                  |
| P4       | UEL lookup table real power (fifth point)                                       |
| Q4       | UEL lookup table reactive power (fifth point)                                   |
| P5       | UEL lookup table real power (sixth point)                                       |
| Q5       | UEL lookup table reactive power (sixth point)                                   |
| P6       | UEL lookup table real power (seventh point)                                     |
| Q6       | UEL lookup table reactive power (seventh point)                                 |
| P7       | UEL lookup table real power (eigth point)                                       |
| Q7       | UEL lookup table reactive power (eigth point)                                   |
| P8       | UEL lookup table real power (ninth point)                                       |
| Q8       | UEL lookup table reactive power (ninth point)                                   |
| P9       | UEL lookup table real power (tenth point)                                       |
| Q9       | UEL lookup table reactive power (tenth point)                                   |

---

<a id="voltage-compensator"></a>

## Voltage Compensator

*Source: [`Content/TransientModels_HTML/Voltage Compensator.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator.htm)*

_This topic has no body text in the source help file._

---

<a id="ccomp"></a>

## CCOMP

*Source: [`Content/TransientModels_HTML/Voltage Compensator CCOMP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator CCOMP.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Voltage Compensator CCOMP 0001](images/Voltage_Compensator_CCOMP_0001.svg)

**Parameters:**

|      |                                                                                                |
| ---- | ---------------------------------------------------------------------------------------------- |
| rc   | Cross compensation resistance, p.u.                                                            |
| xc   | Cross compensation reactance, p.u.                                                             |
| rt   | Joint compensation resistance, p.u.                                                            |
| xt   | Joint compensation reactance, p.u.                                                             |
| tf   | Filtering time constant, sec.                                                                  |
| flag | Flag 0 means compensation uses sum of current; 1 = means compensation used individual currents |

---

<a id="ccomp4"></a>

## CCOMP4

*Source: [`Content/TransientModels_HTML/Voltage Compensator CCOMP4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator CCOMP4.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Voltage Compensator CCOMP4 0001](images/Voltage_Compensator_CCOMP4_0001.svg)

**Parameters:**

|      |                                                                    |
| ---- | ------------------------------------------------------------------ |
| K1   | Compensation Constant for self                                     |
| K2   | Compensation Constant for Sister Gen 2                             |
| K3   | Compensation Constant for Sister Gen 3                             |
| K4   | Compensation Constant for Sister Gen 4                             |
| Kc   | Overall loop gain; typically set to 1.0 but can be set differently |
| T    | Time Constant, seconds                                             |
| Vmax | Maximum Output, pu                                                 |
| Vmin | Minimum Output, pu                                                 |

---

<a id="comp"></a>

## COMP

*Source: [`Content/TransientModels_HTML/Voltage Compensator COMP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator COMP.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Voltage Compensator COMP 0001](images/Voltage_Compensator_COMP_0001.svg)

**Parameters:**

|    |                        |
| -- | ---------------------- |
| Xe | Vc = Abs(Vt - jXe\*It) |

---

<a id="compcc"></a>

## COMPCC

*Source: [`Content/TransientModels_HTML/Voltage Compensator COMPCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator COMPCC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Voltage Compensator COMPCC 0001](images/Voltage_Compensator_COMPCC_0001.svg)

**Parameters:**

|    |                      |
| -- | -------------------- |
| R1 | R1 (system MVA base) |
| X1 | X1 (system MVA base) |
| R2 | R2 (system MVA base) |
| X2 | X2 (system MVA base) |

---

<a id="ieeevc"></a>

## IEEEVC

*Source: [`Content/TransientModels_HTML/Voltage Compensator IEEEVC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator IEEEVC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Voltage Compensator IEEEVC 0001](images/Voltage_Compensator_IEEEVC_0001.svg)

**Parameters:**

|    |                       |
| -- | --------------------- |
| Rc | Rc (machine MVA base) |
| Xc | Xc (machine MVA base) |

---

<a id="remcmp"></a>

## REMCMP

*Source: [`Content/TransientModels_HTML/Voltage Compensator REMCMP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Voltage Compensator REMCMP.htm)*

**AutoCorrection Properties**

To be documented.

Model acts as a voltage compensation model. It allows you to specify a remote bus from which the voltage signal to the Exciter model will be obtained.

Model supported by PSSE
