---
title: "Transient Stability — Overview and Data (Part 1 of 2)"
part: "Transient Stability"
chapter_file: "36-transient-stability-overview-and-data-part1.md"
topics: 21
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Transient Stability — Overview and Data (Part 1 of 2)

Transient stability concepts, data management and model handling.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (21)**

- [Transient Stability Overview](#transient-stability-overview)
- [Generator Models](#generator-models)
- [Excitation Limiters](#excitation-limiters)
- [Output Signal of an Excitation Limiter](#output-signal-of-an-excitation-limiter)
- [Compatibility between Excitation Limiter models and Exciter models](#compatibility-between-excitation-limiter-models-and-exciter-models)
- [Auto-Correction at Excitation Limiter Models](#auto-correction-at-excitation-limiter-models)
- [Initialization of Excitation Limiters](#initialization-of-excitation-limiters)
- [Modification of Limits at Excitation Limiters during Initialization](#modification-of-limits-at-excitation-limiters-during-initialization)
- [Renewable Energy Generation Models (Wind, Solar, Energy Storage, Distributed Photo Voltaic)](#renewable-energy-generation-models-wind-solar-energy-storage-distributed-photo-voltaic)
- [Load Models](#load-models)
- [Load Characteristics](#load-characteristics)
- [Load Component and CompLoad characteristic](#load-component-and-compload-characteristic)
- [Load Distribution Equivalent](#load-distribution-equivalent)
- [Load Distributed Generation](#load-distributed-generation)
- [Load Relay Modeling](#load-relay-modeling)
- [Load Model Group](#load-model-group)
- [Load model translation from DYD files](#load-model-translation-from-dyd-files)
- [Load Model Group - CMPLDWNF Load Model](#load-model-group---cmpldwnf-load-model)
- [Line Relay Modeling](#line-relay-modeling)
- [Switched Shunt Models](#switched-shunt-models)
- [DC Transmission Lines](#dc-transmission-lines)

---

<a id="transient-stability-overview"></a>

## Transient Stability Overview

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**The Transient Stability tool is available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for more details.****

Transient stability studies analyze the system response to disturbances such as the loss of generation, line-switching operations, faults, and sudden load changes in the first several seconds following the disturbance. Following a disturbance, synchronous machine frequencies undergo transient deviations from synchronous frequency. The objective of a transient stability study is to determine whether or not machines will return to synchronous frequency following a disturbance.

For more detail on the transient stability modeling see the following links

  - [Generator Modeling](#generator-models)
  - [Renewable Energy Generation Models (Wind, Solar, Energy Storage, Distributed Photo Voltaic)](#renewable-energy-generation-models-wind-solar-energy-storage-distributed-photo-voltaic)
  - [Load Characteristic and Distributed Generation Modeling](#load-models)
  - [Load Relay Modeling](#load-relay-modeling)
  - [Line Relay Modeling](#line-relay-modeling)
  - [Transient Stability Models: Switched Shunt Models](#switched-shunt-models)
  - [DC Transmission Line Modeling](#dc-transmission-lines)
  - [Available Generation Control (AGC) Modeling](36-transient-stability-overview-and-data-part2.md#available-generation-control-agc-modeling)
  - [Transient Stability Numerical Integration](36-transient-stability-overview-and-data-part2.md#integration-techniques)
  - [PlayIn Modeling](36-transient-stability-overview-and-data-part2.md#playin-modeling)
  - [User Defined Models](36-transient-stability-overview-and-data-part2.md#user-defined-models)

For more detail on how to use the Transient Stability tool see the following links

[Transient Stability: Model Data Management](36-transient-stability-overview-and-data-part2.md#transient-stability-data-management)

  - [Stability tab of the Generator, Load, DC Line, etc... Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs)
  - [Transient Stability Case Information Drop-Down](36-transient-stability-overview-and-data-part2.md#case-info-menu)
  - [Transient Stability Folder in the Model Explorer](36-transient-stability-overview-and-data-part2.md#model-explorer)
  - [Transient Stability Block Diagrams](36-transient-stability-overview-and-data-part2.md#block-diagrams)
  - [Reading/Writing Transient Stability Data to various File Formats](36-transient-stability-overview-and-data-part2.md#data-from-external-files)

[Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog)

  - [Simulation](37-transient-stability-analysis-dialog-part1.md#simulation)
  - [Options](37-transient-stability-analysis-dialog-part1.md#options)
  - [Results Storage](37-transient-stability-analysis-dialog-part1.md#results-storage)
  - [Plots](37-transient-stability-analysis-dialog-part2.md#plots)
  - [Results](37-transient-stability-analysis-dialog-part3.md#results-from-ram)
  - [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors)
  - [States/Manual Control](37-transient-stability-analysis-dialog-part3.md#statesmanual-control)
  - [Validation](37-transient-stability-analysis-dialog-part3.md#validation)
  - [SMIB Eigenvalues](37-transient-stability-analysis-dialog-part3.md#smib-eigenvalues)

---

<a id="generator-models"></a>

## Generator Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Generator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Generator.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generator models are the most complex models in a transient stability tool. Generators can have many classes of dynamic model assigned to them including the following types.

  - Machine Model (or converter model for renewal
  - Exciter Model (or electrical control for renewable)
  - Governor Model (or mechanical control for renewable)
  - Stabilizer Model (or pitch control)
  - Under Excitation Limiter
  - Over Excitation Limiter
  - Compensator Model
  - Aerodynamic Model
  - Pref Controller
  - Plant Controller
  - AGC Controller
  - Relay Models

You may define multiple models of each class of model to a generator, but for all types of models (except relays) there can be only one *active* model with a Criteria that evaluates to TRUE.

The relationship between the four primary model (machine, exciter, governor, and stabilizer) is shown in the figure below, along with the variables which are passed between the models. This is not an exhaustive list, but represents the typical relationships between the models. For renewable energy generator models (wind, solar, energy storage, solar pv, etc.), similar relationships exist between a wind machine model, electrical model, mechanical model, and a pseudo-governor model. For more information about wind turbine modeling in Simulator, see the [Renewable Energy Generation Modeling](#renewable-energy-generation-models-wind-solar-energy-storage-distributed-photo-voltaic) help topic.

![Transient Overview Generator Model Relationships](images/Transient_Overview_Generator_Model_Relationships.gif) ![Transient Overview Generator Model Relationships Equations](images/Transient_Overview_Generator_Model_Relationships_Equations.gif)

Governor Response Limits

There is a special generator field in Simulator called *Transient Stability\\Governor Response Limits*. The field determines the response of the governor control limits during a transient stability run. Options are *Normal*, *Down Only*, or *Fixed*. When loading from an EPC file a Baseload flag value of 0 maps Normal, 1 maps to Down Only, and 2 or more maps to Fixed.

A value of *Normal* means that the limits specified in the governor model will be used for the simulation. A value of *Down Only* means that the upper limit is set equal to the initial condition value (and thus control can only go down). A value of *Fixed* means that both the upper and lower limits are set equal to the initial condition (and thus control will be approximately constant). Note that the power output of the generator can still vary for those turbines whose MW output is sensitive to speed (because the speed can obviously still vary).

Also, this field will always be shown as a default field when looking at a case information display showing a list of governors.

Special Accommodation for handling Line Drop Compensation

In modeling the WECC system, a stability issue was encountered at several hydro units such as John Day. The issue, which is described in the papers listed below, arises because of how the exciters for some hydro units with dual generators have been configured to enhance system voltage stability. Rather than regulating their terminal voltage, or a point internal to the generator (using compensation), the generator exciters have been configured using line drop compensation to regulate a point midway through the step-up transformer. This is illustrated in the below figure, which reproduces Figure 3 from the Murdoch/Sanchez-Gasca paper below. The advantage of this approach is it allows the generator exciters to directly regulate a point close to the transmission system (perhaps 50 to 80% of the way through the step-up transformer). If there is just one generator feeding through the transformer then this control can be modeled in the normal fashion. However when there are two generators, an extremely common configuration at hydro plants, physically the exciter inputs at each plant need to receive the currents from both machines in order to insure they are both regulating the same line drop compensated voltage. If this is not done, then the controls will end up fighting each other, driving the excitation current for one generator to its maximum and for the other generator to its minimum. Therefore to correctly model this situation, the PowerWorld Simulator transient stability excitation modeling code has been enhanced to include both generator currents in situations in which line drop compensation causes the regulated voltage to be beyond the generator’s terminal. Otherwise the traditional code is used.

![Transient Stability Overview DualLineDrop](images/Transient_Stability_Overview_DualLineDrop.gif)

NOTE:

When modeling a GENCLS model with H=0 and D=0 it is treated as an infinite bus.

A. Murdoch, J.J. Sanchez-Gasca, “Excitation Control for High Side Voltage Regulation,” Proc. IEEE PES 2000 Summer Meeting, July 2000, pp. 285-289.

C.W. Taylor, “Line drop compensation, high side voltage control, secondary voltage control – why not control a generator like a static var compensator,” Proc. IEEE PES 2000 Summer Meeting, July 2000, pp. 307-310

---

<a id="excitation-limiters"></a>

## Excitation Limiters

*Source: [`Content/MainDocumentation_HTML/transient_stability_overview_Excitation_Limiters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/transient_stability_overview_Excitation_Limiters.htm)*

An exciter model is central to representing a generator's excitation system. The field voltage output from an exciter is used to excite the field winding of an electric machine, and the level of excitation determines the generator's reactive power output. At each level of active power (MW) output, the generator has minimum and maximum limits on the amount of the reactive power (Mvar) that it is safely capable of providing. These reactive power bounds might not be adequately represented by just the static limits found in exciter models. To allow for more detailed modeling in this aspect, there are additional excitation limiter models that can be configured with an exciter model. These limiter models would then work in synergy to limit the field voltage, and hence limit the generator's reactive power output during a dynamic simulation.

There are 3 types of excitation limiters:

  - Under excitation limiter (UEL), which prevents the generator from exceeding its core-end heating limit and/or its stability limit, when it is operating at a leading power factor, i.e., absorbing Mvar.

  - Over excitation limiter (OEL), which prevents the generator from exceeding its field current heating limit, when it is operating at a lagging power factor, i.e., supplying Mvar.

  - Stator current limiter (SCL), which prevents the generator from exceeding its stator current heating limit, when it is operating at a high active power output, but is not limited by an UEL or OEL constraint.

The bounds enforced by these excitation limiters would actually be similar to the limits defined by a generator capability curve. This is also known as a D-curve, which is often part of a generator's input data in power flow studies. In contrast, UEL, OEL and SCL dynamic models also have a dynamic response in addition to enforcing these bounds, and some of these models could also enforce time-varying limits based on an activation logic.

All UEL/OEL models have a transient stability result field called **Activation Status** that succinctly captures their current operation. In all SCL models, there are two fields called **UEL Activation Status** and **OEL Activation Status** reflecting under or over excitation limiting action.

  - *Idle*: *Activation Status* = 0, or *UEL Activation Status* = 0, or *OEL Activation Status* = 0

    Activation logic is not triggered.  
    For UEL/SCL models: Output signal is V<sub>UEL-MIN</sub>  
    For OEL/SCL models: Output signal is V<sub>OEL-MAX</sub>  

  - *Engaged*: *Activation Status* = 1, or *UEL Activation Status* = 1, or *OEL Activation Status* = 1

    The limiter model's activation logic is triggered, and the output is varying between its lower and upper limits  
    For UEL/SCL models: Output signal is in the range (V<sub>UEL-MIN</sub>, V<sub>UEL-MAX</sub>)  
    For OEL/SCL models: Output signal is in the range (V<sub>OEL-MIN</sub>, V<sub>OEL-MAX</sub>)

  - *Saturated*: *Activation Status* = 2, or *UEL Activation Status* = 2, or *OEL Activation Status* = 2

    The limiter model's activation logic is triggered, but the output is already capped  
    For UEL/SCL models: Output signal is V<sub>UEL-MAX</sub>  
    For OEL/SCL models: Output signal is V<sub>OEL-MIN</sub>

---

<a id="output-signal-of-an-excitation-limiter"></a>

## Output Signal of an Excitation Limiter

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Output_Input.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Output_Input.htm)*

Within the framework of generic models, the signal(s) interfacing between an UEL/OEL/SCL and its respective exciter model is such that the output signal from an excitation limiter is either received at a summation point or a takeover gate at the exciter. These two types of location actually expect two different type of signals (differences are discussed later in this topic).

This means that a limiter model could be of a type that outputs a summation point signal or a takeover gate signal, or a limiter model's output could be configurable. Similarly, some exciters accept a limiter signal only at a summation point or only at a takeover gate, or they could also be configurable. Since a summation point limiter output signal is <span class="underline">not</span> compatible as an input signal at a takeover gate, and vice versa, this naturally brings up the question whether a specific limiter model is compatible with a specific exciter model. Also, there are certain older exciter models that do not have an input for an UEL/OEL/SCL – the exciter model would need to be upgraded to so that a limiter models can be used.

Inappropriate combination of an UEL/OEL/SCL and an exciter can cause exciters to have atypical signal clamping (if a summation point signal were to be fed into a takeover gate), or abnormally large error signals (if a takeover gate signal were to be fed into a summation point). Both this situations will result in weird and unintended consequences during the dynamic simulation. To understand why, it is important to draw the distinction between summation points and takeover gates.

  - A summation point input signal at an exciter (from a compatible excitation limiter model) typically feeds in at the voltage reference signal. This serves to automatically modify the voltage reference signal in response to a control action from an UEL/OEL/SCL, and can occur in addition to manual changes to the voltage reference "knob" or digital reference.

      - When an UEL/OEL/SCL is <span class="underline">not yet activated</span>, the UEL/SCL<sub>UEL</sub>/OEL/SCL<sub>OEL</sub> signal should be <span class="underline">zero</span>.

      - When an UEL/SCL limiter is <span class="underline">activated due to under-excitation</span>, the UEL/SCL<sub>UEL</sub> signal would be *positive* (typically between 0.1 to 0.3 p.u.).

      - When an OEL/SCL limiter is <span class="underline">activated due to over-excitation</span>, the OEL/SCL<sub>OEL</sub> signal would be *negative* (typically between -0.3 to -0.1 p.u.).

    In general, a summation point output signal would typically vary around 0 ± 0.3 p.u.

  - A takeover gate input signal at an exciter (from a compatible excitation limiter model) feeds in either at a high‑value select (HV) gate (for UEL/SCL<sub>UEL</sub> signals) or at a low‑value select (LV) gate (for OEL/SCL<sub>OEL</sub> signals). Respectively, this serves as a time-varying lower limit or upper limit to restrict the internal excitation signal, in response to a control action from an UEL/OEL/SCL.

      - When an UEL/OEL/SCL is <span class="underline">not yet activated</span>, the UEL/SCL<sub>UEL</sub> (or OEL/SCL<sub>OEL</sub>) signal should be *less than the static lower limit (or greater than the static upper limit)* at the exciter's internal.

      - When an UEL/SCL limiter is <span class="underline">activated due to under-excitation</span>, the UEL/SCL<sub>UEL</sub> signal would be *greater than the static lower limit* at the exciter's internal.

      - When an OEL/SCL limiter is <span class="underline">activated due to over-excitation</span>, the OEL/SCL<sub>OEL</sub> signal would be *less than the static upper limit* at the exciter's internal.

    In general, a takeover point output signal would typically not be around the value of 0 p.u.

PowerWorld Simulator has compatibility checks in place to prevent inappropriate UEL/OEL/SCL-exciter combinations. For example, excitation limiter OEL4C is not compatible with exciter ESST1A, because ESST1A only accepts a takeover gate OEL input signal but OEL4C can only provide a summation point OEL output signal.

---

<a id="compatibility-between-excitation-limiter-models-and-exciter-models"></a>

## Compatibility between Excitation Limiter models and Exciter models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Compatibility.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Compatibility.htm)*

PowerWorld Simulator has compatibility checks in place to prevent inappropriate UEL/OEL/SCL-exciter combinations. For example, excitation limiter OEL4C is not compatible with exciter ESST1A, because ESST1A only accepts a takeover gate OEL input signal but OEL4C can only provide a summation point OEL output signal.

The remainder of this topic lists the output and input related fields associated with limiter and exciter models. This helps in keeping track of whether models are compatible, which then allows for [auto-correction](#auto-correction-at-excitation-limiter-models) and [modification of limits to prevent initial limit violations](#modification-of-limits-at-excitation-limiters-during-initialization). Ultimately, this ensures proper [initialization of UELs, OELs and SCLs](#initialization-of-excitation-limiters).

Exciter Models

Excitation Limiter Input Signal Type(s)

Depending on the specific type and instance of an exciter model, it might accept an UEL/OEL/SCL input signal at different locations. Exciter models have three fields that specify the input signal types that could be accepted from an UEL, an OEL and a SCL:  
*UEL Input Type(s)* (UELInputTypes)  
*OEL Input Type(s)* (OELInputTypes)  
*SCL Input Types(s)* (SCLInputTypes)

Possible values for these fields are:

1.  *\[No Input\]* – The exciter type does not have an input for a limiter model.  
    Many of the older exciter models do not have a SCL input, and a handful of the older exciter models do not have a UEL/OEL input.  
    Renewable exciter models that actually represent power electronic controls are not compatible, and hence do not have a UEL/OEL/SCL input.

2.  *\[Summation Point\]* – The exciter type only has a summation point input for a limiter model.  
    Many of the older exciter models only have a summation point UEL/OEL input.

3.  *\[Takeover Gate\]* – The exciter type only has a takeover gate input for a limiter model.  
    Some IEEE Revision B exciter models only have a takeover gate UEL/OEL input.

4.  *\[Summation Point, Takeover Gate\]* – The exciter type can be configured to accept an UEL/OEL/SCL signal at its summation point input, or its takeover gate input, or not use the signal.  
    All IEEE revision C and some revision A/B exciter models have configurable UEL/OEL/SCL input.

Excitation Limiter Input Signal Used

There are three additional fields at exciter models that specify the actual input signal used for an UEL, an OEL and a SCL:  
*UEL Input Used* (UELInputUsed)  
*OEL Input Used* (OELInputUsed)  
*SCL Input Used* (SCLInputUsed)  
If an exciter can be configured to accept either a summation point signal or a takeover gate signal from a limiter model, then these fields will reflect the current configuration of a specific exciter instance. Otherwise, these fields will show the same value as the single choice from the corresponding *UEL/OEL/SCL Input Type(s)* fields.

Possible values for these fields are:

1.  *Summation Point* – The exciter will use a summation point input signal.

2.  *Takeover Gate* – The exciter will use a takeover gate input signal.

3.  *No Input* – The exciter type does not have any input location for a UEL/OEL/SCL input signal.

4.  *Not Used* – The specific exciter instance is configured to ignore a UEL/OEL/SCL input signal.

Excitation Limiter Models

Output Signal Type(s)

Depending on the specific type and instance of an excitation limiter model, it might produce a summation point signal or a takeover gate signal. Excitation limiter models have one field that specifies the output signal type that could be produced by an UEL, or an OEL, or an SCL:  
**Output Type(s)** (OutputTypes)

Possible values for this field are:

1.  *\[Summation Point\]* – The excitation limiter type only has a summation point output for an exciter model.  

2.  *\[Takeover Gate\]* – The excitation limiter type only has a takeover gate output for an exciter model.

3.  *\[Summation Point, Takeover Gate\]* – The excitation limiter type can be configured to produce a summation point output signal, or a takeover gate output signal.

Output Signal Used

There is one additional field at excitation limiter models that specifies the actual output signal by the exciter:  
**Output Used** (OutputUsed)  
This field will take into consideration the expected input at the active exciter, and check its compatibility with the choices in the *Output Type(s)* field. If an excitation limiter can be configured to produce either a summation point or a takeover gate signal, then this field will check if the current configuration of a specific limiter instance is compatible with the exciter.

Possible values for this field are:

1.  *Summation Point* – The summation point output signal will be used by the exciter.

2.  *Takeover Gate* – The takeover gate output signal will be used by the exciter.

3.  *No Input* – The output signal will not be used, because the exciter type does not have any input location.

4.  *Not Used* – The output signal will not be used, because the specific exciter instance is configured to ignore an input signal.

5.  *Not Suitable* – The output signal is for a summation point, but the exciter has a takeover gate, or vice versa.  
    Either the type of limiter or the type of exciter will need to be changed.

6.  *Not Configured* – The output signal is for a summation point, but the exciter is configured to accept an input at a takeover gate, or vice versa.  
    Either the exciter configuration can be changed to match the limiter that is present, or the type of limiter can be changed to match the exciter configuration.

7.  *No Exciter* – The output signal will not be, because the exciter model instance is absent.

Cases i and ii would indicate that the limiter model is compatible with its exciter model.  
Cases iii ‑ vii would be shown in red in case information displays.  
Cases iii, iv and vii would be shown as a validation warning.  
Cases v and vi would be shown as a validation error, and auto-correction will make the limiter model not active.

---

<a id="auto-correction-at-excitation-limiter-models"></a>

## Auto-Correction at Excitation Limiter Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Autocorrection.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Autocorrection.htm)*

UEL/OEL/SCL models have model-specific auto-correction that are listed in their respective documentation pages. Additionally, a broader set of checks are applied regardless of their specific type, depending on the **Output Used** (OutputUsed) field of an UEL/OEL/SCL.

UEL/OEL/SCL‑exciter compatibility check

  - Error is shown if **Output Used** ∈ \[*Not Suitable, Not Configured*\]

    Manual correction could be to change either the type of limiter to match the exciter configuration, or the type of exciter, or the exciter configuration (if possible) to match the limiter that is present.

    Both cases would cause exciters to have atypical signal clamping (if a summation point signal were to be fed into a takeover gate), or abnormally large error signals (if a takeover gate signal were to be fed into a summation point). Therefore, these must be corrected, or otherwise they would result in weird and unintended consequences during the dynamic simulation.

    If not manually corrected, auto-correction will make the limiter model not active, and not change anything at the exciter models.

  - Warning is shown if **Output Used** ∈ \[*No Input, Not Used, No Exciter*\]  

    Manual correction could be to change either the type of exciter, or the exciter configuration (if possible) to match the limiter that is present, or add a compatible exciter.

    All three cases would simply not use the limiter model, so the simulation can continue without any correction

    If not manually corrected, no auto-correction is done  

UEL/SCL<sub>UEL</sub> signal lower limit (V<sub>UEL-MIN</sub>) check  
(only if **Output Used** = *Summation Point*)

  - Error shown if (V<sub>UEL-MIN</sub> \< 0).  
    (only if model does not have a fixed zero lower limit)  

    Manual correction could be to set V<sub>UEL-MIN</sub> = 0.  
    A negative UEL signal at a summation point would curb over-excitation, instead of its intended goal of curbing under-excitation.

    If not manually corrected, auto-correction will set V<sub>UEL-MIN</sub> = 0.

  - Error shown if (V<sub>UEL-MAX</sub> \< V<sub>UEL-MIN</sub>).  

    Manual correction could be to set V<sub>UEL-MAX</sub> \> V<sub>UEL-MIN</sub>.  

    If not manually corrected, auto-correction will set V<sub>UEL-MAX</sub> = V<sub>UEL-MIN</sub> + 0.05.

OEL/SCL<sub>OEL</sub> signal upper limit (V<sub>OEL-MAX</sub>) check  
(only if **Output Used** = *Summation Point*)

  - Error shown if (V<sub>OEL-MAX</sub> \> 0).  
    (only if model does not have a fixed zero upper limit).  

    Manual correction could be to set V<sub>OEL-MAX</sub> = 0.  
    A positive OEL signal at a summation point would curb under-excitation, instead of its intended goal of curbing over-excitation.

    If not corrected manually , auto-correction will set V<sub>OEL-MAX</sub> = 0.

  - Error shown if (V<sub>OEL-MIN</sub> \> V<sub>OEL-MAX</sub>).  

    Manual correction could be to set V<sub>OEL-MIN</sub> \< V<sub>OEL-MAX</sub>.  

    If not corrected manually, auto-correction will set V<sub>OEL-MIN</sub> = V<sub>OEL-MAX</sub> - 0.05.

For UEL/OEL/SCL models that meet the criteria (**Output Used** = *Takeover Gate*), upper and lower limits checks are not generalizable like those in B and C, which aim to ensure zero initial derivatives at the exciter when limiter models are not activated. Nevertheless, limits of a takeover gate limiter still needs to be consistent with the internal limits of the associated exciter model, and they need to be tuned relative to each other.

Therefore, the lower and upper limit checks for takeover gate limiters can not be done during auto-correction (i.e., before initialization), because they would have to be specific to each exciter's internal excitation signal. If the "Modify Limits and Run" option is chosen in Transient Stability options, then [these checks](#modification-of-limits-at-excitation-limiters-during-initialization) would be performed during the subsequent step of initialization.

---

<a id="initialization-of-excitation-limiters"></a>

## Initialization of Excitation Limiters

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Initialization.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Initialization.htm)*

The activation logic is first evaluated based on the initial network conditions.

Some models do not have an explicitly defined activation logic, but calculate an error signal that feeds into an Integral or Proportional‑Integral or Proportional‑Integral‑Derivative block.

For an error that is used to determine the UEL/SCL<sub>UEL</sub> signal, the error is normally negative when the signal is not limiting.  
i.e., if error \> 0 then activation logic = True, else activation logic = False.

For an error that is used to determine the OEL/SCL<sub>OEL</sub> signal, the error is normally positive when the signal is not limiting.  
i.e., if error \< 0 then activation logic = True, else activation logic = False.

  - If activation logic = False, then the UEL/OEL/SCL<sub>UEL</sub>/SCL<sub>OEL</sub> signal is considered idle.  
    i.e., *Activation Status* = 0, or *UEL Activation Status* = 0, or *OEL Activation Status* = 0

    States are initialized such that the signal UEL/SCL<sub>UEL</sub> = V<sub>UEL-MIN</sub> and/or the signal OEL/SCL<sub>OEL</sub> = V<sub>UEL-MAX</sub>.

  - If activation logic = True, then the UEL/OEL/SCL<sub>UEL</sub>/SCL<sub>OEL</sub> signal is considered saturated.  
    i.e., *Activation Status* = 2, or *UEL Activation Status* = 2, or *OEL Activation Status* = 2

    States are initialized such that the signal UEL/SCL<sub>UEL</sub> = V<sub>UEL-MAX</sub> and/or the signal OEL/SCL<sub>OEL</sub> = V<sub>UEL-MIN</sub>.

  - States are typically not initialized such that (V<sub>UEL-MIN</sub> \< UEL/SCL<sub>UEL</sub> \< V<sub>UEL-MAX</sub>) and/or (V<sub>UEL-MIN</sub> \< OEL/SCL<sub>OEL</sub> \< V<sub>UEL-MAX</sub>).  
    i.e., *Activation Status* ≠ 1, or *UEL Activation Status* ≠ 1, or *OEL Activation Status* ≠ 1

If the "Modify Limits and Run" option is chosen in Transient Stability options, then [certain limits might be modfied during the initialization stage](#modification-of-limits-at-excitation-limiters-during-initialization). This would occur before the initial UEL/OEL/SCL states values are assigned, hence the above-mentioned method of initialization remains the same.

---

<a id="modification-of-limits-at-excitation-limiters-during-initialization"></a>

## Modification of Limits at Excitation Limiters during Initialization

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Modify_Limits.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Excitation_Limiters_Modify_Limits.htm)*

In "Transient Stability \> Options \> Power System Model \> Common \> Handling of Initial Limit Violations", the option to "Modify Limits and Run" allows all models to modify some of their own limits (during the initialization stage), based on the network conditions and/or other upstream dynamic models. If the option is selected, certain limits in UEL/OEL/SCL models could be modified in an attempt to ensure zero initial derivatives at exciter models.

However, only certain limits of limiter models are modified so that the exciter has zero initial derivatives, and that is done only if the limiter's activation status is 0 (i.e., *Idle*) during initialization.  
i.e., *Activation Status* = 0, or *UEL Activation Status* = 0, or *OEL Activation Status* = 0  
The modification of limits is based on the internal excitation signal of the associated exciter during initialization. The internal excitation signal (V<sub>M</sub>) that is relevant to each limiter model would depend on where the limiter input is being received at the exciter. This could be the voltage error signal, or the voltage regulator signal, or the inner loop regulator signal.

  - For limits associated with an UEL/SCL<sub>UEL</sub> signal:

      - If control is being initialized as *Idle* and if V<sub>UEL-MIN</sub> \> V<sub>M</sub>, then V<sub>UEL-MIN</sub> = V<sub>M</sub>.

      - No change to V<sub>UEL-MAX</sub>.  

  - For limits associated with an OEL/SCL<sub>OEL</sub> signal:

      - If control is being initialized as *Idle* and if V<sub>OEL-MAX</sub> \< V<sub>M</sub>, then V<sub>OEL-MAX</sub> = V<sub>M</sub>.

      - no change to V<sub>OEL-MIN</sub>

---

<a id="renewable-energy-generation-models-wind-solar-energy-storage-distributed-photo-voltaic"></a>

## Renewable Energy Generation Models (Wind, Solar, Energy Storage, Distributed Photo Voltaic)

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_WindModeling.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_WindModeling.htm)*

While strictly speaking, renewable generation does not have an "exciter", "governor", or "stabilizer" in the way that a synchronous generator model does, the relationships in software between the convertor model, electrical model and mechanical model are very similar. These relationships are shown more in the [Generator Models Overview topic.](#generator-models)

As a result, when looking at generators in the Simulator user interface, the various renewable models will be listed under the traditional categories for synchronous machines of "machine model", "exciter", "governor", or "stabilizer". In addition to these blocks, there are also additional blocks for Aerodynamic, Pref Controller, and Plant Controller objects. These were first added in Version 18.

Examples are shown below. 

<table>
<tbody>
<tr class="odd">
<td><p>Model Class</p></td>
<td><p>Grid-Forming Converter</p>
<p>Droop-Control Inverter-Based Resource</p></td>
<td><p>Grid-Forming Converter</p>
<p>Virtual Synchronous Machine Inverter-Based Resource</p></td>
<td><p>Type 3 Wind</p>
<p>Double-Fed Induction Generators</p></td>
<td><p>Type 4 Wind</p>
<p>(Full Inverter)</p></td>
<td><p>Solar PV</p></td>
<td><p>Distributed Solar PV</p></td>
<td><p>Energy</p>
<p>Storage</p>
<p>(BESS)</p></td>
</tr>
<tr class="even">
<td><p>Wind Machine Models</p>
<p> </p></td>
<td><p><a href="38-ts-models-machine.md#regfm-a1">REGFM_A1</a><br />
</p></td>
<td><p><a href="38-ts-models-machine.md#regfm-b1">REGFM_B1</a></p></td>
<td><p><a href="38-ts-models-machine.md#regc-a">REGC_A or</a><br />
<a href="38-ts-models-machine.md#regc-b">REGC_B</a></p></td>
<td><p><a href="38-ts-models-machine.md#regc-a">REGC_A</a> or<br />
<a href="38-ts-models-machine.md#regc-b">REGC_B</a></p></td>
<td><p><a href="38-ts-models-machine.md#regc-a">REGC_A or</a><br />
<a href="38-ts-models-machine.md#regc-b">REGC_B</a></p></td>
<td><p><a href="38-ts-models-machine.md#pvd1">PVD1</a></p></td>
<td><p><a href="38-ts-models-machine.md#regc-a">REGC_A</a><br />
<a href="38-ts-models-machine.md#regc-b">REGC_B</a></p></td>
</tr>
<tr class="odd">
<td><p>Wind Electrical Models</p>
<p>listed as Exciters</p></td>
<td><p>None</p></td>
<td><p>None</p></td>
<td><p><a href="39-ts-models-exciters-part3.md#reec-a">REEC_A</a> or<br />
<a href="39-ts-models-exciters-part4.md#reec-d">REEC_D</a></p></td>
<td><p><a href="39-ts-models-exciters-part3.md#reec-a">REEC_A</a> or<br />
<a href="39-ts-models-exciters-part4.md#reec-d">REEC_D</a></p></td>
<td><p><a href="39-ts-models-exciters-part3.md#reec-a">REEC_A or</a><br />
<a href="39-ts-models-exciters-part4.md#reec-d">REEC_D</a></p></td>
<td> </td>
<td><p><a href="39-ts-models-exciters-part4.md#reec-c">REEC_C</a><br />
<a href="39-ts-models-exciters-part4.md#reec-d">REEC_D</a></p></td>
</tr>
<tr class="even">
<td><p>Wind Mechanical Models</p>
<p>listed as Governors</p></td>
<td><p>None</p></td>
<td><p>None</p></td>
<td><p><a href="40-ts-models-governors-part4.md#wtgt-a">WTGT_A or<br />
</a></p>
<p><a href="40-ts-models-governors-part4.md#wtgt-b">WTGT_B</a></p></td>
<td><p><a href="40-ts-models-governors-part4.md#wtgt-a">WTGT_A or<br />
</a></p>
<p><a href="40-ts-models-governors-part4.md#wtgt-b">WTGT_B</a></p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Wind Pitch Control</p></td>
<td><p>None</p></td>
<td><p>None</p></td>
<td><p><a href="41-ts-models-stabilizers.md#wtgpt-a">WTGPT_A</a> or<br />
<a href="41-ts-models-stabilizers.md#wtgpt-b">WTGPT_B</a></p></td>
<td><p>None</p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Aerodynamic Model</p></td>
<td><p>None</p></td>
<td><p>None</p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#wtgar-a">WTGA_A</a></p></td>
<td><p>None</p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Pref Controller Model</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p><a href="42-ts-models-generator-other-part2.md#wtgtrq-a">WTGTRQ_A</a></p></td>
<td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Plant Controller Model</p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A</a> or<br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A</a> or<br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A</a> or<br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A</a> or<br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A</a> or<br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
<td> </td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-a">REPC_A or</a><br />
<a href="42-ts-models-generator-other-part1.md#repc-c">REPC_C</a></p></td>
</tr>
<tr class="odd">
<td><p>Bus Plant Controller Model (Used when multiple generators are controlled together)</p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
<td> </td>
<td><p><a href="42-ts-models-generator-other-part1.md#repc-d-bus">REPC_D</a></p></td>
</tr>
</tbody>
</table>

Development of these second generation models was performed extensively in the WECC Model Validation Working Group in the western part of the United States. The following documents reports which describe these models in more detail created by WECC.

  - [WECC-Type-1-and-2-Generic-Turbine-Pseudo-Governor-model-1012.pdf](https://www.powerworld.com/WebHelp/Content/Other_Documents/WECC-Type-1-and-2-Generic-Turbine-Pseudo-Governor-model-1012.pdf)
  - [WECC-Type-3-Wind-Turbine-Generator-Model-Phase-II-012314.pdf](https://www.powerworld.com/WebHelp/Content/Other_Documents/WECC-Type-3-Wind-Turbine-Generator-Model-Phase-II-012314.pdf)
  - [WECC-Type-4-Wind-Turbine-Generator-Model-Phase-II-012313.pdf](https://www.powerworld.com/WebHelp/Content/Other_Documents/WECC-Type-4-Wind-Turbine-Generator-Model-Phase-II-012313.pdf)

The following images depict how the Type 3 and Type 4 wind turbine models pass signals between one another. Solar PV and Energy Storage models work the same as well.

<table>
<tbody>
<tr class="odd">
<td><p>Second Generation Type 3 Wind Turbine</p>
<p> </p>
<img src="images/Transient_Stability_Type3Wind_Phase2.png" alt="Transient Stability Type3Wind Phase2" /></td>
<td><p>Second Generation Type 4 Wind Turbine</p>
<p><img src="images/Transient_Stability_Type4Wind_Phase2.png" alt="Transient Stability Type4Wind Phase2" /></p></td>
</tr>
<tr class="even">
<td><p>First Generation Type 4 Wind Turbine</p>
<img src="images/Transient_Stability_Type3Wind_Phase1.png" alt="Transient Stability Type3Wind Phase1" /></td>
<td><p>First Generation Type 4 Wind Turbine</p>
<img src="images/Transient_Stability_Type4Wind_Phase1.png" alt="Transient Stability Type4Wind Phase1" /></td>
</tr>
</tbody>
</table>

It will obviously not make any sense to configure a generator to use a wind machine model with a traditional synchronous machine exciter model and governor, so care should be taken not to setup such configurations. Presently Simulator does perform some validation checks and returns validation errors in situations like this.

A wind farm usually consists of many small (several MW) turbines. Each individual turbine’s voltage is usually less than 1 kV (600 V is common) with a step-up transformer to increase the voltage to several dozen kV (34.5 kV common). The wind farm is usually modeled in aggregate requiring the aggregate model to account for impedance of collector system and then model per unit values at N times individual values. How accurate the aggregation is remains an open question.

There are four major types of wind turbine models used in transient stability studies which will each be considered in detail shortly based on the original model names from about 2012 for what we call the "First Generation Generic Wind Turbine Models".

  - Type 1 : Induction generators with fixed rotor resistance
  - Type 2 : Induction generators with variable rotor resistance
  - Type 3 : Doubly-fed induction generators
  - Type 4 : Full converter generators

Type 1: Induction generators with fixed rotor resistance

The most basic representation of a Type 1 wind turbine is as a conventional induction machine, however inertia is modeled with the machine. More detailed representations also include using a two-mass model (one mass for the generator and one for the turbine), and a pseudo governor. Inertia is sometimes modeled with the machine and sometimes as a governor in Simulator. A pseudo-governor is modeled as either a governor or a stabilizer in Simulator (depending on how inertia is modeled).

The MOTOR1 and GENIND models from the GE DYD file are the same, except for a sign convention on the current. They have integrated inertia. They cannot be used with other Type 1 governor/stabilizer models so no turbine dynamics are included. The CIMTR1, CIMTR2, CIMTR3, and CIMTR4 models from the PTI DYR file have the same restrictions as with the MOTOR1 and GENIND models .

The WT1G model is the GE DYD representation for a Type 1 wind turbine, while the WT1G1 is the PTI DYR model. Electrically they are quite similar to the GENIND model, except they do not include any inertia. Therefore they must be modeled with a WT1T (GE) or WT12T1 (PTI) model, both of which are included in the list of governors. The WT1T/WT12T1 models can represent the generator/turbine using either a one mass or two mass model. Both of these governors can also be used with Type 2 Wind Turbines.

The WT1P (GE) and WT12A1 (PTI) models represent a pseudo governor response model. These models are listed inside Simulator as a stabilizer models. The inputs to these models are machine speed and electrical output, while the output of the model is mechanical power. Again, these models can be used for both Type 1 and Type 2 wind turbines. It is recommended that you use the \[machine / governor / stabilizer\] grouping of \[WT1G / WT1T / WT1P\] or \[WT1G1 / WT12T1 / WT12A1\] to represent Type 1 wind machines.

Type 2 : Induction generators with variable rotor resistance

The Type 2 models augment the Type 1 by allowing for variable rotor resistance control in the wound rotor induction generator. This model is used to represent wind turbines such as the Vestas V80. Resistance control is represented by a PowerWorld Simulator using a model from the "exciter" list. Inertia is included with some machine models, or is included with a pseudo governor model. PowerWorld supports two classes of Type 2 models. From the GE DYD file we support the combination of the GENWRI machine, EXWTG1 exciter, and WNDTRB governor. From the PTI DYR file we support the combination of the WT2G1 machine, WT2E1 exciter, WT12T1 governor, and WT12A1 stabilizer.

Modeling Using GENWRI, EXWTG1, and WNTRB models

The GENWRI models represents a single cage induction generator, and also includes a single mass inertia model with the machine. The initial operating slip must be given. From this, PowerWorld then calculates the necessary resistance to match this slip. The EXWTG1 exciter specifies the minimum and maximum external rotor resistance. The WNDTRB models the blade pitch control with an input of rotor speed and an output of Pmech. The resistance is set initially to match default slip of -0.04. During the fault the resistance increases to compensate for the increased speed.

Modeling Using WT2G1, WT2E1, WT12T1, and WT12A1 models

The W2G1 model is the PTI representation for a Type 2 wind turbine which should be similar to the GE models. These are all based on new standards which are being developed for wind turbine modeling. Electrically it is quite similar to the GENWRI model, except they do not include any inertia. Therefore they must be modeled with a WT1T (GE) or WT12T1 (PTI) model, both of which are included in Simulator as governor models. They also can use the WT1P or WT12A1 pseudo governors (which are included in Simulator as stabilizer models). The initial operating point is given by the R\_Rot\_Max field, which specifies the total rotor resistance. The external rotor resistance is controlled using the WT2E1 model, which is modeled in Simulator as an exciter.

The WT2E1 model controls the external resistance between values given by Rotrv\_min and Rotrv\_max. The inputs to WT2E1 are rotor speed and electrical power. Rotor speed is converted to an equivalent power using a piecewise linear slip-power curve that is entered with the WT2G1 model. The curve is assumed to have odd symmetry (f(-x) = -f(x)). An offset is added to model to get it to initialize to zero.

Type 3 : Doubly-fed induction generators

Modeling using the WT3G ,WT3E, WT3T and WT3P models

The GE DYD file supports a combination of models of a WT3G machine model, WT3E exciter, WT3T governor, and WT3P stabilizer to model a Type 3 wind generator. The WT3G model represents the generator behavior of the Type 3 and is the interface with network equations. The WT3E model represents the reactive power control. The inputs to WT3E are the generator real and reactive power, and the voltages at the terminal and regulated bus, while the outputs are Eqcmd and Ipcmd. The WT3T model represents the mechanical equations. The WT3T inputs are the blade pitch and electrical power, while output is the rotor/turbine speeds. The WT3P model represents the pitch control. The WT3P input is the generator speed/power, while the output is pitch angle.

Modeling using the WT3G1, W3G2 ,WT3E1, WT3T1 and WT3P1 models

The PTI Type 3 models are very similar to the GE models except some default values are different. There are two machine models: WT3G1 and WT3G2. The WT3G2, an enhancement to the WT3G1, is recommended for new studies. WT3E1 is almost identical to WT3E (parameters in different order in the file format and PTI allows different negative rate limit). The WT3T1 is identical to WT3T. The WT3P1 is identical to WT3P (parameters in different order in the file format).

Detailed Models for common GE 1.5, 1.6, and 3.5 MW Turbines

GE provides more detailed models for their popular 1.5 MW, 1.6 MW and 3.5 MW turbines. These are modeled using the GEWTG (machine), EXWTGE (exciter), and WNDTGE (governor). The WNDTGE model combines the wind turbine model with the pitch control model; both one and two mass models are supported. PowerWorld provides the GE defaults for all three units for both single and double mass, and for either 60 or 50 Hz. When reading an EXWTGE model from a DYD file, PowerWorld automatically detects older record formats, reading parameters in the appropriate order for the format.

Type 4 : Full Converter Models

To model full converter wind turbines, use the WT4G1 machine model and WT4E1 exciter model.

---

<a id="load-models"></a>

## Load Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_Loads.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_Loads.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The definition of the dynamic behavior of a load in Simulator is done by assigning a combination of modules to a load record. These modules are generally depicted in the following image and then described below.

![Transient Stability Load Model Overview](images/Transient_Stability_Load_Model_Overview.png)

  - [Load Characteristic Models](#load-characteristics)
      - Multiple active characteristic can be assigned. It is possible to have two active together: one static model and one motor/dynamic model. Also, some special load models are composites of several load models (CMPLDW, CMLD, CLOD). Finally, there is a generic composite load model named CompLoad which can be defined as a list of other load models with fractions assigned.
  - [Load Distributed Generation Model](#load-distributed-generation) Added in Version 19
      - Each load record may be assigned to one active distributed generation model.
  - [Load Distribution Equivalent](#load-distribution-equivalent)
      - Typically the dynamic load model is modeled within the transient stability simulation at the terminal bus of the load record. Optionally, a [Load Distribution Equivalent Type](#load-distribution-equivalent) may be assigned to the load record which allows the load to be modeled at the end of a distribution transformer and a distribution feeder equivalent. See the [Load Distribution Equivalent Type](#load-distribution-equivalent) topic for more details.
      - Also note, that any distributed generation model is also moved to the end of the equivalent.
  - [Load Relay Models](#load-relay-modeling)
      - Multiple load relay models may be assigned. They all act independently deciding how much of the load to trip.

There are also two special objects dedicated to making the specification of dynamic load models easier.

  - [Load Model Group](#load-model-group)
      - An aggregation object specifically for dynamic models. Each load record can optionally be assigned to a Load Model Group. A Load Model Group can then have Distributed Generation Models and Characteristics assigned to it.
      - Load model groups are identified simply by a Name. The expectation is that they groupings capture relationships in transient load characteristics and distributed generation which older aggregations such as Owner, Zone, or Area do not capture. Climate-based groupings such as "High Desert" would be a natural groups as would Economic-activity based grouping such as "Computer Server Farm" or "Mining Operation".
  - [Load Component](#load-component-and-compload-characteristic) Added in Version 20
      - A Load Component is a special object used by the load characteristic named CompLoad. These together give you the ability to create any combination of other load models and give the user more flexibility that exists in the older composite load models such as CLOD, CMPLDW, and CMLD.

The relationships between some of these objects is depicted in the following image. For detailed information on how characteristics, distributed generation, distribution equivalents, and relay models are chosen for particular load see the specific help topics.

![Transient Stability Load Terminology](images/Transient_Stability_Load_Terminology.png)

---

<a id="load-characteristics"></a>

## Load Characteristics

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_LoadCharacteristic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_LoadCharacteristic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

For more detail on specific models, see the [Transient Stability Block Diagram PDF document](36-transient-stability-overview-and-data-part2.md#block-diagrams). This help topic describes the general behavior of these models.

Each load has information related to the amount of MW and Mvar. The simplest transient stability models are purely an algebraic function of voltage and frequency at the terminal of the load. Other stability models model the rotor dynamics of induction motors.

There are also a few transient models that assign a fraction of the load while the remaining would be assumed by the algebraic model used by the load. For example you may assign both a MOTORW model and a WSCC model to a load. The parameter Pul then termines the fraction of the load assigned to MOTORW while (1-Pul) is assigned to WSCC. There are also several models that are an aggregation of other models.

Finally, there are also several composite models that create a combination of hard-coded models by fraction (For example CMPLDW and CMLD typically have 3 induction motors, 1 single phase aircondition, 1 electronic load, and 1 static load). For future composite loads the CompLoad model (Added in Version 20) will be used as it can define a any combination of most of the other load models.

1.  Dynamic models that always apply to the entire load: CIM5, CIM6, CIMW, LD1PAC\_CMP, MOTOR\_CMP, BRAKE, DLIGHT, EXTL, LDFR
2.  Dynamic model that have fraction terms: LD1PAC, MOTORW, MOTOR
3.  Static (algebraic) models which can be used in combination with fractional dynamic models: IEEL, WSCC, and the default model ([Transient Stability Dialog's Option\\Power System Model](37-transient-stability-analysis-dialog-part1.md#power-system-model))
4.  Composite Models: CLOD, CMLD, CMPLDW, CMPLDWNF, CompLoad

Special Rules for when to Ignore Load Models

For any load smaller than 0.001 per unit (0.1 MW when using System Base of 100 MVA), any dynamic load model will be ignored and the load will be treated as purely algebraic.Added in Version 18, build on Sept. 27, 2014.

For complex load models that represent a composite of various load types (for example, CLOD, CMPLDW, MOTORW, and CompLoad) there are additional options for when to ignore these models as described in the [Transient Stability Analysis Options for the Power System Model](37-transient-stability-analysis-dialog-part1.md#power-system-model). Added in Version 19, build on Sept. 14, 2016

CompLoad and [LoadComponent](#load-component-and-compload-characteristic) objects Added in Version 20

A Load Component is a special object used by the load characteristic named CompLoad. These together give you the ability to create any combination of other load models and give the user more flexibility that exists in the older composite load models such as CLOD, CMPLDW, and CMLD.

See the help topic [Load Components](#load-component-and-compload-characteristic) for more details.

Determining which Load Model Characteristic Models to Use

Load Characteristic Models may be applied to either a load, [Load Model Group](#load-model-group), bus, owner, zone, area, or the entire system. During the dynamic simulation, a particular load record will use the following priority when determining what to use as the load characteristic in the stability simulation. Note that this same logic is used to determine which Static and which Motor load model characteristic to use.

  - If a load-specific model exist, this will be used
  - Else if the Load is assigned to a [Load Model Group](#load-model-group) which has a model, this will be used
  - Else if a bus-specific model exists at the terminal bus, this will be used
  - Else if an owner-specific model exists for the load's owner, this will be used
  - Else if an zone-specific model exists for the load's zone, this will be used
  - Else if an area-specific model exists for the area's zone, this will be used
  - Else if an system-specific model exists for the power system, this will be used
  - Else the *Load Modeling* option specified on the [Transient Stability Dialog's Option\\Power System Model](37-transient-stability-analysis-dialog-part1.md#power-system-model) section will be used. (For relays if the default will be to not use a relay model at all)

---

<a id="load-component-and-compload-characteristic"></a>

## Load Component and CompLoad characteristic

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_LoadComponent.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_LoadComponent.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 20

Using Load Component objects and a special load characteristic named CompLoad allows you to create a fractional combination of other load characteristics. The benefit of this is that most new load characteristic model that are added to the software in the future will immediately be available for use inside the CompLoad model.

Load Component Objects

Load Component objects are identified by a name which is a string. They may then have a single [load characteristic model](#load-characteristics) assigned to them. The Load Component Objects are then used inside of the special CompLoad load characteristic.

For load characteristics assigned to a load component, there is a restriction is that the load characteristic must be able to calculate its own initial Mvar. See the discussion of Component Initial Mvar for more information.

Load Characteristic: CompLoad

CompLoad is in most ways the same as any other load characteristic model. Just like any other characteristic, it can be assigned to a load, load model group, bus, owner, zone, area or the entire case. What makes the CompLoad special though is its parameters do not define the dynamic behavior but instead only refer to load components by fraction. Thus the input parameters for the CompLoad are described as follows and then show in the figure afterwards.

  - Comp0, Comp1, ... Comp9 : reference to up to 10 Load Component Objects
  - f0, f1, ... f9 : fraction of the respective load component objects. A negative value may also be specified for a fraction to indicate that the respective Load Component is assigned to the remaining amount. Thus if f0=0.5, f1=0.1, f2=0.2, f3=-1.0 and f4 through f9 are 0.0, then it would be calculated that f2 = 1.0-0.5-0.1-0.2= 0.2. See note at end of this topic for specific handling of degenerate situations. Also note that the fractions with CompLoad really only apply to the assignment of the MWs of the load to the various Load Components. The assignment of Mvars is discussed below.

![Transient Stability Load CompLoad](images/Transient_Stability_Load_CompLoad.png)

Initialize of Components Initial Mvar

The fractions associated with the model apply only to the MWs. As a result, the initial Mvar associated with each load component's characteristic must be determined by the characteristic from the initial voltage and MW. Thus as of the release of Simulator Version 20 the available models for CompLoad are restricted to CIM5, CIM6, CIMW, IEEL, LD1PAC, LD1PAC\_CMP, LDELEC, MOTORW, MOTORX, and MOTOR\_CMP. Existing hard-coded composite models such as CMPLDW, CLOD, and CMLD will not be added in the future, as this CompLoad is meant to replace those. As future load models are added this support will be included.

Motor models have always done this because the steady state Mvar of an induction motor is strictly a function of the terminal voltage and the MW output. For induction motors, the mismatch between the Mvar specified in a power flow solution initial condition are made up by placing an internal capacitance to match the initial condition. The same concept is used with each load characteristic used in a CompLoad, except that the internal capacitance is summed up across all the components.

Using these conventions, each component of the CompLoad will calculate its own initial Mvar. As with the stand-along induction motor models, this means that the total Mvar of the initial condition from the power flow solution may not match this summation of calculated initial Mvars. This total mismatch across the entire CompLoad will then be assign to an internal capacitance at the load bus. If a [distribution system equivalent](#load-distribution-equivalent) is being used in conjunction with this CompLoad, then this mismatch will be used in the calculation of the Bf1 and Bf2 terms as described in the help topic on the [distribution system equivalent](#load-distribution-equivalent).

This should be noted that starting in Version 20, to handle this models LDELEC and IEEL were been modified to include additional input parameters that specify the initial condition power factor of the dynamic load model. When used in CompLoad this parameter is used to determine the initial Mvar of the load. If the initial power factor specified with IEEL or LDELEC is set as zero however, then Simulator initializes that components assuming that the fraction of total Mvars is equal to the fraction of MWs.

Handling of the Fractional Definitions Degenerate Situations

The expectation for user input for CompLoad are as follows

  - Every referenced Load Component will have an active load model
  - All CompAA values which are not assigned will have a fraction fAA = 0.0
  - There will be either 0 or 1 fraction that is negative
  - If there are no negative fractions, then the summation of the fractions will be 1.00000
  - If there is 1 negative fraction, then the summation of fraction will be less than 1.00000

It is possible that the user input may not conform to this in which case the following logic will be applied. This following logic may result in a validation warning or error and those could be seen on the [validation portion of the transient stability dialog](37-transient-stability-analysis-dialog-part3.md#validation).

Any Load Component referenced by a CompLoad which does not have active load characteristic assigned to it will be treated as though the respective fraction is a 0.0. This will not be considered a validation warning and not prevent the simulation from running. Also for any CompAA value which is not assigned (None) , the respective fAA value will be treated as 0.0.

If more than one load component has a negative fraction, then this will be considered a validation and the simulation will abort and not run. Otherwise, Simulator will calculate the summation of all positive fractions assigned to Load Components that have a valid active load characteristic. Call this summation *SumFrac*.

The *SumFrac* value and existence of a negative fraction value will be evaluated with the following logic.

  - If *SumFrac* is zero, then this will also be considered a validation error and the simulation will abort and not run.
  - Else If no negative fraction was specified , then the individual fractions will be internally normalized by dividing by *SumFrac*. (A warning message will be shown in validation if SumFrac \<\> 1.00.)
  - Else If *SumFrac* \>= 1.000, then the negative fraction will be treated as 0.0 and the remaining fractions will be normalized by dividing by *SumFrac* (A warning message will be shown in validation.)
  - Else the negative fraction will be treated as equal to (1.0 - *SumFrac*)

None of the above will modify any of the user input data for fractions f0...f9, but the internally modified fractions may be different than specified to conform the input data to the expectation.

---

<a id="load-distribution-equivalent"></a>

## Load Distribution Equivalent

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_Distribution_Feeder_Equivalent.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_Distribution_Feeder_Equivalent.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Each load can use a distribution equivalent in the transient stability simulation. This means that all [load characteristics](#load-characteristics) and [load distributed generation models](#load-distributed-generation) will be modeled at the end of a distribution transformer and feeder. The Distribution Equivalent is an independent assignment from the [load characteristics](#load-characteristics) and [load distributed generation models](#load-distributed-generation).

In addition to the choice of a distribution equivalent, a specification of the MVA Base used for per unit parameters of the equivalent can be given in a few different ways. The distribution equivalent model itself has a parameter **MBase** which may specify this, but in addition each Load, Load Model Group, Owner, Zone, and Area has 2 fields associated with the distribution equivalent: **TSDistEquiv** and **TSDistEquivMVABase**. It is expected that the per unit distribution equivalent may be specified at an aggregate level such as a Load Model Group, owner, zone, or area. However, the MVABase assumed for those parameters for a particular load might then be specified with the load object itself.

Special Load Characteristics that have built-in Distribution Equivalents

There are also a few load models (CMPLDW, CMLD, and CLOD) that have a built-in distribution equivalent . If any of these load characteristic models end up being used by a particular load, then distributed equivalent model will be ignored.

Special Rules for when to Ignore Distribution Equivalent Models

For any load smaller than 0.001 per unit (0.1 MW when using System Base of 100 MVA), any distribution equivalent model will be ignored. Added in Version 18, build on Sept. 27, 2014.

There are options in [Transient Stability Analysis Options: Power System Model](37-transient-stability-analysis-dialog-part1.md#power-system-model) which provide filters on the load record's MW, P/Q ratio, and initial per unit voltage which may cause a distribution equivalent model to be ignored. Added in Version 19, build on Sept. 14, 2016

Also in [Transient Stability Analysis Options: Power System Model](37-transient-stability-analysis-dialog-part1.md#power-system-model), there is a minimum nominal kV for transformer that can be specified. For any loads connected to a bus with a nominal voltage below this, the input term Xxf will be ignored and the transformer will be skipped in the modeling of the distribution equivalent. The other terms such as the feeder impedance (Rfdr, Xfdr) will still be used. Added in Version 20

Determining which Distribution Equivalent Models to Use

Distribution Equivalent Models may be applied to either a load, [Load Model Group](#load-model-group), owner, zone, or area. During the dynamic simulation, a particular load record will use the following priority when determining what to use as the distribution equivalent in the stability simulation.

  - If the load characteristic model used is a special model (CMPLDW, CLOD, CMLD) that has a built-in distribution equivalent, then that will be used directly.
  - Else If a load is assigned to a **TSDistEquiv**, this will be used (along with the Load object's **TSDistEquivMVABase**)
  - Else if the Load is assigned to a [Load Model Group](#load-model-group) which has a **TSDistEquiv**, this will be used (along with the Load Model Group's **TSDistEquivMVABase** \*see exception below)
  - Else if the load's owner has a **TSDistEquiv**, this will be used (along with the Owner object's **TSDistEquivMVABase** \*see exception below)
  - Else if the load's zone has a **TSDistEquiv**, this will be used (along with the Zone object's **TSDistEquivMVABase** \*see exception below)
  - Else if the load's area has a **TSDistEquiv**, this will be used (along with the Area object's **TSDistEquivMVABase** \*see exception below)
  - Else no distribution equivalent model will be used and the load will be connected directly to the transmission system bus from the power flow case.

Exception: if the Load object's **TSDistEquivMVABase** \<\> 0, that value will always be used directly even if the distribution equivalent model is obtained from one of the aggregation objects of a Load Model Group, owner, zone or area.

Note: This is different than for load characteristics which could also be applied to a Bus or the entire system).

Parameters of the distribution equivalent model

The input parameters for the distribution equivalent are as follows.

**Mbase**: this indicates the MVABase on which the input parameters **Bss**, **Rfdr**, **Xfdr**, **Xxf**, **Rcmp**, and **Xcmp** are specified. The value may be zero or negative and has specifal meaning in that situation. See the initializing the distribution equivalent models section below for more details on this.

**Bss**: Substation shunt capacitor susceptance in per unit

**Rfdr**: Feeder equivalent resistance in per unit

**Xfdr**: Feeder equivalent reactance in per unit

**Fb**: Fraction of feeder shunt capacitance at substation bus end

**Xxf**: Substation transformer reactance in per unit

**Tfixhs**: Transformer high side fixed tap in per unit

**Tfixls**: Transformer low side fixed tap in per unit

**LTC**: 1 for automatic tap adjustment (low side variable tap)

**Tmin**, **Tmax**, **step**: Minimum and maximum variable tap and step size (all in per unit)

**Vmin**, **Vmax**: Minimum and maximum low-side bus voltage

**Tdel**: Time delay to initiate tap adjustment, seconds

**Tdelstep**: Time delay between tap steps, seconds

**Rcmp**, **Xcmp** : Transformer LTC compensating resistance and reactance in per unit.

Initializing the Distribution Equivalent Models

The method used for initializing a distribution equivalent model is shown in the following image using the CMPLDW as an example. The original load is moved to the end of the distribution equivalent inside the transient stability run:

![Transient Stability Load Model Group Distribution Equivalent Type 694x449](images/Transient_Stability_Load_Model_Group_Distribution_Equivalent_Type_694x449.gif)

When calculating the parameters of the distribution equivalent the following calculations are done

Determine the *tempMVABase* from **TSDistEquivMVABase** input parameters

  - If the load object has ( **TSDistEquivMVABase** \<\> 0) then tempMVABase = Load's **TSDistEquivMVABase**
  - Else if the aggregate level object from which the distribution equivalent model is chosen has ( **TSDistEquivMVABase** \<\> 0) then tempMVABase = Aggregate Object's **TSDistEquivMVABase**
  - If the *tempMVABase* = 0, then instead the distribution equivalent model's **MBase** value will be used instead.

The actually Used Distribution Equivalent MVA Base is then determined based *tempMVABase* .

  - If (*tempMVABase* \> 0) then UseDistEquivMVABase = *tempMVABase*

<!-- end list -->

  - If (*tempMVABase* \< 0) then UseDistEquivMVABase = Pinit/*tempMVABase*

<!-- end list -->

  - If (*tempMVABase* = 0) then UseDistEquivMVABase = Pinit/0.8;

The six impedance parameters (**Bss, Rfdr, Xfdr, Xxf, Rcmp, Xcmp**) of the Distribution Equivalent Type are assumed to be on this UseDistEquivMVABase and are converted the to the System MVA Base. For example, Xxf = Xxf \* SystemMVABase/DistEquivMVABase.

Transformer Taps and impedances are converted to the System MVA Base based on the fixed taps. (Note that the variable tab is assumed to be at the Low Side Bus).

  - **Xxf** = **Xxf** \* (**Tfixhs**)2

<!-- end list -->

  - **Step** = **Step**/**Tfixhs**

<!-- end list -->

  - **Tmin** = (**Tmin** + **Tfixls** - 1)/**Tfixhs**

<!-- end list -->

  - **Tmax** = (**Tmax** + **Tfixls** - 1)/**Tfixhs**

The transformer tap ratio is assumed to be set such that the voltage at the Low Side Bus is equal to the average of **Vmin** and **Vmax**. The tap ratio is then rounded to the nearest discrete step and brought back within the **Tmin** - **Tmax** range if necessary.

Using the impedances and taps now available, the Low Side Bus voltage is calculated exactly and the resulting flow on the Low Side Bus of the feeder is calculated exactly (**PLS** + j**QLS**).

We now initially assume that Bf1 and Bf2 are both zero, and from this an estimate of the resulting flow reaching the Load Bus of the feeder is calculated as **Pnew** + j**Qnew** and the resulting Load Bus Voltage as well.

If the Load Bus voltage falls below 0.95 per unit, then the feeder impedances **Rfdr** and **Xfdr** are reduced by a factor that results in a Load Bus Voltage of 0.95 per unit. (Note: if the Low Side Bus Voltage is less than or equal to 0.95, then **Rfdr** and **Xfdr** are set to the minimum impedance values of 0.0000001 + j0.00001 and the load bus voltage is not enforced.)

The perfectly initialized voltage at the Load Bus and the values of **Pnew** + j**Qnew** cannot be immediately calculated. This is because they will depend on the initialization of the transient load model that is assigned to this load record. During the initialization of the load model the resulting extra Mvar values calculated due to motor initialization will be assigned to the feeder shunt values **Bf1** and **Bf2** according to the parameter **Fb**. In the simplest case when **Fb** = 0, all the extra Mvars are assigned at the Load Bus (**Bf2**) and thus the estimate of the voltage at the Load Bus will not change. When **Fb** \> 0 however, this means that some of the Mvars are assign to the Low Side Bus (**Bf1**) and this will slightly impact the calculation of the Load Bus voltage and the values of **Pnew** + j**Qnew**. To accommodate the splitting of this admittance the initialization routine must iteratively perform load initialization and the allocation of the split of **Bf1** and **Bf2** until it converges to a consistent solution. Throughout this iteration the restriction that the Load Bus voltage not fall below 0.95 per unit must also be maintained. This is all done internally by Simulator.

Error Checking on Distribution Equivalent

The impedance parameters of the distribution equivalent are often given using either an MVABase \<= 0 indicating that the MVABase for these impedances is a multiple of the initial power (<span class="underline">MW</span>) of the load. This can cause problems if the initial load has a very bad power factor. For example, a load which is 1.2 MW and 30 Mvars is going to cause trouble because the impedances will be based on an MVABase proportional to 1.2, but the 30 Mvars may then exceed the maximum steady state power transformer across the distribution equivalent. This will make it impossible to initialize the model. To detect this situation, PowerWorld Simulator does a simple validation check and will not permit the simulation to run if this validation check fails.

Validation Check: (**Pinitpu**^2 + **Qinitpu**^2)/(**Vpu**^2) \***Rpu** \> **Pinitpu**

If this validation check is true, then the simulation is aborted and an appropriate error message is presented asking that the load Q/P ratio be fixed.

---

<a id="load-distributed-generation"></a>

## Load Distributed Generation

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_LoadDistributedGeneration.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_LoadDistributedGeneration.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 19

For more detail on specific models, see the [Transient Stability Block Diagram PDF document](36-transient-stability-overview-and-data-part2.md#block-diagrams). This help topic describes the general behavior of these models.

Each load has information related to the amount of distributed generation associated with this load. The NetMW is then the subtraction of TotalLoadMW - DistMW and same for Mvar as described in the help topic on [Load Modeling](06-object-properties-edit-mode-part1.md#load-modeling). The Load Distributed Generation Model is then the transient stability model that defines the behavior of this distributed generation. The [Load Characteristic models](#load-characteristics) apply to the TotalLoad, while the Load Distributed Generation Model applies to the DistMW and DistMvar.

Determining which Distributed Generation Model to Use

Load Distributed Generation Models may be applied to either a load, [Load Model Group](#load-model-group), bus, owner, zone, area, or the entire system. During the simulation, a particular load record will use a the following priority when determining what to use as the distributed generation model in the stability simulation. In addition the DistGenMVABase is specified as described here.

TSDistGenMVABase numbers for a Load, LoadModelGroup, Bus, Owner, Zone, and Area were added in Version 20, Build on March 23, 2018

  - If a load-specific model exist, this will be used
  - Else if the Load is assigned to a [Load Model Group](#load-model-group) which has a model, this will be used (along with the Load object's **TSDistGenMVABase** \*see exception below)
  - Else if a bus-specific model exists at the terminal bus, this will be used (along with the Bus object's **TSDistGenMVABase** \*see exception below)
  - Else if an owner-specific model exists for the load's owner, this will be used (along with the Owner object's **TSDistGenMVABase** \*see exception below)
  - Else if an zone-specific model exists for the load's zone, this will be used (along with the Zone object's **TSDistGenMVABase** \*see exception below)
  - Else if an area-specific model exists for the area's zone, this will be used (along with the Area object's **TSDistGenMVABase** \*see exception below)
  - Else if an system-specific model exists for the power system, this will be used (the entire case does not have a default **TSDistGenMVABase** as this wouldn't make sense anyway)
  - Else the distributed generation will be lumped in with the load and obey the [load characteristic model](#load-characteristics) assigned.

Exception: if the Load object's **TSDistGenMVABase** \<\> 0, that value will always be used directly even if the distribution generation model is obtained from one of the aggregation objects of a Load Model Group, bus, owner, zone, area.

Coordination of Initialization with [Distribution Equivalent](#load-distribution-equivalent)

When used in combination with a [distribution equivalent mode](#load-distribution-equivalent)l, then the MW and Mvar portion of the distributed generation will be translated directly to the load bus (after the transformer and the feeder). The impact of the losses in the distribution equivalent will all be applied to the portion of the load assigned the load characteristic model.

Consider the example below. Presently it takes the “NetMW +jNewMvar” as the P and Q taken from the initial condition of the power flow case seen at the transmission bus. It then goes through a process of translating this P+jQ across a transformer and feeder and ultimately there is a “Pnew + jQnew” seen at the Load Bus. This Pnew+jQnew is then applied to the load model parameters. (We’re leaving out some details here related to the Fb term and initializing motors, but this is the general idea).

![Transient Stability Load Model Group Distribution Equivalent Type Zoom](images/Transient_Stability_Load_Model_Group_Distribution_Equivalent_Type_Zoom.png)

When including the distributed generation model portion, then this same process will occur, but the portion of the load representing distributed generation would translate directly to the load bus, so you’d translate the “Pdg + jQdg” directly to the distributed generation model down at the end of the distribution equivalent. The load amounts then are processed by the load characteristic models in the same manner as with any load characteristic with the amount of MW and Mvar would be modified to “(Pnew+ Pdg) + j (Qnew+ Qdg)”. This is described visually as follows.

![Transient Stability Load Model Group Distribution Equivalent Type DG](images/Transient_Stability_Load_Model_Group_Distribution_Equivalent_Type_DG.png)

---

<a id="load-relay-modeling"></a>

## Load Relay Modeling

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_LoadRelays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_LoadRelays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

For more detail on specific models, see the [Transient Stability Block Diagram PDF document](36-transient-stability-overview-and-data-part2.md#block-diagrams). This help topic describes the general behavior of these models.

Load Relay Models in Simulator are allowed to apply to either a load, bus, owner, zone, area, or the entire system. During the dynamic simulation, a particular load record will automatically compile a list of all the load relay models that are active looking through the hierarchy as follows.

  - All active load-specific models will be added to the list
  - All active bus-specific models will be added to the list
  - All active owner-specific models will be added to the list
  - All active zone-specific models will be added to the list
  - All active area-specific models will be added to the list
  - All active system-specific models will be added to the list

For more detail on specific models, see the [Transient Stability Block Diagram PDF document](36-transient-stability-overview-and-data-part2.md#block-diagrams).

---

<a id="load-model-group"></a>

## Load Model Group

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In many systems PowerWorld has encountered (such as WECC system models in North America) there are 1000s of MOTORW models which have the same set of parameters. The duplicate MOTORW models are then assigned to all different loads. Future WECC models are moving toward a similar situation using the CMPLDW "complex load model". Again there will be 100s or even 1000s of loads which use an identical CMPLDW model.

Simulator's Transient Stability tool has always allowed you to assign load models to an aggregation object such as the entire system, an Area, a Zone, an Owner, or a Bus to make this data management easier. However, frequently the load behavior does not break down in the system based on the definitions of Areas, Zones, Owners, or Buses. In order to make the assignment of load model easier to manage, a new aggregation object called a Load Model Group may now be created.

A Load Model Group is a very simple object which essentially has only a Name and then a list of various Load Characteristic Models (such as MOTORW, WSCC, IEEL, CMPLDW\_NF, etc.) assigned to it in the same way that load characteristics are assign to an Area, Zone, etc. A Load Model Group may represent the behavior of "High Desert" loads or "Coastal Loads" for example.

Once Load Model Groups are created, then each Load Record may optionally be assigned to a specific Load Model Group. When determining which Transient Stability Model to use for a particular load, the following logic is applied. This general hierarchy has always existed in Simulator, with only the Load Model Group part newly added.

Load Model Groups are now included in the hierarchy of Load Characteristics in the Model Explorer as depicted in the following image below. Note also that when reading in a DYD file, Simulator look for MOTORW and CMPLDW load models and automatically create load model groups such as this based on the data seen. This is described in the [Reading and writing CMPLDW and MOTORW from DYD files](#load-model-translation-from-dyd-files) topic.

![Transient Stability Load Model Group Model Explorer](images/Transient_Stability_Load_Model_Group_Model_Explorer.gif)

---

<a id="load-model-translation-from-dyd-files"></a>

## Load model translation from DYD files

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_Reading_Writing_from_DYD.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_Reading_Writing_from_DYD.htm)*

Within a DYD file, CMPLDW records and MOTORW records are frequently assigned to 1000s of individual load records. Often there are dozens or even hundreds of load records which have model with identical parameters. When reading the DYD file, Simulator will automatically interpret these repeated models and create [Load Model Groups](#load-model-group) (for CMPLDW and MOTORW) and [Load Distribution Equivalent Types](#load-distribution-equivalent) (for CMPLDW) from these.

Also, the CMPLDW2 DYD records and associated records that start with \_cmp represent an structure similar to PowerWorld's concepts of a [Load Distribution Equivalent](#load-distribution-equivalent), [Load Distributed Generation Model](#load-distributed-generation), and the [Load Components/CompLoad](#load-component-and-compload-characteristic).

Reading and writing of CMPLDW2 records from DYD files Added in Version 20

CMPLDW2 provides a modularized structure that merges the concept of a [Load Distribution Equivalent](#load-distribution-equivalent), [Load Distributed Generation Model](#load-distributed-generation), and the [Load Components/CompLoad](#load-component-and-compload-characteristic) all into a special model structure. PowerWorld supports reading and writing this structure directly. When reading the first models processed will be any \_cmp\_ models

Translation of Components, Distribution Equivalents, and Distributed Generation

The following DYD records are converted to either Load Components, Load Distribution Equivalents, or Load Distributed Generation Models. PowerWorld Simulator uses string names to uniquely identify load components and load distribution equivalents. The DYD file instead uses special negative integers to link these models together. Thus in PowerWorld Simulator you might have a load component named "Large Motor" or "Air Conditioner Region 2", while in the DYD file these would be identified as -309 and -401 instead. When reading the DYD file, the negative integer values are used to populate special Number fields for PowerWorld's Load Component and Distributed Equivalent objects. When writing out the DYD file, PowerWorld will automatically assign unique negative integers to the Distributed Generation Model and also ensure that the special Number fields on the Load Components and Distribution Equivalents are unique across the case. If they are not unique, PowerWorld will automatically change these numbers to make them unique.

The following are a list of special DYD records which Simulator will interpret as described.

> \_cmp\_dist -3 : 0 0.04 0.04 0.08 1 1 0 0.9 1.1 0.00625 1.025 1.04 30 5 0 0 0
> 
> DYD record is read as a [Load Distribution Equivalent model](#load-distribution-equivalent) and the number field of the distribution equivalent is populated with the absolute value of the negative number specified with this model. The model will be assigned at the same aggregation level as any \_cmpldw2 DYD record which refers to it or to the load object which uses the cmpldw2 DYD record.
> 
>  
> 
> \_cmp\_dgpv -1001 : 1.1 0.5 0.7 1.1 1.2 0.5 58.0 59.0 61.0 62.0 0.0
> 
> DYD record is read as a [load distributed generation model](#load-distributed-generation) DGPV. The model will be assigned at the same aggregation level as any \_cmpldw2 DYD record which refers to it or to the load object which uses the cmpldw2 DYD record.
> 
>  
> 
> \_cmp\_stat -139 : -0.994 2 0.327 1 0.673 0 2 -0.5 1 1.5 -1
> 
> \_cmp\_elec -202 : 1 0.7 0.5 1
> 
> \_cmp\_mot3 -309 : 0.85 0.01 3.1 0.2 0.165 0.8 0.0026 0.2 2 0.7 0.1 0.4 1 9999 0.6 0.1 0.5 0.75 0.25
> 
> \_cmp\_1pac -401 : 1 0.98 0.6 0.1 0.1 9999 0.2 0.95 0.3 0.1 0.6 0.02 0 9999 0.5 0.4 0.6 0.5 15 0.7 1.9 0.025
> 
> DYD record is read as a new [Load Component](#load-component-and-compload-characteristic). The name of the load component will be based on the cmpldw2 or \_cmpldw2 model which refers to it. The load component's number will be set to the absolute value of the special negative number in the DYD file.
> 
> The \_cmp\_stat record translates to PowerWorld's IEEL model (with some appropriate parameter reordering and calculations)
> 
> The \_cmp\_elec record translates to PowerWorld's LDELEC model (with some appropriate parameter reordering)
> 
> The \_cmp\_mot3 record translates to PowerWorld's MOTOR\_CMP model
> 
> The \_cmp\_1pac record translate to PowerWorl'd LD1PAC\_CMP model

Translation of CMPLDW2

The CMPLDW2 DYD record represents a way to assign the `_cmp_XXX` components, a `_cmp_dgpv` distributed generation model, and a `_cmp_dist` distribution equivalent model to a load object. See an example DYD record below.

>   - The invocation specifies the bus to which a new CompLoad load characteristic will be created.
>   - The mva=Value designates the load object's **TSDistEquivMVABase**
>   - The cmp\_dist designates the load object's **TSDistEquiv** assignment
>   - The cmp\_dgpv designates that DGPV distributed generation model be assigned to the load.
>   - The cmp\_mot3, cmp\_l1pac, cmp\_elec, and cmp\_stat parameters designate the load components that will be assigned to the CompLoad load characteristic.

This method differs slightly from PowerWorld Simulator as PowerWorld assigns these three concepts separately, while the DYD file merges them into a single record. Thus in PowerWorld Simulator it would be possible to assign a single DGPV model to the entire case and then have different designation of load components at each load (or by aggregation level of bus, owner, zone, or area). Within the DYD syntax the specification of a DGPV model is combined into the CMPLDW2 structure. Regardless PowerWorld can read the DYD syntax to create a similar structure and handles writing it back out to this format.

> cmpldw2 0 "IND\_SRF" 0 : \# mva=-0.8 /
> 
> cmp\_dist -19/
> 
> cmp\_dgpv -1002 1.0 /
> 
> cmp\_mot3 -305 0.20 /
> 
> cmp\_mot3 -306 0.10 /
> 
> cmp\_mot3 -301 0.05 /
> 
> cmp\_elec -201 0.50 /
> 
> cmp\_1pac -401 0.10 /
> 
> cmp\_stat -111 -1.0

Translation of \_CMPLDW2

The \_CMPLDW2 DYD record is very similar to the CMPLDW DYD record, except that the invocation section determines if the model is assigned to a Load Model Group, Owner, Zone, or Area. A sample of this is as follows.

> \_cmpldw2 0 "IND\_SRF" 0: \# mva=-0.8 /
> 
> "Pmin" 0.0 "PQMin" 0.0 "Vmin" 0.0 /
> 
> cmp\_dist -19 /
> 
> cmp\_dgpv -1002 1.0 /
> 
> cmp\_mot3 -305 0.20 /
> 
> cmp\_mot3 -306 0.10 /
> 
> cmp\_mot3 -301 0.05 /
> 
> cmp\_elec -201 0.50 /
> 
> cmp\_1pac -401 0.10 /
> 
> cmp\_stat -111 -1.0

Reading and writing of MOTORW records from DYD files

When reading a DYD file into PowerWorld Simulator, all MOTORW models are now processed to group those together which have identical parameters and identical MVABase values. For each unique grouping a new Load Model Group is created with a Name of "MOTORW" with additional groups names "MOTORW 2", "MOTORW 3", and so on. A MOTORW model is then created and assigned to the load characteristics of the new Load Model Group.

When writing out a DYD file from PowerWorld Simulator, and MOTORW models which are assigned to an aggregation object such as the new Load Model Group, Area, Zone, Owner, System, or Bus will automatically be written as though the MOTORW is assigned to the specific load record.

Reading and writing of CMPLDW records from DYD files

When reading a DYD file into PowerWorld Simulator, CMPLDW models are automatically split up into a separate [Load Distribution Equivalent Type](#load-distribution-equivalent) and [Load Model Group](#load-model-group) to which a [CMPLDWNF](#load-model-group---cmpldwnf-load-model) load characteristic is assigned.

The names of the [Load Model Group](#load-model-group) and the [Load Distribution Equivalent Type](#load-distribution-equivalent) are initialized from the load record Long ID fields which are read from the EPC file. For each CMPLDW record read from an EPC file, the Long ID field read from the load record's EPC file (in Simulator this is stored in the field EPC File\\GE Long ID) is parsed and split into two strings by the first underscore character. For example, "HID\_RES" would be split into "HID" and "RES". The first string is then used as a potential name for the Load Model Group, while the second string is used as a potential name for the Load Distribution Equivalent Type. If no EPC file Long ID fields are available then the names are initialized to "Unknown" instead. After appropriate names are chosen, the Distribution Equivalent and CMPLDWNF model parameters are set as described below.

When writing a DYD file out of PowerWorld Simulator, special processing is used to handle CMPLDWNF records. Simulator will automatically combine the parameters of the CMPLDWNF and the Load Distribution Equivalent Type to write out the appropriate CMPLDW model.

Load Distribution Equivalent Creation

A separate Load Distribution Equivalent Type is then created for all CMPLDW records for which the following three things are exactly equal.

(1) First 17 CPMLDW parameters

(2) MVABase for the CMPLDW record

(3) Potential name obtained from the GE Long ID

The parameters of the Load Distribution Equivalent Type are taken directly from the first 17 parameters of the CMPLDW record and the MVABase of the CMPLDW record. The Name of the Load Distribution Equivalent Type is taken from the potential name of the GE Long ID field. All load records which are grouped in this way are then assigned to this same Load Distribution Equivalent Type. After creating all of the Load Distribution Equivalent Types using this process it is possible for more than one of the Load Distribution Equivalent Type to have the same name. As a result, the list of Load Distribution Equivalent Types is processed and the Name fields have numerical strings appended to them to ensure the uniqueness of each Name field.

Added in Version 20 If all loads assigned to a load model group use the same distribution equivalent model, then instead of assigning the load object to it's own Distribution Equivalent, the load will just inherited its distribution equivalent from its load model group.

Load Model Group Creation

In a similar manner, a separate Load Model Group is created for all CMPLDW records for which the following three things are exactly equal.

(1) Parameters 18 through 129 of the CPMLDW record

(2) Potential name obtained from the GE Long ID

For each unique grouping, a [CMPLDWNF](#load-model-group---cmpldwnf-load-model) model is created and assigned to the load characteristics of the new Load Model Group. The parameters again are directly taken from parameters 18 through 129 of the CMPLDW record. The Name of the Load Model Group is taken from the potential name of the GE Long ID field. All load records which are grouped in this way are then assigned to this same Load Model Group. After creating all of the Load Model Groups using this process it is possible for more than one of the Load Model Group to have the same name. As a result, the list of Load Model Groups is processed and the Name fields have numerical strings appended to them to ensure the uniqueness of each Name field.

An example final result of Load Distribution Equivalent Types is shown in the following figure:

![Transient Stability Load Model Group Load Distribution Equivalent Case Info](images/Transient_Stability_Load_Model_Group_Load_Distribution_Equivalent_Case_Info.gif)

---

<a id="load-model-group---cmpldwnf-load-model"></a>

## Load Model Group - CMPLDWNF Load Model

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_CMPLDWNF_Type.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Load_Model_Group_CMPLDWNF_Type.htm)*

This represents a new load model identical to the CMPLDW model, except that all the parameters related to the Distribution Equivalent have been removed (the first 17 parameters of CMPLDW and the MVABase). The "NF" at the end of the name stands for "No Feeder". In all other ways this model is identical to the CMPLDW model. The following figure shows the CMPLDWNF load model dialog. Notice that the parameters are identical but they start with parameter **FmA, FmB, FmC, FmD, Fel** which are parameter parameters 18 and after for the CMPLDW model.

![Transient Stability Load Model Group CMPLDWNF](images/Transient_Stability_Load_Model_Group_CMPLDWNF.gif)

---

<a id="line-relay-modeling"></a>

## Line Relay Modeling

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_LineRelays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_LineRelays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transmission Line Relay Models in Simulator are assigned directly to a particular branch in Simulator. Many line relays will also apply to specific end of the branch. When a relay type requires the assignment of a specific end of the branch, there will be a field **Device Location** which can be set to either *From* or *To*. The **Device Location** also becomes one of the key fields for that type of line relay [Key Fields](04-model-explorer-and-case-information-part3.md#key-fields). The **Device Location** can also be specified on the transient stability tab of the branch dialog by checking the box **Device is at From End of Line (otherwise at To End)**. The end specified by the Device Location is referred to as the "Relay End", while the other is referred to as the "Other End".

For most types of relays, only one of that type may be assigned to each end of the branch. Thus you could only have two ZLIN1 relays assigned to a branch with one assigned to the *From* location and the other to the *To*. Some relays however allow multiple relays of the same type to be assigned to the same end of a branch (for example OOSLEN). For these relay types, there will be an another field **Device ID** to which a two character id is assigned. Again, the **Device ID** will be treated as a [Key Field](04-model-explorer-and-case-information-part3.md#key-fields) for that type of relay.

Details about specific line relays are contained in the [Transient Stability Block Diagram PDF document](36-transient-stability-overview-and-data-part2.md#block-diagrams), so look there for more information.

Special User Interface Features for Time Inverse Over-Current Relays

On the branch dialog's [Transient Stability Tab](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs), for relays which represent an impedance-based distance relay, there will also be an extra button **Show Relay Zones** available to help you visualize the Time To Close or Time to Reset curve for the relay. These relay types include LOCTI, TIOCR1, and TIOCRS.

Special User Interface Features for Impedance-Based Distance Relays

On the branch dialog's [Transient Stability Tab](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs), for relays which represent an impedance-based distance relay, there will also be an extra button **Show Relay Zones** available to help you visualize the relay zone data.

![Transient Stability Overview LineRelayForwardReachVisualization](images/Transient_Stability_Overview_LineRelayForwardReachVisualization.gif)

Finally, in the [Transient Stability Model Explorer](36-transient-stability-overview-and-data-part2.md#model-explorer), for Line Relay Models there are three extra columns showing the Forward Reach Percentage for Zones 1, 2, and 3.

![Transient Stability Overview LineRelayForwardReachTable](images/Transient_Stability_Overview_LineRelayForwardReachTable.gif)

If these are not related to the particular line relay, then the fields will appear blank. For those relays for which this is relevant, the forward reach impedance (typically denoted as Rf1, Rf2, etc...) will go through the following calculation to obtain a percentage with the value shown in the respective field.

![Transient Stability Overview LineRelayForwardReach](images/Transient_Stability_Overview_LineRelayForwardReach.gif)

Note that these percentages and the Rforward points are also marked on the plot created when clicking the **Show Relay Zones** buttons mentioned above.

Also for impedance-based distance relays for which a "Far Bus" is specified (such as ZLIN1, ZQLIN1, ZPOTT, etc...), then Simulator will automatically start at the **Device Location** bus of the branch and do a topology search of the network to find the series of branches that get to the "Far Bus". The *Reach Percentage* is then based on the sum of branch impedances on the series path found. In addition the **Show Relay Zones** feature will include additional information about the intermediate points found as this series path is traversed.

If any loops are found while doing this search that circle back to the **Device Location** bus, then this search is aborted and the LineR and LineX of the branch to which the relay is assigned is used as normal. For impedance-based relays that do not have a Far Bus, but do specify transfer trip lines (such as DISTR1), then Simulator will do a similar search to find the series path by assuming that the last branch in this series path is the first transfer trip line.

The following image is what you'll see when a series of two branches are described.

![Transient Stability Overview LineRelayForwardReachVisualizationSeries](images/Transient_Stability_Overview_LineRelayForwardReachVisualizationSeries.gif)

---

<a id="switched-shunt-models"></a>

## Switched Shunt Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_ShuntModels.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_ShuntModels.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched shunt models are handled by a signal transient stability model.

The svsmo1, svsmo2, and svsmo3 models were developed extensively in the WECC Model Validation Working Group in the western part of the United States. The following documents reports which describe these models in more detail created by WECC.

  - [WECC-Type-1-and-2-Generic-Turbine-Pseudo-Governor-model-1012.pdf](https://www.powerworld.com/WebHelp/Content/Other_Documents/WECC-Static-Var-System-Modeling-Aug-2011.pdf)

---

<a id="dc-transmission-lines"></a>

## DC Transmission Lines

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_DCLines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_DCLines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

For transient stability simulations, DC transmission lines without a dynamic model specified are modeled as part of the algebraic network equations in much the same way they are modeled in a power flow solution for steady state analysis. The only exception when moving to a stability simulation is that all DC lines (as well as DC converters for multi-terminal DC lines) are assumed to operate in current control mode during the stability simulation. For those which are configured for power control mode in the steady state power flow input, Simulator will change the control mode to current and change the setpoint to the steady state current on the device.
