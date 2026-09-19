---
title: "Contingency Analysis — Dialog Options"
part: "Contingency Analysis"
chapter_file: "22-contingency-analysis-options.md"
topics: 29
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Contingency Analysis — Dialog Options

The Contingency Analysis dialog: Contingencies tab and the full Options tab.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (29)**

- [Options Tab](#options-tab)
- [Basics](#basics)
- [DC and Screening Options](#dc-and-screening-options)
- [Injection Sensitivities](#injection-sensitivities)
- [Generator Post-Contingency AGC](#generator-post-contingency-agc)
- [Bus Load Throw Over](#bus-load-throw-over)
- [Generator Maximum MW Response](#generator-maximum-mw-response)
- [Contingency Generator Line Drop and Reactive Current Compensation](#contingency-generator-line-drop-and-reactive-current-compensation)
- [Generator Line Drop and Reactive Current Compensation](#generator-line-drop-and-reactive-current-compensation)
- [Switched Shunt Post CTG](#switched-shunt-post-ctg)
- [InjectionGroup](#injectiongroup)
- [Auxiliary Files](#auxiliary-files)
- [Transient Models](#transient-models)
- [Result Storage](#result-storage)
- [Limit Monitoring](#limit-monitoring)
- [Advanced Limit Monitoring](#advanced-limit-monitoring)
- [Island Monitoring](#island-monitoring)
- [Monitoring Exceptions](#monitoring-exceptions)
- [Define Monitoring Exceptions Dialog](#define-monitoring-exceptions-dialog)
- [Custom Monitors](#custom-monitors)
- [Contingency Definitions](#contingency-definitions)
- [Contingency Definition Dialog](#contingency-definition-dialog)
- [Remedial Action Definitions](#remedial-action-definitions)
- [Model Result Override](#model-result-override)
- [Distributed Computing](#distributed-computing)
- [Miscellaneous](#miscellaneous)
- [Contingencies Tab](#contingencies-tab)
- [Contingency Definition Display](#contingency-definition-display)
- [Contingency Violations Display](#contingency-violations-display)

---

<a id="options-tab"></a>

## Options Tab

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Options tab of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) enables you to control many parameters that govern how the contingency analysis flags violations, deals with violations that appeared in the Base Case, and documents the violations in the form of a report.

On the left of the Contingency Options tab there is a pane summarizing all the available options. This pane is split into the following 5 major groupings:

  - **Modeling**: contains various options for how devices respond during a contingency which are described in the topics
      - [Basics](#basics)
      - [DC and Screening Options](#dc-and-screening-options)
      - [Injection Sensitivities](#injection-sensitivities)
      - [Generator Post-Contingency AGC](#generator-post-contingency-agc)
      - [Bus Load Throw Over](#bus-load-throw-over)
      - [Generator Maximum MW Response](#generator-maximum-mw-response)
      - [Generator Line Drop and RCC](#contingency-generator-line-drop-and-reactive-current-compensation)
      - [Contingency Options: Switched Shunt Response](#switched-shunt-post-ctg)
      - [Contingency Options: Injection Group](#injectiongroup)Added in Version 24
      - [Auxiliary Files](#auxiliary-files)
      - [Result Storage](#result-storage)
      - [Transient Models](#transient-models)
  - **Limit Monitoring**: contains options regarding special limit monitoring features for contingency analysis described in [Advanced Limit Monitoring](#advanced-limit-monitoring), [Island Monitoring](#island-monitoring), [Monitoring Exceptions](#monitoring-exceptions), and [Custom Monitors](#custom-monitors).
  - [Contingency Definitions](#contingency-definitions) : contains listings of all contingency elements
  - [Remedial Action Definitions](#remedial-action-definitions): contains options for defining remedial actions as described in [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions), [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog), [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog), [Model Expressions](04-model-explorer-and-case-information-part2.md#model-expressions), and [Model Result Override](#model-result-override)
  - [Legacy Definitions](52-additional-linked-topics-part1.md#contingency-options-legacy-definitions): contains obsolete objects that should be replaced with newer objects as described in [Contingency Blocks](21-contingency-analysis-overview-and-records.md#contingency-blocks) and [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions)
  - [Distributed Computing](#distributed-computing) : contains special distributed computing options for contingency analysis
  - [Miscellaneous](#miscellaneous)

---

<a id="basics"></a>

## Basics

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Modeling.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Modeling.htm)*

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Modeling grouping.

Calculation Method

The calculation method defines how the power flow is solved during the contingency analysis. By default, Simulator uses a **Full Power Flow** for each contingency. For a large set of contingencies and a large case, this can take some time to complete. The Full Power Flow option can utilize either an AC solution or DC solution depending on whether or not the Power Flow Solution Options are set to [Use the DC Approximation in Power Flow](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options). Alternatively, the contingency analysis can be done by calculating the linear approximation of the impact of the contingencies by choosing either the **Linearized Lossless DC** or **Linearized Lossless DC with Phase Shifters** method. These two methods will both solve a set of contingencies much faster than the full power flow. The Lossless DC methods utilize sensitivities of devices to calculate the load flow in a linear fashion. The only difference between the two lossless DC methods is that the first method treats all phase shifters as free-flowing, while the method with phase shifters will hold all in-service phase shifters at their present MW flow value.

If the Power Flow Solution Options are set to Use the DC Approximation in Power Flow, the linearized methods will not be available. Also, if the DC approximation is in use, the option with the [Limit Monitoring Settings to Treat Transmission Line Limits as Equivalent Amps](18-general-tools.md#limit-group-dialog) will be ignored. Line limits will always be reported in MVA.

AC Method Options

The following options are available if using the *Full Power Flow* **Calculation Method** and the Power Flow Solution Options are NOT set to DC Approximation Power Flow.

Retry solution using the Robust Solution Process after a contingency solution failure

Checking this option will force the contingency analysis routine to attempt a robust solution following the failure of a standard Newton-Raphson solution. The robust solution attempt does not guarantee convergence, but will attempt to slowly approach a convergence solution if possible. This process is described in more detail under [Simulation Control](02-simulator-ribbon.md#simulation-control).

Using this option can greatly slow down the contingency solution when there are contingencies that will not converge. In general this option should not be used. If there are contingencies that fail after an initial run, they can always be attempted again using this method if desired.

The Robust Solution Process is not used regardless of how this option is set when solving contingencies as part of either the PV or QV analysis available with the [PVQV add-on](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview) or ATC analysis with the [ATC add-on](32-available-transfer-capability.md#available-transfer-capability-atc-analysis).

Use specific solution options for contingencies

When checked, Simulator will use a different set of [Solution Options](10-power-flow-solution-and-options-part1.md#simulator-options) when solving the contingencies defined in the contingency set. To define the solution options used during the contingency analysis, click the **Define Contingency Solution Options** button to open the [Contingency Solution Options Dialog](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options). If solution options have already been defined, the button will be labeled **Modify Solution Options**.

Do OPF solution for each contingency

Instead of using a standard power flow solution for each contingency, the Primal LP OPF algorithm will be solved. This will be solved with all of the option settings available with the [OPF tool](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview). This option can be used to mitigate violations. If flow constraints are being enforced, there will be no violations reported as long as there are no unenforceable constraints.

Do Not Use Post Power Flow Solution Action List

Checking this option prevents any globally defined [post power flow solution actions](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) defined with the case from being evaluated and performed in the post-contingency power flow solution during contingency analysis runs.

Disable Gen Drop Overlap

When using injection group contingency actions, there are very specific settings that will allow for the accounting of generation that is part of multiple injection groups that drop generation during a contingency. Check this option to disable this accounting. For a full description of how the generation drop overlap accounting works see the [Contingency Element Type: Injection Group topic](24-contingency-element-dialog.md#type-injection-group).

Make-Up Power

When solving a contingency, the make-up power defines how the post-contingency solution accounts for the change in system losses, generation, and load. There are three options for this make-up power.

Determine make-up using:

Area Participation Factors specified below

Simulator models this by temporarily switching to [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) and using the **Calculate Participation Factors from Area Make Up Power Values** option during the contingency solution. The values specifying the **CTG Make Up Gen** for each area are used to determine the contribution of each area in an island to the amount of make-up power needed. Within each area, the individual participation factors of generators on AGC determine how much power will come from each generator.

Note that if all areas have **CTG Make Up Gen** equal to 0.0, then all make-up power will come from the island slack bus. This option generally yields faster solution times, but a concentration of make up power at the island slack bus may not accurately represent the response of the system following a contingency.The [Calculate Participation Factors from Area Make Up Power Values section of Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) describes this in further detail.

Generator Participation Factors From Entire Case Directly

Simulator models this by temporarily switching to [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) and using the **Use Participation Factors of Individual Generators** option during the contingency solution. The individual participation factors of each generator within each island are used to determine how each generator meets the make-up power needs of the island. Area and super area interchange (ACE) requirements are ignored, and all generators on AGC are dispatched to account for the changes in system losses, generation, and load. This option is usually the best approximation of post-contingent system behavior, but may yield longer solution times than island slack bus make-up power (**Area Participation Factors specified below** with **CTG Make Up Gen** set to zero for all areas).

Same as Power Flow Case

This uses the area interchange options specified in the normal power flow.

When using the DC power flow or a linear calculation method and this option is chosen, **Generator Participation Factors From Entire Case Directly** will be used instead.

Make-up Power Tolerance

This specifies the tolerance of the [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) used for both the **Area Participation Factors specified below** and **Generator Participation Factors From Entire Case Directly** options.

Prevent new island without enough controllable generation

This new step that can be optionally used in contingency analysis was added in Version 19, Build on January 9, 2017

Choose this option to try to prevent islands representing less than half the load in the case from being created during contingency analysis which do not have enough controllable generation available to prevent the island slack bus from operating outside of its limits. See the [Advanced Power Flow Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) help topic and the special topic on [Island Creation](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-creation) for more information.

---

<a id="dc-and-screening-options"></a>

## DC and Screening Options

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_DC_and_Screening_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_DC_and_Screening_Options.htm)*

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Modeling grouping.

DC Method Options Moved from Modeling Basics page in Version 20

The following options are available if using one of the *Linearized Lossless DC***Calculation Methods**.

For DC methods, allow amp limits by assuming a constant voltage magnitude

If checked, Simulator will allow converting MVA limits to Amp limits by assuming constant voltage magnitudes based on the state operating point just prior to the contingency calculations. Converting to amp limits is only enforced if the [Limit Monitoring Settings Option of Treat Transmission Line Limits as Equivalent Amps](18-general-tools.md#limit-group-dialog) is checked. When this option is checked, the contingency loading of the line will be calculated from the post-contingency current on the line and the calculated amp limit.

Model reactive power for DC methods by…

When you choose to use one of the Lossless DC calculation methods, you can also specify how to handle changes in reactive power during the calculations. The lossless DC methods are based on the real power MW in the system, thus an assumption needs to be made about the reaction of the Mvar flows during the linear calculations.

The choices are:

**Ignoring reactive power**

Reactive power is completely ignored. This results in the MW flow only being compared to the limits of the elements in the system. It is important to recognize this fact, as branch and transformer limits are usually given in complex power (MVA) ratings, thus, ignoring reactive power results in comparing active power flow (MW) to total complex power limits (MVA.).

**Assuming constant voltage magnitude**

One way to include reactive power in the linearized DC results is to assume the voltage magnitudes remain constant during the linearized DC contingency analysis. Thus, the MW flows are determined from the linearized calculations, and the MVAR flows are calculated from the resulting flows and constant voltage magnitudes. Thus you will still receive an approximate complex power flow on each element (MVA), which can then be directly compared to the complex power limit of the element.

**Assuming reactive power does not change**

Another way to include reactive power in the linearized DC results is to assume that the reactive power magnitudes remain constant during the linearized analysis. Thus, the MW flows are determined from the linearized calculations, and the complex power flow of each element can be approximated using the calculated MW flows and the assumed constant Mvar flows from the base case. This again allows the approximate complex flow on each element to be compared to the complex power limit of the element.

The following option is applicable when using one of the *Linearized Lossless DC***Calculation Methods** or using contingency screening:

Iterate on Action Status (Do NOT treat all Statuses as CHECK)

This option is intended to model conditional actions more accurately during linear analysis. See the [Contingency Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis) topic for details.

Full AC Power Flow Screening Options Added in Version 20

The contingency screening process uses linear contingency analysis to screen contingencies prior to running full AC analysis on contingencies that pass the screening. This attempts to speed up the contingency process by only running full AC analysis on a subset of contingencies.

Screening followed by a full ac power flow solution of contingencies can only be done when using the contingency **Calculation Method** of *Full Power Flow* and the power flow solution options are using AC power flow mode. If these two conditions are not met, screening can still be done if the option to **Screen Only** is used.

When using screening and not choosing to only screen, the contingency solution process is done in two parts. First the screening is done on all contingencies that are not being skipped and **Screen Allow** = *YES*. Second any contingencies that are not being skipped and pass the screening conditions or have **Screen Allow** = *NO* will be solved with the full AC power flow.

Screening is also only done when running all contingencies. If using the option to **Solve Selected Contingency** screening is not done.

Use Screening

This option determines if screening should be used. The following settings are possible:

**No**

No screening will be done. All contingencies will be run using the selected **Calculation Method** set on the [Basics](#basics) page.

**Yes**

Screening will be done for contingencies where **Screen Allow** = *YES* and the contingency is not being skipped. The **Screening Method** will determine how the screened contingencies are processed. Screening will only be done if the **Calculation Method** is set to *Full Power Flow* and the power flow solution is in AC power flow mode. Contingencies that are not being skipped and have **Screen Allow** = *NO* will only be solved using the full AC power flow and no screening will be done.

**Screen Only**

Screening will be done for contingencies where **Screen Allow** = *YES* and the contingency is not being skipped. The **Screening Method** will determine how the screened contingencies are processed.

**Include Voltage**

Check this box to include bus voltage screening when screening is being used with either the **Yes** or **Screen Only** option. Because voltage screening is not done by using linear sensitivities, the screening process can take significantly longer when using this option compared to not using this option. Voltage screening will only be done if the power flow solution options are using AC power flow mode. The process used during voltage screening is described below in the **Voltage Screening Process** section.

Maximum number to select

These options determine how many contingencies will be run using the full AC power flow method following screening. The screening process will determine a ranking of each type of violation for each contingency as described in the **Screening Rank** section below. The ranking is determined from highest impact to lowest. If a contingency has a ranking for a particular violation type that falls within the top number to select for that violation type, that contingency will be run using the full AC solution.

Screening Method

Linear methods are used during the screening. The methods available are **Linearized Lossless DC** and **Linearized Lossless DC With Phase Shifters**. These calculation methods are the same as the options described for the contingency [Calculation Method](#basics).

Screening Rank

The screening determines the rank of each contingency for each type of violation that is screened. The rank for each contingency for each violation type can be found in the [Contingency Records Display](#contingencies-tab). These fields are not shown in this table by default, but they can be found in the list of available fields in the Results\\Screening folder.

Determining the rank for each type of object requires screening tolerances and multipliers that are specified with the limit group of the object being monitored. These values can be found on the [Limit Group Dialog](18-general-tools.md#limit-group-dialog) for the object's limit group. The calculation of the rank for each type of object is as follows:

**Branch**

A branch will be included in the ranking for branches if it is being monitored and its MW flow is greater than its limit adjusted by the screening percent of limit tolerance specified with the branch's limit group.

The limit for a branch is determined based on the limit set chosen for its limit group. The percentage of limit is not applied because the screening percentage is used instead. The **Model reactive power for DC methods by...** options are used when determining the MW flow.

For any monitored branch the rank is then non-zero if (MW \> Limit\*ScreenBranchPercent) and rank = (MW - Limit\*ScreenBranchPercent). The total branch rank for a contingency is the sum of the rank for all monitored branches.

**Interface**

An interface will be included in the ranking for interfaces if it is being monitored and its MW flow is greater than its limit adjusted by the screening percent of limit tolerance specified with the interface's limit group. Interfaces can have negative limits. If the flow is negative it will be compared against the negative limit.

The limit for an interface is determined based on the limit set chosen for its limit group. The percentage of limit is not applied because the screening percentage is used instead.

For any monitored interface the rank is then non-zero if (Abs(MW) \> Abs(Limit\*ScreenInterfacePercent)) and rank = Abs(MW - Limit\*ScreenInterfacePercent). The total interface rank for a contingency is the sum of the rank for all monitored interfaces.

**Bus**

A bus will be included in the ranking for buses if it is being monitored and its voltage is either above its high voltage limit adjusted by the screening high bus voltage tolerance, below its low voltage limit adjusted by the screening low bus voltage tolerance, or voltage changes are being monitored and its change is greater than the change tolerance adjusted by the screening change bus voltage tolerance.

The adjusted high voltage limit becomes: ScreenHighLim = HighLimit - ScreenTolHighVolt.

The adjust low voltage limit becomes: ScreenLowLim = LowLimit + ScreenTolLowVolt.

Change violations are included if the **Always report as a violation if the...** options are in use with the [Advanced Limit Monitoring](#advanced-limit-monitoring) contingency options or with the [Limit Group options](18-general-tools.md#limit-group-dialog) for the limit group to which the bus belongs. These options specify that change violations be reported if the change in bus voltage from the contingency reference state either increases by a specified amount or decreases by a specified amount. For use with the screening rank, these values are modified by the screening change bus voltage tolerance.

The adjusted change tolerances for either an increase or decrease becomes: ScreenChangeLim = ChangeLim - ScreenChangeTolVolt. If ScreenChangeTolVolt \> ChangeLim then ScreenChangeLim = 0.

For any monitored bus the rank is then non-zero for the following conditions:

If (Volt \> ScreenHighLim) then rank = Volt - ScreenHighLim

else if (Volt \< ScreenLowLim) then rank = (ScreenLowLim - Volt)\*ScreenLowVoltMult

else if (Volt \< InitialVolt) and ((InitialVolt - Volt) \> ScreenChangeLim) then rank = (InitialVolt - Volt) - ScreenChangeLim

else if (Volt \> InitialVolt) and ((Volt - InitialVolt) \> ScreenChangeLim) then rank = (Volt - InitialVolt) - ScreenChangeLim

The total bus rank for a contingency is the sum of the rank for all monitored buses.

**Bus Pair**

A bus pair will be included in the ranking for bus pairs if it is being monitored and the absolute value of its angle difference is greater than its limit adjusted by the screening percent of limit tolerance specified with the bus pair's limit group.

The limit for a bus pair is determined based on the limit set chosen for its limit group. The percentage of limit is not applied because the screening percentage is used instead.

For any monitored bus pair the rank is then non-zero if (Abs(AngleDiff) \> Limit\*ScreenBusPairPercent) and rank = (Abs(AngleDiff) - Limit\*ScreenBusPairPercent). The total bus pair rank for a contingency is the sum of the rank for all monitored bus pairs.

Voltage Screening Process

During the screening process, bus voltages are screened using an AC power flow method. Voltage screening is only done if the power flow solution options are set to be in AC power flow mode. Contingencies will be solved using linear solution techniques first. This process will determine which contingency elements and remedial action elements will actually be implemented. The actions are implemented and the AC power flow is solved for two iterations to get an estimate of voltage changes caused by implementing the contingency. The power flow is solved <span class="underline">without</span> automatic control enabled for switched shunts, SVCs, LTC transformers, phase shifters, and DFACTs. Generator Mvar limits will NOT be enforced in the inner power flow loop. Generator make up power will come from all online AGCable generators. Generator line drop compensation will be set based on any PostCTG settings. The bus screening rank is based on the system voltages after the power flow is solved using these settings.

Calculation Method Field

When screening is used, contingency violations will be reported. To determine if these violations were calculated using the linear method used with the screening or the AC method used with the contingency calculation method, a **Calculation Method** field is available with contingency records in the [Contingency Records Display](#contingencies-tab). This field can be found in the Results folder in the list of available fields. Possible entries for this field are: *AC*, *DC*, *DCPS*, *FullDC*, *ScreenDC*, *ScreenDCPS*, *IteratedDC*, *IteratedDCPS*, *IteratedScreenDC*, and *IteratedScreenDCPS*. *AC* is the full power flow solution method. Any entry containing *DC* used the **Linearized Lossless DC** method. The exception to this is the *FullDC* method, which used linear techniques while the power flow solution method was in dc mode. Any entry containing *PS* used the **Linearized Lossless DC With Phase Shifters** method. Any entry containing *Screen* shows results from the screening without running any additional analysis. Any entry containing *Iterated* used the option to **Iterate on Action Status**.

---

<a id="injection-sensitivities"></a>

## Injection Sensitivities

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Injection_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Injection_Sensitivities.htm)*

These options are available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Modeling grouping.

The injection sensitivities options are used to calculate shift factors and/or MW effect of changing generation and load injection for individual contingency violations. These can be used to determine potential generation and load changes needed to reduce loading on violated branches and interfaces.

Sensitivities to Retain

These options determine how many shift factors to report for each violation. When saving both generators and loads, the number of results can include BOTH generators and loads, and the options do not specify the number of each to save. To save a particular number of results for a particular type of injector, the other type of injector must be excluded.

Keep Highest Sensitivities

Specifies how many results are kept for each violation based on the calculated injection sensitivities. The injection sensitivities determine how the flow on the violated element will change due to an injection of MW at the specified generator or load. The results will include the X maximum, where X = Keep Highest Sensitivities, and X minimum sensitivities.

Keep Highest MW Effect

The MW Effect of an injector device determines how increasing or decreasing injection from that injector will cause the MW flow on the violated element to decrease. This option specifies how many results are kept for both the impact of increasing and decreasing injection. The most negative X, where X = Keep Highest MW Effect, MW effects will be kept for both increasing injection and decreasing injection. The amount of injection that can be increased or decreased for a particular injector is determine based on the MW limits for the injector. For a generator the increase in injection is the difference between the maximum MW and present MW for the generator. The decrease in generator injection is the difference between the minimum MW and the present MW. Loads typically do not have maximum and minimum MW limits specified, and they will be ignored even if they are specified. The increase in load injection will be the present output of the load. The decrease in load injection will be 0.

Eligible Generators

For the impact of a generator to be considered for inclusion in the results, the generator must meet the specified filter. The following options are available for filtering:

None

No generators will be considered.

All

All generators will be considered.

Online

Only online generators will be considered.

Area/Zone/Owner Filter

Only generators meeting the Area/Zone/Owner filter will be considered.

Selected

Only generators whose Selected field is YES will be considered.

Filter

Only generators meeting the advanced filter will be considered.

Eligible Loads

For the impact of a load to be considered for inclusion in the results, the load must meet the specified filter. The following options are available for filtering:

None

No loads will be considered.

All

All loads will be considered.

Online

Only online loads will be considered.

Area/Zone/Owner Filter

Only loads meeting the Area/Zone/Owner filter will be considered.

Selected

Only loads whose Selected field is YES will be considered.

Filter

Only loads meeting the advanced filter will be considered.

Reporting Results

The sensitivities for all violations for all contingencies are reported in the [Violation CTG Injection Sensitivities](23-contingency-analysis-running-and-results.md#violation-ctg-injection-sensitivities) case information display.

For individual violations that are reported in the [Contingency Violations Display](#contingency-violations-display), fields can be added to show all of the available sensitivities for that violation. The fields that are available can be found in the Sensitivities\\Injection Sensitivities folder in the list of available fields for the LimitViol object type. A local menu option, **Show Violation CTG Injection Sensitivities**, exists with this case information display to show a case information display of only the sensitivities for the selected violation.

---

<a id="generator-post-contingency-agc"></a>

## Generator Post-Contingency AGC

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Gen_Post_Contingency_AGC.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Gen_Post_Contingency_AGC.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Post-Contingency AGC display can be opened from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) This display provides a specialized generator display with specific fields used for setting the post-contingency AGC response of individual generators.

Set the **Post-CTG Prevent AGC Response** field to indicate whether or not a generator should be on AGC post-contingency. By default, generators are NOT set to prevent AGC response post-contingency. Possible options for this field are:

**YES** - This means that the generator will NOT respond post-contingency. AGC is disabled post-contingency regardless of the generator's AGC setting.

**NO** - This means that the generator will respond according to its AGC setting. If **AGC** = YES then the generator will respond post-contingency.

**RESPOND** - This means that the generator WILL respond post-contingency. AGC is enabled post-contingency regardless of the generator's AGC setting.

Use the **Post-CTG Part. Factor** field to specify the participation factor to be used post-contingency. A value of *same* indicates that the generator should use the same participation factor as set with the generator record **Part. Factor** field. Otherwise, set a numerical value for the post-contingency participation factor to use a factor other than the normal participation factor.

---

<a id="bus-load-throw-over"></a>

## Bus Load Throw Over

*Source: [`Content/MainDocumentation_HTML/Bus_Load_Throw_Over_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Load_Throw_Over_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus Load Throw Over list display, which is opened from the Modeling group of the [Contingency Analysis dialog Options page](#options-tab), provides you with the capability to define how load at a bus should be transferred to a different bus if the original terminal bus becomes disconnected from the system. This is referred to in Simulator as "throw over." This tool is most useful when performing contingency analysis scenarios in which buses containing loads become disconnected and you wish to analyze the impact on the system of switching the load from the disconnected bus to another bus that is still in service.

Load throw over will only attempt to move the load once, from the original bus to the load throw over bus. If the load throw over bus is already disconnected from the system, then the load will be treated as dropped during the contingency solution.

**NOTE:** The load throw over is only used when running the contingency analysis tool to analyze contingency effects on the system. Load throw over records are not used during manual solution of the power flow, even if you manually disconnect a bus with load and perform a load flow solution.

The Bus Load Throw Over display has the following fields:

Number, Name

The bus number and name of the load’s terminal bus.

Nom kV

The nominal voltage level of the load’s terminal bus.

Load Throw Over Bus Number

Enter the number of the bus you wish to have the load transferred to, should the original load terminal bus become disconnected during a contingency in the contingency analysis. The **Load Throwover Bus Name\_kV** field will be automatically populated.

Load Throw Over Bus Name\_kV

Enter the bus name and nominal kV (separated by a \_ between the name and nominal kV) of the bus you wish the load to be transferred to, should the original load terminal bus become disconnected during a contingency in the contingency analysis. The **Load Throw Over Bus Number** will be automatically populated if the corresponding Bus Name\_kV is found.

If choosing to identify objects by [labels](07-object-properties-run-mode-and-general-part2.md#labels), this field can also be used to display and enter the label of the load throw over bus.

---

<a id="generator-maximum-mw-response"></a>

## Generator Maximum MW Response

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Gen_Max_MW_Response.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Gen_Max_MW_Response.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Maximum MW display can be opened from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) This display provides a specialized generator display with specific fields used for setting the post-contingency maximum MW response of individual generators.

Use the **CTG Max Response MW**field for entering the contingency maximum response. During the post-contingency power flow solution, a user may enter a MW amount specifying the maximum amount of generator response from a generator. By default, these values are blank. If you enter a value in this column, the generator response will be limited to this absolute MW response (response may be either an increase or a decrease). Regardless of the response settings, a generator will not respond unless its AGC field is set to YES or any [Generator Post-Contingency AGC](#generator-post-contingency-agc) conditions are set such that the generator will be on AGC post-contingency.

The maximum MW response for a given generator will only be enforced if enforcing generator MW limits for that generator. The maximum MW response is implemented by adjusting the generator minimum and maximum limits in order to limit the response, e.g. (New Max MW) = (Present MW) + (Generator Max MW Response) and (New Min MW) = (Present MW) - (Generator Max MW Response). Therefore, the maximum MW response will only be implemented if a generator's limits are enforced.

Generator maximum MW responses will be enforced, as long as generator MW limits are also enforced, when using all contingency calculation methods including the Full Power Flow method with the power flow in either AC or DC mode and the linearized lossless DC methods.

Note: The user may also add a column called **CTG Max Response %** to the generator display. When entering data in this column, the **CTG Max Response MW** values will be set at a respective percent of the maximum MW output of the generator. If a generator’s maximum MW output is less than or equal to zero, then the Maximum Response will always be set to zero.

---

<a id="contingency-generator-line-drop-and-reactive-current-compensation"></a>

## Contingency Generator Line Drop and Reactive Current Compensation

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Gen_Line_Drop_and_RCC.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Gen_Line_Drop_and_RCC.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Line Drop and RCC display can be opened from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) This display provides a specialized generator display with specific fields used for setting the line drop and reactive current compensation parameters for individual generators.

The [Generator Line Drop Compensation](#generator-line-drop-and-reactive-current-compensation) topic provides details on how this can be used.

---

<a id="generator-line-drop-and-reactive-current-compensation"></a>

## Generator Line Drop and Reactive Current Compensation

*Source: [`Content/MainDocumentation_HTML/Generator_Line_Drop_Compensation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Line_Drop_Compensation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Note: This feature has been available since early versions of PowerWorld Simulator using only **XLDC\_RCC**. The availability of **RLDC\_RCC** was Added in Version 19.

Line Drop and Reactive Current Compensation represent an alternative method for performing generator voltage control. These options can be set through fields associated with the [generator display](05-case-information-displays-by-object-part1.md#generator-display) and a [special display](#contingency-generator-line-drop-and-reactive-current-compensation) exists with contingency analysis options that brings up these fields by default. The fields that must be modified to use line drop or reactive current compensation are **Use LDC\_RCC**, **XLDC\_RCC**, **RLDC\_RCC**,and **AVR**. These will be described below.

While on LDC/RCC control, the generator will vary its MVAR output in a manner that maintains the bus voltage at a fictitious bus that is a user-specified electrical impedance of **XLDC\_RCC** away from the generator. This is called Line Drop Compensation when the impedance specified is positive, and Reactive Current Drop Compensation when the impedance specified is negative. If the absolute value of **XLDC\_RCC** is less than or equal to 2\*10<sup>-6</sup>\*[MVA Base](10-power-flow-solution-and-options-part2.md#power-flow-solution-general), the generator will regulate its terminal bus. (For a typical case with an MVA Base of 100 MVA, this value is 0.0002.)

The impedance is specified by entering a value for **XLDC\_RCC**, **RLDC\_RCC**,and the setpoint voltage is the same as used when regulating a generator in the more traditional manner. A generator will perform LDC/RCC control when it meets the following conditions:

  - **AVR** = YES
  - **Use LDC\_RCC** = YES

If any generators at a bus are set to **Use LDC\_RCC**, this action will disable all traditional AVR control for generators at that bus. Other generators operating on LDC/RCC control are allowed, but no traditional AVR.

When using LDC/RCC control with contingency analysis where this should only be used in the contingency solution, the field **Use LDC\_RCC** must be set to *PostCTG*. When a generator is set to *PostCTG* while implementing the post-contingency power flow, the generator will change the **Use LDC\_RCC** value to *YES*and set **AVR** to *YES*, thereby activating this new voltage control method for the generator. The **AVR** setting is also set to *YES* because the intent of using the *PostCTG* option is to force the generator to operate on LDC/RCC during the contingency solution. The **AVR** flag must be *YES* for a generator to be on any kind of AVR control, so this is a necessary change. After [the reference state](21-contingency-analysis-overview-and-records.md#contingency-case-references) is restored in the contingency analysis, the generator will return back to a setting of *PostCTG*and its reference state **AVR** setting.

There is an option on the local menu of the generator display, **Convert Voltage Setpoint for LDC\_RCC**, that will set the voltage setpoint of the selected generator(s) based on the specified **XLDC\_RCC** and **RLDC\_RCC**,. The voltage at the fictitious bus that is the specified impedance from the generator will be calculated and this is set at the setpoint voltage. If the impedance is less than the threshold specified above, the setpoint will be set to the voltage of the terminal bus. The **Use LDC\_RCC** field will be set to *YES*.

---

<a id="switched-shunt-post-ctg"></a>

## Switched Shunt Post CTG

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Shunt_Response.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Shunt_Response.htm)*

The Switched Shunt Post-Contingency Response display can be opened from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) This display provicccccbgtflgdes a specialized switched shunt display with specific fields used for setting the post-contingency response of individual switched shunts. These fields allow you to general change three things in the post-contingency power flow solution: control mode, Regulation Values, and Max/Min Mvar outputs. Details of these fields are as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>CTGShuntMode</p></td>
<td><p>Specify a value to which <strong>ShuntMode</strong> should be changed during the post contingency power flow solution. Options are the same as for <strong>ShuntMode</strong> field (<em>Fixed</em>, <em>Discrete</em>, <em>Continuous</em>, <em>Bus Shunt</em>, or <em>SVC</em>) but the value may also be set to <em>Default</em> indicating that it should not change the <strong>ShuntMode</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>CTGRegUse</p></td>
<td><p>If this value is set to <em>YES</em>, then during the post contingency power flow solution the <strong>RegHigh</strong> and <strong>RegLow</strong> of the switched shunt will be changed to match <strong>CTGRegHigh</strong> and <strong>CTGRegLow</strong>.</p>
<p>If the existing shunt is set to use the <strong>RegTargetHigh</strong> value then the target values will be changed such that</p>
<p><strong>RegTarget</strong> = <strong>CTGRegLow</strong></p>
<p><strong>RegTargetHigh</strong> = <strong>CTGRegHigh</strong></p>
<p>Otherwise, the target value will be changed to the middle of the new range with a value of</p>
<p><strong>RegTarget</strong> = (<strong>CTGRegLow</strong> + <strong>CTGRegHigh</strong>)/2</p></td>
</tr>
<tr class="even">
<td><p>CTGRegLow</p></td>
<td><p>Use as described in <strong>CTGRegUse</strong> above</p></td>
</tr>
<tr class="odd">
<td><p>CTGRegHigh</p></td>
<td><p>Use as described in <strong>CTGRegUse</strong> above</p></td>
</tr>
<tr class="even">
<td><p>CTGMvarUse</p></td>
<td><p>This is only used for switched shunts that are one of the following</p>
<ol>
<li>Continuous Control Mode (it could get changed to this by <strong>CTGShuntMode</strong> above)</li>
<li>SVC Control Mode (but not if <strong>SVCType</strong> = svsmo2)</li>
</ol>
<p>If this value is set to <em>YES</em>, then during the post-contingency power flow solution, fields associated with the shunt blocks and use of continuous element of the switched shunt will be modified to achieve the <strong>CTGMvarMin</strong> and <strong>CTGMvarMax</strong> values specified.</p></td>
</tr>
<tr class="odd">
<td><p>CTGMvarMin</p></td>
<td><p>Used as described in <strong>CTGMvarUse</strong> above</p></td>
</tr>
<tr class="even">
<td><p>CTGMvarMax</p></td>
<td><p>Used as described in <strong>CTGMvarUse</strong> above</p></td>
</tr>
</tbody>
</table>

---

<a id="injectiongroup"></a>

## InjectionGroup

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_InjectionGroup.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_InjectionGroup.htm)*

These features were added in Version 24.

The Injection Group Post-Contingency Response display can be opened from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) This display provides a specialized InjectionGroup display with specific fields used for setting the post-contingency response of individual injection Groups.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>CTGOutageIntertie</p></td>
<td><p>This field is a string field containing the identifying string for either a Branch or Interface object using the syntax for of Object ID as described in <a href="09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels" class="MCXref xref">ObjectID Field for use in Auxiliary Files</a>. For example, the string may be "Branch 234 143 AB" for a transmission line or "Interface 'MyName'" .</p>
<p> </p>
<p>The use of this field is described in detail in <a href="23-contingency-analysis-running-and-results.md#running-the-contingency-analysis" class="MCXref xref">Running the Contingency Analysis</a>. Generally, if the InjectionGroup has some online generation, load, or shunt objects in the reference case and actions during the contingencies cause all of the devices in the InjectionGroup to be opened, then the branch or interface defined by the CTGOutageIntertie will also be opened. When using an interface, this means that all the AC Branches in the interface will be opened.</p></td>
</tr>
</tbody>
</table>

---

<a id="auxiliary-files"></a>

## Auxiliary Files

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Auxiliary_Files.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Auxiliary_Files.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Options for specifying auxiliary files that can be loaded as part of the contingency process can be accessed from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab) These options provide a means of specifying the auxiliary files that can be applied to all contingencies.

Post Contingency Auxiliary File

The auxiliary file specified here is loaded at the start of each contingency prior to actually implementing the contingency actions. If a contingency has its own [post-contingency auxiliary file specific to that contingency](#contingency-definition-dialog), the contingency-specific file will be loaded instead. This file is applied before any [contingency-specific solution options](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options) are applied. The contingency actions are then implemented after any contingency-specific solution options are applied. In this way, very specialized post-contingency settings can be specified. An example use of this feature could be changing the generator voltage setpoints or AVR status for the post-contingency solution or changing generator AGC status for the post-contingency.

If the file specified does not include a file path, then Simulator will look in the presently active directory, otherwise the file path specified will be used. If the post-contingency AUX file cannot be found in this location, then Simulator will look to see if a file by this name exists in the directory from which the presently loaded case was read. If a file is specified and still cannot be found, then when running the analysis from the contingency analysis dialog, Simulator will show a dialog requesting you to find the file or remove the option.

Instead of specifying a file here, a string containing script commands can be used instead. Multiple script commands can be separated by semi-colons. This will allow the same functionality without requiring a file to be present.

Only data stored with the contingency reference state will be "reset" when the reference state is restored. Therefore, only data stored with the reference state should be loaded via a post-contingency auxiliary file. Click [here](21-contingency-analysis-overview-and-records.md#reference-state-information) for details on the specific information stored with the reference state.

This file is only loaded when the power flow is being solved in AC power flow mode and the *Full Power Flow* **Calculation Method** is being used.

Post Contingency Solution Auxiliary File Added in Version 20

The auxiliary file specified here is loaded after contingency actions have been implemented and the power flow has been run. This file will be loaded for every contingency. This file is useful for saving customized results that are not normally saved with the built-in options for saving results.

If the file specified does not include a file path, Simulator will look in the presently active directory, otherwise the file path specified will be used. If the file cannot be found in this location, Simulator will look to see if a file by this name exists in the directory from which the presently loaded case was read.

Warning - This file will be loaded when solving contingencies with any **Calculation Method** and any power flow solution mode. If using one of the linear methods or solving in DC power flow mode, the contingency reference state will not be restored between contingencies. Any changes that are made to the system state when loading this auxiliary file will carry through into the next contingency solution. The intention of this file is to save custom results and not make changes to the system state.

---

<a id="transient-models"></a>

## Transient Models

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Transient_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Transient_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Options for specifying the Transient Models that can be included in steady-state contingency analysis can be accessed from the Modeling group of the [Contingency Analysis dialog Options page.](#options-tab)

Using these options first requires that you have transient stability models defined for the types that are supported. See the [Transient Stability Overview](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) topic for links to information on modeling or view the [Transient Stability Block Diagrams](36-transient-stability-overview-and-data-part2.md#block-diagrams) topic.

Stability Model Type

The following stability models are supported for use in steady-state contingency analysis:

  - [MSR1 : Switched Shunt Model](44-ts-models-branch-and-shunt-part2.md#msr1)
  - [MSC1 : Switched Shunt Model](44-ts-models-branch-and-shunt-part2.md#msc1)
  - TIOCRSRF Line Relay Model
  - [TIOCRS : Line Relay Model](44-ts-models-branch-and-shunt-part1.md#tiocrs)
  - [LOCTI : Line Relay Model](44-ts-models-branch-and-shunt-part1.md#locti)
  - [TIOCR1 : Line Relay Model](44-ts-models-branch-and-shunt-part1.md#tiocr1)
  - [LHVRT : Generator Relay Model](42-ts-models-generator-other-part2.md#lhvrt) Added in Version 18, build on March 16, 2015

Treatment During Contingency

For each model type there are several options on how to treat this model type during a contingency run. This will affect all models of this type. (To disable a particular model independently of these options, set the **Device Status** field to *Inactive*.) The following options are available:

  - **Ignore** - This is the default setting. Nothing will happen with this model type during contingency analysis.
  - **Trip/Act** - If the conditions of a model are met, actual actions will be taken (such as tripping a line for overcurrent). Models that act will appear in the [What Occurred](23-contingency-analysis-running-and-results.md#what-occurred) results. Some models have a Monitor flag that indicates if they should simply be monitored or if they should act. If this flag is set to monitor only, an individual model will not act regardless of this contingency setting.
  - **Monitor Only** - If the conditions of a model are met, special contingency limit violations are reported. These will show up as **Category** *Transient* in the [violations](#contingency-violations-display).

Maximum Time Delay (seconds)

This determines which models will be ignored during the analysis. A model's pick-up time, or the amount of time under which some condition must be met before the model acts, must be less than or equal to this value. It is not uncommon for users to define large values for these times with the intent of disabling a model. This option is available for those situations, although Simulator has a Status field with transient models to simply disable a model without changing other parameters.

Relay Tripping Order

Transient stability models are handled as part of the POSTCHECK solution steps in the [contingency processing order](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis). All models whose **Treatment During Contingency** is set to *Trip/Act* are evaluated to see if their conditions are met. All transient models and power flow actions whose conditions are met are ordered based on their time delays. All models and actions that will act first, i.e. have the same lowest time delays down to a microsecond, will have their actions implemented. Models and actions that have a zero time delay will act immediately. For inverse-time overcurrent relays, the time delay value is obtained based on the actual current. The power flow is solved after all necessary models have been implemented.

---

<a id="result-storage"></a>

## Result Storage

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Result_Storage.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Result_Storage.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 19, build on July 19, 2016

These options allow storing the results of a contingency run to file instead of in computer memory. These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Modeling grouping.

The options allow specification of the object types and fields that should be stored to file during the contingency run. Results are only stored for objects that are violations during the contingency run, but almost any object can be stored using [Custom Monitors](#custom-monitors). Because files are written as the contingency run processes, post-contingency values that are not normally stored for violations can be stored without causing any additional computer memory to be used. This allows customization of results that is not possible when saving results in memory.

These options must be specified BEFORE the contingency analysis is run. Results cannot be saved to hard drive using these options upon completion of a run.

The following options are available on the Result Storage page.

Write to Hard Drive

Check this box to save results to file instead of computer memory. If saving to file, there will be no results in memory.

File Name

Directory location and prefix of the file name for the file to which results will be saved. Multiple files will be saved based on the Object Types used with the Result Storage object definitions. The given file name will be appended with the relevant Object Type for the results in the file. The file extension specified determines the type of files that will be saved. Using *AUX* as the extension will save a Simulator auxiliary file. Using any other extension will save a CSV (comma separated variable) file.

Use Column Headers

Check this box to identify the fields in the saved files using column headers. If not checked, the fields will be identified by variable name.

Add Defaults

Click this button to create default Result Storage objects. The default objects will define saving of violation results and fields for the ViolationCTG object. This includes the basic information that is stored for a violation including the contingency, violated element identification, violation value, and violation limit.

Result Storage Object Display

The Result Storage object display is a type of [Case Information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has the abilities common to this type of display. Objects can be added to this display by using the **Insert** option on the local menu. To update an existing object use the **Show Dialog** option on the local menu. Most of the fields cannot be updated directly in the display and can only be updated through the dialog.

Object Type

Type of object to store. A separate file will be created for each different type of object specified. When saving an auxiliary file, the object type used in the DATA section header in the file will <span class="underline">always</span> be ViolationCTG. Fields that are specified for different object types will be prepended with that object type enclosed in pipes, e.g. |Bus|, |Branch|, |Gen|, etc. This convention will allow the file to be loaded as an auxiliary file. The contents of the file will be loaded as contingency violations and any fields enclosed in the pipe symbols will be ignored because they are not available for contingency violations.

The following is an example of a file that was saved for the object type *Branch*. The fields that are Branch fields are prepended with the object type, but the fields that are ViolationCTG fields have no modification.

![Contingency Result Storage Branch File Example](images/Contingency_Result_Storage_Branch_File_Example.gif)

Restrict

If a field should only be included in a file for a specific object type, specify that object type here.

This is only useful when saving fields for the ViolationCTG object type. Fields specified for this object type will be stored with all files by default. If a field is only needed if the violation is a bus or a branch violation for example, it needs to be restricted to be only shown in that file and should not appear in the ViolationCTG file that contains all violations regardless of type.

Field Name

Variable name of the field to include in the saved file.

Order

Specifies the order of where a field should be placed in a saved file. For each type of file that is saved, all of the fields to include for that type are sorted from low order to high order to determine their placement.

Example

The following set of Result Storage objects will create three different files: *\_Bus*, *\_Branch*, and *\_ViolationCTG*.

![Contingency Result Storage Setup Example](images/Contingency_Result_Storage_Setup_Example.gif)

The branch file looks like the following. The ViolationCTG fields that are set to **Restrict** = *Bus* do not appear in this file, but do appear in the bus file.

![Contingency Result Storage Branch File Example](images/Contingency_Result_Storage_Branch_File_Example.gif)

The bus file looks like the following:

![Contingency Result Storage Bus File Example](images/Contingency_Result_Storage_Bus_File_Example.gif)

The violation file looks like the following:

![Contingency Result Storage ViolationCTG File Example](images/Contingency_Result_Storage_ViolationCTG_File_Example.gif)

---

<a id="limit-monitoring"></a>

## Limit Monitoring

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Limit_MonitoringGeneral.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Limit_MonitoringGeneral.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options Tab](#options-tab) under the Limit Monitoring grouping. In general all the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) specified with the case are used to determine what is eligible for monitoring. These settings can all be seen by clicking the **Limit Monitoring Settings** button. Other contingency-analysis specific limit monitoring settings are configured on this section as follows

  - [Advanced Limit Monitoring](#advanced-limit-monitoring) : the options on this page allow you to configure limit monitoring depending on how the value changes in relation to the reference case value.
  - [Island Monitoring:](#island-monitoring) Added in Version 20the options on this page allow you to configure whether to report limit violations based on unsolved islands or islands that do not have enough MW Reserves
  - [Monitoring Exceptions](#monitoring-exceptions) : the options on this page allow you to configure exceptions to the normal [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings). Exceptions may cause a line to be included or excluded.
  - [Custom Monitors](#monitoring-exceptions) : the options on this page allow you to configure objects and associated fields to be monitored during a contingency analysis run in addition to the devices that are monitored using the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).
  - **When using Integrated Topology Processing, monitor only the primary bus for each superbus** : checking this box will reduce the repeated bus voltage limit violation that would appear for buses at the same super bus. This box is checked by default. In addition to monitoring the primary bus for each super bus, the bus with the highest low voltage limit and the bus with the lowest high voltage limit will also be monitored so as not to miss any possible violations.

---

<a id="advanced-limit-monitoring"></a>

## Advanced Limit Monitoring

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Limit_Monitoring.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Limit_Monitoring.htm)*

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Limit Monitoring grouping.

The Advanced Limit Monitoring page allows you to shape how limit violations are detected and reported.

Many of these settings can also be specified on a Limit Group-specific basis. See the [Limit Group Dialog](18-general-tools.md#limit-group-dialog) for more information. If specified for a limit group, those settings will supersede those specified here with the contingency options.

Never report violations if…

This section controls the reporting of violations that should NEVER be reported. Minimum changes in branch flows, voltages, and interface flows which must be met before a device is reported as violating a limit can be specified. These options will only be used if the checkbox is checked at the beginning of this section. The minimum change values may be specified for:

**Increase in line/transformer flows** – This is the minimum change in percentage points that the loading on a line/transformer must increase before the line/transformer gets reported as a violation. For example, if this value is set to 2%, line limits are being monitored at 100%, and a line has a base case loading of 99% and a post-contingency loading of 100%, the line will not get reported as a violation.

**Decrease in low bus voltage** – This is the minimum change in a bus voltage that must occur for a bus low voltage violation to be reported. For example, if this value is set to 0.05 pu, the low voltage limit on a bus is 0.90 pu, the base case voltage at the bus is 0.91 pu, and the post-contingency voltage at the bus is 0.89 pu, this bus will not be reported as a low voltage violation.

**Increase in high bus voltage** – This is the minimum change in a bus voltage that must occur for bus high voltage violation to be reported. For example, if this value is set to 0.05 pu, the high voltage limit on a bus is 1.1 pu, the base case voltage at the bus is 1.09 pu, and the post-contingency voltage at the bus is 1.11 pu, this bus will not be reported as a high voltage violation.

**Increase in interface flows** – This is the minimum change in percentage points that the loading on an interface must increase before the interface gets reported as a violation. For example, if this value is set to 2%, interfaces are being monitored at 100%, and an interface has a base case loading of 99% and a post-contingency loading of 100%, the interface will not get reported as a violation.

Always report as a violation if…

This section allows you to specify the minimum change in flow or voltage at which point any device meeting the minimum change requirement will ALWAYS be reported, EVEN if the actual device limit (flow or voltage) is NOT violated. In other words, these options allow the reporting of large changes in flow or voltage, even if the device's actual limit is NOT itself violated. These options will only be used if the checkbox is checked at the beginning of this section. The minimum change values may be specified for:

**Increase in line/transformer flows** – This is the minimum change in line/transformer flow in percentage points that the loading on a line/transformer must increase so that the line/transformer gets reported as a violation even if the loading does not exceed the element’s limit. For example, if this value is set to 2%, line limits are being monitored at 100%, and a line has a base case loading of 50% and a post-contingency loading of 63%, this line will be reported as a violation even though the post-contingency loading does not exceed the limit.

**Decrease in low bus voltage** **** – This is the minimum amount that a bus voltage must decrease for a bus low voltage violation to be reported even if the resulting voltage is higher than the bus low voltage limit. For example, if this value is set to 0.05 pu, the low voltage limit at a bus is 0.90 pu, the base case voltage at the bus is 1.0 pu, and the post-contingency voltage at the bus is 0.95 pu, this bus will be reported as a low voltage violation.

**Increase in high bus voltage** – This is the minimum amount that a bus voltage must increase for a bus high voltage violation to be reported even if the resulting voltage is lower than the bus high voltage limit. For example, if this value is set to 0.05 pu, the high voltage limit at a bus is 1.10 pu, the base case voltage at the bus is 1.0 pu, and the post-contingency voltage at the bus is 1.05 pu, this bus will be reported as a high voltage violation.

**Increase in interface flows** – This is the minimum change in interface flow in percentage points that the loading on an interface must increase so that the interface gets reported as a violation even if the loading does not exceed the interface limit. For example, if this value is set to 2%, interface limits are being monitored at 100%, and an interface has a base case loading of 75% and a post-contingency loading of 77%, this interface will be reported as a violation even though the post-contingency loading does not exceed the limit.

Caution should be used when using the **Always report…** options because this may result in a very large number of reported violations.

Report changes in bus dV/dQ sensitivity

Check this option to enable reporting changes in voltage to reactive power sensitivity for buses in the post-contingency solution. Set the sensitivity multiplier to the minimum change in sensitivity for reporting the value(s) under contingency. Any sensitivity that changes by the given multiple will be reported. You can also define an [advanced bus filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) using the Define Filter button, and choose either the newly defined bus filter or a previously existing bus filter for reporting dV/dQ sensitivity changes at only buses that meet the defined filter.

Also, regardless of the sensitivity multiple setting, any bus that meets the filter and has a negative dV/dQ will be reported as a violation.

Caution should be used when selecting this option. Calculating the dV/dQ sensitivities requires more computation time. Define a filter so that the dV/dQ sensitivities are only calculated for those buses for which it is important to calculate these values.

Report as a violations if a bus becomes disconnected

When checked, buses that become disconnected from the system due to a contingency will be reported as violations.

Re-reporting of base case violations

This section controls the reporting of Base Case violations. Because the concern of contingency analysis often is to identify those limitations that result directly from a particular outage or event, you may desire not to report all violations that were present in the Base Case with each contingency-specific set of violations. These options allow you to specify just how much of the Base Case violation information to report for each contingency. It gives you three options:

Do not report Base Case violations

When this option is checked, any element that was violated in the Base Case is omitted from the set of violations listed for each contingency.

List all Base Case violations for all contingencies

When this option is checked, all elements that were violated in the Base Case and are still violated post-contingency are included in the set of violations listed for each contingency.

Use these criteria

When this option is checked, only those elements that were violated in the Base Case and that meet the four criteria listed below will be listed with the contingency-specific violations. The four criteria include:

**Minimum % increase in line/transformer flows**: Only those branches that were violated in the Base Case whose flow has increased by at least this amount as a result of the contingency will be listed as contingency violations.

**Minimum per-unit decrease in low bus voltage**: Only those bus voltages that were violated in the Base Case that have decreased by at least this amount as a result of the contingency will be listed as contingency violations.

**Minimum per-unit increase in high bus voltage**: Only those bus voltages that were violated in the Base Case that have increased by at least this amount as a result of the contingency will be listed as contingency violations.

**Minimum % increase in interface flows**: Only those interfaces that were violated in the Base Case whose flow has increased by at least this amount as a result of the contingency will be listed as contingency violations.

Percentage values here are expressed in reference to a limit rather than either the base case value or post-contingency flow value. When calculating the percentage for the Base Case violations used in the comparisons, the post-contingency rating sets are used. Comparisons made using percentage changes for branches are done using percentage points and not as a percentage of the actual change. For example, if the value for the minimum percent increase in line flow is 2%, lines are monitored at 100%, and a line is loaded at 100% in the base case and, the line must be loaded to at least 102% post-contingency to be reported.

How to Monitor Voltage Changes

Voltage changes can be monitored either directly on the amount of the bus per unit voltage, or based instead on a percentage change in per unit voltage from the base case per unit voltage values.

---

<a id="island-monitoring"></a>

## Island Monitoring

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Island_Monitoring.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Island_Monitoring.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 20

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Island Monitoring grouping.

Prior to Version 20, Simulator would report a contingency as Solved=NO if any island in the case did not successfully converge to a power flow solution. This meant that if you had a large system and your contingency split an electrical island into 2 islands, even if the new island had only a handful of buses (or Superbuses), then the entire Contingency would be flagged as Solved=NO. There is now an option available in the [Simulator Options dialog](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) called Evaluate Power Flow Solution for Each Island. Choosing this option will force Simulator to continue a power flow solution as long as at least one island continues to converge. Upon completing the contingency solution, the following options may then be used to report violations about islands.

Report Violations for Islands

Check this box to choose to report violations for any islands that either do not solve during the solution, or any islands that do not have enough generation MWreserves during the solution. These will appear as a special category of contingency violation called **Island Unsolved** or **Island Reserve Limits**. In addition to these, any new islands that are created as a result of the contingency will also be reported as a special category called **Island Solved**. Also, you may restrict it so Simulator does not report these special islands for small islands as defined by the following two options.

Minimum Load MW to report an island violation

Only report island violations if the total online load MW in the island is at least this amount.

Minimum number of super buses to report an island violation

Only report island violations if the total number of super buses in the island is at least this amount. For system which are not using Integrated Topology Processing, this would just be the count of the number of buses in the island instead.

---

<a id="monitoring-exceptions"></a>

## Monitoring Exceptions

*Source: [`Content/MainDocumentation_HTML/Monitoring_Exceptions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Monitoring_Exceptions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options Tab](#options-tab) under the Limit Monitoring grouping.

Monitoring exceptions can be used for bus, line, or interface elements to create special rules specifying how specific elements will be monitored under a specific contingency. These rules are exceptions to the case limit monitoring options that are set via the [Limit Monitoring Settings and Limit Violations Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). Monitoring exceptions allow the inclusion or exclusion of monitoring a particular element during a specific contingency. Monitoring exceptions override the monitor status of an element as specified with the case limit monitoring settings.

Monitoring exceptions can be defined and used as given below:

Monitoring Exceptions Dialog

The Monitoring Exceptions dialog is found on the Monitoring Exceptions tab of the [Contingency Definition Dialog](#contingency-definition-dialog). This dialog provides a list of all exceptions that are defined for the selected contingency and provides options about how to apply the exceptions.

![Monitoring Exceptions Dialog](images/Monitoring_Exceptions_Dialog.gif)

Use of Monitoring Exceptions

**Use these exceptions** - Select this option to enable use of the monitoring exceptions that are defined for this contingency. The defined exceptions will apply in addition to the case [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog).

**Ignore these exceptions** - Select this option to disable use of the monitoring exceptions that are defined for this contingency. Only the case [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog) will apply.

**Use only these exceptions and ignore the Limit Monitoring Settings** - Select this option to completely ignore the monitoring defined with the case [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). Only those exceptions with a **Monitor Exception Status** of *Include* will be monitored for this contingency. If the monitoring exceptions list is empty, nothing will be monitored for this contingency.

Monitoring Exceptions Table

The table lists all monitoring exceptions associated with the selected contingency. The standard fields that are listed in the table are detailed in the Monitoring Exceptions display section given below.

To insert a new monitoring exception, right-click on the table and choose **Insert** from the local menu. To edit an existing monitoring exception, right-click on the table and choose **Show Dialog** from the local menu. Either action will open the [Define Monitoring Exceptions dialog](#define-monitoring-exceptions-dialog).

Monitoring Exceptions Display

The Monitoring Exceptions display is found on the Monitoring Exceptions subtab of the Contingency Analysis dialog [Options tab](#options-tab). The Monitoring Exceptions display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with other case information displays.

This display lists all elements that have been selected as monitoring exceptions for all contingencies. The same default fields that are listed with this table are also listed with the Monitoring Exceptions Table that is found on the Monitoring Exceptions dialog detailed above.

The default fields include:

**Contingency** - This is the name of the contingency for which the exception applies.

**Contingency Use Monitoring Exceptions -** Value of the Use of Monitoring Exceptions option that can be set for each contingency. This option can only be set from the Monitoring Exceptions dialog.

Valid entries are:

**Use** - Use these exceptions

**Ignore** - Ignore these exceptions

**Only** - Use only these exceptions and ignore the Limit Monitoring Settings

**Monitored Element** - Bus, Branch, or Interface that is an exception to the monitoring. Element is identified by object type and [key fields](04-model-explorer-and-case-information-part3.md#key-fields).

**Monitor Exception Status** - Determines how an element is monitored as an exception to the case limit monitoring settings.

Valid entries are:

**Include** - The selected object will be included for monitoring with this contingency regardless of its status in the case limit monitoring settings.

**Exclude** - The selected object will be excluded in the monitoring with this contingency regardless of its status in the case limit monitoring settings.

**Default** - The selected object will obey its monitoring status in the case limit monitoring settings. Use this option when a particular monitoring exception should be ignored for a particular case but the object should remain in the list of monitoring exceptions.

---

<a id="define-monitoring-exceptions-dialog"></a>

## Define Monitoring Exceptions Dialog

*Source: [`Content/MainDocumentation_HTML/Define_Monitoring_Exceptions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Define_Monitoring_Exceptions_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to define exceptions for monitoring elements during specific contingencies. This dialog will open when choosing to insert a new exception or changing an exception from either the [Monitoring Exceptions dialog](#monitoring-exceptions) or the [Monitoring Exceptions display](#monitoring-exceptions).

![Define Monitoring Exceptions Dialog](images/Define_Monitoring_Exceptions_Dialog.gif)

Contingency Label

This gives the contingency for which the monitoring exception applies. Click the **Change** button to search through a list of all contingencies and select a different contingency. If inserting or changing monitoring exceptions from the [Monitoring Exceptions dialog](#monitoring-exceptions) that is shown with a given contingency, the contingency cannot be changed and the Change button will not be enabled.

Monitor Type

Three types of elements can be used for monitoring exceptions: bus, line, and interface. When changing the Monitor Type, the list of objects in the Object Selector will be updated accordingly.

Monitor Status

**Include** - The selected object will be included for monitoring with this contingency regardless of its status in the case limit monitoring settings.

**Exclude** - The selected object will be excluded in the monitoring with this contingency regardless of its status in the case limit monitoring settings.

**Default** - The selected object will obey its monitoring status in the case limit monitoring settings. Use this option when a particular monitoring exception should be ignored for a particular case but the object should remain in the list of monitoring exceptions.

Object Selector

Use this to select the object for the monitoring exception. Lists all objects in the case of the type selected under Monitor Type. Use the [filtering and search methods](04-model-explorer-and-case-information-part3.md#find-dialog-basics) to better manage the list in making a selection.

OK, Cancel

Click OK to accept the monitoring exception changes for the selected contingency and close the dialog. Click Cancel to close the dialog without accepting the changes.

---

<a id="custom-monitors"></a>

## Custom Monitors

*Source: [`Content/MainDocumentation_HTML/Custom_Monitors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Monitors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Custom Monitors can be defined, modified, and viewed from the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the [Limit Monitoring](#limit-monitoring) page. Custom Monitors are also available in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) in the Contingency Analysis folder under Custom Monitors.

Custom Monitors can be used to monitor specific objects and fields in addition to the devices that are monitored using the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings). Custom monitors do not represent violations, but rather, specific object fields that are of interest during the contingency analysis. Results for custom monitors will appear in the [Contingency Violations Display](#contingency-violations-display) and [Contingency Results tab](23-contingency-analysis-running-and-results.md#results-tab) on the [View Results By Element page](23-contingency-analysis-running-and-results.md#view-results-by-element). Custom monitors will only be stored when in ac power flow mode and NOT using one of the linear contingency methods. When in dc power flow mode or using one of the linear methods, the impact of contingencies are determined from linear sensitivity calculations and contingencies are not actually implemented. The system state is always in the base case state meaning that contingency values cannot be recorded when monitoring custom monitors.

Added in version 19, build on Dec. 23, 2016 In addition to monitoring objects, custom monitors can also be used to trip objects or abort the entire contingency simulation. This functionality is also only available when in ac power flow mode and not using one of the linear contingency methods. This functionality can be used for modeling cascading outages.

The Custom Monitors table is a type of [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus shares many of the properties and controls common to all other case information displays. Existing custom monitors can be edited directly in the table or by choosing Show Dialog either from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) obtained by right-clicking or choosing this option from the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar). To create a new Custom Monitor, choose Insert from the local menu or Case Information Toolbar.

The dialog for creating and modifying a custom monitor has the following options:

Custom Monitor Name

Name of the custom monitor. Each custom monitor must have a unique name. A default name will be created based on existing custom monitors. Click the **Rename** button to open a dialog that will allow you to change the name.

Enabled

Check this box for the specified object(s) and field to be monitored during a contingency analysis run. When this box is not checked, no results will appear for the custom monitor following a contingency analysis run.

Categories

A comma-separated list of user specified category names. Categories determine which Custom Monitors are applied to each contingency. See the [Contingency Category](21-contingency-analysis-overview-and-records.md#contingency-category) topic for more information.

Choose Object

All Objects of Element Type

Select this option to monitor all objects of the selected **Element Type**.

Specific Object

Select this option to monitor only a specific object of the selected **Element Type**. When this option is selected, the dialog will be modified with a chooser box that will allow selection of a specific object.

Element Type

Type of element to be monitored. One must be selected. Available elements types include: Area, Branch, Bus, DC Transmission Line, Generator, Injection Group, Interface, Limit Set, Load, Model Expression, Multi-Terminal DC Record, Nomogram, Owner, Substation, Super Area, Switched Shunt, Transformer, and Zone.

Choose a Field

Select the field to be monitored for the selected **Element Type**. A field must be selected.

Choose a Pre Filter

Name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device). This is an optional field that can be left blank. If this is specified, an object must meet this filter in the contingency reference state in order for it to be monitored in the contingency analysis run. This filter can be used in conjunction with the option for monitoring **All Objects of Element Type** to select a specific set of objects rather than all objects of the selected **Element Type**.

Click the **Add/Modify** button to specify this filter.

Choose a Post Filter

Name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device). This is an optional field that can be left blank. If this is specified, an object must meet this filter in the post-contingency state in order for it to be monitored in the contingency analysis run.

Click the **Add/Modify** button to specify this filter.

Options Specific to Contingency Results

The following options are useful if the goal is to use the custom monitors to report some sort of "violation." The options will allow comparison of the reference state value to the post-contingency state and allows elimination of the custom monitor object based on that comparison. This is something that cannot as easily be accomplished through the Post Filter as there is no direct access to the post-contingency values through the object being monitored.

Never report violations if the increase in field value \<=

This value must be entered as a positive number. If the difference between the post-contingency and the reference monitored state value (Post-contingency - Reference) is greater than this threshold, the object result will be reported.

Never report violations if the decrease in field value \<=

This value must be entered as a positive number. If the difference between the reference state and the post-contingency monitored value (Reference - Post-contingency) is greater than this threshold, the object result will be reported.

Meaning of Change Values

There are two possible interpretations of the change between the reference state and post-contingency monitored values:

Change from Initial Value

This will do a direct comparison of the difference between the post-contingency and reference monitored values, i.e. check Post-contingency minus reference state value against the specified threshold when checking for the increase or Reference state minus post-contingency value when checking for the decrease.

% Change from Initial Value

This will compare the percentage of the change, (Post-contingency - Reference)/(Reference), against the specified threshold when checking for the increase. (Reference - Post-contingency)/(Reference) will be used when checking for the decrease.

Device Tripping Added in version 19, build on Dec. 23, 2016

In addition to monitoring values, custom monitors can be used to trip an object or completely abort the contingency simulation if a condition is met. This functionality can be used for modeling cascading outages.

Custom monitors for tripping and aborting are evaluated in the POSTCHECK portion of the contingency process as shown with this [description of the processing order of contingencies](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis).

The following options are available when using these features:

Start Tripping Filter

Name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device). This filter is applied to objects that meet the chosen **Element Type** or **Specific Object** and objects that meet the **Pre Filter** to determine if there are any objects that meet this filter. This filter is applied in the post-contingency state.

If the **Action to Take** is *Trip (Open) Device* and no tripping actions have already occurred for this custom monitor, this filter must be met before any objects are tripped. After at least one object is tripped for this custom monitor, the **Post Filter** is used for all subsequent checks to determine if any additional objects should trip.

If the **Action to Take** is *Abort Simulation*, this filter must be met for the entire simulation to be aborted.

Action to Take

**Log Violation Only**

This will record the monitored value as a violation with the contingency results. No additional actions will be taken.

**Trip (Open) Device**

This will open the object if it meets the appropriate filters. If no objects have been tripped for this custom monitor, the **Start Tripping Filter** must be met. If at least one object has tripped for this custom monitor, the **Post Filter** must be met.

**Abort Simulation**

This will abort the entire contingency simulation if the **Start Tripping Filter** has been met.

Use a Time Delay of

This is the amount of time to wait in seconds before the tripping or abort action is actually applied. This time is compared against the time delay of other contingency events that might occur at the same point in the contingency process. Only the events with the smallest time delay will actually be applied. If the custom monitor trip or abort action has a longer time delay than other contingency actions, it will not be applied.

A description of how time delays are treated during the contingency process can be found with the [Treatment of Time Delay of Contingency Elements and Model Filter Condition Time Delays](23-contingency-analysis-running-and-results.md#treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays) topic.

---

<a id="contingency-definitions"></a>

## Contingency Definitions

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_ContingencyDefinitions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_ContingencyDefinitions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);) 

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Contingency Definitions grouping:

All Contingency Elements

Contains a combined list of all the contingency elements for all contingency records.

---

<a id="contingency-definition-dialog"></a>

## Contingency Definition Dialog

*Source: [`Content/MainDocumentation_HTML/Contingency_Definition_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Definition_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Definition Dialog (shown below) serves as an information source for displaying the Contingency Element (or Elements) associated with individual contingencies defined in the case. You can use the Contingency Definition Dialog to scroll through the list of elements, to view and modify their definitions, to insert new elements in a contingency or to delete a contingency. You may access this dialog by choosing either **Show Dialog** or **Insert** from the local menu of the [Contingency Records Display](#contingencies-tab).

After making changes, click **OK** to save your changes and close the dialog. Click **Cancel** to close the dialog without saving your changes. Click **Save** to save your changes (including the addition of a new contingency) without closing the dialog (this allows you to keep working with the dialog). Click **Delete** to remove the selected contingency from the contingency list.

![CTG Definition Dialog](images/CTG_Definition_Dialog.gif)

Contingency Definition Dialog

The Contingency Definition Dialog has the following controls that are available regardless of the tab that is currently selected:

Contingency Label 

Identifies the name of the currently displayed contingency.

Add New

Click the **Add New** button to add a new contingency to the contingency list for the case. You will be prompted to enter a unique name for the new contingency. After naming the new contingency, the name appears in the Contingency Label and you can insert new elements in the contingency definition.

Rename 

Allows you to rename the selected contingency.

Find

Opens a dialog that will allow the use of [advanced search methods](04-model-explorer-and-case-information-part3.md#find-dialog-basics) for finding a particular contingency.

Definition Tab

Insert New Element

Click this button to add a new element to the contingency. This will open the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog), used to define the Action, Model Criteria and Comment associated with the element. When you return to the Contingency Definition Dialog, the display will contain the newly inserted element.

Clear All

Removes all elements from the contingency definition. The Contingency Elements Table will then appear blank, indicating that the contingency involves no associated actions.

Definitions Display

The Contingency Definitions Display lists the elements assigned to the selected contingency. Select **Insert** from the local menu or click on the **Insert New Element** button to add elements to the contingency. Right-click on a specific element in the display and select **Delete** from the local menu to remove the element from the contingency. For more information about this display, see the [Contingency Definitions Display](#contingency-definition-display).

Categories

A comma-separated list of user specified category names. Categories determine which [Custom Monitors](#custom-monitors) are applied to each contingency. See the [Contingency Category](21-contingency-analysis-overview-and-records.md#contingency-category) topic for more information.

Define Solution Options

Click this button to open the [Contingency Solution Options Dialog](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options), used to define specific power flow solutions options for use under the selected contingency.

Use Specific Solution Options

Check this box to enable the use of Contingency Specific Solution Options (see Define Solution Options above).

Ignore ALL contingency specific solution options

If checked, all contingency specific options, either defined individually for the specific contingency or defined globally in the contingency options for all contingencies, are ignored. The [solution options](10-power-flow-solution-and-options-part1.md#simulator-options) as saved with the case will be used.

Include Remedial Actions Added in Version 20

Check this box to include Remedial Actions and Global Actions with this contingency.

Allow Screening Added in Version 20

Check this box to run the [screening process](#dc-and-screening-options) for this contingency. If not running the screening process for this contingency and the screening process is being used, the full ac contingency analysis will always be run for this contingency.

Post-Contingency Auxiliary File

The auxiliary file specified here will be loaded at the start of this contingency, which can be used to alter the reference state for this contingency. If an auxiliary file is specified here, the contingency options [Post-Contingency Auxiliary File](#auxiliary-files) will not be loaded for this contingency. This file is applied before any [contingency-specific solution options](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options) are applied. The contingency actions are then implemented after any contingency-specific solution options are applied.

Click the **Browse** button to open a file dialog for file selection. To remove the file, delete the contents of the text box.

If the file specified does not include a file path, then Simulator will look in the presently active directory, otherwise the file path specified will be used. If the post-contingency AUX file cannot be found in this location, then Simulator will look to see if a file by this name exists in the directory from which the presently loaded case was read. If a file is specified and still cannot be found, then when running the analysis from the contingency analysis dialog, Simulator will show a dialog requesting you to find the file or remove the option.

Instead of specifying a file here, a string containing script commands can be used instead. Multiple script commands can be separated by semi-colons. This will allow the same functionality without requiring a file to be present.

Only data stored with the contingency reference state will be "reset" when the reference state is restored. Therefore, only data stored with the reference state should be loaded via a post-contingency auxiliary file. Click [here](21-contingency-analysis-overview-and-records.md#reference-state-information) for details on the specific information stored with the reference state.

Custom Tab

The [Custom page](01-getting-started.md#memo-display) of the dialog contains two sections: custom fields and memo.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the contingency. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the contingency. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

Monitoring Exceptions Tab

Monitoring exceptions can be defined for each contingency. Defining exceptions is useful when specific elements need to be excluded or included for monitoring on a contingency-by-contingency basis. Click [here](#monitoring-exceptions) for more information about monitoring exceptions.

---

<a id="remedial-action-definitions"></a>

## Remedial Action Definitions

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_RemedialActionDefinitions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_RemedialActionDefinitions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Remedial Action Definitions grouping:

Remedial Actions

Contains a list of all [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions). A Remedial Action is a group of actions that will be processed with EACH contingency.

Remedial Action Elements

Contains a combined list of all of the remedial action elements for all Remedial Action records.

Model Conditions

Clicking this button brings up a list of [model conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog). Model Conditions may be used as part of the Model Criteria defined with [Contingency Elements](24-contingency-element-dialog.md#contingency-element-dialog).

Model Filters

Clicking this button brings up a list of [model filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog). Model Filters may be used as part of the Model Criteria defined with [Contingency Elements](24-contingency-element-dialog.md#contingency-element-dialog).

Model Expressions

Clicking this button brings up a list of [model expressions](04-model-explorer-and-case-information-part2.md#model-expressions). Model Expressions may be used as part of Model Conditions.

Model Result Override Added in Version 20

Clicking this button brings up a list of [model result overrides](#model-result-override). Model Result Overrides may be used to override the result of Model Conditions and Model Expressions.

See the [Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions](52-additional-linked-topics-part1.md#relationship-between-contingencies-model-conditions-model-filters-and-model-expressions) topic for more information about how these work together.

---

<a id="model-result-override"></a>

## Model Result Override

*Source: [`Content/MainDocumentation_HTML/Model_Result_Override.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Result_Override.htm)*

Added in Version 20

Model Result Overrides allow the direct specification of the result of a [Model Condition](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog), [Model Filter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog), or [Model Expression](04-model-explorer-and-case-information-part2.md#model-expressions). When a Model Result Override is active, the logic for the object it is overriding is ignored. This is useful with EMS cases where real-time measurements might determine RAS arming. The logic of the overridden object can remain defined and used when necessary, but a direct replacement of the result is very simple without having to redefine contingency action and remedial action model criteria.

Model Result Overrides can be found in the Model Explorer under **Case Information and Auxiliary \> Model Result Overrides** or on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) on the [Options tab](#options-tab) in the [Remedial Action Definitions grouping](#remedial-action-definitions).

Model Result Override Display

The Model Result Override Display is a type of [Case Information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has the abilities common to this type of display. To create a new Model Result Override, select **Insert** from the local menu. This will open a dialog for entering the **Name** of the model result override. All other parameters for the model result override can be specified in the fields in the display.

The following fields are shown by default on the display:

Name

Unique identifier for the model result override.

Model Object

This is the object type and name of the Model Condition, Model Filter, or Model Expression to which the override is applied. To specify the model object, select this field and the dialog button will appear to the far right of the cell. Click the dialog button to open a dialog that contains an object chooser which allows easy selection of the model object. Double clicking on this field will also open the model object selection dialog.

Result Value

This field will be non-blank if the **Model Object** chosen is a Model Expression. This specifies the value result of the Model Expression that is being overridden.

Result Boolean

This field will be non-blank if the **Model Object** chosen is a Model Condition or Model Filter. This specifies the boolean (YES/NO) result of the Model Condition or Model Filter that is being overridden.

Enabled

Set this field to YES to apply the override and use the result specified in either the **Result Value** or **Result Boolean** field for the chosen **Model Object** and ignore the logic defined with the object itself.

Model Object Overridden Indicators

Model Conditions, Model Filters, and Model Expressions all have an **Overridden** field available in their list of available fields. This field indicates if the object is being overridden by an enabled Model Result Override. If this field is YES, the result that is displayed for the object is the result, either the **Result Value** or **Result Boolean** depending on the object type, that is specified with the Model Result Override.

The object dialogs for these objects also have indicators in which parts of the dialogs will be highlighted in yellow and special messages appear if the object is being overridden by an enabled Model Result Override.

---

<a id="distributed-computing"></a>

## Distributed Computing

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_DistributedComputing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_DistributedComputing.htm)*

**The Distributed Contingency Analysis tool is available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for more details.****

These options are all available on the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options Tab](#options-tab) under the Distributed Computing Grouping.

Distributed Computing is available for use with Contingency Analysis. In order to use distributed computing you must first configure a list of remote computers which can be utilized along with appropriate authentication information for those computers. The computer list and authentication information is common to all the distributed computing tools in Simulator and can be found in the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), or reached with the Distributed Computing Options button. They are described in [Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons).

The only two options specific to Contingency Analysis for Distributed Computing are as follows

Use Distributed Computing

Check this box to signify that when processing contingencies distributed computing should be used.

Number of Contingencies per Process

When distributed computing is used for contingency analysis, the entire list of contingencies to be solved will be split up into groups of contingencies. This setting specifies the number of contingencies to include in each group. During the distributed computing, Simulator will sent a group of contingencies to each computer available as specified in the [Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons). As the remote computers complete a group, Simulator will send another grouping to that computer. This will continue until the contingency analysis results are completed.

---

<a id="miscellaneous"></a>

## Miscellaneous

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Miscellaneous.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Miscellaneous.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](#options-tab) under the Miscellaneous grouping.

Always save results with the contingency list when you save it to a file

If this option is checked, the violation results for each contingency will also be stored in an auxiliary file when the list of contingencies is saved to an auxiliary file. This allows for recovering the results of a contingency analysis run for a case, without reloading and re-running all the contingencies saved in the file.

Save contingency analysis definitions/results in the case PWB file

If this option is checked, the contingency definitions and any processed results will be saved with the load flow case in the PWB file when you save the case.

Setting Reference Case when Contingency Analysis is Opened

These options determine how the reference case for the contingency analysis is treated each time you open the contingency analysis dialog. The reference state is initially defined as the power system state that exists when the contingency analysis is run for the first time for a given power flow case during a Simulator session. The exception to this is that it might be set to the current system state when the dialog is open, prior to running any analysis, if the option that is described below is specified to set the reference case each time that the dialog is opened. (See [Contingency Case References - Defining the Reference State](21-contingency-analysis-overview-and-records.md#defining-the-reference-state) for more information.) The choices are to how this option can be set are:

Always set reference case to the current case

This option will always assume that any changes you have made to the load flow case since the contingency analysis was last opened should be applied and will store the current state of the load flow as the new reference state for the contingency analysis.

Always use the existing contingency analysis reference case

This option will assume that if the contingency reference state has already been set, just continue to use that. This means that any changes that have been made to the load flow case since the initial setting of the reference case will be lost, as the contingency analysis tool will reset the load flow state to the stored reference state.

Prompt for which reference case to use (the current case or the pre-existing reference case) whenever the Contingency Analysis Form is opened

When this option is checked, you will always be prompted when you open the contingency analysis if the reference case has already been set. You will then have the option to choose from one of the two previous settings, to either set the reference state to the current case or use the existing reference case currently stored with the contingency analysis tool.

Contingency Action Description in What Occurred

This provides options for the naming convention used when identifying the actions that occurred during the contingency. This affects how the Actions are specified in the [What Occurred](23-contingency-analysis-running-and-results.md#what-occurred) information. This option needs to be changed BEFORE the contingency analysis is run. If it is changed AFTER, no changes are made to the action identifier.

---

<a id="contingencies-tab"></a>

## Contingencies Tab

*Source: [`Content/MainDocumentation_HTML/Contingencies_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingencies_Tab.htm)*

The Contingencies tab of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) provides tools for managing and simulating lists of contingencies. The top portion of the page lists the contingency records that have been defined for the case. This table is called the Contingency Records Display. The contingency records display is a type of [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus shares many of the properties and controls common to all other case information displays.

General Functionality

You can sort the display’s contents by any field just by clicking on the field’s heading. The default fields shown in the contingency records display are described at the bottom of this page.

As you scroll through the records in the contingency records display, you will notice that the contents of the tables that occupy the middle third of the contingency analysis dialog change. These tables are the [Contingency Definition Display](#contingency-definition-display), the [Contingency Violations Display](#contingency-violations-display), and the [What Occurred Display](23-contingency-analysis-running-and-results.md#what-occurred). These displays show the violations, the specific actions, and what actions were applied if the contingency was implemented for the contingency that is selected in the contingency records display at the top of the dialog. You may optionally hide the Contingency Definition Display by clicking on the X to the upper right of this display. To show the display again, click on the O to reopen it. You may change the relative width of the Contingency Definition and Violations/What Occured displays by moving your mouse over the line between the displays until your cursor changes. Then left click and drag to modify these widths.

When you first load a new contingency list into memory, the current status indicator along the bottom of the display will indicate the contingencies have been Initialized. During a contingency analysis run, the current status indicator may take on the values *Running*, *Paused*, *Aborted*, or *Finished*.

The contingency tab of the contingency analysis dialog offers several ways to run the contingency analysis. To start a run, you may click the **Start Run** button. Alternatively, you may choose **Run Contingency Analysis** from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the contingency records display. Once a contingency analysis run has started, you may pause it at any time by clicking the **Pause Run** button, after which you may resume the run by clicking **Continue**. In addition to running the full set of contingencies, you may also choose to run just a single contingency. See [Running the Contingency Analysis](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis) for more details.

Several other actions related to contingency analysis are also available from the Contingencies Tab. These are accessed by clicking on the **Other Actions \>** button. They are described on the [Other Contingency Actions](23-contingency-analysis-running-and-results.md#other-contingency-actions) page.

You may close the Contingency Analysis Dialog at any time either by clicking **Close** or by selecting **Close** from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the Contingency Records Display or the [Contingency Violations Display](#contingency-violations-display).

Local Menu Options

By right-clicking on the display, you gain access to its [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which offers several choices:

  - **Insert** allows you to insert a new contingency record
  - **Insert Special** gives the following options:
      - **Quick Insert of Single Element Contingency** will allow you to quickly specify a single element contingency via the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog)
      - **Auto Insert Contingencies** will open the [Auto Insert Contingencies](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) dialog
      - **Merge Contingency Block Elements** will eliminate contingency blocks by adding the elements that are in contingency blocks to the contingency elements, Global Actions, or Remedial Actions that are using the blocks. We encourage you to discontinue use of [Contingency Blocks](21-contingency-analysis-overview-and-records.md#contingency-blocks).
      - **Convert Global Actions into Remedial Action** will convert legacy [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) into a more versatile [Remedial Action](21-contingency-analysis-overview-and-records.md#remedial-actions). A single Remedial Action will be created. We encourage you to use Remedial Actions instead of Global Actions.
      - **Merge Pairs of Selected Contingencies** will generate every possible pair of contingencies based on the selected contingencies. For instance, if you select 4 contingencies (A, B, C, D), then click **Merge Pairs of Selected Contingencies**, 6 new contingencies will be generated: A+B, A+C, A+D, B+C, B+D, and C+D.
      - **Clone Contingencies** will make a copy of each selected contingency.
      - **Join Active Contingencies** creates new contingencies that are the join of the current contingency list and a list read in from an auxiliary file or the present list itself. Contingencies with their **Skip** property set to YES will not be included in the join. A dialog will allow selection of the list to join with the present list. The dialog will also allow you to insert a solve power flow action between the joined actions and delete the original existing contingencies upon completion of the join.
      - **Create Stuck Breaker Contingencies...** creates new contingencies from contingencies that have explicit breaker outages defined. New contingencies will be created by treating each breaker as stuck in turn. The new contingencies will be comprised of all existing elements, minus the stuck breaker outage, plus open actions for breakers that are identified to isolate the stuck breakers. Only branches with Branch Device Type of *Breaker* will be considered in determining the stuck breakers. Selecting this option will open a dialog with options as described in the [Create Stuck Breaker Contingencies](52-additional-linked-topics-part1.md#contingencies-tab-create-stuck-breaker-contingencies) topic.
    <!-- end list -->
      - **Create Expanded Breaker Contingencies** converts any "Open with Breakers" or "Close with Breakers" contingency actions into OPEN or CLOSE actions on explicit breakers. This will permanently modify the contingency definitions.
      - **Merge Contingencies that Result in Identical Breaker Actions** will modify existing contingencies. If a contingency is defined with OPENCB or CLOSECB actions and results in the same set of actions as another contingency, the contingencies will be merged into a single contingency. One contingency will be retained and the other deleted. The one that is retained contains the highest priority element with the priority determined by: (1) line with largest X, (2) generator with largest MaxMW, (3) load with largest Nominal MW, and (4) switch shunt with largest nominal Mvar.
      - **Convert into Primary Contingencies** converts regular/secondary contingencies to Primary contingencies that are used with CTG Combo Analysis. After selecting this option a dialog will open that contains the following options for the conversion. Once the options are set, click the **OK** button to do the conversion or **Cancel** to abandon the conversion. Not all actions that are supported for regular/secondary contingencies are supported for Primary contingencies. Examine any messages in the log after the conversion to determine if actions were not converted.
          - **Only Selected**
          - The contingencies that have been selected by using the mouse will be converted.
          - **Currently Displayed**
          - All contingencies that are currently in the display will be converted. If an advanced filter or area/zone/owner filter is being used, only the contingencies that are displayed because they meet the filter will be converted.
          - **Keep the original contingency**
          - The original regular/secondary contingency will be retained and a new Primary contingency will also be created.
          - **Delete the original contingency**
          - The original regular/secondary contingency will be deleted and a new Primary contingency will be created.
          - **Prefix**
          - The Primary contingency will be named using the name of the regular/secondary contingency modified including this prefix.
          - **Suffix**
          - The Primary contingency will be named using the name of the regular/secondary contingency modified including this suffix.
  - **Delete** allows you to delete a particular contingency
  - **Show Dialog** displays the [Contingency Definition Dialog](#contingency-definition-dialog) corresponding to a particular contingency
  - **Contingency Records** gives the following options:
      - **Open Dependency Explorer** will open the [Dependency Explorer](21-contingency-analysis-overview-and-records.md#dependency-explorer) with the selected contingency as the *Top* object
      - **Solve Selected Contingency** (see [Contingency Case References - Reference State Solution Options](21-contingency-analysis-overview-and-records.md#reference-state-solution-options))
      - **Solve and Set as Reference** (see [Contingency Case References - Reference State Solution Options](21-contingency-analysis-overview-and-records.md#reference-state-solution-options))
      - **Apply Selected Contingency** will apply the actions in the contingency definition, but does not solve the contingency or calculate violations.
      - **What Occurred** will display the details of the actions that were applied and skipped during the contingency (see [](23-contingency-analysis-running-and-results.md#what-occurred)[Contingency Results: What Occurred](23-contingency-analysis-running-and-results.md#other-contingency-actions))
      - **Run Contingency Analysis** (see [Running the Contingency Analysis](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis))
      - **Filter Results Using Limit Monitoring Settings** (see [Other Contingency Actions](23-contingency-analysis-running-and-results.md#other-contingency-actions))
      - **Compare Contingency Definitions** will compare the current contingency list against a contingency list stored in a user-specified auxiliary file. The results of comparison are saved in a user-specified CSV (Comma-Separated Value) file. To determine if contingencies are the same, only their actions are compared. Model Criteria is not included.
      - **Compare Two Lists of Contingency Results** (see [Comparing Contingency Analysis Results](23-contingency-analysis-running-and-results.md#comparing-two-contingency-analysis-results))
      - **Verify Contingencies for Iterated Linear Actions** will evaluate the contingency list and save a summary of fields that are handled and not handled properly if using the iterated linear method. The user is prompted to specify a text file in which to save the summary. (see [Contingency Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis))
  - Many other options (e.g., printing, finding, and sorting) which are characteristic of [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays).
  - **Save As** gives several options characteristic of case information displays as well as options unique to the contingency records display:
      - **Auxiliary File**, **Auxiliary File (only selected records)**, and **Auxiliary File (only selected records/columns)** will only save contingency definitions. Any supporting data such as contingency blocks, global actions, model criteria, etc. will not be saved. To make sure that this supporting data is saved, use one of the **(all contingency related info)** options described below.
      - **Auxiliary File with Options** and **Auxiliary File with Options (Last Used)** will save contingency definitions using options that specify the objects to save and formats to use according to the [Saving Auxiliary Files with Options dialog](52-additional-linked-topics-part1.md#saving-case-information-display-contents-as-html-tables). The **(Last Used)** option allows quickly saving using the options that were last specified without having to change options in the dialog.
      - **Auxiliary File (all contingency related info)** first opens a file dialog for specification of the auxiliary file. Clicking Save from the file dialog opens a **Contingency Settings** dialog for specification of related settings to save in the same auxiliary file, including [Contingency Options](#options-tab), [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings), [General Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options), List Display Settings ([Case Information Customization](04-model-explorer-and-case-information-part1.md#case-information-customizations-display)), Contingency Results, and whether or not to save unlinked elements. Definitions of all contingencies are also saved. This has the same functionality as clicking the **Save** button in the bottom panel.
      - **Auxiliary File (all contingency related/only selected records)** has the same functionality as **Auxiliary File (all contingency related info)**, except contingency definition(s) are only saved for the selected contingency record(s). You may also specify related settings to save.

Field Descriptions

By default, the contingency records display presents the following fields:

Label

The name of the contingency.

Category

Comma-separated list of user specified category names. Categories determine which Custom Monitors are applied to each contingency. See the [Contingency Category](21-contingency-analysis-overview-and-records.md#contingency-category) topic for more information.

Skip

Indicates whether Simulator should skip the corresponding contingency in performing the contingency analysis. If the value of the Skip field is *YES* for a contingency, then that contingency will not be implemented when performing the contingency analysis. This is a toggleable field, which means that you can toggle its value by double-clicking the field.

Processed

Indicates whether the contingency has been analyzed yet as part of the current contingency run. Possible entries are *YES* and *NO*.

Solved

The possible entries for this field are as follows. Based on the entry fields for the contingency record will be highlighted if the contingency has been processed:

**NO** - Contingency has not been processed (**Processed** = *NO*) or contingency has been processed (**Processed** = *YES*) but the power flow is unable to converge within tolerance. Highlighting color is light red.

**YES** - Contingency has been processed (**Processed** = *YES*) and the power flow is able to converge within tolerance. Highlighting color is the normal fill color.

**ABORTED** - Contingency that has been aborted due to an [Abort](24-contingency-element-dialog.md#type-abort) contingency action being implemented. Highlighting color is light orange.

**RESERVE LIMITS** - Indicates that there was not enough MW reserves in the [make-up power](#basics) specification to cover the MW changes caused by the contingency. This can only result if enforcing generator MW limits for the make-up power option selected. This will only be reported for full ac contingency analysis. Violations will still be recorded if there are any, but you must be aware that a portion of the make-up power has been covered by the system slack bus instead of the specified make-up power option. To see how much deficit there is in the reserves, the **Make Up Power Deficit** field can be added to the contingency records display. Highlighting color is light yellow.

**PARTIAL** -Added in Version 20 Indicates that there are multiple islands in the solution and some islands solved while other islands did not solve. If using the option to [Report Violations for Islands](#island-monitoring), the islands that were unsolved will be reported as violations. Highlighting color is light yellow.

Include Remedial Actions Added in Version 20

Indicates if all Remedial Actions and Global Actions should be included with this contingency. Possible entries are *YES* and *NO*.

Screen Allow Added in Version 20

Indicates if the contingency [screening process](#dc-and-screening-options) should be run for this contingency. Possible entries are *YES* and *NO*. If this is set to *NO* and the screening process is being used, the screening process will not be run for this contingency and the full ac contingency analysis will always be run for this contingency.

Post-CTG AUX

The auxiliary file specified here will be loaded at the start of this contingency, which can be used to alter the reference state for this contingency. If an auxiliary file is specified here, the contingency options [Post-Contingency Auxiliary File](#auxiliary-files) will not be loaded for this contingency. 

Double-click a cell to edit the specified post-contingency auxiliary file. A specified post-contingency auxiliary file may be removed using the [Contingency Definition Dialog](#contingency-definition-dialog).

Only data stored with the contingency reference state will be "reset" when the reference state is restored. Therefore, only data stored with the reference state should be loaded via a post-contingency auxiliary file. Click [here](21-contingency-analysis-overview-and-records.md#reference-state-information) for details on the specific information stored with the reference state.

Islanded Load

Displays the sum of the amount of load that was islanded from the rest of the system due to the contingency. This will only include load that is islanded due to changes in topology. It does not include load where the status of the load is opened as part of the contingency.

Islanded Gen

Displays the sum of the amount of generation that was islanded from the rest of the system due to the contingency. This will only include generation that is islanded due to changes in topology. It does not include generation where the status of generator is opened as part of the contingency.

Global Actions

Number of [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) applied during a contingency.

Transient Actions

Number of [Transient Actions](#transient-models) applied during a contingency.

Remedial Actions

Number of [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions) applied during a contingency.

Custom Monitor Violations

Number of [Custom Monitors](#custom-monitors) that are listed with the Violation results. The **Violations** value does not include the number of Custom Monitors in the Violations.

Violations

This field has several entries based on the value of the **Solved** field. If **Solved** is the following, the explanation determines what the **Violations** field contains:

**NO** - The string *Unsolvable* will be displayed

**YES** - An integer number identifying the number of violations caused by this contingency. This number represents the total number of violations (branch thermal violations + bus violations + interface violations) that were caused by the contingency. Depending on how you have configured the [reporting of Base Case violations](#advanced-limit-monitoring), this number may include all, some, or none of the violations that were present in the Base Case model.

[Custom Monitors](#custom-monitors) are listed with the [Violations results](#contingency-violations-display), but they are not included in the total number of violations caused by this contingency. Separate fields exist that provide the number of violations of specific types, i.e. **Branch Violations**, **Bus Violations**, **Interface Violations**, and **Custom Monitor Violations**.

**ABORTED** - The string *Aborted* will be displayed

**RESERVE LIMITS** - The string *All make-up power at limits* will be displayed

**PARTIAL** - The string *Partial* will be displayed Added in Version 20

Max Branch %

Indicates the percentage overload of the worst-case branch violation. If there are no branch violations, this field will be blank.

Min Volt

Indicates the lowest bus voltage resulting from the contingency. If there are no low voltage violations, this field will be blank.

Max Volt

Indicates the highest bus voltage resulting from the contingency. If there are no high voltage violations, this field will be blank.

Max Interface %

Indicates the percentage overload of the worst-case interface violation. If there are no interface violations, this field will be blank.

Max Bus Pair Angle Added in Version 20

Indicates the maximum angle difference for all bus pair violations resulting from the contingency. If there are no bus pair violations, this field will be blank.

Memo

User specified text entered for a particular contingency.

---

<a id="contingency-definition-display"></a>

## Contingency Definition Display

*Source: [`Content/MainDocumentation_HTML/Contingency_Definition_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Definition_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Definition Display lists the elements assigned to the selected contingency. This display appears on both the [Contingency Tab](#contingencies-tab) and the [View Results By Element](23-contingency-analysis-running-and-results.md#view-results-by-element) page of the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog), it also appears on the [Contingency Definition Dialog](#contingency-definition-dialog). This display is also used in a modified form when showing the Remedial Action Elements that are part of a [Remedial Action.](21-contingency-analysis-overview-and-records.md#remedial-actions)

Select **Insert** from the local menu to add elements to the contingency. Right-click on a specific element in the display and select **Delete** from the local menu to remove the element from the contingency.

The contingency definition display is a type of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and shares many characteristics and controls common to all other case information displays.

The Contingency Definition Display contains the following fields when showing contingency elements and remedial action elements:

Actions

This shows a string that describes the action. You may customize the format of the string that describes the contingency actions by right-clicking on the Contingency Definition Display and choosing **Display Descriptions By**, and then choosing *Name*, *Num*, *Name/Num*, *PW File Format by Numbers*, *PW File Format by Name/kV*, *PTI File Format*, or *Label*.

See the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details on the contingency actions that can be defined.

Model Criteria

This specifies a criterion under which a contingency action will occur. See the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

Status

This field determines how an action is applied in the presence or absence of **Model Criteria**. See the [Contingency Element Status](24-contingency-element-dialog.md#contingency-element-status) topic for more details.

Persistent

This field determines if an action can be applied after it has already been applied. See the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

Time Delay

This specifies the time to wait in seconds before an action is applied. See the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

Comment

An optional user-specified comment string associated with the action. See the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

The Contingency Definition Display is also used when showing Remedial Action Elements. This display will appear on the [Remedial Action Definition dialog](52-additional-linked-topics-part1.md#remedial-action-definition-dialog) and when showing the [Remedial Actions Display](21-contingency-analysis-overview-and-records.md#remedial-actions) on the [Options tab](#options-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). In addition to the fields listed above, the following fields are included:

Inclusion Filter

This is an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device) that determines if the remedial action element is applied with each contingency. See the [](52-additional-linked-topics-part1.md#remedial-action-definition-dialog)[Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog)topic for more details.

Arming Criteria Added in Version 20

This specifies a criterion under which a remedial action element will be armed. See the [](52-additional-linked-topics-part1.md#remedial-action-definition-dialog)[Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

Arming Status Added in Version 20

This specifies how arming of the remedial action element is determined in the presence or absence of **Arming Criteria**. See the [](52-additional-linked-topics-part1.md#remedial-action-definition-dialog)[Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) topic for more details.

Armed Added in Version 20

This specifies if the remedial action element is currently armed. This determination is made based on the present system state and might differ from how arming is determined during the contingency analysis process. Model Conditions and Model Filters have options that allow them to be disabled if they are true in the contingency reference state. These options are ONLY applied during the contingency analysis process and are not applicable when the value of the Armed field is determined.

In order for a remedial action element to actually be implemented, it must be armed based on its own criteria and the Remedial Action to which it belongs must also be armed. Remedial Actions have their own Arming Criteria and Arming Status that are described with the [Remedial Action Definition dialog](52-additional-linked-topics-part1.md#remedial-action-definition-dialog) topic.

---

<a id="contingency-violations-display"></a>

## Contingency Violations Display

*Source: [`Content/MainDocumentation_HTML/Contingency_Violations_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Violations_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Violations Display is found at the bottom of the [Contingencies tab](#contingencies-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) and is used to list the violations that were caused by the contingency selected in the [Contingency Records Display](#contingencies-tab).

The contingency violations display lists all of the power system elements that become violated as a result of the selected contingency. If you have selected a violation, you may click on the **Show related contingencies** button to view all contingencies that cause a violation on this power system element. Clicking this button automatically moves you to the [Results tab](23-contingency-analysis-running-and-results.md#results-tab) and selects the appropriate power system element. You can also right-click on a violation in the list and choose **Show Dialog** from the popup menu to see the information dialog of the violated element. In addition to showing violations for branches, buses, interfaces, bus pairs, islands, and the system, results for [Custom Monitors](#custom-monitors) or [Transient Models](#transient-models) will also be displayed here. Custom Monitors are not violations, but are specific quantities that are tracked in addition to the limit monitoring.

If the contingency selected in the Contingency Records Display resulted in no violations or has not yet been processed, the Contingency Violations Display will display the words *None Defined*. This display is a type of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus shares many characteristics and controls common to all other case information displays. You can sort the list of violations by any field simply by clicking on that field’s caption.

The **Combined Tables** button provides access to the Combined Tables options described in [Other Contingency Actions](23-contingency-analysis-running-and-results.md#other-contingency-actions). In addition to these options, there is one other tab for displaying **[What occurred](23-contingency-analysis-running-and-results.md#what-occurred)**. Selecting this will display a table with details of how actions were applied during the contingency.

The following describes some of the most common fields accessed with this display:

Category

The type of violation that occurred. If the violation is only due to the options set in [Advanced Limit Monitoring](#advanced-limit-monitoring), then the type will start with the word *Change.*

Valid categories include:

**Branch Amp** - branch violated due to current limit being exceeded

**Branch MVA** - branch violated due to MVA limit being exceeded

**Bus Low Volts** - bus violated due to low voltage limit being exceeded

**Bus High Volts** - bus violated due to high voltage limit being exceeded

**Bus dV/dQ** - bus violated due to dV/dQ sensitivity exceeding specified change threshold

**Bus Neg dV/dQ** - bus violated due to the dV/dQ sensitivity becoming negative

**Bus Disconnected**- bus violated due to becoming disconnected during the contingency

**Nomogram MW**- nomogram violated due to MW limit being exceeded

**Interface MW** - interface violated due to MW limit being exceeded

**Custom (would show name of custom monitor)** - value of specific object field being monitored. The name of the custom monitor will be shown in the Category field.

**Bus Pair Angle** - Added in Version 20 bus pair violated due to angle difference exceeding the angle limit

**Transient**- indicates that a transient model exceeded some pick-up limit. This will appear for *Monitor Only* models. The Element will indicate the associated model.

**Unsolved** -Added in Version 20 means that the entire contingency was not solved for this particular contingency

**Island Unsolved** - Added in Version 20An unsolved island was found during the solution. These are only created when using special [Island Monitoring options](#island-monitoring).

**Island Reserve Limits** - Added in Version 20An island was found that did not have enough makeup generation. These are only created when using special [Island Monitoring options](#island-monitoring).

**Island Solved** -Added in Version 20 A new island was created during the contingency. These are only created when using special [Island Monitoring options](#island-monitoring).

Element

A character string that describes the element that suffered the violation or the element that is being monitored with a Custom Monitor. For violations, this can either be a branch, a bus, or an interface. For Custom Monitors, this can be any object type that can be monitored with the custom monitors.

When the element is a branch, this string provides you with three pieces of information:

  - The branch that was violated
  - The terminal of the branch which had the highest loading
  - The direction of the flow on this branch

Example 1: Jamie (22) -\> Amy (33) CKT 1 at Amy (33)

This means that a branch connecting Jamie(22) to Amy (33) with circuit ID 1 is violated. The violation is at the Amy(33) terminal. The -\> indicates that the flow on this line is from Jamie toward Amy.

Example 2: Xena (55) \<- Harley (77) CKT 1 at Harley (77)

This means that a branch connecting Xena (55) to Harley (77) with circuit ID 1 is violated. The violation is at the Harley (77) terminal. The flow on this line is from Harley toward Xena.

For Custom Monitors, the string identifies the type of object that is being monitored, the identifier of the object that is being monitored, and the variablename of the specific field that is being monitored.

For Transient results, this identifies the model that exceeded the pick-up limit.

Value

Indicates the value of the violating quantity. For example, if the category of the violation is *Branch Amp* and the Value field is x, then the current on the violated element is x.

For Custom Monitors this is the value of the monitored field following the contingency.

For Transient results this is the monitored value that exceeds the pick-up limit.

Limit

Identifies the limit value that was violated. For example, if the category of the violation is *Branch Amp* and the Limit field is y, then the limit on the current that may flow through the element is y.

For Custom Monitors this will always be zero.

For Transient results this is the pick-up limit.

Percent

The Value for the element as a percentage of the Limit.

For some violations such as Bus dV/dQ, Bus Disconnected, Custom Monitors, Island Reserve Limits, Island Unsolved, Island Solved, and Unsolved this will always be blank. For bus change voltage violations, this will show the value relative to the reference state value.

Area Name Assoc.

Lists the areas with which the violated element is associated. If the element is a branch, Area Name identifies the area in which each of the branch’s terminal resides. If the element is a bus, Area Name identifies the area in which the bus resides. If the element is an area-to-area interface, Area Name will identify the areas that the interface ties; otherwise, it will read *N/A*.

For Custom Monitors, Island, and Unsolved violations this will always be blank.

Nom kV Assoc.

Identifies the maximum voltage level associated with the violated element. If the violated element is a branch, then Nom kV lists the nominal voltage of its higher-voltage terminal. If the violated element is a bus, then Nom kV simply identifies the bus’ nominal voltage. If the violated element is an interface that is made up strictly of branches, Nom kV lists the maximum nominal voltage of its terminals; otherwise, it will appear as *-9999.9*.

For Custom Monitors, Island, and Unsolved violations this will always be blank.

Island Results\\Count of Bus, Count of Superbus, Generator MW, Load MW

Added in Version 20For special island violation reported when using [Island Monitoring options](#island-monitoring) , these fields will populate to show information about the island created by the contingency.

Scaled Results

By default violations are reported based on the rating set selected with the limit monitoring settings. The violation percentage and limit are based on the selected rating set used during contingency analysis. Scaled results provide results for what the violation and percentage are for all available limits.

Scaled Results are found in their own folder in the list of available fields with the *LimitViol* object type, which is the type of object shown in the Violations display. The *Limit Scale* field is the limit that was used when the violation was recorded. This is used with the *Scaled Limit* and *Scaled Percent* fields to show what the limit would have been using any of these limits at their present values.

*Scaled Limit X= (Limit/Limit Scale)\*PresentDeviceLimitX*

*Scaled Percent X = (Percent\*Limit Scale)\*PresentDeviceLimitX*

Sensitivities\\Injection Sensitivities

This folder and subfolders contain fields to show all of the available sensitivity results for each violation along with the particular injector (generator or load) associated with the sensitivity or MW flow effect on the violation when calculating [Injection Sensitivities](#injection-sensitivities).

Sensitivity results can be reported by the following:

MW Effect Dec

This is the change in MW on the overloaded element by decreasing the injector by the total range by which it can be decreased: (MW Range Dec) \* (MW Inj Sensitivity).

MW Effect Inc

This is the change in MW on the overloaded element by increasing the injector by the total range by which it can be increased: (MW Range Inc) \* (MW Inj Sensitivity).

Sensitivity Max

This is the shift factor sensitivity of the injector if the sensitivity is in the group of maximum sensitivities.

Sensitivity Min

This is the shift factor sensitivity of the injector if the sensitivity is in the group of minimum sensitivities.

Local Menu Options

The following special options are available on the local menu of the Violations Display.

Create Contingent Interface For Selection

Selecting this option will create an interface that uses the currently selected violated element as the monitored element in an interface and the currently selected contingency as the contingent element within the interface. This option will only create an interface if the violated element is a branch. Contingent elements within the interface are only added for line outages or closures that are part of the selected contingency. Multiple contingent elements can be added to the interface.

Contingency Sensitivity Analysis

Selecting this option will open the [Contingency Sensitivity Analysis](23-contingency-analysis-running-and-results.md#contingency-sensitivity-analysis) tool for the selected violated element and contingency. This option will only be available for violations of branches.

Show Violation CTG Injection Sensitivities

Selecting this option will open a case information display showing the [Violation CTG Injection Sensitivities](23-contingency-analysis-running-and-results.md#violation-ctg-injection-sensitivities) for only the selected violation.
