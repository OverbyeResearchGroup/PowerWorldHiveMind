---
title: "Object Properties — Edit Mode (Part 2 of 3)"
part: "Viewing Case Data"
chapter_file: "06-object-properties-edit-mode-part2.md"
topics: 12
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Object Properties — Edit Mode (Part 2 of 3)

Edit-mode property dialogs for every Simulator object type.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (12)**

- [Transmission Line/Transformer Options](#transmission-linetransformer-options)
- [Display](#display)
- [Parameters](#parameters)
- [Line Shunts Information](#line-shunts-information)
- [Line Per Unit Impedance Calculator Dialog](#line-per-unit-impedance-calculator-dialog)
- [Transmission Line Parameter Calculator](#transmission-line-parameter-calculator)
- [Transformer Control](#transformer-control)
- [Transformer AVR Dialog](#transformer-avr-dialog)
- [Series Capacitor](#series-capacitor)
- [Multi-Section Line Information](#multi-section-line-information)
- [Line Field Information](#line-field-information)
- [Series Capacitor Field Options](#series-capacitor-field-options)

---

<a id="transmission-linetransformer-options"></a>

## Transmission Line/Transformer Options

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Branch Options dialog is used to view and modify the parameters associated with each transmission line and transformer in the system. You can also insert new transmission lines and delete existing transmission lines from this dialog. From this dialog, you can also open dialogs for attached devices.

The Edit Mode version of this dialog is very similar in content to its [Run Mode](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) counterpart.

The Branch Options dialog has the following fields:

From Bus Number and Name

*From Bus* number and name. For transformers, the *from bus* is the tapped side.

To Bus Number and Name

*To Bus* number and name.

Circuit

Two-character identifier used to distinguish between multiple lines joining the same two buses. Default is ‘1'.

Find By Numbers

To find a line or transformer by its bus numbers, enter the *from* and *to* bus numbers and the circuit identifier. Then click this button. Use the spin button to cycle through the list of lines and transformers in the system.

Find By Names

To find a line or transformer by the names of its terminal buses, enter the *from* and *to* bus names and the circuit identifier. Then click this button.

Find…

If you do not know the exact from and to bus numbers or names you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

From End Metered

This field is only used for lines and transformers that serve as tie lines, which are lines that join two areas. If this field is checked for a tie line, then the *from* end of the device is designated as the metered end. Otherwise the *to* end is metered. By default, the *from* end is metered. The location of the metered end is important in dealing with energy transactions because it determines which party must account for transmission losses.

Default Owner (Same as From Bus)

Read-only check-box that indicates whether the line’s owner is the same than the from bus’ owner.

From and To Bus Area Name

Name of control area in which each terminal bus is located.

From and To Bus Nominal kV

Nominal voltage level of each terminal bus, in kV.

Labels

Clicking on this button will open the [Label Manager](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) [Dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the [labels](07-object-properties-run-mode-and-general-part2.md#labels) assigned for the selected branch.

OK, Save, Delete, Cancel, and Help

**OK** saves your changes and closes the dialog. **Save** saves your changes but does not close the dialog; this allows you to use, for example, the **Find By Number** command to edit additional transmission lines. **Delete** deletes the current branch. The Delete button is not visible if editing a branch that was accessed via the oneline diagram. **Cancel** closes the dialog but does not save any changes. **Help** opens this help topic.

Display

See [Branch Options: Display](#display).

Parameters

See [Branch Options: Parameters](#parameters).

Transformer Control

This tab is only visible for transformer objects. See [Transformer Control](#transformer-control) for details on modeling either LTC or phase shifting transformers.

Series Capacitor

This tab is only visible for series capacitor objects. See [Series Capacitor](#series-capacitor) for details on modeling series capacitors.

Fault Info

The parameters on this tab are used when running a [fault analysis](27-fault-analysis.md#fault-analysis) study. The values represent the zero sequence impedance and zero sequence line shunt admittances for the analysis. By default, the positive and negative sequence line impedances and line shunt admittances are the same as the load flow impedance. The same fields are used for transformers, along with the configuration field. The configuration field defines the winding type combinations for the transformer (wye, delta, etc.) As a default, Simulator assumes a grounded wye to grounded wye transformer, which has the same model as a transmission line. Usually transformers are not of this type, and the proper type would need to be defined either manually or loaded from an external file in order for the fault analysis to be accurate.

Owner, Area, Zone, Sub

The **Default Owner (Same as From Bus)** read-only check-box indicates whether the branch’s owner is the same as the from bus’ owner. Transmission elements can have up to four different owners, each with a certain owner percentage. To add an owner of a transmission element, change one of the Owner fields to a new owner number, and update the owner percentages accordingly. Note that if you do not set the new owner percentages of all specified owners such that the total is 100%, Simulator will normalize the percentages such that the total is 100% when you click **Save** or **OK** on the branch options dialog.

The area, zone, and substation to which the From and To buses belong, are also shown.

Custom

This page of the dialog contains two sections: custom fields and memo. 

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the branch. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the branch. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

Stability

This tab is only visible with the [Transient Stability Add-On](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) tool. Any branch-specific transient stability modeling information is contained on this tab. For more information see the [Transient Stability Data: Object Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs).

---

<a id="display"></a>

## Display

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Display tab of the [Branch Options](#transmission-linetransformer-options) dialog is available when opening the dialog by right-clicking on a display object.

Pixel Thickness

Thickness of the display object in pixels.

Anchored

If checked, the object is anchored to its terminal bus, which means that it will move when you move the terminal bus. See [Anchored Objects](11-building-onelines-network-objects.md#anchored-objects) for details.

Link to New Line

Use the **Link to New Line** button to create a new line corresponding to the entries you have made in the dialog. This button performs the same function as pressing **Save**. Note that adding a new line to the case in this way does not add a transmission line to the oneline display; the new line is present only in the model. You may then add the newly modeled line to the oneline diagram in the usual way (such as select **Network \> Transmission Line** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab).

Symbol Segment

Only visible for transformer and series capacitor objects. This field specifies which "segment" of the branch contains the transformer or capacitor symbol. A segment constitutes a section of the line between vertex points of the line object, and are numbered starting at the from bus.

Symbol Size

Only visible for transformer and series capacitor objects. Specifies the size (width) of the transformer or capacitor symbol on the branch.

Symbol Percent Length

The distance or "length" of the symbol on the segment of the branch which contains it.

Show Detailed Line Vertices

When checking this option, a new group of information appears, showing the x,y coordinates of every vertex of the line. Additionally to being able to edit those locations, it is possible to shift or scale all the values with the buttons **Shift All Values** and **Scale All Values**, respectively.

---

<a id="parameters"></a>

## Parameters

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Parameters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Parameters.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Parameters tab of the [Branch Options](#transmission-linetransformer-options) dialog displays the common parameters required for defining a transmission branch.

Status

Current status of the device. Either *Open*or *Closed*.

Length

If the length of the line is known, it can be entered here in miles for informational purposes.

Per Unit Impedance Parameters

The series resistance and reactance (R and X), the total charging susceptance (that is, B, not B/2) and the shunt conductance (G) of the device (in per unit). In the case of transformers, the magnetizing conductance and susceptance can also be specified.

Line Shunts

Click this button to view the [Line Shunt](#line-shunts-information) Dialog. This dialog is used to only view or modify the values of the line shunts. Line shunts are expressed in terms of the per-unit conductance and susceptance at each end of the line or transformer. If the line has shunts, the check box **Has Line Shunts** is checked.

MVA Limits

Ratings for the transmission line or transformer in MVA. Eight different limits are allowed.

Calculate Impedances

This will display a pop-up menu with the following two options:

…From Per Distance Impedances

Clicking this item will open the [Line Per Unit Impedance Calculator dialog](#line-per-unit-impedance-calculator-dialog), which can be used to convert actual impedance and current limits to per unit impedance and MVA limits, and vice versa.

…From Conductor Type and Tower Configuration

Clicking this item will open the [Transmission Line Parameter Calculator](#transmission-line-parameter-calculator) dialog, which can be used to compute per unit impedance values, based on a conductor type and a tower configuration.

Convert Line to Transformer

Clicking this button turns the currently selected transmission line into a transformer, making the transformer specific fields available.

D-FACTS Devices on the Line

Click this button to view the [D-FACTS Information](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog) dialog. This dialog is used to create or modify [D-FACTS devices](05-case-information-displays-by-object-part2.md#d-facts-devices) on the line.

---

<a id="line-shunts-information"></a>

## Line Shunts Information

*Source: [`Content/MainDocumentation_HTML/Line_Shunts_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Shunts_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line Shunts Information dialog is used to modify the parameters of transmission line shunts. The modeling of the line shunts is explained below.

Line Shunts

Line shunts are included in the model as admittance-to-ground values at either the From end or the To end of a transmission line. These values can represent many things, such as shunt-to-ground capacitors, reactors, zigzag (or grounding) transformers, or equivalenced system values. Line shunt values are entered in per unit, with a positive B corresponding to capacitors and a negative B corresponding to reactors. Mathematically, the line shunts are included in the algorithm in the same manner that line charging capacitance is included using the Pi model.

Line shunt values can be modified from the [Branch Options](#transmission-linetransformer-options) dialog or [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information).

---

<a id="line-per-unit-impedance-calculator-dialog"></a>

## Line Per Unit Impedance Calculator Dialog

*Source: [`Content/MainDocumentation_HTML/Line_Per_Unit_Impedance_Calculator_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Per_Unit_Impedance_Calculator_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line Per Unit Impedance Calculator Dialog allows to convert actual impedance and current limit values to per unit impedance and MVA limit values, and vice versa.

The dialog has the following elements:

Actual Impedance and Current Limits

This part of the dialog shows all the impedance related values in Ohms/length-unit as well as the transmission line limits specified in Amps. If any of these values is modified, the corresponding per unit or MVA value will be changed accordingly, taking into consideration the current line length, length units, and system base values.

Line Length

This value indicates the length of the line in miles or kilometers, depending on the units selected in **Length Units**. The option **When changing convert** is used to convert the values when the length value is modified. The option **PU/MVA --\>** indicates that the actual impedance and current limits will be converted to per unit impedance and MVA limits when the length value is changes. The option **\<-- Electrical** specifies that the per unit impedance and MVA limits will be converted to actual impedance and current limits when the length value is modified.

Length Units

This option indicates the length units. Choices are miles and kilometers. When this parameter is changed, the user will be prompted to confirm to convert the actual impedance and current limits, as well as the line length values, from the old units to the new units. If the answer is positive, then the actual impedance and current limits, and the line length will be the same but they will be expressed in the new units selected. If the answer is negative, the values will not change numerically but they still will be expressed in the new units selected.

System Base Values

The system base values show the power base, the voltage base, and the impedance base. These values can not be modified in this dialog.

Per Unit Impedance and MVA Limits

This part of the dialog shows all the impedance related values in per unit as well as the transmission line limits specified in MVA. If any of these values is modified, the corresponding actual or Amps value will be changed accordingly, taking into consideration the current line length, length units, and system base values.

Conductor Type

Shows the conductor type selected to compute the per unit impedances in the [Transmission Line Parameter Calculator](#transmission-line-parameter-calculator) dialog. It will be blank if there isn’t any.

Tower Configuration

Shows the tower configuration selected to compute the per unit impedances in the [Transmission Line Parameter Calculator](#transmission-line-parameter-calculator) dialog. It will be blank if there isn’t any.

Calculate PU Impedances From Conductor Type and Tower Configuration

Clicking this button will open the [Transmission Line Parameter Calculator](#transmission-line-parameter-calculator) form.

---

<a id="transmission-line-parameter-calculator"></a>

## Transmission Line Parameter Calculator

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Parameter_Calculator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Parameter_Calculator.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The transmission line parameter calculator is a tool designated to compute characteristic line parameters give the type of the conductor and the configuration of a three-phase overhead transmission line.

The parameters computed are the resistance R, reactance X, susceptance B, and conductance G. These values are computed as distributed (per unit of distance), lumped or total (for a specific line distance), and in per-unit.

**Calculations**

The following controls are part of the calculations section:

Parameters Calculation

This section is to enter the necessary data to compute the characteristic line parameters that are shown in the Results panel.

Input Data

Conductor Type:  This is the combo box that lists all the conductor types available in the Conductors table. To add, remove or edit a specific conductor and its characteristics, see Conductor Type section below.

Tower Configuration: This combo box lists all the tower configurations available in the Tower Configurations table. To add, remove or edit a specific tower configuration, please go to the Tower Configuration section below.

Line Length: This is the value of the distance of the transmission line. The units are miles when using English system, or kilometers when using the Metric (SI) system.

Line Length Units: The line length units specify the measurement system to use when entering the line length. The options are English system or Metric (SI) system. The final and intermediate results will also be shown in the system specified here.

Power Base: The system voltampere base in MVA.

Voltage Base: The line-line voltage base in KV.

Impedance Base: The impedance base in Ohms. This value is automatically computed when the power base and the voltage base are entered or modified.

Admittance Base: The admittance base in Siemens. It is also automatically computed as the inverse of the impedance base.

Final Results

When all the input data is entered, the results automatically will be displayed. The values for R, X, B and G are shown in three different sections, each section corresponding to Distributed, Lumped or Total, and Per Unit values, respectively. The Power Surge Impedance Loading is calculated only for the lumped section.

Intermediate Results

The intermediate values calculated to compute the R, X, B, and G values are displayed here. The computed geometric mean radius and geometric mean distance are shown in the Distributed values section. The characteristic impedance and propagation factor are displayed in the Lumped values section.

Note: To see the specific calculations used in this program, see the Calculations section, at the end of this document.

Ampere to MVA Limit Conversion

This section converts the limits of the transmission line from Amperes to MVAs, given the voltage base, and vice versa.

**Conductor Type**

This section is used to add, remove, rename, and edit the information related to the conductor types. This can be done in two ways: using the form for an individual conductor type, or using the table for all the conductor types available.

**Edit By Form**

Conductors are identified by a unique code word. All the available conductors are listed in the Conductor Code Word combo box. By selecting one conductor, all its properties are displayed in the form. There, the user is able to modify any of those values. After modification of any value, the user has to save the changes by clicking on the button **Save** before changing tabs, otherwise the changes will be lost.

By clicking on **New**, a message prompting for a name for a new conductor will be shown. By clicking on **Rename**, a new name for the current conductor type is required. In order to save the current conductor type with a different name is necessary to click on **Save As**. Finally, to remove the current conductor the user can do so by clicking on the **Delete** button.

**Edit By Table**

In this tab, all the conductor types are shown as records in a table, where every field is a characteristic of the conductor. In order to edit the records in this table, use the Database button described in the Database section. While editing the table, the user can not change of tab until changes are posted or discarded.

**Conductor Properties**

The available properties of the conductors are the following:

Code Word: Code name for the type of conductor. The names of bird species are typically used. Code Word has to be unique.

Area: The area of aluminum conductor in circular mils. A circular mil is the cross-sectional area of a circular conductor having a diameter of 1 mil. One mil is one thousandth of an inch (0.001").

Aluminum strands: Number of aluminum strands.

Steel layers: Number of steel strands.

Aluminum layers: Number of aluminum layers.

External diameter: Outside diameter of the conductor in inches.

GMR: Geometric Mean Radius in feet.

DC Resistance: DC resistance of the conductor at 20°C per 1 mile in Ohms.

AC Resistance 25: AC resistance of the conductor at 60 Hz and 25°C per 1 mile in Ohms.

AC Resistance 50: AC resistance of the conductor at 60 Hz and 50°C per 1 mile in Ohms.

AC Resistance 75: AC resistance of the conductor at 60 Hz and 75°C per 1 mile in Ohms.

Inductive Reactance: Inductive reactance per conductor at 1 foot spacing at 60 Hz in Ohms/mile.

Capacitive Reactance: Capacitive reactance per conductor at 1 foot spacing at 60 Hz in MegaOhms/mile.

**Tower Configuration**

This part is used to add, remove, rename, and edit the information related to the tower configurations. This can be done in two ways: using the form for an individual tower configuration, or using the table for all the tower configurations available.

Edit By Form

Tower configurations are identified by a unique name. All the available tower configurations are listed in the Tower Configuration Name combo box. By selecting one specific tower configuration, all its characteristics are displayed in the form. There, the user can modify any of those characteristics. After modification of any value, the user has to save the changes by clicking on the button **Save** before changing tabs, otherwise the changes will be lost.

By clicking on **New**, a message prompting for a name for a new tower configuration will be shown. By clicking on **Rename**, a new name for the current tower configuration is required. In order to save the current tower configuration with a different name is necessary to click on **Save As**. Finally, to remove the current tower configuration the user can do so by clicking on the **Delete** button.

Edit By Table

In this tab, all the tower configurations are shown as records in a table, where every field is a value of the tower configuration. In order to edit the records in this table, use the Database button described in the Database section. While editing the table, the user can not change of tab until changes are posted or discarded.

Tower Configuration Values

The values of the tower configuration are the following:

Name: Name for the tower configuration. Name has to be unique.

Phase spacing: x and y coordinates of phases A, B and C positions. Values are in feet for English system and meters for Metric (SI) system. When these values are modified, the phase spacing graph is automatically updated. **Draw axis** has to be checked for x and y axis to be drawn in the graph.

Conductors per bundle: This section specifies the number of conductors (either single conductor or a bundle of conductors) per phase. The maximum number of conductors per bundle allowed is 4.

Use regular spacing: When using a bundle of conductors, checking the **Use Regular Spacing of** check box will use the specified value as a regular spacing among the conductors. If the **Use Regular Spacing of** check box is not checked, then the custom conductors spacing section has to be used.

Conductors spacing: x and y coordinates of the conductors in the bundle. Values are in feet for English system and meters for Metric (SI) system. When these values are modified, the bundle spacing graph is automatically updated. **Draw axis** has to be checked for x and y axis to be drawn in the graph.

Temperature: Assumed temperature in Fahrenheit degrees for English system and Celsius degrees for Metric (SI) system.

Frequency: Frequency of the system in Hertz.

System of units: The system of units used to specify the values of the tower configuration. The options are English system or Metric (SI) system. The units specified here not necessarily have to math the units specified in the **Input Data** section.

**Database**

The conductor type and tower configurations tables are read by default from the file **conductors.mbd**, which is a MS Access® database. This database can be read from another \*.mdb file by clicking on the **Select Conductors and Configurations Database** button.

Note: The conductors.mdb file can also be viewed and edited in MS Access®.

In order to edit a record in the database tables, the user can use the toolbar designed to do that. Following there is a figure showing this toolbar:

![image\\ebx\_1058328347.gif](images/ebx_1058328347_640x120.gif)

The **First**, **Prior**, **Next**, and **Last** buttons are used to move among records. The **Insert**, **Delete** and **Edit** buttons are used to insert, delete or edit the current record, respectively. While editing a record, the user can not change of tab until modifications are posted through the **Post edit** button or canceled with the **Cancel edit** button. The **Refresh** **data** button just refreshed the data of the entire table.

**Calculations**

Distributed Parameters

Resistance

![Trans Line Param Calc Equation1](images/Trans_Line_Param_Calc_Equation1.gif)

Where:

*Rt* AC resistance at temperature *t* per phase per 1 mile in Ohms

*t *Assumed temperature in Celsius degrees

*R*25 AC resistance of the conductor at 60 Hz and 25°C per 1 mile in Ohms

*R*50 AC resistance of the conductor at 60 Hz and 50°C per 1 mile in Ohms

*R*75 AC resistance of the conductor at 60 Hz and 75°C per 1 mile in Ohms

*N* Number of conductors per phase

Inductive Reactance

![Trans Line Param Calc Equation2](images/Trans_Line_Param_Calc_Equation2.gif)

Where:

*XL* Inductive reactance in Ohms/meter

*f*    Frequency of the system in Hertz

![Trans Line Param Calc Equation3](images/Trans_Line_Param_Calc_Equation3.gif)Geometric mean distance between phases in meters

![Trans Line Param Calc Equation4](images/Trans_Line_Param_Calc_Equation4.gif)Geometric mean radius between conductors of one phase in meters

The **geometric mean distance** between phases is defined as:

![Trans Line Param Calc Equation5](images/Trans_Line_Param_Calc_Equation5.gif)

Where:

![Trans Line Param Calc Equation6](images/Trans_Line_Param_Calc_Equation6.gif) Distances between phases a-b, b-c, c-a, respectively in meters

The **geometric mean radius** between conductors of one phase is defined as:

![Trans Line Param Calc Equation7](images/Trans_Line_Param_Calc_Equation7.gif) For 1 stranded conductor

![Trans Line Param Calc Equation8](images/Trans_Line_Param_Calc_Equation8.gif)For 1 solid cylindrical conductor

![Trans Line Param Calc Equation9](images/Trans_Line_Param_Calc_Equation9.gif)For more then 1 conductor bundle

Where:

![Trans Line Param Calc Equation4](images/Trans_Line_Param_Calc_Equation4.gif) Geometric mean radius in meters

*r* External radius of conductor in meters

*GMR* Geometric mean radius given in tables for one stranded conductor

![Trans Line Param Calc Equation10](images/Trans_Line_Param_Calc_Equation10.gif)Distance between conductors *k* and *m* in meters.

Note: If *k = m*, then ![Trans Line Param Calc Equation10](images/Trans_Line_Param_Calc_Equation10.gif)*=* ![Trans Line Param Calc Equation4](images/Trans_Line_Param_Calc_Equation4.gif)for one stranded or solid cylindrical conductor.

Susceptance

![Trans Line Param Calc Equation11](images/Trans_Line_Param_Calc_Equation11.gif)

Where:

*B* Susceptance in Siemens/meter

*f*  Frequency of the system in Hertz

*e* Constant permittivity = 8.85418 ´ 10-12

![Trans Line Param Calc Equation3](images/Trans_Line_Param_Calc_Equation3.gif) Geometric mean distance between phases, defined as above

![Trans Line Param Calc Equation12](images/Trans_Line_Param_Calc_Equation12.gif)Geometric mean radius between conductors of one phase using external radius in meters

The geometric mean radius between conductors of one phase using external radius is defined as:

![Trans Line Param Calc Equation13](images/Trans_Line_Param_Calc_Equation13.gif)For 1 conductor

![Trans Line Param Calc Equation14](images/Trans_Line_Param_Calc_Equation14.gif) For more then 1 conductor bundle

Where:

![Trans Line Param Calc Equation12](images/Trans_Line_Param_Calc_Equation12.gif) Geometric mean radius in meters

*r* External radius of conductor in meters

![Trans Line Param Calc Equation10](images/Trans_Line_Param_Calc_Equation10.gif) Distance between conductors *k* and *m* in meters.

Note: If *k = m*, then ![Trans Line Param Calc Equation10](images/Trans_Line_Param_Calc_Equation10.gif) *=* *r*.

Conductance

Assumed *G = 0*

Where:

*G* Conductance in Siemens/meter

Lumped (Total) Parameters

Resistance, Inductive Reactance, Conductance and Susceptance, using the equivalent p circuit (long line)

![Trans Line Param Calc Equation15](images/Trans_Line_Param_Calc_Equation15.gif)

Where:

*Z’* Total series impedance of line in Ohms

*Y’* Total series admittance of line in Siemens

*R’* Total series resistance of line in Ohms

*X’* Total series inductive reactance of line in Ohms

*G’* Total series conductance of line in Siemens

*B’* Total series susceptance of line in Siemens

*Zc* Characteristic impedance in Ohms

*g* Propagation constant in meters-1

![Trans Line Param Calc Equation16](images/Trans_Line_Param_Calc_Equation16.gif) Line length in meters

The characteristic impedance and propagation constant are defined as:

![Trans Line Param Calc Equation17](images/Trans_Line_Param_Calc_Equation17.gif)

Where:

*z* Distributed series impedance in Ohms/meter

y Distributed series admittance in Siemens/meter

The **distributed series impedance** and **distributed series admittance** are defined as:

![Trans Line Param Calc Equation18](images/Trans_Line_Param_Calc_Equation18.gif)

Where:

*R* Distributed series resistance in Ohms/meter

*X* Distributed series inductive reactance in Ohms/meter

*G* Distributed series conductance in Siemens/meter

*B* Distributed series susceptance in Siemens/meter

Surge Impedance Loading

The surge impedance loading is defined as the power delivered by a lossless line to a load resistance equal to the surge (or characteristic) impedance *Zc*, and is given by:

![Trans Line Param Calc Equation19](images/Trans_Line_Param_Calc_Equation19.gif)

Where:

*PSIL* Total surge impedance loading in a three-phase line in VA

*VN* Line-line nominal voltage in Volts

Base Values

Impedance Base

![Trans Line Param Calc Equation20](images/Trans_Line_Param_Calc_Equation20.gif)

Where:

![Trans Line Param Calc Equation21](images/Trans_Line_Param_Calc_Equation21.gif) Impedance base in Ohms

![Trans Line Param Calc Equation22](images/Trans_Line_Param_Calc_Equation22.gif) Power base in VA

![Trans Line Param Calc Equation23](images/Trans_Line_Param_Calc_Equation23.gif)Line-line voltage base in Volts

Admittance Base

![Trans Line Param Calc Equation24](images/Trans_Line_Param_Calc_Equation24.gif)

Where:

![Trans Line Param Calc Equation25](images/Trans_Line_Param_Calc_Equation25.gif)Admittance base in Siemens

![Trans Line Param Calc Equation21](images/Trans_Line_Param_Calc_Equation21.gif)Impedance base in Ohms

Per Unit (PU) Parameters

Resistance, Inductive Reactance, Conductance, Susceptance

![Trans Line Param Calc Equation27](images/Trans_Line_Param_Calc_Equation27.gif)

Where:

*RPU* Per unit resistance

*R’* Total series resistance in Ohms

*XPU*  Per unit Inductive reactance

*X’* Total series inductive reactance in Ohms

*XPU*  Per unit conductance

*G’* Total series conductance in Siemens

*BPU*  Per unit susceptance

*B’* Total series susceptance in Siemens

*ZB* Impedance base in Ohms

*YB* Admittance base in Siemens

MVA To Ampere and Ampere To MVA Limits Conversion

MVA to Ampere Limit Conversion

![Trans Line Param Calc Equation28](images/Trans_Line_Param_Calc_Equation28.gif)

Where:

*LimAmp* Limit in Amperes

*LimMVA* Limit in MVAs

*VN* Nominal voltage in Volts

Ampere to MVA Limit Conversion

![Trans Line Param Calc Equation29](images/Trans_Line_Param_Calc_Equation29.gif)

Where:

*LimAmp* Limit in Amperes

*LimMVA* Limit in MVAs

*VN* Nominal voltage in Volts

---

<a id="transformer-control"></a>

## Transformer Control

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Transformer_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Transformer_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transformers are used to transfer power between different voltage levels or to regulate real or reactive flow through a particular transmission corridor. Most transformers come equipped with taps on the windings to adjust either the voltage transformation or the reactive flow through the transformer. Such transformers are called either load-tap-changing (LTC) transformers or tap-changing-under-load (TCUL) transformers.

Another type of transformer is known as a phase-shifting transformer (phase shifter or phase angle regulator). Phase-shifting transformers, which are less common than LTC transformers, vary the angle of the phase shift across the transformer in order to control the MW power flow through the transformer.

Options for specifying transformer control are found on the **Transformer Control** tab of the [Branch Options dialog](#transmission-linetransformer-options) when in Edit mode and the **Transformer** tab of the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) when in Run mode.

**Off-nominal Turns Ratio and Phase Shift Degrees**

**The Off-nominal Turns Ratio** field indicates the voltage transformation, while the **Phase Shift Degrees** field show the phase shift angle. If the transformer is not on automatic control, these values can be changed manually. The off-nominal tap ratio determines the additional transformation relative to the nominal transformation. This value normally ranges from 0.9 to 1.1 (1.0 corresponds to no additional transformation). For phase-shifting transformers the phase shift value normally ranges from about -40° to 40°. The phase angle field can be non-zero for LTC and fixed transformers, most notably +/- 30° if the transformer configuration is a delta-wye or wye-delta configuration. The transformer configuration is very important when performing a [fault analysis](27-fault-analysis.md#fault-analysis) study.

**Automatic Control Type** provides the type of transformer. Valid types are 1) No Automatic Control (in which the taps are assumed fixed), 2) voltage regulation (AVR), 3) Reactive Power Control, and 4) Phase Shift Control.

Simulator provides you with a great deal of flexibility in being able to specify which transformers will actually be used for automatic control in the Power Flow Solution. For a transformer to be used for voltage or flow control, three criteria must be met:

  - For an LTC transformer, the transformer's **Automatic Control Enabled** field must be checked. This field can also be modified on the [Transformer Records display](05-case-information-displays-by-object-part2.md#transformer-display). When the transformer is a phase shifter, the Automatic Control Enabled field has three options. Select *Not Enabled* to completely disable the phase shifter for automatic control. Select *Enabled for Power Flow* to allow automatic control actions during the power flow solution. Select *Enabled for OPF Only* to allow the phase shifter to be a control as part of the OPF solution but not on automatic control as part of the power flow solution.
  - The transformer's area must have automatic transformer control enabled. This is specified on the **Options Tab**of the [Area Records](05-case-information-displays-by-object-part1.md#area-display) display.
  - Transformer control must not be disabled for the entire case. This is specified on the **Power Flow Solution Tab** of the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options). Automatic control for LTC transformers and phase shifters can be disabled separately at the case level.

The type of transformer can be changed on the Transformer Control Info dialog opened by clicking the **Change Automatic Control Options...** button. This dialog contains different information depending on the type of transformer control that is selected. The **Common Options** tab of this dialog allows changing the control type while in Edit mode and displays the type of control while in Run mode. The type CANNOT be modified while in Run mode. The [Time Step Options](26-time-step-simulation-part2.md#transformer-control-time-step-options) tab contains control options specific for the Time Step Simulation tool.

The type-specific information contained on the **Common Options** tab is described below:

No Automatic Control

On this control setting the transformer will operate at the given off-nominal turns ratio and phase shift, and will remain fixed at those values during the entire solution process unless manually changed by the user.

AVR (Automatic Voltage Regulation)

When on automatic voltage control, the transformer taps automatically change to keep the voltage at the regulated bus (usually one of the terminal buses of the transformer) within a voltage range between the minimum voltage and maximum voltage values (given in per unit). The Transformer Control Info dialog is configured as the [Transformer AVR Dialog](#transformer-avr-dialog) when this control type is selected. Note that automatic control is possible only if a regulated bus has been specified.

The tap position for an LTC transformer is indicated on the oneline by the number of tap step positions from the nominal position (i.e., the position when the off-nominal tap ratio is equal to 1.0). When the off-nominal ratio is greater than 1.0, the transformer's tap is said to be in the "raise" position, and an 'R' appears after the number. Likewise, when the off-nominal ratio is less than 1.0, the transformer's tap is said to be in the "lower" position, and an 'L' appears after the number. For example, with a step size of 0.00625 and an off-nominal ratio of 1.05, the tap would be in position 8R. The tap position can be changed manually only when the transformer has been set off automatic voltage control.

Simulator will also detect instances when controlling transformers are in parallel, and will employ checks during the solution routine to prevent the controllers from fighting each other and potentially going to opposite tap solutions, which could result in unwanted loop flow through the transformer objects. This option is enabled by default, but can be turned off in the [Power Flow Solution Advanced Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options).

Transformer Reactive Power Control

When on automatic reactive power control, the transformer taps automatically change to keep the reactive power flow through the transformer (measured at the *from bus*) within a user-specified range. When this control type is selected, the Transformer Control Info dialog is configured as the [Transformer Mvar Control Dialog](06-object-properties-edit-mode-part3.md#transformer-mvar-control-dialog).

Phase Shift Control

When a transformer is on phase shift control, the transformer phase shift angle automatically changes to keep the MW flow through the transformer (measured at the *from bus*) between the minimum and maximum flow values (given in MW, with flow into the transformer assumed positive). The limits on the phase shifting angles are specified in the minimum and maximum phase fields (in degrees). When this control type is selected, the Transformer Control Info dialog is configured as the [Transformer Phase Shifting Dialog](06-object-properties-edit-mode-part3.md#transformer-phase-shifting-information). The phase shift angle changes in discrete steps, with the step size specified in the Step Size field (in degrees). The **MW Per Phase AngleStep Size** provides an estimate of the change in the controlled MW flow value if the phase angle is increased by the step size value.

Area and Case Control Options

This set of options is available when in Run mode and provides a summary of the area and case level options for allowing automatic transformer control. These settings are provided for informational purposes only and cannot be set here.

**Area Transformer Control Enabled** has to be checked for any transformer in that area to be controlled (phase shifter control must be enabled for power flow); **Case LTC Transformer Control Enabled** has to be checked for any LTC type (Voltage Regulation (AVR) or Reactive Power Control) transformer in the entire case to be controlled, and **Case Phase Shifter Control Enabled** has to be checked for any phase shifter in the entire case to be controlled.

Specify Transformer Bases and Impedances

Shows the Transformer Bases and Impedances Dialog. This dialog allows the user to specify the transformer parameters in per unit on the transformer base (taken as its rating). Click **OK** to convert all the transformer parameters values to the system base specified in the [Power Flow Solution General Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-general).

---

<a id="transformer-avr-dialog"></a>

## Transformer AVR Dialog

*Source: [`Content/MainDocumentation_HTML/Transformer_AVR_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_AVR_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transformer AVR Dialog is used to view the control parameters associated with load-tap-changing (LTC) transformers when they are used to control bus voltage magnitudes. To view this dialog, click the ****Change Automatic Control Options** button found with the [Transformer Control options](#transformer-control), provided that the *Voltage Regulation (AVR)* option is chosen from the **Automatic Control Type** group.

The **Common Options** tab of this dialog has the following fields:

Automatic Control Type

This section is only visible on the dialog in edit mode. The control type of the transformer can be changed between no control, voltage regulation, reactive power control, or phase shifter control. Changing the control type will update the dialog to reflect the type of control that is selected.

Regulated Bus Number

The number of the bus whose voltage is regulated by the control.

Present Regulated Bus Voltage

The present voltage of the regulated bus.

Voltage Error

If the regulated bus' voltage falls outside the regulating range of the transformer (as defined by the **Regulation Minimum Voltage** and **Regulation Maximum Voltage** fields), the **Voltage Error** field indicates by how much the voltage deviates from the control range.

Regulation Minimum Voltage

The minimum acceptable voltage at the regulated bus.

Regulation Maximum Voltage

The maximum acceptable voltage at the regulated bus.

Regulation Target Type

As long as the regulated voltage is inside the regulation minimum and maximum, the transformer will not change its tap ratio. When the regulated voltage moves outside of this regulation range, Simulator will calculate a new tap ratio in an attempt to bring the regulated voltage back inside of its range. The **Regulation Target Type** determines what value is used as a target when calculating this change in tap ratio. **Middle** is the default and means that the target is the average of the regulation minimum and maximum regardless of whether the voltage is high or low. **Max/Min** means that the regulation maximum is used as the target when the regulated voltage is above the maximum, and regulation minimum is used as the target value when the regulated voltage is below the minimum.

Present Tap Ratio

The tap ratio of the transformer for the current system state.

Minimum Tap Ratio, Maximum Tap Ratio

Minimum and maximum allowable off-nominal tap ratios for the LTC transformer. Typical values are 0.9 and 1.1.

Tap Step Size

Transformer off-nominal turns ratio increment. The off-nominal turns ratio is either incremented or decremented from 1.0 in integer multiples of this value. Default value is 0.00625.

Voltage to Tap Sensitivity

Shows the sensitivity of the voltage magnitude at the regulated bus to a change in the transformer's tap ratio. You can use this field to assess whether or not the transformer can effectively control the regulated bus voltage. In an ideal case, such as when the LTC transformer is being used to control the voltage at a radial load bus, the sensitivity is close to 1.0 (or -1.0 depending upon whether the tapped side of the transformer is on the load side or opposite side of the transformer). However, sometimes the transformer is very ineffective in controlling the voltage. This is indicated by the absolute value of the sensitivity approaching 0. A common example is a generator step-up transformer trying to control its high-side voltage when the generator is off-line. Simulator automatically disables transformer control if the transformer sensitivity is below the value specified on **Power Flow Solution Tab** of the [Simulator Options dialog](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options).

Line Drop/Reactive Current Compensation

Typical specification of the bus at which the voltage should be controlled by a transformer is an actual bus in the power system model. However, some control schemes require that the voltage at some fictitious bus a specified impedance away from the transformer be controlled instead. This can be accomplished using the line drop and reactive current compensation control method.

This method requires that the regulated bus for a transformer be specified as one of the transformer's terminal buses. This provides a reference point for specifying the location of the fictitious bus that is the actual controlled point. An impedance must also be specified that will determine the location of the fictitious bus in reference to the selected regulated bus.

Check the **Use Line Drop/Reactive Current Compensation** checkbox to use this control method. Specify the impedance for the location of the fictitious controlled bus using the **Line Drop/Reactive Current Compensation Resistance (R)** and **Line Drop/Reactive Current Compensation Reactance (X)** fields. The impedance should be specified in per-unit.

Impedance Correction Table

This field specifies the number of the transformer's corresponding transformer impedance correction table. Transformer impedance correction tables are used to specify how the impedance of the transformer should change with the off-nominal turns ratio. If this number is 0, then no impedance correction table is associated with the transformer, and the impedance of the transformer will thus remain fixed as the tap ratio changes. To assign an existing impedance correction table to the transformer, enter the existing table's number. To view the existing impedance correction tables, click the **Insert/View Impedance Correction Table** button, which brings up the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). To define a brand new impedance correction table for the transformer, enter an unused table number and then click **Insert/View Impedance Correction Table** to prescribe the correction table. Note that the association between a transformer and an impedance correction table is not finalized until you select either **OK** or **Save** on the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) or [Branch Options dialog](#transmission-linetransformer-options).

View Transformer Correction Table or Insert Transformer Correction Table

Click on this button either to view or to insert transformer correction tables. Clicking on this button displays the [Transformer Impedance Correction Dialog](07-object-properties-run-mode-and-general-part1.md#transformer-impedance-correction-tables). Note that a table must contain at least two points in order to be defined.

The [Time Step Options](26-time-step-simulation-part2.md#transformer-control-time-step-options) tab contains control options specific for the Time Step Simulation tool.

---

<a id="series-capacitor"></a>

## Series Capacitor

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Series_Capacitor.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Transformer_Options_Series_Capacitor.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Series Capacitor tab of the [Branch Options](#transmission-linetransformer-options) dialog displays information related to a series capacitor, including its status.

Status

The capacitor itself has two status positions, **Bypassed** and **In Service**. When the series capacitor is in service, the branch is modeled as a reactive branch, using the line parameters from the Parameters page. If the capacitor is bypassed, a low impedance branch is introduced to bypass the capacitor. Note that this is not the same as the branch status of **Open** or **Closed**. The branch status is the indicator of whether or not the entire circuit is operating (closed), regardless of **Bypassed** or **In Service** status on the capacitor itself.

Is Series Capacitor

If this box is checked, the branch can be treated as a series capacitor, with the series Status of Bypassed or In-Service available.

---

<a id="multi-section-line-information"></a>

## Multi-Section Line Information

*Source: [`Content/MainDocumentation_HTML/multi_section_line_information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/multi_section_line_information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Multi-section line records are used to group a number of series-connected transmission lines together so that their status is controlled as a single entity. They are usually used to model very long transmission lines that require multiple individual transmission line records if they are to be modeled accurately. In terms of line status, Simulator then treats each multi-section line as a single device. In other words, changing the status of one line in the record changes the status of the other lines in the record, as well.

Multi-section line records are **not** directly represented on the oneline diagrams. Rather, to view this dialog, right-click the record of interest on the [Multi-Section Line Records](05-case-information-displays-by-object-part2.md#multi-section-lines-display) display and select **Show Dialog** from the resulting local menu. To define a new multi-section line, switch to Edit Mode and, from the Multi-Section Line Records display, right-click and select **Insert** from the resulting local menu.

**Note:** If any of the transmission lines comprising a multi-section line record are deleted, the entire multi-section line record is deleted as well.

The Multi-Section Lines Dialog contains the following fields:

From Bus Number and Name

Number and name of the from bus for the record. If you are defining a new multi-section line, this must be the first data item you specify.

To Bus Number and Name

Number and name of the "to" bus for the record. You cannot specify this value directly. Instead, use the table at the bottom of the dialog to define the intermediate buses and *to* terminal.

Circuit

Two character identifier used to distinguish between multiple records joining the same from/to buses. The first character of the circuit identifier must be an "&."

You can use the spin button immediately to the right of the circuit field to view other multi-section line records. However if you have changed the record, **you must** select **Save** before moving to another record. Otherwise, your changes will be lost.

From End Metered

If checked, the *from end* of the record is the metered end; otherwise the *to end* is metered.

Multi-Section Line Name

The name for the multi-section line.

Table

The table lists the dummy (or intermediate) buses and the *to bus* that comprise the record. The first column should contain the first dummy bus number and the circuit ID of the transmission line joining the *from bus* with the first dummy bus. The next column should contain the second dummy bus number and the circuit id of the transmission line joining this bus to the first dummy bus. Continue until the last column contains the *to* bus and the circuit ID of the transmission line joining the last dummy bus with the "to" bus.

Each transmission line comprising the multi-section line must already exist. If only one transmission line joins any two buses, you may omit the circuit identifier.

OK

Saves any modifications and closes the dialog.

Save

Saves any modifications but does not close the dialog.

Cancel

Closes the dialog without saving modifications to the current record.

Delete

Deletes the current multi-section line record.

**Note:** If any of the transmission lines comprising a multi-section line record are deleted, the entire multi-section line record is deleted as well. One exception is if a section or sections of a multi-section line are removed by [merging](19-edit-mode-tools.md#merging-buses) the section terminal buses together into a single bus. If special conditions are met, the multi-section line record will be maintained.

---

<a id="line-field-information"></a>

## Line Field Information

*Source: [`Content/MainDocumentation_HTML/Line_Field_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Field_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Line field display objects are used to show different values associated with transmission lines and transformers on onelines.

This dialog can be opened by right-clicking on a line display field and choosing to open the **Line Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a line display field.

This dialog is used to view and modify the parameters associated with these fields.

Find…

If you do not know the exact line identifiers you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Near Bus Number

Bus associated with the near end of the object. All fields specifically listed in the **Type of Field**, i.e. NOT the fields in **Select a Field**, display values calculated at the *near bus* end. When inserting fields graphically, this field is automatically set to the closest bus on the oneline.

Far Bus Number

Bus associated with the *far end* of the object.

Circuit

Two-character identifier used to distinguish between multiple lines or transformers joining the same two buses. Default is ‘1’.

Total Digits in Fields

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Delta Per Mouse Click

Only used with the MVA Limit field type. Specifying a nonzero value for this field equips the MVA Limit field with an integrated spin button that can be clicked to increment or decrement the MVA Limit by the amount of the Delta Per Mouse Click value.

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

MW Flow 

MW flow into the line or transformer at the near bus.

Mvar Flow 

Mvar flow into the line or transformer at the near bus.

MVA Flow 

Magnitude of MVA flow into the line or transformer at the near bus.

Amp Flow 

Magnitude of amps into the line at the near bus.

MW Losses 

Real power losses on the line or transformer in MW.

Mvar Losses 

Reactive power losses on the line or transformer in Mvar.

MVA Limit 

MVA limit for the line or transformer. This limit is determined based on the line's Limit Set and the option with that Limit Set that specifies which rating set to use for the Normal Rating Set. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Select a Field 

Choose from any of the available line fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and close the dialog or **Cancel** to close the dialog without saving your changes.

---

<a id="series-capacitor-field-options"></a>

## Series Capacitor Field Options

*Source: [`Content/MainDocumentation_HTML/Series_Capacitor_Field_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Series_Capacitor_Field_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Series capacitor field display objects are used to show field values specific to series capacitors on onelines. Use [Line Fields](12-building-onelines-branches-and-devices.md#transmission-line-fields-on-onelines) to show fields generic to transformers, series capacitors and transmission lines, such as the flow of power through the device.

This dialog can be opened by right-clicking on a series capacitor display field and choosing to open the **Line Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a series capacitor display field.

The series capacitor field options dialog is used to view and modify the parameters associated with series capacitor specific fields.

Near Bus Number

Bus associated with the *near end* of the series capacitor.

Far Bus Number

Bus associated with the *far end* of the series capacitor.

Circuit

Two-character identifier used to distinguish between branches joining the same two buses. Default is '1'.

Anchored

When checked, the text field will move with the series capacitor if the series capacitor is moved on the oneline diagram.

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Rotation Angle in Degrees

The angle at which the text will be placed.

Field Value

The value of the currently selected field.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of series capacitor field to show. The following choices are available:

Status 

Status of the series capacitor.

Series Capacitance 

Per unit impedance of series capacitor.

Select **OK** to save changes and close the dialog or **Cancel** to close dialog without saving your changes.
