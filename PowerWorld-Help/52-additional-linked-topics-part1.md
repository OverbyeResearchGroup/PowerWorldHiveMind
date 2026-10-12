---
title: "Additional Linked Topics (Part 1 of 3)"
part: "Reference"
chapter_file: "52-additional-linked-topics-part1.md"
topics: 41
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Additional Linked Topics (Part 1 of 3)

Topics reachable from links inside the manual but not listed in the help system's table of contents.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (41)**

- [Auto Insert Transient Contingencies Dialog](#auto-insert-transient-contingencies-dialog)
- [Auto Insert Transient Contingencies Dialog](#auto-insert-transient-contingencies-dialog-1)
- [Auto Insert Transient Contingencies Dialog](#auto-insert-transient-contingencies-dialog-2)
- [Background Rectangles on Onelines](#background-rectangles-on-onelines)
- [ChangeParameters Function](#changeparameters-function)
- [ChangeParameters Function (version 9)](#changeparameters-function-version-9)
- [CloseCase Function (version 9)](#closecase-function-version-9)
- [Contact Information](#contact-information)
- [Contingencies Tab: Create Stuck Breaker Contingencies](#contingencies-tab-create-stuck-breaker-contingencies)
- [Contingency Combination Analysis: Results Tab](#contingency-combination-analysis-results-tab)
- [Contingency Definition Dialog](#contingency-definition-dialog)
- [Contingency Options: Legacy Definitions](#contingency-options-legacy-definitions)
- [DC Line Field Options Dialog](#dc-line-field-options-dialog)
- [Device Derived Status Version 19](#device-derived-status-version-19)
- [Driving Point Impedances](#driving-point-impedances)
- [Fault Analysis Dialog: Fault Definitions](#fault-analysis-dialog-fault-definitions)
- [Fault Analysis Dialog: Single Fault](#fault-analysis-dialog-single-fault)
- [Find Parallel AC Branches](#find-parallel-ac-branches)
- [Find Text in Oneline Dialog](#find-text-in-oneline-dialog)
- [Generator Economic Merit Order and Merit Order Close Dispatch](#generator-economic-merit-order-and-merit-order-close-dispatch)
- [GetParameters Function (version 9)](#getparameters-function-version-9)
- [GIC Analysis Non Uniform Field Data](#gic-analysis-non-uniform-field-data)
- [GIC Analysis Sensitivity Analysis](#gic-analysis-sensitivity-analysis)
- [Including Simulator Automation Server Functions (version 9)](#including-simulator-automation-server-functions-version-9)
- [ListOfDevices Function (version 9)](#listofdevices-function-version-9)
- [LoadContingencies Function (version 9)](#loadcontingencies-function-version-9)
- [Make-Up Power Sources](#make-up-power-sources)
- [Multi-Section Line Field Options](#multi-section-line-field-options)
- [Oneline Viewer](#oneline-viewer)
- [OpenCase Function (version 9)](#opencase-function-version-9)
- [PowerWorld Object Variables (Version 9)](#powerworld-object-variables-version-9)
- [ProcessAuxFile Function (version 9)](#processauxfile-function-version-9)
- [Quick Filter](#quick-filter)
- [Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions](#relationship-between-contingencies-model-conditions-model-filters-and-model-expressions)
- [Remedial Action Definition Dialog](#remedial-action-definition-dialog)
- [RunScriptCommand Function (version 9)](#runscriptcommand-function-version-9)
- [SaveCase Function (version 9)](#savecase-function-version-9)
- [Saving Case Information Display Contents As HTML Tables](#saving-case-information-display-contents-as-html-tables)
- [SendToExcel Function (version 9)](#sendtoexcel-function-version-9)
- [Simulator Automation Server (version 9)](#simulator-automation-server-version-9)
- [Simulator Automation Server Functions (version 9)](#simulator-automation-server-functions-version-9)

---

<a id="auto-insert-transient-contingencies-dialog"></a>

## Auto Insert Transient Contingencies Dialog

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_Transient_Contingencies_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_Transient_Contingencies_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows you to automatically generate a transient contingency list containing branch faults, bus faults, or generator opens. To accomplish this, click the **Auto Insert** button along the bottom of the [Transient Stability Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). This opens the **Auto Insertion of Contingencies Dialog**.

When automatically inserting contingencies, you must specify the type, options and naming conventions you want for the new contingencies. You must also specify whether to delete or retain existing contingencies.

The options for auto inserting transient stability contingencies work identically to the options for auto inserting power flow contingencies. These are describe in detail in the [Auto Insert Contingencies](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) help topic, so please see that topic for details on the many options for choosing which devices to auto insert contingencies for. The only differences with the transient stability contingency auto insertion is that additional fields must be specified as follows.

Event Time

This is the time in seconds at which the first contingency events will occur (typically a fault).

Event Duration

This is the time delay (after **Event Time**) in seconds at which subsequent contingency events will occur (typically opening devices).

Location %

For branch faults, this is the percent distance along the line at which the fault occurs. Values must be specified between 0 and 50%.

Self Clearing Fault Added in Version 20, build on May 14, 2018

Check this box for Lines, Transformer and Buses so that the fault applied will be marked as a Self Clearing Fault. This means that once the fault location is isolated then the fault will automatically clear itself. See [Transient Stability Contingency Element Dialog](37-transient-stability-analysis-dialog-part1.md#transient-contigency-element-dialog) for more information on self clearing faults.

Self Clear Open Devices Added in Version 20, build on May 14, 2018

When choosing to auto-insert self clearing faults, if this box is not checked then the additional actions to open devices to isolate the fault will not be used. Check this box to also force the opening device actions to be inserted after the Event Duration as well.

Depending on the type of contingency being automatically inserted, contingencies will be created with appropriate contingency events as follows.

Single Transmission Line

Simulator automatically creates <span class="underline">two</span> contingencies that each have three events. A fault occurs at the **Event Time**, and then two events of OpenFrom and OpenTo are applied after the **Event Duration**. The two contingencies only differ by the **Fault Location**. The user specifies a **Fault Location** in percentage (value between 0 and 50) and then two contingencies are created with **Fault Location** and "100 – **Fault Location**". If a **Fault Location** of 49.5 or higher is specified, then only one contingency with a **Fault Location** of 50% is created.

Single Transformer

Simulator automatically creates <span class="underline">two</span> contingencies which each have three events similar to what is done for a Single Transmission Line. The **Fault Location** however is always at the two terminals of the transformer.

Single Bus

Simulator automatically creates one contingency which has two events. A fault occurs at the bus at the **Event Time** and then the bus is opened (all lines attached to the bus are opened) after the **Event Duration**.

Single Generator

Simulator automatically creates one contingency which has one event. The generator is opened at the **Event Time**.

---

<a id="auto-insert-transient-contingencies-dialog-1"></a>

## Auto Insert Transient Contingencies Dialog

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_Critical_Clearing_Time_Calculator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_Critical_Clearing_Time_Calculator.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows you to automatically generate critical clearing time contingencies. The actual calculation of the critical clearing time values is done as part of the transient stability contingency analysis during the transient stability run. In order to get the Critical Clearing Time, the multiple contingency mode has to be used. A [Transient Limit Monitor](37-transient-stability-analysis-dialog-part3.md#defining-transient-limit-monitors) has to be active or a [Result Analyzer Time Window](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window) has to be defined. When a result analyzer time window is defined the options for **Automatically analyze time windows and keep Signal Violations after running a transient stability simulation** has to be checked and also the both **Include in Calculation** options has to be checked. The critical clearing time is calculated by changing the clearing time of the fault until there is a [transient limit monitor violation](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors-violations) or a [result analyzer signal violation](37-transient-stability-analysis-dialog-part2.md#result-analysis-signal-violation). To accomplish this, click the **Critical Clearing Time Calculator...** button along the bottom of the [Transient Stability Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). This opens the **Critical Clearing Time Calculator Dialog**.

![Transient Stability Critical Clearing Time Calculator Dialog](images/Transient_Stability_Critical_Clearing_Time_Calculator_Dialog.gif)

The object name is included in the contingency name.

Define Branch Filter

This is a filter to set the branches to which a fault is going to be added (solid three phase fault at 0 percent near). The **Insert Branch Contingencies** check is check of these contingencies are going to be added, unchecked to not add them.

Define Bus Filter

This is a filter to set the Bus to which a fault is going to be added (solid three phase fault at 0 percent near). The **Insert Bus Contingencie**s check is check of these contingencies are going to be added, unchecked to not add them

Clear fault action to use

Set the action to clear the fault by either clearing the fault or opening both ends of the branch if a branch fault was created. The initial time of the fault clearing event is 1/4 cycle after the fault event.

Contingency run time (s)

Set the end time of the critical clearing time contingency.

Fault start time (s)

Set the start time of the critical clearing time contingency.

In order to work and calculate the critical clearing time the fields '**Critical Clearing Time Calculate**', '**Critical Clearing Time Max Fault Duration**' and **'Critical Clearing Time Result**' should be added and set correctly in for each contingency in the Transient Contingency Elements table:

![Transient Stability CCT Fields](images/Transient_Stability_CCT_Fields.gif)

The '**Critical Clearing Time Calculate**' field indicates that the critical clearing time should be calculated for the contingency element. This should be the fault clearing contingency element and there should be only one 'Critical Clearing Time Calculate' field per contingency. Right now, this isn't explicitly enforced, but we will only calculate the critical clearing time for the last '**Critical Clearing Time Calculate**' element. To calculate the Critical Clearing Time per contingency you will need to set this field to YES in the Transient Contingency Elements Table.

The '**Critical Clearing Time Max Fault Duration**' is used to stop the critical clearing time calculation if the fault duration exceeds the input value.

The '**Critical Clearing Time Result**' field is used to hold the critical clearing time result instead of changing the time of the clearing event.

**Note:** These fields are available for any contingency element, so it is not necessary to use the critical clearing time dialog to create critical clearing time contingencies. You can set the flag on the fault clearing action to convert a standard contingency to a critical clearing time calculation.

---

<a id="auto-insert-transient-contingencies-dialog-2"></a>

## Auto Insert Transient Contingencies Dialog

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_DistRelay.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_DistRelay.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows you to automatically generate [DistRelay](44-ts-models-branch-and-shunt-part1.md#distrelay) models into the branches.

![Auto Insert DistRelay Models](images/Auto_Insert_DistRelay_Models.gif)

Filter Name

This is an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) to set the branches to which DistRelay models are going to be added.

Zone 1 Reach (%)

This sets the Zone 1 impedance reach in percentage (%) for the DistRelay models added with this dialog.

Add Relay at From Bus

Check to add the DistRelay model at the **From Bus** of the branch.

Add Relay at To Bus

Check to add the DistRelay model at the **To Bus** of the branch.

Enable Transfer Trip

Check to set the Transfer Trip for the DistRelay.

Zone 1 Shape

Select the desired Zone 1 Shape for the distance impedance relay.

The options are:

0 - Circle, lens, or tomato

1 - Rectangle

2 - Reactance Distance

3 - Impedance Distance

---

<a id="background-rectangles-on-onelines"></a>

## Background Rectangles on Onelines

*Source: [`Content/MainDocumentation_HTML/background_triangles_on_onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/background_triangles_on_onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of a oneline diagram can display triangles among other items. ****

Edit Mode

To add a new triangle, first go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Insert \> Background Triangle** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Position the cursor where you would like to place the upper left-hand corner of the rectangle and click with the left mouse button. A triangle having the default size is inserted. Drag the triangle's resizing handles to resize/reshape the rectangle.

To resize or reshape an existing triangle, click on it to select it. The resizing handles will appear, which you can then drag to reshape or resize the rectangle.

To change the color, line thickness or fill color of the rectangle, first select the triangle by clicking on it on the diagram, and then use the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, or right-click on it and select **Format Background Triangle** from the local menu.

---

<a id="changeparameters-function"></a>

## ChangeParameters Function

*Source: [`Content/MainDocumentation_HTML/ChangeParameters_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParameters_Function.htm)*

The ChangeParameters function has been replaced by the [ChangeParametersSingleElement](34-simauto-functions.md#changeparameterssingleelement) function. ChangeParameters can still be called as before, but will now just automatically call ChangeParametersSingleElement, and pass on the parameters to that function.

Unlike the script SetData and CreateData commands, SimAuto does not have any explicit functions to create elements. Instead this can be done using the ChangeParameters functions by making use of the [CreateIfNotFound](33-simauto-overview-and-setup.md#createifnotfound) SimAuto property. Set CreateIfNotFound = True if objects that are updated through the ChangeParameters functions should be created if they do not already exist in the case. Objects that already exist will be updated. Set CreateIfNotFound = False to not create new objects and only update existing ones. The CreateIfNotFound property is global, once it is set to True this applies to all future ChangeParameters calls.

**Function Prototype**

**ChangeParameters(ObjectType, ParamList, Values)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed.

**ParamList : Variant **A variant array storing strings (COM Type BSTR). This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified.

**Values : Variant **A variant array storing variants. This array can store any type of information (integer, string, etc.) in each array position. A value should be passed for each field variable given in the ParamList. The Values array must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) values for the specific device, or the device cannot be identified.

---

<a id="changeparameters-function-version-9"></a>

## ChangeParameters Function (version 9)

*Source: [`Content/MainDocumentation_HTML/ChangeParameters_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ChangeParameters_Function_v9.htm)*

The ChangeParameters function allows you to set a list of parameters for a specific object in a case loaded into the [Simulator Automation Server](#simulator-automation-server-version-9). In addition to changing parameters for objects, this function can also be used to set options for some of the Simulator tools, such as [ATC](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) and [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview). This function is identical in setup to the [GetParameters](#getparameters-function-version-9) function, with the exception that the Values array must contain a value for each field variable given in the ParamList array.

**ChangeParameters(ObjectType, ParamList, Values, EString)**

Parameter Definitions

**ObjectType : String **The type of object for which parameters are being changed. No default.

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](#powerworld-object-variables-version-9). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified. No Default.

**Values : Variant **A variant array storing variants. This array can store any type of information (integer, string, etc.) in each array position. A value should be passed for each field variable given in the ParamList. The Values array must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) values for the specific device, or the device cannot be identified. No Default.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

Example

**ChangeParameters("gen", \[pwBusNum, pwGenID, pwGenAGCAble\], \[1, "1", "Yes"\], EString)**

This function call will change the AGC Status of bus number one, generator ID number 1, to "Yes", meaning the generator will be included in AGC if it's area is on AGC control.

---

<a id="closecase-function-version-9"></a>

## CloseCase Function (version 9)

*Source: [`Content/MainDocumentation_HTML/CloseCase_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/CloseCase_Function_v9.htm)*

The CloseCase function is used to close a load flow case loaded in the [Simulator Automation Server](#simulator-automation-server-version-9). This function should be called at some point after the [OpenCase](#opencase-function-version-9) function. An error will be returned through the EString parameter if an error occurred while trying to close the case.

**CloseCase(EString)**

Parameter Definitions

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

---

<a id="contact-information"></a>

## Contact Information

*Source: [`Content/MainDocumentation_HTML/Contact_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contact_Information.htm)*

PowerWorld Corporation

2001 South First Street

Champaign, IL 61820

Phone: (217) 384-6330

Fax: (217) 384-6329

Toll Free: (877) 748-7840 - U.S. and Canada only

General Information: <info@powerworld.com>

Technical Support: <support@powerworld.com>

Sales: <sales@powerworld.com>

[www.powerworld.com](https://www.powerworld.com/WebHelp/)

---

<a id="contingencies-tab-create-stuck-breaker-contingencies"></a>

## Contingencies Tab: Create Stuck Breaker Contingencies

*Source: [`Content/MainDocumentation_HTML/Contingency_Create_Stuck_Breaker_CTGs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Create_Stuck_Breaker_CTGs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Create Stuck Breaker Contingencies** option can be found on the [Contingencies tab](22-contingency-analysis-options.md#contingencies-tab) of the Contingency Analysis dialog under the **Insert Special** local menu options. The option allows the creation of new contingencies from contingencies that have explicit breaker outages defined. New contingencies will be created by treating each breaker as stuck in turn. The new contingencies will be comprised of all existing elements, minus the stuck breaker outage, plus open actions for breakers that are identified to isolate the stuck breakers. New contingencies will inherit the same value for the **Skip** field from the contingency from which they were created. Only branches with Branch Device Type of *Breaker* will be considered in determining the stuck breakers. Selecting this option will open a dialog with the following options:

Contingency Naming Convention

The options in this section will determine the format of the name of new contingencies. Contingencies will be named in the format *Prefix\_Contingency Label\_Branch Field\_Suffix*.

Prefix

String used as the prefix of the new contingency name. If this is not specified, the underscore following the *Prefix* in the contingency name format will be omitted.

Branch Field

Field whose value will be used in the naming of the new contingency. The branch used to evaluate the field is the stuck breaker. If this is not specified, the underscore following *Branch Field* in the contingency name format will be omitted.

Suffix

String used as the prefix of the new contingency name. The default is "STK".

Include Contingency Label

Check this box to use the name of the existing contingency as part of the new contingency. If this is not checked, the underscore following *Contingency Label* in the contingency name format will be omitted.

Contingency Action Comment

The options in this section will determine the format of the comment of new contingency actions. Comments will be in the format *Prefix\_Branch Field\_Suffix*.

Prefix

String used as the prefix of the new contingency action comment. If this is not specified the underscore following the *Prefix* in the contingency comment format will be omitted.

Branch Field

Field whose value will be used in the comment of a new contingency action. The branch used to evaluate the field is the breaker in the new contingency action. If this is not specified, the underscore following *Branch Field* in the contingency action comment format will be omitted.

Suffix

String used as the suffix of the new contingency action comment.

Contingency Filter

Define Filter

Click this button to specify an Advanced Filter or Device Filter that is applied to contingencies. Only contingencies meeting this filter will have new contingencies created for stuck breakers. If this is not specified, all contingencies will be processed.

Allow New Contingencies with Same Actions as Existing Contingencies

If this box is checked, contingencies with the same actions as existing or newly created contingencies will be allowed.

Create Stuck Breaker Contingencies

Click this button to create the new contingencies. The contingency list will be permanently modified.

Close

Click this button to close the dialog without creating any new contingencies.

---

<a id="contingency-combination-analysis-results-tab"></a>

## Contingency Combination Analysis: Results Tab

*Source: [`Content/MainDocumentation_HTML/Contingency_Combo_Results_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Combo_Results_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results tab of the [Contingency Combination Analysis dialog](25-ctg-combo-analysis.md#ctg-combo-contingency-analysis-dialog) contains many options for viewing the results of a contingency analysis run.

The Choose What Results To Show lets the user see results by different options:

  - Contingency Violations List : get a combined list of all contingency/limiting element pairs that result in a violation. This option has a special drop down menu that let filter the Violation CTG by element. The filters are All, Bus, Branch , Interface, Bus Pair Custom, Transient and Island.
  - [What Occurred](23-contingency-analysis-running-and-results.md#what-occurred) : Get a list of actions that occurred during the selected contingency. This is especially useful for identifying those actions conditional on Model Criteria being applied. It is also helpful when using the special [Open with Breakers](24-contingency-element-dialog.md#contingency-element-open-breakers) contingency actions because the list will indicate which breakers need to be opened to isolate the devices.
  - Injection Sensitivities: Provides access to results based on Injection Sensitivities.
  - Select Objects to Show: Get a list of objects to show by Contingency Primary, Contingency, Bus, Branch, Interface or Bus Pair.

The Primary Contingency To Show lets the user see results by Primary Contingency. The options to filter the results by primary contingency are All, Selected, Single or by Filter.

The Contingency To Show lets the user see results by Contingency. The options to filter the results by contingency are All, Selected, Single or by Filter.

---

<a id="contingency-definition-dialog"></a>

## Contingency Definition Dialog

*Source: [`Content/MainDocumentation_HTML/Contingency_Combo_Definition_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Combo_Definition_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Definition Dialog (shown below) serves as an information source for displaying the Contingency Element (or Elements) associated with individual contingencies defined in the case. You can use the Contingency Definition Dialog to scroll through the list of elements, to view and modify their definitions, to insert new elements in a contingency or to delete a contingency. You may access this dialog by choosing either **Show Dialog** or **Insert** from the local menu of the Primary Contingencies Display.

After making changes, click **OK** to save your changes and close the dialog. Click **Cancel** to close the dialog without saving your changes. Click **Save** to save your changes (including the addition of a new contingency) without closing the dialog (this allows you to keep working with the dialog). Click **Delete** to remove the selected contingency from the contingency list.

![CTG Combo Definition Dialog](images/CTG_Combo_Definition_Dialog.jpg)

Contingency Primary Actions Elements Dialog

The Contingency Primary Actions Elements Dialog has the following controls that are available regardless of the tab that is currently selected:

Contingency Primary Label 

Identifies the name of the currently displayed primary contingency.

Add New

Click the **Add New** button to add a new primary contingency to the contingency list for the case. You will be prompted to enter a unique name for the new contingency. After naming the new contingency, the name appears in the Contingency Label and you can insert new elements in the contingency definition.

Rename 

Allows you to rename the selected primary contingency.

Find

Opens a dialog that will allow the use of [advanced search methods](04-model-explorer-and-case-information-part3.md#find-dialog-basics) for finding a particular primary contingency.

Definition Tab

Insert New Element

Click this button to add a new element to the contingency. This will open the [Contingency Combination Element Dialog](25-ctg-combo-analysis.md#contingency-combination-element-dialog), used to define the Action, Model Criteria and Comment associated with the element. When you return to the Contingency Definition Dialog, the display will contain the newly inserted element.

Clear All

Removes all elements from the contingency definition. The Contingency Elements Table will then appear blank, indicating that the contingency involves no associated actions.

Definitions Display

The Primary Contingency Definitions Display lists the elements assigned to the selected contingency. Select **Insert** from the local menu or click on the **Insert New Element** button to add elements to the contingency. Right-click on a specific element in the display and select **Delete** from the local menu to remove the element from the contingency.

Define Solution Options

Click this button to open the [Contingency Solution Options Dialog](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options), used to define specific power flow solutions options for use under the selected contingency.

Use Specific Solution Options

Check this box to enable the use of Contingency Specific Solution Options (see Define Solution Options above).

Ignore ALL contingency specific solution options

If checked, all contingency specific options, either defined individually for the specific contingency or defined globally in the contingency options for all contingencies, are ignored. The [solution options](10-power-flow-solution-and-options-part1.md#simulator-options) as saved with the case will be used.

Include Remedial Actions Added in Version 20

Check this box to include Remedial Actions and Global Actions with this contingency.

Skip

Check this box to skip the Primary Contingency from the analysis when pressing Run in the [Contingency Combination Analysis Dialog](25-ctg-combo-analysis.md#ctg-combo-contingency-analysis-dialog).

Custom Tab

The [Custom page](01-getting-started.md#memo-display) of the dialog contains two sections: custom fields and memo.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the contingency. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the contingency. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

---

<a id="contingency-options-legacy-definitions"></a>

## Contingency Options: Legacy Definitions

*Source: [`Content/MainDocumentation_HTML/Contingency_Options_LegacyDefinitions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Options_LegacyDefinitions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are all available on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under the [Contingency Options tab](22-contingency-analysis-options.md#options-tab) under the Legacy Definitions grouping. Legacy objects used with contingency analysis are strongly discouraged. They are still supported for older data that has not been converted to newer object structures that are more appropriate for the same modeling purpose, but they may no longer be supported in future versions of Simulator. It is highly encouraged that these legacy objects be converted. Global Actions can be converted to Remedial Actions. Contingency Blocks can be replaced with Injection Groups or Interfaces. The individual topics on these objects describe how to convert them.

Contingency Blocks

A [contingency block](21-contingency-analysis-overview-and-records.md#contingency-blocks) stores a list of contingency actions and has a name (or label) associated with it. A contingency block can then be called from a contingency record. This allows you to define a block of common actions you wish to have processed during several different contingencies, and then assign the block to each contingency instead of constantly redefining the same actions for each contingency. The **Contingency Block Elements** contains a combined list of all the contingency block elements for all contingency blocks.

Contingency Block Elements

Contains a combined list of all of the contingency block elements for all Contingency Block records.

Contingency Global Actions

A [global action](21-contingency-analysis-overview-and-records.md#global-actions) is an action that will automatically be processed as part of EACH contingency unless an Inclusion Filter is specified that allows defining with which contingencies the action will be included. Thus, if you have actions that are to be performed in every single contingency you define, you can insert it once in the global actions list, and Simulator will automatically use the defined action for every contingency it processes.

---

<a id="dc-line-field-options-dialog"></a>

## DC Line Field Options Dialog

*Source: [`Content/MainDocumentation_HTML/DC_Line_Field_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Line_Field_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

DC line field display objects are used to show different values associated with DC lines on onelines.

This dialog can be opened by right-clicking on a dc line display field and choosing to open the **DC Line Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a dc line display field.

This dialog is used to view and modify the parameters associated with these fields.

Find…

If you do not know the exact line identifiers you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Near Bus Number

Bus associated with the near end of the object. All fields display values calculated at the *near bus* end. When inserting fields graphically, this field is automatically set to the closest bus on the oneline.

Far Bus Number

Bus associated with the *far end* of the object.

Circuit

Two-character identifier used to distinguish between multiple dc lines joining the same two buses. Default is ‘1’.

Total Digits in Fields

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Delta Per Mouse Click

This option is not currently used with any of the available fields.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Rotation Angle in Degrees

The angle at which the text will appear on the diagram.

Anchored

If checked, the line analog is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated line.

Include Suffix

If the *Include Suffix* checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of line field to show. The following choices are available:

Control Mode

Control model for the DC line; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Setpoint Magnitude

Set point magnitude for the DC line; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Setpoint Location

Set point location for the DC line; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Set Voltage

Set voltage for the DC line; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

MW Flow 

MW flow into the DC line at the near bus; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Mvar Flow 

Mvar flow into the DC line at the near bus; see [DC Transmission Line dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Select a Field 

Choose from any of the available dc line fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Select **OK** to save changes and close the dialog or **Cancel** to close the dialog without saving your changes.

---

<a id="device-derived-status-version-19"></a>

## Device Derived Status Version 19

*Source: [`Content/MainDocumentation_HTML/Device_Derived_Status_version19.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Device_Derived_Status_version19.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the determination of derived status as it was in version 19. To see derived status as it as of version 20 click [here](35-integrated-topology-processing.md#device-derived-status).

Differences exist between planning models and full-topology EMS models when it comes to determining if a device is energized and what the status is of the device.

With planning software and bus-branch models, two distinct fields exist: **Status** and **Online**. The **Status** field is an explicit field that exists to determine if a device is open or closed. This is needed because breakers are not modeled. The **Online** field indicates if the device is actually energized which will be affected by the status of branches.

With full-topology EMS models, breaker or disconnect status determines the status of other devices, i.e. whether or not they are energized. No explicit status field exists for other devices like generators, loads, lines, transformers, etc. Typically when using a full-topology model in Simulator, the **Status** of non-switching devices (generators, loads, lines, etc.) will be set to *Closed*. A hybrid model with only parts of the system modeled with breaker detail can still use the **Status** field for non-switching devices.

The actual status of a device can be confusing, especially for those accustomed to a planning model. To eliminate confusion, the **Derived Status** field will be used to indicate the status with which planning model users are accustomed.

**Derived Status** is determined by the following:

  - **Status** = *Open* --\> **Derived Status** = *Open*
  - Else
      - Search starting at the device terminals traverse branches with **Status** = *Closed* looking for closed breakers, generation, or load (switched shunts are excluded here)
          - If search successful at all terminals --\> **Derived Status** = *Closed*
          - Else If search successful at FROM end only (if two terminal device) --\> **Derived Status** = *Open To*
          - Else If search successful at TO end only (if two terminal device) --\> **Derived Status** = *Open From*
          - Else --\> **Derived Status** = *Open*
  - Whether or not a device is **Online** has no impact on the **Derived Status**
  - For switching devices (Breaker, Load Break Disconnect, Disconnect, Fuse, and Ground Disconnect) **Derived Status** = **Status**

The following provides examples of how the **Derived Status** field is set for various breaker settings:

![Derived Status 1 653x368](images/Derived_Status_1_653x368.gif)

**Derived Online** is another field that is available for branches. This combines the **Online** field and the **Derived Status** field.

Derived Online is determined by the following:

  - **Online** = *NO* --\> **Derived Online** = *Open*
  - Else
      - **Derived Online** = **Derived Status**

When determining if a branch end is *CLOSED* as part of the **Derived Status** check, several conditions must be met:

  - A closed circuit breaker must be found. A breaker is a branch whose **Branch Device Type** = *Breaker*.
  - Beyond the closed breaker there must be a device of consequence such as:
      - Closed branch (this is any **Branch Device Type**)
      - Generator
      - Load
      - Switched shunts are not included in this check
  - Breakers directly in parallel with a Line, Transformer, or Series Capacitor are excluded

The following are examples of **Derived Status** = *Closed* lines:

![Derived Status 2 version19](images/Derived_Status_2_version19.gif)

The following are examples of **Derived Status** = *Open To* lines:

![Derived Status 3 version19](images/Derived_Status_3_version19.gif)

---

<a id="driving-point-impedances"></a>

## Driving Point Impedances

*Source: [`Content/MainDocumentation_HTML/Driving_Point_Impedances.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Driving_Point_Impedances.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in version 20

This tool is found on the Tools ribbon tab in the [Other ribbon group](02-simulator-ribbon.md#other-tools-ribbon-group) under **Connections \> Driving Point Impedances**or in the [Run Mode ribbon group](02-simulator-ribbon.md#run-mode-ribbon-group) under **Sensitivities \> Driving Point Impedances**.

The driving point impedance for a bus is the impedance looking from that bus out into the system.

Model Type to Use

This determines the Ybus that is used for the calculations. The following options are available:

Transient Stability without Bus Local Shunts

Use the Ybus built from transient stability data. This includes the internal impedances of generators and loads (induction motors). Local impedances at buses including bus shunts, switched shunts, internal impedances of generators, internal impedances of induction motors, etc. are subtracted out of the Ybus for the bus for which the driving point impedance is being calculated. This is similar to what is done in the SMIB two bus equivalent calculations, and is the most appropriate option to choose.

Transient stability data should be loaded prior to running this calculation.

Transient Stability Including Bus Local Shunts

Use the Ybus built from transient stability data but do not subtract out any local shunt impedances as is done in the **without Bus Local Shunts** option.

Transient stability data should be loaded prior to running this calculation.

Power Flow

Use the Ybus built from power flow data only. This depends on the system slack bus and does not include the internal impedances of generators.

Calculate Driving Point Impedances

Click this button to implement the calculations. Any errors will appear in the **Calculation Result** box.

Results

The table at the bottom of the dialog will contain the **Driving Point Impedance X** and **R** values as well as **Mag(nitude)** and **Degrees** at each bus in the case.

---

<a id="fault-analysis-dialog-fault-definitions"></a>

## Fault Analysis Dialog: Fault Definitions

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Dialog_Fault_Definitions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Dialog_Fault_Definitions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This page of the **Fault Analysis Dialog** allows for defining multiple fault points to be sequentially processed, with the fault current and Thevenin impedance calculated for each fault point, and for up to two different fault types (default is three phase balanced and single line to ground.)

To manually create a list of fault points, right-click on the table and choose **Insert** from the pop-up menu. From this method, you can only choose one bus or branch at a time to insert. Alternatively, you can also use the **Auto Insert** button at the bottom of the dialog to use selection criteria to automatically create the fault points list. When the faults are run using the **Run Faults** button, the results will be calculated and displayed for each fault point within this table.

---

<a id="fault-analysis-dialog-single-fault"></a>

## Fault Analysis Dialog: Single Fault

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Dialog_Single_Fault.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Dialog_Single_Fault.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Single Fault** page is where the type and location of a single detailed fault are specified, and where the results of the detailed fault analysis can be seen in tabular format.

Fault Location

Choose to perform the fault at a bus location, or at a point somewhere on a line. If Bus Fault is selected, the only information needed is the bus number, which needs to be entered in the Fault Bus field. If an in-line fault is desired, the from and to bus numbers, circuit ID, and location of the fault (entered in percent of total line length, measured from the From Bus) will need to be given. Selecting the **Fault…** option from the bus or line local menus will automatically set up the Fault Location fields.

Fault Type

Choose from one of four types of fault to calculate at the fault location:

**Single Line - to - Ground **Computes a single phase line - to - ground fault using a user defined ground fault impedance. The phase evaluated is always referenced as phase A.

**Line - to - Line **Computes a line - to - line fault, assuming an impedance of 999 + j999 to ground. Phases B and C are always referenced as the faulted phases.

**3 Phase Balanced **Balanced three-phase line fault - to - ground using a user-defined ground fault impedance.

**Double Line - to - Ground **Computes a line - to - line - to - ground fault, using a user defined ground fault impedance.

Fault Current

Displays the magnitude and angle of the current at the fault location during the fault. The units of the fault current can be set to either per unit (p.u.) or Amps.

Subtransient Phase Current

Displays the magnitude and angle of the subtransient phase current A, B and C at the fault location during the fault. The units of the subtransient phase current can be set to either per unit (p.u.) or Amps.

Calculate

Pressing this button will run the fault analysis. In order for the results to be calculated, the power flow has to be in a solved state for the results to have any relevance. Therefore the first thing performed when **Calculate** is pressed is to solve the power flow. You can observe this by viewing the [Message Log](01-getting-started.md#message-log) when you run the calculation. Once the power flow has been solved, then the fault analysis calculations are run and the results displayed.

Clear

Pressing **Clear** will clear any fault analysis results currently in memory and displayed on the dialog.

There are also six informational displays at the bottom of this dialog for showing the fault analysis calculation results:

[Buses](27-fault-analysis.md#fault-analysis-bus-records)

[Lines](27-fault-analysis.md#fault-analysis-line-records)

[Generators](27-fault-analysis.md#fault-analysis-generator-records)

[Loads](27-fault-analysis.md#fault-analysis-load-records)

[Switched Shunts](27-fault-analysis.md#fault-analysis-switched-shunt-records)

Y-Bus Matrices

---

<a id="find-parallel-ac-branches"></a>

## Find Parallel AC Branches

*Source: [`Content/MainDocumentation_HTML/Find_Parallel_AC_Branches.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find_Parallel_AC_Branches.htm)*

To access the Find Parallel AC Branches dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \>Find Parallel AC Branches** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group.

When clicking the **Calculate** button on this dialog, Simulator will determine groups of AC Branch objects that are connected between the same two ZBRBus groups. A ZBRBus group is managed internally by PowerWorld Simulator and represents a group of buses connected by very low impedance branches (branches below the ZBR Threshold specified in the [Power Flow Solution: Advanced Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options)). These groupings of buses will then be identified by an integer. This identifying integer is written into the field specified on the dialog by the **Label each group of branches** choice field (which by default is Custom Integer 1). In addition to this a count of the number of branches in each group is written to the field specified on the dialog by the **Number of branches per group** choice field (which by default is Custom Integer 2). When the calculation is done these two fields are populated for every Branch object in the system.

The options on the right of the dialog present ways to filter the results on this dialog.

Options exist to restrict the results shown to only those branches that below to groups that have a Number of Branches between a minimum and maximum.

Options also exist to restrict results to groups that have different number of zero-impedance branches

Finally, the branches can be restricted to only **Identify parallel transformers which have conflicting tap orientation**. This means that there are parallel transformers which have a different From/To bus order. This is allowed, but any variable tap on a transformer is always on the FROM side of the branch, so if parallel transformers have their From/To terminals switched then the variable taps will be on opposite sides of the transformers. This is allowed in the software but would never be done in a real power system and likely indicates some input data errors.

The Dialog is sorted by the integer label field by default and when this is done shading is used to visually show the groups.

![Connections FindParallelACBranches](images/Connections_FindParallelACBranches.png)

---

<a id="find-text-in-oneline-dialog"></a>

## Find Text in Oneline Dialog

*Source: [`Content/MainDocumentation_HTML/Find_Text_Oneline.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find_Text_Oneline.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

![Find Text Oneline](images/Find_Text_Oneline.gif)

The **Find Text in Oneline** dialog can be used to find a text in the Oneline.

The *Options* are:

Find

Search for the text specified int he box. Press **Find** to search the oneline or the linked objects for the specified text. After selecting a desired object from the table press **Pan Object on Oneline** to locate the selected object on the oneline diagram.

Search for Text in Oneline

When checked it will search for the text in the current selected Oneline. It includes searching for text inside Background Text.

Search for Text in Linked Object Fields

When checked it will search for the text in the linked object fields based on either one of the following options:

\-*Only Key Fields, Labels, Custom Fields, and Memos* in the object. When selected it will search of this fields that are linked to the current oneline.

\-*All fields* in the object. When this option is selected it will search in all of the fields that are linked to the current oneline.

Type, X/Y Location

The remainder of the display shows the type, location, identification, layer, applicable zoom level, anchored property, and font size for each unlinked object. This table is a type of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus behaves similarly to all other case information displays.

Link Object Description

The description of the link object of the online object in the diagram.remainder

String where Text is Found

The string where the text was found after the search.

Field Variable where was Found

The Field variable where the text was found. Hovering over this column will show the field variable description.

Variable Name

The variable name of the field where the text was found. Hovering over this column will show the field variable description.

---

<a id="generator-economic-merit-order-and-merit-order-close-dispatch"></a>

## Generator Economic Merit Order and Merit Order Close Dispatch

*Source: [`Content/MainDocumentation_HTML/Generator_Economic_Merit_Order_Dispatch.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Economic_Merit_Order_Dispatch.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are two different dispatch methods available with [PV analysis](29-pv-and-qv-curves.md#pv-curves), [Scaling](18-general-tools.md#scaling), [ATC analysis](32-available-transfer-capability.md#advanced-options), and [scaling injection groups as part of Time Step Simulation](26-time-step-simulation-part1.md#input-page) that make use of generator economic MW limits and will connect generators as necessary to achieve a specified dispatch level. One is called **Economic Merit Order Dispatch** and the other is **Merit Order Close Dispatch**. Economic Merit Order Dispatch is a method that attempts to dispatch generators so that they are at the same relative point in their economic minimum MW to economic maximum MW range. Merit Order Close Dispatch will dispatch each generator in merit order until it hits its economic MW limit before dispatching another generator.

The similarities in input data and operation are described below as well as the specifics of each of the dispatch methods.

Input Data

There are two basic requirements for input data in order to properly use these features:

Injection Group Specifying Merit Order

Injection groups must be used to specify the merit order in which generators will be dispatched. The participation factors assigned with each generator as part of the injection group define the merit order. The actual merit order is based on participation factors normalized for all generators participating in the dispatch.

Generators will be excluded from the dispatch if the option to **Allow only AGC units to vary**is checked and **AGC =** *NO* for that generator. Generators will NOT be excluded if their normalized participation factor is less than or equal to zero. The normalized participation is used for ranking only and generators will be dispatched in the order of highest to lowest normalized participation factor. Generators that are offline can also participate in the dispatch as long as they can be energized either by changing the Status of the generator or closing breakers to energize. See the **Closing Breakers to Energize Generators** section below on more information.

Generator Economic Range Fields

The desired economic range in which generators should be dispatched is defined by the **MW Economic Minimum** and **MW Economic Maximum** fields. These fields can be found on the [Generator Display](05-case-information-displays-by-object-part1.md#generator-display). In order for a generator to participate in one of these merit order dispatch methods, **MW Economic Maximum** must be greater than zero.

**Economic Merit Order Dispatch**

Specified values will also be swapped to enforce the relationship that **Min MW** \<= **MW Economic Minimum** \<= **MW Economic Maximum** \<= **Max MW**. The **Min MW** and **Max MW** fields are the fields that define the overall minimum and maximum output of a generator. The **Min MW** limit will always be enforced, but the **Max MW** limit will only be enforced if the option to **Enforce unit MW limits** is in use.

**Merit Order Close Dispatch**

Only MW Economic Minimum and MW Economic Maximum limits will be used during this dispatch. These limits will be enforced regardless of how the **Enforce unit MW limits** option is set.

Dispatching the Generators

**Economic Merit Order Dispatch**

Economic merit order dispatch allows specifying how generators are dispatched at various transfer levels. Ideally, generators will maintain their output within an economic range. If at a particular transfer level generators will exceed their economic maximum value, additional generators will be dispatched so that all generators are within their economic range. Generators that are not needed to provide MW output will also not provide Mvar output. If at a particular transfer level, generators will fall below their economic minimum value, generators will be de-energized until all generators are within their economic range.

To determine the economic merit order dispatch for an injection group at a particular injection level, all generators in the group are first assumed to be at 0 MW. Valid generators are dispatched in merit order. If the desired dispatch is below the **Min MW** value of the first generator, that first generator will be turned on to its **Min MW**and no additional generators will be dispatched. Additional generators will be energized in merit order if previous generators will exceed their **MW Economic Maximum** values. All energized generators are dispatched such that they are at the same relative point in their **MW Economic Min** to **MW Economic Max** range. If energizing a new generator will cause all energized generators to fall below their **MW Economic Min** levels, all generators will be dispatched such that they are at the same relative point in their **Min MW** to **MW Economic Min** range. If all available generators are dispatched and the desired injection exceeds the total **MW Economic Maximum** for all generators, all generators will be dispatched such that they are at the same relative point in their **MW Economic Maximum** to **Max MW** range. If using the option to **Enforce unit MW limits**, generators will not be dispatched beyond their **Max MW** limit. If NOT using this option and the desired injection exceeds the total **Max MW** for all generators, all generators will be dispatched in proportion to their **Max MW** limits.

If a generator is not valid for dispatch (i.e. **AGC** = *NO* if using option **Allow only AGC units** to vary or **MW Economic Maximum** \<= 0) or is not needed in the dispatch, that generator will remain de-energized if not already energized or will have its **Status** set to *Open* so that it will not provide Mvar output in addition to not providing MW output. If a generator is energized, breakers will not be opened to de-energize the generator. Changing the **Status** of the generator itself will force the generator to be de-energized. Breakers will only change status if a generator needs to be energized but is not already energized because of open breakers.

An example of a injection group with 5 generators is shown below along with the dispatch at various transfer levels:

![Generator Economic Merit Order Dispatch 2 444x204](images/Generator_Economic_Merit_Order_Dispatch_2_444x204.jpg)

![Generator Economic Merit Order Dispatch 1 602x378](images/Generator_Economic_Merit_Order_Dispatch_1_602x378.jpg)

**Merit Order Close Dispatch**Added in version 19, build on Aug. 4, 2016

Injection group generators will be dispatched by moving individual generators to either their **MW Economic Maximum** or **MW Economic Minimum** limits as appropriate in succession based on their relative participation factors ordered from highest to lowest. Generator economic MW limits will be enforced for those units participating in the merit order close dispatch regardless of how the **Enforce unit MW limits** option is set.

If increasing the injection and the next generator in merit order is not already online, the **Status** of the generator will be set to *Closed* with an initial Mvar output of 0. Breakers will also be closed if necessary to connect the generator in addition to changing its own status. If changing the status or closing breakers will not actually connect the generator, that generator will be skipped, no changes will be made for that generator, and the next generator in merit order will be processed. See the **Closing Breakers to Energize Generators** section for more information on how breakers are selected.

If decreasing the injection and generators are being backed down to their minimum economic limit, generators will remain online when they hit their limits and the status of generators and breakers will not change.

Closing Breakers to Energize Generators

Generators can participate in one of these merit order dispatch methods provided they can be energized. If a generator is not presently energized, is the next generator in the merit order ranking, and the case has breakers, an attempt will be made to identify breakers that can be closed in order to energize the generator. This functionality does not require having the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) to work.

When selecting which breakers can be closed to energize a particular generator, breakers are only selected if in the process of closing them they would ONLY energize the particular generator. Breakers that would energize additional devices will not be selected as valid for energizing the generator. If no appropriate breakers can be found, a generator will remain de-energized and will not be available for dispatch.

Branches with **Branch Device Type** of *Breaker* and *Load Break Disconnect* are included when searching for switching devices to energize generators. *Disconnects* are not included.

See the [Close Breakers Overview](24-contingency-element-dialog.md#contingency-element-close-breakers) topic for more information on how the close with breakers process works.

---

<a id="getparameters-function-version-9"></a>

## GetParameters Function (version 9)

*Source: [`Content/MainDocumentation_HTML/GetParameters_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GetParameters_Function_v9.htm)*

The GetParameters function is used to request the values of specified fields for a particular object in the load flow case. For returning field values for multiple objects, you can use a loop to make repeated calls to the GetParameters function, and pass the object and desired field information for each object. This function is identical in setup to the [ChangeParameters](#changeparameters-function-version-9) function, with the exception that the Values array will be updated with the values for the field variables defined in ParamList.

**GetParameters(tObjectType, ParamList, Values, EString)**

Parameter Definitions

**TobjectType : String **The type of object you are changing parameters for. No default.

**ParamList : Variant **A variant array storing strings. This array stores a list of PowerWorldâ object field variables, as defined in the section on [PowerWorld Object Fields](#powerworld-object-variables-version-9). The ParamList must contain the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables for the specific device, or the device cannot be identified. The remaining field variables in the array define which values to retrieve from Simulator. No Default.

**Values : Variant **A variant array storing variants. This array can store any type of information (integer, string, etc.) in each array position. Values must be passed for the [key field](04-model-explorer-and-case-information-part3.md#key-fields) variables in ParamList, in the same array position. The remaining field positions in the Values array can initially be filled with either empty strings or zeroes, as the values will be replaced when the function is processed. No Default.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

Example

**GetParameters("gen", \[pwBusNum, pwGenID, pwGenAGCAble\], ValArray = \[1, "1", ""\], EString)**

This function call will return the AGC Status of bus number one, generator ID number 1, in the ValArray variable. Note that the generator bus number and ID had to be passed into the function, while the remaining field could be assigned an empty string. If the bus number and ID had not been passed, an error would have been returned since Simulator would not be able to identify a generator. With a valid bus number and ID for the generator, the ValArray variable would have returned an array of the following format: ValArray = \[1, "1", "Yes"\].

---

<a id="gic-analysis-non-uniform-field-data"></a>

## GIC Analysis Non Uniform Field Data

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_Non_Uniform_Field_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_Non_Uniform_Field_Data.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When data was loaded to create a Non-uniform electric field using the [Time Varying Electric Field](47-geomagnetically-induced-currents.md#gic-analysis-time-varying-electric-field-inputs) then the data can be selected in the following tab:

![GIC Analysis Non Uniform Field Data](images/GIC_Analysis_Non_Uniform_Field_Data.gif)

In the **Non-Uniform Time Point** a specific point can be selected and the electric field data by Latitude and Longitude can be view in the table below once the data loaded after pressing **GO** This table is used for testing and analysis of the [Time Varying Electric Fields](47-geomagnetically-induced-currents.md#gic-analysis-time-varying-electric-field-inputs).

---

<a id="gic-analysis-sensitivity-analysis"></a>

## GIC Analysis Sensitivity Analysis

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_Sensitivity_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_Sensitivity_Analysis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The GIC tool allows fast computation of sensitivities of transformer with respect to GIC electric field and across transmission lines (dIGIC/dEfield).

![GIC Analysis Sens Ieffective](images/GIC_Analysis_Sens_Ieffective.gif)

**Type of Sensitivity Calculation:**

**Line Amp Input Sensitivity** can identify transmission lines with greatest effect on transformer GIC current. Click Recalculate Sensitivities to compute this type of calculation.

**Transformer Ieffective GIC Sensitivity** can identify transmission lines with greatest effect on transformer GIC current. Click **Recalculate Sensitivities** to compute this type of calculation.

**Sensitivity Options:**

**Assumed Line Injection (Amps) or Assumed Direction (Degrees, 0 to 360)** If the *Type of Sensitivity Calculation* is *Line Amp Input Sensitivity* then the Assumed Line Injection will be available. If the *Transformer Ieffeective GIC Sensitivity* is selected then Assumed Direction will be available.

**Assumed Field Direction:** (Only available if *Type of Sensitivity Calculation* is *Transformer Ieffeective GIC Sensitivity*

Parallel to Line: The Field Direction will be parallel to the line.

Specified Direction: The Field Direction will be at the angle specified in *Assumed Direction (Degrees, o to 360)*

To Calculate relative sensitivities for substations with high neutral GIC currents click *Calculate Sub Driving Point Values* and a new Tab "*Substation*" will appear with the sensitivities of the GIC currents to the substations.

---

<a id="including-simulator-automation-server-functions-version-9"></a>

## Including Simulator Automation Server Functions (version 9)

*Source: [`Content/MainDocumentation_HTML/Including_Simulator_Automation_Server_Functions_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Including_Simulator_Automation_Server_Functions_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Before you can access the [functions](#simulator-automation-server-functions-version-9) defined by the [Simulator Automation Server](#simulator-automation-server-version-9) when writing the code for your external program, you must first include the library of functions defined for the Simulator Automation Server. This kind of library is referred to as a Type Library, which describes the available functions in a manner that can be interpreted by different programming languages. Importing a Type Library from another program is usually fairly simple, but the procedure does vary depending on the programming tool you are using. Please see the help for your programming tool of choice on how to import a Type Library or COM functions from another program.

Examples

The following examples are just a few specific examples for certain programming media. The procedure may be different for other programming media not listed. In addition, a procedure given for a certain type of programming media may be one variation from several possible procedures for accomplishing the same task.

Borland Delphi 5

  - Install the version of PowerWorld Simulator with the Simulator Automation Server included.
  - In Delphi 5, choose Import Type Library… from the Project menu.
  - In the list of libraries, search for and choose pwrworld Library.
  - If pwrworld Library is not in the list, click Add. Find and choose the Pwrworld.exe file from the PowerWorld Simulator directory, and click Open.
  - You should see the class name TSimulatorAuto in the list of Class names.
  - Click Install to include the PowerWorld Simulator Type Library.

Microsoft Visual Basic

  - Install the version of PowerWorld Simulator with the Simulator Automation Server included.
  - In VB, choose **References…** from the **Tools** menu. Find and choose pwrworld Library from the list of references.
  - If pwrworld Library is not in the list, click Browse. Change the file type to \*.exe, find and choose the Pwrworld.exe file from the PowerWorld Simulator directory, and click Open.
  - Click OK to install the Simulator Type Library reference.

Microsoft Visual C++

  - Install the version of PowerWorld Simulator with the Simulation Automation Server included.
  - Add **\#import "…\\powerworld.exe"** in your external program code, using the full path to the PowerWorld Simulator executable program.
  - Add **using namespace pwrworld** in your external program code.

---

<a id="listofdevices-function-version-9"></a>

## ListOfDevices Function (version 9)

*Source: [`Content/MainDocumentation_HTML/ListOfDevices_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ListOfDevices_Function_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The ListOfDevices function is used to request a list of objects and their [key fields](04-model-explorer-and-case-information-part3.md#key-fields) from the [Simulator Automation Server](#simulator-automation-server-version-9). The function can return all devices of a particular type, or can return only a list of devices of a particular type based on an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) defined for the loaded case. This function is best used in conjunction with a looping procedure and the [ChangeParameters](#changeparameters-function-version-9) or [GetParameters](#getparameters-function-version-9) functions to process a group of devices.

**ListOfDevices(tObjType, EString, filterName, objList1, {objList2}, {objList3})**

Parameter Definitions

**TobjType : String **The type of object for which you are acquiring the list of devices. No default.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

**FilterName : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) defined in the load flow case open in the Simulator Automation Server. If the filter cannot be found, the server will default to returning all objects in the case of type TobjType.

**ObjList1 : Variant **This parameter must be assigned a variable declared as a Variant. The Simulator Simulation Server will return a variant array filled with the first [key field](04-model-explorer-and-case-information-part3.md#key-fields) for the devices of type TobjType. This parameter is required for all types of devices.

**ObjList2 : Variant **This parameter **may** be optional. For device types that only have one [key field](04-model-explorer-and-case-information-part3.md#key-fields), you can omit passing a variable for this parameter. If the device type requested has two or more key fields, then this parameter must be assigned a variable declared as a Variant. The Simulator Simulation Server will return a variant array filled with the second key field for the devices of type TobjType.

**ObjList3 : Variant **This parameter **may** be optional. For device types that have one or two [key fields](04-model-explorer-and-case-information-part3.md#key-fields), you can omit passing a variable for this parameter. If the device type requested has three key fields, then this parameter must be assigned a variable declared as a Variant. The Simulator Simulation Server will return a variant array filled with the third key field for the devices of type TobjType.

Example

**ListOfDevices("gen", EString, "", objList1, objList2)**

This function call will return a list of all generators in the load flow case. By passing an empty string as the filter name, Simulator will not use an advanced filter before returning the generator key fields. Since generators have two key fields, bus number and ID, it was required to pass two variant array variables to receive the key fields. Each generator in the case would have its bus number returned in objList1 and ID in objList2. The corresponding bus number and ID are stored in the same index position in the two arrays. If only one variant array, objList1, had been passed in this instance, an error would have been returned stating more arrays were necessary. If the third variant array, objList3, had been included, Simulator would have still returned the key fields in objList1 and objList2, and would have returned objList3 as an empty variant.

---

<a id="loadcontingencies-function-version-9"></a>

## LoadContingencies Function (version 9)

*Source: [`Content/MainDocumentation_HTML/LoadContingencies_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LoadContingencies_Function_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The LoadContingencies function can be used to read a set of predefined contingencies from a PowerWorldâ Auxiliary Contingency file. Thus once you have defined a set of [contingencies](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview) in Simulator and saved the list to a PowerWorldâ Auxiliary file, you can specify the filename with this function and the [Simulator Automation Server](#simulator-automation-server-version-9) will load the contingencies into memory.

**LoadContingencies(fileName, EString, {tAppend})**

Parameter Definitions

**Filename : String **The name of the PowerWorldâ Auxiliary file containing the defined contingencies. If the file cannot be found, and error will be returned through EString.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

**TAppend : Boolean **This parameter is optional. If you have more than one list of contingencies in separate files, you can append the lists together in the Simulator Automation Client by passing the Boolean value True in this parameter. The default if not passed is False, meaning any existing contingencies in the Simulator Automation Client would be cleared prior to loading the new list.

Example

**LoadContingencies("c:\\my files\\ctgfile.aux", EString, True)**

This function call will load a previously created list of contingencies that was saved in the PowerWorld Auxiliary file format. The file name string identifies the location and name of the auxiliary file. By passing the value True in the optional parameter tAppend, Simulator will read the list of contingencies and add them to any existing contingencies already loaded in Simulator. Contingencies in the list existing list with the same name as contingencies in the appending list will be replaced by the records in the appending list.

---

<a id="make-up-power-sources"></a>

## Make-Up Power Sources

*Source: [`Content/MainDocumentation_HTML/Make_Up_Power_Sources.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Make_Up_Power_Sources.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generator, load, injection group, and switched shunt contingencies may cause imbalances between generated power and demand. The default way to handle these imbalances is to assign them to the system slack. There are other global options that can be specified for contingency analysis as a whole to deal with [make-up power](22-contingency-analysis-options.md#basics). The global settings are the preferred way of dealing with make-up power, but more specific compensation for make-up power can be specified for certain contingency actions.

To implement more local compensation for generation, load, injection group, and switched shunt changes, use the Make-Up Power Sources Dialog. This dialog can be accessed by from the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) by clicking the button labeled **Make-Up Power Sources**. Most of the dialog is occupied by a grid that lists bus numbers and relative contributions. This grid is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), so its behavior should be familiar. For example, right-click on the grid to display its local menu.

We shall call those buses that must compensate for the changes caused by a generator, load, injection group, or switched shunt contingency "compensators". To insert a new compensator, select **Insert** from the grid’s local menu. This opens another dialog, where you should specify the bus number of the compensator and its contribution. Specify the contribution of the compensator either as a percentage or as a fixed number of MW. If a particular contingency has multiple compensators, then the choice of basis for the contribution (either MW or percent) should be consistent for each. After identifying the compensator, click **OK**. The grid should update with your newly added compensator.

To delete an existing compensator, select it from the grid and select **Delete** from the local menu.

To determine how much each compensator contributes to the imbalance, each contribution value is normalized to the total sum of all contribution values. This allows the values to be entered in either percent or MW. Keep in mind that when entering the values in percent that the sum of all contribution values should equal 100 or the actual contribution amounts will not occur in the expected percentages.

Compensators account for the changes caused by a generator, load, injection group, or switched shunt contingency by changing either generation or load to satisfy its defined contribution. For example, suppose compensator contributions are specified as percentages, and Simulator needs to compensate for 100 MW lost in a particular generation contingency. Suppose the contingency has 4 compensators defined as follows:

Bus Number Contribution

1  20

2  30

3  10

4  40

Suppose buses 1 and 2 are load buses, and buses 3 and 4 are generators. Then bus 1’s load will decrease by 20 MW, bus 2’s load will decrease by 30 MW, bus 3’s generation will increase by 10 MW, and bus 4’s generation will increase by 40 MW. These changes will be instituted regardless of the compensators’ operating limits or AGC status. In fact, any compensating units will be set off AGC to ensure that the prevailing AGC control does not distort the dictates of the contingency. Furthermore, maximum MW limits on generators will not be checked.

If a compensator has both generators and loads attached to it, the generator will take precedence. The generator will function as the compensating device, and the load will be left unchanged.

---

<a id="multi-section-line-field-options"></a>

## Multi-Section Line Field Options

*Source: [`Content/MainDocumentation_HTML/Multi_Section_Line_Field_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Section_Line_Field_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Multi-section line field display objects are used to show different values associated with multi-section lines on onelines.

This dialog can be opened by right-clicking on a multi-section line display field and choosing to open the **Multi-Section Line Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a multi-section line display field.

This dialog is used to view and modify the parameters associated with these fields.

Find…

If you do not know the exact line identifiers you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Near Bus Number

Bus associated with the near end of the object. All fields specifically listed in the **Type of Field**, i.e. NOT the fields in **Select a Field**, display values calculated at the *near bus* end. When inserting fields graphically, this field is automatically set to the closest bus on the oneline.

Far Bus Number

Bus associated with the *far end* of the object.

Circuit

Two-character identifier used to distinguish between multiple multi-section lines joining the same two buses. Default is ‘1’.

Total Digits in Fields

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Delta Per Mouse Click

This option is not used with this type of field object.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Rotation Angle in Degrees

The angle at which the text will appear on the diagram.

Anchored

If this checkbox is checked, the line analog is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated line.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of line field to show. The following choices are available:

Name

A name can optionally be assigned to a multi-section line. If assigned this field displays that name.

MW Flow 

MW flow into the multi-section line at the near bus.

Mvar Flow 

Mvar flow into the multi-section line at the near bus.

MVA Flow 

Magnitude of MVA flow into the multi-section line at the near bus.

Amp Flow 

Magnitude of amps into the multi-section line at the near bus.

Select a Field 

Choose from any of the available multi-section line fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Select **OK** to save changes and close the dialog or **Cancel** to close the dialog without saving your changes.

---

<a id="oneline-viewer"></a>

## Oneline Viewer

*Source: [`Content/MainDocumentation_HTML/Oneline_Viewer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Viewer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Oneline Viewer provides an easy way to organize and view a large number of oneline diagrams. It is accessible in the **View** Ribbon Group on the **Onlines** Ribbon Tab.

![OnelineViewer](images/OnelineViewer.gif)

Oneline Navigation

The Oneline Navigation pane on the left can be pointed at a specific folder in the file system to watch. It populates with any display files or folders containing display files, so a basic hierarchical organization can be constructed. Double-clicking a listed file will open that display in the window to the right. Recently viewed displays are listed as tabs.

Use the **Browse** button to set the folder of interest (by default it looks in the directory of the current case). The **Refresh** button re-loads the target folder; use this button to update the Oneline Viewer to accurately display any changes that made have been made while the viewer was open.

Keywords provide another means of organizing PWD files: the **Keywords** folder in the Oneline navigation pane contains links to onelines, sorted by keywords . Currently, keywords and other metadata can only be added to PWD files.

Note that the navigation pane is populated with *all* display files in the target directory structure, not just those which can be linked to the current case.

Oneline Metadata

PowerWorld PWD oneline files can contain metadata useful for organization. The metadata of any PWD file displayed in the Oneline Navigation can be set with the **Edit View Metadata** button below the navigation pane. The view can be given a name different than its file name, a longer description, and a list of organizational keywords (comma delimited). These keywords allow for flexible organizational schemes.

Supported Display Files

The Oneline Viewer currently links three types of display file:

PWD

PowerWorld's own oneline display format. These files can contain metadata useful for sorting in the Oneline Viewer.

AXD

PowerWorld's text format for display files.

DDL

Areva display files can be read in and displayed in Simulator under some circumstances. The case must be an HDB export directly from the Areva/Alstom State Estimator or Contingency Analysis model, and a customized AUX file is needed to guide the conversion. If you are interested in opening Areva displays in Simulator, please contact PowerWorld.

---

<a id="opencase-function-version-9"></a>

## OpenCase Function (version 9)

*Source: [`Content/MainDocumentation_HTML/OpenCase_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OpenCase_Function_v9.htm)*

The OpenCase function will load a PowerWorldâ Simulator load flow file into the [Simulator Automation Server](#simulator-automation-server-version-9). If an error occurs trying to open the case, an error message will be returned through EString.

**OpenCase(filename, EString)**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Simulator case file to be loaded into the Simulator Automation Server. This string includes the directory location and full file name. If the file cannot be found or an error occurs while reading the file, an error message will be returned through EString.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

---

<a id="powerworld-object-variables-version-9"></a>

## PowerWorld Object Variables (Version 9)

*Source: [`Content/MainDocumentation_HTML/PowerWorld_Object_Variables_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerWorld_Object_Variables_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The ability to access power system data for different objects through various [Simulator Automation Server functions](#simulator-automation-server-functions-version-9) is based on variables defined in Simulator that can be referred to as Object Field Variables. Each object (i.e. bus, generator, etc.) can have numerous fields associated with it. Each of these fields, in turn, has a variable associated with the field to enable access to the field for the purpose of acquiring or changing data. For example, the [GetParameters](#getparameters-function-version-9) function has a parameter called ParamList, which is intended to store a list of Object Field Variables for a particular type of object. When the function is called, the Simulator Automation Server will return the values associated with each particular field variable for the type of object specified. These field variables allow for complete flexibility by the user in specifying as many or as few fields for a particular object when acquiring or changing data.

Examples of Field Variables

**PWBusGenMW**

**PWBusNum**

Simulator has literally hundreds of parameters spanning numerous types of device and option specifications. Rather than list all of the field variables and the value they represent in this help file, we have enabled Simulator to automatically generate a text file containing the field variables and a description of what value the variable represents. PowerWorld Corporation highly recommends that you examine this list. To generate this text file, run PowerWorld Simulator and access the **Help** menu. Choose the option **Export Object Fields…** Specify a file name and location for saving the file, and click Save. Simulator will save out the field variables, the type of variable (string, integer, etc.), and a description of the value the field variable represents, with key fields for different objects marked with an asterisk. The field variables will also be split into sections based on the type of object they are valid for. Note that the same field variable may be available for more than one object, but that the value represented by the field variable might vary for different objects.

Examples of Field Variables in Listing

PwBusGenMW Real 'Bus Gen MW'

\* PwBusNum Integer 'Bus Number' (\* denotes key field in text file)

ATC\_MaxLimElements Integer 'Max \# Limiting Elements'

The last note on the Object Field Variables is that some of the object field variables are reused for more than one value for an object. For example, a transmission line has "from" and "to" buses associated with the line. Rather than have separate field variables for values at each terminal bus, the same field variable is used for both, with a colon followed by a number appended to the variable to signify which bus the value represents. As an example, consider the field variable for bus per unit voltage, which is PWBusPUVolt. Since there are two buses per line, the "From" bus voltage would be represented as PWBusPUVolt:0, and the "To" bus voltage would be represented as PWBusPUVolt:1. The enumeration of the field variables always starts with 0 for the first instance. You may note that in the text file of field values that you don't see any field variables with :0 appended to them. Since we did not want you to have to always append the :0 on all field variables, the default for a field variable with no appended :\# is 0. Thus you would only need to be concerned with appending the :\# for field variables that require a number greater than 0.

---

<a id="processauxfile-function-version-9"></a>

## ProcessAuxFile Function (version 9)

*Source: [`Content/MainDocumentation_HTML/ProcessAuxFile_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ProcessAuxFile_Function_v9.htm)*

The ProcessAuxFile function will load a PowerWorldâ Auxiliary file into the [Simulator Automation Server](#simulator-automation-server-version-9). This allows you to create a text file (conforming to the PowerWorldâ Auxiliary file format) that can list a set of data changes and other information for making batch changes in Simulator. If an error occurs while processing the auxiliary file, an error message is returned through EString.

**ProcessAuxFile(filename, EString)**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Auxiliary file to be loaded into the Simulator Automation Server. This string includes the directory location and full file name.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

---

<a id="quick-filter"></a>

## Quick Filter

*Source: [`Content/MainDocumentation_HTML/Quick_Filter.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Quick_Filter.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Quick filters are essentially the same as an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering), including the pre-filter option using [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters), but is not saved as an advanced filter with the load flow case. A quick filter applies the filter criteria immediately without requiring naming and saving the filter definition. A quick filter can be expanded to multiple criteria, either at the time the quick filter is initially defined, or at a later time by clicking on another column, choosing Quick Filter again, and setting the additional criteria for the selected column. Criteria points can also be removed by viewing the Quick Filter definition and clicking the **X** next to each criteria you want removed from the quick filter. If you decide to save the Quick Filter definition as an advanced filter, click the **Find...** button to open the Advanced Filters dialog. The Quick filter criteria will be added to the dialog. You can then apply a filter name and save the criteria as an advanced filter for later re-use.

Added more options to drop down in Version 20

When clicking the Quick Filter drop down on the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar), a sub menu appears which has the following options.

**Dialog** : This will open the Quick Filter dialog for defining a quick filter in the same way an advanced filter is defined.

**Clear** : This will clear out the conditions in the Quick Filter and also remove the filter from the present case information display

**Logic DropDown**: This allows you to change the Boolean logic of the Quick Filter to AND, OR, NAND, NOR, XOR, or ONETRUE

**Add VariableName = 123.56**: click on the menu item with this syntax to add a new filter condition to the Quick Fitler.

**Add Selected = YES** : click on this menu to add a new filter condition that the Selected Field equals YES

**Add Selected = NO** : click on this menu to add a new filter condition that the Selected Field equals NO

![QuickFilterMenu](images/QuickFilterMenu.png)

---

<a id="relationship-between-contingencies-model-conditions-model-filters-and-model-expressions"></a>

## Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions

*Source: [`Content/MainDocumentation_HTML/Relationship_CTG_ModelCondition_Filter_Expression.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Relationship_CTG_ModelCondition_Filter_Expression.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Model Conditions, Model Filters, and Model Expressions are all very useful for defining Model Criteria for conditional contingency actions and defining the amount of change for a contingency action. This same relationship between these objects exists when assigning Arming Criteria for Remedial Actions and Remedial Action Elements.

The following image shows the relationship between these objects:

![Relationship CTG ModelCondition Filter Expression](images/Relationship_CTG_ModelCondition_Filter_Expression.gif)

---

<a id="remedial-action-definition-dialog"></a>

## Remedial Action Definition Dialog

*Source: [`Content/MainDocumentation_HTML/Remedial_Action_Definition_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Remedial_Action_Definition_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Remedial Action Definition dialog serves as an information source for displaying the elements associated with individual remedial actions. The Remedial Action Definition dialog can be used to scroll through the list of elements, view and modify their definitions, insert or delete elements, or delete an entire remedial action. You may access this dialog by choosing either **Show Dialog** or **Insert** from the local menu of the [Remedial Actions Display](21-contingency-analysis-overview-and-records.md#remedial-actions).

After making changes, click **OK** to save your changes and close the dialog. Click **Cancel** to close the dialog without saving your changes. Click **Save** to save your changes (including the addition of a new remedial action) without closing the dialog (this allows you to keep working with the dialog). Click **Delete** to remove the selected remedial action.

![RemedialAction Definition Dialog](images/RemedialAction_Definition_Dialog.gif)

The Remedial Action Definition dialog has the following controls that are available regardless of the tab that is currently selected:

Remedial Action

Identifies the name of the currently displayed remedial action. Use the drop-down arrow to select a different contingency, or use the scroll buttons to navigate through the list of contingencies. When adding a new contingency, Contingency Label will show *New Contingency.* The user can change the Contingency Label by clicking **Rename**.

Add New

Click the **Add New** button to add a new contingency to the contingency list for the case. You will be prompted to enter a unique name for the new contingency. After naming the new contingency, the name appears in the Contingency Label and you can insert new elements in the contingency definition.

Rename 

Allows you to rename the selected contingency.

Find

Opens a dialog that will allow the use of [advanced search methods](04-model-explorer-and-case-information-part3.md#find-dialog-basics) for finding a particular contingency.

Definition Tab

Insert New Element

Click this button to add a new element to the remedial action. This will open the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog), used to define all of the details associated with the Action of the element. When you return to the Remedial Action Definition dialog, the display will contain the newly inserted element.

Clear All

Removes all elements from the remedial action definition. The remedial action elements table will then appear blank, indicating that the remedial action involves no associated actions.

Definitions Display

The Remedial Action Definitions Display lists the elements assigned to the selected contingency. Select **Insert** from the local menu or click on the **Insert New Element** button to add elements to the remedial action. Right-click on a specific element in the display and select **Delete** from the local menu to remove the element from the contingency. For more information about this display, see the [Contingency Definitions Display](22-contingency-analysis-options.md#contingency-definition-display).

Arming Status Added in Version 20

This field determines how an action is armed in the presence or absence of **Arming Criteria**. See the [Contingency Element Status](24-contingency-element-dialog.md#contingency-element-status) topic for more details.

Arming Criteria Added in Version 20

If specified, Arming Criteria can be either a [Model Condition](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) or [Model Filter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog). This specifies a criterion under which a remedial action is armed. In order for a remedial action to actually be applied it must first be armed. The Arming Criteria is always evaluated in the contingency reference state. The **Arming Status** field determines if the Arming Criteria needs to be evaluated or if the remedial action is simply always armed or never armed.

Special options exist for Model Conditions and Filters during contingency analysis that affect how they are evaluated. See the [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) and [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) topics for more information on this.

Custom Tab

The [Custom page](01-getting-started.md#memo-display) of the dialog contains two sections: custom fields and memo.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the contingency. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the contingency. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

---

<a id="runscriptcommand-function-version-9"></a>

## RunScriptCommand Function (version 9)

*Source: [`Content/MainDocumentation_HTML/RunScriptCommand_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RunScriptCommand_Function_v9.htm)*

The RunScriptCommand function is used to execute a list of script statements. The script actions are those included in the script sections of the [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux). If an error occurs trying to run a script command, an error will be returned through EString.

**RunScriptCommand(Statements, EString)**

Parameter Definitions

**Statements : String **The block of script actions to be executed. Each script statement must end in a semicolon. The block of script actions should **not** be enclosed in curly braces.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

Example

**RunScriptCommand("Entermode(RUN); SolvePowerFlow;", EString)**

This function call will switch to Run mode and then will solve the power flow of the present case.

---

<a id="savecase-function-version-9"></a>

## SaveCase Function (version 9)

*Source: [`Content/MainDocumentation_HTML/SaveCase_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SaveCase_Function_v9.htm)*

The SaveCase function is used to save a case previously loaded in the [Simulator Automation Server](#simulator-automation-server-version-9) using the [OpenCase](#opencase-function-version-9) function. The function allows you to specify a file name and a format for the save file. If an error occurs while trying to save a case, an error message is returned through EString.

**SaveCase(fileName, EString, {fileType}, {Overwrite})**

Parameter Definitions

**fileName : String **The name of the file you wish to save as, including file path. No default.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

**fileType : String **This parameter is optional. If you desire to save the case in a format other than the current PowerWorld Binary (pwb) format, you must specify the type of format in this parameter as a string. If the parameter is not passed, the format type defaults to the most recent version of PowerWorld binary (pwb) file. If a string is passed for this parameter, it must at least be the "PWB" string. An empty string will return an error. The following list is the currently supported list of string identifiers and the file types they represent.

"PTI23"  PTI version 23 (raw)  
"PTI24"  PTI version 24 (raw)  
"PTI25"  PTI version 25 (raw)  
"PTI26"  PTI version 26 (raw)  
"PTI27"  PTI version 27 (raw)  
"GE"  GE PSLF (epc)  
"IEEE"  IEEE common format (cf)  
"PWB70"  PowerWorld Binary version 7.0 (pwb)  
"PWB"  PowerWorld Binary (most recent) (pwb)

**Overwrite : Boolean **This parameter is optional. If you do not want to overwrite a file with the same name as passed in filename, you must specify this parameter as False. Default is True.

---

<a id="saving-case-information-display-contents-as-html-tables"></a>

## Saving Case Information Display Contents As HTML Tables

*Source: [`Content/MainDocumentation_HTML/Saving_Case_Information_Display_Auxiliary_File_With_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Case_Information_Display_Auxiliary_File_With_Options.htm)*

Simulator's allow you to save their contents as an aux file with many options on how to save the data. To do this, right-click on any row of the table and select **Save Auxiliary File with Options...** from the resulting local menu. This brings up the following dialog with options:

![Save Aux with Options](images/Save_Aux_with_Options.jpg)

The option will save the contents of the case information display to an external file that the user can select once OK is pressed. 

What To Save

This option allows saving All the content, Selected Records or Selected Records and Columns of the case information display to an auxiliary file.

Which identifiers would you like to use for identifying objects in SUBDATA and within fields in the extra DATA Sections?

This option allows to set the Identifiers to be the Numbers, Name and Nominal kV or Labels.

Use Auxiliary Export Format

This option allows to only select the fields from the [Aux Export Format](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system) of the selected object. The Aux Export Format Description can be selected from the drop-down menu or a new export format can be selected by pressing Define Formats.

Additional Objects and How to Save Them

A list of additional objects will appear in the bottom of the dialog if the selected object have additional data that usually can be saved with the object. The options on how to save those additional objects are the following: **Do Not Save** the data, Save the objects as an **Extra Data** section or save the object as a **SUBDATA** section in the original object. The user can then select how to save the different additional objects by selecting the desired options. When a particular how to save option have an X it means that saving that object in that particular way is not allowed.

---

<a id="sendtoexcel-function-version-9"></a>

## SendToExcel Function (version 9)

*Source: [`Content/MainDocumentation_HTML/SendToExcel_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SendToExcel_Function_v9.htm)*

The SendToExcel function can be called to send data from the [Simulator Automation Server](#simulator-automation-server-version-9) to an Excel spreadsheet. The function is flexible in that you can specify the type of object data you want to export, an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) name for a filter you want to use, and as many or as few [field types](#powerworld-object-variables-version-9) as desired that are supported by the type of object. The first time this function is called, a new instance of Excel will be started, and the data requested will be pasted to a new sheet. For each subsequent call of this function, the requested data will be pasted to a new sheet within the same workbook, until the workbook is closed. If an error occurs while trying to send data to Excel, an error message is returned through EString.

**SendToExcel(tObjectType, filterName, EString, {tFieldList})**

Parameter Definitions

**tObjectType : String **A string describing the type of object for which your are requesting data. No Default.

**filterName : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) which was previously defined in the case before being loaded in the Simulator Automation Server. If no filter is desired, then simply pass an empty string. If a filter name is passed but the filter cannot be found in the loaded case, no filter is used. Default is an empty string.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

**TFieldList : Variant **This parameter is optional. A variant array of strings, where each string represents an object field variable, as defined in the section on [PowerWorld Object Variables](#powerworld-object-variables-version-9). If no array is passed, the Simulator Automation Server will use predefined default fields when exporting the data.

Example

**SendToExcel("gen", "", EString, \[pwBusNum, pwGenID, pwGenAGCAble\])**

This function call will send the values of the fields in tFieldList to an Excel workbook for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found. By specifying the fields in the optional parameter tFieldList, only the three field values for each generator will be returned. If the optional parameter tFieldList had been omitted, Simulator would have returned internally defined default information for the generators.

---

<a id="simulator-automation-server-version-9"></a>

## Simulator Automation Server (version 9)

*Source: [`Content/MainDocumentation_HTML/Simulator_Automation_Server_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Simulator_Automation_Server_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**NOTE: The function calls for version 9 of SimAuto have become obsolete in version 10. The reason for the change was due to problems that arose with the structure of the functions in certain programming languages. The function structures have been modified for version 10 of Simulator. If you have code written that uses version 9 SimAuto function structures, it is fairly straightforward to convert the function calls from version 9 to version 10. Please see the updated section on the** [**Simulator Automation Server**](33-simauto-overview-and-setup.md#automation-server) **for version 10. If you still have questions, please contact PowerWorld Corporation.**

The PowerWorldâ Automation Server is only available to customers who have purchased the SimAuto add-on for PowerWorldâ Simulator. The PowerWorld Simulator Automation Server is intended for enabling a PowerWorld customer with the ability to access PowerWorld Simulator functionality from within a program written externally by the user. The Simulator Automation Server acts as a COM object, which can be accessed from various different programming languages that have COM compatibility. Examples of programming tools with COM compatibility are Borlandâ Delphi, Microsoftâ Visual C++, and Microsoftâ Visual Basic, just to name a few. For more information on COM and Automation servers, see the help for Microsoft Windows.

The Automation Server of Simulator works very well in combination with Simulator Script Commands and [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux). It is beneficial to become familiar with these topics when considering using the Simulator Automation Server.

---

<a id="simulator-automation-server-functions-version-9"></a>

## Simulator Automation Server Functions (version 9)

*Source: [`Content/MainDocumentation_HTML/Simulator_Automation_Server_Functions_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Simulator_Automation_Server_Functions_v9.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following list of functions is currently available once the SimulatorAuto object is set in your code. Check the help sections on these functions to see more detail on the particular function.

[ChangeParameters](#changeparameters-function-version-9)

[CloseCase](#closecase-function-version-9)

[GetParameters](#getparameters-function-version-9)

[ListOfDevices](#listofdevices-function-version-9)

[LoadContingencies](#loadcontingencies-function-version-9)

[OpenCase](#opencase-function-version-9)

[ProcessAuxFile](#processauxfile-function-version-9)

[RunScriptCommand](#runscriptcommand-function-version-9)

[SaveCase](#savecase-function-version-9)

[SendToExcel](#sendtoexcel-function-version-9)

[WriteAuxFile](52-additional-linked-topics-part3.md#writeauxfile-function-version-9)
