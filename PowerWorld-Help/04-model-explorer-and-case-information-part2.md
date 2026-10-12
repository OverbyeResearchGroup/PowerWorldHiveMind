---
title: "Model Explorer and Case Information Displays (Part 2 of 3)"
part: "Viewing Case Data"
chapter_file: "04-model-explorer-and-case-information-part2.md"
topics: 13
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Model Explorer and Case Information Displays (Part 2 of 3)

Model Explorer and the mechanics of case information displays: filtering, sorting, columns, formats.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (13)**

- [Case Information Filterbar](#case-information-filterbar)
- [Area/Zone/Owner and DataMaintainer Filters](#areazoneowner-and-datamaintainer-filters)
- [Advanced Filtering](#advanced-filtering)
- [Advanced Filters Dialog](#advanced-filters-dialog)
- [Advanced Filters View Filter Logic Graphical Display](#advanced-filters-view-filter-logic-graphical-display)
- [Advanced Filtering: Advanced](#advanced-filtering-advanced)
- [Advanced Filtering: Device](#advanced-filtering-device)
- [Advanced Filters Display](#advanced-filters-display)
- [Expressions](#expressions)
- [Expressions Display](#expressions-display)
- [String Expressions](#string-expressions)
- [Functions and Operators Available](#functions-and-operators-available)
- [Model Expressions](#model-expressions)

---

<a id="case-information-filterbar"></a>

## Case Information Filterbar

*Source: [`Content/MainDocumentation_HTML/Case_Information_Filterbar.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Filterbar.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

On the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer), directly above the case information display is the Case Information Filterbar. Although the Filterbar is not shown by default on other case information displays not embedded in the Model Explorer, the Filterbar can be shown by right-clicking on the Case Information Toolbar and choosing **Filterbar\>Top** or **Filterbar\>Bottom**. The Filterbar is shown in the following image.

![Model Explorer Case Info Filterbar](images/Model_Explorer_Case_Info_Filterbar.gif)

For some object types it is possible to filter based on data for a related object class instead of for the actual object class. For example, an Advanced Filter for a Bus may exist to only show buses with a Nominal Voltage larger than 138 kV. You may then want to use this filter on a case information display which shows generators. For object types which support this feature, the **Filter By Dropdown** and the **Filter Type Dropdown** will be available. For objects which do not support this, these dropdowns will not be visible.

Filter By Dropdown

This value will be either *Advanced* or *Device*. For more information about this setting see the [Advanced Filtering Dialog](#advanced-filters-dialog) help.

Filter Type Dropdown

This dropdown allows you to specify which class to base the filter on. For more information about this setting see the [Advanced Filtering Dialog](#advanced-filters-dialog) help.

List of Filters or Devices Dropdown

When the **Filter By Dropdown** is set to *Advanced*, this dropdown will contain a list of all the presently defined advanced filters for the object type specified in the **Filter Type Dropdown**.

When the **Filter By Dropdown** is set to *Device*, this dropdown will contain a list of all objects of the object type specified in the **Filter Type Dropdown**.

When clicking on this dropdown the appropriate list will be shown and by choosing an entry from this dropdown the respective advanced or device filter is applied to the case information display. Also, if the dropdown contains more than 1,000 entries in it, clicking on this dropdown will instead have the same effect as clicking on the **Find... Button**.

Find... Button

Click on this button to open the [Advanced Filtering Dialog](#advanced-filters-dialog) for the case information display.

Remove Button

Click this button to remove the [Advanced Filter](#advanced-filtering) or [Quick Filter](52-additional-linked-topics-part1.md#quick-filter) from the present case information display. This does not delete an advanced filter definition, but only removes the reference to it from the active case information display. The filter can easily to reapplied after removing it. If you would like to permanently delete an Advanced Filter see [Advanced Filtering.](#advanced-filtering)

Quick Filter Drop Down

Click this button to open a menu with options regarding defining a [Quick Filter](52-additional-linked-topics-part1.md#quick-filter). There are methods of provide open the Quick Filter dialog, Clear the Quick Filter, change the Boolean logic, as well as quickly add a condition to the quick-filter using the column in which the cursor is currently set in the display. See the [Quick Filter](52-additional-linked-topics-part1.md#quick-filter) help for more details.

---

<a id="areazoneowner-and-datamaintainer-filters"></a>

## Area/Zone/Owner and DataMaintainer Filters

*Source: [`Content/MainDocumentation_HTML/Area_Zone_Owner_Filters.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Zone_Owner_Filters.htm)*

Anywhere in the help documentation or the software that reference is made to either "Area/Zone filtering" or "Area/Zone/Owner filtering" this really refers to the all Area, Zone, Owner, and Data Maintainer filtering. This is done for brevity.

The Area/Zone/Owner Filters Dialog allows you to filter the information shown on the [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) and other dialogs by area, zone or owner. There are a several ways to open the Area/Zone/Owner Filters Dialog.

  - Go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose**![AreaZoneFilterButton](images/AreaZoneFilterButton.gif)Area/Zone/Owner Filters** from the **Case Information** ribbon group
  - Click on the button ![Model Explorer Case Info Toolbar AreaZone Filter](images/Model_Explorer_Case_Info_Toolbar_AreaZone_Filter.gif)on the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar)
  - There are also many buttons on user interface dialogs throughout the program that invoke this dialog as well.

Added in the Version 20 build on October 17, 2017, you may also use [Data Maintainer](07-object-properties-run-mode-and-general-part1.md#datamaintainer) filtering, which will be ANDED with the Area/Zone/Owner filtering. To do this you must first define appropriate Data Maintainers, then check the box **Use Data Maintainers Filtering on Case Information Displays**. This same check box option is also available in the Options drop-down on the [Case Information Display Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar).

For small cases, you will usually not need to use this filtering capability, but it can be very useful for large cases. The filters display lists each area, zone and owner in the case, the number of buses in each, the range of bus numbers contained in each, and whether or not information about that area, zone or owner should be displayed. In order for a device to be displayed, its Area, Zone, Owner and DataMaintainer Filter property must be set to yes. For devices which can belong to more than one area, zone, or owner (for instance a transmission line that connects two areas, i.e. a tie line), then the device will be displayed if any end of the device meets the area/zone/owner filter. For devices that have multiple owners then if any owner is meets the filter the device will.

You can switch between displaying the filters for the case areas, zones, owners, or DataMaintainers by clicking on the associated tab.

The area/zone/owner/datamaintainer filters list is itself a case information display and therefore shares many of the same [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) options and characteristics. Using the local menu, you can search for an area, zone or owner by number or by name, copy records to and from other applications, and send the records to a printer. You can inspect an area, zone or owner by selecting *Show Dialog* from the local menu, which invokes the [Area Information](07-object-properties-run-mode-and-general-part2.md#area-information), [Zone Information](06-object-properties-edit-mode-part3.md#zone-information), [Owner Information](05-case-information-displays-by-object-part3.md#owner-dialog) Dialogs. You can also change the format and content of the filters display by selecting the [Display Column/Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) item from the local menu. The records can be sorted by any of its component fields simply by clicking the corresponding column’s heading.

On each tab there is an enterable field entitled *Shown*, which may assume only the values Yes and No. For example, if the Area/Zone/Owner Filters setting for an area is *No*, then any case information display configured to enforce area/zone/owner filters will omit the area’s elements from the resulting record set. You can specify whether a particular case information display enforces filters using the display’s [Display/Column Options Dialog](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays).

Double-click on a cell in the *Shown* field to toggle its value. Use the [cell handle](04-model-explorer-and-case-information-part1.md#using-cell-handles) to propagate a particular value to multiple areas, zones or owners, or use the *Toggle All Yes* or *Toggle All No* local menu options to set the values of all area, zone or owner records.

---

<a id="advanced-filtering"></a>

## Advanced Filtering

*Source: [`Content/MainDocumentation_HTML/Advanced_Filtering.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Filtering.htm)*

Filtering by areas, zones and owners using [Area/Zone/Owner Filtering](#areazoneowner-and-datamaintainer-filters) is a quick and simple way to filter, however Simulator also contains the ability to perform custom filtering on case information displays as well. Advanced Filtering is accessed by clicking on the [Case Information Toolbar Filtering Menu](04-model-explorer-and-case-information-part1.md#filtering-menu) and choosing Advanced Filter or right-clicking on a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and choosing Advanced Filter from the local menu. This brings up the [Advanced Filters Dialog](#advanced-filters-dialog), which allows you to custom filter the information in the display. Advanced Filters require a filter name, and are stored with your power system case.

Note that you can also use the [Quick Filter](52-additional-linked-topics-part1.md#quick-filter) option on a case information display to set conditions for a filter just as you would for an advanced filter, without requiring a filter name. Quick filter conditions are not saved with the load flow case.

A [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) will have the phrase "Filter: *Name of Filter*" in its caption if an Advanced Filter has been applied to it. To remove a filter from a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), choose Remove Filter from the Case Information Toolbar Filtering Menu or bring up the [Advanced Filters Dialog](#advanced-filters-dialog) and click on **Remove**. Note that Remove does NOT delete the filter, but just stops using it to filter the data. You can always remove the filter temporarily and then come back and reapply the filter. If you want to Delete a filter, you must bring it up in the [Advanced Filters Dialog](#advanced-filters-dialog) and click on **Delete**.

---

<a id="advanced-filters-dialog"></a>

## Advanced Filters Dialog

*Source: [`Content/MainDocumentation_HTML/Advanced_Filters_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Filters_Dialog.htm)*

The Advanced Filter dialog is accessible from many places within Simulator. This is generally available wherever it is possible to assign an advanced filter.

![AdvancedFiltersFilterByType](images/AdvancedFiltersFilterByType.png)

Filter By

The following options are available from this dialog:

Advanced

Advanced filtering allows you to define a set of logical comparisons for the various fields which must be met. For example you may want to only see Buses that meet the conditions "Nominal Voltage \> 100 kV" AND "MW Load \> 100 MW". For more help on Advanced Filtering see the topic [Advanced Filtering: Advanced](#advanced-filtering-advanced).

Device

Device filtering allows you to directly use one of the power system model objects as a filter. The relationship between the object type being listed and the object type of the device filter determines how filtering is done. For example, if you use an Injection Group as a device filter to filter a list of Generators, then you will get only the generators that are inside the Injection Group. As another example, if you are using an Injection Group as a device filter to filter a list of Branches, then you will get only branches that are connected to the terminal bus of any generator, load, or switched shunt contained in the injection group. Device filtering can be used instead of more complicated Advanced Filters. For more help on Device Filtering see the topic [Advanced Filter: Device](#advanced-filtering-device).

Select Filter Type

When defining an Advanced Filter, normally this type is the same as the object type for which your are defining a filter. When defining a Device Filter, normally this type will be different.

By changing the drop-down next to Select Filter Type, it is possible to filter based on data for a related object instead of for the actual object. For example, an Advanced Filter for a Bus may exist to only show buses with a Nominal Voltage larger than 138 kV. You may then want to use this filter on a case information display that shows generators. This is possible by changing the Filter Type to be a Bus when showing the Filter Dialog on the Generator case information display. Just click the drop-down to see which related objects' filters can be used for that particular situation.

View Filter Logic

Select [View Filter Logic](#advanced-filters-view-filter-logic-graphical-display) to show a graphical display to visualize the logic diagram for an Advanced Filter.

Save Filter...

Click this button to save the filter in an auxiliary file. A drop-down will present these options for saving: *Save Current Filter, Save Object Filters* and *Save All Filters*. The *Save Current Filter* saves only the that is currently selected in the dialog.*Save Object Filters* saves all filters of the current object type. *Save All Filters* saves all of the filters in the case.

Comments Regarding Auxiliary Files and the Use of Advanced Filters

Throughout auxiliary script commands, the ability to specify an advanced filter by name is available. In this context, if the use of an advanced filter for a different object type is needed, the filtername should be preceded by the object type enclosed in less than and greater than signs: "\<Objecttype\>filtername". For example if an Advanced Bus filter is desired in a place where an Advanced Generator filter is needed, then use the string "\<BUS\> filtername" to represent the filter. If the use of a device filter is desired, then use the string "\<DEVICE\> objecttype 'key1' 'key2' 'key3'" to represent the device filter.

---

<a id="advanced-filters-view-filter-logic-graphical-display"></a>

## Advanced Filters View Filter Logic Graphical Display

*Source: [`Content/MainDocumentation_HTML/Advanced_Filters_View_Filter_Logic_Graphical_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Filters_View_Filter_Logic_Graphical_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Advanced Filter Logic Display** feature provides a graphical display which allows you to quickly browse information about an [Advanced Filter](#advanced-filtering) and the corresponding conditions The advanced filter logic displays enable convenient Advanced Filter-by-Advanced Filter navigation through the complete list of model filters. From the advanced filter logic display, you can find out an advanced filter name and Logical Comparison object, and conditions names that are part of the particular advanced filter. Moreover you can find out all information associated with the advanced filter by pressing right click with the mouse and directly invoking their associated information dialogs. The advantage of the advanced filter logic displays, is that they are auto-created logic diagrams.

Below this top panel sits the actual advanced filter display. The advanced filter you have chosen to inspect, is represented as the last advanced filter to the right of the display. When you drag the mouse over one of the neighboring advanced filters symbols, it turns into a pointing finger, then by clicking the left mouse button when the mouse cursor is in this shape redefines the target advanced filter to be the advanced filter whose symbol you just clicked. The advanced filter view display is redrawn to show the same sort of display for the newly chosen target. Right-clicking on the advanced filter view display’s background will generate the local menu.

The advanced filter background color can be red or green. Green means that the criteria is satisfied and the evaluation of the model filter is true. Red means that the evaluations is false. Repeated colors of the Advanced Filter Names and Conditions represent that the particular Advanced Filter or Condition is used more than once in the Advanced Filter Display.

The advanced filter view display can be generated using the following method:

  - Pressing the "**View Filter Logic**" button in the [Advanced Filter](#advanced-filters-dialog) dialog.

---

<a id="advanced-filtering-advanced"></a>

## Advanced Filtering: Advanced

*Source: [`Content/MainDocumentation_HTML/Advanced_Advanced_Filtering.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Advanced_Filtering.htm)*

The [Advanced Filters Dialog](#advanced-filters-dialog) when **Filter By** is set to **Advanced** is shown in the following figure:

![AdvancedFilters](images/AdvancedFilters.png)

When you open this dialog, you will only see filters that have been defined for the type of object you are trying to filter (e.g. Bus, Generator, Interface, etc.). You can choose a filter from the **Filter Name** drop-down box showing the list of filters available, or you can create a new filter. To make a new filter, simply click on **Save As** to save a copy of the present filter under a new name and then specify the properties of the filter as discussed below. When you have specified the filter as you wish, click **Filter**.

When this dialog is opened from a location where an Advanced Filter is not already applied, **Filter Name** will be blank and the default is to assume that a new filter should be created.

Advanced filters are stored with the case file when the case is saved. In addition, the filters can be exported to a Simulator [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux) for storage and import into other cases. A list of all advanced filters defined for a case can be viewed in the [Advanced Filters case information display](#advanced-filters-display).

To create an Advanced Filter you must specify the following things:

Filter Name

A string that uniquely names the filter so that it can be referenced from other dialogs. Filter names must be unique for each object type but do not have to be unique across different object types.

Condition 1, Condition2, etc.

Describes the conditions of your filter. To define a condition:

  - Specify the field you are filtering. The drop-down list will open an embedded field chooser with useful options for finding the desired field. The **Find** button will open a very similar field chooser dialog.
  - Specify the comparison operation such as *between* or *greater than*.
  - Specify the values to which the field is compared. Depending on the comparison operation, either one or two values are needed.
  - Select **ABS** to use the absolute value of the field value in the comparison operation. For Fields that are strings, select **Case Sens.** to make the comparison case sensitive.

Noteworthy comments about defining conditions:

  - The comparison operation *within integer range list* uses the same format as described in [Entering a Range of Numbers](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers).
  - To add or delete conditions click on the **Add\>\>** or **Delete…** button. You can also delete an individual condition by clicking on the **X** button next to the condition.
  - There is no limit to the number of comparisons you can use for the Advanced Filter.

Logical Operators

The following describes how the filter uses the conditions that are specified such that the filter itself is met:

  - AND means that all conditions should be true
  - Not AND is the opposite of AND (i.e. any one of the conditions can be false)
  - OR means that any one of the conditions can be true
  - Not OR is the opposite of OR (i.e. all of the conditions must be false)
  - Added in Version 19 XOR will return true if an <span class="underline">odd</span> number of conditions are TRUE
  - Added in Version 19 One TRUE will return true if <span class="underline">exactly one</span> of the conditions is TRUE
  - Added in Version 21 Num TRUE will return true if the specified number of conditions is TRUE

To use different logical operators within the same filter, refer to the **Using Different Logical Operators** section below.

Pre-Filter using Area/Zone/Owner Filters

When this box is checked, data is filtered first by the [Area/Zone/Owner Filters](#areazoneowner-and-datamaintainer-filters) and then by the Advanced Filter, therefore the data must meet both the Area/Zone/Owner Filters and the Advanced Filters in order to be shown. When this box is unchecked, the [Area/Zone/Owner Filters](#areazoneowner-and-datamaintainer-filters) are ignored.

Keep in mind that using this option will change how the filter behaves when Area/Zone/Owner filters change. Area/Zone/Owner filters are often used as a quick way of filtering. To ensure that a filter is not dependent on something that can easily change, it is best to include conditions on Areas, Zones, Owners, and Data Maintainers directly in the filter and refrain from using this pre-filter option.

Enable Field to Field Comparisons

When this box is checked, it is possible to compare two fields of the device or a field with a Model Expression. The dialog will be modified to show a drop-down with options for the type of field to use in the comparison, and the **Find** button will appear to make it easier to search for a particular field. In the drop-down **Field** indicates a comparison of a field for the same device and **Expression** indicates a comparison to the named Model Expression. If no Model Expressions have been defined this option is not available.

The following depicts what a particular condition looks like when the Enable Field to Field Comparisons checkbox is checked:

![AdvancedFiltersFieldToField](images/AdvancedFiltersFieldToField.png)

Using Different Logical Operators

Once a logical operator is chosen, that operator is used for all conditions in the filter. Therefore if you wish to use the AND operator, all conditions you define will be combined using AND. Nested filters are used to combine different conditions in the same filter with different logical operators. In other words, one condition of a filter can be that another filter is met. This allows you to define some conditions using one logical operator in one filter, and then use that filter to combine those conditions with other conditions using a different logical operator.

For example, consider the logical comparison of **A and (B or C)**. To replicate this, you would define one advanced filter (AF1) that contains the logic **B or C**. Then you can define an advanced filter (AF2) that uses AF1 as **A and (AF1)**.

To refer to one filter from within another, check the **Use Another Filter**box. When using another filter the comparison operations that are available are *meets filter* and *not meets filter*. The comparison value box will turn into a drop-down that contains all defined filters that are applicable for the object type of the filter. The **Find** button can be used to open a dialog that will make it easier to search for filters. Device filters that use a particular object as a means of filtering can also be used as another filter. To use a device filter the string of the format `<DEVICE> objecttype 'key1' 'key2' 'key3'` should be entered in the comparison value box.

---

<a id="advanced-filtering-device"></a>

## Advanced Filtering: Device

*Source: [`Content/MainDocumentation_HTML/Advanced_Device_Filtering.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Device_Filtering.htm)*

The [Advanced Filters Dialog](#advanced-filters-dialog) when **Filter by** is set to **Device** is shown in the following figure

![AdvancedFilterDevice](images/AdvancedFilterDevice.gif)

Device Filtering allows you to directly use one of the power system model objects as a filter. The relationship between the object type being listed and the object type of the device filter determines how filtering is done. For example, the image below shows the use an Injection Group as a device filter to filter a list of Generators. The result of using this filter will be only the generators which are inside the Injection Group.

As another example, if you are using an Injection Group as a device filter to filter a list of Branches, then you will get only branches that are connected to the terminal bus of any generator, load, or switched shunt contained in the injection group. Device filtering can be used instead of more complicated Advanced Filters.

---

<a id="advanced-filters-display"></a>

## Advanced Filters Display

*Source: [`Content/MainDocumentation_HTML/Advanced_Filters_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_Filters_Display.htm)*

The Advanced Filters Display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) available under the folder *Conditions, Filters, and Expressions* on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The purpose of this display is to list any [advanced filters](#advanced-filtering) you have defined for the current case. Each record will list the name of the filter, the type of object the filter is for, and filter logic.

Normally you will create advanced filters directly on a case information display that is showing a particular object type. However you can also choose **Insert** from the [Case Information Toolbar Records Menu](04-model-explorer-and-case-information-part1.md#records-menu) to create an advanced filter. You will then be prompted to choose the object type on a dialog before proceeding to the [Advanced Filters Dialog.](#advanced-filters-dialog)

Normally you will delete advanced filters from the [Advanced Filters Dialog](#advanced-filters-dialog), however you can also choose **Delete** from the [Case Information Toolbar Records Menu](04-model-explorer-and-case-information-part1.md#records-menu) to delete an advanced filter. This will then remove the filter from any case info displays, [dynamic formatting definitions](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog), [select by criteria definitions](14-editing-onelines.md#select-by-criteria-dialog), or any other locations that are presently using this advanced filter.

The most common use of this display is using the [Case Information Toolbar: Save Auxiliary Files Menu](04-model-explorer-and-case-information-part1.md#save-auxiliary-files-menu) option to save a list of advanced filters to an auxiliary file. Saving to an auxiliary file makes it easy to transfer defined Advanced Filters from one case to another.

Advanced Filters can be created to filter the list of Advanced Filters. This is most useful if only wanting to save filters for a particular object type or from a particular Data Maintainer.

---

<a id="expressions"></a>

## Expressions

*Source: [`Content/MainDocumentation_HTML/Custom_Expressions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Expressions.htm)*

Simulator allows you to define Expressions that are functions of other fields. These Expressions can then be shown as a column in a Case Information Display. To define expressions, right-click in a Case Information Display table and choose **Define Expression** from the local menu or choose **Expressions Menu \> Define Expression** from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar). This brings up the Define Expressions dialog. When you bring up the dialog you will only see expressions that have been defined for the type of object shown on the Case Information Display (e.g. Bus, Generator, Interface, etc.).

![ExpressionDefineDialog](images/ExpressionDefineDialog.png)

To define a new Expression click **New**.

Expression Name

You can name the expression for easy identification in the list of fields for the object by filling in this field.

Define Variables

To define the Expression, first specify which fields you would like to use in the expression and assign them to the variables x1, x2, …, x8.

Field, Model Field, Model Expression, or Model String Expression

Fields can be chosen that apply to the type of object for which the expression is being defined or a Model Field that is a field associated with a specific object, a [Model Expression](#model-expressions), or a Model String Expression can be chosen.

Treat blank as zero

This check box should be checked if a blank entry for the field should be treated as a zero in the expression rather than treating it as an invalid variable.

Evaluate Field in Contingency Reference State

Added in Version 19, build on December 18, 2015. This check box will impact how the Expression behaves when evaluated during the contingency analysis solution. This can impact the behavior when the expression is used as part of a ModelConditionCondition, an advanced filter, Custom Monitor, or as part of a Injection Group participation point calculation when evaluated for use during contingency analysis. If this box is checked, the value of the field will be determined in the contingency reference state and will remain constant at this value whenever this expression is used during the contingency solution.

Function (x1, x2, x3...)

After fields or Model Expressions have been assigned to variables, type in the expression as a function of the variables x1, x2, …, x8. For example

x1 \* SIN(x2) + EXP(-x5)

or

TAN(x1) + ABS(x6)\*8 - 100

For a complete list of functions and operators that are available to you, see [Functions and Operators Available](#functions-and-operators-available).

Once the Expression has been defined, clicking OK will save the expression and close the dialog. A prompt will ask if the expression should be added to the case information display. The field can also be added or removed later using the options to update columns found in the [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) topic.

---

<a id="expressions-display"></a>

## Expressions Display

*Source: [`Content/MainDocumentation_HTML/Custom_Expressions_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Expressions_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open the Expressions Display, select **Case Information and Auxiliary** **\> Expressions** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). If you have defined any [expressions](#expressions) for your case, you can see the list of those expressions in this display. The type of object to which the expression applies, the name of the expression, and the expression itself are given. The display also shows the values being represented by each of the variables in the expression.

Expressions cannot be inserted manually in this display, but they can be loaded from an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) by right-clicking on the grid and selecting **Load \> Auxiliary File (any data)…** from the local menu. Conversely, you can save a list of expressions in a case to an auxiliary file by right-clicking on the grid and choosing **Save As \> Auxiliary file**.

---

<a id="string-expressions"></a>

## String Expressions

*Source: [`Content/MainDocumentation_HTML/Custom_String_Expressions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_String_Expressions.htm)*

Simulator allows you to define String Expressions to generate a string from other fields. These String Expressions can then be shown as a column in a Case Information Display. To define string expressions, right-click in a Case Information Display table and choose **Define String Expression** from the local menu or choose **Expressions Menu \> Define String Expression** from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar).. This brings up the Define String Expressions dialog. When you bring up the dialog you will only see expressions that have been defined for the type of object shown on the Case Information Display (e.g. Bus, Generator, Interface, etc.).

To define a new expression click **New**.

You can name the expression for easy identification in the list of fields for the object by filling in the **Expression Name** field.

To define the expression, first specify which fields you would like to use in the expression and assign them to the variables x1, x2, …, x8. Fields can be chosen that apply to the type of object for which the expression is being defined or a Model Field that is a field associated with a specific object, [Model Expression](#model-expressions), or Model String Expression can be chosen.

The string expression is then defined in terms of the variables x1, x2, ..., x8. Different elements of the expression are concatenated with a + symbol. A number of different types of elements can be combined.

  - Static strings can be specified inside of quotation marks
  - Variables containing string data (such as Bus Name) may be added directly
  - Variables containing numeric data may be formatted using the function Str(*variable*, *minlength*, *decimals*). The *variable* parameter is the value to be formatted, the *minlength* parameter is the minimum number of characters for the result, and the *decimals* parameter specifies the number of characters to the right of the decimal point. If the *decimals* parameter is specified as a negative number, then all trailing zeros beyond the decimal are truncated.

For example

"This string expression displays the bus name (" + x1 + ") and per unit voltage (" + Str(x2, 3, 2) + ")"

For a complete list of functions and operators that are available to you for numeric expressions, see [Functions and Operators Available](#functions-and-operators-available).

Once the String Expression has been defined, clicking OK will save the string expression and close the dialog. A prompt will ask if the string expression should be added to the case information display. The string expression can also be added or removed later using the options to update columns found in the [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) topic.

---

<a id="functions-and-operators-available"></a>

## Functions and Operators Available

*Source: [`Content/MainDocumentation_HTML/Functions_and_Operators_Available.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Functions_and_Operators_Available.htm)*

Below is a list of functions and operators that are available for use in defining [Expressions](#expressions), [String Expressions](#string-expressions), [Model Expressions](#model-expressions), and Model String Expressions:

Note: Trigonometric functions are in radians.

Operators

<table>
<tbody>
<tr class="odd">
<td><p><strong>Precedence</strong></p>
<p>Higher precedence operators are processed first</p></td>
<td><p><strong>Symbol</strong></p></td>
<td><p><strong>Description</strong></p></td>
<td><p><strong>Example</strong></p></td>
</tr>
<tr class="even">
<td><p>0</p></td>
<td><p>OR</p></td>
<td><p>OR</p></td>
<td><p>(2 &gt; 1) OR (2 &gt; 3) = not zero*</p></td>
</tr>
<tr class="odd">
<td><p>1</p></td>
<td><p>XOR</p></td>
<td><p>XOR</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>AND</p></td>
<td><p>AND</p></td>
<td><p>(2 &gt; 1) AND (2 &gt; 3) = 0*</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>NOT</p></td>
<td><p>NOT</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>&gt;</p></td>
<td><p>Greater than</p></td>
<td><p>9 &gt; 2 = not zero*</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>&lt;</p></td>
<td><p>Less than</p></td>
<td><p>7 &lt; 4 = 0*</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>==</p></td>
<td><p>Equal test</p></td>
<td><p>5 == 4 = 0*</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>&gt;=</p></td>
<td><p>Greater or equal</p></td>
<td><p>3 &gt;= 3 = not zero*</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>&lt;=</p></td>
<td><p>Less or equal</p></td>
<td><p>3 &lt;= 9 = 0</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>&lt;&gt;</p></td>
<td><p>Not equal</p></td>
<td><p>12 &lt;&gt; 20 = not zero*</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>bitor</p></td>
<td><p>bitwise OR</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>bitxor</p></td>
<td><p>bitwise XOR</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>bitand</p></td>
<td><p>bitwise AND</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>shl</p></td>
<td><p>Shift Left</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>shr</p></td>
<td><p>Shift Right</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>+</p></td>
<td><p>Add</p></td>
<td><p>1 + 1 = 2</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>-</p></td>
<td><p>Subtract</p></td>
<td><p>9 - 5 = 4</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>*</p></td>
<td><p>Multiply by</p></td>
<td><p>3 * 6 = 18</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>/</p></td>
<td><p>Divide by</p></td>
<td><p>9 / 2 = 4.5</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>\</p></td>
<td><p>Integer divide by</p></td>
<td><p>9 \ 2 = 4</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>MOD</p></td>
<td><p>Modulo (remainder)</p></td>
<td><p>7 mod 4 = 3</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>bitnot</p></td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>!</p></td>
<td><p>Factorial</p></td>
<td><p>5! = 120</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>^</p></td>
<td><p>Raised to the power of</p></td>
<td><p>4 ^ 5 = 1024</p></td>
</tr>
<tr class="even">
<td><p>13</p></td>
<td><p>( )</p></td>
<td><p>Prioritizes an expression</p></td>
<td><p>5*(1+1) = 10</p></td>
</tr>
</tbody>
</table>

Functions

<table>
<tbody>
<tr class="odd">
<td><p><strong>Symbol</strong></p></td>
<td><p><strong>Description</strong></p></td>
<td><p><strong>Example</strong></p></td>
</tr>
<tr class="even">
<td><p>IIF</p></td>
<td><p>If condition</p></td>
<td><p>IIf(1+1==2,4,5) = 4</p></td>
</tr>
<tr class="odd">
<td><p>ISTRUE</p>
<p>Added in version 19, build on November 19, 2015</p></td>
<td><p>Returns 1 if the string entered is: T, TRUE, CONNECTED, CLOSED, YES, Y, or 1. Otherwise returns 0.</p></td>
<td><p>IsTrue('Closed') = 1</p></td>
</tr>
<tr class="even">
<td><p>MIN</p></td>
<td><p>Minimum value</p></td>
<td><p>min(10,3,27,15) = 3</p></td>
</tr>
<tr class="odd">
<td><p>MAX</p></td>
<td><p>Maximum value</p></td>
<td><p>max(1,9)=9</p></td>
</tr>
<tr class="even">
<td><p>SIN</p></td>
<td><p>Sine</p></td>
<td><p>sin(3.14159265) = 0</p></td>
</tr>
<tr class="odd">
<td><p>COS</p></td>
<td><p>Cosine</p></td>
<td><p>cos(3.14159265) = -1</p></td>
</tr>
<tr class="even">
<td><p>TAN</p></td>
<td><p>Tangent</p></td>
<td><p>tan(3.14159265) = 0</p></td>
</tr>
<tr class="odd">
<td><p>ASIN</p></td>
<td><p>Arc sine</p></td>
<td><p>asin(1) = 1.570</p></td>
</tr>
<tr class="even">
<td><p>ACOS</p></td>
<td><p>Arc cosine</p></td>
<td><p>acos(-1) = 3.141</p></td>
</tr>
<tr class="odd">
<td><p>ATAN, ATN</p></td>
<td><p>Arc tangent</p></td>
<td><p>atan(0) = atn(0) = 0</p></td>
</tr>
<tr class="even">
<td><p>SEC</p></td>
<td><p>Secant</p></td>
<td><p>sec(0) = 1</p></td>
</tr>
<tr class="odd">
<td><p>CSC</p></td>
<td><p>Cosecant</p></td>
<td><p>csc(1) = 1.18</p></td>
</tr>
<tr class="even">
<td><p>COT</p></td>
<td><p>Cotangent</p></td>
<td><p>cot(1) = 0.642</p></td>
</tr>
<tr class="odd">
<td><p>SINH</p></td>
<td><p>Hyperbolic sine</p></td>
<td><p>sinh(3) = 10.01</p></td>
</tr>
<tr class="even">
<td><p>COSH</p></td>
<td><p>Hyperbolic cosine</p></td>
<td><p>cosh(2) = 3.76</p></td>
</tr>
<tr class="odd">
<td><p>TANH</p></td>
<td><p>Hyperbolic tangent</p></td>
<td><p>tanh(1) = 0.76</p></td>
</tr>
<tr class="even">
<td><p>COTH</p></td>
<td><p>Hyperbolic cotangent</p></td>
<td><p>coth(1) = 1.31</p></td>
</tr>
<tr class="odd">
<td><p>SECH</p></td>
<td><p>Hyperbolic secant</p></td>
<td><p>sech(0) = 1</p></td>
</tr>
<tr class="even">
<td><p>CSCH</p></td>
<td><p>Hyperbolic cosecant</p></td>
<td><p>csch(1) = 0.85</p></td>
</tr>
<tr class="odd">
<td><p>ASINH</p></td>
<td><p>Hyperbolic arc sine</p></td>
<td><p>asinh(2) = 1.44</p></td>
</tr>
<tr class="even">
<td><p>ACOSH</p></td>
<td><p>Hyperbolic arc cosine</p></td>
<td><p>acosh(9) = 2.89</p></td>
</tr>
<tr class="odd">
<td><p>ATANH</p></td>
<td><p>Hyperbolic arc tangent</p></td>
<td><p>atanh(.1) = 0.10</p></td>
</tr>
<tr class="even">
<td><p>ACOTH</p></td>
<td><p>Hyperbolic arc cotangent</p></td>
<td><p>acoth(7) = 0.14</p></td>
</tr>
<tr class="odd">
<td><p>ASECH</p></td>
<td><p>Hyperbolic arc secant</p></td>
<td><p>asech(.3) = 1.87</p></td>
</tr>
<tr class="even">
<td><p>ACSCH</p></td>
<td><p>Hyperbolic arc cosecant</p></td>
<td><p>acsch(2) = 0.48</p></td>
</tr>
<tr class="odd">
<td><p>ABS</p></td>
<td><p>Absolute value</p></td>
<td><p>abs(-8) = 8</p></td>
</tr>
<tr class="even">
<td><p>EXP</p></td>
<td><p>e to the power of</p></td>
<td><p>exp(3) = 20.08</p></td>
</tr>
<tr class="odd">
<td><p>EXP2</p></td>
<td><p>2 to the power of</p></td>
<td><p>exp2(3) = 8</p></td>
</tr>
<tr class="even">
<td><p>EXP10</p></td>
<td><p>10 to the power of</p></td>
<td><p>exp10(3) = 1000</p></td>
</tr>
<tr class="odd">
<td><p>LOG, LN</p></td>
<td><p>Natural log</p></td>
<td><p>ln(16) = log(16) = 2.77</p></td>
</tr>
<tr class="even">
<td><p>LOG2</p></td>
<td><p>Log base 2</p></td>
<td><p>log2(8) = 3</p></td>
</tr>
<tr class="odd">
<td><p>LOG10</p></td>
<td><p>Log base 10</p></td>
<td><p>log10(100) = 2</p></td>
</tr>
<tr class="even">
<td><p>CEIL</p></td>
<td><p>Round up</p></td>
<td><p>ceil(6.2) = 7</p></td>
</tr>
<tr class="odd">
<td><p>RAND</p></td>
<td><p>Random number</p></td>
<td><p>rnd(1) = .969</p></td>
</tr>
<tr class="even">
<td><p>INT</p></td>
<td><p>Truncate to an integer</p></td>
<td><p>int(6.8) = 6</p></td>
</tr>
<tr class="odd">
<td><p>SGN, SIGN</p></td>
<td><p>Sign of expression (-1, 0, or 1)</p></td>
<td><p>sgn(-9) = sign(-9) = -1</p></td>
</tr>
<tr class="even">
<td><p>SQR, SQRT</p></td>
<td><p>Square root</p></td>
<td><p>sqr(64) = sqrt(64) = 8</p></td>
</tr>
<tr class="odd">
<td><p>FRAC</p></td>
<td><p>Fraction of float</p></td>
<td><p>fract(5.125)= 0.125</p></td>
</tr>
<tr class="even">
<td><p>AVERAGE</p></td>
<td><p>Average</p></td>
<td><p>average(7, 8, 9, 10, 11) = 9</p>
<p>any number of parameters</p></td>
</tr>
<tr class="odd">
<td><p>ASC</p></td>
<td><p>Returns ASCII integer of the character</p></td>
<td><p>asc('A') = 65</p></td>
</tr>
<tr class="even">
<td><p>CHR</p></td>
<td><p>Returns character of an ASCII integer</p></td>
<td><p>Chr(65) = 'A'</p></td>
</tr>
<tr class="odd">
<td><p>STR</p></td>
<td><p>Converts a floating point number into a string of a specified number of digits and right of decimal point</p></td>
<td><p>str(12.3456, 5, 2) = 12.36</p></td>
</tr>
<tr class="even">
<td><p>LEFT</p></td>
<td><p>Copy of the left-most characters from a string</p></td>
<td><p>left('PowerWorld', 5) = 'Power'</p></td>
</tr>
<tr class="odd">
<td><p>RIGHT</p></td>
<td><p>Copy of the right-most characters from a string</p></td>
<td><p>Right('PowerWorld', 5) = 'World'</p></td>
</tr>
<tr class="even">
<td><p>MID</p></td>
<td><p>Copy characters from inside a string starting at a particular character and going a particular number of characters</p></td>
<td><p>Mid('PowerWorld', 3, 5) = 'werWo'</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>TRIM</p>
<p>Added in Version 19, build on December 11, 2015</p></td>
<td><p>Remove leading and trailing spaces from a string</p></td>
<td><p>Trim('   PowerWorld  ') = 'PowerWorld'</p></td>
</tr>
<tr class="even">
<td><p>LTRIM</p>
<p>Added in Version 19, build on December 11, 2015</p></td>
<td><p>Remove leading spaces from a string</p></td>
<td><p>LTrim('   PowerWorld  ') = 'PowerWorld  '</p></td>
</tr>
<tr class="odd">
<td><p>RTRIM</p>
<p>Added in Version 19, build on December 11, 2015</p></td>
<td><p>Remove trailing spaces from a string</p></td>
<td><p>RTrim('   PowerWorld  ') = '   PowerWorld'</p></td>
</tr>
<tr class="even">
<td><p>FIND</p>
<p>Added in Version 19, build on January 5, 2017</p></td>
<td><p>Find(Find_Text, Within_Text, [Start_Num]).</p>
<p>Returns the integer position of the sub-string Find_Text looking inside the string Within_Text. You may optionally instruct us to start the search at character position Start_Num. If Start_Num is not specified, then we start at position 1. The search is case-sensitive. You may not use wildcard characters * or ?. If Find_Text is not found then function will return 0.</p></td>
<td><p>Find('bc', 'aBcd-xyz-abcd') = 2</p>
<p>Find('bc', 'aBcd-xyz-abcd', 5) = 11</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>SEARCH</p>
<p>Added in Version 19, build on January 5, 2017</p></td>
<td><p>Search(Find_Text, Within_Text, [Start_Num]).</p>
<p>Returns the integer position of the sub-string Find_Text looking inside the string Within_Text. You may optionally instruct us to start the search at character position Start_Num. If Start_Num is not specified, then we start at position 1. The search is not case-sensitive. Also the Find_Text may include a ? to indicate any single character of an * to indicate any number of characters. If Find_Text is not found then function will return 0.</p></td>
<td><p>Search('B?d', 'aBcd-xyz-abcd') = 2</p>
<p>Search('B?d', 'aBcd-xyz-abcd', 5) = 0</p>
<p>Search('b?d', 'aBcd-xyz-abcd') = 11</p>
<p>Search('b?d', 'aBcd-xyz-abcd', 5) = 11</p>
<p>Search('B*b', 'aBcd-xyz-abcd', 5) = 2</p></td>
</tr>
<tr class="even">
<td><p>INTEGER, LONG</p></td>
<td><p>Typecast another type as an integer</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>FLOAT</p></td>
<td><p>Typecast another type as a float</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>SINGLE</p></td>
<td><p>Typecast another type as a single</p>
<p>(4 byte floating point)</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>DOUBLE</p></td>
<td><p>Typecast another type as a double</p>
<p>(8 byte floating point)</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>STRING</p></td>
<td><p>Typecast another type as a string</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>TEXT</p></td>
<td><p>Convert floating point number which represents a date into a formatted text string. The integral part of the value is the number of days that have passed since 12/30/1899. The fractional part of the value is fraction of a 24 hour day that has elapsed.</p>
<p>See <a href="04-model-explorer-and-case-information-part3.md#data-and-time-formatting-strings" class="MCXref xref">Data and Time Formatting Strings</a> for information on specifying the formatting string.</p></td>
<td><p>Text(42999.760416667, 'mm/dd/yyyy hh:nn:ss AM/PM') =</p>
<p>09/21/2017 6:15:00 PM</p></td>
</tr>
<tr class="even">
<td><p>DATETIMEVALUE</p></td>
<td><p>Converts a formatted date string into a floating point number.</p></td>
<td><p>DateTimeValue('9/21/2017 6:15:00 PM') = 42999.760416667</p></td>
</tr>
<tr class="odd">
<td><p>DATEVALUE</p></td>
<td><p>Converts a formatted date string into a floating point number. It then truncates the fractional part of the floating point number giving only the integral number of days that have passed since 12/30/1899</p></td>
<td><p>DateValue('9/21/2017 6:15:00 PM') = 42999.00</p></td>
</tr>
<tr class="even">
<td><p>TIMEVALUE</p></td>
<td><p>Converts a formatted date string into a floating point number. It then removes the integral part of the floating point number giving only the fractional part of a day representing the time</p></td>
<td><p>TimeValue('9/21/2017 6:15:00 PM') = 0.760416667</p></td>
</tr>
</tbody>
</table>

\* Functions that evaluate to true or false will return a zero, 0, value if true and a non zero value if false.

---

<a id="model-expressions"></a>

## Model Expressions

*Source: [`Content/MainDocumentation_HTML/Model_Expressions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Expressions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Model Expressions can be accessed and created by choosing **Case Information and Auxiliary \> Model Expressions** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). To open the Define Model Expressions dialog, right-click and choose **Insert**, when creating a new expression, or **Show Dialog** to view an existing expression.

The **Save**, **Save As**, **Rename**, and **Delete** buttons and the drop-down list of expressions at the top of the dialog allow for the additional of new expressions, modification of existing expressions, and removal of existing expressions. There are two types of Model Expressions: an expression and a lookup table.

Lookup Tables

The dialog as configured when creating a lookup table appears as follows:

![Model Expression Lookup Table](images/Model_Expression_Lookup_Table.gif)

A lookup table may be either one or two-dimensional by specifying the **Lookup Type**. The **Number of Points** must be set for each dimension. This will determine the size of the table. A Model Field must also be selected for each dimension. Clicking the **Define** button next to either the **x1** or **x2** field opens the Model Field Dialog. This dialog allows the selection of an **Element Type** and a specific element of this type. The list of elements behaves the same as the [Find Dialogs](04-model-explorer-and-case-information-part3.md#find-dialog-basics) found throughout Simulator. After selecting the element, choose the field associated with this element that will be used in the Lookup Table. Click **OK** to accept the element and field selected and close the dialog.

Fill in the Lookup Table with the desired values. If selecting a one-dimensional table, there will be two columns, one containing the values for the **x1** Model Field and the other containing the Values to return from the Lookup Table when the Model Field is at the defined value. There will be one header row plus as many additional rows as defined in the **Number of x1** **Points**. If selecting a two-dimensional table, there will be one column for the **x1** Model Field and as many other columns as selected for the **Number of x2 Points**. There will be one header row for defining the **x2** values plus as many additional rows as defined in the **Number of x1 Points**. The cells under the first row and to the right of the first column are used for defining the Values to return from the Lookup Table when the Model Fields meet the defined values.

If selecting a one-dimensional table, the returned Value is determined based on the current value of the **x1** Model Field. The returned value is the Value corresponding with the **x1** value that is less than or equal to the current value of the Model Field. If the current value of the Model Field is less than the smallest value of **x1** in the table, then the Value returned corresponds to the smallest **x1** value. If selecting a two-dimensional table, the same rules apply except that the Value returned corresponds to the current value of the **x1** AND **x2** Model Fields and where these intersect in the table.

Expressions

The dialog as configured when creating an expression appears below:

![Model Expression Example](images/Model_Expression_Example.gif)

To define the Model Expression as an expression, specify the Model Fields that the expression should be a function of by clicking the **Define** button next to the appropriate variable. Clicking the **Define** button opens the Model Field dialog:

![Model Expression Defin](images/Model_Expression_Defin.gif)

This dialog allows the selection of an **Element Type** and a specific element of this type, including Model Conditions, Model Filters, and other Model Expressions. The list of elements of a particular type can be searched, filtered, and sorted to make finding an element easier. After selecting the element, choose the field associated with this element that will be used in the expression.

**Treat blank as zero check box**

The **Treat blank as zero** check box should be checked if a blank entry for the field should be treated as a zero in the expression rather than treating it as an invalid variable.

**Evaluate Field in Contingency Reference State Check Box**

Added in Version 19, build on December 18, 2015. The check box **Evaluate Field in Contingency Reference State** will impact how the Model Expression behaves when evaluated during the contingency analysis solution. This can impact the behavior when the model expression is used as part of a Contingency Element, a ModelConditionCondition, an advanced filter, Custom Monitor, or as part of a Injection Group participation point calculation when evaluated for use during contingency analysis.

Click **OK** to accept the element and field selected and close the dialog.

After the Model Fields have been defined, enter the function using the variables x1, x2, ..., x8. For example:

x1 \* SIN(x2) + EXP(-x5)

or

TAN(x1) + ABS(x6)\*8 - 100

For a complete list of functions and operators that are available, see [Functions and Operators Available](#functions-and-operators-available).

After model expressions have been defined, new options will appear on the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog) and on the [Advanced Filter Dialog](#advanced-filters-dialog).

Normally, you may only enter a constant for the comparison value on the [Advanced Filter Dialog](#advanced-filters-dialog). However, if you select **Enable Field to Field Comparisons**, the advanced filter dialog will feature a drop-down from which you can choose *Expression.* After choosing *Expression*, you may select the name of the model expression, or click the **Find** button to search for the name.

![Model Expression Filter Example](images/Model_Expression_Filter_Example.gif)

Similarly, normally you may only enter a *Constant* or a *Field* for the *Move*, *Set To*, or *Change By* **Action Types** on the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog). However, now you will have the option to choose *Model Expression*. To change the type of the **Amount**, choose *Model Expression* from the second drop-down box. After doing this, enter or choose the name of the model expression in the first **Amount** drop-down box, or click on the **Find…** button to search for a name.

![Contingency Element Dialog Expression](images/Contingency_Element_Dialog_Expression.gif)

Once a Model Expression has been saved, it may be referenced directly in a Case Information Display or AUX file using [special notation](04-model-explorer-and-case-information-part3.md#referencing-model-expressions).

See the [Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions](52-additional-linked-topics-part1.md#relationship-between-contingencies-model-conditions-model-filters-and-model-expressions) topic for more information about how these work together.

Model Result Override Added in Version 20

[Model Result Overrides](22-contingency-analysis-options.md#model-result-override) can override the result of a Model Expression. If a model expression is being overridden, all of its logic is ignored and the result comes directly from what is specified with the Model Result Override. If a model expression is being overridden by a model result override that is enabled, portions of the dialog will be highlighted in yellow and the message *Model Expression is overridden by a Model Result Override* will appear on the dialog. The model expression can still be modified while it is being overridden.
