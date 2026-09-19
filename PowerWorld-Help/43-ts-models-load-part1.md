---
title: "TS Models — Loads (Part 1 of 3)"
part: "Transient Models"
chapter_file: "43-ts-models-load-part1.md"
topics: 21
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Loads (Part 1 of 3)

Load characteristic models, distributed generation, distribution equivalents and load relays.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (21)**

- [Load](#load)
- [Characteristic](#characteristic)
- [All](#all)
- [BRAKE](#brake)
- [CIM5](#cim5)
- [CIM5_PTR](#cim5-ptr)
- [CIM6](#cim6)
- [CIMW](#cimw)
- [CLOD](#clod)
- [CMLD](#cmld)
- [CMPLDW](#cmpldw)
- [CMPLDWNF](#cmpldwnf)
- [DLIGHT](#dlight)
- [EXTL](#extl)
- [IEEL](#ieel)
- [INDMOT1P](#indmot1p)
- [INDMOT1P_PTR](#indmot1p-ptr)
- [INDMOT3P_A](#indmot3p-a)
- [LD1PAC](#ld1pac)
- [LD1PAC_CMP](#ld1pac-cmp)
- [LDELEC](#ldelec)

---

<a id="load"></a>

## Load

*Source: [`Content/TransientModels_HTML/Load.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load.htm)*

_This topic has no body text in the source help file._

---

<a id="characteristic"></a>

## Characteristic

*Source: [`Content/TransientModels_HTML/Load Characteristic.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic.htm)*

_This topic has no body text in the source help file._

---

<a id="all"></a>

## All

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder All.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder All.htm)*

_This topic has no body text in the source help file._

---

<a id="brake"></a>

## BRAKE

*Source: [`Content/TransientModels_HTML/Load Characteristic BRAKE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic BRAKE.htm)*

**AutoCorrection Properties**

Any inservice load which has a BRAKE model assigned to it will cause a validation error and prevent any simulation from running.

Note that the actual MW and Mvar of the respective load in the power flow case are ignored.

Added in Version 19, build on January 13, 2016

This model represents a braking resistor such as the Chief Joseph Braking resistor. This model has 5 input parameters (ZmwStart, ZmvarStart, ZmwEnd, ZmvarEnd, and Tinsert). When a load with this characteristic is Closed during a simulation, it will start as a constant nominal impedance represented by ZmwStart + jZmvarStart. It will than linearly change into a constant nominal impedance represented by ZmwEnd + jZmvarEnd over a time of Tinsert seconds. Tinsert seconds after the load is closed in, the model will automatically trip the load again. The figure below depicts this. During validation, if the load record to which this stability model is assigned is inservice, a validation error will occur which prevents you from running transient stability. The expectation is that the braking resistor will be represented by an OPEN load which has zero MW and zero Mvar in the power flow case, however the actual MW and Mvar in the power flow case are ignored.”

Example:

![Load Characteristic BRAKE](images/Load_Characteristic_BRAKE.png)

Model Equations and/or Block Diagrams

![Load Characteristic BRAKE 0001](images/Load_Characteristic_BRAKE_0001.svg)

**Parameters:**

ObjectFieldSummary

Field Name Description

|            |                                                                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| ZmwStart   | The initial resistance in the units of MW. This will represent the load MWs that the brake would be at 1.0 per unit voltage.    |
| ZmvarStart | The initial reactance in the units of Mvar. This will represent the load Mvars that the brake would be at 1.0 per unit voltage. |
| ZmwEnd     | The final resistance in the units of MW. This will represent the load MWs that the brake would be at 1.0 per unit voltage.      |
| ZmvarEnd   | The final reactance in the units of Mvar. This will represent the load Mvars that the brake would be at 1.0 per unit voltage.   |
| Tinsert    | Time in seconds that the brake remains inserted after being activated.                                                          |

---

<a id="cim5"></a>

## CIM5

*Source: [`Content/TransientModels_HTML/Load Characteristic CIM5.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CIM5.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - R1: 1) If motor is not Double Cage or Type 1, then if circuit parameters result in a Tp time constant which is too small then set R1 to a multiple of Tp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage or type 2, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R1 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).
  - R2: 1) If motor is Double Cage and Type 1, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage and Type 2, then if circuit parameters result in a Tp time constant which is too small then set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Load Characteristic CIM5 0001](images/Load_Characteristic_CIM5_0001.svg)

![Load Characteristic CIM5 0002](images/Load_Characteristic_CIM5_0002.svg)

![Load Characteristic CIM5 0003](images/Load_Characteristic_CIM5_0003.svg)

**Parameters:**

|       |                                                                                           |
| ----- | ----------------------------------------------------------------------------------------- |
| IT    | 1: Motor type 1; 2: Motor type 2                                                          |
| Ra    | Armature Resistance in per unit on machine MVABase                                        |
| Xa    | Leakage Reactance in per unit on machine MVABase                                          |
| Xm    | Magnetizing Reactance in per unit on machine MVABase                                      |
| R1    | Rotor Resistance in per unit on machine MVABase                                           |
| X1    | Rotor Reactance in per unit on machine MVABase                                            |
| R2    | Second Winding Rotor Resistance in per unit on machine MVABase                            |
| X2    | Second Winding Rotor Reactance in per unit on machine MVABase                             |
| E1    | E1                                                                                        |
| SE1   | SE1                                                                                       |
| E2    | E2                                                                                        |
| SE2   | SE2                                                                                       |
| Mbase | When MBASE = 0, motor MVA base = PMULT x MW load. When MBASE \> 0, motor MVA base = MBASE |
| Pmult | Pmult                                                                                     |
| H     | H (inertia, per unit motor base)                                                          |
| Vi    | Per unit voltage for dropping induction motor                                             |
| Ti    | Time needed for voltage to remain below Vi for dropping induction motor, cycles           |
| Tb    | Breaker delay for tripping, cycles                                                        |
| D     | D (load damping factor)                                                                   |
| Tnom  | Tnom, Load torque at 1 pu speed (used for motor starting only) (≥ 0)                      |

---

<a id="cim5-ptr"></a>

## CIM5_PTR

*Source: [`Content/TransientModels_HTML/Load Characteristic CIM5_PTR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CIM5_PTR.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - R1: 1) If motor is not Double Cage or Type 1, then if circuit parameters result in a Tp time constant which is too small then set R1 to a multiple of Tp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage or type 2, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R1 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).
  - R2: 1) If motor is Double Cage and Type 1, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage and Type 2, then if circuit parameters result in a Tp time constant which is too small then set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

This model builds on the CIM5 model, but makes some modifications

1\. Removes the modeling of magnetic saturation.

2\. Replaces the definite time under voltage relay with a progressing tripping and reconnecting for under voltage model.

3\. Modification of the network interface equations to include the impact of terminal frequency

**Parameters:**

|        |                                                                                                                                  |
| ------ | -------------------------------------------------------------------------------------------------------------------------------- |
| LF     | Load Factor. All values are on an MVABaseUsed=(MW\_init)/LF                                                                      |
| MBase  | If MBase \> 0 then machine parameters are on this MVABaseUsed is equation to this, otherwise the MVABaseUsed is MWinit/LF        |
| Tnom   | Nominal load torque used for motor starting studies. For online motors this is automatically calculated from initial conditions. |
| Ra     | Armature Resistance in per unit on machine MVABase                                                                               |
| Xa     | Leakage Reactance in per unit on machine MVABase                                                                                 |
| Xm     | Magnetizing Reactance in per unit on machine MVABase                                                                             |
| R1     | Rotor Resistance in per unit on machine MVABase                                                                                  |
| X1     | Rotor Reactance in per unit on machine MVABase                                                                                   |
| R2     | Second Winding Rotor Resistance in per unit on machine MVABase                                                                   |
| X2     | Second Winding Rotor Reactance in per unit on machine MVABase                                                                    |
| H      | Inertia constant for the motor                                                                                                   |
| Etrq   | Exponent of the exponential term of the mechanical torque equation T\_mech=T\_nom (ω\_r^(E\_trq ) )                              |
| Tv     | Voltage measurement delay in seconds                                                                                             |
| V1off  | Voltage in per unit at which load fraction begins decreasing                                                                     |
| V2off  | Voltage in per unit at which load fraction decreases to zero                                                                     |
| V1on   | Voltage in per unit at which load fraction begins increasing                                                                     |
| V2on   | Voltage in per unit at which load fraction increases back to \[FracMin + Frecon\*(1.0- FracMin)\]                                |
| Frecon | Fraction of load that has been disconnected that will come back as voltage recovers                                              |
| Tdelay | Time delay use to approximate time vs voltage nature of load loss as the voltage is decreasing expressed in seconds              |
| Vtd    | Voltage threshold below with the Time delay used starts decreasing toward 0 seconds at a voltage of 0                            |
| Trecon | Time delay use to approximate the reconnection of load as the voltage is increasing                                              |

![Load Characteristic CIM5 PTR 0002](images/Load_Characteristic_CIM5_PTR_0002.svg)

![Load Characteristic CIM5 PTR 0003](images/Load_Characteristic_CIM5_PTR_0003.svg)

![Load Characteristic CIM5 PTR 0004](images/Load_Characteristic_CIM5_PTR_0004.svg)

![Load Characteristic CIM5 PTR 0005](images/Load_Characteristic_CIM5_PTR_0005.svg)

<span class="underline">User Parameters</span>

V1off, V2off, V1on, V2on, Frecon

<span class="underline">Rules:</span>

V2off \<= V1off

V1on \>= V1off

V2off \<= V2on \<= V1on

<span class="underline">Inputs to Block</span>

DelayBlockOutput = output of Time Delay block

PresentV = measured voltage to block

<span class="underline">Initialization section does the following</span>

if Frecon \< 0.0 then Frecon = 0.0

else if Frecon \> 1.0 then Frecon = 1.0

// Order of precedence for trustworthiness of input is V1off, V2off, V2on, then V1on.

if V2off \> V1off then V2off = V1off // decrease V2off to at least V1off

if V1on \< V1off then V1on = V1off // increase V1on to at least V1off

if V2on \< V2off then V2on = V2off // increase V2on to at least V2off

if V1on \< V2on then V1on = V2on // increase V1on to at least V2on

Vmin = V1off

FracMin = 1.0

<span class="underline">Following updated at the beginning of each Time Step</span>

// FracMin is the minimum fraction during the simulation

if FracMin \> DelayBlockOutput \< then begin

FracMin = DelayBlockOutput

if FracMin \>= 1.0 then Vmin = V1off

else if FracMin \<= 0.0 then Vmin = V2off

else Vmin = V2off + FracMin \*(V1off – V2off)

end

<span class="underline">Following Function for calculating a new DelayBlockInput</span>

if PresentV \<= Vmin then begin

if PresentV \<= V2off then result = 0.0 // aaaa

else result = (PresentV – V2off)/(V1off – V2off) // bbbb red curve

end

else if (Vmin \>= V1off) then result = 1.0 // cccc purple curve

else if (PresentV \<= V2on) then result = FracMin // dddd light blue curve

else if (PresentV \< V1on) then begin

// see image on right above for situation when Vmin \> V2on

if Vmin \> V2on then tempV = Vmin

else tempV = V2on

result = FracMin + Frecon\*(1.0 - FracMin)\*(PresentV - tempV)/(V1on – tempV) // eeee orange

end

else result = FracMin + Frecon\*(1.0 - FracMin) // ffff green curve

---

<a id="cim6"></a>

## CIM6

*Source: [`Content/TransientModels_HTML/Load Characteristic CIM6.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CIM6.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - R1: 1) If motor is not Double Cage or Type 1, then if circuit parameters result in a Tp time constant which is too small then set R1 to a multiple of Tp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage or type 2, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R1 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).
  - R2: 1) If motor is Double Cage and Type 1, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage and Type 2, then if circuit parameters result in a Tp time constant which is too small then set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-Model is the same as CIM5, except for the load torque.

\-Load Torque = T(Aω^2 + Bω + C0 + Dω^E). For motor starting T = TNOM. For online motors, T is calculated during initialization

**Parameters:**

|       |                                                                                           |
| ----- | ----------------------------------------------------------------------------------------- |
| IT    | 1: Motor type 1; 2: Motor type 2                                                          |
| Ra    | Armature Resistance in per unit on machine MVABase                                        |
| Xa    | Leakage Reactance in per unit on machine MVABase                                          |
| Xm    | Magnetizing Reactance in per unit on machine MVABase                                      |
| R1    | Rotor Resistance in per unit on machine MVABase                                           |
| X1    | Rotor Reactance in per unit on machine MVABase                                            |
| R2    | Second Winding Rotor Resistance in per unit on machine MVABase                            |
| X2    | Second Winding Rotor Reactance in per unit on machine MVABase                             |
| E1    | E1                                                                                        |
| SE1   | SE1                                                                                       |
| E2    | E2                                                                                        |
| SE2   | SE2                                                                                       |
| Mbase | When MBASE = 0, motor MVA base = PMULT x MW load. When MBASE \> 0, motor MVA base = MBASE |
| Pmult | Pmult                                                                                     |
| H     | H (inertia, per unit motor base)                                                          |
| Vi    | Per unit voltage for dropping induction motor                                             |
| Ti    | Time needed for voltage to remain below Vi for dropping induction motor, cycles           |
| Tb    | Breaker delay for tripping, cycles                                                        |
| A     | Equation parameter                                                                        |
| B     | Equation parameter                                                                        |
| D     | Equation parameter                                                                        |
| E     | Equation exponent                                                                         |
| C0    | Equation parameter                                                                        |
| Tnom  | Tnom, Load torque at 1 pu speed (used for motor starting only) (≥ 0)                      |

---

<a id="cimw"></a>

## CIMW

*Source: [`Content/TransientModels_HTML/Load Characteristic CIMW.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CIMW.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - R1: 1) If motor is not Double Cage or Type 1, then if circuit parameters result in a Tp time constant which is too small then set R1 to a multiple of Tp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage or type 2, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R1 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).
  - R2: 1) If motor is Double Cage and Type 1, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage and Type 2, then if circuit parameters result in a Tp time constant which is too small then set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-Model is the same as CIM5, except for the load torque.

\-Load Torque = T(Aω^2 + Bω + C0 + Dω^E). This motor can not be used for starting. C0 = 1 - Aω^2 - Bω - Dω^E

---

<a id="clod"></a>

## CLOD

*Source: [`Content/TransientModels_HTML/Load Characteristic CLOD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CLOD.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Characteristic CLOD 0001](images/Load_Characteristic_CLOD_0001.svg)

**Parameters:**

|            |                                |
| ---------- | ------------------------------ |
| PercLmotor | % large motor                  |
| PercSmotor | % small motor                  |
| PercTex    | % transformer exciting current |
| PercDis    | % discharge lighting           |
| PercP      | % constant power               |
| Kp         | KP of remaining                |
| BranchR    | Branch R (pu on load MW base)  |
| BranchX    | Branch X (pu on load MW base)  |

---

<a id="cmld"></a>

## CMLD

*Source: [`Content/TransientModels_HTML/Load Characteristic CMLD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CMLD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Vmax \< Vmin then swap the values. If Vmax \< 0 then Vmax change sign to positive. Also if Vmin \< 0.96 then Vmin = 0.96; and also if Vmax \< 0.96 then Vmax = 0.96
  - Mtypa, Mtypb, Mtypc and Mtypd: Must be either 1 or 3. This is an error and do not autocorrect the values.
  - FmA, FmB, FmC, FmD and Fel: Summation of (FmA + FmB + FmC + FmD + Fel) must be less or equal than 1.0, and if not then the values will be normalized so that sum equals 1.0.
  - For Motor Type 1 Motors (LD1PAC):
      - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
      - If 0.0 \< Tth \< 0.5\*Mult\*TimeStep then Tth = 0, ElseIf 0.5\*Mult\*TimeStep \< Tth \< Mult\*TimeStep then Tth = Mult\*TimeStep
      - If 0.0 \< Frst \< 0.5\*Mult\*TimeStep then Frst = 0, ElseIf 0.5\*Mult\*TimeStep \< Frst \< Mult\*TimeStep then Frst = Mult\*TimeStep
      - If 0.0 \< CompPF \< 0.01\*Mult\*TimeStep then CompPF = 0.0  
        ElseIf 0.01\*Mult\*TimeStep \< CompPF \< Mult\*TimeStep then CompPF = Mult\*TimeStep
  - For Motor Type 3 Motors (*MOTOR\_CMP*):
      - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
      - If H \< 0.01 then H = 0.01.
      - If Lp \> 0.4\*Ls then Lp = 0.4\*Ls
      - If Lpp \> Lp then Lpp = Lp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-Same model as CMPLDW.

\-Model supported by PSSE

**Parameters:**

|          |                                                                                                                   |
| -------- | ----------------------------------------------------------------------------------------------------------------- |
| Mbase    | Load MVA basea                                                                                                    |
| Bss      | Substation shunt B (pu on Load MVA base)                                                                          |
| Rfdr     | Feeder R (pu on Load MVA base)                                                                                    |
| Xfdr     | Feeder X (pu on Load MVA base)b                                                                                   |
| Fb       | Fraction of Feeder Compensation at substation end                                                                 |
| Xxf      | Transformer Reactance - pu on load MVA basec                                                                      |
| Tfixhs   | High side fixed transformer tap                                                                                   |
| Tfixls   | Low side fixed transformer tap                                                                                    |
| LTC      | flag (1: active during simulation, 0: inactive, -1: active during initialization, but inactive during simulation) |
| Tmin     | LTC min tap (on low side)                                                                                         |
| Tmax     | LTC max tap (on low side)                                                                                         |
| Step     | LTC Tstep (on low side)                                                                                           |
| Vmin     | LTC Vmin tap (low side pu)                                                                                        |
| Vmax     | LTC Vmax tap (low side pu)                                                                                        |
| TD       | LTC Control time delay (sec)                                                                                      |
| TC       | LTC Tap adJustment time delay (sec)                                                                               |
| Rcmp     | LTC Rcomp (pu on load MVA base)                                                                                   |
| Xcmp     | LTC Xcomp (pu on load MVA base)                                                                                   |
| FmA      | Motor A Fraction                                                                                                  |
| FmB      | Motor B Fraction                                                                                                  |
| FmC      | Motor C Fraction                                                                                                  |
| FmD      | Motor D Fraction                                                                                                  |
| Fel      | Electronic Load Fractiond                                                                                         |
| PFel     | PF of Electronic Loads                                                                                            |
| Vd1      | Voltage at which elect. loads start to drop                                                                       |
| Vd2      | Voltage at which all elect.load have dropped                                                                      |
| PFs      | Static Load Power Factor                                                                                          |
| P1e      | P1 exponente                                                                                                      |
| P1c      | P1 coefficient                                                                                                    |
| P2e      | P2 exponent                                                                                                       |
| P2c      | P2 coefficient                                                                                                    |
| Pfrq     | Frequency sensitivity                                                                                             |
| Q1e      | Q1 exponent                                                                                                       |
| Q1c      | Q1 coefficient                                                                                                    |
| Q2e      | Q2 exponent                                                                                                       |
| Q2c      | Q2 coefficient                                                                                                    |
| Qfrq     | Frequency sensitivity                                                                                             |
| MtypA    | Motor typef                                                                                                       |
| LFmA     | Loading factor (MW/MVA rating)                                                                                    |
| RaA      | Stator resistance                                                                                                 |
| LsA      | Synchronous reactance                                                                                             |
| LpA      | Transient reactance                                                                                               |
| LppA     | Sub-transient reactance                                                                                           |
| TpoA     | Transient open circuit time constant                                                                              |
| TppoA    | Sub-transient open circuit time constant                                                                          |
| HA       | Inertia constant                                                                                                  |
| etrqA    | Torque speed exponent                                                                                             |
| Vtr1A    | U/V Trip1 V (pu)                                                                                                  |
| Ttr1A    | U/V Trip1 Time (sec)                                                                                              |
| Ftr1A    | U/V Trip1 fraction                                                                                                |
| Vrc1A    | U/V Trip1 reclose V (pu)                                                                                          |
| Trc1A    | U/V Trip1 reclose Time (sec)                                                                                      |
| Vtr2A    | U/V Trip2 V (pu)                                                                                                  |
| Ttr2A    | U/V Trip2 Time (sec)                                                                                              |
| Ftrt2A   | U/V Trip2 fraction                                                                                                |
| Vrc2A    | U/V Trip2 reclose V (pu)                                                                                          |
| Trc2A    | U/V Trip2 reclose Time (sec)                                                                                      |
| MtypB    | Motor type                                                                                                        |
| LFmB     | Loading factor (MW/MVA rating)                                                                                    |
| RaB      | Stator resistance                                                                                                 |
| LsB      | Synchronous reactance                                                                                             |
| LpB      | Transient reactance                                                                                               |
| LppB     | Sub-transient reactance                                                                                           |
| TpoB     | Transient open circuit time constant                                                                              |
| TppoB    | Sub-transient open circuit time constant                                                                          |
| HB       | Inertia constant                                                                                                  |
| etrqB    | Torque speed exponent                                                                                             |
| Vtr1B    | U/V Trip1 V (pu)                                                                                                  |
| Ttr1B    | U/V Trip1 Time (sec)                                                                                              |
| Ftr1B    | U/V Trip1 fraction                                                                                                |
| Vrc1B    | U/V Trip1 reclose V (pu)                                                                                          |
| Trc1B    | U/V Trip1 reclose Time (sec)                                                                                      |
| Vtr2B    | U/V Trip2 V (pu)                                                                                                  |
| Ttr2B    | U/V Trip2 Time (sec)                                                                                              |
| Ftrt2B   | U/V Trip2 fraction                                                                                                |
| Vrc2B    | U/V Trip2 reclose V (pu)                                                                                          |
| Trc2B    | U/V Trip2 reclose Time (sec)                                                                                      |
| MtypC    | Motor type                                                                                                        |
| LFmC     | Loading factor (MW/MVA rating)                                                                                    |
| RaC      | Stator resistance                                                                                                 |
| LsC      | Synchronous reactance                                                                                             |
| LpC      | Transient reactance                                                                                               |
| LppC     | Sub-transient reactance                                                                                           |
| TpoC     | Transient open circuit time constant                                                                              |
| TppoC    | Sub-transient open circuit time constant                                                                          |
| HC       | Inertia constant                                                                                                  |
| etrqC    | Torque speed exponent                                                                                             |
| Vtr1C    | U/V Trip1 V (pu)                                                                                                  |
| Ttr1C    | U/V Trip1 Time (sec)                                                                                              |
| Ftr1C    | U/V Trip1 fraction                                                                                                |
| Vrc1C    | U/V Trip1 reclose V (pu)                                                                                          |
| Trc1C    | U/V Trip1 reclose Time (sec)                                                                                      |
| Vtr2C    | U/V Trip2 V (pu)                                                                                                  |
| Ttr2C    | U/V Trip2 Time (sec)                                                                                              |
| Ftrt2C   | U/V Trip2 fraction                                                                                                |
| Vrc2C    | U/V Trip2 reclose V (pu)                                                                                          |
| Trc2C    | U/V Trip2 reclose Time (sec)                                                                                      |
| Tstall   | stall delay (sec)g                                                                                                |
| Trestart | restart delay (sec)                                                                                               |
| Tv       | voltage input time constant(sec)                                                                                  |
| Tf       | frequency input time constant(sec)                                                                                |
| CompLF   | compressor load factor, pu of rated powerh                                                                        |
| CompPF   | compressor power factor at 1.0 pu voltage                                                                         |
| Vstall   | compressor stall voltage at base condition (pu)                                                                   |
| Rstall   | compressor motor res. with 1.0 pu currenti                                                                        |
| Xstall   | compressor motor stall reactance - unsat.                                                                         |
| LFadj    | Load factor adjustment to the stall voltagej                                                                      |
| Kp1      | real power constant for running state 1k                                                                          |
| Np1      | real power exponent for running state 1                                                                           |
| Kq1      | reactive power constant for running state 1                                                                       |
| Nq1      | reactive power exponent for running state 1                                                                       |
| Kp2      | real power constant for running state 2                                                                           |
| Np2      | real power exponent for running state 2                                                                           |
| Kq2      | reactive power constant for running state 2                                                                       |
| Nq2      | reactive power exponent for running state 2                                                                       |
| Vbrk     | compressor motor "breakdown" voltage (pu)                                                                         |
| Frst     | fraction of motors capable of restart                                                                             |
| Vrst     | voltage at which motors can restart (pu)                                                                          |
| CmpKpf   | real power constant for freq dependencyl                                                                          |
| CmpKqf   | reactive power constnt for freq dependency                                                                        |
| Vc1off   | Voltage 1 at which contactors start dropping out (pu)                                                             |
| Vc2off   | Voltage 2 at which all contactors drop out (pu)                                                                   |
| Vc1on    | Voltage 1 at which all contactors reclose (pu)                                                                    |
| Vc2on    | Voltage 2 at which contactors start reclosing (pu)                                                                |
| Tth      | compressor motor heating time constant(sec)m                                                                      |
| Th1t     | temp at which comp. motor begin tripping                                                                          |
| Th2t     | temp at which comp. all motors are tripped                                                                        |
| Fuvr     | fraction of comp. motors with U/V relays                                                                          |
| UVtr1    | 1st voltage pick-up (pu)                                                                                          |
| Ttr1     | 1st definite time voltage pickup (sec)                                                                            |
| UVtr2    | 2nd voltage pick-up (pu)                                                                                          |
| Ttr2     | 2nd definite time voltage                                                                                         |
| Frcel    | Fraction of eletronic load that can restart                                                                       |

---

<a id="cmpldw"></a>

## CMPLDW

*Source: [`Content/TransientModels_HTML/Load Characteristic CMPLDW.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CMPLDW.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Vmax \< Vmin then swap the values. If Vmax \< 0 then Vmax change sign to positive. Also if Vmin \< 0.96 then Vmin = 0.96; and also if Vmax \< 0.96 then Vmax = 0.96
  - Mtypa, Mtypb, Mtypc and Mtypd: Must be either 1 or 3. This is an error and do not autocorrect the values.
  - FmA, FmB, FmC, FmD and Fel: Summation of (FmA + FmB + FmC + FmD + Fel) must be less or equal than 1.0, and if not then the values will be normalized so that sum equals 1.0.
  - For Motor Type 1 Motors (LD1PAC):
      - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
      - If 0.0 \< Tth \< 0.5\*Mult\*TimeStep then Tth = 0, ElseIf 0.5\*Mult\*TimeStep \< Tth \< Mult\*TimeStep then Tth = Mult\*TimeStep
      - If 0.0 \< Frst \< 0.5\*Mult\*TimeStep then Frst = 0, ElseIf 0.5\*Mult\*TimeStep \< Frst \< Mult\*TimeStep then Frst = Mult\*TimeStep
      - If 0.0 \< CompPF \< 0.01\*Mult\*TimeStep then CompPF = 0.0  
        ElseIf 0.01\*Mult\*TimeStep \< CompPF \< Mult\*TimeStep then CompPF = Mult\*TimeStep
  - For Motor Type 3 Motors (*MOTOR\_CMP*):
      - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
      - If H \< 0.01 then H = 0.01.
      - If Lp \> 0.4\*Ls then Lp = 0.4\*Ls
      - If Lpp \> Lp then Lpp = Lp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Load Characteristic CMPLDW 0001](images/Load_Characteristic_CMPLDW_0001.svg)

**Parameters:**

|                |                                                                                                                                                                                                                                                                                                          |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mbase          | Mbase: Determines how the distribution equivalent MVABase is calculated for loads. Mbase\>0 means DistMVABase = Mbase; Mbase\<0 means DistMVABase = LoadMW/abs(Mbase); Mbase=0 means DistMVABase = LoadMW/0.8; Each load record can override this by specifying the TSDistEquivMVABase directly as well. |
| Bss            | Bss: Substation shunt capacitor susceptance, p.u.                                                                                                                                                                                                                                                        |
| Rfdr           | Rfdr: Feeder equivalent resistance, p.u.                                                                                                                                                                                                                                                                 |
| Xfdr           | Xfdr: Feeder equivalent reactance, p.u.                                                                                                                                                                                                                                                                  |
| Fb             | Fb: Fraction of feeder shunt capacitance at substation bus end                                                                                                                                                                                                                                           |
| Xxf            | Xxf: Substation transformer reactance, p.u.                                                                                                                                                                                                                                                              |
| Tfixhs         | Tfixhs: Transformer high side fixed tap, p.u.                                                                                                                                                                                                                                                            |
| Tfixls         | Tfixls: Transformer low side fixed tap, p.u.                                                                                                                                                                                                                                                             |
| LTC            | LTC: 1 for automatic tap adjustment (low side variable tap)                                                                                                                                                                                                                                              |
| Tmin           | Tmin: Minimum variable tap, p.u.                                                                                                                                                                                                                                                                         |
| Tmax           | Tmax: Maximum variable tap, p.u.                                                                                                                                                                                                                                                                         |
| step           | step: Variable tap step size, p.u.                                                                                                                                                                                                                                                                       |
| Vmin           | Vmin: Minimum low-side voltage, p.u.                                                                                                                                                                                                                                                                     |
| Vmax           | Vmax: Maximum low-side voltage, p.u.                                                                                                                                                                                                                                                                     |
| Tdel           | Tdel: Time delay to initiate tap adjustment, sec.                                                                                                                                                                                                                                                        |
| Tdelstep       | Tdelstep: Time delay between tap steps, sec.                                                                                                                                                                                                                                                             |
| Rcmp           | Rcmp: Transformer LTC compensating resistance, p.u.                                                                                                                                                                                                                                                      |
| Xcmp           | Xcmp: Transformer LTC compensating reactance, p.u.                                                                                                                                                                                                                                                       |
| FmA            | FmA: Motor A fraction of load P                                                                                                                                                                                                                                                                          |
| FmB            | FmB: Motor B fraction of load P                                                                                                                                                                                                                                                                          |
| FmC            | FmC: Motor C fraction of load P                                                                                                                                                                                                                                                                          |
| FmD            | FmD: Motor D fraction of load P                                                                                                                                                                                                                                                                          |
| Fel            | Fel: Electronic load fraction of load P                                                                                                                                                                                                                                                                  |
| PFel           | PFel: Electronic load power factor                                                                                                                                                                                                                                                                       |
| Vd1            | Vd1: Voltage below which electronic load decreases, p.u.                                                                                                                                                                                                                                                 |
| Vd2            | Vd2: Voltage below which electronic load is zero, p.u.                                                                                                                                                                                                                                                   |
| frcel          | frcel : Fraction of electronic load that recovers from low voltage trip                                                                                                                                                                                                                                  |
| PFs            | PFs: Power factor of static load component                                                                                                                                                                                                                                                               |
| P1e            | P1e: Static load – exponent of first P term                                                                                                                                                                                                                                                              |
| P1c            | P1c: Static load – coefficient of first P term                                                                                                                                                                                                                                                           |
| P2e            | P2e: Static load – exponent of second P term                                                                                                                                                                                                                                                             |
| P2c            | P2c: Static load – coefficient of second P term                                                                                                                                                                                                                                                          |
| Pfrq           | Pfrq: Frequency sensitivity factor for P                                                                                                                                                                                                                                                                 |
| Q1e            | Q1e: Static load – exponent of first Q term                                                                                                                                                                                                                                                              |
| Q1c            | Q1c: Static load – coefficient of first Q term                                                                                                                                                                                                                                                           |
| Q2e            | Q2e: Static load – exponent of second Q term                                                                                                                                                                                                                                                             |
| Q2c            | Q2c: Static load – coefficient of second Q term                                                                                                                                                                                                                                                          |
| Qfrq           | Qfrq: Frequency sensitivity factor for Q                                                                                                                                                                                                                                                                 |
| Mtypa          | Mtypa: Motor A type                                                                                                                                                                                                                                                                                      |
| Mtypb          | Mtypb: Motor B type                                                                                                                                                                                                                                                                                      |
| Mtypc          | Mtypc: Motor C type                                                                                                                                                                                                                                                                                      |
| Mtypd          | Mtypd: Motor D type                                                                                                                                                                                                                                                                                      |
| LFma           | (Type 3) LFma: Motor loading factor, (Type 1) LFma: Motor loading factor                                                                                                                                                                                                                                 |
| Rsa\_CompPFa   | (Type 3) Rsa: Stator resistance, p.u., (Type 1) CompPFa: Power Factor                                                                                                                                                                                                                                    |
| Lsa\_Vstalla   | (Type 3) Lsa: Synchronous reactance, p.u., (Type 1) Vstalla: Stall voltage, p.u.                                                                                                                                                                                                                         |
| Lpa\_Rstalla   | (Type 3) Lpa: Transient reactance, p.u., (Type 1) Rstalla: Stall resistance, p.u.                                                                                                                                                                                                                        |
| Lppa\_Xstalla  | (Type 3) Lppa: Subtransient reactance, p.u., (Type 1) Xstalla: Stall reactance, p.u.                                                                                                                                                                                                                     |
| Tpoa\_Tstalla  | (Type 3) Tpoa: Transient open circuit time constant, sec., (Type 1) Tstalla: Stall time delay, sec.                                                                                                                                                                                                      |
| Tppoa\_Frsta   | (Type 3) Tppoa: Subtransient open circuit time constant, sec., (Type 1) Frsta: Fraction of load that can restart after stalling                                                                                                                                                                          |
| Ha\_Vrsta      | (Type 3) Ha: Inertia constant, sec., (Type 1) Vrsta: Voltage at which restart can occur, p.u.                                                                                                                                                                                                            |
| Etrqa\_Trsta   | (Type 3) Etrqa: Mechanical torque exponent, (Type 1) Trsta: Restart time delay, sec.                                                                                                                                                                                                                     |
| Vtr1a\_Fuvra   | (Type 3) Vtr1a: First low voltage trip level, p.u. V, (Type 1) Fuvra: Fraction of load with undervoltage relay protection                                                                                                                                                                                |
| Ttr1a\_Vtr1a   | (Type 3) Ttr1a: First low voltage trip delay time, sec., (Type 1) Vtr1a: First undervoltage trip level, p.u.                                                                                                                                                                                             |
| Ftr1a\_TTr1a   | (Type 3) Ftr1a: First low voltage trip fraction, (Type 1) Ttr1a: First undervoltage trip delay time, sec.                                                                                                                                                                                                |
| Vrc1a\_Vtr2a   | (Type 3) Vrc1a: First low voltage reconnection level, p.u. V, (Type 1) Vtr2a: Second undervoltage trip level, p.u.                                                                                                                                                                                       |
| Trc1a\_Ttr2a   | (Type 3) Trc1a: First low voltage reconnection delay time, sec., (Type 1) Ttr2a: Second undervoltage trip delay time, sec.                                                                                                                                                                               |
| Vtr2a\_Vc1offa | (Type 3) Vtr2a: Second low voltage trip level, p.u. V, (Type 1) Vc1offa: Contactor voltage at which tripping starts, p.u.                                                                                                                                                                                |
| Ttr2a\_Vc2offa | (Type 3) Ttr2a: Second low voltage trip delay time, sec., (Type 1) Vc2offa: Contactor voltage at which tripping is complete, p.u.                                                                                                                                                                        |
| Ftr2a\_Vc1ona  | (Type 3) Ftr2a: Second low voltage trip fraction, (Type 1) Vc1ona: Contactor voltage at which reconnection is complete, p.u.                                                                                                                                                                             |
| Vrc2a\_Vc2ona  | (Type 3) Vrc2a: Second low voltage reconnection level, p.u. V, (Type 1) Vc2ona: Contactor voltage at which reconnection starts, p.u.                                                                                                                                                                     |
| Trc2a\_Ttha    | (Type 3) Trc2a: Second low voltage reconnection time delay, sec., (Type 1) Ttha: Thermal time constant, sec.                                                                                                                                                                                             |
| Th1ta          | (Type 1) Th1ta: Thermal protection trip start level, p.u. temperature                                                                                                                                                                                                                                    |
| Th2ta          | (Type 1) Th2ta: Thermal protection trip completion level, p.u. temperature                                                                                                                                                                                                                               |
| Tva            | (Type 1) Tva: Voltage measurement lag, sec.                                                                                                                                                                                                                                                              |
| LFmb           | (Type 3) LFmb: Motor loading factor, (Type 1) LFmb: Motor loading factor                                                                                                                                                                                                                                 |
| Rsb\_CompPFb   | (Type 3) Rsb: Stator resistance, p.u., (Type 1) CompPFb: Power Factor                                                                                                                                                                                                                                    |
| Lsb\_Vstallb   | (Type 3) Lsb: Synchronous reactance, p.u., (Type 1) Vstallb: Stall voltage, p.u.                                                                                                                                                                                                                         |
| Lpb\_Rstallb   | (Type 3) Lpb: Transient reactance, p.u., (Type 1) Rstallb: Stall resistance, p.u.                                                                                                                                                                                                                        |
| Lppb\_Xstallb  | (Type 3) Lppb: Subtransient reactance, p.u., (Type 1) Xstallb: Stall reactance, p.u.                                                                                                                                                                                                                     |
| Tpob\_Tstallb  | (Type 3) Tpob: Transient open circuit time constant, sec., (Type 1) Tstallb: Stall time delay, sec.                                                                                                                                                                                                      |
| Tppob\_Frstb   | (Type 3) Tppob: Subtransient open circuit time constant, sec., (Type 1) Frstb: Fraction of load that can restart after stalling                                                                                                                                                                          |
| Hb\_Vrstb      | (Type 3) Hb: Inertia constant, sec., (Type 1) Vrstb: Voltage at which restart can occur, p.u.                                                                                                                                                                                                            |
| Etrqb\_Trstb   | (Type 3) Etrqb: Mechanical torque exponent, (Type 1) Trstb: Restart time delay, sec.                                                                                                                                                                                                                     |
| Vtr1b\_Fuvrb   | (Type 3) Vtr1b: First low voltage trip level, p.u. V, (Type 1) Fuvrb: Fraction of load with undervoltage relay protection                                                                                                                                                                                |
| Ttr1b\_Vtr1b   | (Type 3) Ttr1b: First low voltage trip delay time, sec., (Type 1) Vtr1b: First undervoltage trip level, p.u.                                                                                                                                                                                             |
| Ftr1b\_TTr1b   | (Type 3) Ftr1b: First low voltage trip fraction, (Type 1) Ttr1b: First undervoltage trip delay time, sec.                                                                                                                                                                                                |
| Vrc1b\_Vtr2b   | (Type 3) Vrc1b: First low voltage reconnection level, p.u. V, (Type 1) Vtr2b: Second undervoltage trip level, p.u.                                                                                                                                                                                       |
| Trc1b\_Ttr2b   | (Type 3) Trc1b: First low voltage reconnection delay time, sec., (Type 1) Ttr2b: Second undervoltage trip delay time, sec.                                                                                                                                                                               |
| Vtr2b\_Vc1offb | (Type 3) Vtr2b: Second low voltage trip level, p.u. V, (Type 1) Vc1offb: Contactor voltage at which tripping starts, p.u.                                                                                                                                                                                |
| Ttr2b\_Vc2offb | (Type 3) Ttr2b: Second low voltage trip delay time, sec., (Type 1) Vc2offb: Contactor voltage at which tripping is complete, p.u.                                                                                                                                                                        |
| Ftr2b\_Vc1onb  | (Type 3) Ftr2b: Second low voltage trip fraction, (Type 1) Vc1onb: Contactor voltage at which reconnection is complete, p.u.                                                                                                                                                                             |
| Vrc2b\_Vc2onb  | (Type 3) Vrc2b: Second low voltage reconnection level, p.u. V, (Type 1) Vc2onb: Contactor voltage at which reconnection starts, p.u.                                                                                                                                                                     |
| Trc2b\_Tthb    | (Type 3) Trc2b: Second low voltage reconnection time delay, sec., (Type 1) Tthb: Thermal time constant, sec.                                                                                                                                                                                             |
| Th1tb          | (Type 1) Th1tb: Thermal protection trip start level, p.u. temperature                                                                                                                                                                                                                                    |
| Th2tb          | (Type 1) Th2tb: Thermal protection trip completion level, p.u. temperature                                                                                                                                                                                                                               |
| Tvb            | (Type 1) Tvb: Voltage measurement lag, sec.                                                                                                                                                                                                                                                              |
| LFmc           | (Type 3) LFmc: Motor loading factor, (Type 1) LFmc: Motor loading factor                                                                                                                                                                                                                                 |
| Rsc\_CompPFc   | (Type 3) Rsc: Stator resistance, p.u., (Type 1) CompPFc: Power Factor                                                                                                                                                                                                                                    |
| Lsc\_Vstallc   | (Type 3) Lsc: Synchronous reactance, p.u., (Type 1) Vstallc: Stall voltage, p.u.                                                                                                                                                                                                                         |
| Lpc\_Rstallc   | (Type 3) Lpc: Transient reactance, p.u., (Type 1) Rstallc: Stall resistance, p.u.                                                                                                                                                                                                                        |
| Lppc\_Xstallc  | (Type 3) Lppc: Subtransient reactance, p.u., (Type 1) Xstallc: Stall reactance, p.u.                                                                                                                                                                                                                     |
| Tpoc\_Tstallc  | (Type 3) Tpoc: Transient open circuit time constant, sec., (Type 1) Tstallc: Stall time delay, sec.                                                                                                                                                                                                      |
| Tppoc\_Frstc   | (Type 3) Tppoc: Subtransient open circuit time constant, sec., (Type 1) Frstc: Fraction of load that can restart after stalling                                                                                                                                                                          |
| Hc\_Vrstc      | (Type 3) Hc: Inertia constant, sec., (Type 1) Vrstc: Voltage at which restart can occur, p.u.                                                                                                                                                                                                            |
| Etrqc\_Trstc   | (Type 3) Etrqc: Mechanical torque exponent, (Type 1) Trstc: Restart time delay, sec.                                                                                                                                                                                                                     |
| Vtr1c\_Fuvrc   | (Type 3) Vtr1c: First low voltage trip level, p.u. V, (Type 1) Fuvrc: Fraction of load with undervoltage relay protection                                                                                                                                                                                |
| Ttr1c\_Vtr1c   | (Type 3) Ttr1c: First low voltage trip delay time, sec., (Type 1) Vtr1c: First undervoltage trip level, p.u.                                                                                                                                                                                             |
| Ftr1c\_TTr1c   | (Type 3) Ftr1c: First low voltage trip fraction, (Type 1) Ttr1c: First undervoltage trip delay time, sec.                                                                                                                                                                                                |
| Vrc1c\_Vtr2c   | (Type 3) Vrc1c: First low voltage reconnection level, p.u. V, (Type 1) Vtr2c: Second undervoltage trip level, p.u.                                                                                                                                                                                       |
| Trc1c\_Ttr2c   | (Type 3) Trc1c: First low voltage reconnection delay time, sec., (Type 1) Ttr2c: Second undervoltage trip delay time, sec.                                                                                                                                                                               |
| Vtr2c\_Vc1offc | (Type 3) Vtr2c: Second low voltage trip level, p.u. V, (Type 1) Vc1offc: Contactor voltage at which tripping starts, p.u.                                                                                                                                                                                |
| Ttr2c\_Vc2offc | (Type 3) Ttr2c: Second low voltage trip delay time, sec., (Type 1) Vc2offc: Contactor voltage at which tripping is complete, p.u.                                                                                                                                                                        |
| Ftr2c\_Vc1onc  | (Type 3) Ftr2c: Second low voltage trip fraction, (Type 1) Vc1onc: Contactor voltage at which reconnection is complete, p.u.                                                                                                                                                                             |
| Vrc2c\_Vc2onc  | (Type 3) Vrc2c: Second low voltage reconnection level, p.u. V, (Type 1) Vc2onc: Contactor voltage at which reconnection starts, p.u.                                                                                                                                                                     |
| Trc2c\_Tthc    | (Type 3) Trc2c: Second low voltage reconnection time delay, sec., (Type 1) Tthc: Thermal time constant, sec.                                                                                                                                                                                             |
| Th1tc          | (Type 1) Th1tc: Thermal protection trip start level, p.u. temperature                                                                                                                                                                                                                                    |
| Th2tc          | (Type 1) Th2tc: Thermal protection trip completion level, p.u. temperature                                                                                                                                                                                                                               |
| Tvc            | (Type 1) Tvc: Voltage measurement lag, sec.                                                                                                                                                                                                                                                              |
| LFmd           | (Type 3) LFmd: Motor loading factor, (Type 1) LFmd: Motor loading factor                                                                                                                                                                                                                                 |
| Rsd\_CompPFd   | (Type 3) Rsd: Stator resistance, p.u., (Type 1) CompPFd: Power Factor                                                                                                                                                                                                                                    |
| Lsd\_Vstalld   | (Type 3) Lsd: Synchronous reactance, p.u., (Type 1) Vstalld: Stall voltage, p.u.                                                                                                                                                                                                                         |
| Lpd\_Rstalld   | (Type 3) Lpd: Transient reactance, p.u., (Type 1) Rstalld: Stall resistance, p.u.                                                                                                                                                                                                                        |
| Lppd\_Xstalld  | (Type 3) Lppd: Subtransient reactance, p.u., (Type 1) Xstalld: Stall reactance, p.u.                                                                                                                                                                                                                     |
| Tpod\_Tstalld  | (Type 3) Tpod: Transient open circuit time constant, sec., (Type 1) Tstalld: Stall time delay, sec.                                                                                                                                                                                                      |
| Tppod\_Frstd   | (Type 3) Tppod: Subtransient open circuit time constant, sec., (Type 1) Frstd: Fraction of load that can restart after stalling                                                                                                                                                                          |
| Hd\_Vrstd      | (Type 3) Hd: Inertia constant, sec., (Type 1) Vrstd: Voltage at which restart can occur, p.u.                                                                                                                                                                                                            |
| Etrqd\_Trstd   | (Type 3) Etrqd: Mechanical torque exponent, (Type 1) Trstd: Restart time delay, sec.                                                                                                                                                                                                                     |
| Vtr1d\_Fuvrd   | (Type 3) Vtr1d: First low voltage trip level, p.u. V, (Type 1) Fuvrd: Fraction of load with undervoltage relay protection                                                                                                                                                                                |
| Ttr1d\_Vtr1d   | (Type 3) Ttr1d: First low voltage trip delay time, sec., (Type 1) Vtr1d: First undervoltage trip level, p.u.                                                                                                                                                                                             |
| Ftr1d\_TTr1d   | (Type 3) Ftr1d: First low voltage trip fraction, (Type 1) Ttr1d: First undervoltage trip delay time, sec.                                                                                                                                                                                                |
| Vrc1d\_Vtr2d   | (Type 3) Vrc1d: First low voltage reconnection level, p.u. V, (Type 1) Vtr2d: Second undervoltage trip level, p.u.                                                                                                                                                                                       |
| Trc1d\_Ttr2d   | (Type 3) Trc1d: First low voltage reconnection delay time, sec., (Type 1) Ttr2d: Second undervoltage trip delay time, sec.                                                                                                                                                                               |
| Vtr2d\_Vc1offd | (Type 3) Vtr2d: Second low voltage trip level, p.u. V, (Type 1) Vc1offd: Contactor voltage at which tripping starts, p.u.                                                                                                                                                                                |
| Ttr2d\_Vc2offd | (Type 3) Ttr2d: Second low voltage trip delay time, sec., (Type 1) Vc2offd: Contactor voltage at which tripping is complete, p.u.                                                                                                                                                                        |
| Ftr2d\_Vc1ond  | (Type 3) Ftr2d: Second low voltage trip fraction, (Type 1) Vc1ond: Contactor voltage at which reconnection is complete, p.u.                                                                                                                                                                             |
| Vrc2d\_Vc2ond  | (Type 3) Vrc2d: Second low voltage reconnection level, p.u. V, (Type 1) Vc2ond: Contactor voltage at which reconnection starts, p.u.                                                                                                                                                                     |
| Trc2d\_Tthd    | (Type 3) Trc2d: Second low voltage reconnection time delay, sec., (Type 1) Tthd: Thermal time constant, sec.                                                                                                                                                                                             |
| Th1td          | (Type 1) Th1td: Thermal protection trip start level, p.u. temperature                                                                                                                                                                                                                                    |
| Th2td          | (Type 1) Th2td: Thermal protection trip completion level, p.u. temperature                                                                                                                                                                                                                               |
| Tvd            | (Type 1) Tvd: Voltage measurement lag, sec.                                                                                                                                                                                                                                                              |

![Load Characteristic CMPLDW 0002](images/Load_Characteristic_CMPLDW_0002.svg)

![Load Characteristic CMPLDW 0003](images/Load_Characteristic_CMPLDW_0003.svg)

---

<a id="cmpldwnf"></a>

## CMPLDWNF

*Source: [`Content/TransientModels_HTML/Load Characteristic CMPLDWNF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic CMPLDWNF.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Mtypa, Mtypb, Mtypc and Mtypd: Must be either 1 or 3. This is an error and do not autocorrect the values.
  - FmA, FmB, FmC, FmD and Fel: Summation of (FmA + FmB + FmC + FmD + Fel) must be less or equal than 1.0, and if not then the values will be normalized so that sum equals 1.0.
  - For Motor Type 1 Motors (LD1PAC):
      - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
      - If 0.0 \< Tth \< 0.5\*Mult\*TimeStep then Tth = 0, ElseIf 0.5\*Mult\*TimeStep \< Tth \< Mult\*TimeStep then Tth = Mult\*TimeStep
      - If 0.0 \< Frst \< 0.5\*Mult\*TimeStep then Frst = 0, ElseIf 0.5\*Mult\*TimeStep \< Frst \< Mult\*TimeStep then Frst = Mult\*TimeStep
      - If 0.0 \< CompPF \< 0.01\*Mult\*TimeStep then CompPF = 0.0  
        ElseIf 0.01\*Mult\*TimeStep \< CompPF \< Mult\*TimeStep then CompPF = Mult\*TimeStep
  - For Motor Type 3 Motors (*MOTOR\_CMP*):
      - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
      - If H \< 0.01 then H = 0.01.
      - If Lp \> 0.4\*Ls then Lp = 0.4\*Ls
      - If Lpp \> Lp then Lpp = Lp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-This represents a load model identical to the CMPLDW model, except that all the parameters related to the Distribution Equivalent have been removed (the first 17 parameters of CMPLDW and the MVABase).

**Parameters:**

|                |                                                                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| FmA            | FmA: Motor A fraction of load P                                                                                                      |
| FmB            | FmB: Motor B fraction of load P                                                                                                      |
| FmC            | FmC: Motor C fraction of load P                                                                                                      |
| FmD            | FmD: Motor D fraction of load P                                                                                                      |
| Fel            | Fel: Electronic load fraction of load P                                                                                              |
| PFel           | PFel: Electronic load power factor                                                                                                   |
| Vd1            | Vd1: Voltage below which electronic load decreases, p.u.                                                                             |
| Vd2            | Vd2: Voltage below which electronic load is zero, p.u.                                                                               |
| frcel          | frcel : Fraction of electronic load that recovers from low voltage trip                                                              |
| PFs            | PFs: Power factor of static load component                                                                                           |
| P1e            | P1e: Static load – exponent of first P term                                                                                          |
| P1c            | P1c: Static load – coefficient of first P term                                                                                       |
| P2e            | P2e: Static load – exponent of second P term                                                                                         |
| P2c            | P2c: Static load – coefficient of second P term                                                                                      |
| Pfrq           | Pfrq: Frequency sensitivity factor for P                                                                                             |
| Q1e            | Q1e: Static load – exponent of first Q term                                                                                          |
| Q1c            | Q1c: Static load – coefficient of first Q term                                                                                       |
| Q2e            | Q2e: Static load – exponent of second Q term                                                                                         |
| Q2c            | Q2c: Static load – coefficient of second Q term                                                                                      |
| Qfrq           | Qfrq: Frequency sensitivity factor for Q                                                                                             |
| Mtypa          | Mtypa: Motor A type                                                                                                                  |
| Mtypb          | Mtypb: Motor B type                                                                                                                  |
| Mtypc          | Mtypc: Motor C type                                                                                                                  |
| Mtypd          | Mtypd: Motor D type                                                                                                                  |
| LFma           | (Type 3) LFma: Motor loading factor, (Type 1) LFma: Motor loading factor                                                             |
| Rsa\_CompPFa   | (Type 3) Rsa: Stator resistance, p.u., (Type 1) CompPFa: Power Factor                                                                |
| Lsa\_Vstalla   | (Type 3) Lsa: Synchronous reactance, p.u., (Type 1) Vstalla: Stall voltage, p.u.                                                     |
| Lpa\_Rstalla   | (Type 3) Lpa: Transient reactance, p.u., (Type 1) Rstalla: Stall resistance, p.u.                                                    |
| Lppa\_Xstalla  | (Type 3) Lppa: Subtransient reactance, p.u., (Type 1) Xstalla: Stall reactance, p.u.                                                 |
| Tpoa\_Tstalla  | (Type 3) Tpoa: Transient open circuit time constant, sec., (Type 1) Tstalla: Stall time delay, sec.                                  |
| Tppoa\_Frsta   | (Type 3) Tppoa: Subtransient open circuit time constant, sec., (Type 1) Frsta: Fraction of load that can restart after stalling      |
| Ha\_Vrsta      | (Type 3) Ha: Inertia constant, sec., (Type 1) Vrsta: Voltage at which restart can occur, p.u.                                        |
| Etrqa\_Trsta   | (Type 3) Etrqa: Mechanical torque exponent, (Type 1) Trsta: Restart time delay, sec.                                                 |
| Vtr1a\_Fuvra   | (Type 3) Vtr1a: First low voltage trip level, p.u. V, (Type 1) Fuvra: Fraction of load with undervoltage relay protection            |
| Ttr1a\_Vtr1a   | (Type 3) Ttr1a: First low voltage trip delay time, sec., (Type 1) Vtr1a: First undervoltage trip level, p.u.                         |
| Ftr1a\_TTr1a   | (Type 3) Ftr1a: First low voltage trip fraction, (Type 1) Ttr1a: First undervoltage trip delay time, sec.                            |
| Vrc1a\_Vtr2a   | (Type 3) Vrc1a: First low voltage reconnection level, p.u. V, (Type 1) Vtr2a: Second undervoltage trip level, p.u.                   |
| Trc1a\_Ttr2a   | (Type 3) Trc1a: First low voltage reconnection delay time, sec., (Type 1) Ttr2a: Second undervoltage trip delay time, sec.           |
| Vtr2a\_Vc1offa | (Type 3) Vtr2a: Second low voltage trip level, p.u. V, (Type 1) Vc1offa: Contactor voltage at which tripping starts, p.u.            |
| Ttr2a\_Vc2offa | (Type 3) Ttr2a: Second low voltage trip delay time, sec., (Type 1) Vc2offa: Contactor voltage at which tripping is complete, p.u.    |
| Ftr2a\_Vc1ona  | (Type 3) Ftr2a: Second low voltage trip fraction, (Type 1) Vc1ona: Contactor voltage at which reconnection is complete, p.u.         |
| Vrc2a\_Vc2ona  | (Type 3) Vrc2a: Second low voltage reconnection level, p.u. V, (Type 1) Vc2ona: Contactor voltage at which reconnection starts, p.u. |
| Trc2a\_Ttha    | (Type 3) Trc2a: Second low voltage reconnection time delay, sec., (Type 1) Ttha: Thermal time constant, sec.                         |
| Th1ta          | (Type 1) Th1ta: Thermal protection trip start level, p.u. temperature                                                                |
| Th2ta          | (Type 1) Th2ta: Thermal protection trip completion level, p.u. temperature                                                           |
| Tva            | (Type 1) Tva: Voltage measurement lag, sec.                                                                                          |
| LFmb           | (Type 3) LFmb: Motor loading factor, (Type 1) LFmb: Motor loading factor                                                             |
| Rsb\_CompPFb   | (Type 3) Rsb: Stator resistance, p.u., (Type 1) CompPFb: Power Factor                                                                |
| Lsb\_Vstallb   | (Type 3) Lsb: Synchronous reactance, p.u., (Type 1) Vstallb: Stall voltage, p.u.                                                     |
| Lpb\_Rstallb   | (Type 3) Lpb: Transient reactance, p.u., (Type 1) Rstallb: Stall resistance, p.u.                                                    |
| Lppb\_Xstallb  | (Type 3) Lppb: Subtransient reactance, p.u., (Type 1) Xstallb: Stall reactance, p.u.                                                 |
| Tpob\_Tstallb  | (Type 3) Tpob: Transient open circuit time constant, sec., (Type 1) Tstallb: Stall time delay, sec.                                  |
| Tppob\_Frstb   | (Type 3) Tppob: Subtransient open circuit time constant, sec., (Type 1) Frstb: Fraction of load that can restart after stalling      |
| Hb\_Vrstb      | (Type 3) Hb: Inertia constant, sec., (Type 1) Vrstb: Voltage at which restart can occur, p.u.                                        |
| Etrqb\_Trstb   | (Type 3) Etrqb: Mechanical torque exponent, (Type 1) Trstb: Restart time delay, sec.                                                 |
| Vtr1b\_Fuvrb   | (Type 3) Vtr1b: First low voltage trip level, p.u. V, (Type 1) Fuvrb: Fraction of load with undervoltage relay protection            |
| Ttr1b\_Vtr1b   | (Type 3) Ttr1b: First low voltage trip delay time, sec., (Type 1) Vtr1b: First undervoltage trip level, p.u.                         |
| Ftr1b\_TTr1b   | (Type 3) Ftr1b: First low voltage trip fraction, (Type 1) Ttr1b: First undervoltage trip delay time, sec.                            |
| Vrc1b\_Vtr2b   | (Type 3) Vrc1b: First low voltage reconnection level, p.u. V, (Type 1) Vtr2b: Second undervoltage trip level, p.u.                   |
| Trc1b\_Ttr2b   | (Type 3) Trc1b: First low voltage reconnection delay time, sec., (Type 1) Ttr2b: Second undervoltage trip delay time, sec.           |
| Vtr2b\_Vc1offb | (Type 3) Vtr2b: Second low voltage trip level, p.u. V, (Type 1) Vc1offb: Contactor voltage at which tripping starts, p.u.            |
| Ttr2b\_Vc2offb | (Type 3) Ttr2b: Second low voltage trip delay time, sec., (Type 1) Vc2offb: Contactor voltage at which tripping is complete, p.u.    |
| Ftr2b\_Vc1onb  | (Type 3) Ftr2b: Second low voltage trip fraction, (Type 1) Vc1onb: Contactor voltage at which reconnection is complete, p.u.         |
| Vrc2b\_Vc2onb  | (Type 3) Vrc2b: Second low voltage reconnection level, p.u. V, (Type 1) Vc2onb: Contactor voltage at which reconnection starts, p.u. |
| Trc2b\_Tthb    | (Type 3) Trc2b: Second low voltage reconnection time delay, sec., (Type 1) Tthb: Thermal time constant, sec.                         |
| Th1tb          | (Type 1) Th1tb: Thermal protection trip start level, p.u. temperature                                                                |
| Th2tb          | (Type 1) Th2tb: Thermal protection trip completion level, p.u. temperature                                                           |
| Tvb            | (Type 1) Tvb: Voltage measurement lag, sec.                                                                                          |
| LFmc           | (Type 3) LFmc: Motor loading factor, (Type 1) LFmc: Motor loading factor                                                             |
| Rsc\_CompPFc   | (Type 3) Rsc: Stator resistance, p.u., (Type 1) CompPFc: Power Factor                                                                |
| Lsc\_Vstallc   | (Type 3) Lsc: Synchronous reactance, p.u., (Type 1) Vstallc: Stall voltage, p.u.                                                     |
| Lpc\_Rstallc   | (Type 3) Lpc: Transient reactance, p.u., (Type 1) Rstallc: Stall resistance, p.u.                                                    |
| Lppc\_Xstallc  | (Type 3) Lppc: Subtransient reactance, p.u., (Type 1) Xstallc: Stall reactance, p.u.                                                 |
| Tpoc\_Tstallc  | (Type 3) Tpoc: Transient open circuit time constant, sec., (Type 1) Tstallc: Stall time delay, sec.                                  |
| Tppoc\_Frstc   | (Type 3) Tppoc: Subtransient open circuit time constant, sec., (Type 1) Frstc: Fraction of load that can restart after stalling      |
| Hc\_Vrstc      | (Type 3) Hc: Inertia constant, sec., (Type 1) Vrstc: Voltage at which restart can occur, p.u.                                        |
| Etrqc\_Trstc   | (Type 3) Etrqc: Mechanical torque exponent, (Type 1) Trstc: Restart time delay, sec.                                                 |
| Vtr1c\_Fuvrc   | (Type 3) Vtr1c: First low voltage trip level, p.u. V, (Type 1) Fuvrc: Fraction of load with undervoltage relay protection            |
| Ttr1c\_Vtr1c   | (Type 3) Ttr1c: First low voltage trip delay time, sec., (Type 1) Vtr1c: First undervoltage trip level, p.u.                         |
| Ftr1c\_TTr1c   | (Type 3) Ftr1c: First low voltage trip fraction, (Type 1) Ttr1c: First undervoltage trip delay time, sec.                            |
| Vrc1c\_Vtr2c   | (Type 3) Vrc1c: First low voltage reconnection level, p.u. V, (Type 1) Vtr2c: Second undervoltage trip level, p.u.                   |
| Trc1c\_Ttr2c   | (Type 3) Trc1c: First low voltage reconnection delay time, sec., (Type 1) Ttr2c: Second undervoltage trip delay time, sec.           |
| Vtr2c\_Vc1offc | (Type 3) Vtr2c: Second low voltage trip level, p.u. V, (Type 1) Vc1offc: Contactor voltage at which tripping starts, p.u.            |
| Ttr2c\_Vc2offc | (Type 3) Ttr2c: Second low voltage trip delay time, sec., (Type 1) Vc2offc: Contactor voltage at which tripping is complete, p.u.    |
| Ftr2c\_Vc1onc  | (Type 3) Ftr2c: Second low voltage trip fraction, (Type 1) Vc1onc: Contactor voltage at which reconnection is complete, p.u.         |
| Vrc2c\_Vc2onc  | (Type 3) Vrc2c: Second low voltage reconnection level, p.u. V, (Type 1) Vc2onc: Contactor voltage at which reconnection starts, p.u. |
| Trc2c\_Tthc    | (Type 3) Trc2c: Second low voltage reconnection time delay, sec., (Type 1) Tthc: Thermal time constant, sec.                         |
| Th1tc          | (Type 1) Th1tc: Thermal protection trip start level, p.u. temperature                                                                |
| Th2tc          | (Type 1) Th2tc: Thermal protection trip completion level, p.u. temperature                                                           |
| Tvc            | (Type 1) Tvc: Voltage measurement lag, sec.                                                                                          |
| LFmd           | (Type 3) LFmd: Motor loading factor, (Type 1) LFmd: Motor loading factor                                                             |
| Rsd\_CompPFd   | (Type 3) Rsd: Stator resistance, p.u., (Type 1) CompPFd: Power Factor                                                                |
| Lsd\_Vstalld   | (Type 3) Lsd: Synchronous reactance, p.u., (Type 1) Vstalld: Stall voltage, p.u.                                                     |
| Lpd\_Rstalld   | (Type 3) Lpd: Transient reactance, p.u., (Type 1) Rstalld: Stall resistance, p.u.                                                    |
| Lppd\_Xstalld  | (Type 3) Lppd: Subtransient reactance, p.u., (Type 1) Xstalld: Stall reactance, p.u.                                                 |
| Tpod\_Tstalld  | (Type 3) Tpod: Transient open circuit time constant, sec., (Type 1) Tstalld: Stall time delay, sec.                                  |
| Tppod\_Frstd   | (Type 3) Tppod: Subtransient open circuit time constant, sec., (Type 1) Frstd: Fraction of load that can restart after stalling      |
| Hd\_Vrstd      | (Type 3) Hd: Inertia constant, sec., (Type 1) Vrstd: Voltage at which restart can occur, p.u.                                        |
| Etrqd\_Trstd   | (Type 3) Etrqd: Mechanical torque exponent, (Type 1) Trstd: Restart time delay, sec.                                                 |
| Vtr1d\_Fuvrd   | (Type 3) Vtr1d: First low voltage trip level, p.u. V, (Type 1) Fuvrd: Fraction of load with undervoltage relay protection            |
| Ttr1d\_Vtr1d   | (Type 3) Ttr1d: First low voltage trip delay time, sec., (Type 1) Vtr1d: First undervoltage trip level, p.u.                         |
| Ftr1d\_TTr1d   | (Type 3) Ftr1d: First low voltage trip fraction, (Type 1) Ttr1d: First undervoltage trip delay time, sec.                            |
| Vrc1d\_Vtr2d   | (Type 3) Vrc1d: First low voltage reconnection level, p.u. V, (Type 1) Vtr2d: Second undervoltage trip level, p.u.                   |
| Trc1d\_Ttr2d   | (Type 3) Trc1d: First low voltage reconnection delay time, sec., (Type 1) Ttr2d: Second undervoltage trip delay time, sec.           |
| Vtr2d\_Vc1offd | (Type 3) Vtr2d: Second low voltage trip level, p.u. V, (Type 1) Vc1offd: Contactor voltage at which tripping starts, p.u.            |
| Ttr2d\_Vc2offd | (Type 3) Ttr2d: Second low voltage trip delay time, sec., (Type 1) Vc2offd: Contactor voltage at which tripping is complete, p.u.    |
| Ftr2d\_Vc1ond  | (Type 3) Ftr2d: Second low voltage trip fraction, (Type 1) Vc1ond: Contactor voltage at which reconnection is complete, p.u.         |
| Vrc2d\_Vc2ond  | (Type 3) Vrc2d: Second low voltage reconnection level, p.u. V, (Type 1) Vc2ond: Contactor voltage at which reconnection starts, p.u. |
| Trc2d\_Tthd    | (Type 3) Trc2d: Second low voltage reconnection time delay, sec., (Type 1) Tthd: Thermal time constant, sec.                         |
| Th1td          | (Type 1) Th1td: Thermal protection trip start level, p.u. temperature                                                                |
| Th2td          | (Type 1) Th2td: Thermal protection trip completion level, p.u. temperature                                                           |
| Tvd            | (Type 1) Tvd: Voltage measurement lag, sec.                                                                                          |

---

<a id="dlight"></a>

## DLIGHT

*Source: [`Content/TransientModels_HTML/Load Characteristic DLIGHT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic DLIGHT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|        |                            |
| ------ | -------------------------- |
| Pcoeff | Real Power Coefficient     |
| Qcoeff | Reactive Power Coefficient |
| Vbreak | Breakpoint Voltage         |
| Vext   | Extinction Voltage         |

---

<a id="extl"></a>

## EXTL

*Source: [`Content/TransientModels_HTML/Load Characteristic EXTL.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic EXTL.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Characteristic EXTL 0001](images/Load_Characteristic_EXTL_0001.svg)

**Parameters:**

|        |                   |
| ------ | ----------------- |
| Kp     | P Integrator gain |
| Pmltmx | Pmult Maximum     |
| Pmltmn | Pmult Minimum     |
| Kq     | Q Integrator gain |
| Qmltmx | Qmult Maximum     |
| Qmltmn | Qmult Minimum     |

---

<a id="ieel"></a>

## IEEL

*Source: [`Content/TransientModels_HTML/Load Characteristic IEEL.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic IEEL.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Characteristic IEEL 0001](images/Load_Characteristic_IEEL_0001.svg)

**Parameters:**

|    |                                                                                                                                                                                        |
| -- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| a1 | Power a1 constant                                                                                                                                                                      |
| a2 | Power a2 constant                                                                                                                                                                      |
| a3 | Power a3 constant                                                                                                                                                                      |
| a4 | Reactive power a4 constant                                                                                                                                                             |
| a5 | Reactive power a5 constant                                                                                                                                                             |
| a6 | Reactive power a6 constant                                                                                                                                                             |
| a7 | Power a7 constant                                                                                                                                                                      |
| a8 | Reactive power a8 constant                                                                                                                                                             |
| N1 | Power N1 exponential                                                                                                                                                                   |
| N2 | Power N2 exponent                                                                                                                                                                      |
| N3 | Power N3 exponent                                                                                                                                                                      |
| N4 | Reactive power N4 exponent                                                                                                                                                             |
| N5 | Reactive power N5 exponent                                                                                                                                                             |
| N6 | Reactive power N6 exponent                                                                                                                                                             |
| Pf | Power factor of electronic load. 0 indicates to use the Q value from the load record directly.; a positive value indicates positive Mvars,; a negative value indicates negative Mvars. |

---

<a id="indmot1p"></a>

## INDMOT1P

*Source: [`Content/TransientModels_HTML/Load Characteristic INDMOT1P.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic INDMOT1P.htm)*

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="indmot1p-ptr"></a>

## INDMOT1P_PTR

*Source: [`Content/TransientModels_HTML/Load Characteristic INDMOT1P_PTR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic INDMOT1P_PTR.htm)*

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="indmot3p-a"></a>

## INDMOT3P_A

*Source: [`Content/TransientModels_HTML/Load Characteristic INDMOT3P_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic INDMOT3P_A.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="ld1pac"></a>

## LD1PAC

*Source: [`Content/TransientModels_HTML/Load Characteristic LD1PAC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LD1PAC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tth \< 0.5\*Mult\*TimeStep then Tth = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Tth \< Mult\*TimeStep then Tth = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="ld1pac-cmp"></a>

## LD1PAC_CMP

*Source: [`Content/TransientModels_HTML/Load Characteristic LD1PAC_CMP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LD1PAC_CMP.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tth \< 0.5\*Mult\*TimeStep then Tth = 0  
    ElseIf 0.5\*Mult\*TimeStep \< Tth \< Mult\*TimeStep then Tth = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0.0  
    ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-Model is the same as LD1PAC, except parameters on the right below are

\-Hard-coded as shown.

**Parameters:**

|                |                                                        |
| -------------- | ------------------------------------------------------ |
| Lfm            | Loading Factor                                         |
| TV             | Voltage input time in sec.                             |
| CompPF         | Compressor Power Factor                                |
| Vstall         | Compressor Stalling Voltage in p.u.                    |
| Rstall         | Compressor Stall resistance in p.u.                    |
| Xstall         | Compressor Stall impedance in p.u.                     |
| Tstall         | Compressor Stall delay time in sec.                    |
| Frst           | Restarting motor fraction                              |
| Vrst           | Restart motor voltage in p.u.                          |
| Trst           | Restarting time delay in sec.                          |
| Vc1off         | Voltage 1 contactor disconnect load in p.u.            |
| Vc2off         | Voltage 2 contactor disconnect load in p.u.            |
| Vc1on          | Voltage 1 contactor re-connect load in p.u.            |
| Vc2on          | Voltage 2 contactor re-connect load in p.u.            |
| Tth            | Compressor heating time constant in sec.               |
| Th1t           | Compressor motors begin tripping                       |
| Th2t           | Compressor motors finished tripping                    |
| fuvr           | Fraction of compressor motors with undervoltage relays |
| uvtr1 to uvtr2 | Undervoltage pickup level in p.u.                      |
| ttr1 to ttr2   | Undervoltage definite time in sec.                     |
| Tf             | 0.05                                                   |
| LFadj          | 0                                                      |
| KP1 to KP2     | Kp1 = 0; Kp2 = 12                                      |
| NP1 to NP2     | Np1 = 1; Np2 = 3.2                                     |
| KQ1 to KQ2     | Kq1 = 6; Kq2 = 11                                      |
| NQ1 to NQ2     | Nq1 = 2; Nq2 = 2.5                                     |
| Vbrk           | 0.86                                                   |
| CmpKpf         | 1                                                      |
| CmpKqf         | \-3.3.                                                 |
| MBase          | Treated as -abs(Lfm)                                   |

---

<a id="ldelec"></a>

## LDELEC

*Source: [`Content/TransientModels_HTML/Load Characteristic LDELEC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LDELEC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

The input parameters for the electronic load model are as follows:

\-Vd1 - Upper voltage cutoff, power is constant for voltages above this, linearly decreasing if below (pu)

\-Vd2 - Lower voltage cutoff, power is zero for voltages below this value, linearly increasing if above (pu)

\-Frcel - Fraction of load that is restarted when the voltage recovers

\-pfel - Power factor of electronic load. 0 - indicates to use the Q value from the load record directly. A positive value indicates positive Mvars; a negative value indicates negative Mvars.

Notes:

\-Load must present in the working case with non-zero constant active power.

\-If load bus voltage is greater than Vd1, the electronic load model is constant P and Q.

\-If load bus voltage is between Vd1 and Vd2, the P and Q are linearly reduced to zero.

\-frcel is a fraction of electronic load. If frcel is greater than zero, the frcel which was tripped will be reconnected linearly as the voltage recovers.

The logic for the electronic load model low voltage tripping is as follows:

If ( V \< Vmin ) Vmin = V \[Initially, Vmin = Vo\]

If ( Vmin \< Vd2 ) Vmin = Vd2 \[Vmin tracks the lowest voltage during the simulation but not below Vd2\]

If ( V \< Vd2 )

Fvl = 0.0 \[All load is tripped for V below Vd2\]

else if ( V \< Vd1 )

if ( V \<= Vmin ) \[While decreasing between Vd1 and Vd2\]

Fvl = (V – Vd2) / (Vd1 – Vd2)

else \[While recovering above Vmin, partial reconnection\]

Fvl = ( (Vmin – Vd2) + frcel \* (V - Vmin) ) / (Vd1 – Vd2)

endif

else

if ( Vmin \>= Vd1 )

Fvl = 1.0 \[If V has not gone below Vd1\]

else \[V has been below Vd1 but has recovered\]

Fvl = ( (Vmin – Vd2) + frcel \* (Vd1 - Vmin) )/ (Vd1 – Vd2)

endif

endif

Pel = Fvl \* Pel0

Qel = Fvl \* Qel0

**Parameters:**

|       |                                                                                                                                                                                        |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vd1   | Upper voltage cutoff, power is constant for voltages above this, linearly decreasing if below                                                                                          |
| Vd2   | Lower voltage cutoff, power is zero for voltages below this value, linearly increasing if above                                                                                        |
| Frcel | Fraction of load that is restarted when the voltage recovers                                                                                                                           |
| pfel  | Power factor of electronic load. 0 indicates to use the Q value from the load record directly.; a positive value indicates positive Mvars,; a negative value indicates negative Mvars. |
