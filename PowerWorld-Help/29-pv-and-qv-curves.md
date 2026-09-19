---
title: "PV and QV Curves (PVQV)"
part: "Add-Ons"
chapter_file: "29-pv-and-qv-curves.md"
topics: 26
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# PV and QV Curves (PVQV)

PV curves, QV curves and the PV/QV refine model.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (26)**

- [PowerWorld Simulator PVQV Overview](#powerworld-simulator-pvqv-overview)
- [PV Curves](#pv-curves)
- [Dialog](#dialog)
- [Setup](#setup)
- [Common Options](#common-options)
- [Injection Group Ramping Options](#injection-group-ramping-options)
- [Interface Ramping Options](#interface-ramping-options)
- [Advanced Options](#advanced-options)
- [PV/QV Quantities to Track](#pvqv-quantities-to-track)
- [Limit Violations](#limit-violations)
- [Output](#output)
- [Results](#results)
- [Overview](#overview)
- [Plot](#plot)
- [Track Limits](#track-limits)
- [QV Curves](#qv-curves)
- [Dialog](#dialog-1)
- [Buses](#buses)
- [Options](#options)
- [Solution](#solution)
- [Contingencies](#contingencies)
- [Output](#output-1)
- [Distributed Computing](#distributed-computing)
- [Results](#results-1)
- [Listing](#listing)
- [PV/QV Refine Model](#pvqv-refine-model)

---

<a id="powerworld-simulator-pvqv-overview"></a>

## PowerWorld Simulator PVQV Overview

*Source: [`Content/MainDocumentation_HTML/PowerWorld_Simulator_PV_QV_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerWorld_Simulator_PV_QV_Overview.htm)*

**The PV and QV tools are only available if you have purchased the PVQV add-on to the base Simulator package. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information) for more details.**

PVQV, PowerWorld's voltage adequacy and stability assessment add-on, is used to analyze the voltage characteristics of a power system.

The PowerWorld Simulator (Simulator) is an interactive power system simulation package designed to simulate high voltage power system operation. With the voltage adequacy and stability (**PVQV**) add-on, multiple power flow solutions are used to generate a [PV curve](#pv-curves) for a particular transfer or a [QV curve](#qv-curves) at a given bus.

The PVQV functionality is accessed using the PV and QV Curves (PVQV) ribbon group from the [Add Ons ribbon tab](02-simulator-ribbon.md#add-ons-tab-overview). The commands available in this ribbon group are [Refine Model](#pvqv-refine-model), [PV Curves](#pv-curves), and [QV Curves](#pv-curves).

The purpose of the PVQV add-on is monitor system voltages, or other user specified parameters, as a real power transfer is increased or reactive power is injected at selected buses. The PVQV add-on uses the Simulator built-in Newton Raphson power flow algorithm to accomplish this task. After PV and QV simulations are completed, the user can choose to graph any of the monitored system parameters, designated in [Quantities to Track](#pvqv-quantities-to-track).

---

<a id="pv-curves"></a>

## PV Curves

*Source: [`Content/MainDocumentation_HTML/PV_Curves.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Curves.htm)*

Simulator's **PV Curves** tool provides the ability to produce plots of maximum power transfer (PV) curves for voltage at any bus in the system, as well as 2-dimensional plots of various quantities tracked during the simulation. In Run Mode, select **PV** from the **Add Ons** ribbon tab to open the [PV Curves dialog](#dialog). The PV Curves dialog allows you to specify the quantities to be tracked during the simulation, control solution parameters, set violation boundaries, and run the PV analysis.

The traditional PV curve process will automatically solve a sequence of power flows at incremental levels of power transfer between a source Injection Group and a sink Injection Group. [Injection Groups](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) may contain generators, loads, or a combination of both. Each **Contingency** defined in the [Contingency Analysis Tool](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview) that is not flagged to be skipped will be processed and tracked as a separate **PV Scenario**, along with the pre-contingent base case, at each incremental power transfer. After each successful power flow solution, the user-specified [Quantities to Track](#pvqv-quantities-to-track) are recorded and the transfer is increased by the next increment. If a power flow solution fails, then the last successful solution for that scenario is applied and a smaller incremental transfer is applied. The process concludes after finding the maximum power transfer for the user-specified number of critical scenarios.

The PV tool also allows a ramping method that increases the loading on up to two selected interfaces. This process automatically solves a sequence of OPF solutions at incremental levels of increased loading on these interfaces. A flow limit can optionally be enforced on a third interface during the OPF solutions. This process is described in detail in the [Interface Ramping](#interface-ramping-options) topic.

---

<a id="dialog"></a>

## Dialog

*Source: [`Content/MainDocumentation_HTML/PV_Curve_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Curve_Dialog.htm)*

To display this dialog, go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **PV**from the **PV and QV Curves (PVQV)** ribbon group.

The PV Curves dialog contains all of the setup and controls for processing and analyzing the PV curve analysis. The dialog is broken down into several pages:

[Setup](#setup)

[Quantities to track](#pvqv-quantities-to-track)

[Limit violations](#limit-violations)

[PV output](#output)

[PV results](#results) (Launching the analysis is done from this page.)

[Plots](37-transient-stability-analysis-dialog-part2.md#plots)

There are several buttons at the bottom of the dialog that are available regardless of the selected page.

![PV Curve Dialog](images/PV_Curve_Dialog.jpg)

Save Auxiliary

Clicking this button will prompt for a filename in which to save an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux). Use this auxiliary file to store any results and settings that need to be retained for future use.

Added in version 23PV options are stored with PWB files, and results can optionally be stored.

The **PV Curve Tool Settings** dialog shown below will be displayed with options for specific data to include in the auxiliary file. Check the box next to a particular data set to save this data in the auxiliary file. Which key field to use when identifying objects in the file can also be specified on this dialog. Click **OK** on this dialog to finalize saving the file or close the dialog to abandon the file save.

![PV Curve Tool Settings Dialog](images/PV_Curve_Tool_Settings_Dialog.png)

Load Auxiliary

Clicking this button will open a dialog to allow the user to select an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) to load. This is intended to be used for loading any relevant option settings to be used during the PV analysis. The dialog will be updated according to the option settings loaded from the file.

Help

Displays this help page.

Close

This will close the dialog without running the analysis. The currently set options will be saved, and the dialog will not close unless all option settings are valid.

---

<a id="setup"></a>

## Setup

*Source: [`Content/MainDocumentation_HTML/PV_Setup.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Setup.htm)*

The Setup tab is found on the [PV Curves dialog](#dialog).

The main part of the Setup tab allows selection of the **Ramping Method**. The options are:

  - **Injection Group Source/Sink** - This is the traditional PV ramping method that increases generation or decreases load in the Source injection group and decreases generation or increases load in the Sink injection group to model a transfer. Ramping setup and other options are described in the [Injection Group Ramping Options](#injection-group-ramping-options) topic.
  - **Interface MW Flow** - This method implements a transfer by increasing the loading on up to two selected interfaces. This process automatically solves a sequence of OPF solutions at incremental levels of increased loading on these interfaces. Ramping setup and other options are described in the [Interface Ramping Options](#interface-ramping-options) topic.

Once the ramping method has been defined, the ramping process is performed incrementally, based upon user specified [options](#common-options) on how the transfer should vary during the solution process.

The remainder of the setup options are found on sub-tabs for [Common Options](#common-options) and [Advanced Options](#advanced-options).

---

<a id="common-options"></a>

## Common Options

*Source: [`Content/MainDocumentation_HTML/PV_Setup_Common_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Setup_Common_Options.htm)*

These options are located the Common Options sub-tab found on the [Setup](#setup) tab of the [PV Curves dialog](#dialog). These are the options most commonly adjusted for the PV analysis.

![PV Setup Common Options](images/PV_Setup_Common_Options.gif)

Stop after finding at least ... critical scenarios

A large number of contingencies can be specified for analysis. Usually, there is only concern with determining a certain number of the most critical scenarios instead of running each scenario to its critical point. Set this number to stop the analysis of all scenarios once the specified number of critical scenarios has been found. It should be noted that this number really serves to find *at least* the specified number of critical scenarios. Depending on when a scenario becomes critical in the process, it is possible that more than the specified number of critical scenarios will be found.

Before implementing a new transfer step for all contingencies, the number of scenarios that are already critical is checked against the number of critical scenarios to find. If at that point the number found is greater than or equal to the number specified, the process will stop. At each transfer step, all contingencies that are not already critical are implemented and a power flow solution is attempted for each contingency. If any contingency does not solve, that contingency is evaluated independently to determine the transfer level at which it becomes critical. If multiple contingencies cannot be solved at a particular transfer step, all of these contingencies will be evaluated independently to determine the transfer level at which it becomes critical. All contingencies are evaluated even if this would cause the number of critical scenarios found to exceed the specified number of critical scenarios to find.

Skip contingencies

The PV Curve tool computes PV curves for both the base topology and for any contingencies that have been defined, unless the **Skip contingencies** checkbox is checked. If the **Skip contingencies** checkbox is checked, a PV curve will be computed only for the model in its present (base case) topology.

Manage contingency list…

Clicking this button will open the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) for managing or inserting contingencies to be processed during the PV analysis. Contingencies defined and marked for processing in the contingency analysis dialog will be included. Only those contingencies whose **Skip** field is set to *NO* will be included in the PV analysis.

Note: The Robust Solution Process option that can be utilized with the contingency analysis when a contingency solution failure occurs is not applied when a contingency is implemented during the PV analysis. Most other options defined with contingency analysis such as contingency specific solution options and make-up power specifications are used when applying a contingency during the PV analysis. The exception here is for the contingency-specific solution option for Minimum Per Unit Voltage for Constant Power Load. This is always set to 0 pu during the PV analysis. Also, Model Conditions and Filters that are part of contingency model criteria used during PV and QV analysis allow the use of the Model Condition option to Disable if Condition is True in Contingency Reference State.

Run base case to completion

The PV curve tool is designed to ramp a transfer until the prescribed number of critical scenarios, including both critical contingencies and critical base topology, have been found. If the requested number of critical scenarios have all been identified as being associated with contingencies, the tool will not reveal how much a transfer can be ramped for the base topology, unless the **Run base case to completion** checkbox is checked. Checking this checkbox forces the tool to continue to ramp the transfer until the base case can no longer be solved, regardless of whether the requested number of critical transfer level / topology combinations have been found.

If using the **Stop when transfer exceeds** option, it is possible that the base case will not be run to completion if the specified transfer level is exceeded before the critical point for the base case is found.

Base Case Solution Options …

Click this button to bring up the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options). This allows the specification of the solution options to use for solving pre-contingency cases and the options used when no contingency-specific solution options are defined. Changing these options affect all power flow computations, even those outside the PV process.

Because the goal is to stress the system while performing the PV analysis, there are two power flow solution options that are set internally as part of the PV process. These are the options that specify the minimum per unit voltage for constant power and constant current loads. These options are both set to 0 pu and override any user-specified settings.

![PV Setup Common Options Min PU Volt](images/PV_Setup_Common_Options_Min_PU_Volt.jpg)

These options are both set to 0 pu during both the base case solution and any contingency case solution.

Initial Step Size (MW)

This option indicates the initial increment in which the transfer will be increased following each successful iteration. The default value is 100 MW.

Minimum Step Size (MW)

Whenever the PV process fails to solve the system at a given transfer level, it will return to the previously solved transfer level, reduce the step size by the specified factor, and then try to solve the system with the transfer incremented by the newly reduced step size. The **Minimum Step Size** option specifies the minimum size this increment can be. Once the system fails to solve when the step size is at this value, the process will conclude that we have come very close to the voltage collapse point and terminate the analysis. So, the minimum step size essentially functions as a tolerance for computing the voltage collapse point. The default value is 10 MW. The minimum step size must be greater than or equal to 0.1 MW.

See the topic below about **Tolerances in PV Tool** for more information about how the minimum step size interacts with the Island-Based AGC Tolerance and power flow MVA Convergence Tolerance.

When convergence fails, reduce step by a factor of…

Whenever the PV process fails to solve the system at a given transfer level, it will reduce the transfer step size by the value specified for this option. The default value is 2. Therefore, the process will start incrementing the transfer in 100 MW steps. When it reaches a transfer level that it cannot solve, it will return to the last solved transfer level, reduce the step size to 50 MW, increment the transfer by 50 MW, and attempt to solve the case again. The next time it fails to solve, it will reduce the step size to 25 MW, and then to 12.5 MW, and finally to 6.25 MW. Since 6.25 MW is less than the **Minimum Step Size** value of 10 MW, it will instead use a final step size of 10 MW. Once the system fails to converge with this step size, the analysis will terminate because it concludes that it has arrived at the voltage collapse point, within the specified tolerance. This value must be greater than or equal to 1.01.

Stop when transfer exceeds

Check this box to terminate the PV analysis once the transfer between the source and sink reaches an amount equal to the MW value specified.

Added in version 20, build on January 30, 2018

When this transfer level is reached, a scenario will be reported as critical.

Tolerances in PV Tool

Tolerances must be set correctly with the PV tool or injection changes will end up being picked up by the system slack instead of the sink injection group or no injection changes will be made at all. The **Minimum Step Size** will dictate what the **MVA Convergence Tolerance**, set with the [Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options) on the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), and the **Island-Based AGC Tolerance** can be. Before the analysis starts, the MVA Convergence Tolerance will be checked to make sure that it is less than 0.1\*(Minimum Step Size). If not, the MVA Convergence Tolerance will be set to 0.1\*(Minimum Step Size). The Island-Based AGC Tolerance will also be checked to make sure that it is less than 0.5\*(Minimum Step Size). If not, the Island-Based AGC Tolerance will be set to 0.5\*(Minimum Step Size). The MVA Convergence Tolerance will then be checked to make sure that it is less than 0.2\*(Island-Based AGC Tolerance). If not, the MVA Convergence Tolerance will be set to 0.2\*(Island-Based AGC Tolerance). This will order the tolerances such that (MVA Convergence Tolerance) \< (Island-Based AGC Tolerance) \< (Minimum Step Size). The original tolerances will be restored when the initial state stored with the PV tool is restored.

Another issue dealing with tolerances is cumulative system slack error. The cumulative system slack error will be recorded after each ramping step. This is done so that an attempt can be made to keep the system slack from deviating more than the Island-Based AGC Tolerance over all of the ramping by adjusting for this error during the next ramping step. This error will be applied to the amount of change required from the sink injection group in an attempt to bring the system slack back towards its original output. Without this accounting it is possible that the system slack could move by the Island-Based AGC Tolerance at each ramping step, and the overall results would be that the system slack could move (Island-Based AGC Tolerance) \* (Number of ramping steps) by the completion of the process. With this accounting, the system slack may move up and down slightly over the course of all ramping, but on average will stay near its starting output within the Island-Based AGC Tolerance.

---

<a id="injection-group-ramping-options"></a>

## Injection Group Ramping Options

*Source: [`Content/MainDocumentation_HTML/PV_Setup_InjectionGroup_Ramping_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Setup_InjectionGroup_Ramping_Options.htm)*

These options are found at the top of Setup tab found on the [PV Curves dialog](#dialog) and the Injection Group Ramping Options tab of the same dialog. The remainder of the setup options are found on sub-tabs for [Common Options](#common-options) and [Advanced Options](#advanced-options).

![PV Setup Injection Group](images/PV_Setup_Injection_Group.gif)

The Setup tab contains the options for defining the source and sink for the PV study transfer. The PV tool expects the source and the sink to be [injection groups](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) defined by the user.

Source

Use this drop-down box to identify the source [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview). To model an increase in transfer, generator points in the source injection group will increase their output, and load points will decrease their magnitude in amounts proportional to their participation factors.

If the injection group to use for the source has not already been created, click the View/Define Groups button in order to create it. After the injection group has been created, it will show up in this drop-down box and can then be selected.

Sink

Use this drop-down box to identify the sink [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview). To model an increase in transfer, generator points in the sink injection group will decrease their output, and load points will increase their magnitude in amounts proportional to their participation factors.

If the injection group to use for the sink has not already been created, click the View/Define Groups button in order to create it. After the injection group has been created, it will show up in this drop-down box and can then be selected.

View/Define Groups

If injection groups have not been previously defined in the current case, they can be created by clicking on this button. To create a new injection group, right-click on the resulting injection group [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and choose **Insert** from the popup menu.

Alternatively, if a list of injection groups has been previously saved in an [auxiliary](03-cases-files-and-formats.md#auxiliary-file-format-aux) file, they can be loaded into the current case by right-clicking on the resulting injection group case information display and choosing **Load \> Auxiliary File** from the popup menu.

Island-Based AGC Tolerance

When implementing the transfer, island-based AGC is used. Injection changes for the transfer are first made to the source injection group, and when the power flow is solved, the sink injection group is adjusted for any injection changes due to the source injection group changes and any changes in losses due to the transfer. Because the process to determine required injection changes during the power flow solution MW control loop is an iterative process, a tolerance value must be specified to determine when the changes to the sink injection group are acceptable. This tolerance is NOT the same value that is set with the [power flow solution options for specifying island-based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc).

As a general rule of thumb, the Minimum Step Size should be at least 2 times larger than this tolerance. If not, all changes due to an incremental transfer that is smaller than this tolerance will actually occur between the source and the system slack instead of the source and the sink.

See the [Tolerances in PV Tool](#common-options) topic for more information about how the AGC tolerance interacts with the **[Minimum Step Size](#common-options)** and power flow **MVA Convergence Tolerance**.

Allow only AGC units to vary

Individual generating units are distinguished according to whether they do or do not participate in the automatic generation control (AGC) effort. Each generator has a field that determines whether or not that particular generator is AGC-able. By checking this option, only those generators whose AGC field is set to *YES* will contribute to the power transfer being studied. Otherwise, all units in the injection groups will be allowed to participate regardless of their AGC status.

Enforce unit MW limits

If this option is checked, the output of any participating generating unit will be kept within its designed operating range of MinMW \< Output \< MaxMW. When a unit is pegged at one of its limits, participation factors of the other points in the limited generator's injection group will be adjusted to pick up the difference.

If this option is checked and during the ramping all units in either the source or sink hit their limits, the scenario for which the ramping is being done will be considered critical. The [Critical Reason](#overview) for the scenario will reflect whether the source or sink ran out of resources.

Do not allow negative loads

This is the analog of the previous option for loads. If a load is used as a source point (or sink point when choosing to apply the [reverse transfer](#advanced-options)), it will be decreased to make power available for the transfer. Checking this option will instruct the PV process to keep loads from falling below 0 MW. If a particular load is capped at 0 MW, participation factors for the remaining points in its injection group will be recalculated to make up the difference. If there are not enough resources in the injection group to continue with the transfer, the scenario for which the ramping is being done will be considered critical. The [Critical Reason](#overview) for the scenario will reflect whether the source or sink ran out of resources.

Ramping Method Modified in version 19, build on Aug. 4, 2016

Several different injection group ramping methods are available. These can be selected separately for either the Source or Sink.

Proportional

The MW output for generators and loads in the injection group will be adjusted in proportion to their specified participation factors. These factors will be normalized for all generators and loads participating in the dispatch. Mvar load will be adjusted according to the options found on the [Advanced Options](#advanced-options) tab.

Merit Order

Injection group generators and loads will be dispatched by moving individual generators and loads to their maximum/minimum MW limits as appropriate in succession based on their relative participation factors ordered from highest to lowest. Generator MW limits will be enforced for those units participating in the merit order dispatch regardless of how the **Enforce unit MW limits** option is set. Loads that have both their minimum and maximum MW limits set to zero will not be allowed to increase. They can only decrease to 0 MW. Mvar load will be adjusted by keeping a constant power factor.

Economic Merit Order

This method involves dispatching generators so that they are dispatched within an economic range. Details about how economic merit order dispatch is performed can be found under the [Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the loads will be adjusted in proportion to their participation factors and economic merit order dispatch will not be used.

Merit Order Close Added in version 19, build on Aug. 4, 2016

This method will dispatch generators in a merit order determined by their specified participation factors. Economic generator limits will be enforced during this process regardless of how the **Enforce unit MW limits** option is set. Details about this method can be found under the [Generator Merit Order Close Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the loads will be adjusted in proportion to their participation factors and merit order close dispatch will not be used.

Injection groups have their own set of options that can override the options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

---

<a id="interface-ramping-options"></a>

## Interface Ramping Options

*Source: [`Content/MainDocumentation_HTML/PV_Setup_Interface_Ramping_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Setup_Interface_Ramping_Options.htm)*

Before describing the options used to set up the interface ramping method, the details behind this method are described.

Interface MW Flow Ramping Method

This method is used to modify the flows on selected interfaces along a specified Search Direction. The flows are modified by moving along the Search Direction in specified step sizes. These step sizes are specified with the [Common Options](#common-options). At each step the interface flows are calculated based on the base case flow and the search angle direction. Interface flows are then enforced by solving the OPF algorithm. If the OPF solves, the interface flows are not unenforceable, and the power flow solves, non-critical contingencies are tested at the new nominal transfer level. If a contingency does not solve at a given nominal transfer level, the step size is reduced, new interface flows are determined, and the OPF is solved again to determine the nominal transfer level at which the contingency will be tested again. The reported results provide the highest nominal transfer level at which the OPF algorithm solves, the power flow solves, and all specified interface flows are enforceable.

This method changes how the transfer is modified as part of the PV process. Other inputs to the PV process work the same as they do with the more traditional injection group ramping including [Quanitities to Track](#pvqv-quantities-to-track), [Limit Violations](#limit-violations), [PV Output](#output), and [Plots](37-transient-stability-analysis-dialog-part2.md#plots).

The following image describes the interface ramping method. At a minimum, Interface X must be defined. If this is the only interface defined, the process starts at X0, which is the base case flow on Interface X, and increases the Step Size until a critical point is found. At each step the limit of the interface is increased by the Step Size and the OPF tries to enforce the flow on the interface to this new limit.

If both Interface X and Y are defined, an Angle must also be defined. This specifies the Search Direction. The process starts at X0, Y0, which is the base case flow for both Interface X and Interface Y, and increase the Step Size along the Search Direction until a critical point is found. At each step, the new values for the limits of Interface X and Interface Y are determined base on the distance along the Search Direction and the Angle. The OPF tires to enforce the flows on both interfaces to these new limits.

An optional third Interface Z can be defined. If this is defined, a single MW Setpoint for the flow on this interface must be specified. The ramping process is the same as described above ramping for either Interface X or Interface X and Interface Y, except now the OPF tries to enforce the flow on Interface Z to the same setpoint at each step.

![PV Interface Ramping Method](images/PV_Interface_Ramping_Method.gif)

Interface Ramping Options

These options are found at the top of Setup tab found on the [PV Curves dialog](#dialog) and the Interface Group Ramping Options tab of the same dialog. The remainder of the setup options for interface ramping are found on the [Common Options](#common-options) sub-tab.

![PV Setup Interface](images/PV_Setup_Interface.gif)

Interface X

Select the name of the interface from the dropdown or click the **Find** button to use the Choose an Interface dialog to find the interface.

Use Interface Y

Check this box to define Interface Y.

**Interface Y**

Select the name of the interface from the dropdown or click the **Find** button to use the Choose an Interface dialog to find the interface.

**Angle**

An angle in degrees must be entered to specify the Search Direction as described in the **Interface MW Flow Ramping Method** section. An angle of zero means to increase only Interface X, an angle of 45 degrees means to increase each interface equally, and an angle of 90 degrees means to only increase Interface Y.

Use Interface Z

Check this box to define Interface Z.

**Interface Z**

Select the name of the interface from the dropdown or click the **Find** button to use the Choose an Interface dialog to find the interface.

**MW Setpoint**

Specify the MW flow that should be maintained on Interface Z during the ramping process.

OPF Setup for Interface Ramping

Several options can be set by the user to ensure that the OPF algorithm works as intended:

  - [OPF Common Options](30-optimal-power-flow-part1.md#opf-options---common-options)
      - Minimum Control Change Objective Function is the suggested option although costs can be defined to mimic a minimum control change algorithm and to allow better control over specific generators and loads
  - [OPF Control Options](30-optimal-power-flow-part1.md#opf-options---control-options)
  - OPF Advanced Options
  - [OPF Constraint Options](30-optimal-power-flow-part1.md#opf-options---constraint-options)
      - Interface Percent Correction Tolerance
      - Interface MW Auto Release Percentage
      - Interface Maximum Violation Cost
      - All other options set automatically by the PV tool
  - Generator participation - which ones are on AGC control plus minimum and maximum limits
  - Load participation - which ones are on AGC control plus minimum and maximum limits
  - Specify the Areas or Super Areas that are on OPF control

Several options are set automatically by the PV tool to ensure that interfaces are enforced correctly:

  - [OPF Constraint Options](30-optimal-power-flow-part1.md#opf-options---constraint-options)
      - Only interface constraints will be enabled
  - Only interfaces selected in the PV setup are monitored
  - Interfaces are enforced with equality constraints
  - Interface limits that are enforced
  - Contingent interface elements will always be ignored

---

<a id="advanced-options"></a>

## Advanced Options

*Source: [`Content/MainDocumentation_HTML/PV_Setup_Advanced_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Setup_Advanced_Options.htm)*

These options are found on the Advanced Options sub-tab located on the [Setup](#setup) tab of the [PV Curves dialog](#dialog). These options only apply when using [Injection Group Ramping](#injection-group-ramping-options).

![PV Setup Advanced Options](images/PV_Setup_Advanced_Options.gif)

The power transfer that occurs during the PV analysis is a real power (MW) transfer. Loads can be specified as part of either the source or sink injection group that define the transfer. When loads are included in the transfer, the default is to only adjust the real power (MW) component of the load and leave the reactive power (Mvar) component constant. If any change is made to the reactive power load (Mvar) during the transfer, the default is to have all changes be made to the constant power component of the load. The Advanced Options tab allows specification of load variation for both real and reactive load to be something other than the defaults during the transfer.

The transfer amount and how the transfer is adjusted are determined by options found on the [Common Options](#common-options) tab.

How should reactive power load change as real power load is ramped?

Total read power load changes, *ΔP*, at each load are determined based on the load's participation factor as defined with its associated injection group and the amount of transfer that is being implemented. *ΔP* is then used in conjunction with the selected reactive power change option to determine the associated total reactive power change, *ΔQ*, at each load.

Maintain the MW/MVAR ratio at each load, but then scale MVAR by a factor of

The total reactive power change, *ΔQ*, is determined based on the power factor, *pf*, at each nominal load (*P*<sub>nom</sub>*,Q*<sub>nom</sub>) prior to the load change and the change in total real power load, *ΔP*, due to the transfer. The power factor is determined by the following:

![PV Setup Advanced Options Equation1](images/PV_Setup_Advanced_Options_Equation1.gif)

An additional multiplier, *pfQMult*, can be specified in order to modify the total reactive power load change to allow adjustment away from the present power factor. This multiplier is 1.0 by default. The change in reactive power load is then:

![PV Setup Advanced Options Equation2](images/PV_Setup_Advanced_Options_Equation2.gif)

Maintaining a constant MW/MVAR ratio implies a sign convention that is lost when applying the arctan function to the ratio. An additional check is done to make sure that the calculated *ΔQ* is in the correct direction (maintains the correct leading or lagging power factor).

![PV Setup Advanced Options Equation3](images/PV_Setup_Advanced_Options_Equation3.gif)

When loads are specified as constant power, constant current, and constant impedance components (ZIP components) rather than simply all constant power, the total load becomes a function of voltage. Maintaining a constant power factor at each load requires that we use nominal load (load at 1.0 pu voltage) that does not change as a function of voltage. When only constant power components are specified, the actual load is the same as the nominal load. Therefore, in all situations the power factor is determined based on the nominal load.

As MW changes, change the MVAR at a power factor of

This option allows the specification of power factor, *pf*<sub>specified</sub>, for defining the total reactive power change, *ΔQ*, at a load. The change in reactive power load is then dependent on the change in total real power load due to the transfer, *ΔP*, and this specified power factor.

![PV Setup Advanced Options Equation4](images/PV_Setup_Advanced_Options_Equation4.gif)

For this option, *ΔQ* is assumed to be in the same direction (has the same sign) as *ΔP* .

Injection groups have their own set of options that can override the options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

Load Component Variation

The total real power load change, *ΔP*, at a load during a PV transfer is determined by the load's participation factor as defined with its associated injection group and the amount of transfer that is being implemented. The total reactive power load change, *ΔQ*, is determined by the option selected for how reactive power should change during ramping as explained in the previous section. Total load change, (*ΔP*,*ΔQ*), at a load can be broken into ZIP components for constant power (*ΔP*<sub>S</sub>,*ΔQ*<sub>S</sub>), constant current (*ΔP*<sub>I</sub>,*ΔQ*<sub>I</sub>), and constant impedance (*ΔP*<sub>Z</sub>,*ΔQ*<sub>Z</sub>). During the PV transfer, the user can specify how changes in load due to the transfer should be split among these components.

The constant current and constant impedance components are a function of voltage and the nominal values specified for these components. Because of this, it becomes important to determine the load changes for the components based on nominal voltage and then apply these changes to the nominal components.

All changes apply to constant power (S MW, S MVAR)

All changes to load will be made to the constant power component:

![PV Setup Advanced Options Equation5](images/PV_Setup_Advanced_Options_Equation5.gif)

The constant power component of load is not dependent on voltage so the total load change can be applied directly to the constant power component.

Vary in proportion to existing Z,I,P ratios

This option will change the load at a given load such that the ratios of the ZIP components do not change during the load adjustment. The existing ZIP ratios at a load are determined based on the present nominal load prior to any change due to the transfer. The existing total nominal power (*P*<sub>nom</sub>,*Q*<sub>nom</sub>) at a load is the sum of the components:

![PV Setup Advanced Options Equation6](images/PV_Setup_Advanced_Options_Equation6.gif)

The component ratios are simply the ratio of each nominal component to the total nominal load at a load:

![PV Setup Advanced Options Equation7](images/PV_Setup_Advanced_Options_Equation7.gif)

The resulting change in nominal load for each load component at a load is then the product of the ratio of each component and the total nominal power change:

![PV Setup Advanced Options Equation8](images/PV_Setup_Advanced_Options_Equation8.gif)

Where the total nominal power change is determined from the total power change required at a load as a function of the present voltage, *V*, at the bus:

![PV Setup Advanced Options Equation9](images/PV_Setup_Advanced_Options_Equation9.gif)

*ΔQ*<sub>nom</sub> is calculated from *ΔP*<sub>nom</sub> based on the selection of the option on how reactive power should change during the ramping as described in the previous section.

Vary using proportions specified below:

The factors are divided into four groups: real power load in the source injection group, real power load in the sink injection group, reactive power load in the source injection group, and reactive power load in the sink injection group. Each of these groups determines how the various components will change based on whether the load change is being done to real or reactive load and whether the load is part of the source or sink injection group. The default setting for each group is to apply changes only to the constant power component; **Power (S)** factor is 1 while all other factors are 0. The sum of the factors for each grouping must add up to 1. The **Impedance (Z)** factors are not enterable and are calculated to ensure that the sum is always 1. Simply adjust the **Power (S)** and **Current (I)** factors to appropriate values and the **Impedance (Z)** factor will be set automatically.

The calculation for determining the change in load components is done the same as described above when using existing ZIP ratios except that the ratios are user-specified here.

Reverse Transfer

The standard way of performing a PV analysis is to increase a transfer from the source to the sink in positive step increments determined by the Initial Step Size and other parameters that control the size of the step. When a contingency does not solve at zero transfer (base case conditions), it might be possible to find a solvable point by adjusting generation and/or load in the system. The Reverse Transfer option will attempt to find this solvable point by increasing a transfer from the sink to the source (instead of source to sink). This is done by incrementing the transfer from the source to the sink in negative step increments, effectively making the transfer go from the sink to the source.

When the **Apply Reverse Transfer** box is checked, an attempt will be made at finding a solvable point by applying the reverse transfer (sink to source) for any contingency that will not solve at zero transfer. A condition for this option to be used is that the base case power flow must solve.

When choosing to attempt the reverse transfer for contingencies that will not solve, all unsolvable contingencies will be processed even if the number of unsolvable contingencies exceeds the number of critical scenarios specified on the [Results](#results) tab. The reverse transfer process will be done for all unsolvable contingencies prior to the standard PV process. After the reverse transfer process completes, the standard PV process (positive transfer from source to sink) will be performed on all contingencies that do solve at zero transfer level as long as the number of critical scenarios specified is not exceeded already by the number of contingencies that wouldn't solve as zero transfer.

The initial step magnitude by which the transfer is increased is the Initial Step Size specified with the Common Options. When a transfer level is found at which a contingency will solve, the step magnitude is reduced by the reduction factor specified with the Common Options. This is done in an attempt to find the minimum transfer required to reach a solvable point. This process will continue until a solvable point is found for each contingency of the **Maximum Reverse Transfer (MW \> 0)** threshold is exceeded. It is likely that no solvable point can be found for some contingencies. The Maximum Reverse Transfer threshold should be set such that a reasonable transfer amount is attempted before abandoning the attempt at finding a solvable point. This process could be very time consuming if there are a number of contingencies that do not solve at zero transfer.

In addition to attempting to find a solvable point, the reverse transfer process can also attempt to find a solvable point at which all voltages are considered adequate. To check for adequate voltages during the reverse transfer process, check the option to **Stop when voltage becomes inadequate** that is found on the [Limit Violations](#limit-violations) tab of the PV Curves dialog. This will force the process to find a reverse transfer point at which the contingency solves and all voltages are above the voltage level specified as inadequate. The inadequate voltage level is specified with the **Voltage level to consider inadequate** option also found on the Limit Violations tab.

If a reverse transfer point is found at which a contingency will solve, and voltages are adequate if choosing to include that check, the [results](#results) for the scenario will list the **Critical Reason** as *SRT - original critical reason* with *original critical reason* being the reason why the contingency was considered not to be solved at the zero transfer level. The **Max Export**, **Max Import**, and **Max Shift** values that are reported are the minimum (in magnitude) transfer levels at which the contingency will solve and any voltage conditions are met. Values for any parameters that are being tracked through [Quantities to Track](#pvqv-quantities-to-track) will also be recorded at this transfer level. If there are multiple steps at which the contingency will solve and any voltage conditions are met while trying to find the minimum step, multiple transfer level points will be recorded making it possible to plot a few points of a PV curve.

If during the reverse transfer process no point can be found for which a contingency will solve and voltage conditions are met, the original results will be reported as if the reverse transfer process was not attempted.

If enforcing generator MW limits and/or not allowing negative loads during the transfer causes either the source or sink to not have enough resources to meet the required transfer, two other Critical Reason messages are possible. If the sink is maxed during the transfer, the **Critical Reason** will be given as *RT Sink Maxed - original critical reason*. If the source is maxed during the transfer, the Critical Reason will be given as *RT Source Maxed - original critical reason*. The **Max Export**, **Max Import**, and **Max Shift** values reported will be the values at which either the source or sink hit limits. Either of these messages indicates that the contingency will not solve or voltage conditions are not met, but the reverse transfer cannot continue because there are not enough resources in either the source or sink to do so. If either the source or sink is at its limits the contingency solution will still be attempted. If the contingency does solve and the voltage conditions are met, the **Critical Reason** will be given as *SRT - original critical reason*.

When the reverse transfer process completes, the system state is returned to the base case state in place when the PV analysis was first initiated. No reverse transfer amount will remain in the system state upon completion of the reverse transfer process even if the analysis is such that only the reverse transfer process is completed and no forward transfer scenarios are attempted.

---

<a id="pvqv-quantities-to-track"></a>

## PV/QV Quantities to Track

*Source: [`Content/MainDocumentation_HTML/PV_Quantities_to_Track.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Quantities_to_Track.htm)*

Specification of quantities to track during analysis is almost identical for both the PV and QV analysis (exceptions will be noted below). For PV analysis, the Quantities to Track tab is accessed from the [PV Curves](#dialog) dialog, and for the QV analysis, this tab is accessed from the [QV Curves](#dialog-1) dialog. Quantities to track are monitored and stored as the transfer increases for the PV analysis or the voltage set-point changes for the QV analysis. Any unselected system parameters will not be saved. The Quantities to Track page contains several sub-tabs that allow the monitoring of different types of objects including: buses, generators, injection groups, lines, transformers, shunts, interfaces, and the case as a whole. There is also a sub-tab for monitoring devices at limits.

Each of the object sub-tabs contains fields that can be tracked during the analysis. The default tracking for all of these fields is *NO*. To monitor a particular quantity, double-click the corresponding field entry to toggle it to *YES*, or in the case of some line quantities, the appropriate monitoring direction.

Quantities that are tracked can be plotted using the [Plot](#plot) page. They can also be stored to an auxiliary file with both the PV and QV tools. With the QV analysis a special file is created that stores the tracked quantities. For more information on this see the Extra Monitoring File section with the [QV Curves Options: Output](#output-1) topic.

Buses

**Voltage** - per unit voltage

**kV Voltage** - actual voltage in kV

**Angle** - voltage angle in degrees

**MW Load** - total real power load

**Mvar Load** - total reactive power load

**dV/dQ** - sensitivity of voltage to change in reactive power injection at the same bus. This value is not calculated for QV analysis and should not be monitored.

**VP Sensitivity** - sensitivity of voltage change due to real power transfer. For PV analysis this is the sensitivity of the voltage at the bus due to the selected transfer from source to sink. This value is not calculated for QV analysis and should not be monitored.

VP sensitivities can also be calculated using the [Flow and Voltage Sensitivities tool](20-sensitivities.md#flow-and-voltage-sensitivities). With this tool there is an option to turn AVR control off for generators and continuous switched shunts that are at buses participating in the transfer. This same option is not available when calculating these sensitivities during the PV analysis because of the overhead of additional power flow solutions that would be required at each transfer step to implement this option. Leaving devices on AVR control will maintain the voltage setpoint at the regulated buses creating PV buses in the power flow Jacobian. At PV buses the sensitivity of voltage to a transfer will be zero.

**Shunt Inj** - total switched shunt reactive power (Mvar) output

For PV analysis if the intent is to trace PV curves, it makes sense to monitor at least one bus voltage. The process will not automatically monitor and store voltage quantities.

If the [Integrated Topology Processing](35-integrated-topology-processing.md#topology-processing-overview) add-on is available, an additional option will be available on the Buses tracking tab, the **Modify Existing Bus Tracking to Track Only Single Bus Per Super Bus** button. When using topology processing, only a single bus per super bus will be in the consolidated case. That means that the parameters for each bus in the super bus will be the same, i.e. same voltage magnitude and angle, etc. This button can be used to eliminate any excess tracking that would just take up computer memory by tracking essentially the same quantities at the same bus multiple times. To take advantage of this option and only track a single bus per super bus, first set up the bus tracking to track all of the necessary quantities. Then push the **Modify...** button. The field entries in the table will then be updated to only include a single bus per super bus. When determining the primary node (the primary node is the bus that will ultimately be tracked during the analysis) and super buses, the active defined contingencies will be used to determine how the case is consolidated. Because the consolidation can be different based on the contingency set, or lack thereof, it is best to just define the tracking to include all necessary buses and use this option to refine the list down to a single bus per super bus rather than manually trying to maintain such a list.

Generators

**Gen MW** - real power output

**Gen Mvar** - reactive power output

**Mvar Reserve** - reactive power reserves in the positive direction (Max Mvar - Mvar)

Injection Groups

This allows the monitoring of injection group parameters.

**Mvar Reserve** - total reactive power reserves in the positive direction for all generators in the group (Max Mvar - Mvar)

**Gen MW** - total real power output of all generators in the group

**Gen Mvar** - total reactive power output of all generators in the group

**Load MW** - total real power load for all loads in the group

**Load Mvar** - total reactive power load for all loads in the group

Lines

Note: all branches (whether transmission lines or transformers) appear on the **Lines** sub-tab.

**Branch MW** - real power flow on the branch in either the FROM-TO or TO-FROM direction

**Branch Mvar** - reactive power flow on the branch in either the FROM-TO or TO-FROM direction

**Branch MVA** - total power flow on the branch in either the FROM-TO or TO-FROM direction

**Branch MW Loss** - real power loss

**Branch Mvar Loss** - reactive power loss

**Branch PTDF** - [Power Transfer Distribution Factor](20-sensitivities.md#power-transfer-distribution-factors) on the branch due to a defined real power transfer. This parameter only makes sense when doing the PV analysis. The PTDF is calculated for the transfer from the selected source to sink. This is a meaningless quantity for the QV analysis and should not be monitored.

**Xfmr Tap** - tap ratio if the branch is a transformer

For the flow (Branch MW, Branch Mvar, and Branch MVA) and Branch PTDF fields, double-clicking on a particular entry will toggle its value from *NO* to *FROM-TO*, and double-clicking again will toggle its value to *TO-FROM*. Double-clicking on a loss field or Xfmr Tap field will toggle the value between *YES* and *NO*.

Transformers

Note: all branches (whether transmission lines or transformers) appear on the **Lines** sub-tab. See **Lines** above for setting up common branch quantities. Only branches containing transformers will appear on the **Transformers** sub-tab.

**Type** - set the transformer type (Fixed, LTC, Mvar, or Phase)

**Reg Val** - regulated value for the transformer control

**Tap Pos** - tap position

**Reg Err** - deviation of the regulated value from the regulation Min/Max range

All fields specified above except for the Type field are used to determine which quantities should be monitored and stored during the analysis. The Type field can be accessed here in order to change the type of transformer. The type will not be monitored during the analysis.

Shunts

This allows the monitoring of switched shunt parameters.

**Actual Q** - actual reactive power output

**Actual P** - actual real power output

**Nom Q** - nominal reactive power output

**Nom P** - nominal real power output

**Reg Err** - deviation of the regulated value from the regulation Min/Max range. This can either be in per unit voltage or Mvar depending on the type of regulation that the shunt is doing.

**Reg Val** - value of regulated quantity at the regulated bus. This can either be in per unit voltage or Mvar depending on the type of regulation that the shunt is doing.

Interfaces

**MW Flow** - real power flow

**Mvar Flow** - reactive power flow

**MVA Flow** - total power flow

**MW Loss** - real power losses

**Mvar Loss** - reactive power losses

**Interface PTDF** - [Power Transfer Distribution Factor](20-sensitivities.md#power-transfer-distribution-factors) on the interface due to a defined real power transfer. This parameter only makes sense when doing the PV analysis. The PTDF is calculated for the transfer from the selected source to sink. This is a meaningless quantity for the QV analysis and should not be monitored.

Case

These options allow the tracking of case quantities to provide a better picture of what is going on in the case as a whole without requiring the individual tracking of quantities that make up the case total. These quantities are determined in the same manner as those found in the Case Totals section of the [Case Summary dialog](05-case-information-displays-by-object-part1.md#case-summary).

Available quantities for tracking include:

**Load MW/Mvar** - total real or reactive power load for the entire case

**Generation MW/Mvar** - total real or reactive power generation for the entire case

**Shunts MW/Mvar** - total real or reactive shunt injection from switched shunts, bus shunts, and line shunts. A positive value will indicate shunt load where a negative value will indicate shunt compensation such as capacitance.

**Losses MW/Mvar** - total real or reactive power losses for the entire case

ATC Extra Monitors

This option is only available when using the PV Curves tool. The following will appear at the bottom of the Quantities to Track tab accessed from the PV Curves dialog.

![PV Quantities To Track ATC Extra Monitors](images/PV_Quantities_To_Track_ATC_Extra_Monitors.jpg)

[ATC Extra Monitors](32-available-transfer-capability.md#atc-extra-monitors-dialog) are typically used with the [ATC add-on tool](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) to monitor special branches or interfaces in addition to ones monitored by setting the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings). This would be done for example if trying to determine an interface flow limit so that interface can be used as a proxy for limiting the transfer between a source and a sink. This same functionality is desirable when using the PV analysis. Both the ATC and PV analyses are similar in that they study the impacts of real power transfers. The ATC analysis is concerned with thermal limitations while the PV analysis looks at voltage stability limitations. Use of the ATC Extra Monitors with the PV analysis could be additionally useful for developing a proxy interface to help prevent voltage stability problems.

Click the **Define ATC Extra Monitors** button to view a list of existing ATC Extra Monitors or create new ones. To include monitoring of these elements at part of the PV analysis, check the **Include ATC Extra Monitors** box.

When monitoring ATC Extra Monitors with the PV analysis, the real power (MW) flow on the specified branches and/or interfaces will be monitored at each base case transfer level. No monitoring is done with contingencies implemented.

ATC Extra Monitors can be added to the [Overview](#overview) table, available on the [PV Results](#results) tab, via the [Display/Column Options...](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog. When displayed in this table, the value reported with the extra monitor is the flow on the extra monitor at the Max Shift level of transfer for the given scenario. Values for ATC Extra Monitors will only be displayed in the Overview table for critical scenarios.

Values for ATC Extra Monitors can also be displayed in the Overview table for transfer levels at which inadequate voltages are found. These values will only be available if using the option found on the [Limit Violations](#limit-violations) tab to **Store inadequate voltages**. Fields for reporting these values are found in the Inadequate Voltage folder in the list of available fields for the Overview table. The value reported for each extra monitor is the flow on the extra monitor at the **Inadequate Voltage Nominal Shift** transfer level.

Access to the ATC Extra Monitor values stored at transfer levels other than the Max Shift transfer for critical scenarios and values stored for non-critical scenarios is available through SUBDATA sections of the PWPVResultListContainer data type that is saved when saving PV results to an auxiliary file or in the output file saved when choosing to save results to file from the [PV output](#output) tab.

Devices at Limits

The **Devices at Limits**sub-tab allows the selection of various options to track devices that hit or back off limits during the PV analysis. Devices at limits can only be tracked for PV analysis and will not be tracked for QV analysis. Generators and switched shunts at var limits, LTC transformers at tap limits, and lines and interfaces at thermal limits can all be tracked.

![PV Quantities To Track Devices At Limits](images/PV_Quantities_To_Track_Devices_At_Limits.jpg)

To track the limits of any of these devices, check the appropriate checkbox. Next to each checkbox there is a dropdown box for selecting an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) to apply to the tracking. A new filter can be defined for a particular device by clicking the **Define** button next to that device. The filter will limit the number of devices that get tracked. It is a good idea to define a filter for tracking devices so that all elements in the case will not be tracked. Keep in mind that tracking any quantities will take up space in the computer memory. If too many devices are tracked, it is possible to run out of memory.

With these options, device limits are only tracked in the base case at valid transfer levels. No device limit tracking is done with contingencies implemented.

---

<a id="limit-violations"></a>

## Limit Violations

*Source: [`Content/MainDocumentation_HTML/PV_Limit_Violations.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Limit_Violations.htm)*

The Limit Violations tab is found on the [PV Curves dialog](#dialog). There are two sub-tabs that allow for the definition of what is considered a critical scenario that will force the PV process to stop and what is considered a violation for monitoring only.

The options on the **Critical Scenarios** sub-tab will force the PV process to stop and consider a scenario critical if the defined criteria are met.

![PV Limit Violations Critical Scenarios](images/PV_Limit_Violations_Critical_Scenarios.png)

Inadequate voltage level

Voltages can be considered inadequate if they are low or high. Similar options exist for specifying the voltages to consider inadequate, whether high or low.

Stop when voltage becomes inadequate

Checking this box will stop the PV process for a scenario when any monitored bus voltage falls below the voltage level to consider inadequate or exceeds the high voltage level to consider inadequate. The [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) dictate which buses are monitored.

Log inadequate voltages

Check the appropriate box to store inadequate low or high bus voltages encountered for each scenario. The [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) dictate which buses are monitored. Lists of inadequate voltages for each scenario and transfer level will then be available for viewing as local menu options obtained by right-clicking on the [Overview](#overview) table (**PV Curve records \> Show Inadequate Voltages** or **PV Curve records \> Show Inadequate High Voltages**). Inadequate voltages will also be stored in the SUBDATA section of the PWPVResultListContainer DATA section when storing PV results to an auxiliary file.

**Interpolate inadequate voltages**- If checked add the ability to estimate at what transfer level a voltage becomes inadequate by linearly interpolating between the two transfer levels where it goes from adequate to inadequate. It also will interpolate if an inadequate voltage occurs at the zero transfer level to determine the negative transfer at which the voltage becomes inadequate.

There are several fields available on the **Overview** table that provide summary information about low inadequate voltages:

**Inadequate Voltage Nominal Shift**- nominal transfer level at which the first inadequate low voltage is recorded

**Inadequate Voltage Worst Voltage**- minimum voltage of all buses that have inadequate low voltages at the Inadequate Voltage Nominal Shift transfer level

**Inadequate Voltage Worst Voltage Bus**- bus with the minimum low voltage of all buses that have low inadequate voltages at the Inadequate Voltage Nominal Shift transfer level

**Inadequate Voltage ATC Mon**- if any ATC Extra Monitors are being tracked during the analysis, this will list of the flow on the given extra monitor at the Inadequate Voltage Nominal Shift transfer level

If choosing to **Stop when voltage becomes inadequate**, no inadequate voltages will be stored even if this option is selected. When a scenario becomes critical because of inadequate voltages, the results that are given in the Overview table are from the last transfer level at which all voltages were adequate. The inadequate voltage reported in the results is the voltage that would be inadequate if we went beyond the reported transfer level. Because of how the reporting works to report the last non-critical results, it makes sense that there would not be any inadequate voltages stored.

The inadequate voltage thresholds when choosing to either stop or log inadequate voltages are determined by the following options. Options exist for specifying both the low and high inadequate voltage thresholds:

**Specify voltage for all buses in pu** - specify a single inadequate voltage threshold to be used for all monitored buses

**Use Low Voltage Violation Limits for each bus** or **Use High Voltage Violation Limits for each bus** - use the limit monitoring settings

**Use a specified Low Voltage Limit Set** or **Use a specified Low Voltage Limit Set** - select a limit set to specify the limit from the drop-down. Up to four (A-D) specific limit sets can be specified for a bus. When using this option, all monitored buses should have the selected limit set specified. If not, the default voltage limit will be -1.

**Do not consider radial buses to have inadequate voltage (including buses that become radial due to a contingency)** - check this box to exclude monitoring buses that are radial regardless of whether they are radial because they are connected to the system by a single line or because they are radial because they are connected to the system via a single in-service line (i.e. they could have more connections but all but one of the connections is open).

This option works somewhat in conjunction with a similar option found on the [Limit Monitoring Settings dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). The option **Do not monitor radial lines and buses** found on the Limit Monitoring Settings dialog will exclude any bus from monitoring if it is radial in the base case. This limit monitoring settings option considers buses to be radial if they are connected by a single branch and only a single branch. When the limit monitoring settings option is selected, radial buses by that definition will be excluded from the PV monitoring. When the PV option is selected, buses that are connected by only a single in-service branch after the application of any scenario contingency, or in the base case if there is no contingency, are considered radial and will be excluded from the monitoring. The PV option is enforced regardless of whether or not the option with the limit monitoring settings is selected.

Stop when dV/dQ sensitivities become negative

Checking this box will treat negative dV/dQ bus sensitivities as a critical scenario. If this option is used and there are negative dV/dQ sensitivities, the critical transfer level will be determined by backing off the transfer to the point at which no dV/dQ sensitivities are negative.

Buses that are monitored for negative dV/dQ sensitivities are the buses that are set to have their dV/dQ sensitivities tracked with the [Quantities to Track](#pvqv-quantities-to-track) setup.

Branch and Interface Violations

Branch and interface violations can be monitored or treated as critical scenarios. Limit Monitoring Settings determine which branches and interfaces are monitored and the limits that should be used for determining violations. For each type of element the following options are available:

**Ignore** - completely ignore violations

**Log Only** - log the violations. If there are any logged violations the Overview table will have entries for **Show Branch Violations** and **Show Interface Violations**.

**Stop When Violated**- treat a violation as a critical scenario and stop the analysis of a scenario when a limit is encountered

**Stop in Base Case Only** - only treat the base case scenario as critical and stop the analysis of this scenario when violations are encountered. Contingency scenarios will continue processing if violations are encountered.

The options on the **Monitor Only** sub-tab are for reporting purposes only and will not force the PV run to stop.

![PV Limit Violations Monitor Only](images/PV_Limit_Violations_Monitor_Only.png)

Identify bus voltages with...

These options will store monitored bus voltages that violate either their high or low voltage limit as of the last successful solution for each scenario. Only those buses that are set to be monitored based on the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) will be monitored, and the low and high voltage limits for each bus are also determined by the limit monitoring settings.

**Low Voltage Violations** - check this box to store the buses that have low voltage violations

**Always Report Lowest Voltage** - check this box to always store the lowest voltage even if it is not a violation

**High Voltage Violations** - check this box to store the buses that have high voltage violations

**Limit Group Definitions** - click this button to open the [Limiting Monitoring Settings dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog)

When choosing to identify limit violations, the [Overview](#overview) table on the [PV Results](#results) tab will contain information about the number of violations (\#Viol), worst voltage violation (Worst V Viol), and bus at which the worst voltage violation occurs (Worst V Bus). Also, for any scenario in which a violation occurs, the **Show Violations** option is enabled on the local right-click menu of the Overview table. Choosing this option will open a table detailing all of the violations.

---

<a id="output"></a>

## Output

*Source: [`Content/MainDocumentation_HTML/PV_Output.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Output.htm)*

The Output tab is found on the [PV Curves dialog](#dialog) and allows the designation of where data should be logged.

During the PV analysis, the value of each monitored quantity is recorded at each solved transfer level. This data will only be present in memory unless some output file is specified.

Save Results in PWB File

Added in version 23PV results can optionally be stored in PWB files by checking this box; options are always stored.

Specifying File for Results

Save results to file

Click this option to save results to a file. In the adjacent text box supply the complete path and name for the output file. If a directory is included with the output file and it does not exist, the directory will be created. If the directory cannot be created, an error will result and the PV analysis will not start. Click the **Browse** button to open a save dialog that will allow selection of the output file. Click the **View** button to open the specified output file in a text editor. The **View** button will be enabled if the specified output file exists.

The results will be saved as a comma-separated variable file regardless of the file extension chosen. Set the file extension to .CSV to make the file type more recognizable by programs such as Excel. If using the save dialog opened with the Browse button, the Save as type field on the save dialog should be set to reflect the desired file extension. Regardless of the file extension chosen, the file is a text file with all contents separated by commas.

When saving results to a file, a log file will also be created that indicates how long the entire PV process took and the different base case and contingency scenarios examined at each nominal shift level. This log file will use the same file name specified for the output file with "\_LOG" appended to the end of the file name. The log file will be saved with .TXT extension. If running multiple instances of Simulator for PV analysis, a unique file name must be given to each set of results to avoid overwriting results created from other instances.

Transpose results

Click this option to transpose the columns and rows in each section of the output file. The output file is divided in sections for each of the studied scenarios. The default file format organizes the file so that each row represents a transfer level and each column represents a tracked quantity. The transposed file is formatted such that each row represents a tracked quantity with each column representing a transfer level. This format is useful when the number of tracked quantities exceeds the number of transfer levels.

Single Header File

Additional file formats are available when saving results to file when not transposing the file. If using the default output format (Single Header file option and Transpose results option both unchecked), each scenario will be written as a section with a header line at the beginning of each section indicating what fields are included. Scenarios that become critical during the analysis will be listed with the base case scenario at the shift level at which they became critical. An example of this format is given below:

**Example for Default PV Output:**

RESULTS FOR PV STUDY "PVSTUDY" \*

\*Scenario\*\* "base case"

"Nominal", "Export", "Import","Bus 3 (Three\_138.0) PU Volt","Bus 5 (Five\_138.0) PU Volt","Newly Critical"

0.0000, 0.0000, 0.0000, 0.9927, 1.0066,

100.0000,100.0000,-98.7365, 0.9928, 1.0062,

200.0000,200.0000,-193.4265, 0.9928, 1.0054,

300.0000,300.0000, -278.6270, 0.9928, 1.0043,

400.0000,400.0000, -365.9341, 0.9927, 1.0031,

500.0000,500.0000,-449.7520, 0.9926, 1.0015,

600.0000,599.9999,-525.2490, 0.9924, 0.9996,

650.0000,650.0000,-563.8931, 0.9923, 0.9986,

675.0000,674.9999,-582.8196, 0.9923, 0.9980,L\_00002Two-00006SixC1 (Reached Nose)

If choosing to use a **Single Header File** by checking this option, only a single field header will be shown at the top of the file. The first line of the file indicates that these are the results for a PV study. Following the header are lines indicating scenarios that have become critical during the analysis. Following this information is the single header line that indicates what fields are provided with the results. Following the header are the results for each scenario. An example is given below:

**Example Single Header File Output:**

RESULTS FOR PV STUDY "PVSTUDY"

"Newly Critical","L\_00002Two-00006SixC1 (Reached Nose)"

"Scenario","Nominal","Export","Import","Bus 3 (Three\_138.0) PU Volt","Bus 5 (Five\_138.0) PU Volt"

base case, 0.0000, 0.0000, 0.0000, 0.9927, 1.0066

base case, 100.0000,100.0000, -98.7366, 0.9928, 1.0062

base case, 200.0000,200.0000,-193.4267, 0.9928, 1.0054

base case, 300.0000,300.0000,-278.6272, 0.9928, 1.0043

base case, 400.0000,400.0000,-365.9344, 0.9927, 1.0031

base case, 500.0000,500.0000,-449.7524, 0.9926, 1.0015

base case, 600.0000,599.9999,-525.2494, 0.9924, 0.9996

base case, 650.0000,650.0000,-563.8935, 0.9923, 0.9986

base case, 675.0000,674.9999,-582.8201, 0.9923, 0.9980

L\_00001One-00002TwoC1, 0.0000, 0.0000, 0.0000, 0.9906, 1.0067

L\_00001One-00002TwoC1, 100.0000, 100.0000,-98.7366, 0.9882, 1.0062

L\_00001One-00002TwoC1, 200.0000, 200.0000,-193.4267, 0.9849, 1.0053

State Archiving

In addition to saving how the monitored quantities vary with the transfer, the entire system state can be saved to file at regular intervals during the analysis. This can be helpful if for analyzing particular transfer levels more closely after the analysis is complete. Keep in mind that, depending on the size of your system, archiving states frequently can require significant disk space and will delay the process.

The state that is saved to file has automatic generation control disabled for the entire case. This is to prevent confusion when these cases are opened. With this option disabled and any changes are made to a case, the only generator that will move will be the system slack. The onus is then on the user to decide if automatic generation control should be enabled for the case and how this will be handled on an area, superarea, or island-wide basis.

When using [Integrated Topology Processing](35-integrated-topology-processing.md#topology-processing-overview), state archiving is available. The state will be archived using the consolidated planning-type model.

The following options are available for archiving states:

Do not save system states

This is the default option. No system states will be saved to file.

Save only the base case for each critical contingency

The base case state without the contingency implemented will be saved to file for each scenario that is critical. The state will be saved at the transfer level that is reported as the critical Max Shift value as given in the [Results](#results).

Save all states

Choosing this option will save to file all scenarios at each valid transfer level. Contingency scenarios will be saved with the contingency implemented, unless at the critical transfer level. If a scenario is critical, the base case state without the contingency implemented will be saved at the critical transfer level.  For critical scenarios, the critical transfer level is the value that is reported as the Max Shift value given in the [Results](#results). The base case state with just the transfer implemented will also be saved for all scenarios at all transfer levels at which the scenario will solve.

Save state as

Use this drop-down to select the file type that should be used when archiving states. Files can be saved as [PowerWorld auxiliary files (\*.aux), PowerWorld binary files (\*.pwb)](03-cases-files-and-formats.md#case-formats), or both.

Specify a prefix to use in naming the state archives

Saved state files will be distinguished by a naming convention based on the scenario name and transfer level or critical state indicator and scenario name. Use a prefix to further distinguish these files if saving multiple study results to the same directory.

State Archiving and Plot Storage

Specify the directory where state files should be saved. Click the **Browse** button to open a dialog to use for selecting the directory. This directory is also the location where plots files automatically generated during a run are stored.

---

<a id="results"></a>

## Results

*Source: [`Content/MainDocumentation_HTML/PV_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Results.htm)*

The PV Results page is found on the [PV Curves dialog](#dialog). This is the page from which the PV analysis is launched and provides access to all of the results. This page is divided into some general information at the top and sub-tabs at the bottom that provide details about the results.

![PV Results](images/PV_Results.jpg)

Run

Click this button to start the analysis.

Stop

Click this button to stop the analysis once it has been started. This button will only be enabled if the analysis has been started.

Restore Initial State on Completion of Run

Check this box to return the system state to the initial state that existed prior to running the PV analysis. When not checked, the state that the case is left in is the last analyzed scenario with the transfer in place but any contingency removed (i.e. base case state at the critical transfer level).

When not returning the system state to the initial state, care must be taken when rerunning PV analysis. When PV analysis is started, the new initial state becomes the current system state. If it is desirable to rerun from the original initial state, this state must be restored manually so that the correct analysis is done.

Status information

Status messages will be displayed as scenarios are examined and the power transfer changes.

Summary information about the transfer

The **Gen MW** and **Load MW** values reflect the actual total of those components in the source and sink injection groups in the current system state as the transfer changes. The **Present nominal shift** is updated to reflect the transfer that is applied in the current system state. If the analysis is actively ramping the transfer and studying scenarios, the **Present step size** field will update with the step size currently in use. Once the analysis is complete, this value is not very meaningful and this box will be blank.

Added in version 20, build on Oct. 23, 2017

At the end of the PV analysis, this will be the transfer amount that is currently present in the system state. This can be the transfer amount of the last critical scenario that was studied or zero. It will be zero if the option to **Restore Initial State on Completion of Run** is selected. It will also return to 0 if the manual option to **Restore initial state** is applied.

View detailed results

Click this button to open a text editor that contains detailed solution results. The results are in the same format as the output file described on the [Output](#output) tab.

Other actions \>\>

Clicking this button opens a menu that provides access to a number of other options:

View activity log

This option will be enabled if choosing to save the output to a file via options found on the [Output](#output) tab. If enabled and selected, the log file will be displayed.

View detailed results

This option does the same thing as the **View detailed results** button described above.

Clear results

This option will destroy all of the results. Nothing is done to the system state.

Save critical contingencies

Only those contingencies for critical scenarios will be saved to an auxiliary file. Selecting this option will open a dialog prompting for a file name. In addition to contingency definitions, additional data including limit monitoring settings, contingency solution options, and power flow solution options will be saved.

Restore initial state

When the PV analysis first starts running, the present system state is stored in memory and identified as the initial state. Choose this option to return back to the initial state.

When the analysis completes, the state that the case is left in is the last analyzed scenario with the transfer in place but any contingency removed (i.e. base case state at the critical transfer level). If the last analyzed scenario is a reverse transfer scenario, the system state that is in place is the base case state in place when the PV analysis first starts running. The reverse transfer process always restores to the base case state upon completion.

The initial state can also be set by the **Set current state as initial** option. If this is done, choosing to restore initial state will return back to whatever the set initial state was.

Restore last solved state

When the analysis completes, the state that the case is left in is the last analyzed scenario with the transfer in place but any contingency removed (i.e. base case state at the critical transfer level). This option can be used to set the state to the last solved state. The last solved state is the base case state at the last transfer level at which it was studied and solved. This transfer level will most likely be higher than the transfer level at the last studied critical scenario. If the last analyzed scenario is a reverse transfer scenario, the last solved state is the base case state in place when the PV analysis first starts running.

The way that the process works when ramping in the positive direction is to ramp the transfer by the specified step size in the base case. The base case state at the last solved ramped amount becomes the last solved state. Then all contingency scenarios are tested. If any contingency does not solve at the present transfer level, the contingency is studied individually to determine the transfer level at which it becomes critical. This transfer level will most likely be less than the last solved state transfer level.

Added in version 20, build on Oct. 23, 2017

The caption of the option will contain the MW amount of transfer that is applied in the last solved state.

Set current state as initial

Choose this option to set the initial state to be the current state. This might be useful if doing analysis outside of the PV tool and needing to be able to return to the present state. The **Restore initial state** option can then be used to return to the state designated as the initial state. This option might also be useful if desiring to do another analysis starting from the present state and choosing to do this by using the **Start over** option. The Start over option will restore back to the initial state before starting any analysis so it is important that the initial state be set correctly.

Keep in mind that once the **Run** button is clicked to start the analysis, whatever state is presently in place will be designated as the initial state.

Start over

This option will destroy any existing results, clear the log, clear all plots and plot controls, and restore the system state to the initial state. See comments in the **Restore initial state** and **Set current state as initial** options for more details on the initial state.

Details about the sub-tabs at the bottom of page can be found at the following:

[Overview](#overview)

[Legacy Plots](#plot)

[Track Limits](#track-limits)

---

<a id="overview"></a>

## Overview

*Source: [`Content/MainDocumentation_HTML/PV_Results_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Results_Overview.htm)*

The Overview sub-tab is found on the [PV Results](#results) tab of the [PV Curves dialog](#dialog). This page provides a summary of all scenarios studied and their results. This table will update as the analysis progresses.

![PV Results Overview](images/PV_Results_Overview.png)

The overview is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays.

There are a number of fields that are shown by default on the display:

PV Scenario

Name of the scenario. Either *Base Case* or the contingency name.

Critical

*YES* if the scenario is considered to be critical. Otherwise, *NO*.

Critical Reason

This will be blank as long as the scenario is not critical. If the scenario is critical, there are a number of reasons that could be displayed explaining why the scenario is critical:

**Reached Nose** - The power flow failed to solve so the system is considered to be at the nose of the PV curve.

**Aborted Contingency** - The power flow failed to solve because an [Abort contingency action](24-contingency-element-dialog.md#type-abort) was implemented. This indicates that the contingency is simply being skipped at this transfer level without actually trying to solve the power flow.

**Inadequate Voltage** - The process stopped because at least one voltage is considered inadequate. This reason will only occur when using the option specified on the [Limit Violations](#limit-violations) tab to **Stop when voltages become inadequate**. The message will be appended with the bus and voltage of the bus with the lowest inadequate voltage.

**Inadequate High Voltage** - The process stopped because at least one voltage is considered inadequate because it is higher than the high inadequate voltage threshold. This reason will only occur when using the option specified on the [Limit Violations](#limit-violations) tab to **Stop when voltages become inadequate**. The message will be appended with the bus and voltage of the bus with the highest inadequate voltage.

**Source Maxed** - The source no longer has enough resources to continue the power transfer. Source resources are affected by the options **Enforce unit MW limits** and **Do not allow negative loads** found on the [Injection Group Ramping Options](#injection-group-ramping-options) sub-tab of the Setup tab. They could also be affected if choosing to use merit order dispatch in which unit limits are always enforced.

**Sink Maxed** - The sink no longer has enough resources to continue the power transfer. Sink resources are affected by the options **Enforce unit MW limits** and **Do not allow negative loads** found on the [Injection Group Ramping Options](#injection-group-ramping-options) sub-tab of the Setup tab. They could also be affected if choosing to use merit order dispatch in which unit limits are always enforced.

**SRT** - Indicates that a solvable reverse transfer has been found when choosing to use the reverse transfer option found on the [Advanced Options](#advanced-options) sub-tab of the Setup tab. This message is appended with the original critical reason that required the use of the reverse transfer.

**RT Source Maxed** - Indicates that the source no longer has enough resources to continue the power transfer when using the reverse transfer option found on the [Advanced Options](#advanced-options) sub-tab of the Setup tab. This message is appended with the original critical reason that required the use of the reverse transfer.

**RT Sink Maxed** - Indicates that the sink no longer has enough resources to continue the power transfer when using the reverse transfer option found on the Advanced Options sub-tab of the Setup tab. This message is appended with the original critical reason that required the use of the reverse transfer.

**Reached Nose in Base Case** - This message will only occur for a contingency scenario. It indicates that the contingency scenario is actually less limiting than the base case scenario and that the analysis of the contingency scenario cannot continue because of the base case limitation. The power transfer is always ramped in the base case prior to implementing the contingency. The contingency cannot be attempted unless the base case solves with the transfer implemented.

**Negative dV/dQ** - Indicates that a critical scenario was encountered due a bus dV/dQ sensitivity being negative. The bus with the most negative dV/dQ sensitivity will be reported.

**OPF Cannot be Solved** - This indicates that the OPF cannot be solved and will be followed by a message indicating why the OPF cannot be solved. This will most likely be because the power flow could not be solved, i.e. the same as **Reached Nose**. This is reported when using the Interface MW Flow Ramping Method.

**Interface ... Unenforceable**- This will contain the name of the interface that cannot be enforced to its specified limit. This is reported when using the Interface MW Flow Ramping Method.

**Maximum Transfer**- Indicates that a critical scenario was encountered because the **Stop when transfer exceeds** transfer level is met. Added in version 20, build on January 30, 2018

**Branch Violation** - At least one branch exceeded a limit when choosing to treat branch violations as critical scenarios. The loading percent and branch at which the largest violation occurred will be reported.

**Interface Violation** - At least one interface exceeded a limit when choosing to treat interface violations as critical scenarios. The loading percent and interface at which the largest violation occurred will be reported.

Max Shift

This value will only be filled in for critical scenarios. This is the nominal shift that was implemented to reach the critical scenario. The nominal shift is the actual accumulated transfer that was attempted.

Note: With a few exceptions, shift values (includes Max Shift, Max Export, and Max Import) that are reported are from the last solved solution before the critical point was reached. Because the critical point is not considered a valid solution, no valid shift can be determined at this point. Therefore, the values that are reported are as close to this point as the process can get within the tolerances specified for the transfer step size. Exceptions to this occur when using the reverse transfer option. In this case, the values that are reported are for the minimum transfer level at which the contingency will solve and all voltages are adequate. Another exception occurs when a scenario becomes critical because of inadequate voltages at the zero transfer level. Because the scenario can be solved at this point, the shift values will be recorded at the actual step at which the voltages are inadequate. If a case becomes critical due to inadequate voltages and is not at the zero transfer level, the shift values reported for these will follow the rule that they come from the last solved step at which all voltages were adequate. The recording of values determined by [Quantities to Track](#pvqv-quantities-to-track) will also follow these same rules.

If a scenario is critical because either the source or sink does not have enough resources to continue the power transfer, the shift values and tracked quantities that are reported are at the maximum transfer level that can be achieved without source and sink limits being violated.

When using the [Interface MW Flow Ramping Method](#interface-ramping-options), this value is the maximum nominal shift along the search path.

Max Export

This value will only be filled in for critical scenarios. This is the amount that the injection changed in the source injection group due to the transfer and contingency implementation. This value's magnitude can differ from the Max Shift value due to injection changes resulting from make-up power requirements from the contingency.

See note with Max Shift for additional explanation on how shift values are recorded.

This value is only used with the Injection Group Ramping Method.

Max Import

This value will only be filled in for critical scenarios. This is the amount that the injection changes in the sink injection group due to the transfer, loss changes due to the transfer, and contingency implementation. This value's magnitude can differ from the Max Shift value due to the injection changes resulting from make-up power requirements from the contingency and making up for losses due to the transfer. The sink injection group is designated to account for all losses due to the transfer.

See note with Max Shift for additional explanation on how shift values are recorded.

This value is only used with the Injection Group Ramping Method.

Interface X MW Flow, Interface Y MW Flow, and Interface Z MW Flow

These values are reported when using the Interface MW Flow Ramping Method. These are the actual flows on the respective interface at Max Shift.

\#Viol, Worst V Viol, Worst V Bus

These fields will be filled when choosing to monitor low or high voltage violations and there are violations for a given scenario. The options to monitor voltage violations are found on the [Limit violations](#limit-violations) tab. These fields give the total number of all bus violations for a scenario, the voltage of the worst violation, and the bus at which the worst violation occurs, respectively. The worst violation is considered to be the one with the lowest voltage.

Max P Mism Bus \#, Max P Mism Bus Name, Max MW Mism

These fields will only be filled in for critical scenarios. These give the bus number, bus name, and real power mismatch for the bus with the maximum real power mismatch for the power flow solution at which the scenario becomes critical. For scenarios that are at the nose of the PV curve, the mismatch should reflect the fact that the power flow solution will not converge and might give some insight into problem areas of the system.

Max Q Mism Bus \#, Max Q Mism Bus Name, Max Mvar Mism

These fields will only be filled in for critical scenarios. These give the bus number, bus name, and reactive power mismatch for the bus with the maximum reactive power mismatch for the power flow solution at which the scenario becomes critical. For scenarios that are at the nose of the PV curve, the mismatch should reflect the fact that the power flow solution will not converge and might give some insight into problem areas of the system.

The right-click local menu has several options specific to PV results:

Show Dialog

Choosing this option will open the [Contingency Definition dialog](22-contingency-analysis-options.md#contingency-definition-dialog) for the associated scenario's contingency. This dialog can be used to examine the contingency and make any necessary changes.

PV Curve records

There are several PV tool specific options available under this menu item:

Show Violations

This option is available when choosing to monitor low or high voltage violations and there are violations for a given scenario. When monitoring voltage violations, any bus voltages that violate limits will be stored for each scenario at the last studied transfer level. For a given scenario this option will display a table of buses that have voltage violations.

Show Inadequate Voltages

This option is available when choosing to store inadequate low voltages and there are inadequate low voltages for a given scenario. This option will open a table listing any bus that has an inadequate voltage for any transfer level for the given scenario and the voltage for each listed bus at each studied transfer level. If a bus voltage is blank, that means the voltage at that bus was not inadequate for that transfer level.

Show Inadequate High Voltages

This option is available when choosing to store inadequate high voltages and there are inadequate high voltages for a given scenario. This option will open a table listing any bus that has an inadequate high voltage for any transfer level for the given scenario and the voltage for each listed bus at each studied transfer level. If a bus voltage is blank, that means the voltage at that bus was not inadequate for that transfer level.

Show Branch Violations

This option is available when choosing to log branch violations. For a given scenario, this will open a table listing each branch that is a violation at each studied transfer level.

Show Interface Violations

This option is available when choosing to log interface violations. For a given scenario, this will open a table listing each interface that is a violation at each studied transfer level.

Calculated Fields

[Calculated fields](04-model-explorer-and-case-information-part1.md#calculated-fields) are available for use with the PV results. The object type that is used for the PV results is **PV Curve**. This type of calculated field can only be used with PV results. Calculated fields are useful when doing advanced filtering that might involve returning, for example, only the scenario with the lowest inadequate voltage at the lowest inadequate transfer level. Calculated fields are needed to return the lowest inadequate transfer level and then the lowest inadequate voltage that occurs at a transfer level less than or equal to the lowest inadequate transfer level. This type of filtering is needed because it would be possible for inadequate voltages to occur for different scenarios at the same transfer level. The most critical would then be interpreted as the scenario that produces the lowest inadequate voltage.

---

<a id="plot"></a>

## Plot

*Source: [`Content/MainDocumentation_HTML/PV_Results_Plot.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Results_Plot.htm)*

Plotting functionality is almost identical for both the PV analysis and QV analysis (exceptions will be noted below). For PV analysis, the Plot tab is accessed from the [PV Results](#results) tab of the [PV Curves dialog](#dialog). For QV analysis, the Plots tab is accessed from the [QV Results](#results-1) tab of the [QV Curves dialog](#dialog-1). Any of the values selected to be [monitored](#pvqv-quantities-to-track) can be plotted using this display.

![PV Results Plot](images/PV_Results_Plot.gif)

The page is broken into two basic sections: the left and right half. The right half of the display allows selection of the scenarios that should be included on a given plot. The left half allows selection of the quantities that will be charted on the plot.

Selecting Scenarios to Plot

The right half of the display gives a table of all scenarios that were studied. Change the **Plot?** field to *YES* to include a scenario in the current plot. The Plot? field is a toggleable field and can be changed from *YES* to *NO* and back again by double-clicking on the appropriate entry. Any scenario whose Plot? field is set to *YES* will be included on the same plot once the **Plot** button is clicked.

The **Always include base case** box should be checked if the base case scenario should be included in the plot along with any other scenarios selected. This option is not available for QV results plotting.

Before a plot can be created, the quantities to plot must also be set. The results for each selected element will be plotted for each of the selected scenarios.

Selecting Quantities to Plot

The left half of the display gives the various options for selecting what quantities should be plotted.

The **Horizontal axis value** drop-down contains any parameters that were monitored. Additionally, for the PV analysis, this drop-down also contains the independent quantities (Nominal Shift, Export, and Import) recorded during the analysis. If the **Pre-contingency** box is checked, the x values for each plotted scenario will come from the base case instead of the results of a given scenario. The Pre-contingency check box is not available for QV results plotting.

The **Vertical axis value type** drop-down contains a list of all the types of values that were monitored. The type selected in this drop-down will determine the actual elements that are listed in the **Plot values for these elements** table. To include an element in the plot, change the **Plot?** field to *YES* for that element. The Plot? field is a toggleable field and can be changed from *YES* to *NO* and back again by double-clicking on the appropriate entry. Any element whose Plot? field is set to *YES* will be included in the same plot once the **Plot** button is clicked.

Before a plot can be created, the scenarios to plot must also be set. The results for each selected element will be plotted for each of the selected scenarios.

Plot Title

Optional field that can be set to add a title to a plot and distinguish one plot from another.

Plot

After selecting the scenarios and values to plot, click this button to actually generate the plot. The plot will appear in its own window. The number of plots that can be created is limited only by computer system memory.

Right-clicking on a plot will expose a local menu with several options. The plot can be saved as a bitmap, Windows metafile, JPEF, or text file by clicking **Save** and selecting the appropriate file type. **Copy** will allow the plot to be copied and pasted into other applications. **Print** will send the plot to a printer that can be configured by selecting the **Printer Setup** option. Selecting **Close** will close the plot window.

Clear

Click this button to reset all of the **Plot?** fields to *NO* for both the scenarios to plot and the values to plot.

---

<a id="track-limits"></a>

## Track Limits

*Source: [`Content/MainDocumentation_HTML/PV_Results_Track_Limits.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_Results_Track_Limits.htm)*

The Track Limits sub-tab is found on the [PV Results](#results) tab of the [PV Curves dialog](#dialog). This page provides access to the results of [tracking devices at limits](#pvqv-quantities-to-track) that are determined during the PV analysis.

![PV Results Track Limits](images/PV_Results_Track_Limits.gif)

The page is divided into several additional sub-tabs for the different types of devices that can be tracked. Tables on each tab are similar in that they list all of the devices of that type that were tracked. For PV analysis, each column of the table is the transfer amount at which the device limits were checked. For PV analysis, device limits are only checked for base case conditions (i.e. no contingencies are applied). The results show where each element was located relative to its min/max limits during each step of the analysis using the indicators of *Within Limits*, *Within* *Range*, *At* *Max***,** and *At Min*. To simplify the display and exclude those elements that were always within their limits during all steps of the process, check the box **Filter out devices that never hit or backoff a limit during the PV run**.

---

<a id="qv-curves"></a>

## QV Curves

*Source: [`Content/MainDocumentation_HTML/QV_Curves.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curves.htm)*

The QV Curves tool provides the ability to compute QV curves for any bus in the system. A QV analysis studies how variations in reactive power (Q) injection at a bus affects the voltage (V) at that same bus. Other system parameters can also be monitored as the reactive power injection changes.

To create a QV curve, a fictitious generator (synchronous condenser) is placed at a bus that is being studied. The voltage set-point of this generator is varied and its var output is allowed to be any valued needed to meet this voltage set-point. The vertical axis (y-axis) of a QV curve depicts the output of the fictitious generator in Mvar. The horizontal (x-axis) depicts the respective voltage under this condition. The base case operating point of the system is represented by the x-intercept of the curve. This is the point where the fictitious generator is at 0 Mvar output and represents the base case. There are situations in which the output of the fictitious generator is not 0 Mvar in the base case, but these will be explained with the appropriate option settings. **When considering a contingency scenario in the QV analysis, the term** *base case operating point* **will also be used. This is the starting case that represents the system prior to performing any analysis for the curve tracing.**

Tracing down the curve from higher to lower voltage set-points represents a decrease in the fictitious generator's Mvar output which is representative of an increase in Mvar load. The curve is then tracing what the voltage would be as the Mvar load increases. At some point the Mvar value of the generator will stop decreasing and the bottom of the curve will be reached. This point represents the maximum increase in load Mvar that can occur at this bus before voltage collapse is reached.

The following shows a typical QV curve. The plot is actually a VQ curve, but this is traditionally called the QV curve.

![QV Curves 614x357](images/QV_Curves_614x357.jpg)

The following plot shows a situation in which there is not enough Mvar reserve. There is no base case operating point as the curve never crosses the x-axis. The difference between the bottom of the curve and the x-axis is the amount of Mvar injection needed to achieve a solvable case and to come out of collapse.

![QV Curves Mvar Deficiency 628x367](images/QV_Curves_Mvar_Deficiency_628x367.jpg)

To use the QV Curves tool, select **QV Curves** on the **PV and QV Curves (PVQV)** ribbon group on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab. The [QV Curves dialog](#dialog-1) will open from which buses to be monitored can be specified, options for the QV curves can be set, and the QV curve analysis can be run.

---

<a id="dialog-1"></a>

## Dialog

*Source: [`Content/MainDocumentation_HTML/QV_Curves_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curves_Dialog.htm)*

To display this dialog, go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **QV Curves** from the **PV and QV Curves (PVQV)** ribbon group.

The QV Curves dialog contains all of the setup and controls for processing and analyzing the QV curve analysis. The dialog is broken down into several pages:

[Buses](#buses)

[Quantities to Track](#pvqv-quantities-to-track)

[Options](#options)

[Results](#results-1)

There is a section at the top of the dialog containing several buttons that will be displayed regardless of the page that is selected.

![QV Curves Dialog Run](images/QV_Curves_Dialog_Run.png)

Run

When all options have been set, click **Run** to start the QV analysis. The progress of the analysis can be monitored from the **Results** tab. While the analysis is in progress, the Run button will become a **Stop** button that can be clicked to stop the analysis.

When running the QV analysis, the first step is to make sure that the base case is solvable. If it is not solvable, a message will prompt the user to decide if a solvability analysis be done of the base case. A solvability analysis on the base case will process each of the buses selected for analysis. As each bus is processed, the fake generator (synchronous condenser) that is normally added to trace the QV curve at a bus will first be used to determine if Mvar injection/absorption can be adjusted such that a solvable point is found. This process can be quite time consuming. The process first tries to find a solvable point by increasing the studied setpoint voltage and tracing up the curve up to the maximum voltage. It is more likely that a solvable point will be found tracing up the curve due to the increased Mvar injection required to meet the setpoint voltage. If a solvable point is found, this solvable point with the fake generator injection/absorption in place will then be the starting point for the QV curve tracing. Because the base case is not solvable, no attempt will be made at solving any contingency scenarios. If the base case is not solvable and the solvability analysis is not done, the QV process will stop.

Load

Clicking this button will open a dialog to allow the user to select an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) to load. This is intended to be used for loading any relevant option settings to be used during the QV analysis. The dialog will be updated according to the option settings loaded from the file.

Save

Clicking this button will prompt for a filename in which to save an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux). Use this auxiliary file to store any results and settings that need to be retained for future use.

Added in version 23QV options are stored with PWB files, and results can optionally be stored.

The **QV Curve Tool Settings** dialog shown below will be displayed with options for specific data to include in the auxiliary file. Check the box next to a particular data set to save this data in the auxiliary file. Which key field to use when identifying objects in the file can also be specified on this dialog. Click **OK** on this dialog to finalize saving the file or close the dialog to abandon the file save.

![QV Curve Tool Settings Dialog](images/QV_Curve_Tool_Settings_Dialog.png)

Delete All Results

All results are deleted including the QV curves and tracked quantities.

Help

Displays the help topic for the currently selected tab.

---

<a id="buses"></a>

## Buses

*Source: [`Content/MainDocumentation_HTML/QV_Curve_Buses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curve_Buses.htm)*

The Buses page is found on the [QV Curves dialog](#dialog-1).

![QV Curves Dialog Buses](images/QV_Curves_Dialog_Buses.png)

The Buses page is used to designate the buses at which QV curves should be calculated. Depending on other options that are selected, a QV curve will be determined for each selected bus for the base case and any selected contingencies. Each bus/contingency (or base case) pair comprise a QV scenario.

By default, the table lists all buses in the case. This table is a bus case information display and [filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) can be applied to this table to make the selection of buses easier. Several QV-specific fields are listed by default:

QV Selected

Set this field to *YES* to calculate a QV curve for this bus. This field can be toggled between *YES* and *NO* by double-clicking on the appropriate entry.

Min Volt

Specify the minimum voltage at which the analysis will be performed for this particular bus. If this is not specified, the default minimum voltage set with the default [options](#solution) is used. Only non-default values will be shown. If the value is changed to the default setting, the cell will be set blank.

Max Volt

Specify the maximum voltage at which the analysis will be performed for this particular bus. If this is not specified, the default maximum voltage set with the default [options](#solution) is used. Only non-default values will be shown. If the value is changed to the default setting, the cell will be set blank.

Step Size

Increment between voltage set-points used to trace the curve for this particular bus. If this is not specified, the default step size set with the default [options](#solution) is used. Only non-default values will be shown. If the value is changed to the default setting, the cell will be set blank.

Modify Selected Buses to Select Only Singe Bus Per Super Bus

This button will only be visible if the [Integrated Topology Processing](35-integrated-topology-processing.md#topology-processing-overview) add-on is available. When using topology processing, only a single bus per super bus will be in the consolidated case. That means that the parameters for each bus in the super bus will be the same, i.e. same voltage magnitude and angle, etc. This button can be used to eliminate any excess QV curves that would just take up computer memory by drawing the same curve multiple times for the same super bus. To take advantage of this option and only select a single bus per super bus, first set up the bus selection to monitor all of the necessary buses and then push the **Modify...** button. The QV Selected field in the table will then be updated to only include a single bus per super bus. When determining the primary node (the primary node is the bus that will ultimately be the one monitored during the analysis) and super buses, the active defined contingencies will be used to determine how the case is consolidated. Because the consolidation can be different based on the contingency set, or lack thereof, it is best to just define the selected buses to include all necessary buses and use this option to refine the list down to a single bus per super bus rather than manually trying to maintain such a list.

Buses can also be explicitly selected for analysis by using several options found at the bottom of the dialog. **A range of bus numbers or the name of a bus** can be specified in the appropriate boxes. Clicking the **Add** button for either entry will set the **QV Selected** field to *YES* for the designated buses. These options are used to make setting the **QV Selected** field more convenient.

Automatically Identify Buses

Check this box to analyze additional buses based on selected conditions. Set the number of **Lowest-voltage Buses** and/or **Highest dv/dq Buses** for buses at which curves should be calculated. The dv/dq sensitivity is the sensitivity of voltage at a bus to an injection of reactive power at the same bus. The sensitivities are ranked based on their magnitude. These lowest-voltage buses and highest dv/dq buses are determined for each scenario once any contingency has been applied. Use the **Limit Group** drop-down to specify which buses should be considered when evaluating these conditions. Only buses that are assigned to the selected [limit group](18-general-tools.md#limit-monitoring-settings) will be considered, and buses that have generators on AVR control will also not be considered.

If the buses identified when evaluating these conditions already have been selected by the user, no additional buses will be selected to make sure that the number of additional buses to include is achieved by buses that have not been user selected.

---

<a id="options"></a>

## Options

*Source: [`Content/MainDocumentation_HTML/QV_Curve_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curve_Options.htm)*

The Options tab is found on the [QV Curves dialog](#dialog-1). The Options page contains several additional sub-tabs from which parameters necessary for carrying out a QV analysis can be set:

[Solution](#solution)

[Contingencies](#contingencies)

[Output](#output-1)

[Distributed Computing](#distributed-computing)

---

<a id="solution"></a>

## Solution

*Source: [`Content/MainDocumentation_HTML/QV_Curves_Options_Solution.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curves_Options_Solution.htm)*

These options are found on the Solution sub-tab located on the [Options](#options) page of the [QV Curves dialog](#dialog-1).

![QV Curves Options Solution](images/QV_Curves_Options_Solution.png)

Default solution parameters

Voltage step size (pu)

Increment between voltage set-points used to trace a QV curve. This is the default value that will be applied to a bus unless a bus-specific value is specified.

Minimum voltage (pu)

Minimum voltage at which the analysis will be performed. This is the default value that will be applied to a bus unless a bus-specific value is specified.

Maximum voltage (pu)

Maximum voltage at which the analysis will be performed. This is the default value that will be applied to a bus unless a bus-specific value is specified.

Use initial voltage as Vmax

Check this box to use the initial voltage at a bus as the maximum voltage at which the analysis will be performed. This option overrides any of the other options that set the maximum voltage for a bus. The initial voltage at a bus is determined prior to starting the QV analysis but after applying contingencies and applying any additional var support necessary to make an unsolvable scenario solvable.

Power flow solution options

Global solution options

Click this button to bring up the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options). This allows the specification of the solution options to use for solving pre-contingency cases and the options used when no contingency-specific solution options are defined. Changing these options affect all power flow computations, even those outside the QV process.

The global solution options will be used in the QV analysis unless QV-specific solution options are defined using the option described below. If contingency-specific solution options are defined for a contingency, those options will override both the QV-specific solution options and the global solution options.

QV Power Flow Solution Options

Click this button to bring up a dialog that allows specification of QV-specific power flow solution options. These are the same options that are described in the Simulator Options Dialog for [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options). The order in which QV-specific solution options are applied relative to the contingency solution options is controlled by the next option.

The option to *Dynamically Add/Remove Slack Buses as Topology is Changed (Allow Multiple Islands)* is handled in a special manner when applying these options. This option cannot be set to allow multiple islands if it has previously been set to not allow multiple islands. This will be enforced when these options are applied.

When to apply QV Power Flow Solution Options (Added in Version 21, build on January 29, 2021)

The sequence of when to apply the QV Curve power flow solution options is determined by this option. It may be set to either be applied **Before** or **After** the contingency (or base case) power flow solutions. Prior to the Version 21, build on January 29, 2021, this option was not available and the QV curve was always processed as though the option was set to **Before**. If the value is set to **Before**, then the QV curve options are applied before the contingency solution, and as a result any contingency solution options will override any QV curve options. If the value is set to **After**, then the QV curve options are applied after the contingency power flow solution and thus the QV options will override any contingency solution options.

The overall process for a particular contingency (or base case) is as follows:

> 1.  Start with the Global Power Flow Solutions options
> 
> 2.  If **When to Apply** = **Before**, then apply the QV Curve Power Flow Solution Options
> 
> 3.  Apply the Contingency Power Flow Solution Options (not for the base case)
> 
> 4.  Solve the power flow for the contingency (or base case)
> 
> 5.  If **When to Apply** = **After**, then apply the QV Curve Power Flow Solution Options
> 
> 6.  Trace the QV curve by varying the voltage setpoint as desribed in the help topic [QV Curves](#qv-curves)

Because the goal is to stress the system while performing the QV analysis, there are two power flow solution options that are set internally as part of the QV process. These are the options that specify the minimum per unit voltage for constant power and constant current loads. These options are both set to 0 pu and override any user-specified settings.

![PV Setup Common Options Min PU Volt](images/PV_Setup_Common_Options_Min_PU_Volt.jpg)

These options are both set to 0 pu during both the base case solution and any contingency case solution.

---

<a id="contingencies"></a>

## Contingencies

*Source: [`Content/MainDocumentation_HTML/QV_Curves_Options_Contingencies.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curves_Options_Contingencies.htm)*

These options are found on the Contingencies sub-tab located on the [Options](#options) page of the [QV Curves dialog](#dialog-1).

![QV Curves Options Contingencies](images/QV_Curves_Options_Contingencies.png)

Process each of the currently defined contingencies

Check this box to have contingencies included in the QV analysis.

QV curves can be calculated for the specified buses for both base and contingency conditions. To analyze a set of contingencies, these must be defined using the separate [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). Any contingency whose **Skip** field is set to *NO* will then be included in the QV analysis.

Another option that is relevant to the QV analysis that must be set for a contingency on the contingency analysis dialog is the **QV Autoplot** field. This field must be set to *YES* in order to have a QV curve plotted automatically for a contingency scenario. More information about the option to plot curves automatically is found on the [Output](#output-1) sub-tab. There is no requirement to have a plot made automatically during the run; this can always be done after the analysis is complete.

Note: The Robust Solution Process option that can be utilized with the contingency analysis when a contingency solution failure occurs is not applied when a contingency is implemented during the QV analysis. All other options defined with contingency analysis such as contingency-specific solution options and make-up power specifications are used when applying a contingency during the QV analysis.

Skip base case

Check this box to prevent the computation of QV curves for base case conditions.

Attempt to make unsolvable contingencies solvable with synchronous condenser

Some contingencies may not solve when implemented. If this box is checked, an attempt will be made to make an unsolvable contingency solvable by providing additional var injection/absorption through use of a fictitious generator (synchronous condenser). As each selected bus is processed, the fake generator (synchronous condenser) that is normally added to trace the QV curve at a bus, will first be used to determine if Mvar injection/absorption can be adjusted such that a solvable point is found. This process can be quite time consuming. The process first tries to find a solvable point by increasing the studied setpoint voltage and tracing up the curve up to the maximum voltage. It is more likely that a solvable point will be found tracing up the curve due to the increased Mvar injection required to meet the setpoint voltage. If a solvable point is found, this solvable point with the fake generator injection/absorption in place will then be the starting point for the QV curve tracing.

The **Q0** results field found on the [Listing](#listing) sub-tab of the [Results](#results-1) tab indicates the injection of the fake generator at the base case or initial contingency solution point. This field being non-zero is indicative of an unsolvable contingency with the value of the field being the Mvar injection required to solve the contingency.

Finding a solvable point can be time consuming if there are a number of contingencies that do not solve and a large number of buses are selected for analysis. Uncheck this box if long solution times become an issue.

It is possible that the base case does not solve. If this option is checked and not skipping the base case, there will be a prompt when running from the GUI asking if the base case should be made solvable. If running from script there is a parameter with the script command indicating if the base case should be made solvable. If the base case should be made solvable, an attempt will be made by using each selected bus as described in the process to make contingency scenarios solvable.

---

<a id="output-1"></a>

## Output

*Source: [`Content/MainDocumentation_HTML/QV_Curves_Options_Output.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curves_Options_Output.htm)*

These options are found on the Output sub-tab located on the [Options](#options) page of the [QV Curves dialog](#dialog-1).

![QV Curves Options Output](images/QV_Curves_Options_Output.png)

Save Results in PWB File

Added in version 23QV results can optionally be stored in PWB files by checking this box; options are always stored.

Save QV Curve Results to File

Check this box to save a comma-delimited file format for QV results. This format can easily be imported into a spreadsheet. This file format cannot be loaded back into Simulator.

The comma-delimited file is grouped into sections for each scenario. Each scenario is identified by a header than indicates the bus and either base case or contingency identifier. The header is followed by a line that provides the field order of the actual data. The field line is followed by lines of data. Each scenario grouping is separated by a blank line. All results are sorted by the voltage setpoint.

The fields have the following meaning:

**V(PU)** - per-unit voltage set-point

**Q\_sync(MVR)** - output of the fake generator (synchronous condenser)

**Q\_shunt(MVR)** - sum of bus shunt, on-line switched shunt, and on-line generator Mvar (excluding the fake generator)

**Q\_tot(MVR)** - Q\_sync + Q\_shunt

**Q\_res(MVR)** - available reserve at the bus

**Q\_tot\_res(MVR)** - Q\_sync + Q\_shunt + Q\_res

Here is an example of the comma-delimited file:

\*\*BUS\*\* 3 (Three\_138.0),\*\*CASE\*\* L\_000001ONE-000003THREEC1

V(PU), Q\_sync(MVR), Q\_shunt(MVR), Q\_tot(MVR), Q\_res(MVR), Q\_tot\_res(MVR)

1.1000, 437.5849, 48.4000, 485.9849, 242.0000, 727.9849

1.0962, 419.8296, 48.0627, 467.8923, 240.3136, 708.2059

1.0862, 374.1186, 47.1898, 421.3083, 235.9489, 657.2572

1.0762, 329.2408, 46.3248, 375.5656, 231.6243, 607.1899

1.0662, 285.1944, 45.4679, 330.6623, 227.3396, 558.0020

1.0562, 241.9775, 44.6190, 286.5965, 223.0950, 509.6915

1.0462, 199.5884, 43.7781, 243.3665, 218.8904, 462.2568

1.0362, 158.0253, 42.9451, 200.9705, 214.7257, 415.6962

1.0262, 117.2866, 42.1202, 159.4069, 210.6011, 370.0079

1.0162, 77.3706, 41.3033, 118.6739, 206.5164, 325.1904

1.0062, 38.2757, 40.4944, 78.7701, 202.4718, 281.2419

0.9962, 0.0000, 39.6934, 39.6934, 198.4671, 238.1605

0.9962, 0.0000, 39.6934, 39.6934, 0.0000, 39.6934

0.9962, 0.0000, 39.6934, 39.6934, -119.0803, -79.3869

0.9862, -37.4572, 38.9005, 1.4433, -116.7015, -115.2582

0.9762, -74.0981, 38.1156, -35.9825, -114.3467, -150.3292

0.9662, -109.9612, 37.3386, -72.6225, -112.0160, -184.6385

0.9562, -144.9682, 36.5697, -108.3985, -109.7092, -218.1077

0.9462, -179.1652, 35.8088, -143.3564, -107.4264, -250.7828

0.9362, -212.5517, 35.0559, -177.4958, -105.1676, -282.6635

To save data in the auxiliary file format that can be loaded back into Simulator, use the Save button found at the top of the QV Curves dialog. The values saved to the comma-delimited file are the same values that are saved in the SUBDATA section for QVCurve data saved to an auxiliary file.

Save results in file

Specify the name and file path of the file to which to save the results. This option will be enabled when the **Save Results to File** option is checked. Click the **Browse** button to open a dialog that will allow selection of the file path and name.

Save Quantities to Track to File

Check this box to save the [Quantities to track](#pvqv-quantities-to-track) to file. By default this file will be named *ExtraMonitoring.csv* and will be stored in the current directory. If a filename is specified in the **Save result in file** box, the extra monitoring file will be named using the filename specified with *\_ExtraMonitoring* appended to the filename. The file extension will be the same as that specified with the filename. Regardless of the specified file extension, this file will be a comma-delimited text file.

The results for the tracked quantities will also be stored in an auxiliary file if choosing to store the QV results to auxiliary file. The extra monitoring file is not meant to replace this but to simply provide a format that is easy to load into Excel for analysis outside of Simulator. If a file in this format is needed after the analysis is complete, the **Save Quantities to Track (After Run Completion)** button can be clicked to save this file.

Plot curves as they are computed

Check this box to draw and update QV curve plots during each step of the QV analysis process. In order to have QV curves automatically plotted for a contingency during each step of the analysis, the **QV Autoplot** field belonging to that contingency must be set to *YES* on the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog).

If curves are not plotted at they are computed, they can be easily created upon completion of the analysis from an option found on the [Listing](#listing) sub-tab on the [Results](#results-1) tab.

When plotting V versus Q, treat Q as...

There are several options that determine how the Q quantity should be plotted on a QV curve. These options are applicable whether plotting the curves automatically as they are computed or plotting the curves upon completion of the analysis.

An example plot is shown below with examples of the plots that result from the four possible options for how to treat Q.

The output of the fictitious synchronous condenser (Qsync)

Select this option to treat Q as the output of the fake generator (synchronous condenser) only. This is the Q\_sync(MVR) curve shown in the example plot below.

The total reactive injection at the bus, including shunts but excluding load

Select this option to treat Q as the sum of the output of the fake generator (synchronous condenser), any on-line shunts, and any on-line Mvar generation other than the fake generator. Shunts include both bus shunts and switched shunts. This is the Q\_tot(MVR) curve shown in the example plot below.

Include reserves (status = closed, generators on AVR, switched shunts not fixed)

Check this box to offset the Q values by the appropriate Mvar reserves values.

When the QV curve is traced for a given bus, any existing switched shunts on control at that bus are turned off control and any existing generators on AVR control at that bus are turned off control. The amount of Mvar support that these devices can provide is then recorded and determined at each voltage set-point. These are the reserves values. Only devices that are on-line and on control will be included. This means that for a generator the AVR status = *YES* and for a switched shunt the control mode must not be *Fixed*.

The amount of down (decrease) reserves at a given voltage set-point for a switched shunt is determined by the difference between the current nominal output of the shunt and its minimum nominal output multiplied by the square of the voltage set-point: (Nominal Mvar - Min Nominal Mvar)\*V<sup>2</sup>. The amount of down (decrease) reserves for a generator at a given voltage set-point is the difference between the current output and the minimum Mvar output: (Mvar Output - Min Mvars). The amount of up (increase) reserves at a given voltage set-point for a switched shunt is determined by the difference between the maximum nominal output of the shunt and its current nominal output multiplied by the square of the voltage set-point: (Max Nominal Mvar - Nominal Mvar)\*V<sup>2</sup>. The amount of up (increase) reserves for a generator at a given voltage set-point is the difference between the maximum Mvar output and the current output: (Max Mvars - Mvar Output). The total reserves of each type at any voltage set-point is the sum of reserves of that type for all qualifying switched shunts and generators at the studied bus.

Which type (up or down) of reserves to consider at a particular voltage set-point is determined based on the location of the voltage set-point relative to the base case operating voltage. When considering contingencies, the base case operating voltage is the voltage at a bus following implementation of the contingency but before any QV curve tracing is started. If the voltage set-point is less than the base case operating voltage, the up reserves are considered. This part of the curve represents an increase in the Mvar load at a bus. The difference in the bottom of the curve and the x-axis is the amount that the Mvar load at a bus can be increased before voltage collapse. Being able to inject additional Mvar through available reserves will further increase this margin. When plotting including reserves, the portion of the curve to the left of the base case operating point is then offset downward by the amount of up reserves that are available at each voltage set-point, thus increasing the margin before collapse. The portion of the curve to the right of the base case operating point is then offset upward based on the amount of down reserves available at each voltage set-point.

Instead of listing an absolute value of reserves available, the Q\_res(MVR) value as reported with the QV output results (either comma-delimited file or auxiliary file) is reflective of the offset required when plotting the curve including the reserves.

When choosing to include reserves, the values that are plotted are either Q\_sync\_res(MVR) or Q\_tot\_res(MVR). The Q\_sync\_res(MVR) value is not included in the QV output results (either comma-delimited file or auxiliary file) but is equal to the sum of Q\_sync(MVR) and Q\_res(MVR): Q\_sync\_res(MVR) = Q\_sync(MVR) + Q\_res(MVR). Q\_sync\_res(MVR) represents the combination of selecting the option to plot **The output of the synchronous condenser** and including reserves. Q\_tot\_res(MVR) represents the combination of selecting the option to plot **The total reactive injection at the bus...** and including reserves.

![QV Curves Results Plot 662x491](images/QV_Curves_Results_Plot_662x491.jpg)

Note: The reserves and the existing injection in the above plot are represented solely by switched shunts. All of the curves tend to converge toward the same Q at lower voltages. This is because of the relationship of the actual output of a switched shunt to the nominal output: (Actual Mvar) = (Nominal Mvar)\*V2.

---

<a id="distributed-computing"></a>

## Distributed Computing

*Source: [`Content/MainDocumentation_HTML/QV_Curve_Distributed_Computing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curve_Distributed_Computing.htm)*

Added in version 24

**The Distributed QV Curves tool is available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)for more details.****

These options are all available on the [QV Curves dialog](#dialog-1) on the [Options page](#options) under the Distributed Computing grouping.

Distributed Computing is available for use in distributing groups of buses and contingencies that combine to form the QV result scenarios. In order to use distributed computing you must first configure a list of remote computers which can be utilized along with appropriate authentication information for those computers. The computer list and authentication information is common to all the distributed computing tools in Simulator and can be found in the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), or reached with the Distributed Computing Options button. They are described in [Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)[ ](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons).

The options to specify to QV Curves analysis for Distributed Computing are the following:

Use Distributed Computing

Check this box to signify that when processing QV scenarios distributed computing should be used.

Number of Buses or Contingencies per Process

QV scenarios are a combination of contingency and analyzed bus. This values specifies the *ChunkSize* used when determining how to define scenarios for the distributed processes. To analyze a single bus there are far more power flow solutions than the single power flow solution required for a single contingency. It makes sense to first consider the number of buses to process when determining how to split the scenarios over distributed computing processes, but if there are far more contingencies than buses it might make sense to split the scenarios based on contingencies. The following calculations determine how scenarios are split over distributed processes:

BusCount: Number of QVSelected = YES buses (this might be 0 if only choosing to auto identify buses)

CTGCount: If including contingencies then Number of Skip = No contingencies

CTGCount: If including base case add 1

if BusCount \>= *ChunkSize* then

NumberBusesPerProcess = *ChunkSize* (might be less than this for the last process)

NumberCTGsPerProcess = 1

TotalNumberProcesses = Ceil(BusCount/*ChunkSize*)\*CTGCount

else

if (BusCount \> 0) then

NumberBusesPerProcess = BusCount

NumberCTGsPerProcess = *ChunkSize*

TotalNumberProcesses = Ceil(*ChunkSize*/CTGCount)

else

NumberCTGsPerProcess = *ChunkSize* (might be less than this for the last process)

TotalNumberProcesses = Ceil(CTGCount/*ChunkSize*)

---

<a id="results-1"></a>

## Results

*Source: [`Content/MainDocumentation_HTML/QV_Curve_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Curve_Results.htm)*

The Results tab is found on the [QV Curves dialog](#dialog-1). This page provides access to all of the QV results. This page is divided into several additional sub-tabs from which different categories of results are available:

[Listing](#listing)

[Plots](#plot)

The Results tab also displays messages about the progress of the analysis. The messages are displayed regardless of the sub-tab that is selected.

---

<a id="listing"></a>

## Listing

*Source: [`Content/MainDocumentation_HTML/QV_Results_Listing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/QV_Results_Listing.htm)*

The Listing sub-tab is found on the [Results](#results-1) page of the [QV Curves dialog](#dialog-1). This page provides a summary of all scenarios studied and their results. This table will update as the analysis progresses.

![QV Curves Results Listing](images/QV_Curves_Results_Listing.png)

The listing is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays.

There are a number of fields that are shown by default on the display:

Number, Name, Nom kV

Number, name, and nominal kV voltage of the studied bus, respectively. This along with the Case Name identifies the scenario. A scenario is uniquely identified by key fields using the Number and Case Name.

Case Name

Either *BASECASE* or the name of a contingency.

V at Q0

Per-unit voltage in the starting case (base case operating point). The starting case is either the base case or a contingency case. This is the voltage that is recorded prior to starting any QV curve tracing. This is the voltage at **Q0**.

If the case is not solvable and a successful attempt is made at finding the solvable point by using the fake generator to provide Mvar injection, this is the voltage recorded once the case becomes solvable.

Q0

Mvar output of the fake generator in the starting case (base case operating point). The starting case is either the base case or contingency case. This is the Mvar output that is recorded prior to starting any QV curve tracing.

If the case is not solvable and a successful attempt is made at finding the solvable point by using the fake generator to provide Mvar injection, this is the Mvar output of the fake generator that is required to make the case solvable. Therefore, a non-zero entry means that the initial starting case was not solvable.

Qinj\_0

Total Mvar injection in the starting case (base case operating point). The starting case is either the base case or contingency case. This is the total injection that is recorded prior to starting any QV curve tracing. This includes the shunt injection from bus shunts and switched shunts and the output of the fake generator.

Vmax

Maximum per-unit voltage that was recorded.

Q at VMax

Mvar injection of the fake generator at the maximum per-unit voltage that was recorded, **Vmax**.

Qinj at Vmax

Total Mvar injection at the maximum per-unit voltage that was recorded, **Vmax**. This includes the shunt injection from bus shunts and switched shunts and the output of the fake generator.

V at Qmin

Per-unit voltage at the minimum recorded fake generator injection, **Qmin**.

Qmin

Minimum recorded fake generator injection. If negative, this is the amount that the Mvar load can be increased before voltage collapse. If positive, this is the amount of Mvar injection required to come out of collapse and achieve a solvable case.

Qinj\_min

Total minimum recorded Mvar injection. This includes the shunt injection from bus shunts and switched shunts and the output of the fake generator.

Vmin

Minimum per-unit voltage that was recorded.

Q at Vmin

Mvar injection of the fake generator at the minimum per-unit voltage that was recorded, **Vmin**.

Qinj at Vmin

Total Mvar injection at the minimum per-unit voltage that was recorded, **Vmin**. This includes the shunt injection from bus shunts and switched shunt and the output of the fake generator.

These fields will all contain *DIVERGED* if the contingency cannot be solved. They will contain *ABORTED* if the contingency cannot be solved because an [Abort contingency action](24-contingency-element-dialog.md#type-abort) was implemented.

The right-click local menu has one option specific to QV results:

Plot QV Curve

This will plot the QV curve for the selected scenario. What value of Q to plot is determined by the options selected for how to treat Q as found on the [Output](#output-1) sub-tab of the [Options](#options) page. If multiple scenarios are selected, the curves for the multiple scenarios will be shown on the same plot.

A special field has been added to the Listing table that is intended to make it a bit easier for ordering and selecting multiple scenarios for plotting. This field is called **User Defined Integer** and allows the user to simply order the scenarios to be plotted on the same plot. Doing a simple sort on this field will then arrange all of the scenarios so that they can easily be selected for plotting.

---

<a id="pvqv-refine-model"></a>

## PV/QV Refine Model

*Source: [`Content/MainDocumentation_HTML/PV_QV_Refine_Model.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PV_QV_Refine_Model.htm)*

Modeling idiosyncrasies may exist that cause premature loss of convergence during either a PV or QV analysis. The PVQV add-on has a tool to modify the currently open case in an attempt to fix some of these idiosyncrasies. This is the Refine Model tool that is available on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab in the **PV and QV Curves (PVQV)** ribbon group.

![PV QV Refine Model Dialog](images/PV_QV_Refine_Model_Dialog.gif)

The case can be refined with the following options:

Fix transformer taps

If there are transformers that have Vmax and Vmin that are very close together, the power flow may have a difficult time converging. This option allows the user to fix all transformer taps at their present values if their Vmax - Vmin is less than or equal to the user specified tolerance.

Fix shunts

If there are switched shunts that have Vmax and Vmin that are very close together, the power flow may have a difficult time converging. This option allows the user to fix all switched shunts at their present values if their Vmax-Vmin is less than or equal to the user specified tolerance.

Take units off AVR control

If there are generators that have Qmax and Qmin that are very close together, the power flow may have a difficult time converging. This option allows the user to remove these units from AVR control, thus locking their MVAR output at its present value, if their Qmax - Qmin is less than or equal to the user specified tolerance.

Apply to

These refinements will only be applied to those areas or zones that have the **Apply?** field set as *YES* in this dialog box. This field can be toggled between *YES* and *NO* by left-clicking on the appropriate entry.

OK

Click this button to make the selected changes to the currently open power flow case. After the changes are made the **Close** button must be clicked to close the dialog. If any changes have been made and the dialog is closed, the user will be prompted to save the case to a file.

Close

Click this button to close the dialog without implementing any changes to the power flow case in memory.
