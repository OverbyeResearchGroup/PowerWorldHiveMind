---
title: "Auxiliary Files and Script Commands"
part: "Scripting & Automation"
chapter_file: "09-auxiliary-files-and-script-commands.md"
topics: 8
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Auxiliary Files and Script Commands

Auxiliary file format, script commands, export format descriptions and object field variable names.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (8)**

- [Auxiliary File Format PDF](#auxiliary-file-format-pdf)
- [Auxiliary File Export Format Description (For both Display and Power System)](#auxiliary-file-export-format-description-for-both-display-and-power-system)
- [Complete Case Auxiliary File Export Format Description](#complete-case-auxiliary-file-export-format-description)
- [Network Model AUX Export Format PDF](#network-model-aux-export-format-pdf)
- [PowerWorld Object Field Variable Names](#powerworld-object-field-variable-names)
- [ObjectID Field for use in Auxiliary Fiels](#objectid-field-for-use-in-auxiliary-fiels)
- [Script Command Execution Dialog](#script-command-execution-dialog)
- [Quick Auxiliary Files Dialog](#quick-auxiliary-files-dialog)

---

<a id="auxiliary-file-format-pdf"></a>

## Auxiliary File Format PDF

*Source: [`Content/Other_Documents/Auxiliary-File-Format.pdf`](https://www.powerworld.com/WebHelp/Content/Other_Documents/Auxiliary-File-Format.pdf)*

This topic is a PDF supplied with the PowerWorld help system rather than an HTML page.

- Local copy: [`pdf/Auxiliary-File-Format.pdf`](pdf/Auxiliary-File-Format.pdf)
- Online: <https://www.powerworld.com/WebHelp/Content/Other_Documents/Auxiliary-File-Format.pdf>


---

<a id="auxiliary-file-export-format-description-for-both-display-and-power-system"></a>

## Auxiliary File Export Format Description (For both Display and Power System)

*Source: [`Content/MainDocumentation_HTML/Auxiliary_ExportFormatDescription.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auxiliary_ExportFormatDescription.htm)*

Definition of an Export Format Description

> An export format description consists of the following items:
> 
> 1.  A set of object types
> 2.  The fields and subdata to be exported for each object type, including how each field should be formatted when written (e.g., number of digits, number of decimal places)
> 3.  The format (comma-delimited, space-delimited, etc.) that should be used when writing the object data to disk.
> 
> For instance, an export format description might have two object types defined—buses and generators—with indications to export the bus numbers for each of these objects and to write this information to a space-delimited .AUX file.

Types of Export Format Descriptions

> Export format descriptions can be defined for both the Display Objects and the Power System Objects,
> 
>   - Display objects, e.g., background lines, pie charts, displayed fields, etc. Export format descriptions for display objects are defined by selecting Display Objects Export Format Description… on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, under the List Display Menu on the **Active** ribbon group.
>   - Power system objects, e.g., buses, loads, generators, etc. Export format descriptions for power system objects are defined by selecting Power System Objects Export Format Description from the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab on the **Case Data** ribbon group.
> 
> The dialogs used to define both types of export format description are very similar; any differences between the two dialogs will be clearly noted below.

Export Format Description Dialog

> Clicking on **Display Objects Export Format Description** or **Power System Objects Export Format Description**, opens the Export Format Description Dialog. There are several buttons at the bottom of the dialog:
> 
>   - **Create Format for Complete Case** : click on this button and a drop down will appear giving you the ability to specify hard-coded built-in auxiliary file export format descriptions that define various inputs for PowerWorld Simulator. The various options for input data are described in more detail in [Complete Case Auxiliary File Export Format Description](#complete-case-auxiliary-file-export-format-description). This button will not be available when defining export descriptions for display objects.
>   - **Save AUX** : click button to save the list of Auxiliary File Export Format Descriptions to an Auxiliary file.
>   - **Load AUX** : click button to load an auxiliary file.
>   - **OK** : save the current settings to the selected export format description, and close the dialog
>   - **Create AUX File with Specified Format** : writes data to a file using the current settings. A dialog pops up to select the filename for storing the data. If the file already exists, the data is appended; otherwise, a new file will be created. Uncheck the **Use Concise Variable Names and Auxiliary File Headers** checkbox to use legacy variable names and format for the auxiliary file. If defining an export description for power system data and the ITP add-on is available, the **Use Consolidated Model** checkbox can be checked to save the consolidated model instead of the full topology model.
>   - **Cancel** : do not save the current settings and close the dialog
>   - **Help** : open the help associated with the dialog .
> 
> ![Auxiliary ExportFormatDescription](images/Auxiliary_ExportFormatDescription.png)
> 
>  
> 
> The other parts of this dialog box are discussed in detail below

Format Name Section

> The uppermost part of the dialog box is used to manage the set of export descriptions. Once one export description has been saved (by clicking Save or Save As, after defining some object types), a drop-down box will appear which allows selection of an export format description from the set of export format descriptions saved with the case: The buttons underneath the drop-down box have the following functions:
> 
>   - **New** : clear the rest of the form in order to define a new export format description
>   - **Save** : save the information in the rest of the dialog box to the export format description currently selected in the drop-down box. If no export format description is selected, this is equivalent to clicking Save As.
>   - **Save As** : save the information in the rest of the dialog box to a new export format description; a dialog will pop-up asking for the name of the new export format description.
>   - **Rename** : rename the currently selected export format description
>   - **Delete** : delete the currently selected export format description
> 
> The list of export format descriptions for display objects and power system objects is kept separate, so the drop-down box will only contain export format descriptions defined for the object type selected from the menu (Display Objects Export Format Description Dialog or Power System Objects Export Format Description Dialog).

Object Type and Filter Method Section

> The two-column section on the left side of the dialog box is used to define object types and a filter for each object type.
> 
> Object Type
> 
> > The first column is used to specify which object types are to be exported. To insert a new object type (corresponding to a new row) into the export format description, there are two options—either click the New button above the **Object Type** column heading, or right click on a row and select **Insert**. Upon doing this, a dialog will pop up to choose an object type:
> > 
> > Type into the text box to search for a particular object type. The list of object types depends on the type of export description being defined. When defining display object export descriptions, only display object types will show up in this list; similarly, when defining power system export descriptions, only power system objects will show up.
> > 
> > Clicking **Choose** will insert the object type into the list of object types to be exported.
> > 
> > Double-clicking an existing object type will pop-up this same dialog box, allowing the object type to be changed. Doing so will empty the exported fields, subdata, and filter method.
> 
> Filter Method
> 
> > The second column is used to define an object filter. The default behavior is to export all objects without any filtering, but this can be changed by double-clicking on the filter description. Upon double-clicking on the filter description, a dialog will appear allowing you to choose the filter. The options available for determining which objects are exported are as follows
> > 
> >   - **All** : export all objects, disregarding any filters defined in the current case
> >   - **Use Area/Zone/Owner Filter** : only export those objects that satisfy the currently defined area/zone/owner filter. Clicking on **Select Area/Zone** will pop up the dialog box used to define area/zone/owner filters.
> >   - **Use Selected** : only export those objects that have the Selected field set to Yes. Clicking on **Select** pop up the dialog box used to set the Selected flag for each of the objects in the case. Note that this particular option does not exist for display objects, because display objects do not currently support the Selected field.
> >   - **Meets Filter** : only export those objects that meet an advanced filter, which can be either selected from the drop-down box or defined using the **Define Filter** button.
> >   - When the specified filter only contains a single condition, a prompt will allow storing the single condition as the filter instead of linking to the advanced filter. Using single-condition filters are convenient to use because they do not require that an advanced filter be created and passed along with any aux export descriptions stored in auxiliary files.

Fields And Subdata To Be Exported

> After specifying an object type (and, optionally, a filter), selecting the row on the left side of the dialog box will allow you to specify the fields and subdata to be exported.
> 
> Fields To Be Exported
> 
> > By default, no fields are selected for export. To define fields for export, click on the **Modify** button to the right of the Fields heading the **Select Fields dialog** box will popup. This dialog is used to specify which fields are to be exported, along with any field-specific formatting of numerical values . Generally the dialog behaves identically to the [Configuring Case Information Displays Dialog](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays), so for more detailed help see that topic. There are parts of the dialog that behave differently however, and these are described as follows.
> > 
> >   - **Total Digits / Dec Places** : these two boxes are used to set the number of total digits and the number of decimal places to use when writing the data for the fields current selected in the Selected Fields section. Leaving these two boxes blank means that the default number of digits and decimal places should be used. Also, if multiple fields are selected that have different settings for the number of digits or number of decimal places, these boxes will be grayed out, but still enterable. Once entering a value into either box, all selected fields will then have the same setting, and the box will no longer be greyed out.
> 
> Subdata To Be Exported
> 
> > By default, no subdata is selected to be exported. Also, many objects (e.g., Bus and Area) do not have subdata associated with them, so the **Modify** button will be greyed out. If an object type does have subdata, then the SubData definition section will be grayed out.
> > 
> > To add subdata that should be exported, click the **Modify** button to the right of the SubData heading. This brings up the Select SubData dialog. A description of the options/settings on this dialog follows.
> > 
> >   - **Available SubData** : lists the SubData that exist for this object type. If Exclude subdata already selected is checked, then only SubData that is not already in the Selected SubData section will show up in this list.
> >   - **Exclude subdata already selected** : if checked, then the Available SubData section will only contain items that are not already in the Selected SubData section
> >   - **Selected SubData** : lists the SubData to be exported for this object type
> >   - **Add -\>** : set the currently selected SubData in the Available SubData section to be exported
> >   - **\<- Remove** : set the currently selected SubData in the Selected SubData section to not be exported
> >   - **OK** : save the settings and close the dialog
> >   - **Save** : save the settings, but leave the dialog open
> >   - **Cancel** : do not save the settings and close the dialog
> >   - **Help** : click on this to open the help associated with the Select Fields dialog

---

<a id="complete-case-auxiliary-file-export-format-description"></a>

## Complete Case Auxiliary File Export Format Description

*Source: [`Content/MainDocumentation_HTML/Complete Case Auxiliary File Export Format Description.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Complete Case Auxiliary File Export Format Description.htm)*

When choosing to **Create Format for Complete Case** from the [Auxiliary File Format Description dialog](#auxiliary-file-export-format-description-for-both-display-and-power-system), a dialog will appear asking you to choose which types of input data to define for storage. The options as of the Version 19, build on March 4, 2016included the following.

|                                 |                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Custom Info                     | Defines information for Custom Field Descriptions, Filter, Condition, Expression, String Expression, and Calculated Field objects                                                                                                                                                                                                                                                       |
| Network Model                   | Defines information that defines the network model. This is documented in detail in a special PDF document found at the following link: [Record Format for a Power Flow Case](https://www.powerworld.com/WebHelp/Content/Other_Documents/ExportFormatNetworkModel.pdf)                                                                                                                  |
| Contingency                     | Defines information related to contingency analysis tool. For example, this would include include CTG\_Options\_Value, CTG\_AutoInsert\_Options, CustomMonitor, Contingency Blocks, Global Actions, Remedial Actions, Contingencies and Contingency Monitoring Exceptions. It also includes special fields used by contingency analysis for some others objects (Area, Gen, Bus, Shunt) |
| Geomagnetically Induced Current | Defines additional input data and options beyond what is specified in the Network Model required to perform Geomagnetically Induced Current calculations.                                                                                                                                                                                                                               |
| Transient Models                | Defines information for all the transient stability model objects                                                                                                                                                                                                                                                                                                                       |
| Transient                       | Defines input data related to performing a transient stability simulation. This includes options, plot information, what values to store to RAM, as well as Transient Contingency and Transient Limit Monitor objects.                                                                                                                                                                  |
| Scheduled Actions               | Defines additional input for Scheduled Actions Tool including Scheduled Actions and Scheduled Action Groups.                                                                                                                                                                                                                                                                            |
| Model Info                      | Defines information for special model objects. This includes Model Filters, Model Condition, Model Expression, Model String Expression and Supplemental Data and Contained Objects                                                                                                                                                                                                      |
| Voltage Conditioning            | Defines options, voltage targets, and objects to which the voltage targets apply when using the Case Voltage Conditioning tool.                                                                                                                                                                                                                                                         |
| Weather Dependent Limits        | Defines Weather Stations, XY Curve data, and objects to which weather data can be applied.                                                                                                                                                                                                                                                                                              |
| Contingency Combination         | Defines options and Contingency Primary objects for use with the Contingency Combination Analysis tool.                                                                                                                                                                                                                                                                                 |

PowerWorld also plans to go through and define the following groupings of input data as hard-coded built-in Auxiliary File Export Format Descriptions. These hard-coded options will provide the user an easy way to automatically export the various input data related to particular features in the software. Some of this is already part of tools such as contingency analysis, ATC, PVQV, however the built-in auxiliary file exports on those tools also includes the solution result structures. The intent of these new features in the Auxiliary File Export Format Description is to define <span class="underline">input data</span> structures for sharing data between PowerWorld users. The flexibility of the auxiliary file format is great, but these hard-coded definitions will provide the user with information about which fields go with which tools.

|                    |                                                                                                      |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| Options General    | *Not implemented yet.* Options in Simulator                                                          |
| PV Curve           | *Not implemented yet.* Additional input data related to the PV Curve tool                            |
| QV Curve           | *Not implemented yet.* Additional input data related to the QV Curve tool                            |
| Fault              | *Not implemented yet.* Additional input data related to performing fault analysis                    |
| ATC                | *Not implemented yet.* Additional input data related to the Available Transfer Capability (ATC) tool |
| Optimal Power Flow | *Not implemented yet.* Additional input for Optimal power flow                                       |
| Oneline            | *Not implemented yet.* Additional input options related to oneline diagrams                          |
| Time Step          | *Not implemented yet.* Additional input for the Time Step Simulation tool                            |

---

<a id="network-model-aux-export-format-pdf"></a>

## Network Model AUX Export Format PDF

*Source: [`Content/Other_Documents/ExportFormatNetworkModel.pdf`](https://www.powerworld.com/WebHelp/Content/Other_Documents/ExportFormatNetworkModel.pdf)*

This topic is a PDF supplied with the PowerWorld help system rather than an HTML page.

- Local copy: [`pdf/ExportFormatNetworkModel.pdf`](pdf/ExportFormatNetworkModel.pdf)
- Online: <https://www.powerworld.com/WebHelp/Content/Other_Documents/ExportFormatNetworkModel.pdf>


---

<a id="powerworld-object-field-variable-names"></a>

## PowerWorld Object Field Variable Names

*Source: [`Content/MainDocumentation_HTML/PowerWorld_Object_Variables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerWorld_Object_Variables.htm)*

The ability to access power system data for different objects through various Simulator Automation Server functions is based on variables defined in Simulator that can be referred to as Object Field Variables. Each object (i.e. bus, generator, etc.) can have numerous fields associated with it. Each of these fields, in turn, has a variable associated with the field to enable access to the field for the purpose of acquiring or changing data. For example, the [GetParametersSingleElement](34-simauto-functions.md#getparameterssingleelement) function has a parameter called ParamList, which is intended to store a list of Object Field Variables for a particular type of object. When the function is called, the Simulator Automation Server will return the values associated with each particular field variable for the type of object specified. These field variables allow for complete flexibility by the user in specifying as many or as few fields for a particular object when acquiring or changing data.

**Examples of Field Variables**: **GenMW** and **BusNum**

Simulator has literally thousands of parameters spanning numerous types of device and option specifications. Rather than list all of the field variables and the value they represent in this help file, we have enabled Simulator to automatically generate a text file containing the field variables and a description of what value the variable represents. PowerWorld Corporation highly recommends that you examine this list. To generate this text file, run PowerWorld Simulator and access the **Help** menu. Choose the option **Export** **Case** **Object Fields…** The list of fields can either be saved to a text file or sent to Excel. The list will consist of the field variables, the type of variable (string, integer, etc.), and a description of the value the field variable represents, with key fields for different objects marked with an asterisk. The field variables will also be split into sections based on the type of object they are valid for. Note that the same field variable may be available for more than one object, but that the value represented by the field variable might vary for different objects.

Legacy Variable Names with Location Integers

When listing object field variables, some field variable names may be augmented with a field location. These are in the format variablename:`location`. One example of this is the variable name LineMW. For a branch, there are two MW flows associated with the line: one MW flow at the from bus, and one MW flow at the to bus. So that the number of variable names does not become huge, the same variable name is used for both of these values. For the from bus flow, we write LineMW:0, and for the to bus flow, we write LineMW:1. Field variable names using a location of 0, such as LineMW:0, may simply leave off the :0.

Concise Variable Names

Added in Version 19

Variable names within Simulator have been overhauled starting in Version 19. Most no longer utilize the special location integer and instead spell out such information in the field variable name. In general the variable names have been made more concise or at least more understandable if they are longer. Therefore what was once called LineMW:1 for a BRANCH is now called MWTo. Similarly LineMW:2 is now called MWFromCalc (representing the MW flow at the from bus of branch calculated from the terminal voltages). The only fields that continue to use the location integer are those that represent fields for which a dynamic number of fields are available. Examples of this include the CustomInteger, CustomString, and CustomFloat fields which use the location integer to specify which value is used. Other examples include the multiple direction PTDF results fields PTDFMult:0, PTDFMult:1, and so on.

Referring to Variable Name Integer Location by String

There are several variable names that can be referred to by the user-defined variable name for the field rather than using the location number. These are variable names that might have their location numbers change when different auxiliary files are merged in the same case. Referring to these by name can eliminate this possible confusion. These variable names can be defined in the format variablename:`location_by_name`. They can also be referred to by location number as well.

Variable names that allow referring to the location by name are:

  - Expressions = "CustomExpression:`my expression name`"
  - Custom fields (Floating Point, Integer, and String) - "CustomSingle:`my custom single name`." Using this format for custom fields requires that [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions) be created for the fields to be used.
  - Calculated Fields - "BGCalcField:`my calculated field name`"

Within select SimAuto functions the keyword ALL can be used instead of using the location number of a field when specifying variable names as part of a field list. This will return all fields with the same variable name. This is intended to allow easier access to fields when the exact number of fields is not known, such as with multiple TLR (MultBusTLRSens:ALL) or PTDF (LinePTDFMult:ALL) results. This can be used with [SendToExcel](34-simauto-functions.md#sendtoexcel) and [WriteAuxFile](34-simauto-functions.md#writeauxfile) functions.

---

<a id="objectid-field-for-use-in-auxiliary-fiels"></a>

## ObjectID Field for use in Auxiliary Fiels

*Source: [`Content/MainDocumentation_HTML/AuxiliaryFile_ObjectID_Field.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/AuxiliaryFile_ObjectID_Field.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are many places in an Auxiliary File where a particular object may be referenced. Simulator offers the ability to reference objects using either primary keys, secondary keys, or [labels](07-object-properties-run-mode-and-general-part2.md#labels). In some places you want a single field for an object which you can use as an identifier string that can take as an input any of these potential keys. This special field is available with most objects and is called the **ObjectID** field. When loading an AUX file or when copying/pasting from a spreadsheet, Simulator will look for identifiers using the following precedence

1.  ObjectID
2.  Label
3.  Primary Keys
4.  Secondary Keys

In this way, if the ObjectID is found it will be used as the identifier always. When loading by either ObjectID or Label, you can not create a new object. These fields are only used to refer to existing objects.

The ObjectID returns a string that is space delimited with the first string representing the object type. Following the object type string there will be identification information for the object. This can either be the label for the object, the primary keys listed in order (with a single quote character used to enclose strings that have spaces), or the secondary keys listed in order (again with the single quote character used to unify). Example ObjectID strings are as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Object Type</p></td>
<td><p>Primary Keys</p></td>
<td><p>Secondary Keys</p></td>
<td><p>Label</p></td>
</tr>
<tr class="even">
<td><p>Gen</p></td>
<td><p>"GEN 23 '12'"</p></td>
<td><p>"GEN 'Bus 23_138.00' '12'"</p></td>
<td><p>"GEN 'GrandCoule12'"</p></td>
</tr>
<tr class="odd">
<td><p>Bus</p></td>
<td><p>"BUS 33"</p></td>
<td><p>"BUS 'Bus 33_500.00'"</p></td>
<td><p>"BUS 'Coulee_N56'"</p></td>
</tr>
<tr class="even">
<td><p>Branch</p></td>
<td><p>"BRANCH 23 29 'AB'"</p></td>
<td><p>"BRANCH 'Bus 23_138.00' 'Bus 29_138.00' 'AB'"</p></td>
<td><p>"BRANCH 'CaptJackGrizzly_56"</p></td>
</tr>
<tr class="odd">
<td><p>Branch</p>
<p>(multi-section line)</p></td>
<td><p>"BRANCH 23 29 'AB' 4"</p></td>
<td><p>"BRANCH 'Bus 23_138.00' 'Bus 29_138.00' 'AB' 4"</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Branch</p>
<p>(winding 3WXFormer)</p></td>
<td><p>"BRANCH 23 29 66 'AB'"</p></td>
<td><p>"BRANCH 'Bus45_345.00' 'Bus29_138.00' 'Bus28_69.00' 'AB'"</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>3WXFormer</p></td>
<td><p>"3WXFORMER 23 29 66 'AB'"</p></td>
<td><p> </p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Area</p></td>
<td><p>"AREA 51"</p></td>
<td><p>"AREA 'Fifty One'"</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Zone</p></td>
<td><p>"ZONE 93"</p></td>
<td><p>"ZONE 'Ninety Three'"</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Substation</p></td>
<td><p>"SUBSTATION 37"</p></td>
<td><p>"SUBSTATION 'Thirty Seven'"</p></td>
<td> </td>
</tr>
</tbody>
</table>

Special Note on FixedNumBus Added in Version 24

For objects that use bus numbers in their identifying string, the an FixedNumBus designations for the bus will also impact this string as described in [FixedNumBus Uses in AUX and other Text Files](08-view-case-data-tools.md#fixednumbus-in-aux-and-other-text-files). In the locations where bus integer numbers are used, the ObjectID may also be specified using all the FixedNumBus integers instead. In those situations then all integers in a string must be specified as FixedNumBus integers. Not also then when writing out an AUX file, if FixedNumBus integers are specified, then they will be used

Special Note on Branch and LineShunt objects and Multi-Section Lines

In PowerWorld Simulator as well as PSS/E RAW files, branch records have 3 unique identifiers: “from bus”, “to bus”, and “circuit ID”. There is also a concept of a multi-section line, but this is purely an aggregation object that groups together a series of branches whose statuses are coordinated. Thus within a multi-section line, when one branch changes status, then all branches within the multi-section line group change status to stay coordinated with other branches. The unique identifiers within the various branches in the multi-section line include the intermediate bus numbers or name/kv combinations.

Within a PSLF EPC file format however, the concept of a multi-section line is fundamentally embedded within the concept of the EPC format’s branch record. Thus instead of only 3 identifiers, there are 4 identifiers for a branch within the EPC format: “from bus”, “to bus”, “circuit ID”, and “section number”. There can then be a number of sections that traverse the from bus toward the to bus.

As an example, consider the multi-section line shown below which has 7 sections in series that traverse from bus 40489 to 40687. Normally within PowerWorld Simulator (and a PSS/E RAW file) the 4th section would be identified as "Branch 40704 40706 2". Within GE PSLF however, this branch would instead be identified as "Branch 40489 40687 2 4". Both of these have the same meaning but there are fundamental differences in the identifiers used.

![Auxiliary File ObjectID MSLineSpecial](images/Auxiliary_File_ObjectID_MSLineSpecial.png)

When writing to the Concise Contingency and RAS format we provide an option to write out ObjectID strings that are consistent with those used in the EPC format. The intermediate bus numbers 40700 through 40710 above would not appear in the EPC file format at all and thus are not part of EPC data files. This can be done because the Contingency and RAS format does not create any branch objects, but only refers to branches to define contingency events, model conditions, and so forth.

Therefore, for the branch object ID string with primary or secondary keys as described above, if the branch is part of a multi-section line, then 4 identifiers must be used and parsed accordingly. For branches that are not part of a multi-section line then only 3 identifiers are used. When reading in the AUX file and using the ObjectID as the identifier, Simulator will handle the omission of the identifier if it’s not needed. In addition we will ignore this 4th identifier in a file if it’s not needed. When identifying branches using labels this is not relevant and the object ID string is simply "Branch 'My Label'".

A similar convention will be used for the LineShunt object. If a line shunt exists with Shunt ID “A” at bus 40706 at Section 6 of the multi-section line as shown in the picture above, then normally PowerWorld Simulator would refer to this Line Shunt as "LineShunt 40708 40710 40708 2 A". To maintain compatibility with the treatment of multi-section lines in the EPC file format then when using this special option it will instead by expressed as "LineShunt 40489 40687 40489 2 A 6". The Section ID has been appended to the end of the key field lists. Also note that the 3rd identifier shows the terminal bus identifier for the multi-section line record which is on the same side as the line shunt relative to its branch.

Again, anywhere that a LineShunt is referred to using the object ID string with primary or secondary keys as described above, if the branch to which the LineShunt is connected is part of a multi-section line, then 6 identifiers must be used and parsed accordingly instead of 5. Note that when identifying line shunts using labels this is not relevant and the object ID string would be simply "LineShunt 'My Label String'".

Special Note on Branch objects and Three-Winding Transformers

In PowerWorld Simulator as well as EPC files, when referring to a particular winding of a three-winding transformer, the unique identifiers include the bus identifier for the internal bus (also called the star bus). Within a PSS/E RAW file however, the identifying information for these internal buses is not persistent (for example, in a RAW file the internal buses of three-winding transformers do not exist in the bus table). This is similar to the previous concept in the EPC format where the intermediate buses of multi-section lines do not exist. As a result, to help allow PSS/E support when reading or writing a particular winding of a terminal of a three-winding transformer we will allow an alternate way to describe the branch. This will effect situations such as defining interface definitions, or when monitoring the flow on a winding branch of a three-winding transformer in a Model Condition.

Consider a three-winding transformer which has terminals at buses 10001, 10002 and 10003 and has a circuit of AB and an internal bus number of 10004. In the past in Simulator and PSLF one would refer to one of the windings using the internal star bus number. Instead we will now identify the branch using 4 unique identifiers that include the three terminal buses and the circuit ID. The branch will then be interpreted to represent the winding associated with the first terminal bus listed. This means that the order of the second and third buses lists does not matter. As a result our three windings would be represented as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Winding</p></td>
<td><p>Traditional Identifying String</p>
<p>in PSLF and Simulator</p></td>
<td><p>Modified Method which will not</p>
<p>use the Internal Bus Number</p></td>
</tr>
<tr class="even">
<td><p>Primary</p></td>
<td><p>"BRANCH 10001 10004 'AB'"</p></td>
<td><p>"BRANCH 10001 10002 10003 'AB'" or</p>
<p>"BRANCH 10001 10003 10002 'AB'"</p></td>
</tr>
<tr class="odd">
<td><p>Secondary</p></td>
<td><p>"BRANCH 10002 10004 'AB'"</p></td>
<td><p>"BRANCH 10002 10001 10003 'AB'" or</p>
<p>"BRANCH 10002 10003 10001 'AB'"</p></td>
</tr>
<tr class="even">
<td><p>Tertiary</p></td>
<td><p>"BRANCH 10003 10004 'AB'"</p></td>
<td><p>"BRANCH 10003 10001 10002 'AB'" or</p>
<p>"BRANCH 10003 10002 10001 'AB'"</p></td>
</tr>
</tbody>
</table>

---

<a id="script-command-execution-dialog"></a>

## Script Command Execution Dialog

*Source: [`Content/MainDocumentation_HTML/Script_Command_Execution_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Script_Command_Execution_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Script Command Execution dialog provides a location for the user to enter script commands manually, or to load [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) containing Script and/or Data sections previously defined. This dialog is opened by pressing the **Script** button in the **Log** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.

Loading Auxiliary Files

The first feature of the Script Command Execution dialog is that it provides a location to load previously defined [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) for the currently loaded case. The **Auxiliary File** menu provides a location for loading an auxiliary file, or simply validating that the Script and/or Data sections of an Auxiliary file are correctly formatted in the file.

The **Quick Aux** option allows you to open the [Quick Auxiliary Files](#quick-auxiliary-files-dialog) dialog for creating a list of auxiliary files to be opened and processed en masse.

Lastly, you can export the Simulator recognized objects and object fields using the **Export Field Names** option. You can export the field names to a text for or to Excel.

Running Script Commands

The second feature of the Script Command Execution dialog is that you can run script commands manually. To run a script command, type the command into the display, and press the **Execute** button. Note that if the **Execute on ENTER key** option is checked, the command will also be processed when ENTER is pressed. Note that similar to script command syntax in the Script section of auxiliary files, script commands must be ended with a semi-colon (;) in the Script Command Execution dialog as well.

You can enter multiple script commands to be processed in sequence in this display. To do so, you must uncheck the option **Execute on ENTER key**. Then you can press enter after each script command to move to the next line and enter another command. Use the **Execute** button to process the sequence of script commands.

If you are running a sequence of script commands and wish to abort the run, use the **Abort** button.

If you wish to view the message log while script commands are processing, open the log using the **Show Log** button.

See the [Auxiliary Files and Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux) topic for more details about available script commands and auxiliary data formats.

---

<a id="quick-auxiliary-files-dialog"></a>

## Quick Auxiliary Files Dialog

*Source: [`Content/MainDocumentation_HTML/Quick_Auxiliary_Files_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Quick_Auxiliary_Files_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Quick Auxiliary Files dialog can be accessed from the **Quick Aux Files** menu option of the [Script Command Execution](#script-command-execution-dialog) dialog. This dialog gives you a location for creating a list of auxiliary files to be processed en masse for the currently loaded case.

Using the **Define** option of the **Quick Aux Files** menu, the Quick Auxiliary Files dialog will open. Use this dialog to **Add** previously defined [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) to the list of files to be processed. You can rearrange the order of the files by selecting a file and using the up and down arrows on the right to move the selected file within the list, or you can sort them alphabetically using the **Sort** button. To remove an auxiliary file from the list, use the **Delete** button.

Once the list of auxiliary files to process is complete, press the **Execute** button to process the list of auxiliary files.
