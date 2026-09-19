---
title: "Transient Stability — Overview and Data (Part 2 of 2)"
part: "Transient Stability"
chapter_file: "36-transient-stability-overview-and-data-part2.md"
topics: 11
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Transient Stability — Overview and Data (Part 2 of 2)

Transient stability concepts, data management and model handling.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (11)**

- [Available Generation Control (AGC) Modeling](#available-generation-control-agc-modeling)
- [Transient Contour Toolbar](#transient-contour-toolbar)
- [Integration Techniques](#integration-techniques)
- [PlayIn Modeling](#playin-modeling)
- [User Defined Models](#user-defined-models)
- [Transient Stability Data Management](#transient-stability-data-management)
- [Transient Tab of Object Dialogs](#transient-tab-of-object-dialogs)
- [Case Info Menu](#case-info-menu)
- [Model Explorer](#model-explorer)
- [Block Diagrams](#block-diagrams)
- [Data from External files](#data-from-external-files)

---

<a id="available-generation-control-agc-modeling"></a>

## Available Generation Control (AGC) Modeling

*Source: [`Content/MainDocumentation_HTML/Available_Generation_Control_Modeling.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Available_Generation_Control_Modeling.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 19

Available Generation Control can be modeled in transient stability by defining an Area AGC model along with Generator AGC Controllers. The signals for this structure are shown in the following image.

![Transient Stability AGCSignals](images/Transient_Stability_AGCSignals.png)

AreaAGC Model assigned to an Area object

Initially there in only one Area AGC Model which has the following 8 fields.

|              |                                                                                                                                         |          |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Parameter    | Description                                                                                                                             | Units    |
| Bus          | Specification of the bus at which frequency measurement is taken                                                                        |          |
| Bias         | Frequency Bias \[MW/0.1Hz\]                                                                                                             | MW/0.1Hz |
| Deadband     | No response if ACE within thisdeadband                                                                                                  | MW       |
| PanicHighOn  | PanicMode is entered if the frequency goes above this                                                                                   | Hz       |
| PanicHighOff | If a panic mode is entered due to HIGH frequency, this is the frequency in Hz BELOW which the system must fall to exit the panic mode   | Hz       |
| PanicLowOn   | Panic mode is entered if the frequency goes below this                                                                                  | Hz       |
| PanicLowOff  | If a panic mode is entered due to LOW frequency, this is the frequency in Hz ABOVE which the system must recover to exit the panic mode | Hz       |
| UpdateTime   | AGC UpdateCycle Time in Seconds. AGC signals are updated at this interval                                                               | Seconds  |

Notes about the Area AGC Model

  - Area Frequency is measured at the bus indicated by the AreaAGC Model.
  - The ACE calculation uses the Bias and Deadband terms as well as the list of Area to Area Tie-Lines that exist in the power system model.
  - Panic Mode is a special feature that will cause the response of the various Generator AGC Controllers to change. When in Panic mode then generators with an AGC control model which has a mode of either LOCAL (2) or BASELOAD (3) will participate in AGC just like they were set to a mode of ON (1). Also, when in panic mode, the ACE calculation will no longer include the tie-line flow portion of the calculation meaning that the ACE is only concerned with returning the system to nominal frequency when in panic mode.

AGC update is done at user-specified interval of UpdateTime seconds (specificified in the AreaAGC). Within the numerical integration this is handled at the start of each on each time-step and thus appears algebraic to the differential equations. When the update is done it performs the following steps

1.  CalculateACE
2.  Call UpdateAGCSignal on each generator in the area
3.  Call RespondToAGCSignal on each generator in the area

This also requires an update of many other models which receive a MWReference input signal (such as Pref on most governor models), but this will be discussed below.

AGC ACE Calculation

The area designation in the power system model determine the list of area to area tie-lines. ACE attempts to bring tie-line flows back to the initial condition. The ACE Calculation is as follows

  - Normal: ACE = (MeasBusFreq - NominalFreq)\*10\*Bias + (SumTieFlows - InitialTieFlow)
  - Panic Mode: ACE = (MeasBusFreq - NominalFreq)\*10\*Bias

For both there is also a Deadband applied so that if the absoluate value of ACE is less than the deadband, then the ACE = 0.0.

Determination of which Generators to respond and Participation Factor Summation

Use the ACE value for the entire area, each generator in the area is then processed to determine whether the generator will respond and the summation of the participation factors. Below is some pseudo-code describing this response with each generator flagged as AGCActive as well as the summation PartFactSum maintained.

![Transient Stability AGCUpdateAGCSignals](images/Transient_Stability_AGCUpdateAGCSignals.png)

Then using this list of generators and summation, each generator responds to the ACE signal and the participation factor summation based on its AGC Controller which will be described next.

Generator AGC Controller Model

There are 2 primary types of AGC controllers: AGCSetpoint and AGCPulseRate. The AGCSetpoint controller will take the signals received from the AreaAGC model and interpret them as an immediate change in the MWSetpoint of the generator. The AGCPulseRate controller will take the signals received and instead either ramp up or ramp down its MWSetpoint at a predefined rate.

AGC Controller Mode

One thing which is common to the AGC Controller models however is the concept of a Mode for the controller. Each controller has an integer parameter called mode which can have 4 values which are interpreted as follows

  - 0 (OFF) : means the generator is ignored for AGC purposes (its MWSetpoint remains constant)
  - 1 (ON) : means the generator participates in AGC
  - 2 (LOCAL) : means the generator normally does not participate in AGC, but during Panic Mode it will participate
  - 3 (BASELOAD) : means it only participates if moving its reference pushes the generator back toward its initial value

AGCSetpoint

The AGCSetpoint model has the follow 5 fields.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Parameter</p></td>
<td><p>Description</p></td>
<td><p>Units</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Mode</p></td>
<td><p>Integer Value 0 (OFF), 1 (ON), 2 (LOCAL), or 3 (BASELOAD). See description above for details.</p></td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Default</p></td>
<td><p>Integer Value 0 (No, use specific values), 1 (get values from case)</p>
<p>If value set to 1, then PartFact, Pmax, and Pmin will be obtained from the power flow input data and stability record values are ignored</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PartFact</p></td>
<td><p>Participation Factor for us in AGC</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Pmax</p></td>
<td><p>Maximum Power reference signal output</p></td>
<td><p>MW</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Pmin</p></td>
<td><p>Minimum Power reference signal output</p></td>
<td><p>MW</p></td>
</tr>
</tbody>
</table>

AGCPulseRate

The AGCPulseRate model has the follow 8 fields.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Parameter</p></td>
<td><p>Description</p></td>
<td><p>Units</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Mode</p></td>
<td><p>Integer Value 0 (OFF), 1 (ON), 2 (LOCAL), or 3 (BASELOAD). See description above for details.</p></td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Default</p></td>
<td><p>Integer Value 0 (No, use specific values), 1 (get values from case)</p>
<p>If value set to 1, then PartFact, Pmax, and Pmin will be obtained from the power flow input data and stability record values are ignored</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PartFact</p></td>
<td><p>Participation Factor for us in AGC</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Pmax</p></td>
<td><p>Maximum Power reference signal output</p></td>
<td><p>MW</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Pmin</p></td>
<td><p>Minimum Power reference signal output</p></td>
<td><p>MW</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>PulseRate</p></td>
<td><p>Rate at which the MWReference signal changes</p></td>
<td><p>MW/Second</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PulseLength</p></td>
<td><p>Length of time that the pulse up or down occurs. This should normally be less than the Area AGC Model’s UpdateTime. Thus the UpdateTime may be 10 seconds and PulseLength is 2 seconds</p></td>
<td><p>Second</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>PulseLengthPanic</p></td>
<td><p>When Area AGC Model enters panic mode, then you can increase the length of the pulse.</p></td>
<td><p>Second</p></td>
</tr>
</tbody>
</table>

Response of Generator to AGC Signal

Each generator then responds based on PartFactSum calculated. The following is pseudo code for the AGCSetpoint and AGCPulseRate models

![Transient Stability AGCRespondToAGCSignals](images/Transient_Stability_AGCRespondToAGCSignals.png)

The following images demonstrate how the MWSetpoint of the geenerators respond for the two types of AGC Controllers.

![Transient Stability AGCRespondToAGCSignalsExamples](images/Transient_Stability_AGCRespondToAGCSignalsExamples.png)

Passing the new MWReference Signal

The new MWReference will then be passed to the appropriate generator model to respond. This will depend on which generator models are defined with the following precedence.

1.  A Plant Controller is defined and active (REPC\_A, REPC\_B)
2.  A Pref Controller is defined and active (LCFB1, WTGTRQ\_A)
3.  WT3P (special stabilizer model for first generation wind turbine models)
4.  A Governor model is defined and active (most of the dozens of governor types have a "Pref")
5.  Mechanical power for the active machine model will be changed appropriately
6.  If there isn't even a machine model, then the algebraic Electrical Power of the generator will be changed.

Taking a a MWReference signal an modifying a particular transient stability model is <span class="underline">unique</span> for each model. This is done by Simulator using algebra with the following assumptions.

  - Assume the generator is operating at steady state (nominal frequency)
  - Calculate Pref that would be needed when initializing the model from steady state if the MW output was equal to the new MWReference.

This makes the assumption that the AGC system is always trying to drive the system back to nominal frequency. It is important to realize that for some models it is not possible to do this calculation. For example, isochronous governor models (Rselect=0 or R=0 on GGOV1 governor for example. Let's use GGOV1 as an example.

![Transient Stability AGCMWReferenceUpdateGGOV1](images/Transient_Stability_AGCMWReferenceUpdateGGOV1.png)

Using these dependencies, the new value of Pmset and Pref for the GGOV1 model are updated as shown in the following pseudo-code.

![Transient Stability AGCMWReferenceUpdateGGOV1 Psuedo](images/Transient_Stability_AGCMWReferenceUpdateGGOV1_Psuedo.png)

---

<a id="transient-contour-toolbar"></a>

## Transient Contour Toolbar

*Source: [`Content/MainDocumentation_HTML/Transient Contour Toolbar.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient Contour Toolbar.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Contour Toolbar is a special toolbar for generating a time-sequenced series of contour images based on the transient stability results. The results of the transient stability must have already been calculated and either [stored to RAM](37-transient-stability-analysis-dialog-part1.md#storage-to-ram) or [stored to Hard Drive](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive) as discussed in the [Results Storage](37-transient-stability-analysis-dialog-part1.md#results-storage). When generating a plot, an attempt will be made to retrieve from the results [stored to RAM](37-transient-stability-analysis-dialog-part1.md#storage-to-ram). If results are not available for a particular plot series in RAM, then results will be retrieved from those values [stored to Hard Drive](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive). If they are still not available then a plot will be generated which omits any plot series for which data can not be retrieved.

The Transient Contour Toolbar looks as follows.

![Transient Stability Contour Toolbar](images/Transient_Stability_Contour_Toolbar.gif)

This toolbar can be opened in one of two ways

1.  Click the **Show Transient Contour Toolbar** option from the [Transient Stability Case Info Menu](#case-info-menu).
2.  Click the **Show Transient Contour Toolbar** button at the bottom of the [Transient Stability Analysis Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

The various buttons on this table are described from left to right below.

Close

Click this button to hide the Transient Contour Toolbar.

Reset

Click this button to reset the time of the data being contoured back to the start time stored with the results. A contour image is automatically generated at this start time then.

Back

Click this button to move the present time of the data being contoured backward the number of stored time points specified by the **Step per Animate** option.

Play

Click this to continue moving the contour visualization forward in time with each animation frame determined by the **Steps per Animate** option

Forward

Click this button to move the present time of the data being contoured forward by the number of stored time points specified by the **Step per Animate** option.

Pause

Click this button to

Steps per Animate

The entry of this integer value determines how time progresses when clicking the other buttons here.

Present Time

Shows the present time of the data being visualized by the contour

Start and End Time

Show the start and end time of the data available for visualization from the results.

Device Type and Field

Modifying the **Device Type** and **Field** in tandem determines which objects are to have values contoured and which field determines the contour value. The devices available will be an overlap between those devices which can by contoured and those devices for which results can be saved in the transient stability tool. This list of available fields will look very similar to the list available on the [Plot Designer](37-transient-stability-analysis-dialog-part2.md#plot-designer).

Options

Clicking this button shows the [Contour Options Dialog](17-oneline-view-printing-and-contouring.md#contouring-options) for a special Transient Contour Value field. This value will be populated according to the **Device Type** and **Field** options above.

---

<a id="integration-techniques"></a>

## Integration Techniques

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Integration.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Integration.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The simulation of a transient stability event involves solving a set of differential and algebraic equations. PowerWorld Simulator uses a second order Runge-Kutta integration method to simulate the differential equations. A few special topics related to the integration method are as follows.

Handling Ignored States

In a commercial software package, each model must be implemented in a generic manner which accounts for all possible configurations that model may take. Because of this, Simulator must implement the maximum number of system state variables possible for each model. The software must then determine from the input data whether or not to ignore a particular state. As an example consider the ESAC1A exciter shown in the block diagram below.

![Transient Stability Data BlockDiagrams](images/Transient_Stability_Data_BlockDiagrams.gif)

If the parameters Tc and Tb are both entered with a value of zero, this indicates that the state associated with the lead lag block will not be a dynamic state and instead will always be equal to the input value. Simulator's integration engine automatically handles these situations and the derivative of particular states will be reported as Ignored in the interface in these situations as shown in [Transient Stability Data: Object Dialogs](#transient-tab-of-object-dialogs). Also the propagation of values will automatically be handled. For example, any change to the input to the Tc block will immediately propagate to the output of that block.

Sub-Interval Integration

Like most commercial transient stability software, PowerWorld Simulator uses an explicit integration approach that alternates between solving the differential equations and solving the algebraic network power balance equations. This approach can be quite useful provided there are no model dynamics with time constants faster than the transient stability time step (using ½ cycle). However for some transient stability models, such as the EXST1 exciter model, and during induction motor startup, these conditions can be violated. To avoid numerical instabilities with these models, we have implemented a technique known as sub-interval integration. When using this approach, within each transient stability time step the differential equations for some specific models are integrated using a much smaller time step with the assumption that during these shorter time steps the algebraic (network) variables remain fixed. This approach has proven to be quite successful in integrating very fast dynamics.

As an example, the two figures below show the internal sub-transient voltages for an induction motor startup for one second of simulation time. In order to show the fast voltage transients that can occur during motor startup, the first figure is integrated with a very small time step (1/20 cycle) without the subinterval integration. Note the oscillations that occur during the first 0.1 seconds, with a frequency on the order of 60 Hz. The second figure repeats the first except using the new sub-interval functionality and a time step of one cycle. Because of the longer time step, the faster oscillations are no longer visible, but the response is numerically stable and is quite similar to the case with the much smaller time step. Without subinterval integration this case is numerically unstable with a time step of 1/5 cycle. Two key advantages of the subinterval integration approach with the longer time step are 1) that network algebraic equations are evaluated much less frequently, and 2) the subinterval integration is only applied to the handful of models for which it is required.

![Transient Stability Integration SubInterval](images/Transient_Stability_Integration_SubInterval.gif)

For Sub-Interval models in PowerWorld information [Go Here](52-additional-linked-topics-part3.md#transient-stability-numerical-integration-sub-interval-models).

---

<a id="playin-modeling"></a>

## PlayIn Modeling

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Overview_PlayIn.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Overview_PlayIn.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PlayIn models are used to play input data into the transient stability tool at a specified time. The models are set to be used as a generator, a reference signal or a governor. Respectively there are three types of PlayIn models available: PlayInGen, PlayInRef, PlayInGov and PlayInEx. The data for the models can be set manually using the **PlayIn Configuration** model type inside the Transient Stability folder on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

In the PlayIn Configuration model type you can insert a PlayIn model signal by its name and specified Offset to be applied when play in that particular model. To insert a new PlayIn model, right click on the PlayIn entry and choose Insert. This will open a dialog to enter the PlayIn model Name. Then after pressing OK the PlayIn Time offset can be specified. To insert data to a particular PlayIn Model right click on the entry and choose Show Dialog. This will open another dialog with a case information display to enter the data for the PlayIn Model. The Dialog have the PayInName which can be rename and also the Time Offset can be changed. Below there are two tabs: Signals Info and Signals.

In the Signal Info tab you specified the Signal Index as well as a respective name, scale, offset and filter. These signals are the signals that the PlayIn Model will have. For example, a PlayIn generator will need a signal for the amplitude of the Thevenin source and the frequency of the generator. The scale is used to scale the signal to a particular value. The offset will be applied to the signal to match the initial condition of the particular signal established in the initialization of the model. The filter values is a time constant, such as for a filter block \[1/(1+sT)\], used to filter the signal.

In the Signal Tab the signal value can be specified for the particular signal index. To insert a new signal time right click in an entry and choose insert. This will open a dialog to specify a time for the signals.

The other easy way to enter PlayIn signals and new PlayIn models is to use an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) with the desired signals and the desired data values, offset, scale and filter values.

PlayInGen Model

The [PlayInGen](38-ts-models-machine.md#playingen) model is a generator model to play in data to the transient stability tool. The PlayIn Gen models a generator Thevenin voltage amplitude source in p.u. and the frequency amplitude in p.u.

The model can be entered in the generator dialog Machine Models [Stability Tab](#transient-tab-of-object-dialogs) and will required the following:

  - PlayIn Model Signal applied for the particular generator.
  - VIndex: Index of the Thevenin Voltage amplitude signal.
  - FIndex: Index of the frequency amplitude signal.
  - Rth: The Thevenin resistance of the generator in p.u.
  - Xth: The Thevenin reactance of the generator in p.u.

PlayInRef Model

The [](42-ts-models-generator-other-part1.md#playinref)[PlayInRef](https://www.powerworld.com/WebHelp/Content/TransientModels_PDF/Generator/Others/Plant%20Controller%20PLAYINREF.pdf) model is a voltage regulator and governor reference model to play in data to the transient stability tool. The PlayInRef models a voltage regulator reference voltage in p.u. and the governor reference Pref (Speed-load reference) in p.u.

The model can be entered in the generator dialog Other Models [Stability Tab](#transient-tab-of-object-dialogs) and will required the following:

  - PlayIn Model Signal applied for the particular generator.
  - VIndex: Index of the voltage regulator reference signal.
  - FIndex: Index of the governor reference signal.

PlayInGov Model

The [PlayInGov](40-ts-models-governors-part3.md#playingov) model is a governor model to play in data to the transient stability tool. The PlayInGov models a governor mechanical power (Pmech) in p.u.

The model can be entered in the generator dialog Governors [Stability Tab](#transient-tab-of-object-dialogs) and will required the following:

  - PlayIn Model Signal applied for the particular generator.
  - FIndex: Index of the governor Pmech reference signal.

PlayInEx Model

The [PlayInEx](39-ts-models-exciters-part3.md#playinex) model is a n exciter model to play in data to the transient stability tool. The PlayInEx models an exciter field voltage in p.u.

The model can be entered in the generator dialog Exciters [Stability Tab](#transient-tab-of-object-dialogs) and will required the following:

  - PlayIn Model Signal applied for the particular generator.
  - FIndex: Index of the exciter field voltage signal.

---

<a id="user-defined-models"></a>

## User Defined Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_User_Defined_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_User_Defined_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

User Defined Models (UDMs) are transient stability models that can be shared between users and programs. Each UDM is a dynamic link library (DLL) which contains code for implementing the model. The UDM process is the following:

  - Engineers design a model.
  - A developer writes a DLL for the model, creating the functions needed by the calling application (Simulator). The model is a black box to the calling application.  The inner details of the DLL are completely separate code.
  - Users of the DLL have instances of the model in their case. The user's interaction with this model is the same as with in-built models.

Simulator can call DLLs developed in languages including C++, Fortran, and Pascal using standard calling conventions. Other calling applications may use the same DLLs. The UDM DLLs necessarily have a well-defined interface with the transient stability software. It is critical that the user defined model developer adhere exactly to the specifications of this interface. Details of this interface are documented in PowerWorld's User Defined Model Development Guide for those seeking a more in-depth understanding of model interactions. Contact PowerWorld Corporation at support@powerworld.com for more information.

User Defined Model data is managed on the [Options: User Defined Models](52-additional-linked-topics-part3.md#transient-stability-dialog-options-user-defined-models) tab of the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). User defined models are supported for the following types of objects.

Generator-Related Models

  - Machines
  - Exciters
  - Governors
  - Stabilizers

Load-Related Models

  - Load Characteristics

Multi-Terminal DC Record - Related Models

  - Record Level Model (outputs a current setpoint to each DC converter)
  - Multi-Terminal DC Converters (outputs a cosine of the firing angle at each converter)

---

<a id="transient-stability-data-management"></a>

## Transient Stability Data Management

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Data_Management.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Data_Management.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transient Stability tool introduces a very large amount of additional input data which must be entered to define the dynamic models of the system. Interaction with this data is completely integrated with the rest of PowerWorld Simulator and is done primarily through the following methods

  - [Stability tab of the Generator, Load, DC Line, etc... Dialogs](#transient-tab-of-object-dialogs)
  - [Transient Stability Case Information Drop-Down](#case-info-menu)
  - [Transient Stability Folder in the Model Explorer](#model-explorer)
  - [Transient Stability Block Diagrams](#block-diagrams)
  - [Reading/Writing Transient Stability Data to various File Formats](#data-from-external-files)

Details on these methods are found in the individual topics.

---

<a id="transient-tab-of-object-dialogs"></a>

## Transient Tab of Object Dialogs

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Data_ObjectDialogs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Data_ObjectDialogs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

On the various option dialogs for devices such as Generators, Load, Switched Shunts, DC Lines, and Transmission Lines, there will be a tab labeled Stability. On this tab you will be able to define the appropriate dynamic models for the device. An example of the generator dialog's Stability tab is shown as below.

![Transient Stability Data GenObjectDialog](images/Transient_Stability_Data_GenObjectDialog.gif)

All of these tabs have a similar layout which includes the following attributes

Insert Button

Clicking this button to insert a new model. A dialog will appear prompting you to choose which specific type of dynamic model to add for the object.

Delete Button

Clicking this button to delete a model.

Type Drop-Down

Shows a list of the presently defined models for this class. A model which is active will say *Active* before giving the name of the model. Normally there will only be one model of each class, but Simulator does permit you to define multiple models. For some models only one can be active at a time.

Active Check-box

There will be a check-box to make a dynamic model *Active* or *Not Active*. When a model is not active then it will be included in the dynamic simulation. Also note that for some classes of models you can have only one active model at a time. Governors, Exciters, Machine Models, and Stabilizers for generators all behave this way, however if you're defining a relay model you may have more than one active.

Show Block Diagram Button

When clicking this button, the [BlockDiagrams.pdf Adobe Acrobat file](#block-diagrams) will automatically be opened which contains all the dynamic model block diagrams. This PDF file will automatically be navigated to show the block diagram of the presently model.

Parameter List

At the bottom of the tab is a panel with numerical edit boxes allowing you to define all the input parameter values for the model. Next to each edit box is the name of the parameter. In addition to this if you hover the mouse over the edit box a hint will appear with a more detailed description of the parameter. The edit box, the non-default parameters will be highlighted as bold.

Special Options only on the Generator Dialogs

Set to Default

On the generator dialog there are options to change the parameters to PowerWorld's default settings.

Option to enter values on either the Device MVA base or the System MVA base

Normally per unit values for stability data are entered on the MVA base of the device. If you would like to change to enter data on the System MVA base instead, change this option. (Note: this option only affects the dialog entries. Entries in the case information displays will always be on the device MVA base.)

Several Model Class Tabs

Generator dialogs will list sub-tabs for Machine Models, Exciters, Governors, Stabilizers, and Other Models. Each of these sub-tabs has the same layout.

Step-up Transformer Tab

Information about an assumed step-up transformer may also be included with the generator and can be entered here.

Terminal and State Tab

After the transient stability run has been initialized on the Transient Stability Dialog, you may go to the Terminal and State Tab to View information about the terminal values and dynamic states. Under this tab will be several more sub-tabs as follows

**Bus/Setpoint Values**: Shows voltage and current on the system MVA base at the terminal bus. Shows the MW, Mvar and MVA being injected into the system at the terminal bus as well. Also shows the Exciter Setpoint (Vref) and Governor Setpoint (Pref) values if appropriate.

**Terminal Values**: Shows the Terminal Voltage and Current on the device per unit base. Mechanical MW, Accelerating MW, and Terminal MW. Also shows information about the internal rotor angle, Frequency Deviation (omega), and acceleration. Also shows information about the Field Voltage and Current and the Direct and Quadrature axis terminal and internal voltages and currents

**Several Model Class State Tabs**: tabs for Machine Models, Exciters, Governors, and Stabilizers will be available. Each will contain a list of the present states for the model as well as the derivatives of each state. For the derivative values, the states are sometimes ignored (such as when a time constant is zero). If this is true for the model, the derivative will be listed as *Ignored*.

Create VCurve

Creates a curve of 50 points intervals of the Field Voltage and the Field Current of the generator in reciprocal and non-reciprocal values. To get the results it will used the current terminal of the bus and the minimum MW of the generator and it will vary the MVar of the generator from the minimum to the maximum MVar. It will repeat the same procedure with the present MW and the maximum MW of the generator.

Special Options only on the Load Dialog

Type Drop-Down Modification

Because for a load model, the model can be inherited from the bus, owner, zone, area or system, the model listed under the Type drop-down may not be associated directly with the Load object. If this is the case the model list will show the string *Inherited*. For inherited models you will not be able to edit the Parameter List directly. To edit the parameter list you will need to go to the dialog for that particular object in the [Transient Stability portion of the Model Explorer](#model-explorer).

Special Options only on the Branch Dialog for Line Relays

Show Relay Zones

Many line relays are impedance type relays which have a specified geometric circle, lens, tomato, or rectangular characteristic. For these relays there will be an extra button Show Relay Zones. Click on this button to display a mho circle plot showing the relay zones in the Apparent R-X plane. Note also that various points showing the location of the impedance of the actual branch, as well as the forward reach points and percentages will be shown.

Set Device ID

![Transient Stability Dialog DeviceID](images/Transient_Stability_Dialog_DeviceID.gif)

Many Relay model allow to have multiple relays at both ends of the branch. The Set Device ID will let you modify the DeviceID from the dialog for those line relays.

When you press the Set Device ID button the following message box will appear and there you could enter the new Device ID. It will only rename the Device ID if the new Device ID does not exists. If the Device ID already exists then the following message will appear: "A Device ID (ID) already exists at From/To end (Line Name). Please Modify that particular (Relay Name)relay."

---

<a id="case-info-menu"></a>

## Case Info Menu

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Case_Info_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Case_Info_Menu.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Stability Case Info menu is available by selecting **Stability Case Info** in the **Transient Stability (TS)** ribbon group on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab.

![Ribbon Add Ons Transient Case Info Menu](images/Ribbon_Add_Ons_Transient_Case_Info_Menu.gif)

The menu provides direct access to several case information displays that show default columns related to input and output of the transient stability tool. There are also options available for loading and saving transient stability models.

Transient Stability

Choose this option to open the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

Show Transient Contour Toolbar

Choose this option to make the [Transient Contour Toolbar](#transient-contour-toolbar) visible.

Case Information\\Exciters, Governors, Machine Models, Stabilizers, Load Characteristic Models, Load Relays, Other Stability Models...

Choosing any of these options will open a case information display for the appropriate model type. This same information can be accessed through the **Transient Stability** folder on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The stability case information displays can be used to change and define new models with the case. For a more complete description of the Model Explorer interaction with the transient stability models, see the [Transient Stability Model Explorer](#model-explorer) help topic.

Models in Use

Choose this option to view a summary of transient stability models defined in the case. The summary includes the model name, whether the model is active or inactive, and whether or not the model is fully supported in Simulator. (For a small number of models, the model can be read by Simulator but is not actually supported for stability simulation. These models are marked as Fully Supported = NO).

![Transient Stability ModelsInUse](images/Transient_Stability_ModelsInUse.gif)

Generator Model Use

Choose this option to view a summary of all generators in the case and any stability models that have been defined for each generator. Inactive models are shown in parenthesis. Use toggle to change active status of models. If multiple models exist for a particular model type, they are listed separated by commas.

![Transient Stability Generator Model Use](images/Transient_Stability_Generator_Model_Use.gif)

Load Model Use

Choose this option to view a summary of all loads in the case and any stability models that have been defined for each load. Inactive models are shown in parenthesis. Use toggle to change active status of models. If multiple models exist for a particular model type, they are listed separated by commas.

![Transient Stability Load Model Use](images/Transient_Stability_Load_Model_Use.gif)

Models Supported Status

Choose this option to view a list of all models which can be created in PowerWorld Simulator along with designations regarding what other software supports these models, and whether Simulator is able to include these models in the stability simulation.

![Transient Stability ModelSupportStatus](images/Transient_Stability_ModelSupportStatus.gif)

DYD Extra Record

Choose this option to view a list of the DYD Extra Records transient models that we do not have support for in PowerWorld but was read and stored when a dyd file was loaded in PowerWorld. Example of DYD Extra Records are the dc line models of vscdc and dcmt that now are read and stored as a DYD Extra Record object. These records only contain the string data that was read from the dyd file and are also written to a dyd file if the user decide to save the dynamic models into a dyd file. The DYD Extra Record are also saved in the pwb file. The records can only be deleted from the table and can only be added by reading a dyd file or loading an aux file with a DYDExtraRecord object.

Load/Save Transient Stability Data

Choose the appropriate option to save or load transient stability model data in the desired format. Models are supported in the Simulator auxiliary file format (\*.aux), BPA dynamics data format (\*.swi), GE dynamics data format (\*.dyd or \*.dyc), GE OTGD data (\*.otgd ) and PTI dynamics data format (\*.dyr). MCRE \*.rwm files, MTRLD \*.dat files, GNET \*.idv files, and BASEGEN \*.dat files can also be applied. For more details about loading the GE DYD file see the [Reading DYD files](#data-from-external-files) help topic.

Insert Transient Stability Data

Choose to [Auto Insert DistRelay Models](52-additional-linked-topics-part1.md#auto-insert-transient-contingencies-dialog-2).

Clear All Transient Stability Data

Choose this option to delete all transient stability models.

---

<a id="model-explorer"></a>

## Model Explorer

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Data_Model_Explorer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Data_Model_Explorer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

On the Explore pane on the Model Explorer, there is a folder for Transient Stability. Immediately under this folder is a Summary folder containing links to Generator Model Use, Model Support Status, and Models in Use. These three features are discussed in more detail in the [Transient Stability Case Info Menu](#case-info-menu) topic. Under this folder is a list of the various classes of models such as Exciter, Stabilizer, Load Characteristic, etc. which are available in the transient stability tool. When choosing one of these entries, the right portion of the Model Explorer will be populated with a case information display showing models of that class. In addition there will be a new pane showing the specific types of that class of model. This pane has the following attributes

  - Gray text indicates a model type which is not presently used by any device in the present power system case
  - The number in parenthesis next to the model name indicates the number of models of that type which are used by a device in the present power system case
  - Green icons indicate that the model is fully supported by the transient stability numerical integration Simulator.
  - Red icons indicate that the model is not supported by the transient stability numerical integration in Simulator. When encountering a new model, PowerWorld will first configure the ability to define the model as well as read and write it from various file formats. After that the model will be implemented. Our intention over time is that all red icons will become green icons.
  - At the bottom of the pane is a set of 4 check boxes showing **PW only**, **BPA**, **PTI**, and **GE**. These indicate which model types to show in the list depending one whether that model is supported by another software package. If you want to see only models which are support by the BPA IPF program then uncheck the other three check boxes and check the BPA check box. For a complete listing of all models and where they are supported see the *Summary\\Model Support Status* in the Model Explorer.
  - The list of specific types will always include an entry at the top of **All** which lists all the models of that class. Below this will be a list of all the specific types of that model class. As you click on the various entries in the pane, the case information display will be populated accordingly.
  - At the bottom are buttons to **Save** or **Load** [dynamic data from an external file](#data-from-external-files).

The following shows such a listing for the generator Exciter models.

![Transient Stability Model Explorer](images/Transient_Stability_Model_Explorer.gif)

All

On the listing which shows all models, there will only be columns which show identifiers for the object as well as two generic columns common to all models. The **Fully Supported** column is a YES/NO column which shows whether the model is supported by Simulator's transient stability numerical integration (the fast majority will say YES). The **Device Status** column will show either *Active* or *Not Active* depending on whether the device is specified to be used in the numerical integration.

Specific Model Type

When you choose a particular model type, additional columns will appear showing all the input parameters for that model type. This is depicted in the image below.

![Transient Stability Model Explorer Parameters](images/Transient_Stability_Model_Explorer_Parameters.gif)

Show Block Diagram Button

At the top-right of the case information displays listing models will be the Show Block Diagram button. When clicking this button, the [BlockDiagrams.pdf Adobe Acrobat file](#block-diagrams) will automatically be opened which contains all the dynamic model block diagrams. This PDF file will automatically be navigated to show the block diagram of the presently selected model in the case information display.

Load Characteristic Models

Load models in Simulator are configured to apply to either a load, bus, owner, zone, area, or the entire case. This is discussed in more detail in [Transient Stability Overview](36-transient-stability-overview-and-data-part1.md#transient-stability-overview). As a result you will see special folders at the bottom of the specific model type list for *Load-Specific*, *Bus-Specific*, *Owner-Specific*, *Zone-Specific*, *Area-Specific*, and *System-Specific*.

![Transient Stability Load Characteristics](images/Transient_Stability_Load_Characteristics.gif)

---

<a id="block-diagrams"></a>

## Block Diagrams

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Data_BlockDiagrams.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Data_BlockDiagrams.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

As part of the help documentation, Simulator includes an Adobe Acrobat File names *Block Diagrams.pdf* which contains all the block diagrams of dynamic models implemented in PowerWorld Simulator. This file is also posted on our [website](https://www.powerworld.com/WebHelp/files/Block-Diagrams-18.pdf). This file can be automatically opened and the appropriate block diagram navigated to from both the [Transient Stability Case Information Displays](#model-explorer) and from the [Stability Tab on the Generator, Load, DC Line, etc... dialogs](#transient-tab-of-object-dialogs). The format of these block diagrams is very standardized. The block diagram will appropriately label all the input parameters for the model type. There will also be a list of the dynamic states which exist for the model. These states will be labeled by number with a circle the number. In addition there will be a comment regarding whether another software product supports this model. The following is an example for the ESAC1A excitation system.

![Transient Stability Data BlockDiagrams](images/Transient_Stability_Data_BlockDiagrams.gif)

---

<a id="data-from-external-files"></a>

## Data from External files

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Data_GEDYD.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Data_GEDYD.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transient Stability data can be read from several external file types including a PowerWorld Auxiliary File (AUX), PTI File (DYR), GE File (DYD), or BPA File (SWI). Access for loading these files is found in several places within Simulator.

  - Menus within the [File menu](03-cases-files-and-formats.md#file-menu)
  - Bottom of the specific model pane on the [Transient Stability portion of the Model Explorer](#model-explorer),
  - Options within [Stability Case Info Menu](#case-info-menu),
  - Buttons at the bottom of the [Transient Stability Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

Save to Auxiliary

in the will prompt for a filename in which to save an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux). Use this option to store any results and settings that need to be retained for future use or use with different power flow cases. Transient stability-specific results and option settings can optionally be saved with the PowerWorld binary file (\*.pwb).

Load Auxiliary

Clicking this button will open a dialog to allow the user to select an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) to load. This is intended to be used for loading any relevant option settings to be used during the transient stability analysis. The dialog will be updated according to the option settings loaded from the file.

Save GE DYD Data, Save GE DYD Data with Options, Save PTI DYR Data, Save BPA SWI Data

Choosing this option will allow you to save models to the appropriate file format. Note that only models which are supported by the specific format will be saved to the file. For a list of which models are supported by which format see the [Model Support Status case information display](#case-info-menu). When saving a DYD file, the model names are always stored lower case. When saving a DYR file, a GNET \*.idv and a BASEGEN \*.dat are also saved. The filename and path used are the same as for the DYR file, except "\_GNET" and "\_BASEGEN" are appended to the file names. Selecting "Save GE DYD Data with Options" allows the options to save data of only records modified in difference case, add a bus filter and sort generators, loads and switched shunts.

Load GE DYD Data, Load PTI DYR Data, Load BPA SWI Data

Choosing this option will allow you to load models from the GE DYD file format. Selecting the option "DYR Data with Options" will allow you to specify a MCRE \*.rwm file to split up generators, a MTRLD \*.dat file to split up motors, a GNET \*.idv file to disable generator models, and a BASEGEN \*.dat file to specify the Governor Response Limits flag for generators. "Load Specific PTI DYR Helper Files" allows you to apply those files on their own.  
When loading from a GE DYD file a few special features have been implemented.

Load WECC Switch Data

Choosing this option will allow you to load transient contingencies in the WECC file format used with WECC switching processors. These files generally have a \*.swt extension and describe the switching action desired and the time at which it occurs.

GE DYD: Special Handling for the Generator Baseload Flag

When loading GE EPC files, a flag exists in the EPC file with each generator record called the "Baseload flag". This field determines how governor limits are handled during a transient stability run. This feature is supported using Simulator generator field called *Transient Stability\\Governor Response Limits* . For more information see the [Transient Stability Overview: Generator Models](36-transient-stability-overview-and-data-part1.md#generator-models) topic.

GE DYD: Special Handling of EPCMOD models

In many example DYD files which PowerWorld has encountered, there are EPCMOD records which represents a user-defined model htat represent a Series Capacitor Relay and a Capacitor Relay Model. Because these models were so common, PowerWorld added two new kinds of relays to our model suite. The CAPRELAY model can be assigned to a switched shunt record. This represents a relay which can open and close a switched shunt based on a definite time relay measuring voltage. A SERIESCAPRELAY model can be assigned to a branch and used to bypass and place back inservice a series capacitor branch.

When parsing the DYD file, Simulator will detect an EPCMOD record and if that record refers to the EPCL program "MSC01.p", then we automatically assume it represents a switched shunt relay and create a CAPRELAY model. An appropriate log message will be written indicating this has occurred such as the following: "Info: An EPCMOD record using "MSC01.P" was found. Simulator will attempt to read following as a CAPRELAY: 30.000 1.2000".

When parsing the DYD file, Simulator will detect an EPCMOD record and if that record refers to the EPCL program "MSC02\_R1.p", then we automatically assume it represents a series cap relay and create a SERIESCAPRELAY model. An appropriate log message will be written indicating this has occurred.

GE DYD: Special Handling of GENCC models

In the DYD often represent cross-compound generators in a special manner. A cross-compound generator represents two generators which both operate off the same steam plant. In a DYD file a cross-compound plant will be represented by 2 machine models, 2 exciters, 2 stabilizers, and 1 governor. In DYD files, the governor will be either the IEEEG1 or CRCMGV governors. Ideally, the power flow model represented by the EPC file will model these two generators explicitly and thus the DYD file will refer to the two generators when specifying the machines, exciters, stabilizer and governor. The DYD file however also supports a special machine model called the GENCC which is really just a GENTPF model but it signals to the tool reading the DYD file that two generators in the DYD file may represent one generator in the EPC file.

To accommodate this situation, Simulator's DYD parser has been written to first go through the entire DYD file and look for any bus which has only one generator in the existing case (EPC file), but the DYD file has 2 GENCC records at the bus with IDs that do NOT match any existing generator. If this situation is found, the user will be asked whether they would like to automatically split the existing generator into two generators to accommodate this modeling. If you choose yes, then the case will be permanently modified to split the generators into two. An appropriate log message will be written indicating this has occurred such as the following: "Info: New generator created at ALAMT3 G (24003) \#L and existing generator ID changed to \#H because 2 GENCC records found for Bus ALAMT3 G (24003) with IDs "H" and "L", but only one generator exists in the case at this bus with id "3"."

Also note that the GENCC records in the DYD file have parameters Pfac and Qfac which determine the percentage of MW and Mvar assigned to each generator. When the generators are split into 2 units, the following fields are multiplied by appropriate normalized Pfac and Qfac values: MW output, Max MW, Min MW, Mvar output, Max Mvar, and Min Mvar. The MVABase will also be multiplied but only if the GENCC record did not include this as part of its definition (normally it is included in the DYD file).

GE DYD or PTI DYR Data: Special Handling of Saturation Functions (SE)

When reading in a DYD or DYR file, there is an option regarding how to treat saturation functions for which the magnitude of SE1 and SE2 are backwards. This option is set to "Flip Values" when reading a PSSE DYR file to match that treatment. This option is set to "Ignore Saturation" when reading a PSLF DYD file to match that treatment.

GE DYD: Read DYD file containing devices identified by label.

GE DYD: Reading of the AMETA record from a DYD file to indicate storage of angle information to transient stability results.

GE DYD: When the IFMON record is encountered all our options regarding storing results to include the MW and Mvar flows on interfaces are modified.

GE DYD: A check at the end of reading a DYD file to determine if there are loads which do not have any static/algebraic stability models assigned to them. If this is the case, then messages are written to the log notifying the user that all loads that do not have static load models will default to a "Constant Current P, Impedance Q". Also checking is done to see if there are ALWSCC models assigned to some areas but not others, and if this is the case then log messages are written to notify the user that some areas do not have ALWSCC models and list those areas.

GE DYC: Appending changes

When loading files with the extension ".dyc", the contents are automatically appended to the existing models.
