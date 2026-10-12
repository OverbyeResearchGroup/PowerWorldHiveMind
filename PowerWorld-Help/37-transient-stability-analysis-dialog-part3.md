---
title: "Transient Stability — Analysis Dialog (Part 3 of 3)"
part: "Transient Stability"
chapter_file: "37-transient-stability-analysis-dialog-part3.md"
topics: 11
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Transient Stability — Analysis Dialog (Part 3 of 3)

The Transient Stability Analysis dialog: simulation, options, plots, results and validation.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (11)**

- [Result Analysis Signal Modes](#result-analysis-signal-modes)
- [Result Analysis Mode](#result-analysis-mode)
- [Results from RAM](#results-from-ram)
- [Time Values](#time-values)
- [Transient Limit Monitors](#transient-limit-monitors)
- [Defining Transient Limit Monitors](#defining-transient-limit-monitors)
- [Transient Limit Monitors Violations](#transient-limit-monitors-violations)
- [States/Manual Control](#statesmanual-control)
- [Validation](#validation)
- [SMIB Eigenvalues](#smib-eigenvalues)
- [Simulating Multiple Contingencies](#simulating-multiple-contingencies)

---

<a id="result-analysis-signal-modes"></a>

## Result Analysis Signal Modes

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisSignalModes.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisSignalModes.htm)*

[A description of the theory of the calculation of the Transient Result Analyzer Modal Calculation is in a separate topic.](37-transient-stability-analysis-dialog-part2.md#modal-analysis-theory)

When performing results analysis on defined [Transient Stability Result Analaysis Time Windows](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window), with every signal being analyzed and PowerWorld will determine a trending line and a contribution of every mode to each signal, with the contribution described by a complex number. These values are summarized for all signals on the **Result Analyzer - Damping\\Signal Dmaping and Modes** portion of the Transient Stability Dialog.

When looking at all the signals, the display is filtered to show only the contingency chosen from the contingency drop-down shown in the red box below. In addition to make filtering by particular time windows easier, there is a display listing all time windows in the blue box below. By checking or unchecking particular time windows the list of signals is filtered. Each row in the table represents a particular field of a particular object and we call each of these rows a "TSResultAnalysisSignal". As you click on a row in the table of signals, a second case information display to the bottom left is updated to show you information about all the Modes and their contribution to the signal you're looking at. In addition if you **Auto** checkbox is checked just above the list of modes on this dialog then as you click on rows in the upper table the bottom right portion of the dialog will update a display showing you the raw data of the signal in blue (the actual results from transient stability) and the approximate reproduced signal in red.

![Transient Stability Dialog ResultAnalysisSignalModesAll](images/Transient_Stability_Dialog_ResultAnalysisSignalModesAll.png)

There are many fields which can be added to the [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) of signals. As with all case information displays you may configure the display to show many more columns than are added by default to the display. See the [Configuring Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) for more information about how to add those. Of special not with this display however are the following columns

Time Window Name

Name of the [Time Window](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window) for which the signal was calculated.

CTG Name

Name of the [Transient Contingency](37-transient-stability-analysis-dialog-part1.md#simulation) from which the transient results were obtained

Field

The field for the signal

Object

The object for the signal

Trend Line For Signal

There are 3 fields to show the A, B, C coefficients of the trend quadratic function.

Cost Function Value

This is a measure of how closely the approximated signal matches the actual signal. Sort by this to see which signals match the worse. If the plot in the bottom right looks reasonable accurate then you know that even the worse match is pretty good. If the plot in the bottom right looks bad, then you may need to change the Time Window definition to change the time window to not include discrete jumps or increase the maximum sample frequency to improve the match.

Undamped Modes Has

Value will show a YES if the undamped mode count is greater than 0

Undamped Modes Count

A count of the number of [modes](#result-analysis-mode) within the signal that meets the UndampMinHz, UndampDampPerc, and UndampMinRank as defined by the [Time Window](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window)

Modes by Sorted Magnitude

Provides information about the ModeMagAngle objects sorted by magnitude. Shows the Angle, Damping Ratio Percentage, Frequency, Lambda, Magnitude End, Magnitude, Mode Index, and Rank Percentage for every mode's contribution to this signal. The values are referred to as A, B, C, etc to represent the sort order.

Modes by Mode Index

Provides information about the ModeMagAngle objects sorted by magnitude. Shows the Angle, Damping Ratio Percentage, Frequency, Lambda, Magnitude End, Magnitude, Mode Index, and Rank Percentage for every mode's contribution to this signal. The values are referred to as 1, 2, 3, etc to represent the particular mode index.

Object Fields

There are various fields to show information about buses, areas, zones, and so forth for the object related to the signal.

Statistics

This folder contains the statistics which appear as default columns on the [Signal Statistics tab](37-transient-stability-analysis-dialog-part2.md#result-analysis-signal-statistics).

If you right-click on a particular Signal and choose Show Dialog you will see information about only one signal. This shows information about the Time Window at the top of the dialog as well as the Contingency, Object, and Field related to the Signal. After this is a list of contributions of each mode to the signal being shown. The contributions are called TSResultAnalysisModeMagAngle objects. The first columns shown is Mode Include Reproduced and as you toggle those fields between YES to NO it impacts which mode contributions are included in the reproduced signal visualized on the right. When including all the contributions the reproduced signal should reasonably match the Raw signal if the Modal Analysis has worked well.

![Transient Stability Dialog ResultAnalysisSignalModes](images/Transient_Stability_Dialog_ResultAnalysisSignalModes.png)

The columns shown with the contributions from each mode are as follows.

IncludeReproduced

Set to YES to Include this mode when calculating the reproduced signal from the modes and showing that in the user interface.

Magnitude (Mag)

Magnitude at Start Time for mode within Signal

Magnitude End (MagEnd)

Magnitude at End Time for mode within Signal

Angle

Angle for mode within Signal in degrees

Rank

This is the rank contribution of this mode to this signal based on the magnitude. It's based on the large of either Mag or MagEnd and is then normalized across all modes for this particular signal such that the summation of Rank values is 100.

Mode Frequency (Freq)

For Mode: Frequency of the mode in Hz

Mode Damping % (Damp)

The damping ratio percentage. This is 100 times the damping ratio which is equal to -100\*Lambda/sqrt(sqr(Lambda) + sqr(2\*pi\*Frequency))

Mode Lambda (Lambda)

Exponential term for the mode which represents the damping. Negative Lambda indicates positive damping

Mode Number (Number)

Number of the mode. Number as just assigned by the calculation tool in no particular order

To demonstrate how toggling the **IncludeReproduced** field results in the reproduction of the raw signal see the following example.

Notice in the example that the 0.000 Hz mode in Row 4 is undamped because it has a positive lambda and thus negative damping percentage. However, this mode is not really representing an oscillation but is instead just slightly bending the curve to match the signal of the time window chosen. This would be ignored when considering whether the overall signal is damped or not.

<table>
<tbody>
<tr class="odd">
<td><p> </p>
<p>Toggle all the IncludeReproduced to NO in this example</p>
<p>shows only the trend line of the signal.</p></td>
<td><p> </p>
<p>Now add in the 0.171 Hz signal from Row 1 which gives</p>
<p>the general shape of the signal only.</p></td>
</tr>
<tr class="even">
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisSignalReproduceTrend.png" alt="Transient Stability Dialog ResultAnalysisSignalReproduceTrend" /></td>
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisSignalReproduceTrendRow1.png" alt="Transient Stability Dialog ResultAnalysisSignalReproduceTrendRow1" /></td>
</tr>
<tr class="odd">
<td><p> </p>
<p>Now add in the 0.000 Hz signal in Row 2 which improves the match of the signal at the beginning of the signal</p></td>
<td><p> </p>
<p>Now add in the 0.000 Hz signal in Row 4 which improves the match of the signal at the end of the signal.</p></td>
</tr>
<tr class="even">
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisSignalReproduceTrendRow12.png" alt="Transient Stability Dialog ResultAnalysisSignalReproduceTrendRow12" /></td>
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisSignalReproduceTrendRow124.png" alt="Transient Stability Dialog ResultAnalysisSignalReproduceTrendRow124" /></td>
</tr>
<tr class="odd">
<td><p> </p>
<p>Finally add in the mode from Row 3 which includes the higher frequency 1.364 Hz oscillation. All these added together have reproduced our signal almost exactly.</p></td>
<td> </td>
</tr>
<tr class="even">
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisSignalReproduceTrendRow1243.png" alt="Transient Stability Dialog ResultAnalysisSignalReproduceTrendRow1243" /></td>
<td> </td>
</tr>
</tbody>
</table>

---

<a id="result-analysis-mode"></a>

## Result Analysis Mode

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisMode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisMode.htm)*

[A description of the theory of the calculation of the Transient Result Analyzer Modal Calculation is in a separate topic.](37-transient-stability-analysis-dialog-part2.md#modal-analysis-theory)

When performing results analysis on defined [Transient Stability Result Analaysis Time Windows](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window), PowerWorld will calculate the modes and the contribution of each mode to each signal as described later on this page. The list of modes that are calculated are found under the **Result Analyzer - Damping\\Modes** portion of the [Transient Stability dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

When looking at all the modes, the display is filtered to show only the contingency chosen from the contingency drop-down shown in the red box below. In addition to make filtering by particular time windows easier, there is a display listing all time windows in the blue box below. By checking or unchecking particular time windows the list of signals is filtered. Each row in the table represents one mode that has been calculated for a particular Time Window and Transient Contingnecy. We call each of these rows a "TSResultAnalysisMode". As you click on a row in the table of modes, a second case information display to the bottom left is updated to show you information about all the Signals and the contribution the selected mode to this signal. In addition as you click on rows in the upper table the bottom right portion of the dialog will update a display showing a compass plot of all the contributions of this mode to all signals that were studied.

Remember from the [theory of Modal Analysis](37-transient-stability-analysis-dialog-part2.md#modal-analysis-theory) that this contribution is a complex number with both a magnitude and angle. In the example image below you can see that there are groups of buses that have 180 degrees of separate between them which tells you that one group of signals is oscillating against the other group of signals. On the right you may also specify two options for the compass plot of the mode contributions

Sort Signals By

Specify whether the Magnitude or Rank is used to sort and display the contribution. The Compass plot will then be normalized based on the largest contribution of those being shown.

Signals to Show

A colors dot will be shown to represents each signal and the legend below the compass plot will list the signals that have the largest magnitude of contribution. Set this value to either All to show all signals, or set it to Top Count and specify an integer to choose to only show a specified number of colored dots on the compass plot.

![Transient Stability Dialog ResultAnalysisModeAll](images/Transient_Stability_Dialog_ResultAnalysisModeAll.png)

The columns shown with the contributions from each mode are as follows.

Time Window Name

Name of the [Time Window](37-transient-stability-analysis-dialog-part2.md#result-analysis-time-window) for which the mode was calculated.

CTG Name

Name of the [Transient Contingency](37-transient-stability-analysis-dialog-part1.md#simulation) from which the transient results were obtained

Frequency (Freq)

Frequency of the mode in Hz

Damping % (Damp)

The damping ratio percentage. This is 100 times the damping ratio and is equal to

![Transient Stability Dialog ResultAnalysisTheoryDampingRatioPerc 448x45](images/Transient_Stability_Dialog_ResultAnalysisTheoryDampingRatioPerc_448x45.png)

Lambda (Lambda)

Exponential term for the mode which represents the damping. Negative Lambda indicates positive damping

Number (Number)

Number of the mode. Number as just assigned by the calculation tool in no particular order

If you right-click on a particular Mode and choose Show Dialog you will see information about only one mode. This shows information about the Time Window at the top of the dialog as well as the Contingency, Mode Number, Frequency, Damping Ratio %, and Lambda. After this is a list of contributions of the mode to all the signals is shown. The contributions are called TSResultAnalysisModeMagAngle objects. On the bottom right of the dialog there will be a compass plot showing the contributions from this mode across signals which was described earlier in this help topic.

![Transient Stability Dialog ResultAnalysisMode](images/Transient_Stability_Dialog_ResultAnalysisMode.png)

The columns in the table of contributions are as follows

Magnitude (Mag)

Magnitude at Start Time for selected mode's contribution to the signal represents in the row

Magnitude End (MagEnd)

Magnitude at End Time for selected mode's contribution to the signal represents in the row

Angle

Angle in desgrees for selected mode's contribution to the signal represents in the row

Rank

This is the rank contribution of this mode to this signal based on the magnitude. It's based on the large of either Mag or MagEnd and is then normalized across all modes for this particular signal such that the summation of Rank values is 100.

Signal Field

The field that the signal result represents

Signal Object, and many other object related fields for Area, Zone, etc.

The object that the signal result represents

---

<a id="results-from-ram"></a>

## Results from RAM

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results from RAM page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). This page provides a summary of various results from a transient stability analysis run. The results shown here are currently what is being stored in RAM.

![Transient Stability Dialog Results](images/Transient_Stability_Dialog_Results.gif)

The Results from RAM page is divided into several sub-tabs:

Time Values

This page contains a table of all results selected with [Results to Store to RAM](37-transient-stability-analysis-dialog-part1.md#results-storage). For details on this display see [Transient Stability Results: Time Values](#time-values).

Minimum/Maximum Values

The Minimum/Maximum Values tab contains two lists: one of generators and one of buses. Each list contains summary information for the objects. The bus list contains information about the maximum and minimum voltage values and time. The generator list contains maximum and minimum information about angles and frequency. Note that when the **Process Contingencies** option is set to *One Contingency at a Time*, the list will only apply to the presently active contingency chosen from the **For Contingency** drop-down menu. (See [Transient Stability: Running Multiple Contingencies](#simulating-multiple-contingencies).)

Summary

Time Solution Started

Time that the transient stability analysis started.

Time to Solve (Seconds)

Amount of computing time needed to solve the analysis.

Maximum Angle Difference (Deg)

Maximum angle difference between any two generator rotors at any time during the analysis.

Time of Max. Angle Diff. (Seconds)

Analysis time at which the maximum angle difference occurred.

Newton Solution Results

This contains information about the Newton Solutions needed during the Simulation

Events

![Transient Stability Events](images/Transient_Stability_Events.gif)

The Events tab will show a list of events which occurred during the stability run.

The Events can be filter by *Event Levels* AND by *Object Types*. This facilitates the search of particular events easier to the user.

The user-defined transient contingency elements will be listed in the event list. In addition, any actions caused by the action of a relay or motor tripping action of one of the stability models may be listed as an event. An event will be shown id the network solution failed during the simulation.

Solution Details

This page provides some summary information about the Newton solution results.

---

<a id="time-values"></a>

## Time Values

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results_TimeValues.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Results_TimeValues.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Time Values are found as a sub-tab under he Results from RAM page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). The table lists values for each of the selected objects and fields as columns and the various time steps as rows. Note that for time-step at which an event (such as a fault) occurs, there may be multiple time steps listed showing the same time. The first listed time step will represent the system state immediately before that time (T-) and the second listed time step will represent the system state immediately after the events occur. There are also options along the left to choose which fields to show as columns as well a column filtering options to use an advanced filter to limit the columns. Finally there is an option to specify whether columns should be sorted first by *Object then Field* or by *Field then Object*. This is all depicted in the following image.

Note that when the **Process Contingencies** option is set to *One Contingency at a Time*, the list will only apply to the presently active contingency chosen from the **For Contingency** drop-down menu. (See [Transient Stability: Running Multiple Contingencies](#simulating-multiple-contingencies).)

Load from Hard Drive File into RAM results specified by Store to RAM Options

Click this button to cause Simulator to go to the file specified in **[Save to Hard Drive Options](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive)** and load in the values specified by the **[Store to RAM Options](37-transient-stability-analysis-dialog-part1.md#storage-to-ram)**. These results will be loaded into RAM and shown in the Time Values tables even though results were originally stored to hard drive. If processing multiple contingencies, only the results for the presently selected contingency will be loaded into RAM.

![Transient Stability Dialog ResultsTimeValues RAM](images/Transient_Stability_Dialog_ResultsTimeValues_RAM.gif)

Clear Time Values from RAM

Clicking this button allows the clearing of the Time Values results from RAM. Results are only cleared for the presently selected contingency.

Clear Min/Max Values, Summary, Events, and/or Solution Details from RAM

Clicking this button opens a dialog that allows the clearing of any of the specified types of results from RAM. Time Values are cleared from their own button described above. Results are only cleared for the presently selected contingency.

---

<a id="transient-limit-monitors"></a>

## Transient Limit Monitors

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Limit Monitors page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

When running a transient stability simulation, the actual numerical results and plotting is useful, but sometimes what you really want to know is if and when any particular Operating Standards were violated. For example, tn the Western United States there are particular standards for voltage dips and frequency deviations referred to as WECC Category B and WECC Category C standards. You can add these standards by right clicking on the table and going to the Transient Limit Monitor records. Also the WECC 2016 Fault Clearing and No Fault Standard Monitors can be added in the same manner.

You can think of this similarly to how Limit Monitoring works in traditional power flow based contingency analysis. In traditional contingency analysis we do not report the voltage at every bus and the flow on every line during each contingency. Instead we only report violations of limits, which greatly reduces the amount of output data created by the tool.

In order to provide the ability to flag violations of these standards, PowerWorld has created an object called a *Transient Limit Monitor* which provides a great deal of flexibility for allowing the simulation to automatically monitor for these types of standards without requiring us to store the entire trace of each monitored quantity. When creating a transient stability monitor, you choose a field for a particular type of object and then build a description of what is considered a limit violation.

Defining Transient Limit Monitors Tab

To define Transient Limit Monitors, look on the Transient Stability dialog under Transient Limit Monitors and choose the Transient Limit Monitors option. When choosing this a case information display listing the transient limit monitors will be shown. For more information see [Transient Stability : Defining Transient Limit Monitors](#defining-transient-limit-monitors). The *Re-evaluate to Get Limit Monitor Violations* button is use to re-evaluate the results stored to get the transient limit monitor violations. First it will look at the results stored in RAM and then, if no results are found, look into the Hard Drive \*.tsr file. If the button is press under Multiple Contingencies mode the it will re-evaluate all the contingencies results.

Viewing Transient Limit Monitor Violations Tab

While running a transient stability simulation, violations of the transient limit monitors defined will be recorded and listed under the Transient Limit Monitors\\Monitor Violations table on the Transient Stability Analysis Dialog. Monitor Violations will be designated by which transient contingency caused them so that when [running multiple transient contingencies](#simulating-multiple-contingencies) you will be able to see which contingency caused the violation. It may be feasible for you to abandon storing all the transient stability numerical results and instead only store the violations of the limit monitors. If violations are found you can then revisit the run and store appropriate results. For more information on monitor violations see[Transient Stability : Transient Limit Monitors Violations](#transient-limit-monitors-violations).

Limit Logic Tab

An object to combine Transient Limit Monitors in a logic expression. The object will provide a Logic Variable identifier with a Transient Limit Monitor to include that monitor in an expression. A limit Logic object is created with a Logic expression that is a combination of Logic Variables *AND*, *OR*, and *NOT* that are supported with appropriate parentheses. A Logic Variable need to be assign to a Transient Limit Monitor at the Logic Variable column in the Transient Limit Monitors Tab, then in the Limit Tab under the Logic column write the wanted Logic expression.

The Limit Logic violations will report objects that meet the Logic expression at any point during the transient stability run. There is no time component to the logic. The Limit Logic expression should only include Transient Limit Monitors of the same object type.

---

<a id="defining-transient-limit-monitors"></a>

## Defining Transient Limit Monitors

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors_Define.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors_Define.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Limit Monitors page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

When inserting a new transient limit monitor you are presented with the following dialog. This gives you great flexibility in defining monitors for the various values which can be recorded in a transient stability run. Note that there are some very simple [Generic Limit Monitors](37-transient-stability-analysis-dialog-part1.md#generic-limit-monitors) for synchronous machines which are define as part of the Transient Stability options that may also be of use.

![Transient Stability Dialog TransientLimitMonitorDialog](images/Transient_Stability_Dialog_TransientLimitMonitorDialog.gif)

In the top portion of the dialog you first give the transient limit monitor a name. There is then an option to make a transient limit monitor **Active** or not. Below the middle of the dialog there is the Action To Take options: **Log Violation Only**, **Abort Simulation** or **Trip (Open) Device**. The **Log Violation Only** will show the violation only in the message log. The **Abort Simulation** will abort simulation at a specified time after a violation of the monitor occurs. The **Trip (Open) Device** will option to trip/open a device" if a monitoring violation occurs (this works for Buses, AC Lines, Generators, Loads, and DC Lines). There is also a choice for **Maximum number of violations of this limit monitor** to store. This is needed so that too many limit violations of the same limit monitor are not created. If you know the lowest 100 bus frequencies, you don't need any more than that.

The option **Maximum Sort Field** was Added in Version 23 to a user to specify which violations to keep. Prior to Simulator Version 23, the first 100 violations in time-order would be kept and after the **Maximum number of violations of this limit monitor** was reached no additional [TSLimitViolations](#transient-limit-monitors-violations) would be stored. The **Maximum Sort Field** gives 5 options to specify which violations should be kept. The options are the following 5 fields stored with the [TSLimitViolation](#transient-limit-monitors-violations): *ValueTime*, *ValueStartTime*, *ValueExtremeTime*, *ValueExtreme*, or *ValueExtremeConv*. When deciding which TSLimitViolation objects to create once the **MaxViolStore** count is reached, this sort field determines which violations to keep. The default choice is *ValueTime* which is the time at which all conditions for a violation to be recorded was met and thus our old default of the first violations in time-order. We expect that the *ValueExtreme* and *ValueExtremeConv* will also b used extensively as these choices will record as a violation the signals that have the extreme deviation from the **Limit Value** during the simulation.

The **Categories** input is a comma-separated list of user specified category names. Categories determine which Transient Limit Monitors are applied to each contingency. See the [Contingency Category](21-contingency-analysis-overview-and-records.md#contingency-category) topic for more information.

There are then choices to specify the **device type** and a **filter** which together will determine all the objects which are ultimately monitored by the transient limit monitor. Note that a decision regarding which objects meet the filter will be done at the start of a stability simulation based on the steady state values of the power system. You then specify which **field** of the device type will be monitored.

The top portion of the dialog describes which particular object/field pair traces are going to be monitored. The bottom portion of the dialog will define what shape of the trace will be considered a limit violation. For the basic limit monitor you specify three values: **Limit Value, Limit Duration**, and **Limit Type**. These choices work together to determine what is considered a violation. Typically limit types are *Lower* and a trace will be considered violated if the value is below the Limit Value for a duration specified by Limit Duration. For a *Upper* limit type, then it must be above the Limit Value instead. The choice for **Meaning of the values specified** affect how the Limit Value and values specified for special triggers discussed shortly are interpreted. The first choice is Actual Value which simply means the limit value represents the exact numerical value considered a violation. The other choices are based on a deviation from the initial steady state value or a percent or percent deviation from the initial value. As an example, for a system with a 60 Hz nominal frequency, the following are equivalent: \[Actual value = 59.6 Hz\] and \[Deviation from initial value = -0.4 Hz\]. Similarly, when monitoring a voltage the following are equivalent: \[Percent of initial value = 70%\] and \[Percent deviation from initial value = -30%\]. Finally there is a option **ABS: After using meaning, take absolute value**, which will take the absolute value of the value.

The check-box option for **Cumulative Time** was added in Version 22, build on September 28, 2022. Normally when **Cumulative Time** is not checked, if a signal drops below the **Limit Value** threshold briefly but does not stay below for the full **Limit Duration**, then immediately upon moving back on the good side of the **Limit Value** the timer is reset and the signal will need to be violated the **Limit Value**for an additional full **Limit Duration**. When choosing **Cumulative Time**, then the timer is not reset and a signal is considered violated if the cumulative time during the simulation for which the signal is violated exceeds the **Limit Duration**. As an example, if **Limit Duration** = 0.15 seconds, when using **Cumulative Time**, if a signal drops below a low limit for 0.1 seconds, swings back above for a while and then drops below again for an additional 0.05 seconds, it would be considered to have violation the 0.15 **Cumulative LImit Duration**.

When to Monitor

By default the transient limit monitoring does not start until after the last user-specified contingency event occurs. This is done because values such as voltage will obviously be violating during a bus fault (they'll be zero\!), so what you really want to know is whether the voltage is below a value for a specified duration after the fault clears. To change this default behavior, there are also special options available by clicking on **When to Monitor** tab of this dialog. These are shown in the dialog below. The values specified here will obey the choice for **Meaning of the values** specified discussed above.

The settings regarding the Time to Begin Checking are the same options as present for the [Global Transient Result Options](37-transient-stability-analysis-dialog-part1.md#result-options). Setting these to default will just use those global settings, or you can override these settings for a specific Transient Limit Monitor. You may also configured when to stop checking a particular Limit Monitor.

![Transient Stability Dialog TransientLimitMonitorDialogTriggers](images/Transient_Stability_Dialog_TransientLimitMonitorDialogTriggers.gif)

Built-In Transient Limit Monitors for WECC Standards

WECC criteria changed in 2016 and 5 built-in Transient Limit Monitor definitions were created to describe these signal requirements. These can be inserted going to the Transient Limit Monitors case information display choosing the **Records** menu dropdown from the case information toolbar and then choosing the appropriate option for **Build WECC 2016 Fault Clearing Standard Monitors** or **Build WECC 2016 No Fault Standard Monitors**. Note that by default all these 2016 standard monitors are always inserted into a new power system case. The standards are initially marked as Active = NO however so they must be set to Active = YES in order to use them.

The **WECC 2016 Fault Clearing Standard Monitors** create the following transient limit monitors.

  - WECC 2016 Fault WR1 1.3

  - WECC 2016 Fault WR1 1.4 Part 1

  - WECC 2016 Fault WR1 1.4 Part 2

The **WECC 2016 No Fault Standard Monitors** create the following transient limit monitors.

  - WECC 2016 No Fault WR1 1.5 Part 1

  - WECC 2016 No Fault WR1 1.5 Part 2

For Studies done before 2016, Simulator has built in the ability to automatically insert transient limit monitors which represent WECC Category B and WECC Category C standards. This can be inserted going to the Transient Limit Monitors case information display choosing the **Records** menu dropdown from the case information toolbar and then choosing the appropriate option for **Build WECC Pre-2016 Category B Standard Monitors** or **Build WECC Pre-2016 Category C Standard Monitors**.

The WECC Category B Standards create four transient limit monitors.

  - *WECC Category B Voltage Dip for Non-Load Buses* will monitor all non-load buses for any voltage dip of 30% below the initial voltage value at any time.
  - *WECC Category B Voltage Dip for Load Bus* will monitor all load buses for a voltage dip of 25% below the initial voltage at any time.
  - *WECC Category B Voltage Dip for Load Bus Duration* will monitor all load buses for a voltage dip of 20% below the initial voltage for a duration of 0.3333 seconds (20 cycles) and the dialog is shown above.
  - *WECC Category B Frequency* will monitor all load buses for a frequency dip below 59.6 Hz for a duration of 0.10 seconds (6 cycles) and the dialog is shown to the right as an example.

The WECC Category C Standards create three transient limit monitors.

  - *WECC Category C Voltage Dip Any Bus* will monitor all buses for a voltage dip of 30% below the initial voltage at any time.
  - *WECC Category C Voltage Dip Any Bus Duration* will monitor all buses for a voltage dip of 20% below the initial voltage for a duration of 0.6667 seconds (40 cycles).
  - *WECC Category C Frequency* will monitor all load buses for a frequency dip below 59.0 Hz for a duration of 0.10 seconds (6 cycles).

---

<a id="transient-limit-monitors-violations"></a>

## Transient Limit Monitors Violations

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors_Violations.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Transient_Limit_Monitors_Violations.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Limit Monitors page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

As a transient stability run is processed, any violations of the Transient Limit Monitors will be stored as a monitor violation and can be seen in the Monitor Violations table. An example is shown in the following case information display. Note that there is an option in **the Records Menu** for this object to **Make a New Plot**. Choosing to make a new plot will automatically create a new plot definition on the [Plot Designer](37-transient-stability-analysis-dialog-part2.md#plot-designer) portion of the dialog.

![Transient Stability Dialog TransientLimitMonitorViolations](images/Transient_Stability_Dialog_TransientLimitMonitorViolations.gif)

The key fields for the Monitor Violations will be the *Limit Monitor Name*, *Transient Contingency Name*, and the identity of the *violated device*. In addition to these keys, up to four additional points will be reported. Each of these four points will be represented by a *value* and a *time of value* representing the y-x point of the trace for that point. This gives up to 8 additional values. The four points are depicted in the following figure.

![Transient Stability Dialog TransientLimitMonitorExplain](images/Transient_Stability_Dialog_TransientLimitMonitorExplain.gif)

A description of the four points are as follows.

  - Point A represents the initial time at which the trace has violated the Limit Value. When processing the transient stability run, a monitor violation will not be generated at the point but the trace will start to be tracked. Also note that as soon as the trace no longer violates the limit value, point A will essentially be reset.
  - Once a Point A has been encountered and the trace is being tracked, a value/time pair for Point B will be maintained as part of the result to indicate when the most extreme violation of the limit value occurs. Note that point B may occur before or after point C depending on the shape of the trace.
  - Point C represents the time at which the trace completely violates the limit monitoring. At this point the limit value has been violated for the appropriate limit duration. Once this violation occurs then a Transient Limit Monitor Violation object will be generated for the results. Points A and B will be stored at this point as well, although point B may be modified if the trace continues to get worse. If the limit duration is zero, then point C and point A are the same point.
  - After the violation occurs, the tracking of the trace will continue to see if at a later time during the simulation the value no longer violates the Limit Value. If this occurs then a Point D will also be stored with the monitor violation object. This provides information about how long the value was ultimately violated so that you know if you almost met the standard. For instance if you have a limit duration of 0.3333 seconds (20 cycles) you might want to know the difference between a violation that lasted 0.34 seconds and one that lasted 1.2 seconds.

---

<a id="statesmanual-control"></a>

## States/Manual Control

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_States_Manual_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_States_Manual_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The States/Manual Control page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). This page provides a means to manually control a transient stability run and view generator and bus states at each step of the process. It will be very helpful in determine which part of the system is causing an instability. It is also helpful to look at initial State Limit Violations as described below. Also note that when you first open the Transient Stability Dialog, Simulator does not immediately initialize the transient stability simulation. This initialization obviously occurs when you start simulation, but it also occurs when you switch to either the States/Manual Control or the [SMIB Eigenvalues](#smib-eigenvalues).

One particular good use of this section is to sort by the *Derivative* column under the All States sub-tab to ensure of that the state derivatives are all near zero at the initialized system state. Note: many induction motor states will never be exactly zero because their initial states must be determined by an iterative process, but in general derivatives should be very near zero. Another good use of this section is to look at the initial condition State Limit Violations.

![Transient Stability Dialog States Manual Control](images/Transient_Stability_Dialog_States_Manual_Control.gif)

Reset to Start Time

Click this button to reset the simulation back to the start time as specified on the [Simulation Control](37-transient-stability-analysis-dialog-part1.md#simulation) page.

Run Until Specified Time

Click this button to run to the specified **Run Until Time**. The Run Until Time should be set in seconds. The simulation is run from the present time to this specified time. The current time is shown in the **Simulation Status** field that is displayed at the top of the [Transient Stability Analysis dialog.](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) The Run Until Time must be later than the present simulation time.

Do Specified Number of Timestep(s)

Click this button to run the specified **Number of Timesteps to Do**. The simulation starts at the present time and does the number of timesteps. The current time is shown in the Simulation Status field that is displayed at the top of the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

Transfer Present State to Power Flow

Click this button to transfer the present state resulting from the transient stability analysis to the power flow model. The present state is not transferred to the power flow model when running the transient stability analysis when not using the manual mode.

Restore Power Flow Model

Click this button to restore the power flow model to the pre-transient stability analysis state. This option can be used when the transient stability state information has been transferred to the power flow model.

Save Time Snapshot

Click this button to save the power flow model to file with the present transient stability results. Transient stability results will only be saved if choosing a file type of either \*.pwb or \*.aux. If the transient stability state has been transferred to the power flow model, the power flow model is first restored to the pre-transient stability analysis state before saving.

All States

This sub-tab contains a list of every state in the dynamic simulation. The *Value* of each state is listed along with the *Derivative* of the state.

State Limit Violations

This sub-tab contains a list of all the state limit violations in the initialized system. This State Limit Violations are also organized into lists of All, Modified, and Not Modified. The list of Modified State Limit Violations shows at the initial condition a list of violations for which the limits have been temporarily changes according to the [Option for Handling of Initial Limit Violations](37-transient-stability-analysis-dialog-part1.md#power-system-model).

Generators and Buses

This sub-tab contains a list of all the present terminal values for the generators and buses. These are the same values you can see on the [Transient Stability Data: Object Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs) and include fields such as Field Voltage, Rotor Angle, Accelerating MW, etc...

In the Generators sub-tab, in addition to getting all the present terminal values for the generators by right-clicking on the Generator entries and choosing Save Two Bus Equivalent from the local menu, you can save the Two Bus system from the selected bus to an infinite bus. When writing out this two bus equivalent model, generators automatically set to AVR = NO In addition when saving the Two Bus equivalent it can save a GENCLS model on the slack bus saved to represent an infinite bus.

Transient Stability YBus

This sub-tab displays the transient stability Y-Bus following the last transient stability analysis timestep.

GIC GMatrix

The GMatrix page shows the entries in the G (conductance) matrix. The entries are for the parallel combination of all three phases.

Two Bus Equivalents

This let you save the Two Bus system from the selected buses to an infinite bus. When writing out this two bus equivalent model, generators automatically set to AVR = NO. In addition when saving the Two Bus equivalent it can save a GENCLS model on the slack bus saved to represent an infinite bus. You can select the file format (PowerWorld, PSSE or PSLF) to save the equivalent. Also a *Directory Location* can be specified to save the equivalents and also a *Playback File Name* can be specified. The equivalent can include the cross compound generators at a bus by checking the specified check box. The button *Save All Selected Two Bus Equivalents in Desired Formats* will automatically save the buses set to Yes in the *Save Two Bus Equivalent* column in the table.

---

<a id="validation"></a>

## Validation

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

Because a transient stability simulation is a numerical integration of a set of equations, the numerical integration imposes some restrictions on the input data in order to prevent numerical instability. Numerical instability is instability caused not by the actual power system but by the limitations of the computer algorithms used to perform numerical integration. Simulator provides the ability to both validate the model and auto-correct many of the input values. These features are available on the Validation portion of the Transient Stability Dialog as shown in the following figure. Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Running both of these features will generate a list of validation errors, validation warnings, and informational messages. Validation errors are typically related to time constants or machine reactance values as discussed below. Validation errors may also appear for models which have been read in but are not supported by the numerical integration. Validation warnings will appear for things such as a generator model which has no machine model, a generator connected to a bus with zero voltage, or for parameters outside of their expected range. Information messages also appear for parameters outside of the expected range, and when using the Auto Correction tools messages regarding changes to input values will appear.

![Transient Stability Dialog Validation](images/Transient_Stability_Dialog_Validation.gif)

Unsupported Models

Determine how to proceed if an unsupported transient stability model is defined for any element. An error will prevent the transient stability analysis from running and provide a message. A warning will set the status of any unsupported models to inactive and provide a message. No error or warning will set the status of any unsupported models to inactive but provide no message.

Minimum time constant size as multiple of time step

For limits on time constants as discussed below, this the multiple of the time step used in the validation routines.

Time of Last Validation

This shows the time that the last validation check was run. This time is either from the last time that the process was run manually or part of the check done at the beginning of a transient stability analysis run.

Errors: and Warnings:

Provides a count of the number of errors and warnings that have been found. Errors will prevent the transient stability analysis from being run.

Summary Tables

This page is divided into three sub-tabs: **Validation Errors**, **Validation Warnings**, and **Informational Messages**. The **Validation Errors** page provides a list of any objects that have errors and provides a description of the error. Any errors will prevent the transient stability analysis from being run. The **Validation Warnings** page also provides a list of any objects that have problems and provides a description of the error. The difference is that warnings are not considered to be severe enough to prevent the transient stability analysis from being run. The **Informational Messages** page lists objects and messages about any errors or warnings that have been auto-corrected by the software.

Common Validation Messages

Minimum time constant size as multiple of time step

The most common limitations are on time constants in the various dynamic models. There are several common restrictions on a time constant. For a simple integration block \[1/(sT)\], the time constant must be greater than a specified multiple of the integration time step and cannot be zero.

The second common type of restriction on a time constant, such as for a filter block \[1/(1+sT)\], is similar except that it also allows the time step to be zero. If the time step is zero then the filter block is ignored in the integration and results in an ignored state as discussed in [Transient Stability Numerical Integration](36-transient-stability-overview-and-data-part2.md#integration-techniques).

A third common type of restriction applies across two different time constants such as for a lead-lag block \[(1+sT1)/(1+sT2)\]. For a lead-lag block the denominator time constant must be greater than a multiple of the time step. It can also be zero, but if it is zero, then the causality requires that the numerator’s time constant also be zfero.

Model validation like this must be built into the software throughout to avoid numerical instability; or as in the case of violating causality, we must avoid breaking fundamental laws of physics. For Simulator our testing has shown that for most model time steps must be at least 2-4 times the integration time step when using our 2nd order Runga-Kutta numerical integration technique.

Machine Model Reactance Validation

Another set of data which should be validated is related to the various reactance values of synchronous machine models. These reactance values are specified on the d-axis and q-axis and are referred to as synchronous reactance (Xd and Xq), transient reactance (Xdp and Xqp), subtransient reactance (Xdpp and Xqpp), and leakage reactance (Xl). In order for the equations which model the machine to be numerically stable, the reactance must obey the following relationships: \[Xl\>Xqpp\>Xqp\>Xq\] and \[Xl\>Xdpp\>Xdp\>Xd\]. A violation of any of these relationships can cause numerical instability and also just fundamentally does not make sense. Despite this, these types of errors are very common.

When encountering models which do not obey these relationships, PowerWorld Simulator will perform the following error checking, and when using auto-correction will make the following changes to the input data.

if Xqp \> Xq then Xqp = 0.8\*Xq

if Xdp \> Xd then Xdp = 0.8\*Xd

if Xqpp \> Xqp then Xqpp = 0.8\*Xqp

if Xdpp \> Xdp then Xdpp = 0.8\*Xdp

if Xl \> Xqpp then Xl = 0.8\*Xqpp

if Xl \> Xdpp then Xl = 0.8\*Xdpp

As a reminder though, running the auto-correction in Simulator will permanently change your input data.

Here is the list of the complete validation Parameter Checks:

\-[Areas](52-additional-linked-topics-part2.md#transient-stability-analysis-areas-validation-parameter-check)

\-[Generator Machine Models](52-additional-linked-topics-part2.md#transient-stability-analysis-generator-machines-models-validation-parameter-check)

\-[Generator Other Models](52-additional-linked-topics-part2.md#transient-stability-analysis-generator-other-models-validation-parameter-check)

\-[Exciters](52-additional-linked-topics-part2.md#transient-stability-analysis-exciters-validation-parameter-check)

\-[Governors](52-additional-linked-topics-part2.md#transient-stability-analysis-governors-validation-parameter-check)

\-[Stabilizers](52-additional-linked-topics-part2.md#transient-stability-analysis-stabilizers-validation-parameter-check)

\-[Load Characteristics](52-additional-linked-topics-part2.md#transient-stability-analysis-load-characteristics-validation-parameter-check)

\-[Line Relay](52-additional-linked-topics-part2.md#transient-stability-analysis-line-relays-validation-parameter-check)

\-[Switched Shunts](52-additional-linked-topics-part2.md#transient-stability-analysis-switched-shunts-validation-parameter-check)

\-[Line Shunts](52-additional-linked-topics-part2.md#transient-stability-analysis-line-shunts-validation-parameter-check)

Note: When validating stability data, the validation will also validate models which are out-of-service, but can be closed in during the simulation. An example of this would be the induction motor models which include Generator Machine Models MOTOR1, CIMTR1, CIMTR2, etc., and Load Characteristic models CIM5 and CIM6.

---

<a id="smib-eigenvalues"></a>

## SMIB Eigenvalues

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_SMIB.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_SMIB.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SMIB Eigenvalues are found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

The Single Machine Infinite Bus (SMIB) Eigenvalue Analysis is another model error checking tool which was added to Simulator. In PowerWorld's own testing, this has proven invaluable while performing model data input checking. The SMIB eigenvalue tool internally builds a dynamic model of one generator connected to an infinite bus. All of that generator's dynamic models (machine model, exciter, governor, and stabilizer) are included in this model. A linear matrix of all the dynamic states is constructed at the steady state solution and eigenvalue and eigenvector analysis is run on this matrix.

These features are available on the SMIB Eigenvalues portion of the Transient Stability Dialog. To generate these results, click on the **Run SMIB Eigen Analysis** button. After running the SMIB Eigen Analysis, it is very useful to sort the results descending by the Max Eigenvalue column to show any positive eigenvalues (as shown in the first figure below), or to sort ascending by Min EigenValue to show negative eigenvalues with a large magnitude (as shown in the second figure below). Positive eigenvalues represent potentially unstable system states, while very large negative eigenvalues represent extremely fast system states which can cause numerical instability. Often times the large negative eigenvalues will be caused by particular exciter models such as the EXST1\_GE and REXS models which contain extremely fast feedback loops. The particular models require special consideration in the numeric integration algorithm because of this and are discussed more in the [Transient Stability Numerical Integration](36-transient-stability-overview-and-data-part2.md#integration-techniques) topic regarding sub-interval integration.

![Transient Stability Dialog SMIB](images/Transient_Stability_Dialog_SMIB.gif)

![Transient Stability Dialog SMIB2](images/Transient_Stability_Dialog_SMIB2.gif)

In addition to getting the eigenvalue information by right-clicking on the SMIB entries and choosing Show SMIB dialog from the local menu, you can open a dialog which shows you the A matrix and the details regarding the eigenvalues and participation factors determined from the eigenvector analysis. The participation factors indicate which particular system states are most contributing to the particular eigenvalue. The following shows an example of the Eigenvalues for one of the generators which had a positive eigenvalue.

![Transient Stability Dialog SMIBDialog](images/Transient_Stability_Dialog_SMIBDialog.gif)

In some testing this small positive eigenvalue always appeared for these hydro power plants. When looking at the eigenvector analysis though it pointed us toward looking at the PI feedback look in the PIDGOV governor model. In looking at the input data, it was seen that the Rperm (droop) of those governors had a negative value which ultimately leads to an unstable governor. In this manner it validated the SMIB tool as correctly showing the input data which led to the positive eigenvalue.

Also by right-clicking on the SMIB entries and choosing Save Two Bus Equivalent from the local menu, you can save the Two Bus system from the selected bus to an infinite bus. When writing out this two bus equivalent model, generators automatically set to AVR = NO In addition when saving the Two Bus equivalent it can save a GENCLS model on the slack bus saved to represent an infinite bus.

---

<a id="simulating-multiple-contingencies"></a>

## Simulating Multiple Contingencies

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Multiple_Contingencies.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Multiple_Contingencies.htm)*

Most of the help documentation discusses how [Transient Stability Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) functions when you are simulating only a single transient contingency event. When changing the **Process Contingencies** option to *Multiple Contingencies* instead, the dialog will change in small ways throughout. This topic discusses how the dialog behaves differently when running multiple contingencies.

The ultimate goal of the transient stability tool is to run multiple potential transient contingencies to determine if any violations of any standards has occurred. When running multiple contingencies, our design goal was to make a transient stability run very similar to running a contingency analysis run using repeated power flow solutions. The transient stability interface has been designed to provide the ability to simulate and interact with multiple stability runs simultaneously. Obviously the speed of such a simulation will be much slower than for contingency analysis, but the goal for the tool should be to emulate the contingency analysis environment. These sections discuss three topics related to achieving this goal: user interface implications, data storage, and the use of transient limit monitors.

Using a Power Flow Contingency to modify the Initial Condition for Multiple Contingencies ( Added in version 24 )

Each TSContingency may assign a field for PowerFlowContingency which specifies a [Power Flow Contingency](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) that represents the initial condition for the Transient Contingency simulation.

![Transient Stability Dialog Simulation Control](images/Transient_Stability_Dialog_Simulation_Control.png)

General User Interface Changes

When choosing to process multiple contingencies, the [Simulation](37-transient-stability-analysis-dialog-part1.md#simulation) portion of the Transient Stability dialog into a form which looks very similar to PowerWorld's existing contingency analysis tool. At the top will be a list of the transient contingency definitions with columns for the Start Time, End Time, Cycles for Step, and Time Step. When you select a particular transient contingency from this list, the list at the bottom of the dialog will show the particular elements which are part of the selected transient contingency. This is shown in the figure below.

![Transient Stability Dialog MultipleContingencies 969x464](images/Transient_Stability_Dialog_MultipleContingencies_969x464.gif)

There are 3 fields to indicate if the contigency is Solved, Processed and the Reason Not Solved:

1\. Processed: This will say YES if the transient contingency solution was attempted

2\. Solved: This will say YES only if the transient contingency solution was run and successfully finished

3\. Reason Not Solved: When Solved = NO, this will be a string indicating why the solution was not finished

Also note that the [States/Manual Control](#statesmanual-control) portion of the dialog is removed. The assumption is that you will not want to manually step through a stability run a few time steps at a time if you're running multiple transient contingencies. The [Plots](37-transient-stability-analysis-dialog-part2.md#plots) and [Results](#results-from-ram) (for viewing tabular result) are changed when interpreting multiple contingency analysis runs. These will be discussed shortly.

Other portions of the dialog have very few changes. The [Options](37-transient-stability-analysis-dialog-part1.md#options) do not change at all and will apply to all transient contingencies. The [Results Storage](37-transient-stability-analysis-dialog-part1.md#results-storage) will also apply to all transient contingencies. [Validation](#validation) and [SMIB Eigenvalues](#smib-eigenvalues) only apply to the initial steady state system so they will also not change. [Transient Limit Monitors](#transient-limit-monitors) do not change because they apply to all contingencies and each of the Transient Limit Violations always reference a particular transient contingency.

Plots for Multiple Contingency Results

The Plots portion of the Transient Stability dialog changes slightly when processing multiple contingency results. By default, a dropdown allows you to choose for which transient contingency a plot will be drawn. When creating a plot for only one contingency the behavior is identical as described in Section 6. You may also check the box **Plot Multiple Contingencies** which will modify the behavior of plotting. When doing this you should then click the button **Choose Contingencies to Plot** which brings up a list of all the Transient Contingencies defined in the case. This is all depicted in the following figure.

![Transient Stability Dialog MultipleContingenciesPlots](images/Transient_Stability_Dialog_MultipleContingenciesPlots.gif)

On the list of contingencies there will be five new columns with values that may be specified and whose affect is described as follows. Setting **Show** to YES will cause plot series for that contingency to be generated. If a plot has 10 subplot series inside of it and you choose to show results for 4 transient contingencies, then the resulting chart will contain each of those 10 plot series for each of the 4 contingencies and thus contain 40 plot series. Changing the **Plot Color** will allow each plot series for that particular contingency to use this color, overriding what was specified with the plot definition. Similarly the **Dashed**, **Thickness**, and **Point Symbol** may be changed with the resulting attribute applied to all plot series for the particular contingency overriding what is specified with the plot definition.

In this way you can generate a plot showing multiple traces from multiple transient contingency simulations. An example is shown below of a state space plot for two different faults, with a different color used for each contingency.

![Transient Stability Dialog MultipleContingenciesPlotsExample](images/Transient_Stability_Dialog_MultipleContingenciesPlotsExample.gif)

Two fields for a TSContingency object named ResultFilename and ResultDirectory were added in the May 17, 2023 patch of Simulator 23. By default these are blank and the existing behavior will remain which is that hard-drive results are stored to and read from the directory specified in the Hard Drive Result Storage options and all result files are expected to have the name of the TSContingency with the appropriate extension (TSR, AUX, image file format such as JPEG, and so on). This default behavior can now be overridden by specifying either a ResultFilename or ResultDirectory.

TSContingency ResultFilename field May 17, 2023 patch of Simulator 23

Should not include any file extension, so if a value of MyFile.tsr is specified in this field, then the actual files written out would have names such as "MyFile.tsr.tsr" and "MyFile.tsr.aux". So do not include an extension in ResultFileName.

TCContingency ResultDirectory fieldMay 17, 2023 patch of Simulator 23

May be either an absolute path or a relative path. An empty string means the directory specified in the Save to Hard Drive Options is used. If this is a relative path, then it will be the path relative to the RSHD\_Directory path set with the Save to Hard Drive Options. If this is an absolute path it will be used directly.

Tabular Results for Multiple Contingency Analysis Simulations

Showing of tabular results was already extremely intricate for looking at only one transient contingency event. At this time the user interface has not been designed to support viewing tabular results for multiple transient contingency simulations simultaneously. As a result when going to the Results portion of the transient stability dialog it will be modified slightly to provide a dropdown that allows you to choose for which transient contingency to view results. This is shown in the figure below. From this point the behavior is identical as described in [Transient Stability Results: Time Values](#time-values).

![Transient Stability Dialog MultipleContingenciesResults](images/Transient_Stability_Dialog_MultipleContingenciesResults.gif)

Note that in Results from RAM tab to Show Multiple Contingencies Events when Multiple Contingencies are being processed, there is an option to Show Results for - *Only Active Contingency* or *All Contingencies* that is available for Minimum/Maximum Values, Events, and Solution Details tabs. *Only Active Contingency* will how the results for the current active contingency, or *All Contingencies* will show the results for all of the contingencies in transient stability:

![Transient Stability Multiple Contingencies Show Results AllorActive](images/Transient_Stability_Multiple_Contingencies_Show_Results_AllorActive.gif)
