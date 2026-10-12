---
title: "Contingency Element Dialog"
part: "Contingency Analysis"
chapter_file: "24-contingency-element-dialog.md"
topics: 24
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Contingency Element Dialog

The Contingency Element dialog and every element action type.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (24)**

- [Contingency Element Dialog](#contingency-element-dialog)
- [Contingency Element: Open Breakers](#contingency-element-open-breakers)
- [Contingency Element: Close Breakers](#contingency-element-close-breakers)
- [Contingency Element Status](#contingency-element-status)
- [Type: 3-Winding Transformer](#type-3-winding-transformer)
- [Type: Abort](#type-abort)
- [Type: Area](#type-area)
- [Type: Branch](#type-branch)
- [Type: Bus](#type-bus)
- [Type: DC Converter](#type-dc-converter)
- [Type: DC Line](#type-dc-line)
- [Type: Generator](#type-generator)
- [Type: Injection Group](#type-injection-group)
- [Type: Interface](#type-interface)
- [Type: Line Shunt](#type-line-shunt)
- [Type: Load](#type-load)
- [Type: Multi-Section Line](#type-multi-section-line)
- [Type: Phase Shifter](#type-phase-shifter)
- [Type: Series Capacitor](#type-series-capacitor)
- [Type: Solve Power Flow](#type-solve-power-flow)
- [Type: Script](#type-script)
- [Type: Substation](#type-substation)
- [Type: Switched Shunt](#type-switched-shunt)
- [Type: VSC DC Line](#type-vsc-dc-line)

---

<a id="contingency-element-dialog"></a>

## Contingency Element Dialog

*Source: [`Content/MainDocumentation_HTML/contingency_element_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/contingency_element_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contingency Element Dialog provides information on the individual elements that comprise a contingency definition. You may use this dialog to modify an existing contingency’s definition or to add elements to new or existing contingencies.

This dialog is also used when defining [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions) and [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions). The options that appear will be different depending on what type of object is being defined with the dialog and the dialog caption will change to reflect the type of object being defined. Differences will be noted in the option descriptions.

There are several ways to open the Contingency Element Dialog:

  - By pressing the **Insert New Element** button on the [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog).
  - By right-clicking on a [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display) and choosing **Insert** or **Show Dialog**.
  - By right-clicking on the [Contingency Tab](22-contingency-analysis-options.md#contingencies-tab) of the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) and choosing **Insert Special \> Quick Insert of Single Element Contingency**.

After making the desired changes, click **OK** to save changes and close the dialog or click **Cancel** to close the dialog without saving your changes.

![Contingency Element Dlg](images/Contingency_Element_Dlg.jpg)

The Contingency Element Dialog has the following options and controls:

Description

Identification of the element action that is defined by the dialog options. This is a drop-down control that allows the selection of any element that is defined for the currently selected contingency. This allows any element for the current contingency to be modified, inserted, or deleted without having to close the dialog. New contingency elements can be added by clicking the **Insert** button. Clicking the **Save** button will modify the selected element with any changes that have been made in the dialog. Clicking the **Delete** button will delete the selected element.

Element Type

Indicates the type of element involved in the contingency action. The Element Type will dictate what **Action Types** are available, and the selection of the Element Type, in conjunction with the **Action Type**, **Amount**, and **in** options settings, determines what actually happens during the contingency.

What actually happens during a contingency action based on the **Element Type**, **Action Type**, and **in** options is described in detail in the topics referenced below:

[Branch](#type-branch)

[Generator](#type-generator)

[Load](#type-load)

[Switched Shunt](#type-switched-shunt)

[Bus](#type-bus)

[Interface](#type-interface)

[Injection Group](#type-injection-group)

[Multi-Section Line](#type-multi-section-line)

[Series Capacitor](#type-series-capacitor)

[Phase Shifter](#type-phase-shifter)

[3-Winding Transformer](#type-3-winding-transformer)

[Line Shunt](#type-line-shunt)

[DC Line](#type-dc-line)

[VSC DC Line](#type-vsc-dc-line) (Added in version 20, build on January 11, 2018)

[DC Converter](#type-dc-converter)

[Area](#type-area)

[Substation](#type-substation)

[Script](#type-script)

[Abort](#type-abort)

[Solve Power Flow](#type-solve-power-flow)

[Contingency Block](21-contingency-analysis-overview-and-records.md#contingency-blocks)

The individual actions of the Contingency Block are applied according to how they are defined. There are no Action Types available for a Contingency Block.

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

This field determines how an action is applied in the presence or absence of **Model Criteria**. See the [Contingency Element Status](#contingency-element-status) topic for more details.

Persistent Added in Version 19

Normally after any contingency element, RemedialActionElement, etc. is applied during the [contingency solution process](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis) it will not be applied again. Marking an action as **Persistent** changes this behavior. Any action that is marked as **Persistent** and also has the **Status** field set to SOLUTIONFAIL, POSTCHECK or TOPOLOGYCHECK will be applied in the appropriate section of the overall contingency process any time that its Criteria is met. An exception to this is that a SOLUTIONFAIL element will only remain persistent up until a solution is successfully achieved. Once a solution is achieved then the SOLUTIONFAIL elements that had been applied will no longer be evaluated. This is done to ensure the SOLUTIONFAIL loop is not entered repeatedly.

Criteria Check Once Added in version 22, build on August 11, 2022

This option will only be available when the dialog is being used to define [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions).

When this option is checked the **Model Criteria** will only be checked once during the process of applying a Remedial Action Element in response to contingency actions. This means that the Model Criteria will only be evaluated once for elements with TOPOLOGYCHECK, POSTCHECK, or SOLUTIONFAIL **Status**. If the criteria is not met, this action will not be implemented and the criteria will not be evaluated again. The **Persistent** field is ignored when this option is checked. The action will not be implemented and the criteria will not be evaluated again for a criteria that is met but the Time Delay is greater than the time delays of other actions whose criteria is also met. This option has no impact if the **Model Criteria** is not defined.

This option is intended to allow the modeling of a Remedial Action Element that should only be implemented due to contingency actions and not respond due to remedial actions.

Model Criteria

Simulator allows you to define Model Criteria, which can consist of both [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) and [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog). These specify a criterion under which a contingency action would occur. For example, you could specify that a generation outage only occur if the pre-contingency flow on a line is higher than a specified amount. Normally, no Model Criteria will be specified, and this field will be blank. The **Status** field will determine when Model Criteria is evaluated.

Special options exist for Model Conditions and Filters during contingency analysis that affect how they are evaluated. See the [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) and [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) topics for more information on this.

Arming Status Added in Version 20

This option will only be available when the dialog is being used to define [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions).

This field determines how an element is armed in the presence or absence of **Arming Criteria**. See the [Contingency Element Status](#contingency-element-status) topic for more details.

Arming Criteria Added in Version 20

This option will only be available when the dialog is being used to define [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions).

If specified, Arming Criteria can be either a [Model Condition](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) or [Model Filter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog). This specifies a criterion under which a remedial action element is armed. In order for a remedial action element to actually be applied it must first be armed. The Arming Criteria is always evaluated in the contingency reference state. The **Arming Status** field determines if the Arming Criteria needs to be evaluated or if the remedial action element is simply always armed or never armed.

In order for a remedial action element to actually be implemented, it must be armed based on its own criteria and the Remedial Action to which it belongs must also be armed. Remedial Actions have their own Arming Criteria and Arming Status that are described with the [Remedial Action Definition dialog](52-additional-linked-topics-part1.md#remedial-action-definition-dialog) topic.

Special options exist for Model Conditions and Filters during contingency analysis that affect how they are evaluated. See the [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) and [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) topics for more information on this.

Inclusion Filter

This option will only be available when the dialog is being used to define [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) or [Remedial Action Elements](21-contingency-analysis-overview-and-records.md#remedial-actions).

The Inclusion Filter is an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device) that gets applied to each contingency. If the contingency meets the Inclusion Filter defined with a particular global action or remedial action element, that contingency will include that global action or remedial action element. Otherwise, a global action or remedial action element will be ignored for that contingency. To select an Inclusion Filter, click the **Add/Modify** button. This will open the advanced filter dialog that will allow selection of the filter. To include a global action or remedial action with all contingencies, leave the Inclusion Filter blank. The Inclusion Filter is evaluated in the reference case to determine if a contingency meets the filter.

Time Delay

The time to wait in seconds before an action is applied. Default value is 0. When other than 0, this serves as a relative ordering for the implementation of actions during steady state analysis. When a ContingencyElement’s Criteria refers to a ModelCondition, then this TimeDelay will be used directly. When a ContingencyElement’s Criteria refers to a ModelFilter, then the Time Delay used will be the summation of the ContingencyElement’s TimeDelay and the Calculated Time Delay of a Model Filter. For more information on how a ModelFilter’s Calculated Time Delay is determined see [Treatment of Model Filter and Contingency Element Time Delays](23-contingency-analysis-running-and-results.md#treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays).

Actions with the smallest time delay (down to a microsecond) will be applied first during the TOPOLOGYCHECK and POSTCHECK solution steps. The time delay is ignored during the CHECK solution step. This is NOT an absolute time at which an action occurs, but serves as a relative ordering for the implementation of actions. Actions with the smallest time delay will be applied first during the TOPOLOGYCHECK and POSTCHECK solution steps. See the [contingency processing order](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis) topic for more information on how the time delay is used in the solution steps.

[Contingency Blocks](21-contingency-analysis-overview-and-records.md#contingency-blocks) and [Post Power Flow Solutions Actions](10-power-flow-solution-and-options-part2.md#post-power-flow-solution-actions-dialog) do not allow a Time Delay.

Comment

An optional user-specified comment string associated with the action. For example, for an action with Model Criteria specified, you could add a sentence explaining why the action is only performed under the specified criteria. While this comment is not used by Simulator in any way, it is saved with the contingency element when saving contingency records in contingency auxiliary data files or with the case PWB file.

Open Breakers for Contingencies

When using the *Open Breakers* contingency action, Simulator will automatically search the topology of the system to determine which breakers must be opened to isolate this device. For more information on this functionality see the topic [Contingency Element: Open Breakers](#contingency-element-open-breakers).

Close Breakers for Contingencies

When using the *Close Breakers* contingency action, breakers are identified individually for each element that is using this action and the element is not already energized. A list of breakers to be closed is created for each affected element regardless of whether closing the breakers will actually energize the element. The lists of breakers for each individual element are merged into a set of unique breakers. New temporary contingency actions are created for these breakers so that when the contingency action is actually implemented, the selected breakers are closed instead of the element itself changing status. Once the contingency has been implemented and solved, the temporary contingency actions are removed so that the user never sees the actions created for the breakers. During the actual contingency solution, the *[What Occurred](23-contingency-analysis-running-and-results.md#what-occurred)* list will be updated and can be examined in the results to determine what breakers were needed to energize the device, even though the actions created for the breakers are removed after the contingency has been examined.

The **Close Breakers** contingency action is only available for contingency records and [remedial actions](21-contingency-analysis-overview-and-records.md#remedial-actions) and is not available for [contingency block definitions](21-contingency-analysis-overview-and-records.md#contingency-blocks) or for [global contingency actions](21-contingency-analysis-overview-and-records.md#global-actions). Only branches of **Branch Device Type** of *Breaker* are used with contingency actions, and *Disconnects* are not used.

More information about how breakers are selected can be found in the [Close Breakers Overview](#contingency-element-close-breakers) topic.

---

<a id="contingency-element-open-breakers"></a>

## Contingency Element: Open Breakers

*Source: [`Content/MainDocumentation_HTML/Contingency_OpenBreakers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_OpenBreakers.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The contingency action type *Open Breakers* is available for each contingency element type for which the *Open* action type is available. This includes the following element types: Branch, Bus, Load, Generator, Switched Shunt, DC Line, Injection Group, Interface, and Substation. This action type is only available for contingency records and is not available for [contingency block definitions](21-contingency-analysis-overview-and-records.md#contingency-blocks) or for [global contingency actions](21-contingency-analysis-overview-and-records.md#global-actions).

In order to handle the *Open Breakers* contingency elements, before one contingency's solution is performed, the list of contingency elements for that contingency is processed by looking for elements that use *Open Breakers*. For elements with this action type, all of the terminal buses of the respective device are processed using the algorithm below to determine which breakers to open to isolate the device (and possibly which generators to outage). The basic idea of the algorithm is to search for a list of breakers that will isolate all of the terminal buses of the device from in-service generation. The algorithm will also return a list of online generators that must be opened to isolate the bus as well. Remember that a breaker is specified by setting the **Branch Device Type** to *Breaker*.

Using the list of breakers and generators found from the algorithm, contingency analysis augments the contingency element list with a dynamically created list of contingency elements of action type *Open* for each breaker and generator device. The dynamically created elements are given the same [Model Criteria and Status](22-contingency-analysis-options.md#contingency-definition-display) as the contingency element that required their creation. If multiple *Open Breakers* contingency elements require the same breaker to open, one new contingency element will be created. When *Open Breakers* contingency elements have different Model Criteria, a new contingency element will be created for each unique Model Criteria. During the actual contingency solution, the *What Actually Occurred* list will be updated and can be examined in the results to determine what breakers were needed to isolate the device. Finally, after the contingency solution is completed, all of the dynamically created contingency elements are deleted, and as a result, the user can only see which breakers or generators were opened by looking at the *What Actually Occurred* list.

For brevity in the context of tools that either automatically switch or identify breakers to open a device, the term *breaker* is used to indicate any type of device that can be switched automatically. For contingency analysis, only **Branch Device Types** of *Breaker* will be switched, and *Disconnects* are not included. Other tools may allow different branch device types or user options to specify the branch device types. If the model has no branches defined with the specified branch device types, this option will not work because the algorithm will never find any breakers. See the [Full Topology Model](35-integrated-topology-processing.md#full-topology-model) topic for more information on defining breakers.

Algorithm Description for Open with Breakers During Contingency Analysis

The [general algorithm](35-integrated-topology-processing.md#open-with-breakers) for determining the breakers to open applies during contingency analysis. There are a few exceptions during contingency analysis as noted below:

> 1.  If there is another contingency action inside this same contingency that specifies an action type of *Open* or *OpenCBs* for a generator device, encountering that generator won't count toward the list of generators to open or the maximum of 10 buses to encounter with online generation. The same is done for any generator connected to a bus or inside an injection group, if the bus or injection group has a contingency action of type *Open* or *OpenCBs*.
> 2.  If there is a contingency action inside this same contingency that specifies a breaker with action type *Open Breakers*, the algorithm will traverse across this breaker (this models a breaker failure where a breaker is supposed to open but fails to operate.)
> 3.  If there is a contingency action inside this same contingency which specifies an action type of *Open* for a branch or DC line device, the algorithm will NOT traverse across that branch or DC line. The same is done for any branch which is part of a three-winding transformer, interface, or connected to a bus of the three-winding transformer, interface, or bus has a contingency action of type *Open*.
> 4.  While a list of generators to open is maintained, if no online load is encountered while traversing buses in the algorithm, then the generator OPEN contingency actions will not be created. This is because the breakers will create an isolated island with no load and thus opening the generation is not necessary.

---

<a id="contingency-element-close-breakers"></a>

## Contingency Element: Close Breakers

*Source: [`Content/MainDocumentation_HTML/Close_Breakers_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Close_Breakers_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are several places in Simulator where functionality is available to close breakers in order to energize a particular device or devices. This functionality is generally available when breakers, or other branch devices that are allowed to be automatically switched, are defined in the case. For some functionality, the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is required in addition to having breakers defined.

This overview is intended to provide information on which branch device types can be automatically switched, how breakers are selected, and the tools in Simulator that make use of close with breakers functionality. Additional information about how this functionality might work differently with specific tools will be described with those particular topics.

Branch Device Types that will Automatically Operate

The **Branch Device Type** field for a branch must be set to one of the following options in order for a branch to be considered a device that can automatically operate when using close breaker functionality:

  - Breaker
  - Load Break Disconnect
  - Disconnect
  - Fuse
  - Ground Disconnect

Not all of the types listed above can be used for automatic switching with all tools that allow this. The different tools will indicate which types are allowed. For brevity, the term *breaker* will be used throughout this discussion to indicate branch devices that can be automatically switched.

Added in version 20

For a branch to be considered for automatic switching it must also have its **Allow Open or Close Breakers** field set to *YES*. This field can be changed by the user, and there are several options that will update this field based on the present case. For more information on how this field can be updated by Simulator, see the [Update Allow Open or Close Breakers](05-case-information-displays-by-object-part2.md#update-allow-open-or-close-breakers) topic. When **Allow Open or Close Breakers** = *NO* and a branch is closed, it will be traversed when looking for breakers to close regardless of its Branch Device Type. Normally, in the search process if a branch is a Branch Device Type that is being included in the search, the search will terminate on a path that contains a closed branch.

Algorithm Description for Close Breakers

The following descriptions apply when using automated methods for closing breakers to energize a device. The method for identifying open breakers that might energize a particular device is the same whether using the automated methods to actually close breakers or a method with user input. Methods that allow user input will not actually close breakers until the user determines which breakers to actually close.

Single Terminal Devices

This includes buses, generators, loads, and switched shunts.

In order for a device to be considered de-energized, its terminal bus must be disconnected. If a device is already energized, no determination of breakers is made.

To determine if the device can be energized, the algorithm starts at the terminal bus of the device and traverses closed ac branches (non breakers). Closed breakers will not be traversed. If an open breaker is encountered, it is added to a list of potentially valid breakers. The traversal down a particular connection path terminates when a breaker is found or an open branch of any type is found. The algorithm completes when all paths have been explored.

Some functions require that no additional devices other than the one being checked can be energized by closing the selected breakers. If this check is in place when looking for breakers and it is determined that other devices will be energized, the algorithm is aborted and no breakers are found that can energize the selected device.

An additional check that is made to determine if a device can be energized is based on the normal status of a breaker. If more than one open breaker is found in the search for the open breakers, only those breakers that are normally closed will be considered valid. If only a single open breaker is found, normally open or closed breakers will be considered valid.

Once the final list of valid breakers is known, a final check is made to determine if closing these breakers will actually energize the device. If so, and the function calls for actually closing the breakers, the breakers will be closed.

If breakers are actually closed, the status of the device will also be set to closed if it is presently open. It is anticipated that the close breakers to energize functionality will be used with full-topology models in which the status of the device will always be closed and that breakers will be used to determine the actual energized status of the device, however, there is no strict requirement for this. In order to make sure that the device is actually energized, the status of the device might need to be set as well.

Multi-Terminal Devices

This includes branches (ac lines and transformers) and dc lines.

To find breakers that can be closed to energize a transmission branch, both terminal buses of the branch are examined. Breakers are found for each terminal bus separately by assuming that the branch itself is open and cannot be traversed. The breakers are then determined for each bus by using the same method described above for single terminal devices, i.e. the algorithm starts at a terminal bus and traverses closed ac branches (non breakers). A list of open breakers is built as each open breaker is encountered. The traversal down a particular connection path terminates when a breaker or an open branch of any type is found. The algorithm completes when all paths have been explored.

Because transmission branches are often closed to energize other devices, no restriction is placed on energizing other devices when looking for breakers to energize a branch; the algorithm does not abort when other devices are encountered that will also be energized by closing breakers to energize the branch.

Each set of breakers for the two terminals of the branch are checked separately for the condition based on the normal status of the breaker. If more than one open breaker is found in the set of open breakers, only those breakers that are normally closed will be considered valid. If only a single open breakers is found, normally open or closed breakers will be considered valid.

Once the final list of valid breakers is determined for each terminal bus, no additional check is made to determine if closing these breakers will actually energize the device. If the function calls for actually closing the breakers, all valid breakers will be closed. This is done because closing branches is often done to energize other devices and because closing the breakers that will energize one terminal bus might be needed to energize the other terminal bus.

If breakers are actually closed, the status of the branch will be set to closed if it is presently open.

Added in version 20, build on Oct. 17, 2017

If a branch or dc line is only open at one end, breakers will be identified to completely close the device. To determine if the device is not completely closed, the condition **Derived Status** \<\> *Closed* is used. Information on how Derived Status is determined is found [here](35-integrated-topology-processing.md#device-derived-status).

Aggregations

This includes interfaces, injection groups, or groups of objects of the same type selected via filtering.

When dealing with groups of objects, two methods of determining which breakers to close can be used. The first method assumes that all devices are handled separately and only breakers identified for each device will be examined when determining if a device can be energized by closing breakers. The second method assumes that breakers that are identified for one device might be needed to energize another device. When this method is used, breakers are identified for individual objects first, and then all breakers that have been identified for all devices are assumed to be available to energize any individual device. When identifying which breakers can be closed, the two methods described above for Single Terminal and Multi-Terminal Devices will be used.

Automated methods will generally assume the second method where all breakers can be used to energize individual devices. The CloseWithBreakers script command will allow user input on how to handle the breakers.

Close Normally Closed Disconnects Added in version 20

Some tools allow normally closed disconnects that are currently open to be closed during the process of identifying breakers. The tools that allow this will have an option for using this feature. Disconnects are considered to be only branches where **Branch Device Type** is *Disconnect*.

When using this option, if an open but normally closed disconnect is found in the process of searching for breakers, that disconnect will be included in the devices that will close to energize a device, and that disconnect will also be traversed in the search for additional breakers to close. The search on a path will terminate when an open breaker is found. This breaker will also be closed. Additionally, any disconnects that are in series with identified breakers will be closed if they are normally open. This will allow any disconnects that are found beyond the breakers to close to also be closed.

The normal status of a branch is determined by the **Normal Status** field.

Breakers in Series with Shunt Devices (Switched Shunts, Generators, and Loads) Added in version 20

When attempting to energize any device except for a switched shunt during the process of searching for breakers and disconnects to close, any breaker or disconnect that is strictly in series with only switched shunts and disconnects will be excluded from the switching devices that can close. This check effectively looks for switched shunts that are connected radially by a breaker or disconnect. This will prevent switched shunt breakers from operating inappropriately when closing a line that has a tap point with switched shunts.

Modified in version 20, build on May 18, 2018

In addition to switched shunts, generators and loads are included in the series check for breakers and disconnects when identifying which switching devices can close. If a particular switched shunt, generator, or load should be connected, only that particular device will be connected if other radially connected shunt devices are found.

Tools that Use Close Breakers Functionality

[Contingency Analysis](#contingency-element-dialog)

[Close Breakers to Energize Switched Shunts](05-case-information-displays-by-object-part3.md#switched-shunt-control)

[Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) (Used with PV and ATC tools)

Local menu option for display objects and [case information displays](04-model-explorer-and-case-information-part1.md#records-menu)

Several objects (buses, branches, dc lines, generators, loads, and switched shunts) have a special local menu option, **Close Breakers to Energize**, that allows them to be closed using breakers. This option is present on both the local menu for display objects and the local menu of case information displays for the specified types. This option does not require having the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) to work.

There are three sub-options available:

**Only Breakers**

Only **Branch Device Type** of *Breaker* will be included as valid switching devices.

**Breakers and Load Break Disconnects**

Only **Branch Device Types** of *Breaker* and *Load Break Disconnect* will be included as valid switching devices.

**With Options**

A dialog will open that allows for user input on the **Branch Device Types** that are included for valid switching devices. There is also an option **Close Normally Closed Disconnects**. If this option is selected, *Disconnects* will be included in the search algorithm as described in the **Close Normally Closed Disconnects section** above.

When using this option, a dialog will open that allows the user to determine which breakers should be closed instead of just closing the breakers automatically. The dialog that is presented will show the list of breakers that have been identified using the methods described above.

If attempting to energize a single terminal device, a single list of breakers, **Breakers for Terminal Bus**, will be displayed. If attempting to energize a multiple terminal device, two lists of breakers, will be displayed. One will show the list of breakers identified to energize the from terminal bus, **Breakers for From Terminal Bus**, and the other will show the list of breakers identified to energize the to terminal bus, **Breakers for To Terminal Bus**.

Regardless of how many lists of breakers are shown, they will be listed with a set of common fields:

**From Number, From Name\_Nominal kV, To Number, To Name\_Nominal kV, Circuit**

These are the key field identifiers for the breaker.

**Energized Bus Number**

At most one terminal bus of a selected breaker can be energized. This field indicates which, if any, of the buses is energized. This field is used to help determine which combination of breakers will actually energize the device.

**Normal Status**

This indicates the normal status of a breaker. Options are *Closed* or *Open*.

**Close?**

Set this to *YES* for this breaker to be closed when clicking the **Close Breakers** button. When the dialog is first opened, this field is set according to how automatic methods would choose which breakers are valid for closing based on the conditions described above in the **How Breakers are Selected** section.

There are some additional options on the dialog that provide information about the device to be energized:

**Device**

This identifies the device that is to be energized by closing breakers.

**Device Status**

This provides the status of the device prior to trying to energize the device. If the status is *Open*, the status will be set to *Closed* when the **Close Breakers** button is clicked.

**Check if Can Be Energized**

Clicking this button will run a check on the combination of breakers that have been selected for closing to determine if the device will actually be energized by closing them. The check is done without actually closing any breakers or changing the status of the device.

Use the following options to actually close breakers or just close the dialog:

**Close Breakers**

Click this button to close the breakers that have the **Close?** field set to *YES* and then close the dialog. If the status is *Open*, the status will be set to *Closed*.

**Cancel**

Click this button to close the dialog without changing the status of any breakers.

[CloseWithBreakers script command](03-cases-files-and-formats.md#auxiliary-file-format-aux)

Scheduled Actions

---

<a id="contingency-element-status"></a>

## Contingency Element Status

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Status.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Status.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Each contingency element has an associated Status. This determines if the action will be implemented at all, and if Model Criteria is defined, when that will be evaluated.

Some of the status options are available with Arming Status that can be specified with [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions) and Remedial Action Elements. The options that are applicable to Arming Status will be described with that option.

Status Field Options

Check

The action will only be executed if the Model Criteria is true or if no Model Criteria is specified. **Check** is the default status setting.

This action is available for the Arming Status used with Remedial Actions and Remedial Action Elements. A Remedial Action or Remedial Action Element will only be armed if its Arming Criteria is true or no Arming Criteria is specified.

Always

The action will always be executed, regardless of the Model Criteria.

This action is available for the Arming Status used with Remedial Actions and Remedial Action Elements. A Remedial Action or Remedial Action Element will always be armed regardless of its Arming Criteria.

Never

The action will never be executed, regardless of the Model Criteria. This allows you to disable a particular contingency action without deleting it.

This action is available for the Arming Status used with Remedial Actions and Remedial Action Elements. A Remedial Action or Remedial Action Element will never be armed, which means that it will never be executed regardless of its Arming Criteria. This allows you to disable a Remedial Action or Remedial Action Element without deleting it.

TopologyCheck

The Model Criteria for this action will be evaluated after **Check** and unconditional actions are applied but before the power flow is solved. This action will only be executed if the Model Criteria is true or if no Model Criteria is specified. If no Model Criteria is specified, this action will be applied when the **Check** actions are evaluated. When evaluated before the power flow is solved, this type of action is only useful with topology changes because line flow and bus voltage changes will not take affect until after the power flow is solved.

Additionally, any **TopologyCheck** actions that have not been applied will be evaluated again AFTER the power flow is solved. **TopologyCheck** actions will be treated the same as **PostCheck** actions when they are evaluated after the power flow is solved. This will allow evaluation of any Model Criteria that might depend on other **TopologyCheck** actions being applied. If any actions, either **TopologyCheck** or **PostCheck**, are applied, any remaining **TopologyCheck** actions will again be evaluated BEFORE the power flow is solved again and after the topology update has been performed. This process will continue until no additional **TopologyCheck** or **PostCheck** actions are applied.

This behavior only occurs when the [Calculation Method](22-contingency-analysis-options.md#basics) for the analysis is set to *Full Power Flow* and solving the ac power flow or using [Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis). Otherwise, the **TopologyCheck** status instead acts as a **Check** status.

PostCheck

This action will be considered AFTER all **Check, Always,** and **TopologyCheck** actions have been performed and the power flow solution solved. If no Model Criteria is specified, this action will be applied when the **Check** actions are evaluated, i.e. before the power flow is solved. If the Model Criteria specified for the **PostCheck** action is met in the solved power flow solution, this action is taken and the power flow is solved again. If the model conditions are not met, the action is skipped. This process repeats recursively for all **Postcheck** actions until complete.

Additionally, any **TopologyCheck** actions that have not been applied will be evaluated along with the **PostCheck** actions AFTER the power flow is solved. See the **TopologyCheck** section above about more information on how the TopologyCheck actions are evaluated before and after the power flow is solved.

This behavior only occurs when the [Calculation Method](22-contingency-analysis-options.md#basics) for the analysis is set to *Full Power Flow* and solving the ac power flow or using [Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis). Otherwise, the **PostCheck** status instead acts as a **Check** status.

SolutionFail

Added in Version 19

This action is considered immediately after a power flow solution is attempted during the process of [running a contingency](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis). If a solution failure is encountered the power flow solution state will be restored to what existed before the failed solution. Then if this action's Model Criteria is met (or none is defined) the action will be applied and another power flow solution will be attempted.

See the topic [Running the Contingency Analysis](23-contingency-analysis-running-and-results.md#running-the-contingency-analysis) for more information on how contingency actions are processed based on Status and other settings. Additionally, [Transient Models](22-contingency-analysis-options.md#transient-models) can be included in a steady-state contingency run. This topic will describe where they are included in the process.

---

<a id="type-3-winding-transformer"></a>

## Type: 3-Winding Transformer

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_3W_Transformer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_3W_Transformer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *3-Winding Transformer*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected three-winding transformer to *Open* if the three-winding transformer Status is *Closed*. If the three-winding transformer Status is already *Open*, this action does nothing.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected three-winding transformer to *Closed* if the three-winding transformer Status is *Open*. If the three-winding transformer Status is already *Closed*, this action does nothing.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

---

<a id="type-abort"></a>

## Type: Abort

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Abort.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Abort.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Abort*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

There are no action settings for the abort action.

The abort contingency will immediately abort a contingency once the conditions are met for the abort action. No other actions will be implemented, no violations will be reported, and no custom monitors will be reported.

---

<a id="type-area"></a>

## Type: Area

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Area.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Area.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Area*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Set To

Make-up power is important to compensate for any real power (MW) changes during a contingency. Based on system conditions, the make-up power for an area might need to be different during a contingency than the area control settings used in the base case. This is the main use of the area contingency action.

When the Area type is selected, the contingency element dialog will be modified to allow input of options specific to this element type. The only option available with this action is to set the **Area Control Type**. Available control types are *Off AGC*, *Part. AGC*, *Area Slack*, and *IG Slack*. The [Area Control](10-power-flow-solution-and-options-part3.md#area-control) topic provides more information about these control types. If selecting *Area Slack*, the **Area Control Object** must be set to select the bus that will act as the area slack during the contingency action. If selecting *IG Slack*, the **Area Control Object** must be set to select the injection group that will act as the area slack during the contingency action.

In order for the Area contingency action to work correctly, there are contingency and power flow solution options that must be set correctly. Simulator does not automatically set these options so the user must make sure they are set.

  - Area control must be enabled in the contingency base case, i.e. the [Power Flow Solution Option for Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) must be set to *Disable (Use the Area and Super Area Dispatch settings)*.
  - The contingency **[Make-Up Power](22-contingency-analysis-options.md#basics)** option must be set to *Same as Power Flow case*.
  - The option to *Disable Automatic Generation Control (AGC)* found with the [Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options) must NOT be selected.

Another suggestion, although not a strict requirement, is that the area should be on area control prior to contingency analysis if a control type other than *Off AGC* is going to be set during a contingency. If a large ACE exists in the base case with area control off, switching the area on control during the contingency will zero out the ACE in addition to compensating for required make-up power.

---

<a id="type-branch"></a>

## Type: Branch

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Branch.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Branch.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Branch*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

If **Branch Device Types** other than *Line* exist in the case, a special filtering drop down will appear that allows selecting branches by device type. Selecting a particular type will limit the entries in the chooser display to branches of that type.

Open

The Open action will set the Status of the selected branch to *Open*if the branch Status is *Closed*. If the branch Status is already *Open,* this action does nothing.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected branch to *Closed* if the branch Status is *Open*. If the branch Status is already *Closed*, this action does nothing.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Set To

The only option available with this action is **MVA Limit**, which will change the contingency limit of the selected branch for the duration of the contingency. The **[Amount](#contingency-element-dialog)** must be specified for the new limit in MVA.

---

<a id="type-bus"></a>

## Type: Bus

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Bus.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Bus.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Bus*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of all ac branches connected to the selected bus to *Open*. If all of the ac branches are already open, then this action does nothing.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

---

<a id="type-dc-converter"></a>

## Type: DC Converter

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_DC_Converter.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_DC_Converter.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *DC Converter*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected dc converter to *Open*. If the dc converter is already open, this action does nothing.

Close

The Close action will set the Status of the dc converter to *Closed*. When selecting the Close action, the **Amount** must be specified for the new Setpoint of the dc converter in either **MW** or **Amps**. If specifying the Setpoint in **MW**, the Set Mode of the converter will be set to *Power*. If specifying the Setpoint in **Amps**, the Set Mode of the converter will be set to *Current*.

Set To

The Set To action will set the selected dc converter’s Setpoint to a specified **[Amount](#contingency-element-dialog)** and could possibly change the Set Mode of the converter. If the Set Mode of the converter is presently *Voltage*, no changes are made. The Setpoint can be set in **Percent**, **MW**, or **Amps**. When the Setpoint is set in **Percent**, the Setpoint is set to the specified percentage of the contingency reference state Setpoint of the converter and the Set Mode remains unchanged. When the Setpoint is set in **MW**, the Setpoint is set to the specified MW amount, and the Set Mode is changed to *Power* if the Set Mode is presently *Current*. When the Setpoint is set in **Amps**, the Setpoint is set to the specified current amount, and the Set Mode is set to *Current* if the Set Mode is presently *Power*.

Change By

The Change By action will change the selected dc converter's Setpoint by the specified **[Amount](#contingency-element-dialog)** and could possibly change the Set Mode of the converter. If the Set Mode of the converter is presently *Voltage*, no changes are made. The Setpoint can be changed in **Percent**, **MW**, or **Amps**. When the dc converter’s Setpoint is changed in **Percent**, the Setpoint is changed by the specified percentage of the contingency reference state Setpoint of the line and the Set Mode remains unchanged. When the Setpoint is changed in **MW**, the Setpoint is changed by the specified MW amount, and the Set Mode is changed to *Power* if the Control Mode is presently *Current*. When the Setpoint is changed in **Amps**, the Setpoint is changed by the specified current amount, and the Set Mode is set to *Current* if the Control Mode is presently *Power*.

When the Set Mode changes from either *Power* to *Current* or from *Current* to *Power*, the appropriate conversions are done so that the resulting Setpoint value reflects the original Setpoint and the change in Setpoint in the same units. The Mode of the multi-terminal dc line to which the converter belongs as well as all other non-voltage controlling converters will be set to the same Set Mode.

---

<a id="type-dc-line"></a>

## Type: DC Line

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_DC_Line.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_DC_Line.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *DC Line*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Control Mode of the selected dc line to *Blocked*. If the dc line is already blocked, this action does nothing.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Control Mode of the selected dc line to either *Power* or *Current*. When selecting the Close action, the **Amount** must be specified for the new Setpoint of the dc line in either **MW** or **Amps**. If specifying the Setpoint in **MW**, the Control Mode of the dc line will be set to *Power*. If specifying the Setpoint in **Amps**, the Control Mode of the dc line will be set to *Current*.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Set To

The Set To action will set the selected dc line’s Setpoint or resistance to a specified **[Amount](#contingency-element-dialog)** and could possibly change the Control Mode of the line. The Setpoint can be set in **Percent**, **MW**, or **Amps**. When the dc line’s Setpoint is set in **Percent**, the Setpoint is set to the specified percentage of the contingency reference state Setpoint of the line and the Control Mode remains unchanged. If the Control Mode is presently *Blocked*, the resulting Setpoint will be 0 regardless of the Amount entered. When the Setpoint is set in **MW**, the Setpoint is set to the specified MW amount, and the Control Mode is changed to *Power* if the Control Mode is presently *Current*. If the Control Mode is *Blocked* or *Power*, then the Control Mode remains unchanged. When the Setpoint is set in **Amps**, the Setpoint is set to the specified current amount, and the Control Mode is set to *Current* if the Control Mode is presently *Power*. If the Control Mode is *Blocked* or *Current*, then the Control Mode remains unchanged.

The **R (Ohms)** setting will change the dc line's resistance to the specified Amount in ohms.

Change By

The Change By action will change the selected dc line’s Setpoint by the specified **[Amount](#contingency-element-dialog)** and could possibly change the Control Mode of the line. The Setpoint can be changed in **Percent**, **MW**, or **Amps**. When the dc line’s Setpoint is changed in **Percent**, the Setpoint is changed by the specified percentage of the contingency reference state Setpoint of the line and the Control Mode remains unchanged. If the Control Mode is presently *Blocked*, the resulting Setpoint will be 0 regardless of the Amount entered. When the Setpoint is changed in **MW**, the Setpoint is changed by the specified MW amount, and the Control Mode is changed to *Power* if the Control Mode is presently *Current*. If the Control Mode is *Blocked* or *Power*, then the Control Mode remains unchanged. When the Setpoint is changed in **Amps**, the Setpoint is changed by the specified current amount, and the Control Mode is set to *Current* if the Control Mode is presently *Power*. If the Control Mode is *Blocked* or *Current*, the Control Mode remains unchanged.

When the Control Mode changes from either *Power* to *Current* or from *Current* to *Power*, the appropriate conversions are done so that the resulting Setpoint value reflects the original Setpoint and the change in Setpoint in the same units.

---

<a id="type-generator"></a>

## Type: Generator

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Generator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Generator.htm)*

The following describes the options available when creating a contingency element of type *Generator*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected generator to *Open* if the generator Status is *Closed*. If the generator Status is already *Open*, this action does nothing.

When using the Open action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in generation due to the contingency action.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected generator to *Closed* if the generator Status is *Open*. If the generator Status is already *Closed*, this action does nothing.

When using the Close action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in generation due to the contingency action.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Move

The Move action allows the transferring of generation from an existing generator bus to another bus in a specified **[Amount](#contingency-element-dialog)**. A generator move can be done on a bus basis (impacting the total generation of all generators at the selected bus) or can be targeted at a specific generator. Generators that are adjusted by the Move action will have their AGC Status set to *No*. If there are no on-line generators at the selected generator bus, no generation move will occur. Generation may be moved in **Percent** or **MW**. A **Percent** move will move the specified percent of the contingency reference state generator MW and Mvar to the defined **Bus to Move to**. A **MW** move will move the specified amount of generator MW to the Bus to Move to. The Move amount can be either positive or negative. A positive amount will decrease the output of the selected generator bus, and a negative amount will increase the output of the selected generator bus. The Bus to **Move to** will respond accordingly.

If a generator already exists at the bus to which the generation is being moved, the generation at that bus is adjusted according to the move amount. If a generator does not exist but a load exists, then the load is adjusted by the move amount. If no generator or load exists, then a load is added at the bus and the injection is set according to the move amount. In terms of power injection, positive generation is the same as negative load.

Move actions are not allowed for Contingency Primary Elements used with [CTG Combo Analysis](25-ctg-combo-analysis.md#ctg-combo-analysis-overview).

Set To

The Set To action will set the selected bus’ generation or specified generator's parameters to a specified **[Amount](#contingency-element-dialog)**. Generator Set To actions can be done on a bus basis (impacting the total generation of all generators at the selected bus) or can be targeted at a specified generator. Generators that are adjusted by a Set To action will have their AGC Status set to *No*. If there are no on-line generators at the selected generator bus, no generation change will occur. Generator parameters can be set in **Percent**, **MW**, **Mvar** or **Setpoint Voltage**. When the generation is set in **Percent**, total generator MW output will be set to a value based on the specified percent of the contingency reference state total generator MW output. When the generation is set in **MW**, total generator MW output will be set to the specified MW amount. When the generation is set in **Mvar**, total generator Mvar output will be set to the specified Mvar amount (AVR is set to NO). When the generation is set in **Setpoint Voltage**, the voltage set-point of all generators at the selected bus will be set to the specified amount in per unit.

When using the Set To action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in generation due to the contingency action.

Change By

The Change By action will change the selected bus’ generation or specified generator's parameters by a specified **[Amount](#contingency-element-dialog)**. Generator Change By actions can be done on a bus basis (impacting the total generation of all generators at the selected bus) or can be targeted at a specified generator. Generators that are adjusted by a Change By action will have their AGC Status set to *No*. If there are no on-line generators at the selected generator bus, no generation change will occur. Generator parameters can be changed in **Percent**, **MW**, **Mvar** or **Setpoint Voltage**. When the change is in **Percent**, total generator MW output will be changed based on the specified percent of the contingency reference state total generator MW output. When the change is in **MW**, total generator MW output will be changed by the specified MW amount. When the change is in **Mvar**, total generator Mvar output will be changed by the specified Mvar amount (AVR is set to NO). When the change is in **Setpoint Voltage**, the voltage set-point of all generators at the selected bus will be changed by the specified amount in per unit.

When using the Change By action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in generation due to the contingency action.

---

<a id="type-injection-group"></a>

## Type: Injection Group

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Injection_Group.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Injection_Group.htm)*

The following describes the options available when creating a contingency element of type *Injection Group*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of all generators and loads in the selected injection group to *Open* if the Status is *Closed*. If the Status is already *Open*, this action does nothing. If the injection group contains other injection groups, the Status of the generators and loads in the other injection groups will also be set to *Open*.

When using the Open action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for real power changes due to the status changes of generators and loads in the contingency action.

The **Number Elements** option is available to open a specified number of elements in the injection group. The **[Amount](#contingency-element-dialog)** fields will be available to specify the number. Elements will be opened in the order of highest participation factor to lowest. The Status of generators, loads, and switched shunts in the injection group will be set to *Open* if the Status is *Closed*. If the Status is already *Open*, no changes are made to an element.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of all generators and loads in the selected injection group to *Closed* if the Status is *Open*. If the Status is already *Closed*, this action does nothing. If the injection group contains other injection groups, the Status of the generators and loads in the other injection groups will also be set to *Closed*.

When using the Close action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for real power changes due to the status changes of generators and loads in the contingency action.

Added in version 20

The **Number Elements** option is available to close a specified number of elements in the injection group. The **[Amount](#contingency-element-dialog)** fields will be available to specify the number. Elements will be closed in the order of highest participation factor to lowest. The Status of generators, loads, and switched shunts in the injection group will be set to *Closed* if the Status is *Open*. If the Status is already *Closed*, no changes are made to an element.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Set To

The Set To action will set the real power injection of the injection group to the specified **[Amount](#contingency-element-dialog)**. If loads are included in the injection group, the Mvar load will be adjusted by keeping the power factor constant. The injection can be set in **Percent** or **MW**. When setting the injection in **Percent**, the real power injection is set to the specified percent of the contingency reference state real power injection. The real power injection of the injection group is determined by taking the difference between the total generator MW and total load MW in the injection group. When setting the injection in **MW**, the real power injection is set to the specified amount.

**Scale Order** Modified in version 19, build on May 3, 2016

This option determines how the participation points within the injection group will be adjusted to implement the desired action. The following choices are available:

Proportional

All online generators and loads in the injection group with non-zero participation factors are adjusted according to their relative participation factors to meet the desired injection.

Merit Order

Generators and loads will be adjusted in order of highest relative participation factor to lowest with each generator and load in the list being adjusted until it hits either its maximum or minimum MW limit before moving on to the next element. This process continues until the desired injection is met. Mvar load will be adjusted by keeping a constant power factor.

Generators will not be opened in this process, which means all online generators will continue to provide Mvar support.  Loads that have both their minimum and maximum MW limits set to zero will not be allowed to increase. They can only decrease to 0 MW.

Merit Order Open

If this option is chosen and the MW injection being requested is *lower* (change is *negative*) than the existing MW injection of the injection group, the merit order dispatch will be modified by only opening generators. (Note: PowerWorld's expectation is that the Change By option would most frequently be used with this option.) In this case, the generator in the injection group with the highest participation factor will have its status changed to *Open*, followed by the second generator and so on. If the MW injection being requested is *higher* (change is *positive*) than the existing MW injection of the injection group, the merit order dispatch will be modified by opening loads. In this case, the load in the injection group with the highest participation factor will have its status changed to *Open*, followed by the second load and so on.

If the MW output requested is *higher* (change is *positive*) than the present MW injection, and there are no loads in the injection group, generators will be increased toward their maximum MW output as though the **Merit Order** option was chosen. If the MW injection requested is *lower* (change is *negative*) than the present MW injection, and there are no generators in the injection group, loads will be increased toward their maximum MW output as though the **Merit Order** option was chosen.

When an injection group contains another injection group, the entire contained injection group will be opened when it is encountered based on its participation factor.

When opening in merit order there are two options used to specify how this is done:

**Do Not Exceed Amount** - This will open generators or loads until the amount of MW opened is as close to the desired amount as possible but has *not exceeded* the desired amount of change. If opening an element will cause the amount of MW opened to exceed the desired amount, that element will be skipped and the next one in merit order will be examined.

**Allow to Exceed Amount** - This will open generators or loads until the amount of MW opened is equal to or greater than the desired amount.

Best Fit Open Added in version 20

When using this option, typically only generators or loads will be opened, but not both. Which types of objects are opened depends on the direction of change for the MW injection being requested. If this option is chosen and the MW injection being requested is *lower* (change is *negative*) than the existing MW injection of the injection group, typically only generators will be opened to achieve the change. If the MW injection being requested is *higher* (change is *positive*) than the existing MW injection of the injection group, typically only loads will be opened to achieve the change. Atypical opening of generators or loads would occur if they are operating at negative output.

Participation factors do not impact which objects are opened. All generators or loads defined with the injection group can participate if they are online. Specifically which generators or loads open depends on an algorithm that attempts to get the actual injection change within 5% of the desired injection change by opening the smallest number of generators or loads. If **Allow to Exceed Amount** is used, the action will attempt to achieve an injection change that is above the desired change, but within 5%. If **Do Not Exceed Amount** is used, the action will attempt to achieve an injection change that is below the desired change, but within 5%.

When an injection group contains another injection group, the injection impact of the entire injection group is taken into account in the best fit algorithm. The entire injection group will be opened if needed.

Modified in version 22, build on May 26, 2021

The algorithm attempts to find the smallest number of devices that can meet the desired amount. The more devices there are to consider the more time it takes to determine all of the possible combinations. If there are more than 20 devices (2^20 = 1,048,572 combinations), the devices will be sorted from high to low impact and examined in blocks of 20. If the entire 20 devices are needed to meet the desired amount all will be opened and then the next block of 20 devices will be used to meet the remaining amount. This process continues until it is not necessary that a set of 20 devices are all required to meet the remaining amount. This block will use the combination algorithm to fine tune which devices are opened.

When using the Set To action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for real power changes due to the status changes of generators and loads in the contingency action.

Change By

The Change By action will change the real power injection of the injection group to the specified **[Amount](#contingency-element-dialog)**. If loads are included in the injection group, the Mvar load will be adjusted by keeping the power factor constant. The injection can be set in **Percent**, **MW**, or **MW Effect**. When setting the injection in **Percent**, the real power injection is set to the specified percent of the contingency reference state real power injection. The real power injection of the injection group is determined by taking the difference between the total generator MW and total load MW in the injection group. When setting the injection in **MW**, the real power injection is set to the specified amount.

MW Effect option was added in Version 19

When choosing the **MW Effect** option, the Scale Order option **Best Fit Open** is automatically checked. The value that is specified with the action will be the desired MW Effect that the action should have. The participation factors defined with the Injection Group will be interpreted as effectiveness factors akin to transfer distribution factors. These factors are supplied as input by the user when defining the injection group. The effectiveness factors are multiplied by the present output of generators (or loads) in the injection group to determine how much effect they will have if dropped. If the effect is in the opposite direction of the desired effect, that object will be skipped. The action will find the smallest number of generator (or loads) to drop that results in a total MW Effect that is within 5% of the desired MW Effect. If the option is picked to **Allow to Exceed Amount** then the action will attempt to achieve a MW effect that is above the value specified, but within 5%. If the option is picked to **Do Not Exceed Amount**, then the action will attempt to achieve a MW effect that is below the value specified, but within 5%.

**Scale Order** Modified in version 19, build on May 3, 2016

This option determines how the participation points within the injection group will be adjusted to implement the desired action. The following choices are available:

Proportional

Same as **Set To** section.

Merit Order

Same as **Set To** section.

Merit Order Open

Same as **Set To** section.

Best Fit Open

Same as **Set To** section for changing in **MW** or **Percent**. This option could only be used with **MW Effect** in Version 19, but it is available with **Percent**, **MW**, and **MW Effect** in in Version 20.

When using the Change By action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for real power changes due to the status changes of generators and loads in the contingency action.

Evaluate Part Points in Reference State

When using an action that requires participation factors, this option can be used to indicate that participation factors should be determined in the contingency reference state. This will only be done for participation points using having an **Initial Value** that indicates the factor should be dynamically determined and the **AutoCalc** field is set to *YES* for the participation point. See the [participation point records](05-case-information-displays-by-object-part3.md#participation-point-records-display) topic for more information on these settings.

Accounting for Generation Drop Overlapping

Injection group actions can be used to implement remedial action schemes (RAS). These schemes can be made up of generation drop scenarios in which the same generators can be part of one or more RAS. Too much generation might be dropped if the amount of overlapping generation is not accounted for. If using either the **Set To** or **Change By** action type and using the options for **Merit Order Open**, overlapping of generators is accounted for unless the option [Disable Gen Drop Overlap](22-contingency-analysis-options.md#basics) is checked. When accounting for overlapping generators, generators that have already been dropped will be included in the total of generation that is dropped for a particular injection group, which will prevent that injection group from exceeding the desired amount of generation drop.

As an example assume that Injection Group A and Injection Group B are both using Generator 1 that is online at 100 MW. Injection Group A action occurs first and needs to drop 500 MW. As part of this action, Generator 1 drops 100 MW and the remaining 400 MW is made up from other generators in Injection Group A. Injection Group B action occurs next and needs to drop 300 MW. When using the gen overlap accounting, the 100 MW that has already been dropped by Generator 1 is included in the total drop for Injection Group B. This means that Injection Group B only needs to drop an additional 200 MW from other generators. By accounting for the overlap, Injection Group B does not exceed its total desired gen drop. If we were not accounting for the overlap, Injection Group B would drop 300 MW from generators in addition to Generator 1. This would mean that the total gen drop for Injection Group B is 400 MW.

When accounting for overlapping generators, the [What Occurred](23-contingency-analysis-running-and-results.md#what-occurred) results will indicate how much gen overlap was encountered during the contingency for each injection group action. There are also two fields that are available with [contingency records](22-contingency-analysis-options.md#contingencies-tab) that give information about how much gen dropped occurred during a contingency. The **Dropped Gen** field indicates the total amount of MW generation that was dropped by injection groups using the specific option settings required for the accounting of gen drop overlap. The **Overlap Gen** field indicates how much MW overlap was found when dropping generation from injection groups using the specific option settings required for the accounting of gen drop overlap.

Modified in version 24

When using the **Best Fit Open Scale Order** option, generators that have already been dropped due to other injection group actions will be included if the impact of dropping the generator is in the same direction as specified by the Amount of the action. The Amount will be adjusted to include the impact of generation that has already been dropped, and the Best Fit algorithm will be applied on this adjusted amount. When determining if a change is close enough to the desired amount, 5% of the original Amount will be used as the tolerance.

---

<a id="type-interface"></a>

## Type: Interface

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Interface.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Interface.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Interface*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of all ac branches in the selected interface to *Open*. If all of the ac branches are already open, then this action does nothing. The Status of any dc lines that are part of the interface will remain unchanged due to the contingency action. If the selected interface contains additional interfaces, the Status of all ac branches in the additional interfaces will also be set to *Open*.

Added in version 19, build on November 21, 2016

In addition to all ac branches being opened, all generators and loads will have their Status set to *Open* . This includes generators and loads in injection groups and any generators and loads contained in other interfaces contained by the interface being opened.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of all ac branches in the selected interface to *Closed*. If all of the ac branches are already closed, then this action does nothing. The Status of any dc lines, generators, loads, or injection groups that are part of the interface will remain unchanged due to the contingency action. If the selected interface contains additional interfaces, the Status of all ac branches in the additional interfaces will also be set to *Closed*.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Set To Added in version 19, build on May 3, 2016

The Set To action will set the real power flow on the interface to the specified **[Amount](#contingency-element-dialog)**by opening devices in the interface. The real power flow can be set in **Percent** or **MW**. When setting the flow in **Percent**, the flow is set to the specified percent of the contingency reference state real power flow. When setting the flow in **MW**, the real power flow is set to the specified amount. The treatment of interfaces within interfaces will be to open the entire contained interface.

**Scale Order**

This option determines how the devices within the interface will be opened to implement the desired action. The following choices are available:

Merit Order Open

Each element within an interface has a **Par Fac** field that specifies the merit order in which the flow will be adjusted by opening elements. Each element is opened in the order of highest to lowest Par Fac until the desired flow is met. If opening an element will cause a change in flow that is not in the desired direction, that element is not opened and the next element in merit order is examined. The flow of an element is determined by its MW flow multiplied by the **Weighting** factor specified with the element. See the **Specifying Participation Factors for Interfaces** section below for more information on how to specify these.

Depending on the mix of elements included within the interface, the Weighting should be used to determine the correct direction of flow for an element. As an example, the flow for a load will be negative because it is a negative injection into the system. If using an interface that includes branches as proxies for multiple loads in addition to some single loads, the loads in the interface should use a Weighting of -1 to get a positive flow value. The branches used as proxies for multiple loads should be specified in the direction of positive flow so that the total flow on the interface is positive. The desired Amount can then be specified relative to this positive flow.

There are two options that determine how the opening of elements is done:

**Do Not Exceed Amount** - This will open elements until the amount of MW opened is as close to the desired amount as possible but has *not exceeded* the desired amount. If opening an element will cause the amount of MW opened to exceed the desired amount, that element will be skipped and the next one in merit order will be examined.

**Allow to Exceed Amount** - This will open elements until the amount of MW opened is equal to or greater than the desired amount.

**Best Fit Open** Added in version 20

When using this option the participation factors of interface elements do not impact which elements are opened. The flow on an element, which is determined by its MW flow multiplied by the **Weighting** factor specified with the element, is used to determine which elements should be opened. If the flow on an element is in the appropriate direction to achieve the desired flow change on the interface, that element is eligible for being opened.

To determine if an element will actually be opened, the best fit algorithm attempts to determine the combination of elements that will achieve the desired flow change by opening the least amount of elements and achieving an actual flow change within 5% of the desired flow change. If **Allow to Exceed Amount** is used, the action will attempt to achieve a flow change that is above the desired change, but within 5%. If **Do Not Exceed Amount** is used, the action will attempt to achieve a flow change that is below the desired change, but within 5%.

Modified in version 22, build on May 26, 2021

The algorithm attempts to find the smallest number of devices that can meet the desired amount. The more devices there are to consider the more time it takes to determine all of the possible combinations. If there are more than 20 devices (2^20 = 1,048,572 combinations), the devices will be sorted from high to low impact and examined in blocks of 20. If the entire 20 devices are needed to meet the desired amount all will be opened and then the next block of 20 devices will be used to meet the remaining amount. This process continues until it is not necessary that a set of 20 devices are all required to meet the remaining amount. This block will use the combination algorithm to fine tune which devices are opened.

Change By Added in version 19, build on May 3, 2016

The Change By action will change the real power flow in the interface by the specified **[Amount](#contingency-element-dialog)**. The real power flow can be changed in **Percent**, **MW**, or **MW Effect**. When changing the flow in **Percent**, the flow is changed by the specified percent of the contingency reference state real power flow. When changing the flow in **MW**, the real power flow is changed by the specified amount. The treatment of interfaces within interfaces will be to open the entire contained interface.

Added in version 20

When choosing the **MW Effect** option, the Scale Order option **Best Fit Open** is automatically checked. The value that is specified with the action will be the desired MW Effect that the action should have. The participation factors, **Par Fac** field, defined with the interface elements will be interpreted as effectiveness factors akin to transfer distribution factors. These factors are supplied as input by the user when defining the interface. The effectiveness factors are multiplied by the present MW flow of elements in the interface to determine how much effect they will have if dropped. The flow of an element is determined by its MW flow multiplied by the **Weighting** factor specified with the element. If the effect of a particular element is in the opposite direction of the desired effect, that element is skipped. The action will find the smallest number of elements to drop that results in a total MW Effect that is within 5% of the desired MW Effect. If the option is picked to **Allow to Exceed Amount** then the action will attempt to achieve a MW effect that is above the value specified, but within 5%. If the option is picked to **Do Not Exceed Amount**, then the action will attempt to achieve a MW effect that is below the value specified, but within 5%.

**Scale Order**

This option determines how the devices within the interface will be opened to implement the desired action. The following choices are available:

Merit Order Open

Same as **Set To** section.

Best Fit Open Added in Version 20

Same as **Set To** section for changing in **MW** or **Percent**. This option can also be used with **MW Effect** changes as described above.

Evaluate Part Points in Reference State Added in version 19, build on May 3, 2016

When using an action that requires participation factors, this option can be used to indicate that participation factors should be determined in the contingency reference state.

Specifying Participation Factors for Interfaces Added in version 19, build on May 3, 2016

When using an action that requires participation factors, the participation factors can be set through the [Interface Display](05-case-information-displays-by-object-part3.md#interface-display) using the **Par Fac** field. The Par Fac can be specified as a floating point value, a field associated with the interface element, or a Model Expression. To specify a field, the following syntax should be used: `<Field>`*variablename*. To specify a Model Expression, the following syntax should be used: `<Expression>`*ModelExpressionName*. When using either a field or model expression, checking the **Evaluate Part Points in Reference State** option will use the value determined in the contingency reference state, otherwise the present value will be used.

---

<a id="type-line-shunt"></a>

## Type: Line Shunt

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Line_Shunt.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Line_Shunt.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Line Shunt*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected line shunt in the branch from or to side to *Open*. If the line shunt are already open, then this action does nothing. The Status of any line shunt that are part of the branch will remain unchanged due to the contingency action.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected line shunt in the branch from or to side, to *Closed*. If the line shunt are already closed, then this action does nothing. The Status of any line shunt that are part of the branch will remain unchanged due to the contingency action.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

---

<a id="type-load"></a>

## Type: Load

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Load.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Load.htm)*

The following describes the options available when creating a contingency element of type *Load*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected load to *Open* if the load Status is *Closed*. If the load Status is already *Open*, this action does nothing.

When using the Open action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in load due to the contingency action.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected load to *Closed* if the load Status is *Open*. If the load Status is already *Closed*, this action does nothing.

When using the Close action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in load due to the contingency action.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Move

The Move action allows the transferring of load from an existing load bus to another bus by a specified **[Amount](#contingency-element-dialog)**. A load move can be done on a bus basis (impacting the total load of all loads at the selected bus) or can be targeted at a specific load. Load may be moved in **MW (const pf)**, **Percent**,**MW**, or **Mvar**. The load amount that is moved is the total actual load and may be different than the nominal load if the area of the load has a Load MW Multiplier other than 1.0 or the load contains constant impedance or constant current components. If there is no on-line load at the selected load bus or the bus at which the load is located is *Open*, no load move will occur. A **MW (const pf)** move will move the specified amount of load MW to the **Bus to Move to** while moving a Mvar amount that will maintain a constant power factor at the selected load bus. A **Percent** move will move the specified percent of the contingency reference state load MW and Mvar to the defined Bus to Move to. A **MW** move will move the specified amount of the load MW to the Bus to Move to. A **Mvar** move will move the specified amount of the load Mvar to the Bus to Move to. The Move amount can be either positive or negative. A positive amount will decrease the load at the selected bus, and a negative amount will increase the load at the selected bus. The Bus to **Move to** will respond accordingly.

If a load already exists at the bus to which the load is being moved, the load at that bus is adjusted according to the move amount. If no load exists, then a load is added at the bus and the load is set according to the move amount.

Move actions are not allowed for Contingency Primary Elements used with [CTG Combo Analysis](25-ctg-combo-analysis.md#ctg-combo-analysis-overview).

Set To

The Set To action will set the selected bus’ load parameters to a specified **[Amount](#contingency-element-dialog)**. Load Set To actions can be done on a bus basis (impacting the total load of all loads at the selected bus) or can be targeted at a specific load. Load parameters can be set in **MW (const pf)**, **Percent**, **MW**, or **Mvar**. The load value that is set for each of these options is the actual constant power component of the load. This value may be different than the nominal constant power component of the load if the area that contains the load has a Load MW Multiplier other than 1.0. If there is no on-line load at the selected load bus and the bus at which the load is located is *Closed*, load status at the selected load bus will change so that one load is *Closed* and the total constant power load at the bus will be set to the specified amount. If the bus at which the load is located is *Open* or there is no existing load, either *Open* or *Closed*, at that bus, then no load change will occur. When the load is set in **MW (const pf)**, the actual constant power MW will be set to the specified amount and the actual constant power Mvar will be set so that a constant power factor is maintained at the load bus. When the load is set in **Percent**, the actual constant power MW and Mvar will be set to the specified percent of the contingency reference state load MW and Mvar. When the load is set in **MW**, the actual constant power MW at the selected load will be set to the specified amount. When the load is set in **Mvar**, the actual constant power Mvar at the selected load will be set to the specified amount.

When using the Set To action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in load due to the contingency action.

Change By

The Change By action will change the selected bus’ load parameters by a specified **[Amount](#contingency-element-dialog)**. Load Change By actions can be done on a bus basis (impacting the total load of all loads at the selected bus) or can be targeted at a specific load. Load parameters can be changed in **MW (const pf)**, **Percent**, **MW**, or **Mvar**. The load value that is changed for each of these options is the actual constant power component of the load. This value may be different than the nominal constant power component of the load if the area that contains the load has a Load MW Multiplier other than 1.0. If there is no on-line load at the selected load bus or the bus at which the load is located is *Open*, no load move will occur. When the load is changed in **MW (const pf)**, the actual constant power MW will be changed by the specified amount and the actual constant power Mvar will be changed so that a constant power factor is maintained at the load bus. When the load is changed in **Percent**, the actual constant power MW and Mvar will be changed by the specified percent of the contingency reference state load MW and Mvar. When the load is changed in **MW**, the actual constant power MW at the selected load bus will be changed by the specified amount. When the load is changed in **Mvar**, the actual constant power Mvar at the selected load bus will be changed by the specified amount.

When using the Change By action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in load due to the contingency action.

---

<a id="type-multi-section-line"></a>

## Type: Multi-Section Line

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Multi_Section_Line.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Multi_Section_Line.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Multi-Section Line*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of all ac branches in the selected Multi-Section line to *Open*. If all of the ac branches are already open, then this action does nothing. The Status of any branches that are part of the Multi-Section line will remain unchanged due to the contingency action.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of all ac branches in the selected Multi-Section line to *Closed*. If all of the ac branches are already closed, then this action does nothing. The Status of any branches that are part of the Multi-Section line will remain unchanged due to the contingency action.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

---

<a id="type-phase-shifter"></a>

## Type: Phase Shifter

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Phase_Shifter.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Phase_Shifter.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Phase Shifter*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Set To

The Set To action will set the middle of the regulation range of the selected phase shifter to the specified **[Amount](#contingency-element-dialog)**. The middle of the regulation range is calculated by taking the average of the Regulation Minimum MW Flow and Regulation Maximum MW Flow. The middle of the regulation can be set in **Percent** or **MW**. If the middle of the regulation range is set in Percent, the middle of the range is set to the specified percent of the contingency reference state middle of the regulation range. If the middle of the regulation range is set in **MW**, then the middle of the regulation range is set to the specified amount. Regardless of the method used to set the middle of the regulation range, the regulation range will remain the same, but the Regulation Minimum MW Flow and Regulation Maximum MW Flow will be adjusted so that the specified middle of the regulation range is met.

Added in version 20

By selecting the **Degrees** option the phase angle of the phase shifter can be set to the specified Amount. Automatic control for this phase shifter will be disabled so that it will not be adjusted by any automatic control schemes.

Change By

The Change By action will change the middle of the regulation range of the selected phase shifter by the specified **[Amount](#contingency-element-dialog)**. The middle of the regulation range is calculated by taking the average of the Regulation Minimum MW Flow and the Regulation Maximum MW Flow. The middle of the regulation range can be changed in **Percent** or **MW**. When the middle of the regulation range is changed in Percent, the change is based on the specified percent of the contingency reference state middle of the regulation range. When the middle of the regulation range is changed in **MW**, the middle of the present regulation range is changed by the specified amount. Regardless of the method used to change the middle of the regulation range, the regulation range will remain the same, but the Regulation Minimum MW Flow and Regulation Maximum MW Flow will be adjusted so that the specified middle of the regulation range is met.

Added in version 20

By selecting the **Degrees** option the phase angle of the phase shifter will be changed from its present value by the specified Amount. Automatic control for this phase shifter will be disabled so that it will not be adjusted by any automatic control schemes.

---

<a id="type-series-capacitor"></a>

## Type: Series Capacitor

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Series_Capacitor.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Series_Capacitor.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Series Capacitor*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Bypass

The Bypass action will change the Bypass Status of the selected series capacitor to *Bypassed* if the Bypass Status is *Not Bypassed*. If the Bypass Status is already *Bypassed*, this action does nothing.

Added in version 19, build on April 8, 2016

If the series capacitor Bypass Status is not already *Bypassed*, an explicit breaker is found in parallel with the series capacitor, and the Status of the series capacitor is *Closed*, the breaker will be closed instead of changing the Bypass Status.

Inservice

The Inservice action will change the Bypass Status of the selected series capacitor to *Not Bypassed* if the Bypass Status is *Bypassed*. If the Bypass Status is already *Not Bypassed*, this action does not change the Bypass Status.

Added in version 19, build on April 8, 2016

If an explicit breaker is found in parallel with the series capacitor and the Status of the series capacitor is *Closed*, the breaker will be opened instead of changing the Bypass Status.

Set To

The Set To action will set the series reactance of the series capacitor to a specified **[Amount](#contingency-element-dialog)**. The reactance may be set in **X (percent)** or **X (per unit)**. If the reactance of the series capacitor is set in **X (percent)**, the per unit reactance is set to the specified percent of the per unit reactance of the series capacitor in the reference state. If the reactance is set in **X (per unit)**, the per unit reactance of the series capacitor is set to the specified amount.

---

<a id="type-solve-power-flow"></a>

## Type: Solve Power Flow

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Solve_Power_Flow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Solve_Power_Flow.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Solve Power Flow*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

The solve power flow type is unique in that you can include an action that forces Simulator to solve the power flow as part of the contingency. There are rare special cases of sophisticated contingency definitions this can be used for, as requested by one or more PowerWorld customers. The load flow is already generally solved for each contingency as part of the processing.

If a contingency has one or more Solve Power Flow actions, then there will be a few changes in how the contingency definition display behaves.

  - Sorting of the list of actions is no longer allowed. This is because the order of the actions is now important to how the contingency is processed.
  - When you right-click on the list of contingency actions there will be two new options for Move Up and Move Down. These can be used to reorder the actions.
  - On the Contingency Definition Dialog, there will be up/down arrows on the right of the dialog that may be used to reorder the actions.

Implementation

Solve power flow actions impose an order in which actions are applied. Groups of actions that are applied together are separated by Solve Power Flow actions. The [Status](#contingency-element-status) of an action will dictate how it fits into this order. TOPOLOGYCHECK actions will ignore this order and be checked and applied as necessary with each group of actions. Any CHECK actions that are part of [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions) or [Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions) will be checked and applied if necessary in the first group of actions. POSTCHECK actions will be checked and applied if necessary after all groups of actions have been applied.

---

<a id="type-script"></a>

## Type: Script

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Script.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Script.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in version 20

The following describes the options available when creating a contingency element of type *Script*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

There are no action settings for a script action.

Command

This edit box will contain the script command to be run as a contingency action. Multiple script commands can be entered and must be specified as a single line of text with the multiple commands separated by semi-colons. If an unknown script command is entered or other inappropriate formatting is included, the contingency will be aborted. When the contingency is aborted the results will be reported in the same manner as the [Abort](#type-abort) contingency action.

Available script commands are described Auxiliary File Format document posted on the PowerWorld website at [http://www.powerworld.com/files/Auxiliary-File-Format.pdf](https://www.powerworld.com/WebHelp/files/Auxiliary-File-Format.pdf).

---

<a id="type-substation"></a>

## Type: Substation

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Substation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Substation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the options available when creating a contingency element of type *Substation*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

This action will open the selected substation. All tie lines from the substation and all branches within the substation will have their Status set to *Open*.

Open Breakers

This will open all branches within the substation and branches that are ties from the substation by changing the status of breakers. See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Set To Added in version 20

The Set To action will set the MW output of online generators in the substation to the specified **[Amount](#contingency-element-dialog)**. The MW output can be set in **Percent** or **MW**. When setting the MW output in **Percent**, the output is set to the specified percent of the contingency reference state MW output of the generators in the substation. When setting the output in **MW**, the MW output of generators in the substation is set to the specified amount. Individual generators within the substation are adjusted based on a weighting of their present output divided by the total present output of all online generators in the substation. Generator limits are not enforced, but generation is not allowed to go negative. If a generator is adjusted by this action, its AGC flag is set to *NO* so that it will not be adjusted by any automatic MW control schemes.

Change By Added in version 20

The Change By action will change the MW output of online generators in the substation by the specified **[Amount](#contingency-element-dialog)**. The MW output can be changed in **Percent** or **MW**. When changing the MW output in **Percent**, the output is changed by the specified percent of the contingency reference state MW output of the generators in the substation. When changing the output in **MW**, the MW output of generators in the substation is changed by the specified amount. Individual generators within the substation are adjusted based on a weighting of their present output divided by the total present output of all online generators in the substation. Generator limits are not enforced, but generation is not allowed to go negative. If a generator is adjusted by this action, its AGC flag is set to *NO* so that it will not be adjusted by any automatic MW control schemes.

---

<a id="type-switched-shunt"></a>

## Type: Switched Shunt

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_Switched_Shunt.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_Switched_Shunt.htm)*

The following describes the options available when creating a contingency element of type *Switched Shunt*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected switched shunt to *Open* if the switched shunt Status is *Closed*. If the switched shunt Status is already *Open*, this action does nothing.

When using the Open action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in the real power portion of the switched shunt due to the contingency action.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the Status of the selected switched shunt to *Closed* if the switched shunt Status is *Open*. If the switched shunt Status is already *Closed*, this action does nothing.

When using the Close action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in the real power portion of the switched shunt due to the contingency action.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Move

The Move action allows the transferring of switched shunt MW and/or Mvar from an existing switched shunt bus to another bus by the specified **[Amount](#contingency-element-dialog)**. A switched shunt move can be done on a bus basis (impacting the total shunt output of all switched shunts at the selected bus) or can be targeted at a specific switched shunt. During the move action, the nominal values of the switched shunts are adjusted, and switched shunts that are adjusted have their Control Mode set to *Fixed*. If there are no switched shunts at the selected switched shunt bus with a Status of *Closed*, no switched shunt move will occur. Switched shunt Moves may be done in **Percent**, **MW**, or **Mvar**. A switched shunt Move in **Percent** will move the specified percent of contingency reference state nominal MW and Mvar at the switched shunt bus to the defined **Bus to Move to**. A **MW** move will move the specified amount of switched shunt MW to the Bus to Move to. A **Mvar** move will move the specified amount of switched shunt Mvar to the Bus to Move to. The Move amount can be either positive or negative. A positive amount will decrease the nominal MW and/or Mvar at the selected switched shunt bus, and a negative amount will increase the nominal MW and/or Mvar at the selected switched shunt bus. The Bus to Move to will respond accordingly.

If a switched shunt exists at the bus to which the switched shunt MW and/or Mvar is being moved, the switched shunt at that bus is adjusted according to the move amount. If there are existing switched shunts at the Bus to Move to but all of them have a Status of *Open*, the first switched shunt Status will be set to *Closed*, the Control Mode will be set to *Fixed*, and the nominal MW and/or Mvar will be adjusted according to the move amount. If no switched shunt exists at the Bus to Move to, then the nominal constant impedance load is adjusted according to the move amount. If no switched shunt exists at that bus, then a switched shunt is added and the nominal injection is adjusted according to the move amount.

Move actions are not allowed for Contingency Primary Elements used with [CTG Combo Analysis](25-ctg-combo-analysis.md#ctg-combo-analysis-overview).

Set To

The Set To action will set the selected bus’ switched shunt parameters to a specified **[Amount](#contingency-element-dialog)**. Switched shunt Set To actions can be done on a bus basis (impacting the total shunt output of all switched shunts at the selected bus) or can be targeted at a specific switched shunt. Switched shunts that are adjusted during Set To actions have their Control Mode set to *Fixed*. Switched shunt parameters can be set in **Percent**, **MW**, **Mvar**, or **Setpoint Voltage**. When a switched shunt bus is set in **Percent**, the nominal MW and Mvar are set to the specified percent of the contingency reference state nominal MW and Mvar of the switched shunt bus. When the switched shunt bus is set in **MW**, the nominal MW is set to the specified amount. When the switched shunt bus is set in **Mvar**, the nominal Mvar is set to the specified amount. When the switched shunt bus is set in **Setpoint Voltage**, the Target Value of the controllable switched shunt at the bus is set to the specified amount. Switched shunts may either regulate voltage or generator Mvar. The amount entered for the Setpoint Voltage is considered to be in per unit when the switched shunt is regulating voltage and is considered to be in Mvar when regulating generator Mvar. If there are no switched shunts at the selected bus with a Status of *Closed* when setting MW or Mvar amounts, the Status of the first switched shunt at the bus will be set to *Closed*, the Control Mode will be set to *Fixed*, and the nominal value will be set appropriately.

When using the Set To action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in switched shunt MW due to the contingency action.

Change By

The Change By action will change the selected bus’ switched shunt parameters by a specified **[Amount](#contingency-element-dialog)**. Switched shunt Change By actions can be done on a bus basis (impacting the total shunt output of all switched shunts at the selected bus) or can be targeted at a specific switched shunt. Switched shunts that are adjusted during the Change By action have their Control Mode set to *Fixed*. Switched shunt parameters can be changed in **Percent**, **MW**, **Mvar**, or **Setpoint Voltage**. When a switched shunt bus is changed in **Percent**, the nominal MW and Mvar are changed by the specified percent of the contingency reference state nominal MW and Mvar of the switched shunt bus. When the switched shunt bus is changed in **MW**, the nominal MW is changed by the specified amount. When the switched shunt bus is changed in **Mvar**, the nominal Mvar is changed by the specified amount. When the switched shunt bus is changed in **Setpoint Voltage**, the Target Value of the controllable switched shunt at the bus is change by the specified amount. Switched shunts may either regulate voltage or generator Mvar. The amount entered for the Setpoint Voltage change is considered to be in per unit when the switched shunt is regulating voltage and is considered to be in Mvar when regulating generator Mvar. If there are no switched shunts at the selected bus with a Status of *Closed* when setting MW or Mvar amount, the Status of the first switched shunt at the bus will be set to *Closed*, the Control Mode will be set to *Fixed*, and the nominal value will be set appropriately.

When using the Change By action, the **Make-up Power Sources** button is enabled and power sources can be specified to account for the changes in switched shunt MW due to the contingency action.

---

<a id="type-vsc-dc-line"></a>

## Type: VSC DC Line

*Source: [`Content/MainDocumentation_HTML/Contingency_Element_Type_VSC_DC_Line.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Element_Type_VSC_DC_Line.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

(Support for this contingency element type was added in Version 20 build on January 11, 2018)

The following describes the options available when creating a contingency element of type *VSC DC Line (Voltage Source Converter)*. Contingency elements are created from the [Contingency Element Dialog](#contingency-element-dialog), and additional details of how to create contingency elements can be found here.

Action Settings

Open

The Open action will set the Status of the selected VSC DC line to *Open*. If the VSC DC line is already open, this action does nothing.

Open Breakers

See the special topic on [Open Breakers](#contingency-element-open-breakers) for more detail.

Close

The Close action will set the status of the selected VSC DC line to *Closed*. When selecting the Close action, the **Amount** must be specified for the new Setpoint of the VSC DC line in **MW**. Either the From or To Converter must be configured to a DC Setpoint mode of Power. The converter which is set to the power mode will have its setpoint changed.

Close Breakers

See the **Close Breakers for Contingencies** topic on the [Contingency Element Dialog](#contingency-element-dialog) topic.

Set To

The Set To action will set the selected VSC DC line’s Setpoint or resistance to a specified **[Amount](#contingency-element-dialog)**. The Setpoint can be set in **Percent** or **MW**. When the VSC DC line’s Setpoint is set in **Percent**, the Setpoint is set to the specified percentage of the contingency reference state Power Setpoint of the line. If the status is presently *Open*, the resulting Setpoint will be 0 regardless of the Amount entered. Either the From or To Converter must be configured to a DC Setpoint mode of Power. The converter which is set to the power mode will have its setpoint changed.

The **R (Ohms)** setting will change the dc line's resistance to the specified Amount in ohms.

Change By

The Change By action will change the selected VSC DC line’s Setpoint or resistance to a specified **[Amount](#contingency-element-dialog)**. The Setpoint can be set in **Percent** or **MW**. When the VSC DC line’s Setpoint is set in **Percent**, the Setpoint is set to the specified percentage of the contingency reference state Power Setpoint of the line. If the status is presently *Open*, the resulting Setpoint will be 0 regardless of the Amount entered. Either the From or To Converter must be configured to a DC Setpoint mode of Power. The converter which is set to the power mode will have its setpoint changed.
