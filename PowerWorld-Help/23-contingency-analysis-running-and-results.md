---
title: "Contingency Analysis — Running and Results"
part: "Contingency Analysis"
chapter_file: "23-contingency-analysis-running-and-results.md"
topics: 19
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Contingency Analysis — Running and Results

Running contingency analysis, file formats, sensitivity analysis, results and comparing runs.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (19)**

- [Contingency Analysis Dialog](#contingency-analysis-dialog)
- [Save to Auxiliary File from Contingency Analysis](#save-to-auxiliary-file-from-contingency-analysis)
- [Contingency Definitions and RAS Definitions AUX File PDF](#contingency-definitions-and-ras-definitions-aux-file-pdf)
- [PSLF Contingency Format](#pslf-contingency-format)
- [Running the Contingency Analysis](#running-the-contingency-analysis)
- [Treatment of Time Delay of Contingency Elements and Model Filter Condition Time Delays](#treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays)
- [Iterated Linear Analysis](#iterated-linear-analysis)
- [Other Contingency Actions](#other-contingency-actions)
- [Contingency Sensitivity Analysis](#contingency-sensitivity-analysis)
- [Results Tab](#results-tab)
- [View Results by Element](#view-results-by-element)
- [Contingencies Section](#contingencies-section)
- [What Occurred](#what-occurred)
- [Violation CTG Notes](#violation-ctg-notes)
- [Violation CTG Injection Sensitivities](#violation-ctg-injection-sensitivities)
- [Report Writing](#report-writing)
- [Summary Tab](#summary-tab)
- [Comparing Two Contingency Analysis Results](#comparing-two-contingency-analysis-results)
- [Comparing Contingencies List Displays](#comparing-contingencies-list-displays)

---

<a id="contingency-analysis-dialog"></a>

## Contingency Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/contingency_analysis_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/contingency_analysis_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator’s contingency analysis tools can be accessed only from [Run Mode](01-getting-started.md#run-mode-introduction). To access this dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Contingency Analysis** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This will open the Contingency Analysis dialog.

Each tab of the contingency analysis dialog covers a particular aspect of the analysis.

The [Contingencies tab](22-contingency-analysis-options.md#contingencies-tab) is used primarily to manage the contingency list and to learn basic information regarding each contingency and the violations that it causes.

The [Options tab](22-contingency-analysis-options.md#options-tab) contains a panel on the left which provides access to all the options for contingency analysis. The tab enables you to dictate various parameters for the analysis that govern such things as how violations are flagged in both the Base Case and for contingency conditions and what information should be included in the contingency report. It also provides access to more complex contingency definitions and as well as Distributed Computing options.

The [Results tab](#results-tab) contains a panel on the left which provides access to look through the results of the contingency analysis. It includes the ability to [View Result by Element](#view-results-by-element) as well as by contingency. Other convenient summaries of contingency analysis results are also available as well as the ability to write results to a Text File.

The **Load** button will allow the opening of any of the file formats defined in the [Loading Contingencies from a File](21-contingency-analysis-overview-and-records.md#loading-a-contingency-list-from-a-file) topic.

The **Save** button will allow the saving of contingency definitions and supporting information. The file formats that are allowed are:

  - [Simulator Auxiliary File Format (\*.aux)](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - Simulator Version 5-7 Contingency File Format (\*.ctg) (see the old users manual, or [contact](52-additional-linked-topics-part1.md#contact-information) PowerWorld Corporation)
  - [PTI PSS/E-formatted Contingency Files (\*.con)](21-contingency-analysis-overview-and-records.md#psse-contingency-format)
  - [WECC Contingency and RAS File (\*.aux)](21-contingency-analysis-overview-and-records.md#concise-contingency-and-remedial-action-scheme-format)

The **Auto Insert** button will open the [Auto Insertion of Contingency Records](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) dialog.

The **Other \>** button will open a menu containing various [contingency related options](#other-contingency-actions).

The **Start Run** button will start the contingency analysis. Additional buttons will appear after the run has started including: **Pause Run**, **Abort** and **Continue**. For more description of how to perform a contingency analysis simulation and what these buttons do see [Running the Contingency Analysis](#running-the-contingency-analysis).

Added in version 19, build on July 6, 2016

When the contingency analysis dialog is open and choosing to [save a case](03-cases-files-and-formats.md#saving-cases), checks are done to ensure that the user does not accidentally save a post-contingency system state. If the contingency reference state exists and at least one system device status in the present system is different than the status in the contingency reference state, a dialog will appear prompting the user if they want to store the present system state to file.

---

<a id="save-to-auxiliary-file-from-contingency-analysis"></a>

## Save to Auxiliary File from Contingency Analysis

*Source: [`Content/MainDocumentation_HTML/Contingency_Analysis_Save_Aux.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Analysis_Save_Aux.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There is a huge amount of potential data related to contingency analysis that you may want to save when saving contingency definitions. As a result when choosing to do this on the [contingency analysis dialog](#contingency-analysis-dialog), a very large dialog appears as shown below. The options on the left portion of this dialog determine what information is stored to the auxiliary file. The options on the right side of the dialog specify formatting options.

![Contingency Analysis SaveAUXDialog](images/Contingency_Analysis_SaveAUXDialog.png)

Set What to Store and Formatting options to match the WECC RAS and Contingency Format

Click this box to change all the options in this dialog to match what must be done to replicate the options that are stored to the [Concise Format used for the WECC RAS and Contingency Format](21-contingency-analysis-overview-and-records.md#concise-contingency-and-remedial-action-scheme-format).

Web Help on RAS and Contingency AUX Format

Click this box to open the PDF document that describes the format used for the [WECC RAS and contingency format](https://www.powerworld.com/WebHelp/files/PowerWorld_RASFileFormat.pdf).

Save Data Maintainers with Filter = YES

By checking this box only those objects that are part of the DataMaintainers object that have their field Filter = YES will be saved. We will denote below which objects this effects under the What to Store section. (Prior to Version 20, build on October 17, 2017, the Selected field was used instead)

Use Area/Zone Filters for Contingency Options and Limit Monitoring Settings related to Area, Bus, Gen, Shunt objects

Added in Version 20

Check this box to save objects according to the Area/Zone filter settings. This affects the following options: Area Make Up Power, Gen Max MW Response, Gen Post CTG AGC Response, Gen Line Drop Comp, Bus Load Throwover, Switched Shunt Post CTG, and Limit Monitoring Settings for Area, Zone, Bus, Branch, and Interface objects.

Force saving of objects used by other objects selected in What to Store

Added in Version 19, build on April 12, 2017

Check this box to save dependencies of the objects selected with the **What to Store** options. Dependencies are objects that are required to completely define another object. The hierarchy of objects will be saved with the top of the hierarchy defined by the **What to Store** objects.

As an example of how this works, assume that you would like to save all Remedial Actions and any objects required to define these. To accomplish this the **Save Remedial and Global Actions** box should be checked and the **Force saving of objects used...** box should also be checked. No additional boxes need to be checked in the **What to Store** section. Remedial Actions are dependent on Remedial Action Elements to be completely defined. Because dependencies are being saved, all required Remedial Action Elements will be saved. Remedial Action Elements have Model Criteria that define when the action is taken. Remedial Action Elements are dependent on the Model Condition or Model Filter that specifies the Model Criteria. Model Conditions and Model Filters that are used by Remedial Action Elements that are being saved will also be saved. Model Conditions and Model Filters have their own dependencies that will also be saved. When using the option to save objects used by other objects, Simulator will search through the hierarchy completely and save only those objects that are being used. This search starts from the objects selected in What to Store and searches the hierarchy for each of these objects looking for dependencies. This makes it easier on the user to ensure that everything is being saved and also allows saving only those objects that are being used instead of saving all objects of a particular type. You will not necessarily want to save all Model Conditions or Model Filters, but rather you would only want to save those associated with Remedial Actions.

When using the option to **Save Data Maintainers with Filter = YES** the data maintainer condition will only be enforced for the objects specified in **What to Store** and dependencies will not have this enforced.

Formatting Options

Save Data Using

Specify whether to identify the objects written to the Auxiliary file using primary keys (Bus Numbers), secondary keys (bus Name\_NomkV), or [Labels](07-object-properties-run-mode-and-general-part2.md#labels). This also impacts the strings that will appear when using the special ObjectID fields. When modifying this value it will temporarily change the Key Fields options described in the [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) help topic.

Replace SUBDATA with DATA (recommended)

It is highly recommended that this option be chosen as this represents a better way to export files. Simulator has supported reading files in this manner since . The ability to read and write objects in this manner has been available since Version 13.

Some objects can be written in a SUBDATA section of a containing object or in their own separate DATA section in an auxiliary file. An example of this are the PartPoint objects that are contained inside of each InjectionGroup. Generally, we recommend that you check this box as the SUBDATA sections are being replaced in Simulator over time (we will continue to read old files of course).

Use Concise Variable Names and AUX Headers

Added in Version 19

Check this box to change the auxiliary file output to use the concise variable names as described in the [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names) help topic and the concise AUX headers described in the [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) help topic.

Use Object ID fields

Added in Version 18

Check this box to replace the various key fields used to write out Area, Zone, Bus, Branch, Gen, Shunt, and Interface objects to the Auxiliary file with the standard [ObjectID field](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels) that automatically obeys the Save Data Using option (see [ObjectID Field for use in Auxiliary Files](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels)). We recommend that this be done as it simplifies the structure of the AUX file output. Version 18 and later will read files that use this field.

Use Special Object IDs for MS Line Section and 3 winding Transformer windings

Added in Version 19

These are special options for writing out multi-section line sections and individual windings of three-winding transformers using the ObjectID field. See [ObjectID Field for use in Auxiliary Files](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels) details on this feature.

What to Store

Depending on the choices made on this dialog, the following table describes what gets saved to the AUX file. The order the objects are listed in this table is the order that objects are written to file. This order is important because objects such as Injection Groups and Interfaces may be referred to by subsequent objects such as a ContingencyElement.

<table>
<tbody>
<tr class="odd">
<td><p><strong>Check Box Option</strong></p></td>
<td><p><strong>Entire Objects or Fields that will be stored</strong></p></td>
<td><p><strong>Treatment for Only Selected DataMaintainer</strong></p></td>
</tr>
<tr class="even">
<td><p>Save Calculated Fields and Custom Expressions Used by Other Objects</p></td>
<td><p>These objects will ONLY be saved if they are being used by an objects selected in What to Store or dependencies of these objects:</p>
<p>BGCalculatedField objects</p>
<p>CustomExpression objects</p></td>
<td><p>Always Saved</p></td>
</tr>
<tr class="odd">
<td><p>Save Injection Group Definitions</p></td>
<td><p>InjectionGroup objects</p>
<p>PartPoint objects (may be in SUBDATA of InjectionGroup)</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Interface Definitions</p></td>
<td><p>Interface objects</p>
<p>InterfaceElement objects (may be in SUBDATA of Interface)</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="odd">
<td><p>Save Limit Monitoring Settings</p></td>
<td><p>LimitSet Objects, (LimitSet cost functions as SUBDATA always)</p>
<p>Limit_Monitoring_Option field (LMS_IgnoreRadial)</p>
<p>Area fields (MonitorLimits, MonitorMinkV, MonitorMaxkV)</p>
<p>Zone fields (MonitorLimits, MonitorMinkV, MonitorMaxkV)</p>
<p>Bus fields (Monitor, LimitSet)</p>
<p>Branch fields (Monitor, LimitSet)</p>
<p>Interface fields (Monitor, LimitSet)</p>
<p><em>The fields used as key field identifiers in the auxiliary file for these objects will depend on the</em> <strong>Save Data Using</strong> <em>option and the</em> <strong>Use Object ID Fields</strong> <em>option.</em></p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Contingency Options</p></td>
<td><p>CTG_Options objects</p>
<p>CTG_Options_Value objects</p></td>
<td><p>Not Saved</p></td>
</tr>
<tr class="odd">
<td><p>Save Distributed Computing Settings</p></td>
<td><p>Distributed_Options object</p>
<p>DistributedComputer object</p></td>
<td><p>Not Saved</p></td>
</tr>
<tr class="even">
<td><p>Save General Power Flow Solution Solution Options</p></td>
<td><p>Sim_Solution_Options objects</p>
<p>Sim_Solution_Options_Value objects</p>
<p>PostPowerFlowActions</p>
<p>PostPowerFlowActionsElement (may be in SUBDATA of PostPowerFlowActions)</p></td>
<td><p>Not Saved</p></td>
</tr>
<tr class="odd">
<td><p>Save Contingency Options</p>
<p>(repeated check on this option)</p></td>
<td><p>*Area fields (CTGMakeupGen)</p>
<p>If (not <strong>Suppress Gen and Bus Contingency Options</strong>) then also the following</p>
<p>*Gen fields (CTGMaxResp, CTGPreventAGC, CTGPartFact, UseLineDrop, Xcomp, Rcomp)</p>
<p>*Bus fields (CTGLoadThrow)</p>
<p>*Switched Shunt fields (CTGShuntMode ,CTGRegUse, CTGRegHigh, CTGRegLow, CTGMvarUse, CTGMvarNomMax, CTGMvarNomMin)</p>
<p><em>The fields used as key field identifiers in the auxiliary file for these objects will depend on the</em> <strong>Save Data Using</strong> <em>option and the</em> <strong>Use Object ID Fields</strong> <em>option.</em></p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Voltage Control Groups</p></td>
<td><p>VoltageControlGroup objects</p>
<p>Switched Shunt fields (VoltageControlGroup) <em>Always written using ObjectID field</em></p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="odd">
<td><p>Save Advanced Filters Used by Other Objects</p></td>
<td><p>Filter (<em>Only for those filters that are used by the objects lists</em>)</p>
<p>Condition (may be in SUBDATA of Filter)</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Model Filters, Model Conditions, Model Expressions, and Model Result Overrides</p></td>
<td><p>ModelExpression objects (LookupTable SUBDATA always)</p>
<p>ModelCondition objects</p>
<p>ModelConditionCondition objects (may be in SUBDATA of ModelCondition)</p>
<p>ModelFilter objects</p>
<p>ModelFilterCondition objects (may be in SUBDATA of ModelFilter)</p>
<p>ModelResultOverride objects</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="odd">
<td><p>Save Custom Monitors</p></td>
<td><p>CustomMonitor objects</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Contingency Definitions or Save Remedial Action Definitions</p></td>
<td><p>CTGElementBlock objects</p>
<p>CTGElementBlockElement objects (may be in SUBDATA of CTGElementBlock)</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="odd">
<td><p>Save Remedial Action Definitions</p></td>
<td><p>RemedialAction objects</p>
<p>RemedialActionElement objects (may be in SUBDATA of RemedialAction)</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="even">
<td><p>Save Contingency Definitions</p></td>
<td><p>Contingency objects</p>
<p>ContingencyElement objects (may be in SUBDATA of Contingency)</p>
<p>ContingencyMonitoringException objects (may be in SUBDATA of Contingency)</p>
<p>If <strong>Save Contingency Results</strong> then also the following</p>
<p>additional fields with Contingency objects</p>
<p>ViolationCTG objects (may also be SUBDATA of Contingency objects)</p>
<p>WhatOccurredDuringContingency objects</p></td>
<td><p>Checks Data Maintainers</p></td>
</tr>
<tr class="odd">
<td><p>Save List Display Settings</p></td>
<td><p>This will store several DataGrid objects associated with the case information displays that are on the Contingency Analysis dialog. These effect the default columns shown on this case information displays.</p></td>
<td><p>Not Saved</p></td>
</tr>
</tbody>
</table>

Merge Contingency Blocks and Global Actions

Generally options below determine which objects and fields are stored to the AUX file. There is a special option called Merge Contingency Blocks and Global Actions which we general recommend starting in Version 19 of Simulator. Checking this option will do the following.

  - Take all contingency blocks and merge them into the individual Contingency, and RemedialAction objects that use them
  - Merge the Global Contingency Actions and into a new RemedialAction object

It is more appropriate to manage only the Contingency and RemedialAction objects.

---

<a id="contingency-definitions-and-ras-definitions-aux-file-pdf"></a>

## Contingency Definitions and RAS Definitions AUX File PDF

*Source: [`Content/Other_Documents/PowerWorld_RASFileFormat.pdf`](https://www.powerworld.com/WebHelp/Content/Other_Documents/PowerWorld_RASFileFormat.pdf)*

This topic is a PDF supplied with the PowerWorld help system rather than an HTML page.

- Local copy: [`pdf/PowerWorld_RASFileFormat.pdf`](pdf/PowerWorld_RASFileFormat.pdf)
- Online: <https://www.powerworld.com/WebHelp/Content/Other_Documents/PowerWorld_RASFileFormat.pdf>


---

<a id="pslf-contingency-format"></a>

## PSLF Contingency Format

*Source: [`Content/MainDocumentation_HTML/PSLF_Contingency Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PSLF_Contingency Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can [read](21-contingency-analysis-overview-and-records.md#loading-a-contingency-list-from-a-file) the contingency format used by PSLF. The current version of Simulator supports most of this format. If you need Simulator to support more parts of this format, contact PowerWorld Corporation to express your need. Otherwise, we recommend you make use of Simulator’s [tool to auto-insert contingencies](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list).

---

<a id="running-the-contingency-analysis"></a>

## Running the Contingency Analysis

*Source: [`Content/MainDocumentation_HTML/Running_the_Contingency_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Running_the_Contingency_Analysis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To run the contingency analysis means to model and solve one or more contingencies from the case’s current contingency list. Simulator’s [Contingency Analysis Dialog](#contingency-analysis-dialog) gives you several options for running the contingency analysis. You may:

  - Run every contingency in the contingency list (except, of course, for those you have designated to skip using the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab)).
  - Run a selected contingency to identify its limit violations and then leave the system in this post-contingency state. (Realize that prior to solving another contingency, Simulator will reset the system state to the reference state. For more information see [Contingency Case References](21-contingency-analysis-overview-and-records.md#contingency-case-references)).
  - Run a selected contingency to identify its limit violations and keep the resulting case as the new reference point for further contingency analysis runs.

To run the complete contingency list, do any one of the following:

  - Right-click on the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab) to bring up its [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) and select **Run Contingency Analysis**.
  - Click the **Start Run** button at the bottom of the [Contingency Analysis Dialog](#contingency-analysis-dialog).

To pause the contingency run once it has started, click either **Pause Run** at the bottom of the [Contingency Analysis Dialog](#contingency-analysis-dialog). To resume a paused contingency run, click the **Continue** button[ ](#summary-tab). Finally, to terminate a contingency run, click the **Abort** button next to the **Pause**/ **Continue** button. The status indicator will inform you of the run’s current state.

To solve a single contingency, identify its violations, and then leave the system in this post-contingency, select the contingency you wish to model in the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab), right-click to invoke the display’s [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), and select **Contingency records \> Solve Selected Contingency**. (Realize that prior to solving another contingency, Simulator will reset the system state to the reference state).

To solve a single contingency and set it as the reference (starting) case for further contingency analysis activity, select the contingency you wish to model in the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab), right-click to invoke the display’s [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), and select **Contingency records \> Solve and Set As Reference**. Simulator will model the selected contingency, flag its violations, and leave the resulting case in memory so your future work will affect the post-contingency system rather than the original pre-contingency state. See [Contingency Case References](21-contingency-analysis-overview-and-records.md#contingency-case-references) for more information.

When selecting the **Solve and Set as Reference** option, a warning dialog will appear that allows you to verify if this is the action that you really want to take. Selecting **Yes** will continue with this action. Selecting **No** will abandon this operation. Selecting **Yes to All** will specify that you no longer want to see this dialog and the next time you call this action it will occur with no prompt and the action will occur. The **Yes to All** option will remain in effect until the contingency analysis dialog is closed. Once the dialog is re-opened again and this option is selected, the warning dialog will appear again.

The **Refresh Displays After Each Contingency** checkbox is used to force a refresh of the counters after each contingency, which may slow down processing of the contingency set (accordingly, this box is unchecked by default to maximize solution speed).

How Each Contingency is Implemented

Each contingency is processed in the same manner. All of the actions that are defined with the [contingency itself](22-contingency-analysis-options.md#contingency-definition-dialog) are combined with the actions of all [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions) that are not set to be skipped and all [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) if using the global action list. Regardless of the origin of the action, the actions are processed in an order and manner based on their action Status and other settings as described below.

Added in Version 20

At the beginning of the process while the system state is still in the contingency reference state (base case state), any Arming Criteria specified with a Remedial Action or Remedial Action Element where the Arming Status is CHECK is evaluated to determine if the Remedial Actions or Remedial Action Elements are armed. Only Remedial Action Elements that are armed can have their actions implemented during the processing described below. Remedial Actions and Remedial Action Elements can also be armed if their Arming Status is ALWAYS or their Arming Criteria is not specified. In order or a Remedial Action Element to be applied during the solution process, it must be armed and the Remedial Action to which is belongs must also be armed.

Persistent option was added in Version 19

Normally after any contingency element, Remedial Action Element, etc. is applied during this solution process, it will not be applied again. The exception to this is actions that are marked as Persistent = YES.

Contingency Processing Order Based on Status and Calculation Method

The following describes the order in which the different [action statuses](24-contingency-element-dialog.md#contingency-element-status) are evaluated and when the actions are applied. This process is only applicable when the [Calculation Method](22-contingency-analysis-options.md#basics) is set to *Full Power Flow* and solving the ac power flow or when using [Iterated Linear Analysis](#iterated-linear-analysis). Differences in the process when using these two methods are noted.

1.  Various post-contingency settings for Generator and Switched Shunt controls may be changed for the contingency solution as described in [Generator Post-Contingency AGC](22-contingency-analysis-options.md#generator-post-contingency-agc), [Generator Maximum MW Response](22-contingency-analysis-options.md#generator-maximum-mw-response), [Generator Line Drop and RCC](22-contingency-analysis-options.md#contingency-generator-line-drop-and-reactive-current-compensation), and [Contingency Options: Switched Shunt Response](22-contingency-analysis-options.md#switched-shunt-post-ctg). For any [InjectionGroup with a CTGOutageIntertie defined](22-contingency-analysis-options.md#injectiongroup) \[Added in Version 24\], if there are any online generator, load, or shunt objects in the initial case then we flag that InjectionGroup for use in Step 5 below.
2.  Apply ALWAYS, unconditional actions (actions with no Model Criteria except for SOLUTIONFAIL actions), and true CHECK actions
3.  Update topology (branch and bus status and derived status)
4.  Apply true TOPOLOGYCHECK actions
      - TOPOLOGYCHECK actions wssith the smallest Time Delay will be applied
5.  \[Added in Version 24\]For any InjectionGroups flagged in Step 1, if all generator, load, and shunt objects in the InjectionGroup are not opened, then also open the [branch or interface specified as the CTGOutageIntertie](22-contingency-analysis-options.md#injectiongroup).
6.  Store reference state for use if solution failure occurs and SOLUTIONFAIL actions existc
7.  Solve power flow (For full ac analysis, the power flow is actually solved here. For iterated linear analysis, the linear estimates of branch flows are determined for branches that are being monitored in a linear contingency state.)
      - SOLUTIONFAIL actions were Added in Version 19
      - If the power flow solution fails and any SOLUTIONFAIL actions are available, the reference state in step 6 is restored and any true SOLUTIONFAIL actions with the smallest Time Delay are then applied
    <!-- end list -->
      - If any SOLUTIONFAIL actions are applied, the process will go back to step 6 and repeat (This loop will abort after 100 solution failures)
      - If there is still a solution failure, abort the contingency process and report failure
8.  Apply true POSTCHECK actions and true TOPOLOGYCHECK actions
      - [TRANSIENT](22-contingency-analysis-options.md#transient-models) actions will also be evaluated
      - [CUSTOMMONITORs](22-contingency-analysis-options.md#custom-monitors) with Trip action will be evaluated Added in version 19, build on December 23, 2016
      - TRANSIENT, CUSTOMMONITOR, POSTCHECK, or TOPOLOGYCHECK actions with the smallest Time Delay will be applied
      - TRANSIENT models and CUSTOMMONITORs are only included when doing full ac analysis
9.  Repeat steps 3-8 until no more POSTCHECK, TOPOLOGYCHECK, CUSTOMMONITOR, or TRANSIENT actions are done (This loop will abort after 100 iterations)

Contingency Processing Order Based on Action

Within a given processing step as described above in the **Contingency Processing Order Based on Status and Calculation Method** section multiple actions can be applied. When more than one action is applied at the same time, the **Element Type** and **Action Type** of the contingency element determine the order in which they applied. The following list gives details of this order:

1.  **Element Type** = Abort
2.  **Element Type** = Branch, Bus, Interface, Series Capacitor, 3-Winding Transformer, or DC Line and **Action Type** = Close
3.  **Element Type** = Generator, Load, Switched Shunt, Injection Group, Line Shunt, or DC Converter and **Action Type** = Close
4.  **Element Type** = Branch, Generator, Load, Switched Shunt, Interface, Injection Group, Series Capacitor, Phase Shifter, DC Line, DC Converter, Substation, or Script and **Action Type** = Move, Set To, or Change By
5.  **Element Type** = Generator, Load, Switched Shunt, Injection Group, Line Shunt, DC Converter, or Substation and **Action Type** = Open
6.  **Element Type** = Branch, Bus, Interface, Series Capacitor, 3-Winding Transformer, or DC Line and **Action Type** = Open
7.  **Element Type** = Area and **Action Type** = Set To

---

<a id="treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays"></a>

## Treatment of Time Delay of Contingency Elements and Model Filter Condition Time Delays

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_TimeDelay_Treatment.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_TimeDelay_Treatment.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 19

A Time Delay must be calculated for any [ModelFilter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) that has ModelFilterConditions that use TimeDelays. The calculated time delay of a ModelFilter depends on the logic of the gate (OR, AND, NOR, NAND, XOR, OneTRUE) and the various TimeDelays in the logic diagram. The calculation occurs as follows.

Each input ModelFilterCondition will determine its own calculated time delay based on whether the Criteria object is a [ModelFilter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) or a [ModelCondtion](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog). We will call that the InputTimeDelay.

|                 |                                                                                                                               |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Criteria Object | *InputTimeDelay* for the ModelFilterCondition                                                                                 |
| ModelFilter     | Use the summation of the Calculated Time Delay of the ModelFilter and the TimeDelay associated with this ModelFilterCondition |
| ModelCondition  | Directly use TimeDelay associated with this ModelFilterCondition                                                              |

With these InputTimeDelays, the ModelFilter’s calculated time delay is then determined based on the Logic of the ModelFilter.

|            |                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------- |
| Gate Logic | Calculated Time Delay                                                                     |
| AND        | The maximum *InputTimeDelay* associated with any of the TRUE ModelFilterCondition inputs  |
| OR         | The minimum *InputTimeDelay* associated with any of the TRUE ModelFilterCondition inputs  |
| NAND       | The minimum *InputTimeDelay* associated with any of the FALSE ModelFilterCondition inputs |
| NOR        | The maximum *InputTimeDelay* associated with any of the FALSE ModelFilterCondition inputs |
| XOR        | The minimum *InputTimeDelay* associated with any of the TRUE ModelFilterCondition inputs. |
| OneTRUE    | The *InputTimeDelay* associated with the TRUE ModelFilterCondition                        |

Note that the calculated time delay for XOR gates has some ambiguity in what should be returned. We specify that the time delay is that associated with the minimum InputTimeDelay associated with any of the TRUE inputs.

To illustrate the calculation of the time delays, consider the following example logic diagram. The yellow filled boxes represent ModelCondition objects. The orange filled logic gates represent ModelFilter objects. The Blue boxes represent ModelFilterCondition objects. Also note that some of the ModelFilterCondition objects have NOT logic associated with them.

![ModelFilter CalculatedTimeDelay](images/ModelFilter_CalculatedTimeDelay.png)

---

<a id="iterated-linear-analysis"></a>

## Iterated Linear Analysis

*Source: [`Content/MainDocumentation_HTML/Contingency_Iterated_Linear_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Iterated_Linear_Analysis.htm)*

Linear analysis of the impact of contingencies is done by calculating sensitivities (LODFs and power injection sensitivities) based on a solved power flow Jacobian. No contingency actions are actually implemented and the system state does not change. This poses a limitation to accurately modeling the impact of conditional actions within a contingency when all conditions are evaluated in the contingency reference state instead of being evaluated following the implementation of other actions. To model conditional actions more accurately, an iterative approach to the linear analysis can be taken. Instead of doing a single calculation with all conditions modeled in the contingency reference state where TOPOLOGYCHECK and POSTCHECK actions are treated as CHECK actions, [contingencies are processed](#running-the-contingency-analysis) in the order of a full ac solution, but instead of solving the power flow the linear impact of all actions that can be implemented is determined. This process will most likely be slower than the non-iterative linear calculation, but will yield the benefits of a more accurate solution when that is required from the linear calculations, such as with ATC calculations.

Using the Iterated Linear Analysis Method

To use the iterated linear analysis method, the contingency [Calculation Method](22-contingency-analysis-options.md#basics) must be set to one of the *Linearized* options and the [Iterate on Action Status](22-contingency-analysis-options.md#dc-and-screening-options) option must be selected. The [power flow solution options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options) must also be set for ac power flow.

Determining if Iterated Process is Needed

Even though the appropriate settings are selected to use the iterated linear analysis method, it might not be necessary to use it. To save on calculation time, Simulator will only use the process when necessary. At the beginning of each contingency process that is set to use the iterated linear process, a pre-processing is done to determine if it is necessary. It will only be necessary if a field needs to be evaluated in some contingency state other than the reference state and it is a handled field. The **Which Fields are Handled** section describes how you can determine these. It will be necessary if any of the following are found:

  - TOPOLOGYCHECK action using a Model Criteria (Model Condition, Model Filter, and Model Expression are checked) with a handled field
  - POSTCHECK action using a Model Criteria (Model Condition, Model Filter, and Model Expression are checked) with a handled field
  - [Contingency action](24-contingency-element-dialog.md#contingency-element-dialog) specifying the **Amount** of change by either a Model Field or Model Expression and the **Evaluate in Reference State** option is set to *NO*

Which Fields are Handled

Because linear contingency analysis does not actually change the system state, only fields that are specifically defined to be evaluated during a linear contingency state will be handled correctly. All other fields will ALWAYS be evaluated in the contingency reference state. Determining which fields should be handled will be a learning process of checking conditional actions and adding fields as necessary. We will require user input on doing this.

A tool has been added to provide a summary of fields that are handled and which ones are in use by conditional checks or contingency actions that are not handled. The local menu of the [Contingencies table](22-contingency-analysis-options.md#contingencies-tab) contains the **Verify Contingencies for Iterated Linear Analysis** tool that will process the current list of contingencies, Remedial Actions, and Global Actions to determine which fields are and are not handled. A user-specified text file will store the results.

The file will look something like the following. If you have any fields in the NOT handled section, please [contact](52-additional-linked-topics-part1.md#contact-information) PowerWorld for assistance.

![Contingency Iterated Linear Analysis Handled Fields](images/Contingency_Iterated_Linear_Analysis_Handled_Fields.gif)

Calculating Flows During Iterated Method

  - MW flows are determined from the contingency reference state MW plus the change in MW flow from the contingency determined by using LODF calculations.
  - MVA flows are calculated based on the MW flows and the Reactive Power Model chosen.
      - The Reactive Power Model comes from the [contingency options](22-contingency-analysis-options.md#basics) during contingency analysis
      - The Reactive Power Model comes from the [ATC options](32-available-transfer-capability.md#advanced-options) during ATC analysis but the flows are calculated based on the [contingency methodology](22-contingency-analysis-options.md#basics).
  - Amps determined from MVA and contingency reference state voltages

---

<a id="other-contingency-actions"></a>

## Other Contingency Actions

*Source: [`Content/MainDocumentation_HTML/Other_Contingency_Actions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Other_Contingency_Actions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Clicking the **Other \>** button on the bottom of the [Contingency Analysis dialog](#contingency-analysis-dialog) provides access to various actions as described below:

Delete All Contingencies

Click this to delete all the contingencies presently stored in memory.

Clear All Contingency Results

Click this to clear all the results of the contingencies from memory. This will not delete the contingencies.

Set As Reference

Click this to set the case presently in memory as the Reference State for contingency analysis. For more information on the reference state, see [Contingency Case References](21-contingency-analysis-overview-and-records.md#contingency-case-references).

Restore Reference

Click this to set the state of the present power system case back to the contingency analysis reference state. For more information on the reference state, see [Contingency Case References](21-contingency-analysis-overview-and-records.md#contingency-case-references).

Convert Contingencies to Transient Contingencies

This option will create transient contingencies from the currently defined steady state contingencies based on a hardcoded set of assumptions. Additional changes may be required to completely model the transient events, but this functionality provides a starting point for a conversion.

The following assumptions are used in the conversion:

  - Fault on time
  - 1 second
  - Fault location
  - If first element in contingency is a bus, apply fault at that bus
  - If first element in contingency is a branch, apply fault at from bus of that branch
  - If first element in contingency is anything except a bus or branch, do not apply a fault but do open all elements at 1 second
  - Fault type
  - Balanced 3 phase
  - Fault clearing time
  - Bus fault
  - 500 kV bus use 1 second plus 3 cycles
  - 230 kV bus use 1 second plus 4 cycles
  - 115 kV bus use 1 second plus 6 cycles
  - Branch fault
  - 500 kV branch use 1 second plus 3 cycles at from end and 1 second plus 4 cycles at to end
  - 230 kV branch use 1 second plus 4 cycles at from end and 1 second plus 5 cycles at to end
  - 115 kV branch use 1 second plus 6 cycles at from end and 1 second plus 7 cycles at to end
  - Time at which to change remaining elements
  - If bus fault open all remaining elements when fault is cleared
  - If branch fault open all remaining elements when to end of the line is opened

Convert to Device Contingencies

This command is intended for use with full topology models, where breakers and disconnects are defined in addition to generators, loads, transmission lines, etc. This function would have no affect on a traditional planning model representation in which no breakers or disconnects are explicitly defined.

The purpose of this option is to allow the user to take a contingency set that is defined with outages of breakers and disconnects in a full topology model and convert them to outages of the traditional planning model elements, such as generators, loads, transmission lines, etc. This would be used in conjunction with the ability to save a full topology model as a consolidated model. A consolidated model reduces the full model down to a traditional planning model by examining the breaker and disconnect statuses and reducing the system down by consolidating breakers and disconnects that are in service. The resulting model is a smaller model with the traditional planning elements represented, but breakers and disconnects have been removed and nodes aggregated into bus representations. This function will also take the breaker and disconnect statuses and convert them into contingencies of the planning model devices affected by opening the original breakers or disconnects. Thus, you could create a contingency that is defined for the consolidated model and can be run on the consolidated model with the same results as if the original contingency set is run on the full topology model.

The contingency set generated depends on the statuses of the breakers and disconnects, and the contingencies created will be different for the different statuses of breakers and disconnects in the full topology model.

There are two options when converting to device contingencies:

Keep Only Devices

This is the default functionality where the contingency results will only contain the devices that are affected by the operation of breakers in the original contingency definition. This could result in contingencies with no actions if no devices are found that are affected by the breakers in the contingency.

Keep Original If Empty

After the conversion process is complete, original breaker definitions will be retained for any contingencies that end up with no actions. This could result because no devices are found that are affected by the original breakers in the contingency. This functionality is necessary if there are contingency definitions that open single breakers without the intent of isolating other devices.

Cleanup Blocks and Global Actions

Merge Contingency Block Elements

Selecting this will eliminate contingency blocks by adding the elements that are in contingency blocks to the contingency elements, Global Actions, or Remedial Actions that are using the blocks. We strongly encourage you to discontinue use of [Contingency Blocks](21-contingency-analysis-overview-and-records.md#contingency-blocks).

Convert Global Actions Into Remedial Action

Selecting this will convert legacy [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) into a more versatile [Remedial Action](21-contingency-analysis-overview-and-records.md#remedial-actions). A single Remedial Action will be created. We strongly encourage you to use Remedial Actions instead of Global Actions.

Combined Tables

Contingency Violation Matrices

Clicking **Process Contingency Results** will go through the existing contingency analysis tool results and build tables showing the limit violation values for all violated branches, interfaces, buses, bus pairs, custom monitors and the contingencies for which each element is violated. Upon opening, it is possible to limit processing to branches, buses, interfaces, bus pairs, and/or custom monitors. Also, you can specify whether to display percentages or actual flows in the resulting tables.

Contingency Violation List

Opens a table of all violations for all contingencies.

Contingency Element Definitions

Opens a table of all individual contingency actions from the current contingency list.

What Actually Occurred?

Opens a table of all individual records indicating which actions were applied or skipped for the current contingency list.

Produce Report

Select this option to produce a detailed report of the results of the contingency analysis. This will launch a save window that will save the information you customized on the [Report Writing](#report-writing) page. You will also be given the option of viewing the report in WordPad immediately after creating the file.

Compare Two Lists of Contingency Results

Click this to open a dialog which allows you to specify two sets of contingency analysis results to compare. For more information on this comparison, see [Comparing Contingency Analysis Results](#comparing-two-contingency-analysis-results).

Filter Results Using Limit Monitoring Settings

Click this to filter the contingency analysis results using the present [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings). This action will go through each violation for each contingency and verify that the element that was violated is set to be monitored. If the element is not set to be monitored, then Simulator will flag the violation internally as **inactive**. You will then not be able to see these violations on any of the displays, although they will still be saved in memory until you delete these contingencies, or reprocess them. These violations will also not be saved when you choose to save the contingency results.

Because the violations are saved in memory however, you can get them back without reprocessing the contingency list. To do this, change your Limit Monitoring Settings so that those violations will be set for monitoring again. Then click this option again.

When using this option, keep in mind that Simulator cannot filter results that do not exist in memory. If the filter is to be used to filter out different percentages of overload, then the contingency analysis should be run with the lowest percentage desired. For example, if the filter option is to be used to give all of those elements that are loaded above 70% of their limit and then those that are loaded above 90% of their limit, the contingency analysis should be run with the Limit Monitoring Settings defined to monitor elements that are loaded at 70% of their limit. Also, keep in mind that the more elements are monitored the slower the processing will be.

Auto-fill Blank Contingency Element Comments

Selecting this option will fill the Comment field of the Contingency actions in the [Contingency Definition](22-contingency-analysis-options.md#contingency-definition-display) table with a copy of the contingency action definition. The action description itself cannot be modified, but the comment can be modified to be more descriptive of the action being taken, for your own reference.

Sensitivity Calculations \>

Simulator provides the [PTDF tool](20-sensitivities.md#power-transfer-distribution-factors) for calculating the impact of a MW transfer on all the transmission lines in the system. The Simulator [ATC tool](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) further extends the linearized methods by integrating linearized contingency analysis with the PTDF calculations. The sensitivity calculations provided here are an extension of this. They allow you to ask the question, **How will each contingency-caused branch or interface violation be affected by a MW transfer?**. This calculation is not relevant for bus violations.

Calculate OTDFs using existing PTDFs

Before executing this, you must first go to the [PTDF Dialog](20-sensitivities.md#power-transfer-distribution-factors-dialog) and calculate the PTDFs for the transfer direction you are interested in. These PTDF values will then be used throughout the OTDF calculation. Click this to calculate OTDFs for each contingency-caused branch or interface violation. The values calculated will be a measure of what percent of a transfer would appear on the branch or interface after the respective contingency occurs. Realize for branch violations, that the sign of the OTDF value will be relative to the direction of the MW flow found during the contingency analysis (see the Element description on the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display)).

The OTDF and PTDF values for each violation for which they have been calculated can be found in either the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display) that is used to list the violations for a contingency selected in the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab) or the Contingency Violation List, which lists all violations for any contingency and is found on the [Results tab](#results-tab) of the contingency analysis dialog. The OTDF and PTDF fields are not shown by default in these tables and will need to be added.

The following options are applicable when calculating the PTDFs and LODFs needed for calculating the OTDFs:

  - Transfer direction is specified with the [PTDF calculation options](20-sensitivities.md#power-transfer-distribution-factors-dialog) for Seller and Buyer
  - The calculation method selected with the [PTDF calculation options](20-sensitivities.md#power-transfer-distribution-factors-dialog) determines if phase shifters are assumed to enforce their flow during the PTDF and LODF calculations. Phase shifters will only be enforced if selecting the *Lossless DC with Phase Shifters* option.
  - Make up power is determined by the contingency analysis setting for [make up power](22-contingency-analysis-options.md#basics). If the *Area Participation factors specified below* option is selected, that will be used, otherwise the *Generator Participation Factors From Entire Case Directly* option will be used.
  - When calculating LODFs the [DC power flow model options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options) for DC Power Flow Line Model, Ignore Transformer Impedance Correction Tables, and Ignore Phase Shift Angle Effects are used.
  - To include the effects of conditional actions when determining the linear impact of the contingency, the contingency option to [Iterate on Action Status](22-contingency-analysis-options.md#dc-and-screening-options) can be used

Filter out Violations Using OTDFs

Once you have calculated the OTDFs using the existing PTDFs, you can then filter the results by selecting this option. A dialog will appear for you to enter a minimum OTDF value. All violations that have an OTDF smaller than this number will be flagged as **inactive** and will not show up in the list of violations. See the note above regarding the **Filter Results using Limit Monitoring Settings** to better understand how inactive violations are treated.

---

<a id="contingency-sensitivity-analysis"></a>

## Contingency Sensitivity Analysis

*Source: [`Content/MainDocumentation_HTML/Contingency_Sensitivity_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Sensitivity_Analysis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Sensitivity Analysis tool allows closer inspection of the impact that a contingency has on a particular violation through the use of linear sensitivity calculations. Accessing this tool is linked to a contingency violation and can be done by selecting **Contingency Sensitivity Analysis** found under the record type specific options on the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display) found on the [Contingencies tab](22-contingency-analysis-options.md#contingencies-tab) of the [Contingency Analysis dialog](#contingency-analysis-dialog) or the local menu of the Contingency Violation List found on the [Results tab](#results-tab) of the Contingency Analysis dialog. This tool will only be available if using the contingency analysis **Calculation Method** of *Full Power Flow* and the case is in ac power flow mode. This tool is also only available for branch and interface violations.

Opening the tool will apply the contingency that is associated with the selected violation. The contingency will remain applied until the user manually restores the contingency reference state or another contingency is run. The contingency sensitivity analysis dialog will remain open until the user closes it. If the **Contingency Sensitivity Analysis** option is selected for another violation while the dialog is open, the contingency reference state is restored, the contingency associated with the newly selected violation is applied, and the dialog is updated with the new contingency and violation information.

Sensitivities that will be calculated include [Transmission Loading Relief (TLR)](20-sensitivities.md#shift-factor-sensitivities) type sensitivities. These types of sensitivities determine how the loading on a monitored branch can be impacted by real power transfers. The sensitivities used here will calculate the impact on the violation of transferring power from single generators and loads to the system slack. These sensitivities will always be calculated for the violation. Optionally, additional interfaces can be selected for which TLR sensitivities will be calculated. These can be selected with the **Interface Selection for TLR** options.

[Line Outage Distribution Factors (LODF)](20-sensitivities.md#line-outage-distribution-factors-lodfs) can be calculated for closed lines and Line Closure Distribution Factors (LCDF) can be calculated for open lines. These calculations determine the impact on the violation of either opening or closing the selected lines. These calculations are only done if there are branches selected with the **Branch Selection for LODF/LCDF** options.

Both the TLR and LODF/LCDF sensitivities are calculated using the Lossless DC calculation method. Phase shifters are assumed to operate if the power flow solution option specified with contingency analysis allows phase shifters to operate. Specifically, the **Disable Phase Shifter Control** power flow solution option is not checked for the [different ways](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options) in which contingency power flow options are specified. When phase shifters are allowed to operate in sensitivity calculations this means that the sensitivity of the phase shifter to any changes (injection changes for TLR and line status changes for LODF/LCDF) is 0 because it can maintain its specified flow.

The dialog is broken into two main sections: (1) the top section with general information about the violation and contingency and buttons to control the calculation of sensitivities and (2) the bottom section containing tabs of sensitivity results and options for graphically highlighting the results.

Contingency Name

Informational field giving the name of the contingency that caused the selected violation.

Violation

Description of the selected violation. For a branch violation, this indicates the direction of flow and the end at which the violation is recorded.

Near MW

MW flow on the violation at the near bus indicated in the violation description during the contingency. For an interface violation this will indicate the flow on the interface according to how the interface is defined.

Far MW

MW flow on the violation at the far bus indicated in the violation description during the contingency. This will be blank if the violation is an interface.

View Violation Filter

An advanced filter is automatically created for the violated element. This filter is named *CTG Violation Filter*. The filter will be created for the object type of the violation. The violation will be returned if the violation is a branch and this filter is applied to a list of branches or if the violation is an interface and this filter is applied to a list of interfaces. Clicking this button will open the dialog to view this filter and make modifications as necessary. As different violations are selected for examination this same filter will be updated to reflect the new violation.

This filter is created because it can be useful when defining [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for highlighting sensitivity results on oneline displays.

Interface Selection for TLR

Use these options to select additional interfaces for which TLR sensitivities will be calculated.

The **Use Selected** option will calculate sensitivities for any interfaces where the **Selected** field is *YES*. Click the **Select Interfaces** button to open a dialog that allows easy setting of the Selected fields.

The **Meets Filter** option will calculate sensitivities for any interfaces that meets the specified filter. Click the **Define Filter** button to open a dialog to select the filter.

Any selected interfaces will show up in additional columns in the tables on the **Generators Tab** and **Loads Tab**.

Branch Selection for LODF/LCDF

Use these options to select branches for which to study the impact of the outage/closure (LODF/LCDF) on the violation.

The **Use Selected** option will calculate LODF/LCDF sensitivities for any branch where the **Selected** field is *YES*. Click the **Select Branches** button to open a dialog that allows easy setting of the Selected fields.

The **Meets Filter** option will calculate LODF/LCDF sensitivities for any branch that meets the specified filter. Click the **Define Filter** button to open a dialog to select the filter.

Any selected branches will show up as rows in the table on the **Branches Tab**.

Calculate Sensitivities

Click this button to actually perform the calculations.

Restore Contingency Reference

Click this button to restore the system state to the stored contingency reference state. Opening the Contingency Sensitivity Analysis dialog will implement the contingency associated with the selected violation. The contingency will remain implemented, even if the Contingency Sensitivity Analysis dialog is closed, until the contingency reference state is restored manually or as part of the contingency solution process when another contingency is implemented.

Set as Contingency Reference

Click this button to set the current system state as the contingency reference state.

Generators Tab

This tab contains the TLR sensitivities for the transfer of real power from single generators to the system slack. The impact of these transfers is shown for the violation and any selected interfaces.

The **Increase Generator** table contains default fields to show how increasing the output of generators will cause the flow on the violation to decrease. The **Decrease Generator** table contains default fields to show how decreasing the output of generators will cause the flow on the violation to decrease. The common default fields for both tables are the following:

Object ID

Identifies the generator. The key fields used for identification will change if the [Key Fields to Use in Subdata Sections](10-power-flow-solution-and-options-part2.md#case-information-display-options) option changes.

Gen MW

Present MW output of the generator. This is informational only and cannot be changed.

Gen Max MW

Max MW of the generator. This is informational only and cannot be changed.

Gen Min MW

Min MW of the generator. This is informational only and cannot be changed.

Violation

A column will exist for the violation with the header being the name of the violation element. The values are the power transfer distribution factors for the impact on the violation of transferring real power from the generator in the respective row to the system slack. This is the same as doing a TLR calculation on the violation.

Interfaces

Columns will be added for the interfaces that are selected with the **Interface Selection for TLR** options. The column headers will be the names of the interfaces. The values in each column are the power transfer distribution factors for the impact on the interface of transferring real power from the generator in the respective row to the system slack. This is the same as doing a TLR calculation on each of the interfaces.

The following field(s) are available on both tables but are not shown by default:

Selected

This is the same as the **Selected** field found with generator records. This field is available because it can be useful when defining [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for highlighting sensitivity results on oneline displays. Click the **Unselect All Generators** button to set **Selected** to *NO* for all generators in the case.

In addition to the fields specified above, the **Increase Generator** table contains the following field(s) by default:

Max Line MW Flow Decrease by Increase Gen

This value is the maximum amount of MW relief that can be achieved on the violation by increasing generator MW output up to Gen Max MW. Relief = (Gen Max MW - MW)\*(-TLR Sensitivity). If the generator is operating above its max MW limit, the amount of relief will be 0.

By default, this field will automatically be sorted from high to low.

In addition to the fields specified above, the **Decrease Generator** table contains the following field(s) by default:

Max Line MW Flow Decrease by Dropping Gen

This value is the maximum amount of MW relief that can be achieved on the violation by dropping the generator. Relief = (MW)\*(TLR Sensitivity).

By default, this field will automatically be sorted from high to low.

The following field(s) are available and relevant for the **Decrease Generator** table but is not shown by default:

Max Line MW Flow Decrease by Decrease Gen

This values is the maximum amount of MW relief that can be achieved on the violation by decreasing generator MW output down to Gen Min MW. Relief = (MW - Gen Min MW)\*(TLR Sensitivity). If the generator is operating below its min MW limit, the amount of relief will be 0.

Loads Tab

This tab contains the TLR sensitivities for the transfer of real power from single loads to the system slack. This impact of these transfers is shown for the violation and any selected interfaces.

The **Increase Load** table contains default fields to show how increasing the output of loads will cause the flow on the violation to decrease. The **Decrease Load** table contains default fields to show how decreasing the output of loads will cause the flow on the violation to decrease. The common default fields for both tables are the following:

Object ID

Identifies the load. The key fields used for identification will change if the [Key Fields to Use in Subdata Sections](10-power-flow-solution-and-options-part2.md#case-information-display-options) option changes.

Load MW

Present MW output of the load. This is informational only and cannot be changed.

Load Max MW

Max MW of the load. This is informational only and cannot be changed.

Load Min MW

Min MW of the load. This is informational only and cannot be changed.

Violation

A column will exist for the violation with the header being the name of the violation element. The values are the power transfer distribution factors for the impact on the violation of transferring real power from the load in the respective row to the system slack. This is the same as doing a TLR calculation on the violation.

Interfaces

Columns will be added for the interfaces that are selected with the **Interface Selection for TLR** options. The column headers will be the names of the interfaces. The values in each column are the power transfer distribution factors for the impact on the interface of transferring real power from the load in the respective row to the system slack. This is the same as doing a TLR calculation on each of the interfaces.

The following field(s) are available on both tables but are not shown by default:

Selected

This is the same as the **Selected** field found with load records. This field is available because it can be useful when defining [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for highlighting sensitivity results on oneline displays. Click the **Unselect All Loads** button to set **Selected** to *NO* for all loads in the case.

In addition to the fields specified above, the **Increase Load** table contains the following field(s) by default:

Max Line MW Flow Decrease by Increase Load

This value is the maximum amount of MW relief that can be achieved on the violation by increasing load MW output up to Load Max MW. Relief = (Load Max MW - MW)\*(TLR Sensitivity). If no limits are specified for the load or the load is above is max MW limit, the amount of relief will be 0.

By default, this field will automatically be sorted from high to low.

In addition to the fields specified above, the **Decrease Load** table contains the following field(s) by default:

Max Line MW Flow Decrease by Decrease Load

This value is the maximum amount of MW relief that can be achieved on the violation by decreasing load MW output down to Load Min MW. Relief = (MW - Min MW)\*(-TLR Sensitivity). If no limits are specified for the load, 0 is assumed for Min MW. If the load is operating below its min MW limit, the amount of relief will be 0.

By default, this field will automatically be sorted from high to low.

Branches Tab

This tab contains the LODF/LCDF sensitivities for the impact on the violation of any branches chosen with the **Branch Selection for LODF/LCDF** options. Each row of the results represents a line that is either being outaged or closed.

The following fields are available:

Object ID

Identifies the branch that is being outaged/closed. The key fields used for identification will change if the [Key Fields to Use in Subdata Sections](10-power-flow-solution-and-options-part2.md#case-information-display-options) option changes.

LODF/LCDF Line Status

Status of the branch that is being outaged/closed. This is informational only and cannot be changed.

LODF/LCDF

LODF/LCDF sensitivity of the violation in the direction in which the element is a violation (Near --\> Far). If outaging the line causes new islands to be formed or closing in the line would connect two different islands, the sensitivity calculation cannot be done. *Island Change* will appear in this field and the other results will be blank.

MW LODF/LCDF Line

MW flow on the branch that is being outaged/closed. For a line that is currently open, the post-closure flow is shown. Because we do not know what this value is until we actually close the line, we also need to calculate this from linear sensitivities and the pre-closure voltages and angles.

MW Change Violation Near

Change in MW flow on the violation at the Near end of the violation due to the outage/closure.

MW Change Violation Far

Change in MW flow on the violation at the Far end of the violation due to the outage/closure.

New MW Violation Near

Resulting MW flow on the violation at the Near end of the violation due to the outage/closure. This is (Near MW) + (MW Change Violation Near).

New MW Violation Far

Resulting MW flow on the violation at the Far end of the violation due to the outage/closure. This is (Far MW) + (MW Change Violation Far).

Selected

This field is not shown by default but is available. This is the same as the **Selected** field found with branch records. This field is available because it can be useful when defining [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for highlighting sensitivity results on oneline displays. Click the **Unselect All Branches** button to set **Selected** to *NO* for all branches in the case.

Highlight Options Tab

This tab contains information that is useful for defining [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for highlighting sensitivity results on oneline displays. The values on the sensitivity dialog are not accessible through typical auxiliary file fields and script commands. To make them accessible and useful to dynamic formats, the options on this tab allow selected sensitivity values to be transferred to custom fields that can be accessed by dynamic formats and other auxiliary file functions.

Object Type

The available types include *Generators*, *Loads*, and *Branches* and correspond to the tabs of results that are provided. To access particular results from a tab, select the object type of that tab.

Sensitivity Field

The dropdown contains all of the fields that are available in the results for the selected object type. The **Find** button will open a dialog that provides easy searching and selection of a field. This is the field that will populate a custom field. The following options determine which values to actually populate:

**Use Absolute Value**

Check this box to use the absolute value of the chosen sensitivity field. Prior to populating the values in the selected field, the values are sorted. If using this option, the absolute value will be used in the sorting. The sorting will then determine which values are populated in the **Top X to Include**.

**Sign of Values**

When populating values in the selected field, values can be excluded if they are not the correct sign. To ignore the sign choose *All Values*. To use only values greater than zero choose *Only Positive*. To use only values less than zero choose *Only Negative*.

**Exclude Zeros**

Check this box to not populate zero values in the selected field.

**Sort High to Low**

Prior to populating the values in the selected field, the values are sorted. Check this box to sort from high to low. If this box is not checked, the values will be sorted from low to high. The **Use Absolute Value** option is applied to the values prior to the sorting. The sorting will then determine which values are populated in the **Top X to Include**.

Field to Populate

Only Custom Floating Point fields can be populated. This dropdown allows selection of which Custom Floating Point field should be populated.

Clear Existing Values

Check this box to remove any values that currently exist in the selected **Field to Populate** prior to populating new values.

Top X to Include

Before populating values in the selected field, the values are sorted based on the **Sort High to Low** option. The **Use Absolute Value** option is applied prior to the sorting. This option then determines how many values to populate from the specified sorting. The **Sign of Values** and **Exclude Zeros** options will cause values to be skipped in the sort order if they do not meet the condition. The skipped values will not count towards the number to include. If specified as 0, all values will be populated as long as they meet the **Sign of Values** and **Exclude Zeros** conditions.

Populate Values

Click this button to transfer the selected **Sensitivity Field** to the **Field to Populate**.

Example

All of these options are useful and necessary to identify generators and loads that have the largest impact on reducing the flow on the violation. As an example, there could be many different generators that have an impact on reducing the flow, but maybe you are only interested in seeing the 10 generators with the highest impact highlighted. These generators must also be dropped to reduce the flow. The following settings will accomplish this:

![Contingency Sensitivity Analysis Highlighting 724x591](images/Contingency_Sensitivity_Analysis_Highlighting_724x591.gif)

Dynamic formats using the custom floating point values that have been populated and the violation filter can then be defined to highlight the generators with the largest impact (thick blue lines) on the violation (dark red line) as shown below.

![Contingency Sensitivity Analysis Highlighting2](images/Contingency_Sensitivity_Analysis_Highlighting2.gif)

---

<a id="results-tab"></a>

## Results Tab

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results tab of the [Contingency Analysis dialog](#contingency-analysis-dialog) contains many options for viewing the results of a contingency analysis run.

  - [View Results by Element](#view-results-by-element) : navigate the list of limit violations by the element which is violated.
  - View Results by Contingency : navigate the list of limit violations by the contingency which caused the violation. Essentially shows the same layout as seen on the [Contingencies Tab](22-contingency-analysis-options.md#contingencies-tab).
  - Contingency Violations List : get a combined list of all contingency/limiting element pairs that result in a violation. This table has special right-click options to **View/Modify Existing Violation CTG Note** and **Create Violation CTG Note** that will provide information about [Violation CTG Notes](#violation-ctg-notes)(Added in Version 20)that apply to particular violations. See the [Violations CTG Notes help](#violation-ctg-notes) for more information on Violation CTG Notes.
  - [Violation CTG Notes](#violation-ctg-notes): Violation CTG Notes are special notations about contingency violations that commonly occur in your system. If you know ahead of time that a particular contingency often causes violations on a particular set of branches, then you may want to provide some text notes about these. The Violation CTG Notes can then be shown on the a list of contingency violations.
  - [Violation CTG Injection Sensitivities](#violation-ctg-injection-sensitivities): Violation CTG Injection Sensitivities are shift factor sensitivities that are calculated for each contingency violation. This list contains all of the injection sensitivities that are calculated for each violation for each contingency.
  - [What Occurred](#what-occurred) : Get a list of actions that occurred during the selected contingency. This is especially useful for identifying those actions conditional on Model Criteria being applied. It is also helpful when using the special [Open with Breakers](24-contingency-element-dialog.md#contingency-element-open-breakers) contingency actions because the list will indicate which breakers need to be opened to isolate the devices.
  - Contingency Violation Matrices : Provides access to a dialog where a matrix of contingency versus limit elements can be created with entries showing the flow or voltage of the element to the respective contingency.[Text File Report Writing](#report-writing) : provides options for writing out a text file report
  - [Summary](#summary-tab) : a simple text summary showing the progress of the contingency analysis run.

---

<a id="view-results-by-element"></a>

## View Results by Element

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_Tab_View_Results_By_Element.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_Tab_View_Results_By_Element.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These contingency results are all available on the [Contingency Analysis dialog](#contingency-analysis-dialog) under the [Contingency Analysis: Results tab](#results-tab).

The View Results By Element category contains the following sub-pages: Lines/Transformers, Buses, Interfaces, Bus Pairs, Nomogram Interfaces, and Custom Monitors. The information contained on each of the sub-pages provides an alternate method of viewing information similar to that contained on the [Contingencies tab](22-contingency-analysis-options.md#contingencies-tab). The individual pages show model objects (subject to area/zone/owner and advanced filters) only if they are associated with specific contingencies. For objects other than Custom Monitors, the user can select any model object on its respective page to see how many times a violation occurred on the device during a run of a set of contingencies. When a particular device is selected, the two pages at the bottom give the details of the analysis for the selected device.

Note: the information contained in the [Contingencies](#contingencies-section) and [Contingency Definition](22-contingency-analysis-options.md#contingency-definition-display) sections of the View Results By Element page is object specific. The information present only pertains to contingencies that resulted in violations on the selected object.

---

<a id="contingencies-section"></a>

## Contingencies Section

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_Tab_View_Results_By_Element_Contingencies_Section.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_Tab_View_Results_By_Element_Contingencies_Section.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingencies section gives a list of all the contingencies that caused a violation on the selected device during the analysis. This display is very similar to the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display). While the Contingency Violations Display shows the *elements violated under the contingency*, this display shows the *contingencies that caused the violation*. If you then select one of the contingencies in this list, the [Contingency Definition section](22-contingency-analysis-options.md#contingency-definition-display) displays the actions that took place during the selected contingency. Also, when you have selected a contingency from this list, you can click the **Show Other Violations** button. This will change your dialog to the contingencies tab and select the contingency you have selected, thus allow you to see other violations caused by this contingency.

The **Combined Tables** button provides access to the Combined Tables options described in [Other Contingency Actions](#other-contingency-actions). In addition to these options, there is one other option for displaying **[What occurred](#what-occurred)** found under the Combined Tables button. Selecting this will display a dialog box giving the details of the actions applied during all contingencies and any actions that may have been skipped.

This page provides an easier way to check the contingency results when you are concerned with the results for a specific device in the system. The View Results By Element page provides a much easier tool for this kind of examination, as opposed to looking through each contingency on the Contingencies tab and trying to find each instance of a violation on the desired element.

---

<a id="what-occurred"></a>

## What Occurred

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_What_Occurred.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_What_Occurred.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The What Occurred information with contingency analysis results provides details of the actions associated with each contingency and those that were applied or skipped. Additional information about the status of devices, i.e. line flows before a line is open or generation level changes, is also supplied. The What Occurred information can be accessed from several places.

  - To view a list of what occurred for a single contingency, a tab is available next to the [Contingency Violations Display tab](22-contingency-analysis-options.md#contingency-violations-display) when selecting a single contingency from the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab)
  - To view a list of what occurred for a single contingency, click on the **What Occurred** option from the local menu of the [Contingency Records Display](22-contingency-analysis-options.md#contingencies-tab)
  - To view a list of what occurred for a single contingency, click on the **What Occurred** option from the local menu of the Contingency Violation List table found on the [Contingency Results tab](#results-tab)
  - To view a list of what occurred for all contingencies, the [Contingency Results tab](#results-tab) contains the **What Occurred** table

Each row of the table represents a contingency element action with the details of what occurred. An example of the table format is shown below:

![What Occurred Table Format](images/What_Occurred_Table_Format.gif)

Field Descriptions

The fields that appear in either the text or table format of What Occurred have the following meaning:

Contingency

Name of the contingency to which this element belongs.

Applied or Skipped

Applied actions are those that are implemented during the contingency. Skipped actions result because the **Model Criteria** specified with the contingency is not met. Only actions that belong to the contingency itself will be reported as skipped. [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions), [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions), and [Transient Actions](22-contingency-analysis-options.md#transient-models) will not be reported as skipped because there could be a large number of these defined that are routinely skipped.

Actions

Contingency element action as provided with the [contingency element definition](24-contingency-element-dialog.md#contingency-element-dialog). The format of the actions can be changed by changing the **Contingency Action Description in What Occurred** found with the [Miscellaneous](22-contingency-analysis-options.md#miscellaneous) options. This option must be set BEFORE the analysis is run for the changes to take effect.

Model Criteria

Contingency element Model Criteria as defined with the [contingency element definition](24-contingency-element-dialog.md#contingency-element-dialog).

Status

Contingency element Status as defined with the [contingency element definition](24-contingency-element-dialog.md#contingency-element-dialog).

Comment

Contingency element Comment as defined with the [contingency element definition](24-contingency-element-dialog.md#contingency-element-dialog).

Brief What Occurred

This provides details of what happened when applying this contingency element action. This will show details such as how much flow was on a line when it was opened, how much generation changed, how much load changed, etc.

When using the *Open Breakers* or *Close Breakers* [contingency actions](24-contingency-element-dialog.md#contingency-element-dialog) for a device, this field will indicate which breakers operated to isolate or close a device. Additional action records will be added for each breaker that operated.

Origin of Action

Each contingency can be comprised of elements from the base contingency record, contingency blocks, global actions, remedial actions, and transient actions. This field provides details of where the element is defined. This is useful when tracking the implementation of special protection schemes (SPS) or remedial action schemes (RAS) that might be defined outside of the contingency definition.

The elements that are included within the implementation of a contingency can come from several sources:

ELEMENT - element is defined with the [base contingency record](22-contingency-analysis-options.md#contingencies-tab)

BLOCK - element is defined with a [Contingency Block](21-contingency-analysis-overview-and-records.md#contingency-blocks) that is part of the [base contingency record](22-contingency-analysis-options.md#contingencies-tab)

GLOBAL - element is defined with the [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions)

REMEDIAL - element is defined with the [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions)

TRANSIENT - element is defined as one of the [Transient Models](22-contingency-analysis-options.md#transient-models) that acted

*Open Breakers* and *Close Breakers* contingency actions will dynamically determine the breakers that need to operate. These actions will appear in the what occurred list as *Open* or *Close* actions on the actual breakers. To indicate that these actions were dynamically created and not defined explicitly with the contingency or remedial action, the keyword DYNAMIC will be appended to the source keyword for the action.

Remedial Action

Name of the remedial action to which the action belongs if the **Origin of Action** is REMEDIAL; otherwise, this field will be blank.

What Occurred

This is a repeat of the entirety of what occurred in the **Text Format**.

Time Delay

This is the time delay that was used when the action was applied. Time delays can come from several different sources as described in the [treatment of time delays topic](#treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays).

Group Order

This is an integer value that specifies the group in which the action was applied. The [contingency process](#running-the-contingency-analysis) has different steps that are determined by the **Status** of an action, i.e. CHECK, TOPOLOGYCHECK, POSTCHECK, etc. These different steps of the process define a new group. Any *Solve Power Flow* contingency actions will also define a new group. This value helps determine the overall order in which actions were applied.

Group Status

Status that defines the step in the [contingency process](#running-the-contingency-analysis) in which the action was applied, i.e. CHECK, TOPOLOGYCHECK, POSTCHECK, etc.

Subgroup Order

This is an integer value that specifies the order in which an action with applied within its **Group**. Sorting the what occurred results by **Group Order** and then **Subgroup Order** will give the overall order in which actions were applied.

---

<a id="violation-ctg-notes"></a>

## Violation CTG Notes

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_ViolationCTGNotes.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_ViolationCTGNotes.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Violation CTG Notes are special notations about contingency violations that commonly occur in your system. If you know ahead of time that a particular contingency often causes violations on a particular set of branches, then you may want to provide some text notes about these. A ViolationCTGNote has the fields which are described below. A ViolationCTGNote will be considered to apply to a particular ViolationCTG or LimitViol object if all of the logic described below the list of fields evaluates to true.

On the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display), there are then fields which can show the Notes on the case information display as well as a right-click option to open up any ViolationCTGNotes that may apply to a particular Violation.

Also, associated with the development of the Violation CTG Notes was work to make viewing contingency analysis results from an EMS system easier. In order to facilitate this, special fields were added to a Bus, Branch, Interface, BusPair, LimitViol and ViolationCTG object which identify these objects in a syntax used with one EMS system. These fields are available under the Topology Folder of the list of fields for particular objects. The field names are EMSViolID for most object, but for the ViolationCTG object the field name is LV\_EMSViolID.

Contingency

(KEY FIELD) Name of the contingency to which the note applies. Can be specified as blank meaning this note applies under all contingencies for objects below.

ObjectType

(KEY FIELD) The type of object to which this note applies. Can be specified as blank meaning this note applies to all violations for Contingency above. Note: The ObjectType must be specified as a valid ObjectType recognized by Simulator.

Object

(KEY FIELD) object identifying string indicating the object to which the note applies (example SUBSTATION$ND$891 to designate a particular ND to monitor) If this field is left blank, then this note applies to all objects of the type ObjectType. The type of the Object also does not have to match the ObjectType.

Category

(KEY FIELD) String used to be a filter on the Category of the limit violation. The check will be if the Violation's Category contains the string defined by the field. Thus if you wanted a ViolationCTGNote to apply to either a "Branch MVA" or a "Branch Amp" then you would just set Category to "Branch". Similarly you could just enter Category to "Bus" if you wanted to this note to apply to any of the various types of bus violations. The list of Category possible can be found in the [Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display) help.

FilterSubstation

(KEY FIELD) This could be blank in which case we would ignore the value. Otherwise it is the Name of the [substation](05-case-information-displays-by-object-part1.md#substation-records-display) at which the violation occurs.

  - For bus violations this would mean the bus must belong to the substation.
  - For branch violations this means the violated end must match the substation.
  - For bus pair violations this means that either the from bus or the to bus of the Bus Pair belongs to the substation.
  - For interface violations this would be ignored

FilterNomkVMin

(KEY FIELD) This could be blank in which case we would ignore the value.

If this value is specified and the **FilterNomkVMax** value is not specified, then the bus associated with the violation must be equal to this value

If this value is specified AND **FilterNomkVMax** is also specified, then the bus associated with the violation must be between **FilterNomkVMin** and **FilterNomkVMax**.

This would apply to bus object directly. For branches it applies to the violated end. For Bus Pair violations then if either bus meets the criteria it passes. For interface violations this is ignored.

To avoid worrying about floating point comparisons such as does 137.9999 = 138.0000, comparison are done with a 0.1% tolerance. Thus any nominal voltage that is within 0.1% of either **FilterNomkVMin** or **FilterNomkVMax** values will always be treated as though they are equal. Thus a value of nominal voltage of 100.09 would be treated as equal to 100.00 because it's within 0.1%..

FilterNomkVMax

(KEY FIELD) This could be blank in which case we would ignore the value.

If this value is specified and **FilterNomkVMin** is not specified, then the bus associated with the violation must be equal to this value. If **FilterNomkVMin** is specified then see discussion above.

The note regarding floating point comparisons in the **FilterNomkVMin** text above also applies to **FilterNomkVMax**.

Filter

(KEY FIELD) Name of a [filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) that is applied to the objects of type <span class="underline">ObjectType</span> (this is not applied to the ViolationCTG or LimitViol objects). The user may also enter a simple string defining a single field comparison such as “NomkV = 500” so that a named filter need not be created.

Note

This is the string containing the note being maintained. The ViolationCTGNote can also be displayed in a dialog. When shown in a dialog the note can be very long and have multiple lines of text. The field shown in the case information display however will always contain only 1 line of text. To signify a new line of text the special characters /n/r should be added to the text. Thus the following string

Xena Warrior/n/rHarley

would appear in the dialog as

Xena Warrier

Harley

NoteNew

This is a string that would be a potential “new note” that would be applied. Same rules about new lines being represented by /n/r in the string as done for the Note field also apply to this field.

Modified

This is a YES/NO field that can be changed by the user. It will also be changed to YES every time that the Note field changes. This is meant to help a user keep track of which ViolationCTGNotes that have been changed.

ContingencyValid

Will show YES if the Contingency Name specified matches a presently defined contingency in the case (or if the Contingency is blank). Otherwise it will show NO.

FilterSubstationValid

Will show YES if the FilterSubstation Name specified matches a presently define contingency in the case (or if the FilterSubstation is blank). Otherwise will show NO.

Logic Used to determine if a ViolationCTGNote Applies to a particular ViolationCTG

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p><strong>// Check that Contingencies match</strong></p>
<p>(</p>
<p>(ViolationCTGNote.Contingency is not specified) // applies to all</p>
<p>OR</p>
<p>(ViolationCTGNote.Contingency = ViolationCTG.Contingency)</p>
<p>)</p>
<p>AND</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p><strong>// Check that objects match</strong></p>
<p>(</p>
<p>(ViolationCTGNote.ObjectType is not specified) // applies to all</p>
<p>OR</p>
<p>(ViolationCTGNote.Object = ViolationCTG.Object) // direct match</p>
<p>OR</p>
<p>(</p>
<p>// check for a match of the type</p>
<p>(ViolationCTGNote.ObjectType = type of ViolationCTG.Object)</p>
<p>AND</p>
<p>(</p>
<p>(ViolationCTGNote.Object is not specified)</p>
<p>OR</p>
<p>(ViolationCTGNote.Object contains the ViolationCTG.Object)</p>
<p>)</p>
<p>)</p>
<p>)</p>
<p>AND</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p><strong>Make sure the category matches</strong></p>
<p>AND</p>
<p>(ViolationCTG.Category contains the string ViolationCTGNote.Category)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p><strong>// Make sure that the violated object meets the filter specified</strong></p>
<p>(</p>
<p>(ViolationCTGNote.Filter is not specified)</p>
<p>OR</p>
<p>(ViolationCTG.Object meets the filter ViolationCTGNote.Filter)</p>
<p>)</p>
<p>AND</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p><strong>// Logic for checks against FilterSubstation</strong></p>
<p>(</p>
<p>(ViolationCTGNote.FilterSubstation is not specified)</p>
<p>OR</p>
<p>(Substation location of violation is at a substation</p>
<p>with the name FilterSubstation)</p>
<p>// For a branch the violated end will matter</p>
<p>)</p>
<p>AND</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>// If only one value of FilterNomkVMin and FilterNomkVMax</p>
<p>// is specified then do an equality check.</p>
<p>// If both are specified do a between check.</p>
<p>(</p>
<p>(</p>
<p>(FilterNomkVMin is not specified) AND (FilterNomkVMax is not specified)</p>
<p>)</p>
<p>OR</p>
<p>(</p>
<p>(FilterNomkVMin is specified) AND (FilterNomkVMax is not specified)</p>
<p>AND</p>
<p>(Bus at which violation occurs has a NomkV = FilterNomkVMin)</p>
<p>)</p>
<p>OR</p>
<p>(</p>
<p>(FilterNomkVMin is not specified) AND (FilterNomkVMax is specified)</p>
<p>AND</p>
<p>(Bus at which violation occurs has a NomkV= FilterNomkVMax)</p>
<p>)</p>
<p>OR</p>
<p>(</p>
<p>(FilterNomkVMin is specified) AND (FilterNomkVMax is specified)</p>
<p>AND</p>
<p>(Bus at which violation occurs has a NomkV &gt;= FilterNomkVMin)</p>
<p>AND</p>
<p>(Bus at which violation occurs has a NomkV &lt;= FilterNomkVMax)</p>
<p>)</p>
<p>)</p></td>
</tr>
</tbody>
</table>

---

<a id="violation-ctg-injection-sensitivities"></a>

## Violation CTG Injection Sensitivities

*Source: [`Content/MainDocumentation_HTML/Contingency_Results_Violation_CTG_Injection_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Results_Violation_CTG_Injection_Sensitivities.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These contingency results are available on the [Contingency Analysis dialog](#contingency-analysis-dialog) under the [Contingency Analysis: Results tab](#results-tab). Contingency injection shift factors and/or the MW effect are of changing generation and load injection for individual contingency violations are calculated according to the [Injection Sensitivities options](22-contingency-analysis-options.md#injection-sensitivities). These results can be used to determine potential generation and load changes needed to reduce loading on violated branches and interfaces.

The following fields are available:

Injector

(Key Field) Identifying information for the generator or load for which the injection sensitivity is calculated.

Name

(Key Field) Name of the contingency under which the violation occurs and the sensitivities are calculated.

Element (file format)

(Key Field) Identifying information for the branch or interface that is the violation for which the sensitivities are calculated.

MW Inj Sensitivity

Sensitivity of the MW flow (shift factor) on the Element under the contingency to a MW injection at the Injector.

MW Range Inc

Available range on the Injector to increase injection.

MW Range Dec

Available range on the Injector to decrease injection.

MW Effect Inc

The change in MW flow on the Element under the contingency if increasing the injection of the injector by the full range to increase injection: (MW Range Inc) \* (MW Inj Sensitivity)

MW Effect Dec

Th change in MW flow on the Element under the contingency if decreasing the injection of the injector by the full range to decrease injection: (MW Range Dec) \* (MW Inj Sensitivity)

The amount of injection that can be increased or decreased for a particular injector is determine based on the MW limits for the injector. For a generator the increase in injection is the difference between the maximum MW and present MW for the generator. The decrease in generator injection is the difference between the minimum MW and the present MW. Loads typically do not have maximum and minimum MW limits specified, and they will be ignored even if they are specified. The increase in load injection will be the present output of the load. The decrease in load injection will be 0.

---

<a id="report-writing"></a>

## Report Writing

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_Tab_Report_Writing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_Tab_Report_Writing.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis Dialog](#contingency-analysis-dialog) under the [Results Tab](#results-tab).

Simulator can produce a report that details the results of the contingency analysis. The Report Writing Tab allows you to control the content and appearance of the report. By default, the report will identify each contingency, whether or not it could be solved, and what violations resulted from it. By selecting options on this tab, you can include additional information in the report.

Optional Report Contents

Case Summary

The case summary prints the [Case Description](05-case-information-displays-by-object-part1.md#case-description) and then tallies the number of different power system components in the model.

Option Settings

If this item is checked, the report will list each of the options selected on the [Options Tab](22-contingency-analysis-options.md#options-tab) of the Contingency Analysis Dialog.

Monitored Areas, Monitored Zones

If either of these items is checked, the report will identify the areas and/or zones in which Simulator has looked for limit violations, and over what voltage ranges.

Line Flow, Interface Flow, and Bus Voltage Extremes

If one of these items is checked, the report will list the worst-case line flows or voltages seen for each monitored element during the contingency analysis. None, one, two, or all three of these can be chosen at one time.

Base Case Outages

If this item is checked, the report will list the limit violations that existed in the Base Case.

All

Selecting this option will select all of the other options.

Identify buses by

This setting determines how the buses are listed in the data stored in the report. You can choose to have the buses displayed by number or name only, or by a combination of the number and name. You can also choose to identify with nominal voltage by checking the box labeled **Identify with Nominal Voltage**.

Show the actions involved in each contingency

If this box is checked, the definition of each contingency will be included in the report. The definition of each contingency simply identifies the actions that were implemented as part of the contingency.

Report only contingencies that cause violations

Checking this option will cause only the contingencies that cause violations to be shown in the report. Any contingency that did not cause a violation will not be included in the report. This option is useful if you wish to limit the size of the contingency report.

Report only limit type with violations for each contingency

Checking this option will result in reporting only the contingency violations of the type checked in the **Limit Type Violations to Include** box.

Report Inactive Violations and show all Rating Sets

When this box is checked, all violations that are normally being ignored during the contingency analysis (for example, base case violations) will be written to the report. Included with this option is the ability to show the different rating sets for each violated element.

Limit Type Violations to Include

Check the boxes of the types of violations you would like to be written to the report. This corresponds to the **Report only limit type with violations for each contingency** option above.

Maximum Violations of a single type to report

Enter the value of the maximum number of violations of a single type to be written to the report.

Create database-friendly tables

Checking this box will create three additional files for viewing contingency results: FILENAME\_ctgelem, FILENAME\_ctgviol, and FILENAME\_ctgstat where FILENAME is the name of the file where the main report is saved. The user can choose which symbol to use to separate the columns by choosing a delimiting symbol. These files can be easily imported into a database or spreadsheet program such as Access or Excel as delimited text files, where they can be analyzed more rigorously. These files will be automatically created and saved in the same folder as the main report.

Produce Report

Clicking this button will open a Save Dialog for selecting the file to which the report should be written. The file is saved as a text file (\*.txt). Enter the file path and name and click **Save** to write the report to the selected file. After saving the file, a dialog will provide the option of viewing the report file immediately.

---

<a id="summary-tab"></a>

## Summary Tab

*Source: [`Content/MainDocumentation_HTML/Contingency_Summary_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Summary_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis Dialog](#contingency-analysis-dialog) under the [Results Tab](#results-tab).

The Summary Tab of the [Contingency Analysis Dialog](#contingency-analysis-dialog) provides additional information on the status of the contingency analysis run. The top half of the Summary Tab charts the progress of the contingency analysis run and issues warning messages when a particular contingency fails to solve. The next section features counters that indicate the total number of contingencies that comprise the list, the number of these contingencies that have been processed thus far, the number of contingencies that failed to solve, and the total number of violations that have been flagged.

---

<a id="comparing-two-contingency-analysis-results"></a>

## Comparing Two Contingency Analysis Results

*Source: [`Content/MainDocumentation_HTML/Comparing_Contingency_Analysis_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Comparing_Contingency_Analysis_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

After performing an automated contingency analysis, the results of the analysis can be saved to an auxiliary file. Once the results have been saved to a file, they can then be compared to different results in another file or to results existing in memory in the Contingency Analysis tool. To compare two sets of contingencies, do the following:

  - Process each set of contingencies and save the results for at least one set in an auxiliary file.
      - To save a contingency list, right-click on the list of contingencies and choose **Save As \> Auxiliary File**.
      - In the Save Contingency File Dialog, choose a name for the file, and then click **Save**.
      - You will then be prompted to choose options for saving the contingency list to an auxiliary file. By default, the contingency definitions themselves are saved, along with the contingency options. The optional information you may choose to save are the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings), General [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options), [List Display Settings](10-power-flow-solution-and-options-part2.md#case-information-display-options), and [Contingency Results](22-contingency-analysis-options.md#contingency-violations-display). When saving the contingency results with the file, you may also choose to include inactive violations.  
        Inactive violations are considered violations on elements for a DIFFERENT limit than what is currently being monitored. For example, a branch may have an A limit rating of 50 MVA, and a B limit rating of 100 MVA. Consider if the B limits are being used to report violations during a contingency. A value of 75 MVA flow on the branch would not be reported in the contingency analysis as a violation, considering the B limit of 100 MVA is being used. However, Simulator internally will flag the element as a potential violation if the limit set used is switched to the A rating set. Simulator considers these types of situations as inactive violations. These are kept track of to allow the user to easily switch the rating set used for reporting violations from one set to another and see the results immediately, without having to re-run the entire contingency set to determine the violations for the new rating set. Choosing to include the inactive violations when saving an auxiliary file maintains this flexibility when the contingency definitions and results are read into a case from an auxiliary file. You can also choose for the identifiers used in the file to be either the bus numbers or the bus name and nominal kV voltage.  
        Note: For comparing two lists of contingency results, you MUST save the contingency results with each of the two auxiliary files being compared.
      - Click **OK** to save the contingencies and the results to the auxiliary file specified.
  - Once you have two different lists of contingency results (at least one of the lists must be saved in an auxiliary file), right-click on the contingency list and choose **Compare Two Lists of Contingency Results** or choose **Other \> Compare Two Lists of Contingency Results**. This will bring up a dialog on which you have to specify the Contingency Lists you are interested in comparing. You must specify the **Controlling Contingency List** and the **Comparison Contingency List**. The definitions of these two lists are found below.
  - Click on the **Browse** buttons to specify the two Contingency Lists you would like to compare. You can also choose to use the presently open Contingency List as either the Controlling Contingency List or the Comparison Contingency List.

Controlling Contingency List:

The list that controls what is displayed on the dialog. Only contingencies that are defined in this list will be displayed on the form. Only violations that occur for contingencies in this list will appear in the Violations List for each contingency.

Comparison Contingency List:

This is the list to which the Controlling Contingencies will be compared. Comparisons will occur for those contingencies in the lists that have the same **CONTINGENCY NAME**. Note that contingencies in the Comparison list whose **CONTINGENCY NAME** does not match one of those in the Controlling list will not be displayed. Also, violations which occur in a specific Comparison contingency that do not occur in the respective Controlling contingency will not be displayed.

Example:

A user has a power system case and a list of contingencies. The user runs contingency analysis on this system for this list of contingencies. The results are saved in a file called comparison.aux. The user now changes the system state, possibly adding in a 500 MW transaction between two areas. The contingency analysis is run on this new state of the system for the list of contingencies. The results are saved in a file called controlling.aux. You should define the contingency results you are more interested in viewing as the Controlling List because this list determines what is shown on the dialog. In this case, we are more interested in seeing the violations caused when the transaction is in place, so that list is defined as the Controlling List.

The comparison of the two sets of contingencies is now done by right-clicking and choosing **Compare Two Contingency List Results**. The file controlling.aux is set as the **Controlling List** and comparison.aux as the **Comparison List**.

  - After clicking **OK** on the dialog, the contingency lists will be read from the specified files or from the presently open list. After Simulator has completed reading these files, a prompt will appear which asks, "**Would you like to set the dialog with default columns for comparing contingency lists?**"**.** It is recommended that you choose **YES** so that the case information displays on the Contingency Dialog will automatically be set to show fields that will help you compare the two lists of contingencies. For information on the default fields used when comparing contingencies see [Comparing Contingencies List Displays](#comparing-contingencies-list-displays).

---

<a id="comparing-contingencies-list-displays"></a>

## Comparing Contingencies List Displays

*Source: [`Content/MainDocumentation_HTML/Comparing_Contingencies_List_Displays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Comparing_Contingencies_List_Displays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When comparing two sets of contingency results, there are several additional default fields added to several list displays which help you compare the results. These fields are described below for the various list displays.

Contingencies Records on [Contingencies Tab](22-contingency-analysis-options.md#contingencies-tab)

Violations

The total number of violations for this contingency under the Controlling List.

Comp Violations

The total number of violations for this contingency under the Comparison List.

New Violations

The number of violations which occur in the Controlling List which do not occur in the Comparison List.

Max Branch % (Max Interface %)

The highest branch (interface) violation caused by this contingency in the Controlling List.

Comp Max Branch % (Comp Max Interface %)

The highest branch (interface) violation caused by this contingency in the Comparison List.

Worst Branch Violation (Worst Interface Violation)

This is the maximum of the following two values: \[**Worst Increase Violation**\] and \[**Worst New Violation - 100%**\]

Min Volt (Max Volt)

The worst violation in the controlling list.

Comp Min Volt (Comp Max Volt)

The worst violation in the comparison list.

Worst LowV Violation (Worst HighV Violation)

The worst new violation.

[Contingency Violations Display](22-contingency-analysis-options.md#contingency-violations-display) on [Contingencies Tab](22-contingency-analysis-options.md#contingencies-tab) and Contingency Violations on the [View Results By Element Page](#view-results-by-element)

When Viewing Lines/Transformers, Buses, Interfaces, or Nomogram Interfaces

Value

The value of the violation under the controlling list.

Comp Value

The value of the violation under the comparison list.

Diff Value

The difference between **Value** and **Comp Value**

Limit

The limit of the element in the controlling list.

Comp Limit

The limit of the element in the comparison list.

Diff Limit

The difference between **Limit** and **Comp Limit**

Percent

The percent violation in the controlling list.

Comp Percent

The percent violation in the comparison list.

Diff Percent

The difference between **Percent** and **Comp Percent**

Contingency Violations on the [View Results By Element Page](#view-results-by-element) When Viewing Custom Monitors

Value

The value of the monitor under the controlling list.

Reference Value

The value of the monitor in the reference state under the controlling list.

Change Value

The difference between **Value** and **Reference Value**

Comp Value

The value of the monitor under the comparison list.

Diff Value

The difference between **Value** and **Comp Value**

Line/Transformer (Interface) Records on the [View Results By Element Page](#view-results-by-element)

Violations

This shows the number of branch (interface) violations which occurred in the Controlling List

New Violations

This shows the number of branch (interface) violations which occurred in the Controlling List, but did not occur in the Comparison List.

Max % Loading Cont.

The worst branch (interface) violation in the controlling list.

Max % Ld Cont Comp

The worst branch (interface) violation which occurred in the comparison list.

Worst Increased Violation

The worst increase in a branch (interface) violation from the comparison list to the controlling list.

Bus Records on the [View Results By Element Page](#view-results-by-element)

Violations

This shows the number of violations which occurred in the Controlling List

New Violations

This shows the number of violations which occurred in the Controlling List, but did not occur in the Comparison List.

Max Voltage Cont.

The worst high voltage violation in the controlling list.

Max Voltage Cont Comp

The worst high voltage violation which occurred in the comparison list.

Worst Max Volt CTG Change

The worst increase in a high voltage violation.

Min Voltage Cont.

The worst low voltage violation in the controlling list.

Min Voltage Cont Comp

The worst low voltage violation which occurred in the comparison list.

Worst Min Volt CTG Change

The worst decrease in a low voltage violation.

Nomogram Interfaces Records on the [View Results By Element Page](#view-results-by-element)

Violations

This shows the number of violations which occurred in the controlling list.

Max % Loading Cont.

The worst nomogram interface violation in the controlling list.

Custom Monitor Records on the [View Results By Element Page](#view-results-by-element)

No changes.
