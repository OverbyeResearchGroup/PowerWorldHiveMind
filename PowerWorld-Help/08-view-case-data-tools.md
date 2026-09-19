---
title: "Data View, Data Check and Other Case Data Tools"
part: "Viewing Case Data"
chapter_file: "08-view-case-data-tools.md"
topics: 15
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Data View, Data Check and Other Case Data Tools

Data View, Data Check, Bus View, Substation View, Spatial View, labels, difference case and fixed-number buses.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (15)**

- [Data View](#data-view)
- [Data Check Overview](#data-check-overview)
- [Data Checks Results shown in Case Information Displays](#data-checks-results-shown-in-case-information-displays)
- [Data Check Definitions](#data-check-definitions)
- [Bus View Display](#bus-view-display)
- [Substation View Display](#substation-view-display)
- [Spatial View Oneline](#spatial-view-oneline)
- [Difference Case](#difference-case)
- [Difference Case:  Using Difference Case](#difference-case-using-difference-case)
- [Present Topological Differences from Base Case](#present-topological-differences-from-base-case)
- [FixedNumBus Features](#fixednumbus-features)
- [FixedNumBus in AUX and other Text Files](#fixednumbus-in-aux-and-other-text-files)
- [Save Merged FixedNumBus Case](#save-merged-fixednumbus-case)
- [User Interface Interactions](#user-interface-interactions)
- [FixedNumBus Relationship to RAW Format](#fixednumbus-relationship-to-raw-format)

---

<a id="data-view"></a>

## Data View

*Source: [`Content/MainDocumentation_HTML/Data_View.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Data_View.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 20

The Data View provides a mechanism for showing a user-customizable dialog that allows you to view the fields of one object. The Data View is built from the same customization used for the list of fields shown on a case information display. The specification of how to layout the Data View is stored in that same structure. See the topic on [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays). Thus the actual object that stores the customization is the Case Information Customization object (DataGrid, [Case Information Customizations Display](04-model-explorer-and-case-information-part1.md#case-information-customizations-display)) and the User Defined Case Information Displays (UserDefinedDataGrid, [User-Defined Case Information Displays](04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays)).

Accessing the Data View

The Data View can be opened from many places within PowerWorld. Also note that multiple Data View may be open simultaneously. The locations of where a Data View can be opened are as follows.

1.  [Case Information Ribbon tab under the Views Ribbon Group](02-simulator-ribbon.md#case-information-tab-overview) or on the [Onelines Ribbon Tab under the Views Ribbon Group](02-simulator-ribbon.md#onelines-tab-overview)
2.  Right-Click Menu of a most [case information displays](04-model-explorer-and-case-information-part1.md#local-menu-options) and in the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar).
3.  Right-Click menu of many oneline diagram objects
4.  When left-clicking on any oneline object that links to a model object, then any open Data View will automatically update to reflect what has been selected. It also looks at the secondary objects associated with the selection as well. For example, if you have a Data View open showing an Area object type, then if you left click on a bus the Data View will automatically update to reflect the area of the bus. Take advantage of having multiple Data View open as well by having a Gen, Load, and Shunt Data View open. When clicking on a oneline display object bus then all Data View will update.

Data View dialog

There are various buttons at the top of the Data View which allow you to choose which object is shown on the data view.

  - Click The **Find** button to choose a different object (but the same type as presently being shown).
  - Click the **Type** button to change the type of object being shown on the Data View (any object type in PowerWorld can be chosen).
  - Click the **Refresh** button to refresh the fields on the dialog for the object being shown. The Data View will stay open while you are interacting with other dialogs in PowerWorld, so it is possible that values have been changed on another dialog and the Data View has not been refreshed to reflect this. Click refresh to ensure they stay up to date.
  - Click the **New** button to open another Data View. There can be multiple Data View dialogs open simultaneously.

There are also various options at the bottom of the Data View .

  - Click the **Modify** button to open the same dialog as seen you get when choosing Display/Column options on a case information display. This allows you to [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) and thus the Data View Layout. This will be discussed more below.
  - Click the **Close** button to close the Data View.
  - The drop down list at the bottom of the dialog will show you a list of all [customized case information displays](04-model-explorer-and-case-information-part1.md#case-information-customizations-display) (DataGrid) that have actually been customized by the user. In addition it will also list all [User-Defined Case information display](04-model-explorer-and-case-information-part3.md#user-defined-case-information-displays) definitions (UserDefinedDataGrid). You may choose one of these to change the list of fields shown in the middle portion of the Data View.
  - **Options**: Choose what captions are shown on the Data View as either Column Headings, Concise Variable Names, or Legacy Variable Names.
  - **Options**: Uncheck **Allow Auto Update** to prevent the dialog from refreshing to reflect any oneline object that is clicked upon.
  - **Options**: Check **Show Customization Pane** to show a colored pane along the right side of the Data View dialog. When the Customization Pane is visible, then you may click on a particular field being shown on the dialog and the Customization Pane will show you information about Digits, Decimals, Tab/Row/Col Breaks and Captions as described below. The field will be highlighted in the same color as the Customization Pane as well.

The middle of the dialog shows the fields (according to the DataGrid or UserDefinedDataGrid chosen) for the object (according to the object chosen). The layout of the Data View is described next.

Customization of the Data View Layout

The Data View allows you to layout fields into a tabbed dialog that includes groupings of fields with group captions. The resulting dialog for the Data View can be configured to look as shown in the following figure. Notice the general layout of the dialog which consists of a portion at the top of the dialog containing fields that presumably define which object is being shown. Then below this top portion are a series of tabs. Within each tab, there can then be groupings of fields arranged into rows and columns of groupings.

![DataView](images/DataView.png)

The Data View Layout is built by specifying a value for TabBreak, RowBreak, and ColBreak for each field. For each break that is a YES, you may also specify a TabCaption, RowCaption, or ColumnCaption. TabCaptions are used on the dialog for the tabs. RowCaptions and ColumnCaptions are used as captions of group boxes on the dialog. If the RowCaption or ColCaption are blank then no group box is drawn. The resulting dialog is then automatically created from these choices. The top portion of the dialog is made up of all fields before the first TabBreak. Each list of fields before a subsequent tab break are then shown inside a unique tab. If youdo not want any fields above the tabs, then just specify TabBreak = YES for the first field in this list. Within the list of fields inside a tab, you may then also specify RowBreaks and ColumnBreaks. RowBreaks have precedence over column breaks.

Ultimately the Data View Layout is stored with a Case Information Customization. You may modify this layout in three different ways, but all of these methods are modifying the same entries.

1.  **Customization Pane**: Under the options menu, choose **Show Customization Pane**. You may then click on a particular field on the dialog and the customization pane will update to show the Digits, Decimals, Tab/Row/Col Breaks and Captions for that field. Just edit them directly in the Customization Pane. (See first image below)
2.  **Right-clicking**: You may also customize the breaks by right-clicking on the a particular field on the dialog and choosing the options such as **Add Tab Break** or **Remove Col Break**, or **Edit Row Break Caption** (See the left portion of the first image below).
3.  **[Display/Column options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)** : the Data View Layout is actually stored as part of the customization of a case information display and can be modified on the Data View Layouts tab the Display/Column options dialog as shown in the second image below.

![DataViewCustomizationPane](images/DataViewCustomizationPane.png)

![CaseInfoDisplayColumnOptionsDataViewLayout](images/CaseInfoDisplayColumnOptionsDataViewLayout.png)

Example

As an example, if you configured 21 fields using the following settings, you would get the dialog as depicted on the right.

Variable Name

Tab

Break

Tab

Caption

Row

Break

Row

Caption

Col

Break

Col

Caption

 ![DataViewLayout](images/DataViewLayout.png)

Field 0

Field 1

Field 2

Field 3

Field 4

YES

My Cap

Field 5

YES

EDFG

Field 6

Field 7

Field 8

YES

HIJK

Field 9

Field 10

Field 11

YES

Test,Cap

Field 12

YES

Another

YES

Heref

Field 13

Field 14

YES

Field 15

YES

LMNO

Field 16

Field 17

YES

ABCD

Field 18

YES 2

XYZ

Field 19

YES

Field 20

A few notes about this example are as follows.

  - Column caption that goes with Field 14 is blank which means that no group box with caption is listed.
  - Field 18 has a Col Break specified as "YES 2" to indicate that a column should be skipped and left empty
  - Field 12 has both a Tab Break and a Row Break. The Row break is only necessary so that a Row Caption can be specified.

---

<a id="data-check-overview"></a>

## Data Check Overview

*Source: [`Content/MainDocumentation_HTML/Data_Check_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Data_Check_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Data Check objects were added in Version 20, Patch April 9, 2018

Data Check objects provide a mechanism for defining a check on specific data that you want to flag. A data check applies to a particular object type and an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) is used to define which objects meet this data check. PowerWorld's expectation is that user will create filters that look for "bad" data, but it can really be any data you want summary information on. Once a data check is created then objects of the respective type will have columns available which show whether they meet or do not meet that data check. In addition, aggregate data check information will be available to show the count of objects within an aggregation which meet the filter. For example, consider a data check that looks for any bus with a voltage greater than 1.05 per unit. If the data check aggregation field were added to an area table, then the column would display information about the count of the number of buses in the area which have a voltage greater than 1.05 per unit.

There are a few help topics related to Data Checks which are

  - [Data Check Overview](#) (this topic)
  - [Data Check Definitions](#data-check-definitions) (help on the Data Check definition)
  - [Data Checks Results shown in Case Information Displays](#data-checks-results-shown-in-case-information-displays) (shows how the data checks are used)

To define Data Checks as well as view the results of the Data Checks, go to the [Case Information Ribbon Tab](02-simulator-ribbon.md#case-information-tab-overview) and click on the Data Check button. This brings up a dialog with a three tabs which are described below.

Define Checks

This tab contains a case information display showing the defined Data Check objects and DataCheckExemption objects. For more information about defining a Data Check see the [Data Check Definitions](#data-check-definitions) help.

DataCheckExemption object were added in Version 23, Patch September 25, 2023. When clicking on the list of DataCheck objects on the left side of the Define Checks tab, the case information display on the right-side of the display will update to show any DataCheckExemptions for the selected DataCheck. There is also a check-box with the caption Show **DataCheckExemption for all DataCheck**. Checking this box will instead show a list of all DataCheckExemption objects (across all DataCheck objects).

Check Results Tab

On the left of this tab is a folder view of all the object types for which at least one Data Check has been defined. As you click on any entry underneath the folder on this view you will see a list of data checks based on the folder. Under each folder is a list of all the data checks for the respective object type with check boxes on the left. As you check and uncheck these boxes, columns for Data Checks will be automatically added and removed to show appropriate data checks. The folder icons on this view also have a small check box inside them. You may check and uncheck the folder icons to check or uncheck all boxes underneath the folder. The check box state for individual Data Check objects on this dialog is stored as the [field *Show* of the Data Check object](#data-check-definitions).

There is also a check box at the top of the case information display called **Include Fields used by Data Check Filter**. Check this box to automatically add columns associated with the Filter defined with each Data Check shown.

Finally, the check box **Only Objects that meet one Data Check shown** may be checked so that the case information display is automatically filtered to only show objects that meet at least on Data Check that has been shown in this table. This will mean as the check and uncheck Data Checks on the left the list of objects shown in the case information display will automatically change.

![DataCheckResults](images/DataCheckResults.png)

Check Aggregation Results

On the left of this tab is a folder for [Area](05-case-information-displays-by-object-part1.md#area-display), [Data Maintainer](07-object-properties-run-mode-and-general-part1.md#datamaintainer), [Owner](05-case-information-displays-by-object-part3.md#owner-dialog), and [Zone](05-case-information-displays-by-object-part1.md#zone-display) objects. Under each of these folders is a list of all object types which can be aggregated at the respective levels (Area, Data Maintainer, Owner or Zone). The support of aggregations is the same as that used by [Calculated Fields](04-model-explorer-and-case-information-part1.md#calculated-fields). The list of Data Check objects again have check boxes on the left. Check and uncheck these boxes to change which columns are shown. If more than 10 potential data checks exist for an Aggregation object, then sub-folders may be automatically created to show any object type that has more than 2 Data Checks defined. You may click on the sub-folder icons to check or uncheck all boxes contained inside the folders. The check box state on this tab is stored as the [field *ShowAggregation* of the Data Check object](#data-check-definitions).

The case information display shown will automatically add columns based on the check boxes chosen. Also note that changing the check box under the Area folder will automatically change the check box under the Data Maintainer, Owner, and Zone objects as well. There is only one field *ShowAggregation* which is maintained across all aggregations.

When viewing the result of a Data Check Aggregation Field in either a case information or in the output to an Auxiliary File, the result will be information on the count of objects that meet the filter. As an example, assume you are showing a generator aggregation data check on an area table. Then assume that your area contains 153 generator and of those 46 meet the filter defined in the data check. Depending on the choices made for the *Aggregation Format* in the Data Check definition this field will be shown as either "46", "46 / 153", or "46 : 107". The following shows an example Area table showing Data Check Aggregation Fields.

![DataCheckAggrResults](images/DataCheckAggrResults.png)

---

<a id="data-checks-results-shown-in-case-information-displays"></a>

## Data Checks Results shown in Case Information Displays

*Source: [`Content/MainDocumentation_HTML/Data_Check_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Data_Check_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Data Check objects were added in Version 20, Patch April 9, 2018

For help on defining Data Check objects see [Data Check Definitions](#data-check-definitions) help. For an overview of Data Checks see [Data Check Overview](#data-check-overview) help.

Each Data Check has a field ObjectType which indicates the type of object to which the data check applies. After creating a Data Check, fields will become available to objects of that type. These fields will be in the folder "Data Check" and will show the name of the Data Check. Also after creating a Data Check, there will be fields made available to object types which can utilize [Calculated Fields](04-model-explorer-and-case-information-part1.md#calculated-fields) of the Data Check's ObjectType. These fields will be made available under Data Check\\Aggregations. See the [Calculated Fields](04-model-explorer-and-case-information-part1.md#calculated-fields) help for more information on object type relationships, The easy examples are aggregations such as an Area, Zone, Owner, or Data Maintainer which can do calculations across all the generators or buses that they contain.

Starting in the Version 23, Patch September 25, 2023, the ability to define DataCheckExemption objects was added. By right-clicking on a column showing the DataCheck results for a particular object you may choose a option to "Add Exemptions for selected objects from Data Check". This option will get the objects from the rows in the table and the DataCheck objects based on the columns in the table and will then create a DataCheckExemption for any DataCheck/Object pair for which the Object presently meets the DataCheck. A dialog will appear asking for a reason to be entered (which can be blank). Upon defining the DataCheckExemption the row chosen may disappear (because the object no longer meets the DataCheck).

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Fields Available for Data Check</p>
<p>The picture to the right shows the field list for a generator table. Notice the folder <span class="underline">Data Check</span> under which fields are shown. The fields that appear under this Data Check folder will automatically change as you create and delete Data Check objects.</p>
<p>Inside the Data Check folder will be a list of Data Checks related to the object type of the table you are viewing. For example, the image to the right shows fields for a generator table and the fields indicated with a red outline represent the data checks that apply to this Gen object type.</p>
<p>When viewing the result of a Data Check field in either a case information display or in the output to an Auxiliary File, if the object meets the Data Check's Filter then the result will display the string specified by the <a href="#data-check-definitions">FilterMeetsString</a> in the Data Check Definition. If the object does not meet the Data Check's Filter then the result will display the string specified by the <a href="#data-check-definitions">FilterNotMeetsString</a>. See information on <a href="#data-check-definitions">defining a Data Check</a> for more information.</p>
<p> </p>
<p>Fields Available for Data Check\Aggregation</p>
<p>If Data Checks for related object types are available, then the folder Aggregation will appear under Data Check. Notice the Aggregation folder under which there are folder for Branch, Bus, and Zone objects with the fields boxed in blue on the right.</p>
<p>As an example, adding the aggregation data check field of a <span class="underline">branch</span> to a <span class="underline">generator</span> table would give count information related to how many branches connected to the generator meet the filter of the Branch Data Check object. A more common example would be using a Data Check that applies to a Gen or Bus object on an Area table to show the count of gen or bus objects within the area that meet the Filter.</p>
<p>When viewing the result of a Data Check Aggregation Field in either a case information or in the output to an Auxiliary File, the result will be information on the count of objects that meet the filter. As an example, assume you are showing a generator aggregation data check on an area table. Then assume that your area contains 153 generator and of those 46 meet the filter defined in the data check. Depending on the choices made <a href="#data-check-definitions">for the <em>Aggregation Format</em> in the Data Check definition</a> this field will be shown as either "46", "46 / 153", or "46 : 107".</p>
<p>See information on <a href="#data-check-definitions">defining a Data Check</a> for more information.</p></td>
<td><img src="images/DataCheckFields.png" alt="DataCheckFields" /></td>
</tr>
</tbody>
</table>

Example Data Check Results

![DataCheckResults](images/DataCheckResults.png)

Example Data Check Aggregation Results

![DataCheckAggrResults](images/DataCheckAggrResults.png)

Variable Names for Data Check Fields (DataCheck:location )

The variable name for the data checks associated with the same object type as the Data Check will be of the form DataCheck:location where the location is an integer number indicating an index into the array of DataCheck objects of *this particular type*. For example you could use

"DataCheck:NERC at Mvar Limit"

Variable Names for Data Check Aggregation Fields (DataCheckAggr:location)

The variable name for the field under the aggregation folder will be of the form DataCheckAggr:location where the location is an integer number indicating an index into the array of all DataCheck objects (this integer location will not match those used with DataCheck:location). In addition, the integer value can be replaced with a string with the name of the objecttype followed by a space and then followed by the name of the Data Check. For example you could use

"DataCheckAggr:Bus 'CASE Missing BA'"

---

<a id="data-check-definitions"></a>

## Data Check Definitions

*Source: [`Content/MainDocumentation_HTML/Data_Check_Define.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Data_Check_Define.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Data Check objects were added in Version 20, Patch April 9, 2018

For an overview of Data Checks see [Data Check Overview](#data-check-overview) help. For help on using Data Checks in Case Information Displays see [Data Checks Results shown in Case Information Displays](#data-checks-results-shown-in-case-information-displays)

This help topic describes how to define a Data Check object. The fastest way to get a list of Data Checks to the [Case Information Ribbon Tab](02-simulator-ribbon.md#case-information-tab-overview) and click on the Data Check button. This brings up a dialog with a three tabs. The third tab provides access to a case information display showing the list of Data Checks.

Data Check Exemptions

DataCheckExemption objects were added in Version 23, Patch September 25, 2023

A DataCheckExemption groups an Object and a DataCheck together. By defining a DataCheckExemption, then the Object will never return that it meets the respective DataCheck.

Field

Description of Field

DataCheckName

(KEY FIELD) Name of the data check to which this exemption applies

Object

(KEY FIELD) String identifying the object using its objecttype and keyfields or label. This will follow the same syntax used for the [ObjectID Field for use in Auxiliary Files](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels). This field will show object strings based on the option set in the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) for either Primary, Secondary , or Label key field identifiers.

Reason

User enterable reason for the exemption. This string can be anything the user wants to enter and can also be a blank string.

MeetsCriteria

Will show YES if the Object meets the DataCheck. If it is NO then it means the Exemption is not needed.

Data Check Objects

A data check object has key fields of ObjectType to which it applies and a Name. The Name need only be unique across all the Data Check objects that apply to the same ObjectType. The important fields of a Data Check are as follows.

Field

Description of Field

ObjectType

(KEY FIELD) This is the type of object to which the Data Check applies.

Name

(KEY FIELD) The Name need only be unique across all the Data Check objects that apply to the same ObjectType

Filter

This is the name of a [filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) that is applied to the objects of type <span class="underline">ObjectType</span>. The user may also enter a simple string defining a single field comparison such as “Vpu \< 0.94” so that a named filter need not be created.

Show

This is either YES or NO and determines whether to show the data check on the Check Results tab of the [Data Check overview dialog](#data-check-overview) . This stores the check box status from that dialog.

ShowAggregation

This is either YES or NO and determines whether to show the data check on the Check Aggregation Results tab of the [Data Check overview dialog](#data-check-overview) . This stores the check box status from that dialog.

Filter Meets String

If a particular object meets the Filter, then it will display the string specified here in the column associated with this data check. See

Filter Not Meets String

Same as before, but this string will appear in the column associated with this Data Check if the object does *not* meet the filter.

Description

This is the string that will appear when hovering the mouse over top the column headers associated with the Data Checks in the same way other column header hints work in case information displays

Aggregation Format

The Aggregation Format describes how the aggregation fields will be displayed. The choices are

  - Meets
  - Meets/Total
  - Meets:Not Meets

See examples on the [Data Checks Results shown in Case Information Displays](#data-checks-results-shown-in-case-information-displays).

... additional fields...

A Data Check object can also be used to implement Dynamic Formatting on either the case information displays or the oneline diagrams. See help on [Dynamic Formatting Overview](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) for more information. Use this to dynamic highlight using colors and other graphic features data that meets the Filter of the data check.

Data Check Dialog

Right-clicking on a Data Check object in the case information display and choosing to Show Dialog will show the Data Check dialog. The Data Check dialog is shown in the following figure and provide access to editing the fields above. If you want to edit all the features related to [Dynamic Formatting Dialog](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog) based on objects that meeting the Filter of the Data Check, then check the box **Show Dynamic Formatting Features** to expose those options.

![DataCheck](images/DataCheck.png)

---

<a id="bus-view-display"></a>

## Bus View Display

*Source: [`Content/MainDocumentation_HTML/Bus_View_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_View_Display.htm)*

The **Bus View Display** feature provides a graphical display which allows you to quickly browse information about a bus and everything connect to that bus. The bus view displays enable convenient bus-by-bus navigation through the power system. From the bus view, you can find out a bus’ voltage and angle, the load, shunt compensation, and generation connected to the bus, and the flows on all lines emanating from the bus. You can also discover the bus’ area and zone affiliations, as well as the bus’ marginal cost. Moreover you can find out all information about the elements associated with the bus by directly invoking their associated information dialogs. The advantage of the bus view displays, is that they are auto-created oneline diagrams.

Along the top of the bus view display resides a panel of controls. The buttons labeled **Back** and **Ahead**allow you to step through the history of buses you have viewed thus far. To move the bus view to a particular bus, type a number or name into the edit box next to the caption **Bus**. If a number is typed the case will be scanned for a bus of that number, otherwise the case will be scanned for a bus that starts with the string entered. If you’re unsure which bus that you are looking for click the **Find…** button to bring up a display that allows you to search using wildcard strings for the bus. The **History** menu will show a list of the last 30 buses which have been visited in a bus view. There are also drop-downs in this top panel for **Options** and **Views **. These are discussed below.

Below this top panel sits the actual bus display. The bus you have chosen to inspect, which we shall refer to as the *target bus*, is represented by a long, thick horizontal line. Notice that the bus’ voltage in kV and per unit, its angle, and its marginal cost are specified to the left of the bus. Any loads and generating loads connected to the target bus are drawn above the bus symbol, along with their associated annotation. Also any radial connections to a single bus containing load, generator or switched shunts will be drawn above the bus symbol.

Emanating from the bottom of the bus symbol are all transmission lines and transformers that connect the target bus to its neighbors. The transmission line and transformer symbols are equipped with pie charts and annotation identifying flows as measured at the target bus, as well as arrows to identify the direction of MW flow on the branch. Neighboring buses are represented as filled rectangular regions, with symbol indicators included if other types of devices, such as loads, generators, etc., are attached. When you drag the mouse over one of the neighboring bus symbols, it turns into a pointing finger. Clicking the left mouse button when the mouse cursor is in this shape redefines the target bus to be the bus whose symbol you just clicked. The bus view display is redrawn to show the same sort of display for the newly chosen target. You can go back to the previously displayed target bus by clicking the ** **Back** arrow, and then return to this record by clicking the **Ahead** arrow.

It is useful to think of the bus view displays as nothing more than an additional oneline diagram. In other words, you interact with the objects drawn on the bus view display in the same way you work with objects on a more conventional Simulator oneline. Right-clicking on any power system object will bring up that object’s local menu, which includes a link to the object’s associated information dialog. As on a conventional oneline diagram, flows on a bus view display can be animated. Right-clicking on the bus view display’s background will generate the same local menu as other oneline diagrams.

The bus view display can be generated using any of the following methods:

  - Go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and click on the **Bus View** from the **Views** ribbon group
  - Go to the [](02-simulator-ribbon.md#onelines-tab-overview)[Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, and click on the **Bus View** from the **Views** ribbon group.
  - Right click on the bus of interest on the oneline diagram to display the bus’ local menu, and choose Bus View. The bus view display will open with the selected bus already displayed.
  - From the oneline diagram, right click on the [shunt](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects), [gen](11-building-onelines-network-objects.md#generator-display-objects), [lines](05-case-information-displays-by-object-part2.md#line-and-transformer-display) and [DC lines](05-case-information-displays-by-object-part2.md#dc-lines-display) symbol and under Bus Information select Bus View.
  - From any of the case information displays that convey bus information, right click on a record to bring up its local menu, and choose Bus View Oneline. The bus view display will open with the corresponding bus already displayed.
  - Click the **Bus View** Button on the [Case Information Toolbar.](04-model-explorer-and-case-information-part1.md#case-information-toolbar)
  - While in Run Mode, left clicking on a bus name or number field.

To switch between the bus view and the main oneline, use the **Open Windows Menu** available on the **Views** ribbon group on the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab,or [Windows](02-simulator-ribbon.md#window-tab-overview) ribbon tab. To close the bus view display, simply close the form using the **X** button in the top right corner of the bus view display.

Note that when viewing a consolidated superbus while using consolidation via the topology processing tool, Simulator will always show circuit breaker symbols on branches, loads, generators, and switched shunts which are open (out of service.)

Bus View Options

Layout Options

Show Serial Buses

When putting in the branch connections, the Bus View display will look out into the network and find the next bus which has more than two neighbors. It will then make this the destination bus for that branch of the Bus View. The intermediate buses will then be shown in order above the destination branch. This option works especially well in systems with a lot of multi-section lines.

Show Equivalent Lines

This option indicates to the Bus View display whether or not to include branches representing equivalent circuits as connections in the display.

Represent Multi-Section Line Objects

This option indicates to the Bus View display whether or not to draw multi-section line display objects when appropriate. If this option is not checked, then the intermediate buses of the multi-section lines will be rendered normally. If this option is checked then the intermediate buses of multi-section lines will not be rendered on the bus view and only the terminals of the multi-section line will appear.

Show Field Suffixes

This option specifies whether to display the field values units as suffixes. If this option is not selected, all the fields will be display as a value without units.

Include Field Labels

Selecting this option will place labels for each displayed field on the bus view diagram.

Default Drawing Values

Choosing this option will open the Default Drawing Values for New Objects dialog. Changing these options can change some of the drawing aspects of the bus view, including device color and font size or color.

Dynamic Formatting

Click on this to bring up the [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog) for case information displays, and all views and onelines.

Number of Tiers

The bus view can display one or two "tiers" of buses in the display. Use this selection from the **Options** menu to toggle the number of tiers displayed.

Open Multiple Bus Views

This option indicates whether to open multiple bus views simultaneously. Choices are never, always, and prompt for confirmation when a new additional bus view is about to open.

Show Hints

When this option is checked, holding the cursor over an object will briefly pop up a hint box containing information about that object.

Views

Define Custom View

The fields displayed on the bus view can be customized using this option. Clicking on this option will open a customization settings display, in which you can add and remove field definitions for the objects on the bus view display. Customized bus view layouts can be saved with the case for recall, identifiable by a custom bus view layout name. Custom layouts can also be saved to a file for loading into another load flow case.

Input Data

Switching the bus view to Input Data changes the bus view from displaying system state information to displaying input data information. For example, switching to Input Data view will display line impedances and limits, generator minimum and maximum outputs, etc. The default Input Data view fields can be modified using the Define Custom View customization dialog.

System State

Switching the bus view to System State changes the bus view from displaying Input Data information to displaying system state information. This will result in line flows being displayed, voltage and angles displayed, etc., of the current solution state of the system. The default System State view fields can be modified using the Define Custom View customization dialog.

---

<a id="substation-view-display"></a>

## Substation View Display

*Source: [`Content/MainDocumentation_HTML/Substation_View_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_View_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Substation View Display feature is analogous to the [Bus View Display](#bus-view-display).

Along the top of the substation view display resides a panel of controls. The buttons labeled **Back** and **Ahead** allow you to step through the history of substations you have viewed thus far. Substation View options are available from the **Options** menu. To find a substation using search tools, click on the **Search For** button. The next two controls following the Substation label allow to specify a substation name (in the first text box) or a number (in the second text box). If you type a number or name that does not exist, the substation display will continue displaying the current substation.

Below this top panel sits the actual substation view display.

Just as with the bus view, it is useful to think of the substation view displays as nothing more than a oneline diagram. In other words, you interact with the objects drawn on the substation view display in the same way you work with objects on a more conventional Simulator oneline. Right-clicking on any power system object will bring up that objects local menu, which includes a link to the object’s associated [information dialog](06-object-properties-edit-mode-part1.md#substation-information). As on a conventional oneline diagram, flows on a substation view display can be animated. Right-clicking on the substation view display’s background will generate the same [local menu](15-using-onelines-tools-and-options.md#oneline-local-menu) as other oneline diagrams. The substation view can be generated using any of the following methods:

  - Go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and click on the **Substation View** from the Views Ribbon Group
  - Go to the [](02-simulator-ribbon.md#onelines-tab-overview)[Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab,and click on the **Substation View** from the **Views** ribbon group.
  - Right click on the substation of interest on the oneline diagram to display the substation’s local menu, and choose Substation View. The substation view display will open with the selected substation already displayed.
  - From any of the case information displays that convey substation information, right click on a record to bring up its local menu, and choose Substation View Oneline from the Substation Records menu. The substation view display will open with the corresponding substation already displayed.
  - Click the **Substation View** Button under the **Records** menu on the [Case Information Toolbar.](04-model-explorer-and-case-information-part1.md#case-information-toolbar)

To switch between the substation view and the main oneline, use the **Window** menu tree on the main menu. To close the substation view display, simply close the form using the **X** button in the top right corner of the substation view display.

---

<a id="spatial-view-oneline"></a>

## Spatial View Oneline

*Source: [`Content/MainDocumentation_HTML/Spatial_View_Oneline.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Spatial_View_Oneline.htm)*

Spatial View Onelines (SVOs) provide a quick means to automatically create oneline diagrams for either buses or substations using geographic information. They are the most useful when geographic information is available, but they can also be used when none is available. SVOs bridge the gap between [Bus](#bus-view-display) and [Substation](#substation-view-display) Views and [Geographic Data Views (GDV)](04-model-explorer-and-case-information-part3.md#geographic-data-view). While intended for mostly temporary use, they can be saved as PWD or AXD files.

Bus Spatial View Oneline (Bus SVO)

Options to create Bus SVOs can be found in many of the same places where Bus Views can be created including Case Information Display local menus and local menus for display objects.

Here is an example of a bus Spatial View Oneline.

![Spatial View Oneline](images/Spatial_View_Oneline.jpg)

Bus Spatial View Oneline Objects

The bus SVO consists of bus geographic data view objects (GDVs) and GDV line summary objects (GLSOs) showing the lines connecting the buses.

The GDVs have default lines of text that display bus identifying information along with MW and Mvar information for the generators, loads, and shunts attached to the bus. A green tab will appear on a GDV for which all of the first neighbors for a bus are drawn on the oneline. If there is no green tab, there are first neighbors for a bus that are not shown on the oneline.

When geographic latitude and longitude information is available for a bus, this will be used to place the bus GDV objects. When this information is not available, a default layout algorithm will be used to place the bus GDV objects. The number of buses in the display can be increased while in Run Mode by double clicking on a bus GDV to draw all of its neighbors. The placement of buses can be changed by holding down the left mouse button on a bus GDV and dragging to a new location.

GDV Line Summary Objects (GLSOs) for Bus GDVs

The GLSOs are the lines connecting the buses with field information showing the MW and Mvar flows and the maximum percent of the line limit. The magnitude of the MW and Mvar flows are taken at the end of the line with the lowest bus number. If there are multiple lines between two buses, the GLSOs are the summation of the flows on all of these lines. The GLSOs are drawn using the [Default Drawing Values](14-editing-onelines.md#default-drawing-values) for Transmission Line thickness and color based on the nominal kV level. Transformers will be drawn with thicker lines in which the inner color stripe is the lower nominval kV level and the outer color stripes are the higher nominal kV level. Green arrows on the lines show the direction of MW flow, and magenta arrows show the direction of Mvar flow. Right-click options are available for the GLSOs to show the information dialogs for the component line(s).

Deleting GDVs

Individual GDVs can be deleted by right-clicking on the GDV and choosing **Delete Selected GDV Object**. While in Edit Mode, multiple GDVs can be deleted by selecting them and pressing **Delete**. Delete functionality is only deleting the oneline representation of a bus and will never delete the linked data object.

Customizing GDVs

The GDVs can be customized by using the [Geographic Data View Style Options](04-model-explorer-and-case-information-part3.md#geographic-data-view) dialog. This dialog can be displayed by right-clicking on any GDV and selecting **View Geographic Data View Options**.

Quick resizing of the GDVs and the field boxes for the GLSOs can be done by using Shift+Up Arrow to increase the size and Shift+Down Arrow to decrease the size.

Customizing GLSOs

The GLSOs can be customized by using the [Geographic Data View Style Options](04-model-explorer-and-case-information-part3.md#geographic-data-view) dialog. This dialog can be displayed by right-clicking on any GLSO and selecting **View Geographic Data View Options**. Clicking the **Show Line Flow Summary Options and List Dialog** button will bring up a dialog of options that are applicable to the GLSOs.

Line vertices can be added to the GLSOs by holding down the CTRL key and left-clicking on the line. Vertices can be deleted by holding down the CTRL key and left-clicking on an existing vertex.

Substation Spatial View Oneline (Substation SVO)

Options to create Substation SVOs can be found in many of the same places where Substation Views can be created including Case Information Display local menus and local menus for display objects.

Substation Spatial View Oneline Objects

The substation SVO consists of substation geographic data view objects (GDVs) and GDV line summary objects (GLSOs) showing aggregate lines connecting the substations.

The GDVs have default lines of text that display substation identifying information along with MW and Mvar information for the generators, loads, and shunts in the substation. A green tab will appear on a GDV for which all of the neighboring substations are shown on the oneline. A yellow tab will appear if all possible connections for a substation are shown on the oneline but some lines connect to buses without substations. If there is no tab, all neighboring substations are not shown on the oneline.

When geographic latitude and longitude information is available for a substation, this will be used to place the substation GDV objects. When this information is not available, a default layout algorithm will be used to place the substation GDV objects. The number of substations in the display can be increased while in Run Mode by double clicking on a substation GDV to draw all of its neighbors. The placement of substations can be changed by holding down the left mouse button on a substation GDV and dragging to a new location.

GDV Line Summary Objects (GLSOs) for Substation GDVs

The GLSOs are the aggregate lines connecting the substations with field information showing the summation of the MW and Mvar flows on all connecting lines and the maximum percent of the aggregate line limit.

The MW and Mvar flow values are taken at the end of the line with the lowest substation number. The GLSOs are drawn using the [Default Drawing Values](14-editing-onelines.md#default-drawing-values) for Transmission Line thickness and color based on the highest nominal kV level. Green arrows on the lines show the direction of MW flow, and magenta arrows show the direction of Mvar flow. Right-click options are available for the GLSOs to show the information dialogs for the component line(s).

The above Bus SVO sections on **Deleting GDVs**, **Customizing GDVs**, and **Customizing GLSOs** are also applicable to Substation SVOs.

Visualizing Shortest Path Between Buses with SVOs

The [Determine Shortest Path Between](06-object-properties-edit-mode-part1.md#shortest-path-between-buses) elements tool has an option to visualize the buses found in the path of shortest measurement.

---

<a id="difference-case"></a>

## Difference Case

*Source: [`Content/MainDocumentation_HTML/Difference_Flows.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Difference_Flows.htm)*

Note: Prior to Version 20, this was called Difference Flows

The **Difference Case** feature provides an easy mechanism for comparing two power system cases. For example, Difference Case can be used to show the difference in transmission line flows and bus voltages resulting from a contingency or a change in power transfer between two areas. Using the [Present Topological Differences from Base dialog](#present-topological-differences-from-base-case) you can also see additions and deletions of entire data objects as well.

Difference Case is available in both [Run Mode](01-getting-started.md#run-mode-introduction) and [Edit Mode](01-getting-started.md#edit-mode-introduction), however when you switch from Run Mode back to Edit Mode, Simulator automatically resets you to the Present Mode. This is done so that you do not accidentally try to edit data while in Difference or Base. Once you are in Edit Mode however, you can still manually switch back to Difference, Base, or Change Mode.

To toggle between the different case modes, open this dialog and select the desired mode. Alternatively, you can click the **Difference Case** button in the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group) on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab and select the desired Difference Case display mode.

For more information about how to use Difference Case see [Using Difference Case](#difference-case-using-difference-case).

The Difference Case Dialog can be accessed by:

  - Go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Difference Case \> Difference Case** from the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group). [ ](01-getting-started.md#edit-mode-introduction).
  - Selecting **Difference Case** from the [oneline local menu](15-using-onelines-tools-and-options.md#oneline-local-menu).
  - All Difference Case Actions are controlled via the Difference case Dialog or the drop-down list on the Difference Case toolbar button.

![Difference Flows Dialog](images/Difference_Flows_Dialog.gif)

Key Field to Use

The difference case feature makes a comparison between the Present Case and the values stored in the Base to determine which objects match one another. The Key Fields to Use specifies whether this matching is done using Primary Keys (bus numbers), Secondary Keys (bus names/Nom kV pair), or by Label.

Display Mode

Changing the display mode affects all aspects of the Simulator environment. Information shown on oneline diagrams and case information displays is governed by which of the four (Present, Base, Difference, and Change) is currently being displayed.

  - **Base** – A solved power system that serves as the reference for the difference case tool. To establish a base, set up a power system corresponding to the desired operating point. Open the Difference Case Dialog and click the button labeled **Set Present as Base**. You can also set the present from the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group) on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.
  - **Present** – The operating point used in the Difference Case comparison. The Present Case must have the same key field scheme as the Base for proper operation of the Difference case tool. See [Topological Differences](#present-topological-differences-from-base-case) for more information.
  - **Difference** – The difference between the Present and the Base values. The values displayed in the Difference are established using the Base as the reference, thus the Difference Mode will show numerical difference of \[Present - Base\]. When showing status fields for branches, generators, etc... fields will show up as either OPEN|CLOSED or CLOSED|OPEN if the status changed. The status in the present case will be listed first. A similar format will be used for fields such as generator AGC Status and other text fields.
  - **Change** - (Added in Version 20)Change mode will only show the fields that have changed between the base and present. If a field has changed, then the present value will be shown, otherwise the value will be shown as a blank. There are also some special considerations for change mode discussed below related to blank entries and determining when numeric fields are considered the same.

Show Present|Base in Difference and Change Mode

Choose this option so that instead of showing the numerical difference for a field we instead show the present value followed by the pipe | character and then followed by the Base Value. When in Difference Mode this will be done if there is a numerical difference, otherwise it will just show the present value (which is of course the same as the base). When in Change Mode, you will still only see values that have changed, but again instead of seeing only the present value, you will see the present and base values separated by a pipe character. For string fields you may see the field start with a pipe (meaning the field is presently blank bus the base was not) or end with a pipe (meaning the field now has an entry but was blank in the base).

Examples of Mode along with Show Present|Base option

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Mode</p></td>
<td><p>Numeric Field</p>
<p>(with change)</p></td>
<td><p>Numeric Field</p>
<p>(no change)</p></td>
<td><p>String Field</p>
<p>(with change)</p></td>
<td><p>String Field</p>
<p>(no change)</p></td>
<td><p>Special Field such as Latitude</p>
<p>(with change)</p></td>
<td><p>Special Field such as Longitude</p>
<p>(no change)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Present Value</p></td>
<td><p>56.43</p></td>
<td><p>78.90</p></td>
<td><p>Jackson</p></td>
<td><p>Redwood</p></td>
<td><p>40.116</p></td>
<td><p>-88.243</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Base Value</p></td>
<td><p>12.12</p></td>
<td><p>78.90</p></td>
<td><p>Serena</p></td>
<td><p>Redwood</p></td>
<td><p> </p></td>
<td><p>-88.243</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Difference Mode</p></td>
<td><p>-44.31</p></td>
<td><p>0.00</p></td>
<td><p>Jackson|Serena</p></td>
<td><p>Redwood</p></td>
<td><p>40.116</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Change Mode</p></td>
<td><p>12.12</p></td>
<td><p> </p></td>
<td><p>Jackson</p></td>
<td> </td>
<td><p>40.116</p></td>
<td><p>_same_</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Difference Mode with Present|Base</p></td>
<td><p>56.43|12.12</p></td>
<td><p>78.90</p></td>
<td><p>Jackson|Serena</p></td>
<td><p>Redwood</p></td>
<td><p>40.116|</p></td>
<td><p>-88.243</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Change Mode with Present|Base</p></td>
<td><p>56.43|12.12</p></td>
<td> </td>
<td><p>Jackson|Serena</p></td>
<td> </td>
<td><p>40.116|</p></td>
<td><p>_same_</p></td>
</tr>
</tbody>
</table>

User Interface Coloring For Different Modes (Coloring added in Version 20)

When looking at case information displays there is also automatic coloring when in the Base, Difference or Change Modes.

Purple rows represents objects that are in the Present Case, but a corresponding object was not found in the Base Case. In Versions 20 - 23\], these rows were orange.

Green Columns indicate fields that are not part of the Difference Case tool presently.

If you find green columns which are not presently part of the Difference Case tool which you would like us to add, please contact PowerWorld Corporation.

![DifferenceCaseColors 649x258](images/DifferenceCaseColors_649x258.png)

Special Considerations for Change Mode

(Added in Version 20)

For some input fields, a blank is a valid user input indicating that none is defined. For example, for the latitude and longitude coordinate of a bus or substation a value of blank indicates that the value is not defined. In this situation we can not use blank in Change mode to indicate that nothing changed. For example, the Latitude might be presently 23.45, but in the Base system it was blank. For these fields instead of showing a value of blank when nothing has changed, the string "\_same\_" will be shown instead..

Numeric fields present a challenge for doing a case comparison. Values are stored internally as a floating point numbers in the software, so it is possible that a value may be stored as 12.34567 in the Base, but has changed to 12.34568 in the present. This would represent a meaningless change. To avoid this, by default numeric values are considered the same if the percent change between them is less than 0.0001% (they are the same to about 6 significant digits). Thus a value is considered changed if it meets the following comparison

![Difference Flows Tolerance](images/Difference_Flows_Tolerance.png)

where TolPerc = 0.0001 by default

The DiffChangeTolerance object settings allow you to control when a numeric value is considered to be changed.

DiffChangeTolerance (June 25, 2018 patch of Simulator 20)

In the June 25, 2018 patch of Simulator 20, the DiffChangeTolerance object was added to give the ability to control what is considered a changed value. The DiffChangeTolerance objects can be viewed by choosing **Change Mode Tolerances** from the [Difference Case Menu](02-simulator-ribbon.md#other-tools-ribbon-group). There is also a button on the [Present Topological Differences from Base dialog](#present-topological-differences-from-base-case) that brings up the same dialog.

The easiest way to specify the tolerance settings discussed below for a particular field however is to change the user interface to Display Mode of Change. When viewing the Display Mode is set to Change, inside a case information display you may right-click on a numeric column for a field which is part of the base case and the option at the top of the right-click menu will be **Set Difference Change Tolerance**. This will allow you to open a dialog to specify the tolerance settings discussed below for that particular field.

The identifier for each DiffChangeTolerance is the ObjectType and ObjectField to which the tolerance applies. There is an entry for ObjectType = Default which represents the global default mentioned above and it can be modified to change the global default (though we wouldn't normally recommend that\!). Otherwise, each DiffChangeTolerance has the following fields TolType, TolPerc, and TolAbs. The TolType has 4 options which then use the appropriate TolPerc or TolAbs as described below.

1\. TolType = Absolute

Choose this Type to specify the absolute value of the Present - Base difference that will be considered a change.

![Difference Flows ToleranceAbsolute](images/Difference_Flows_ToleranceAbsolute.png)

2\. TolType = Percent

Choose this Type so that the percent change from the base case value is used to determine if a value has changed. The actual check done is as follows to take into account a base case value that may be very small.

![Difference Flows TolerancePercent](images/Difference_Flows_TolerancePercent.png)

3\. TolType = Perc OR Abs

Choose this Type to do a combination of the Absolute and Percent tolerances. The value will be considered changed if it meets <span class="underline">either</span> the TolPerc <span class="underline">or</span> the TolAbs constraint. Note that if the Base value is too small then the TolPerc check is ignored.

![Difference Flows TolerancePercOrAbs](images/Difference_Flows_TolerancePercOrAbs.png)

4\. TolType = Perc AND Abs

Choose this Type to do a combination of the Absolute and Percent tolerances. The value will be considered changed if it meets <span class="underline">both</span> the TolPerc <span class="underline">and</span> the TolAbs constraint. Note that if the Base value is too small then the TolPerc check is ignored.

![Difference Flows TolerancePercAndAbs](images/Difference_Flows_TolerancePercAndAbs.png)

---

<a id="difference-case-using-difference-case"></a>

## Difference Case:  Using Difference Case

*Source: [`Content/MainDocumentation_HTML/Using_Difference_Flows.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Using_Difference_Flows.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To use the Difference Case tool:

  - Set up a solved power system corresponding to a desired operating point. This operating point will be defined as the [Base](#difference-case).
  - Select **Difference Case** from the Run Mode ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, or select **Difference Case** from the [oneline local menu](15-using-onelines-tools-and-options.md#oneline-local-menu) in Run Mode.
  - On the **Difference Case Dialog,** click the button labeled **Set Present as Base**. This stores the current operating point as the Base.

<!-- end list -->

  - Define the operating point ([Present](#difference-case) ) for which to perform the difference case comparison. The Present may be developed either by modifying the Base as desired and re-solving, or by opening a new case selecting **Open Case** from the [File menu](03-cases-files-and-formats.md#file-menu). In the latter situation, the new case that you open must have the same key field scheme as the Base.
  - See [Difference Case Modes](#difference-case) for information on toggling between modes. The currently displayed mode is shown in the [PowerWorld Simulator Status Bar](01-getting-started.md#status-bar). When viewing either the Base, Difference, or Change the corresponding status bar display will be highlighted.

![image\\ebx\_-1613044881.gif](images/ebx_-1613044881_156x22.gif)

The Difference Case tool can only be used in both Edit Mode and Run Mode.

When showing the Difference, most of the fields shown on the onelines and case information displays show the numerical difference between the present value and its Base value (Present - Base). For example, on the Generator Records Display, an entry of 0.0 in the MW field indicates that the real power output of the generator did not change. An entry of 10.0 in the MW field indicates that the present real power output of the generator is 10 MW greater than it was in the Base .

At any time during a simulation, you can set the Present as the Base by clicking the corresponding button on the Difference Cases Dialog.

If you have made changes to the present, and you wish to revert to some or all of the base values, you can click on the **Reset Case…** button. When you click this button, the dialog will expand to show you options for resetting specific types of values to their base case values.

![Difference Flows](images/Difference_Flows.gif)

Expanded Difference Case Dialog

Once you have indicated which types of values you want to reset (by default, all are selected), you can click on the **Reset Present to Base Values** button to complete the process of reverting to base values. Note: once you have finished resetting to the base values, you can hide the Reset options by clicking the Hide Reset Button in the upper right hand corner of the Reset options panel.

The oneline diagrams and case information displays cannot indicate structural differences in the case very well, such as the addition or removal of a device. To identify such differences, make use of the [Present Topological Differences from Base](#present-topological-differences-from-base-case) tool to identify topology differences.

---

<a id="present-topological-differences-from-base-case"></a>

## Present Topological Differences from Base Case

*Source: [`Content/MainDocumentation_HTML/Present_Topological_Differences_from_Base_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Present_Topological_Differences_from_Base_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Present Topological Differences from Base dialog provides a way to compare the topological differences between two different cases in Simulator. Topological differences are new objects in the case as well as removed objects.

To compare two cases topologically, you must load the first case you wish to use as the reference into Simulator. Use the [Difference Case](#difference-case) tool to set the case as the base in memory. Once this case has been stored as the base, open the second case into Simulator. Now if you check the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose the **Difference Case Menu** on the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group), you will see the option **Present Topological Differences from Base**. Choosing this option will open the dialog to display the topological differences.

At the top of the dialog regardless of where you are navigated to in the tree view structure, there are options for changing the **Difference Case Mode** to either Present, Base, Difference or Change and an option to **Show Present|Base in Difference and Change Mode**. There is also a button for specifying the **Change Tolerances**. ( The Change Mode and related features were added in Added in Version 20). See the [Difference Case](#difference-case) topic for more information on this topic.

The left portion of the dialog has two tabs. Inside each tab is a tree view of many different object types showing by Type and by whether it is a list of objects that are New, Removed, or in Both. The tab **By New/Removed/Both** has the highest level folders of New, Removed, and Both. Under each of those folder is then an Aggregation and Network folder mimicking the groupings found in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) Explore Pane. The **By Type** tab has the highest level folders of Aggregation and Network again, with the object types underneath those, and then folder for Both, New and Removed under this. See image below for example.

Within each tab there are the following entries

Summary

This is the first entry in both tabs and is depicted in the image below. A listing of the types of objects in the case are shown along with columns showning

The New column shows the number of devices in the present case that were not in the base.

The Removed column shows the number of devices in the base case that do NOT exist in the present case

The Both column shows the number of items that were matched between the two cases.

New Elements Case Information Displays

Tabular listings of all objects that exist in the present case, but not in the base case. The can

Removed Elements Case Information Displays

Tabular listings of all objects that exist in the base case, but are not in the present case. A right-click option from the pop-up menu on the Elements Removed tables allows for saving the removed elements selected to a GE EPC file format. Also, above the various removed case information displays, above the Difference Mode features, there is a check box **Assume base Areas/Zones/Owners and Data Maintainers that are not in present case meet the filters**. This check box indicates how those [filtering options](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) work when the base case objects does not belong to an Area/Zone/Owner or Data Maintainer which is not in the present case.

Both Elements in Case Information Displays

Tabular listings of all objects present in both cases.

Create Bus Swap List

This is the last entry in both tabs. It is used for setting up a bus renumbering list. It is possible that discrepancies in topology between the present case and the base case can be due to a difference in bus numbering between the two cases. [Renumbering the buses](19-edit-mode-tools.md#bus-renumbering-dialog) in the present case may take care of most of the topology discrepancies that are reported in this instance.

![Present Topological Differences from Base Case Dialog](images/Present_Topological_Differences_from_Base_Case_Dialog.gif)

Save To \> drop-down menu

The **Save To \>** drop-down menu has several entries for exporting the Elements Added, Elements Removed, and Elements In Both to other files. These options will open a confirmation dialog asking you whether to save (1) All Lists, (2) Only New Elements, (3) Only Removed Elements or (4) Only Both Elements. In addition they may ask how to filter the objects for export giving you a choice of (1) None (All Objects), (2) Use Both Area/Zone/Owner and Data Maintainer Filters, (3) Use Only Area/Zone /Owner Filters, or (4) Use Only Data Maintainer Filters. In addition there is a check box **Assume base Areas/Zones/Owners and Data Maintainers that are not in present case meet the filters** to indicate how filtering should be handled.

Legacy Complete Model (Version 18 and earlier)

This is an legacy feature which attempted to construct an AUX file that converter one case into another. It does not do as complete a job as the newer Complete Model option, so we would not recommend using this any more. This option does not offer option to filter only by Area/Zone/Owner filter or only by Data Maintainer filters.

Removed Objects to EPC File

Use this option to export a special EPC file which exports removed elements to the GE EPC file format using a special status value of -4.

Send Tables to Excel

Choosing this option will go through all the various tables on this dialog and perform an Send to Excel action on every table. The filtering and fields that are presently shown on those tables will be exported

Complete Model

Choose this option to export an Auxiliary file which when loaded back into your original base case will convert the base case to the present case. This feature makes extensive use of the hard-coded Network Model [Auxiliary File Export Format Description](09-auxiliary-files-and-script-commands.md#complete-case-auxiliary-file-export-format-description). A PDF document describing these fields can also be found at at the following link: [Record Format for a Power Flow Case](https://www.powerworld.com/WebHelp/Content/Other_Documents/ExportFormatNetworkModel.pdf). When choosing to export this AUX file an Auxiliary is written which contains the following.

Saving Removed Elements

A series of DATA sections and SCRIPT sections that use the Selected field for objects along with the script command *Delete(objecttype, SELECTED)* to delete objects that were in the base case but are not in the present case. These represent the Removed Elements on this dialog.

Saving New Elements

Special Data Section for Bus Nominal Voltage Changes (\* See description below)

Special Data Section Device Area, Zone, Balancing Authority, and Owner changes (\*\* See description below)

Finally, write out all the various objects that have been new to the case (objects in the present case that were not in the base case)

Saving Both Elements

Write out all the various objects that are in both the present and base case, but only write out the values that have changed. This makes extensive use of the **Change Mode** of the [Difference case](#difference-case) tool. In addition you will see some object types be split into 2 separate data sections representing fields that normally don't change and those that often do. For example, the bus field Vpu and Vangle are written in a separate Data section from the other fields of a bus.

Special Handling is done with three-winding transformer star bus numbers. A section of AUX file may be written to renumber star bus numbers at the beginning of the Both Element objects.

**\*Special Data Section for Bus Nominal Voltage Changes:**

A list of BRANCH or 3WXFormer object that meets the following special conditions will be determined

1\. The BRANCH or 3WXFormer is an added object (exists in the present case, but did not exist in the base case)

2\. A terminal bus of this branch is in both the present and base case

3\. The terminal bus has a nominal voltage that changed between the present and base case

For these terminal buses found, an extra bus data section will be written which changes the nominal voltage before we write out the newly added objects. This is done because internally in PowerWorld Simulator the impedances and tap information for these objects are stored on the system base (meaning the nominal voltage of the bus impacts this). Thus as we read the branch information in on the <span class="underline">transformer base</span>, and then go and change the bus nominal voltages later, this means that the *transformer base* values automatically change. This is not desired behavior in this situation.

**\*\*Special Data Section Device Area, Zone, Balancing Authority, and Owner changes:**

The ownership of many objects is automatically synchronize their ownership with their terminal bus owner if the device and bus share the same owner. Thus if in the base case a load with owner XYZ is connected to a Bus with owner of XYZ, and then the bus owner has been changed to ABC in the present case , then within PowerWorld Simulator the owner of the load is automatically changed as well. (If the load object had a different owner to start with, then it would not automatically). The same behavior applies to the area, zone, and balancing authority designation of a load, shunt, or generator object.

This is desired behavior most of the time, but causes trouble for this feature in a special situation. Consider the following situation:

Base Case: Bus Owner = 21 and Load Owner = 21

Present Case: Bus Owner = 45 and Load Owner = 21

The problem is that strictly speaking the load owner in this situation *has not changed*, however if we write an AUX file that changes the bus owner then when loading the AUX file we may also automatically change the load owner which is not desired behavior. To prevent this from happening, the software detects these situation and then writes out special Bus Data section the change the bus owner, area, zone, or balancing authority designations before the new objects connected to these buses are created.

Special Object Types for Removed objects

To provide easier access to the objects that have been identified as being removed when viewing the topological differences, special object types have been created that allow these objects to be accessed via script commands. These objects provide access to the Elements Removed. All of the object names start with *Removed* with the rest of the name just being the usual object name. To identify buses use the object name *RemovedBus*. To get generators use *RemovedGen*, etc. These objects can be accessed through the [SaveData](03-cases-files-and-formats.md#auxiliary-file-format-aux) script command and [GetParametersMultipleElement](34-simauto-functions.md#getparametersmultipleelement) through SimAuto. If these object types are loaded back into Simulator, the corresponding objects will be deleted if you are in Edit Mode.

A field is available for all object types that can be used with the difference flows tool. This field is found under **Difference Case\\In Diff Base** and indicated whether or not an object was in the difference flows base case. This field is useful for filtering only the new elements that are only in the present case, field value = NO, or all of the elements in both the present and base case, field value = YES. This will make it possible to use script actions or filters to return only the Elements Added or Elements In Both.

---

<a id="fixednumbus-features"></a>

## FixedNumBus Features

*Source: [`Content/MainDocumentation_HTML/FixedNumBus_Features.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBus_Features.htm)*

The concepts of SuperBus and Subnet has been in PowerWorld Simulator since 2006. The concept of FixedNumBus was added in Version 24

What is a Bus? This is a fundamental concept that all power engineers feel like we know, but when defining it precisely, it becomes less clear. Many network objects in our power system model are a physical device that is easy to define: transformers and series capacitors for example. An engineer can walk into a substation and point at the device. Transmission lines get more complicated, but they still represent a piece of equipment. The concept of a bus however does not represent a physical device, and depending on the software tool or the engineer using the word "bus" they may mean either (1) **a singular point** where devices connect to each another, (2) *a group of points* that share a voltage phasor in a software calculation, or (3) *a user defined group of points* that may represent several voltage phasors. That is at least 3 different concepts being tied to the same word. Only the <span class="underline">singular point</span> concept has some tie to the physical world and even that is not easily described as you will see below. All of these concepts are abstract concepts used by software toola and if you compare multiple software tools you will find that they use the same word "Bus" to describe different concepts.

In PowerWorld there have 4 different objects that are related to these concepts and they are as follows

Bus (a singular connection point)

A Bus defines the physical location where other devices connect to the power system. Load, generator, and switched shunt objects in the power system model have a terminal bus at which they are connected. In addition they have a voltage regulation point which is defined as a bus. AC branch devices (lines, 2-winding transformers, series caps, breakers, disconnects, etc...) have two terminal buses at which they are connected. 3-winding transformers have 3 terminal buses. A restriction for a bus however is that no single device can have two of its terminals connect to the same bus. A Bus can represent many different things in the physical system: a BusBar inside a substation, the point where disconnect switches connect to transformer bushings, a tap on a transmission tower, and a multitude of others.

A Bus has a unique voltage phasor which is fundamental to the network calculations done. All software tools that model a power system have this concept somewhere in their data structure because this is the unique voltage phasor calculated in these software tools. Energy Management Systems (EMS) software tools often call this concept a Node. When PowerWorld Corporation started working with full-topology models used in EMS system in 2006, we made the choice to continue calling this software object a "Bus" inside PowerWorld Simulator.

SuperBus (group of connection points connected by closed switching or extremely low impedance devices)

SuperBus objects are <span class="underline">automatically determined</span> by software. Every time a new branch is defined or a branch status changes from OPEN to CLOSED or from CLOSED to OPEN, the SuperBus objects will be automatically redetermined the next time they are needed.

Branch objects have a field specifying a BranchDeviceType with the choices described in the help topic [Integrated Topology Processing: Full-Topology Model](35-integrated-topology-processing.md#full-topology-model). A SuperBus is a group of Buses (connection points) that are connected by other **closed** AC branches that have an extremely low impedance which include the BranchDeviceTypes Breaker, Load Break Disconnect, Disconnect, ZBR, Fuse, and Ground Disconnect. This leaves only the BranchDeviceTypes Line, Transformer, TransformerWinding, and SeriesCap that are not considered extremely low impedance.

When performing Integrate Topology Processing power flow calculations, each SuperBus will have one voltage phasor calculated and all Buses inside the SuperBus will share the same voltage phasor.

Subnet (group of connection points connected by any switching or extremely low impedance devices)

Subnet objects are <span class="underline">automatically determined</span> by software. They are the similar to SuperBus objects, but when automatically determining these groupings the status of the branch is ignored.

FixedNumBus (group of connection points defined by the user) Added in Version 24

Background on creation of a FixedNumBus

Each object in PowerWorld Simulator has a [list of key fields](04-model-explorer-and-case-information-part3.md#key-fields) which uniquely identify an object within the software data structure. Since the very beginning of power system software a convention has been used which defines the terminal bus integer number for many objects as the key field for those objects. This includes objects such as AC Branch, Gen, Load, Shunt, etc. Thus for a generator for example, the primary key fields are the terminal bus number and an 2-character string ID to uniquely identify multiple generators at the bus. This long ago choice has created a lot of problems for the industry because changing just a single bus number will impact the unique keys of all the devices connected to that bus. Thus changing 1 bus number may impact the keys for 10 more devices: 1 bus that has 2 generators, 1 load, and 7 branches connected to it would break the key fields for 10 devices. This has meant that other data source files such as contingency lists, limit monitoring, oneline diagrams, and more will no longer work when the bus numbers change. In 2001, PowerWorld added the concept of [string identifiers called labels](07-object-properties-run-mode-and-general-part2.md#labels) which would remain unchanged or fixed even as the terminal bus numbers may change. Our customers who work with EMS system models have used those label identifiers to create contingency lists, monitoring lists, scheduled outage files, linking to SCADA measurements, and oneline diagrams which do not rely on unchanged bus numbers to continue to function as the underlying model topology changes. While we continue to encourage all customers to make use of label identifiers, the PSS/E software platform has added a feature we call a FixedNumBus which creates a distinction between a integer terminal number of a device used as a key field which is a fixed number. This FixedNumBus however can have multiple connection points inside it and thus multiple voltage phasors associated with it.

Assignment of a FixedNumBus

Each bus is assigned a link to a bus that will act as its "Fixed Number Bus" or **FixedNumBus**. By default, every bus will point to itself and thus use its own bus number. The assignment of the FixedNumBus of a Bus is done by typing an integer in the Bus Field named FixedNumBus, loading an AUX file that assigns this field, or when loading special Substation sections of PSS/E RAW Version 34 and later text files. Before accepting the assignment of a bus to a FixedNumBus, Simulator will require that there are not any Branch objects that connect 2 buses inside the same FixedNumBus. If such an assignment is attempted, PowerWorld will ignore the assignment and a message will be written to the [message log](01-getting-started.md#message-log).

Also, after assigning a Bus to a new FixedNumBus several changes may be made to the power system model automatically to harmonize the data definitions. All of these changes are done to harmonize the definition of a FixedNumBus inside Simulator and also to ensure it maintains the structure required when writing back out to a PSS/E RAW Version 34 or later text file.

> 1.  The Bus being assigned will have its NomkV, Substation, Area, Zone, and Owner field chanced to match the values at the FixedNumBus .
> 
> 2.  In addition when editing these fields at buses that below to a FixedNumBus, the fields at all other buses within the FixedNumBus will be changed to match one another.
> 
> 3.  If any Load, Gen, Shunt, Branch objects that are connected to the Bus being assigned will now match the 2-character ID strings of other objects in the FixedNumBus grouping, then 2-character ID strings will be changed so there are not conflicts and a message written to the [message log](01-getting-started.md#message-log) indicating this. The image below shows the constraints on the 2-character IDs.
> 
> <table>
> <tbody>
> <tr class="odd">
> <td> </td>
> <td><p>All buses in the image below are assigned to the same FixedNumBus. When adding the new load boxed in yellow, the ID can not be set to either 1 or 2 because other buses within the FixedNumBus already use this ID.</p>
> <img src="images/FixedNumBus_LoadIDConstraint.png" alt="FixedNumBus LoadIDConstraint" /></td>
> <td><p>Buses on the left below are assigned to FixedNumBus = 1234 and buses on the right are assigned to FixedNumBus = 5678. Existing branches between these groupings used Circuit 1 and 2. When assigning a new Branch between these groupings the new ID must not be 1 or 2.</p>
> <img src="images/FixedNumBus_BranchIDConstraint.png" alt="FixedNumBus BranchIDConstraint" /></td>
> </tr>
> </tbody>
> </table>

SubNodeNum

For supporting PSS/E RAW files, PowerWorld also includes an integer with each bus called a SubNodeNum. In PowerWorld Simulator this integer is not important, but when writing out to a RAW file these integers must be unique for each bus within a substation. When loading a RAW file each bus will be assigned to a FixedNumBus and a SubNodeNum. In the RAW file the SubNodeNum must be between 1-999 and the FixedNumBus must be between 1-999999. To make things reproducible when reading RAW files PowerWorld reads both these values and then creates a bus number equal to 1000000\*SubNodeNum + FixedNumBus (except when the SubNodeNum is 1 in which case the bus number is simply FixedNumBus).

Uses of FixedNumBus

The FixedNumBus designations impact how a user interacts with the power system model several locations.

> 1.  [User Interface Interactions such as the Bus View, Case Information Displays, Object Dialog (described in a separate help topic)](#user-interface-interactions)
> 
> 2.  [Oneline diagram FixedNumBus features (described in a separate help topic)](17-oneline-view-printing-and-contouring.md#displaybus-property-allowfixednum)
> 
> 3.  [FixedNumBus comes from the RAW version 34 and later formats (described in a separate help topic)](#fixednumbus-relationship-to-raw-format)
> 
> 4.  [Interacting with text files such as Auxiliary Files and other PSS/E formats such as CON and MON Files (described in a separate help topic)](#fixednumbus-in-aux-and-other-text-files)

Visualization of Bus, Subnet, SuperBus and FixedNumBus

An example system with these concepts visualized is shown below. Each black line segment represents a Bus in PowerWorld Simulator. The groupings of buses are then represented by different colored regions with Subnet in pink, SuperBus in yellow, and FixedNumBus in blue.

<table>
<tbody>
<tr class="odd">
<td><p>Each pink region represents a Subnet. These grouping are automatically determined by PowerWorld. In this example, we are only showing buses at a single nominal voltage level so the Subnet designation is the same as a Substation. All objects in the Subnet are connected by extremely low impedance branches or switching devices. All connections between a Subnet will be either Transmission Line, Transformer, Series Cap, or TransformerWinding (of a 3-winding transformer)</p></td>
<td><p>Each yellow region represents a SuperBus. These grouping are automatically determined by PowerWorld. A SuperBus will always be contained inside of a single Subnet. The connections between SuperBus objects inside the same Subnet will be open switching devices denoted in the image below by purple circles.</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p><img src="images/FixedNumBus_Subnet.png" alt="FixedNumBus Subnet" /></p>
<p> </p></td>
<td><img src="images/FixedNumBus_SuperBus.png" alt="FixedNumBus SuperBus" /></td>
</tr>
<tr class="odd">
<td><p>Each blue region represents a FixedNumBus grouping. These grouping are user-specified. They will normally be inside the same Subnet and all buses inside a FixedNumBus grouping will normally be connected to each other, and we would recommend that, but that is not required. In PowerWorld Simulator there is nothing different about the switching devices that connect between two FixedNumBus within the same substation, but within the PSS/E format these in a special section of the RAW file called the "System Switching Devices. See the help topic on <a href="#fixednumbus-relationship-to-raw-format">FixedNumBus and RAW Format</a> for more information.</p></td>
<td><p>The image below here is showing both the FixedNumBus and the SuperBus groupings. Each orange outline represents the SuperBus groupings and you will notice the open switching devices connecting them. Each blue region respresents the FixedNumBus groupings. This is image is here to emphasize that a SuperBus and FixedNumBus are not the same thing.</p></td>
</tr>
<tr class="even">
<td><a href="https://www.powerworld.com/WebHelp/Content/Images/FixedNumBus_FixedNumBusAndSuperBus.png"><img src="images/FixedNumBus_FixedNumBus.png" alt="FixedNumBus FixedNumBus" /></a></td>
<td><img src="images/FixedNumBus_FixedNumBusAndSuperBus.png" alt="FixedNumBus FixedNumBusAndSuperBus" /></td>
</tr>
</tbody>
</table>

---

<a id="fixednumbus-in-aux-and-other-text-files"></a>

## FixedNumBus in AUX and other Text Files

*Source: [`Content/MainDocumentation_HTML/FixedNumBus_TextFileUses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBus_TextFileUses.htm)*

Added in Version 24

Bus objects can be assigned to a FixedNumBus as described in the help topic [Fixed Number Bus (FixedNumBus) Features](#fixednumbus-features). When this is done it adds additional ways to describe objects using a text string in various other file formats such as the PowerWorld Simulator AUX file or the PSS/E \*.con and \*.mon files. To illustrate this the image below shows two buses and various network objects attached to those buses. The image depicts

  - Bus on the left is number 3002425 and has been assigned to FixedNumBus 2425

  - Bus on the right is number 20003057 and has been assigned to FixedNumBus 3057

  - The left bus has a load object connected to it with ID=1

  - The right bus has a generator object connected to it with ID = 2

  - There is a branch connecting both buses with circuit = AB

![FixedNumBus Identifiers](images/FixedNumBus_Identifiers.png)

Single String Object Identifiers

PowerWorld would traditionally refer to the load object using the string "Load 30002425 1". However, with the FixedNumBus designation, the load can also be referred to as "Load 2425 1". Both of these would be equivalent. These strings might be used in the Object field of a ContingencyElement for example. These same type of strings using in various other formats such as \*.con and \*.mon files from PSS/E will function the same way. This also impacts all the places in PowerWorld's AUX file format where an object string is used as described in the help topic [ObjectID Field for use in Auxiliary Files](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels).

<table>
<tbody>
<tr class="odd">
<td><p>Load on Left</p>
<p> </p></td>
<td><p>The follow 2 strings will both describe this load</p>
<p>"Load 3002425 1"</p>
<p>"Load 2425 1"</p></td>
</tr>
<tr class="even">
<td><p>Generator on Right</p>
<p> </p></td>
<td><p>The follow 2 strings will both describe this generator</p>
<p>"Gen 20003057 2"</p>
<p>"Gen 3057 2"</p></td>
</tr>
<tr class="odd">
<td><p>Branch</p>
<p> </p></td>
<td><p>The follow 2 strings will both describe this branch</p>
<p>"Branch 3002425 20003057 AB"</p>
<p>"Branch 2425 3057 AB"</p>
<p>Note that if the FixedNumBus is used at one terminal it must also be used at the second terminal. Thus the following string would not be a valid: "Branch 3002425 3057 AB"</p></td>
</tr>
</tbody>
</table>

Fixed Number Bus in a CON file

As mentioned above, the FixedNumBus will also be used to search for objects in a CON file. See the following image for an example.

![FixedNumBus CONFile](images/FixedNumBus_CONFile.png)

Special Treatment in an AUX file with keyfields

Some other special treatment is available inside an AUX file for objects identifying. The key fields that show a bus number can be populated via a SimAuto command, Copy/Paste from Excel, or an AUX file using the FixedNumBus integers as well. Thus you would normally expect that to change the MW load in the example above the AUX file would have the following syntax

<table>
<tbody>
<tr class="odd">
<td><p>Traditional AUX</p>
<p>File Numbers</p></td>
<td><pre><code>   Load (BusNum,ID,MW)
   {
   3002425 &quot;1&quot; 123.45
   }</code></pre></td>
<td><pre data-space="preserve"><code>   Gen (BusNum,ID,MW)
   {
   20003057 &quot;2&quot; 123.45
   }</code></pre></td>
<td><pre data-space="preserve"><code>   Branch (BusNumFrom,BusNumTo,ID,LimitMVAA)
   {
   3002425 20003057 &quot;AB&quot; 123.45
   }</code></pre></td>
</tr>
<tr class="even">
<td><p>These will also work</p>
<p>by using FixedNumBus</p></td>
<td><pre><code>   Load (BusNum,ID,MW)
   {
   2425 &quot;1&quot; 123.45
   }</code></pre></td>
<td><pre data-space="preserve"><code>   Gen (BusNum,ID,MW)
   {
   3057 &quot;2&quot; 123.45
   }</code></pre></td>
<td><pre data-space="preserve"><code>   Branch (BusNumFrom,BusNumTo,ID,MW)
   {
   2425 3057 &quot;AB&quot; 123.45
   }</code></pre></td>
</tr>
</tbody>
</table>

---

<a id="save-merged-fixednumbus-case"></a>

## Save Merged FixedNumBus Case

*Source: [`Content/MainDocumentation_HTML/FixedNumBus_SaveMergedCase.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBus_SaveMergedCase.htm)*

Added in Version 24

Fully Topology cases are best used when using PowerWorld Simulator's Integrated Topology Processing Add-on. Without this add-on you can use many features to navigate looking at the power system model, but the numerical solutions will not be as effective and reliable.

You can however use a special feature in the File menu of the program to choose

**File\\Save Merged FixedNumBus Case**

This will save a case (PWB or RAW file) which includes all the FixedNumBus and any additional bus needed because the FixedNumBus has been split into multiple electrical points and thus has multiple voltage/angle phasors. For example, in the image below you original case is represented by the top portion of the image. In this example, we assume that the LEFT, MIDDLE, and RIGHT shaded regions represent 3 different FixedNumBus groupings in the case. When choosing to save a Merged FixedNumBus case, the resulting case will have 4 buses in it. This is because the LEFT ring bus has been split into 2 electrical points and in order to maintain the integrity of the case we must have separate voltage phasors.

![FixedNumBus SaveMerged](images/FixedNumBus_SaveMerged.png)

---

<a id="user-interface-interactions"></a>

## User Interface Interactions

*Source: [`Content/MainDocumentation_HTML/FixedNumBus_UserInterfaceInteractions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBus_UserInterfaceInteractions.htm)*

Added in Version 24

When a case has been configured with [buses assigned to FixedNumBus grouping](#fixednumbus-features)s, then portions of the user interface will behave differently. In particular the Case Information Displays, User Interface Dialogs, and the Bus View will include additional features.

Case Information Display FixedNumBus features

Many case information tables will include additional default columns for FixedNumBus or SubNodeNum when cased have FixedNumBus defined.

  - FixedNumBus : For the object table shown which has a bus number, this will be the FixedNumBus to which that bus is assigned. On a table of Bus objects this field can be edited as described in [Fixed Number Bus (FixedNumBus) Features](#fixednumbus-features).

  - SubNodeNum : On a bus table this field is also shown which can be edited and is described in [Fixed Number Bus (FixedNumBus) Features](#fixednumbus-features).

The images below show these extra columns boxed in red.

<table>
<tbody>
<tr class="odd">
<td><p>On some of the bus case information displays special <strong>Filter By</strong> choices are shown.</p>
<p>These allow you to filter the table to show <strong>All</strong> buses, <strong>FixedNumBus Only</strong>, or <strong>SuperBus Only</strong>.</p></td>
<td><img src="images/FixedNumBus_BusCaseInfoFilterBy.png" alt="FixedNumBus BusCaseInfoFilterBy" /></td>
</tr>
<tr class="even">
<td><p>On some of the Branch case information displays, a special <strong>Filter By BranchType</strong> option is shown on the left of the table. A list of checkboxes are then shown with available BranchDeviceType.Check and uncheck these to filter the display by these types.</p></td>
<td><img src="images/FixedNumBus_BranchCaseInfoFilterBy.png" alt="FixedNumBus BranchCaseInfoFilterBy" /></td>
</tr>
</tbody>
</table>

Gen, Load, Shunt, Branch Object Find Dialogs

There are many places in PowerWorld Simulator where a dialog box is used to Find an object. This dialog may be opened as a stand-alone dialog or it may be embedded inside another dialog. These dialogs are described elsewhere in the help at [Find Dialog/Object Chooser](04-model-explorer-and-case-information-part3.md#find-dialog-basics). For objects to which FixedNumBus fields are relevant, these Find Dialogs wll be changed to include ways to search by Bus or by FixedNumBus.

For example on the Gen, Load and Shunt Find Dialogs there will be a drop-down that has 3 choices to choose (1) By Bus Only, (2) by Bus and FixedNumBus, or (3) by FixedNumBus Only. An example image is the next image. The entries in the find dialog in Blue represent identifiers using the FixedNumBus while the entries in black are using the bus number. Note that when choosing to show by Bus and FixedNumBus that the same object may appear twice in the list as it can be identified in 2 different ways.

![FixedNumBus FindGenDialog](images/FixedNumBus_FindGenDialog.png)

Similar options will appear for a Branch object as well

![FixedNumBus FindBranchDialog](images/FixedNumBus_FindBranchDialog.png)

Bus View

Bus View onelines are very useful for navigating the topology of the power system model. These are described generally in the [Bus View Display](#bus-view-display) help topic. There is a dropdown with 4 choices

1.  Full Topology

2.  Consolidated SuperBus

3.  Consolidated Subnet

4.  Consolidated FixedNumBus

Choose the option as desired and you will only see connections to other SuperBus, FixedNumBus or Subnet.

![FixedNumBus BusViewConsolidatedFixedNumBus](images/FixedNumBus_BusViewConsolidatedFixedNumBus.png)

![FixedNumBus BusViewConsolidatedSuperBus](images/FixedNumBus_BusViewConsolidatedSuperBus.png)

---

<a id="fixednumbus-relationship-to-raw-format"></a>

## FixedNumBus Relationship to RAW Format

*Source: [`Content/MainDocumentation_HTML/FixedNumBus_RAWFileFormat.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBus_RAWFileFormat.htm)*

Support for this was added in Version 24. In Simulator Version 23 we could read these files, but we would not maintain the FixedNumBus structures in Simulator and the nodes inside substation would be assigned an unused number.

There are some fundamental data structure differences between PowerWorld's data structure and the structure described in the RAW file format. For example, Substation objects in PowerWorld Simulator have no bearing on the existing of full topology models. Substation objects have existed in PowerWorld Simulator since about 2000 and a Substation is purely a grouping of Bus objects. You can create substations for your entire system model and assign each bus to a substation even in a case that does not model any switching devices. In the RAW file data structure however, the existance of a substation is intertwined with the concept of topology and nodes. A general summary of the structure

<table>
<tbody>
<tr class="odd">
<td><p>PowerWorld Simulator</p></td>
<td><p>RAW file data structure</p></td>
</tr>
<tr class="even">
<td><ul>
<li><p>Bus</p>
<ul>
<li><p>Number.</p>
<ul>
<li><p>For RAW file PowerWorld assigns a number equal to<br />
1000000*SubNodeNum + FixedNumBus<br />
(except for SubNodeNum=1 is FixedNumBus)</p></li>
</ul></li>
<li><p>Can be assigned a FixedNumBus</p></li>
<li><p>Can be assigned to a Substation</p></li>
<li><p>Assigned a SubNodeNum between 1-999 to maintain RAW file compatiblity. This is not required for PowerWorld.</p></li>
</ul></li>
<li><p>Branch</p>
<ul>
<li><p>Have a BranchDeviceType specified as described in <a href="35-integrated-topology-processing.md#full-topology-model" class="MCXref xref">Integrated Topology Processing: Full-Topology Model</a>.</p></li>
</ul></li>
<li><p>Substation objects</p></li>
</ul></td>
<td><ul>
<li><p>A Bus described at the top of the RAW file actually represents a group of Nodes (PowerWorld would call this a FixedNumBus). In this description below we will call it a PSSE_Bus.</p>
<ul>
<li><p>A PSSE_Bus can have multiple voltage phasors associated with it as the PSSE_Bus can be split inside the substation</p></li>
<li><p>PSSE_Bus has a number between 1-999999 which is unique</p></li>
</ul></li>
<li><p>System Switching Devices are listed separately at the top of the RAW file similar to the way Lines and transformers are listed.</p>
<ul>
<li><p>Each switching device has a "Device type" which is either a 1, 2 or 3. PowerWorld maps these types to 1=ZBR, 2=Breaker and 3=Disconnect</p></li>
</ul></li>
<li><p>Substation objects are special structures at the bottom of the RAW file</p>
<ul>
<li><p>Each substation has its own list of Nodes in it.</p>
<ul>
<li><p>Each Node has a number between 1-999 that is unique within the substation</p></li>
<li><p>Each Nodes must be assigned to a one PSEE_Bus objects listed at the top of the RAW file. Every node assigned to a PSSE_Bus could have a different voltage phasor depending on the status of switching devices</p></li>
<li><p>Nodes in 2 different substations can not be assigned to the same PSEE_Bus</p></li>
</ul></li>
<li><p>Each substation has a list of Substation Switching Devices. These devices must be between 2 nodes inside the substation and each of those nodes must be assigned to the same PSSE_Bus. If a switching device connects 2 different PSSE_Bus objects then it can NOT be list in this section and must instead be listed in the special System Switching Devices list mentioned above.</p>
<ul>
<li><p>Each switching device has a "Device type" which is either a 1, 2 or 3. PowerWorld maps these types to 1=ZBR, 2=Breaker and 3=Disconnect</p></li>
</ul></li>
<li><p>Every object that connects to any node in the substation must have additional records to represent the Terminal Data connection. Thus there are special entries for</p>
<ul>
<li><p>1 for each generator</p></li>
<li><p>1 for each load</p></li>
<li><p>1 for each switched shunt</p></li>
<li><p>2 for each branch</p></li>
<li><p>2 for each system switching device</p></li>
<li><p>2 for each 2-winding transformer</p></li>
<li><p>3 for each 3-winding transformer</p></li>
<li><p>2 for each DC transmission line</p></li>
<li><p>and so on</p></li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

As an example, consider the system topology depicted in the following image

![FixedNumBus FixedNumBus](images/FixedNumBus_FixedNumBus.png)

RAW File Top portion for PSSE\_Bus, Branch, System Switching Devices

Below is a concentration of only Substation 3053 which is represented in the RAW file data structure. The top portion of the RAW file contains the following

  - 4 PSSE\_Bus objects number 3053, 3055, 3057 and 3058 (highlighted in red below)

  - 7 Branch objects which represent transmission lines between these PSSE\_Bus objects (highlighted in blue below)

  - 4 System Switching Devices that represent ZBR, Breaker, or Disconnect (highlighted in green below)

![FixedNumBus RAWFileTopPart](images/FixedNumBus_RAWFileTopPart.png)

One Substation section at the bottom of a RAW file

At the bottom of the RAW file is then a section for Substation and then the Substation Nodes, Switching Devices and Terminal Data.

![FixedNumBus RAWSubstation](images/FixedNumBus_RAWSubstation.png)

Substation Node Data

A close-up of the Substation Node Data is shown next and illustrates how some of the PSSE\_Bus objects have been split into different electrical points and thus must include the voltage and angle in their definition. It also illustrates how PowerWorld assigned a bus number equal to

PowerWorld Bus Number = SubNodeNum \* 1000000 + FixedBusNus.

![FixedNumBus RAWSubstationNode](images/FixedNumBus_RAWSubstationNode.png)

Substation Terminal Data

![FixedNumBus RAWSubstationTerminalData](images/FixedNumBus_RAWSubstationTerminalData.png)
