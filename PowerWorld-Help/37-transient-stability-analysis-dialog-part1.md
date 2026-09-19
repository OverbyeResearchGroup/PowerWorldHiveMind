---
title: "Transient Stability — Analysis Dialog (Part 1 of 3)"
part: "Transient Stability"
chapter_file: "37-transient-stability-analysis-dialog-part1.md"
topics: 13
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Transient Stability — Analysis Dialog (Part 1 of 3)

The Transient Stability Analysis dialog: simulation, options, plots, results and validation.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (13)**

- [Transient Stability Analysis Dialog](#transient-stability-analysis-dialog)
- [Simulation](#simulation)
- [Transient Contigency Element Dialog](#transient-contigency-element-dialog)
- [Options](#options)
- [General](#general)
- [Power System Model](#power-system-model)
- [Remedial Actions](#remedial-actions)
- [Result Options](#result-options)
- [Generic Limit Monitors](#generic-limit-monitors)
- [Distributed Computing](#distributed-computing)
- [Results Storage](#results-storage)
- [Storage to RAM](#storage-to-ram)
- [Storage to Hard Drive](#storage-to-hard-drive)

---

<a id="transient-stability-analysis-dialog"></a>

## Transient Stability Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog.htm)*

To display this dialog, go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **Transient Stability** from the **Transient Stability (TS)** ribbon group.

All of the help documentation will discuss how this dialog functions when you are simulating only a single transient contingency event. When changing the **Process Contingencies** option to *Multiple Contingencies* instead, the dialog will change in small ways throughout. For a description of how the dialog behaves differently when running multiple contingencies, see the [Transient Stability Dialog Multiple Contingencies](37-transient-stability-analysis-dialog-part3.md#simulating-multiple-contingencies) help topic.

![Transient Stability Simulation Control](images/Transient_Stability_Simulation_Control.gif)

The dialog is broken down into several steps designed to take the user through the setup, processing, and analysis of results. The pages are as follows:

<table>
<tbody>
<tr class="odd">
<td><p><a href="#simulation">Simulation</a></p>
<p> </p></td>
<td><p>Define the transient contingency elements which describe the event to simulate. Specify start time, end time, and time step.</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p><a href="#options">Options</a></p>
<p> </p></td>
<td><p>Specify the options: <a href="#general">General</a>, <a href="#power-system-model">Power System Model</a>, <a href="#result-options">Result Options</a>, <a href="#generic-limit-monitors">Generic Limit Monitors</a> , and <a href="52-additional-linked-topics-part3.md#transient-stability-dialog-options-user-defined-models">User Defined Models</a></p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p><a href="#results-storage">Results Storage</a></p>
<p> </p></td>
<td><p>Specify what results to store during the simulation for <a href="37-transient-stability-analysis-dialog-part3.md#time-values">viewing</a>, <a href="37-transient-stability-analysis-dialog-part2.md#plots">plotting</a>, and <a href="36-transient-stability-overview-and-data-part2.md#transient-contour-toolbar">contouring</a> later. Also specify whether to <a href="#storage-to-ram">store to RAM</a>, <a href="#storage-to-hard-drive">store to Hard-Drive</a>, both, or neither (when using <a href="37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors">Transient Limit Monitors</a> appropriately, it may be unnecessary to store the actual numerical results.)</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p><a href="37-transient-stability-analysis-dialog-part2.md#plots">Plots</a></p>
<p> </p></td>
<td><p>Build plot descriptions to both view results and specify what to store to RAM</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p><a href="37-transient-stability-analysis-dialog-part2.md#result-analyzer">Result Analyzer - Damping</a></p></td>
<td><p>Define transient stability result analysis time windows. Time Windows can be used to calculate statistical information about signals (Max, Min, average, etc) or to perform model analysis to calculate modes and damping of the signals. Added in Version 22</p></td>
</tr>
<tr class="even">
<td><p><a href="37-transient-stability-analysis-dialog-part3.md#results-from-ram">Results</a></p>
<p> </p></td>
<td><p>View the numeric results of the simulation as well as a summary of events that occurred</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p><a href="37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors">Transient Limit Monitors</a></p>
<p> </p></td>
<td><p>Define transient limit monitors to look for violations of stability criteria during the simulation. For example, look for a specific drop in frequency that lasts for period of time.</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p><a href="37-transient-stability-analysis-dialog-part3.md#statesmanual-control">States/Manual Control</a></p>
<p> </p></td>
<td><p>Provides ability to manual step through the simulation a few time steps at a time. Also gives access to view the initialized stability state variables and initial state limit violations.</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p><a href="37-transient-stability-analysis-dialog-part3.md#validation">Validation</a></p>
<p> </p></td>
<td><p>Provides options to validate the stability data specified for possible errors and warning.</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p><a href="37-transient-stability-analysis-dialog-part3.md#smib-eigenvalues">SMIB Eigenvalues</a></p>
<p> </p></td>
<td><p>Perform Single Machine Infinite Bus (SMIB) analysis on each generator in the system to help debug potential model errors which lead to instability.</p>
<p> </p></td>
</tr>
</tbody>
</table>

There are several buttons at the top of the dialog that are normally available regardless of the selected page.

![Transient Stability Dialog Top](images/Transient_Stability_Dialog_Top.jpg)

Run Transient Stability

Click this button to start the analysis once all options and models have been set.

Pause

Click this button to pause a study that is in progress.

Abort

Click this button to stop a study that is in progress.

Simulation Status

Indicates the progress of a study.

For Contingency:

This drop-down determines which contingency is presently being studied. See the [Transient Stability Dialog Multiple Contingencies](37-transient-stability-analysis-dialog-part3.md#simulating-multiple-contingencies) for processing multiple transient contingencies simultaneously.

Add, Delete, Rename

Click these buttons to Add, Delete, or Rename Transient Contingencies. See the [Simulation](#simulation) topic for more details.

There are several buttons at the bottom of the dialog that are available regardless of the selected page.

Save All Settings To...

Clicking this button will show a drop-down menu for saving transient stability data to an external file. More details are found in the [Transient Stability Data from External files](36-transient-stability-overview-and-data-part2.md#data-from-external-files) help topic.

Load All Settings From...

Clicking this button will show a drop-down menu for loading transient stability data from an external file. More details are found in the [Transient Stability Data from External files](36-transient-stability-overview-and-data-part2.md#data-from-external-files) help topic.

Show Transient Contour Toolbar

Clicking this button will automatically add a toolbar to the bottom of the main window in Simulator. This toolbar allows you to visualize the results of the stability run through a series of contour images. It's operating is described in more detail in the [Transient Contour Toolbar](36-transient-stability-overview-and-data-part2.md#transient-contour-toolbar) Topic.

Auto Insert...

Clicking this button will open the [Auto Insert Transient Contingencies Dialog](52-additional-linked-topics-part1.md#auto-insert-transient-contingencies-dialog) which allows the auto creation of several kinds of transient contingencies. More details are found in the [Auto Insert Transient Contingency Dialog](52-additional-linked-topics-part1.md#auto-insert-transient-contingencies-dialog) help topic.

Critical Clearing Time Calculator...

Clicking this button will open the [Critical Clearing Time Calculator Dialog](52-additional-linked-topics-part1.md#auto-insert-transient-contingencies-dialog-1) which allows the auto creation of critical clearing time transient contingencies. More details are found in the [Critical Clearing Time Calculator Dialog](52-additional-linked-topics-part1.md#auto-insert-transient-contingencies-dialog-1) help topic.

---

<a id="simulation"></a>

## Simulation

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Simulation_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Simulation_Control.htm)*

The Simulation Control page is available on the [Transient Stability Analysis dialog.](#transient-stability-analysis-dialog)

The Transient Stability Dialog allows you to define a particular transient stability event which you want to study. PowerWorld refers to this as a *Transient Stability Contingency* because in concept it is similar to the contingency analysis run using power flow solutions. The goal is to simulate a particular contingency to see if it causes any problems for the system. The contingency will consist of one or more events. For example, a transient contingency with only one event might be to model the outage of a generator with the goal of seeing how the governor response of the remaining generators handles this. Another contingency might be to model a fault at a bus which requires two events: one to initiate the fault and a second to clear the fault.

![Transient Stability Simulation Control](images/Transient_Stability_Simulation_Control.gif)

Defining a Transient Contingency

When the **Process Contingencies** option is set to *One Contingency at a Time*, the dialog will appear as depicted below. When defining multiple transient contingencies see [Transient Stability: Running Multiple Contingencies](37-transient-stability-analysis-dialog-part3.md#simulating-multiple-contingencies).

Use the Add, Delete, and Rename buttons to manage your transient contingencies. The drop-down allows you to choose the presently active transient contingency. Transient Contingencies differ from the power-flow based contingency analysis most importantly by introducing the concept of timing. Transient Contingencies require you to specify a Start Time and an End Time for the simulation, both specified in seconds. You must also specify a simulation time step which will be used by the numerical integration software. The following parameters for the transient contingencies are specified at the top of the dialog.

Add..

Click to add a new transient contingencies. The new contingency will automatically be given an unused name starting with "My Transient Contingency". Note that when choosing to [Store Results to Hard Drive](#storage-to-hard-drive), then name of the transient contingency will determine the name of the file to which results are stored.

Delete...

Click to Delete the present contingency. Note that at least one transient contingency must always exist. If you choose to delete the only transient contingency defined, then a new empty transient contingency names "My Transient Contingency" will automatically be created.

Rename

Click this button to be prompted to rename the present transient contingency.

Clone Contingency...

Click this button to clone the current contingency. It will copy the contingency start and end time. Also the time steps and the events of the contingency.

Start Time, End Time

Specify the start and end time of the analysis in seconds.

Time Step

The time step is entered in either seconds or cycles (60 cycles/second) depending on the setting of the **Specify Time Step in** option. This value will change to reflect the appropriate units if the **Specify Time Step in** option is changed.

Specify Time Step in

The **Time Step** can either be specified in seconds or cycles. Changing this option will update the value specified in **Time Step** to reflect the appropriate units. The time step may be specified in seconds or in a number of cycles. For instance, for large studies PowerWorld recommends that you use a half cycle as a time step.

Tripped

Total generation and load in MW tripped during the simulation. For Loads the total include, relay and models trips.

Relay Tripped

Total load in MW tripped by relay models during the simulation.

Model Tripped

Total load in MW tripped by load models during the simulation.

Islanded

Total generation and load in MW islanded during the simulation.

Categories

A comma-separated list of user specified category names. Categories determine which [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#defining-transient-limit-monitors) are applied to each contingency. See the [Contingency Category](21-contingency-analysis-overview-and-records.md#contingency-category) topic for more information.

**Change and Clear Buttons**

Click the Change button to change the categories using a comma-delimited string. Click the Clear Button to clear the Categories

Power Flow Contingency \[Added in Version 24\]

Typically, a power system base case represents the starting point for all the TSContingency simulations specified. Alternatively, the name of a [Power Flow Contingency](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) may be entered in this location. When Simulating the transient stability Contingency then the first step will be to modify the initial condition power flow by solving the specified [Power Flow Contingency](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog).

**Change and Clear Buttons**

Click the Change button to bring up a list of Power Flow Contingencies by name to choose. Clear the Clear Button to clear the entry.

Defining Transient Contingency Elements

Once you've specified this timing, you must then specify the transient contingency elements. Again they are similar to contingency elements for power-flow based simulation, except that these events must have a time associated with them. An example shown in the figure above is a transient contingency which faults a bus at 0.2 seconds and then clears the fault at 0.3 seconds.

Insert Elements

Click this button to open the [Transient Stability Contingency Element Dialog](#transient-contigency-element-dialog).

Clear All Elements

Click this button to delete all currently defined events.

Insert Apply and Clear Fault

Clicking this button also opens [Transient Stability Contingency Element Dialog](#transient-contigency-element-dialog), however the dialog will be modified to only allow the specification of a bus fault or a branch line fault. There will also be an option on the dialog to enter the Clearing Time in Seconds. This provide a convenient way to more quickly enter a fault and the clearing time of that fault instead of having to enter the dialog twice. When performing this action for a transmission branch it will automatically add THREE actions: Apply Fault, BRANCH Open Near, and BRANCH Open Far.

Time Shift (seconds)

Click this button to time shift all contingency elements of the selected contingencies. The amount of time (seconds) to be shifted is specified to the right of the button.

Element Table

This table provides a listing of all transient stability elements that are currently defined. This is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and provides the case information toolbar and local right-click menu for options. New events can be inserted through the **Insert** menu/toolbar item. Events can be deleted through the **Delete** menu/toolbar item. Use the **Show Dialog** option to open the [Transient Stability Contingency Element Dialog](#transient-contigency-element-dialog) to modify the event. Model criteria can be applied to transient contingency actions in this table as well. The action will then only be applied of the initial conditions meet the model criteria.

Monitor Violation Table

As a transient stability run is processed, any violations of the Transient Limit Monitors will be stored as a monitor violation and can be seen in the [Monitor Violations table](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors-violations).

---

<a id="transient-contigency-element-dialog"></a>

## Transient Contigency Element Dialog

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Event_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Event_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Stability Contingency Element Dialog is used to specify specific transient stability events and when they occur during the analysis.

![Transient Stability Dialog ContingencyElement 804x619](images/Transient_Stability_Dialog_ContingencyElement_804x619.gif)

Event Description

Drop-down containing a list of all currently defined events. An even description will be created automatically based on the event time, event object, and even action. This drop-down can be used to switch between events and make any necessary modifications.

Object Type

Specify the object type for the event. The type of object chosen will change the type of events that can occur.

Choose the Element

This list will be updated as the **Object Type** is changed. This list contains all of the available objects for the selected **Object Type**. Select a specific object from this list for which the event will be applied.

Event Time

Specify the time in seconds at which the event occurs.

Event Type, Event Parameters

The type of event and parameters will change depending on the Object Type chosen. Valid options are:

Bus

**Apply Fault**

Apply the specified fault type and fault across.

**Fault Type** - *Balanced 3 Phase*, *Single Line to Ground*, *Line to Line*, or *Double Line to Ground*.

**Fault Across** - *Solid*, *with Impedance* and specifying **PU Resistance** and **PU Reactance**, or *with Admittance* specifying **PU Conductance** and **PU Susceptance**. Starting in Version 19, there are also choices for *to Achieve Voltage* and *To Scale Voltage*.

Added in Version 19When choosing any of the unbalanced fault types, then a check box entitled **Calculate Effective Impedance from Sequence Networks** is made active and an image is shown in the right portion of the dialog depicting how the total effective positive sequence fault impedance is calculated from the driving point sequence impedance at the fault point and the fault impedance. This check box is used in combination with the choice of **Fault Across** choice below to determine the impedance used to model the fault in the positive sequence network with this calculation being described in the table at the end of this topic.

Added in Version 20, May 14, 2018 patchWhen choosing to **Apply Fault**, a check box option for **Self Clearing Fault** is available. To default behavior and previous behavior is represented by not checking this box. This means that when a bus becomes isolated due to opening other branches to isolate this bus, the fault will remain in place. Because the bus is isolated it will not impact the simulation, however if branches are closed back in such that the bus is no longer isolated then the fault will again be there. By checking **Self Clearing Fault** however, as soon as a fault location becomes isolated the fault will automatically clear itself. It is appropriate to <span class="underline">not check</span> this box when modeling a permanent fault such as a tree falling on a line, while it may be appropriate to <span class="underline">check</span> this box to model a lightning strike or a wind blowing a tree branch into a line.

**Clear Fault**

Clear a fault.

**Open**

Opens all AC lines connected to a bus.

Generator

**Open**

Open the generator.

**Close**

Close the generator.

**Ramp Values**

Ramp the output of the generator as defined by the **Action Field**. Options for the Action Field are MW Setpoint at Bus, Exciter Setpoint (Vref), Governor Setpoint (Pref), Part. Factor and Rotor Angle (Degrees), Delta Speed (Hz). Specify that the output be ramped **By** **Value** or **Percentage**. Specify the **Ramp Duration** in seconds at which the ramping lasts.

**Set Values**

Set the output of the generator as defined by the **Action Field**. Options for the Action Field are MW Setpoint at Bus, Exciter Setpoint (Vref), Governor Setpoint (Pref), Part. Factor and Rotor Angle (Degrees), Delta Speed (Hz). Specify that the output be set **By** **Value** or **Percentage.**

**Change Values**

Change the output of the generator as defined by the **Action Field**. Options for the Action Field are MW Setpoint at Bus, Exciter Setpoint (Vref), Governor Setpoint (Pref), Part. Factor and Rotor Angle (Degrees), Delta Speed (Hz). Specify that the output be chamge **ByValue** or **Percentage.**

**Enable AGC**

Enable AGC on the generator.

**Disable AGC**

Disable AGC on the generator.

Load

**Open, Close**

Specify that the load either be opened or closed.

**Change Values**

Change the output of the load as defined by the **Action Field**. Option for the Action Field is MW. Specify that the output be set **By** **Value** or **Percentage.**

**Set Values**

Set the output of the load as defined by the **Action Field**. Option for the Action Field is MW. Specify that the output be set **By** **Value** or **Percentage.**

**Ramp Values**

Ramp the output of the load as defined by the **Action Field**. Options for the Action Field are MW. Specify that the output be ramped **By** **Value** or **Percentage**. Specify the **Ramp Duration** in seconds at which the ramping lasts.

NOTE: When changing, setting or ramping a load, a new scalar is computed using the initial Real Power of the load. When the load does not has a motor transient model, that scalar is multiplied to the present Real Power to get the desired value. The same scalar is multiplied to the present Reactive Power to compute a new value. The power factor then remain the same during initial load change. When the load has a motor transient model the real power is only modified and the reactive power is not modified thus will react accordingly to the change.

Switched Shunt

**Open, Close**

Specify that the load either be opened or closed.

**Change Values**

Change the output of the switched shunt as defined by the **Action Field**. Option for the Action Field is Nominal Mvar. Specify that the output be set **By** **Value** or **Percentage.**

**Set Values**

Set the output of the switched shunt as defined by the **Action Field**. Option for the Action Field is Nominal Mvar. Specify that the output be set **By** **Value** or **Percentage.**

Branches/Transformer

**Apply Fault**

Apply the specified fault type.

**Fault Type** - Balanced 3 Phase, Single Line to Ground, Line to Line, or Double Line to Ground

**Fault Across** - Solid, with Impedance and specifying **PU Resistance** and **PU Reactance**, or with Admittance specifying **PU Conductance** and **PU Susceptance**. Starting in Version 19, there are also choices for *to Achieve Voltage* and *To Scale Voltage*.

**Percent Location (near to far)** - Specify the location of the fault as a percentage of the distance from the near end of the line. A fault at the near end would be a percentage of 0% and a fault at the far end would be percentage of 100%.

Added in Version 19When choosing any of the unbalanced fault types, then a check box entitled **Calculate Effective Impedance from Sequence Networks** is made active and an image is shown in the right portion of the dialog depicting how the total effective positive sequence fault impedance is calculated from the driving point sequence impedance at the fault point and the fault impedance. This check box is used in combination with the choice of **Fault Across** choice below to determine the impedance used to model the fault in the positive sequence network with this calculation being described in the table at the end of this topic.

Added in Version 20, May 14, 2018 patchWhen choosing to **Apply Fault**, a check box option for **Self Clearing Fault** is available. To default behavior and previous behavior is represented by not checking this box. This means that when a fault location becomes isolated due to either opening both ends of this branch or by opening other branches to isolate a portion of the system, the fault will remain in place. Because the fault location is isolated it will not impact the simulation, however if branches are closed back in such that the fault location is no longer isolated then the fault will again be there. By checking **Self Clearing Fault** however, as soon as a fault location becomes isolated then the fault will automatically clear itself. It is appropriate to <span class="underline">not check</span> this box when modeling a permanent fault such as a tree falling on a line, while it may be appropriate to <span class="underline">check</span> this box to model a lightning strike or a wind blowing a tree branch into a line.

**Clear Fault**

Clear a fault.

**Open**

**Which End** - Both Ends, From End Only, To End Only, One Phase Open

**Close**

**Which End** - Both Ends, From End Only, To End Only

**Bypass**, and **Not Bypass**

Use this option to either Bypass or Not Bypass a branch. Normally we would expect this branch to be a series capacitor or reactor.

**Set Values**

Use this option to Set Value Type of Line Impedance PU Resistance and PU Reactance or GMD-Induced DC Voltage value.

DC Line

**Open**

Open the entire DC line.

Injection Group

**Open**

**P or Q** - MW, MVAr

**Device** - Generation, Loads

**MW or MVAr** - Amount to open. The amount to open will be based on the initial condition of the device (not the transient condition), and devices will be opened in order of highest participation factor to lowest participation until at least the amount specified has been exceeded.

Line Shunt

**Open, Close**

Specify that the line shunt either be opened or closed.

Transformer

**Set Values**

Set the value of the transformer as defined by the **Action Field**. Options for the Action Field are LTC Tap, Phase in Deg, Tap Step Position, Setpoint for Control and Range for Control. Specify that the value be set in the box specified.

**Change Values**

Change the value of the transformer as defined by the **Action Field**. Options for the Action Field are LTC Tap, Phase in Deg, Tap Step Position, Setpoint for Control and Range for Control. Specify that the value be set in the box specified.

**Enable Auto Control**

Enable Auto Control on the transformer.

**Disable Auto Control**

Disable Auto Control on the transformer.

Area

**Ramp Values**

Ramp the output of the Areaas defined by the **Action Field**. Option for the Action Field is Export to Other Area (MW). Specify that the output be ramped **By** **Export MW**. Specify the **Other Area Number** to which the export is happening. Specify the **Ramp Duration** in seconds at which the ramping lasts.

**Enable AGC**

Enable AGC on the Area.

**Disable AGC**

Disable AGC on the Area.

OK

Click this button to accept any changes and close the dialog.

Save

Click this button to save any modifications to the current event. The dialog will remain open.

Insert

Click this button to create a new event with the specified parameters.

Delete

Click this button to delete the current event as defined by the **Event Description**.

Help

Click this button to open this help topic.

Cancel

Close the dialog without saving any of the changes.

Calculation of the Total Effective Positive Sequence Impedance seen at the fault Point

The check box **Calculate Effect Impedance from Sequence Networks** was added in Version 19.

Fault Across

Fault Type Choices

Balanced 3 Phase

Unbalanced Faults: Single Line to Ground, Line to Line, or Double Line to Ground

Solid

A very small impedance is assumed to represent a solid fault. Simulator uses a Fault impedance of

Zfault = 0 + j1E-8

You must specify to **Calculate Effective Impedance from Sequence Network** when choosing to fault across *Solid* in combination with any unbalanced Fault type. If you do not do this on the dialog box then Simulator will not allow you to close the dialog. If you specify a Solid unbalanced fault in an Auxiliary file without specifying the option to CALCSEQ, then Simulator will assume the option to calculate effective impedance was intended. An appropriate warning message is also written to the message log to indicate that this is being done.

with Impedance but <span class="underline">not</span>

**Calculate Effect Impedance from Sequence Networks**

Option will appear to specify the **PU Resistance** and **PU Reactance**. This represents the total effective positive sequence impedance seen at the fault point looking into the fault. Note that when choosing **Fault Across** to be *with Impedance* and not checking the box **Calculate Effective Impedance from Sequence Network**, then the **Fault Type** choice has no effect on the simulation. Users may still choose the **Fault Type** as it is informational.

with Impedance and

**Calculate Effect Impedance from Sequence Networks**

Not applicable. When choosing a *Balanced 3 Phase***Fault Type**, the check box to **Calculate Effective Impedance** is not available.

Option will appear to specify the **PU Resistance** and **PU Reactance**. This represents the impedance across the fault itself. The total effective positive sequence impedance seen at the fault point looking into the fault is then calculated from the driving point sequence impedance at the fault point and this fault impedance. The image on the right portion of the dialog depicts how this total effect impedance is calculated.

with Admittance

Option will appear to specify the **PU Conductance** and **PU Susceptance** which represents the admittance seen at the fault point looking into the fault. An admittance value of 0 - j1E8 would be equivalent to our default fault impedance. Otherwise this option works the same as specifying with Impedance, but instead a user enters a value of admittance.

to Achieve Voltage

Option will appear to specify a **PU Voltage**. This represents the desired PU voltage at the fault point immediately after applying the fault. PowerWorld Simulator will then automatically determine a fault impedance needed to result in that post-fault voltage. Note that when choosing **Fault Across** to be *to Achieve Voltage*, then the **Fault Type** choice has no effect on the simulation, but remains informational.

to Scale Voltage

Option will appear to specify a **Factor**. This represents the factor by which it is desired that the PU voltage at the fault point be changed immediately after applying the fault. For example, if the pre-fault voltage is 1.05 pu and and a factor of 0.6 is specified, then the desired post-fault voltage is 0.63 per unit. PowerWorld Simulator will then automatically determine a fault impedance needed to result in that post-fault voltage. Note that when choosing **Fault Across** to be *to Achieve Voltage*, then the **Fault Type** choice has no effect on the simulation, but remains informational.

---

<a id="options"></a>

## Options

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options.htm)*

The Options page is found on the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). The Options page is broken down into several sub-categories of options described as follows.

[General](#general) : options for various user interface choices of how data is displays and how the user interacts

[Power System Model](#power-system-model) : options for the actual transient stability numerical simulation

[Remedial Actions](#remedial-actions): options for including Remedial Action Schemes (RAS) with Transient Stability

[Result Options](#result-options) : options for how the results are stored during the simulation

[Generic Limit Monitors](#generic-limit-monitors) : special options that apply generic limit monitors to all objects during the simulation

[User Defined Models](52-additional-linked-topics-part3.md#transient-stability-dialog-options-user-defined-models) : set browsing path and view available user defined models

[Distributing Computing](#distributed-computing): set to distribute transient contingencies.

---

<a id="general"></a>

## General

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_General.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_General.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The General sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). This contains various choices of how data is displayed in the user interface and how you interact with the user interface.

![Transient Stability Dialog Options General](images/Transient_Stability_Dialog_Options_General.gif)

MVA Base for Input/Display of Generator Values

Specify the MVA base to use for generators: either the MVA base value entered for each individual generator or the MVA base value specified for the case.

Identify Buses in Events and Results by

Choose how to identify any buses that appear in transient stability events and results. Buses can be identified by number or name or a combination of both. The nominal kV of the bus can also be used as part of the identifier.

When Case has a Transient Stability Model Show Confirmation Dialog

If in the middle or at the end of a transient stability simulation the user tries to save the case, Simulator can prompt whether to save the case with the power system state after the transient stability simulation or to save the case with the power system state in place prior to starting the transient stability analysis. This option determines when the prompt will appear. If not prompted, the state will remain in the state following the transient stability simulation.

Automatic Update and Transfer Results to Power Flow Options

Specify the interval in time steps to update the displays or when to transfer results to the power flow model. Also, specify whether or not the displays should be updated and when/if results should be transferred to the power flow model. Any open plots will be refreshed automatically when performing the interval check while running transient stability.

---

<a id="power-system-model"></a>

## Power System Model

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_Power_System_Model.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_Power_System_Model.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Power System Model sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). This contains options for how the actual transient stability numerical simulation is performed.

![Transient Stability Dialog Options PowerSystemModel](images/Transient_Stability_Dialog_Options_PowerSystemModel.gif)

Common: Power System Values

Nominal System Frequency (Hz)

Set the nominal system frequency in hertz. The default is 60 Hz.

System MVA Base

MVA base for the system. The value cannot be changed here and is shown for informational purposes only. To change this value, go to the [Power Flow Solution General page](10-power-flow-solution-and-options-part2.md#power-flow-solution-general) found under [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Initial System Frequency (Hz)

Normally, the assumed initial system frequency is the Nominal System Frequency. To set the initial condition's frequency differently change this value.

When Using Playin Models Set Initial Hz to First Value Added in Version 20.

Choose this check box to automatically set the initial system Frequency to the initial frequency from the PlayInGen model's frequency PlayIn signal.

Common: Network Equation Solution Options

Solution Tolerance (MVA)

Specify the convergence tolerance used in the transient stability's power flow algorithm. This option setting only affects the transient stability power flow algorithm and does not affect the power flow model.

Maximum Iterations

Specify the maximum number of iterations allowed in the transient stability's power flow algorithm. This option setting only affects the transient stability power flow algorithm and does not affect the power flow model.

Abort after number of failed solutions Added in Version 20.

When running a transient stability simulation, a particular network solution may have a hard time converging and result in oscillating near a solution but not actually achieve a solution to within the tolerance. It is not uncommon for the network solution to then be achieved easily on the next time step's network solution. This option defaults to a value of 10 meaning that the simulation will not abort until 10 consecutively failed network solutions.

Force Network Equation Update

Specify a time in seconds which forces a full network equation update every so many seconds. This option can be helpful to avoid small unit oscillations caused by small mismatches.

Use Voltage Extrapolation

When this option is checked, an estimate of the voltage at time step will use the voltage at the previous three time steps to estimate what the next voltage will be. This essentially models the voltage as a quadratic function of time based on the last three time steps and creates an estimate of what the next voltage will be. This greatly aids in the initial guess sof the network equation voltages at a time step and helps speed up the simulation.

Inner Loop Mismatch Scalar

PowerWorld Simulator uses a second order Runge-Kutta integration method. As a result network equation solutions are sometimes done at intermediate time steps as part of the integration method. Specifying a scalar here which is larger than 1.0 will allow those intermediate network equation solution to have a larger mismatch.

Common: Handling of Initial Limit Violations

The first step in a transient stability numerical simulation is to initialize the transient stability dynamic models based on the initial condition taken from the power flow solution. It is not uncommon for this initialization to result in many violations of limits specified in the dynamic models. This gives you three options for how to handle these initial limit violations. The options and what the do are as follows

1\. Modify Limits and Run: choose this to have Simulator temporarily modify the limits that are violated during this transient stability simulation.

2\. Abort: choose this to abort the numerical simulation completely if any state violations exist. In an ideal world, all these would be corrected before continuing, but you may not have information on how to correct either the stability model or the initial power flow solution.

3\. Run without Changing Limits: choose this to run Simulator leaving the limits alone. This means that the states in simulation will immediately start moving at the initial time as the numerical simulation enforces these limits.

A list of limit violations is available on the [Transient Stability Analysis: States/Manual Control](37-transient-stability-analysis-dialog-part3.md#statesmanual-control)

Common: Integration Method

Option to specify whether to use the Second Order Runga-Kutta Order 2 (RK2) integration time step or a simple Euler step.

Common: Infinite Bus Modeling

Select whether or not to use infinite buses. If using infinite buses, the power system slack bus(es) will be used as the infinite buses. If not using infinite buses, then an **Angle Reference** must be selected on the [Result Options](#result-options). At infinite buses the angle does not change. When using infinite buses, these are used as the angle reference.

Common: Frequency Measurement Options

Bus Frequency Measurement Time Constant (Sec.)

Bus frequency in a transient stability simulation is a value which is calculated by performing a special calculation similar to taking the derivative of the bus angle. This means there is a time-constant associated with calculating this frequency and this value can be specified here. Also note that Bus frequency is calculated at all buses during a transient stability simulation.

Minimum PU voltage for relay frequency measurement Added in Version 19, November 24, 2015

Some transient stability models involve using bus frequency as signal that determines whether to trip a device. Load relays or generator relays for instance. In some extreme situations at very low voltages, the calculation of bus frequency using a time constant can give very low or very high frequency values which would not be seen by a real relay. In a real relay device there is always a voltage threshold below which these types of relays be blocked from operating. This is because frequency in relays in calculated by looking at the zero crossing of a the AC wave form. The counting of zero crossings becomes unreliable at low voltage. This option (which defaults to 0.3 per unit) will change how relays perceive frequency when the per unit voltage is below this threshold. If the voltage falls below this threshold the relay will behave as though it is seeing the nominal frequency.

Calculate Bus ROCOF (Rate of Change of Frequency) Added in Version 20

Check this box to also calculate the derivative of the bus frequency.

Common: Negative Load Models for Generators without Models

Specify as either a constant impedance or a constant current. This determines how the generator is modeled during the simulation if the generator does not have any machine model specified.

Common: Island Synchronization Added in Version 20

Transient stability simulations do not fully model the closing of a transmission line that connects two separately synchronized electrical islands. In order to properly model this numerically, one must assume that the presently the phase angles on either side of the AC branch being closed in are nearly matched and that the frequencies of both islands are nearly matched. In a real system, an system operator may need to change generator governor set points to bring the system frequencies to a common value, but in a numerical simulation this may be cumbersome. Assuming that the bus voltage angles are brought back close to one another is an easier task as really the angle in the system are really only important as compared to other angles. It is appropriately to rotate all angles in the system by the same degrees. These decisions lead to 2 options.

Angle Options and Value Added in Version 20

This is the choice about how to change the angles in separate electrical islands before closing in an AC branch.

1\. Set to Degree Value: This option means that the angle difference across the AC line will be set to the **Degree Value** specified. This is done by rotating all the angles in one electrical island to achieve this.

2\. Set if \> Degree Value: This option is similar to the first, but we will only rotate bus angles if the existing angle difference is larger than the **Degree Value** specified.

3\. No Change. This option means no change will be made.

Frequency Options and Value Added in Version 20

This is the choice about how to change the frequencies in separate electrical islands before closing in an AC branch.

1\. Set to Hz Value: This option means that the frequency difference across the AC line will be set to the **Hz Value** specified. It is provided as a convenience for a numerical simulation tool, but you should realize that this has no physical meaning and is achieved numerically by instantaneously changing the machine speed state of all synchronous machines in the electrical island and also changing the calculated frequency of all buses in the island. This is not physically possible, but can be useful in a simulation tool.

2\. Set if \> Hz Value: This option is similar to the first, but we will only change the frequencies if the existing frequency difference is larger than the **Hz Value** specified.

3\. No Change. This option means no change will be made.

Common: Simulate New Island Requirements

As branches change status during a transient stability simulation, new islands can be created. These options will determine if a newly created island continues to be simulated. If the newly created island does not have at least a specified number of buses AND a specified number of gnerators then it will not be numerically simulated. When an island is not simulated it means that all buses in the newly created island are assumed to be dead with a 0.0 voltage at all buses and all dynamic models ignored.

Bus Count \>= Added in July 10, 2023 patch of Version 23

Specify a minimum number of buses

Generator Count \>= Added in July 10, 2023 patch of Version 23

Specify a minimum number of generators.

Common: Geomagnetic Induced Current Options

Include GIC Effects

Check this box to include GIC effects (Mvar losses caused by GIC) in the transient stability simulation.

Just Calculated GIC with No Network Solution Added in Version 20

Check this option to use the transient stability simulation tool as a convenient tool for running a time-series of GIC DC network calculations. This means that the traditional transient stability simulation will not be done at all, but instead at each time-step the GIC DC currents will be calculated but no further calculations will be done.

Load Modeling: Default Load Model

Specify what load model to use by default in the transient stability simulation when the load does not have a load model characteristic defined. Normally it is best to define a load characteristic model specifically (it is even possible to define a load characteristic model which applies to the entire case), but if one is not specified this default will be used.

Load Modeling: Minimum Per Unit Voltages for

When modeling loads as **Constant Power Models** or **Constant Current Models**, the load will start to fall off by a particular function if the voltage falls below the specified value. The values specified here are the same as the values for minimum voltages specified on the [Power Flow Solution Advanced Options page](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) found under [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options). Clicking the **Change** button will open the Power Flow Solution Advanced Options page.

Load Modeling: When to use Complex Load Models

There are several global filters which are used to indicate when complex [load characteristics](36-transient-stability-overview-and-data-part1.md#load-characteristics) that represent a composite of various other load types should be ignored. (Examples of these types of loads are CLOD, CMPLDW, CMLD, MOTORW and CompLoad). These filters also apply to the [distribution equivalent model](36-transient-stability-overview-and-data-part1.md#load-distribution-equivalent). If the load record meets any of these filters then the distribution equivalent will be ignored and the complex load model will not be used and the default load model will be used instead.

Minimum Load P (MW) Added in Version 19, September 14, 2016 patch

A complex l[oad characteristic model](36-transient-stability-overview-and-data-part1.md#load-characteristics) and [distribution equivalent model](36-transient-stability-overview-and-data-part1.md#load-distribution-equivalent) will not be used if the load is less than this power.

Minimum Load P/Q (MW) Added in Version 19, September 14, 2016 patch

A complex l[oad characteristic model](36-transient-stability-overview-and-data-part1.md#load-characteristics) and [distribution equivalent model](36-transient-stability-overview-and-data-part1.md#load-distribution-equivalent) will not be used if the ratio of real power to reactive power is less than this value. Default value is 0.25 which would mean that the real power of the load is 4 times smaller than the reactive power of the load.

Minimum Initial per unit voltage Added in Version 20

A complex ll[oad characteristic model](36-transient-stability-overview-and-data-part1.md#load-characteristics) and [distribution equivalent model](36-transient-stability-overview-and-data-part1.md#load-distribution-equivalent) will not be used if the initial voltage at the transmission level bus is less than this value.

Load Modeling: Distribution Equivalent Model Options

Min Nom kV for Transformer Added in Version 20

Any [distribution equivalent model](36-transient-stability-overview-and-data-part1.md#load-distribution-equivalent) that is assigned to a load which is connected to a bus with a nominal voltage below this value will automatically ignore the Xxf term of the transformer. Essentially for that particular load the Xxf value will be assumed to be 0.0.

Compatibility Options: Exciter Saturation Model

Option to specify the type of saturation function to use for an exciter model. Choices are Quadratic (GE Approach), Scaled Quadratic, or Exponential. When loading a PSLF DYD file it defaults to the Quadratic exciter saturation function. When loading a PSS/E DYR file it defaults to the Scaled Quadratic exciter saturation function. When loading a IPF SWI file it defaults to the Exponential exciter saturation function.

Compatibility Options: Exciter Automatic Parameters

Allow implementation of option to determine how Ke is determined, either using the GE approach \[setting Vr=0\] by selecting *Vr = Zero Approach*, or the PSSE approach (of equal to Vrmax/10 by selecting *Vr \> Zero Approach*.

Compatibility Options: Machine Saturation for S12 \< S10

Selecting *Flip Values* will Flip the values when this condition (S12 \< S10) is met. Selecting Ignore Saturation will ignore the saturation when the condition (S12 \< S10) is met.

Compatibility Options: Saturation when One SE is Zero

Selecting *Treat as Always Zero* will give the Saturation a zero value. Selecting *Normal Curve Fit* will try to give the Saturation the value by doing a curve fitting.

Compatibility Options: MotorW Modeling

The PSLF MotorW induction motor model, which is also used inside the CMPLDW and CMPLDWNF model, but does not use a standard induction motor model with 7 input parameters.

Instead MotorW only provides 6 input parameters (it omits the leakage reactance) and it uses different dynamic equations. For the case of a single cage motor, the equations of MOTORW are the same as other induction motors, but for the case of a double-cage motor the models are different. In order to match the results seen in PSLF you must set this option to PSLF. If you choose Full Model, then the leakage reactance is assumed to be equal to 0.8\*Xpp. If you want to specify a particular leakage reactance than use a different load model.

Compatibility Options: Governor Fast Valving

A few specific governor models such as TGOV3 include an effect called Fast Valving. This option specifies at what time the fast valving option is initiated. After choosing when you would like it to initiate you then specify either a frequency deviation in rad/sec or a time in second as the parameter **Fast Valving Parameter (rad/sec or sec)**.

Compatibility Options: Ignore Speed Effects in Generator Swing Equation

The generator swing equation includes a term divides the Mechanical Power by the per unit speed of the generator. Checking this box will ignore this speed effect. Normally you should not ignore this effect.

Compatibility Options: Include Undocumented Governor PI Limits

Selecting this option will enforce non-windup limit for the governors regarding of the parameters settings in the governor. This includes the following governors: HYPID, GPWSCC, PIDGOV, HYG3

Compatibility Options: Include dynamics of 3 terminal Pacific DC Intertie or Intermountain DC if appropriate MTDC records exists

Selecting this option will inlude the modeling of the dymaics of 3 terminal Pacific DC Intertie or Intermountain DC models.

---

<a id="remedial-actions"></a>

## Remedial Actions

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS.htm)*

The Remedial Actions sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). This contains options for running transient stability and including remedial actions in the simulation.

Remedial actions that are defined for use with steady-state analysis can also be used with transient stability. Remedial actions are not included by default and some features that are used with steady-state analysis are not available with transient stability. There are features available to better understand what actions and fields are translated for use with transient stability.

![Transient Stability Dialog RAS Options](images/Transient_Stability_Dialog_RAS_Options.png)

Run Remedial Action Validation

Not all actions and fields are available for use with transient stability. Click this button to validate remedial actions prior to running transient stability. Here is more [info on the validation process](52-additional-linked-topics-part2.md#transient-stability-analysis-options-remedial-action-validation).

Show Valid Remedial Action Fields

Clicking this button will open a table listing all of [the available fields by object type](52-additional-linked-topics-part2.md#transient-stability-analysis-options-valid-remedial-actions-fields).

Include Remedial Actions in Transient Analysis

Select this check-box if remedial actions are to be included in the transient stability analysis.

---

<a id="result-options"></a>

## Result Options

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_ResultOptions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_ResultOptions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Result Options sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). The options on the Result Options determine how the results are stored during the simulation.

![Transient Stability Dialog Options ResultOptions](images/Transient_Stability_Dialog_Options_ResultOptions.gif)

Time to Begin Checking for Minimum and Maximum Results

Minimum and maximum values for several bus and generator parameters are automatically stored during the analysis. This option determines when the recording of these minimum and maximum values should begin.

If you choose *After last event*, then the recording of minimum and maximum results will start after the last transient contingency element is processed for the simulation. This is the most common option and is used to prevent the recording of very low voltages during a fault event from being recorded as the minimum result when you are really only concerned with how the voltages recover after the fault clears.

If you choose *Immediately*, then the minimum and maximum result recording will start at the beginning of the simulation.

If choosing to use a *Custom Time*, a field will appear that will allow entry of a specific time in seconds when recording should begin.

Time to Begin Checking for Limit Monitors Results

This option determines when the recording of the [Limit Monitor Results](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors) values should begin.

If you choose *After last event - Time after last event*, then the recording of limit monitor results will start after the last transient contingency element is processed and a specific time after that can be specified.

If you choose *Immediately*, then thelimit monitor result recording will start at the beginning of the simulation.

If choosing to use a *Custom Time*, a field will appear that will allow entry of a specific time in seconds when recording should begin.

Angle Reference Options

Note: if infinite buses are being modeled as part of the [Power System Model options](#power-system-model), this option is not used and the fixed angle at infinite bus is automatically used as the reference.

Generator Rotor Angles in a transient stability simulation are calculated with respect to what is called the synchronous reference frame. The synchronous reference frame represents how the angles would move with respect to a theoretical rotating reference frame based on the system nominal frequency. When a transient stability simulation converges to a new steady state frequency which is higher than nominal frequency, then inherently the rotor angles as expressed in this synchronous reference frame will continue to increase toward infinity. This will not indicate instability as long as the angles in relation to one another converge upon a new steady state.

The use of the synchronous reference leads to the angle reference option. This option specifies a reference which will be used to calculate an angle reference at each time step in a simulation. This angle reference will be calculated across the entire system. The generator field *Rotor Angle* recorded at a particular time in the results will then be equal to this system angle reference subtracted from the rotor angle on the synchronous reference frame. (Note: normally an angle reference option should be chosen because the generator rotor angle in the synchronous reference frame may be stored as an independent result variable called *Rotor Angle, No Shift*, which is distinct from the *Rotor Angle*.)

When looking at a plot of rotor angles in the synchronous reference frame, the plot may look as shown on the left below. If a angle reference option is chosen, then when plotting generator rotor angles, the plot will instead look as shown on the right. Both plots show the same system, but the plot on the right more clearly shows that the system is stable. Here is a link with a detailed explanation of the [angle reference and other type of angles](52-additional-linked-topics-part3.md#transient-stability-angle-reference) available in PowerWorld.

![Transient Stability Dialog Options ResultOptions AngleReference](images/Transient_Stability_Dialog_Options_ResultOptions_AngleReference.gif)

The options for angle reference are as follows

  - *Average of Generator Angles* : reference equals the straight average of all rotor angles in the system
  - *Weighted Average of Generator Angles* : reference equals the average of all rotor angles in the system weighted by each generators MVA base.
  - *Specified Angle Reference Generator Terminal Angle*: the terminal bus angle of the generator specified on the dialog as the **Angle Reference Generator** will be used.
  - *Specified Angle Reference Generator Internal Angle*: the internal bus angle of the generator specified on the dialog as the **Angle Reference Generator** will be used.
  - *Synchronous Reference Frame (No Angle Shift)* : no reference angle is used so all rotor angles are reported on the synchronous reference frame.

Angle Reference Generator

This option must be set if the option for **Angle Reference Option** is set to one of the choices for using a specific generator.

Initialize with Reference Angle at Zero

This initializes the reference angle, regardless of the method selected for determining the reference angle, to zero at the beginning of the analysis. In practice this is done by recording the starting reference angle. At each time step the reference angle is determined and then this is offset by subtracting the original reference angle value from the current reference angle value and this new value becomes what is used as the reference angle at each time step.

When choosing a generator as the Angle Reference which is presently out-of-service, or is not a synchronous machine, and choosing to use an angle reference which uses that generator, Simulator will now create a validation warning alerting you of the problem. The simulation will still run, but the angle reference will be the Synchronous Reference Frame (No Angle Shift) instead of your choice

Do not store Events during simulation

This option must be check to not store events during the simulation.

Do not store Solution Details during simulation

This option must be check to not store the solution details during the simulation.

Result Event Reporting

This option let the user select where the *Transition, Model Trip* and *Relay Trip* messages will be shown.

The options to Where to Report are: *Both Log and Event*, (massages log and Events table in simulator) or *Event Only, Not Log* ( onlye in the Events table in simulator). The event

---

<a id="generic-limit-monitors"></a>

## Generic Limit Monitors

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_GenericLimitMonitors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_GenericLimitMonitors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generic Limit Monitors sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). It contains the following special options apply generic limit monitors to all objects during the simulation.

![Transient Stability Dialog Options GenericLimitMonitors](images/Transient_Stability_Dialog_Options_GenericLimitMonitors.gif)

Synchronous Generator Limit Monitors

**Only Apply to Generators Without Relays** is a check-box which chooses to apply these generic limit monitors only to generators which do not have their own generator relay (such as a GP1) assigned to them.

There are three generic limit monitors which can be applied to all synchronous generators. These limit monitors are as follows

  - **Absolute Angle Deviation** : monitors for synchronous generators whose rotor angle increases to a value which is substantially different than the initial rotor angle. This is a very crude attempt to monitor for out-of-step generators.
  - **Over Speed** : monitors for synchronous generators which experience high speed.
  - **Under Speed** : monitors for synchronous generators which experience low speed.

The limit monitors can then be configured to look for a violation of a specified Pickup Value that occurs for a specified Pickup Time. If a violation occurs you then specify an action to take due to this violation which can be either *Ignore*, *Log Warning*, *Trip (Open)*, or *Abort*. *Ignore* does nothing. *Log Warning* will return an Event in the Transient Stability Results indicating that a violation occurred and when it occurred. *Trip (Open)* will cause the generator to trip off-line (an event will also be logged stating this). If *Trip (Open)* is chosen then the generator will trip after a delay in cycles specified by the **Breaker Delay Time (cycles)**. Finally, *Abort* will causing the simulation to immediately abort when the limit monitor violation occurs.

Maximum Allowable Angle Difference (degrees):

This parameter determines the maximum allowable angle difference between any two generator rotor angles in the case. If this value is exceeded, the transient stability analysis will stop

Branch Limit Monitors

There is one generic limit monitors which can be applied to all branches. These limit monitors is as follows

  - **Apparent Impedance** : monitor the Apparent Impedance at both ends of branches, by using a simple impedance relay within a reach circle. This can be applied to all AC branches in the case, or to only those branches that meet a filter.

The limit monitors can then be configured to look for a violation of a specified Percent of Branch Series Impedance that occurs for a specified Pickup Time. If a violation occurs you then specify an action to take due to this violation which can be either *Ignore*, *Log Warning*, *Trip (Open)*, or *Abort*. *Ignore* does nothing. *Log Warning* will return an Event in the Transient Stability Results indicating that a violation occurred and when it occurred. *Trip (Open)* will cause the branch to trip off (an event will also be logged stating this). Finally, *Abort* will causing the simulation to immediately abort when the limit monitor violation occurs.

Filter Name:

Filter to apply the Apparent Impedance generic limit monitor to those branches specified in the filter.

For more customizable limit monitors, see the [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors) section.

---

<a id="distributed-computing"></a>

## Distributed Computing

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_Distributed_Computing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_Distributed_Computing.htm)*

**The Distributed Transient Stability Analysis tool is available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for more details.****

The Distributed Computing sub-tab is found on the [Options](#options) page of the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog).

Distributed Computing is available for use with Transient Stability Analysis. In order to use distributed computing you must first configure a list of remote computers which can be utilized along with appropriate authentication information for those computers. The computer list and authentication information is common to all the distributed computing tools in Simulator and can be found in the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), or reached with the Distributed Computing Options button in the Distributed Computing sub-tab. They are described in [Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons).

The only option specific to Transient Stability Analysis for Distributed Computing is the following

Use Distributed Computing

Check this box to signify that when processing contingencies distributed computing should be used.

---

<a id="results-storage"></a>

## Results Storage

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results_To_Save.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results_To_Save.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results Storage page is found on the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog). The settings on this page determine

  - What results are stored during the stability simulation.
  - Where results are stored: RAM, Hard Drive, Both, or Neither.
  - The frequency with which results are stored.

You may want to store results to RAM so that they can be viewed in the [Transient Stability Results: Time Values](37-transient-stability-analysis-dialog-part3.md#time-values). Be careful however because if too many results are stored you will run out of RAM causing the simulation to fail or generally slow down your computer.  

When storing results to Hard Drive you can be much more free with how much data is saved. After running you will still be able to load those results into RAM later (using the **Load from Hard Drive File into RAM results specified by Store to RAM Options** button that is found on the [Time Values](37-transient-stability-analysis-dialog-part3.md#time-values) sub-tab of the [Results from RAM](37-transient-stability-analysis-dialog-part3.md#results-from-ram) page), and you will also be able to [visualize Plot Charts](37-transient-stability-analysis-dialog-part2.md#plots) directly from the hard drive results.

When using the [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors), it can be reasonable to run a simulation which does not store any numeric results of the simulation. This is because when the goal is only to verify that all system performance criteria as described by the transient limit monitors are met, then the actual numerical results are not necessary.

Store Results to RAM

Check this box to store results using the [Save to RAM](#storage-to-ram) Options.

Store Results to Hard Drive

Check this box to store results using the [Save to Hard Drive](#storage-to-hard-drive) Options.

Save the Results stored in RAM in the PWB file

The user can select to just store the transient stability parameters, store the parameters results, or not store either the transient stability parameters or results in the \*.pwb file. Storing transient stability information in the \*.pwb file makes it convenient to open a case and run the transient stability analysis, but storing this information, especially the results, could significantly increase the size of the \*.pwb file. Auxiliary files can also be used for storing the parameters and results instead of, or in addition to, storing this information in the \*.pwb file.

Save Results Every n Time Steps

When writing results to RAM or the Hard Drive, specify the number of time steps after which results should be stored. If a value of 10 is entered then results will only be stored every 10 time steps. Note: this setting will NOT effect the use of [Generic Limit Monitors](#generic-limit-monitors) or [Transient Limit Monitors](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors) . The Generic Limit Monitors and Transient Limit Monitors are an integrated part of the numerical integration solution and are checked at every time step regardless of how frequently results are saved to RAM or the Hard Drive.

Do Not Combine RAM Results with Hard Drive Results

When designing plots and choosing values to include in plots, values can be plotted from both RAM and hard drive. If this box is checked, only the results stored in RAM will be shown and used as valid values to be plotted. Values stored in hard drive will be excluded.

Save the Min/Max Results stored to RAM in the PWB file

Check this box to save then Min/Max, Events, and Summary information in the PWB file even if not storing the Time Values to PWB.

---

<a id="storage-to-ram"></a>

## Storage to RAM

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultStorage_RAM.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultStorage_RAM.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results Storage page is found on the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog).

This section describes how to choose which results to store to RAM during the transient stability simulation. You may want to store results to RAM so that they can be viewed in the [Transient Stability Results: Time Values](37-transient-stability-analysis-dialog-part3.md#time-values). Be careful however because if too many results are stored you will run out of RAM causing the simulation to fail or generally slow down your computer. The Store to RAM Options mostly consist of a list of all the various objects in the model and a list of field which can be stored during the transient simulation. This is depicted in the figure below. Any information needed for a subplot's horizontal axis data is automatically stored to RAM.

![Transient Stability Dialog ResultStorage RAM](images/Transient_Stability_Dialog_ResultStorage_RAM.gif)

Tables of Devices

Results for Generators, Buses, Loads, Switched Shunts, Branches, DC Lines, Multi-Terminal DC Records, Multi-Terminal DC Converters, Areas, Zones, Interfaces, and Injection Groups can be stored during the transient stability analysis. Each type of object has a list of transient stability related parameters that can be stored. Toggling the appropriate field to *YES* for an object will store that parameter for the selected object. Some objects such as generators also have dynamic models associated with them for which dynamic states can be stored. For these you will see columns for **Machine States**, **Exciter States**, **Governor States**, etc... which can be set to *YES* to store those states. Each object also has a **Save All** field. If this field is set to *YES* for a particular object, all transient stability related fields (except dynamic states) will be stored for that particular object without having to set all of the fields to *YES* for all of the parameters. For dynamic states you can not use the Save All field and must toggle the specific state field instead.

Also note that any values which are set to be part of a plot series in a plot definition will automatically be stored to RAM

All results are presently stored in memory. This means that a memory limitation could be reached is storing a large number of results.

Save Results for Open Devices

Check this box to save results for devices that are currently open. It is possible that a device that is currently open could be closed during the transient stability analysis so this device should not be excluded from the results.

Set All NO

Click the **Set All NO** button to reset all fields regarding RAM storage for the present tab being viewed to *NO*.

Set All NO for All Types

Click the **Set All NO for All Types** button to reset all fields regarding RAM storage to *NO* for all object types.

Set Save All by Type...

Click this bus to bring up a dialog containing check-boxes which allows you to choose which device types to toggle the **Save All** paramter to *YES* for. There will also be check-boxes regarding the various dynamic model state fields.

Plotting

Transient stability results are usually interpreted with the assistance of some sort of plot. There can be a large amount of data to sort through and options on this page as well as the [Plots](37-transient-stability-analysis-dialog-part2.md#plots) page are designed to assist in setting up meaningful plots. Plot Definitions must be created in order to view a plot. The plot buttons contained on the Results to Save page assist in creating Plot Definitions outside of the Plots page. See the [Plots](37-transient-stability-analysis-dialog-part2.md#plots) page for more detailed information about Plot Definitions and plot parameters. Once options on the Results to Save page are used to create plots, the plot definitions will show up on the [Plots](37-transient-stability-analysis-dialog-part2.md#plots) page.

In order to make a plot, objects and fields to include in the plot must be specified. How many objects and fields are selected will determine which of the following buttons are enabled and how the plot will be designed. To select objects and fields for a plot, simply select cells in the appropriate device table that include the fields and objects to show on a plot.

For example, to plot all generator rotor angles on a single plot, go to the Generators tab and select all of the records under the Rotor Angle field. After selecting the objects and fields, click the appropriate plot button, as described below, to create the plot definition.

![Transient Stability Dialog Results to Save Plotting1](images/Transient_Stability_Dialog_Results_to_Save_Plotting1.gif)

As another example, to plot only the rotor angles and terminal MW value of only generators 1 and 2, go to the Generators tab. Move the MW Terminal field so that it is next to the Rotor Angle field. This can be done by using the [Display/Column Options dialog](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) or holding down the CTRL key and dragging a column to move it to a different place in the table. Select the records for generator 1 and 2 under both the Rotor Angle and MW Terminal fields. After selecting the objects and fields, click the appropriate plot button, as described below, to create the plot definition.

![Transient Stability Dialog Results to Save Plotting2](images/Transient_Stability_Dialog_Results_to_Save_Plotting2.gif)

![Transient Stability Dialog ResultStorage RAM Plot](images/Transient_Stability_Dialog_ResultStorage_RAM_Plot.gif)

Make Plot

This button is enabled when at least one object record for a transient stability field is selected. This option will create a plot definition with a single subplot with all selected objects and fields appearing on the same axis group.

Make Plot Group by Field

This button is enabled when more than one transient stability field is selected. This option will create a plot definition with a single subplot with a separate axis group for each of the selected fields. All selected objects will appear on a given axis group.

Make Plot Group by Object

This button is enabled when more than one transient stability object is selected. This option will create a plot definition with a single subplot with a separate axis group for each of the selected objects. All selected fields will appear on a given axis group.

---

<a id="storage-to-hard-drive"></a>

## Storage to Hard Drive

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultStorage_HardDrive.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultStorage_HardDrive.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results Storage page is found on the [Transient Stability Analysis dialog](#transient-stability-analysis-dialog).

This section describes how to choose which results to store to Hard Drive during the transient stability simulation. Results that are stored to Hard Drive can still be directly visualized using Simulator's [Plotting tools](37-transient-stability-analysis-dialog-part2.md#plots). The options are depicted in the figure below.

![Transient Stability Dialog ResultStorage HardDrive](images/Transient_Stability_Dialog_ResultStorage_HardDrive.gif)

Location

Specify the directory on your computer in which to store the results. For each [transient contingency](#simulation), one file will be written to this directory. The filename will be the name of the contingency with the \*.TSR file extension. When a transient stability simulation is started for a particular transient contingency, if a file already exists in this directory with the appropriate name then the file will be emptied and replaced with the results from the new stability run.

If this field is left blank, Simulator will attempt to save data in the same directory the case was loaded from. If a directory is specified but does not exist, Simulator will give you the option to create that directory or abort the run.

Because a large amount of data will be written to this file, it is best to not use a network drive which may cause some latency in writing results during the simulation. This latency can slow down the numerical simulation if the network drive is slow.

There will be log message warnings when parsing a TSR file to warn if objects in the TSR file do not exist in the present power flow case, but only 20 log messages will be written regarding objects that are not in the present case.

Two fields for a TSContingency object named ResultFilename and ResultDirectory were added in the May 17, 2023 patch of Simulator 23. By default these are blank and the existing behavior will remain which is that hard-drive results are stored to and read from the directory specified in the Hard Drive Result Storage options and all result files are expected to have the name of the TSContingency with the appropriate extension (TSR, AUX, image file format such as JPEG, and so on). This default behavior can now be overridden by specifying either a ResultFilename or ResultDirectory.

TSContingency ResultFilename field

Should not include any file extension, so if a value of MyFile.tsr is specified in this field, then the actual files written out would have names such as "MyFile.tsr.tsr" and "MyFile.tsr.aux". So do not include an extension in ResultFileName.

TCContingency ResultDirectory field

May be either an absolute path or a relative path. An empty string means the directory specified in the Save to Hard Drive Options is used. If this is a relative path, then it will be the path relative to the RSHD\_Directory path set with the Save to Hard Drive Options. If this is an absolute path it will be used directly.

Object Types to Include

A list of objects types for which transient stability results can be stored. All fields (including the dynamic states) will be stored for each object in the TSR file. The only filtering allowed presently is to limit the results by the [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) by checking the box **Only store every result for objects which meet the Area/Zone Filters**. Clicking the Edit Area/Zone Filters will open the [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) case information display.

Storage of States, Other Fields, and Input Fields

Specify how the states, other fields and input fields are stored in the Hard Drive for the objects. Selecting **Also store states for each object** will store all of the states for the objects. Selecting **Also store other fields for each object** will store the other fields with each object. Selecting **Also store input fields for each object** will store the inputs for the objects.

TSR File Archiving

Check the **Enable Auto-Archive of TSR Files** checkbox to save multiple copies of TSR files for the same contingencies. The names will be appended with a number indicator to distinguish the files. The **Maximum Number of Archive Files** value should be set to indicate how many archived files should be kept. When the maximum number of files has been archived, the first archived file will be overwritten and the archiving will continue from there overwriting subsequent files in the order in which they were created. If a file in the order has been deleted, that file will be created first. For example, assume that archive files with numbers 1, 2, 4, 5, and 6 exist. The next file to be created will be the file appended with 3.
