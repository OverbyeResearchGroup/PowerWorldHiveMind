---
title: "Contingency Analysis — Overview and Records"
part: "Contingency Analysis"
chapter_file: "21-contingency-analysis-overview-and-records.md"
topics: 19
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Contingency Analysis — Overview and Records

What contingency analysis does, available contingency actions, case references and contingency records.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (19)**

- [Contingency Analysis Overview](#contingency-analysis-overview)
- [Available Contingency Actions](#available-contingency-actions)
- [Contingency Analysis Power Flow Solution Options](#contingency-analysis-power-flow-solution-options)
- [Contingency Case References](#contingency-case-references)
- [Reference State Information](#reference-state-information)
- [Defining the Reference State](#defining-the-reference-state)
- [Reference State Solution Options](#reference-state-solution-options)
- [Defining Contingencies](#defining-contingencies)
- [Automatically Generating a Contingency List](#automatically-generating-a-contingency-list)
- [Loading a Contingency List from a File](#loading-a-contingency-list-from-a-file)
- [PSS/E Contingency Format](#psse-contingency-format)
- [PSS/E Load Throw Over Files](#psse-load-throw-over-files)
- [Concise Contingency and Remedial Action Scheme Format](#concise-contingency-and-remedial-action-scheme-format)
- [Saving Contingency Records to a File](#saving-contingency-records-to-a-file)
- [Global Actions](#global-actions)
- [Contingency Blocks](#contingency-blocks)
- [Remedial Actions](#remedial-actions)
- [Contingency Category](#contingency-category)
- [Dependency Explorer](#dependency-explorer)

---

<a id="contingency-analysis-overview"></a>

## Contingency Analysis Overview

*Source: [`Content/MainDocumentation_HTML/contingency_analysis_an_introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/contingency_analysis_an_introduction.htm)*

Contingency analysis is a vitally important part of any power system analysis effort. Industry planners and operators must analyze power systems covering scenarios such as the long-term effects on the transmission system of both new generation facilities and projected growth in load. Market analysts and planners must make informed decisions regarding transactions for energy trade - whether that trade is for the next hour or months down the road. PowerWorld Simulator’s Contingency Analysis tools provide the ability not only to analyze a power system in its base case topology, but also to analyze the system that results from any statistically likely contingent scenario.

Industry planning and operating criteria often refer to the n-1 rule, which holds that a system must operate in a stable and secure manner following any single transmission or generation outage. In PowerWorld Simulator, the individual contingency conditions can also be tailored to consist of either a single element (such as the loss of a transmission line or transformer), or multiple elements (such as the loss of a generator, several buses and a number of branches simultaneously). See [Available Contingency Actions](#available-contingency-actions) for a complete list of possible contingency actions.

Simulator can be set to use a Full Newton solution or use a DC Load Flow method to analyze each contingency. The Full Newton approach is not as fast as a DC Load Flow, but the results tend to be significantly more accurate and allow for gauging voltage/var effects.

The [Tutorial Links](49-distributed-computing-and-tutorials.md#tutorials) is a great place to start learning about using Simulator’s Contingency Analysis Tool.

---

<a id="available-contingency-actions"></a>

## Available Contingency Actions

*Source: [`Content/MainDocumentation_HTML/Contingency_Analysis_Available_Contingency_Actions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Analysis_Available_Contingency_Actions.htm)*

The following contingency actions can be applied to specific device types. More details on exactly how the actions can be defined is found with the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) information:

Transmission Lines and Transformers (Branches)

  - The opening or closing of transmission lines and transformers
  - Operating breakers to open or close transmission lines and transformers
  - Setting the contingency rating of a line for the duration of the contingency

Individual Generators, Loads, or Switched Shunts

  - Loss or recovery of a particular generator, load, or switched shunt
  - Operating breakers to open or close a particular generator, load, or switched shunt

All of or particular Generation, Load, or Switched Shunt at a particular bus

  - Movement of generation, load, or switched shunt MWs or Mvars to another terminal bus
  - Changing or setting of load, switched shunt, or generator MWs or Mvars
  - Change or setting of a generator or switched shunt voltage setpoint
  - Operating breakers to open or close a particular generator, load or switched shunt

Bus

  - Opening of all lines connected to a bus
  - Operating breakers to isolate a bus

Interface

  - Opening of all elements in an interface except dc lines
  - Closing of all ac lines or transformers in an interface
  - Operating breakers to open or close all lines or transformers in an interface
  - Setting or Changing the MW flow by a Percent or MW value by opening elements in merit order
  - Setting or Changing the MW flow by a Percent or MW value by opening elements using a best fit order algorithm
  - Changing the new MW flow to achieve a specified MW Effect

Multi-Section Line

  - Opening or closing of a multi-section line. The same thing can be accomplished by selecting a line section that is part of a multi-section line using a Branch action, but this action makes it easier to select a multi-section line.

Injection Group

  - Opening, closing, or changing of output of all devices in an injection group
  - Opening or closing a specified number of devices in an injection group
  - Setting or Changing the net MW injection by a Percent or MW value and by proportion, by merit order, or by using a best fit algorithm
  - Changing the net MW injection to achieve a specified MW Effect
  - Operating breakers to open or close all devices in an injection group
  - Operating breakers to open a specified number of devices in an injection group

Series Capacitor

  - Bypassing or placing series capacitors in service
  - Setting of the Series Reactance by percent or to a particular per unit value

DC Transmission Line

  - Opening or closing DC Lines
  - Changing DC Line setpoint MW or Amp values
  - Changing the resistance of the DC line
  - Operating breakers to open or close DC lines

DC Converter

  - Opening or closing DC Converters
  - Setting or Changing the setpoint MW or Amp values

Phase-Shifting Transformer

  - Setting or Changing the Phase-Shifter Regulation MW value
  - Setting or Changing the phase shifter phase angle

Three-Winding Transformer

  - Opening or closing all legs of three winding transformers
  - Operating breakers to open or close all legs of a three winding transformer

Line Shunt

  - Opening or closing a line shunt

Area

  - Setting the area control type and area slack

Substation

  - Opening an entire substation
  - Operating breakers to open an entire substation
  - Setting or Changing the MW output of generators in the substation

Abort

  - Abort the contingency without applying any additional actions

Solving the Power Flow

Contingency Block

---

<a id="contingency-analysis-power-flow-solution-options"></a>

## Contingency Analysis Power Flow Solution Options

*Source: [`Content/MainDocumentation_HTML/Contingency_Solution_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Solution_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

By default, the contingency analysis will use the same options as the power flow algorithm when solving each contingency. You may also override these options for all contingencies, and/or for a specific contingency. This results in the ability to set the power flow solution options in contingency analysis at three different levels (see the **Contingency Combination Analysis** section below for additional options when using combination analysis):

1.  Contingency Specific Options (see [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog))
2.  Contingency Analysis Options (see [Contingency Options Tab](22-contingency-analysis-options.md#options-tab))
3.  General Power Flow Solution Options (see [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options))

When Simulator executes a particular contingency, it will first look at options specified for that contingency. Any options that are defined for this contingency will be used. Other options set as *Use Default* will look to the Contingency Analysis Options. Again, any options that are defined for contingency analysis will be used. Finally, options marked in the Contingency Analysis Options as *Use Default* will be set to the same setting as the power flow solution options.

In order to specify options for a specific contingency, click on the **Define/Modify Solution Options** button on the [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog). In order to specify options for all contingencies, click on the **Define/Modify Solution Options** button on the [Contingency Options: Modeling/Basics page](22-contingency-analysis-options.md#options-tab). Both of these will bring up the Contingency Analysis Power Flow Solution Options dialog.

This dialog contains many options regarding the power flow solution. For options that are a numerical value, just specify a new value to use. For options that are specified by a check-box, the check-box will have three settings: *use option,do no use option*, and *use default*. For a more detailed explanation of each option see the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) topic.

To set the values to be the same as the present power flow solution options, click the **Set same as for Power Flow** button. To set all options back to use default, click the **Clear All Settings** button.

The option to *Dynamically Add/Remove Slack Buses as Topology is Changed (Allow Multiple Islands)* is handled in a special manner when applying the contingency options. This option cannot be set to allow multiple islands if it has previously been set to not allow multiple islands. This will be enforced when the contingency solution options are applied. The main reason for having this option as part of the contingency solution options is for buses that become disconnected from the system slack bus during a contingency to form a dead island rather than selecting a new slack bus for the newly formed island and leaving it energized.

Contingency Combination Analysis

When running contingency combination analysis two additional levels of solution options are possible. Solution options can be specified for all primary contingencies and/or options can be specified for individual primary contingencies. Additionally the existing options with the secondary contingencies will also be used when applying secondary contingencies. This will allow the primary contingencies and secondary contingencies to be solved with different options. If options for secondary contingencies are not specified then the primary contingency options will be used for secondary contingencies as well.  Here are the levels at which solution options can be specified for combination analysis:

1.  (Secondary) Contingency Specific Options (see [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog))
2.  Contingency Analysis Options (see [Contingency Options Tab](22-contingency-analysis-options.md#options-tab))
3.  Primary Contingency Specific Options (see [Contingency Primary Definition dialog](52-additional-linked-topics-part1.md#contingency-definition-dialog))
4.  Contingency Combination Analysis Options (see [Contingency Combination Analysis dialog](25-ctg-combo-analysis.md#ctg-combo-contingency-analysis-dialog))
5.  General Power Flow Solution Options (see [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options))

---

<a id="contingency-case-references"></a>

## Contingency Case References

*Source: [`Content/MainDocumentation_HTML/Contingency_Case_References.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Case_References.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Contingency Analysis always stores a Reference State or pre-contingency state. The Reference State stores information pertaining to various network objects and solution options. See [Reference State Information](#reference-state-information) for details on the specific information stored.

The reference state is loaded into memory prior to the execution of each contingency during automatic processing of the contingency list. This ensures that all contingencies start from a common Base Case. Furthermore, the system is set back to the reference state following completion of the automatic processing. The system is not restored to the reference state when the **Solve Selected Contingency** option is selected from the Contingency Record Display’s local menu (see [Reference State Solution Options](#reference-state-solution-options) for more information).

The reference state is always stored in Simulator after the first instance of opening the contingency analysis form, with a few exceptions. If you switch to Edit Mode or add or delete MW Transactions between areas, the contingency reference state will be destroyed. If the reference state is still in memory, opening the contingency analysis again may result in a prompt from the program. This prompt will ask you if you wish to set the contingency analysis reference state to the current state of the system (in case you have made changes since the last contingency analysis run), or if you wish to keep the existing contingency analysis reference state (which was set by previously opening the contingency analysis dialog.) If you choose the second option, any changes you may have made to the case outside of the contingency analysis will be lost, as the reference state stored with the contingency analysis tool will reset the system state to the reference state.

Click [here](#defining-the-reference-state) for information on defining the reference state.

---

<a id="reference-state-information"></a>

## Reference State Information

*Source: [`Content/MainDocumentation_HTML/Contingency_Case_References_State_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Case_References_State_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator stores the following information with the Contingency Analysis Reference State. This list should include all of the information that can be directly accessed by the user. Care should be taken with modifying any data that is not stored in the reference state as it will not be restored at the end of each contingency.

Bus State

  - In or out of service
  - Voltage Magnitude and angle
  - Boolean expression stating whether any load exists at the bus (this is used because some of the contingency actions such as *MOVE GEN* will create a fictitious load if there is no generation at the destination bus)
  - MW Marginal Cost
  - GIC DC Voltage
  - Conductance (G)
  - Susceptance (B)

Line State

  - In or out of service
  - Bypassed?
  - Transformer Control - Control Mode (YES/NO for transformers, Not Enabled/Enabled for Power Flow/Enabled for OPF Only for phase shifters), Regulation Minimum/Maximum, Line Drop Compensation Reactance (X), Use Line Drop Compensation, GIC Induced Var Losses, Magnetizing G and B
  - Tap ratio
  - Phase shift
  - Series Reactance X (only for series capacitors because a contingency element can change this)
  - GIC DC Current
  - GIC Induced DC Voltage
  - DFACTs Operational Mode
  - Line Limits

Line Shunt State

  - In or out of service
  - Conductance (G)
  - Susceptance (B)

Generator State

  - In or out of service
  - MW Output
  - Mvar Output
  - Max/Min MW Output
  - Participation Factor
  - Max/Min Mvar Output
  - Voltage Setpoint
  - Regulated Bus Number
  - AGC Status (YES/NO)
  - AVR Status (YES/NO)
  - Capability Curve
  - Use Capability Curve
  - Line Drop Compensation Impedance
  - Line Drop Compensation Status (YES/NO/POSTCTG)
  - Economic Dispatch Loss Sensitivity

Load State

  - In or out of service
  - Constant power MW and Mvar components of load
  - Constant current MW and Mvar components assuming one per unit voltage
  - Constant impedance MW and Mvar components assuming one per unit voltage
  - Distributed generation Status, MW Input, and Mvar Input
  - MW Scale
  - Mvar Scale
  - AGC Status
  - Min/Max Load MW

Switched Shunt State

  - In or out of service
  - Auto Control
  - Nom value MW, Mvar
  - Control mode (FIXED/DISCRETE/CONTINUOUS/SVC)
  - Description of Mvar blocks
  - Low/high range for control regulation
  - Target value for control regulation
  - Discrete Control Options - Use Continuous Element, Single Largest Step, Minimum and Maximum Susceptance
  - Use High Target Value and High Target Value

Area State

  - Unspecified MW Transactions
  - MW Scale
  - Mvar Scale
  - AGC Status
  - Area Slack - either bus or injection group
  - Loss Percent
  - Auto Shunts
  - Auto XF

Super Area State

  - MW Scale
  - Mvar Scale
  - AGC Status
  - Use Area Participation Factors
  - Loss Percent

DC Line State

  - In or out of service
  - Control Mode
  - Setpoint
  - Setpoint voltage
  - Resistance
  - Compounding Resistance
  - Rectifier and Inverter Tap Value
  - Firing Angles (alpha and gamma)

Multi-Terminal DC Line State

  - In or out of service
  - Control Mode
  - Bus of ac converter station controlling dc voltage
  - For each converter - converter setpoint, firing angle, tap, and in or out of service

VSC DC Line State

  - In or out of service
  - AC and DC modes at each terminal
  - AC and DC setpoints at each terminal

Substation State

  - GIC DC Ground Voltage
  - GIC DC Neutral Voltage
  - GIC Grounding Resistance (Ohms)

MW Transaction

  - MW Value
  - Enabled Status

Limit Group State

  - Rating sets for normal operation (Line, Interface…A, B, etc…)
  - Bus rating sets for contingency operation

Power Flow Solution Options

The following options can be set as part of the contingency-specific power flow solution options:

  - MVA Convergence Tolerance
  - Maximum Number of Iterations
  - Initialize from Flat Start
  - Disable Power Flow Optimal Multiplier
  - Dynamically add/remove slack buses as topology is changed (Allow Multiple Islands)
  - Disable Checking Gen MVAR Limits
  - Check Gen MVAR Limits Immediately
  - Check Gen MVAR Back Off Limits Immediately
  - Disable Switched Shunt Control
  - Disable SVC Control
  - Disable Treating Continuous SSs as PV Buses
  - Disable LTC Transformer Control
  - Min. Sensitivity for LTC Control
  - Disable Balancing of Parallel LTC Taps
  - Disable Phase Shifter Control
  - Model Phase Shifters as Discrete Controls
  - Enforce Generator MW Limits
  - Prevent Controller Oscillations
  - Maximum Number of Voltage Control Loop Iterations
  - Min. pu voltage for constant power load
  - Min. pu voltage for constant current load

The following are included as part of the reference state but are not included as contingency-specific power flow solution options:

  - Disable Angle Rotation Processing
  - Disable Angle Smoothing
  - Sharing of generator vars across groups of buses during remote regulation
  - Disable Transformer Tap Control if Tap Sens. is the Wrong Sign
  - Transformer Stepping Methodology
  - Use Topology Processing
  - Close Breakers to Energize Switched Shunts
  - Disable D-FACTS Control

---

<a id="defining-the-reference-state"></a>

## Defining the Reference State

*Source: [`Content/MainDocumentation_HTML/Contingency_Case_References_Defining_the_Reference_State.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Case_References_Defining_the_Reference_State.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The reference state is initially defined as the power system state that exists when the contingency analysis is run for the first time for a given power flow case during a Simulator session. The exception to this is that it might be set to the current system state when the dialog is open, prior to running any analysis, if the [Setting Reference State When Contingency Analysis is Opened](22-contingency-analysis-options.md#miscellaneous) option is specified to set the reference case each time that the dialog is opened.

See [Reference State Information](#reference-state-information) for details on the specific information stored in the reference state.

![Contingency Reference State](images/Contingency_Reference_State.jpg)

**Setting the reference state**

The reference state can be changed each time that the Contingency Analysis Dialog is opened after having already established a reference state. The [Setting Reference State When Contingency Analysis is Opened](22-contingency-analysis-options.md#miscellaneous) option is available for determining how the reference state should be set any time that the dialog is opened during a Simulator session.

To change the reference while the Contingency Analysis Dialog is open, select the **Set as Reference** option from the [Other \>](23-contingency-analysis-running-and-results.md#other-contingency-actions) button on the bottom of the Contingency Analysis Dialog. The reference state can also be redefined using the **Solve and Set as Reference** option from the Contingency Record Display’s local menu (See [Reference State Solution Options](#reference-state-solution-options) for more information).

---

<a id="reference-state-solution-options"></a>

## Reference State Solution Options

*Source: [`Content/MainDocumentation_HTML/Contingency_Case_References_Reference_State_Solution_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Case_References_Reference_State_Solution_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**![Contingency Reference State Solution Options](images/Contingency_Reference_State_Solution_Options.jpg)**

**Contingency Record Display Local Menu**

When you solve contingencies one at a time, you may choose between the **Solve Selected Contingency** and **Solve and Set As Reference** options from the [Contingency Record Display's](22-contingency-analysis-options.md#contingencies-tab) [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options).

**Solve Selected Contingency**

This causes Simulator to first load the reference state into memory then solve the contingency. Following the solution, *the reference state is not restored*; the system state then reflects the power system flows of the post-contingency state. The advantage of this approach is the ability to implement a contingency and then modify the system looking for possible actions that might mitigate violations caused by the contingency. Be aware; however, that prior to solving another contingency, Simulator will reset the system state to reference state thereby removing all modifications made following the previous contingency solution. The user may also automatically restore the system state to reference state by selecting **Other \> Restore Reference** from the Contingency Analysis Dialog.

**Solve and Set As Reference**

This acts the same as **Solve Selected Contingency** with one exception. After executing the contingency, the post-contingency state is automatically set as the reference state. As a result, all subsequent contingencies will use the post-contingent state as the Reference State.

When selecting this option for the first time after the contingency dialog has been opened, a prompt will be presented asking if you want to continue with this operation. Selecting **Yes** will continue with the contingency being solved and the reference state being set to the state after the contingency solution. Selecting **No** will abandon this operation and the contingency will not be solved and the reference state will not be set. Selecting **Yes to All** will continue with the contingency being solved and the reference state being set to the state after the contingency solution. An answer of **Yes** will then be assumed for each subsequent time that this option is selected, and the prompt will not appear. The prompt will appear again once the contingency dialog is closed and reopened again.

Click [here](#reference-state-information) for details on the specific information stored in the reference state.

Click [here](#defining-the-reference-state) for information on defining the reference state.

---

<a id="defining-contingencies"></a>

## Defining Contingencies

*Source: [`Content/MainDocumentation_HTML/Contingency_Analysis_Defining_Contingencies.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Analysis_Defining_Contingencies.htm)*

There are four options for defining contingencies:

  - [Load Contingencies from a File](#loading-a-contingency-list-from-a-file)
  - [Auto Insert Contingencies](#automatically-generating-a-contingency-list)
  - Use the local menu to **Insert** contingencies
  - Use the local menu to **Quick Insert a Single Element Contingency**

---

<a id="automatically-generating-a-contingency-list"></a>

## Automatically Generating a Contingency List

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_Contingencies.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_Contingencies.htm)*

Simulator allows you to automatically generate a contingency list containing branch, generator, switched shunt, substation and/or bus outages. To accomplish this, click the **Auto Insert** button along the bottom of the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) or right-click on the list of contingencies table in the [Contingencies Tab](22-contingency-analysis-options.md#contingencies-tab) and select **Insert Special \> Auto Insert Contingencies…**. This opens the **Auto Insertion of Contingency Records dialog**.

When automatically inserting contingencies, you must specify the type, options and naming conventions you want for the new contingencies. You must also specify whether to delete or retain existing contingencies.

Auto Insertion of Contingency Records Dialog

The Auto Insertion of Contingencies dialog has the following controls:

Automatically generate contingency involving a…

The options available in this box define what to add to each automatically inserted contingency element. You can choose single transmission line, transformer, transmission line or transformer, 3-Winding transformer, generating unit, bus, switched shunt, or substation contingencies. Choosing one of these options results in each contingency containing only one element of the specific type.

Bus Grouping

This feature will find groupings of buses and devices connected inside a group of branches that are explicit breakers, implicit breakers, or open branches. Contingencies are then formed from these groupings. Details of how the groupings and resulting contingencies are formed can be found with the [Breaker Isolated Groups](18-general-tools.md#breaker-isolated-groups) topic.

The **Use branch Normal Status for groupings** option is available when creating contingencies by bus groupings. This option is also described in the [Breaker Isolated Groups](18-general-tools.md#breaker-isolated-groups) topic.

Combination of... choice

You can also define contingencies containing multiple outages by checking the **Combination of…** option, and then specifying how many of each type of element (Lines, Transformers, and Generating Units) you want considered in the contingency. When you use the **Combination of…** option, Simulator will automatically determine all possible combinations for the element types specified (based on the settings in **Options**used to filter elements) and create the contingencies. Combination contingencies do not currently allow the inclusion of bus, switched shunt, or substation contingencies.

**Restrict to Parallel or Common**

These options will be enabled if choosing to do combinations where more than 1 of either a transmission line, transformer, or generator are specified.

**No restrictions (All)**: All combinations will be created.

**Common Substation**: If multiple lines are to be grouped together, only combinations of lines where at least one terminal of each line is in a common substation will be included. If multiple transformers are to be grouped together, only combinations of transformers where at least one terminal of each transformer is in a common substation will be included. If multiple generators are to be grouped together, only combinations of generators that are in the same substation will be included. There is no requirement that the combinations of different types of elements are contained in the same substation. For example, combinations of lines with generators will ensure that all of the lines grouped together are in the same substations and all of the generators grouped together are in the same substation, but the groups of lines and generators grouped together can be in different substations.

**Common bus**: This option works the same as the **Common substation** option except that common objects are grouped such that they have a common bus instead of substation.

**Parallel Branch (Common bus for gens)**: If multiple lines are grouped together, only combinations of lines where both terminal buses of the lines are the same will be grouped together. If multiple transformers are grouped together, only combinations of transformers where both terminals buses of the transformers are the same will be grouped together. If multiple generators are grouped together, only combinations of generators at the same bus will be included. There is no requirement that the combinations of different types of elements be parallel. For example, combinations of lines must be parallel but they can be combined with generators that are at a different bus than either of the line terminal buses.

Action Type to Create

Two options are available for specifying how the actions for the individual contingency elements should be defined. When defining contingency actions that involving opening an element, two formats are available: OPEN or OPEN BREAKERS TO ISOLATE. The OPEN format will implement an open action by changing the status of the affected element. The OPEN BREAKERS TO ISOLATE format will identify all breakers that should be opened in order to isolate the element. This option is very useful when using a full topology model in which breakers are identified in the case. Select the **Open** option to create the OPEN contingency definitions or the **Open Breakers** option to create the OPEN BREAKERS TO ISOLATE contingency definitions.

Options

When Simulator auto-generates the contingency records for the element types specified, the options in this section will further determine which elements are included and which elements are ignored.

Delete Existing Contingencies

When checked, any previously existing contingency records will be deleted before any automatically created contingencies are inserted.

Use Area/Zone Filters

When checked, the elements included in the auto-generated contingencies will be only elements that are within areas and zones defined in the [Area/Zone/Owner Filters dialog](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). You may edit the Area/Zone/Owner filters by clicking on the **Edit Area/Zone Filters** button.

Filter using nominal voltage range

When checking the box **All Voltages**, then filtering by nominal voltage is not done. When this box is unchecked, then specify a **Max** and **Min** nominal voltage in kV which you would like to filter by. This filtering is done in addition to any other filtering you specify. Thus an object will only be added as a new contingency if it meets the Area/Zone, Nominal Voltage, AND the Advanced Filter specified. When filtering the nominal kV level of a transformer object which has more than one nominal voltage associated with it, then use the option **Branch End to** Use to specify which of these voltages to compare to the **Min** and **Max** values.

Only include … meeting an advanced filter

When checked, the branches, generators, buses, substations, switched shunts, 3-winding transformers, or line shunts included in the auto-generated contingencies will be only those elements meeting conditions outlined by an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering). To set the conditions to be used, click the respective **Define… Filter** button.

Treatment of Transformers that are Part of 3-Windings

Options are only enabled when *Single transformer*, or *Single transmission line or transformer* is selected. The options are on how to treat the transformers that are part of a 3-Winding transformer. When a transformer branch is found during the auto insert simulator could either:

**Insert winding outages separately**, will insert separately the outages of the individual transformers that are part of the 3-Winding transformer object.

**Insert 3-Winding transformer outages**, will insert an outages of the 3-Winding transformer object instead of the outage of the individual transformers that are part of the 3-Winding transformer.

**Ignore (Do not insert these outages)**, will ignore the outage of the transformer branches that are part of a 3-Winding transformer.

Only include elements within

When checked, only elements that are within a particular distance of the specified bus will be included when creating the contingencies. The distance measure must be chosen from the drop down with choices of *Number of Nodes*, *X*, *Z*, and *Length*. This allows integrated use of the features available from the [Connections\\Determine Path Distances to Buses](16-oneline-gis-tools.md#path-distances-from-bus-or-group) on the tools menu of Simulator.

For example when using *Number of Nodes*, consider bus 1 is electrically connected to bus 2, which is in turn connected to bus 3. If we specify the bus to be bus 1, and choose to include only elements that are within 0 buses of bus 1, then the contingency record will include the branch between buses 1 and 2, and if desired any generators attached to bus 1. However, the branch between buses 2 and 3 and any devices attached to bus 2 and 3 will NOT be included in the contingency because bus 2 is electrically 1 bus away from bus 1.

To specify the bus used, you can find the bus by using the search engine. The search engine allows you to search by name or number. If you know the bus number, choose Sort by Number, and type the bus number in the search box. If you know the name of the bus, choose Sort by Name, and type the name of the bus in the search box. If you are not sure of the name of the bus, you can use wildcard characters to search through the list of buses until you find the desired bus.

How to name the contingencies

This section allows you to define how each automatically inserted contingency record will be named.

Identify … using prefix

These fields allow you to set a specific prefix for generators, lines, transformers, buses, 3-Winding transformers, switched shunts, substations, and line shunts so that you can easily determine what type or types of contingencies are modeled in the auto-generated contingency records. By default, the prefixes are L for lines, T for transformers, 3WT for 3-Winding transformers, G for generators, B for buses, S for switched shunts, SUB for substations, and LS for line shunts. However, you can change these prefixes to any character or set of characters you wish.

Identify buses by

This field allows you to specify whether each contingency is labeled using the bus numbers, bus names, both and labels (Use Numbers if no label) as identifiers. Whichever type of identifier you choose here will be combined with the defined prefixes to uniquely define the individual contingency elements within each auto-generated contingency record.

Include Nominal Voltages

When this check box is checked, the nominal voltage of buses will be included in contingency labels.

Do Insert Contingencies

Press this button to generate the contingency list once all other options have been set.

Save to Aux

Press this button to save the dialog settings to an auxiliary file so that they can be recalled for later use.

Cancel

Press this button to abandon creation of contingencies and close the dialog.

---

<a id="loading-a-contingency-list-from-a-file"></a>

## Loading a Contingency List from a File

*Source: [`Content/MainDocumentation_HTML/Loading_Contingencies_From_a_File.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Loading_Contingencies_From_a_File.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can load contingency definitions from a text file. The contingencies may be specified in any of the following formats:

  - [Simulator Auxiliary File Format (\*.aux)](03-cases-files-and-formats.md#auxiliary-file-format-aux)
      - Selecting this file type will also load the [WECC Contingency and RAS File (\*.aux)](#concise-contingency-and-remedial-action-scheme-format) format
  - Simulator Version 5-7 Contingency File Format (\*.ctg) (see the old users manual, or [contact](52-additional-linked-topics-part1.md#contact-information) PowerWorld Corporation)
  - [GE PSLF formatted Contingency Files (\*.otg)](23-contingency-analysis-running-and-results.md#pslf-contingency-format)
  - [PTI PSS/E-formatted Contingency Files (\*.con)](#psse-contingency-format)
  - [PTI Load Throw Over Files (\*.thr; \*.dat)](#psse-load-throw-over-files)
  - Areva Contingency File (\*.csv)

To load contingencies from a text file, click the **Load** button along the bottom of the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). A dialog box will be provided for you to specify the file from which to load the contingency records. Specify the file type in the **Files of Type** dropdown box, and select the appropriate file. If contingency records have already been defined for the case with which you are working, you will be asked if you wish to delete the existing contingencies. Respond affirmatively to delete the existing contingencies before adding the new ones from the specified files. Otherwise, click **No**, and the contingencies loaded from the file will be appended to the already existing list.

---

<a id="psse-contingency-format"></a>

## PSS/E Contingency Format

*Source: [`Content/MainDocumentation_HTML/PSS_E_Contingency_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PSS_E_Contingency_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can [read](#loading-a-contingency-list-from-a-file) and [write](#saving-contingency-records-to-a-file) parts of the contingency format used by Power Technologies, Inc. PSS/E. The current version of Simulator supports most of this format, except it does not recognize PTI’s Automatic Contingency Specification flags. If you need Simulator to support these keywords, contact PowerWorld Corporation to express your need. Otherwise, we recommend you make use of Simulator’s [tool to auto-insert contingencies](#automatically-generating-a-contingency-list).

---

<a id="psse-load-throw-over-files"></a>

## PSS/E Load Throw Over Files

*Source: [`Content/MainDocumentation_HTML/PSS_E_Load_Throw_Over_Files.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PSS_E_Load_Throw_Over_Files.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can read [load throw over](22-contingency-analysis-options.md#bus-load-throw-over) settings used by Power Technologies, Inc. PSS/E. These files typically have the extension of \*.thr or \*.dat. Note, however, that any modifications made to load throw over settings cannot be saved back to the PSS/E throw over file (only read access is currently available).

---

<a id="concise-contingency-and-remedial-action-scheme-format"></a>

## Concise Contingency and Remedial Action Scheme Format

*Source: [`Content/MainDocumentation_HTML/Contingency_Concise_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Concise_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This format was first created as a means to exchange data for defining contingencies and Remedial Action Schemes (RAS) among entities throughout the Western Electricity Coordinating Council (WECC). Starting in version 18 this format is an enhancement to the data section of the traditional auxiliary file format found in Simulator, and it can be loaded into Simulator anywhere that an auxiliary file can be loaded.

A file can be saved in this format from the **Save** button found on the bottom of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). The **Save as type** entry needs to be set to *WECC Contingency and RAS File (\*.aux)*.

A full description of this format is available [here](https://www.powerworld.com/WebHelp/Content/Other_Documents/PowerWorld_RASFileFormat.pdf).

---

<a id="saving-contingency-records-to-a-file"></a>

## Saving Contingency Records to a File

*Source: [`Content/MainDocumentation_HTML/Saving_Contingency_Records_to_a_File.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Contingency_Records_to_a_File.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can save contingency definitions to a text file. To save contingencies:

  - Click the **Save** button on the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). This action will save all contingency definitions and contingency options. Choosing the [Simulator Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux) provides a Contingency Settings dialog with options providing numerous options about what to save related settings such as [limit monitoring settings](18-general-tools.md#limit-monitoring-settings), [general power flow solution options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options), and [list display settings](04-model-explorer-and-case-information-part1.md#case-information-customizations-display) in the same auxiliary file. Contingency Elements may also be defined in the auxiliary file using Bus Numbers, Bus Name and Nominal kV, or [Label](07-object-properties-run-mode-and-general-part2.md#labels). The dialog that appears looks as follows and is described in detail in the [Save to Auxiliary File from Contingency Analysis](23-contingency-analysis-running-and-results.md#save-to-auxiliary-file-from-contingency-analysis)

[![Contingency Analysis SaveAUXDialog](images/Contingency_Analysis_SaveAUXDialog.png)](23-contingency-analysis-running-and-results.md#save-to-auxiliary-file-from-contingency-analysis)

  - Select **Save As…** from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the [contingency records display](22-contingency-analysis-options.md#contingencies-tab) . Several options for saving contingency information to Simulator’s Auxiliary File Format are available:
      - **Auxiliary File...** This action will save the information from the columns presently shown on the contingency records display, plus the contingency elements for each contingency record.
      - **Auxiliary File (only selected records)...** This action will save the information from the columns presently shown on the contingency records display and the contingency records currently selected, plus the contingency elements for each selected contingency record.
      - **Auxiliary File (only selected records/columns)...** This action will save the information from the columns and the contingency records currently selected, plus the contingency elements for each selected contingency record.
      - **Auxiliary File (all contingency related info)...** This action is identical to that of the **Save** button on the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) (see above).
      - **Auxiliary File (all contingency related info/only selected records)...** This action is identical to that of the **Save** button on the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) (see above), except only definitions of the selected contingencies will be saved.
      - Options for other file formats are also available, as are typically shown on case information [local menus](04-model-explorer-and-case-information-part1.md#local-menu-options). Such other formats are generally not suitable for loading contingency information back into Simulator.
  - Click the **Save to Aux** button on the Auto Insertion of Contingencies Dialog. This action will save the Auto Insertion options, but not the contingencies themselves.

The contingencies may be specified in the following formats. These formats can be found when using the **Save** button on the bottom of the contingency analysis dialog and changing the **Save As Type** setting:

  - [Simulator Auxiliary File Format (\*.aux)](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - [WECC Contingency and RAS file (\*.aux)](#concise-contingency-and-remedial-action-scheme-format)
  - Simulator Version 5-7 Contingency File Format (\*.ctg) (see the old users manual, or contact PowerWorld Corporation)
  - [PTI PSS/E-formatted Contingency Files (\*.con)](#psse-contingency-format). This format includes an option to truncate the contingency labels to 8 or 12 characters for compatibility with versions of PSS/E that do not support longer labels. The truncated labels will be named such that each is unique. There is also an option to use bus name and bus nominal kV in identification of contingency elements.

To specify the format for the contingency file, set the **Save As Type** option accordingly.

Note that there are limitations when saving to the Simulator Version 5-7 format or the PTI PSS/E formatted files.

Limitations on the Simulator Version 5-7 format

  - Does not support the actions SET or CHANGE.
  - Does not support the action MOVE, except for Loads.
  - Does not support any actions regarding an Interface
  - Does not support any actions regarding a Bus

Limitations on the PTI PSS/E format

  - Does not support any actions regarding an Interface

---

<a id="global-actions"></a>

## Global Actions

*Source: [`Content/MainDocumentation_HTML/Global_Actions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Global_Actions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Why You Might Not Want to Use Contingency Global Actions

Before using Contingency Global Actions, consider them a legacy feature that has been used to model scenarios that might better be modeled using [Remedial Actions](#remedial-actions). Although global actions will continue to be supported in traditional auxiliary files, a new [concise file format for modeling contingencies and remedial action schemes](#concise-contingency-and-remedial-action-scheme-format) does not support global actions. When saving in this format, global actions will automatically be merged into a single Remedial Action, but if you want to do this manually there is a button on the top of the Contingency Global Actions display to **Convert Global Actions into Remedial Action**. This same option is available on the local menus of several case information displays associated with contingency definitions.

Global Actions Description

Contingency Global Actions allow you to define a list of contingency elements that occur for ALL contingencies and do not have to be entered as individual elements in each contingency. These contingency elements are defined and processed in the same manner as contingency elements defined with specific contingencies. A global action can be excluded from not being included with all contingencies by using the Inclusion Filter described below.

Contingency global actions are defined from the Contingency Global Actions display accessed via the [Contingency Definitions grouping](22-contingency-analysis-options.md#contingency-definitions) found on the [Options tab](22-contingency-analysis-options.md#options-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). Right-click on the table to open the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog), which allows the addition of contingency elements to be treated as part of the global actions.

When used with global actions, the Contingency Element Dialog will be modified to allow selecting an **Inclusion Filter** to use with a global action. The Inclusion Filter is an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or [device filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device) that gets applied to each contingency. If the contingency meets the Inclusion Filter defined with a particular global action, that contingency will include that global action. Otherwise, a global action will be ignored for that contingency. To select an Inclusion Filter for a global action, click the **Add/Modify** button. This will open the advanced filter dialog that will allow selection of the filter. To include a global action with all contingencies, leave the Inclusion Filter blank. The Inclusion Filter is evaluated in the reference case to determine if a contingency meets the filter.

The format of the string that describes the actions and the **Model Criteria** and **Status** fields are set in the same manner as described in the [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display).

To disable the use of the Global Actions, check the **Do Not Use Global Action List** option found at the top of the display.

---

<a id="contingency-blocks"></a>

## Contingency Blocks

*Source: [`Content/MainDocumentation_HTML/Contingency_Blocks.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Blocks.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Why You Might Not Want to Use Contingency Blocks

Before using Contingency Blocks, consider them a legacy feature that has been used to model scenarios that might better be modeled elsewhere, like [Injection Group actions](24-contingency-element-dialog.md#type-injection-group) or [Remedial Actions](#remedial-actions). Although contingency blocks will continue to be supported in traditional auxiliary files, a new [concise file format for modeling contingencies and remedial action schemes](#concise-contingency-and-remedial-action-scheme-format) does not support contingency blocks. When saving in this format, contingency blocks will automatically be merged into the Contingencies, Global Actions, and Remedial Actions using them, but if you want to do this manually there is a button on the bottom of the Contingency Element Block display to **Merge Contingency Elements into other structures and remove contingency blocks**. This same option is available on the local menus of several case information displays associated with contingency definitions.

Contingency Block Description

Contingency Blocks are very similar to a [Contingency Record](22-contingency-analysis-options.md#contingency-definition-display), however no results can be associated with them. Contingency Blocks consist of a list of contingency actions. The block is then given a name so that any Contingency Record can call on a Contingency Block. When a contingency block is included as part of a contingency, the Contingency Record will incorporate all the actions from the contingency block into the actions performed by the contingency.

Contingency blocks are defined from the Contingency Element Block display accessed via the [Contingency Definitions grouping](22-contingency-analysis-options.md#contingency-definitions) found on the [Options tab](22-contingency-analysis-options.md#options-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). Right-clicking in the Contingency Blocks grid and choosing **Insert** allows you to insert a new Contingency Block. A dialog very similar to the [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog) will open. Use this dialog to insert elements into the contingency block, create additional contingency blocks, or modify existing contingency blocks. Once a new contingency block has been created, actions can be added to the block by right-clicking in the Contingency Definition grid and choosing **Insert**. This will open the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) that allows the addition and modification of elements in the contingency block. When using the Contingency Element Dialog with Contingency Blocks, the option to insert an Element Type of *Contingency Block* is not available. Time Delays cannot be specified.

The format of the string that describes the contingency block actions and the **Model Criteria** and **Status** fields are set in the same manner as described in the [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display). Contingency block actions cannot use a Status of SOLUTIONFAIL. Contingency blocks cannot contain Persistent actions.

To disable the use of a Contingency Block, set the **Skip** field to *YES*. When a Contingency Block is disabled, all of the actions defined in the block will be ignored in all of the contingencies in which the block is included.

Once Contingency Blocks have been defined, a new Element Type, *Contingency Block* will appear on the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog). You may then add a contingency block to a contingency by right-clicking on a contingency in the [Contingency Records](22-contingency-analysis-options.md#contingencies-tab) list display, choose show dialog (or insert if you are adding a new contingency record), click on Insert New Element, and choose Contingency Block from the list of element types.

Using a contingency block is an easy way to include a set of common actions in multiple contingency scenarios, without having to re-define the actions for each contingency.

---

<a id="remedial-actions"></a>

## Remedial Actions

*Source: [`Content/MainDocumentation_HTML/Contingency_Remedial_Actions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Remedial_Actions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Contingency Remedial Actions allow you to define a list of contingency actions that occur for ALL contingencies and do not have to be entered as individual elements in each contingency. These contingency actions are defined and processed in the same manner as contingency elements defined with specific contingencies. Typical use of Remedial Actions is to define actions that are conditional on something occurring in the system, i.e. a branch being out of service or a branch flow exceeding a specified threshold. These conditional actions are often called remedial action schemes (RAS), special protection schemes (SPS), or operating guides (OG).

Remedial Actions are similar to Contingency Global Actions in that they will occur for all contingencies, however, Remedial Actions make it much more convenient to define operating schemes comprised of multiple actions. Global Actions will remain in use for legacy reasons, but we encourage you to use Remedial Actions when defining new operating schemes. At the top of the [Global Actions display](#global-actions) there is a button to **Convert Global Actions into Remedial Action** make it very easy for you to convert your legacy Global Actions into the new (with version 18) Remedial Action format.

Remedial Actions Display

Remedial Actions are defined from the Remedial Action display accessed via the [Remedial Action Definitions grouping](22-contingency-analysis-options.md#remedial-action-definitions) found on the [Options tab](22-contingency-analysis-options.md#options-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). A Remedial Action is a container of contingency elements that serves to define a single operating scheme. Remedial Actions are made up of Remedial Action Elements. Each element is a single action that is defined in a similar manner as any other [contingency element](24-contingency-element-dialog.md#contingency-element-dialog). The Remedial Action display provides a list of all Remedial Actions that exist at the top of the display. At the bottom of the display there is a [Contingency Definition display](22-contingency-analysis-options.md#contingency-definition-display) that lists the individual elements in each Remedial Action.

The display contains the **Ignore Remedial Action Elements if Model Criteria is True in Contingency Reference State** option that applies to all remedial action elements. If this option is checked, any remedial action element that has a Model Criteria defined and the Model Criteria evaluates to true in the contingency reference state will be ignored during the contingency solution process. The element will be ignored regardless of the Status of the action. When loading an Areva contingency file, this option is set based on the SCNBCRAS field in the ITEMS record.

Local Menu Options

From the Remedial Action display use the right-click menu option **Insert** to create a new Remedial Action. To modify an existing Remedial Action, the right-click menu **Show Dialog** option can be used. Both of these actions will open the Remedial Action Elements dialog that is a stripped down version of the [Contingency Definition Dialog](22-contingency-analysis-options.md#contingency-definition-dialog) that will allow you to add and modify new Remedial Action Elements.

Special options are available on the local menu to save the remedial actions and any objects that are required to completely define them (dependencies). Objects required to define a remedial action include Remedial Action Elements, Model Conditions and Model Filters that define the Model Criteria and Arming Criteria, Injection Groups included in the actions, and many others. When using these save options, Simulator will search through the object hierarchy completely starting at the top from the remedial actions being saved and save them and all of their dependencies. When using these options, the file format options used are the same as those required by the [WECC RAS and contingency format](https://www.powerworld.com/WebHelp/files/PowerWorld_RASFileFormat.pdf). The following options are available:

**Save As \> Auxiliary File (all related info)...** Added in Version 19, build on April 12, 2017

This option will save all of the remedial actions currently showing in the display along with all of the dependencies of these remedial actions. Filtering on the display can be used to limit the remedial actions that are saved.

**Save As \> Auxiliary File (all related/only selected records)...** Added in Version 19, build on April 12, 2017

This option will save only the remedial actions that are currently selected in the display along with all of the dependencies of these remedial actions.

Display Fields

The following fields are shown by default in the Remedial Action display:

Skip

Set this field to *YES* to exclude this remedial action from being included with any contingency. By default this is set to *NO*.

Arming Criteria Added in Version 20

This specifies a criterion under which a remedial action will be armed. See the [Remedial Action Definition dialog](52-additional-linked-topics-part1.md#remedial-action-definition-dialog) topic for more details.

Arming Status Added in Version 20

This specifies how arming of the remedial action is determined in the presence or absence of **Arming Criteria**. See the [Remedial Action Definition dialog](52-additional-linked-topics-part1.md#remedial-action-definition-dialog) topic for more details.

Armed Added in Version 20

This specifies if the remedial action is currently armed. This determination is made based on the present system state and might differ from how arming is determined during the contingency analysis process. Model Conditions and Model Filters have options that allow them to be disabled if they are true in the contingency reference state. These options are ONLY applied during the contingency analysis process and are not applicable when the value of the Armed field is determined.

Remedial Actions Element Display

The Remedial Action Elements display is accessed via the [Remedial Action Definitions grouping](22-contingency-analysis-options.md#remedial-action-definitions) found on the [Options tab](22-contingency-analysis-options.md#options-tab) of the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) and allows you to access the individual elements directly rather than going through the Remedial Action. The **Contingency Label** field for this display indicates the Remedial Action to which a particular element belongs.

---

<a id="contingency-category"></a>

## Contingency Category

*Source: [`Content/MainDocumentation_HTML/Contingency_Category.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contingency_Category.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Contingency categories can be defined with both [steady-state contingencies](22-contingency-analysis-options.md#contingencies-tab) and [transient stability contingencies](37-transient-stability-analysis-dialog-part1.md#simulation). Categories are often used to group contingencies by monitoring criteria and that is the reason they have been added to Simulator. Steady-state contingency categories will be used to determine which Custom Monitors will be active for a contingency. Transient stability contingency categories will be used to determine which Transient Limit Monitors will be active for a contingency. Both Custom Monitors and Transient Limit Monitors have associated categories that can be assigned with them.

Categories within Simulator are simply user-specified text. There are no set categories that Simulator defines. More than one category can be assigned to a contingency, Custom Monitor, or Transient Limit Monitor. They are entered as comma-separated strings in relevant fields with these objects.

Contingency Analysis Categories

Categories with steady-state contingencies determine which [Custom Monitors](22-contingency-analysis-options.md#custom-monitors) will be active for a contingency. If no categories are specified for a contingency, all Custom Monitors will be active for a contingency. If a Custom Monitor does not have any categories specified, it will apply to all contingencies. Otherwise, a Custom Monitor will only be active if it has at least one category that matches one of the contingency's categories.

Transient Stability Analysis Categories

Categories with transient stability contingencies determine which [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#defining-transient-limit-monitors) will be active for a contingency. If no categories are specified for a transient contingency, all Transient Limit Monitors will apply for a transient contingency. If a Transient Limit Monitor does not have any categories specified, it will apply to all transient contingencies. Otherwise, a Transient Limit Monitor will only be active for a transient contingency if it has at least one category that matches one of the transient contingency's categories.

---

<a id="dependency-explorer"></a>

## Dependency Explorer

*Source: [`Content/MainDocumentation_HTML/Dependency_Explorer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Dependency_Explorer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in version 19

The Dependency Explorer is found on the [Tools ribbon tab](02-simulator-ribbon.md#tools-tab-overview) in the [Run Mode ribbon group](02-simulator-ribbon.md#run-mode-ribbon-group) under **RAS + CTG Case Info \> Dependency Explorer**. It can also be opened by clicking the **Open Dependency Explorer** button on the [Options tab](22-contingency-analysis-options.md#options-tab) of the Contingency Analysis dialog. It can also be found on the local menu of case information displays for objects that can have dependencies.

The intent of the dependency explorer is to enhance the understanding of remedial actions used with contingency analysis. It allows for the viewing and modification of objects that are used in the definition of remedial actions, as well as any conditional contingency actions. *Dependencies* are objects that are necessary to completely define another object. Some examples of dependencies include:

  - Contingencies and Remedial Actions that use Model Criteria have a dependency of either a Model Filter or Model Condition
  - Model Filters can have dependencies of Model Conditions and other Model Filters
  - Contingency Elements and Remedial Action Elements have dependencies of the objects, i.e. Branch, Generator, Load, etc., to which the action is applied
  - Injection Groups have dependencies of the Participation Points that comprise the Injection Group and these in turn have dependencies on the Generators, Loads, Switched Shunts, Buses, and other Injection Groups that belong to them.

![Dependency Explorer](images/Dependency_Explorer.gif)

The Dependency Explorer is broken into several panes.

Top Object

The *Top Object* is the object currently being examined. The **Find** button will open a dialog for selecting which object to examine. If the dialog has been opened from an object case information display, the top object will be set as that object. The navigation buttons allow scrolling through the history of objects that have been examined.

Clicking the **Show Dialog** button will open the user interface dialog for the *Top Object*.

Clicking the **Save Auxiliary** button will save the *Top Object* and all of its dependencies to an auxiliary file. The format options that are used in saving the auxiliary file are the same as those required by the [WECC RAS format](23-contingency-analysis-running-and-results.md#save-to-auxiliary-file-from-contingency-analysis).

Used By

This is a tree view of all of the objects used by the *Top Object*. The hierarchy of objects is given in the nodes of the tree view. This is most useful with Model Filters and Model Conditions because changing these will impact how a conditional action is applied and the same changes might not carry through to all objects using them.

The maximum depth of any single node is limited to 6. This is to help with the performance of the tree view as expanding and collapsing nodes can become very slow if there are many nodes.

A local menu is available by right-clicking on an object in this tree view. Details of the available local menu options are given in the **Local Menu** section below.

This pane contains some buttons and color coding that are the same as those used in the **Contains** pane. These are described in the **Common Features on All Panes** section below.

Contains

This is a tree view of all of the objects that are dependencies of the *Top Object*. The hierarchy of objects is given in the nodes of the tree view. As objects are selected in the tree view, the **Field Info** pane updates with fields for that object.

A local menu is available by right-clicking on an object in this tree view. Details of the available local menu options are given in the **Local Menu** section below. The maximum depth of any single node is limited to 6 by default. This is to help with the performance of the tree view as expanding and collapsing nodes can become very slow if there are many nodes. This depth can be changed using the **Change Maximum Depth** option on the local menu.

This pane contains some buttons and color coding that are the same as those used in the **Used By** pane. These are described in the **Common Features on All Panes** section below. This pane has two additional buttons:

**Delete**

Click this button to delete the object that is currently selected in this pane.

**Show Drag/Drop Editor**

Click this to open the drag/drop editor that allows easy modification of Model Filters by adding or removing other Model Filters and Model Conditions.

![Dependency Explorer Drag Drop Editor](images/Dependency_Explorer_Drag_Drop_Editor.gif)

To add a Model Filter or Model Condition to another Model Filter, select the Model Filter or Model Condition in the object selector by left-clicking on it and then drag and drop it on the appropriate Model Filter in the Contains pane.

To remove a Model Filter or Model Condition from either a Model Filter or as part of the Mode Criteria for a Contingency Element or Remedial Action Element, left-click on it in the Contains pane and drag and drop it on the **Drag/Drop here to Delete** pane of the drag/drop editor.

Field Info

This pane is similar to a case information display for an object except that it shows information only for a single object. The single object for which it shows information is the one that is currently selected in the **Contains** tree view. Fields that can be modified through a case information display can be modified here. The [color scheme](10-power-flow-solution-and-options-part2.md#case-information-display-options) that indicates the type of field and whether or not it can be modified is that same as that used for case information displays. The fields that are displayed are those deemed relevant for modeling contingencies and remedial actions. These fields are those that are hardcoded as part of the [Complete Case Auxiliary File Export Format Description](09-auxiliary-files-and-script-commands.md#complete-case-auxiliary-file-export-format-description).

The **Headings** option specifies how the captions are shown for the fields. The following options are available:  

**Column Headings**

This displays the fields using the longer names that are normally used with column headings in case information displays.

**Concise Variable Names**

This displays the fields using the concise variable names as described in the [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names) topic.

**Legacy Variable Names**

This displays the fields using the legacy variable names as described in the [PowerWorld Object Variables](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names) topic.

Filter Visualization

This pane will appear if a Model Filter is selected in the **Contains** tree view. This will display the [Model Filter Logic Display](04-model-explorer-and-case-information-part3.md#model-filters-view-filter-logic-graphical-display), which is a graphical representation of the Model Filter logic. Right-clicking on an object in the logic display will open the user interface dialog for that object. Left-clicking on a Model Filter will set that as the new *Top Object*.

Common Features on All Panes

There are several features and buttons that operate in the same manner regardless of the pane in which they are contained.

Background Highlighting

The following highlighting colors are used to indicate special things about Model Filters and Model Conditions. When showing a Model Filter or Model Condition the background of entries in both the Used By and Contains tree view are highlighted and the background of the Field Info pane is highlighted.

**Red**

Result of Model Filter or Model Condition is NO.

**Green**

Result of Model Filter or Model Condition is YES.

**Yellow**

Model Filter or Model Condition contains unlinked elements.

**Blue**

Model Filter or Model Condition contains a circular reference.

Collapse Button

Clicking this will collapse all nodes in the tree view on the pane in which the button is clicked.

Expand Button

Clicking this will expand all nodes in the tree view on the pane in which the button is clicked.

Navigate Button

Clicking this will set the object selected in the tree view on the pane in which the button is clicked as the new *Top Object*.

Dialog Button

Clicking this will open the user interface dialog for the object selected in the tree view on the pane in which the button is clicked.

Local Menu

A local menu can be accessed by right clicking on an object in either the **Used By** or **Contains** pane. The following options are available:

Navigate to Object

Selecting this will set the object that was clicked on as the new *Top Object*.

Show Dialog for Object

Selecting this will open the user interface dialog for the object that was clicked on.

Delete Object

This option is only available on the **Contains** pane. Selecting this will delete the object that was clicked on.

Find New Top Object

Selecting this will open the object chooser dialog that allows selection of a new Top Object.

Show Drag/Drop Editor

This option is only available on the **Contains** pane. Selecting this will open the drag/drop editor for Model Filters and Model Conditions as described above in the **Show Drag/Drop Editor** section.

Change Maximum Depth

This option is only available on the **Contains** pane.

By default the depth of the tree view is set to 6. When this limit is reached no additional detailed information is presented. An entry of "...more..." is given instead. This depth can be increased by using this option. The depth is originally limited because the more entries there are in the tree view the slower the performance may be of expanding and collapsing nodes. It is suggested that the depth only be increased if necessary to see additional details.
