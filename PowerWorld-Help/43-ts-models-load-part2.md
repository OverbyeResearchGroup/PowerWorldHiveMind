---
title: "TS Models — Loads (Part 2 of 3)"
part: "Transient Models"
chapter_file: "43-ts-models-load-part2.md"
topics: 10
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Loads (Part 2 of 3)

Load characteristic models, distributed generation, distribution equivalents and load relays.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (10)**

- [LDEV1](#ldev1)
- [LDFR](#ldfr)
- [LDRANDOM](#ldrandom)
- [LDVFD_A](#ldvfd-a)
- [LoadTimeSchedule](#loadtimeschedule)
- [MOTORC](#motorc)
- [MOTORW](#motorw)
- [MOTORX](#motorx)
- [MOTOR_CMP](#motor-cmp)
- [PERC1](#perc1)

---

<a id="ldev1"></a>

## LDEV1

*Source: [`Content/TransientModels_HTML/Load Characteristic LDEV1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LDEV1.htm)*

Added in September 22, 2025 Simulator 24 patch

LDEV1 is based on the model developed by EPRI summarized in the November 2022 report entitled

"A Positive Sequence Model for Aggregated Representation Electric Vehicle Chargers"

EPRI Project 1-116982

written by L. Sundaresh and P. Matra

Description of the LDEV1 model

This model was developed by EPRI for use as an electric vehicle charger model. However, this model can be used to represent any aggregation of a large number of power electronic loads. Examples would be an electrical vehicle charging station, a large number of computers such as a data center, a crypto-currency mining facility, a large number of variable frequency drives, and so on.

The values MWinit and Mvarinit on the left of the block diagram below are calculated as part of the stability simulation initialization routine. MWInit is set equal to the initial MW of the load. When this model is used inside the [CompLoad component-based load structure](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic), then the parameter QPRatio is used to calculate the Mvarinit value and any extra Mvars are assigned as done with the [CompLoad](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic). When this model is used as a stand-alone model as part of a LoadModelGroup, Load, Bus, Area, etc. then the QPRatio is ignored and the Mvarinit is set equal to the load's initial Mvar. If a simple event occurs in the simulation and the final voltage returns to the initial voltage and the cease and reconnect logic is never engaged during the simulation, then this model will bring the MW and Mvar back to the same as the initial condition. The top half of the block diagram below represents the real power (MW) response of the load while the bottom half of the block diagram represents the reactive power (Mvar) response.

The dynamic portion of this model is described in the left side of the block diagram by the dynamic states 1 - 6 . The washout blocks (Kvp/Tvp and Kvq/Tvq parameters) model a response where the model load will decrease when a decreasing voltage is encountered (such as after and during a fault) and the load will then increase when the voltage is increasing (during fault recovery). This is meant to model a device such as a variable frequency drive which may reduce the electrical power during a fault, but then after the fault clears an additional amount of load will be seen to re-accelerate the mechanical load that the VFD is driving. This model is not simulating any characteristics of the mechanical load or the control system that causes this behavior, but is using the simple washout blocks to approximation the behavior. The MW control path also includes a simple frequency droop with deadband response that the load may have. After this the lead lag blocks are used to model any other transient response of the real and reactive loads. This leads to States 1 and 2 in the block diagram below which represent the model's request for a per unit power based on the initial voltage Vinit.

After this, both the real power and reactive portions of this model are split into 4 independent paths determined by the fractions FrA, FrB, FrC, and a fourth path with a fraction (1 - FrA - FrB - FrC). Each of these control paths have a user input which is the exponent of the voltage relationship relative to the initial voltage. Any value of nPA and nQA is allowed, but it is useful to realize that nPA = 0 indicates a path that acts as a constant power at steady state, nPA = 1 indicates constant current, and nPA = 2 indicates constant impedance. After the exponent is modeled, each path then divides by per unit voltage to convert to a current signal. The limits Ipmax/Ipmin or Iqmax/Iqmin are then used. Next the fractional amount of the path (FrA) is applied and then this amount is multiplied by a value FracOnA which represents the fraction of a particular path that remains connected to the system. The FracOnA models the Cease and Reconnect logic of the path. Paths A, B, and C have such logic, while Path D does not have fractional cease and reconnect logic. For each, if the filtered voltage is less than VcA for more than TcA seconds, then a decision to cease a portion of the load. Then after an an additional delay of TdelayA seconds, the FracOnA is reduced to a value of (1 - FcA). Then the system will wait to see if the filtered voltage goes above VrA for more than TrA seconds at which time it will begin ramping the FracOnA value back up to 1.0 over a time of Tramp seconds. Additional detail is included below to describe how these timers are reset and how a voltage drops after the model begins to ramping is handled. See the pseud-code and diagrams below for more details.

Finally, the output of each path goes through a delay block using the Tnum time constant to result a final desired current for each path. The currents from the 4 paths are then summed to give a total real current (Ipmw) and total reactive current (Iqmvar) for the load. The treatment of this model in the algebraic network boundary equations is then a constant current.

Model Equations and/or Block Diagrams

Modified in Version 24 patch on February 11, 2026. Added the initialization feature Iqextra when the model is used as a stand-alone model.

![Load Characteristic LDEV1 0001](images/Load_Characteristic_LDEV1_0001.svg)

**Parameters:**

<table>
<tbody>
<tr class="odd">
<td>Lfm</td>
<td>Loading factor used to calculate MVAbase of model as MWinit/Lfm.<br />
Lfm&lt;0.001 is treated as a 1.00.</td>
</tr>
<tr class="even">
<td>Tfltr</td>
<td>Voltage measurement time constant [s]<br />
(values less than 2*TimeStep are treated as 0, values less than 4*timestep are treated as 4*Timestep)</td>
</tr>
<tr class="odd">
<td>Dbd</td>
<td>Deadband on frequency response [pu] (&gt;= 0, absolute value will be used)</td>
</tr>
<tr class="even">
<td>Kdroop</td>
<td>Frequency droop [per unit]</td>
</tr>
<tr class="odd">
<td>Kvp</td>
<td>Proportional constant for active power washout</td>
</tr>
<tr class="even">
<td>Tvp</td>
<td>Time constant for active power washout [seconds] (&lt;= 2*TimeStep will result in washout block being ignored)</td>
</tr>
<tr class="odd">
<td>QPratio</td>
<td>Q/P ratio for MvarInit computation from MWInit. MvarInit = QPRatio*MWInit<br />
</td>
</tr>
<tr class="even">
<td>Kvq</td>
<td>Proportional constant for reactive power washout</td>
</tr>
<tr class="odd">
<td>Tvq</td>
<td>Time constant for reactive power washout [seconds] (&lt;= 2*TimeStep will result in washout block being ignored)</td>
</tr>
<tr class="even">
<td>Ta</td>
<td>Lead time constant [seconds]</td>
</tr>
<tr class="odd">
<td>Tb</td>
<td>Lag time constant [seconds] (&lt;= 2*TimeStep will result in lead lag block being ignored)</td>
</tr>
<tr class="even">
<td>FrA</td>
<td>Fraction of Type A (If FrA + FrB + FrC &gt; 1.0 they are normalized to sum to 1.0)</td>
</tr>
<tr class="odd">
<td>FrB</td>
<td>Fraction of Type B (If FrA + FrB + FrC &gt; 1.0 they are normalized to sum to 1.0)</td>
</tr>
<tr class="even">
<td>FrC</td>
<td>Fraction of Type C (If FrA + FrB + FrC &gt; 1.0 they are normalized to sum to 1.0)</td>
</tr>
<tr class="odd">
<td>nPA</td>
<td>Active Power Exponential for Type A</td>
</tr>
<tr class="even">
<td>nQA</td>
<td>Reactive Power Exponential for Type A</td>
</tr>
<tr class="odd">
<td>nPB</td>
<td>Active Power Exponential for Type B</td>
</tr>
<tr class="even">
<td>nQB</td>
<td>Reactive Power Exponential for Type B</td>
</tr>
<tr class="odd">
<td>nPC</td>
<td>Active Power Exponential for Type C</td>
</tr>
<tr class="even">
<td>nQC</td>
<td>Reactive Power Exponential for Type C</td>
</tr>
<tr class="odd">
<td>nPD</td>
<td>Active Power Exponential for Type D</td>
</tr>
<tr class="even">
<td>nQD</td>
<td>Reactive Power Exponential for Type D</td>
</tr>
<tr class="odd">
<td>FcA</td>
<td>Fraction that will cease for Type A (0&lt;=FcA&lt;=1)</td>
</tr>
<tr class="even">
<td>VcA</td>
<td>Voltage threshold for cease logic for Type A [per unit]</td>
</tr>
<tr class="odd">
<td>TcA</td>
<td>Time delay for cease logic to be initiated for Type A [seconds]</td>
</tr>
<tr class="even">
<td>TdelayA</td>
<td>Time delay to cease after detection for Type A [seconds]</td>
</tr>
<tr class="odd">
<td>VrA</td>
<td>Voltage threshold to initiate power ramp logic for Type A [per unit]</td>
</tr>
<tr class="even">
<td>TrA</td>
<td>Time delay for ramp up reconnection logic to be initiated for Type A [seconds]</td>
</tr>
<tr class="odd">
<td>TrampA</td>
<td>Ramp up time for Type A [seconds]</td>
</tr>
<tr class="even">
<td>FcB</td>
<td>Fraction that will cease for Type B (0&lt;=FcB&lt;=1)</td>
</tr>
<tr class="odd">
<td>VcB</td>
<td>Voltage threshold for cease logic for Type B [per unit]</td>
</tr>
<tr class="even">
<td>TcB</td>
<td>Time delay for cease logic to be initiated for Type B [seconds]</td>
</tr>
<tr class="odd">
<td>TdelayB</td>
<td>Time delay to cease after detection for Type B [seconds]</td>
</tr>
<tr class="even">
<td>VrB</td>
<td>Voltage threshold to initiate power ramp logic for Type B [per unit]</td>
</tr>
<tr class="odd">
<td>TrB</td>
<td>Time delay for ramp up reconnection logic to be initiated for Type B [seconds]</td>
</tr>
<tr class="even">
<td>TrampB</td>
<td>Ramp up time for Type B [seconds]</td>
</tr>
<tr class="odd">
<td>FcC</td>
<td>Fraction that will cease for Type C (0&lt;=FcC&lt;=1)</td>
</tr>
<tr class="even">
<td>VcC</td>
<td>Voltage threshold for cease logic for Type C [per unit]</td>
</tr>
<tr class="odd">
<td>TcC</td>
<td>Time delay for cease logic to be initiated for Type C [seconds]</td>
</tr>
<tr class="even">
<td>TdelayC</td>
<td>Time delay to cease after detection for Type C [seconds]</td>
</tr>
<tr class="odd">
<td>VrC</td>
<td>Voltage threshold to initiate power ramp logic for Type C [per unit]</td>
</tr>
<tr class="even">
<td>TrC</td>
<td>Time delay for ramp up reconnection logic to be initiated for Type C [seconds]</td>
</tr>
<tr class="odd">
<td>TrampC</td>
<td>Ramp up time for Type C [seconds]</td>
</tr>
<tr class="even">
<td>Ipmax</td>
<td>Maximum Ip [per unit]</td>
</tr>
<tr class="odd">
<td>Ipmin</td>
<td>Minimum Ip [per unit]</td>
</tr>
<tr class="even">
<td>Iqmax</td>
<td>Maximum Iq [per unit]</td>
</tr>
<tr class="odd">
<td>Iqmin</td>
<td>Minimum Iq [per unit]</td>
</tr>
<tr class="even">
<td>ndelt</td>
<td>Time step subdivision factor (not used by PowerWorld)</td>
</tr>
<tr class="odd">
<td>Tnum</td>
<td>Time delay for outputs [seconds] (If &lt; 4*TimeStep are treated as 4*TimeStep)</td>
</tr>
</tbody>
</table>

![Load Characteristic LDEV1 CeaseReconnect2](images/Load_Characteristic_LDEV1_CeaseReconnect2.png)

![Load Characteristic LDEV1 CeaseReconnect](images/Load_Characteristic_LDEV1_CeaseReconnect.png)

![Load Characteristic LDEV1 0004](images/Load_Characteristic_LDEV1_0004.svg)

---

<a id="ldfr"></a>

## LDFR

*Source: [`Content/TransientModels_HTML/Load Characteristic LDFR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LDFR.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Characteristic LDFR 0001](images/Load_Characteristic_LDFR_0001.svg)

**Parameters:**

|      |                                |
| ---- | ------------------------------ |
| Ple  | Real power load exponent       |
| Qle  | Reactive power load exponent   |
| Iple | Real current load exponent     |
| Iqle | Reactive current load exponent |

---

<a id="ldrandom"></a>

## LDRANDOM

*Source: [`Content/TransientModels_HTML/Load Characteristic LDRANDOM.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LDRANDOM.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tfilter \< 0.5\*Mult\*TimeStep then Tfilter = 0, ElseIf 0.5\*Mult\*TimeStep \< Tfilter \< Mult\*TimeStep then Tfilter = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

The Random Load Model simulates a random load. The user needs to input the Percent of Standard Deviation to generate a random number; a Time for the filter and the Start time when the random load will start to be model. Once the random load model start internally it uses a filter and the generated random number to modify the load.

**Parameters:**

|            |                            |
| ---------- | -------------------------- |
| PercStdDev | Percent Standard Deviation |
| StartTime  | Start Time (Seconds)       |
| Tfilter    | T (Filter Time Constant)   |

---

<a id="ldvfd-a"></a>

## LDVFD_A

*Source: [`Content/TransientModels_HTML/Load Characteristic LDVFD_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LDVFD_A.htm)*

**AutoCorrection Properties**

Following corrections are automatically when using LDVFD\_A when simulating.

  - For parameters Tv, T1, and T2  
    If T \< 4\*TimeStep then T = 4\*TimeStep

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Load Characteristic LDVFD A 0001](images/Load_Characteristic_LDVFD_A_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                                                                          |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| K1     | Washout gain for active power (pu)                                                                                                                                                                                                                                       |
| T1     | Time Constant for active power (seconds)                                                                                                                                                                                                                                 |
| K2     | Washout gain for reactive power (pu)                                                                                                                                                                                                                                     |
| T2     | Time Constant for reactive power (seconds)                                                                                                                                                                                                                               |
| Pmax   | Maximum value of active power (as a multiple of the initial MW output)                                                                                                                                                                                                   |
| Qmax   | Maximum value of reactive power (as a multiple of the initial Mvar output)                                                                                                                                                                                               |
| V0     | voltage break-point for low voltage cut-out of the inverter (Multiplier = 0.0 at this voltage)                                                                                                                                                                           |
| V1     | voltage break-point for low voltage cut-out of the inverter (Multiplier = 1.0 at this voltage)                                                                                                                                                                           |
| Tv0    | voltage break-point for low voltage cut-out timer (If voltage stays below vl0 for more than tvl0 seconds, then the multiplier will remain zero for the simulation)                                                                                                       |
| Tv1    | voltage break-point for low voltage cut-out timer (If voltage stays below vl1 for more than tvl1 seconds, then the multiplier will track a depressed curve according to Vrfrac and an internally tracked value of the minimum voltage experienced during the simulation) |
| Vrfrac | fraction of device that recovers after voltage comes back to within vl1 \< V \< vh1 (Note that the timers Tvl1 also impact when this fraction is used)                                                                                                                   |
| Tv     | time constant on the output of the voltage cut-out                                                                                                                                                                                                                       |
| Pfinit | Initial power factor (used when part of a CompLoad)                                                                                                                                                                                                                      |

---

<a id="loadtimeschedule"></a>

## LoadTimeSchedule

*Source: [`Content/TransientModels_HTML/Load Characteristic LoadTimeSchedule.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic LoadTimeSchedule.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|              |                                                              |
| ------------ | ------------------------------------------------------------ |
| ScheduleType | Set to zero to disable, 1 to multiply load by schedule value |

---

<a id="motorc"></a>

## MOTORC

*Source: [`Content/TransientModels_HTML/Load Characteristic MOTORC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic MOTORC.htm)*

Model Equations and/or Block Diagrams

This model builds on the INDMOT1P model, but makes some modifications

1\. Replaces the saturation input parameters and has user enter ASat and BSat directly

2\. Simplifies the mechanical torque equation to a single parameter D.

3\. Includes under-voltage, contractor, and thermal relays identical to the LD1PAC model

**Parameters:**

|          |                                                                                                                                                                                                                     |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R\_ds    | stator d-axis resistance in per unit                                                                                                                                                                                |
| R\_qs    | stator q-axis resistance in per unit                                                                                                                                                                                |
| X\_m     | magnetizing reactance in per unit                                                                                                                                                                                   |
| X\_c     | capacitor reactance in per unit (will be negative)                                                                                                                                                                  |
| X\_ds^'  | stator d-axis reactance in per unit                                                                                                                                                                                 |
| X\_qs^'  | stator q-axis reactance in per unit                                                                                                                                                                                 |
| X\_r     | rotor reactance in per unit                                                                                                                                                                                         |
| T\_o^'   | rotor time constant in seconds. Entered instead of R\_r , R\_r=X\_r/(ω\_b T\_o^' )                                                                                                                                  |
| H        | inertia constant for the motor                                                                                                                                                                                      |
| D        | Exponential term of the mechanical power equation: T\_mech=T\_nom (ω\_r^(D-1) ); (Note: This term will always be 1 more than the Etrq term on a similar INDMOT1P model)                                             |
| Asat     | Parameter for Saturation equation                                                                                                                                                                                   |
| Bsat     | Parameter for Saturation equation                                                                                                                                                                                   |
| n        | ratio of stator auxiliary winding turns to stator main winding turns                                                                                                                                                |
| ndelt    | This parameter is not used by PowerWorld, but is carried around to support DYD files                                                                                                                                |
| wdelt    | This parameter is not used by PowerWorld, but is carried around to support DYD files                                                                                                                                |
| V\_c1off | Voltage in per unit at which load fraction begins decreasing                                                                                                                                                        |
| V\_c2off | Voltage in per unit at which load fraction decreases to zero                                                                                                                                                        |
| V\_c1on  | Voltage in per unit at which load fraction begins increasing                                                                                                                                                        |
| V\_c2on  | Voltage in per unit at which load fraction increases                                                                                                                                                                |
| T\_th    | Compressor heating time constant in seconds                                                                                                                                                                         |
| T\_h1t   | Compressor motors begin tripping                                                                                                                                                                                    |
| T\_h2t   | Compressor motors finish tripping                                                                                                                                                                                   |
| F\_uvr   | Fraction of compressor motors with undervoltage relays                                                                                                                                                              |
| V\_tr1   | First undervoltage pickup level, p.u.                                                                                                                                                                               |
| T\_tr1   | First definite time for U/V trip, sec.                                                                                                                                                                              |
| V\_tr2   | Second undervoltage pickup level, p.u.                                                                                                                                                                              |
| T\_tr2   | Second definite time for U/V trip, sec.                                                                                                                                                                             |
| T\_v     | Voltage measurement delay in seconds                                                                                                                                                                                |
| MBase    | If MBase \> 0 then machine parameters are on MVABaseUsed=MBase; If MBase = 0 then machine parameters are on MVABaseUsed = abs(MWInit); If Mbase \< 0 then machine parameters are on MVABaseUsed = abs(MWInit/MBase) |

![Load Characteristic MOTORC 0001](images/Load_Characteristic_MOTORC_0001.svg)

![Load Characteristic MOTORC 0002](images/Load_Characteristic_MOTORC_0002.svg)

![Load Characteristic MOTORC 0003](images/Load_Characteristic_MOTORC_0003.svg)

---

<a id="motorw"></a>

## MOTORW

*Source: [`Content/TransientModels_HTML/Load Characteristic MOTORW.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic MOTORW.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
  - If 0.0 \< Tppo \< 0.5\*Mult\*TimeStep then Tppo = 0, ElseIf 0.5\*Mult\*TimeStep \< Tppo \< Mult\*TimeStep then Tppo = Mult\*TimeStep
  - If H \< 0.01 then H = 0.01.
  - Pul: This is a normalized value, thus check if greater than 1, or less than 0; this catches a user ending a percentage value but do not autocorrect the value.
  - If Lp \> 0.4\*Ls then Lp = 0.4\*Ls
  - If Lpp \> Lp then Lpp = Lp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Load Characteristic MOTORW 0001](images/Load_Characteristic_MOTORW_0001.svg)

**Parameters:**

|                          |                                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------------- |
| Mbase                    | MBase: MBase of Load Model                                                                  |
| ApplyToConstantPowerOnly | 0 means it applies to all, 1 means it applies to only the constant power part of the load   |
| Pul                      | Fraction of constant-power load to be represented by this motor model (between 1.0 and 0.0) |
| Ls                       | Synchronous reactance                                                                       |
| Lp                       | Transient reactance                                                                         |
| Ra                       | Stator resistance, p.u.                                                                     |
| Tpo                      | Transient rotor time constant                                                               |
| H                        | Inertia constant, sec.                                                                      |
| D                        | Damping factor, p.u.                                                                        |
| VT                       | Voltage threshold for tripping (default = 0), p.u.                                          |
| TV                       | Voltage trip pickup time (default = 999), sec.                                              |
| Tbkr                     | Circuit breaker operating time (default = 999), sec.                                        |
| Acc                      | Acceleration factor for initialization                                                      |
| Lpp                      | Sub-transient reactance, p.u.                                                               |
| Tppo                     | Sub-transient rotor time constant, sec.                                                     |
| ndelt                    | Time step subdivision factor.                                                               |
| wdelt                    | Speed threshold for subdividing time step, p.u.                                             |

---

<a id="motorx"></a>

## MOTORX

*Source: [`Content/TransientModels_HTML/Load Characteristic MOTORX.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic MOTORX.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - R1: 1) If motor is not Double Cage or Type 1, then if circuit parameters result in a Tp time constant which is too small then set R1 to a multiple of Tp/(Minimum time constant size as a multiple of time step). 2) If motor is Double Cage, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R1 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).
  - R2: 1) If motor is Double Cage and Type 1, then if circuit parameters result in a Tpp time constant which is too small then change the motor to single cage by setting R2 and X2 to zero only if Tpp is less than Half the Minimum time constant size as a multiple of time step, and if not just set R2 to a multiple of Tpp/(Minimum time constant size as a multiple of time step).

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Load Characteristic MOTORX 0001](images/Load_Characteristic_MOTORX_0001.svg)

**Parameters:**

|           |                                                                                                  |
| --------- | ------------------------------------------------------------------------------------------------ |
| MBase     | MBase: MBase of Load Model                                                                       |
| AppliesTo | 0 means it applies to all, 1 means it applies to only the constant power part of the load        |
| Pul       | Pul: Fraction of constant-power load to be represented by this motor model (between 1.0 and 0.0) |
| Rs        | Rs: Stator winding resistance, p.u.                                                              |
| Xs        | Xs: Stator winding reactance, p.u.                                                               |
| Xm        | Xm: Magnetizing reactance, p.u.                                                                  |
| R1        | R1: Rotor resistance, p.u.                                                                       |
| X1        | X1: Rotor leakage reactance, p.u.                                                                |
| R2        | R2: Rotor resistance, p.u. (0 for single cage motor)                                             |
| X2        | X2: Rotor leakage reactance, p.u. (0 for single cage motor)                                      |
| H         | H: Inertia constant, sec.                                                                        |
| D         | D: Damping factor, p.u.                                                                          |
| Vt        | Vt: Voltage threshold for tripping, p.u.                                                         |
| Tv        | Tv: Voltage trip pickup time, sec.                                                               |
| Tbkr      | Tbkr: Circuit breaker operating time, sec.                                                       |
| Acc       | Acc: Acceleration factor for initialization                                                      |
| ndelt     | ndelt: Time step subdivision factor.                                                             |
| wdelt     | wdelt: Speed threshold for subdividing time step, p.u.                                           |
| pfact     | pfact: Mbase Multiplier                                                                          |

---

<a id="motor-cmp"></a>

## MOTOR_CMP

*Source: [`Content/TransientModels_HTML/Load Characteristic MOTOR_CMP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic MOTOR_CMP.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tpo \< Mult\*TimeStep then Tpo = Mult\*TimeStep
  - If 0.0 \< Tppo \< 0.5\*Mult\*TimeStep then Tppo = 0, ElseIf 0.5\*Mult\*TimeStep \< Tppo \< Mult\*TimeStep then Tppo = Mult\*TimeStep
  - If H \< 0.01 then H = 0.01.
  - Pul: This is a normalized value, thus check if greater than 1, or less than 0; this catches a user ending a percentage value but do not autocorrect the value.
  - If Lp \> 0.4\*Ls then Lp = 0.4\*Ls
  - If Lpp \> Lp then Lpp = Lp

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

\-MOTOR\_CMP is similar to MOTORW, with the following exceptions

\-The MVABase for this model is equal to MVABase = (Pinitial/Lfm)

\-Etrq is the exponent for the torque equation. Thus if Etrq = 0 that represents constant torque, but would be equivalent equivalent to a MOTORW D parameter of 1.

\-Reminder: MOTOR\_CMP again does not include the parameter Ll (leakage reactance), so again its behavior is determined by the global option regarding how to handle MOTORW models

\-There are 2 stages of under-voltage load tripping and restarting defined with this model. The motor will be reduced by a fraction of Ftr1 if the terminal voltage falls below Vtr1 for Ttr1 seconds. This portion of the load will reconnect however if the voltage subsequently got above Vrc1 for Ttrc1 seconds.

\-Similar process is done for the Vtr2, Ttr2, Ftr2, Vrc2, and Trc2 parameters.

\-Note however that this tripping and reconnected is not modeling the dynamics of different portions of the loads slowing down and restarting. There is only one rotor speed state for this entire load model which is an approximation of 1000s of individual motors. The fractions of load that trip and then reconnect will not exhibit the restarting torques seen with an individual motor model.

\-This model is used inside the CMPLDW and CMLD composite models

**Parameters:**

|      |                                         |
| ---- | --------------------------------------- |
| Lfm  | Lfm                                     |
| Ra   | Stator resistance, p.u.                 |
| Ls   | Synchronous reactance                   |
| Lp   | Transient reactance                     |
| Lpp  | Sub-transient reactance, p.u.           |
| Tpo  | Transient rotor time constant           |
| Tppo | Sub-transient rotor time constant, sec. |
| H    | Inertia constant, sec.                  |
| Etrq | Exponent for the torque equation.       |
| Vtr1 | Fall Below Terminal Voltage 1           |
| TTr1 | Fall Below Time 1                       |
| Ftr1 | Fraction of Motor Reduced 1             |
| Vrc1 | Reconnect Terminal Voltage 1            |
| Trc1 | Reconnect Time 1                        |
| Vtr2 | Fall Below Terminal Voltage 2           |
| TTr2 | Fall Below Time 2                       |
| Ftr2 | Fraction of Motor Reduced 2             |
| Vrc2 | Reconnect Terminal Voltage 1            |
| Trc2 | Reconnect Time 2                        |

---

<a id="perc1"></a>

## PERC1

*Source: [`Content/TransientModels_HTML/Load Characteristic PERC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic PERC1.htm)*

Available in October 27, 2025 path of Version 24

PERC1 is an acronym for the **Power Electronic Reconnecting and Ceasing** load model. It is based on LDEV1 which was based on the model developed by EPRI summarized in the November 2022 report entitled

"A Positive Sequence Model for Aggregated Representation Electric Vehicle Chargers"

EPRI Project 1-116982

written by L. Sundaresh and P. Matra

This model is based on the LDEV1 model. PERC1 is appropriate to represent any aggregation of a large number of power electronic loads. Examples would be an electrical vehicle charging, a large number of computers such as a data center, a cryptocurrency mining facility, a large number of variable frequency drives, and so on. The differences between LDEV1 and this model are as follows

1.  **Frecon** is provided so that after reconnecting is complete the fraction may not come back to 1.00 but instead to a reduced value of (1 - Fcease + Frecon\*Fcease)

2.  **Tap**, **Tbp**, **Taq**, **Tbq**: Separate Lead/Lag time constants are provided for the P and Q paths

3.  **Dbfl** and **Dbfh** are separate parameters for low and high frequency deadband

4.  Has a single path for P and Q instead of 4 fractional paths. Multiple PERC1 load models could be used with the [CompLoad component-based load structure](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic) to model multiple paths.

Description of the PERC1 model

While the model developed by EPRI was for an electric vehicle charger model, this model can be used to represent any aggregation of a large number of power electronic loads. Examples would be an electrical vehicle charging station, a large number of computers such as a data center, a crypto-currency mining facility, a large number of variable frequency drives, and so on.

The values MWinit and Mvarinit on the left of the block diagram below are calculated as part of the stability simulation initialization routine. MWInit is set equal to the initial MW of the load. When this model is used inside the [CompLoad component-based load structure](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic), then the parameter QPRatio is used to calculate the Mvarinit value and any extra Mvars are assigned as done with the [CompLoad](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic). When this model is used as a stand-alone model as part of a LoadModelGroup, Load, Bus, Area, etc. then the QPRatio is ignored and the Mvarinit is set equal to the load's initial Mvar. If a simple event occurs in the simulation and the final voltage returns to the initial voltage and the cease and reconnect logic is never engaged during the simulation, then this model will bring the MW and Mvar back to the same as the initial condition. The top half of the block diagram below represents the real power (MW) response of the load while the bottom half of the block diagram represents the reactive power (Mvar) response.

The dynamic portion of this model is described in the left side of the block diagram by the dynamic states 1 - 6 . The washout blocks (Kvp/Tvp and Kvq/Tvq parameters) model a response where the model load will decrease when a decreasing voltage is encountered (such as after and during a fault) and the load will then increase when the voltage is increasing (during fault recovery). This is meant to model a device such as a variable frequency drive which may reduce the electrical power during a fault, but then after the fault clears an additional amount of load will be seen to re-accelerate the mechanical load that the VFD is driving. This model is not simulating any characteristics of the mechanical load or the control system that causes this behavior, but is using the simple washout blocks to approximation the behavior. The MW control path also includes a simple frequency droop with deadband response that the load may have. After this the lead lag blocks are used to model any other transient response of the real and reactive loads. This leads to States 1 and 2 in the block diagram below which represent the model's request for a per unit power based on the initial voltage Vinit.

After this, both the real power and reactive portions of this model have a user input which is the exponent of the voltage relationship relative to the initial voltage. Any value of nP and nQ is allowed, but it is useful to realize that nP = 0 indicates a constant power at steady state, nP = 1 indicates constant current, and nP = 2 indicates constant impedance. After the exponent, it then divides by per unit voltage to convert to a current signal. The limits Ipmax/Ipmin or Iqmax/Iqmin are then used. Next the current is multiplied by a value FracOn which represents the fraction of the load that remains connected to the system. The FracOn models the Cease and Reconnect logic. If the filtered voltage is less than Vcease for more than Tcease seconds, then a decision to cease a portion of the load is made. Then, after an additional delay of Tdelay seconds, the FracOn is reduced to a value of (1 - Fcease). Then the system will wait to see if the filtered voltage goes above Vrecon for more than Trecon seconds at which time it will begin ramping the FracOn value back up over a time of Tramp seconds to a value of (1 - Fcease + Fcease\*Frecon). Additional detail is included below to describe how these timers are reset and how a voltage drops after the model begins ramping is handled. See the pseudo-code and diagrams below for more details.

Finally, the output goes through another delay block using the Tt time constant to result a final desired current for each path. The treatment of this model in the algebraic network boundary equations is then a constant current.

Model Equations and/or Block Diagrams

Modified in Version 24 patch on February 11, 2026. Added the initialization feature Iqextra when the model is used as a stand-alone model.

![Load Characteristic PERC1 0001](images/Load_Characteristic_PERC1_0001.svg)

<table>
<tbody>
<tr class="odd">
<td>Parameter</td>
<td>Description</td>
<td>Default</td>
</tr>
<tr class="even">
<td>Lfm</td>
<td>Loading factor used to calculate MVAbase of model as MWinit/Lfm.<br />
If Lfm &lt; 0.001 then software will use a value of 0.80</td>
<td>0.80</td>
</tr>
<tr class="odd">
<td>QPratio</td>
<td>Q/P ratio for MvarInit computation from MWInit. MvarInit = QPRatio*MWInit</td>
<td>0.66</td>
</tr>
<tr class="even">
<td>Dbfl</td>
<td>Deadband on frequency response low (&lt;=0) [pu]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>Dbfh</td>
<td>Deadband on frequency response high (&gt;=0) [pu]</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>Kdroop</td>
<td>Frequency droop [per unit]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>Kvp</td>
<td>Proportional constant for active power washout</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>Tvp</td>
<td>Time constant for active power washout [seconds]</td>
<td>0.10</td>
</tr>
<tr class="odd">
<td>Kvq</td>
<td>Proportional constant for reactive power washout</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>Tvq</td>
<td>Time constant for reactive power washout [seconds]</td>
<td>0.10</td>
</tr>
<tr class="odd">
<td>Tap</td>
<td>Lead time constant for real power path [seconds]</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>Tbp</td>
<td>Lag time constant for real power path [seconds]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>Taq</td>
<td>Lead time constant for reactive power path [seconds]</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>Tbq</td>
<td>Lag time constant for reactive power path [seconds]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>nP</td>
<td>Active Power Exponential</td>
<td>0.00</td>
</tr>
<tr class="even">
<td>nQ</td>
<td>Reactive Power Exponential</td>
<td>1.00</td>
</tr>
<tr class="odd">
<td>Ipmax</td>
<td>Maximum Ip [per unit]</td>
<td>1.00</td>
</tr>
<tr class="even">
<td>Ipmin</td>
<td>Minimum Ip [per unit]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>Iqmax</td>
<td>Maximum Iq [per unit]</td>
<td>0.66</td>
</tr>
<tr class="even">
<td>Iqmin</td>
<td>Minimum Iq [per unit]</td>
<td>-0.66</td>
</tr>
<tr class="odd">
<td>Fcease</td>
<td>Fraction that will cease (between 0 and 1)</td>
<td>1.00</td>
</tr>
<tr class="even">
<td>Vcease</td>
<td>Voltage threshold for cease logic [per unit]</td>
<td>0.50</td>
</tr>
<tr class="odd">
<td>Tcease</td>
<td>Time delay for cease logic to be initiated for (&gt;= 0) [seconds]</td>
<td>0.01</td>
</tr>
<tr class="even">
<td>Tdelay</td>
<td>Time delay to cease after detection for (&gt;= 0) [seconds]</td>
<td>0.00</td>
</tr>
<tr class="odd">
<td>Vrecon</td>
<td>Voltage threshold to initiate power ramp reconnection logic (Vrecon &gt;= Vcease) [per unit]</td>
<td>0.60</td>
</tr>
<tr class="even">
<td>Trecon</td>
<td>Time delay for ramp up logic to be initiated (&gt;= 0) [seconds]</td>
<td>0.05</td>
</tr>
<tr class="odd">
<td>Tramp</td>
<td>Ramp up time (&gt;= 0) [seconds]</td>
<td>1.00</td>
</tr>
<tr class="even">
<td>Frecon</td>
<td>Of the fraction that ceases, this is the fraction that then reconnects (&gt;=0).<br />
Frecon &gt; 1.0 allowed for a load that comes back above the initial value after reconnecting. Ability to specify Frecon &gt; 1.0 was added in July 14, 2026 patch of Simulator 24.<br />
</td>
<td>1.00</td>
</tr>
<tr class="odd">
<td>Tt</td>
<td>Time delay for outputs [seconds] (If &lt; 4*TimeStep will be treated as 4*TimeStep)</td>
<td>0.02</td>
</tr>
<tr class="even">
<td>Tv</td>
<td>Voltage measurement time constant [s]</td>
<td>0.02</td>
</tr>
<tr class="odd">
<td>Tf</td>
<td>Frequency measurement time constant [s]</td>
<td>0.02</td>
</tr>
</tbody>
</table>

![Load Characteristic PERC1 CeaseReconnect3](images/Load_Characteristic_PERC1_CeaseReconnect3.png)

![Load Characteristic PERC1 CeaseReconnect2](images/Load_Characteristic_PERC1_CeaseReconnect2.png)

![Load Characteristic PERC1 CeaseReconnect1](images/Load_Characteristic_PERC1_CeaseReconnect1.png)

![Load Characteristic PERC1 0004](images/Load_Characteristic_PERC1_0004.svg)
