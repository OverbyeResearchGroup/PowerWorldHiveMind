---
title: "Object Properties — Edit Mode (Part 1 of 3)"
part: "Viewing Case Data"
chapter_file: "06-object-properties-edit-mode-part1.md"
topics: 21
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Object Properties — Edit Mode (Part 1 of 3)

Edit-mode property dialogs for every Simulator object type.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (21)**

- [Bus Options](#bus-options)
- [Bus Field Information](#bus-field-information)
- [Shortest Path Between Buses](#shortest-path-between-buses)
- [Bus Voltage Regulating Devices](#bus-voltage-regulating-devices)
- [Substation Information](#substation-information)
- [Substation Field Options](#substation-field-options)
- [Generator Information](#generator-information)
- [Generator Field Information](#generator-field-information)
- [Display](#display)
- [Power and Voltage Control](#power-and-voltage-control)
- [Costs](#costs)
- [Fault Parameters](#fault-parameters)
- [Owners, Area, Zone, Sub](#owners-area-zone-sub)
- [Generator Cost Description](#generator-cost-description)
- [Generator Participation Factors](#generator-participation-factors)
- [Generator Reactive Power Capability Curve](#generator-reactive-power-capability-curve)
- [Load Options](#load-options)
- [Load Information](#load-information)
- [OPF Load Dispatch](#opf-load-dispatch)
- [Load Field Information](#load-field-information)
- [Load Modeling](#load-modeling)

---

<a id="bus-options"></a>

## Bus Options

*Source: [`Content/MainDocumentation_HTML/Bus_Options_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Options_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view/modify information about each bus in the system during Edit Mode. It is very similar in content to its [Run Mode](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) counterpart.

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus. You can use the spin button immediately to the right of the number to move to the next bus (click the up arrow) or the previous bus (click the down arrow).

If adding a new bus to the one-line display, this dialog will open after selecting the location of the bus display object. This dialog can be used to add a bus to the one-line for buses that already exist in the power flow case or new buses that should be created. If entering the bus number of a bus that does not already exist in the case, an informational message will appear above the Bus Number field indicating that using this bus number will insert a new bus into the power system data model and not just to the one-line display.

Find By Number

To find a bus by its number, enter the number into the **Bus Number** field and then click this button.

Bus Name

Unique alphabetic identifier for the bus.

Find By Name

To find a bus by its name, enter the bus name into the Bus Name field (case insensitive) and then click this button.

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Nominal Voltage

Nominal voltage of the bus in kV.

Labels

Clicking on this button will open the [Label Manager Dialog](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) listing all of the labels assigned for the selected bus.

Area Number

Number of the bus’ area. Each bus must be associated with an area record. If a bus is specified as belonging to an area that does not already exist in the model, the new area is created.

Area Name

Alphabetic identifier for the bus’ area. If the area already exists, you do not need to enter this value.

Zone Number

Number of the bus’ zone, between 1 and 2,147,483,647 (equals 2^31 minus 1). Each bus must be associated with a zone record. If a bus is specified as belonging to a zone that does not already exist in the model, the new zone is created. Zones provide a useful mechanism for breaking up a large system. Buses can be assigned to zones independent of their area assignments. Thus, a single area could contain multiple zones, or a single zone could span multiple areas. You can use the [Zone Dialog](06-object-properties-edit-mode-part3.md#zone-information) to list the buses in a particular zone and easily move a group of buses from one zone to another.

Zone Name

Alphabetic identifier for the bus’ zone. If the zone already exists, you do not need to enter this value.

Owner Number

The number of the bus’ owner.

Owner Name

The name of the bus’ owner.

Substation Number

The number of the substation the bus is contained in. This is typically blank in most power flow data, unless specifically added to a PowerWorld binary save file.

Substation Name

The name of the substation the bus is contained in. This is typically blank in most power flow data, unless specifically added to a PowerWorld binary save file.

OK, Save, and Cancel

**OK** saves your changes and closes the dialog. **Save** saves your changes but does not close the dialog; this allows you to use, for example, the **Find By Number** command to edit additional buses. **Cancel** closes the dialog without saving any changes.

Bus Information

Voltage (pu), Angle (degrees)

Current per-unit voltage magnitude and angle for the bus. If you are inserting a new bus into an existing system, **you should not change the initial per unit voltage values**. Rather, when you first switch to Run Mode, Simulator will estimate the voltage magnitude and angle at the new buses in such a way as to reduce the initial mismatches. **This automatic estimation is only available if you have not modified the voltage in any way.** Select **Bus Voltage Regulator Devices** to view the individual devices regulating the voltage for the bus. Selecting this button displays the [Bus Voltage Regulating Devices Dialog.](#bus-voltage-regulating-devices)

System Slack Bus

Check only if the bus should be modeled as a system slack bus. Each case requires at least one slack bus. Simulator can also dynamically determine slack buses as described in the [Advanced Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options).

Display

Orientation

Set the orientation of the bus. The current choices are right, left, up or down. For the current bus object shapes of Rectangle and Ellipse, right and left are analogous to horizontal, up and down are analogous to vertical. Additional shapes for buses may be available in the future for which right, left, up and down may have more specific impact on the appearance of the bus object.

Shape

Sets the shape of the bus object.

Width

Specifies the horizontal axis of an elliptical bus or horizontal side length of a rectangular bus.

Size

Specifies the vertical axis of an elliptical bus or the vertical side length of a rectangular bus.

Scale Width with Size

When this option is checked, changing the size will cause the width to automatically adjust to keep the same ratio of width to size. To adjust the width independent of the size, uncheck this option or adjust the width separately after adjusting the size.

Link to New Bus

If you have right clicked on a bus and opened the bus information dialog, you could change the bus number in the **Bus Number** field and press this button to force the bus object on the diagram to link to the new bus number and information in the load flow data.

Attached Devices

Load Summary Information

Displays the net MW and Mvar load at the bus. You cannot change either of these fields from this display. Select the Add or Edit Bus Load Records to view the individual load records for the bus via the [Load Dialog](#load-options).

Shunt Admittance

The real (G) and reactive (B) components of shunt compensation at the bus, expressed in MW and MVR, respectively.

Geography

The Geography page of the dialog provides information on the geographic location of the bus on the currently active oneline diagram. Also it provides a conversion tool between [Lat/Lon and UTM Coordinates](07-object-properties-run-mode-and-general-part2.md#latitudelongitude-and-utm-coordinates-conversion).

Fault Parameters

This tab is only visible when viewing the bus information for a bus with attached load. The parameters on this tab are used when running a fault analysis study. The values represent the total load at the bus for the negative and zero sequence as equivalent admittances. By default, these values are zero. For load buses, these values can be changed by the user, or they can be specified by loading short circuit data from within the [Fault Analysis Dialog](27-fault-analysis.md#fault-analysis-dialog).

Custom

The Custom page of the dialog contains two sections: custom fields and memo. 

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the bus. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the bus. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

---

<a id="bus-field-information"></a>

## Bus Field Information

*Source: [`Content/MainDocumentation_HTML/Bus_Field_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Field_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Bus field display objects are used primarily to indicate various quantities associated with bus devices on onelines. Some bus field types, which are distinguished by an integrated spin button, may be used to change bus device properties.

This dialog can be opened by right-clicking on a bus display field and choosing to open the **Bus Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a bus display field.

The Bus Fields Options dialog can be used to modify the properties of individual bus fields on the oneline. The dialog displays the following fields:

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Bus Number

Number of the bus associated with the field. Use the drop-down box to view a list of all buses in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Bus Name

Name of the bus associated with the field. Use the drop-down box to view a list of all buses in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Delta Per Mouse Click

This option is currently not used for bus fields.

Maintain Constant Load Power Factor

This option is currently not used for bus fields.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without the units will be displayed.

Anchored

If this checkbox is checked, the bus field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated bus, which means that it will move with the bus.

Rotation Angle in Degrees

The angle at which the text will appear on the diagram.

Type of Field

Used to determine the type of bus field to show. The following choices are available:

Bus Name 

Name of the bus.

Bus Number 

Number of the bus.

Bus Voltage 

Per unit voltage magnitude of the bus.

Bus Angle 

Voltage angle of the bus in degrees.

MW Marginal Cost 

Bus MW marginal cost in $/MW·hr; available only with OPF

Mvar Marginal Cost 

Bus Mvar marginal cost in $/Mvar·hr; available only with OPF

MW Loss Sensitivity 

Increase in MW losses due to injecting real power at this bus and absorbing this at the system slack. The portion of the system in which the loss increase is calculated is based on a loss function type.

Select a Field 

Choose from any of the available bus fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="shortest-path-between-buses"></a>

## Shortest Path Between Buses

*Source: [`Content/MainDocumentation_HTML/Shortest_Path_Between_Elements.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Shortest_Path_Between_Elements.htm)*

To access the Determine Shortest Path Between elements dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \> Determine Shortest Path Between...** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group. The Determine Shortest Path Between dialog provides a way to find the shortest electrical pathway between two parts of the power system.

After clicking the **Calculate** button, the shortest path of AC branches will be determined with the first bus being inside the Start Element and the last bus being inside the End Element. Options described below allow the user to choose the Start Element, End Element, Distance Measure for each branch, and branches that are allowed to be traversed. The results will be displayed in a case information display at the bottom of the dialog showing the sequence of buses that are traversed between the start and end elements.

The options on the dialog are described below.

Start Element Type and Element

Choose an element type to be either a Bus, Substation, Area, Zone, Super Area or Injection Group. Then use the object chooser to choose the particular object to be the starting element. For more help on the object choose see the [Find Dialog Basics](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

End Element Type and Element

Choose an element type to be either a Bus, Substation, Area, Zone, Super Area or Injection Group. Then use the object chooser to choose the particular object to be the ending element. For more help on the object choose see the [Find Dialog Basics](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Distance Measure

Choose the distance measure that will be used to determine distances between nodes. Each branch will be treated as having a length based on the choice below. Note: negative values are not allowed, therefore negative values will be treated as extremely small lengths instead.

**X** - Per unit series reactance.

**|Z|** - Magnitude of the series impedance (based on the per unit reactance and resistance).

**Length** - Length field for each branch.

**Number of Nodes** - Length of 1.0 is used for all branches.

**Other** - When choosing Other, click the **Find..** button to choose any numeric field of a branch.

Lines to Process

Regardless of the Distance Measure above, you can choose which branches are allowed to be traversed when finding the shortest path.

**All** - All branches are allowed to be traversed.

**Only Closed** - Only branches that are presently closed can be traversed.

**Filter** - Only branches that meet the advanced filter specified can be traversed. Click **Define...** to choose or create and advanced filter.

**Selected** - Only branches whose Selected field is set to *YES* can be traversed.

Calculate and Visualize on Spatial View Oneline

Clicking this button will calculate the distance measurement and visualize the buses in the Path Buses table using a [Spatial View Oneline](08-view-case-data-tools.md#spatial-view-oneline).

---

<a id="bus-voltage-regulating-devices"></a>

## Bus Voltage Regulating Devices

*Source: [`Content/MainDocumentation_HTML/Bus_Voltage_Regulating_Devices_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Voltage_Regulating_Devices_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus Voltage Regulating Devices Dialog displays summary information about the devices regulating by the selected bus. The regulating devices can be Generators, Switched Shunts and Transformers.

Also the Bus Voltage Regulating Devices Dialog displays a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) for the regulating devices. In addition to the information available about the [Generators](05-case-information-displays-by-object-part1.md#generator-display), [Switched Shunts](05-case-information-displays-by-object-part3.md#switched-shunt-display) and [Transformers](05-case-information-displays-by-object-part2.md#transformer-display) Display, the Bus Voltage Regulating Devices Dialogs Display also shows and allows to modify the Regulating Max and Min per unit voltage, the Device Voltage Target, the Transformer (if any) Regulation Target Type and Device Voltage Target High.

---

<a id="substation-information"></a>

## Substation Information

*Source: [`Content/MainDocumentation_HTML/Substation_Information_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Information_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Substation Dialog is used in the [Edit Mode](01-getting-started.md#edit-mode-introduction) to view information about a substation and to move one or more buses from one substation to another. (See [Substation Information (Run Mode)](07-object-properties-run-mode-and-general-part1.md#substation-information) for help on the corresponding [Run Mode](01-getting-started.md#run-mode-introduction) version.) To view this dialog, first select **Aggregation \> Substations** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to view the [Substations Records](05-case-information-displays-by-object-part1.md#substation-records-display) Display. Then, right-click on the desired substation record and select **Show Dialog** to view this dialog.

The dialog has the following fields:

Substation Number

An integer identifier for the substation. You can use the spin button immediately to the right of this field to move to either the next substation (click the up arrow) or the previous substation (click the down arrow).

Substation Name and ID

Two alphanumeric identifiers for the substation. You can use these fields to change the substation’s name or ID, provided you click either Save or OK.

Find By Number

To find a substation by its number, enter the number into the **Substation Number** field, then click this button.

Find By Name

To find a substation by its name, enter the name into the **Substation Name** field, then click this button.

Find By Sub ID

To find a substation by its substation ID, enter the ID into the **Substation ID** field, then click this button.

Find…

If the exact substation number, name and ID are not known, you can use the [Find Dialog](04-model-explorer-and-case-information-part3.md#find-dialog-basics) to search for and select a substation from a list of substations.

Labels

Clicking this button will open the [Subscribed Aliases dialog](07-object-properties-run-mode-and-general-part2.md#labels) displaying the list of defined labels for the substation. New labels can also be added for the substation from the dialog as well.

Buses

This table lists all of the buses in the substation. Number, name, voltage, area number and name, and zone number and name are shown for each bus. This table can be used to move buses to a different substation. Select the bus or buses you would like to move with the mouse. Then, enter the Destination Substation Number, which is the substation to which you want to move the selected buses. You may enter a substation number that does not already exist, too, so that the buses will be moved to a brand new substation. In this case, be sure to provide the new substation a name and ID, as well. Finally, click the Move Selected Bus(s) to Destination Substation button to implement the move.

Display Options

The Display Options tab of the Substation Information dialog is only visible if an open diagram contains an object representing the substation. This tab allows you to choose the general appearance of the substation object. Use the Width and Height fields to set the **width** and **height** of the substation object. The **Shape** field allows you to choose what shape the substation object will take.

By clicking on **Link to New Object**, the Choose Object selector will appear, allowing the user to select another substation in the load flow data to be linked to this particular graphical object.

The **Substation Layout Oneline, URL or Command** field allows you to specify the same of the Simulator oneline diagram (pwd) file that should be automatically opened if you click on the substation object on the diagram in run mode. If no oneline is specified, Simulator will search for a default name of the format AreaName\_SubstationName. If a diagram cannot be found, then Simulator will not attempt to open any oneline diagrams when the substation is clicked. Optionally, a HTTP URL can be entered in the form *http://example.com*. Also, a line command can be entered, such as *Excel.exe* *c:\\file.xls*.

Substation Generators, Loads, and Switched Shunts Tables

These tables list all of the generators, loads, and switched shunts in the substation. Number, name, ID, status, and additional fields for each type of device are shown.

Custom

Enter any text notes you wish in the Memo page. When the case is saved as a Simulator PWB file, the memo text will also be saved. Custom fields can also be entered for storage with the selected substation.

Geography

Displays geographic information about the location of the substation, in Latitude and Longitude. When showing the dialog by right-clicking on a [substation oneline display object](11-building-onelines-network-objects.md#substation-display-objects) from a oneline diagram, then a button will also appear that states **Copy Longitude/Latitude from Oneline Location**. This button will then determine the longitude/latitude of the center of the substation object on the oneline diagram and copy these values into the Substation Data Record. Also it provides a conversion tool between [Lat/Lon and UTM Coordinates](07-object-properties-run-mode-and-general-part2.md#latitudelongitude-and-utm-coordinates-conversion).

OK, Save, Cancel

OK saves any changes to the substation name or ID, and closes the dialog.

Save saves any changes to the substation name or ID, but does not close the dialog.

Cancel closes the dialog ignoring any changes.

---

<a id="substation-field-options"></a>

## Substation Field Options

*Source: [`Content/MainDocumentation_HTML/Substation_Field_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Field_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Substation field display objects are used to show different values associated with substations on onelines.

This dialog can be opened by right-clicking on a substation display field and choosing to open the **Substation Field Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a substation display field.

This dialog is used to view and modify the parameters associated with these fields.

Substation Number

Select the number of the substation for which you are inserting or viewing information of a substation field.

Find…

If you do not know the exact substation you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Substation Name

The name of the currently selected substation.

Substation ID

The substation ID number.

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Rotation Angle in Degrees

The angle at which the text will appear on the diagram.

Field Value

Shows the current output for the super area field. Whenever you change the **Type of Field** selection, this field is updated.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Anchored

If this checkbox is checked, the substation field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated substations, which means that it will move with the substation.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of super area field to show. The following choices are available:

Substation Name, Substation Number 

Name or number of the selected substation.

Substation ID

ID string for the selected substation.

Max Nominal Voltage 

Displays the nominal voltage of the highest nominal voltage bus in the substation.

Substation Load MW, Substation Load Mvar

Total Load MW or MVAR in the substation.

Substation Gen MW, Substation Gen MVAR 

Total Generator MW or MVAR in the substation.

Select a Field

Choose from any of the available substation fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="generator-information"></a>

## Generator Information

*Source: [`Content/MainDocumentation_HTML/Generator_Options_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Options_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters associated with each generator in the system. It can also be used to insert new generators and sometimes to delete existing generators.

The Edit Mode version of the Generator Information Dialog is almost identical to the [Run Mode](07-object-properties-run-mode-and-general-part1.md#generator-information) version.

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus to which the generator is attached. The dropdown list enumerates all generator buses in the case that meet the criteria established by [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). You may select a bus number directly from the dropdown list, or you may use the spin buttons to cycle through the list of generator buses.

Bus Name

Unique alphabetic identifier for the bus to which the generator is attached, consisting of up to eight characters. Use this dropdown box to view a list of all generator bus names in the case with valid [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

Two-character alphanumeric ID used to distinguish multiple generators at a bus; ‘1’ by default.

Find By Number

To find a generator by its number and ID, enter the number into the **Bus Number** field and the ID into the **ID** field. Then click this button.

Find By Name

To find a bus by its name and ID, enter the bus name into the **Bus Name** field (case insensitive) and the ID into the **ID** field. Then click this button.

Find…

If you do not know the exact generator bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Status of the generator, either Closed (connected to terminal bus) or Open (not connected). You can use this field to change the status of the generator.

Area Name

Alphabetic identifier for the terminal bus’ area.

Labels

Clicking on this button will open the [Subscribed Aliases dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the labels or aliases assigned for the selected generator.

Fuel Type

Type of fuel used by the generator this model represents. In most cases, this field is unnecessary for normal load flow analysis, and hence the default value is Unknown. However, this value can be useful during the [Security Constrained OPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview) analysis.

Unit Type

The type of unit the generator represents, such as combined cycle, steam, hydro, etc.

There are six additional areas of information on this dialog for specific aspects of generation:

[Display Information](#display)

[Power and Voltage Control](#power-and-voltage-control)

[Costs](#costs)

[Fault Parameters](#fault-parameters)

[Owner, Area, Zone, Sub](#owners-area-zone-sub)

[Custom](01-getting-started.md#memo-display)

[Stability](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs)

---

<a id="generator-field-information"></a>

## Generator Field Information

*Source: [`Content/MainDocumentation_HTML/Generator_Field_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Field_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generator field display objects are used primarily to indicate various quantities associated with generation devices. Some generator field types, which are distinguished by an integrated spin button, may be used to change generation device properties.

This dialog can be opened by right-clicking on a generator display field and choosing to open the **Generator Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a generator display field.

The Generator Field Options dialog can be used to modify the properties of individual generator fields on the oneline. The dialog displays the following fields:

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Bus Number

Number of the bus to which the generator associated with the field is connected. Use the dropdown box to view a list of all buses with generators in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Bus Name

Name of the bus to which the generator associated with the field is connected. Use the dropdown box to view a list of all buses with generators in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

ID of the generator associated with the field. Generator IDs are two-character alphanumeric fields.

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Delta Per Mouse Click

Generator fields can be used not only to show various fields associated with generation devices, but they can also be used to change some values. This is accomplished using spin buttons shown to the right of the generator field. When the up spin button is clicked, the generator field value is increased by the amount specified in the *delta per mouse click* field. When the down spin button is clicked, the generator field value is decreased by the same amount.

This field is only used for fields of the following types: Gen MW Output, Gen Mvar Output, and Gen Setpoint Voltage. Specifying a nonzero value in this field causes the integrated spin button to appear as part of the generator field on the oneline.

Rotation Angle in Degrees

The rotation angle at which the text field should be displayed.

Anchored

If this checkbox is checked, the generator field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated generator, which means that it will move with the generator.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of generator field to show. The following choices are available:

Gen MW Output 

MW generation. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Gen Mvar Output 

Mvar generation. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Gen AGC Status 

AGC status of generator. While in run mode left clicking on this field will toggle the AGC status of the generator.

Gen AVR Status 

AVR status of generator. While in run mode left clicking on this field will toggle the AVR status of the generator.

Gen Setpoint Voltage 

Desired voltage to which the generator is regulating. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Select a Field 

Choose from any of the available generator fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="display"></a>

## Display

*Source: [`Content/MainDocumentation_HTML/Generator_Options_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Options_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This information is located on the Display Information tab of the [Generator Information Dialog](#generator-information).

Display Size

The size of the generator.

Scale Width with Size

If checked, the Display Width will automatically be scaled to the appropriate setting when the Display Size is changed. If unchecked, then only the length of the generator object will be affected by changing the value of the Display Size.

Display Width

The width of the display object. This setting is automatically set if Scale Width with Size is checked and the value of the Display Size field is changed, or the Display Width value can be set manually to a new value.

Pixel Thickness

Thickness of the display object in pixels.

Orientation

Specifies the direction in which to draw the object.

Anchored

If checked, the object is anchored to its terminal bus. See [Anchored Objects](11-building-onelines-network-objects.md#anchored-objects) for details.

Link to New Generator

Links the object to a different generator in the data.

Rotor Shape

Several shapes are available for the rotor symbol. The default is the "dog bone" shape, but options are also available for symbols that represent the fuel type of the unit. There is no link between the Fuel Type field that can be specified with a generator and the rotor symbol. The rotor shape must be specified independently of the Fuel Type field. Options are No Shape, Dog Bone, Sine Wave, Battery, Hydrokinetic, Coal, Hydro, Natural Gas, Nuclear, Oil, Solar, and Wind Turbine. (Battery and Hydrokinetic were added in added in version 24)

Fill Rotor Symbol with Color 2, Fill with Color 2

Check the **Fill Rotor Symbol with Color 2** box to use the color specified in the **Fill with Color 2** field to fill the rotor symbol with a different color than the generator background color.

---

<a id="power-and-voltage-control"></a>

## Power and Voltage Control

*Source: [`Content/MainDocumentation_HTML/Generator_Information_Power_and_Voltage_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Information_Power_and_Voltage_Control.htm)*

The **Power Control** grouping fields are used to show/change the values associated with the real power output of the generator.

MW Output

Current real power output of the generator.

MW Setpoint

If a generator is presently online this will show the same value as the MW Output. If the generator either has a status of OPEN or if the bus is disconnected, then MW Output will show 0.00, but the MW Setpoint will show the value of MW that is stored with generator and if the generator does get reconnected that is the MW it will be at.

Minimum and Maximum MW Output

Minimum and maximum real power output limits for the generator. Simulator will not let the MW output go below its minimum value or above its maximum value if the *Enforce MW Limits* option is exercised.

Available for AGC

Determines whether or not the generator is available for automatic generation control (AGC). Normally this box should be checked. However, there are times when you would like to control the generator output manually (such as if you are using the generator to remove a line limit violation), in which case you should leave this box unchecked. A generator is also placed on "manual" control any time you manually change its output. You could then place the generator back on AGC control by using this dialog.

Enforce MW Limits

If checked, the minimum and maximum MW limits are enforced for the generator, provided the **Enforce Generator MW Limits** field is also checked on the Limits Tab of the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options). If this box is checked and a generator is violating a real power limit, the generator's MW output is immediately changed.

Participation Factor

The participation factor is used to determine how the real power output of the generator changes in response to demand when the generator is available for AGC and the area is on [participation factor control](10-power-flow-solution-and-options-part3.md#area-control). When you open a case using the [PTI Raw Data Format](03-cases-files-and-formats.md#case-formats) this field is initialized to the per unit MVA rating of the generator, since participation factor information is not stored in the PTI format.

Loss Sensitivity

Shows how the losses for an area will change for an incremental increase in the generation at the bus. This information is useful in determining the economic dispatch for the generation. The implicit assumption in calculating this field's value is that the incremental change in generation will be absorbed by the system "slack bus." This field cannot be changed.

The **Voltage Control** grouping is used to show/change values associated with controlling the voltage/reactive power output of the generator.

Mvar Output

Current reactive power output of the generator. You can manually change this value only if **Available for AVR** is not checked.

Min and Max Mvar Output

Specify the minimum and maximum allowable reactive power output of the generator.

Available for AVR

Designates whether or not the generator is available for automatic voltage regulation (AVR). When the AVR field is checked, the generator will automatically change its reactive power output to maintain the desired terminal voltage within the specified reactive power range. If a reactive limit is reached, the generator will no longer be able to maintain its voltage at the setpoint value, and its reactive power will then be held constant at the limit value.

Use Capability Curve

If checked, the generator's reactive power limits are specified using a reactive capability curve that prescribes the dependence of the generator's reactive power limits on its real power output. Otherwise, the fixed values given in the **Min Mvar Output** and **Max Mvar Output** fields are used. The generator reactive capability can be defined using the table that appears at the bottom of the dialog. Please see [Generator Reactive Power Capability Curve](#generator-reactive-power-capability-curve) for details.

Regulated Bus Number

Number of the bus whose voltage the generator is regulating. This is usually, but not always, the generator's terminal bus. Multiple generators can regulate the same remote bus, but the regulated bus must not be another generator bus. If the generator is at a slack bus, it must regulate its own terminal voltage. Select **Solution Details \> Remotely Regulated Buses** from the **[Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)** to view the [Remotely Regulated Bus Records Dialog](05-case-information-displays-by-object-part1.md#remotely-regulated-bus-display) , which identifies all buses that are being remotely regulated. Also see topic explaining the [theory of Remote Voltage Regulation](10-power-flow-solution-and-options-part1.md#power-flow-remote-voltage-regulation).

Actual Reg. Bus Voltage

Shows the actual per unit voltage at the regulated bus. If the generator is on AVR and has not reached a reactive power limit, the actual regulated bus voltage should be equal to the desired regulated bus voltage. This field cannot be changed.

SetPoint Voltage

Specifies the desired per unit voltage for the generator at the regulated bus. The regulated bus need not be the terminal bus of the generator.

SetPoint Voltage Tol Added in Version 21

Specifies the tolerance of the desired per unit voltage for the generator at the regulated bus. This then utilized [Voltage Setpoint tolerance algorithm](10-power-flow-solution-and-options-part1.md#power-flow-voltage-setpoint-tolerance) for the power flow equations.

Remote Reg %

This field is used when a number of generators are regulating the same bus, whether the bus is remote or the terminal bus of the generator, to determine how much reactive power this generator provides to maintain the regulated bus voltage. The power flow solution option for [Mvar Sharing Between Generators](10-power-flow-solution-and-options-part1.md#power-flow-mvar-sharing-between-generators) determines how this percentage is used.

Line Drop Compensation

**Use LDC** can be set to NO, YES, or PostCTG to specify when to use the [Line Drop compensation](10-power-flow-solution-and-options-part1.md#power-flow-line-drop-compensation) in the voltage control algorithm. When using line drop compensation, the value of **Xcomp** and **Rcomp** will be used by the power flow solution. The values on this dialog are given in per unit on the <span class="underline">System</span> MVA BAse.

Voltage Droop Control

Specify the name of the VoltageDroopControl object to which the generator is assigned. This is blank by default. When specified the generator will participate in [Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband).

Wind Control Mode and Power Factor 

The Wind Control Mode effects how generator Mvar limits are treated and can be set to either *None*, *Boundary Power Factor* , *Constant Power Factor*or *Follow Min Mvar Capability Curve*.

When the mode is *None*, then the generator behaves using the standard settings of the **Min and Max Mvar Output** and **Capability Curve** described above.

For *Follow Min Mvar Capability Curve* mode, the **Mvar output** of the generator is determined by a lookup from the capability curve's Min Mvar value. Essentially the **Max Mvar Output** and the **Min Mvar Output** are then made equal to this value. This provides the ability to make a generator's **Mvar output** any piece-wise linear function of the **MW output**.

For both the *Boundary* and *Constant* modes, the Mvar limit magnitudes are determined from the actual **MW Output** and the **Wind Control Mode Power Factor** value.

Magnitude = **MWOutput** \* tan(arccos(**Power Factor**))

For *Boundary* mode, the **Max Mvar Output** is positive and the **Min Mvar Output** is negative. This provides a boundary under which the Mvar must operate.

![WindControlBoundary](images/WindControlBoundary.gif)

For *Constant* mode, **Max Mvar Output** and the **Min Mvar Output** are made the same with a positive **Wind Control Mode Power Factor** meaning the limits have the same sign as the actual **MW Output**, and a negative **Wind Control Mode Power Factor** meaning the limits are the opposite sign as the actual **MW Output**, thus the **Mvar output** is a function of **MW Output** and **Power Factor**.

![WindControlConstantPositive](images/WindControlConstantPositive.gif)

![WindControlConstantNegative](images/WindControlConstantNegative.gif)

---

<a id="costs"></a>

## Costs

*Source: [`Content/MainDocumentation_HTML/Generator_Options_Costs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Options_Costs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Costs** tab**** of the Generator Information dialog (run mode) is used to show/change values associated with the cost of operation of the generator. See [Generator Cost Information](#generator-cost-description) for details. Cost data can also be saved/loaded using the [Generator Cost Data files](03-cases-files-and-formats.md#auxiliary-file-format-aux).

Output Cost Model

Cost Model

Simulator can model generators as not having a cost model, or having either a cubic cost model or a piecewise linear model. The cost model type you choose determines the content of the remainder of this dialog

Unit Fuel Cost

The cost of fuel in $/MBtu. This value can be specified only when you have chosen to use a cubic cost model.

Variable O\&M

The Operations and Maintenance costs. Only used for cubic cost models.

Fixed Costs (costs at zero MW Output)

The fixed costs associated with operating the unit. These costs are independent of the generator's MW output level and is added to the cost prescribed by the cubic or piecewise linear model to obtain the total cost of operating the generator in $/MWHr. The total fixed cost is the addition of the fuel cost independent value and the fuel cost dependent value multiplied by unit fuel cost.

Cubic Cost Coefficients A, B, C, D

For cubic cost models of the form C(Pgi) = (d\*Pgi^3 + c\*Pgi^2 + b\*Pgi ) \* (fuel cost) + fixed costs (as described above), specify the cost curve's coefficients. The A coefficient is historically the fuel cost dependent fixed cost value, which is combined separately now with the fuel cost independent value. These coefficients can be specified only when you have chosen to use a cubic cost model.

Piecewise Linear Table

If you have chosen to use a piecewise linear cost model, a table appears that allows you to specify pairs of MW output levels and corresponding generator operating costs. To insert a new point on the cost curve, right-click on the table and choose *Insert New Point* from the resulting local menu. To delete an existing point from the cost curve, right-click on the table and choose *Delete Point* from the resulting local menu. To edit an existing point in the table, simply enter your changes to the appropriate cells.

Convert Cubic Cost to Linear

Use this option to create a piecewise linear cost function from the cubic cost function specified by the coefficients A, B, C, and D and the fuel cost. Specify the number of break points, and hence the number of segments, in the **Number of Break Points** field. Click the **Convert to Linear Cost** button to create the piecewise linear function that approximates the cubic cost function. This action switches **Cost Model** option to *Piecewise Linear* **** and displays the **Piecewise Linear Table** that identifies the piecewise linear curve’s breakpoints.

Bid Scale / Shift

Cost Shift, Cost Multiplier 

The cost shift and cost multiplier allow you to easily apply a shift to the cost function for the purpose of assessing how variations in bids impact profit. The cost function is affected based on the following equation:

(Original Cost Function + Cost Shift) \* Cost Multiplier

Marginal Cost (run mode only) 

Shows the marginal cost of producing real power at the generator at its current output level, dCi(Pgi)/dPgi.

ED/OPF Cost (run mode only)

This is the cost of production for this generator following an economic dispatch or optimal power flow solution, *including* the scaling from the cost shift and cost multiplier fields.

Unscaled Cost (run mode only)

The cost of production of the generator, *ignoring* the cost multiplier and cost shift. This cost is the result of the original cost function by itself.

OPF Reserve Bids

This tab is only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview). Detailed information about this tab can be found in the [Generator and Load OPF Reserves Bids](31-scopf-and-opf-reserves.md#generator-and-load-opf-reserves-bids) topic.

---

<a id="fault-parameters"></a>

## Fault Parameters

*Source: [`Content/MainDocumentation_HTML/Generator_Options_Fault_Parameters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Options_Fault_Parameters.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The parameters on this tab are used when running a [fault analysis](27-fault-analysis.md#fault-analysis) study.

Generator MVA Base

The assumed MVA base for the generator. This value is used when calculating fault analysis values for the internal generator parameters.

Neutral Grounded

Check this check-box if the generator has the neutral grounded.

Generator Step Transformer

The resistance, reactance and tap setting for the generator step-up transformer, if one is being modeled internally with the generator. By default, no internal transformer model is assumed.

Internal Impedance

These fields represent the internal impedance of the generator for all three sequences. By default, all three values are initially the same as the load flow internal impedance of the generator. All three sets of values can be modified, either manually or by loading values from an external file using the [Fault Analysis Dialog](27-fault-analysis.md#fault-analysis-dialog).

Neutral-to-Ground Impedance

Neutral-to-ground impedance for the generator. These values get implemented with the zero sequence admittance matrix. Note that the neutral-to-ground impedance will not be used, even if specified, if the original model for the generator implicitly models the generator step-up transformer. This is because the implicitly modeled transformer is assumed to have a delta winding on the generator side of the transformer, which isolates the generator from the rest of the zero sequence network.

---

<a id="owners-area-zone-sub"></a>

## Owners, Area, Zone, Sub

*Source: [`Content/MainDocumentation_HTML/Generator_Options_Owners_Area_Zone_Sub.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Options_Owners_Area_Zone_Sub.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This information is located on the [Generator Information Dialog](#generator-information).

This tab is used to display or change the generator’s owner information, area information, zone information, and substation information.

Same Owner as Terminal Bus

Read-only check-box that indicates whether the generator’s owner is the same than the terminal buses’ owner.

Owners

Currently, Simulator supports up to four owners for generators. To add an owner of a generator, change one of the Owner fields to a new owner number, and update the owner percentages accordingly. To modify an owner's percentage of ownership, simply modify the value in the percentage field for that owner. If you set the percentage of an owner to 0, that owner will be removed from the list of owners for the device. You can also remove an owner from owning part of a device by changing the owner field for that owner to 0. Note that if you do not set the new owner percentages of all specified owners such that the total is 100%, Simulator will normalize the percentages such that the total is 100% when you click **Save** or **OK** on the generator dialog.

Area Number, Area Name

The area number and name to which the generator belongs. Note that you can change the area of the generator to be different than the area of the terminal bus. If you do so, you will be prompted to confirm that you wish to place the generator within a different area than that of the bus to which it is electrically connected.

Zone Number, Zone Name

The zone number and name to which the generator belongs. Note that you can change the zone of the generator to be different than the zone of the terminal bus. If you do so, you will be prompted to confirm that you wish to place the generator within a different zone than that of the bus to which it is electrically connected.

Substation Number, Substation Name

The name and number of the substation to which the generator belongs, and it is the same than that of the terminal bus.

---

<a id="generator-cost-description"></a>

## Generator Cost Description

*Source: [`Content/MainDocumentation_HTML/Generator_Cost_Description.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Cost_Description.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The cost associated with operating a generator varies according to the output of the generator, with the general rule that getting more power out of a generator costs more. In Simulator, there are two options for modeling generator cost. The first employs the common cubic relationship

 Ci(Pgi)  = IndFixedCost + ( ai + bi Pgi + ci (Pgi)2 + di (Pgi)3 ) \* fuel cost $/Hour

where Pgi is the output of the generator at bus i in MW. IndFixedCost is the fuel cost independent fixed cost, and therefore is not multiplied by the fuel cost. The value ai is the fuel cost dependent fixed cost, and is therefore multiplied by the fuel cost. The values bi, ci, and di are used to model the generator's input-output (I/O) curve. The I/O curve specifies the relationship between how much heat must be input to the generator (expressed in MBtu per hour) and its resulting MW output. Normally, the cubic coefficients remain constant for a generator. The last term in the equation is the fuel cost, expressed in $/MBtu. This value varies depending on the fuel used in a generator. Typical values would be $ 1.25/MBtu for coal and $ 2/Mbtu for natural gas. The resultant equation is known as the fuel-cost curve. The value of the fixed costs, bi, ci, di, and fuel cost can be viewed and modified using the [Generator Information Dialog](#generator-information).

Simulator can also model generator costs using a piecewise linear model consisting of pairs of MW output and incremental cost ($/MWhr) of generation, along with a fixed cost. These piecewise linear curves must be convex curves, meaning the marginal cost of the current MW break point must be higher than the previous MW break point.

Such curves can be defined using the [Generator Information Dialog](#generator-information) or by loading data from [generator cost data](03-cases-files-and-formats.md#auxiliary-file-format-aux) files.

---

<a id="generator-participation-factors"></a>

## Generator Participation Factors

*Source: [`Content/MainDocumentation_HTML/Set_Generator_Participation_Factors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Set_Generator_Participation_Factors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Participation factor control is another of Simulator’s mechanisms for distributing an area’s responsibility to serve its load, losses, and interchange. It is particularly well-suited to implementing [automatic generation control (AGC)](10-power-flow-solution-and-options-part3.md#area-control) when you do not have good economic information for an area’s generators. With participation factor control, the amount of power that each generator contributes to meeting its areas load, loss, and interchange responsibilities is controlled by the size of its participation factor. The unit that has the largest participation factor contributes the most, and the unit that has the smallest participation factor contributes the least.

The **Set Generator Participation Factors Dialog** gives you a convenient way to define the participation factors for multiple generators. You can set the participation factor according to a number of different formulae and then apply this prescription to all generators in a specific area, all generators in a specific zone, all generators in the system, or all generators whose display filters are currently set to true.

To display the **Set Generator Participation Factors Dialog**, you first need to open the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information) and switch to the Area MW Control Options page. The Area Information Dialog has a button labeled **Set Participation Factors** that is enabled only if the Participation Factor Control option is selected under the Area Control Options heading. Set the area on participation factor control by selecting the Participation Factors option, and then press the **Set Participation Factors** option.

The Set Generator Participation Factors Dialog is divided into two parts. The first part, which occupies the top half of the form, allows you to indicate how the participation factors should be calculated or set for each generator. Your options include:

**Max MW Rating of Generator** The participation factor for each generator is set to the generator’s maximum MW capability.

**Difference Between Max and Current Output** The participation factor for each generator is set to the generator’s reserve power, so that each generator participates in proportion to how much it has left to contribute.

**Constant Value of** The participation factor for each generator is set to the same hard-coded value.

**File** The participation factor for each generator is read from a file. The first line of the file should contain the keyword NUMBERS or NAMES indicating whether generators are identified by bus number or by bus name in the file. All subsequent lines should be comma-delimited and contain three fields: the number or name of the generator’s bus, the generator’s id, and the generator’s participation factor.

If you choose any of the first three options, you then must tell Simulator to what generators you want to assign the participation factors. To assign the participation factors to all generators in a specific area, select the **All Generators in Area** option, and then choose the area from the adjacent dropdown box. If you want to assign the participation factors to all generators in a specific zone, select the **All Generators in Zone** option, and then choose the zone from the adjacent dropdown box. If you want to assign the participation factor to all generators in the system regardless of their area or zone affiliation, select the **All Generators in System** option. Finally, if you want to assign the participation factor to just those generators whose display filter criteria evaluates to true, choose the **All Generators With Valid Display Filters** option.

If you instead chose to read participation factors from a file, only those generators whose factors you read from the file will have their factors set by this action. However, unless each generator’s associated area is set to control generator output using participation factor control, this information will be ignored. To make sure that each generator’s area is set to participation factor control, check the **Set Corresponding Areas to Participation Factor Control** box. Then, each corresponding area will be set to participation factor control.

---

<a id="generator-reactive-power-capability-curve"></a>

## Generator Reactive Power Capability Curve

*Source: [`Content/MainDocumentation_HTML/Generator_Reactive_Power_Capability_Curve.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Reactive_Power_Capability_Curve.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The reactive power output of most generators depends on the real power output of the generator. This dependence is expressed using a reactive capability curve. Simulator models the reactive capability curve using a piecewise linear approximation. The reactive capability curve is modified on the [generator dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) and can be saved/loaded using the [Generator Reactive Capability Curve Auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux).

**Modeling a Reactive Power Capability Curve From the Generator Dialog**

  - Make sure the **Use Capability Curve** checkbox is checked.
  - In the table at the bottom of the dialog, prescribe the reactive capability curve using up to 50 points. The points should be ordered by MW, in numerically increasing order. At each point specify the MW value, the minimum reactive power value in Mvar, and the maximum reactive power value in Mvar. The first point should correspond to the minimum MW output of the generator while the last point should correspond to the maximum MW output although there is not a strict requirement that the generator's minimum and maximum output be specified in the curve. If the MW output of the generator is less than the MW value of the first point specified for the curve, the first curve point will be used to determine the minimum and maximum Mvar. If the MW output of the generator is greater than the MW value of the last point specified for the curve, the last curve point will be used to determine the minimum and maximum Mvar.
  - To insert a new point, click on the desired column, and then right-click to display the table's local menu. Select Insert Point.
  - To remove a point, click on the desired column, and then right-click to display the table's local menu. Select Delete Point.
  - When finished be sure to select **Save** to save your modifications.

In the Run Mode, you can view the reactive power capability curve graphically by right-clicking on the generator to display its submenu and then selecting **Reactive Capability Curve**.

---

<a id="load-options"></a>

## Load Options

*Source: [`Content/MainDocumentation_HTML/Load_Options_Edit_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Options_Edit_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view and modify the parameters associated with each load in the system. It can also be used to insert new loads and sometimes to delete existing loads. It is nearly identical in structure to its [Run Mode](07-object-properties-run-mode-and-general-part1.md#load-information) counterpart.

The Load Information Dialog can be used to inspect and modify the model of a bus load. To view the Load Information Dialog, select the load and choose **Show Dialog** from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) or right-click on the load of interest and select **Load Information Dialog** from the resulting local menu. The dialog has the following fields:

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus to which the load is attached. The dropdown box provides a list of all load buses with valid [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). You can use the spin button to cycle through the list of load buses.

When you insert objects graphically, the Bus Number and Bus Name fields are usually set automatically to the bus upon which you placed the object.

Bus Name

Unique alphabetic identifier for the bus to which the load is attached, consisting of up to eight characters. The dropdown box lists the names of all load buses in the case with valid [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

Two-character ID used to distinguish multiple loads at a bus. By default, the load ID is equal to "1 ." An identifier of ‘99’ is used to indicate an equivalent load.

Find By Number

To find a load by its number and ID, enter the number into the Bus Number field and the ID into the ID field. Then click this button.

Find By Name

To find a load by its name and ID, enter the bus name into the Bus Name field (case insensitive) and the ID into the ID field. Then click this button.

Find…

If you do not know the exact load bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Status of the load, either Closed (connected to terminal bus) or Open (not connected). You can use this status field to change the load’s status.

Labels

Clicking on this button will open the [Label Manager](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) dialog listing all the labels assigned for the selected load.

Area Number, Area Name

Number and name of the area the load is a member of.

Zone Number, Zone Name

Number and name of the zone the load is a member of.

Substation Number, Substation Name

Number and name of the substation the load and the terminal bus are members of.

Owner Number, Owner Name

Number and name of the owner the load is a member of. If the load owner is the same as the terminal bus owner, the **Same Owner as Terminal Bus** box will be checked. Loads DO NOT have to be owned by the same owner as the terminal bus.

OK, Save, Delete, and Cancel

**OK** saves your changes and closes the dialog. **Save** saves your changes but does not close the dialog; this allows you to use, for example, the Find By Number command to edit additional loads. **Delete** deletes the current load. **Cancel** closes the dialog without saving your changes.

Specific load information can be found on the following pages of the Load Options dialog:

[Load Information](#load-information)

[OPF Load Dispatch](#opf-load-dispatch)

[Custom](01-getting-started.md#memo-display)

[Stability](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs)

---

<a id="load-information"></a>

## Load Information

*Source: [`Content/MainDocumentation_HTML/Load_Options_Load_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Options_Load_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This page of the Load Options dialog contains information on the load magnitude and display settings.

Base Load Model (MW and Mvar Value Fields)

The MW and Mvar Value fields are used to represent the amount of base real and reactive load at the bus. Usually this load is modeled as being "constant power," meaning that the amount of load is independent of the bus voltage magnitude. However, Simulator also permits modeling "constant current" load, for which the load varies in proportion to the bus voltage magnitude, and "constant impedance" load, for which the load varies in proportion to the square of the bus voltage magnitude. Values in these fields are specified in MW and Mvar assuming one per unit voltage. All six fields can be modified by the user.

The MW Load is then MW = SMW + IMW\*V+ZMW\*V^2 with a similiar equation for Mvar.

Distributed Generation (MW, Mvar and Open/Closed)

Added in Version 19 Distributed Generation MW and Mvar values may be specified with each load record. These values are only used when the Distributed Generation status is set to Closed. When Closed then this represent the distributed generation MW and Mvar represented inside this load. When this is in use, then the net MW and Mvar seen by the power flow solution algorithm will be equal to the Base Load Values minus the Distributed generation.

The Net MW Load is then NetMW=MW - DistMW and NetMvar = Mvar - DistMvar

Display Size

Size of the load.

Scale Width with Size

If checked, the Display Width will automatically be scaled to the appropriate setting when the Display Size is changed. If unchecked, then only the length of the generator object will be affected by changing the value of the Display Size.

Display Width

The width of the display object. This setting is automatically set if Scale Width with Size is checked and the value of the Display Size field is changed, or the Display Width value can be set manually to a new value.

Pixel Thickness

Thickness of the display object in pixels.

Orientation

Specifies the direction to draw the object.

Anchored

If checked, the object is anchored to its terminal bus. See [Anchored Objects](11-building-onelines-network-objects.md#anchored-objects) for details.

Link to New Load

Links the object to a different load record in the data.

---

<a id="opf-load-dispatch"></a>

## OPF Load Dispatch

*Source: [`Content/MainDocumentation_HTML/Load_Options_OPF_Load_Dispatch.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Options_OPF_Load_Dispatch.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This tab of the Load Options dialog contains settings for allowing the load to be included as an OPF Control. The load(s) can then be dispatched in the OPF algorithm according to the assigned costs.

Benefit Model

Benefit Model

If this field is set to none, the load will not be dispatchable in the OPF solution. If the option is set to Piecewise Linear, the load is dispatchable during the OPF, according to the following fields.

Min. and Max. MW Output

Minimum and maximum load MW demand for OPF dispatch.

Available for AGC

If checked, the load will be available for redispatch during the OPF routine.

Fixed Benefit

Value of the load benefit at minimum demand.

Piece-wise Linear Benefit Curve

This table allows you to specify pairs of MW demand levels and corresponding load benefit values, which in turn define the starting points and slopes of the piece-wise linear benefit curve segments. To insert a new point on the cost curve, right-click on the table and choose *Insert New Point* from the resulting local menu. To delete an existing point from the cost curve, right-click on the table and choose *Delete Point* from the resulting local menu. To edit an existing point in the table, simply enter your changes to the appropriate cells.

OPF Reserve Bids

This tab is only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview). Detailed information about this tab can be found in the [Generator and Load OPF Reserves Bids](31-scopf-and-opf-reserves.md#generator-and-load-opf-reserves-bids) topic.

---

<a id="load-field-information"></a>

## Load Field Information

*Source: [`Content/MainDocumentation_HTML/Load_Field_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Field_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Load field display objects are used primarily to indicate various quantities associated with load devices on onelines. Some load field types, which are distinguished by an integrated spin button, may be used to change load device properties.

This dialog can be opened by right-clicking on a load display field and choosing to open the **Load Field Information Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a load display field.

The Load Field Options dialog can be used to modify the properties of individual load fields on the oneline. The dialog displays the following fields:

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Bus Number

Number of the bus to which the load associated with the field is connected. Use the dropdown box to view a list of all buses with loads in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Bus Name

Name of the bus to which the load associated with the field is connected. Use the dropdown box to view a list of all buses with loads in the case with [valid area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

ID of the load associated with the field. Load ID fields are two characters in length.

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

The current value of the field being displayed.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Delta Per Mouse Click

Load fields can be used not only to show various fields associated with load devices, but they can also be used to change some values. This is accomplished using spin buttons shown to the right of the load field. When the up spin button is clicked, the load field value is increased by the amount specified in the *delta per mouse click* field. When the down spin button is clicked, the load field value is decreased by the same amount.

This field is only used for fields of the following types: Load MW and Load Mvar. Specifying a nonzero value in this field causes the integrated spin button to appear as part of the load field on the oneline.

Note that the **Maintain Constant Load Power Factor** option will allow you to specify a Delta per Mouse-click for the MW load, and when the MW value is changed in run mode, the MVAR load will also change in such a way as to keep the power factor of the load constant.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Anchored

If this checkbox is checked, the load field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated load, which means that it will move with the load.

Rotation Angle in Degrees

The angle at which the text is placed on the diagram, in degrees.

Type of Field

Used to determine the type of load field to show. The following choices are available:

Load MW 

Net MW load. This is the total load that is comprised of constant power, constant current, and constant impedance components. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline. If the **Maintain Constant Load Power Factor** option is used in conjunction with the **Delta per Mouse Click** option, the Mvar load will be changed along with the MW load.

Load Mvar 

Net Mvar load. This is the total load that is comprised of constant power, constant current, and constant impedance components. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline.

Select a Field 

Choose from any of the available load fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="load-modeling"></a>

## Load Modeling

*Source: [`Content/MainDocumentation_HTML/Load_Modeling.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Modeling.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Base Load

Each load can be modeled as having voltage variation. The voltage variation is modeled using the Base Load Model fields on the [Load Information](07-object-properties-run-mode-and-general-part1.md#load-information) dialog. Thus the actual real and reactive value of each load is determined using the following equation:

MW = Load MW Multiplier \* (SMW + IMW \* V + ZMW \* V \* V)

Mvar = Load Mvar Multiplier \* (SMvar + IMvar \* V + ZMvar \* V \* V)

where

MW  current real power load in MW

Mvar current reactive power load in Mvar

SMW constant power MW value

Smvar constant power Mvar value

IMW constant current MW value (assuming 1.0 per unit voltage)

Imvar constant current Mvar value (assuming 1.0 per unit voltage)

ZMW constant impedance MW value (assuming 1.0 per unit voltage)

Zmvar constant impedance Mvar value (assuming 1.0 per unit voltage)

V per unit bus voltage magnitude

Load MW Multiplier = (Area MW Multiplier) \* (Zone MW Multiplier)

Load Mvar Multiplier = (Area Mvar Multiplier) \* (Zone Mvar Multiplier)

The Area Multipliers scale all of the loads in an area. The Zone Multipliers scale all of the loads in a zone. These are static values that do not vary over time. If a time varying schedule of loads is required, the [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation) tool should be used instead of the static multipliers.

Distributed Generation and NetMW and NetMvar

Added in Version 19 Distributed Generation MW and Mvar values may be specified with each load record. These values are only used when the Distributed Generation status is set to Closed. When Closed then this represent the distributed generation MW and Mvar represented inside this load. When this is in use, then the net MW and Mvar seen by the power flow solution algorithm will be equal to the Base Load Values minus the Distributed generation.

The Net MW Load is then NetMW= Load MW Multiplier \* (SMW + IMW \* V + ZMW \* V \* V) - DistMW

The Net Mvar Load is then NetMvar= Load Mvar Multiplier \* (SMvar + IMvar \* V + ZMvar \* V \* V) -DistMW

One thing to note in the treatment above, the Load MW Multipliers at the Area and Zone are not applied to the distributed generation value.
