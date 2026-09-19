---
title: "TS Models — Branches and Shunts (Part 2 of 2)"
part: "Transient Models"
chapter_file: "44-ts-models-branch-and-shunt-part2.md"
topics: 16
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Branches and Shunts (Part 2 of 2)

Branch, line shunt and switched shunt dynamic models.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (16)**

- [ABBSVC1](#abbsvc1)
- [CAPRELAY](#caprelay)
- [CHSVCT](#chsvct)
- [CSSCST](#csscst)
- [FACRI_SS](#facri-ss)
- [MSC1](#msc1)
- [MSR1](#msr1)
- [MSS1](#mss1)
- [MSS2](#mss2)
- [SVCALS](#svcals)
- [SVSMO1](#svsmo1)
- [SVSMO1_AK_A](#svsmo1-ak-a)
- [SVSMO1_AK_B](#svsmo1-ak-b)
- [SVSMO2](#svsmo2)
- [SVSMO3](#svsmo3)
- [SWSHNT](#swshnt)

---

<a id="abbsvc1"></a>

## ABBSVC1

*Source: [`Content/TransientModels_HTML/Switched Shunt ABBSVC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt ABBSVC1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T4\< 0.5\*Mult\*TimeStep then T4= Mult\*TimeStep
  - If 0.0 \< T7\< 0.5\*Mult\*TimeStep then T7= Mult\*TimeStep
  - If 0.0 \< T9\< 0.5\*Mult\*TimeStep then T9= Mult\*TimeStep
  - If 0.0 \< T11\< 0.5\*Mult\*TimeStep then T11= Mult\*TimeStep
  - If 0.0 \< TBReg \< 0.5\*Mult\*TimeStep then TBReg = Mult\*TimeStep
  - If 0.0 \< TLL2\< 0.5\*Mult\*TimeStep then TLL2= 0, ElseIf 0.5\*Mult\*TimeStep \< TLL2\< Mult\*TimeStep then TLL2= Mult\*TimeStep
  - If B2MAX\< B2MIN then swap the values
  - If BMAXDes \< BMINDes then swap the values
  - If BMAXDes2 \< BMINDes2 then swap the values
  - If VPODMAX \< VPODMIN then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If B1\> B1MAX, then B1MAX= B1 or if B1 \< B1MIN or , then B1MIN = B1
  - If VPOD \> VPODMAX, then VPODMAX= VPOD or if VPOD \< VPODMIN , then VPODMIN = VPOD
  - If V2 \> V2Max then V2Max = V2
  - IF I1 \> I1MAXClim then IMAXClim = I1
  - IF I1 \> then ITCRMAX = I1
  - If I1 \< IMINI then IMINI = I1

Model Equations and/or Block Diagrams

![Switched Shunt ABBSVC1 0001](images/Switched_Shunt_ABBSVC1_0001.svg)

![Switched Shunt ABBSVC1 0002](images/Switched_Shunt_ABBSVC1_0002.svg)

![Switched Shunt ABBSVC1 0003](images/Switched_Shunt_ABBSVC1_0003.svg)

**Parameters:**

|           |                                                                                                                                                       |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| RPC       | reactive power control flag; 0: Non; 1: Supplementary Control; 2: External Caps; 3: Supplementary + External Caps                                     |
| PODStatus | flag to indicate status of aux. signal; 0: None; 1: Supplementary Control; 2: External Caps; 3: Supplementary + External Caps                         |
| ENABIN    | flag to indicate if sign of the aux. signal to be changed or not; 1: Change POD output sign when input signal becomes negative; 0: Do not change sign |
| SVCBASE   | Base MVA (\>0)                                                                                                                                        |
| T4        | Integrator time constant (s) (\>0)                                                                                                                    |
| Ts        | Thyristor firing delay (s)                                                                                                                            |
| Tth       | Thyristor firing time constant (s)                                                                                                                    |
| Xcc       | Slope for capacitive range, on SVC base (pu voltage/pu current)                                                                                       |
| Xci       | Slope for inductive range, on SVC base (pu voltage/pu current)                                                                                        |
| TLL1      | Voltage controller lead time constant (s)                                                                                                             |
| TLL2      | Voltage controller lag time constant (s)                                                                                                              |
| B1MAX     | max. limit for voltage controller (pu on SVC base)                                                                                                    |
| B1MIN     | min. limit for voltage controller (pu on SVC base)                                                                                                    |
| B2MAX     | max. susceptance of SVC (pu on SVC base)                                                                                                              |
| B2MIN     | min. susceptance of SVC (pu on SVC base)                                                                                                              |
| OVThrsld  | overvoltage tripping threshold (pu)                                                                                                                   |
| OVDelay   | overvoltage tripping delay (s)                                                                                                                        |
| SVLow     | severe undervoltage strategy low voltage threshold (pu)                                                                                               |
| SVHigh    | severe undervoltage strategy high voltage threshold (pu)                                                                                              |
| SBFClear  | severe undervoltage strategy susceptance (pu on SVC base)                                                                                             |
| STBFClear | timing of severe undervoltage strategy (s)                                                                                                            |
| VLow      | undervoltage strategy low voltage threshold (pu)                                                                                                      |
| VHigh     | undervoltage strategy high voltage threshold (pu)                                                                                                     |
| USDelay   | undervoltage strategy delay (s)                                                                                                                       |
| BFClear   | undervoltage strategy susceptance (pu on SVC base)                                                                                                    |
| TBFClear  | timing of undervoltage strategy (s)                                                                                                                   |
| V2Max     | max. SVC bus voltage limit (pu)                                                                                                                       |
| K6        | controller (V2) gain (pu)                                                                                                                             |
| T6        | controller (V2) time constant (s)                                                                                                                     |
| T7        | controller (V2) integrator time constant (s) (\>0)                                                                                                    |
| V2Clim    | controller (V2) minimum limit (pu on SVC base) (\<0)                                                                                                  |
| I1MAXC    | maximum capacitive current limit (pu on SVC base) (\>0)                                                                                               |
| K8        | controller (I1MAXC) gain (pu)                                                                                                                         |
| T8        | controller (I1MAXC) time constant (s)                                                                                                                 |
| T9        | controller (I1MAXC) integrator time constant (s) (\>0)                                                                                                |
| IMAXClim  | controller (I1MAXC) minimum limit (pu on SVC base) (\<carat0)                                                                                         |
| IMINI     | maximum inductive current limit (pu on SVC base) (\<carat0)                                                                                           |
| K10       | controller (I1MINI) gain (pu)                                                                                                                         |
| T10       | controller (I1MINI) time constant (s)                                                                                                                 |
| T11       | controller (I1MINI)s integrator time constant (s) (\>0)                                                                                               |
| IMINClim  | controller (I1MINI) minimum limit (pu on SVC base) (\>0)                                                                                              |
| ITCRMAX   | maximum TCR current limit (pu on SVC base) (≥ 0)                                                                                                      |
| K1        | controller (ITCR) gain (pu)                                                                                                                           |
| T1        | controller (ITCR) time constant (s)                                                                                                                   |
| T2        | controller (ITCR) integrator time constant (s) (\>0)                                                                                                  |
| TCRLimTRG | TCR current limiter voltage trigger (pu)                                                                                                              |
| TCRMIN    | minimum TCR limit for ITCR control (pu on SVC base)                                                                                                   |
| FShunt    | fixed shunt compensation (pu on SVC base) (≥ 0) (this is always the filters, which are always capacitive; hence≥ zero)                                |
| BRegMAX   | supplementary control capacitive threshold (pu on SVC base)                                                                                           |
| BRegMIN   | supplementary control inductive threshold (pu on SVC base)                                                                                            |
| VRefMAX   | maximum reference voltage for regulated bus voltage (pu)                                                                                              |
| VRefMIN   | minimum reference voltage for regulated bus voltage (pu)                                                                                              |
| TBReg     | integrator time constant for supplementary control(s) (\>0)                                                                                           |
| DVBRegMAX | max. output of supplementary control (pu)                                                                                                             |
| DVBRegMIN | min. output of supplementary control (pu)                                                                                                             |
| BMAXDes   | MSC slow switching capacitive threshold (pu on system base)                                                                                           |
| BMINDes   | MSC slow switching inductive threshold (pu on system base)                                                                                            |
| TDelay1   | time delay for slow switching of MSCs (s)                                                                                                             |
| BMAXDes2  | MSC fast switching capacitive threshold (pu on system base)                                                                                           |
| BMINDes2  | MSC fast switching inductive threshold (pu on system base)                                                                                            |
| TDelay2   | time delay for fast switching of MSCs, (s)                                                                                                            |
| PODTW1    | washout filter 1 time constant (s) (if zero, the washout is disabled)                                                                                 |
| PODTW2    | washout filter 1 time constant (s) (\>0) (if zero, the washout is disabled)                                                                           |
| PODTM1    | POD 1st lead-lag block lead time constant (s)                                                                                                         |
| PODTM2    | POD 1st lead-lag block lag time constant (s)                                                                                                          |
| PODTM3    | POD 2nd lead-lag block lead time constant (s)                                                                                                         |
| PODTM4    | POD 2nd lead-lag block lag time constant (s)                                                                                                          |
| PODTM5    | 3rd POD lead-lag block lead time constant (s)                                                                                                         |
| PODTM6    | 3rd POD lead-lag block lag time constant (s)                                                                                                          |
| KPOD      | POD gain (pu)                                                                                                                                         |
| VPODMAX   | POD max. output limit (pu)                                                                                                                            |
| VPODMIN   | POD min. output limit (pu)                                                                                                                            |
| PODTW4    | washout filter 4 time constant (s)                                                                                                                    |

---

<a id="caprelay"></a>

## CAPRELAY

*Source: [`Content/TransientModels_HTML/Switched Shunt CAPRELAY.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt CAPRELAY.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|         |                                                                    |
| ------- | ------------------------------------------------------------------ |
| Rem Bus | Remote Bus                                                         |
| Tfilter | Voltage filter time constant in sec.                               |
| tbClose | Circuit breaker closing time for switching shunt ON in sec.        |
| tbOpen  | Circuit breaker closing time for switching shunt OFF in sec.       |
| V1On    | First voltage threshold for switching shunt capacitor ON in sec.   |
| T1On    | First time delay for switching shunt capacitor ON in sec.          |
| V2On    | Second voltage threshold for switching shunt capacitor ON in sec.  |
| T2On    | Second time delay for switching shunt capacitor ON in sec.         |
| V1Off   | First voltage threshold for switching shunt capacitor OFF in sec.  |
| T1Off   | First time delay for switching shunt capacitor OFF in sec.         |
| V2Off   | Second voltage threshold for switching shunt capacitor OFF in sec. |
| T2Off   | Second time delay for switching shunt capacitor OFF in sec.        |

---

<a id="chsvct"></a>

## CHSVCT

*Source: [`Content/TransientModels_HTML/Switched Shunt CHSVCT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt CHSVCT.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Tw, T2 and Tm2 must be great than Mult\*TimeStep. If they are not, they are set to Mult\*TimeStep
  - T4 and Tm4 can be zero. If they are less than 0.5\*Mult\*TimeStep they are set to zero. If they are between 0.5\*Mult\*TimeStep and Mult\*TimeStep they are rounded up to Mult\*TimeStep.
  - If Vsmax \< Vsmin then swap the values.
  - If Bfmax \< Bfmin then swap the values.
  - If Bmax \< Bmin then swap the values.
  - SMF Bus must be one of the terminal of the SMF Branch. If it is not, then SMF Bus is treated as the from bus of the SMF Branch.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Switched Shunt CHSVCT 0001](images/Switched_Shunt_CHSVCT_0001.svg)

**Parameters:**

|        |                           |
| ------ | ------------------------- |
| Switch | 0: 0; \<\>0: Input        |
| Xc     | Slope                     |
| V1     | Vclamp V1                 |
| V2     | Vclamp V2                 |
| Td2    | Delay block time constant |
| T1     | Time constant, sec        |
| T2     | Time constant, sec        |
| T3     | Time constant, sec        |
| T4     | Time constant, sec        |
| K      | Gain                      |
| Bfmax  | Maximum limit             |
| Bfmin  | Minimum limit             |
| Td1    | Delay block time constant |
| Bmax   | Bshunt Maximum            |
| Bmin   | Bshunt Minimum            |
| Km     | Time constant, sec        |
| Tw     | Time constant, sec        |
| Td3    | Delay block time constant |
| Tm1    | Time constant, sec        |
| Tm2    | Time constant, sec        |
| Tm3    | Time constant, sec        |
| Tm4    | Time constant, sec        |
| Vsmax  | Maximum limit             |
| Vsmin  | Minimum limit             |

---

<a id="csscst"></a>

## CSSCST

*Source: [`Content/TransientModels_HTML/Switched Shunt CSSCST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt CSSCST.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0.0 \< T4 \< 0.5\*Mult\*TimeStep then T4 = 0, ElseIf 0.5\*Mult\*TimeStep \< T4 \< Mult\*TimeStep then T4 = Mult\*TimeStep
  - If 0.0 \< T5 \< 0.5\*Mult\*TimeStep then T5 = 0, ElseIf 0.5\*Mult\*TimeStep \< T5 \< Mult\*TimeStep then T5 = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Thyristor \> MaxShuntB, then MaxShuntB= Thyristor or if Thyristor \< MinShuntB, then MinShuntB= Thyristor
      - Originaly, MaxShuntB = SwitchedShuntMaxShuntB and MinShuntB = SwitchedShuntMinShuntB

Model Equations and/or Block Diagrams

See **CSVGN1**, **CSVGN3** and **CSVGN4** for more information.

**Parameters:**

|      |                             |
| ---- | --------------------------- |
| K    | Gain                        |
| T1   | Time constant 1 (sec)       |
| T2   | Time constant 2 (sec)       |
| T3   | Time constant 3 (\<0) (sec) |
| T4   | Time constant 4 (sec)       |
| T5   | Time constant 5 (sec)       |
| VMax | VMax (Mvars)                |
| VMin | VMin (Mvars)                |
| Vov  | Vov (override voltage) (pu) |

---

<a id="facri-ss"></a>

## FACRI_SS

*Source: [`Content/TransientModels_HTML/Switched Shunt FACRI_SS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt FACRI_SS.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|                 |                                                                                       |
| --------------- | ------------------------------------------------------------------------------------- |
| uv1             | Switching Group 1 under voltage level 1 (pu)                                          |
| uv2             | Switching Group 1 under voltage level 2 (pu)                                          |
| uv1td           | Switching Group 1 time delay level 1 (sec)                                            |
| uv2td           | Switching Group 1 time delay level 2 (sec)                                            |
| inttd           | Switching Group 1 first switch time delay, initial time delay (sec)                   |
| uv3             | Voltage at terminal bus that triggers Switching Group 2 switching logic (pu)          |
| uv4             | Switching Group 2 under voltage low level (pu)                                        |
| uv5             | Switching Group 2 under voltage high level (pu)                                       |
| td1             | Switching Group 2 time delay for loop 1 (sec)                                         |
| td2             | Switching Group 2 time delay for loop 2 (sec)                                         |
| td3             | Switching Group 2 time delay for loop 3 (sec)                                         |
| td4             | Switching Group 2 time delay for loop checks (sec)                                    |
| td5             | Duration of time that conditions are checked Monitored Bus b while in each loop (sec) |
| Extra Object 1  | Capacitor 1 – Switching Group 1                                                       |
| Extra Object 2  | Capacitor 2 – Switching Group 1                                                       |
| Extra Object 3  | Reactor 1 – Switching Group 1                                                         |
| Extra Object 4  | Reactor 2 – Switching Group 1                                                         |
| Extra Object 5  | Reactor 3 – Switching Group 1                                                         |
| Extra Object 6  | Capacitor a1 – Switching Group 1                                                      |
| Extra Object 7  | Capacitor a2 – Switching Group 1                                                      |
| Extra Object 8  | Reactor a1 – Switching Group 1                                                        |
| Extra Object 9  | Monitored Bus b – Switching Group 2                                                   |
| Extra Object 10 | Reactor b1 – Switching Group 2                                                        |
| Extra Object 11 | Capacitor b1 – Switching Group 2                                                      |
| Extra Object 12 | Capacitor b2 – Switching Group 2                                                      |

**The following pseudo code describes how the inputs are used to determine switched shunt operation:**

**Switching Group 1 Switching Logic**

Each time that voltage and time delay conditions are met for Switching Group 1, the reactors and capacitors are checked in the following order until a device is found that can be switched. Reactors are tripped and capacitors are closed. Only one device is switched each time switching is required.

(1) Reactor 1

(2) Reactor a1

(3) Reactor 2

(4) Reactor 3

(5) Capacitor 1

(6) Capacitor a1

(7) Capacitor 2

(8) Capacitor a2

**Switching Group 2 Switching Logic**

Each time that voltage and time delay conditions are met for Switching Group 2, if the reactor is online it will be tripped first before any capacitor switching. Depending on voltage conditions, capacitors may or may not be turned on. When capacitors are switched, they are checked in the following order until a device is found that can be switched. Only one capacitor is switched each time switching is required.

(1) Capacitor b1

(2) Capacitor b2

**If** (Reactor online) **Then Begin**

Trip Reactor

**If** (VoltMeasBusb \<= uv4) **Then Begin**

Do capacitor switching

**End**

**End**

**Else If** (not Reactor online) **Then Begin**

**If** (VoltMeasBusb \<= uv4) or (VoltMeasBusb \<= uv5) **Then Begin**

Do capacitor switching

**End**

**End**

**Initialization at the start of transient stability run**

FirstSwitchComplete = False

Initialize Switching Group 2 Loop Trackers

**Operations performed at each time step**

VoltMeas = Voltage at the terminal bus of the switched shunt to which this model is assigned

// If voltage falls below specified thresholds, timers are started to record how long the voltages remain below these thresholds.

// The specific timer pseudo code is not shown here.

**If** (not FirstSwitchComplete) and ( (VoltMeas \< uv1 for inttd) or (VoltMeas \< uv2 for inttd))

**Then Begin**

Check Group 1 Switching

FirstSwitchComplete = True

**End**

**If** (FirstSwitchComplete) **Then Begin**

**If** (VoltMeas \< uv1 for uv1td)

**Then Begin**

Check Group 1 Switching

Reset Group 1 Timer

**End**

**If** (VoltMeas \< uv2 for uv2td)

**Then Begin**

Check Group 1 Switching

Reset Group 1 Timer

**End**

**End**

**If** (VoltMeas \> uv1) **Then Begin**

Reset Group 1 Timers

FirstSwitchComplete = False

**End**

// The condition of VoltMeas \< uv3 triggers the checking of voltages at Monitored Bus b. This latches on for the duration specified by

// td4. The specific timer pseudo code is not shown here, but Group2Timer will be used to keep track of this.

VoltMeasBusb = Voltage at Monitored Bus b

**If** (VoltMeas \< uv3) and (Group2Timer \< td4) **Then Begin**

**If** (Group2Timer \> td1) and (not Group2Loop1Done) **Then Begin**

Check Group 2 Switching

Group2Loop1Done = True

// Continue doing Check Group 2 Switching for td5 until some switching done

**End**

**If** (Group2Timer \> td2) and (not Group2Loop2Done) **Then Begin**

Check Group 2 Switching

Group2Loop2Done = True

// Continue doing Check Group 2 Switching for td5 until some switching done

**End**

**If** (Group2Timer \> td3) and (not Group2Loop3Done) **Then Begin**

Check Group 2 Switching

Group2Loop3Done = True

// Continue doing Check Group 2 Switching for td5 until some switching done

**End**

**End**

**Else If** (Group2Timer \> td4) **Then Begin**

Reset Group 2 Timers

Reset Group 2 Loop Trackers

**End**

---

<a id="msc1"></a>

## MSC1

*Source: [`Content/TransientModels_HTML/Switched Shunt MSC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt MSC1.htm)*

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
<td><p>Find the <span class="underline">highest</span> low voltage value (<strong>Vmin1</strong> or <strong>Vmin2</strong>) specified which has a time-delay associated with it which is less than the <strong>TSModelMaxDelay</strong> specified as part of dynamic model input data (call this <strong>UseLowVolt</strong>). For the value found for <strong>UseLowVolt</strong>, take the corresponding Voltage Trip Time and call this <strong>UseLowVoltTime</strong> (<strong>Tin1</strong> or <strong>Tin2</strong>).</p>
<p> </p>
<p>Find the <span class="underline">lowest</span> high voltage value (<strong>Vmax1</strong> or <strong>Vmax2</strong>) specified which has a time-delay associated with it which is less than the <strong>TSModelMaxDelay</strong> specified as part of dynamic model input data (call this <strong>UseHighVolt</strong>). For the value found for <strong>UseHighVolt</strong>, take the corresponding Voltage Trip Time and call this <strong>UseHighVoltTime</strong> (<strong>Tout1</strong> or <strong>Tout2</strong>).</p>
<p> </p>
<p>Evaluate whether</p>
<p>“Present Voltage PU &gt; <strong>UseHighVolt</strong>” or</p>
<p>“Present Voltage PU &lt; <strong>UseLowVolt</strong>”</p></td>
</tr>
<tr class="odd">
<td><p>TimeDelay used in <strong>Trip/Act</strong></p></td>
<td><p>Time in seconds that the model needs to remain “violated” before it will actually apply an action.</p></td>
<td><p>If Violated because of exceeding <strong>UseHighVolt</strong>, then <strong>TimeDelay</strong> is <strong>UseHighVoltTime</strong></p>
<p>If Violated because of exceeding <strong>UseLowVolt</strong>, then <strong>TimeDelay</strong> is <strong>UseLowVoltTime</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Trip/Act</strong> Action</p></td>
<td><p>If violated for the particular time, then this procedure must be written to actually implement the action.</p></td>
<td><p>If above <strong>UseHighVolt</strong>, then move the switched shunt down one step in Mvar injection</p>
<p>If below <strong>UseLowVolt</strong>, then move the switched shunt up one step in Mvar injection</p></td>
</tr>
</tbody>
</table>

Model Equations and/or Block Diagrams

**Parameters:**

|       |                                 |
| ----- | ------------------------------- |
| Tin1  | Time 1 for Switching in (sec.)  |
| Vmin1 | Voltage lower limit 1 (p.u.)    |
| Tout1 | Time 1 for Switching out (sec.) |
| Vmax1 | Voltage upper limit 1 (p.u.)    |
| Tin2  | Time 2 for Switching in (sec.)  |
| Vmin2 | Voltage lower limit 2 (p.u.)    |
| Tout2 | Time 2 for Switching out (sec.) |
| Vmax2 | Voltage upper limit 2 (p.u.)    |
| Tlck  | Lock out time (sec.)            |

---

<a id="msr1"></a>

## MSR1

*Source: [`Content/TransientModels_HTML/Switched Shunt MSR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt MSR1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Vmax1 \< Vmin1 then swap the values
  - If Vmax2 \< Vmin2 then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

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

<a id="mss1"></a>

## MSS1

*Source: [`Content/TransientModels_HTML/Switched Shunt MSS1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt MSS1.htm)*

**AutoCorrection Properties**

\-None

Model Equations and/or Block Diagrams

**Parameters:**

|         |                                                |
| ------- | ---------------------------------------------- |
| Vlow1   | Voltage threshold Vlow1 (p.u.)                 |
| Vlow2   | Voltage threshold Vlow2 (p.u.)                 |
| Vhigh1  | Voltage threshold Vhigh1 (p.u.)                |
| Vhigh2  | Voltage threshold Vhigh2 (p.u.)                |
| Tbrk    | Time required by MSS breaker to operate (sec.) |
| Tdlow1  | Time dlow 1 for switching in (sec.)            |
| Tdlow2  | Time dlow 2 for switching in (sec.)            |
| Tcount  | Capacitor lock out time (sec.)                 |
| Tdhigh1 | Time dhigh 1 for switching in (sec.)           |
| Tdhigh2 | Time dhigh 2 for switching in (sec.)           |

---

<a id="mss2"></a>

## MSS2

*Source: [`Content/TransientModels_HTML/Switched Shunt MSS2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt MSS2.htm)*

**AutoCorrection Properties**

\-None

Model Equations and/or Block Diagrams

**Parameters:**

|         |                                                |
| ------- | ---------------------------------------------- |
| Vlow1   | Voltage threshold Vlow1 (p.u.)                 |
| Vlow2   | Voltage threshold Vlow2 (p.u.)                 |
| Vhigh1  | Voltage threshold Vhigh1 (p.u.)                |
| Vhigh2  | Voltage threshold Vhigh2 (p.u.)                |
| Tbrk    | Time required by MSS breaker to operate (sec.) |
| Tdlow1  | Time dlow 1 for switching in (sec.)            |
| Tdlow2  | Time dlow 2 for switching in (sec.)            |
| Tcount  | Capacitor lock out time (sec.)                 |
| Tdhigh1 | Time dhigh 1 for switching in (sec.)           |
| Tdhigh2 | Time dhigh 2 for switching in (sec.)           |

**footnotes:** This model is the dame as MSS1 but the difference is that the timers (Tdlow1, Tdhigh1) and (Tdlow2, Tdhigh2) are operated and evaluated independently.

---

<a id="svcals"></a>

## SVCALS

*Source: [`Content/TransientModels_HTML/Switched Shunt SVCALS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVCALS.htm)*

Added in version 19

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< T3 \< Mult\*TimeStep then T3 = Mult\*TimeStep
  - If 0 \< T6 \< Mult\*TimeStep then T6 = Mult\*TimeStep
  - If 0 \< T7 \< Mult\*TimeStep then T7 = Mult\*TimeStep
  - If 0.0 \< T2 \< 0.5\*Mult\*TimeStep then T2 = 0, ElseIf 0.5\*Mult\*TimeStep \< T2 \< Mult\*TimeStep then T2 = Mult\*TimeStep
  - If 0.0 \< T2x \< 0.5\*Mult\*TimeStep then T2x = 0, ElseIf 0.5\*Mult\*TimeStep \< T2x \< Mult\*TimeStep then T2x = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If SlowB \> Vrmax, then Vrmax = SlowB or if SlowB \< Vrmin, then Vrmin = SlowB
  - If Vref \> Vefrmax, then Vrefmax = Vref or if Vref \< Vrefmin, then Vrefmin = Vref
  - If Qsvc \> Qsvcmax, then Qsvcmax = Qsvc or if Qsvc \< Qsvcmin, then Qsvcmin = Qsvc
  - If Itcr \> Itcrmax, then Itcrmax = Itcr or if Itcr \< Itcrmin, then Itcrmin = Itcr
  - If ItcrNum \> -0.006, then ItcrNum = -0.006 or if ItcrNum \< Qtcrmin, then ItcrNum = Qtcrmin
  - If Alpha \> Amax, then Amax = Alpha or if Alpha \< Amin, then Amin = Alpha
  - If Itcrorder \> UL3, then UL3= Itcrorder or if Itcrorder \< LL3, then LL3= Itcrorder
  - If KIV \> UL1, then UL1= KIV or if KIV \< LL1, then LL1 = KIV

Model Equations and/or Block Diagrams

![Switched Shunt SVCALS 0001](images/Switched_Shunt_SVCALS_0001.svg)

![Switched Shunt SVCALS 0002](images/Switched_Shunt_SVCALS_0002.svg)

**Parameters:**

|            |                                                             |
| ---------- | ----------------------------------------------------------- |
| TSC\_FLG   | Flag to indicate whether TSC is in-service or not; 0        |
| MODE\_FLG  | Flag: = 0 Normal mode = 1. Const. current; = 2 Const. MVAR. |
| TBASE      | TCR Base (if TBASE = 0 then TBASE = system base)            |
| BFILTER    | Susceptance of fixed filter on LV bus, p.u. (System base)   |
| BTSC       | Susceptance of TSC, p.u. (System base)                      |
| BTCR\_FC   | Susceptance of TCR at full conduction, p.u. (System base)   |
| KSL        | Slope correction factor                                     |
| SL         | Slope of SVC                                                |
| KIV        | Voltage control PI integrator gain                          |
| KPV        | Voltage control PI proportional gain                        |
| UL1        | Voltage control integral upper limit, p.u.                  |
| LL1        | Voltage control integral lower limit, p.u.                  |
| UL2        | SVC current order upper limit, p.u.                         |
| LL2        | SVC current order lower limit, p.u.                         |
| UL3        | TCR current order upper limit, p.u.                         |
| LL3        | TCR current order lower limit, p.u.                         |
| KTCR       | TCR control gain                                            |
| AMAX       | TCR integral upper limit, degrees                           |
| AMIN       | TCR integral lower limit, degrees                           |
| T2         | SVC current order compensator lag time constant, sec.       |
| KTSCON     | TSC switching deblock threshold, p.u.                       |
| KSSH       | TSC steady-state hysteresis gain, p.u.                      |
| KTRH       | TSC transient hysteresis gain, p.u.,                        |
| T3         | TSC transient hysteresis time constant, sec.                |
| T7         | TSC output lag time constant, sec.                          |
| KKICK      | Kick TCR gain, p.u.                                         |
| T6         | Kick TCR time constant, sec.                                |
| UVL1S      | Undervoltage level1 set, p.u.                               |
| UVL1R      | Undervoltage level1 reset, p.u.                             |
| UVL2S      | Undervoltage level2 set, p.u.                               |
| UVL2R      | Undervoltage level2 reset, p.u.                             |
| TUV1S      | Undervoltage level1 set delay, sec.                         |
| TUV1R      | Undervoltage level1 reset delay, sec.                       |
| TUV2S      | Undervoltage level2 set delay, sec.                         |
| TUV2R      | Undervoltage level2 reset delay, sec.                       |
| MSS\_ON    | MSS switching ON time delay , sec.                          |
| MSS\_ON1   | MSS subsequent switching ON time delay, sec.                |
| MSS\_OFF   | MSS switching OFF time delay, sec.                          |
| MSC\_THR   | MSC threshold, p.u.                                         |
| MSR\_THR   | MSR threshold, p.u.                                         |
| MSS\_Vcoff | MSS cut off voltage, p.u.                                   |
| MSS\_SW\_n | Number of MSS ON/OFF switchings allowed                     |
| MSS\_WAIT  | Wait time for MSS switching after switching OFF, sec.       |
| VSVCMAX    | Max. voltage at SVC bus, p.u.                               |
| ITCRMAX    | Max. TCR current, p.u. TBASE                                |
| ITCRMIN    | Min. TCR current, p.u. on TBASE                             |
| QSVCMAX    | Max. SVC reactive power, Mvar                               |
| QSVCMIN    | Min. SVC reactive power, Mvar                               |
| ISVCMAX    | Max. SVC current, p.u.                                      |
| ISVCMIN    | Min. SVC current, p.u.                                      |
| KPS        | Proportional gain of slow susceptance control (SSC)         |
| KIS        | Integral gain of slow susceptance control (SSC)             |
| VRMAX      | SSC PI-controller maximum output                            |
| VRMIN      | SSC PI-controller minimum output                            |
| EPS        | Small delta added to the SSC susceptance bandwidth          |
| BSCS       | Smaller threshold for switching MSCs Mvar                   |
| BSIS       | Smaller threshold for switching MSRs, Mvar                  |
| MSS\_FLG   | Flag: 1 or 0 = Allow or do not allow MSS switching          |
| T1X        | Lead constant for Lead Lag Time constant, sec.              |
| T2X        | Lag constant for Lead Lag Time constant, sec.               |
| T1         | SVC current order compensator lead time constant, sec.      |

---

<a id="svsmo1"></a>

## SVSMO1

*Source: [`Content/TransientModels_HTML/Switched Shunt SVSMO1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVSMO1.htm)*

Some important [SVC Control Considerations when running Transient Stability](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode-and-transient-simulation).

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If 0.0 \< Tdelay1 \< 0.5\*Mult\*TimeStep then Tdelay1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay1 \< Mult\*TimeStep then Tdelay1 = Mult\*TimeStep
  - If 0.0 \< Tdelay2 \< 0.5\*Mult\*TimeStep then Tdelay2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay2 \< Mult\*TimeStep then Tdelay2 = Mult\*TimeStep
  - Xc1: Xc1 value should matchthe Xc value in the power flow model, if not the same the then Xc1 parameter is autocorrected to the Xc value of the power flow model.
  - Kiv: If Kiv \> 1/(2\*TimeStep) then Kiv = 1/(2\*TimeStep)
  - Kis: If Kis \> 1/(2\*TimeStep) then Kis = 1/(2\*TimeStep)

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If SlowB \> Vrmax, then Vrmax = SlowB or if SlowB \< Vrmin, then Vrmin = SlowB
  - If Vref \> Vefrmax, then Vrefmax = Vref or if Vref \< Vrefmin, then Vrefmin = Vref
  - If Verr \> Vemax, then Vemax = Verr or if Verr \< Vemin, then Vemin = Verr
  - If Bpi \> Bmax, then Bmax = Bpi or if Bpi \< Bmin, then Bmin = Bpi

Model Equations and/or Block Diagrams

![Switched Shunt SVSMO1 0001](images/Switched_Shunt_SVSMO1_0001.svg)

**Parameters:**

|          |                                                                                |
| -------- | ------------------------------------------------------------------------------ |
| UVSBmax  | Maximum capacitive limit during undervoltage strategy                          |
| UV1      | Under Voltage Setpoint 1, pu                                                   |
| UV2      | Under Voltage Setpoint 2, pu                                                   |
| UVT      | Under Voltage Trip Setting Time, sec                                           |
| OV1      | Over Voltage Setpoint 1, pu                                                    |
| OV2      | Over Voltage Setpoint 2, pu                                                    |
| UVtm1    | Under Voltage Trip Time 1, sec                                                 |
| UVtm2    | Under Voltage Trip Time 2, sec                                                 |
| OVtm1    | Over Voltage Trip Time 1, sec                                                  |
| OVtm2    | Over Voltage Trip Time 2, sec                                                  |
| Flag1    | MSS Switching enabled(1) or disabled(0)                                        |
| Flag2    | Liner(0) or Non-linear(1) Slope                                                |
| Xc1      | Slope (nominal linear slope or first section of piecewise linear slope, pu/pu) |
| Xc2      | Slope of second section of piecewise linear slope, pu/pu                       |
| Xc3      | Slope of third section of piecewise linear slope, pu/pu                        |
| Vup      | Upper Voltage Break-point for non-linear slope, pu                             |
| Vlow     | Lower Voltage Break-point for non-linear slope, pu                             |
| Tc1      | Voltage measurement lead time constant, sec                                    |
| Tb1      | Voltage measurement lag time constant, sec                                     |
| Tc2      | Lead time constant for transient gain reduction, sec                           |
| Tb2      | Lag time constant for transient gain reduction, sec                            |
| Kpv      | Voltage regulator proportional gain, pu/pu                                     |
| Kiv      | Voltage regulator integral gain, pu/pu                                         |
| Vemax    | Max. allowed voltage error, pu                                                 |
| Vemin    | Min. allowed voltage error, pu                                                 |
| T2       | Firing delay time constant, sec                                                |
| Bshrt    | Short-term max. capacitive rating of the SVC, pu                               |
| Bmax     | Continuous max. capacitive rating of the SVC, pu                               |
| Bmin     | Continuous min. inductive rating of the SVC, pu                                |
| Tshrt    | Short-term rating definite time delay, sec                                     |
| Kps      | Proportional gain of slow-susceptance regulator, pu/pu                         |
| Kis      | Integral gain of slow-susceptance regulator, pu/pu                             |
| Vrmax    | Max. Allowed PI controller output of slow-susceptance regulator, pu            |
| Vrmin    | Min. Allowed PI controller output of slow-susceptance regulator, pu            |
| Vdbd1    | Steady-state deadband, pu                                                      |
| Vdbd2    | Inner voltage deadband, pu                                                     |
| Tdbd     | Definite time deadband delay, sec                                              |
| PLLdelay | PLL delay in recovering if voltage remains below UV1 for more than UVtm1, sec  |
| Eps      | Small delta added to the susceptance bandwidth, MVAr                           |
| Blcs     | Large threshold for switching MSS in capacitive side, MVAr                     |
| Bscs     | Small threshold for switching MSS in capacitive side, MVAr                     |
| Blis     | Large threshold for switching MSS in inductive side, MVAr                      |
| Bsis     | Small threshold for switching MSS in inductive side, MVAr                      |
| Tmssbrk  | MSS breaker switch delay, sec                                                  |
| Tdelay1  | Definite time delay for large switching threshold, sec                         |
| Tdelay2  | Definite time delay for small switching threshold, sec                         |
| Tout     | Discharge time for mechanically switched capacitors, sec                       |

---

<a id="svsmo1-ak-a"></a>

## SVSMO1_AK_A

*Source: [`Content/TransientModels_HTML/Switched Shunt SVSMO1_AK_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVSMO1_AK_A.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="svsmo1-ak-b"></a>

## SVSMO1_AK_B

*Source: [`Content/TransientModels_HTML/Switched Shunt SVSMO1_AK_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVSMO1_AK_B.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="svsmo2"></a>

## SVSMO2

*Source: [`Content/TransientModels_HTML/Switched Shunt SVSMO2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVSMO2.htm)*

Some important [SVC Control Considerations when running Transient Stability](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode-and-transient-simulation).

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If 0.0 \< Tdelay1 \< 0.5\*Mult\*TimeStep then Tdelay1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay1 \< Mult\*TimeStep then Tdelay1 = Mult\*TimeStep
  - If 0.0 \< Tdelay2 \< 0.5\*Mult\*TimeStep then Tdelay2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay2 \< Mult\*TimeStep then Tdelay2 = Mult\*TimeStep
  - Xc1: Xc1 value should matchthe Xc value in the power flow model, if not the same the then Xc1 parameter is autocorrected to the Xc value of the power flow model.
  - Kiv: If Kiv \> 1/(2\*TimeStep) then Kiv = 1/(2\*TimeStep)
  - Kis: If Kis \> 1/(2\*TimeStep) then Kis = 1/(2\*TimeStep)

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If SlowB \> Vrmax, then Vrmax = SlowB or if SlowB \< Vrmin, then Vrmin = SlowB
  - If Vref \> Vefrmax, then Vrefmax = Vref or if Vref \< Vrefmin, then Vrefmin = Vref
  - If Verr \> Vemax, then Vemax = Verr or if Verr \< Vemin, then Vemin = Verr
  - If Bpi \> Bmax, then Bmax = Bpi or if Bpi \< Bmin, then Bmin = Bpi

Model Equations and/or Block Diagrams

![Switched Shunt SVSMO2 0001](images/Switched_Shunt_SVSMO2_0001.svg)

**Parameters:**

|          |                                                                                |
| -------- | ------------------------------------------------------------------------------ |
| UVSBmax  | Maximum capacitive limit during undervoltage strategy                          |
| UV1      | Under Voltage Setpoint 1, pu                                                   |
| UV2      | Under Voltage Setpoint 2, pu                                                   |
| UVT      | Under Voltage Trip Setting Time, sec                                           |
| OV1      | Over Voltage Setpoint 1, pu                                                    |
| OV2      | Over Voltage Setpoint 2, pu                                                    |
| UVtm1    | Under Voltage Trip Time 1, sec                                                 |
| UVtm2    | Under Voltage Trip Time 2, sec                                                 |
| OVtm1    | Over Voltage Trip Time 1, sec                                                  |
| OVtm2    | Over Voltage Trip Time 2, sec                                                  |
| Flag1    | MSS Switching enabled(1) or disabled(0)                                        |
| Flag2    | Liner(0) or Non-linear(1) Slope                                                |
| Xc1      | Slope (nominal linear slope or first section of piecewise linear slope, pu/pu) |
| Xc2      | Slope of second section of piecewise linear slope, pu/pu                       |
| Xc3      | Slope of third section of piecewise linear slope, pu/pu                        |
| Vup      | Upper Voltage Break-point for non-linear slope, pu                             |
| Vlow     | Lower Voltage Break-point for non-linear slope, pu                             |
| Tc1      | Voltage measurement lead time constant, sec                                    |
| Tb1      | Voltage measurement lag time constant, sec                                     |
| Tc2      | Lead time constant for transient gain reduction, sec                           |
| Tb2      | Lag time constant for transient gain reduction, sec                            |
| Kpv      | Voltage regulator proportional gain, pu/pu                                     |
| Kiv      | Voltage regulator integral gain, pu/pu                                         |
| Vemax    | Max. allowed voltage error, pu                                                 |
| Vemin    | Min. allowed voltage error, pu                                                 |
| T2       | Firing delay time constant, sec                                                |
| Bshrt    | Short-term max. capacitive rating of the SVC, pu                               |
| Tshrt    | Short-term rating definite time delay, sec                                     |
| Kps      | Proportional gain of slow-susceptance regulator, pu/pu                         |
| Kis      | Integral gain of slow-susceptance regulator, pu/pu                             |
| Vrmax    | Max. Allowed PI controller output of slow-susceptance regulator, pu            |
| Vrmin    | Min. Allowed PI controller output of slow-susceptance regulator, pu            |
| Vdbd1    | Steady-state deadband, pu                                                      |
| Vdbd2    | Inner voltage deadband, pu                                                     |
| Tdbd     | Definite time deadband delay, sec                                              |
| PLLdelay | PLL delay in recovering if voltage remains below UV1 for more than UVtm1, sec  |
| Eps      | Small delta added to the susceptance bandwidth, MVAr                           |
| Blcs     | Large threshold for switching MSS in capacitive side, MVAr                     |
| Bscs     | Small threshold for switching MSS in capacitive side, MVAr                     |
| Blis     | Large threshold for switching MSS in inductive side, MVAr                      |
| Bsis     | Small threshold for switching MSS in inductive side, MVAr                      |
| Tmssbrk  | MSS breaker switch delay, sec                                                  |
| Tdelay1  | Definite time delay for large switching threshold, sec                         |
| Tdelay2  | Definite time delay for small switching threshold, sec                         |
| Tout     | Discharge time for mechanically switched capacitors, sec                       |
| dbe      | Voltage error deadband, pu                                                     |
| dbb      | Susceptance deadband, pu                                                       |
| PrintB   | Print All unique posible combinations of TSCs and TSRs                         |

---

<a id="svsmo3"></a>

## SVSMO3

*Source: [`Content/TransientModels_HTML/Switched Shunt SVSMO3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SVSMO3.htm)*

Some important [SVC Control Considerations when running Transient Stability](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode-and-transient-simulation).

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If 0.0 \< Tdelay1 \< 0.5\*Mult\*TimeStep then Tdelay1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay1 \< Mult\*TimeStep then Tdelay1 = Mult\*TimeStep
  - If 0.0 \< Tdelay2 \< 0.5\*Mult\*TimeStep then Tdelay2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tdelay2 \< Mult\*TimeStep then Tdelay2 = Mult\*TimeStep
  - Xc0: Xc0 value should matchthe Xc value in the power flow model, if not the same the then Xc1 parameter is autocorrected to the Xc value of the power flow model.
  - Ki: If Ki \> 1/(2\*TimeStep) then Ki = 1/(2\*TimeStep)
  - Kir: If Kir \> 1/(2\*TimeStep) then Kir = 1/(2\*TimeStep)

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If SlowB \> Vrmax, then Vrmax = SlowB or if SlowB \< Vrmin, then Vrmin = SlowB
  - If Vref \> Vefrmax, then Vrefmax = Vref or if Vref \< Vrefmin, then Vrefmin = Vref
  - If Verr \> Vemax, then Vemax = Verr or if Verr \< Vemin, then Vemin = Verr
  - If Bpi \> Bmax, then Bmax = Bpi or if Bpi \< Bmin, then Bmin = Bpi

Model Equations and/or Block Diagrams

![Switched Shunt SVSMO3 0001](images/Switched_Shunt_SVSMO3_0001.svg)

**Parameters:**

|         |                                                                      |
| ------- | -------------------------------------------------------------------- |
| modbase | Model Base, MVA                                                      |
| Xc0     | Constant linear drop, pu)                                            |
| Tc1     | Voltage measurement lead time constant, sec                          |
| Tb1     | Voltage measurement lag time constant, sec                           |
| Kp      | Voltage regulator proportional gain, pu/pu                           |
| Ki      | Voltage regulator integral gain, pu/pu sec                           |
| vemax   | Max. allowed voltage error, pu                                       |
| vemin   | Min. allowed voltage error, pu                                       |
| To      | Firing sequence control delay, sec                                   |
| Imax1   | Max. continuous current rating, pu on model MVA base                 |
| dbd     | Voltage control deadband, pu                                         |
| Kdbd    | Ratio of outer to inner deadband, pu                                 |
| Tdbd    | Deadband time, sec                                                   |
| Kpr     | Proportional gain for slow reset control, pu/pu                      |
| Kir     | Integral gain for slow reset control, pu/pu sec                      |
| Idbd    | Deadband range for slow reset control, pu                            |
| Vrmax   | Maximum limit of slow reset control, pu                              |
| Vrmin   | Minimum limit of slow reset control, pu                              |
| Ishrt   | Max. short term current rating as multiple of continuous rating, pu  |
| UV1     | Voltage at which performance limit starts to be reduced lineraly, pu |
| UV2     | Voltage below which performance limit is blocked, pu                 |
| OV1     | Voltage above which limit lineraly drops, pu                         |
| OV2     | Voltage above which blocks its output, pu                            |
| Vtrip   | Voltage above which trips after Tdelay2, pu                          |
| Tdelay1 | Short term rating delay, sec                                         |
| Tdelay2 | Trip time for V \> Vtrip, sec                                        |
| ecap    | Enable(1) or disable(0) MSS switching                                |
| Iupr    | Upper threshold for switching MSS, pu                                |
| Ilwr    | Lower threshold for switching MSS, pu                                |
| TdelLC  | Time delay for switching in a shunt, sec                             |
| Tout    | Time cap. bank should be out before switching back, sec              |
| sdelay  | Delay, sec                                                           |
| I2t     | I2t limit, pu pu sec                                                 |
| Reset   | Reset rate I2t limit, pu pu                                          |
| hyst    | Hysteresis, pu                                                       |
| Flag1   | Slow reset is On(1) or Off(0)                                        |
| Flag2   | Non-linear droop is On(1) or Off(0)                                  |
| Xc1     | Non-linear droop slope 1, pu/pu)                                     |
| Xc2     | Non-linear droop slope 2, pu/pu                                      |
| Xc3     | Non-linear droop slope 3, pu/pu                                      |
| V1      | Non-linear droop upper voltage, pu                                   |
| V2      | Non-linear droop lower voltage, pu                                   |
| Tc2     | Lead time constant, sec                                              |
| Tb2     | Lag time constant, sec                                               |
| Tmssbrk | MSS breaker switch delay, sec                                        |

---

<a id="swshnt"></a>

## SWSHNT

*Source: [`Content/TransientModels_HTML/Switched Shunt SWSHNT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Switched Shunt SWSHNT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

**Parameters:**

|     |                                                                             |
| --- | --------------------------------------------------------------------------- |
| Ib  | Remote Bus                                                                  |
| NS  | Total number of switches allowed                                            |
| VIN | High voltage limit                                                          |
| PT  | Pickup time for high voltage in sec.                                        |
| ST  | Switch time to close if reactor or switch time to open if capacitor in sec. |
| VIN | Low voltage limit                                                           |
| PT  | Pickup time for low voltage in sec                                          |
| ST  | Switch time to close if reactor or switch time to open if capacitor in sec. |
