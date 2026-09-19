---
title: "Additional Linked Topics (Part 2 of 3)"
part: "Reference"
chapter_file: "52-additional-linked-topics-part2.md"
topics: 17
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Additional Linked Topics (Part 2 of 3)

Topics reachable from links inside the manual but not listed in the help system's table of contents.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (17)**

- [Sparklines](#sparklines)
- [Switched Shunt SVC Control Mode](#switched-shunt-svc-control-mode)
- [Switched Shunt SVC Control Mode and Controllable Shunts Algorithm](#switched-shunt-svc-control-mode-and-controllable-shunts-algorithm)
- [Switched Shunt SVC Control Mode and Transient Simulation](#switched-shunt-svc-control-mode-and-transient-simulation)
- [TemperatureBasic1](#temperaturebasic1)
- [Transient Stability Analysis Options: Remedial Action Validation](#transient-stability-analysis-options-remedial-action-validation)
- [Transient Stability Analysis Options: Valid Remedial Actions Fields](#transient-stability-analysis-options-valid-remedial-actions-fields)
- [Transient Stability Analysis: Areas Validation Parameter Check](#transient-stability-analysis-areas-validation-parameter-check)
- [Transient Stability Analysis: Exciters Validation Parameter Check](#transient-stability-analysis-exciters-validation-parameter-check)
- [Transient Stability Analysis: Generator Machines Models Validation Parameter Check](#transient-stability-analysis-generator-machines-models-validation-parameter-check)
- [Transient Stability Analysis: Generator Other Models Validation Parameter Check](#transient-stability-analysis-generator-other-models-validation-parameter-check)
- [Transient Stability Analysis: Governors Validation Parameter Check](#transient-stability-analysis-governors-validation-parameter-check)
- [Transient Stability Analysis: Line Relays Validation Parameter Check](#transient-stability-analysis-line-relays-validation-parameter-check)
- [Transient Stability Analysis: Line Shunts Validation Parameter Check](#transient-stability-analysis-line-shunts-validation-parameter-check)
- [Transient Stability Analysis: Load Characteristics Validation Parameter Check](#transient-stability-analysis-load-characteristics-validation-parameter-check)
- [Transient Stability Analysis: Stabilizers Validation Parameter Check](#transient-stability-analysis-stabilizers-validation-parameter-check)
- [Transient Stability Analysis: Switched Shunts Validation Parameter Check](#transient-stability-analysis-switched-shunts-validation-parameter-check)

---

<a id="sparklines"></a>

## Sparklines

*Source: [`Content/MainDocumentation_HTML/Sparklines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Sparklines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Sparklines are small character-sized graphics used to provide a quick representation of numerical information. They are used to represent the general shape of a value over time in a condensed form. They can be displayed instead of a field value when showing a field on a oneline diagram. Because they are only useful with a series of information, they can currently only be used with transient stability results.

Geographic Data Views also allow showing sparklines instead of field values. More information about how to use sparklines with [geographic data views](04-model-explorer-and-case-information-part3.md#geographic-data-view) can be found with that topic.

Adding Sparklines from Oneline Field Dialogs

Oneline fields that allow the use of sparklines will contain a **Draw Sparkline** checkbox on their field option dialogs. This option will be located near the **Find Field** button that allows selection of the field to show. Sparklines are only allowed when using a field with the **Select a Field** option. When the **Draw Sparkline** checkbox is checked, the list of fields that are shown in the Choose a Field dialog and the field dropdown are limited to those fields that can be used with sparklines.

Additional options will appear on the field dialog when the **Draw Sparkline** checkbox is checked. These allow modification of how the sparkline is rendered.

Edit Sparkline Style

Click this button to open the Sparkline Style dialog. Typically the same style will be used for all objects of the same type that are showing the same field. See the **Sparkline Style Dialog** topic below for more information on how to define the style.

Style Name

Shows the name of the Sparkline Style being used. This field might be blank even though a style has been assigned. Typically the same style will be used for all objects of the same type that are showing the same field. If this situation a name does not have to be assigned to the style. Different styles for the same object type for the same field will require a unique name.

Override Ymin and Ymax with

Defaults for the Ymin and Ymax values shown on the y-axis of the sparkline will be determined automatically from the data that is being displayed. To override these defaults with user-specified values, check the box next to the correct limit, **Use Ymin** or **Use Ymax**, and specify the new value. The Ymin and Ymax values can be overridden.

Limits Actually Used

These values are informational only and show the limits of the data displayed on the sparkline.

Get Sparkline Values

Click this button to open a dialog showing the values being displayed on the sparkline.

Sparkline Style Dialog

The style of a sparkline determines how the chart is rendered and the limits used within the chart axes. Sparkline styles are defined with the oneline diagrams on which they are used and can be different for multiple onelines open with the same case.

The sparkline style dialog can be accessed by clicking the Edit Sparkline Style button found on a oneline field dialog or the [Geographic Data View Customization Dialog](04-model-explorer-and-case-information-part3.md#geographic-data-view).

The dialog contains the following options:

All Styles

This dropdown shows all available styles based on the selected object type and field.

Add New Style

Click this button to add a new style for the selected object type and field.

Object Type

Name of the object type for which the style is applicable. This cannot be changed on this dialog and will be set based on the object type selected prior to the sparkline style dialog being opened.

Variable Name

Variable name of the field for which the style is applicable. This cannot be changed on this dialog and will be set based on the field selected prior to the sparkline dialog being opened.

Style Name

Unique name of the style if more than one style exists for the same object type and field. This will be blank if only one style exists for a given object type and field.

Rename

Click this button to open a dialog that allows entering a new name for the presently selected style.

Thickness

This is the thickness of the chart line.

Color

This is the color of the chart line. To change the background color of the chart, use the [Line/Fill properties](14-editing-onelines.md#linefill-properties) found on the Format dialog and set the options to Use Background Fill and the Fill Color.

Width Ratio

As the height of the sparkline is changed, the width of the sparkline will retain this specified ratio relative to the height.

Margin X Ratio

This specifies the horizontal margin between the chart and the border of the sparkline box. This ratio is relative to the width of the sparkline box. Half of this margin appears on either side of the chart.

Margin Y Ratio

This specifies the vertical margin between the chart and the border of the sparkline box. This ratio is relative to the height of the sparkline box. Half of this margin appears on both the top and bottom of the chart.

Maximum Points

This option is not currently used.

Axis Settings

These options determine the **X Minimum**, **X Maximum**, **Y Minimum**, and **Y Maximum** limits that are specified for values shown in the chart. Check the **Auto** box next to the appropriate limit to allow these to be auto determined based on the values being shown, or enter values to **User Specify** these.

The **Treatment of User Specified Min/Max** options are not currently used.

Example

The following is an example showing sparklines for bus frequency from transient stability results.

![Sparklines](images/Sparklines.gif)

---

<a id="switched-shunt-svc-control-mode"></a>

## Switched Shunt SVC Control Mode

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched Shunt SVC Control Mode simulates a continuous or discrete shunt element that can control up to 8 fixed shunts. These shunts do not have to have a Control Mode that is fixed, but they are treated as fixed as long as they are being controlled by an SVC. To operate in this mode, the SVC Control Mode has to be selected in the Parameter tab of the Shunt Information dialog in either [Edit](06-object-properties-edit-mode-part3.md#switched-shunt-information) mode or [Run](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) mode.

The following tabs are available for specifying SVC shunt parameters and options:

SVC Control Options

SVC Type

Chose between *None*, *SVSMO1*, *SVSMO2* and *SVSMO3*.

*SVSMO1*: For thus type the limits consider the Susceptane (B) of the shunt.

*SVSMO2*: For thus type the limits consider the susceptane (B) of the shunt and the continuous element is replaced by discrete shunts.

*SVSMO3*:.For thus type the limits consider the Reactive Current of the shunt.

Minimum Continuous Nom Mvar or Minimum Continuous Curr.(pu) in svsmo3

Minimum value of B continuous element in Mvar. (Not used in *SVSMO3*).

Maximum Continuous Nom Mvar or Maximum Continuous Curr.(pu) in svsmo3

Maximum value of B continuous element in Mvar or Reactive Current in p.u. for SVSMO3 type.

Minimum Switching Nom Mvar (Bminsh) pu or Minimum Switching Curr.(pu) in svsmo3

Minimum value fo B in Mvar or Reactive Current in p.u. for SVSMO3 type to perform shunt switching.

Maximum Switching Nom Mvar (Bmaxsh) pu or Maximum Switching Curr.(pu) in svsmo3

Maximum value fo B in Mvar or Reactive Current in p.u. for SVSMO3 type to perform shunt switching or Reactive Current in p.u. for SVSMO3 type.

Note: Here is the link for the algorithm used in PowerWorld about [Switching Fixed controllable shunts](#switched-shunt-svc-control-mode-and-controllable-shunts-algorithm).

Comp. reactance (Xc) pu

Compensating Reactance for voltage control in p.u. When using the compensating reactance (Xc \<\> 0) the shunt will not regulate the Regulated Bus but instead will regulate its own terminal plus the linear slope, using the parameter Xc. For example, if a 3% voltage change is allowed across the entire control range of an SVC, and the SVC is rated +200/-100 Mvar and we assume a system MVA base of 100 MVA, then the slope is Xc = 0.03/3 = 0.01 pu on 100 MVA base. In steady-state (as along as it has not run out of capacitive/inductive range) the SVC will act until Vcomp is equal to Vsched. Vcomp = Vbus + (Vbus)\*(Bsvc)\*(Xc), where Vbus is the actual bus voltage. What the results will show for the voltage is the Vcomp value. The SVC output (Bsvc) is limited to stay within Bmax/Bmin. When the case solves the actual bus voltage will be Vbus = Vsched – (Vbus)\*(Bsvc)\*(Xc).

Slow control status (stsb)

Slow Control Status.

Slow Bmin (Bminsb) pu

Slow control minimum B in p.u. (Not used in *SVSMO3*).

Slow Bmax (Bmaxsb) pu

Slow control maximum B in p.u. (Not used in *SVSMO3*).

Slow Bmin voltage (Vrefmin) pu

Slow control minimum voltage in p.u.

Slow Bmax voltage (Vrefmax) pu

Slow control maximum voltage in p.u..

Change in V/change in B (dvdb)

Slow control p.u. Change in V by p.u. change in B. if the shunt is *SVSMO3* then it is the Slow control p.u. Change in V by p.u. change in I (Reactive Current).

Add Fixed Shunts

By clicking on this button, a dialog will open to select any shunts to be controlled by the SVC Shunt. Shunts with any control mode except for *SVC* can be controlled by an SVC. These shunts will be treated as fixed as long as the SVC controlling them is on active control. If the SVC is not on control, they will operate based on their own control mode. These Fixed Shunts are also used with the transient stability models of the SVCs.

SVC Fixed Shunt Options

On this tab there is information about the SVC Shunt that is controlling this particular shunt. Shunts with any Control Mode except *SVC* can be controlled by an SVC and will be treated as fixed while being controlled by an SVC. Options will be disabled if the control mode of the current shunt is not applicable for being controlled by an SVC.

Select SVC Shunt

This button will open a dialog that allows selection of the SVC that should control this shunt.

SVC Shunt Object ID

Object ID of the SVC controlling the shunt. The Object ID will be based on the Key Fields, that could be the Primary, Secondary or Label.

Available for SVC Control

Checking this box means that the shunt can be controlled by the specified SVC.

Some important [SVC Control Considerations when running Transient Stability](#switched-shunt-svc-control-mode-and-transient-simulation).

---

<a id="switched-shunt-svc-control-mode-and-controllable-shunts-algorithm"></a>

## Switched Shunt SVC Control Mode and Controllable Shunts Algorithm

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode_Controllable_Shunts.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode_Controllable_Shunts.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched Shunt SVC Control Mode simulates a continuous or discrete shunt element that can control up to 8 fixed shunts. These shunts do not have to have a Control Mode that is fixed, but they are treated as fixed as long as they are being controlled by an SVC. To control these 8 fixed shunts the following algorithm is used to determine when to switch in or out a controllable fixed shunt.

The pseudo-code of the algorithm is as follows:

![SwitchingAlgo1 719x538](images/SwitchingAlgo1_719x538.jpg)

![SwitchingAlgo2 721x561](images/SwitchingAlgo2_721x561.jpg)

NOTE: For svsmo3, we need the current thus that is calculated as B of SVC in PU \*(Voltage at Terminal Bus). The algorithm is the same but with the correct current parameters.

The MVA Convergence Tolerance is found on the [Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options).

---

<a id="switched-shunt-svc-control-mode-and-transient-simulation"></a>

## Switched Shunt SVC Control Mode and Transient Simulation

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode_Transient_Simulation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_SVC_Control_Mode_Transient_Simulation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched Shunt SVC Control Mode simulates a continuous or discrete shunt element that can control up to 8 fixed shunts. These shunts do not have to have a Control Mode that is fixed, but they are treated as fixed as long as they are being controlled by an SVC. To operate in this mode, the SVC Control Mode has to be selected in the Parameter tab of the Shunt Information dialog in either [Edit](06-object-properties-edit-mode-part3.md#switched-shunt-information) mode or [Run](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) mode.

The following conditions need to be corrected in order for the [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) Simulation to run without the following error (The Transient Model SVSMO1,2 or 3 do not matche the power flow control model):

SVC Control Considerations when running Transient Stability

In PowerWorld we do not allow to run a transient simulation that have a switched shunt transient models svsmo1, svsmo2 and svsmo3 if the power flow model is not matching the corresponding SVC model. The reason for this is that it will cause initialization problems because the initial power flow solution will not match the transient model and this will make the output of the shunt to move as soon as the transient simulation starts.

Below are the control options that **MUST** be corrected in order for the error to disappear and to be able to at least run the transient stability simulation:

Correct the Shunt Control Model and SVC Type:

Set the Switched Shunt Control Mode to *SVC*:

![contorlmodess 547x515](images/contorlmodess_547x515.gif)

Set the SVC to the corresponding Type in the SVC Control Options Tab that matches the transient stability model of the switched shunt (*SVSMO1*, *SVSMO2* and *SVSMO3*):

![svctype 545x518](images/svctype_545x518.gif)

Below are the control options that are **RECOMMENDED** in order to have a better transient stability solution that matches the power flow initial conditions:

The Continuous Nom Mvar needs to match the Bmax and Bmin of the SVSMO1 or SVSMO3 transient model. The reason for this is only noticeable if that SVC is on a limit during the power flow. If the limits from the power flow do not match the limits of the transient model then the SVC will probably start to move as soon as the transient simulation is started in particular if the transient model limits are higher or lower than the power flow limits:

![svcminmax 542x514](images/svcminmax_542x514.gif)

The Min and Max in the transient mode can be found in the transient model as Bmax and Bmin for *SVSMO1* or Imax1 for *SVSMO3*:

![svcminmaxts 543x516](images/svcminmaxts_543x516.gif) ![svcminmaxts3 544x519](images/svcminmaxts3_544x519.gif)

Please **NOTE** that the Bmax, Bmin and Imax1 are in pu in the transient model and in the power flow control options the limits are in Nom Mvar for *SVSMO1* and *SVSMO2*, and in Nom Amps for *SVSMO3*. The *SVSMO2* Min and Max values are determined by the switched blocks.

---

<a id="temperaturebasic1"></a>

## TemperatureBasic1

*Source: [`Content/MainDocumentation_HTML/Weather_Model_Temperature.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Model_Temperature.htm)*

Weather Related Models were added in Version 23

This model takes the temperature at the generator (in either Fahrenheit or Celsisus depending on the input parameter TempCF) and converts this into a normalized output scalar as shown in the figure below. This normalized value is then multiplied by the model parameter **MWMax** to create the output of the Wind Model which represents the weather-dependent MWMax value that should be used by the generator.

Model Inputs

<table>
<tbody>
<tr class="odd">
<td><p>Inputs</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>TempF</p>
<p>TempC</p></td>
<td><p>The TempF or TempCwill be obtained from the generator field <strong>WS_TempF</strong> field <strong>WS_TempC</strong>as described in the help topic <a href="28-weather.md#generator-assignments-to-weatherstation-and-xycurve" class="MCXref xref">Generator assignments to WeatherStation and XYCurve</a>.</p>
<p>If this is not available we will assume an input that is in the middle of the normal range which results in an output scalar of 1.000.</p></td>
</tr>
</tbody>
</table>

Parameters for SolarPVBasic1 and SolarPVBasic2.

<table>
<tbody>
<tr class="odd">
<td><p>Parameter</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>TempCF</p></td>
<td><p>Set to 1 to indicate temperatures are given in Fahrenheit degrees</p>
<p>Otherwise we assume Celsius degrees</p></td>
</tr>
<tr class="odd">
<td><p>MWMax</p></td>
<td><p>The scalars are all per unit on this base.</p></td>
</tr>
<tr class="even">
<td><p>TempNormalLow</p></td>
<td><p>The lowest temperature at which the OutputScalar is 1.000</p></td>
</tr>
<tr class="odd">
<td><p>TempNormalHigh</p></td>
<td><p>The highest temperature at which the OutputScalar is 1.000</p></td>
</tr>
<tr class="even">
<td><p>TempLow</p></td>
<td><p>As temperature goes below TempNormalLow, the OutputScalar linearly reduces down to a value of TempLowScalar at the temperature TempLow</p></td>
</tr>
<tr class="odd">
<td><p>TempLowScalar</p></td>
<td><p>See TempLow description</p></td>
</tr>
<tr class="even">
<td><p>TempHigh</p></td>
<td><p>As temperature goes above TempNormalHigh, the OutputScalar linearly reduces down to a value of TempHighScalar at the temperature TempHigh</p></td>
</tr>
<tr class="odd">
<td><p>TempHighScalar</p></td>
<td><p>See TempHigh description</p></td>
</tr>
</tbody>
</table>

![WeatherTemperatureNormalizedOutput](images/WeatherTemperatureNormalizedOutput.png)

---

<a id="transient-stability-analysis-options-remedial-action-validation"></a>

## Transient Stability Analysis Options: Remedial Action Validation

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS_Validation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS_Validation.htm)*

More types of actions are available with steady-state remedial action definitions than those available for transient stability. More fields for inclusion with criteria monitoring are available with steady-state definitions than those available for transient stability. A validation tool is available to provide guidance on what is supported with transient stability. This validation tool can be run by clicking the **Run Remedial Action Validation** button on the [Remedial Actions tab of the Transient Stability dialog](37-transient-stability-analysis-dialog-part1.md#remedial-actions).

The TS Valid Reason field indicates the parts of the hierarchy that cannot be evaluated each transient time step.

The local menu option to Show Transient Stability RAS Validation is intended to help read the TS Valid Reason by spreading it out into different objects in the hierarchy as shown in the example below. Local menu option to Show Transient Stability RAS Validation Info will open a dialog showing the TS Valid Reason field but in an easier to read format:

![Transient Stability Dialog RAS Validation TSValidReason 893x518](images/Transient_Stability_Dialog_RAS_Validation_TSValidReason_893x518.jpg)

The **TS Valid Reason** field provides more details about components of the Model Criteria that are evaluated for the transient initial condition. If (**TS Valid** = *Armed*) and (**TS Valid Reason** is not blank), some components are evaluated for the transient initial condition and some are evaluated during the transient run. Then the **TS Valid Reason** field is then used to indicate the parts of the hierarchy that cannot be evaluated each transient time step. The **TS Valid Field** meaning are explained in the following table:

<table>
<tbody>
<tr class="odd">
<td><p>TS Valid Field</p></td>
<td><p>Meaning</p></td>
<td><p>Translated</p></td>
</tr>
<tr class="even">
<td><p>Skip*</p></td>
<td><p>Remedial Action <strong>Skip</strong> = <em>YES</em></p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Not Armed*</p></td>
<td><p><strong>Arming Criteria</strong> is not met. For a Remedial Action Element this means that its own Arming Criteria is not met or the Arming Criteria for its Remedial Action is not met.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Full TS*</p></td>
<td><p>For a Remedial Action this means that all of the Model Criteria for all of its Remedial Action Elements can be evaluated each transient time step and all Remedial Action Elements are valid.</p>
<p>For a Remedial Action Element this means that the Model Criteria and all of its components can be evaluated each transient time step and the action itself is valid.</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p>Partial TS*</p></td>
<td><p>For a Remedial Action this means that some of the Model Criteria for its Remedial Action Elements cannot be evaluated each transient time step of some of its Remedial Action Elements are invalid for another reason.</p>
<p>For a Remedial Action Element this means that parts of its Model Criteria cannot be evaluated each transient time step.</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>No Elements**</p></td>
<td><p>Remedial Action has no Remedial Action Elements that have Model Criteria that can be evaluated each transient time step of there is another reason why the Remedial Action Element is not valid for transient stability.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>No Elements Evaluate TS**</p></td>
<td><p>Remedial Action has no Remedial Action Elements that have Model Criteria that can be evaluated each transient time step or there is another reason why the Remedial Action Element is not valid for transient stability.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Invalid Status</p></td>
<td><p>Action <strong>Status</strong> is not valid for translation (must be TOPOLOGYCHECK or POSTCHECK)</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Invalid Action</p></td>
<td><p>Action is not valid for translation (OPEN/CLOSE or particular SETTO/CHANGEBY)</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>No Model Criteria</p></td>
<td><p><strong>Model Criteria</strong> is not defined</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Initial Condition</p></td>
<td><p><strong>Model Criteria</strong> is completely evaluated for the transient stability initial condition</p></td>
<td><p>No</p></td>
</tr>
</tbody>
</table>

\* This entry is valid for both Remedial Actions and Remedial Action Elements

\*\* This entry is only valid for Remedial Actions

No star means that this entry is valid only for Remedial Action Elements

Remedial Actions and Remedial Action Elements that have a **TS Valid** field of *Full TS* or *Partial TS* will be translated for use during the transient analysis. All others will be ignored and never implemented. For *Partial TS* this means that some components of the model criteria will be evaluated each transient time step and some are evaluated for the transient initial condition.

In addition to changing the **TS Valid** field entries for Remedial Actions and Remedial Action Elements, a **TS Valid** field was added to **Model Conditions, Model Condition Conditions, Model Filters, Model Filter Conditions, Model Planes, Model Expressions,** and **Model Expression** variables to indicate whether these objects are valid for being evaluated each transient time step. This **TS Valid Field** for these variables are explained in the following table:

<table>
<tbody>
<tr class="odd">
<td><p>TS Valid Field</p></td>
<td><p>Meaning</p></td>
<td><p>Translated</p></td>
</tr>
<tr class="even">
<td><p>None</p></td>
<td><p>Model Criteria is not used a part of any Remedial Action Element definition.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Full TS</p></td>
<td><p>All parts of object and any objects that is uses can be evaluated in transient stability.</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Evaluate in Ref</p></td>
<td><p>The option to evaluate the object in the contingency reference state is true.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Disable If True in Ref</p></td>
<td><p>The option to disable the object if it is true in the contingency reference state is true and the object evaluates to true in the initial transient stability state.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Model Result Override</p></td>
<td><p>The object is being overridden by a Model Result Override.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Not Specified Evaluate in TS</p></td>
<td><p>The options for <strong>Eval Trans Time</strong> and <strong>EvalTrans</strong> are not true and the field being evaluated is not one that is always evaluated each transient time step.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Invalid Field</p></td>
<td><p>The field is not supported for evaluation each transient time step.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Circular Reference</p></td>
<td><p>The object is defined in such a way as it ends up referencing itself. This is an error in the definition of the object.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>No Components Evalute in TS</p></td>
<td><p>The will result for a</p>
<ul>
<li>Model Filter if none of the contained Model Filter Conditions can be evaluated every transient time step</li>
<li>Model Condition if none of the contained Model Condition Conditions can be evaluated every transient time step</li>
<li>Model Condition Condition if none of the parts that make up the condition can be evaluated every time step</li>
<li>Model Expression if none of the variables can be evaluated every transient time step</li>
</ul></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Some Components Evaluate in TS</p></td>
<td><p>This will result for a</p>
<ul>
<li>Model Filter if only some of the contained Model Filter Conditions can be evaluated every transient time step</li>
<li>Model Condition if only some of the contained Model Condition Conditions can be evaluated every transient time step</li>
<li>Model Condition Condition if only some of the parts that make up the condition can be evaluated every transient time step</li>
<li>Model Expression if only some of the variables can be evaluated every transient time step</li>
</ul></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p>Secondary Filter</p></td>
<td><p>This will result for a Model Condition if the filter applied to the object in the condition is not for the same object type as the condition object.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Other Error</p></td>
<td><p>Catch for any other problems that might be encountered.</p>
<p>Please contact PowerWorld if you encounter this.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>FIlter Not Enabled</p></td>
<td><p>This will result for a Model Condition if the filter applied to the object in the condition is not enabled.</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Use Another Filter</p></td>
<td><p>This will result for a Model Condition if the filter applied to the object in the condition has the <strong>Use Another Filter</strong> option selected.</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Object Not Defined</p></td>
<td><p>This will result for a Model Expression variable if an object is not specified for the variable.</p></td>
<td><p>No</p></td>
</tr>
</tbody>
</table>

With the to **Model Conditions, Model Condition Conditions, Model Filters, Model Filter Conditions, Model Planes, Model Expressions,** and **Model Expression** tables, an option exists on the right-click menu to **Open Dependency Explorer**. This will make it easier to navigate around the hierarchy of the remedial action element and model criteria:

![Transient Stability Dialog RAS Validation RightClick 910x520](images/Transient_Stability_Dialog_RAS_Validation_RightClick_910x520.jpg)

---

<a id="transient-stability-analysis-options-valid-remedial-actions-fields"></a>

## Transient Stability Analysis Options: Valid Remedial Actions Fields

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_RAS_Fields.htm)*

Many more fields are available for inclusion in steady-state remedial action definition and criteria monitoring than are available for transient stability. The **Show Valid Remedial Action Fields** button on the [Remedial Actions tab of the Transient Stability dialog](37-transient-stability-analysis-dialog-part1.md#remedial-actions) will provide the most up-to-date list of the fields and object types for which they are supported.

The resulting list of fields supported in transient stability will contain the following information:

Object Type

Name of object type for which the field is supported.

Variable Name

Variable name of the field that is supported.

Allow Derivative

This will be YES if the time derivative of the field can be calculated when it is used as part of a Model Expression.

Always Every Time Step

When this field is YES the user has no input on whether or not this field will be evaluated every time step. Fields where this is imposed are Status, Online, DerivedStatus, and DerivedOnline. When this field is NO the user <span class="underline">must</span> specify if this field should be evaluated every transient time step. If a field is not evaluated every time step it is evaluated in the initial state for a transient stability run and this value remains constant for every time step.

![Transient Stability Dialog RAS Fields](images/Transient_Stability_Dialog_RAS_Fields.png)

To specify that a field be evaluated every transient time step, there are options with Model Conditions and Model Expressions.

On the Model Condition dialog the **Eval Trans Time** checkbox will be enabled if a field is selected that is supported for being evaluated every transient time step and the field is not forced to be evaluated every time step, i.e., Status, Online, DerivedStatus, and DerivedOnline:

![Transient Stability Dialog RAS Fields MC](images/Transient_Stability_Dialog_RAS_Fields_MC.png)

On the Model Expression dialog each expression variable has an **EvalTrans** option to specify whether or not it should be evaluated every time step. This option will only be enabled for fields that are supported for evaluation every transient time step and not forced to be evaluated every time step, i.e., Status, Online, DerivedStatus, and DerivedOnline:

![Transient Stability Dialog RAS Fields ME](images/Transient_Stability_Dialog_RAS_Fields_ME.png)

When defining Model Conditions and Model Expressions and using the Choose a Field dialog to select fields, checking the **Show Transient Stability Remedial Action Fields**checkbox will limit the list of fields shown in the chooser to only those that are supported for being evaluated every transient time step:

![Transient Stability Dialog RAS Fields CAF](images/Transient_Stability_Dialog_RAS_Fields_CAF.png)

---

<a id="transient-stability-analysis-areas-validation-parameter-check"></a>

## Transient Stability Analysis: Areas Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Area.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Area.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

**Area models**

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-**[AreaAGC](46-ts-models-other.md#areaagc)**

---

<a id="transient-stability-analysis-exciters-validation-parameter-check"></a>

## Transient Stability Analysis: Exciters Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Exciters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Exciters.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Exciter models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

All of the models that have the following parameters until stated otherwise in the model:

  - If 0.0 \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep  
    ElseIf Tb \<= 0 then Tb = 0.
  - Checks for Tb1, and Tb2, are the same as for Tb
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then T1 = 0.0  
    ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Te \> 1 then Te = 1 and if Te \<= 0 then Te = 0.
  - If K \> 400 then K = 400 and if K \< 1 then K = 1.
  - Checks for Kc are the same as K.
  - If Efdmax \> 10 then Efdmax = 10 and if Efdmax \< 2 then Efdmax = 2.
  - If Efdmin \> 1 then Efdmin = 1 and if Efdmin \<= 0 then Efdmin = 0.
  - Checks for Emin are the same as Efdmin.

\-*[MEXS](39-ts-models-exciters-part3.md#mexs)*

\-*[SCRX](39-ts-models-exciters-part4.md#scrx)*

\-*[ESDC1A](39-ts-models-exciters-part2.md#esdc1a)*

\-*[ESDC2A](39-ts-models-exciters-part2.md#esdc2a)*

\-*[ESDC3A](39-ts-models-exciters-part2.md#esdc3a)*

\-*[DC4B](39-ts-models-exciters-part1.md#dc4b)*

\-*[IEEET1](39-ts-models-exciters-part3.md#ieeet1)*

\-*[IEET1A](39-ts-models-exciters-part3.md#ieet1a)*

\-*[IEET1B](39-ts-models-exciters-part3.md#ieet1b)*

\-*[IEEET2](39-ts-models-exciters-part3.md#ieeet2)*

\-*[IEEET3](39-ts-models-exciters-part3.md#ieeet3)*

\-*[IEEET4](39-ts-models-exciters-part3.md#ieeet4)*

\-*[IEEET5](39-ts-models-exciters-part3.md#ieeet5)*

\-*[IEET5A](39-ts-models-exciters-part3.md#ieet5a)*

\-*[IEEEX1](39-ts-models-exciters-part3.md#ieeex1)*

\-*[IEEEX2](39-ts-models-exciters-part3.md#ieeex2)*

\-*[IEEX2A](39-ts-models-exciters-part3.md#ieex2a)*

\-*[IEEEX3](39-ts-models-exciters-part3.md#ieeex3)*

\-*[IEEEX4](39-ts-models-exciters-part3.md#ieeex4)*

\-*[EXAC1](39-ts-models-exciters-part2.md#exac1)*

\-*[EXAC1A](39-ts-models-exciters-part2.md#exac1a)*

\-*[EMAC1T](39-ts-models-exciters-part1.md#emac1t)*

\-*[EXAC2](39-ts-models-exciters-part2.md#exac2)*

\-*[EXAC3](39-ts-models-exciters-part2.md#exac3)*

\-*[EXAC3A](39-ts-models-exciters-part2.md#exac3a)*

\-*[EXAC4](39-ts-models-exciters-part2.md#exac4)*

\-*[EXAC6A](39-ts-models-exciters-part2.md#exac6a)*

\-*[EXBAS](39-ts-models-exciters-part2.md#exbas)*

\-*[EX2000](39-ts-models-exciters-part2.md#ex2000)*

\-*[EXAC8B](39-ts-models-exciters-part2.md#exac8b)*

\-*[EXBBC](39-ts-models-exciters-part2.md#exbbc)*

\-*[BBSEX1](39-ts-models-exciters-part1.md#bbsex1)*

\-*[EXIVO](39-ts-models-exciters-part3.md#exivo)*

\-*[IVOEX](39-ts-models-exciters-part3.md#ivoex)*

\-*[EXELI](39-ts-models-exciters-part3.md#exeli)*

\-*[EXWTG1](39-ts-models-exciters-part3.md#exwtg1)*

\-*[WT2E](39-ts-models-exciters-part5.md#wt2e)*

\-*[WT2E1](39-ts-models-exciters-part5.md#wt2e1)*

\-*[EXWTGE](39-ts-models-exciters-part3.md#exwtge)*

\-*[EWTGFC](39-ts-models-exciters-part2.md#ewtgfc)*

\-[*WT3E and WT3E1*](39-ts-models-exciters-part5.md#wt3e)

\-*[WT4E1](39-ts-models-exciters-part5.md#wt4e1)*

\-*[WT4E](39-ts-models-exciters-part5.md#wt4e)*

\-*[REEC\_A](39-ts-models-exciters-part3.md#reec-a)*

\-*[REEC\_B](39-ts-models-exciters-part4.md#reec-b)*

\-*[REEC\_C](39-ts-models-exciters-part4.md#reec-c)*

\-*[EXPIC1](39-ts-models-exciters-part3.md#expic1)*

\-*[ESAC1A](39-ts-models-exciters-part1.md#esac1a)*

\-*[ESAC2A](39-ts-models-exciters-part1.md#esac2a)*

\-*[ESAC3A](39-ts-models-exciters-part1.md#esac3a)*

\-*[ESAC4A](39-ts-models-exciters-part2.md#esac4a)*

\-*[ESAC5A](39-ts-models-exciters-part2.md#esac5a)*

\-*[ESAC6A](39-ts-models-exciters-part2.md#esac6a)*

\-*[AC7B](39-ts-models-exciters-part1.md#ac7b)*

\-*[AC8B](39-ts-models-exciters-part1.md#ac8b)*

\-*[ESAC7B](39-ts-models-exciters-part1.md#ac7b)*

\-*[ESAC8B or ESAC8B\_PTI](39-ts-models-exciters-part2.md#esac8b-pti)*

\-[*ESAC8B or ESAC8B\_GE*](39-ts-models-exciters-part2.md#esac8b-ge)

\-[*EXST1\_GE*](39-ts-models-exciters-part3.md#exst1-ge)

\-*[EXST1\_PTI](39-ts-models-exciters-part3.md#exst1-pti)*

\-*[EXST2](39-ts-models-exciters-part3.md#exst2)*

\-*[EXST2A](39-ts-models-exciters-part3.md#exst2a)*

\-*[EXST3](39-ts-models-exciters-part3.md#exst3)*

\-*[EXST3A](39-ts-models-exciters-part3.md#exst3a)*

\-*[EXST4B](39-ts-models-exciters-part3.md#exst4b)*

\-[*ESST1A or ESST1A\_GE*](39-ts-models-exciters-part2.md#esst1a)

\-*[ESST2A](39-ts-models-exciters-part2.md#esst2a)*

\-*[ESST3A](39-ts-models-exciters-part2.md#esst3a)*

\-*[ESST4B](39-ts-models-exciters-part2.md#esst4b)*

\-[*ST5B and ESST5B*](39-ts-models-exciters-part2.md#esst5b)

\-*[ST6B and ESST6B](39-ts-models-exciters-part2.md#esst6b)*

\-[*ST7B and ESST7B*](39-ts-models-exciters-part2.md#esst7b)

\-[*URST5T*](39-ts-models-exciters-part5.md#urst5t)

\-*[EXDC1](39-ts-models-exciters-part2.md#exdc1)*

\-*[EXDC2\_PTI](39-ts-models-exciters-part3.md#exdc2-pti)*

\-*[EXDC2\_GE](39-ts-models-exciters-part2.md#exdc2-ge)*

\-*[EXDC2A](39-ts-models-exciters-part3.md#exdc2a)*

\-*[EXDC4](39-ts-models-exciters-part3.md#exdc4)*

\-*[REXS](39-ts-models-exciters-part4.md#rexs)*

\-*[REXSYS](39-ts-models-exciters-part4.md#rexsys)*

\-*[REXSY1](39-ts-models-exciters-part4.md#rexsy1)*

\-*[TEXS](39-ts-models-exciters-part5.md#texs)*

---

<a id="transient-stability-analysis-generator-machines-models-validation-parameter-check"></a>

## Transient Stability Analysis: Generator Machines Models Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Generator_Machine_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Generator_Machine_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Generator Machine models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

*Machine Model Reactance Validation*

These reactance values are specified on the d-axis and q-axis and are referred to as synchronous reactance (Xd and Xq), transient reactance (Xdp and Xqp), subtransient reactance (Xdpp and Xqpp), and leakage reactance (Xl). In order for the equations which model the machine to be numerically stable, the reactance must obey the following relationships: \[Xl\>Xqpp\>Xqp\>Xq\] and \[Xl\>Xdpp\>Xdp\>Xd\]. A violation of any of these relationships can cause numerical instability and also just fundamentally does not make sense. Despite this, these types of errors are very common.

When encountering models which do not obey these relationships, PowerWorld Simulator will perform the following error checking, and when using auto-correction will make the following changes to the input data.

if Xqp \> Xq then Xqp = 0.8\*Xq

if Xdp \> Xd then Xdp = 0.8\*Xd

if Xqpp \> Xqp then Xqpp = 0.8\*Xqp

if Xdpp \> Xdp then Xdpp = 0.8\*Xdp

if Xl \> Xqpp then Xl = 0.8\*Xqpp

if Xl \> Xdpp then Xl = 0.8\*Xdpp

All of the synchronous generator models that have the following parameters until stated otherwise in the model:

  - If H \< 0.1, then H = 0.1

\-*[GENCLS](38-ts-models-machine.md#gencls) and [GENCLS\_PLAYBACK](38-ts-models-machine.md#gencls-playback)*

\-*[GENSAL](38-ts-models-machine.md#gensal), [GENSAE](38-ts-models-machine.md#gensae), [GENROU](38-ts-models-machine.md#genrou) and [GENROE](38-ts-models-machine.md#genroe)*

\-*[GENTPF](38-ts-models-machine.md#gentpf), [GENTPJ](38-ts-models-machine.md#gentpj) and [GENCC](38-ts-models-machine.md#gencc)*

\-*[GENDCO](38-ts-models-machine.md#gendco)*

\-*[GENPWTwoAxis](38-ts-models-machine.md#genpwtwoaxis)*

\-*[GENPWFluxDecay](38-ts-models-machine.md#genfluxdecay)*

\-*[STCON](38-ts-models-machine.md#stcon)*

\-*[CIMTR1](38-ts-models-machine.md#cimtr1), [CIMTR2](38-ts-models-machine.md#cimtr2), [CIMTR3](38-ts-models-machine.md#cimtr3) and [CIMTR4](38-ts-models-machine.md#cimtr4)*

\-*[MOTOR1](38-ts-models-machine.md#motor1)*

\-*[WT1G](38-ts-models-machine.md#wt1g)*

\-*[WT2G](38-ts-models-machine.md#wt2g)*

\-*[GEWTG](38-ts-models-machine.md#gewtg)*

\-*[WT3G](38-ts-models-machine.md#wt3g)*

\-*[WT3G2](38-ts-models-machine.md#wt3g2)*

\-*[WT4G](38-ts-models-machine.md#wt4g)*

\-*[WT4G1](38-ts-models-machine.md#wt4g1)*

\-[*REGC\_A*](38-ts-models-machine.md#regc-a)

\-*[PVD1](38-ts-models-machine.md#pvd1)*

\-*[CSVGN1](38-ts-models-machine.md#csvgn1)*

\-*[CSVGN3](38-ts-models-machine.md#csvgn3)*

\-*[CSVGN4](38-ts-models-machine.md#csvgn4)*

\-*[CSVGN5](38-ts-models-machine.md#csvgn5)*

\-*[CSVGN6](38-ts-models-machine.md#csvgn6)*

\-*[CBattery](38-ts-models-machine.md#cbattery)*

\-*[CBEST](38-ts-models-machine.md#cbest)*

---

<a id="transient-stability-analysis-generator-other-models-validation-parameter-check"></a>

## Transient Stability Analysis: Generator Other Models Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Generator_Other_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Generator_Other_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Generator Other models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-*[UEL1](42-ts-models-generator-other-part2.md#uel1)*

\-*[MNLEX1](42-ts-models-generator-other-part2.md#mnlex1)*

\-*[MNLEX2](42-ts-models-generator-other-part2.md#mnlex2)*

\-*[MNLEX3](42-ts-models-generator-other-part2.md#mnlex3)*

\-[*WTGTRQ\_A or WTGQ\_A*](42-ts-models-generator-other-part2.md#wtgtrq-a)

\-*[REPC\_A](42-ts-models-generator-other-part1.md#repc-a)*

\-[*REPC\_B*](42-ts-models-generator-other-part1.md#repc-b)

\-[*WTGAR\_A and WTGA\_A*](42-ts-models-generator-other-part1.md#wtgar-a)

\-*[H6BD](40-ts-models-governors-part1.md#h6b-and-h6bd)*

---

<a id="transient-stability-analysis-governors-validation-parameter-check"></a>

## Transient Stability Analysis: Governors Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Governors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Governors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Governor models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

All of the models that have the following parameters until stated otherwise in the model:

  - Gv: Check that the Nonlinear gain is a constantly increasing function starting at a specified parameter.

\-*[CRCMGV](40-ts-models-governors-part1.md#crcmgv)*

\-*[DEGOV](40-ts-models-governors-part1.md#degov)*

\-*[DEGOV1](40-ts-models-governors-part1.md#degov1)*

\-[*GAST\_PTI*](40-ts-models-governors-part1.md#gast-pti)

\-*[GAST2A](40-ts-models-governors-part1.md#gast2a)*

\-[*[GAST2A\_AIR](40-ts-models-governors-part1.md#gast2a-air)*](40-ts-models-governors-part1.md#gast2a-air)

\-*[GASTWD](40-ts-models-governors-part1.md#gastwd)*

\-*[GASTWD\_AIR](40-ts-models-governors-part1.md#gastwd-air)*

\-*[GGOV1](40-ts-models-governors-part1.md#ggov1)*

\-*[GGOV2](40-ts-models-governors-part1.md#ggov2)*

\-*[GGOV3](40-ts-models-governors-part1.md#ggov3)*

\-*[GPWSCC](40-ts-models-governors-part1.md#gpwscc)*

\-*[G2WSCC](40-ts-models-governors-part1.md#g2wscc)*

\-*[HYGOV](40-ts-models-governors-part2.md#hygov)*

\-*[HYGOVR](40-ts-models-governors-part2.md#hygovr)*

\-*[HYGOVRU](40-ts-models-governors-part3.md#hygovru)*

\-*[HYGOV2](40-ts-models-governors-part2.md#hygov2)*

\-*[HYPID](40-ts-models-governors-part3.md#hypid)*

\-*[HYG3](40-ts-models-governors-part2.md#hyg3)*

\-*[HYGOV4](40-ts-models-governors-part2.md#hygov4)*

\-*[HYST1](40-ts-models-governors-part3.md#hyst1)*

\-*[PIDGOV](40-ts-models-governors-part3.md#pidgov)*

\-*[WEHGOV](40-ts-models-governors-part3.md#wehgov)*

\-*[WPIDHY](40-ts-models-governors-part4.md#wpidhy)*

\-*[IEEEG1 or IEEEG1\_GE](40-ts-models-governors-part3.md#ieeeg1)*

\-*[IEEEG2](40-ts-models-governors-part3.md#ieeeg2)*

\-*[IEEEG3\_PTI](40-ts-models-governors-part3.md#ieeeg3-pti)*

\-*[IEEEG3\_GE](40-ts-models-governors-part3.md#ieeeg3-ge)*

\-*[IEESGO](40-ts-models-governors-part3.md#ieesgo)*

\-*[TGOV1](40-ts-models-governors-part3.md#tgov1)*

\-*[TGOV2](40-ts-models-governors-part3.md#tgov2)*

\-*[TGOV3](40-ts-models-governors-part3.md#tgov3)*

\-*[TGOV5](40-ts-models-governors-part3.md#tgov5)*

\-*[WESGOV](40-ts-models-governors-part3.md#wesgov)*

\-*[W2301](40-ts-models-governors-part3.md#w2301)*:

\-*[HRSGSimple](40-ts-models-governors-part2.md#hrsgsimple)*

\-*[WNDTGE](40-ts-models-governors-part4.md#wndtge)*

\-*[WNDTRB](40-ts-models-governors-part4.md#wndtrb)*

\-*[WT1T](40-ts-models-governors-part4.md#wt1t)*

\-*[WT12T](40-ts-models-governors-part4.md#wt2t)*

\-*[WT3T](40-ts-models-governors-part4.md#wt3t)*

\-*[WT3T1](40-ts-models-governors-part4.md#wt3t1)*

\-*[WT4T](40-ts-models-governors-part4.md#wt4t)*

\-*[WTGT\_A](40-ts-models-governors-part4.md#wtgt-a)*

\-*[WSIEG1](40-ts-models-governors-part4.md#wsieg1)*

\-*[URGS3T](40-ts-models-governors-part3.md#urgs3t)*

\-*[WSHYDD](40-ts-models-governors-part4.md#wshydd)*

\-*[WSHYGP](40-ts-models-governors-part4.md#wshygp)*

\-*[CCBT1](40-ts-models-governors-part1.md#ccbt1)*

\-*[H6B](40-ts-models-governors-part1.md#h6b-and-h6bd)*

\-*[Hydro\_Bradley](40-ts-models-governors-part2.md#hydro-bradley)*

\-*[ISOGOV1](40-ts-models-governors-part3.md#isogov1)*

---

<a id="transient-stability-analysis-line-relays-validation-parameter-check"></a>

## Transient Stability Analysis: Line Relays Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Line_Relays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Line_Relays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Line Relays models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-*[TIOCRS](44-ts-models-branch-and-shunt-part1.md#tiocrs)*

---

<a id="transient-stability-analysis-line-shunts-validation-parameter-check"></a>

## Transient Stability Analysis: Line Shunts Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Line_Shunts.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Line_Shunts.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

**Line Shunts models**

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-[*MSLR1 or MSR1*](44-ts-models-branch-and-shunt-part1.md#mslr1)

---

<a id="transient-stability-analysis-load-characteristics-validation-parameter-check"></a>

## Transient Stability Analysis: Load Characteristics Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Load_Characteristics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Load_Characteristics.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Load Characteristic models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-*[CIM5](43-ts-models-load-part1.md#cim5)*

\-*[CIM6](43-ts-models-load-part1.md#cim6)*

\-*[CIMW](43-ts-models-load-part1.md#cimw)*

\-*[LDRANDOM](43-ts-models-load-part2.md#ldrandom)*

\-*[LD1PAC](43-ts-models-load-part1.md#ld1pac)*

\-*[MOTORW](43-ts-models-load-part2.md#motorw)*

\-*[MOTORX](43-ts-models-load-part2.md#motorx)*

\-*[MOTOR\_CMP](43-ts-models-load-part2.md#motor-cmp)*

\-*[CMPLDW](43-ts-models-load-part1.md#cmpldw)*

\-*[CMPLDWNF](43-ts-models-load-part1.md#cmpldwnf)*

---

<a id="transient-stability-analysis-stabilizers-validation-parameter-check"></a>

## Transient Stability Analysis: Stabilizers Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Stabilizers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Stabilizers.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Stabilizers models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-*[IEEEST](41-ts-models-stabilizers.md#ieeest)*

\-*[PSS1A](41-ts-models-stabilizers.md#pss1a)*

\-*[IEE2ST](41-ts-models-stabilizers.md#iee2st)*

\-*[PSS2A](41-ts-models-stabilizers.md#pss2a)*

\-*[PSS2B](41-ts-models-stabilizers.md#pss2b)*

\-*[PSS3B](41-ts-models-stabilizers.md#pss3b)*

\-*[PSSSB](41-ts-models-stabilizers.md#psssb)*

\-*[PSSSH](41-ts-models-stabilizers.md#psssh)*

\-*[PTIST1](41-ts-models-stabilizers.md#ptist1)*

\-*[PTIST3](41-ts-models-stabilizers.md#ptist3)*

\-[*ST2CUT*](41-ts-models-stabilizers.md#st2cut)

\-*[STAB1](41-ts-models-stabilizers.md#stab1)*

\-*[STAB2A](41-ts-models-stabilizers.md#stab2a)*

\-*[STAB3](41-ts-models-stabilizers.md#stab3)*

\-*[STAB4](41-ts-models-stabilizers.md#stab4)*

\-*[STBSVC](41-ts-models-stabilizers.md#stbsvc)*

\-*[WSCCST](41-ts-models-stabilizers.md#wsccst)*

\-*[IVOST](41-ts-models-stabilizers.md#ivost)*

\-*[PFQRG](41-ts-models-stabilizers.md#pfqrg)*

\-[*WT1P and WT12A1*](41-ts-models-stabilizers.md#wt12a1)

\-*[WT1P\_B](41-ts-models-stabilizers.md#wt1p-b)*

\-[*WTGPT\_A or WTGP\_A*](41-ts-models-stabilizers.md#wtgpt-a)

---

<a id="transient-stability-analysis-switched-shunts-validation-parameter-check"></a>

## Transient Stability Analysis: Switched Shunts Validation Parameter Check

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Switched_Shunts.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Validation_Parameter_Check_Switched_Shunts.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Validation page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).

*Switched Shunts models*

Clicking the **Run Validation** button will run the validation and clicking the **Run AutoCorrection** button will modify many of the input values. In Simulator running the auto correction will permanently change your input data. Then many user assume these corrections are valid for their cases but in reality it just make the simulation run without errors but do not means the solution is correct. In order to have an idea of the correction Simulator does during **AutoCorrection** here is a list of the Parameter Check and corrections done to the transient stability models.

\-*[CSSCST](44-ts-models-branch-and-shunt-part2.md#csscst)*

\-*[MSR1](44-ts-models-branch-and-shunt-part2.md#msr1)*

\-*[SVSMO1](44-ts-models-branch-and-shunt-part2.md#svsmo1)*

\-*[SVSMO2](44-ts-models-branch-and-shunt-part2.md#svsmo2)*

\-*[SVSMO3](44-ts-models-branch-and-shunt-part2.md#svsmo3)*

\-*[SVSCALS](44-ts-models-branch-and-shunt-part2.md#svcals)*
