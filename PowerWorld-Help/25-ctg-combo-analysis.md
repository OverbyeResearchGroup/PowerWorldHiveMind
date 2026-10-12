---
title: "CTG Combo Analysis"
part: "Contingency Analysis"
chapter_file: "25-ctg-combo-analysis.md"
topics: 3
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# CTG Combo Analysis

Contingency combination analysis and the combination element dialog.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (3)**

- [CTG Combo Analysis Overview](#ctg-combo-analysis-overview)
- [CTG Combo Contingency Analysis Dialog](#ctg-combo-contingency-analysis-dialog)
- [Contingency Combination Element Dialog](#contingency-combination-element-dialog)

---

<a id="ctg-combo-analysis-overview"></a>

## CTG Combo Analysis Overview

*Source: [`Content/MainDocumentation_HTML/CTG_Combo_contingency_analysis_an_introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CTG_Combo_contingency_analysis_an_introduction.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Contingency combination analysis is what industry planning and operating criteria often refer to the n-1-1 rule, which holds that a system must operate in a stable and secure manner following any single transmission or generation outage plus another contingency after the first set of n-1 contingency was applied. Previously, this analysis was already possible in Simulator, but required the upfront creation of a list containing all contingencies in a combinatorial fashion, which was memory intensive.

The new tool maintains an additional list of Primary Contingencies, and each N-1-1 contingency is internally managed by combining one primary contingency and one item from the normal contingency list. The normal contingency list will be referred to as the Secondary Contingency List during this analysis. This significantly reduces memory requirements.

![CTG Combo PrimaryList SecondaryList 896x384](images/CTG_Combo_PrimaryList_SecondaryList_896x384.jpg)

Improvements have also been made to the user interface for user friendly viewing, filtering, or saving results produced by Contingency Combination Analysis.

Contingency Combination Analysis is accessed and controlled through the [Contingency Combination Analysis dialog](#ctg-combo-contingency-analysis-dialog).

---

<a id="ctg-combo-contingency-analysis-dialog"></a>

## CTG Combo Contingency Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/contingency_combo_analysis_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/contingency_combo_analysis_dialog.htm)*

Simulator’s contingency combo analysis tools can be accessed only from [Run Mode](01-getting-started.md#run-mode-introduction). To access this dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **CTG Combo Analysis** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This will open the Contingency Combination Analysis dialog.

![CTG Combo Dialog 727x335](images/CTG_Combo_Dialog_727x335.jpg)

The top section of this dialog controls the combination analysis run. Click the **Run** button to start the analysis, and click the **Abort** button to stop analysis once it has been started. The **Primary Contingency** box will show the primary contingency that is currently being processed and any additional messages that are necessary during the analysis.. The **Contingency** box will show the secondary contingency that is currently being processed. Clicking **Close** will close the dialog.

The contingency combination analysis dialog contains the following tabs:

Primary Contingencies

The Primary Contingencies tab is used to manage the primary contingency list and to view basic information regarding each contingency definition.

Options

This tab contains subtabs with the following information:

Modeling

**Calculation Method**

The only method that is currently available is the **Full Power Flow** method. If the case is set to use the DC approximation in the power flow, combination analysis is not allowed and an appropriate error message will result.

**AC Method Options**

When the **Use specific solution options for contingencies** option is checked, Simulator will use the specified set of [Solution Options](10-power-flow-solution-and-options-part1.md#simulator-options) when solving the primary contingencies. To define the solution options used during the combination analysis, click the **Define Contingency Solution Options** button to open the Contingency Analysis Power Flow Solution Options dialog. See the [Contingency Analysis Power Flow Solution Options](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options) topic on more information about how these options are set and the various levels at which solution options can be set.

**Primary Contingency Reference**

**Use Primary CTG as Reference for Remedial and CTG Actions**

The system state following the solution of the primary contingency is used as the reference state for solving Remedial Actions for secondary contingencies. This affects the reference state that is used with Model Conditions, Model Filters, and Model Expressions and to evaluate Arming Criteria. This also affects contingency actions that allow Model Expressions and Model Fields to be evaluated in the reference state when determining the Amount of change for the action. This reference will also be used for the original value when solving secondary contingency actions that require a percent change.

**Use Primary CTG as Reference for Limit Monitoring**

The system state following the solution of the primary contingency is used as the reference state for determining violations that report changes between the contingency state compared to a base reference state when determining secondary contingency violations. These are generally the options that are specified with contingency [Advanced Limit Monitoring](22-contingency-analysis-options.md#advanced-limit-monitoring). When using Custom Monitors, this also determines the reference state that is used when applying the Pre Filter and the reporting of change violations.

Primary Contingency Definitions

This tab contains a case information display that lists all of the primary contingency elements for all primary contingencies.

Results By Combination

This tab contains a case information display of summary results for every primary and secondary contingency combination that was run. A case information display for all Violations or What Occurred for each combination can be viewed in the lower grid by clicking on a combination.

Results

This tab allows access to all Violations, What Occurred, and Injection Sensitivities for all combinations of primary and secondary contingency. Details about the built-in filtering can be found with the [Contingency Combination Analysis: Results Tab](52-additional-linked-topics-part1.md#contingency-combination-analysis-results-tab) topic.

---

<a id="contingency-combination-element-dialog"></a>

## Contingency Combination Element Dialog

*Source: [`Content/MainDocumentation_HTML/contingency_combo_element_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/contingency_combo_element_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Element Dialog provides information on the individual elements that comprise a contingency definition. You may use this dialog to modify an existing contingency’s definition or to add elements to new or existing contingencies.

This dialog is also used when defining [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions) and [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions). The options that appear will be different depending on what type of object is being defined with the dialog. Differences will be noted in the option descriptions.

There are several ways to open the Contingency Element Dialog:

  - By pressing the **Insert New Element** button on the [Contingency Primary Action Elements Dialog](52-additional-linked-topics-part1.md#contingency-definition-dialog).
  - By right-clicking on a Primary Contingencies table and choosing **Insert** or **Show Dialog**.

After making the desired changes, click **OK** to save changes and close the dialog or click **Cancel** to close the dialog without saving your changes.

Click **Delete** to remove the element from the contingency.

![Contingency Combo Element Dlg 772x610](images/Contingency_Combo_Element_Dlg_772x610.jpg)

Contingency Element Dialog

The Contingency Element Dialog has the following controls:

Element Type

Indicates the type of element involved in the contingency action. The Element Type will dictate what **Action Types** are available, and the selection of the Element Type, in conjunction with the **Action Type**, **Amount**, and **in** options settings, determines what actually happens during the contingency.

What actually happens during a contingency action based on the **Element Type**, **Action Type**, and **in** options is described in detail in the topics referenced below:

[Branch](24-contingency-element-dialog.md#type-branch)

[Generator](24-contingency-element-dialog.md#type-generator)

[Load](24-contingency-element-dialog.md#type-load)

[Switched Shunt](24-contingency-element-dialog.md#type-switched-shunt)

[Bus](24-contingency-element-dialog.md#type-bus)

[Interface](24-contingency-element-dialog.md#type-interface)

[Injection Group](24-contingency-element-dialog.md#type-injection-group)

[Multi-Section Line](24-contingency-element-dialog.md#type-multi-section-line)

[Series Capacitor](24-contingency-element-dialog.md#type-series-capacitor)

[Phase Shifter](24-contingency-element-dialog.md#type-phase-shifter)

[3-Winding Transformer](24-contingency-element-dialog.md#type-3-winding-transformer)

[Line Shunt](24-contingency-element-dialog.md#type-line-shunt)

[DC Line](24-contingency-element-dialog.md#type-dc-line)

[VSC DC Line](24-contingency-element-dialog.md#type-vsc-dc-line) (Added in version 20, build on January 11, 2018)

[DC Converter](24-contingency-element-dialog.md#type-dc-converter)

[Area](24-contingency-element-dialog.md#type-area)

[Substation](24-contingency-element-dialog.md#type-substation)

Choose the Element

Use this portion of the dialog to choose the element involved in this action. This behaves the same as the [Advanced Find Dialogs](04-model-explorer-and-case-information-part3.md#find-dialog-basics) used throughout the software.

Action Type

Defines the change specified by the contingency action. The Action Types available depend on the **Element Type** selected. Possible Action Types include: Open, Open Breakers, Close, Close Breakers, Move, Set To, Change By, Bypass, and Inservice. The behavior of each of these actions for the different elements is described with **Element Type**.

Amount

Enterable fields used to specify the quantity of change desired for the contingency element. The Amount fields are enabled when the appropriate **Action Type** is set depending on the **Element Type** selected. The top field is used to define a *Constant*, *Field*, or [Model Expression](04-model-explorer-and-case-information-part2.md#model-expressions) depending on the entry selected in the bottom drop-down box. Use the **Find** button to display a dialog listing *Fields* or *Model Expressions*. This dialog behaves the same as the [Advanced Find Dialogs](04-model-explorer-and-case-information-part3.md#find-dialog-basics) used throughout Simulator.

The Amount of change that occurs is based on the value of the top field entry. The top entry field is a constant, field name, or model expression name. When this entry is a field name, the value of the change is based on the value of the selected element field when the contingency occurs. When this entry is a model expression, the value of the change is based on the value of the selected model expression when the contingency occurs. If the **Evaluate in Reference State** box is checked when specifying a *Field* or *Model Expression*, the value is based on the value of the respective entry in the contingency reference state (base case).

The Amount of change that occurs for the selected element is based on the value entered in the top field and the parameter set with the **in** options. The availability of the **in** options will change based on the Element Type selected and the Action Type selected. The availability of these options is described in detail with **Element Type.**

Make-up Power Sources

Power injection contingency actions result in power imbalances - typically picked up by the system slack - that may result in Power Flow Convergence Problems. Simulator provides the option of specifying Make-up Power Sources for generation, load, injection group, and switched shunt contingencies to both offset the resulting real power imbalance and provide a more realistic simulation. See [Make-up Power Sources](52-additional-linked-topics-part1.md#make-up-power-sources) for more information.

Status

This field determines how an action is applied. See the [Contingency Element Status](24-contingency-element-dialog.md#contingency-element-status) topic for more details.

Comment

An optional user-specified comment string associated with the action. For example, for an action with Model Criteria specified, you could add a sentence explaining why the action is only performed under the specified criteria. While this comment is not used by Simulator in any way, it is saved with the contingency element when saving contingency records in contingency auxiliary data files or with the case PWB file.

Open Breakers for Contingencies

When using the *Open Breakers* contingency action, Simulator will automatically search the topology of the system to determine which breakers must be opened to isolate this device. For more information on this functionality see the topic [Contingency Element: Open Breakers](24-contingency-element-dialog.md#contingency-element-open-breakers).

Close Breakers for Contingencies

When using the *Close Breakers* contingency action, breakers are identified individually for each element that is using this action and the element is not already energized. A list of breakers to be closed is created for each affected element regardless of whether closing the breakers will actually energize the element. The lists of breakers for each individual element are merged into a set of unique breakers. New temporary contingency actions are created for these breakers so that when the contingency action is actually implemented, the selected breakers are closed instead of the element itself changing status. Once the contingency has been implemented and solved, the temporary contingency actions are removed so that the user never sees the actions created for the breakers. During the actual contingency solution, the *[What Occurred](23-contingency-analysis-running-and-results.md#what-occurred)* list will be updated and can be examined in the results to determine what breakers were needed to energize the device, even though the actions created for the breakers are removed after the contingency has been examined.

The **Close Breakers** contingency action is only available for contingency records and [remedial actions](21-contingency-analysis-overview-and-records.md#remedial-actions) and is not available for [contingency block definitions](21-contingency-analysis-overview-and-records.md#contingency-blocks) or for [global contingency actions](21-contingency-analysis-overview-and-records.md#global-actions). Only branches of **Branch Device Type** of *Breaker* are used with contingency actions, and *Disconnects* are not used.

More information about how breakers are selected can be found in the [Close Breakers Overview](24-contingency-element-dialog.md#contingency-element-close-breakers) topic.
