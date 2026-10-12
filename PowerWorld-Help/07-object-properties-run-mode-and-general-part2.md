---
title: "Object Properties — Run Mode and General (Part 2 of 2)"
part: "Viewing Case Data"
chapter_file: "07-object-properties-run-mode-and-general-part2.md"
topics: 30
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Object Properties — Run Mode and General (Part 2 of 2)

Run-mode and general property dialogs, object groups, supplemental data and data maintainers.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (30)**

- [Labels](#labels)
- [Label Manager Dialog](#label-manager-dialog)
- [Latitude/Longitude and UTM Coordinates Conversion](#latitudelongitude-and-utm-coordinates-conversion)
- [Area Information](#area-information)
- [Area Buses](#area-buses)
- [Area Gens](#area-gens)
- [Area Loads](#area-loads)
- [Area MW Control Options](#area-mw-control-options)
- [Information/Interchange](#informationinterchange)
- [Options](#options)
- [Tie Lines](#tie-lines)
- [OPF](#opf)
- [Custom](#custom)
- [Area Field Information](#area-field-information)
- [Super Area Information](#super-area-information)
- [Super Area Field Information](#super-area-field-information)
- [Interface Information](#interface-information)
- [Interface Element Information](#interface-element-information)
- [Interface Field Information](#interface-field-information)
- [Interface Pie Chart Information](#interface-pie-chart-information)
- [Automatically Inserting Interfaces in Case](#automatically-inserting-interfaces-in-case)
- [Nomogram Information Dialog](#nomogram-information-dialog)
- [Bus Pair Information](#bus-pair-information)
- [Injection Groups Overview](#injection-groups-overview)
- [Creating Injection Groups](#creating-injection-groups)
- [Auto Insert Injection Groups](#auto-insert-injection-groups)
- [Deleting Injection Groups](#deleting-injection-groups)
- [Import PTI Subsystems Dialog](#import-pti-subsystems-dialog)
- [Participation Points Overview](#participation-points-overview)
- [Add Participation Points Dialog](#add-participation-points-dialog)

---

<a id="labels"></a>

## Labels

*Source: [`Content/MainDocumentation_HTML/Labels_Topic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Labels_Topic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Using Labels for Identification

Most data objects (such as buses, generators, loads, switched shunts, transmission lines, areas, zones, and interfaces) may have alternative names assigned to them. These alternative names are called labels. Labels allow you to refer to equipment in the model in a way that may be unique to your organization. Labels may thus help clarify which elements are described by a particular set of data, especially when the short names employed by the power system model prove cryptic. Furthermore, since labels are likely to change less frequently than bus numbers, and since a label must, by definition, identify only one power system component, they may function as an immutable key for importing data from [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) into different cases, even when bus numbering schemes change between the cases. Labels must be unique for devices of the same type, but the same label can be used for a device of a different type.

Information dialogs corresponding to buses, generators, loads, switched shunts, transmission lines, areas, zones, and interfaces feature a button called **Labels**. If you press this button, the device’s Label Manager Dialog will appear. The [Label Manager Dialog](#label-manager-dialog) lists the labels associated with the device and allows adding, deleting, and modifying labels. The **Labels (All)** field (variablename = LabelsAll) in a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) lists all of the labels that have been associated with a device. The device's primary label is the one that is listed first in this field. This field lists all labels assigned to a device as a comma-delimited string. Even though multiple labels may be assigned to a device, any label can be used to import data from [auxiliary data files](03-cases-files-and-formats.md#auxiliary-file-format-aux). The Label Manager Dialog can be used to assign labels or the string of labels can be entered directly in the **Labels (All)** field.

Labels can be used to map data from an auxiliary data file to a power system device. Recall that [auxiliary data files](03-cases-files-and-formats.md#auxiliary-file-format-aux) require you to include a device’s key fields in each data record so that data may be mapped to the device. Labels provide an alternative key. Instead of supplying the bus number to identify a bus, for example, you can supply one of the bus’s labels. The label will enable Simulator to associate the data with the device associated with that label. This mechanism performs most efficiently when the primary label is used, but other labels will also provide the mapping mechanism. The **Label (for use in input from AUX or Paste)** field (variablename = Label) is used for importing data using labels and will display only the primary label if more than one label has been assigned. Keep in mind that all devices read via an auxiliary file using the label field should have a non-blank label. Otherwise, information for that device will not be read. Even if the primary or secondary key fields are provided with the device, as long as the label field is present, that is the only field that will be used to identify the device. New devices cannot be created by simply identifying them by label. Either the primary or secondary key fields must be present to create a new device and the label field should not be present.

Again, it is important to remember this: a single power system device may have multiple labels, but each label may be associated with only one device of a particular type. This is the key to enabling data to be imported from an auxiliary file using labels.

Saving Auxiliary Files Using Labels

All devices that can be identified by labels will have the **Labels (All)** and **Label (for use in input from AUX or Paste)** fields available in their case information displays. In order to save auxiliary files that identify devices by label, the two label fields should be added to the case information display prior to saving the data in an auxiliary file. Keep in mind that devices with blank labels cannot be identified when loading in an auxiliary file, so avoid saving auxiliary files by label if all devices do not have labels.

Many devices require SUBDATA sections. These sections have custom formats specific to the type of information that they contain. When saving auxiliary files with devices that require SUBDATA sections, the user can choose to use primary or secondary key fields or labels to identify devices in the SUBDATA sections. The user will either be prompted when saving the devices, or there is an option to change the key field to use when saving subdata sections on the PowerWorld Simulator Options dialog under the [Case Information Displays](10-power-flow-solution-and-options-part2.md#case-information-display-options) category. When choosing to use labels, if a device has a label, it will be used. If it is a device that can be identified by buses and bus labels exist, bus labels will be used. Finally, if the device does not have a label and the buses do not have labels, the primary key for the device will be used for identification.

Devices that have SUBDATA sections that contain other devices that can be identified by labels include: contingencies, interfaces, injection groups, post power flow solution actions, and owners.

The setting to choose which identifier to use for the SUBDATA sections does not just apply to SUBDATA sections. Often when saving groups of options, this setting will apply to everything being saved with those options and not just the SUBDATA sections. This includes contingency options, ATC options, limit monitoring settings, and PVQV options. In these cases, there will be a prompt asking the user to decide which identifier to use in the auxiliary file.

Loading Auxiliary Files SUBDATA Sections Using Labels

The various SUBDATA sections that represent references to other objects can also be read using labels. Examples include contingencies, interfaces, injection groups, post power flow solution actions, and owners. When reading a SUBDATA section such as this, PowerWorld makes no assumption ahead of time about what identification was used to write this SUBDATA section. Instead, an order of precedence for the identification is as follows

<table>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p> </p></td>
<td style="text-align: left;"><p><strong>Identification</strong></p></td>
<td style="text-align: left;"><p>Explanation</p></td>
<td style="text-align: left;"><p>Example</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><strong>1</strong></p></td>
<td style="text-align: left;"><p><strong>Key Fields</strong></p></td>
<td style="text-align: left;"><p>assumes that the strings represent Key Fields</p></td>
<td style="text-align: left;"><p>BRANCH 8 9 1</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p><strong>2</strong></p></td>
<td style="text-align: left;"><p><strong>Secondary Key Fields</strong></p></td>
<td style="text-align: left;"><p>assumes that the strings represent Secondary Key Fields</p></td>
<td style="text-align: left;"><p>BRANCH Eight_138 Nine_230 1</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><strong>3</strong></p></td>
<td style="text-align: left;"><p>Labels for component objects</p></td>
<td style="text-align: left;"><p>the key/secondary key fields for some objects consist of references to other objects. An example of this is the BRANCH object that is described by the From Bus, To Bus, and Circuit ID. This assumes that labels of the component objects are used.</p></td>
<td style="text-align: left;"><p>BRANCH Label8 Label9 1</p>
<p> </p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p><strong>4</strong></p></td>
<td style="text-align: left;"><p>Labels</p></td>
<td style="text-align: left;"><p>Assumes that the string represents one of the Labels of the object</p></td>
<td style="text-align: left;"><p>BRANCH LabelForBranch</p></td>
</tr>
</tbody>
</table>

Special Use of Labels

There are a few special cases where objects have fields that identify other devices. These devices can be identified by label but not in the conventional means because the label field applies to the object that contains the device and a SUBDATA section is not necessary. These special cases include: (Note all fields given below are by variable name because the use of labels is most relevant with auxiliary files.)

ATC Scenarios

[ATC Scenario](32-available-transfer-capability.md#multiple-scenario-available-transfer-capability-dialog) change records usually contain primary key fields to identify the devices that should be adjusted during the scenario. If using labels, these primary key fields will be replaced with a single **Label** field. The use of this field is different because the Label field refers to the device in the change record and not to the change record itself. When labels are used with ATC scenarios, device labels only can be used. Bus labels cannot be used to identify devices for which no label exists but a bus label does.

ATC Scenarios are saved in an auxiliary file if choosing to Save Settings on the [ATC Dialog](32-available-transfer-capability.md#available-transfer-capability-dialog).

ATC Extra Monitors

[ATC Extra Monitors](32-available-transfer-capability.md#atc-extra-monitors-dialog) identify either branches or interfaces to monitor during the ATC analysis. These devices are identified in the **WhoAmI** field of ATC Extra Monitor records. Usually, the **WhoAmI** field is a special format that contains key field tags. Optionally, this field can use the label of the device for the extra monitor. If the device label is not available, the standard format will be used. There is no option to use bus labels if they exist and the device labels do not.

ATC Extra Monitors area saved in an auxiliary file if choosing to Save Settings on the [ATC Dialog](32-available-transfer-capability.md#available-transfer-capability-dialog).

Model Conditions

Devices in [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) are usually identified by the **WhoAmI** field which is in a special format that contains key field tags. Optionally, this field can use the label of the device. If the device label does not exist, the standard format will be used. There is no option to use bus labels if they exist and the device labels do not.

Model Expressions

[Model Expressions](04-model-explorer-and-case-information-part2.md#model-expressions) contain Model Fields. Model Fields are identified by the **WhoAmI** fields in the Model Expressions. Usually, the WhoAmI fields are in a special format that contains key field tags. Optionally, these fields can use the label of the device associated with the Model Field. If the device does not exist, the standard format will be used. There is no option to use bus labels if they exist and the device labels do not.

Bus Load Throw Over Records

[Bus Load Throw Over Records](22-contingency-analysis-options.md#bus-load-throw-over) are used with contingency analysis. These records have an option to identify the bus to which the load will be transferred by either number or name\_kV combination. If choosing to identify objects by label, the **BusName\_NomVolt:1** field will contain the label of the bus instead of the name\_kV combination.

Bus Load Throw Over Records will be saved in an auxiliary file if choosing to [Save](21-contingency-analysis-overview-and-records.md#saving-contingency-records-to-a-file) settings on the Contingency Analysis dialog.

Injection Group Participation Points

All participation points and the injection groups to which they belong can be listed on the [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display). Load, generator, and shunt devices that can be assigned to a participation point must be identified by bus and ID. The bus can be identified by either the number or name. When identifying by name, the **BusName\_NomVolt** field is used to provide the name\_kV combination for the bus. If choosing to identify devices by label, this field instead will contain the label of the device. If the device does not have a label but the bus does, the bus label will be used instead in conjunction with the ID of the device. Even if the device does contain a label, the ID field must be included in any auxiliary file that is going to be loaded because it is a key field. Injection groups can be included in other injection groups. Injection groups can be identified by label, even though this is not a normal thing to do. If any injection groups have labels and these injection groups are included in other injection groups, their labels will also appear in the BusName\_NomVolt field. If they do not have labels, they will be identified by the injection group name that appears in the PPntID field.

---

<a id="label-manager-dialog"></a>

## Label Manager Dialog

*Source: [`Content/MainDocumentation_HTML/Label_Manager_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Label_Manager_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Label Manager Dialog allows the creation and modification of [labels](#labels) to identify power system devices. Labels can be used for most data objects (such as buses, generators, loads, switched shunts, transmission lines, areas, zones, and interfaces) as alternate names for these devices. See the [Labels](#labels) topic for more information on how labels can be used.

The Label Manager Dialog can be accessed by clicking the Labels button on any of the information displays for objects that allow labels.

![Label Manager Dialog](images/Label_Manager_Dialog.gif)

List of Labels

Multiple labels can be assigned to a single object. The list on the left of the dialog shows all of the labels that have been assigned with the primary label listed first and highlighted in yellow.

Add New

Click this button to add a new label after entering the new label in the box to the right of the button. If this new label should be the primary label, check the **Primary** box. Labels must be unique for each type of object. That means that there cannot be two buses labeled *One*. However, there could be objects of different types with the same label. There could be a bus and a generator both labeled *One*. If attempting to label an object with a label that has already been used by the same object type, the label will be assigned to the current object and removed from the object to which it was previously assigned.

Delete

Click this button to delete a label after first selecting the label in the list of labels.

Make Primary

Click this button to make a label the primary label after first selecting the label in the list of labels. The primary label will be moved to the top of the list. The primary label will always appear at the top of the list and will be used for sorting when sorting by label.

---

<a id="latitudelongitude-and-utm-coordinates-conversion"></a>

## Latitude/Longitude and UTM Coordinates Conversion

*Source: [`Content/MainDocumentation_HTML/LatLon_UTM Coordinates_Conversion.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LatLon_UTM Coordinates_Conversion.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This tool is used to convert between Latitude/Longitude and UTM Coordinates in a particular Bus. The Tool is located in the Geography Tab of a Bus or Substation Dialog in the Run or Edit mode.

![LatLon UTM Coordinates Conversion](images/LatLon_UTM_Coordinates_Conversion.gif)

Latitude (degrees)

Entry for the latitude information that is stored with the chosen bus. The Latitude entry can also be entered manually.

Longitude (degrees)

Entry for the longitude information that is stored with the chosen bus. The Longitude entry can also be entered manually.

Datum

Entry for the Datum (model of the shape of the earth) information that is stored with the chosen bus. The Datum entry can also be entered manually. Example: WGS-84.

Convert Lat/Lon to UTM Coord.

Press *Convert Lat/Lon to UTM Coord.* to convert from Lat/Lon coordinates to UTM coordinates.

UTM North/South

Entry for the side of the hemisphere: North or South. The UTM North/South entry can also be entered manually.

UTM Longitude Zone

Entry for the zone information. Also the UTM Longitude Zone entry can also be entered manually.

UTM Northing

Entry for the Northing information. Also the UTM Northing entry can also be entered manually.

UTM Easting

Entry for the Easting information. Also the UTM Easting entry can also be entered manually.

Convert UTM to Lat/Lon Coord.

Press *Convert UTM to Lat/Lon Coord.* to convert from UTM coordinates to Lat/Lon coordinates.

For more information on the Map Projections or conversion between UTM and Latitude/Longitude coordinates please go to http://www.uwgb.edu/dutchs/usefuldata/utmformulas.htm or:

Snyder, John P., Map Projections - A Working Manual, U. Geological Survey Professional Paper 1395, United States Government Printing Office, Washington, D.C.: 1987.

---

<a id="area-information"></a>

## Area Information

*Source: [`Content/MainDocumentation_HTML/Area_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Area Information Dialog shows information about each area in the system. It displays an area’s load, generation and losses; the area’s scheduled interchange with other areas; options for controlling the area’s generators, transformers, and shunts; the flows on its tie lines; and its operating cost information. You may view this dialog by doing any of the following:

  - Select Areas from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This displays the [Area Display](05-case-information-displays-by-object-part1.md#area-display). Select the desired area and click the Show Dialog option on the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar), or right-click on the record corresponding to the desired area to bring up the display’s local menu and choose Show Dialog.
  - Right-click in an empty portion of the oneline near a bus in the area of interest to display the [oneline’s local menu](15-using-onelines-tools-and-options.md#oneline-local-menu). Select Area Information Dialog.
  - While in Run Mode, right-click on an [Area Display Object](11-building-onelines-network-objects.md#area-display-objects) that represents an area and choose Information Dialog. Note: Doing this while in Edit Mode will show the [Area Display Options](11-building-onelines-network-objects.md#area-display-options-dialog) dialog instead of the Area Information Dialog.

The Area Information Dialog contains the following information:

Number

A drop-down box that specifies the area number. Select an area from the drop-down box, or use the spin button to cycle through the list.

Find By Number

To find an area by its number, type the number in the **Number** field and click this button.

Name

A drop-down box that specifies the area’s alphabetic identifier, which may be any length in Simulator. When saving area names to other load flow formats, the names are truncated at the maximum character length supported by that format.

Find By Name

To find an area by its name, type the name in the **Name** field and click this button.

Find…

If you do not know the exact area number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Super Area

To associate an area with a particular super area, either select an existing super area from the drop-down box, or type the name of a new super area.

Area Control Options

Select to change the area’s method of [Automatic Generation Control (AGC.)](10-power-flow-solution-and-options-part3.md#area-control)

Labels

To assign alternative identifying labels to the area, click the Labels button.

The rest of the Area Information Dialog is divided into nine pages of controls:

  - [Info/Interchange](#informationinterchange)
  - [Options](#options)
  - [Area MW Control Options](#area-mw-control-options)
  - [OPF](#opf)
  - [Tie Lines](#tie-lines)
  - [Buses](#area-buses)
  - [Gens](#area-gens)
  - [Loads](#area-loads)
  - [Custom](#custom)

---

<a id="area-buses"></a>

## Area Buses

*Source: [`Content/MainDocumentation_HTML/Area_Information_Area_Buses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Area_Buses.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Area Buses grid shows a list of all buses that are in the area. The grid displays the bus number, bus name and other bus information. The Area Buses display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has options available to these types of displays.

---

<a id="area-gens"></a>

## Area Gens

*Source: [`Content/MainDocumentation_HTML/Area_Information_Area_Gens.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Area_Gens.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Area Gens grid shows a list of all generators that are in the area. The grid displays the bus number, bus name, generator ID and other generator information. The Area Gens display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has options available to these types of displays.

---

<a id="area-loads"></a>

## Area Loads

*Source: [`Content/MainDocumentation_HTML/Area_Information_Area_Loads.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Area_Loads.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Area Loads grid shows a list of all loads that are in the area. The grid displays the bus number, bus name, load ID and other load information. The Area Loads display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has options available to these types of displays.

---

<a id="area-mw-control-options"></a>

## Area MW Control Options

*Source: [`Content/MainDocumentation_HTML/Area_Information_Area_MW_Control_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Area_MW_Control_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Set Participation Factors...

Press this button to open the [Generator Participation Factors Dialog](06-object-properties-edit-mode-part1.md#generator-participation-factors), which gives you control over how the participation factor for each generating unit is defined. If you decide not to prescribe participation factors using this button, the existing participation factors defined with each generator will be used. This button will be enabled only if the area has been set to Participation Factor area control.

Area Slack Bus Number

Identifies which bus to model as the area’s slack bus.

Injection Group Area Slack

An additional area generation control option that can be utilized is the ability for Simulator to use a defined [injection group](#injection-groups-overview) as the sink for Area Slack control. When an injection group is selected, and the area is set on Area Slack control, any needed injection changes in the area will be accounted for by the devices in the injection group.

Some typical injection group options are also available here for handling the injection group dispatching during the Injection Group Area Slack Control. These options include:

Allow only AGC gen/load to vary:

Only generators and loads in the injection group that are designated as available for AGC control will be allowed to participate in injection changes.

Enforce generator MW limits (ignore case and area options):

Generators in the injection group can be designated to enforce their MW limits independent of the global case and area options for generator MW limit enforcement.

Do not allow negative loads:

If loads are decreasing demand as part of an injection group area dispatch, you can specify whether or not those loads should be allowed to go below 0 demand.

How should reactive power load change as real power load is ramped?

You can choose to keep the ratio of real and reactive power constant for each load that is included in the injection group, or you can specify a constant power factor that the MVAR value will be determined from when the MW value is changed.

Injection groups have their own set of options that can override the default options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

---

<a id="informationinterchange"></a>

## Information/Interchange

*Source: [`Content/MainDocumentation_HTML/Area_Information_Information_Interchange.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Information_Interchange.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Info/Interchange Tab serves as an accounting sheet for flows into and out of an area. It houses the following controls:

Load, Generation, Shunts, Losses, Interchange

These read-only fields express the total real and reactive load, generation, shunt compensation, losses, and interchange for the area.

Interchange

Interchange in MW between the area and all other areas (exporting power is positive). To prescribe an interchange with a specific area, simply enter the amount of power in MW to export to that area in the MW Export column. To specify an import, enter a negative value. If the recipient of the power is unknown, you may enter the net total in the **Unspecified MW Interchange** ** field found above the list of transactions. The net value of the MW imports and exports is displayed in **Transaction MW**.

Check the box **Only Show Areas with Nonzero Interchange** to display only those areas whose interchange is different from zero.

By default, one interchange record is initially defined between each area. The total interchange between two areas can be managed using this single record. However, it is possible to define multiple interchange records between the same areas. To do so, you can right-click in the interchange table and select Insert from the local menu. This will open the [Transaction Dialog](05-case-information-displays-by-object-part3.md#mw-transactions-information-dialog), which will allow you to insert a new transaction. Transactions between the same two areas must have unique transaction IDs. Once you have multiple transactions defined between the same two areas, you can choose which transactions are enabled using the Enabled property in the Base Interchange table. This field is a toggleable field, meaning you can double-click in the field to toggle its value.

The total interchange defined for an area will be displayed in the summary field labeled **Interchange** in the area summary totals on the left side of the page.

AGC Tolerance

The MW tolerance is used in enforcing area interchange. When the absolute value of the ACE is less than this value, Simulator considers the area interchange constraint to be satisfied.

ACE (Area Control Error)

Current area control error (ACE) for the area in MW. Note that, when the constant frequency model is used, ACE = area generation - area load - area losses - scheduled area interchange - area shunt MW.

Area Has Multiple Islands

This is an informational field that cannot be changed. If checked, then Simulator has detected that the area has devices in separate [electrical islands](05-case-information-displays-by-object-part3.md#island-display) in the system. This is important because it is sometimes impossible for an area using some form of generation control ([AGC](10-power-flow-solution-and-options-part3.md#area-control)) to solve for the generation dispatch in the entire area (Area Generation = Area Load + Area Losses + Area Interchange + Area Shunt MW) when the area is not entirely within the same electrical island. If Simulator is unable to solve for areas that span multiple islands, the AGC status of the area will automatically be set to "Off AGC" and a warning message will be written to the Simulator [message log](01-getting-started.md#message-log).

---

<a id="options"></a>

## Options

*Source: [`Content/MainDocumentation_HTML/Area_Information_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Report Limit Violations

If checked, limit violations for this area are reported. Limits violations are reported in the [Limit Violations List.](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog)

Generation AGC Values

These fields indicate the total available AGC range for all the generators in the area **that are specified as being on AGC and have nonzero participation factors**. That is, these fields show the total amount the generation in the area that can be increased or decreased using the presently on-line generation. This may be referred to as the *spinning reserve*. The generator status, AGC status, and participation factor can be changed on the [Generator Records Display](05-case-information-displays-by-object-part1.md#generator-display).

Load MW Multiplier Value

This value is used for scaling the area MW load. The base load remains unchanged.

Load MVAR Multiplier

This value is used for scaling the area MVAR load. The base load remains unchanged.

Automatic Control Options

The Automatic Control Options section provides a convenient mechanism to enable or disable automatic control of switched shunts and transformers in the area.

This section also provides a check box for setting if the generators in the area should enforce their Generator MW Limits or not. Typically this should be checked. Note that even if unchecked, the [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) routine end Economic Dispatch will ignore this setting and will always enforce generator MW limits during an OPF solution. Settings for enforcing MW limits at individual generators and globally for the case will also be ignored if using OPF or Economic Dispatch control.

Include Loss Penalty Factors in ED

If this box is unchecked, then the economic dispatch for the area is calculated assuming that the area is lossless. Otherwise, the solution will incorporate losses when computing the economic dispatch. The penalty factors gauge the sensitivity of the area’s losses to changing injection at specific generators. The option to calculate loss penalty factors is relevant only when the area operates according to *Economic Dispatch Control*. Usually, if the system’s cost curves are relatively flat, the inclusion of losses in the solution will not have much of an effect on the dispatch.

Economic Dispatch Lambda

The lambda value calculated during the economic dispatch computation. This field is valid only when the area is on economic dispatch control.

---

<a id="tie-lines"></a>

## Tie Lines

*Source: [`Content/MainDocumentation_HTML/Area_Information_Tie_Lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Tie_Lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Tie Lines display shows the flow on all of the tie lines for the selected area. This display is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and contains many of the options available to these types of displays.

The default fields that are shown in the grid identify each line and show the flow on each line.

Near Area Name, Near Area Number

These fields identify the area name and number of the tie line terminal located in the selected area.

Near Number, Near Name

These fields identify the bus number and name of the tie line terminal located in the selected area.

Far Area Name, Far Area Number

These fields identify the area name and number of the tie line terminal located in the other area.

Far Number, Far Name  

These fields identify the bus number and name of the tie line terminal located in the other area.

Ckt

This is the circuit identifier for the tie line.

Meter MW, Meter Mvar

These are the real and reactive power **flowing on the tie line from the selected area to the other area**. (Real and reactive power flowing on line from the Near bus to the Far bus.)

Status

This field gives the status of the tie line as *Open* or *Closed*.

MW Loss, Mvar Loss

These fields show the real and reactive power losses on the tie line.

To determine the total loss for an area, losses for tie-lines between areas are assigned to the area in which the terminal bus that is NOT the metered bus is contained. The **Metered End** field for a branch determines which of the terminals is metered.

---

<a id="opf"></a>

## OPF

*Source: [`Content/MainDocumentation_HTML/Area_Information_OPF.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_OPF.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Tab contains information regarding the [Optimal Power Flow (OPF)](30-optimal-power-flow-part1.md#opf-primal-lp) solution data for an area. It houses the following information:

Average LMP for Area

The computed average locational marginal price of all buses contained in the area.

LMP Standard Deviation

The standard deviation of the locational marginal price for all buses contained in the area.

Min/Max LMP

The minimum and maximum locational marginal price of all the buses in the area.

Total Generator Production Cost (Scaled)

The scaled cost includes the Cost Shift and Cost Multiplier. These two values can be defined for each generator, and allow the user a way to assess changes to the LMP results when a generators cost or "bid" is modified, without actually changing the original generator cost or bid curve. The scaled cost function for each generator is equal to:

(original cost function + cost shift) \* cost multiplier

Total Generator Unscaled Production Cost

The total unscaled generator production cost, based on the original generator cost or bid curves.

Total Generator LMP Profit

The profit of the generators in the area based on the Locational Marginal Prices (LMPs) determined by the OPF solution. The profit is determined as:

LMP Price \* MW Output – Unscaled Cost Function

Cost of Energy, Loss, and Congestion Reference

Specify a reference for determining the cost of energy, loss and congestion. The choices are Existing loss sensitivities directly, Area’s Bus’ Loads, [Injection Group](#injection-groups-overview), or a specific bus.

Reserve Requirement Curves

These options are only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview). More information about these options can be found in the [Area and Zone OPF Reserve Requirement Curves topic](31-scopf-and-opf-reserves.md#area-and-zone-opf-reserve-requirement-curves).

---

<a id="custom"></a>

## Custom

*Source: [`Content/MainDocumentation_HTML/Area_Information_Custom.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Information_Custom.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Custom page of the [Area Information](#area-information) dialog contains two sections: custom fields and memo.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for areas. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the Area Information dialog is simply a location to log information about the area. To log information about the area, simply switch to the Custom page on the dialog, and start typing your information or comments about the area in the memo box.

---

<a id="area-field-information"></a>

## Area Field Information

*Source: [`Content/MainDocumentation_HTML/Area_Field_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Field_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Area field display objects are used to show different values associated with areas and the system on onelines.

This dialog can be opened by right-clicking on an area display field and choosing to open the **Area Field Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on an area display field.

This dialog is used to view and modify the parameters associated with these fields.

Area Number

Area number associated with the field. When you insert fields graphically, this field is automatically set to the area number associated with the closest bus on the oneline. With most types of area fields, an area number of 0 is valid and defines the field as showing values for the entire system.

Find…

If you do not know the exact area you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Total Digits in Fields

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Rotation Angle in Degrees

The angle at which the text is to appear on the oneline diagram.

Other Area Number

Some of the fields, such as **MW Flow to Other Area**, require that a second area be specified. If applicable, enter the second (other) area here.

Other Area Transaction ID

Because it is possible to have more than one base transaction defined between the same two areas, base transactions must now also have a unique ID to distinguish between transactions among the same two areas. If you are displaying a field that pertains to the display of the scheduled flow between areas, the ID of the transaction in question will also need to be entered here.

Delta MW per Mouse Click

This value is used only with the **Sched Flow to Other Area** field type. When there is a nonzero entry in this field, and the field type is **Sched Flow to Other Area**, a spin button is shown to the right of the area field. When the up spin button is clicked, the flow to the other area is increased by this number of MW; when the down button is clicked, the scheduled flow is decreased by this amount.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Field Value

Shows the current output for the area field. Whenever you change the **Type of Field** selection, this field is updated.

For the **Sched Flow to Other Area** field type only, you can specify a new value in MW. Exports are assumed to be positive.

Anchored

If checked, the area field will be anchored to a corresponding [Area Object](11-building-onelines-network-objects.md#area-display-objects). If the area object is moved on the diagram, the text field will move with it.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of bus field to show. The following choices are available:

Name 

Name of the area. **Area Number** must be non-zero for this field to be non-blank.

Number 

Number of the area. **Area Number** must be non-zero for this field to be non-blank.

MW Load, Mvar Load

If the **Area Number** is non-zero, then these fields show Total MW or Mvar load for the area. If the area number is zero, these fields show the total load in the entire system.

MW Generation, Mvar Generation 

If the **Area Number** is non-zero, then these fields show Total MW or Mvar generation for the area. If the area number is zero, these fields show the total generation in the entire system.

MW Losses, Mvar Losses

If the **Area Number** is non-zero, then these fields show Total MW or Mvar losses for the area. If the area number is zero, these fields show the total losses in the entire system.

ACE (MW) 

Area Control Error in MW for the area. The **Area Number** field must correspond to a valid non-zero area.

Hourly Cost ($/hr) 

If the **Area Number** is non-zero, then this field shows the hourly cost for the area. If the area number is zero, these fields show the hourly cost for the entire system.

Total Cost ($)

If the **Area Number** is non-zero, this field shows the total cost incurred by the area since the beginning of the simulation. If the area number is zero, this field shows the total cost incurred throughout the system since the beginning of the simulation.

MW Flow to Other Area,

Mvar Flow to Other Area

Total MW or Mvar flow from the area specified in the **Area Number** field to the area specified in the **Other Area Number** field. The area number field must correspond to a valid non-zero area. If the **Other Area Number** field is zero, this field shows the area’s total MW or Mvar exports.

Sched. Flow to Other Area

Scheduled MW transaction from the area specified in the **Area Number** field to the area specified in the **Other Area Number** field, and with the Transaction ID given in the **Other Area Transaction ID** field. The area number field must correspond to a valid non-zero area. If the **Other Area Number** field is zero, this field shows the area’s total scheduled MW transactions. **Delta per Mouse Click** can be specified to show a spin button next to this value that can be used for changing it directly from the oneline. Also, you may directly enter a new value in the **Field Value** field.

Load Schedule Multiplier (MW Only)

Indicates the current value of the MW multiplier applied to the area’s loads.

AGC Status

Displays the AGC status of the area.

Select a Field 

Choose from any of the available area fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and close the dialog or **Cancel** to close dialog without saving your changes.

---

<a id="super-area-information"></a>

## Super Area Information

*Source: [`Content/MainDocumentation_HTML/Super_Area_Information_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Super_Area_Information_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Super Area Information Dialog displays information pertaining to [Super Area Display](05-case-information-displays-by-object-part1.md#super-area-display). It summarizes the super area's real and reactive load and generation, scheduled transactions, and constituent areas. It also allows you to manage the list of areas to include in the super area and to designate how its generation should be controlled. To display the Super Area Information Dialog, right-click on the [Super Area Records Display](05-case-information-displays-by-object-part1.md#super-area-display) and select **Show Dialog** from the resulting local menu.

The Super Area Information Dialog has the following fields:

Area in Super Area

Name

The list of all super areas that have been defined in the case are listed in this dropdown box. Select one of the super areas to display its information, or type a new name in the box and click **Add New** to define a new super area.

Rename

Click this button to change the name of the super area specified in the Name field.

Save

Saves the super area of the name specified in the list of super areas.

Delete

Click this button to delete the super area specified in the Name field.

Area in Super Area

Areas in Super Area

Lists the areas contained in the super area. Right-click on a row and select **Remove** to remove the area from the super area.

Super Area Control Options

Specify the type of generation control to employ for the super area. The super area may be removed from area control or employ Participation Factor or Economic Dispatch control. See [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for details on these types of generation control.

An additional type of control available to Super Areas is to **Use Area Participation Factors**. If the super area is set to participation factor control, and this option is NOT checked, then the generators within the super area respond by redispatching to meet the entire super area generation change based on their own participation factors.

However, if this option IS checked, then an additional level of participation control complexity is added for the super area. First, the total super area generation change is divided across each area forming the super area, according to the participation factors of the AREAS, as set in the grid on this dialog. Once the total generation change has been determined for each area within the super area, then the generators within each individual area are dispatched using [area participation factor control](10-power-flow-solution-and-options-part3.md#area-control) to meet each specific area's determined generation change.

Use Area Participation Factors

If the super area control is set to Participation Factor control, you can specify participation factors for each area in the list of areas that indicate how each area should contribute towards changes in generation for the super area. For example, if you have three areas in the super area and you set the participation factors to 1, 1 and 2, the three areas will contribute to the total change in generation in the super area by ratios of 25%, 25%, and 50%, respectively. The contribution of each area is then further divided among the generators within each area by the participation factors of the individual generators.

This option will be applied when calculating [TLR](20-sensitivities.md#shift-factor-sensitivities-dialog), [PTDF](20-sensitivities.md#power-transfer-distribution-factors-dialog), [voltage](20-sensitivities.md#flow-and-voltage-sensitivities), and [ATC](32-available-transfer-capability.md#available-transfer-capability-dialog) sensitivities. When calculating these sensitivities, the assumption is that the super area is on participation factor control even if the control method is something other than this. If this option is selected, it will be enforced regardless of the control method when calculating these sensitivities.

New Area Name

Use the dropdown box to select an area to add to the super area. Click the **Add New Area by Name** to add the selected area to the super area.

New Area \#'s

Enter in a list of area numbers separated with dashes or commas and click **Add New Areas by Number** button to add the areas to the Super Area

Summary Information

ACE Total (MW)

The total area control error for the super area. It is calculated by summing the ACE for all areas comprising the super area.

ACE Tolerance (MW)

The Area Control Error tolerance observed for the super area during a load flow solution.

Total Scheduled Transactions

Lists the total scheduled import or export for the super area. It is computed by summing the scheduled interchange for all areas comprising the super area. Exports are positive.

Lambda

The marginal cost associated with the super area. Lambda is valid only for super areas that are on economic dispatch control.

Hourly Cost

Current average hourly cost for the super area in $/hour.

Load, Generation, Shunts, Losses, Interchange

The Load and Generation section of the Super Area Information Dialog accounts for the real and reactive power flows into, out of, and within the super area. Each quantity is computed by summing over the areas comprising the super area.

OPF

The OPF Tab contains information regarding the [Optimal Power Flow (OPF)](30-optimal-power-flow-part1.md#opf-primal-lp) solution data for a super area. It houses the following information:

Average LMP for Area

The computed average locational marginal price of all buses contained in the area.

LMP Standard Deviation

The standard deviation of the locational marginal price for all buses contained in the area.

Min/Max LMP

The minimum and maximum locational marginal price of all the buses in the area.

Total Generator Production Cost (Scaled)

The scaled cost includes the Cost Shift and Cost Multiplier. These two values can be defined for each generator, and allow the user a way to assess changes to the LMP results when a generators cost or "bid" is modified, without actually changing the original generator cost or bid curve. The scaled cost function for each generator is equal to:

(original cost function + cost shift) \* cost multiplier

Total Generator Unscaled Production Cost

The total unscaled generator production cost, based on the original generator cost or bid curves.

Total Generator LMP Profit

The profit of the generators in the area based on the Locational Marginal Prices (LMPs) determined by the OPF solution. The profit is determined as:

LMP Price \* MW Output – Unscaled Cost Function

Cost of Energy, Loss, and Congestion Reference

Specify a reference for determining the cost of energy, loss and congestion. The choices are Existing loss sensitivies directly, Area’s Bus’ Loads, [Injection Group](#injection-groups-overview), or a specific bus.

Custom

This page of the dialog can be used to enter notes about the super area. Any information entered in the memo box will be stored with the case when the case is saved to a PWB file. Custom fields can also be entered on this page in the form of floating point, integer, and string fields. These custom fields are stored with the super area and can be used for various tasks in Simulator.

---

<a id="super-area-field-information"></a>

## Super Area Field Information

*Source: [`Content/MainDocumentation_HTML/Super_Area_Field_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Super_Area_Field_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Super area field display objects are used to show different values associated with super areas on onelines.

This dialog can be opened by right-clicking on a super area display field and choosing to open the **Super Area Field Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on a super area display field.

This dialog is used to view and modify the parameters associated with these fields.

Super Area Name

Select the name of the super area for which you are inserting or viewing information of a super area field.

Find…

If you do not know the exact super area name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

Shows the current output for the super area field. Whenever you change the **Type of Field** selection, this field is updated.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Rotation Angle in Degrees

The angle at which the text will appear on the diagram.

Anchored

If this checkbox is checked, the super area field is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated super area, which means that it will move with the super area.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of super area field to show. The following choices are available:

Name 

Name of the super area.

MW Load, Mvar Load

Total MW or Mvar load for the super area.

MW Generation, Mvar Generation 

Total MW or Mvar generation for the super area.

MW Losses, Mvar Losses

Total MW or Mvar losses for the super area.

ACE (MW) 

Area Control Error in MW for the super area.

MW Exports

Total MW exports for the super area.

Hourly Cost ($/hr) 

The hourly cost for the super area.

AGC Status

Displays the AGC status of the super area.

MW Marginal Cost ($ / MWhr)

MW marginal cost for the super area.

Select a Field 

Choose from any of the available switched shunt fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Select **OK** to save changes and to close the dialog, or click **Cancel** to close the dialog without saving your changes.

---

<a id="interface-information"></a>

## Interface Information

*Source: [`Content/MainDocumentation_HTML/Interface_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Interface Dialog is used to create, modify, or delete interface records in both the Edit and Run Modes. This dialog has the following controls:

Interface Name

An alphanumeric identifier for the interface. Use the dropdown box or the spin button to navigate through the list of existing interface records.

Interface Number

An integer identifier for the interface.

Find Interface…

If you do not know the exact interface name or number you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Add New Interface

Click the Add New Interface button to define a new interface from the Interface Dialog. When you click this button, the **Interface Name** field and **Interface Elements** table are cleared, requiring you to enter a new name and new elements.

Delete Interface

Select this button to delete the currently displayed interface. Once the interface record has been deleted, the **Interface Name** field displays the previous interface record, if any. If there are not previously defined interface records, Simulator will close the dialog.

Interface Limits

Specify the possible limits for net interface flow. As for transmission lines and transformers, up to eight distinct limits can be specified for interfaces. Which limit set is used can be controlled from the *Limits Tab* of the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options) or the [Line and Transformer Limit Violations Display](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog).

Monitoring Direction

This area allows the user to change the flow monitoring direction. Clicking on the interface in the **Interface Elements** area will bring up the **Interface Elements Dialog**. This is where the default direction is set. To keep this default direction, choose FROM à TO, to change this direction, choose TO à FROM, and to monitor both directions, choose Both Directions.

Noncontingent MW Flow Contribution

Indicates the present net flow through the interface elements, not including affects of contingencies, in MW.

Contingent MW Flow Contribution

The amount of flow that would be added to the interface flow if the contingency defined with the interface were to occur, in MW.

Total MW Flow

The sum of the non-contingent MW flow and Contingent MW flow, for the total MW flow considered on the interface, in MW.

PTDF Value (%)

The [Power Transfer Distribution Factor](20-sensitivities.md#power-transfer-distribution-factors) for the interface, if calculated.

Interface Elements

The Interface Elements Table lists each element comprising the interface. If Simulator is in Run Mode, the table will also show the present flow through each element. To edit or delete an existing element in the table, click on it to bring up the [Interface Element Dialog](#interface-element-information). Use the Interface Element Dialog to modify or delete the element.

Insert New Element

Click the Insert New Element Dialog to add a new element to the interface using the [Interface Element Dialog](#interface-element-information).

Click **OK** to save any changes you have made and to close the Interface Information Dialog. Click **Save** to save your changes but to leave the dialog open so that you can view and modify other interface records. Click **Cancel** to close the dialog without saving your latest change.

Element Identifiers

Choose whether to show the interface descriptions using the interface names, the interface numbers, or a combination of both.

OPF

The OPF page will only be visible if you have the Optimal Power Flow add-on for PowerWorld Simulator. This page contains interface information relating to performing an OPF solution.

Enforce Interface Flow Limit

If checked, the Interface limit will be checked for enforcement during an OPF solution.

Treat Limit as Equality Constraint

If checked, the OPF routine will try and maintain the flow on the interface at its limit value. Otherwise the limit will be treated as the maximum for an inequality constraint.

MW Flow on Interface

The actual MW flow on the interface.

Present MW Limit

The currently defined limit for the interface.

Percentage of Limit

The MW flow on the interface as a percentage of the limit.

Limit Marginal Cost

The incremental cost of maintaining the flow on the Interface at its limit value.

MW Flow Constraint

The constraint status of the interface in the OPF solution is shown here with the corresponding boxes checked by Simulator. These boxes can not be changed by the user.

---

<a id="interface-element-information"></a>

## Interface Element Information

*Source: [`Content/MainDocumentation_HTML/Interface_Element_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Element_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Interface Element Dialog is used to redefine or to add the individual elements comprising an [interface](05-case-information-displays-by-object-part3.md#interface-display). Individual lines or transformers, inter-area ties, inter-zone ties, line contingencies, DC lines, injection groups, generators, and loads may make up an interface. Also, several contingent element types are allowed as well. The Interface Element Dialog allows you to add all varieties of interface elements to an interface.

The Interface Element Dialog comes in two very similar forms, depending upon how it was invoked. The dialog may be called from the [Interface Information Dialog](#interface-information) by clicking on either the Interface Elements Table or the Insert New Element button.

The Interface Element Dialog contains the following controls:

Element Type

Specifies the type of interface element being investigated or added. Interface element types available are as follows.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Type</p></td>
<td><p>Description</p></td>
<td><p>Auxiliary File Syntax</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Branch</p></td>
<td><p>Monitor the MW flow on the branch starting from bus num1 going to bus num2 with circuit ckt. (order of bus numbers defines the direction).</p></td>
<td><p>"BRANCH num1 num2 ckt"</p>
<p>"BRANCH 123 456 1"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Area to Area</p></td>
<td><p>Monitor the sum of the AC branches that connect area1 and area2.</p></td>
<td><p>"AREA num1 num2"</p>
<p>"AREA 34 63"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Zone to Zone</p></td>
<td><p>Monitor the sum of the AC branches that connect zone1 and zone2.</p></td>
<td><p>"ZONE num1 num2"</p>
<p>"ZONE 34 25"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Branch Open</p>
<p>Contingency</p></td>
<td><p>When monitoring the elements in this interface, monitor them under the contingency of opening this branch</p></td>
<td><p>"BRANCHOPEN num1 num2 ckt"</p>
<p>"BRANCHOPEN 123 235 2"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Branch Close</p>
<p>Contingency</p></td>
<td><p>When monitoring the elements in this interface, monitor them under the contingency of closing this branch</p></td>
<td><p>"BRANCHCLOSE num1 num2 ckt"</p>
<p>"BRANCHCLOSE 123 15 4"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>DC Line</p></td>
<td><p>Monitor the flow on a DC line</p></td>
<td><p>"DCLINE num1 num2 ckt"</p>
<p>"DCLINE 123 15 2"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Injection Group</p></td>
<td><p>Monitor the net injection from an injection group (generation contributes as a positive injection, loads as negative)</p></td>
<td><p>"INJECTIONGROUP 'name'"</p>
<p>"INJECTIONGROUP 'my name'"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Generator</p></td>
<td><p>Monitor the net injection from a generator (output is positive injection)</p></td>
<td><p>"GEN num1 id"</p>
<p>"GEN 123 AB"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Load</p></td>
<td><p>Monitor the net injection from a load (output is negative injection)</p></td>
<td><p>"LOAD num1 id"</p>
<p>"LOAD 12 C"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Multisection</p>
<p>Line</p></td>
<td><p>Monitor the MW flow on the multi-section line starting from bus num1 going to bus num2 with circuit ckt</p></td>
<td><p>"MSLINE num1 num2 ckt"</p>
<p>"MSLINE 12 51 D"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Interface</p></td>
<td><p>Monitor the MW flow on the interface given by name</p></td>
<td><p>"INTERFACE 'name'"</p>
<p>"INTERFACE 'The Name'"</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Generator Open</p>
<p>Contingency</p></td>
<td><p>When monitoring the elements in this interface, monitor them under the contingency of closing this generator</p>
<p>(added in Version 20, build on January 9, 2018)</p></td>
<td><p>"GENOPEN num1 id"</p>
<p>"GENOPEN 123 1"</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Load Open</p>
<p>Contingency</p></td>
<td><p>When monitoring the elements in this interface, monitor them under the contingency of closing this load</p>
<p>(added in Version 20, build on January 9, 2018)</p></td>
<td><p>"LOADOPEN num1 id"</p>
<p>"LOADOPEN 121 5"</p></td>
</tr>
</tbody>
</table>

When the selection for Element Type changes, the available **Element Identifiers** change to allow you to pick the appropriate elements of that type.

Element Identifiers

Depending upon the **Element Type** selection, different element identifiers are required to designate the element to add to the interface. You can search through the list of identifiers to find the particular elements you wish to include. Note that the flow direction on transmission line, transformer, and DC line elements will be dependent on which end of the line you choose as the near bus. The flow will always be measured in the direction of near bus to far bus. The flow will be positive when flowing from near to far, and negative when flow from far to near. In addition, line elements also have an additional setting labeled **Monitor Flow at To End**. This determines which magnitude of flow should be reported. If checked, the flow at the To end of the line will be reported, otherwise the flow magnitude at the From end is used.

Insert

If you came to the Interface Element Dialog by pressing the Insert New Element button on the Interface Information Dialog, only the **Insert**, **Cancel**, and **Help** buttons will be available. Click the Insert button to add the element you have just defined to the list of elements comprising the interface. After you click Insert, the dialog will disappear, and the Interface Elements table on the Interface Information Dialog will contain the element you just added.

Replace, Delete

If you arrived at the Interface Element Dialog by clicking on an element in the Interface Elements Table of the Interface Information Dialog, the **Replace**, **Delete**, **Cancel**, and **Help** buttons will be visible. Click **Replace** to modify the interface element according to your specifications on this dialog. Click **Delete** to remove the element from the interface definition.

Cancel

Click **Cancel** to close the Interface Elements Dialog **** without saving your changes.

---

<a id="interface-field-information"></a>

## Interface Field Information

*Source: [`Content/MainDocumentation_HTML/Interface_Field_Information_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Field_Information_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Interface field display objects are used to show the different values associated with [interface records](05-case-information-displays-by-object-part3.md#interface-display) on onelines. This dialog is used to view and modify the parameters associated with these fields.

This dialog can be opened by right-clicking on an interface display field and choosing to open the **Interface Field Dialog** while in run mode. If in edit mode this dialog will be opened simply by right-clicking on an interface display field.

The dialog has the following fields:

Interface Name

Case insensitive name of an existing interface.

Find…

If you do not know the exact interface name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Total Digits in Field

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Rotation Angle in Degrees

The rotation angle at which the text field should be displayed.

Anchored

If checked, the interface field is anchored to its associated interface display object.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of interface field to show. The following choices are available:

Name

Name interface.

MW Flow

Number of the interface.

MW Limit

MW limit for the interface. This limit is determined based on the interface's Limit Set and the option with that Limit Set that specifies which rating set to use for the Normal Rating Set.

Percent

MW Flow as a percent of the MW Limit.

Select a Field 

Choose from any of the available interface fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and close the dialog or **Cancel** to close dialog without saving your changes.

---

<a id="interface-pie-chart-information"></a>

## Interface Pie Chart Information

*Source: [`Content/MainDocumentation_HTML/Interface_Pie_Chart_Information_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Pie_Chart_Information_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Interface Pie Chart objects are used to graphically show the percentage flow associated with [interface records](05-case-information-displays-by-object-part3.md#interface-display). This dialog is used to view and modify the parameters associated with these fields. The dialog has the following fields:

Interface Name

Case-insensitive name of an existing interface (12 characters maximum).

Size

Size of the pie chart. Note that the pie chart's size and color can be set to change automatically when the interface's loading is above a specified limit. Please see [Oneline Display Options](11-building-onelines-network-objects.md#oneline-display-options) for details.

Actual Value (read-only)

In Run Mode, this field shows the current MW loading for the interface.

Percent (read-only)

In Run Mode, this field shows the current percentage loading for the interface; if the MVA rating is zero, the percentage is defined as zero, as well.

Anchored

If checked, the interface pie chart object is [anchored](11-building-onelines-network-objects.md#anchored-objects) to its associated interface.

MW Rating

MW limit for the interface, using the current limit set for the case.

Style

The style of the pie chart. It can be set individually for the particular pie chart, or it can use the style specified in the [Interfaces Pie Chart Options](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-interfaces).

---

<a id="automatically-inserting-interfaces-in-case"></a>

## Automatically Inserting Interfaces in Case

*Source: [`Content/MainDocumentation_HTML/Automatically_Inserting_Interfaces_in_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatically_Inserting_Interfaces_in_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Inserting Interfaces Dialog** is used to insert a group of [interfaces](#interface-information). Only interfaces between adjacent areas or adjacent zones can be inserted automatically; single-branch interfaces between buses must be inserted with line insertion options. Adjacent areas or zones are those that share at least one tie line. To reach this dialog, first open the Interfaces Display by selecting **Aggregations \> Interfaces** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer), and then from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) select **Records \> Auto Insert Interfaces** ****. This dialog is NOT brought up through the menu item **Auto Insert \> Interfaces** found on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group of the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, which is for inserting [interface objects](12-building-onelines-branches-and-devices.md#interface-display-objects) on an oneline diagram.

The Inserting Interfaces Dialog sports the following fields:

Type of Interfaces to Insert

Select the type of interfaces to insert. Area-to-area interfaces join adjacent areas, while zone-to-zone interfaces join adjacent zones. The name of the new interface defaults to "Area1- Area2" or "Zone1-Zone2" with an **Optional Prefix**.

Optional Prefix

This field allows you to specify an optional prefix of up to three characters. Use this prefix to avoid duplicating names, particularly when some of the areas or zones have the same name.

Delete Existing Interfaces

If this option is checked, then all existing interfaces are deleted before inserting the new interfaces. By default, this option is checked. If this option is not checked, the existing interfaces are not deleted. However, new interfaces will automatically overwrite any existing interfaces having the same name.

Only Insert Between Areas/Zones with Area/Zone Filters Set

If this option is checked, the set of potential areas or zones for inserting interfaces is limited to those for which the area/zone filter setting is *Yes*.

Limits

Simulator can either calculate an interface rating based on the ratings of the components included in the interface, or the user can specify a set of ratings to be used for the interface. If neither of these options is used to set an interface limit, then by default, the interface limits are left as 0, indicating no limit has been applied.

Insert Interfaces

Click this button to insert the interface records into the case.

Cancel

Closes the dialog without modifying the list of interfaces.

---

<a id="nomogram-information-dialog"></a>

## Nomogram Information Dialog

*Source: [`Content/MainDocumentation_HTML/Nomogram_Information_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Nomogram_Information_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Nomogram Dialog is used to create, modify, or delete nomogram records in both the Edit and Run Modes. Nomograms are used for combining a pair of [interface objects](05-case-information-displays-by-object-part3.md#interface-display) for the purpose of monitoring a combined flow restriction on the two interfaces together.

This dialog has the following controls:

Nomogram Name

An alphanumeric identifier for the nomogram.

Interface A

The first interface forming the interface pair. To add the interface from scratch in the nomogram dialog, click on the **Insert New Element** button. In this manner you will be creating the interface from the individual elements, the same as creating an interface on the [interface dialog](#interface-information). If you already have an interface defined, and wish to clone the elements of that interface for this nomogram, use the button labeled **Clone Elements From** to find the interface and copy the element definition.

Interface B

The second interface forming the interface pair. To add the interface from scratch in the nomogram dialog, click on the **Insert New Element** button. In this manner you will be creating the interface from the individual elements, the same as creating an interface on the [interface dialog](#interface-information). If you already have an interface defined, and wish to clone the elements of that interface for this nomogram, use the button labeled **Clone Elements From** to find the interface and copy the element definition.

Nomogram Breakpoints

This section is used for defining the limit boundaries for the interface. The limit boundaries are defined by inserting nomogram breakpoints. These breakpoints correspond to a pair of MW flows on each interface. In other words, you define the amount of flow allowed on Interface B when interface A is at a certain amount. Typically you will have a flow limit on Interface B that is constant for a certain range of flow in interface A. However, at some point as the flow on Interface A increases, the limit of flow on Interface B can start to decrease due to desired flow limit restrictions of the combined interfaces. At some point, the limit of Interface A would reach a maximum amount and remain constant, and the range of flow on interface B would be fairly small due to the heavy loading in Interface A.

To build this Nomogram Limiting Boundary, begin by right-clicking in the Nomogram Breakpoints list and choose Insert Point. Note that the boundary definition must be a convex piecewise linear curve. You would typically being by defining the flow limit allowed on Interface B when the flow on interface A is small or zero. Then define breakpoints where the limit on B decreases as the flow on A increases. Eventually you will define a point where the flow on A reaches a limit as the flow on B continues to decrease towards zero. In short, the nomogram limiting boundary is actually a combination of boundary limits that are scaled combinations of the individual interface limits. See the image below for an example of a nomogram limiting boundary.

![image\\ebx\_1167350533.gif](images/ebx_1167350533_470x323.gif)

---

<a id="bus-pair-information"></a>

## Bus Pair Information

*Source: [`Content/MainDocumentation_HTML/BusPair_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/BusPair_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 20

For information on Bus Pair objects see the help on [Bus Pair Case Information Displays](05-case-information-displays-by-object-part3.md#bus-pair-display).

---

<a id="injection-groups-overview"></a>

## Injection Groups Overview

*Source: [`Content/MainDocumentation_HTML/injection_groups_overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/injection_groups_overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

An injection group is a collection of loads, generators, switched shunts, buses, and/or other injection groups. In that respect, injection groups are somewhat analogous to areas and zones. However, unlike with areas and zones, generators, loads, switched shunts, buses, and injection groups can belong to more than one injection group. Moreover, a single injection group may contain generators, loads, switched shunts, and buses from several different areas and zones. Thus, injection groups are useful when modeling a collection of generators, loads, switched shunts, and buses that act together as a unit, regardless of each individual’s area or zone affiliation. The most common use for injection groups is to model a transfer of power from one group of generators and loads to another for [PTDF](20-sensitivities.md#power-transfer-distribution-factors) calculations and for [PV/QV analysis](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview). They are called **injection groups** because their components (generators, loads, and switched shunts) are objects that inject power into the network.

Buses as Injection Points

An injection point within an injection group can simply be defined as a bus. Bus injection points will be ignored in tools that use injection groups and actually cause changes to the system, i.e. scaling and ramping a power transfer in the PV or ATC tools. Without defining specific devices for the injection, Simulator makes no assumption as to how generators or loads should be adjusted at a bus. Standalone sensitivities tools that by the nature of their linear calculations do not require injection from specific devices can use bus injection points.

Specifically, tools that do NOT allow the use of bus injection points and for which bus injection points will be ignored are the following. All other tools that allow the use of injection groups or involve the use of injection group participation points to determine some sort of weighting will include bus participation points:

  - [PV ramping](29-pv-and-qv-curves.md#pv-curves)
  - [ATC iterated methods](32-available-transfer-capability.md#solution-methods)
  - [Scaling](18-general-tools.md#scaling)
  - [Island-Based AGC using an injection group](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc)
  - [Scaling injection group with Time Step Simulation](26-time-step-simulation-part1.md#input-page)
  - Determining power factor for an injection group
  - Injection group used as part of [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)
  - [Injection group contingency actions](24-contingency-element-dialog.md#type-injection-group)

---

<a id="creating-injection-groups"></a>

## Creating Injection Groups

*Source: [`Content/MainDocumentation_HTML/Creating_Injection_Groups.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Creating_Injection_Groups.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Injection groups can be created from the [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display), [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog), [Generator Display](05-case-information-displays-by-object-part1.md#generator-display), [Load Display](05-case-information-displays-by-object-part2.md#load-display), [Switched Shunt Display](05-case-information-displays-by-object-part3.md#switched-shunt-display), or by selecting a group of display objects on the oneline display.

To create an injection group from the Injection Group Display, select **Aggregation \> Injection Groups** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to open the [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display). This display is organized into two tab pages with additional tabs and displays available under each. The Injection Groups tab lists and provides a summary of all defined injection groups. Click the right mouse button on this display, and select **Insert** from the resulting [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) and the [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) will open with a default name assigned to the new injection group. The Injection Group Dialog allows the addition of participation points to the new injection group and allows updating existing injection groups. The **Load** option on the local menu of the Injection Group Display can also be used to import injection groups from an Injection Group Auxiliary Data File and the **Auto Insert Injection Groups** option can be used to automatically insert injection groups based on options set in the [Auto Insertion of Injection Groups Dialog](#auto-insert-injection-groups).

If the [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) is already open, clicking the button labeled **New** **** will create a new injection group. A prompt will then ask for the name of the injection group to add.

To create an injection group from the [Generator Display](05-case-information-displays-by-object-part1.md#generator-display), [Load Display](05-case-information-displays-by-object-part2.md#load-display), or [Switched Shunt Display](05-case-information-displays-by-object-part3.md#switched-shunt-display), select the elements to add to the injection group from one of these displays, right-click on the selection to bring up the local menu, and select **Create Injection Group from Selection** from the local menu. The [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) will open with the selected elements added to a new injection group. Any necessary modifications to the group can be made from the Injection Group Dialog.

To create an injection from a selection of display objects, select the objects to add to the injection group. Only generators, loads, and switched shunts will be added to an injection group, but if other objects are selected, the injection group will still be created. The objects that cannot be added to an injection group will simply be ignored. Once all objects are selected, right-click on the selection to bring up the local menu. On the local menu select **Create Injection Group from Selection**. The [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) will open with the selected objects added to a new injection group. Any necessary modifications to the group can be made from the Injection Group Dialog. More than one object must be selected on the display for the create injection group option to be available.

---

<a id="auto-insert-injection-groups"></a>

## Auto Insert Injection Groups

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_Injection_Groups.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_Injection_Groups.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Many times injection groups need to be created comprised of generators, loads, or switched shunts grouped by areas, zones, super areas, owners, or some other criteria. Injection groups can be created automatically by setting the grouping options by using the Auto Insertion of Injection Groups Dialog.

The Auto Insertion of Injection Groups Dialog can be accessed by selecting **Records \> Auto Insert Injection Groups...** from the case information toolbar on an [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display). The following options are available:

Element Type

This option is used to select the type of element, **Generators**, **Loads**, or **Switched Shunts**, to add to the new injection groups. Only a single type of element can be added to the new injection groups.

Group By

This option dictates the common property by which all elements in the injection group will be grouped. Elements can be grouped by **Areas**, **Zones**, **Super Areas**, **Owners**, or a selected **Custom Field**. If for example the Area option is selected, then injection groups will be created for each of the defined areas in the case. The same holds true for Zones, Super Areas, and Owners. If the **Custom Field** option is selected, then injection groups will be created for all elements whose Custom Field value is the same. For example, if the Custom Field option is selected and Cust Float 1 is set as the field to use, then all of the elements whose Cust Float 1 field are the same will be grouped together. If there are elements whose Cust Float 1 field is set to *1* and there are elements whose Cust Float 1 field is set to *2*, then two new injection groups will be created. One will contain all of the elements whose Cust Float 1 field is *1* and the other will contain all of the elements whose Cust Float 1 field is *2*. Elements whose selected Custom Field is blank will not be included in any of the new injection groups.

For **Areas**, **Zones**, **Super Areas**, and **Owners**, the creation of injection groups can be limited by only creating injection groups for which the **Selected** field is set to *YES* for these groups. To use this option, check the **Only Selected** checkbox.

Participation Factor

The options for specifying participation factor are the same as those used on the [Add Participation Points Dialog](#add-participation-points-dialog).

Delete Existing Injection Groups

When this option is checked, all existing injection groups will be deleted before inserting the new injection groups.

How to Name the Injection Groups

The new injection groups will be named based on the options set in this section. The **Use Prefix** field determines the prefix that will be used on all injection groups. This field can be blank. The **Start at** field determines what integer to start at when counting the new injection groups. The new injection groups will all be numbered in sequential order starting at the value specified. The **Group By** property chosen will also be part of the injection group name. The **Group By** property can be identified based on **Numbers**, **Names**, or **Both**. The field at the bottom of this section provides an example of how the injection groups will be named based on the option settings.  

Set Name to Use Prefix

If the options chosen on the injection group dialog are set such that exactly ONE injection group will be created, you can check this option to name that single injection group using the text entered in the **Use Prefix** field. If more than one injection group will be automatically inserted from the options set in the dialog, this check box option will be ignored, and the injection groups will be create as usual, with the Use Prefix text used as a prefix for the naming convention options selected.

Do Insert Injection Groups

Click this button to implement the options selected and create the injection groups.

Save to Aux

This saves the option settings specified on the dialog to an auxiliary file.

---

<a id="deleting-injection-groups"></a>

## Deleting Injection Groups

*Source: [`Content/MainDocumentation_HTML/Deleting_Injection_Groups.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Deleting_Injection_Groups.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To delete an injection group, select **Aggregations \> Injection Groups** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to open the [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display). This display is organized into two tab pages with additional tabs and displays available under each. The Injection Groups tab lists all defined injection groups. Click the right mouse button on this display on the injection group to delete, and select **Delete** from the resulting local menu.

Alternatively, if the [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) is open, the injection group listed in the Name dropdown box can be deleted by clicking the **Delete** button.

---

<a id="import-pti-subsystems-dialog"></a>

## Import PTI Subsystems Dialog

*Source: [`Content/MainDocumentation_HTML/Import_PTI_Subsystems_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Import_PTI_Subsystems_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Injection groups can be created from PTI subsystem definition files from the [Injection Groups Case Information Display](05-case-information-displays-by-object-part3.md#injection-group-display). Click the right mouse button on this display and select **Load** **\> Subsystem from \*.sub file** from the resulting local menu. From the **Import Injection Groups Dialog**, select the file name for the file to import.

If there is no ambiguity in the import file, new injection groups will be created with the defined subsystem names without further prompts to the user. No ambiguity means that either participation points are defined for buses that have either load or generation but not both or that no participation points are defined and that injection group participation points will be defined based on the maximum generation for each on-line generator in the defined subsystem. If participation points are defined without ambiguity, each participation point will be assigned to either the load or generation at the bus split equally across all loads or generators at the bus.

If there is ambiguity in defined participation points, the Insert PTI Subsystems into Injection Groups Dialog will be displayed. This dialog prompts the user how participation points should be handled for buses with both load and generation or buses with no load or generation.

Buses with Load and Generation

This option allows the user to select how a defined [participation point](#participation-points-overview) will be assigned if the participation point bus has both load and generation.

**Assign Participation Point to Generation**

The participation point will be assigned to generation at the bus. The participation point will be split equally across all generators, either on-line or off-line, at the bus.

**Assign Participation Point to Load**

The participation point will be assigned to load at the bus. The participation point will be split equally across all loads, either connected or not, at the bus.

Buses with No Load or Generation

This option allows the user to select how a defined participation point will be assigned if the participation point bus has no load or generation.

**Ignore Participation Point**

The participation point will be ignored.

**Add Equivalent Load (closed load with ID=’99’ and 0 MW and 0 Mvar) and Assign Participation Point to this Load**

This option adds a connected load at the participation point bus with ID=’99’ and 0 MW and 0 Mvar. The participation point is then assigned to this new load.

For each subsystem that is read that is found to have ambiguity in the defined participation points, the Insert PTI Subsystems into Injection Groups Dialog will be displayed unless the user selects Same Options for All Subsystems (Do not prompt again).

---

<a id="participation-points-overview"></a>

## Participation Points Overview

*Source: [`Content/MainDocumentation_HTML/Participation_Points_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Participation_Points_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A participation point is a member of an injection group. It is a generator, load, switched shunt, bus, or another injection group that participates in, or contributes to, the output of an injection group. Each participation point record identifies the generator, load, switched shunt, bus, or injection group that fills this role, its participation factor, and how that participation factor is calculated. A participation point’s participation factor identifies the degree to which the point will contribute to its injection group’s output relative to the other points making up the group. Participation factors may be defined as having a fixed value, or they may be re-calculated with every use to stay true to how they were originally defined.

Each time that an injection group is used, the participation factors for all participation points in the group are normalized so that the factors of all participating participation points sum to 100%. The normalized factors dictate how much a generator, load, bus, or switched shunt contributes to the output of an injection group. The normalization accounts for the re-calculation of the participation factors with each use of the injection groups and the exclusion of participation points because of options set with the various tools that use injection groups. Participation points can be excluded for various reasons including, but not limited to, the exclusion of generator participation points because the generator is not on AGC control or because the generator is at a minimum or maximum limit. Bus participation points will not be used in tools that actually change the injection of the group, but they may be included in some linear sensitivity calculations.

Participation points are added to or deleted from an injection group using the [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog). The Injection Group Dialog houses the [Participation Point Records Display](05-case-information-displays-by-object-part3.md#participation-point-records-display), which allows the addition or deletion of points and opening the [Participation Points Dialog](#add-participation-points-dialog) to obtain more information about the points.

---

<a id="add-participation-points-dialog"></a>

## Add Participation Points Dialog

*Source: [`Content/MainDocumentation_HTML/add_participation_points_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/add_participation_points_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Add Participation Points Dialog enables the addition of participation points to an [injection group](#injection-groups-overview) as well as the modification of existing participation points. This dialog is accessed from a [Participation Point Records Display](05-case-information-displays-by-object-part3.md#participation-point-records-display) by right-clicking in the participation points list and selecting **Insert** from the resulting [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options). Participation Point Records Displays are available from the [Injection Group Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) or [Injection Group Display](05-case-information-displays-by-object-part3.md#injection-group-display).

![Add Participation Points Dialog](images/Add_Participation_Points_Dialog.gif)

The Add Participation Points dialog features five tabs: one tab each for adding generators, loads, switched shunt, injection groups, and buses.

The five tabs are almost identical and contain the following controls:

Filtering

If the **Use Area/Zone Filters** box is checked, the list box beneath it, which lists generators, loads, switched shunts, previously defined injection groups, or buses depending on the tab, will list only those elements contained in areas or zones or by owners whose [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) setting is *YES*. If this box is not checked, all generators, loads, switched shunts, and buses in the case will be listed. Injection groups will not be filtered using the area/zone/owner filter.

Alternatively, a custom filter can also be defined by clicking on the **Define Filter** button. This will open the [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) dialog, which allows the customization of a filter for determining the devices to list in the display.

Once the list of devices has been set, with or without filtering, the list can be searched using the advanced search techniques in Simulator. These techniques allow the list to be sorted by name or by number and allow the use of wildcard characters. Simply choose Name or Number, and type the name or number of interest in the box. Simulator will look for and highlight the first matching device in the list. If the first device is not the one of interest, use **Search Next** to find the next device that matches the search criteria. For a comprehensive list of all objects matching the search criteria, press **Search All**.

Element List

The box that occupies the left side of each tab lists the generators, loads, switched shunts, injection groups, or buses (depending on which tab is active) that can be added to the injection group. Injection groups will only show up in the element list if they do not cause a circular reference by being added to the current injection group. This means that any injection group that would cause the current injection group to link back to itself will be omitted from the list. Multiple elements can be selected from each of these lists. To select several elements in a row, drag the mouse to highlight the elements to be added. Alternatively, click the first element to add, press and hold the shift key, and click the last element to add. To select elements that are not adjacent in the list, click the first element you to add and hold down the CTRL key while clicking the other elements to add.

Once an element is selected in the Element List, it is ready to be added to the injection group.

Participation Factors

There are several options for defining the participation factors of the selected points.

For generators, a value can be specified, the generator’s present participation factor (which comes from the case and is displayed in the [Generator Display](05-case-information-displays-by-object-part1.md#generator-display)) can be used, the participation factor can be calculated as the difference between its present output and either the unit maximum or minimum, its maximum output capability can be used, or the value contained in a selected Custom Field can be used.

For loads, a value can be specified, the participation factor can be based on the load’s size, or the value contained in a selected Custom Field can be used.

For switched shunts, a value can be specified, the value contained in a selected Custom Field can be used, or the factor can be based on positive reserve, negative reserve, or MVAR capability.

For injection groups, a value can be specified to use for every point in the injection group, the values already defined for the injection group can be used, or the value contained in a selected Custom Field can be used. These three options are available if the option to **Include Individual Group Points** is checked. When this option is checked, copies of the participation points from the selected injection groups are made and added to the current injection group with the participation factors based on the selected option. When **Include Individual Group Points** is not checked, entire injection groups are included, indicated by the Point Type of *INJECTIONGROUP* in the [Participation Point Records Display](05-case-information-displays-by-object-part3.md#participation-point-records-display), in the current injection group and the only option for adding the points is to specify the value for the participation factor. When including an injection group in another injection group as the entire group, the normalization and use of the participation factors follows the discussion of ParFac found in the [Participation Point Records Display](05-case-information-displays-by-object-part3.md#participation-point-records-display). Including an injection group in another injection group as the entire group is useful when the injection of the entire group needs to be changed relative to other individual elements or other injection groups.

For buses, a value can be specified or a value contained in a selected Custom Field can be used.

Bus participation points will be ignored in tools that actually make system changes. These include [Scaling](18-general-tools.md#scaling), [PV](29-pv-and-qv-curves.md#injection-group-ramping-options), [ATC](32-available-transfer-capability.md#advanced-options), [Time Step Simulation](26-time-step-simulation-part1.md#input-page), [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc), and [Injection Group Area Slack](#area-mw-control-options). Bus participation points will be allowed in linear sensitivity calculations and [ATC calculations using only the Single Linear Step method](32-available-transfer-capability.md#single-linear-step-sl).

Use Field or Model Expression

All participation point types allow this option for defining the participation factor. A Field associated with the element in the participation point can be chosen to define the factor. The value of the field will then be used for the participation factor. A Model Expression can also be selected and the result of the model expression will be used for the participation factor.

When choosing either a Field or Model Expression, the participation factors can be recalculated dynamically based on the present value of the Field or Model Expression by checking the **Recalculate Factors Dynamically** box.

Recalculate Factors Dynamically

If this box is checked, the participation factors of the points being added will be automatically updated every time the points are used. Such points will then have an **AutoCalc** value of *YES*. If this box is not checked, the participation factors of the points being added will be fixed at the values defined at the time they were created.

To add the points that have been selected, click the **Add -\>** button. The new points will be added to the list box on the right.

To update existing points, follow the same process for adding points and simply set the participation factors with the new values. When the **Add-\>** button is clicked, the existing points will be updated with the new values.

The list box that occupies the right side of each tab lists the points that already comprise the injection group. To delete specific points from the injection group, select them from this list box and click the **\<-Remove** button.

To close this dialog, click **OK**.
