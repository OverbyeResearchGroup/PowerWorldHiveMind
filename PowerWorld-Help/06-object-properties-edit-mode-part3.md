---
title: "Object Properties — Edit Mode (Part 3 of 3)"
part: "Viewing Case Data"
chapter_file: "06-object-properties-edit-mode-part3.md"
topics: 18
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Object Properties — Edit Mode (Part 3 of 3)

Edit-mode property dialogs for every Simulator object type.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (18)**

- [Transformer Field Options](#transformer-field-options)
- [DC Transmission Line Options](#dc-transmission-line-options)
- [Line Parameters](#line-parameters)
- [Rectifier/Inverter Parameters](#rectifierinverter-parameters)
- [OPF](#opf)
- [VSC DC Line Dialog](#vsc-dc-line-dialog)
- [Multi-Terminal DC Record Information](#multi-terminal-dc-record-information)
- [Bus Information](#bus-information)
- [Converter Information](#converter-information)
- [Line Information](#line-information)
- [Transformers Bases and Impedances Dialog](#transformers-bases-and-impedances-dialog)
- [Transformer Impedance Correction Table Display](#transformer-impedance-correction-table-display)
- [Transformer Mvar Control Dialog](#transformer-mvar-control-dialog)
- [Transformer Phase Shifting Information](#transformer-phase-shifting-information)
- [Three Winding Transformer Information](#three-winding-transformer-information)
- [Switched Shunt Information](#switched-shunt-information)
- [Switched Shunt Field Information](#switched-shunt-field-information)
- [Zone Information](#zone-information)

---

<a id="transformer-field-options"></a>

## Transformer Field Options

*Source: [`Content/MainDocumentation_HTML/Transformer_Field_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Field_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transformer field display objects are used to show field values specific to transformers on onelines. Use [Line Fields](12-building-onelines-branches-and-devices.md#transmission-line-fields-on-onelines) to show fields generic to transformers and transmission lines, such as the flow of power through the device.

This dialog can be opened by right-clicking on a transformer display field and choosing to open the **Transformer Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a transformer display field.

The transformer field options dialog is used to view and modify the parameters associated with transformer-specific fields.

Near Bus Number

Bus associated with the *near end* of the transformer.

Far Bus Number

Bus associated with the *far end* of the transformer.

Circuit

Two-character identifier used to distinguish between transformers joining the same two buses. Default is '1'.

Find…

If you do not know the exact transformer you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Delta per Mouse Click

This value is used only with the **Off-nominal Tap Ratio** and **Phase Shift Angle** field types. When there is a nonzero entry in this field, and the field type is valid, a spin button is shown to the right of the zone field. When the up spin button is clicked, the field value is increased by this number; when the down button is clicked, the field value is decreased by this amount.

Field Value

Shows the current output for the transformer field. Whenever you change the **Type of Field** selection, this field is updated.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Rotation Angle in Degrees

The angle at which the text is to appear on the oneline diagram.

Anchored

When checked, the text field will move with the transformer if the transformer is moved on the oneline diagram.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Designates the type of transformer field to show. The following choices are available:

Off-nominal Tap Ratio 

Actual tap ratio on the system base. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Phase Shift Angle 

Actual phase shift in degrees. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Off-nominal Tap Position 

Tap position in steps, usually ranging from -16 to +16.

Automatic Control Status 

The status of the control for the transformer. While in run mode left clicking on this field will toggle the automatic control status of the transformer.

Select **OK** to save changes and close the dialog or **Cancel** to close dialog without saving your changes.

---

<a id="dc-transmission-line-options"></a>

## DC Transmission Line Options

*Source: [`Content/MainDocumentation_HTML/DC_Transmission_Line_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Transmission_Line_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters associated with each two-terminal DC transmission line in the system. It can also be used to insert new two-terminal DC transmission lines or to delete existing ones.

The following fields are available regardless of which tab of the dialog is selected:

Rectifier and Inverter Bus Numbers and Names

These fields indicate the numbers and names of the rectifier and inverter ends of the line. When graphically inserting a DC line, these fields are automatically determined based upon the starting and ending buses used in drawing the line. When investigating existing DC line records, you may use the **Find By Numbers** button to identify a DC line between a specific rectifier - inverter pair. You may also use the spin control to cycle through the list of DC line records modeled in the case.

Circuit ID

Two-character identifier used to distinguish between multiple DC lines joining the same two buses. Default is ‘1'.

Find By Numbers

To find a DC line by its bus numbers, enter the **Rectifier** and **Inverter** bus numbers and the **Circuit ID**. Then click this button. Use the spin button to cycle through the list of DC lines in the system.

Area Name

Names of the areas in which the rectifier and inverter buses are located.

Labels

Clicking this button will open the [Subscribed Aliases dialog](07-object-properties-run-mode-and-general-part2.md#labels) displaying the list of defined labels for the DC line. New labels can also be added for the DC Line from this dialog as well.

Link to New DC Line

This button is only available if this dialog is accessed by selecting a [DC transmission line display object](12-building-onelines-branches-and-devices.md#dc-transmission-line-display-objects) or inserting a new one.

Use the *Link to New DC Line* button to link an existing DC transmission line display object to a different DC transmission line. Clicking this button will open a dialog from which the new DC line can be selected.

This dialog has separate pages: [Line Parameters](#line-parameters), [Rectifier/Inverter Parameters](#rectifierinverter-parameters), [OPF](#opf), [Custom](01-getting-started.md#memo-display), and [Stability](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs). The separate pages can be accessed using the tabs shown at the top of the dialog. These pages can be used to view/change the modeling parameters associated with the DC lines.

---

<a id="line-parameters"></a>

## Line Parameters

*Source: [`Content/MainDocumentation_HTML/DC_Line_Options_Line_Parameters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Line_Options_Line_Parameters.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This page is found on the [DC Transmission Line Options](#dc-transmission-line-options) dialog. This page contains the following DC line parameters:

Status

Operating status of the DC transmission line. If the status is *Open*, then no power can flow on the DC line regardless of the control mode setting. If the status is *Closed*, then the control mode will dictate how power flows on the line.

Control Mode

The initial control mode for the line. Specify *Blocked* to disable the DC line, *Power* to maintain specified MW power flow through the line, or *Current* to maintain specified current flow through the line.

Setpoint

If the line operates in the *Power* **Control Mode**, **Setpoint** should indicate the desired power flow in MW. To specify power flow at the rectifier end, enter a positive value. Enter a negative value to specify power flow at the inverter end. If the DC line operates in *Current* **Control Mode**, enter the desired line flow in amps.

Setpoint Margin

Value between 0 and 1. When the DC voltage schedule cannot be achieved, the power or current order will not be reduced by more than this amount multiplied by the setpoint. Beyond this point, the voltage schedule will be reduced instead.

Resistance

Resistance of the DC Line.

Sched. Voltage

Scheduled DC line voltage in kV. The value of Rcomp is used to determine whether this value specifies the inverter end, the rectifier end, or some point in the middle.

Switch Voltage

When the line operates in the *Power* **Control Mode**, this is the inverter voltage level in kV at which the line switches from constant power to constant current control.

RComp

Compounding resistance. The compounding resistance dictates the point along the line where the voltage is controlled. RComp = 0 means the voltage is controlled at the inverter, and RComp = DC Line Resistance means the voltage is controlled at the rectifier. A value equal to one half the resistance of the line means that the voltage is controlled half way along the DC line.

Setpoint Specified At

Indicates which end of the DC transmission line the **Setpoint** value is designated. This will be the terminal where the setpoint value is maintained. The opposite terminal flow value will be a calculated quantity.

Metered End of Line

Indicates which end of the DC line is assumed metered for Area interchange calculations.

Flow

These parameters provide the calculated **MW Flow**, **Mvar Flow**, and **DC Voltage (kV)** at both the rectifier and inverter. **DC Line Current (Amps)** is also provided.

---

<a id="rectifierinverter-parameters"></a>

## Rectifier/Inverter Parameters

*Source: [`Content/MainDocumentation_HTML/DC_Line_Options_Rectifier_Parameters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Line_Options_Rectifier_Parameters.htm)*

This page is found on the [DC Transmission Line Options](#dc-transmission-line-options) dialog. This page is used to enter parameters associated with both the rectifier and inverter end of the dc line.

The following parameters are available for both the rectifier and inverter:

\# of Bridges

Number of valve bridges in series.

Base Voltage

Base AC voltage in kV on primary side of transformer.

XF Ratio

Transformer ratio.

XF Tap

Transformer tap setting.

XF Min/Max Tap, XF Tap Step

Transformer minimum and maximum tap settings, and the tap's step size.

Commuting XF Resistance and Reactance

Commuting resistance and reactance for the transformer, in ohms.

Minimum, Maximum, and Actual Firing Angle

Minimum, maximum, and actual values of the firing angle for the rectifier.

DC transmission line options relate the Power and Reactive Power injections created at DC converter terminals.

Fixed Parameters of the Converter

Nr and Ni = number of bridges at rectifier and inverter

Xcr and Xci = commutating reactance in Ohms per phase

Rcr and Rci = commutating resistance in Ohms per phase (these model converter losses)

Vioder and Vdiodei = diode voltage drop at the rectifier and inverter (these model converter losses)

ACBaser and ACBasei= base AC voltage for the rectifier and inverter

TRr and TRi = ratio of DCBase/ACBase for the rectifier and inverter

Stepr and Stepi= step size for the variable AC tap at the converter

Limiting parameter of the converter

TapMin and TapMax = Minimum and maximum variable AC tap ratio

AlphaMin and AlphaMax or GammaMin and GammaMax= Minimum and maximum firing angle limits at converter

Imax = maximum dc current allowed through the converter

Variables calculated in the DC system

Vdcr, Vdci, Idcr, Idci = DC system voltage and current in kV and kAmps

Alpha and Gamma = firing angle at rectifier and inverter

Tap = Variable AC tap: (Note: TotalTap = FixedTap + Tap - 1.0)

Network Injection Equations for Rectifier and Inverters for the AC power flow solution

For a given terminal AC voltage in per unit, these equations convert the DC quantities into a real and reactive power demand at the terminal bus. The rectifier has positive values while the inverter has negative values.

A Power Flow Solution option exists to ["Disable DC Line Transformer Tap Control](10-power-flow-solution-and-options-part1.md#simulator-options)". If that is chosen then the tap ratios for DC lines will remain fixed.

If tap control is allowed, then the DC taps will move between their minimum and maximum control range trying to keep the firing angle (Alpha or Gamma) and a minimum possible value that is still above the minimum firing angle.

![DCRectifierInverterEquations](images/DCRectifierInverterEquations.png)

---

<a id="opf"></a>

## OPF

*Source: [`Content/MainDocumentation_HTML/DC_Line_Options_OPF.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Line_Options_OPF.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This page is found on the [DC Transmission Line Options](#dc-transmission-line-options) dialog. This page is used to enter parameters associated with the OPF.

Rectifier/Inverter Bus MW Marginal Costs

Displays the marginal costs of the branches terminal buses, following the solution of the OPF.

OPF Control

Minimum and Maximum Setpoint Value

The minimum and maximum setpoint allowed for the DC Line. When on OPF Control the DC Line will be dispatched between these values.

Current Setpoint Value

The current Setpoint as found on the [Line Parameters tab](#line-parameters).

Transmission Charge

This is the cost incurred for moving power across the DC transmission line. The cost is zero at a zero MW flow and increases linearly using this charge.

OPF Control Enabled for this DC line

This check box must be checked if the DC limit is going to be enforced when running an OPF solution. If this box is not checked, the OPF routine will allow the DC line to violate its limits.

Include Impact of DC Line Marginal Losses

When dispatching the DC Line this determines whether the marginal losses from the DC line are taken into account.

Area and Case OPF Control Options

In order for a DC line to be on control during the OPF in addition to control being enabled for the DC line itself, the OPF control of DC lines must be enabled for the area in which the DC line is contained and OPF control of DC lines for the entire case must be enabled. These two options allow enabling DC line OPF control at the area and case level.

---

<a id="vsc-dc-line-dialog"></a>

## VSC DC Line Dialog

*Source: [`Content/MainDocumentation_HTML/VSC DC Line Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/VSC DC Line Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows the modeling of newer types of Voltage Source Converter DC lines, which use Insulated Gate Bipolar Transistors (IGBT) and Gate Turn-off Thyristors (GTO) to perform pulse-width modulation or multi-level switching. They are also referred to as "HVDC Light" (ABB) or "HVDC Plus" (Siemens).

For power flow purposes, these devices are simple: they completely decouple real and reactive power controls.

There is currently no way to display VSC DC lines on oneline diagrams. However, they are displayed in [Bus View](08-view-case-data-tools.md#bus-view-display) (in a similar manner to [Multi-Terminal DC Lines](#line-information)), [Power Flow](05-case-information-displays-by-object-part1.md#power-flow-list), and [Quick Power Flow](05-case-information-displays-by-object-part1.md#quick-power-flow-list) lists.

VSC DC Name

Name of the VSC DC Transmission Line. This is the unique identifier for the device. The dialog field is not editable itself, but the name can be changed with the "Rename" button.

To/From Converter

Gives information about the endpoint buses: the numbers, names, and associated Substations and Areas. These fields are not editable, the information displayed here can only be changed through the buses themselves. The connected buses can be changed on the **Converter Parameters** tab below.

Status

Allows the line to be opened or closed.

Resistance

Set the resistance of the line.

Converter Parameters Tab

This tab gives control over the parameters for the converters on each end of the line.

![VSC Parameters](images/VSC_Parameters.gif)

Terminal Bus

Allows the connected buses to be set.

DC Setpoint

Specifies the DC control mode for each converter, either Out-Of-Service, Voltage, or Power.

DC Setpoint: MW Set Side

Specify whether the DC MW Setpoint is interpreted as the MW flow on the "DC side" or "AC Side" of the converter. If there are not any converter losses modeled then this does not matter.

![VSC Mode Table](images/VSC_Mode_Table.gif)

AC Setpoint

Specifies the AC control mode for each converter, either per unit Voltage or Power Factor. If the AC control mode is set to Voltage and the other converter is out of service, it acts as an SVC.

Regulated Bus, Remote Regulation %

When the AC mode is Voltage, the Regulated Bus does not have to be the converter AC terminal. If this is blank, it signifies it regulated its own terminal. For more information on Remote Regulation, refer to the [Generator Information Power and Voltage Control page](06-object-properties-edit-mode-part1.md#power-and-voltage-control).

A loss, B loss

The converter losses for each end are defined as: ConverterLosskW = A<sub>loss</sub> + I<sub>dc</sub>\*B<sub>loss</sub>

Minimum Loss

If this field is specified, it sets a lower bound on the value calculated from A<sub>loss</sub>, B<sub>loss</sub> and I<sub>DC</sub>

Maximum AC MVA

Converter MVA rating specified in MVA. If set to 0, there is no limit.

Maximum AC Current

Converter current rating in amps. If set to 0, there is no limit.

Power Weighting Factor

Power weighting factor is a value between 0 and 1. It is used to reduce real and reactive power when limits are hit.

Maximum Mvar

Maximum Mvar injection into the AC network. This is used only when the AC mode is Voltage.

Minimum Mvar

Minimum Mvar injection into the AC network. This is used only when the AC mode is Voltage.

Flows and Voltages Tab

These fields are not editable.

AC MW Flow

The real power flow on the AC side of the converter.

AC MVar Flow

The reactive power on the AC side of the converter.

DC MW Flow

The power flow on the DC side of the converter.

DC Voltage

The voltage on the DC side of the converter, in kV.

DC Line Current

The current flowing on the DC line, in amps.

Custom Tab

Tab containing [Custom Fields](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

Stability Tab

Tab for configuring the VSCDC Line Model for stability analysis

---

<a id="multi-terminal-dc-record-information"></a>

## Multi-Terminal DC Record Information

*Source: [`Content/MainDocumentation_HTML/Multi_Terminal_DC_Record_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Terminal_DC_Record_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters associated with multi-terminal DC records. It is also used when inserting new multi-terminal DC records.

The Multi-Terminal DC Record dialog can be used to inspect and modify the model of a multi-terminal DC network record. To view the Multi-Terminal DC Record, simply right-click on the record of interest in the [Multi-Terminal DC Record Display](05-case-information-displays-by-object-part2.md#multi-terminal-dc-record-display) and select *Show Dialog* from the resulting popup menu. The dialog has the following fields:

Record Number

Unique number between 1 and 999 which identifies the current multi-terminal DC record.

Number of Devices

Lists the number of DC buses, converters, and DC Lines that form the multi-terminal DC network.

Control

The control method used when solving the multi-terminal DC network.

Controlling Converter

The AC converter bus number where the DC voltage is being controlled.

MTDC Network Status

Status of the entire Multi-terminal DC network. If this field is set to Closed, the entire DC subnetwork of the MTDC model is considered disconnected in the load flow case.

DC Buses Tab

This page of the dialog displays the DC bus records for the multi-terminal DC network. The display on this page exhibits the same features as other [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays). To view the specific information for a DC bus, right-click on the record of interest and choose *Show Dialog* from the popup menu.

DC Converters Tab

This page of the dialog displays the DC converter records for the multi-terminal DC network. The display on this page exhibits the same features as other [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays). To view the specific information for a DC converter, right-click on the record of interest and choose *Show Dialog* from the popup menu.

DC Lines Tab

This page of the dialog displays the DC line records for the multi-terminal DC network. The display on this page exhibits the same features as other [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays). To view the specific information for a DC line, right-click on the record of interest and choose *Show Dialog* from the popup menu.

Custom Tab

Enter any text notes you wish in the Memo page. When the case is saved as a Simulator PWB file, the memo text will also be saved. Custom strings and values can also be entered and saved with the case file as well.

---

<a id="bus-information"></a>

## Bus Information

*Source: [`Content/MainDocumentation_HTML/Multi_Terminal_DC_Bus_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Terminal_DC_Bus_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters specific to multi-terminal DC network buses. The dialog is also used to enter values for new multi-terminal DC buses when inserting a [Multi-Terminal DC Record](#multi-terminal-dc-record-information).

To view the Multi-Terminal DC Bus Record dialog, right-click on a bus record in the DC Buses tab of the [Multi-Terminal DC Record dialog](#multi-terminal-dc-record-information) and select *Show Dialog* from the resulting popup menu. The dialog has the following fields:

DC Bus Number, DC Bus Name

The number and name identifiers for the selected DC bus.

AC Bus Number

The AC bus number connected to the DC bus through an AC/DC converter. If the selected DC bus is a bus that is internal to the DC multi-terminal network (not directly connected to an AC bus,) this field will be 0.

Area Number, Area Name

The number and name identifiers of the control area the DC bus is contained in.

Zone Number, Zone Name

The number and name identifiers of the zone the DC bus is contained in.

Ground Resistance

Resistance to ground of the DC bus, entered in Ohms. This field is currently only for storage of values supported by other load flow formats, and is currently not used by Simulator.

---

<a id="converter-information"></a>

## Converter Information

*Source: [`Content/MainDocumentation_HTML/Multi_Terminal_DC_Converter_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Terminal_DC_Converter_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters specific to multi-terminal DC network buses. The dialog is also used to enter values for new multi-terminal DC buses when inserting a [Multi-Terminal DC Record](#multi-terminal-dc-record-information).

To view the Multi-Terminal DC Bus Record dialog, right-click on a bus record in the DC Buses tab of the [Multi-Terminal DC Record dialog](#multi-terminal-dc-record-information) and select *Show Dialog* from the resulting popup menu. The dialog has the following fields:

Converter Parameters

Number of Bridges

Number of bridges in series for the selected converter.

Converter Type

**R** for rectifier or **I** for inverter.

Commutating Impedance

Commutating impedance per bridge, in Ohms.

Firing Angle Limits

The maximum and minimum firing angle limits, in degrees.

Transformer Parameters

AC Base

The primary AC base voltage, in kV.

DC Base

The DC base voltage, in kV.

Transformer Ratio

Actual transformer ratio.

Tap Settings

Displays the actual tap setting, the tap step, and maximum and minimum tap values for the converter transformer.

Control Parameters

Setpoint

The setpoint control value at the converter. For the voltage-controlling converter, this field is set to 0. For the remaining converters, this field displays MW when in Power mode, or Amps when in Current mode.

Margin

Rectifier margin, entered in per-unit of the DC power or current. This field is currently only for support of other load flow formats, and is not used by Simulator.

DC Participation Factor

Converter participation factor. This field is currently only for support of other load flow formats, and is not used by Simulator.

Voltage

The DC Voltage magnitude at the DC side of the converter.

Solved Parameters

Firing Angle

The firing angle of the converter, as determined during the load flow solution.

DC Current

The calculated DC current at the converter DC terminal.

MW, MVAR

The real and reactive power delivered to (or absorbed from) the AC system by the converter.

---

<a id="line-information"></a>

## Line Information

*Source: [`Content/MainDocumentation_HTML/Multi_Terminal_DC_Line_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Terminal_DC_Line_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters specific to multi-terminal DC network buses. The dialog is also used to enter values for new multi-terminal DC buses when inserting a [Multi-Terminal DC Record](#multi-terminal-dc-record-information).

To view the Multi-Terminal DC Bus Record dialog, right-click on a bus record in the DC Buses tab of the [Multi-Terminal DC Record dialog](#multi-terminal-dc-record-information) and select *Show Dialog* from the resulting popup menu. The dialog has the following fields:

From and To DC Bus Number

The DC bus numbers of the From and To buses in the multi-terminal DC network. These fields must contain valid DC bus numbers of the selected multi-terminal DC record. AC bus numbers from the load flow case are not acceptable bus numbers for a multi-terminal DC line.

DC Circuit

The circuit identifier for the DC line.

DC Resitance and DC Inductance

The resistance and inductance of the DC line. Resistance is in Ohms, and is used for solving the load flow of the DC network. The inductance is in milliHenries, and is not used for solving the load flow. The inductance field is currently only for support of other load flow formats, and is not used by Simulator.

---

<a id="transformers-bases-and-impedances-dialog"></a>

## Transformers Bases and Impedances Dialog

*Source: [`Content/MainDocumentation_HTML/Transformers_Bases_and_Impedances_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformers_Bases_and_Impedances_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Typically the impedances and tap values of transformers is already assumed to have been converted to unity tap base and bus nominal voltage base. However, some load flow formats provide the taps and impedances on specific transformer bases, which are different than the bus voltage and unity tap base assumptions. In these cases, Simulator will convert parameters from the transformer bases to the unity tap and bus nominal voltage base. Display of the impedances and tap values normally displayed in the [Branch Options](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) dialog are displayed on the Simulator assumed bases. However, if you wish to view the original transformer values on the transformer supplied bases, this dialog will display the original values. You can modify the original values stored here in this dialog. Note that when you do so, the converted values that Simulator stores on the system bases will also be automatically updated to reflect the change that has been made to the original values on the transformer bases.

---

<a id="transformer-impedance-correction-table-display"></a>

## Transformer Impedance Correction Table Display

*Source: [`Content/MainDocumentation_HTML/Transformer_Impedance_Correction_Table_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Impedance_Correction_Table_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transformer Impedance Correction Display shows information about all the transformer impedance correction tables in the case. The Transformer Impedance Correction Display is used to model the change in the impedance of the transformer as the off-nominal turns ratio or phase shift angle is varied.

The impedance correction display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables) of its associated correction tables. When in Edit Mode, you can define new tables using the **Insert** option, or delete existing tables using **Delete** .

To show this display select **Network \> Impedance Correction Tables** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The display contains the following fields by default:

Table \#, Table Name

Shows the table number and name for the record.

Transformer Impedance Scaling Factors

The rest of the default columns show the actual fields in the table. The first field of each pair shows the off-nominal turns ratio or phase shift angle and is named *Tap*, while the second field shows the associated scaling factor for the transformer’s impedance and is named *Value*. Up to 100 points are allowed for each table. To determine the appropriate scaling factor, interpolation will be used based on the current tap or phase angle.

---

<a id="transformer-mvar-control-dialog"></a>

## Transformer Mvar Control Dialog

*Source: [`Content/MainDocumentation_HTML/Transformer_Mvar_Control_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Mvar_Control_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transformer Mvar Control dialog is used to view the control parameters associated with load-tap-changing (LTC) transformers that are used to control the Mvar flow through the transformer. To view this dialog, click on the **Change Automatic Control Options** button found with the [Transformer Control options](06-object-properties-edit-mode-part2.md#transformer-control), provided that the *Reactive Power Control* option is chosen from the **Automatic Control Type** group.

When used to control reactive power, the LTC transformer always controls the reactive power flow at the *from* end of the transformer (i.e., the tapped side), with positive flow assumed to be going through the transformer to the *to* bus. Therefore the regulated bus field is not used.

The **Common Options** tab of this dialog has the following fields:

Automatic Control Type

This section is only visible on the dialog in edit mode. The control type of the transformer can be changed between no control, voltage regulation, reactive power control, or phase shifter control. Changing the control type will update the dialog to reflect the type of control that is selected.

Mvar Flow at *From* Bus

The current Mvar flow as measured at the *from* end of the line. This is the parameter the transformer tries to control.

Mvar Error

If the Mvar flow at the *from* end violates the limits defined by the **Regulation Minimum Mvar Flow** and **Regulation Maximum Mvar Flow** fields, the **Mvar Error** field indicates by how much the flow falls outside the control range.

Regulation Minimum Mvar Flow, Regulation Maximum Mvar Flow

Minimum and maximum allowable reactive power flow as measured at the *from* bus. The transformer attempts to regulate the reactive flow to fall within this range.

Regulation Target Type

As long as the regulated Mvar flow is inside the regulation minimum and maximum, the transformer will not change its tap ratio. When the regulated Mvar flow moves outside of this regulation range, Simulator will calculate a new tap ratio in an attempt to bring the regulated Mvar flow back inside of its range. The **Regulation Target Type** determines what value is used as a target when calculating this change in tap ratio. **Middle** is the default and means that the target is the average of the regulation minimum and maximum regardless of whether the Mvar flow is high or low. **Max/Min** means that the regulation maximum is used as the target when the regulated Mvar flow is above the maximum, and regulation minimum is used as the target value when the regulated Mvar flow is below the minimum.

Present Tap Ratio

The transformer's present off-nominal turns ratio.

Minimum Tap Ratio, Maximum Tap Ratio

Minimum and maximum allowable off-nominal tap ratios for the LTC transformer. Typical values are 0.9 and 1.1.

Tap Step Size

Transformer off-nominal turns ratio increment. The off-nominal turns ratio is either incremented or decremented from 1.0 in integer multiples of this value. Default value is 0.00625.

Mvar to Tap Sensitivity

The amount of Mvar shift that would be implemented by switching one tap position from the current position. This sensitivity indicates the ability of the transformer to control Mvars.

Impedance Correction Table

Specifies the number of the transformer's corresponding transformer impedance correction table. Transformer impedance correction tables are used to specify how the impedance of the transformer should change with the off-nominal turns ratio. If this number is 0, no impedance correction table is associated with the transformer, and the impedance of the transformer will thus remain fixed as the tap ratio changes. Valid impedance correction table numbers range from 1 to 63. To assign an existing impedance correction table to the transformer, enter the existing table's number. To view the existing impedance correction tables, click the **Insert/View Impedance Correction Table** button, which brings up the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). To define a brand new impedance correction table for the transformer, enter an unused table number and then click **Insert/View Impedance Correction Table** to prescribe the correction table. Note that the association between a transformer and an impedance correction table is not finalized until you select either **OK** or **Save** on the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) or [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options).

View Transformer Correction Table or Insert Transformer Correction Table

Click on this button either to view or to insert transformer correction tables. Clicking on this button displays the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). Note that a table must contain at least two points in order to be defined.

The [Time Step Options](26-time-step-simulation-part2.md#transformer-control-time-step-options) tab contains control options specific for the Time Step Simulation tool.

---

<a id="transformer-phase-shifting-information"></a>

## Transformer Phase Shifting Information

*Source: [`Content/MainDocumentation_HTML/Transformer_Phase_Shifting_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Phase_Shifting_Information.htm)*

The Transformer Phase Shifting Dialog is used to view the control parameters of phase-shifting transformers. To view this dialog, click on the **Change Automatic Control Options** button found with the [Transformer Control options](06-object-properties-edit-mode-part2.md#transformer-control), provided that the *Phase Shift Control* option is chosen from the **Automatic Control Type** group.

The **Common Options** tab of this dialog has the following fields:

Automatic Control Type

This section is only visible on the dialog in edit mode. The control type of the transformer can be changed between no control, voltage regulation, reactive power control, or phase shifter control. Changing the control type will update the dialog to reflect the type of control that is selected.

Regulated Bus Number

Regulated Bus number is not used for a phase shifting transformer. A phase shifting transformer regulates the MW flow going in the direction of From Bus towards To Bus of itself.

Current MW Flow

Current MW flow through the transformer measured at the regulated bus terminal.

MW Error

If the current MW flow falls outside the minimum/maximum MW flow limits, the **MW Error** field indicates by how much the flow violates the regulating range.

Regulation Minimum MW Flow, Regulation Maximum MW Flow

Minimum and maximum allowable MW flow through the phase shifter.

When solving the DC power flow, phase shifters will always control to the middle of this regulation range regardless of the Regulation Target Type.

Regulation Target Type

As long as the regulated MW flow is inside the regulation minimum and maximum, the transformer will not change its phase angle. When the regulated MW flow moves outside of this regulation range, Simulator will calculate a new phase angle in an attempt to bring the regulated MW flow back inside of its range. The **Regulation Target Type** determines what value is used as a target when calculating this change in phase angle. **Middle** is the default and means that the target is the average of the regulation minimum and maximum regardless of whether the MW flow is high or low. **Max/Min** means that the regulation maximum is used as the target when the regulated MW flow is above the maximum, and regulation minimum is used as the target value when the regulated MW flow is below the minimum.

When solving the DC power flow, phase shifters will always control to the middle of the regulation range regardless of the specified target type.

Present Phase Angle (Degrees)

The phase angle of the transformer for the current solved system state.

Minimum Phase Angle, Maximum Phase Angle

Minimum and maximum allowable phase shift in degrees.

Step Size (Degrees)

Phase shift change per step in degrees.

MW Flow to Phase Sensitivity

The sensitivity of the controlled MW flow to changes in the transformer's phase. This sensitivity indicates the transformer's ability to regulate its MW flow.

Impedance Correction Table

Specifies the number of the transformer's corresponding transformer impedance correction table. Transformer impedance correction tables are used to specify how the impedance of the transformer should change with the phase angle. If this number is 0, no impedance correction table is associated with the transformer, and the impedance of the transformer will thus remain fixed as the phase angle changes. Valid impedance correction table numbers range from 1 to 63. To assign an existing impedance correction table to the transformer, enter the existing table's number. To view the existing impedance correction tables, click the **Insert/View Impedance Correction Table** button, which brings up the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). To define a brand new impedance correction table for the transformer, enter an unused table number and then click **Insert/View Impedance Correction Table** to prescribe the correction table. Note that the association between a transformer and an impedance correction table is not finalized until you select either **OK** or **Save** on the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) or [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options).

View Transformer Correction Table or Insert Transformer Correction Table

Click on this button either to view or to insert transformer correction tables. Clicking on this button displays the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). Note that a table must contain at least two points in order to be defined.

The [Time Step Options](26-time-step-simulation-part2.md#transformer-control-time-step-options) tab contains control options specific for the Time Step Simulation tool.

---

<a id="three-winding-transformer-information"></a>

## Three Winding Transformer Information

*Source: [`Content/MainDocumentation_HTML/Three_Winding_Transformer_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Three_Winding_Transformer_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Three Winding Transformer Dialog is used to create, modify or delete three winding transformer records in Edit Mode, or to view information for a specific three winding transformer record in run mode. Note that all the values displayed on this dialog are on the system MVA base. If the records were created them from a file, the values are automatically converted to the system base. If a three winding transformer record is entered manually, the parameters need to be entered into Simulator computed with the same system MVA base Simulator is using.

This dialog has the following controls:

Primary Winding

This section of the dialog displays the primary winding terminal bus number, nominal kV, and fixed tap value (in per unit). In addition, the automatic tap changer is assumed to be on the primary winding of a three winding transformer. Therefore the LTC field displays the tap changer tap value (in per unit) on the primary winding.

Secondary Winding

This section of the dialog displays the secondary winding terminal bus number, nominal kV, and fixed tap value (in per unit).

Tertiary Winding

This section of the dialog displays the tertiary winding terminal bus number, nominal kV, and fixed tap value (in per unit).

Star Bus (Internal Node)

This section of the dialog displays the internal node parameters of the three winding transformer model. Three winding transformers are modeled as three two winding transformers connected at the three winding transformer terminal buses to a common or internal node, referred to as the star bus. The parameters displayed for the star bus are the bus number, voltage (in per unit), and angle.

Primary-Secondary, Secondary-Tertiary, and Tertiary-Primary Impedance

These are the actual three winding transformer winding to winding impedances, in per unit on the system base. These values are used to compute the equivalent two winding transformer impedances for the two winding transformers used to model the three winding transformer operation.

Transformer Parameters

The values for the magnetizing conductance (G) and magnetizing susceptance (G), in per unit on the system base.

Circuit ID

The circuit identifier for the three winding transformer.

Status

The status of the three winding transformer. If checked, the three winding transformer model is in service, otherwise the equivalent model is treated as out of service.

Mathematically equivalent two-winding transformers

This table displays the three two winding transformers that are mathematically equivalent representations of the three winding transformer. If you read the three winding transformer record from a file, the two winding equivalent transformers are created automatically. If you are inserting a three winding transformer manually, you can set the parameters for the primary, secondary and tertiary windings in the fields above, then click the **Set Two-Winding Equivalent Transformers** button to have Simulator automatically create the two winding transformer records for you. You can also right-click in this table and insert, modify or delete two winding transformers manually if you already have the two winding transformer representations created.

Once you are finished with the dialog, you can click **Save** or **OK** to save any changes. If you wish to abandon any changes you have made, click **Cancel**.

---

<a id="switched-shunt-information"></a>

## Switched Shunt Information

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Information_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Information_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Switched Shunt Options dialog is used to view and modify the parameters associated with each switched shunt in the system. It can also be used to insert new switched shunts and to delete existing shunts. Multiple switched shunts are permitted at each bus and are allowed to be on automatic control at each bus. Switched shunts usually consist of either capacitors to supply reactive power (in Mvar) to the system, or reactors to absorb reactive power. The switched shunts are represented by a number of blocks of admittance that can be switched in a number of discrete steps.

This dialog can be accessed by right-clicking on a switched shunt display object and choosing **Switched Shunt Information Dialog** or right-clicking on a switched shunt record in the [Switched Shunt Display](05-case-information-displays-by-object-part3.md#switched-shunt-display) and choosing **Show Dialog**.

The Edit mode version of this dialog is very similar in content to its [Run mode](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) counterpart.

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus to which the switched shunt is attached. You can use the spin button immediately to the right of the number to move to the next switched shunt (click the up arrow) or the previous switched shunt (click the down arrow).

Find By Number

To find a switched shunt by its bus number, enter the number into the Bus Number field. Then click this button.

Bus Name

Unique alphabetic identifier for the bus to which the switched shunt is attached, consisting of up to eight characters.

Find By Name

To find a switched shunt by its bus name, enter the bus name into the Bus Name field (case insensitive). Then click this button.

Shunt ID

Since multiple switched shunts are allowed on a single bus, each switched shunt has a unique Shunt ID.

Find…

If you do not know the exact switched shunt bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Open or closed status of the switched shunt.

Status Branch Added in Version 20

Line shunts can be modeled as controllable switched shunts by linking their status to the status of a branch. The Status Branch field specifies a branch whose status will affect the status of a switched shunt. If specified, a switched shunt can only be closed if is has a status of closed and its Status Branch also has a status of closed. If the Status Branch has a status of open, the switched shunt will also have a status of open.

Click the **Choose Branch** button to open a dialog that allows selection of this branch. Click the **Remove** button to no longer associate this switched shunt with a branch.

Labels

Clicking on this button will open the [Label Manager](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) [Dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the [labels](07-object-properties-run-mode-and-general-part2.md#labels) assigned to the selected switched shunt.

Area Number, Area Name

The area number and name to which the switched shunt belongs. Note that you can change the area of the switched shunt to be different than the area of the terminal bus. If you do so, you will be prompted to confirm that you wish to place the switched shunt within a different area than that of the bus to which it is electrically connected.

Zone Number, Zone Name

The zone number and name to which the switched shunt belongs. Note that you can change the zone of the switched shunt to be different than the zone of the terminal bus. If you do so, you will be prompted to confirm that you wish to place the switched shunt within a different zone than that of the bus to which it is electrically connected.

Substation Number, Substation Name

The name and number of the substation to which the switched shunt belongs. This is the same as that of the terminal bus.

Display

Display Size

Size of the switched shunt.

Display Width

Width of the switched shunt symbol.

Scale Width with Size

Automatically scales the width of the symbol when the object is resized.

Pixel Thickness

Thickness of the display object in pixels.

Orientation

Specifies the direction in which to draw the object.

Anchored

If checked, the object is anchored to its terminal bus. See [Anchored Objects](11-building-onelines-network-objects.md#anchored-objects) for details.

Link to New Shunt

Adds a new record in the data or links the selected shunt display object to a different record.

OK, Save, Delete, and Cancel

**OK** saves your changes and closes the dialog. **Save** saves your changes but does not close the dialog; this allows you to use, for example, the Find By Number command to edit additional switched shunts. **Delete** deletes the current switched shunt; this option is not available when inserting objects graphically or opening the dialog by selecting a display shunt object– use the cut command instead. **Cancel** closes the dialog but does not save any changes.

Parameters

Nominal Mvar

The Nominal Mvar field gives the amount of reactive power the device would supply (in Mvars) if its terminal voltage were 1.0 per unit.

Nominal MW

This field is only visible when a switched shunt already has a non-zero MW value assigned. This could occur when the switched shunt has been read from an external file as a Bus Shunt with associated MW. The MW value can also be assigned through the [case information display for a switched shunt](05-case-information-displays-by-object-part3.md#switched-shunt-display). The MW component of a switched shunt has no controllability.

Control Mode

Information about this option can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Regulation Settings

Information about these options can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Switched Shunt Blocks

Information about these settings can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Voltage Control Groups Added in Version 19

Specify if the switched shunt belongs to a voltage control groups. For more information on how voltage control groups work see the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Parameters: Advanced Options

Information about these options can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Parameters: Time Step Options

The [Time Step Options](26-time-step-simulation-part2.md#switched-shunt-control-time-step-options) tab contains control options specific for the [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation) tool.

Control Parameters: SVC Control Options

The SVC Control Options tab contains control options parameters specific for the [SVC Shunt Contro](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode)l.

Control Parameters: SVC Fixed Shunt Options

The SVC Fixed Shunt Options tab contains information of the SVC controlling the shunt ([SVC Shunt Contro](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode)l).

Fault Parameters

Typically switched shunts are treated as open circuits in the zero sequence data for fault analysis. However, it is possible to define zero sequence admittance blocks to be used. The blocks work similarly to the load flow Switched Shunt Blocks discussed above. Usually there will be the same number of blocks in the zero sequence data as in the load flow data. Simulator will determine how many blocks were switched in for the power flow solution, and then use the zero sequence block data to calculate the zero sequence admittance for the same number of blocks.

Custom

This page of the dialog contains three sections: Data Maintainer, Custom Fields, and Memo. 

A [Data Maintainer](07-object-properties-run-mode-and-general-part1.md#datamaintainer) may be specified for the switched shunt by clicking on the **Specify** button. Click the **Remove** button to unassign a data maintainer.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the switched shunt. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the switched shunt. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

Stability

This tab contains information that is used with the [Transient Stability Add-On](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) tool. Any switched shunt-specific transient stability modeling information is contained on this tab. For more information see the [Transient Stability Data: Object Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs).

---

<a id="switched-shunt-field-information"></a>

## Switched Shunt Field Information

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Field_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Field_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched shunt field display objects are used primarily to indicate various quantities associated with switched shunt devices on onelines. Some switched shunt field types, which are distinguished by an integrated spin button, may be used to change switched shunt device properties.

This dialog can be opened by right-clicking on a switched shunt display field and choosing to open the **Switched Shunt Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a switched shunt display field.

The Switched Shunt Field Options dialog can be used to modify the properties of individual switched shunt fields on the oneline. The dialog displays the following fields:

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Bus Number

Number of the bus to which the switched shunt associated with the field is connected. Use the dropdown box to view a list of all buses with switched shunts in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Bus Name

Name of the bus to which the switched shunt associated with the field is connected. Use the dropdown box to view a list of all buses with switched shunts in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

ID of the switched shunt associated with the field.

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Delta Per Mouse Click

Switched shunt fields can be used not only to show various fields associated with switched shunt devices, but they can also be used to change some values. This is accomplished using spin buttons shown to the right of the switched shunt field. When the up spin button is clicked, the switched shunt field value is increased by the amount specified in the *delta per mouse click* field. When the down spin button is clicked, the switched shunt field value is decreased by the same amount.

This field is only used for Switched Shunt Mvar fields. Specifying a nonzero value in this field causes the integrated spin button to appear as part of the switched shunt field on the oneline.

Rotation Angle in Degrees

The angle at which the text is placed on the diagram, in degrees.

Anchored

If this checkbox is checked, the switched shunt field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated switched shunt, which means that it will move with the switched shunt.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of switched shunt field to show. The following choices are available:

Switched Shunt Mvar 

Total Mvar capacitance at the bus. This is the only field for which the **Delta per Mouse Click** option is applicable.

Select a Field 

Choose from any of the available switched shunt fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="zone-information"></a>

## Zone Information

*Source: [`Content/MainDocumentation_HTML/Zone_Information_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Information_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Zone Dialog is used in the Edit Mode to view information about a zone and to move one or more buses from one zone to another. (See [Zone Information (Run Mode)](07-object-properties-run-mode-and-general-part1.md#zone-information) for help on the corresponding Run Mode version.) To view this dialog, open the [Zone Records Display](05-case-information-displays-by-object-part1.md#zone-display) by clicking on **Aggregations \> Zones** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). Then, right-click on the desired zone record and select **Show Dialog** to view this dialog.

The dialog has the following fields:

Zone Number

Zone number between 1 and 999. You can use the spin button immediately to the right of this field to move to either the next zone (click the up arrow) or the previous zone (click the down arrow).

Zone Name

Alphanumeric identifier for the zone. You can use this field to change the zone's name, provided you click either **Save** or **OK.**

Find By Number

To find a zone by its number, type the number in the **Number** field and click this button.

Find…

If you do not know the exact zone number you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Labels

To assign alternative identifying labels to the zone, click the Labels button, which will open the [Label Manager Dialog](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) listing all the labels assigned for the selected zone.

OK, Save, Cancel 

**OK** saves any changes to the zone name and closes the dialog. **Save** saves any changes to the zone name, but does not close the dialog. **Cancel** closes the dialog ignoring any changes.

The zone dialog contains three additional pages of information:

Zone Buses Table

This table lists all of the buses in the zone. Number, name, voltage, area number, and area name are shown for each bus. This table can be used to move buses to a different zone. Select the bus or buses you would like to move with the mouse. Then, enter the **Destination Zone Number**, which is the zone to which you want to move the selected buses. You may enter a zone number that does not already exist, too, so that the buses will be moved to a brand new zone. In this case, be sure to provide the **Zone Name**, as well. Finally, click the **Move Selected Bus(es) to Destination Zone** button to implement the move.

OPF

The **Reserve Requirement Curves** options are only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview). More information about these options can be found in the [Area and Zone OPF Reserve Requirement Curves topic](31-scopf-and-opf-reserves.md#area-and-zone-opf-reserve-requirement-curves).

Custom

The Custom Page of the Zone Information dialog displays custom numbers or strings defined with the viewed zone. The [Memo](01-getting-started.md#memo-display) box is simply a location to log information about the zone. To log information about the zone, simply start typing your information or comments about the zone in the memo box.
