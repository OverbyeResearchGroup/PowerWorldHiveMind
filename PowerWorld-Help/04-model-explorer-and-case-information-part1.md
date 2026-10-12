---
title: "Model Explorer and Case Information Displays (Part 1 of 3)"
part: "Viewing Case Data"
chapter_file: "04-model-explorer-and-case-information-part1.md"
topics: 24
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Model Explorer and Case Information Displays (Part 1 of 3)

Model Explorer and the mechanics of case information displays: filtering, sorting, columns, formats.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (24)**

- [Model Explorer](#model-explorer)
- [Model Explorer: Fields Pane](#model-explorer-fields-pane)
- [Case Information Displays](#case-information-displays)
- [Configuring the Case Information Displays](#configuring-the-case-information-displays)
- [Custom Field Descriptions](#custom-field-descriptions)
- [Custom Field Descriptions Dialog](#custom-field-descriptions-dialog)
- [Custom Field Toggle Choices](#custom-field-toggle-choices)
- [Calculated Fields](#calculated-fields)
- [Case Information Customizations Display](#case-information-customizations-display)
- [Local Menu Options](#local-menu-options)
- [Colors and Cell Styles](#colors-and-cell-styles)
- [Using Cell Handles](#using-cell-handles)
- [Sorting Records](#sorting-records)
- [Finding Records](#finding-records)
- [Saving Case Information Display Contents As HTML Tables](#saving-case-information-display-contents-as-html-tables)
- [HTML Table Format Dialog](#html-table-format-dialog)
- [Case Information Toolbar](#case-information-toolbar)
- [Copy, Paste and Send Menu](#copy-paste-and-send-menu)
- [Filtering Menu](#filtering-menu)
- [Geo Data View Menu](#geo-data-view-menu)
- [Load Auxiliary Files Menu](#load-auxiliary-files-menu)
- [Save Auxiliary Files Menu](#save-auxiliary-files-menu)
- [Records Menu](#records-menu)
- [Set, Toggle, and Columns Menus](#set-toggle-and-columns-menus)

---

<a id="model-explorer"></a>

## Model Explorer

*Source: [`Content/MainDocumentation_HTML/Model_Explorer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Explorer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

![ModelExplorerButton](images/ModelExplorerButton.gif)

Most [Case Information Displays](#case-information-displays) are enclosed inside the Model Explorer. To open the Model Explorer, click on the Model Explorer button shown above. The Model Explorer button is available on both the [Case Information Ribbon Tab](02-simulator-ribbon.md#case-information-tab-overview) and [Tools Ribbon Tab](02-simulator-ribbon.md#tools-tab-overview) by default. It is also placed on the [Quick Access Toolbar](02-simulator-ribbon.md#quick-access-toolbar) by default.

Note: normally only one Model Explorer window will be open at a time. If you choose to open a case information display from various places in the Ribbon, the open Model Explorer will be moved to this case information display. If you want multiple Model Explorers to be open, then click on the **Open New Explorer** button below the Explore Pane.

When you open the Model Explorer you will see a case information display. In addition to this the model explorer has 5 additional regions to help you navigate the model as well as modify the model.

Explore Pane

The Explore Pane contains a hierarchical list of most of the objects contained in the power system model. Entries in the Explore Pane that are grayed out represent objects that presently are not defined in the model. The Explore Pane is separated into eight primary folders, with only the Network and Aggregations folder expanded by default. The primary folders are as follows:

  - **Recent** - contains a list of case information displays that have been recently opened. This same list of case information displays are depicted by the Tabs displayed across the top of the Model Explorer which indicate the currently open data tables.
  - **Network** - contains a list of the network model objects. Generally these represent actual physical devices such as a generator or transmission line.
  - **Aggregations** - contains a list of model objects that represent an aggregation of other model objects. Some examples of data found here are [interfaces](07-object-properties-run-mode-and-general-part2.md#interface-information) and [injection groups](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview).
  - **Case Information and Auxiliary** - contains generic objects that operate on the other objects in the model.
  - **Conditions, Filters, and Expressions** - \[Split out as separate section in Version 24\]contains the [Advanced Filters, Conditions](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced), [Expression](04-model-explorer-and-case-information-part2.md#expressions) and String Expressions, as well as the model-wide variations of those such as [ModelFilter](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog) and [ModelCondition](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) objects.
  - **Optimal Power Flow** - contains a convenient place to access case information displays showing options related to the OPF or [SCOPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview).
  - **Solution Details** - provides access to case information displays that provide details regarding the power flow solution. It includes displays such as the Y-Bus, Jacobian, and summaries of remotely regulated buses
  - **Tools and Add Ons** - contains a convenient place to access case information related various tools and Add Ons such as [contingency analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), [fault analysis](27-fault-analysis.md#fault-analysis), and [Scheduled Actions Analysis](48-scheduled-actions.md#scheduled-actions-tool).
  - **Transient Stability** - contains a convenient place to access case information displays showing options related to [Transient Stabilit](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)y
  - **User-Defined** - contains a list of User-Defined Case Information Displays available. These displays are created by right-clicking on the Explore Pane and choosing to Insert User-Defined Case Info. For more information see the [User-Defined Case Information Displays](04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays) help.

> Explore Pane Options
> 
> There are a few options regarding the Explore Pane which can be accessed by right-clicking on the Explore Pane, Searchbar, Filterbar, or Case Information Toolbar. When right-clicking a local menu will appear that allows you to specify the following options.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><img src="images/Model_Explorer_Explore_Pane_Options.gif" alt="Model Explorer Explore Pane Options" /></td>
<td><p><strong>Fields Pane Location</strong> : Allows you to specify the location of the Fields Pane. See the <a href="#model-explorer-fields-pane">Model Explorer: Fields Pane</a> for more details.</p>
<p><strong>Save Recent (Number)</strong> : Choose this option to change the number of recently viewed case information tables that are kept open and shown as tabs in the Recent Tabs.</p>
<p><strong>Show Number of Objects</strong> : Check this option to show a number next to each entry in the Explore Pane.</p>
<p><strong>Insert User-Defined Case Info,</strong></p>
<p><strong>Remove User-Defined Case Info</strong> : These options allow you to insert and remove user-defined Case Information Displays. For more detailed information see the <a href="04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays">User-Defined Case Information Display</a> help.</p></td>
</tr>
</tbody>
</table>

Fields Pane 

The Fields Pane provides direct access to modifying the columns that appear on the case information displays. This replicates the features that can also be accessed by choosing ![Model Explorer Case Info Toolbar Display Options](images/Model_Explorer_Case_Info_Toolbar_Display_Options.gif) **Display/Column Options** on the [case information toolbar](#case-information-toolbar) to open the dialog for [Configuring the Case Information Displays](#configuring-the-case-information-displays). See the [Model Explorer: Fields Pane](#model-explorer-fields-pane) for more details.

Recent Tabs

The Recent Tabs represent a list of the most recently viewed case information displays on the Model Explorer. You can click on the X to the left of each tab to clear that from the recent list.

Case Information Toolbar

The Case Information Toolbar contains a graphical representation of all the options and actions which can be applied to the case information display. The toolbar is described in detail in the [case information toolbar](#case-information-toolbar) topic. Also note that all the options displayed on the toolbar are also available by right-clicking on the toolbar and showing the [case information local menu](#local-menu-options).

Case Information Filterbar

The Filterbar provides convenient access to apply an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) or a [Device Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device) to the case information display. The toolbar is described in detail in the [Case Information Filterbar](04-model-explorer-and-case-information-part2.md#case-information-filterbar) topic.

Case Information Searchbar

The Searchbar contains a toolbar that allows you to search the active case information display for particular text. This toolbar behaves in the same manner as the [Search For Text Dialog](04-model-explorer-and-case-information-part3.md#search-for-text-dialog).

A picture of the Model Explorer as it appears when showing the generator records is shown below. Besides showing case information display, 

![Model Explorer](images/Model_Explorer.gif)

---

<a id="model-explorer-fields-pane"></a>

## Model Explorer: Fields Pane

*Source: [`Content/MainDocumentation_HTML/Model_Explorer_Fields_Pane.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Explorer_Fields_Pane.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Fields Pane on the Model Explorer provides direct access to all the fields available for the case information display shown. The same features can also be accessed by choosing ![Model Explorer Case Info Toolbar Display Options](images/Model_Explorer_Case_Info_Toolbar_Display_Options.gif) **Display/Column Options** on the [case information toolbar](#case-information-toolbar) to open the dialog for [Configuring the Case Information Displays](#configuring-the-case-information-displays). A picture of the Fields Pane is shown at the bottom of this topic.

**Dragging to Add Fields**

After selecting fields from the Fields Pane, left-click and drag to add fields to the case information display. Fields will be added to the left of the column on which they are dropped. You will see red highlighting in the column headings indicating the position to which the fields will be added.

**Dragging to Remove Fields**

If you hold the CTRL key down and then left-click and drag a column heading from the case information display, you can then drop into the list of fields on the Fields Pane to remove the column.

Dragging to Move Fields

If you hold the CTRL key down and then left-click and drag a column heading on the case information display, you can move the columns around relative to one another. You will see red highlighting in the column headings to indicate the position to which the field is being moved.

**Find Field**

Click this button to search through the list of fields using a wild card search.

**Add -\>**

Click this button and all selected fields in the Fields Pane will be added to the left of the presently selected columns in the case information display.

**\<-Remove**

Click this button and all columns that have any cell presently selected will be removed from the case information display.

**Expand and Collapse**

Click this button to expand or collapse the folder view showing all the available fields.

**Frozen Columns**

The number of columns that are fixed and do not scroll when you scroll left or right in the display. Frozen columns will have a background color of gray instead of white. The number of frozen columns is 1 by default.

**Reset to Factory Defaults**

Click this button to reset all case information display properties to their default settings, including column and data field associations.

**Fields Pane Location**

By right-clicking on the Fields Pane or Explore Pane you can bring up the [Explore Pane Options](#model-explorer). On this drop-down you can specify the Fields Pane Location to be either **Tab with Explore**, **Left Side**, or **Right Side**. The behavior for the various pane locations are shown as follows.

![Model Explorer Fields Pane TAB](images/Model_Explorer_Fields_Pane_TAB.gif)

![Model Explorer Fields Pane RIGHT](images/Model_Explorer_Fields_Pane_RIGHT.gif)

![Model Explorer Fields Pane LEFT](images/Model_Explorer_Fields_Pane_LEFT.gif)

---

<a id="case-information-displays"></a>

## Case Information Displays

*Source: [`Content/MainDocumentation_HTML/Case_Information_Displays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Displays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator offers numerous [Case Information Displays](https://www.powerworld.com/WebHelpvoid\(0\);) that provide a convenient, spreadsheet-like view of the power system and its components and are available regardless of whether the case has an associated oneline diagram or not. Many case information displays are available by using the [Model Explorer](#model-explorer) button found on the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, although these spread-sheet like views appear throughout the software as stand-alone displays and embedded inside other dialogs. Case information displays are available for buses, bus mismatches, generators, generator costs, ac lines, transformers, transformer impedance correction tables, dc lines, interfaces, areas, zones, schedules, and all other types of objects.

It is also possible to create [User-Defined Case Information Display](04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays) on the [Model Explorer](#model-explorer).

Other screens, such as the [Area/Zone/Owner Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) display, also fall into the category of case information displays. There are many different characteristics associated with the Case Information Displays, as discussed in the following topics:

[Colors and Cell Styles](#colors-and-cell-styles)

[Using Cell Handles](#using-cell-handles)

[Case Information Toolbar](#case-information-toolbar)

[Case Information Filterbar](04-model-explorer-and-case-information-part2.md#case-information-filterbar)

[Sorting Records](#sorting-records)

[Configuring the Case Information Displays](#configuring-the-case-information-displays)

[Finding Records](#finding-records)

---

<a id="configuring-the-case-information-displays"></a>

## Configuring the Case Information Displays

*Source: [`Content/MainDocumentation_HTML/Configuring_the_Case_Information_Displays.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Configuring_the_Case_Information_Displays.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The content and format of all case information displays can be controlled through the Display / Column Options dialog. This dialog can be viewed by choosing ![Model Explorer Case Info Toolbar Display Options](images/Model_Explorer_Case_Info_Toolbar_Display_Options.gif) **Display/Column Options** on the [case information toolbar](#case-information-toolbar) or from the case information display’s [local menu](#local-menu-options). The features on this display can also be accessed on the [Model Explorer: Fields Pane](#model-explorer-fields-pane).

To reset all case information display properties to their default settings, including column and data field associations, click the **Reset to Factory Defaults** button.

To save your changes and close the dialog box, click ** **OK**. To save your changes without closing the dialog box, click **Save**. To undo the changes you have specified and close the dialog box, click **Cancel**. Finally, click **Help** to view the corresponding help screen.s

While it is normally sufficient to customize the case information displays that comes with the program, it is also possible to create [User-Defined Case Information Displays](04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays) on the [Model Explorer](#model-explorer). This then provides the ability to switch between different sets of columns, filters, sorting etc. without requiring repeated customizations.

Added in Version 20 Customizing these DataGrids also provides you a way to create custom Data View layouts providing you a mechanism to create custom dialogs. See [Data View](08-view-case-data-tools.md#data-view) help for more information.

Column Options

The Column Options Tab is shown in the figure below.

![CaseInfoDisplayColumnOptions](images/CaseInfoDisplayColumnOptions.gif)

Available Fields

This folder view contains all the fields available for addition to the respective case information display. You may select several entries from this list by holding down the Shift and Control keys. Hold down the control key to select several individual fields. Hold down the Shift key to select all fields between two successive mouse clicks. You may then add multiple fields to the Shown fields (see **Add-\>** below). Fields are generally organized into folder, so make use of the **Find Field** button if you have trouble finding the field you're looking for.

Note: when the mouse hovers over a field, a hint appears giving a longer description of the field.

**Find Field**

Click this button to search through the list of fields using wild card search.

**Expand and Collapse**

Click these button to expand or collapse the folder view showing all the available fields.

Show Variable Names 

When this box is checked, the variable name corresponding to each column heading will be displayed in the list of available fields alongside the appropriate column heading.

Green, Red, and Blue dots

Also note that fields that the Green, Red, and Blue dots next to each string represents what type of value it is. Also, fields that are shown with gray text in the available field list represent fields that are already shown and in the list on the right.

Show these fields in this order

This list contains the fields which are presently shown on the respective case information display. Not that the field name is representing using backslash \\ characters to signify the folders. You may select several entries from this list by holding down the Shift and Control keys. Hold down the control key to select several individual fields. Hold down the Shift key to select all fields between two successive mouse clicks. You may then remove multiple fields (see **Remove** below) or move the order of fields (see **Move** below).

Note: when the mouse hovers over a field, a hint appears giving a longer description of the field.

Column Width

Enter a new value to adjust the physical width of the column. This will affect all fields selected in the Show these fields list.

Total Digits

The number of digits to use when displaying values in the column (including the decimal point.) This will affect all fields selected in the Show these fields list.

Decimal Places

Number of total digits to the right of the decimal point. This will affect all fields selected in the Show these fields list.

Add \> (Inserting Columns)

Click the **Add \>** button to add all selected available fields to the end of the Show these fields list. You may also click on the selected Available fields and drag and drop the field on the Show these fields list. When drag/dropping the fields, all selected fields will be inserted just before the field that the mouse is over when you drop the fields. Once you have added fields you may then utilize the

\< Remove (Removing Columns) 

Click the **\< Remove** button to remove the fields that are currently selected in the Show these fields list. You may also click on the selected fields in the Show these fields list and drag and drop the fields on the Available fields.

Move Up, Move Down (Moving Columns)

If you selected a block of fields in the Show these fields list, you may change the order of the list by clicking on the **Move Up** or **Move Down** button. You can also move the selection by left-clicking and dragging to move the columns around.

Also note that if you hold the CTRL key down and then left-click and drag a column heading on the case information display, you can move the columns around relative to one another. You will see red highlighting in the column headings to indicate the position to which the field is being moved.

Highlight Key Fields

Checking this option will highlight the *key fields* for the type of object displayed in the case information display presently being modified. The fields highlighted in Yellow in the two lists are either the Primary key fields (numbered) or the Secondary key fields (lettered). Note that some key fields, usually the Circuit ID, are both numbered and lettered, meaning they are used as both Primary or Secondary key fields. Either ALL numbered key fields OR all lettered key fields must be included in the list of shown columns if you intend to export the data to either Excel or a text file, modify it, and paste it back into Simulator.

The fields highlighted in Green are the fields that would be necessary in Excel or an auxiliary file in order to create NEW objects of the type displayed when pasting from Excel or reading in an auxiliary file. If all of the green highlighted fields are not present in the external source, Simulator will not be able to create new objects that may be defined in that source, and will only paste information for objects that already exist in the present case.

Frozen Columns

The number of columns that are fixed and do not scroll when you scroll left or right in the display. Frozen columns will have a background color of gray instead of white. The number of frozen columns is 1 by default.

Data View Layouts Added in Version 20

Added in Version 20 Data View Layouts provides a location to modify how the fielssds in this particular case information display will be rendered when shown on the [Data View](08-view-case-data-tools.md#data-view). For more information about where a data view can be accessed see the help documentation on data views. This is the location where you can edit where any Tab, Row, or Column breaks occur on the [Data View](08-view-case-data-tools.md#data-view).

![CaseInfoDisplayColumnOptionsDataViewLayout](images/CaseInfoDisplayColumnOptionsDataViewLayout.png)

Display Options

Use Area / Zone Filters

Check this box to restrict the case information display’s record set to cover only those areas and zones specified by the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). If this box is unchecked, all records, regardless of zone or area, will be displayed. (The area/zone filters option obviously does not apply to the Area/Zone Filters information display.)

Advanced Filter

Clicking this button will open the [Advanced Filters Dialog](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog), which will allow more detailed filtering on the display.

Zoom

You can zoom in and out on a case information display by using the keyboard short cut Ctrl+Up and Ctrl+Down. Alternatively you can zoom in out by setting a percentage on this dialog. This can also by modified under the Options Menu of the [Case Information Toolbar](#case-information-toolbar).

You can also zoom in and out on case information displays by CTRL key down and using the Mouse Wheel up and down. Added in Version 23, build on May 7, 2024

Use Custom Font / Row Height

If checked, then the Row Height and Custom Font specifications will be used. Changing either the Row Height or Custom Font properties will cause this box to become checked automatically. If you wish not to apply your custom specifications to the active case information display, uncheck this box; the default font and row height settings, as defined under the *Case Information Displays* tab of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog box or under the Options Menu of the [Case Information Toolbar](#case-information-toolbar), will be reapplied.

Row Height

Defines the height of the rows of the case information display.

Change Custom Font

Defines the font with which to display the records.

Set as Default

Sets the current Font and Row Height as the defaults.

Auto Size all Column Widths

Constrains all field widths to contain the widest data elements in each column.

---

<a id="custom-field-descriptions"></a>

## Custom Field Descriptions

*Source: [`Content/MainDocumentation_HTML/Custom_Field_Descriptions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Field_Descriptions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Custom Field Descriptions allow specification of custom floating point, integer, and string fields with user-defined column headers and field names. These fields can be added to [case information displays](#case-information-displays) for all power system case data and many supporting data types. Custom fields are currently not available for use with case information displays listing display objects. By default, there are five custom fields of each type available, but any number of each type of field can be defined for each type of data. In addition the default number of fields to have for all objects can also be changed.

To view the Custom Field Descriptions, open **Custom Field Descriptions** found under the **Case Information and Auxiliary** folder on the [Model Explorer](#model-explorer). The table lists the object types for which custom fields have been defined, how many of each type of field has been defined, and any custom field captions and headers for the fields. By default, there will be three entries; there are two fields each for floating point, integer, and string fields for all data types. These defaults will be used unless specific custom fields are defined for a particular data type.

To insert a new description, select **Records \> Insert** from the case information toolbar. To modify an existing description, choose **Show Dialog** from the case information toolbar. Performing either of these actions will open the [Custom Field Description dialog](#custom-field-descriptions-dialog). To remove and existing description, choose **Records \> Delete**. *Default* descriptions cannot be removed.

The following fields are used for defining the custom field descriptions:

Object Type

Type of object for which the field is available. The *Default* type will be used for any data type that does not have its own definition. This field can only be set using the [Custom Field Description dialog](#custom-field-descriptions-dialog) and cannot be changed once a description has been created.

Field Type

The three options for this field are Floating Point, Integer, and String. This is the type of value that will be used in the custom field. This field can only be set on the [Custom Field Description dialog](#custom-field-descriptions-dialog) when inserting a new custom field description.

Number of Type

This value determines how many fields of the particular Field Type will be available.

Captions for Field (comma-separated)

Specify the caption to use for each field. These captions will appear in lists of fields for objects such as the list of available fields used with [Display/Column options](#configuring-the-case-information-displays). Enter the captions as a comma-separated list. Leave an empty entry to not assign a particular caption. If a caption is not defined for a particular field, the default will be used. For example, if the Field Type is Integer and there are two fields defined, the Field Captions will be *Integer 1* and *Integer 2*.

If captions are not defined for the fields and Captions for Headers are defined, the header captions will be used instead of the defaults.

Captions for Header (comma-separated)

Specify the caption to use for each field column header. These headers appear in the case information displays for the particular object type. Enter the captions as a comma-separated list. Leave an empty entry to not assign a particular caption. If a header caption is not defined for a particular field, the default will be used. For example, if the Field Type is Integer and there are two fields defined, the Header Captions will be *Cust Int 1* and *Cust Int 2*.

If captions are not defined for the headers and Captions for Field are defined, the field captions will be used instead of the defaults.

Include in Difference (comma-separated)Added in Version 22

Specify YES/NO as whether to include this particular custom field (for the chosen object type) when in Difference or Change mode. These headers appear in the case information displays for the particular object type. Enter this as a comma-separated list. Leave an blank value to assign it as YES. Also, values not assigned will be internally interpreted as YES.

Only fields assigned as NO will be not included while in Difference or Change mode, and their present value will be displayed. Otherwise fields will be included, and a difference or change value will be shown.

Auxiliary File Script commands

There are two Auxiliary File Script commands that can be used to edit the Custom Field descriptions for a particular ObjectType/FieldType/Location

CustomFieldDescriptionModify(ObjectType, CustomType, Location, FieldString, HeaderString, IncludeInDiff);

CustomFieldDescriptionAppend(ObjectType, CustomType, FieldString, HeaderString, IncludeInDiff);

For more help on these see [Auxiliary File Format Description document](https://www.powerworld.com/WebHelp/Content/Other_Documents/Auxiliary-File-Format.pdf)

---

<a id="custom-field-descriptions-dialog"></a>

## Custom Field Descriptions Dialog

*Source: [`Content/MainDocumentation_HTML/Custom_Field_Descriptions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Field_Descriptions_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Custom Field Description Dialog is used to create and modify custom field descriptions for a selected object type. This dialog can be accessed from the [Custom Field Descriptions display](#custom-field-descriptions) when inserting a new description by selecting **Records \> Insert** or modifying an existing description by selecting **Show Dialog**.

![Custom Field Descriptions Dialog](images/Custom_Field_Descriptions_Dialog.jpg)

Object Name

Type of object for which the field is available. Select the type from the drop-down list or use the Find button to search through a list of available types. This field can only be set when creating a new description and cannot be changed once a description has been created.

Field Type

The three options for this field are Floating Point, Integer, and String. This is the type of value that will be used in the custom field. This field can only be set when inserting a new custom field description and cannot be changed once a description has been created.

Number of Type

This value determines how many fields of the particular Field Type will be available.

Clear Captions

Click this button to clear out any previously defined captions.

Field Captions

Specify the caption to use for each field. These captions will appear in lists of fields for objects such as the list of available fields used with [Display/Column options](#configuring-the-case-information-displays). If a caption is not defined for a particular field, the default will be used. For example, if the Field Type is Integer and there are two fields defined, the Field Captions will be *Integer 1* and *Integer 2*. 

If captions are not defined for the fields and Header Captions are defined, the header captions will be used instead of the defaults.

Header Captions

Specify the caption to use for each field column header. These headers appear in the case information displays for the particular object type. If a header caption is not defined for a particular field, the default will be used. For example, if the Field Type is Integer and there are two fields defined, the Header Captions will be *Cust Int 1* and *Cust Int 2*. 

If captions are not defined for the headers and Captions for Field are defined, the field captions will be used instead of the defaults.

Include in DifferenceAdded in Version 22

Specify YES/NO as whether to include this particular custom field (for the chosen object type) when in Difference or Change mode. These headers appear in the case information displays for the particular object type. Enter this as a comma-separated list. Leave an blank value to assign it as YES. Also, values not assigned will be internally interpreted as YES.

Only fields assigned as NO will be not included while in Difference or Change mode, and their present value will be displayed. Otherwise fields will be included, and a difference or change value will be shown.

OK, Cancel

Click OK to accept the changes and close the dialog or Cancel to ignore the changes and close the dialog.

---

<a id="custom-field-toggle-choices"></a>

## Custom Field Toggle Choices

*Source: [`Content/MainDocumentation_HTML/Custom_Field_Toggle_Choices.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Field_Toggle_Choices.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

\[Added in Version 21, build on December 16, 2019\]

For objects that have custom strings, integers or floating point numbers defined, the user may specify a list of toggle choices for a particular [custom fields](#custom-field-descriptions). This is done by defining CustomFieldToggleChoice objects

To view the Custom Field Toggle Choices, open **Custom Field Toggle Choices** found under the **Case Information and Auxiliary** folder on the [Model Explorer](#model-explorer). The table lists the object types for which custom field toggle choices have been defined. In addition, they can also be defined to the Toggle Choices tab on the [Custom Field Description Dialog](#custom-field-descriptions-dialog)

To insert a new toggle choice, select **Records \> Insert** from the case information toolbar. This will display a dialog asking you to choose and Object Type and a field to which you would like to add a toggle choice. After choosing this, a CustomFieldToggleChoice will be created with an Order one larger than the present maximum order and a default Choice string will be set. The should then edit the Order and the Choice fields as desired.

To modify an existing toggle choice, choose **Show Dialog** from the case information toolbar. This will open the [Custom Field Description dialog](#custom-field-descriptions-dialog) and take you to the Toggle Tab listing all the present CustomFieldToggleChoices for the object type and variable name chosen.

Once Toggle choices for a custom field have been defined, the user interface will treat this field as a [Toggleable field](#colors-and-cell-styles). It is possible that a custom field has been set for an object <span class="underline">before</span> CustomFieldToggleChoices have been defined. In this situation the field may not match one of the CustomFieldToggleChoices that are defined. When this happens, PowerWorld <span class="underline">will not enforce any correction</span>. PowerWorld only enforces the restriction on a toggle choice when it is being entered. The following rules will be applied when editing a custom field for which custom toggle choices have been defined.

  - When editing any custom integer, float, or string, an entry of blank is always permitted and will result in that custom field being set to blank (meaning not defined). This will be done regardless of whether a Toggle Choice of blank has been explicitly defined.
  - When editing a custom string field for which toggle choices have been defined, any entry that does not match one of the choices will be ignored and the custom string will not be changed.
  - When editing a custom integer or floating point number field for which toggle choices have been defined, any entry that does not match one of the choices will be set to the toggle choice that is the closest *numerically* to the entry.

CustomFieldToggleChoice objects are defined by the following fields:

Object Type (key field)

Type of object for which this is available. This field can only be set when creating the object.

Variable Name (key field)

This refers to the variable name for which the toggle choice applied. Remember that the variable name is off by one from the field. Thus the first custom string will have a variable name of CustomString:0, the second will be CustomString:1 and so on. This field can also only be set when creating the object

Order (key field)

This is an integer indicating the order precedence for the choices. When shown in a drop-down inside the user interface, choices with lower Order number will be shown before choices with a higher order number.

Choice (required field for creation)

This is the String for the choice that will be displayed. A blank choice can be explicitly defined as a choice and is appropriate to make it clear users may clear out choices. For custom integer choices only strings that represent an integer will be accepted. For floating point choices, only strings that represent a number will be accepted.

---

<a id="calculated-fields"></a>

## Calculated Fields

*Source: [`Content/MainDocumentation_HTML/Calculated_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Calculated_Fields.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Calculated fields provide a means of performing an arithmetic operation (minimum, maximum, sum, average, median, variance, standard deviation, count) on a group of objects based on a selected field. Based on the object type of the group, a calculated field can be added to a [case information display](#case-information-displays) for a given object. The calculated field value that is displayed is then based on the calculated field parameters and how the object type in the calculated field relates to the given object.

For example, suppose that you want to find the largest line flow for all lines connected to a bus. A calculated field can be set up using the branch object type with a selected field of MVA (maximum) and the maximum operation can be performed on this field. This calculated field can then be associated with buses by adding this field to the [bus case information display](05-case-information-displays-by-object-part1.md#bus-display). The resulting values for this field will show the maximum MVA flow for all lines connected to a given bus. When determining the value, only the branches that have a terminal bus the same as the given bus will be considered, and the maximum MVA value for all of those branches will be reported.

Optionally, filters can be associated with calculated fields to further specify what objects should be considered in the calculation.

The calculated fields case information display can be accessed from the [Model Explorer](#model-explorer) under **Case Information and Auxiliary \> Calculated Fields**. Existing calculated fields can be modified by selecting **Show Dialog** from the [case information toolbar](#case-information-toolbar), and new calculated fields can be added by selecting **Records \> Insert** from the case information toolbar. Both actions will open the Calculated Field dialog shown below.

Calculated Field Dialog

![Calculated Field Dialog](images/Calculated_Field_Dialog.gif)

Calculated Field Name

This is the name of the calculated field as it will appear when added to a case information display. Use the **Save**, **Save As**, **Rename**, and **Delete** buttons to create new calculated fields without exiting the dialog. Switch between existing calculated fields by choosing a name from the drop-down box.

Object Type

Type of object that will be included in the calculation. The type of object determines which objects this field can be used with. This information is displayed to the right of the Object Type option.

Field

Select the field to use in the calculation by selecting a field name from the drop-down box or by clicking the Find button to use [advanced search](04-model-explorer-and-case-information-part3.md#find-dialog-basics) options to locate the field. Check the **Use Absolute Value** box to use the absolute value of the field in the operation.

Operation

Select the type of operation to perform on the object fields.

Treat Blank Entries

Depending on the field selected, some objects may not have entries. Select to either treat these blank entries **As zeros** or to **Ignore** them in the calculation.

Objects to be included in the operation

This option determines if **All** objects of the selected type will be included in the calculation or if they will be filtered by **Only objects that meet the filter below**.

If choosing to apply a filter, the filter can be defined by using the same options available when defining an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog). The **Set Filter Same As** button can be used to select an existing [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) whose actions should be applied to this filter.

Keep in mind that objects included in the calculation will first be determined by the object type. If for example branch is selected, then all branches will be considered. Setting a filter will limit the branches to only those branches that meet the filter. If the calculated field is used with buses, then the branches considered for a given bus will be only those branches that have a terminal bus the same as the given bus. If the calculated field is used with generators, then the branches considered for a given generator will be only those branches that have a terminal bus the same as the terminal bus of the given generator.

---

<a id="case-information-customizations-display"></a>

## Case Information Customizations Display

*Source: [`Content/MainDocumentation_HTML/Case_Information_Customizations_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Customizations_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open the Case Information Customizations display, select **Case Information and Auxiliary** **\>** **Case Info Customizations** from the [Model Explorer](#model-explorer). If you have customized any of the case information displays for your case, you can see a list of the customized displays and their settings from this display.

Case Information Customization settings cannot be inserted manually or modified on this display. Those modifications must be done on the actual case information display. The primary use of this list display is to provide you a location to save and load case information customizations to an auxiliary file. Customizations can be loaded from an auxiliary file by right-clicking on the grid and choosing to load data from an auxiliary file. To save the customizations, right-click on this display and select **Save As \> Auxiliary Data**.

---

<a id="local-menu-options"></a>

## Local Menu Options

*Source: [`Content/MainDocumentation_HTML/case_information_displays_local_menu_options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/case_information_displays_local_menu_options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

All case information displays have a set of local menu options. The local menu can be brought up at any time by right clicking on case information display. Most of the actions and options available in the local menu are identical to the options available in the [Case Information Toolbar.](#case-information-toolbar) This is depicted in the figure below.

![Model Explorer Drop Down](images/Model_Explorer_Drop_Down.gif)

For help on most of the actions and options available in the local menu, please see the [Case Information Toolbar](#case-information-toolbar) help. The other options that are also sometimes available on the right-click menu however are listed below.

Why is this field or line disabled?

This option will display a message showing the reason why the field is disabled. This option will be enabled only if the field is actually disabled.

Help

Display context-sensitive help for the case-information display.

Form Control

This menu option allows to control the case information display.

Print

You can print the contents of most of the case information displays by selecting Print from the local menu.

Close

Closes the case information display.

Make Top Left of Form Visible

Makes the top or the left of the case information display visible, if either the top or the left are not visible.

Shift Form Up

Moves the case information display up so the bottom of the case information display can be visible.

Maximize

Maximizes the size of the case information display.

Unmaximize (Restore)

Restores the size of the case information display.

Minimize

Minimizes the size of the case information display.

---

<a id="colors-and-cell-styles"></a>

## Colors and Cell Styles

*Source: [`Content/MainDocumentation_HTML/Case_Information_Displays_Colors_and_Cell_Styles.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Displays_Colors_and_Cell_Styles.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The case information displays distinguish data field types by text color and cell style. Most of the entries on the case information display are colored using the following color convention. These colors can be customized using the Case Information Displays tab on the[Simulation Options Display](10-power-flow-solution-and-options-part1.md#simulator-options), which can be invoked by selecting ** Simulator Options** from the **Case Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab. **Simulator Options** is also available on the [Tools](02-simulator-ribbon.md#tools-tab-overview) and [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tabs.

There are three types of data fields:

**Standard Fields** Fields that cannot be modified directly from the case information display are colored black by default.

**Enterable Fields** Fields that can be modified are colored navy blue by default. When selected, a cell containing an enterable field will display a tiny filled square in its bottom right corner. This box is called a cell.

**Toggleable Fields** Fields whose values can be toggled are colored green by default. The values contained in toggleable fields are modified by double left-clicking on them or selecting the possible entries from the drop-down or dialog that becomes available when single left-clicking on the field. Like cells in enterable fields, cells in toggleable fields display a cell handle when selected.

Besides indicating field type, color coding is also used to highlight violations of branch flow, generator MW or MVR output, and bus voltage constraints. Fields that are either at a limit or violating a limit are colored red by default. This, too, is configurable from the Case Information Displays tab on [Simulation Options Display](10-power-flow-solution-and-options-part1.md#simulator-options).

---

<a id="using-cell-handles"></a>

## Using Cell Handles

*Source: [`Content/MainDocumentation_HTML/Case_Information_Displays_Using_Cell_Handles.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Displays_Using_Cell_Handles.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When selected, cells corresponding to enterable and toggleable fields exhibit a small filled square in their bottom right corner called a cell handle. The cell handle may be used to propagate the value of the selected cell to other cells in the same field.

Suppose we have selected a toggleable or enterable cell and that we wish to copy its value to other records. Call this cell the *source cell* and its value the *source value*. To copy the source value to another record or records, perform the following steps:

  - Drag the mouse onto the cell handle until the pointer becomes a crosshair.
  - With the mouse pointer showing as a crosshair, click and hold the left mouse button.
  - With the left mouse button depressed, drag the mouse up or down from the source cell to select a group of records to which to copy the source value. These destination cells will display a yellow background when selected in this manner.
  - When you have finished selecting the destination cells, release the left mouse button.
  - A message box will appear asking whether you want to change the values of the destination cells to the source value. Answer Yes to complete the copy.

---

<a id="sorting-records"></a>

## Sorting Records

*Source: [`Content/MainDocumentation_HTML/Case_Information_Display_sorting_records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Display_sorting_records.htm)*

You can sort the entries on the case information displays by just about any field. To sort the records by a particular column, left-click on the column’s heading. Left-click the column’s heading again to reverse the sort order.

To sort the records by the absolute value of a field, hold down the shift key as you left-click on the field’s heading.

Simulator also has a more advanced sorting tool, which can be accessed by selecting **Advanced Sort** from the [local menu](#local-menu-options). Advanced sort allows you to sort information based on values in more than one column of data. Advanced sort also allows you to sort based on the absolute value of numerical fields and by case sensitivity for string fields.

The Advanced Sorting dialog lets you sort by any value. A check box option to **Maintain Selected Row in View** was added in the May 8, 2023 patch of Version 23

---

<a id="finding-records"></a>

## Finding Records

*Source: [`Content/MainDocumentation_HTML/Case_Information_Display_Finding_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Display_Finding_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Find Dialog is used to find the device of the specified type on the different Case Information displays. The Find Dialog is available on most case information displays from the local menu, which can be invoked by right-clicking in the grid.

Different Find dialogs exist for Areas, Buses, Interfaces, Lines and Zones. Note that the Bus Dialog is used to locate all bus objects, such as generators, loads, switched shunts and the bus itself. In general, the format of each dialog is similar, allowing you to find the desired object using either its number or name. The only exception is interfaces, for which no name is defined. The basics of the Find dialog are explained in the [Find Dialog Basics](04-model-explorer-and-case-information-part3.md#find-dialog-basics) help topic.

---

<a id="saving-case-information-display-contents-as-html-tables"></a>

## Saving Case Information Display Contents As HTML Tables

*Source: [`Content/MainDocumentation_HTML/Saving_Case_Information_Display_Contents_As_HTML_Tables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Case_Information_Display_Contents_As_HTML_Tables.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator's [Case Information Displays](#case-information-displays) allow you to save their contents as HTML tables for display on the world-wide web. To do this, right-click on any row of the table and select **Save As HTML** from the resulting local menu. This brings up the [Table Format Dialog](#html-table-format-dialog). Set the various table formatting options and click **OK**. Then, select the name of the file to which to save the HTML code. Finally, if a region of the table was selected, you will be asked if you want to save just the selected region as HTML. Indicate **Yes** to convert just the selected portion of the table, or click **No** to write the entire table as HTML.

---

<a id="html-table-format-dialog"></a>

## HTML Table Format Dialog

*Source: [`Content/MainDocumentation_HTML/html_table_format_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/html_table_format_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Table Format Dialog allows you to set various formatting options for HTML tables. This form is invoked when you try to save a [Case Information Displays](#case-information-displays) as HTML.

The Table Format Dialog is divided into two tabs, **Table Properties** and **Table Elements**.

Table Properties

This tab allows you to specify values for options that govern the appearance of the table as a whole. Here you can specify the following properties:

**Border Weight**

The thickness of the border to draw around each cell. Specify 0 to suppress the drawing of a cell border.

**Horizontal Cell Spacing**

The spacing to employ between cells that neighbor each other horizontally.

**Vertical Cell Spacing**

The spacing to employ between cells that neighbor each other vertically.

**Table Width**

The width of the table. If the Percent checkbox is checked, the width specifies the horizontal dimension of the table relative to the object that contains it on the screen.

**Caption**

The table title that will be printed directly above it on the web page.

Table Elements

These options control how the data will be centered in each cell. Choices include:

**Horizontal Alignment**

Controls how the text in each cell should be positioned horizontally. The default value is Left, but you may also choose to center or right-justify the data in each cell.

**Vertical Alignment**

Controls how the text in each cell should be positioned vertically. The default value is Middle, but you may also choose to align the text with the top or bottom edges of the cell.

If any of the numeric entries (Border Weight, Horizontal Cell Spacing, Vertical Cell Spacing, Table Width) are left blank or zero, your browser will employ its default settings for these values in rendering the table on the screen.

---

<a id="case-information-toolbar"></a>

## Case Information Toolbar

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Directly above most case information displays , the Case Information Toolbar provides easy access to many [Case Information Display](#case-information-displays) options for formatting and customizing a list display. Note that all of the options are also available from the [right-click local menu](#local-menu-options) on the case information display as well.

![Model Explorer Case Info Toolbar](images/Model_Explorer_Case_Info_Toolbar.gif)

![Model Explorer Case Info Toolbar Show Dialog](images/Model_Explorer_Case_Info_Toolbar_Show_Dialog.gif)Show Dialog

Selecting the Show Dialog option will invoke a dialog box containing more detailed information and settings regarding the corresponding system object. For example, clicking Show Dialog while a Bus Case Information Display is the active window opens the [Bus Information Dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog).

![Model Explorer Case Info Toolbar Data View](images/Model_Explorer_Case_Info_Toolbar_Data_View.png)Show Data View Added in Version 20

Selecting the Show Data View will invoke the Data View dialog box containing information about the object in the selected row. See [Data View](08-view-case-data-tools.md#data-view) for more details

![Model Explorer Case Info Toolbar Display Options](images/Model_Explorer_Case_Info_Toolbar_Display_Options.gif)Display/Column Options

The contents and format of the information display can be controlled using the Case Information Display Dialog. See [Configuring the Case Information Displays](#configuring-the-case-information-displays) for more details.

![Model Explorer Case Info Toolbar Auto Width](images/Model_Explorer_Case_Info_Toolbar_Auto_Width.gif)Auto Size all Column Widths

Constrains all field widths to contain the widest data elements in each column.

![Model Explorer Case Info Toolbar Increase](images/Model_Explorer_Case_Info_Toolbar_Increase.gif) ![Model Explorer Case Info Toolbar Decrease](images/Model_Explorer_Case_Info_Toolbar_Decrease.gif)Increase/Decrease Decimals

Adjusts the number of displayed decimal places for all cells in the selected column in a case information display.

![Model Explorer Case Info Toolbar Find](images/Model_Explorer_Case_Info_Toolbar_Find.gif)Find

Use the Find local menu option to retrieve a record pertaining to a particular element. Choosing Find from toolbar opens the [Find Dialog Box](#finding-records)**,** which is used to find records pertaining to an element identified by either number or name.

![Model Explorer Case Info Toolbar Search](images/Model_Explorer_Case_Info_Toolbar_Search.gif)Search

Invokes the [Search for Text](04-model-explorer-and-case-information-part3.md#search-for-text-dialog) dialog; allows you to search for specific text in a case information display.

![Model Explorer Case Info Toolbar Bus View](images/Model_Explorer_Case_Info_Toolbar_Bus_View.gif)Bus View Oneline

On many case information displays click this button to open the [Bus View Oneline](08-view-case-data-tools.md#bus-view-display) to the bus related to the presently active cell of the case information display.

[![Model Explorer Case Info Toolbar Records](images/Model_Explorer_Case_Info_Toolbar_Records.gif)](#records-menu)Records Menu

The Records Menu contains actions that apply to the specific kinds of records displayed in the active case information display. [Expressions](04-model-explorer-and-case-information-part2.md#expressions), [Bus View Oneline](08-view-case-data-tools.md#bus-view-display), [Substation View Oneline](08-view-case-data-tools.md#substation-view-display), [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and are always shown in this drop-down. For more details see the [Case Information Toolbar: Records Menu](#records-menu) Help.

[![Model Explorer Case Info Toolbar Geo Data](images/Model_Explorer_Case_Info_Toolbar_Geo_Data.gif)](#geo-data-view-menu)Geo Data View Menu

The Geo Menu is only available on case information displays that show records related to the network model. For more details see the [Case Information Toolbar: Geo Data Menu Help](#geo-data-view-menu).

[![Model Explorer Case Info Toolbar SetColumns](images/Model_Explorer_Case_Info_Toolbar_SetColumns.gif)](#set-toggle-and-columns-menus)Set and Columns Menu

Set contains actions for setting data or toggling data.

Columns contains actions that act on the column such as [Get Column Metrics](04-model-explorer-and-case-information-part3.md#grid-metrics-dialog). For more details see the [Case Information Toolbar: Set, Toggle, and Column Menu Help](#set-toggle-and-columns-menus).

[![Model Explorer Case Info Toolbar CopyPaste](images/Model_Explorer_Case_Info_Toolbar_CopyPaste.gif)](#copy-paste-and-send-menu)Copy, Paste and Send Menu

The Copy, Paste and Send Menu contains actions that copy and paste data through the Windows Clipboard. In addition it contains actions that send data directly to spreadsheet software such as Microsoft Excel or Open Office Calc. For more details see the [Case Information Toolbar: Copy, Paste, and Send Menu](#copy-paste-and-send-menu) Help.

[![Model Explorer Case Info Toolbar SaveAux](images/Model_Explorer_Case_Info_Toolbar_SaveAux.gif)](#save-auxiliary-files-menu)Save Auxiliary Menu

The Save Auxiliary Drop-Down contains actions that save data in the case information display to various formats. The [Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux) and Comma-Separated-Value (CSV) formats are always available, but some records show other more specific formats. For more details see the [Case Information Toolbar Save Auxiliary Files Menu](#save-auxiliary-files-menu) Help.

[![Model Explorer Case Info Toolbar LoadAux](images/Model_Explorer_Case_Info_Toolbar_LoadAux.gif)](#load-auxiliary-files-menu)Load Auxiliary Menu

The Load Auxiliary Drop-Down contains actions that load data records related to the active case information display. The [Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux) and Comma-Separated-Value (CSV) formats are always available, but some records show other more record-specific formats. For more details see the [Case Information Toolbar: Load Auxiliary Files Menu](#load-auxiliary-files-menu) Help.

![Model Explorer Case Info Toolbar AreaZone Filter](images/Model_Explorer_Case_Info_Toolbar_AreaZone_Filter.gif)Area/Zone/Owner Filters   

Opens the [Area/Zone/Owner Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) display which allows filtering of the case information displays by Area, Zone, and Owner.

[![Model Explorer Case Info Toolbar Filtering](images/Model_Explorer_Case_Info_Toolbar_Filtering.gif)](#filtering-menu)Filtering Menu

The Filtering Drop contains actions related to filtering the records shown in the active case information display. For more details see the [Case Information Toolbar: Filtering Menu](#filtering-menu) Help.

![Model Explorer Case Info Toolbar Sort](images/Model_Explorer_Case_Info_Toolbar_Sort.gif) Advanced Sort

Allows the user to custom sort the information in the display based on desired criteria. See [Case Information Display: Sorting Records](#sorting-records) for more information.

![Model Explorer Case Info Toolbar Expressions](images/Model_Explorer_Case_Info_Toolbar_Expressions.gif)Expressions Menu

The Expressions Menu allows you to edit [Expressions](04-model-explorer-and-case-information-part2.md#expressions),and [String Expressions](04-model-explorer-and-case-information-part2.md#string-expressions).

![Model Explorer Case Info Toolbar Refresh](images/Model_Explorer_Case_Info_Toolbar_Refresh.gif)Refresh Display

Select this option to update the currently displayed data to match the present state of the system.

![Model Explorer Case Info Toolbar Options](images/Model_Explorer_Case_Info_Toolbar_Options.gif)Options Menu

Invokes a drop down menu similar to the Case Information Display options dialog. See [Case Information Display Options](10-power-flow-solution-and-options-part2.md#case-information-display-options) for more details.

> Display/Column Options
> 
> This is the same as clicking on ![Model Explorer Case Info Toolbar Display Options](images/Model_Explorer_Case_Info_Toolbar_Display_Options.gif) Display/Column Options.
> 
> Headings
> 
> This option allows you to choose whether the column headings of the case information displays are the *Normal* column headings or are the *Variable Names* of the type of data stored in each column. Variable names are the strings used when writing data out to an [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux). Change the headings to variable names can be helpful when looking at or creating auxiliary files.
> 
> This option applies to all case information displays.
> 
> When viewing the heading by *Variable Names* there are special characters that are included in parentheses after the variable names. More than one special character can be included with each heading.
> 
>   - **1**,**2**, or **3** - this is a primary key field
>   - **A**, **B**, or **C** - this is a secondary key field
>   - **\*** - this is a required field
>   - **\<** - this is a field that is included in the [Difference Case](08-view-case-data-tools.md#difference-case) tool comparison. This indicator is still a work in progress. Only bus and generator case information displays fully support this.
> 
> Show Grid Lines 
> 
> Grid lines are shown by default in case information displays. Unchecking this box will remove the grid lines from the displays.
> 
> This option applies to all case information displays.
> 
> Show Header Hints
> 
> This option allows the hints for the current field to be displayed when moving the cursor over the column heading.
> 
> This option applies to all case information displays.
> 
> Word Wrap Headings
> 
> Check this box to wrap the heading column text, breaking it in several rows to fit the current column width. If unchecked, the column heading text will be displayed in only one row.
> 
> This option applies to all case information displays.
> 
> Default Row Height
> 
> This sets the row height for all case information displays.
> 
> Highlight Row if Selected Field = YES 
> 
> Check this option to automatically highlight all case information rows that represent a model object that has its **Selected** field set to YES. The row will then be highlighted using the color specified on this dialog. This option will apply to all case information displays representing all types of objects.
> 
> This option applies to all case information displays.
> 
> Zoom
> 
> Set the zoom percentage of the text in the case information display.
> 
> This option only applies to the present case information display.
> 
> Remove Trailing Zeros
> 
> To make the data more concise, this will remove any zeros at the end of numbers in all fields.
> 
> This option only applies to the present case information display.
> 
> Key Fields
> 
> Various fields can identify objects by different key fields. This dropdown allows easy switching between the different key field options. This also affects the key fields that are used when storing SUBDATA in auxiliary files.
> 
> This option applies to all case information displays.
> 
> Use Concise Variable Names and Headers
> 
> Added in Version 19
> 
> Variable names within Simulator have been overhauled starting Version 19. This is described in more detail in the [PowerWorld Object Variables help topic](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). This option must be chosen to use the more concise variable names when looking at field variable names in the user interface or when writing out to an Auxiliary File. If this option is not chosen then the legacy variable names will be used.
> 
> In addition, a new [Concise Auxiliary File (AUX) header](03-cases-files-and-formats.md#auxiliary-file-format-aux) is available when writing out AUX files. This option must be chosen to write out Auxiliary Files using the new concise format.
> 
> Use Data Maintainer Filtering
> 
> Added in October 17, 2017 patch of Version 20
> 
> Check this option so that Data Maintainer filtering is applied in addition to the Area/Zone/Owner Filtering.
> 
> Show Column Metric as Hints
> 
> Added in May 11, 2016 patch of Version 19
> 
> Under the Columns menu, the [Get Column Metrics](04-model-explorer-and-case-information-part3.md#grid-metrics-dialog) button brings up a dialog showing you the statistical metrics of what has been selected. By choosing this option, a hint window will also automatically appear when hovering your mouse over a selection.
> 
> Use Abs Value in Column Metric Hints
> 
> Check to use absolute values in calculation of the hint window column metrics.
> 
> Column Metrics Treat Blanks
> 
> Check to treat blanks as zeros in the calculation of the hint window column metrics.

---

<a id="copy-paste-and-send-menu"></a>

## Copy, Paste and Send Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_CopyPaste.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_CopyPaste.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Case Information Toolbar](#case-information-toolbar) Copy, Paste and Send Menu displays the identical options as shown in the Copy/Paste/Send menu of the [case information display local menu](#local-menu-options). This is depicted in the figure below. The options are described below the figure.

![Model Explorer Drop Down Copy Paste](images/Model_Explorer_Drop_Down_Copy_Paste.gif)

Paste

Select Paste from the local menu to copy a record set from the Windows clipboard into the case information display. See [Copying Simulator Data to and from Other Applications](04-model-explorer-and-case-information-part3.md#copying-simulator-data-to-and-from-other-applications) for more details.

Copy Selection

The Copy Selection menu option copies the records selected in the case information display to the Windows clipboard, from which the selection can be copied into other programs such as Microsoft Excel for further analysis. See [Copying Simulator Data to and from Other Applications](04-model-explorer-and-case-information-part3.md#copying-simulator-data-to-and-from-other-applications) for more details.

Copy All

The Copy All menu option copies the entire record set contained in the case information display to the Windows clipboard, from which it can be copied into other programs such as Excel for further analysis. See [Copying Simulator Data to and from Other Applications](04-model-explorer-and-case-information-part3.md#copying-simulator-data-to-and-from-other-applications) for more details.

Copy / Send Special

The Copy / Send Special menu option will open the a dialog that allows the user to set a few custom options before completing the data copy. The user can choose to copy all or a selection, and to copy the data either to the Windows clipboard or send it directly to Excel. Also, you can choose to copy or send the transpose. In addition, the user can choose whether to use the normal column headings or variable names (see the list of fields in [Data Argument List for Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux)) as column identifiers. Lastly, the user can specify whether or not to include a row containing the type of object the data represents (Object Name) and a row containing the column headers for each column of data. Note that for pasting the information back into Simulator, the Object Name and Column Heading rows must be contained with the data to be pasted. If you have changed the settings on this dialog and wish to make them the case default settings, click on the Make Default for all Copy Actions button.  

Send All to Excel (or to Open Office Calc)

The Send All to Excel menu option copies the entire record set contained in the case information display and automatically sends it to Excel. The first time this option is selected, Simulator will start a new instance of Excel on your machine and paste the data on the first sheet. Subsequent calls to Send to Excel will continue to add sheets and paste data to this instance of Excel, until the Excel instance is closed manually by the user. This functionality works identically for the Open Office Calc spreadsheet as well.

Send Selection to Excel (or to Open Office Calc)

The Send Selection to Excel menu option copies the selected record set in the case information display and automatically sends it to Excel. The first time this option is selected, Simulator will start a new instance of Excel on your machine and paste the data on the first sheet. Subsequent calls to Send to Excel will continue to add sheets and paste data to this instance of Excel, until the Excel instance is closed manually by the user.This functionality works identically for the Open Office Calc spreadsheet as well.

Note: When Choosong to *Send To Excel*, previously Simulator split exports of more than 256 columns into separate sheets in an Excel Workbook. For Excel versions 2007 and later, it will now only do this when the export have more than 16,384 columns.

---

<a id="filtering-menu"></a>

## Filtering Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_Filter.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_Filter.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Filtering Menu, contained on the [Case Information Toolbar](#case-information-toolbar), gives access to several options regarding any [Advanced Filters](04-model-explorer-and-case-information-part2.md#advanced-filtering) that can be applied to the active case information display. In addition it provides access to the [Area/Zone/Owner Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). The drop-down menu is shown in the following figure.

![Model Explorer Drop Down Filter](images/Model_Explorer_Drop_Down_Filter.gif)

The top of the menu has four primary buttons that appear on all case information displays. These four are as follows

> Advanced Filter
> 
> Allows the user to custom filter the information in the display based on desired criteria. See [Advanced Filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) for more information.
> 
>  Use Area/Zone/Owner Filters 
> 
> Filters displayed records by selections made on the [Area/Zone/Owner/DataMaintainer Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) display.
> 
> Area/Zone/Owner Filters
> 
> Opens the [Area/Zone/Owner/DataMaintainer Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) display for setting the areas, zones or owners for which the filter should apply.
> 
> Remove Filter
> 
> Click this button to remove the Advanced Filter from the present case information display. This does not delete the Advanced Filter definition, but only removes the reference to it from the active case information display. The filter can easily to reapplied after removing it. If you would like to permanently delete an Advanced Filter see [Advanced Filtering.](04-model-explorer-and-case-information-part2.md#advanced-filtering)

After the top section of the menu are two sections that may or may not be available for a particular case information display

(List of Filters)

This contains a list of advanced filters for the object type displayed in the active case information display. These filters would have already been created using either the [Advanced Filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) dialog or by reading them from an [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux). In the example image above the "50" and "50MW+" entries represent filters that apply to a generator object. If there are more than 10 advanced filters for the present object type, then a submenu will be shown for the object type as well. Also if an advanced filter is presently applied to the case information display, then the active advanced filtered will be denoted with a check mark.

(List of Filters for Related Objects) 

This contains a list of advanced filters whose object type is *related* to the type of record displayed in the active case information display. For example, the case information display shown in the figure above is showing generator records. Generator records allow you to filter the generator object using a Bus, Substation, Area, Zone, or Branch Filter. In the example above there are 5 filters defined for Bus objects (100kV+, 69, exw, jamie, and Loads) which can be used to filter the generator records. For more information on Related Object Filtering, see the [Advanced Filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) dialog. Also if an advanced filter is presently applied to the case information display, then the active advanced filtered will be denoted with a check mark and the object type of that filter will be denoted with a grayed out check mark.

---

<a id="geo-data-view-menu"></a>

## Geo Data View Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_GeoData.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_GeoData.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Geo Menu, found on the [Case Information Toolbar](#case-information-toolbar), contains options related to opening the Geographic Data View Displays based on the objects selected in the case information display. For more information see the help on [Geographic Data Views](04-model-explorer-and-case-information-part3.md#geographic-data-view).

---

<a id="load-auxiliary-files-menu"></a>

## Load Auxiliary Files Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_LoadAux.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_LoadAux.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Case Information Toolbar](#case-information-toolbar) Load Auxiliary Menu displays the identical options as shown in the Load menu of the [case information display local menu](#local-menu-options). This is depicted in the figure below. The options are described below the figure.

![Model Explorer Drop Down Load 840x570](images/Model_Explorer_Drop_Down_Load_840x570.gif)

This option will load the contents of an external file to the case information display.

Auxiliary File (Any Data)

This option allows loading an auxiliary file containing any data.

Multiple auxiliary files can be selected from the open dialog. Files will be loaded in the order in which they are listed in the open dialog.

Auxiliary File (Only *Specific* Data)

This option allows loading an auxiliary file containing only data related to the current case information display.

Multiple auxiliary files can be selected from the open dialog. Files will be loaded in the order in which they are listed in the open dialog.

CSV File (Only *Specific* Data)

This option allows loading a CSV file containing only data related to the current case information display. The CSV file must be in the same format as the data that is sent to Excel using the [Send All to Excel](#copy-paste-and-send-menu) option or when saving a CSV file from the [Save As CSV](#save-auxiliary-files-menu) option on the case information menu.

At the end of the menu, some case information displays show more specific formats that are relevant only for that type of record. For instance in the figure above you can see support for loading in older file formats previously supported.

---

<a id="save-auxiliary-files-menu"></a>

## Save Auxiliary Files Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_SaveAux.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_SaveAux.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Case Information Toolbar](#case-information-toolbar) Save Auxiliary Menu displays the identical options as shown in the Save As menu of the [case information display local menu](#local-menu-options). This is depicted in the figure below. The options are described below the figure.

![Model Explorer Drop Down Save As](images/Model_Explorer_Drop_Down_Save_As.gif)

This option will save the contents of the case information display to an external file. 

Auxiliary File

This option allows saving all the contents of the case information display to an auxiliary file.

Auxiliary File (only selected records)

This option allows saving the selected record set in the case information display to an auxiliary file.

Auxiliary File (only selected records/columns)

This option allows saving the selected record set and the selected columns in the case information display to an auxiliary file.

Auxiliary File with Options

This option allows saving the records with some options. For more information, see [Auxiliary File with Options](52-additional-linked-topics-part1.md#saving-case-information-display-contents-as-html-tables).

Auxiliary File with Options (Last Used)

This option allows saving the records with the same options previously selected from the Auxiliary File with options dialog,.

CSV (Comma Delimited)

This option allows saving all the contents of the case information display to a comma delimited file.

CSV (only selected records/columns)

This option allows saving the selected record set and the selected columns in the case information display to a comma delimited file.

HTML

You can save the entire table or selected records to an HTML file for viewing from an Internet browser. For more information, see [Saving Case Information Display Contents as HTML Tables](#saving-case-information-display-contents-as-html-tables).

Bitmap

This option allows saving the case information display into a Bitmap picture file.

JPeg

This option allows saving the case information display into a JPEG picture file.

GE EPC format (only selected records)

This option allows to save the selected records into GE EPC file format. A pop-up message to question the user it they want to save the bus records when saving an individual shunt, gen or transformer to an EPC file. When saving selected generator records to an EPC file, bus records will also be saved so that the generator setpoint information is available. Also when using the case information display options from a table of switched shunts or transformers to save the records to the GE EPC format we now also save the bus records automatically as well. The EPC format embeds the voltage regulation information for the shunts and transformers in bus records. Saving the bus records additionally helps avoid some confusion.

At the end of the menu, some case information displays show more specific formats that are relevant only for that type of record. For instance in the figure above you can see a specific Auxiliary File format options which automatically saves all the data related to the cost information of the generator.

---

<a id="records-menu"></a>

## Records Menu

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Case Information Toolbar](#case-information-toolbar) Records Menu displays a combination of the Insert/Delete buttons and the Records and Plot menus on the [case information display local menu](#local-menu-options). This is depicted in the figure below. The options are described below the figure.

![Model Explorer Drop Down Records](images/Model_Explorer_Drop_Down_Records.gif)

Insert and Delete

Many records have an Insert and Delete related buttons. These are used for inserting new records and deleting records. Note that some records can only be inserted or deleted in Edit Mode. In such cases the Insert and Delete button will be grayed out when not in Edit Mode.Use the Bus View Oneline local menu option

Records Menu

> Quick Power Flow List 
> 
> Use the Quick Power Flow List local menu option to invoke [Simulator’s Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) tool.
> 
> Bus View Oneline
> 
> Use the Bus View Oneline local menu option to bring up the [Bus View Display](08-view-case-data-tools.md#bus-view-display), which illustrates how the selected bus is connected to the rest of the system.
> 
> Substation View Oneline
> 
> Use the Bus View Oneline local menu option to bring up the [Substation View Display](08-view-case-data-tools.md#substation-view-display), which illustrates how the selected substation is connected to the rest of the system.
> 
> Define Expression 
> 
> Allows you to define [Expressions](04-model-explorer-and-case-information-part2.md#expressions) that are functions of other fields.
> 
> Pan to Object on Open Onelines
> 
> Selecting this option will move the view on any open oneline diagrams to focus on the device clicked in the table, if an object representing the device exists on the diagram.
> 
> Record-Specific Actions
> 
> At the end of the Record Drop-Down will be a list of options that are special for the particular kind of record shown in the active case information display. For example, in the image above for a generator case information display the option "Create Injection Group From Selection..." allows you to create a new injection group containing all of the presently selected generator records.

---

<a id="set-toggle-and-columns-menus"></a>

## Set, Toggle, and Columns Menus

*Source: [`Content/MainDocumentation_HTML/Case_Information_Toolbar_SetColumns.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Toolbar_SetColumns.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Case Information Toolbar](#case-information-toolbar) Set and Columns Menus display the identical options as shown in the Set/Toggle/Columns menu of the [case information display local menu](#local-menu-options). This is depicted in the figure below. The options are described below the figure.

![Model Explorer Drop Down Set Columns](images/Model_Explorer_Drop_Down_Set_Columns.gif)

Toggle

This option will be available for fields that are toggleable. The number and type of options available will change depending on the type of field being toggled. Some fields simply allow toggling between two YES/NO, TRUE/FALSE, or CLOSED/OPEN entries, while others allow a much larger list of choices. The toggle entries on the toolbar menus are used to toggle the field for all records.

Set All Values To

Click on this menu item to bring up a dialog which allows you to set all the values in a column to the same value. For instance you might change all the buses to have an angle of zero degrees.

A special trick that can be used in conjunction with this option is entering a string of the form "@variablename". When entering data into a field, if the string begins with the symbol @, then Simulator will parse the remaining part of the string to see if it matches one of the variable names associated with that type of object. Variable name strings are what are used in the Auxiliary File Format (see the list of fields in [Data Argument List for Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux)). Essentially this trick allows you to copy one column to another column. Using this trick, you could change the set-point voltage of all the generators in the case to be equal to the terminal bus voltage of the generator.

There is also an option on this dialog to choose to **Scale and Shift Numeric Value**, if the column clicked on is a numeric field. (This was added in Version 23, build on May 24, 2023) When choosing this enter a value for the Scale and Shift and the resulting value for the field will be set to OldValue\*Scale + Shift.

 Set All Values To Field

Click on this menu item to bring up a dialog which allows you to select a field of this record type and then set all the values in a column to the this field. For instance you might change all the generator setpoint voltage to be equal to their present regulated bus voltage. This represents a user-interface method of employing the special trick using the "@variablename" string as discussed in the Set All Value To comments above. 

Select Column(s) 

Use this option to quickly select entire columns in the grid. First highlight the cells of a single record for the columns you wish to highlight, and then choose this option to highlight the entire column.

Select Row(s)  

Use this option to quickly select entire columns in the grid. First highlight the cells of a single record for the columns you wish to highlight, and then choose this option to highlight the entire column.

Get Column Metrics 

This option allows you to compute the metrics for the selected column. Choosing Get Column Metrics from the local menu will bring the [Grid Metrics Dialog](04-model-explorer-and-case-information-part3.md#grid-metrics-dialog). This option is only available for columns whose content is numeric.

Contour Column

Use the Contour Column local menu option to contour a column of the list display. Choosing Contour Column from the local menu will open the [Contour Column Dialog](04-model-explorer-and-case-information-part3.md#contour-column-dialog).

Plot Column(s)

Select this option to plot the values in any selected columns.
