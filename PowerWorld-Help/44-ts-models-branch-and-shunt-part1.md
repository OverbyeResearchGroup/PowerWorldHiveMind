---
title: "TS Models — Branches and Shunts (Part 1 of 2)"
part: "Transient Models"
chapter_file: "44-ts-models-branch-and-shunt-part1.md"
topics: 41
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Branches and Shunts (Part 1 of 2)

Branch, line shunt and switched shunt dynamic models.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (41)**

- [Branch](#branch)
- [All](#all)
- [DIFFRLYG](#diffrlyg)
- [DIFFRLYS](#diffrlys)
- [DIRECLEN](#direclen)
- [DISTR1](#distr1)
- [DISTRELAY](#distrelay)
- [DISTRELAYITR](#distrelayitr)
- [FACRI_SC](#facri-sc)
- [LOCTI](#locti)
- [LTC1](#ltc1)
- [OOSLEN](#ooslen)
- [OOSLNQ](#ooslnq)
- [OOSMHO](#oosmho)
- [RELODEN](#reloden)
- [RXR1](#rxr1)
- [SCGAP](#scgap)
- [SCMOV](#scmov)
- [SERIESCAPRELAY](#seriescaprelay)
- [SIMPLEOC1](#simpleoc1)
- [TIOCR1](#tiocr1)
- [TIOCRS](#tiocrs)
- [TIOCRSRF](#tiocrsrf)
- [TLIN1](#tlin1)
- [UF_AK](#uf-ak)
- [ZDCB](#zdcb)
- [ZLIN1](#zlin1)
- [ZPOTT](#zpott)
- [ZQLIN1](#zqlin1)
- [ZQLIN2](#zqlin2)
- [ZLINW](#zlinw)
- [Differential](#differential)
- [Impedance/Distance](#impedancedistance)
- [Over Current](#over-current)
- [Series Capacitor](#series-capacitor)
- [Transformer](#transformer)
- [Voltage/Frequency](#voltagefrequency)
- [TLIN1O](#tlin1o)
- [Line Shunt](#line-shunt)
- [MSLR1](#mslr1)
- [Switched Shunt](#switched-shunt)

---

<a id="branch"></a>

## Branch

*Source: [`Content/TransientModels_HTML/Branch.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/BranchFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="diffrlyg"></a>

## DIFFRLYG

*Source: [`Content/TransientModels_HTML/Branch Model DIFFRLYG.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model DIFFRLYG.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Model supported by PSLF

**Parameters:**

|           |                                                                            |
| --------- | -------------------------------------------------------------------------- |
| The Area  | Area to be monitored                                                       |
| The Zone  | Zone to be monitored                                                       |
| The Owner | Owner to be monitored                                                      |
| Monitor   | 0 = Alarm; 1 = Trip                                                        |
| kV1       | kV which the timings will be applied (for transformers high side)          |
| kV2       | If 0 then line else it is the low side of transformer                      |
| kV3       | Transformer (tertiary side), If not used = 0                               |
| Tcb       | Breaker Time in Cycles                                                     |
| TcC       | Communication time and relay time delay (and lockout relay time) in Cycles |

---

<a id="diffrlys"></a>

## DIFFRLYS

*Source: [`Content/TransientModels_HTML/Branch Model DIFFRLYS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model DIFFRLYS.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Model supported by PSLF

**Parameters:**

|                      |                                                                            |
| -------------------- | -------------------------------------------------------------------------- |
| Branch 1 to Branch 8 | The Branches to which the relay applies                                    |
| Monitor              | 0 = Alarm; 1 = Trip                                                        |
| Fb                   | First Bus                                                                  |
| Sb                   | Second Bus                                                                 |
| Ckt1                 | Circuid ID between Fb and Sb                                               |
| Ckt 2                | Circuid ID between Sb and Tb                                               |
| Ckt 3                | Circuid ID between Sb and TTb                                              |
| Tb                   | Third Bus (Far end of multi-segment line or three terminal line)           |
| TTb                  | Third Bus (Tertiary for XF or third bus of a three terminal line)          |
| Tcb                  | Breaker Time in Cycles                                                     |
| TcC                  | Communication time and relay time delay (and lockout relay time) in Cycles |

---

<a id="direclen"></a>

## DIRECLEN

*Source: [`Content/TransientModels_HTML/Branch Model DIRECLEN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model DIRECLEN.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays DIRECLEN 0001](images/Line_Relays_DIRECLEN_0001.svg)

**Parameters:**

|         |                                 |
| ------- | ------------------------------- |
| CharAng | Characteristic Angle in Degrees |

---

<a id="distr1"></a>

## DISTR1

*Source: [`Content/TransientModels_HTML/Line Relays DISTR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays DISTR1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays DISTR1 0001](images/Line_Relays_DISTR1_0001.svg)

![Line Relays DISTR1 0002](images/Line_Relays_DISTR1_0002.svg)

**Parameters:**

|                  |                                                                                           |
| ---------------- | ----------------------------------------------------------------------------------------- |
| RelaySlot        | Relay Slot \[1 or 2\]                                                                     |
| ImpedanceType    | Impedance Distance Type; 1 = mho distance; 2 = Impedance Distance; 3 = Reactance Distance |
| Monitor          | Monitor=0, and trip=1                                                                     |
| T1               | Zone 1 Operating Time in Cycles                                                           |
| Reach1           | Zone 1 reach in pu                                                                        |
| Ang1             | Zone 1 centerline angle in degrees                                                        |
| Center1          | Zone 1 center distance                                                                    |
| T2               | Zone 2 Operating Time in Cycles                                                           |
| Reach2           | Zone 2 reach in pu                                                                        |
| Ang2             | Zone 2 centerline angle in degrees                                                        |
| Center2          | Zone 2 center distance                                                                    |
| T3               | Zone 3 Operating Time in Cycles                                                           |
| Reach3           | Zone 3 reach in pu                                                                        |
| Ang3             | Zone 3 centerline angle in degrees                                                        |
| Center3          | Zone 3 center distance                                                                    |
| DirectAngle      | Angle of directional unit for impedance relay                                             |
| ThresholdCurrent | Threshold current, pu                                                                     |
| SelfTrip         | Self trip, cycles                                                                         |
| SelfReclose      | Self reclose, cycles                                                                      |
| TransferTrip     | Transfer trip, cycles                                                                     |
| TransferReclose  | Transfer reclose, cycles                                                                  |
| BlindType1       | First blinder type (+/-1 or +/-2)                                                         |
| BlindInt1        | First blinder intercept (pu)                                                              |
| BlindRot1        | First blinder rotation (degrees)                                                          |
| BlindType2       | Second blinder type (+/-1 or +/-2)                                                        |
| BlindInt2        | Second blinder intercept (pu)                                                             |
| BlindRot2        | Second blinder rotation (degrees)                                                         |

---

<a id="distrelay"></a>

## DISTRELAY

*Source: [`Content/TransientModels_HTML/Line Relays DISTRELAY.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays DISTRELAY.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|                  |                                                                                                                                                                                                                                                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Notrip           | 0 means to monitor and Trip; 1 means it will only monitor                                                                                                                                                                                                                         |
| Shape1           | Zone 1 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape2           | Zone 2 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape3           | Zone 3 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape4           | Zone 4 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| TransferType     | Transfer Trip Type; 0 means none; 1 Direct Underreaching Transfer Trip (DUTT); 2 Permissive Overreaching Transfer Trip (POTT); 3 Permissive Underreaching Transfer Trip (PUTT); 4 means Directional Comparison Blocking (DCB)                                                     |
| UseLoadEncroach  | Use Load Encroachment Model                                                                                                                                                                                                                                                       |
| NumDirect        | Number of Trips which are Direct. 0 is treated as 1, otherwise this is the number of trip branches which are considered a direct trip. Others are considered as transfer trip.                                                                                                    |
| RecloseWithFault | Reclose With Fault Not Cleared? 1 means a YES (Default), 0 means NO                                                                                                                                                                                                               |
| DirectTrip       | Direct trip, cycles                                                                                                                                                                                                                                                               |
| DirectReclose    | Direct reclose, cycles                                                                                                                                                                                                                                                            |
| TransferTrip     | Transfer trip, cycles                                                                                                                                                                                                                                                             |
| TransferReclose  | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| Angle1           | Zone 1 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt1              | Zone 1 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr1              | Zone 1 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng1     | Zone 1 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb1              | Zone 1 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T1               | Zone 1 Time, seconds                                                                                                                                                                                                                                                              |
| IThres1          | Zone 1 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle2           | Zone 2 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt2              | Zone 2 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr2              | Zone 2 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng2     | Zone 2 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb2              | Zone 2 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T2               | Zone 2 Time, seconds                                                                                                                                                                                                                                                              |
| IThres2          | Zone 2 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle3           | Zone 3 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt3              | Zone 3 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr3              | Zone 3 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng3     | Zone 3 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb3              | Zone 3 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T3               | Zone 3 Time, seconds                                                                                                                                                                                                                                                              |
| IThres3          | Zone 3 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle4           | Zone 4 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt4              | Zone 4 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr4              | Zone 4 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng4     | Zone 4 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb4              | Zone 4 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T4               | Zone 4 Time, seconds                                                                                                                                                                                                                                                              |
| IThres4          | Zone 4 IThres, Line Amps                                                                                                                                                                                                                                                          |
| BlindType0       | 1st Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt0        | 1st Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot0        | 1st Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType1       | 2nd Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt1        | 2nd Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot1        | 2nd Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType2       | 3rd Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt2        | 3rd Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot2        | 3rd Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType3       | 4th Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt3        | 4th Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot3        | 4th Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| FarRelayEnd      | Far Relay is at the Other End; 0 (Default) means it will look for the Far Relay Device to be at a different end from this device location end plus the Device id; 1 means it will look for Far Relay Device and only will look for the Device id (The device end will not matter) |

---

<a id="distrelayitr"></a>

## DISTRELAYITR

*Source: [`Content/TransientModels_HTML/Line Relays DISTRELAYITR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays DISTRELAYITR.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|                  |                                                                                                                                                                                                                                                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Notrip           | 0 means to monitor and Trip; 1 means it will only monitor                                                                                                                                                                                                                         |
| Shape1           | Zone 1 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape2           | Zone 2 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape3           | Zone 3 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| Shape4           | Zone 4 Shape; 0 means a circle, lens or tomato; 1 means a rectangle; 2 means reactance distance; 3 means impedance distance                                                                                                                                                       |
| TransferType     | Transfer Trip Type; 0 means none; 1 Direct Underreaching Transfer Trip (DUTT); 2 Permissive Overreaching Transfer Trip (POTT); 3 Permissive Underreaching Transfer Trip (PUTT); 4 means Directional Comparison Blocking (DCB)                                                     |
| UseLoadEncroach  | Use Load Encroachment Model                                                                                                                                                                                                                                                       |
| NumDirect        | Number of Trips which are Direct. 0 is treated as 1, otherwise this is the number of trip branches which are considered a direct trip. Others are considered as transfer trip.                                                                                                    |
| RecloseWithFault | Reclose With Fault Not Cleared? 1 means a YES (Default), 0 means NO                                                                                                                                                                                                               |
| ZoneDir1         | ZoneDir1; 0 means Forward; 1 means Reverse                                                                                                                                                                                                                                        |
| ZoneDir2         | ZoneDir2; 0 means Forward; 1 means Reverse                                                                                                                                                                                                                                        |
| ZoneDir3         | ZoneDir3; 0 means Forward; 1 means Reverse                                                                                                                                                                                                                                        |
| ZoneDir4         | ZoneDir4; 0 means Forward; 1 means Reverse                                                                                                                                                                                                                                        |
| Oper1            | Oper1; 0 means AND; 1 means OR; 2 means NOT; \< 0 means not used Zones Shape 2 and greater                                                                                                                                                                                        |
| Oper2            | Oper2; 0 means AND; 1 means OR; 2 means NOT; \< 0 means not used Zones Shape 3 and greater                                                                                                                                                                                        |
| Oper3            | Oper3; 0 means AND; 1 means OR; 2 means NOT; \< 0 means not used Zones Shape 4 and greater                                                                                                                                                                                        |
| DirectTrip       | Direct trip, cycles                                                                                                                                                                                                                                                               |
| DirectReclose    | Direct reclose, cycles                                                                                                                                                                                                                                                            |
| TransferTrip     | Transfer trip, cycles                                                                                                                                                                                                                                                             |
| TransferReclose1 | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| TransferReclose2 | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| TransferReclose3 | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| TransferReclose4 | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| TransferReclose5 | Transfer reclose, cycles                                                                                                                                                                                                                                                          |
| Angle1           | Zone 1 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt1              | Zone 1 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr1              | Zone 1 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng1     | Zone 1 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb1              | Zone 1 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T1               | Zone 1 Time, seconds                                                                                                                                                                                                                                                              |
| IThres1          | Zone 1 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle2           | Zone 2 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt2              | Zone 2 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr2              | Zone 2 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng2     | Zone 2 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb2              | Zone 2 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T2               | Zone 2 Time, seconds                                                                                                                                                                                                                                                              |
| IThres2          | Zone 2 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle3           | Zone 3 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt3              | Zone 3 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr3              | Zone 3 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng3     | Zone 3 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb3              | Zone 3 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T3               | Zone 3 Time, seconds                                                                                                                                                                                                                                                              |
| IThres3          | Zone 3 IThres, Line Amps                                                                                                                                                                                                                                                          |
| Angle4           | Zone 4 Angle, Degrees                                                                                                                                                                                                                                                             |
| Wt4              | Zone 4 Wt, Primary Ohms                                                                                                                                                                                                                                                           |
| Rr4              | Zone 4 Rr, Primary Ohms                                                                                                                                                                                                                                                           |
| InternalAng4     | Zone 4 InternalAng, Degrees                                                                                                                                                                                                                                                       |
| Rb4              | Zone 4 Rb, Primary Ohms                                                                                                                                                                                                                                                           |
| T4               | Zone 4 Time, seconds                                                                                                                                                                                                                                                              |
| IThres4          | Zone 4 IThres, Line Amps                                                                                                                                                                                                                                                          |
| BlindType0       | 1st Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt0        | 1st Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot0        | 1st Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType1       | 2nd Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt1        | 2nd Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot1        | 2nd Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType2       | 3rd Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt2        | 3rd Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot2        | 3rd Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| BlindType3       | 4th Blind type, 0, +1, -1, +2, or -2                                                                                                                                                                                                                                              |
| BlindInt3        | 4th Blind intercept, Primary Ohms                                                                                                                                                                                                                                                 |
| BlindRot3        | 4th Blind rotation, Degrees                                                                                                                                                                                                                                                       |
| FarRelayEnd      | Far Relay is at the Other End; 0 (Default) means it will look for the Far Relay Device to be at a different end from this device location end plus the Device id; 1 means it will look for Far Relay Device and only will look for the Device id (The device end will not matter) |

---

<a id="facri-sc"></a>

## FACRI_SC

*Source: [`Content/TransientModels_HTML/Line Relays FACRI_SC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays FACRI_SC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagram

**Parameters:**

|                |                                       |
| -------------- | ------------------------------------- |
| Monitored Bus  | Bus at which the voltage is monitored |
| volt\_high     | High cut-in voltage (pu)              |
| volt\_low      | Low cut-in voltage (pu)               |
| td\_high       | High cut-in time delay (sec)          |
| td\_low        | Low cut-in time delay (sec)           |
| Extra Object 1 | Line 1                                |
| Extra Object 2 | Line 2                                |
| Extra Object 3 | Line 3                                |
| Extra Object 4 | Line 4                                |
| Extra Object 5 | Line 5                                |
| Extra Object 6 | Line 6                                |
| Extra Object 7 | Line 7                                |
| Extra Object 8 | Interface 1                           |

**The following pseudo code describes how the inputs are used to determine series capacitor switching:**

SeriesCap = Series capacitor to which this model is assigned

LineSectionsAreOpen = Any line section open for Extra Object 1 to 7

CapBlocked = ((Interface1 MW Flow \< -50) OR (Interface1 MW Flow \> 0)) AND LineSectionsAreOpen

If ((not CapBlocked) and (SeriesCap.Status = Bypassed)) AND ((Monitored Bus Voltage \< volt\_low for td\_low) OR (Monitored Bus Voltage \< volt\_high for td\_high))

Then Begin

SeriesCap.Status = Not Bypassed

End

---

<a id="locti"></a>

## LOCTI

*Source: [`Content/TransientModels_HTML/Line Relays LOCTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays LOCTI.htm)*

**AutoCorrection Properties**

To be documented.

Treatment of Model in Power Flow Contingency Analysis

When a transient stability model is used in the power flow contingency analysis using the [special option for the power flow contingency solution](22-contingency-analysis-options.md#transient-models), then the model determines how to report violation for the Monitor Only option as well as specifying a TimeDelay and Trip/Act action. The following table describes this and uses the following text conventions.

  - **Green**text are parameters of a stability model.
  - **Blue** text are a parameter of the contingency options.
  - Other **bold** text are “local variables” used in this description.

|                                |                                                                                                                                      |                                                                                                                                                                                                                                                                             |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Model Evaluation               | Description                                                                                                                          | Specific Implementation for this model                                                                                                                                                                                                                                      |
| **Monitor Only**               | Determine a Boolean result to indicate whether the stability model is “violated” and ready to do something?                          | Evaluates whether “Present Current on Branch \>**ThresholdCurrent**”.                                                                                                                                                                                                       |
| TimeDelay used in **Trip/Act** | Time in seconds that the model needs to remain “violated” before it will actually apply an action when the Trip/Act option is chosen | TimeDelay is calculated by taking the Present Current on Branch and run this through the **Lookup Table** specified in the dynamic model parameters along with the Time Dial Multiplier. Essentially we use a time assuming that the current remains at this level forever. |
| **Trip/Act** Action            | If violated for the particular time, then this procedure must be written to actually implement the action.                           | Model will open appropriate branches as would be done in transient stability                                                                                                                                                                                                |

Model Equations and/or Block Diagrams

![Line Relays LOCTI 0001](images/Line_Relays_LOCTI_0001.svg)

**Parameters:**

|                  |                                                                                                                                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monitor          | Monitor=0, and trip=1                                                                                                                                                                                                                          |
| ThresholdCurrent | Threshold current, pu                                                                                                                                                                                                                          |
| Tdm              | Time Dial Multiplier. All times specified will be treated as this multiple larger                                                                                                                                                              |
| BreakerTime      | Circuit Breaker Time in Seconds                                                                                                                                                                                                                |
| M1               | Multiple Current Threshold for Pickup Point 1                                                                                                                                                                                                  |
| Tm1              | Time to Close in Seconds for Pickup Point 1                                                                                                                                                                                                    |
| M2               | Multiple Current Threshold for Pickup Point 2                                                                                                                                                                                                  |
| Tm2              | Time to Close in Seconds for Pickup Point 2                                                                                                                                                                                                    |
| M3               | Multiple Current Threshold for Pickup Point 3                                                                                                                                                                                                  |
| Tm3              | Time to Close in Seconds for Pickup Point 3                                                                                                                                                                                                    |
| M4               | Multiple Current Threshold for Pickup Point 4                                                                                                                                                                                                  |
| Tm4              | Time to Close in Seconds for Pickup Point 4                                                                                                                                                                                                    |
| M5               | Multiple Current Threshold for Pickup Point 5                                                                                                                                                                                                  |
| Tm5              | Time to Close in Seconds for Pickup Point 5                                                                                                                                                                                                    |
| ResetTime        | Zero Current Reset time in seconds. Let M = (I/Ithres). Then Time To Reset = Tdm\*{ResetTime/(1-M^2)}                                                                                                                                          |
| t3trip           | 0 means trip monitor winding; 1 means trip whole 3 winding Xfmr                                                                                                                                                                                |
| direct           | 0 means no directional element; 1 means directional element AND Direction will be based upon current leaving the FROM end of the branch; 2 means directional element AND Direction will be based upon current leaving the TO end of the branch |

---

<a id="ltc1"></a>

## LTC1

*Source: [`Content/TransientModels_HTML/Tap Control LTC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Tap Control LTC1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

\-The transformer must exist as a load tap changer in the case.

\-The transformer will regulate voltage at a regulated bus.

\-If the regulated voltage is out of its range for more than Tdelay seconds, a tap motion is started. The tap will take Tmotion seconds to move to the next position.

\-The transformer tap value is obtained from the initial power flow and it is not changed by LTC1

**Parameters:**

|         |                                                                              |
| ------- | ---------------------------------------------------------------------------- |
| Tdelay  | Time in seconds to start tapping                                             |
| Tmotion | Time in seconds for each tap move; only one tap change per time step allowed |
| Noprint | Set to 1 to surpress logging of tap changes                                  |

---

<a id="ooslen"></a>

## OOSLEN

*Source: [`Content/TransientModels_HTML/Line Relays OOSLEN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays OOSLEN.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays OOSLEN 0001](images/Line_Relays_OOSLEN_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                   |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                      |
| Type   | Type: 0 = minimum time between zones, outward travel; 1 = minimum time between zones, inward travel; 10 = minimum time within each zone, outward travel; 11 = minimum time within each zone, inward travel                        |
| Tcb    | Breaker Operating Time (in Seconds)                                                                                                                                                                                               |
| Ang1   | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                            |
| Rf1    | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                         |
| Rr1    | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt1    | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| T1     | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                      |
| Ang2   | Angle (in degrees) of Impedance Zone 2                                                                                                                                                                                            |
| Rf2    | Forward Reach Impedance (in per unit) of Impedance Zone 2                                                                                                                                                                         |
| Rr2    | Reverse Reach Impedance (in per unit) of Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2    | Total Width (in per unit) of Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| T2     | Pickup Time (in Seconds) of Impedance Zone 2                                                                                                                                                                                      |
| Ang3   | Angle (in degrees) of Impedance Zone 3                                                                                                                                                                                            |
| Rf3    | Forward Reach Impedance (in per unit) of Impedance Zone 3                                                                                                                                                                         |
| Rr3    | Reverse Reach Impedance (in per unit) of Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3    | Total Width (in per unit) of Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| T3     | Pickup Time (in Seconds) of Impedance Zone 3                                                                                                                                                                                      |

---

<a id="ooslnq"></a>

## OOSLNQ

*Source: [`Content/TransientModels_HTML/Line Relays OOSLNQ.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays OOSLNQ.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams 

![Line Relays OOSLNQ 0001](images/Line_Relays_OOSLNQ_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                   |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                      |
| Type   | Type: 0 = minimum time between zones, outward travel; 1 = minimum time between zones, inward travel; 10 = minimum time within each zone, outward travel; 11 = minimum time within each zone, inward travel                        |
| Shape1 | Shape of Impedance Zone 1. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape2 | Shape of Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape3 | Shape of Impedance Zone 3. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Tcb    | Breaker Operating Time (in Seconds)                                                                                                                                                                                               |
| Ang1   | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                            |
| Rf1    | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                         |
| Rr1    | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt1    | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr1    | Right Width (in per unit) of Impedance Zone 1. (Only used for rectangular shape)                                                                                                                                                  |
| T1     | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                      |
| Ang2   | Angle (in degrees) of Impedance Zone 2                                                                                                                                                                                            |
| Rf2    | Forward Reach Impedance (in per unit) of Impedance Zone 2                                                                                                                                                                         |
| Rr2    | Reverse Reach Impedance (in per unit) of Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2    | Total Width (in per unit) of Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2    | Right Width (in per unit) of Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2     | Pickup Time (in Seconds) of Impedance Zone 2                                                                                                                                                                                      |
| Ang3   | Angle (in degrees) of Impedance Zone 3                                                                                                                                                                                            |
| Rf3    | Forward Reach Impedance (in per unit) of Impedance Zone 3                                                                                                                                                                         |
| Rr3    | Reverse Reach Impedance (in per unit) of Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3    | Total Width (in per unit) of Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr3    | Right Width (in per unit) of Impedance Zone 3. (Only used for rectangular shape)                                                                                                                                                  |
| T3     | Pickup Time (in Seconds) of Impedance Zone 3                                                                                                                                                                                      |

---

<a id="oosmho"></a>

## OOSMHO

*Source: [`Content/TransientModels_HTML/Branch Model OOSMHO.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model OOSMHO.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays OOSMHO 0001](images/Line_Relays_OOSMHO_0001.svg)

**Parameters:**

|           |                                                                                               |
| --------- | --------------------------------------------------------------------------------------------- |
| NoTrip    | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.  |
| Ang       | Angle (in degrees)                                                                            |
| Rf        | Forward Reach Impedance (in per unit)                                                         |
| Rr        | Reverse Reach Impedance (in per unit). (Note: For backward reach, specify a POSITIVE number.) |
| BlindInt1 | 1st Blinder intercept, p.u. R                                                                 |
| BlindRot1 | 1st Blinder rotation, Degrees                                                                 |
| BlindInt2 | 2nd Blinder intercept, p.u. R                                                                 |
| BlindRot2 | 2nd Blinder rotation, Degrees                                                                 |
| T         | Pickup Time (in Seconds)                                                                      |
| Tcb       | Breaker Operating Time (in Seconds)                                                           |

---

<a id="reloden"></a>

## RELODEN

*Source: [`Content/TransientModels_HTML/Branch Model RELODEN.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model RELODEN.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays RELODEN 0001](images/Line_Relays_RELODEN_0001.svg)

**Parameters:**

|      |                                                                                                                    |
| ---- | ------------------------------------------------------------------------------------------------------------------ |
| func | 0 Do not use, 1 use with distance relay only, 2 use with overcurrent relay only, 3 use with all relays on the line |
| Rf   | Forward Impedance in Primary Ohms                                                                                  |
| Rr   | Reverse Impedance in Primary Ohms                                                                                  |
| PLAF | Positive Forward Angle in Degrees                                                                                  |
| NLAF | Negative Forward Angle in Degrees                                                                                  |
| PLAR | Positive Reverse Angle in Degrees                                                                                  |
| NLAR | Negative Reverse Angle in Degrees                                                                                  |

---

<a id="rxr1"></a>

## RXR1

*Source: [`Content/TransientModels_HTML/Branch Model RXR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model RXR1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="scgap"></a>

## SCGAP

*Source: [`Content/TransientModels_HTML/Line Relays SCGAP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays SCGAP.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Model supported by PSLF

**Parameters:**

|        |                                                          |
| ------ | -------------------------------------------------------- |
| Iflash | Gap firing angle, p.u.                                   |
| Ireins | Reinsertion current, p.u.                                |
| Rdelay | Reinsertion delay, sec.                                  |
| Nshots | Number of reinsertion attempts                           |
| Trmax  | Time after which reinsertion will not be attempted, sec. |

---

<a id="scmov"></a>

## SCMOV

*Source: [`Content/TransientModels_HTML/Line Relays SCMOV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays SCMOV.htm)*

This represents a model of the over-current and over-voltage protection for a series capacitor which uses a Metal Oxide Varistor (MOV) and bypass switch. The model is based on the following paper from 1987.

D. L. Goldsworthy, “A linearized model for MOV-protected series capacitors”, IEEE Transactions on Power Systems, Vol. PWRS-2, No. 4, November 1987

See the Goldsworthy paper for a detailed explanation of this technology. Below is a description of how the model impacts the software simulation.

The Input Parameters for SCMOV are as follows:

<table>
<tbody>
<tr class="odd">
<td><p>Icrated</p></td>
<td><p>Capacitor Rated current in Amps</p></td>
</tr>
<tr class="even">
<td><p>Icappro</p></td>
<td><p>Capacitor protective level current, pu on Icrated base</p></td>
</tr>
<tr class="odd">
<td><p>Ithresh</p></td>
<td><p>Threshold value for MOV activation.<br />
Any value smaller than 0.94879 will be ignored and treated as equal to 0.94879.</p></td>
</tr>
<tr class="even">
<td><p>Daccel</p></td>
<td><p>Parameter not used by PowerWorld Simulator</p></td>
</tr>
<tr class="odd">
<td><p>Enerlim</p></td>
<td><p>MOV energy limit in Mjoules</p></td>
</tr>
<tr class="even">
<td><p>Enerdly</p></td>
<td><p>Bypass delay associated with Enerlim in seconds</p></td>
</tr>
<tr class="odd">
<td><p>Imovlim</p></td>
<td><p>MOV current limit in pu of Icrated</p></td>
</tr>
<tr class="even">
<td><p>Imovdly</p></td>
<td><p>Bypass delay associated with Imovlim in seconds</p></td>
</tr>
<tr class="odd">
<td><p>Icaplim</p></td>
<td><p>Capacitor current limit in pu of Icrated</p></td>
</tr>
<tr class="even">
<td><p>Icapdly</p></td>
<td><p>Bypass delay associated with Icaplim in seconds</p></td>
</tr>
<tr class="odd">
<td><p>Operdly</p></td>
<td><p>Parameter is not used by PowerWorld Simulator</p></td>
</tr>
<tr class="even">
<td><p>Iinsert</p></td>
<td><p>Insertion current in pu of Icrated</p></td>
</tr>
<tr class="odd">
<td><p>Tinsert</p></td>
<td><p>Insertion time in seconds</p></td>
</tr>
<tr class="even">
<td><p>ImovTup</p></td>
<td><p>Pickup time for the Imovlim in seconds</p></td>
</tr>
<tr class="odd">
<td><p>IcapTup</p></td>
<td><p>Pickup time for the Icaplim in seconds</p></td>
</tr>
</tbody>
</table>

Other Output values for SCMOV are as follows

<table>
<tbody>
<tr class="odd">
<td><p>Mode</p></td>
<td><p>Mode of operation</p>
<p>0 = NORMAL (model impedance as Rcap + jXcap)</p>
<p>1 = CAP+MOV (model impedance as Rpc + jXpc calculated as described below)</p>
<p>2 = BYPASS (model impedance as 0.0000001 + j0.00001</p></td>
</tr>
<tr class="even">
<td><p>ItotAmp</p></td>
<td><p>Total current magnitude seen by the network solution in Amps</p></td>
</tr>
<tr class="odd">
<td><p>IcapAmp</p></td>
<td><p>Current magnitude across the capacitor in Amps</p></td>
</tr>
<tr class="even">
<td><p>ImovAmp</p></td>
<td><p>Current magnitude across the MOV in Amps</p></td>
</tr>
<tr class="odd">
<td><p>EnergyMOV</p></td>
<td><p>Accumulated energy absorbed by the MOV in MegaJoules</p></td>
</tr>
<tr class="even">
<td><p>Itotpu</p></td>
<td><p>Total current magnitude seen by the network solution in per unit on the system base</p></td>
</tr>
<tr class="odd">
<td><p>Icappu</p></td>
<td><p>Current magnitude across the capacitor in per unit on the system base</p></td>
</tr>
<tr class="even">
<td><p>Imovpu</p></td>
<td><p>Current magnitude across the MOV in per unit on the system base</p></td>
</tr>
<tr class="odd">
<td><p>Rused</p></td>
<td><p>Rpu (on system base) used in the network algebraic solution<br />
(varies depending on the mode)</p></td>
</tr>
<tr class="even">
<td><p>Xused</p></td>
<td><p>Xpu (on system base) used in the network algebraic solution<br />
(varies depending on the mode)</p></td>
</tr>
</tbody>
</table>

SCMOV Three Modes of Operation

The complex currents used when modeling this device are shown in the figure below.

The model operates in three different modes with the treatment in the algebraic network boundary equation solution as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Mode</p></td>
<td><p>Treatment in Algebraic Network Boundary Equations</p></td>
<td><p>Currents Reported for Output</p></td>
</tr>
<tr class="even">
<td><p>NORMAL</p>
<p>Mode=0</p></td>
<td><p>The original Rpu and Xpu of the series capacitor is used to model the device in the algebraic network boundary equations.</p>
<p>Note: during a algebraic network boundary equation solution, the device will instantaneously change to Mode 1 (CAP+MOV) if the current threshold Ithresh is exceed as described in the transitions below. This special transition during the algebraic solution is needed to prevent very large current spikes that occur at fault inception on or near the terminals of these series capacitors.</p></td>
<td><p>Itot = magnitude of current through branch</p>
<p> </p>
<p>Icap = Itot</p>
<p> </p>
<p>Imov = 0.0</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>CAP+MOV</p>
<p>Mode=1</p></td>
<td><p>An Rpc + jXpc is calculated as described in the image below based on function of the current Ipux described in the Goldsworthy reference paper.</p>
<p>While operating in this mode the energy absorbed by the MOV is calculated by determining the resistance of the equivalent impedance Rpc+jXpc and the branch impedance Rcap+jXcap. This requires solving the following equation for Rmov.</p>
<p>(Rmov+jXmov) = 1 / ( 1/(Rpc+jXpc) - 1/(Rcap + jXcap) )</p>
<p>The power absorbed over a time step as resistive loss is calculated as follows</p>
<p>MegaWattMOV = (Rmov*Imovpu*Imovpu)*SystemMVABase</p>
<p>Integration is approximated by multiplying the TimeStep length in seconds by MegaWattMOV and keeping the accumulated sum as the value EnergyMOV (with units of MegaJoules). Also note that the accumulated EnergyMOV is not reset during the simulation even when transferring out of this mode.</p>
<p>Also note that the Goldsworthy paper suggested using the following equation for the power loss which gives the same answer when Rcap = 0.</p>
<p>MegaWattMOV = (Rpc*Itotpu*Itotpu)*SystemMVABase</p></td>
<td><p>Itot = magnitude of current through branch</p>
<p> </p>
<p>Icap = current calculated from terminal voltage and original Rcap and Xcap</p>
<p> </p>
<p>Imov = magnitude of the <em>complex</em> current calculation (Itot - Icap)</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p>BYPASS</p>
<p>Mode=2</p></td>
<td><p>When operating in Mode 2 (BYPASS) the minimum internal impedance is used of R + jX = 0.0000001 + j0.00001</p></td>
<td><p>Itot = magnitude of current through branch</p>
<p>Icap = 0</p>
<p>Imov = 0</p></td>
</tr>
</tbody>
</table>

![Line Relays SCMOV Currents](images/Line_Relays_SCMOV_Currents.png)

![Line Relays SCMOV Multipliers](images/Line_Relays_SCMOV_Multipliers.png)

Mode Transitions

Transitions between the 3 operating modes can occur as follows with 4 possible transitions as depicted in the next image. The conditions under which these mode transitions occurs are described in the following table.

![Line Relays SCMOV Transitions](images/Line_Relays_SCMOV_Transitions.png)

<table>
<tbody>
<tr class="odd">
<td><p>From Mode</p></td>
<td><p>Transition to Mode</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>NORMAL</p>
<p>Mode=0</p></td>
<td><p>CAP+MOV</p>
<p>Mode=1</p></td>
<td><p>When in Mode 0 (NORMLA), at the end of each time step of the simulation if the following condition is met then the device will switch to Mode 1 (CAP+MOV)</p>
<p>Ipux &gt; Ithresh , where Ipux = ItotAmp/(Icappro*Icrated) .</p>
<p>Note that the current base for getting Ipux in per unit is different than the per unit for comparisons to Icaplim and Imovlim described later because the multiplier Icappro is used with Ipux.</p>
<p>During an algebraic network boundary equation solution, the device will instantaneously switch to Mode 1 (CAP+MOV) if the current threshold Ithresh is exceed as described in Mode 1 description. If this occurs the mode is switched and the algebraic solution is immediately redone.</p></td>
</tr>
<tr class="odd">
<td><p>NORMAL</p>
<p>Mode=0</p></td>
<td><p>BYPASS</p>
<p>Mode=2</p></td>
<td><p>This direct transition will not happen</p></td>
</tr>
<tr class="even">
<td><p>CAP+MOV</p>
<p>Mode=1</p></td>
<td><p>NORMAL</p>
<p>Mode=0</p></td>
<td><p>When in Mode 1 (CAP+MOV), at the end of each time step, if Ipux &lt;= Ithreshthen the device transitions to Mode 0 (NORMAL) for the next time step.</p></td>
</tr>
<tr class="odd">
<td><p>CAP+MOV</p>
<p>Mode=1</p></td>
<td><p>BYPASS</p>
<p>Mode=2</p></td>
<td><p>When in Mode 1 (CAP+MOV), at the end of each time step, three different checks are done to determine if a transition to Mode 2 (BYPASS) is made.</p>
<ol>
<li><p>Enerlim If the accumulated energy absorbed by the MOV stored in EnergyMOV exceeds the MOV energy limit Enerlim for more than Enerdly seconds, then the device will bypass. If Enerlim = 0 this bypassing option is ignored.</p></li>
<li><p>Imovlim: If the current passing through the MOV exceeds Imovlimfor ImovTupseconds, the capacitor and MOV are bypassed after a delay of Imovdly seconds (even if the MOV current falls below the Imovlim during this delay time). If Imovlim = 0 this bypassing option is ignored. Imovlim is in per unit on Icrated base so proper conversions are required when comparing with it.</p></li>
<li><p>Icaplim: If the current passing through the capacitor exceeds Icaplimfor IcapTupseconds, the capacitor and MOV are bypassed after a delay of Icapdly seconds (even if the capacitor current falls below the Icaplim during this delay time). If Icaplim = 0 this bypassing option is ignored. Icaplim is in per unit on Icrated base so proper conversions are required when comparing with it.</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>BYPASS</p>
<p>Mode=2</p></td>
<td><p>NORMAL</p>
<p>Mode=0</p></td>
<td><p>When in Mode 2 (BYPASS), the model allows for reinsertion of the device if the bypass decision was made due to the Imovlim or the Icaplim. Reinsertion will occur if all other bypass conditions are not met and the current is below the Iinsert for Tinsert seconds.</p>
<p>When this transition occurs the Enerdly timer for Enerlim is reset and will start counting again If the device was set to BYPASS due to the EnerLim, then the device will not reinsert the capacitor and MOV. One exception to this is if another stability model or a user event has intentionally removed the Bypass, then this transition will reset the EnergyMOV = 0 and reset the Enerdly timer.</p></td>
</tr>
<tr class="odd">
<td><p>BYPASS</p>
<p>Mode=2</p></td>
<td><p>CAP+MOV</p>
<p>Mode=1</p></td>
<td><p>This direct transition will not happen</p></td>
</tr>
</tbody>
</table>

Pseudo-Code forVariables maintained across time steps

> 
> 
>     Branch Bypass status is something independent of the SCMOV model
>     MOVIsConducting : boolean
>     EnergyMOV : float
>     Itotpu    : float
>     Imovpu    : float
>     Icappu    : float
>     CACHE_BypassSentICAP   : boolean
>     CACHE_BypassSentIMOV   : boolean
>     CACHE_BypassSentEnergy : boolean
>     TimeOfAboveEnerLim     : float
>     TimeOfAboveEnerLimSet  : boolean
>     TimeOfBelowIinsert     : float
>     TimeOfBelowIinsertSet  : boolean
>     TimeOfAboveImovLim     : float
>     TimeOfAboveImovLimSet  : boolean
>     TimeOfAboveIcapLim     : float
>     TimeOfAboveIcapLimSet  : boolean

Pseudo-Code for Model Initialization

> 
> 
>     MOVIsConducting = False
>     EnergyMOV = 0
>     Itotpu = calculate current from terminal voltage using Rcap and Xcap value
>     Icappu = Itotpu
>     Imovpu = 0
>     CACHE_BypassSentICAP   = false
>     CACHE_BypassSentIMOV   = false
>     CACHE_BypassSentEnergy = Branch initially bypassed // treat an initial bypass as permanent
>     TimeOfAboveEnerLim     = 0
>     TimeOfAboveEnerLimSet  = false
>     TimeOfBelowIinsert     = 0
>     TimeOfBelowIinsertSet  = false
>     TimeOfAboveImovLim     = 0
>     TimeOfAboveImovLimSet  = false
>     TimeOfAboveIcapLim     = 0
>     TimeOfAboveIcapLimSet  = false

Pseudo-Code for function to Recalculate Rpc, Xpc, and Rmov based on a new value of Itotpu

> 
> 
>     procedure RecalculateRpcAndXpc(Itotpu) // recalculate Rpc, Xpc, and Rmov using Multiplier functions based on present total current
>       Ipux = Itotpu*Ibase/Icrated/Icappro
>       If     Ipux < 0.94879 then Ipux = 0.94879   // don't let MultiplierR become negative
>       ElseIf Ipux > 17.5684 then Ipux = 17.5684   // don't let MultiplierX become negative
>       EndIf
>       MultR = 0.0745 + 0.49*exp(-0.243*Ipux) - 35.0*exp(-5.0*Ipux) - 0.60*exp(-1.40*Ipux)
>       MultX = 0.1010 - 0.005749*Ipux + 2.088*exp(-0.8566*Ipux)
>       if MultR < 0 then MultR = 0 // shouldn't happen but just make sure
>       if MultX < 0 then MultX = 0 // shouldn't happen but just make sure
>       Rpc = -MultR*Xcap // Xcap = original X
>       Xpc = +MultX*Xcap
>     
>       Gpc =  Rpc/(sqr(Rpc) + sqr(Xpc))
>       Bpc = -Xpc/(sqr(Rpc) + sqr(Xpc))
>       Gcap =  Rcap/(sqr(Rcap) + sqr(Xcap))
>       Bcap = -Xcap/(sqr(Rcap) + sqr(Xcap))
>       Gmov = Gpc – Gcap
>       Bmov = Bpc – Bcap; 
>       Rmov = Gmov/(sqr(Gmov) + sqr(Bmov))

Pseudo-Code for Mode Transitions run at the end of each time-step

> 
> 
> ``` 
>   If (Branch Is Bypass) Then // This is Mode 2
>     Itotpu = calculate currents from terminal voltage small impedance used for bypass
>     Imovpu = 0
>     Icappu = 0
>     CACHE_BypassSentICAP = false
>     CACHE_BypassSentIMOV = false
>     If (not CACHE_BypassSentEnergy ) Then // only allow reinsert if not bypass caused by EnergyLim      
>       if (Itotpu*CACHE_IBase/Icrated <= Iinsert)
>          and ( (Imovpu*IBase/Icrated <= Imovlim) or (Imovlim = 0) ) // make sure other bypass conditions are not met
>          and ( (Icappu*IBase/Icrated <= Icaplim) or (Icaplim = 0) ) // make sure other bypass conditions are not met
>       then 
>         if not TimeOfBelowIinsertSet then begin
>           TimeOfBelowIinsert = PresentTime
>           TimeOfBelowIinsertSet = true
>         EndIf
>         if (PresentTime - TimeOfBelowIinsert >= Tinsert) then begin
>           Write Message indicating a transition from BYPASS to NORMAL has been scheduled immediately
>           Schedule an event to remove the BYPASS on the next timestep (this event will transition us to Mode 0)
>           MOVIsConducting = False  
>           TimeOfAboveEnerLimSet = False // reset EnerLim timer
>         EndIf
>       Else 
>         TimeOfBelowIinsertSet = false // reset Insert timer
>       EndIf
>     EndIf
>   Else 
>     // The SCMOV model itself will never reinsert after it causes a bypass due to the EnergyMOV > Enerlim.
>     // We know that EnergyMOV > Enerlim has happened because CACHE_BypassSentEnergy = TRUE, so the only  
>     // way we get here is if another stability model or a user event has intentionally removed the Bypass.  
>     // In that situation we assume the EnergyMOV has dissipated and reset the EnergyMOV and Enerdly timer
>     If CACHE_BypassSentEnergy then 
>       Write message indicating that we are reseting the EnergyMOV and its timer 
>       CACHE_BypassSentEnergy = FALSE  // reset to allow EnergyMOV to cause it to bypass again
>       EnergyMOV = 0                   // clear energy to make 0.0 again
>       TimeOfAboveEnerLimSet = False   // reset EnerDly timer
>     EndIf
> 
>     // Calculate the Currents
>     ICapComplex = calculate currents from terminal voltage using original R and X value (per unit system base)
>     If MOVIsConducting Then
>       ItotComplex = calculate current from terminal voltage and Rpc and Xpc (per unit system base)
>       ImovComplex = Complex Difference of (ItotComplex - IcapComplex)
>       Itotpu = ItotComplex.Magnitude
>       Icappu = IcapComplex.Magnitude 
>       Imovpu = ImovComplex.Magnitude
>       if TimeStep > 0 then EnergyMOV = EnergyMOV + TimeStep*sqr(Imovpu)*Rmov*SystemMVABase 
>     Else 
>       Itotpu = ICapComplex.Magnitude
>       Icappu = Itotpu
>       Imovpu = 0
>     EndIf
> 
>     // Check the various conditions that will Bypass the device
>     If (not CACHE_BypassSentEnergy) AND (Enerlim > 0) AND (EnergyMOV > fEnerlim) Then
>       If not TimeOfAboveEnerLimSet Then
>         TimeOfAboveEnerLim = PresentTime
>         TimeOfAboveEnerLimSet = true
>         If Enerdly > 0 Then Write out a messsage indicating that the Enerdlg timer has started
>       EndIf
>       If (PresentTime - TimeOfAboveEnerLim >= Enerdly) Then
>         CACHE_BypassSentEnergy = true
>         TimeOfAboveEnerLimSet = False 
>         Schedule an event to apply a BYPASS on the next Time Step (this event will transition us to Mode 2)
>       EndIf
>     EndIf
> 
>     If (ImovLim <= 0) OR (Imovpu*IBase/Icrated >= Imovlim) Then
>       If TimeOfAboveImovLimSet then 
>         Write out a messsage indicating that the ImovTup timer has stopped
>         TimeOfAboveImovLimSet = False
>       EndIf 
>     ElseIf (not CACHE_BypassSentIMOV) Then
>       If not TimeOfAboveImovLimSet Then
>         TimeOfAboveImovLim = PresentTime
>         TimeOfAboveImovLimSet = true
>         If ImovTup > 0 Then Write out a messsage indicating that the ImovTup timer has started
>       EndIf
>       If (PresentTime - TimeOfAboveImovLim >= ImovTup) Then 
>         CACHE_BypassSentIMOV = true
>         TimeOfAboveImovLimSet = False
>         Write message indicating a transition from CAP_MOV to BYPASS has been scheduled to occur in Imovdly 
>         Schedule an event to apply a BYPASS in Imovdly seconds (this event will transition us to Mode 2)
>       EndIf
>     EndIf
> 
>     If (IcapLim <= 0) OR (Icappu*IBase/Icrated >= Icaplim) Then
>       If TimeOfAboveIcapLimSet then 
>         Write out a messsage indicating that the IcapTup timer has stopped
>         TimeOfAboveIcapLimSet = False
>       EndIf 
>     ElseIf (not CACHE_BypassSentICAP) Then
>       If not TimeOfAboveIcapLimSet Then
>         TimeOfAboveIcapLim = PresentTime
>         TimeOfAboveIcapLimSet = true
>         If IcapTup > 0 Then Write out a messsage indicating that the IcapTup timer has started
>       EndIf
>       If (PresentTime - TimeOfAboveIcapLim >=; IcapTup) Then 
>         CACHE_BypassSentICAP = true
>         TimeOfAboveIcapLimSet = False
>         Write message indicating a transition from CAP_MOV to BYPASS has been scheduled to occur in Icapdly 
>         Schedule an event to apply a BYPASS in Icapdly seconds (this event will transition us to Mode 2)
>       EndIf
>     EndIf               
>  
>     // Manage the Mode transitions between Mode 0 and 1
>     If MOVIsConducting Then
>       if (Itotpu*CACHE_IBase/Icrated/Icappro <= Ithresh) Then 
>         MOVIsConducting = False
>         Write message indicating a transition from CAP+MOV to NORMAL 
>       Else          
>         RecalculateRpcAndXpc(Itotpu) // recalculate Rpc and Xpc (see other procedure above)
>       EndIf
>     Else 
>       If (Itotpu*IBase/Icrated/Icappro >   fIthresh) Then 
>         MOVIsConducting = True // transition to MOV mode
>         RecalculateRpcAndXpc(Itotpu) // recalculate Rpc and Xpc (see other procedure above)
>         Write message that we have transitioned from NORMAL to CAP+MOV Mode
>       EndIf
>     EndIf
>   EndIf
> ```

---

<a id="seriescaprelay"></a>

## SERIESCAPRELAY

*Source: [`Content/TransientModels_HTML/Line Relays SERIESCAPRELAY.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays SERIESCAPRELAY.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Model supported by PowerWorld

**Parameters:**

|         |                                                                     |
| ------- | ------------------------------------------------------------------- |
| Tfilter | Voltage filter time constant in sec.                                |
| tbOn    | Switching time On in sec.                                           |
| tbOff   | Switching time Off in sec.                                          |
| V1On    | First voltage threshold for switching series capacitor ON in p.u.   |
| t1On    | First time delay for switching series capacitor ON in sec.          |
| V2On    | Second voltage threshold for switching series capacitor ON in p.u.  |
| t2On    | Second time delay for switching series capacitor ON in sec.         |
| V1Off   | First voltage threshold for switching series capacitor OFF in p.u.  |
| t1Off   | First time delay for switching series capacitor OFF in sec.         |
| V2Off   | Second voltage threshold for switching series capacitor OFF in p.u. |
| t2Off   | Second time delay for switching series capacitor OFF in sec.        |

---

<a id="simpleoc1"></a>

## SIMPLEOC1

*Source: [`Content/TransientModels_HTML/Branch Model SIMPLEOC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model SIMPLEOC1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

Is the same as the [TIOCRS](#tiocrs) with the IEEE C37.112-1996 standard used for the relay modeling.

**Parameters:**

|               |                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------- |
| ThresholdMult | Multiplier on limit to determine threshold current; set to 1 for threshold to match limit                         |
| Tdm           | Time Dial Multiplier                                                                                              |
| Treset        | Time to reset if the current is zero, in seconds                                                                  |
| P             | Curve Exponent Parameter. See more information with paramters A, B                                                |
| A             | Curve Coefficient A. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)} |
| B             | Curve Coefficient B. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)} |

---

<a id="tiocr1"></a>

## TIOCR1

*Source: [`Content/TransientModels_HTML/Line Relays TIOCR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays TIOCR1.htm)*

**AutoCorrection Properties**

To be documented.

Treatment of Model in Power Flow Contingency Analysis

When a transient stability model is used in the power flow contingency analysis using the [special option for the power flow contingency solution](22-contingency-analysis-options.md#transient-models), then the model determines how to report violation for the Monitor Only option as well as specifying a TimeDelay and Trip/Act action. The following table describes this and uses the following text conventions.

  - **Green**ext are parameters of a stability model.
  - **Blue** text are a parameter of the contingency options.
  - Other **bold** text are “local variables” used in this description.

|                                |                                                                                                                                      |                                                                                                                                                                                                                                                                             |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Model Evaluation               | Description                                                                                                                          | Specific Implementation for this model                                                                                                                                                                                                                                      |
| **Monitor Only**               | Determine a Boolean result to indicate whether the stability model is “violated” and ready to do something?                          | Evaluates whether “Present Current on Branch \>**ThresholdCurrent**”.                                                                                                                                                                                                       |
| TimeDelay used in **Trip/Act** | Time in seconds that the model needs to remain “violated” before it will actually apply an action when the Trip/Act option is chosen | TimeDelay is calculated by taking the Present Current on Branch and run this through the **Lookup Table** specified in the dynamic model parameters along with the Time Dial Multiplier. Essentially we use a time assuming that the current remains at this level forever. |
| **Trip/Act** Action            | If violated for the particular time, then this procedure must be written to actually implement the action.                           | Model will open appropriate branches as would be done in transient stability                                                                                                                                                                                                |

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|                  |                                                                                                                                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RelaySlot        | Relay Slot \[1 or 2\]                                                                                                                                                                                                                          |
| Monitor          | Monitor=0, and trip=1                                                                                                                                                                                                                          |
| ThresholdCurrent | Threshold current, pu                                                                                                                                                                                                                          |
| ResetTime        | Zero Current Reset time in seconds. Let M = (I/Ithres). Then Time To Reset = Tdm\*{ResetTime/(1-M^2)}                                                                                                                                          |
| M1               | Multiple Current Threshold for Pickup Point 1                                                                                                                                                                                                  |
| Tm1              | Time to Close in Seconds for Pickup Point 1                                                                                                                                                                                                    |
| M2               | Multiple Current Threshold for Pickup Point 2                                                                                                                                                                                                  |
| Tm2              | Time to Close in Seconds for Pickup Point 2                                                                                                                                                                                                    |
| M3               | Multiple Current Threshold for Pickup Point 3                                                                                                                                                                                                  |
| Tm3              | Time to Close in Seconds for Pickup Point 3                                                                                                                                                                                                    |
| M4               | Multiple Current Threshold for Pickup Point 4                                                                                                                                                                                                  |
| Tm4              | Time to Close in Seconds for Pickup Point 4                                                                                                                                                                                                    |
| M5               | Multiple Current Threshold for Pickup Point 5                                                                                                                                                                                                  |
| Tm5              | Time to Close in Seconds for Pickup Point 5                                                                                                                                                                                                    |
| BreakerTime      | Circuit Breaker Time in Seconds                                                                                                                                                                                                                |
| LoadShedPerc     | Fraction of Transfer Trip Load to shed                                                                                                                                                                                                         |
| direct           | 0 means no directional element; 1 means directional element AND Direction will be based upon current leaving the FROM end of the branch; 2 means directional element AND Direction will be based upon current leaving the TO end of the branch |

---

<a id="tiocrs"></a>

## TIOCRS

*Source: [`Content/TransientModels_HTML/Line Relays TIOCRS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays TIOCRS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - CurveType: Error is created if curve type is not 1 (for IEEE), 2 (for IEC), or 3 (for IAC).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Treatment of Model in Power Flow Contingency Analysis

When a transient stability model is used in the power flow contingency analysis using the [special option for the power flow contingency solution](22-contingency-analysis-options.md#transient-models), then the model determines how to report violation for the Monitor Only option as well as specifying a TimeDelay and Trip/Act action. The following table describes this and uses the following text conventions.

  - **Green**ext are parameters of a stability model.
  - **Blue** text are a parameter of the contingency options.
  - Other **bold** text are “local variables” used in this description.

|                                |                                                                                                                                      |                                                                                                                                                                                                       |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Model Evaluation               | Description                                                                                                                          | Specific Implementation for this model                                                                                                                                                                |
| **Monitor Only**               | Determine a Boolean result to indicate whether the stability model is “violated” and ready to do something?                          | Evaluates whether “Present Current on Branch \>**ThresholdCurrent**”.                                                                                                                                 |
| TimeDelay used in **Trip/Act** | Time in seconds that the model needs to remain “violated” before it will actually apply an action when the Trip/Act option is chosen | TimeDelay is calculated by taking the Present Current on Branch and run this through the **TimeToClose function**. Essentially we use a time assuming that the current remains at this level forever. |
| **Trip/Act** Action            | If violated for the particular time, then this procedure must be written to actually implement the action.                           | Model will open appropriate branches as would be done in transient stability                                                                                                                          |

Model Equations and/or Block Diagrams   View in fullscreen

**Parameters:**

|                  |                                                                                                                                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RelaySlot        | Relay Slot \[1 or 2\]                                                                                                                                                                                                                          |
| Monitor          | Monitor=0, and trip=1                                                                                                                                                                                                                          |
| CurveType        | Curve Type. Determines the function used to describe Relay Time Inverse Curve. Options are 1 = IEEE C37.113 standard; 2 = IEC 255-4 and British BS142; 3 = IAC GE Type                                                                         |
| ThresholdCurrent | Threshold current, Amps                                                                                                                                                                                                                        |
| BreakerTime      | Circuit Breaker Time in Seconds                                                                                                                                                                                                                |
| Tdm              | Time Dial Multiplier. All times specified will be treated as this multiple larger                                                                                                                                                              |
| ResetTime        | Zero Current Reset time in seconds. Let M = (I/Ithres). Then Time To Reset = Tdm\*{ResetTime/(1-M^2)}                                                                                                                                          |
| p                | Curve Exponent Parameter. See more information with paramters A, B, C, D, E                                                                                                                                                                    |
| A                | Curve Coefficient A. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}                                                                                           |
| B                | Curve Coefficient B. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}                                                                                           |
| C                | Curve Coefficient C. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| D                | Curve Coefficient D. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| E                | Curve Coefficient E. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| t3trip           | 0 means trip monitor winding; 1 means trip whole 3 winding Xfmr                                                                                                                                                                                |
| direct           | 0 means no directional element; 1 means directional element AND Direction will be based upon current leaving the FROM end of the branch; 2 means directional element AND Direction will be based upon current leaving the TO end of the branch |

---

<a id="tiocrsrf"></a>

## TIOCRSRF

*Source: [`Content/TransientModels_HTML/Line Relays TIOCRSRF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays TIOCRSRF.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - CurveType: Error is created if curve type is not 1 (for IEEE), 2 (for IEC), or 3 (for IAC).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

The model is the same as the TIOCRS model

The difference is that the model allow for reclosing of the branch. The TIOCRSRF have two new parameters:

\-TransferReclose: It is for the reclosing time (seconds) of the transfer branches. If time is 0 it will not reclose.

\-ReclosewithFault: Reclose With Fauilt Not Cleared? 1 means a YES (Default), 0 means NO

**Parameters:**

|                  |                                                                                                                                                                                                                                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RelaySlot        | Relay Slot \[1 or 2\]                                                                                                                                                                                                                          |
| Monitor          | Monitor=0, and trip=1                                                                                                                                                                                                                          |
| CurveType        | Curve Type. Determines the function used to describe Relay Time Inverse Curve. Options are 1 = IEEE C37.113 standard; 2 = IEC 255-4 and British BS142; 3 = IAC GE Type                                                                         |
| ThresholdCurrent | Threshold current, Amps                                                                                                                                                                                                                        |
| BreakerTime      | Circuit Breaker Time in Seconds                                                                                                                                                                                                                |
| Tdm              | Time Dial Multiplier. All times specified will be treated as this multiple larger                                                                                                                                                              |
| ResetTime        | Zero Current Reset time in seconds. Let M = (I/Ithres). Then Time To Reset = Tdm\*{ResetTime/(1-M^2)}                                                                                                                                          |
| p                | Curve Exponent Parameter. See more information with paramters A, B, C, D, E                                                                                                                                                                    |
| A                | Curve Coefficient A. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}                                                                                           |
| B                | Curve Coefficient B. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}                                                                                           |
| C                | Curve Coefficient C. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| D                | Curve Coefficient D. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| E                | Curve Coefficient E. Usage depends on Curve Type. Let M = (I/Ithres). Then IEEE curves use Tdm\*{B + A/(M^p - 1)}; IEC curves use Tdm\*{A/(M^p - 1)}; IAC curves use Tdm\*{A + B/(M-C) + D/\[(M-C)^2\] + E/\[(M-C)^3\]}                        |
| t3trip           | 0 means trip monitor winding; 1 means trip whole 3 winding Xfmr                                                                                                                                                                                |
| direct           | 0 means no directional element; 1 means directional element AND Direction will be based upon current leaving the FROM end of the branch; 2 means directional element AND Direction will be based upon current leaving the TO end of the branch |
| TransferReclose  | Transfer reclose, cycles                                                                                                                                                                                                                       |
| RecloseWithFault | Reclose With Fauilt Not Cleared? 1 means a YES (Default), 0 means NO                                                                                                                                                                           |

---

<a id="tlin1"></a>

## TLIN1

*Source: [`Content/TransientModels_HTML/Line Relays TLIN1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays TLIN1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays TLIN1 0001](images/Line_Relays_TLIN1_0001.svg)

**Parameters:**

|       |                                          |
| ----- | ---------------------------------------- |
| Input | Input signal flag ( 0 = f , 1 = v )      |
| Flag  | Mode flag                                |
| Tf    | Transducer or filter time constant, sec. |
| V1    | Relay pickup setting, p.u.               |
| T1    | Relay definite time setting, sec.        |
| Tcb1  | Circuit breaker operating time, sec.     |

---

<a id="uf-ak"></a>

## UF_AK

*Source: [`Content/TransientModels_HTML/Branch Model UF_AK.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Branch Model UF_AK.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|        |                                        |
| ------ | -------------------------------------- |
| FREQ   | Under Frequency Pick-up Point in Hertz |
| RDELAY | Relay Time in Seconds                  |
| BDELAY | Brealer Time in Seconds                |

---

<a id="zdcb"></a>

## ZDCB

*Source: [`Content/TransientModels_HTML/Line Relays ZDCB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZDCB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZDCB 0001](images/Line_Relays_ZDCB_0001.svg)

**Parameters:**

|               |                                                                                                                                                                                                                                             |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip        | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                                |
| Shape1        | Shape of Impedance Zone 1. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                            |
| Shape2\_Relay | Shape of Relay End Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape2\_Other | Shape of Other End Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape3\_Relay | Shape of Relay End Impedance Zone 3. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape3\_Other | Shape of Other End Impedance Zone 3. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Tcb           | Breaker Operating Time (in Seconds)                                                                                                                                                                                                         |
| Ang1          | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                                      |
| Rf1           | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                                   |
| Rr1           | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                           |
| Wt1           | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle).           |
| Wr1           | Right Width (in per unit) of Impedance Zone 1. (Only used for rectangular shape)                                                                                                                                                            |
| T1            | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                                |
| Ang2\_Relay   | Angle (in degrees) of Relay End Impedance Zone 2                                                                                                                                                                                            |
| Rf2\_Relay    | Forward Reach Impedance (in per unit) of Relay End Impedance Zone 2                                                                                                                                                                         |
| Rr2\_Relay    | Reverse Reach Impedance (in per unit) of Relay End Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2\_Relay    | Total Width (in per unit) of Relay End Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2\_Relay    | Right Width (in per unit) of Relay End Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2\_Relay     | Pickup Time (in Seconds) of Relay End Impedance Zone 2                                                                                                                                                                                      |
| Ang2\_Other   | Angle (in degrees) of Other End Impedance Zone 2                                                                                                                                                                                            |
| Rf2\_Other    | Forward Reach Impedance (in per unit) of Other End Impedance Zone 2                                                                                                                                                                         |
| Rr2\_Other    | Reverse Reach Impedance (in per unit) of Other End Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2\_Other    | Total Width (in per unit) of Other End Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2\_Other    | Right Width (in per unit) of Other End Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2\_Other     | Pickup Time (in Seconds) of Other End Impedance Zone 2                                                                                                                                                                                      |
| Ang3\_Relay   | Angle (in degrees) of Relay End Impedance Zone 3                                                                                                                                                                                            |
| Rf3\_Relay    | Forward Reach Impedance (in per unit) of Relay End Impedance Zone 3                                                                                                                                                                         |
| Rr3\_Relay    | Reverse Reach Impedance (in per unit) of Relay End Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3\_Relay    | Total Width (in per unit) of Relay End Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr3\_Relay    | Right Width (in per unit) of Relay End Impedance Zone 3. (Only used for rectangular shape)                                                                                                                                                  |
| T3\_Relay     | Pickup Time (in Seconds) of Relay End Impedance Zone 3                                                                                                                                                                                      |
| Ang3\_Other   | Angle (in degrees) of Other End Impedance Zone 3                                                                                                                                                                                            |
| Rf3\_Other    | Forward Reach Impedance (in per unit) of Other End Impedance Zone 3                                                                                                                                                                         |
| Rr3\_Other    | Reverse Reach Impedance (in per unit) of Other End Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3\_Other    | Total Width (in per unit) of Other End Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr3\_Other    | Right Width (in per unit) of Other End Impedance Zone 3. (Only used for rectangular shape)                                                                                                                                                  |
| T3\_Other     | Pickup Time (in Seconds) of Other End Impedance Zone 3                                                                                                                                                                                      |

---

<a id="zlin1"></a>

## ZLIN1

*Source: [`Content/TransientModels_HTML/Line Relays ZLIN1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZLIN1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZLIN1 0001](images/Line_Relays_ZLIN1_0001.svg)

**Parameters:**

|         |                                                                                                                                                                                 |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip  | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                    |
| ImpType | Impedance Type. Specifies the interpretation of Alpha and Forward Reach. 0 means polar (Angle and Magnitude). 1 means rectangular ("Angle" means R and "Forward Reach" means X) |
| Ang1    | Angle (in degrees) of Impedance Zone 1                                                                                                                                          |
| Rf1     | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                       |
| Rr1     | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                               |
| T1      | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                    |
| Tcb1    | Breaker Operating Time (in Seconds) of Impedance Zone 1                                                                                                                         |
| Ang2    | Angle (in degrees) of Impedance Zone 2                                                                                                                                          |
| Rf2     | Forward Reach Impedance (in per unit) of Impedance Zone 2                                                                                                                       |
| Rr2     | Reverse Reach Impedance (in per unit) of Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                               |
| T2      | Pickup Time (in Seconds) of Impedance Zone 2                                                                                                                                    |
| Tcb2    | Breaker Operating Time (in Seconds) of Impedance Zone 2                                                                                                                         |
| Ang3    | Angle (in degrees) of Impedance Zone 3                                                                                                                                          |
| Rf3     | Forward Reach Impedance (in per unit) of Impedance Zone 3                                                                                                                       |
| Rr3     | Reverse Reach Impedance (in per unit) of Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                               |
| T3      | Pickup Time (in Seconds) of Impedance Zone 3                                                                                                                                    |
| Tcb3    | Breaker Operating Time (in Seconds) of Impedance Zone 3                                                                                                                         |

---

<a id="zpott"></a>

## ZPOTT

*Source: [`Content/TransientModels_HTML/Line Relays ZPOTT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZPOTT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZPOTT 0001](images/Line_Relays_ZPOTT_0001.svg)

**Parameters:**

|               |                                                                                                                                                                                                                                             |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip        | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                                |
| Shape1        | Shape of Impedance Zone 1. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                            |
| Shape2\_Relay | Shape of Relay End Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape2\_Other | Shape of Other End Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Tcb           | Breaker Operating Time (in Seconds)                                                                                                                                                                                                         |
| Ang1          | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                                      |
| Rf1           | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                                   |
| Rr1           | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                           |
| Wt1           | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle).           |
| Wr1           | Right Width (in per unit) of Impedance Zone 1. (Only used for rectangular shape)                                                                                                                                                            |
| T1            | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                                |
| Ang2\_Relay   | Angle (in degrees) of Relay End Impedance Zone 2                                                                                                                                                                                            |
| Rf2\_Relay    | Forward Reach Impedance (in per unit) of Relay End Impedance Zone 2                                                                                                                                                                         |
| Rr2\_Relay    | Reverse Reach Impedance (in per unit) of Relay End Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2\_Relay    | Total Width (in per unit) of Relay End Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2\_Relay    | Right Width (in per unit) of Relay End Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2\_Relay     | Pickup Time (in Seconds) of Relay End Impedance Zone 2                                                                                                                                                                                      |
| Ang2\_Other   | Angle (in degrees) of Other End Impedance Zone 2                                                                                                                                                                                            |
| Rf2\_Other    | Forward Reach Impedance (in per unit) of Other End Impedance Zone 2                                                                                                                                                                         |
| Rr2\_Other    | Reverse Reach Impedance (in per unit) of Other End Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2\_Other    | Total Width (in per unit) of Other End Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2\_Other    | Right Width (in per unit) of Other End Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2\_Other     | Pickup Time (in Seconds) of Other End Impedance Zone 2                                                                                                                                                                                      |

---

<a id="zqlin1"></a>

## ZQLIN1

*Source: [`Content/TransientModels_HTML/Line Relays ZQLIN1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZQLIN1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZQLIN1 0001](images/Line_Relays_ZQLIN1_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                   |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                      |
| Shape1 | Shape of Impedance Zone 1. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape2 | Shape of Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape3 | Shape of Impedance Zone 3. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Tcb    | Breaker Operating Time (in Seconds)                                                                                                                                                                                               |
| Ang1   | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                            |
| Rf1    | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                         |
| Rr1    | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt1    | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr1    | Right Width (in per unit) of Impedance Zone 1. (Only used for rectangular shape)                                                                                                                                                  |
| T1     | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                      |
| Ang2   | Angle (in degrees) of Impedance Zone 2                                                                                                                                                                                            |
| Rf2    | Forward Reach Impedance (in per unit) of Impedance Zone 2                                                                                                                                                                         |
| Rr2    | Reverse Reach Impedance (in per unit) of Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2    | Total Width (in per unit) of Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2    | Right Width (in per unit) of Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2     | Pickup Time (in Seconds) of Impedance Zone 2                                                                                                                                                                                      |
| Ang3   | Angle (in degrees) of Impedance Zone 3                                                                                                                                                                                            |
| Rf3    | Forward Reach Impedance (in per unit) of Impedance Zone 3                                                                                                                                                                         |
| Rr3    | Reverse Reach Impedance (in per unit) of Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3    | Total Width (in per unit) of Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr3    | Right Width (in per unit) of Impedance Zone 3. (Only used for rectangular shape)                                                                                                                                                  |
| T3     | Pickup Time (in Seconds) of Impedance Zone 3                                                                                                                                                                                      |

---

<a id="zqlin2"></a>

## ZQLIN2

*Source: [`Content/TransientModels_HTML/Line Relays ZQLIN2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZQLIN2.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZQLIN2 0001](images/Line_Relays_ZQLIN2_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                   |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NoTrip | No Trip Flag. Set to \> 0 to disable breaker tripping. Note: relay signal will still update.                                                                                                                                      |
| Shape1 | Shape of Impedance Zone 1. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape2 | Shape of Impedance Zone 2. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Shape3 | Shape of Impedance Zone 3. 0 means a circle, lens or tomato. 1 means a rectangle                                                                                                                                                  |
| Tcb    | Breaker Operating Time (in Seconds)                                                                                                                                                                                               |
| Ang1   | Angle (in degrees) of Impedance Zone 1                                                                                                                                                                                            |
| Rf1    | Forward Reach Impedance (in per unit) of Impedance Zone 1                                                                                                                                                                         |
| Rr1    | Reverse Reach Impedance (in per unit) of Impedance Zone 1. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt1    | Total Width (in per unit) of Impedance Zone 1. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr1    | Right Width (in per unit) of Impedance Zone 1. (Only used for rectangular shape)                                                                                                                                                  |
| T1     | Pickup Time (in Seconds) of Impedance Zone 1                                                                                                                                                                                      |
| Ang2   | Angle (in degrees) of Impedance Zone 2                                                                                                                                                                                            |
| Rf2    | Forward Reach Impedance (in per unit) of Impedance Zone 2                                                                                                                                                                         |
| Rr2    | Reverse Reach Impedance (in per unit) of Impedance Zone 2. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt2    | Total Width (in per unit) of Impedance Zone 2. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr2    | Right Width (in per unit) of Impedance Zone 2. (Only used for rectangular shape)                                                                                                                                                  |
| T2     | Pickup Time (in Seconds) of Impedance Zone 2                                                                                                                                                                                      |
| Ang3   | Angle (in degrees) of Impedance Zone 3                                                                                                                                                                                            |
| Rf3    | Forward Reach Impedance (in per unit) of Impedance Zone 3                                                                                                                                                                         |
| Rr3    | Reverse Reach Impedance (in per unit) of Impedance Zone 3. (Note: For backward reach, specify a POSITIVE number.)                                                                                                                 |
| Wt3    | Total Width (in per unit) of Impedance Zone 3. If Width \> Rf + Rr, then use union of circles (tomato). If Width \< Rf + Rr, then use intersection of circles (lens). If Width = 0 or Rf + Rr, then just use one circle (circle). |
| Wr3    | Right Width (in per unit) of Impedance Zone 3. (Only used for rectangular shape)                                                                                                                                                  |
| T3     | Pickup Time (in Seconds) of Impedance Zone 3                                                                                                                                                                                      |

---

<a id="zlinw"></a>

## ZLINW

*Source: [`Content/TransientModels_HTML/Line Relays ZLINW.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays ZLINW.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays ZLINW 0001](images/Line_Relays_ZLINW_0001.svg)

**Parameters:**

|        |                                                              |
| ------ | ------------------------------------------------------------ |
| trip   | Monitor. 0 = Alarm; 1 = Trip                                 |
| scline | scline; 0 = Do not include lines with series capacitors.     |
| Td2    | Td2; Zone 2 time delay (pickup).                             |
| Tcb    | Tcb; Breaker Time Delay in seconds.                          |
| Trc    | Trc; Reclosing Time in seconds.                              |
| dz1    | dz1; Zone 1 circle diameter in p.u of line X (dz1\*line\_X). |
| dz2    | dz2; Zone 2 circle diameter in p.u of line X (dz2\*line\_X). |
| KVmin  | Minimum base kV of lines to be included.                     |
| KVmax  | Maximum base kV of lines to be included.                     |

---

<a id="differential"></a>

## Differential

*Source: [`Content/TransientModels_HTML/BranchFolder Differential.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder Differential.htm)*

_This topic has no body text in the source help file._

---

<a id="impedancedistance"></a>

## Impedance/Distance

*Source: [`Content/TransientModels_HTML/BranchFolder ImpedanceDistance.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder ImpedanceDistance.htm)*

_This topic has no body text in the source help file._

---

<a id="over-current"></a>

## Over Current

*Source: [`Content/TransientModels_HTML/BranchFolder OverCurrent.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder OverCurrent.htm)*

_This topic has no body text in the source help file._

---

<a id="series-capacitor"></a>

## Series Capacitor

*Source: [`Content/TransientModels_HTML/BranchFolder SeriesCapacitor.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder SeriesCapacitor.htm)*

_This topic has no body text in the source help file._

---

<a id="transformer"></a>

## Transformer

*Source: [`Content/TransientModels_HTML/BranchFolder Transformer.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder Transformer.htm)*

_This topic has no body text in the source help file._

---

<a id="voltagefrequency"></a>

## Voltage/Frequency

*Source: [`Content/TransientModels_HTML/BranchFolder VoltageFrequency.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BranchFolder VoltageFrequency.htm)*

_This topic has no body text in the source help file._

---

<a id="tlin1o"></a>

## TLIN1O

*Source: [`Content/TransientModels_HTML/Line Relays TLIN1O.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Relays TLIN1O.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Line Relays TLIN1O 0001](images/Line_Relays_TLIN1O_0001.svg)

**Parameters:**

|       |                                          |
| ----- | ---------------------------------------- |
| Input | Input signal flag ( 0 = f , 1 = v )      |
| Flag  | Mode flag                                |
| Tf    | Transducer or filter time constant, sec. |
| V1    | Relay pickup setting, p.u.               |
| T1    | Relay definite time setting, sec.        |
| Tcb1  | Circuit breaker operating time, sec.     |

---

<a id="line-shunt"></a>

## Line Shunt

*Source: [`Content/TransientModels_HTML/Shunt.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Shunt.htm)*

_This topic has no body text in the source help file._

---

<a id="mslr1"></a>

## MSLR1

*Source: [`Content/TransientModels_HTML/Line Shunt MSLR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Line Shunt MSLR1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Vmax1 \< Vmin1 then swap the values
  - If Vmax2 \< Vmin2 then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

Model supported by PSLF

**Parameters:**

|       |                                 |
| ----- | ------------------------------- |
| Tin1  | Time 1 for Switching in (sec.)  |
| Vmax1 | Voltage upper limit 1 (p.u.)    |
| Tout1 | Time 1 for Switching out (sec.) |
| Vmin1 | Voltage lower limit 1 (p.u.)    |
| Tin2  | Time 2 for Switching in (sec.)  |
| Vmax2 | Voltage upper limit 2 (p.u.)    |
| Tout2 | Time 2 for Switching out (sec.) |
| Vmin2 | Voltage lower limit 2 (p.u.)    |

---

<a id="switched-shunt"></a>

## Switched Shunt

*Source: [`Content/TransientModels_HTML/Switched Shunt.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt.htm)*

_This topic has no body text in the source help file._
