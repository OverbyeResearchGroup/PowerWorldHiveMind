---
title: "Time Step Simulation (Part 1 of 2)"
part: "Simulation"
chapter_file: "26-time-step-simulation-part1.md"
topics: 22
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Time Step Simulation (Part 1 of 2)

Time step simulation setup, schedules, controller time delays and running the simulation.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (22)**

- [Time Step Simulation](#time-step-simulation)
- [Time Step Simulation: Quick Start](#time-step-simulation-quick-start)
- [Time Step Simulation Dialog](#time-step-simulation-dialog)
- [Time Step Simulation Toolbar](#time-step-simulation-toolbar)
- [Time Step Simulation Pages](#time-step-simulation-pages)
- [Hourly Summary Page](#hourly-summary-page)
- [Hourly Summary Page: Local Menu](#hourly-summary-page-local-menu)
- [Input Page](#input-page)
- [Matrix Grids](#matrix-grids)
- [Results: Constraints Page](#results-constraints-page)
- [Binding Elements Dialog](#binding-elements-dialog)
- [Results Page](#results-page)
- [Custom Results Selection Dialog](#custom-results-selection-dialog)
- [Results Grid Pages](#results-grid-pages)
- [Time Step Simulation Options](#time-step-simulation-options)
- [Specifying and Maintaining a List of Timepoints](#specifying-and-maintaining-a-list-of-timepoints)
- [New Timepoint Dialog](#new-timepoint-dialog)
- [Change Timepoint Time Dialog](#change-timepoint-time-dialog)
- [TSB Case Description Page](#tsb-case-description-page)
- [Insert/Scale Column Dialog](#insertscale-column-dialog)
- [Loading Hourly Input Data](#loading-hourly-input-data)
- [Setting up Scheduled Input Data](#setting-up-scheduled-input-data)

---

<a id="time-step-simulation"></a>

## Time Step Simulation

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Time Step Simulation tool allows you to specify operating conditions and obtain power flow solutions for a set of points in time. It provides the tools needed to analyze the operation of a power system hour by hour or by intervals down to one second.

Time Step Simulation is available in the base Simulator package. If you own Simulator, you can start taking advantage of this valuable tool right away. In addition, if you own Simulator OPF or SCOPF licenses, you can solve OPF and SCOPF scenarios on a time point to time point basis and use the tool to evaluate the behavior of prices and operating constraints. The tool will obtain the optimized generation dispatch for each time point of the analysis horizon.

In order to access the Time Step Simulation, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Time Step Simulation** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run mode](01-getting-started.md#run-mode-introduction). The following topics describe key components of the time step simulation tool:

  - [Time Step Simulation Quick Start](#time-step-simulation-quick-start)
  - [Time Step Simulation Dialog](#time-step-simulation-dialog)
  - [Specifying and Maintaining a List of Time Points](#specifying-and-maintaining-a-list-of-timepoints)
  - [Loading Input Data](#loading-hourly-input-data)
  - [Setting up Scheduled Input Data](#setting-up-scheduled-input-data)
  - [Storing Input Data and Results](26-time-step-simulation-part2.md#storing-input-data-and-results)
  - [Running a Timed Simulation](26-time-step-simulation-part2.md#running-a-timed-simulation)
  - [Time Step Simulation Toolbar](#time-step-simulation-toolbar)
  - [Running OPF and SCOPF Simulations](26-time-step-simulation-part2.md#running-opf-and-scopf-time-step-simulations)
  - [Application of Controller Time Delays](26-time-step-simulation-part2.md#controller-time-delays)

---

<a id="time-step-simulation-quick-start"></a>

## Time Step Simulation: Quick Start

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation_Quick_Start.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation_Quick_Start.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This topic will get you started with using the [Time Step Simulation tool](#time-step-simulation) and help you become familiar with the basics of setting up a time step simulation run.

The [Time Step Simulation dialog](#time-step-simulation-dialog) is displayed when you access the Time Step Simulation by selecting **Time Step Simulation** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab. This dialog contains several pages. The **Summary** page is used to define and control the time points you want to analyze. As an example, we will assume that you have hourly load data for tomorrow and that you want to determine the system bus voltages for each hour. You would do the following:

Step One: Set the List of Time Points

In order to create a list of points, right-click on the **Summary** page and select **Insert New Timepoint(s)**, which brings up the [New Timepoint Dialog](#new-timepoint-dialog). In this dialog, select tomorrow’s date from the drop down calendar component. Set the field **Total Number of Timepoints to Enter** to 24. Assume the other default values are acceptable and click OK. This will insert 24 time points, one for each hour starting tomorrow at 12:00 AM.

Step Two: Specify Input Data

Input data is specified on the **Input Page**. In this example your input data corresponds to hourly loads. Select the **MW Loads** sub-page. In order to specify hourly load values you have to insert a column for each load. Right-click on the grid and select **Time Point Records \> Insert/Scale Load Column(s)** to bring up the [Insert/Scale Column Dialog](#insertscale-column-dialog). In the selector component, select the load for which you want to specify hourly values. You can press the shift key to select multiple elements. Then press the blue **Arrow Button** to pass the selected loads to the right side of the selector. Select **OK** to insert the new column(s). Now you can specify the hourly MW values for those loads.

Step Three: Specify the Custom Results

Obtaining solutions for a large number of time points has the potential to create unnecessary burden in memory and storage due to the large amount of data that can be generated. For this reason, the Time Step Simulation tool allows you to explicitly specify what quantities you want to display and store. This is done on the [Results page](#results-page). This page contains grids for many devices including Generators, Lines, etc. In this example we want to analyze the bus voltage magnitudes. We specify what quantities we want to store as results for each object by clicking the **View/Modify** button, which brings up the [Custom Results Selection Dialog](#custom-results-selection-dialog). In this dialog select the **Buses** page and click the **Add/Remove Fields** button to bring up the list of **Available Bus Fields**. Find the **Per Unit Voltage** field and **Add** this to the list of **Selected Fields**and then click OK when done modifying fields. Results will be saved only for those buses that have the **Time Selected** field on the grid set to YES. Set this field to YES for the buses that you want to save. Click the **Save and Close** button to save the custom results settings, i.e., which objects, fields and records are to be kept during the solution; in this case bus voltages.

Step Four: Run the Simulation

The upper part of the Time Step Simulation dialog contains buttons used to control the simulation. To do a full run of the 24 hours click the **Do Run** button. The **Last Result** box shows the progress of the simulation as each time point is being solved. If you are in the **Results – Buses** page, you will see that a column was added for each bus set to YES in the **Custom Results Selection Dialog**. Each column shows the bus per unit voltage. Recall that you can right-click on any Simulator grid and select **Plot Column** to obtain a plot of the column values. If you select cells spanning all the bus per unit voltage columns, you will obtain the voltage profiles for each bus, versus time.

If you are in the **Summary** page, the **Processed** column shows that each point was in fact processed and solved.

Step Five: Save the Results

Once you have completed the simulation, you can save the results in a **Time Series Binary** (.tsb) file by pressing the **Save TSB File** button. This file will contain all the input data, the simulation options, the custom results settings, and the results. You can reload this .tsb file any time by pressing the **Read TSB File** button.

---

<a id="time-step-simulation-dialog"></a>

## Time Step Simulation Dialog

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Time Step Simulation dialog is used to control and visualize the time simulation. The top section of the form contains buttons for data input/output and buttons to control the progress of the simulation. The main part of the form has a number of [Time Step Simulation pages](#time-step-simulation-pages) that contain grids and options where input data can be specified and simulation results can be examined.

![Time Step Simulation Dialog Top](images/Time_Step_Simulation_Dialog_Top.gif)

Input/Output Buttons

Insert Time Points

Press this button to open the [New Timepoint Dialog](#new-timepoint-dialog) that allows specification of time point starting date and time, number of time points to enter, and the interval between time points.

Read TSB File

Press this button to read a Time Series Binary file (.tsb File). This files stores input and scheduled data, the simulation options and the results.

Save TSB File

Press this button to save the input, custom inputs and scheduled data, the simulation options, and the results and custom results in a Time Series Binary file (.tsb file).

Clear Results

Press this button to clear any results stored with the time step simulation.

Delete All

Press this button to delete all information associated with a time step simulation including, results, selection of objects and fields for results, schedules, schedule subscriptions, and time points.

Simulation Control Buttons

During the solution, the Time Step Simulation solves each time point in a sequential manner. During this process, the Simulation can be in one of three states:

1.  **Reset**: When the simulation has not started, when it has been completed, or when it has been paused and then reset.
2.  **Running**: When the simulation is solving time points sequentially.
3.  **Paused**: When the user has paused the simulation. The simulation actually waits until the present time point is solved in order to pause. If the simulation includes an SCOPF solution, all the contingencies are processed and the system is optimized before the simulation is paused. Note that once a time point is solved its results are available on the various grids.

The user controls the Time Step Simulation by means of the following control buttons:

Starting Time

Use this selector to specify a start time point other than the first time point in the list. The simulation will disregard the time points before the selected start time point.

Ending Time

Use this selector to specify an end time point other than the end time point in the list. The simulation will stop after processing the selected end time point.

Do Run \[Pause Solution, Continue Solution\]

Press this button to initialize the Time Step Simulation and go through all the time points until the last time point or a time point with the**Skip** field set to *Pause* is found. As the simulation takes place, the **Last Result Box**will be updated with messages. In addition, the [Summary page](#hourly-summary-page) will change the **Processed** and **Solved** fields from NO to YES, reflecting the simulation progress. The [Results](#results-page) grids will be updated once the solution for a time point has been found.

When the Simulation starts, the simulation status changes to **Running**, and the **Do Run** button changes its caption to **Pause Solution**. Press this button to pause the Solution. The simulation will continue until the current time point is solved entirely. Once the Simulation status is set to **Paused**, the **Do Run** button caption changes to **Continue Solution**. Press this button to continue the solution.

Do Single Point

Use this button to solve the next time point. You can see the last processed point in the **Last Result** box. You can also select a specific starting point by using the **Starting Time** selector.

Do Previous Point

Use this button to solve the previous time point. You can see the last processed point in the **Last Result** box. You can also select a specific starting point by using the **Starting Time** selector.

Reset Run

Use this button to go back to the first time point and initialize the simulation. This action does not delete the results of the time points processed so far, but it resets all the **Processed** fields to NO.

![Time Step Simulation Dialog bottom](images/Time_Step_Simulation_Dialog_bottom.jpg)

Last Result

The last result box in the lower left corner of the dialog is used to show solution progress messages. The messages indicate correct solutions or errors in the solution of the particular time point. It also shows the progress of the contingency analysis during a SCOPF solution.

Present Time

If you are solving the time points using a [timed simulation](26-time-step-simulation-part2.md#running-a-timed-simulation), the Present Time of the process is displayed in this field.

Refresh All Displays Each Time Step

Check this box to have all displays refresh after each time step. This could slow the process down if there are a number of displays open.

---

<a id="time-step-simulation-toolbar"></a>

## Time Step Simulation Toolbar

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation_Toolbar.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation_Toolbar.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The purpose of this toolbar (besides providing shortcuts) is to command a [Time Step Simulation](#time-step-simulation) without having to keep the [Time Step Simulation dialog](#time-step-simulation-dialog) in a non-minimized state. This is particularly important during a [Timed Simulation](26-time-step-simulation-part2.md#running-a-timed-simulation), in which you want to see the changes on the oneline diagram as they occur in time.

![Time Step Simulation Toolbar](images/Time_Step_Simulation_Toolbar.jpg)

The figure shows the main functions of the toolbar. \[Reset/Solve Previous Point/Play/Solve Next Time Point/Pause Control Buttons; Last Result Box; Present Time; Progress Bar, and Timed Simulation Options\]. All of the buttons are disabled until a list of time points have been defined in the [Summary page](#hourly-summary-page). The Time Step Simulation Toolbar is available in Run mode and is visible only when the [Time Step Simulation dialog](#time-step-simulation-dialog) is open. Minimize the Time Step Simulation dialog to prevent it from obscuring the oneline.

---

<a id="time-step-simulation-pages"></a>

## Time Step Simulation Pages

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation_Pages.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation_Pages.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Time Step Simulation dialog](#time-step-simulation-dialog) contains a number of pages used to specify input and scheduled data, and to examine the results of the simulation. See the following topics for a detailed explanation of each page:

[Summary](#hourly-summary-page)

[Input](#input-page)

[Results](#results-page)

[Results: Constraints](#results-constraints-page)

[Options](#time-step-simulation-options)

[TSB Description](#tsb-case-description-page)

---

<a id="hourly-summary-page"></a>

## Hourly Summary Page

*Source: [`Content/MainDocumentation_HTML/Hourly_Summary_Page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Hourly_Summary_Page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Summary page of the [Time Step Simulation dialog](#time-step-simulation-dialog) is used to define the time points and display a summary of the simulation. Most of the commands to manage time points can be accessed from the [Summary page local menu](#hourly-summary-page-local-menu).

Once time points are defined, the Summary page presents the following columns for each time point:

Date

The date of the time point. To modify the date, right-click and select **Time Point records \> Change Timepoint Time** on the local menu. This will open the [Change Timepoint Time Dialog](#change-timepoint-time-dialog).

Time

The time of the time point to the second. To modify the time, right-click and select **Time Point records \> Change Timepoint Time** from the local menu. This will open the [Change Timepoint Time Dialog](#change-timepoint-time-dialog).

Skip

Set this field to YES to include the time point in the simulation. If set to NO, the input data and any scheduled actions that occur at this time point are not applied to the power system.

Processed

This field is set to YES if the simulation has processed the time point. This includes applying the input data, applying the scheduled actions, and solving the power flow for that particular time point.

Solution Type

The time point can be solved using one of the following **Solution Types**: Single Solution, Unconstrained OPF, optimal power flow (OPF), and security-constrained optimal power flow (SCOPF). The last three solution types require the Simulator OPF/SCOPF add-ons. See [Running OPF and SCOPF Time Step Simulations](26-time-step-simulation-part2.md#running-opf-and-scopf-time-step-simulations) for more information.

Run Contingencies

If the case has a defined set of [contingencies](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), you can choose to run the contingency analysis for each time point by setting this option to YES.

Solved

This will be set to an integer value indicating at what point a solution was obtained for the time point under the specified Solution Type.

Num Loads

Total number of loads for which input data has been specified.

Total MW Load

Total MW load specified as input data for the time point.

Total Mvar Load

Total reactive load specified as input data for the time point.

Num Gens

Total number of generators in the system for which input data has been specified.

Total MW Gen

Total MW of generation specified in the input data.

Pre Script Cmd

The Time Step Simulation has the capability of running a pre script command before each time point is solved. The pre script command can be run either before applying the input data and scheduled actions or right after applying the input data and scheduled actions but is always run before the power flow solution is solved. See [Time Step Simulation: Options](#time-step-simulation-options) for more information on specifying when the pre script command is run. See the [Script Command](01-getting-started.md#script-mode-introduction) section to learn the details about performing Simulator actions using script commands.

Post Script Cmd

The Time Step Simulation has the capability of running a post script command right after the time point is solved. The post script command can be run either before storing results or after storing results. See [Time Step Simulation: Options](#time-step-simulation-options) for more infomration on specifying when the post script command is run. See the [Script Command](01-getting-started.md#script-mode-introduction) section to learn the details about performing Simulator actions using the script language.

---

<a id="hourly-summary-page-local-menu"></a>

## Hourly Summary Page: Local Menu

*Source: [`Content/MainDocumentation_HTML/Hourly_Summary_Page_Local_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Hourly_Summary_Page_Local_Menu.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The local menu of the [Time Step Simulation](#time-step-simulation) [Summary page](#hourly-summary-page) is used to perform a number of logical actions on the time point grid and is, as every Simulator local menu, accessed by right-clicking anywhere on the grid. When selected from the Summary page, the local menu shows the following additional time step simulation specific options:

Time Point records \> Apply Time Point

Simulator applies the input data of that particular time point to the power system model, without solving the time point. Upon selection of this option, the time point information can be visualized in the [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays).

Time Point records \> Solve Time Point

This option applies the time point input and the scheduled data to the power system and solves the time point with the specified Solution Type.

Time Point records \> Change Timepoint Time

This option allows the user to modify the date/time of the selected time point through the [Change Timepoint Time Dialog](#change-timepoint-time-dialog). If the new date/time belongs to an existing point in the list, an error message is displayed. The time points can be specified with a precision of up to 1 second.

Insert New Timepoint(s)

Use this option to insert new time points into the time point list. This selection brings up the [New Timepoint Dialog](#new-timepoint-dialog).

Delete Entire Timepoint Record

Use this option to delete the selected time point and all of the input data and custom results for that time point.

Set/Toggle/Columns \> Plot Column(s)

Use this option to automatically generate column plots. By default, in the Time Step Simulation grids, the column plots display graphs of column data versus the date/time column (the combination of the date and time columns).

---

<a id="input-page"></a>

## Input Page

*Source: [`Content/MainDocumentation_HTML/Input_Page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Input_Page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Time Step Simulation dialog](#time-step-simulation-dialog) Input page is used to specify input data per time point, scheduled data, time step actions, and custom inputs. This requires that the list of time points have been created. See the [Specifying and Maintaining a List of Timepoints](#specifying-and-maintaining-a-list-of-timepoints) topic for details on managing the list of time points.

The Input page contains several pages that can be grouped in four types: Input Pages, Schedule Pages, Time Step Actions Page, and Custom Inputs Pages.

Input Pages

The time point input pages (MW Loads, Mvar Loads, Actual MW Generation, Maximum Generation, Line Status, Area Loads, Zone Loads, and Injection Groups) are [Matrix Grids](#matrix-grids) that are used to specify data on an time point by time point manner. In order to tell Simulator that we want to specify time point data for a particular object type (e.g. load, generator, line, etc.) we need to add that particular object to the corresponding grid. For instance, suppose that you want to specify MW data for Load 1 at bus 1. Go to the MW Loads page, right-click and select **Time Point records \> Insert/Scale Load Column(s)** to bring up the [Insert/Scale Column Dialog](#insertscale-column-dialog). In this dialog, you can select the load and add it as a column to the MW Loads grid. The corresponding values at each time point for that particular load can then be entered in the grid.

Use the Area Loads and Zone Loads pages to specify the MW load for an entire Area or Zone at a particular time point. When Simulator applies the input data to solve a time point, it will scale the load of the specified area or zone to match the value entered for that time point.

Use the Injection Groups page to specify to total MW injection from an injection group at a particular time point. All loads and generators in an injection group will have their MW injection changed i proportion to their participation factor specified with the injection group to meet the specified MW injection. By default generators will have their minimum and maximum MW limits enforced. (Injection groups have their own set of options that can override the default options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.) Mvar injections will not be modified as part of this input. If a zero injection value is specified for a time point, no modifications will be made to the injection group for that time point. To zero out the injection, change the value to a very small number, e.g. 0.01.

Schedule Pages

The schedule pages ([Schedules page](26-time-step-simulation-part2.md#schedules-page) and [Sched Subscriptions page](26-time-step-simulation-part2.md#schedule-subscriptions-page)) are used to specify scheduled input data, i.e., data that more naturally spans multiple time points rather than being defined at each time point. Examples of data that can be scheduled are scheduled transactions, generator statuses, line statuses, etc. For a detailed explanation on how to set up scheduled data, please read the [Setting Up Scheduled Input Data](#setting-up-scheduled-input-data) section.

Time Step Actions Page

Use this page to specify [Time Step Actions](26-time-step-simulation-part2.md#time-step-actions). These are conditional actions that can be applied during a time step simulation run if their Model Criteria evaluates to true for a specified time period.

Custom Inputs Pages

Custom inputs allow the selection of specific objects, object numeric fields, and the specification of what each selected field should be set to for a particular time point.

The top portion of this page is used to select the objects and fields and specify how the selection of objects and fields should be displayed in the grids contained on the bottom portion of the page. The selection of objects and fields for custom inputs is identical to the selection of objects and fields on the [Results page](#results-page).

Once the objects and fields have been selected, the grids will be updated with a column for each of the selected object and field combinations. Use these columns to specify the values for the selected fields at each time point.

---

<a id="matrix-grids"></a>

## Matrix Grids

*Source: [`Content/MainDocumentation_HTML/Matrix_Grids.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Matrix_Grids.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Matrix Grids are a special type of data grids used in the input and results pages of the Time Step Simulation tool. In these grids, the time dimension is assigned to the rows and the object fields (load MW, generator MW output, etc) are assigned to the columns. The column header corresponds to the ID of the object. The number of columns of the grid depends on the user options and simulation results:

Hourly Input Pages

In the case of input pages, the user has to specify hourly data for each object, e.g., load, generator, area. Thus the user adds each column to the grid explicitly.

Custom Result Pages

In the custom result pages, a column is created for each object whose results have been specified to be stored.

Constraint Pages

Since the constraints are determined at solution time, the columns appear only when constraints have been detected during the solution.

---

<a id="results-constraints-page"></a>

## Results: Constraints Page

*Source: [`Content/MainDocumentation_HTML/Results_Constraints_Page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Results_Constraints_Page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results Constraints page of the [Time Step Simulation dialog](#time-step-simulation-dialog) is used to convey results that are specific to an optimal power flow type of study. This page is only available with the [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) and [SCOPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview) add-ons of Simulator. When the OPF solution type is used to solve a time point, the status of the system during that particular time is optimized so that the total operating cost of the system is minimized, and the normal operation constraints are enforced. In addition, the SCOPF solution type enforces contingency constraints. The OPF and SCOPF solutions contain information about the elements that determine the LMPs, the binding constraints, the violating contingencies, and changes in the control settings.

The information related to contingencies on these pages is available only in the SCOPF Simulator add-on.

The pages of the Results: Constraints page are:

Results Summary

This page is similar to the [Summary Page](#hourly-summary-page), except that it contains additional operating information such as:

Initial Cost

The cost of operating the system given the initial generator set points and a standard power flow solution. No controls are moved to minimize cost.

Unconstrained Cost

The total operating cost after the controls are moved to minimize cost, without enforcing any normal operation or contingency constraint. The result is an operating cost that corresponds to an Economic Dispatch solution.

Unconstrained LMP

The average marginal price of the system under unconstrained optimization.

Final Cost

The total operating cost after a constrained (OPF or SCOPF) solution has been obtained.

LMP

(Average, Standard Deviation, Minimum and Maximum): Metrics of the LMP values.

Binding Lines

Number of transmission lines and transformers that are binding after the OPF/SCOPF solution has been determined.

\# CTGs Unsolvable

Number of unsolvable contingencies. These are severe contingencies that would cause the power flow solution to fail for that particular time point scenario. Unsolvability of the power flow case is related to maximum loadability conditions.

You can access the details of the binding elements by right-clicking and selecting [Show Binding Constraint Dialog](#binding-elements-dialog) on the local menu.

Binding Lines

This is a [matrix grid](#matrix-grids) that shows information for transmission lines and transformers that become binding constraints during the OPF or SCOPF solutions. A similar page is available for binding interfaces.

When transmission lines or transformer thermal ratings become binding constraints for a time point, a column is automatically added, forming in this manner the matrix grid. You can access the details of the binding line or transformer by right-clicking and selecting [Show Binding Constraint Dialog](#binding-elements-dialog) on the local menu. The grid also shows the following summary columns:

Processed

Gets set to YES if the time point was correctly processed.

CTGs with Viols

Number of contingencies that presented one or more violations (violating contingencies). 

\# CTGs Unsolveable

Number of unsolvable contingencies for the time point.

BC Line Viols

Number of transmission line and transformer violations that were identified in the base case.

\# Line Viol

Number of transmission line and transformer thermal violations. 

Binding Lines

Number of binding lines in the OPF/SCOPF solution.

Line Unenforceable

Number of lines with unenforceable limits.

Binding Interfaces

This is a [matrix grid](#matrix-grids) that shows information for interfaces that become binding constraints during the OPF or SCOPF solutions. A similar page for lines is available.

When interfaces become binding constraints for a time point, a column is automatically added to the matrix grid. You can access the details of the binding interface by right clicking and selecting [Show Binding Constraint Dialog](#binding-elements-dialog) on the local menu. The grid also shows the following summary columns:

Processed

Gets set to YES if the time point was correctly processed.

CTGs with Viols

Number of contingencies that presented violations (violating contingencies) 

\# CTGs Unsolveable

Number of unsolvable contingencies for the time point.

BC Interface Viols

Number of interface violations that were identified in the base case.

\# Interface Viol

Number of interface violations.

Binding Interface

Number of binding interfaces in the OPF/SCOPF solution.

Interface Unenforceable

Number of interfaces with unenforceable limits.

Binding Contingencies

This [matrix grid](#matrix-grids) shows information similar to that found on the Binding Lines and Binding Interfaces pages. Here though the data is organized by contingencies, which allows easy identification of the most severe contingencies. Each column of the matrix grid corresponds to a contingency. You can access the details of the binding element by right-clicking and selecting [Show Binding Constraint Dialog](#binding-elements-dialog) on the local menu. The grid also shows the following summary columns:

Processed

Gets set to YES if the time point was correctly processed.

CTGs with Viols

Number of contingencies that presented violations (violating contingencies) .

\# Line Viol

Number of transmission line and transformer thermal violations. 

Binding Lines

Number of binding lines in the OPF/SCOPF solution.

Binding Interfaces

Number of binding interfaces in the OPF/SCOPF solution.

Binding Line Summary Matrix

This [matrix grid](#matrix-grids) shows the number of time points for which a line has been binding due to each contingency. In this case, the rows correspond to binding lines, and the columns to violating contingencies. The grid also shows the following summary columns:

From Number

Binding line from bus number

To Number

Binding line to bus number

Circuit

Binding line circuit ID

Total Hrs

Total number of time points for which the line was binding (in the overall simulation).

Total Hrs Unenforceable

Total number of time points for which the line constraint was unenforceable (in the overall simulation).

Binding Line Summary List

Shows information similar to the **Binding Line Summary Matrix** but in form of a list. The same line may appear several times under different contingencies. Besides the information on the **Binding Line Summary Matrix**, this grid shows the following fields:

Contingency Name

Contingency that causes the line constraint to be binding

Avg MC

Time Average MVA Marginal Cost  

Max MC

Time Maximum MVA Marginal Cost

Min MC

Time Minimum MVA Marginal Cost

---

<a id="binding-elements-dialog"></a>

## Binding Elements Dialog

*Source: [`Content/MainDocumentation_HTML/Binding_Elements_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Binding_Elements_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is called from the [Results: Constraints Page](#results-constraints-page) of the [Time Step Simulation dialog](#time-step-simulation-dialog). Right-click on a time point record in any of the Results Summary, Binding Lines, Binding Interfaces, or Binding Contingencies tables, and select **Show Binding Constraint Dialog** from the local menu. The dialog shows the binding line and interface constraints determined by the OPF/SCOPF solution. The **Time** selector allows easy navigation through the list of time points.

The grid section of the dialog shows the following:

Type

Either line or interface flow

Constraint ID

Line or Interface ID

Contingency Name

Name of the contingency under which the constraint becomes binding.

MVA Marg. Cost.

Marginal cost of enforcing the constraint. For lines, the limit corresponds to the thermal (MVA) limit. For interfaces, it is given by a MW limit.

---

<a id="results-page"></a>

## Results Page

*Source: [`Content/MainDocumentation_HTML/Results_Page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Results_Page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The results of the [Time Step Simulation](#time-step-simulation) are presented on the grids of the Results page. The Time Step Simulation allows you to specify what objects (buses, lines, generators, loads, etc.) and what object fields (bus voltage, bus LMP, gen MW, etc.) should be displayed on the results grids. This gives the user the flexibility needed to explore the relevant results, avoiding at the same time the problem of storing a massive amount of results, most of which may not be relevant. Storage is a critical aspect of the Time Step Simulation, since a set of results comparable to full a PF/OPF/SCOPF solution is generated for each timepoint.

The Results page has two sections: The top section is used to set up the options needed to customize the results display. The grid section is used to display the actual results.

Results Page: Top Section

This section includes the following options:

View/Modify

Press this button to access the [Custom Results Selection Dialog](#custom-results-selection-dialog). This dialog is used to specify the objects and object fields for which results will be stored.

Load

The custom result definitions set up in the [Custom Results Selection Dialog](#custom-results-selection-dialog) can be saved in a Custom Results File (\*.tsc) in order to use them with different \*.tsb files or Simulator cases. Press this button to Load the results file and apply the result definitions to the current time step simulation.

Save

Press this button to save the result definitions in a Custom Results File (\*.tsc).

Group Results by

The results grids for Areas, Buses, etc. are [Matrix Grids](#matrix-grids) that present the time point results for each type of object. For instance, suppose that we want to store the bus voltage magnitude and angle. The Buses grid will show columns for the time point values of voltage magnitude and voltage angle of selected each bus.

**Objects**: The columns will be grouped by objects, e.g., all the fields of bus 1, then all the fields of bus 2, etc.

**Fields**: The columns will be grouped by fields, e.g. all the bus p.u. voltages, then all the bus LMPs, etc.

Identify Results by

The results grids for Areas, Buses, etc. create one column for each object field specified in the [Custom Results Selection Dialog](#custom-results-selection-dialog). The column header thus identifies the particular object for which time point results are displayed. This identification can be made based on the object **Number**, **Name** or **Number + Name** combination.

Send All Results to Excel

Press this button will send all results to Excel. The format and data that gets sent will be the same as when sending each table to Excel one at a time. Only the results tables that actually have objects defined will be sent to Excel. All results will be sent to a new workbook in separate worksheets.

Results Page: Grid Section

This grid section is used to display the results of the [Results Grids](#results-grid-pages).

---

<a id="custom-results-selection-dialog"></a>

## Custom Results Selection Dialog

*Source: [`Content/MainDocumentation_HTML/Custom_Results_Selection_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Results_Selection_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to specify what objects and object fields will be stored during a [Time Step Simulation](#time-step-simulation) and will be displayed on the [Results grids](#results-grid-pages). This dialog is opened using the **View/Modify** button on the [Results](#results-page) page of the [Time Step Simulation dialog](#time-step-simulation-dialog).

To specify that a particular field be stored for a certain object:

1.  Click on the page of the object type to store (Areas, Buses, etc.)
2.  Set to *YES* the **Time Selected** field of those objects for which you want to store information.
3.  Click the **Add/Remove Fields** button to open the Select Fields dialog. Fields contained in the Selected Fields list will be stored for each of the selected objects. To move fields between the Available Fields and Selected Fields lists, drag the fields between lists or select fields and use the Add and Remove buttons as appropriate. Once the fields are selected click the OK button to save the changes and close the dialog.

Once you are done with the selections, press the **Save and Close** button to apply the customization. The [Results grid pages](#results-grid-pages) will be filled with the corresponding columns after the Time Step Simulation starts.

Note that the actual results and the result customization will be stored in the .tsb file. For more information about saving the Time Step Simulation results, please read the [Storing Input Data and Results](26-time-step-simulation-part2.md#storing-input-data-and-results) section.

Fields for Areas, Buses, Generators, Injection Groups, Interfaces, Lines, Loads, Owners, Super Areas, Switched Shunts, Transformers, and Zones can be specified to be displayed on the grids and stored in the .tsb file.

---

<a id="results-grid-pages"></a>

## Results Grid Pages

*Source: [`Content/MainDocumentation_HTML/Results_Grid_Pages.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Results_Grid_Pages.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These are the grids of the [Results page](#results-page) that contain [Time Step Simulation](#time-step-simulation) results based on the fields and objects selected using the [Custom Results Selection Dialog](#custom-results-selection-dialog). The fields and objects must be selected before the time step simulation run is started in order for those results to show up in the grids.

There is one page for each type of object: Areas, Buses, Generators, Injection Groups, Interfaces, Lines, Loads, Owners, Superareas, Switched Shunts, Transformers and Zones.

These pages are all [Matrix Grids](#matrix-grids). Each column of a grid corresponds to a field of a specific object of the power system, e.g., KV voltage of bus 1. Each row of the grid corresponds to a timepoint.

Note that you can plot the results of the grid versus the timepoint date time by right-clicking on the grid and selecting **Set/Toggle/Columns \> Plot Column(s)** from the local menu.

---

<a id="time-step-simulation-options"></a>

## Time Step Simulation Options

*Source: [`Content/MainDocumentation_HTML/Time_Step_Simulation_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Time_Step_Simulation_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Options page of the [Time Step Simulation dialog](#time-step-simulation-dialog) contains options to control how input data is applied and how output results are presented and stored.

Area and Zone Load Scaling

In many practical studies, data of individual MW loads may not be available for all the loads in a control area for each time point. In order to simulate load variations, Simulator allows you to specify the Area or Zone Total MW Load values for each time point in the **Area Loads** and **Zone Loads** pages of the [Input page](#input-page). Thus, the Time Step Simulation load data may be a combination of:

  - Areas or zones where each individual load is specified
  - Areas or zones where only the total MW load is known
  - Areas or zones where some individual loads and the total area load are known

If you have specified individual load values for a load within an area or zone that is also set to be scaled to a total MW value, Simulator will adjust the individual load to the individual value first, and then the load will be scaled with the rest of the loads in the area or zone to achieve the total MW value desired for the time point. The final load will be the total value specified for the area or zone.

When time point values are specified for areas and zones within the same time step input, only one or the other can be used. This can be set in the **Use Time Point Values of** option.

You can also specify in the **Reactive Power Scaling** option how the reactive power is treated when the load is scaled. You can choose to have the reactive power scaled to keep the power factor constant, or for the reactive power to remain fixed at its original value.

Solution Options

These options control the solution process.

Pause if Power Flow Does Not Solve

The simulation is stopped at the time point where a power flow solution cannot be obtained. This is an indication of wrong data or a system brought to its loadability or transfer capability limit.

Enable Power Flow Area Interchange Control

This option ensures that the area interchange control, if possible, is enforced in the case.

Turn generators off AGC when output changes

At each time point, generators can be adjusted by specifying Gen Actual MW values on the Input page or as part of Injection Groups that have their injection changed on the Input page. If area interchange is enabled for the case and associated area or super area where generation changes have been made, this may cause the generators to move away from their values specified on the Input pages. To prevent this, use this option to disable AGC for these generators so that they will not move because of automatic MW control schemes.

Pricing Options 

These options are available only in the OPF/SCOPF add on.

Solve Unconstrained Case

Select this option when you want an unconstrained solution to be obtained before an OPF or SCOPF solution for each time point.

Price Hydro Generation at Marginal Cost

During OPF and SCOPF simulations, hydro generation may experience large changes in output due to its low marginal cost. However, hydro generation is often not as cheap if limited water levels and dam restrictions are observed. These considerations are usually taken care of in the hydro-thermal coordination solution, outside of Simulator. In the OPF and SCOPF solutions it is important to assign a reasonable price to hydro generation to avoid large generation output deviations. A common mechanism to do that is to first obtain the system marginal cost, and then assign this cost to the hydro units.

Reset Hydro Gen Price at the End of Time Period

Choose this option to make the hydro generation price be reset for the next time point solution.

Save Binding Constraints

The binding constraints determined in the OPF/SCOPF are stored.

Injection Group MW Scaling

This is an informational message about how injection group options can be set to scale injection groups as part of the time step tool.

There are no options that can be set with the time step simulation tool as to how injection groups are scaled. By default all loads and generators in an injection group will have their MW injection changed in proportion to their participation factor specified with the injection group to meet the specified MW injection. By default generators will have their minimum and maximum MW limits enforced. (Injection groups have their own set of options that can override the default options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.) By default Mvar injections will not be modified as part of this input. If a zero injection value is specified for a time point, no modifications will be made to the injection group for that time point. To zero out the injection, change the value to a very small number, e.g. 0.01.

If the Injection Group Specific Scaling Options specify that Merit Order Dispatch is selected, both generators and loads in the injection group will be adjusted in order of highest relative participation factor to lowest with each generator and load in the list being adjusted until it hits either its maximum or minimum MW limit before moving on to the next element. This process continues until the desired injection is met. Mvar load will be adjusted by keeping a constant power factor. Loads that have both their minimum and maximum MW limits set to zero will not be allowed to increase. They can only decrease to 0 MW.

If the Injection Group Specific Scaling Options specify that Economic Merit Order Dispatch be used, only generators will be adjusted. Details about how economic merit order dispatch is performed can be found under the [Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

Time Step Simulation Options

The Time Step Simulation can be performed in two ways:

Continuous

With this option time points are solved one after another as soon as one time point finishes. The purpose of the simulation is to obtain the solutions for all time points as quickly as possible.

Timed

With this option the solutions are simulated as they would occur in actual time. The difference in date/time between two time points in the list defines a delay to start the solution of the next point. A **Time Scale** is used to set the speed of the simulation with respect to actual time. Suppose that you have 3 time points defined at the following date/times:

1/20/05 1:00 AM

1/20/05 2:00 AM

1/20/05 4:00 AM

Assume also that the **Time Scale** is 1 hour runs in 10 seconds. If you start the **Timed Simulation** you would see the conditions of the first time point applied to the power system immediately, the conditions of the second time point applied 10 seconds later, and those of the third point applied 20 seconds after the second point. The delays on the simulation allow you to see how the quantities evolve in actual time. In addition, you can animate the time simulation while each time point is being solved. The visualization of the **Timed Simulation** is enhanced when you use the [Time Step Simulation Toolbar](#time-step-simulation-toolbar).

Step Type

This section of options allows you to specify if the data for each time point should be applied only, or if the data should be applied and the load flow solved. Use **Apply and Solve** to apply the input data and actually solve the power flow. Use **Just Apply Data** to apply the input data and not solve the power flow. Check the **Apply Input Data** box to apply input data and custom input data. This does not include scheduled data. Check the **Apply Schedule Data** box to apply scheduled data.

Any pre-script or post-script commands will be applied regardless of how these options are set.

Auto Load TSB File Options (saved in case pwb file)

These are options that relate the power system case (.pwb file) to the time series binary file (.tsb file). These options are saved with the .pwb case.

Automatically Load Default \*.tsb File

The .tsb file specified in the **Default \*.tsb file** is loaded automatically when opening the .pwb case. If the file cannot be found, a message will be issued.

Automatically Run Simulation after Loading \*.tsb

This option is only relevant if the .tsb file was automatically loaded. This instructs the Time Step Simulation form to start the simulation immediately following loading the .tsb file.

Automatically Set Default \*.tsb File to Current \*.tsb File

When leaving Simulator, the current time series information is saved in the **Default \*.tsb file**.

Default \*.tsb File

Default path and name of the \*.tsb file.

Save the Default \*.tsb File after Finishing the Run

If this option is checked, immediately upon finishing the simulation run, the settings and results are saved in the **Default \*.tsb file**.

Result Storage Options

These options allow the selection of where the results from the simulation are directed.

Store results in memory

Only store the results in the computer's random access memory (RAM). This option is prone to running out of memory when many fields are stored over many time points.

Only store results in csv file

With this option the results are sent directly to a CSV file without filling up computer memory. Keep in mind that when this option is chosen, the [Results grids](#results-grid-pages) will not contain any data.

Store in memory and csv file

With this option the results will be stored both in the computer's memory and sent to CSV file.

CSV Object ID Options

When choosing to store results in a CSV file, this option will determine if the objects will be identified by **Primary key (number)**, **Secondary key (name)**, or **Label**.

CSV File Identifier

This is a label that will be prepended to every generated CSV file if choosing to send results to CSV. Files are generated for each result type. For example if a user is storing bus voltage and angle, the results will be stored in a file named *CSV File Identifier*\_Buses.csv. A separate file will be created for each of the results types to store data of that type.

CSV Output Path

This specifies the computer or mapped network drive where the CSV results will be stored.

Auto Contouring Options

The Time Step Simulation allows you to contour quantities on the oneline diagram using Simulator [Contouring](17-oneline-view-printing-and-contouring.md#contouring) at each time point. Optionally, these contour diagrams can be saved in different formats.

No Auto Contouring

Contouring is not used during the Time Step Simulation. Although using the **Timed Simulation** you can see the quantities change and the animation take place on the diagrams, the contouring is not displayed.

Contour but Do not Save

Contouring takes place at each time point, but the diagrams are not saved.

Save in File as Bitmap

The contouring diagrams generated at each time point are saved in Bitmap format.

Save in File as JPEG

The contouring diagrams generated at each time point are saved in JPEG format.

Contour File Name Format

The Bitmap or JPEG contouring diagrams are saved using the specified format, which includes the time point date/time.

Run Pre-Script Command

This option allows the pre-script command to be run Before Applying Input Data or Right After Applying Input Data. Input data includes any hourly input data and scheduled actions. With either setting, the pre-script command is applied prior to solving the power flow solution for the time point.

Run Post-Script Command

This option allows the post-script command to be run either Before Storing Results or After Storing Results. Running the post-script command before storing the results could be useful in situations in which sensitivity analysis is done based on the solution of the time point and these sensitivities need to be stored as part of the results for that time point. Running the post-script command after storing the results could be useful in situations in which a specific control setting was used for the current time point and needs to be restored to the original setting before moving on to the next time point.

Set Reference Case

The reference case is the case that will be restored when resetting the simulation or starting a simulation run. The reference case is initially set to be the case in memory when Time Step Simulation dialog is first opened. If changes are made to the case in memory while the Time Step Simulation dialog is open and these changes need to be reflected in the reference case, click this button to set the case that is currently in memory to be the reference case.

---

<a id="specifying-and-maintaining-a-list-of-timepoints"></a>

## Specifying and Maintaining a List of Timepoints

*Source: [`Content/MainDocumentation_HTML/Specifying_and_Maintaining_a_List_of_Timepoints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Specifying_and_Maintaining_a_List_of_Timepoints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The list of time points is the basis for the [Time Step Simulation](#time-step-simulation). Simulator will go through the list of time points and solve each one of them in sequence. Results will be available only for those time points specified in the list. Intervals as small as one second can define a time point.

Whether you start with an empty list or you already have time points in it, you can insert new time points by right-clicking in the **Summary** page and selecting **Insert New Timepoint(s).** This will bring up the [New Time Point Dialog](#new-timepoint-dialog).

The list of time points will always be sorted based on the date/time shown on the Date and Time columns in the [Summary page](#hourly-summary-page). Thus, if you create a new time point with an intermediate date/time, Simulator will insert it at the appropriate place in the list. If you need to change the date/time of a time point you can right-click in the **Summary** grid and select **Time Point records \> Change Timepoint Time** to bring up the [Change Timepoint Time Dialog](#change-timepoint-time-dialog). This dialog is similar to the [New Timepoint Dialog](#new-timepoint-dialog), with the exception that instead of specifying the date/time for a new time point, you will be modifying the date/time of an existing time point. If the date/time matches the date/time of an existing time point, a warning message is issued.

Each time point is linked to its results data in what is called a **Timepoint Record**. The **Timepoint Record** contains the date and time of the time point, all the input data specified for that point, and if any, the results that have been obtained for that time point. If you delete a time point, the entire record is deleted with it. In order to delete the time point you can right-click in the **Summary** grid and select **Delete Entire Timepoint Record**. Note that you can vertically select cells in this grid and delete several time point records at a time.

Suppose that you have 1:00 AM and 3:00 AM time points that have associated with them hourly MW load data. If you insert 2:00 AM data, the 2:00 AM cell of the MW load will appear empty. If you run a study, no data will be applied to the power system at 2:00 AM, but you will get a result (identical to the one of 1:00 AM). You need to fill the 2:00 AM cells with data in order for the values to be applied at that time point and obtain the correct results for 2:00 AM.

---

<a id="new-timepoint-dialog"></a>

## New Timepoint Dialog

*Source: [`Content/MainDocumentation_HTML/New_Timepoint_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/New_Timepoint_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The New Timepoint Dialog is used to define new time points for a [Time Step Simulation](#time-step-simulation). This dialog is accessed from the [Time Step Simulation dialog](#time-step-simulation-dialog) by right-clicking on any of the grids that displays time points and selecting **Insert New Timepoint(s)** from the local menu or clicking the **Insert Time Points** button at the top of the dialog. One or multiple time points can be defined at once. Use the date drop-down box to bring up a calendar for easy selection of the date. Note that the calendar has visual controls that allow you to navigate through months or years, which allows you to set the desired date easily.

If this is the first time point you will insert in the list, by default the dialog is populated with today’s date at 12:00 AM. If there are other points in the list, the default is one hour after the date/time of the last time point.

The other options in this dialog are:

Date

Use this control to select the date of the time point. You can use the visual controls or the up or down arrow keys to modify the date.

Time

Use the control to enter the hour, minute, second, and AM/PM description of the time. Once you are positioned on the hour, minute, second, or AM/PM values, you can use the up/down arrow buttons for easy selection without having to type. Note that the time points are specified with a precision of up to 1 second.

Total Number of Timepoints to Enter

By default this field is set to 24, meaning that you will enter an entire day's worth of time points with the specified date and time if the interval is left at the default specification of one hour. Note: The maximum number of Timepoints that may be inserted is 100,000.

New Timepoint Interval: Hours

If the **Total Number of Timepoints to Enter** is more than one, this field is used to specify the hour(s) of the interval between each time point. Time points will be Hours + Minutes + Seconds apart. Default is one hour.

New Timepoint Interval: Minutes

If the **Total Number of Timepoints to Enter** is more than one, this field is used to specify the minute(s) of the interval between each time point. Time points will be Hours + Minutes + Seconds apart. Default is zero minutes.

New Timepoint Interval: Seconds

If the **Total Number of Timepoints to Enter** is more than one, this field is used to specify the second(s) of the interval between each time point. Time points will be Hours + Minutes + Seconds apart. Default is zero minutes.

OK, Cancel

Click **OK** to close the dialog and insert the specified time points. Click **Cancel** to close the dialog and abandon any changes.

---

<a id="change-timepoint-time-dialog"></a>

## Change Timepoint Time Dialog

*Source: [`Content/MainDocumentation_HTML/Change_Timepoint_Time_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Change_Timepoint_Time_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Change Timepoint Time Dialog is used to modify the date/time of a time point for the [Time Step Simulation](#time-step-simulation). Only one time point time can be changed at a time. If the new time assigned to the time point already exists, a warning message is generated prompting for the input of a different date/time. If the new date/time does not exist, the time point will be moved to the correct position in the time point list.

The Change Timepoint Time Dialog is accessed by right-clicking on any of the Summary, Input, and Results [Time Step Simulation pages](#time-step-simulation-pages) that list the time point date/time and choosing **Time Point records \> Change Timepoint Time** from the local menu.

Date

Click the calendar icon to use the calendar control to select the date of the time point. You can also position the mouse cursor over the month, day, or year and use the up/down keys on the keyboard to adjust these fields.

Time

Use the control to enter the hour, minute, seconds and AM/PM description of the time. Once the mouse cursor is positioned on the hour, minute, seconds or AM/PM value, you can use the up/down keys on the keyboard for easy selection without having to type. Note that the time points are specified with a precision of up to 1 second.

---

<a id="tsb-case-description-page"></a>

## TSB Case Description Page

*Source: [`Content/MainDocumentation_HTML/TSB_Case_Description_Page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TSB_Case_Description_Page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This page is used to describe the time series binary file (.tsb file) for informational purposes. Use the memo box that comprises most of this page to comment on the case, .tsb file, time step simulation, or anything else that is relevant. These comments will be stored with the .tsb file. The **Version Used to Store the TSB File** and the **Simulator Build Date**are also provided.

---

<a id="insertscale-column-dialog"></a>

## Insert/Scale Column Dialog

*Source: [`Content/MainDocumentation_HTML/Insert_Scale_Column_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Insert_Scale_Column_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Insert/Scale Column Dialog is opened from the [Input page](#input-page) grids of the [Time Step Simulation dialog](#time-step-simulation-dialog). These [matrix grids](#matrix-grids) are used to specify input data for MW Loads, Mvar Loads, Generator MW, Generator Maximum MW, Area Loads, Zone Loads, and Injection Groups. Time point data for each particular object is specified in columns. When no column has been added to the grid, the Insert/Scale Column Dialog allows you only to select the new object. When there are existing columns on the grid, the dialog allows you to insert a **New Column** either alone or based on the values of the existing columns. This option is available because values such as load MW data tend to experience similar fluctuations in time.

Current Column

If there are existing columns and the Insert/Scale Column Dialog is called from one of these existing input data columns, this field shows the position of that column. This field tells the user what column the **New Column** will be based on.

Action

These options determine how the new column will be inserted.

Scale Entire Current Column

This option is available only when the current column corresponds to an existing input data column. When applied, the new column takes the values of the current column scaled by the **Scaling Factor**.

Scale Selected Rows of Current Column

This option allows you to select a group of contiguous rows of a column and scale only those rows of the **Current Column** by the **Scaling Factor**.

Insert New Column Derived from Current Column

This option applies the **Scaling Factor** to the values of the of the **Current Column** and uses these scaled values to populate the **New Column**.

Scaling Factor

Factor used for scaling the current column, selected rows of the current column, or inserting a new column derived from the current column.

Load Scaling

These options are available only when inserting Load columns and are used to scale **Real and Reactive Load, Just Real Load,** or **Just Reactive Load.**

New Columns Selector

Use this selector to specify the ID of the object(s) that will be added as new column(s) to the grid. The bottom section of the dialog is a selector that allows you to specify one or multiple objects at a time and add columns for them by passing the objects from the left list to the right list. All of the options available with the selector may not be shown by default. Click on the down arrow located to the left of the Sort by option to open the menu that allows selection of which options to display. This selector has the following options:

Sort by Name

Check this option to sort the list of available objects by name

Sort by Number

Check this option to sort the list of available objects by number

Define/Find Filter

Press this button to filter the list of available objects using an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering).

Use Area/Zone Filters

Check this box to filter the list of available objects using the Area/Zone filters.

Search Next/Search All

By typing the start of the name of an object in the edit line, you can search the next object or all the objects available that match the search pattern. You can also use wildcards to search for objects.

List of Objects

The objects in the list are selected by clicking on them. Multiple objects that are together can be selected by clicking the mouse while holding the SHIFT key. Multiple objects that are not contiguous in the list can be selected by clicking the mouse while holding the CTRL key.

Select All/Clear All

Use these buttons to select or clear all items selected in the list of objects.

Select Button

Press the blue arrow button to pass the selected objects from the left list to the right list.

Remove Button

Press the trash can button to remove the objects selected in the right list.

For more information about methods to specify input data, please read the [Loading Input Data](#loading-hourly-input-data) section.

---

<a id="loading-hourly-input-data"></a>

## Loading Hourly Input Data

*Source: [`Content/MainDocumentation_HTML/Loading_Hourly_Input_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Loading_Hourly_Input_Data.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Time Step Simulation](#time-step-simulation) allows you to specify the operating conditions of your power system through input data. The input data can be of two types:

**Scheduled Data,** which is specified for data that more naturally spans multiple time points rather than being defined at each time point. To set up scheduled data see the [Setting up Scheduled Input Data](#setting-up-scheduled-input-data) section.

**Time Point-Based Data** is specified for each time point in the [Input pages](#input-page). There are several ways to specify input data:

  - By entering data manually on the [Input pages](#input-page).
  - By deriving or scaling values from another column using the [Insert/Scale Column Dialog](#insertscale-column-dialog).
  - By loading previously formatted data from Excel or .csv files through the **Read Buttons** in the [Time Step Simulation Dialog](#time-step-simulation-dialog).
  - By pasting data from Excel directly to the grid. A common way to do that is to:
      - Set up the desired time points and data columns on the grids of the [Input pages](#input-page)
      - Copy the template to Excel by right-clicking and selecting **Copy/Paste/Send \> Send All to Excel** on the local menu
      - Fill the Excel sheet with the appropriate data
      - Paste the data back to the data grid by selecting and copying it in the Excel sheet, including the column headers, and then right-clicking on the grid back in Simulator and selecting **Copy/Paste/Send \> Paste** on the local menu

---

<a id="setting-up-scheduled-input-data"></a>

## Setting up Scheduled Input Data

*Source: [`Content/MainDocumentation_HTML/Setting_up_Scheduled_Input_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Setting_up_Scheduled_Input_Data.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There area two types of input data for the [Time Step Simulation](#time-step-simulation):

**Time Point-Based Data,** which is described in the [Loading Input Data](#loading-hourly-input-data) section; and,

**Scheduled Data,** which is specified for data that more naturally spans multiple time points rather than being defined at each time point. In this section we describe how to specify this type of input data.

Although it is possible to specify the operating conditions of a power system exclusively by quantities at each time point, there are several quantities whose specification would be redundant and would require significant memory storage if defined in this manner. Examples of such quantities are:

  - The status of a transmission line that is taken out of service on a particular date and time for maintenance.
  - The status of a generator, which follows a particular maintenance schedule.
  - A generator’s voltage set point that is different during the day or at night.
  - A scheduled transaction between to areas that has different MW set points applied at 10 am, 4 pm and 10 pm.
  - A capacitor connection status for a Mvar block that is used only during the day.
  - An industrial load that operates at different levels for different shifts.
  - A peaker generating unit that operates only during certain hours of the day
  - Any many others

All of these quantities can be specified by introducing the concept of **Schedule**. A schedule is a list of pairs **(Date Time, Value)**, where the value can be numerical, conditional (Yes/No or Closed/Open) or text. The Schedule can have any number of time points and can be periodic. The schedule defines the "shape" of how a quantity varies in time. In order to define a schedule, go to the [Schedules sub-page](26-time-step-simulation-part2.md#schedules-page) of the [Input page](#input-page), right-click on the grid and select **Insert New Schedule** to bring up the [Schedule Dialog](26-time-step-simulation-part2.md#schedule-dialog).

Once a schedule has been created, we can assign an object field, such as the status of a transmission line or the MW output of a generator to the schedule by means of a **Schedule Subscription**. The object field will follow the schedule "shape" in time. The use of Schedule and Schedule Subscription objects gives us great flexibility in specifying how quantities should vary. In particular, it is possible to assign many fields to the same schedule. In order to define a **Schedule Subscription**, go to the [Sched Subscriptions sub-page](26-time-step-simulation-part2.md#schedule-subscriptions-page) of the [Input page](#input-page), and right-click on the grid and select **Insert New Subscription** to bring up the [Schedule Subscription Dialog](26-time-step-simulation-part2.md#schedule-subscription-dialog).

An important feature of the Schedules is that their date/times do not need to match the date/times of the list of time points (time points listed in the [Summary page](#hourly-summary-page)). Suppose that your list of time points are defined hourly for the next day: 1am, 2am, etc. up to 11pm. You can schedule a particular action to take place at 2:35 am and see the results of that action in the next time point, i.e., 3 am. A special logic takes care of applying scheduled actions at appropriate time points asynchronously.
