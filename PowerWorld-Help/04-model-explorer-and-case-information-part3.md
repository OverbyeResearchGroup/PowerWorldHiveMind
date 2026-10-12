---
title: "Model Explorer and Case Information Displays (Part 3 of 3)"
part: "Viewing Case Data"
chapter_file: "04-model-explorer-and-case-information-part3.md"
topics: 26
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Model Explorer and Case Information Displays (Part 3 of 3)

Model Explorer and the mechanics of case information displays: filtering, sorting, columns, formats.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (26)**

- [Data and Time Formatting Strings](#data-and-time-formatting-strings)
- [Find Dialog Basics](#find-dialog-basics)
- [Search For Text Dialog](#search-for-text-dialog)
- [Model Conditions Display and Dialog](#model-conditions-display-and-dialog)
- [Model Filters Display and Dialog](#model-filters-display-and-dialog)
- [Model Filters View Filter Logic Graphical Display](#model-filters-view-filter-logic-graphical-display)
- [Entering a Range of Numbers](#entering-a-range-of-numbers)
- [Referencing Model Expressions](#referencing-model-expressions)
- [Copying Simulator Data to and from Other Applications](#copying-simulator-data-to-and-from-other-applications)
- [Save Case Information Data](#save-case-information-data)
- [Key Fields](#key-fields)
- [Required Fields](#required-fields)
- [Contour Column Dialog](#contour-column-dialog)
- [Contour Column Type](#contour-column-type)
- [Grid Metrics Dialog](#grid-metrics-dialog)
- [Geographic Data View](#geographic-data-view)
- [Geographic Data View Styles: Fields and Attributes](#geographic-data-view-styles-fields-and-attributes)
- [Geographic Data View Styles: General Display Options](#geographic-data-view-styles-general-display-options)
- [Geographic Data View Styles](#geographic-data-view-styles)
- [Custom Case Information Display](#custom-case-information-display)
- [Define Fields/Strings](#define-fieldsstrings)
- [Change Field Data](#change-field-data)
- [Show Fields Primary](#show-fields-primary)
- [Show Fields Secondary](#show-fields-secondary)
- [Custom Case Information Display Local Menu](#custom-case-information-display-local-menu)
- [User-Defined Case Information Displays](#user-defined-case-information-displays)

---

<a id="data-and-time-formatting-strings"></a>

## Data and Time Formatting Strings

*Source: [`Content/MainDocumentation_HTML/DateTime_Formatting_String.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DateTime_Formatting_String.htm)*

In various places in PowerWorld, a formatting string to indicate how to convert a floating point number representing the date and time into a formatted string. For example, this is done with the Text functions in the [custom expression function and operators](04-model-explorer-and-case-information-part2.md#functions-and-operators-available).

The floating point number is assumed to represent the date and time using the following convention. The integral part of the value is the number of days that have passed since 12/30/1899. The fractional part of the value is fraction of a 24 hour day that has elapsed. This number is assumed to be stored as a double precision floating point number which results in this number being accurate to about 1 millisecond. The formatting string should then use the table below to determine the results of the Text() function.

The following are several examples assuming that x1 =

|                                                   |                            |
| ------------------------------------------------- | -------------------------- |
| Example Function                                  | String Result of Function  |
| Text(42999.746, 'mm/dd/yyyy hh:nn:ss.zzz AM/PM')  | 09/21/2017 05:54:14.400 PM |
| Text(42999.746, 'd/m/yyyy hh:mm')                 | 21/9/2017 17:54            |
| Text(42999.746, 'h:nn ampm ''on'' ddd, m/d/yyyy') | 5:54 PM on Thu, 9/21/2017  |
| Text(42999.746, 'dddd, m/d/yyyy')                 | Thursday, 9/21/2017        |

In the following table, specifiers are given in lowercase. Case is ignored in formats, except for the "am/pm" and "a/p" specifiers.

|           |                                                                                                                                                                                                                                                                                                      |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Specifier | Displays                                                                                                                                                                                                                                                                                             |
| c         | Displays the date using the format given by the short date format specified in the Windows Region and Language Settings, followed by the time using the format given by the long time format of the Windows settings. The time is not displayed if the date-time value indicates midnight precisely. |
| d         | Displays the day as a number without a leading zero (1-31).                                                                                                                                                                                                                                          |
| dd        | Displays the day as a number with a leading zero (01-31).                                                                                                                                                                                                                                            |
| ddd       | Displays the day as an abbreviation (Sun-Sat) (The Windows Region and Language settings will impact the string used for the days)                                                                                                                                                                    |
| dddd      | Displays the day as a full name (Sunday-Saturday) (The Windows Region and Language settings will impact the string used for the days)                                                                                                                                                                |
| ddddd     | Displays the date using the format given by the short date format specified in the Windows Region and Language settings.                                                                                                                                                                             |
| dddddd    | Displays the date using the format given by the long date format specified in the Windows Region and Language settings.                                                                                                                                                                              |
| e         | Displays the year in the current period/era as a number without a leading zero (Japanese, Korean, and Taiwanese locales only).                                                                                                                                                                       |
| ee        | Displays the year in the current period/era as a number with a leading zero (Japanese, Korean, and Taiwanese locales only).                                                                                                                                                                          |
| g         | Displays the period/era as an abbreviation (Japanese and Taiwanese locales only).                                                                                                                                                                                                                    |
| gg        | Displays the period/era as a full name (Japanese and Taiwanese locales only).                                                                                                                                                                                                                        |
| m         | Displays the month as a number without a leading zero (1-12). If the m specifier immediately follows an h or hh specifier, the minute rather than the month is displayed.                                                                                                                            |
| mm        | Displays the month as a number with a leading zero (01-12). If the mm specifier immediately follows an h or hh specifier, the minute rather than the month is displayed.                                                                                                                             |
| mmm       | Displays the month as an abbreviation (Jan-Dec) (The Windows Region and Language settings will impact the string used for the days)                                                                                                                                                                  |
| mmmm      | Displays the month as a full name (January-December) (The Windows Region and Language settings will impact the string used for the days)                                                                                                                                                             |
| yy        | Displays the year as a two-digit number (00-99)                                                                                                                                                                                                                                                      |
| yyyy      | Displays the year as a four-digit number (0000-9999)                                                                                                                                                                                                                                                 |
| h         | Displays the hour without a leading zero (0-23)                                                                                                                                                                                                                                                      |
| hh        | Displays the hour with a leading zero (00-23)                                                                                                                                                                                                                                                        |
| n         | Displays the minute without a leading zero (0-59)                                                                                                                                                                                                                                                    |
| nn        | Displays the minute with a leading zero (00-59)                                                                                                                                                                                                                                                      |
| s         | Displays the second without a leading zero (0-59)                                                                                                                                                                                                                                                    |
| ss        | Displays the second with a leading zero (00-59)                                                                                                                                                                                                                                                      |
| z         | Displays the millisecond without a leading zero (0-999)                                                                                                                                                                                                                                              |
| zzz       | Displays the millisecond with a leading zero (000-999)                                                                                                                                                                                                                                               |
| t         | Displays the time using the format given by the short time format specified in the Windows Region and Language settings.                                                                                                                                                                             |
| tt        | Displays the time using the format given by the long time format specified in the Windows Region and Language settings.                                                                                                                                                                              |
| am/pm     | Uses the 12-hour clock for the preceding h or hh specifier, and displays 'am' for any hour before noon, and 'pm' for any hour after noon. The am/pm specifier can use lower, upper, or mixed case, and the result is displayed accordingly.                                                          |
| a/p       | Uses the 12-hour clock for the preceding h or hh specifier, and displays 'a' for any hour before noon, and 'p' for any hour after noon. The a/p specifier can use lower, upper, or mixed case, and the result is displayed accordingly.                                                              |
| ampm      | Uses the 12-hour clock for the preceding h or hh specifier along with either an "am" for hours before noon or "pm" for hours after noon. The Windows Region and Language settings will impact the string used for am and pm.                                                                         |
| /         | Displays the date separator character                                                                                                                                                                                                                                                                |
| :         | Displays the time separator character                                                                                                                                                                                                                                                                |
| 'xx'/"xx" | Characters enclosed in single or double quotation marks are displayed as such, and do not affect formatting                                                                                                                                                                                          |

---

<a id="find-dialog-basics"></a>

## Find Dialog Basics

*Source: [`Content/MainDocumentation_HTML/Find_Dialog_Basics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find_Dialog_Basics.htm)*

Many times when working with large load flow cases, it can be somewhat difficult to locate devices in the [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) regarding a specific device. Simulator has many tools to facilitate filtering data, such as the [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) and the [Advanced Filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) tool. Even with these helpful tools, finding a device can still be hampered when the bus number or exact spelling of the bus name are not known.

To facilitate locating devices in Simulator, you can use the Find tool to use Simulator’s advanced search engine for finding the device(s) you are looking for. The Find tool is available from the popup menus of almost all [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), as well as several of the various information dialogs in Simulator. Anywhere you see a button or menu option labeled **Find…** you can open the advanced search tool.

Once the Find dialog has been opened, the dialog will automatically adjust to suit the type of device you are searching for. The caption of the dialog should reflect the type of object the dialog is currently attuned to locate. For most devices, such as buses, generators, loads, etc., there will be one list displayed at the bottom of the dialog containing numbers and names of the type of device you are searching for. In some instances, mostly when searching for branch-type devices, the bottom panel is split with a second list is displayed in the right side panel. This list is used to display the possible connections of the bus selected in the first list. For example, if bus number one is selected and it has connections to bus two and bus three, the second list will display the information for bus two and bus three. Thus you can search for a bus in the first list, then choose from the possible connections in the second list to get a specific branch from the list.

Despite what type of device you are trying to find, the first few options and buttons on the dialog will be the same. **Sort by Name** and **Sort by Number** allow you to choose how you wish to find a device in the list. If you know the bus number you are looking for, choose **Sort by Number**. If you know the name, or at least part of the name, that you are looking for, then choose **Sort by Name**. The list (or first list for branches) will be sorted accordingly.

If you wish to narrow down the list of devices to search through, you have a couple of options for filtering the list before searching through it. First you can make use of the traditional [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) by clicking in the associated check box. If you need to set more specific conditions for filtering the list, you can instead click the **Define** button to set up an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering). The **Quick** button will allow the definition of a [Quick Filter](52-additional-linked-topics-part1.md#quick-filter), and the **Remove** button will remove any Advanced Filter or Quick Filter that has been selected.

Once you have the list set up for your search, you can type in the number or name you wish to find in the text box. If you do not know the exact number or name, you can use wildcards to facilitate the search and find all possible matches for a set of characters or numbers. You can use a question mark (?) to represent a single character wildcard, or an asterisk (\*) to represent a multiple character wildcard.

For example, if you want to find bus number 10005, but all you know is the first four digits are 1000, you can type in \*1000\*, and Simulator will search until it finds the first number that contains those four digits. You can then use the **Search Next** button (note that pressing **Enter** is the same as clicking **Search Next**) to find the next number containing the four numbers, and so on. The same goes for searching by name. If you are looking for bus ACEONE, but all you know is the name contains the string ACE, then you can type in \*ACE\* and then keep pressing **Enter** until you find the bus named **** ACEONE. By using the beginning and ending \*, we would also find elements such as NEWACE, because the double \* looks for strings that contain ACE anywhere in the string. Note that if you know the first few letters (or numbers), you can narrow down the number of elements found from the search by eliminating the first \* from the search string. For example, to find bus ACEONE, we could have instead used ACE\*, and this would have gone through all matches that started with ACE, ignoring other elements such as NEWACE. You can also use wildcards in the middle of a string, such as AC\*NE, and Simulator will find any name that starts with AC and ends with NE.

Once you have entered a wildcard search, you can also click the **Search All** button. This will essentially bring up the same Find dialog again, but with the choices narrowed to those that meet your wildcard search.

---

<a id="search-for-text-dialog"></a>

## Search For Text Dialog

*Source: [`Content/MainDocumentation_HTML/Search_For_Text_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Search_For_Text_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog allows you to search for specific text in a case information display. Specify the text you want to search in **Search for** edit box. Clicking on **Search Next** will take you to the next field whose content matches with the text specified. The search can be made **By Rows**, in which the text is searched first in all the fields of a record, before searching in the next record. If the search is made **By Columns** then the text is searched first in all the fields of a column, before searching the text in the next column. If the option **Match case** is checked, the search for text will be case-sensitive. The option **Find entire cells only** will take you only to fields whose entire content matches completely with the text you are searching for.

When checking the box **Search Ignore Filters**, Simulator will look through all the records of the type on your present case information display, but will ignore any [Area/Zone/Owner Filtering](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) and any [Advanced Filtering](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) specified with that case information display. If text is found which matches your wildcard search, but is for a record presently filtered out, then you will be prompted to remove the filtering so that the record can be displayed.

When checking the box **Search All Fields**, Simulator will look through every available field which can be displayed for the type of records presently represented on your case information display. If text is found which matches your wildcard search, but is for a field that is not presently shown, then you will be prompted to add the field to the columns that are shown.

---

<a id="model-conditions-display-and-dialog"></a>

## Model Conditions Display and Dialog

*Source: [`Content/MainDocumentation_HTML/Model_Conditions_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Conditions_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Model Conditions are a type of Model Criteria. Model Criteria represent boolean expressions regarding the present state of the power system model. They can be used to create a convenient display that shows whether the power system meets a set of criteria. They can also be used in conjunction with the definition of a contingency in the [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display) to create contingency actions that are conditional based on the state of the power system. To see a list of Model Conditions, choose **Case Information and Auxiliary \> Model Conditions**.

A model condition contains two parts: a power system element and an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering). The model condition will then return true or false depending on the result of applying the advanced filter to the power system element specified. Model conditions can also be used as part of a [Model Filter](#model-filters-display-and-dialog).

See the [Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions](52-additional-linked-topics-part1.md#relationship-between-contingencies-model-conditions-model-filters-and-model-expressions) topic for more information about how these work together.

The Model Conditions Display is a type of [Case Information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has the abilities common to this type of display. To delete a model condition, right-click on the display and choose **Delete**. To insert a new model condition, right-click on the display and choose **Insert**. This brings up the Model Conditions Dialog that can be used to create, delete, and modify Model Conditions.

Model Conditions Dialog

The Model Conditions Dialog has three sections. The top section provides the ability to **Save**, **Save As**, **Rename** and **Delete** model conditions. To choose a different Model Condition, click on the down arrow next to the Model Condition name.

The middle section provides a location to specify what power system element this Model Condition is related to. On the left is a list of **Element Types** that are available. When clicking on one of these types, the right portion of the dialog will provide you with a list of the elements of this type. This list is a familiar [Find Dialog](#find-dialog-basics) and provides you the ability to search for the element you are interested in.

The bottom section provides a location to specify an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) which you would like to have applied to the power system element chosen in the middle section. The bottom section of the dialog behaves identically to the [Advanced Filtering Dialog](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog). If an Advanced Filter exists for the type of element for which you are creating a Model Condition, you can click the **Set Filter Same As** button to choose this filter. This will then set the parameters of the Model Condition to be the same as the Advanced Filter.

![ModelConditionDialog](images/ModelConditionDialog.png)

Model Result Override Added in Version 20

[Model Result Overrides](22-contingency-analysis-options.md#model-result-override) can override the result of a Model Condition. If a model condition is being overridden, all of its conditions are ignored and the result comes directly from what is specified with the Model Result Override. If a model condition is being overridden by a model result override that is enabled, portions of the dialog will be highlighted in yellow and the message *Model Condition is overridden by a Model Result Override* will appear on the dialog. The model condition can still be modified while it is being overridden.

Options Used During Contingency Analysis

There are three options that can be specified with Model Conditions that are only applicable when Model Conditions are evaluated during [contingency analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview).

Evaluate in Contingency Reference State

When this option is in use, a Model Condition will be evaluated in the contingency [reference state](21-contingency-analysis-overview-and-records.md#contingency-case-references) and that result will be used when the Model Condition is evaluated again during a contingency implementation instead of evaluating the condition at the present system state.

Disable if True in Contingency Reference State

If this option is in use and a Model Condition evaluates to true in the contingency [reference state](21-contingency-analysis-overview-and-records.md#contingency-case-references), that Model Condition will be disabled, i.e. completely ignored, and treated as if it is not part of a [Model Filter](#model-filters-display-and-dialog) or will evaluate to false if it is being used as a standalone Model Condition. Any Model Filter whose component parts are all disabled will be disabled. This option is useful for applying conditional contingency actions based on an action occurring during a contingency and not being true in the base case. An example would be that generation drop should occur if a line is outaged due to a contingency action and not if it is out in the base case.

Evaluate Field in Contingency Ref State with each individual ModelConditionCondition.

Added in Version 19, build on December 18, 2015, each individual ModelConditionCondition also contains a check-box **Evaluate Field in Contingency Ref. State**. Check this box so that the value of the field chosen is evaluated in the references state of the contingency analysis tool. As an example, this allows the creation of one Model Condition, such as shown below, that specifies that a Branch be Online in this reference state and not Online in the post-contingency state.

---

<a id="model-filters-display-and-dialog"></a>

## Model Filters Display and Dialog

*Source: [`Content/MainDocumentation_HTML/Model_Filters_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Filters_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Model Filters are a type of Model Criteria. Model Criteria represent boolean expressions regarding the present state of the power system model. They can be used to create a convenient display that shows whether the power system meets a set of criteria. They can also be used in conjunction with the definition of a contingency in the [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display) to create contingency actions that are conditional on the state of the power system. To see a list of Model Filters, choose **Case Information and Auxiliary \> Model Filters** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

A model filter contains a list of [Model Conditions](#model-conditions-display-and-dialog) and/or other Model Filters and a boolean operator to apply to these conditions. The model filter then returns true or false depending on the result of applying the boolean operator to the boolean results of the conditions. A **NOT** operator can be applied to each condition so that the boolean opposite of the condition result will be used when evaluating the filter.

See the [Relationship Between Contingencies, Model Conditions, Model Filters, and Model Expressions](52-additional-linked-topics-part1.md#relationship-between-contingencies-model-conditions-model-filters-and-model-expressions) topic for more information about how these work together.

The Model Filters Display is a type of [Case Information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and has the abilities common to this type of display. To delete a model filter, right-click on the display and choose **Delete**. To insert a new model filter, right-click on the display and choose **Insert**. This brings up the Model Filters Dialog that can be used to create, delete, and modify Model Filters.

Model Filters Dialog

The Model Filters dialog behaves in a manner very similar to the [Advanced Filtering Dialog](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) in terms of how conditions are added, modified, and removed and how multiple conditions are combined through a logical comparison.

Filter Name

Name of the Model Filter currently being examined. To choose a different Model Filter, use click on the down arrow next to the Model Filter name.

**Save**, **Save As**, **Rename** and **Delete**

These buttons are found at the top of the dialog and allow the modification, creation, and removal Model Filters from the case without having to close the dialog.

Model Filter Conditions

A model filter is defined by any number of Model Conditions or Model Filters. To insert or delete conditions from the model filter, click the **Add\>\>** or **Delete...** buttons that are found below the list of conditions. The **X** to the left of a model filter condition can also be clicked to delete a condition.

To choose a particular Model Condition or Model Filter, click the dropdown arrow for the appropriate condition. The list will either contain Model Conditions or Model Filters depending on the option to display, either **Condition** or **Filter**. You may also click the **Find...** button to the left of the list.

Individually each condition can have a NOT operator applied to it by checking the **NOT** checkbox next to the condition. A **Time Delay** in seconds may be specified with each condition as well. Time Delays are used during contingency analysis. The treatment of time delays is described in the help topic [Treatment of Model Filter and Contingency Element Time Delays](23-contingency-analysis-running-and-results.md#treatment-of-time-delay-of-contingency-elements-and-model-filter-condition-time-delays).

To modify any Model Conditions definition, click the **Modify Model Conditions** button found below the list of conditions. This will open the [Model Conditions Dialog](#model-conditions-display-and-dialog).

Logical Comparison

When specifying more than one condition, this is the boolean operator that will be used to compare the conditions. The options are described in more detail in the [Advanced Filtering: Advanced](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) topic.

View Filter Logic

Click this button to open a graphical display that [visualizes the logic diagram for a Model Filter](#model-filters-view-filter-logic-graphical-display).

Model Result Override Added in Version 20

[Model Result Overrides](22-contingency-analysis-options.md#model-result-override) can override the result of a Model Filter. If a model filter is being overridden, all of its conditions are ignored and the result of the filter comes directly from what is specified with the Model Result Override. If a model filter is being overridden by a model result override that is enabled, portions of the dialog will be highlighted in yellow and the message *Model Filter is overridden by a Model Result Override* will appear on the dialog. The model filter can still be modified while it is being overridden.

Options Used During Contingency Analysis

Disable if True in Contingency Reference State Added in Version 20

This option is only applicable when Model Filters are being evaluated during [contingency analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview). If a Model Filter contains a Model Filter that has this option enabled and the Model Filter is true in the contingency [reference state](21-contingency-analysis-overview-and-records.md#contingency-case-references), that Model Filter will be disabled, i.e. completely ignored, and treated as if it is not part of the Model Filter. If a Model Filter is being used as a standalone criteria, it will evaluate to false.

Model Conditions can also be disabled using a similar option as described below. Any Model Filter whose component parts are all disabled will be disabled.

Model Conditions Disable if True in Contingency Reference State

[Model Conditions](#model-conditions-display-and-dialog) have an option to **Disable if True in Contingency Reference State**. This option is only applicable when Model Conditions are evaluated during [contingency analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview). If a Model Filter contains a Model Condition that has this option enabled and the condition is true in the contingency [reference state](21-contingency-analysis-overview-and-records.md#contingency-case-references), that Model Condition will be disabled, i.e. completely ignored, and treated as if it is not part of the Model Filter. If all of the Model Conditions in a Model Filter are using this option and all evaluate to true in the contingency reference state, that Model Filter will be disabled, i.e. completely ignored, if it is part of another Model Filter or will evaluate to false if being used as a standalone Model Filter.

---

<a id="model-filters-view-filter-logic-graphical-display"></a>

## Model Filters View Filter Logic Graphical Display

*Source: [`Content/MainDocumentation_HTML/Model_Filters_View_Filter_Logic_Graphical_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Filters_View_Filter_Logic_Graphical_Display.htm)*

The **Model Filter Logic Display** feature provides a graphical display which allows you to quickly browse information about a [Model Filter](#model-filters-display-and-dialog) and the corresponding [Model Conditions](#model-conditions-display-and-dialog). The model filter logic displays enable convenient Model Filter-by-Model Filter navigation through the complete list of model filters. From the model filter logic display, you can find out a model filter name and Logical Comparison object, and model conditions names that are part of the particular model filter. Moreover you can find out all information associated with the model filter or the model conditions by pressing right click with the mouse and directly invoking their associated information dialogs. The advantage of the model filter logic displays, is that they are auto-created logic diagrams.

Along the top of the model filter view display resides a panel of controls. To move the model filter logic view to a particular model filter, use the up and down arrow to move to the desired the model filter in the list. . If you are navigating and want to return to a previously open model filter press **History** to bring up a menu list of the previously open model filters. The menu will show a list of the last model filters which have been visited in a model filter view.

Below this top panel sits the actual model filter display. The model filter you have chosen to inspect, is represented as the last model filter to the right of the display. Notice that from this model filter there are also a connection to other model filters that are in a column. They represent the model filters in which the selected model filter is used as a model condition . When you drag the mouse over one of the neighboring model filters symbols, it turns into a pointing finger, then by clicking the left mouse button when the mouse cursor is in this shape redefines the target model filter to be the model filter whose symbol you just clicked. The model filter view display is redrawn to show the same sort of display for the newly chosen target. Right-clicking on the model filter view display’s background will generate the local menu.

The model filter background color can be red or green. Green means that the model criteria is satisfied and the evaluation of the model filter is true. Red means that the evaluation is false. The model filter objects also can have a circle entering to the model filter. This means that the connecting model filter or model condition will be negated. For example, if the model condition or filter entering another model filter model criteria is true it will evaluated as false in the entering model filter. Repeated colors of the Model Filter Names and Conditions represent that the particular Model Filter or Condition is used more than once in the Model Filter Display.

The model filter view display can be generated using any of the following methods:

  - Right click on the model filter of interest on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) on the model filter [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) of the contingency analysis folder. This will bring the local menu and the display can be opened by selecting "**Insert Filter Logic...**"
  - From the [Contingency Analysis Tool Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog), Go to the [Contingency Definitions](22-contingency-analysis-options.md#contingency-definition-dialog) inside the Options ribbon. In the model filters definitions case information repeat the previously explained process.
  - Pressing the "**View Filter Logic**" button in the [Model Filter Display](#model-filters-display-and-dialog) Dialog.

---

<a id="entering-a-range-of-numbers"></a>

## Entering a Range of Numbers

*Source: [`Content/MainDocumentation_HTML/Entering_a_Range_of_Numbers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Entering_a_Range_of_Numbers.htm)*

On a number of displays it is often convenient to enter a group of numbers, including ranges. Examples include entering buses or areas to scale on the [Scaling Display](18-general-tools.md#scaling) or values when using the *within integer range list* comparison with an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced). The format for this field is to enter individual numbers separated by commas, and/or ranges with a dash between the beginning of the range and the end of the range.

For example the entry

1-5,21,23-25

corresponds to numbers 1 through 5, 21 and 23 through 25.

---

<a id="referencing-model-expressions"></a>

## Referencing Model Expressions

*Source: [`Content/MainDocumentation_HTML/Model_Expression_Reference.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Expression_Reference.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A saved [Model Expression](04-model-explorer-and-case-information-part2.md#model-expressions) may be referenced directly in a Case Information Display or AUX file using special notation. A string of the format "&*ModExpName*:*digits*:*decimals*" will resolve to the result of the model expression named by *ModExpName*, with *digits* specifying the minimum number of digits to display, and *decimals* specifying the number of digits to show to the right of the decimal.

Note that the link to the Model Expression is not maintained after the initial entry. If the Model Expression is modified, or any of the relevant values change, the value in the Case Information Display will not update unless the reference is re-entered manually or the AUX file is re-loaded.

Example:

\&NetGeneration:5:2

---

<a id="copying-simulator-data-to-and-from-other-applications"></a>

## Copying Simulator Data to and from Other Applications

*Source: [`Content/MainDocumentation_HTML/copying_simulator_data_to_and_from_other_applications.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/copying_simulator_data_to_and_from_other_applications.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

You may sometimes find it useful to copy data from Simulator to other applications such as a word processor or spreadsheet program. Alternatively, you may want to copy data from other applications into Simulator. Simulator’s [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) provide a convenient way to accomplish this. In particular, the **Copy All**, **Copy Selection**, and **Paste** options from the local menu or the [Case Information Toolbar: Copy, Paste and Send Menu](04-model-explorer-and-case-information-part1.md#copy-paste-and-send-menu) allow Simulator to pass data with other applications through the windows clipboard.

To copy a selection of data from a case information display to another application, first select the range of cells to copy from the case information display. Then, right-click on the case information display to display its local menu, and choose **Copy Selection**. To copy the entire content of a case information display to another application, follow the same procedure, except choose **Copy All** from the local menu instead of **Copy Selection**. Switch to the application that will serve as destination for the data and use that application’s **Paste** command to finish copying the selected Simulator data to that application. Note that not only is the data copied, but by default so are the data headings. The data headings are very important to maintain if you are planning on copying data from a spreadsheet back into a Simulator case information display. Also note that Simulator copies the text to the windows clipboard with tabs delimiting each cell.

**Note:** Be aware that most programs have limitations on the amount of information you can paste. For example, some spreadsheet programs only allow up to 256 columns and 65,000 rows of information. Some power system information, particularly the Ybus or Jacobian matrices, can easily exceed these limitations.

To paste data from another application into a case-information display, select the data in the other application and use that application’s Copy command. In order to paste back into Simulator, you must have the record type and data headings selected with the columns of data. The record type (or object name) must match the case information display you are attempting to paste into, and the data headings (or variable names) tell Simulator which columns of data you are pasting. In order for the data to be pasted to the correct records, you must include the [key field](#key-fields) columns in the data to be pasted into Simulator. Also if you are attempting to create new data records by pasting back into Simulator then you must include the [required field](#required-fields) columns as well. If the object type is not valid then the **Paste** option will be disabled and the caption will read "object type invalid". If the key fields are missing, then the **Paste** option will be disabled and the caption will read "key fields missing".

It is not necessary to copy and paste all columns or rows of data back into Simulator, as long as the column headings match a valid heading for the case information display. Simulator will skip the data under any column headings that are unrecognized. If you wish to copy data from a spreadsheet into a Simulator display, you must make sure they are ordered in such a way that all the information you wish to paste can be grouped and copied as one block of date from the spreadsheet. Once you have copied all the information from the spreadsheet you wish to transfer, switch to Simulator, open the case information display in which to paste the data, and select **Paste** from its local menu.

**Note:** You can only paste values into the case information displays if the values are enterable on the display (shown blue by default). Also, be careful about pasting redundant data. For example, in the Bus Records display both voltage in *per unit* and voltage in *kV* are enterable, but they specify the same information. Make sure you only copy ONE of these columns into Simulator. Otherwise you may not get what you expect. Simulator will paste the value in twice, and whatever value was pasted 2nd will be used.

---

<a id="save-case-information-data"></a>

## Save Case Information Data

*Source: [`Content/MainDocumentation_HTML/Save_Case_Information_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Save_Case_Information_Data.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Save Data Dialog gives you quick access to saving data from certain [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) in a PowerWorld Simulator [Auxiliary](03-cases-files-and-formats.md#auxiliary-file-format-aux) File.

Specify the name of the auxiliary file in which to save the data records in the text box labeled **Name of File to Save**. Instead of typing the name of the file by hand, you can press the **Browse** button to locate it. Then, indicate whether you want the objects whose data you are writing to the file to be identified by number or by name. Finally, to ensure that only the records currently listed in the [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) are written to the auxiliary file, check the **Save Only Records Listed in this Display** checkbox. Otherwise, data for all such objects in the entire system will be saved to the file.

When you have finished setting these options, click **OK**. If you changed your mind and do not want to save the data to a file, click **Cancel**.

---

<a id="key-fields"></a>

## Key Fields

*Source: [`Content/MainDocumentation_HTML/Key_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Key_Fields.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Key fields are necessary fields when attempting to paste data into a [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) display from another data application. Other fields are also considered [required fields](#required-fields) for the purpose of creating new objects in Simulator by pasting or loading information from another source, such as Excel or a [PowerWorld Auxiliary](03-cases-files-and-formats.md#auxiliary-file-format-aux) file. The key fields are easily identified from a few different locations.

Column Headings

The column headings of case information displays are colored to indicate fields that are [key fields](#). Any field that is a [key fields](#) will be highlighted yellow. Also note that some fields are highlighted green. These fields are [required fields](#required-fields) that are necessary when you are attempting to create a new object by pasting or loading the data from another application. If the necessary [key fields](#) (yellow) are not included in the data loaded from another source, the information for that object is ignored. If all of the [required fields](#required-fields) (green) are not included in an object that is detected as new, Simulator will skip it. If all the required fields are present, then Simulator can create the new object. Note that for new objects, the key fields are necessary as well.

Display/Column Options

The Display/Column Options dialog, available by right-clicking on any case information display, also has the capability to highlight both the [key fields](#) and [required fields](#required-fields), as described above. The check box labeled "Highlight Key Fields" will enable highlighting of the field names in the two lists on the display.

Export Object Fields

This option from the Help menu in Simulator allows you to export a list of most fields for each type of object in a case. The list also indicates which fields are [key fields](#) and required fields for each object. You can output this list of fields as either a text file or into Excel.

The following table lists some of the more commonly accessed key fields needed when attempting to Paste data into existing objects in a Case Information Displays from another data application.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Type of Data</p></td>
<td><p>Data Description</p>
<p> </p></td>
<td><p>Necessary Key Columns for Paste</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Area</p></td>
<td><p>Area Records</p></td>
<td><p>Area Num</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Bus</p></td>
<td><p>Bus Records</p></td>
<td><p>Number</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>DC Line</p></td>
<td><p>DC Line Records</p></td>
<td><p>Rectifier Number</p></td>
<td><p>Inv Number</p></td>
<td><p>Num</p></td>
</tr>
<tr class="odd">
<td><p>Gen</p></td>
<td><p>Gen Records</p></td>
<td><p>Number</p></td>
<td><p>ID</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Interface</p></td>
<td><p>Interface Records</p></td>
<td><p>Name</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Line/Transformers</p></td>
<td><p>Line Records</p></td>
<td><p>From Number</p></td>
<td><p>To Number</p></td>
<td><p>Circuit</p></td>
</tr>
<tr class="even">
<td><p>Load</p></td>
<td><p>Load Records</p></td>
<td><p>Number</p></td>
<td><p>ID</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Substations</p></td>
<td><p>Substation Records</p></td>
<td><p>Sub Num</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Switched Shunt</p></td>
<td><p>Switched Shunt Records</p></td>
<td><p>Number</p></td>
<td><p>ID</p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Zone</p></td>
<td><p>Zone Records</p></td>
<td><p>Zone Num</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

---

<a id="required-fields"></a>

## Required Fields

*Source: [`Content/MainDocumentation_HTML/Required_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Required_Fields.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Required fields are necessary fields when attempting to create new objects by pasting data into a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) or when reading data from an [PowerWorld Auxiliary](03-cases-files-and-formats.md#auxiliary-file-format-aux). These fields are in addition to the [key fields](#key-fields) which identify the object.

There are two purposes of the required fields. First there are some fields for which an appropriate default value is not apparent thus by requiring these fields it forces the specification of the value. Second, when pasting data into Simulator it is possible that the record will not exist in the case. Simulator will then determine whether to create these records by looking to see if the required fields are specified. By doing this, it prevents the accidental addition of records. For instance you may have an Auxiliary File that sets the Monitor field of all branches in your case to Yes or No. If Simulator runs across a branch between two buses that exist, but whose circuit ID does not exist, then Simulator will just skip this line from the Auxiliary File. It will not be possible to accidentally create a bunch of new transmission lines with default impedance parameters because the R and X impedance parameters are required.

The required and key fields are easily identified from a few different locations.

Column Headings

The column headings of case information displays are colored to indicate fields that are [key fields](#key-fields). Any field that is a [key fields](#key-fields) will be highlighted yellow. Also note that some fields are highlighted green. These fields are [required fields](#) that are necessary when you are attempting to create a new object by pasting or loading the data from another application. If the necessary [key fields](#key-fields) (yellow) are not included in the data loaded from another source, the information for that object is ignored. If all of the [required fields](#) (green) are not included in an object that is detected as new, Simulator will skip it. If all the required fields are present, then Simulator can create the new object. Note that for new objects, the key fields are necessary as well.

Display/Column Options

The Display/Column Options dialog, available by right-clicking on any case information display, also has the capability to highlight both the [key fields](#key-fields) and [required fields](#), as described above. The check box labeled "Highlight Key Fields" will enable highlighting of the field names in the two lists on the display.

Export Object Fields

This option from the Help menu in Simulator allows you to export a list of most fields for each type of object in a case. The list also indicates which fields are [key fields](#key-fields) and required fields for each object. You can output this list of fields as either a text file or into Excel.

An example of required fields for an object is for a Branch object. For a branch object, the key fields are the from bus number, to bus number and the circuit ID. Required fields are the Impedance Values R, X, and B and the first three ratings A, B, and C. Without specifying values for these fields you can not create a new branch.

---

<a id="contour-column-dialog"></a>

## Contour Column Dialog

*Source: [`Content/MainDocumentation_HTML/Contour_Column_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contour_Column_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contour Column Dialog allows you to contour case information display columns.

The Contour Column Dialog has two tabs:

[Contour Type](#contour-column-type)

[Custom Color Map](17-oneline-view-printing-and-contouring.md#custom-color-map)

---

<a id="contour-column-type"></a>

## Contour Column Type

*Source: [`Content/MainDocumentation_HTML/Contour_Column_Type.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contour_Column_Type.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Color Map

Choose from various predefined color maps using the color map combo-box. A color map, along with the values specified, defines how values are mapped to a color on the contour image.

If a color map showing both high and low values is desired (such as for bus voltages), use of "Blue = Low, Red = High" is recommended. If a color map showing only high values is desired (such as for line flows), use of "Weather Radar, Nominal to High" is recommended.

A user may also define additional color maps by going to the [Custom Color Map](20-sensitivities.md#advanced-lodf-calculation-dialog) Tab.

Reverse Color Map Colors

Check this box to reverse the colors of the selected color map, so the low color becomes the high color, and vice versa.

Brightness

Modify the brightness track bar to change the brightness of the color map.

Use cell values directly

Select this option to use the cell values to do the contouring.

Use the specified field below

Select this option to use a different field value to do the contouring.

Value

Select the quantity to use in the contouring from the Value dropdown box or click the **Find Value** button to find the desired field.

Draw Color Key

Checking this box will cause the contour to draw a color key showing which colors are mapped to which values. You can also give the color key a title, unit label, and specify the number of digits to display in numerical values.

Title

Title for the color key.

Entry Labels

Units of the contoured value displayed on the color key.

Dec. Pts.

Number of decimal places of the contoured value displayed on the color key.

Scalar

Multiplication factor that can be applied to the values when drawing the color key.

Use Equal Spacing For Discrete Maps

This option will draw the color key with equal spacing for all colors in the map, regardless of how close or distant the values the colors represent.

Use absolute value

Check this check-box to use the absolute values of the quantity selected at the Value dropdown box (above).

Values

These values along with the color map define how to convert your values into a color for the contour. The values are:

**Maximum**  The largest value allowed in the contour. All values above this will be mapped to the highest color. This value corresponds to 100% in the color map.

**Break High** This value is used by some color maps to highlight a lower limit. This value corresponds to 75% in the color map.

**Nominal**  This value is the nominal value for the contour. Values around this will be mapped to the middle color. This value corresponds to 50% in the color map.

**Break Low** This value is used by some color maps to highlight a lower limit. This value corresponds to 25% in the color map.

**Minimum** The smallest value allowed in the contour. All values below this will be mapped to the lowest color. This value corresponds to 0% in the color map.

Note: a representation of the color map is shown to the right of the values.

---

<a id="grid-metrics-dialog"></a>

## Grid Metrics Dialog

*Source: [`Content/MainDocumentation_HTML/Grid_Metrics_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Grid_Metrics_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is accessed from the local menu of a case information display by selecting **Get Column Metrics** from the [Set/Toggle/Columns menu entry](04-model-explorer-and-case-information-part1.md#set-toggle-and-columns-menus). The dialog allows you to determine the metrics for a set of columns. The metrics determined include: Sum, Average, Variance, Standard Deviation, Maximum, Minimum, Total Items, and Total Non-Zero Items.

By default the dialog is set to determine the metrics for the whole column of the case information display where the option has been selected. However, the selected record set can be modified.

Start Column, End Column

These values specify what columns to include in determining the metrics.

Start Row, End Row

These values specify what records to include when computing the metrics.

Treatment of blank cells

If the option *Treat blank cells as zero* is checked, any blank cells will be considered as zero when computing the metrics. Instead, if the option *Ignore blank cells for calculation* is checked, any blank cell will be taken out of the metrics calculation.

Use Absolute Values

Check this box to use the absolute values of field values for the metrics computation.

Update Metrics

Click this button to determine the metrics with the new set of options.

---

<a id="geographic-data-view"></a>

## Geographic Data View

*Source: [`Content/MainDocumentation_HTML/Geographic_Data_View.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Geographic_Data_View.htm)*

Geographic Data Views allow the quick creation and formatting of graphical representations of buses, generators, loads, switched shunts, transmission lines, substations, areas, zones, super areas, and injection groups. Latitude and longitude coordinates specified with buses and substations are used to place objects geographically on a display. The latitude and longitude coordinates must be specified in order to use this feature. Object attributes such as color, size, rotation rate, rotation angle, and visibility can easily be formatted based on the associated data object field values.

To create a Geographic Data View, open a case information display for the desired element type, select the elements for which to add geographic representations, and either right-click on the object grid and choose **Geographic Data View \> Geographic Data View** from the local menu or choose **Geo \> Geographic Data View** from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar). Use the **Select Column, then Geographic Data View** option to select an entire column of elements. The column in which the elements are selected determines the initial selection of the field to use for [attribute settings](#geographic-data-view-styles-fields-and-attributes). The Geographic Data View Customization dialog will open.

Geographic Data View Customization Dialog

![Geographic Data View Customization Dialog](images/Geographic_Data_View_Customization_Dialog.gif)

Oneline for Geographic Data Addition

When creating a new geographic data view, the oneline to which to add the geographic data view objects must be set. Choose either to **Use Already Open Oneline** and then select a oneline from the dropdown list of available onelines or choose to **Open a Oneline** and then either type in the name of a PWD file or click Browse to select a one.

Because geographic data views are dependent on having geographic latitude and longitude information available, the oneline that is selected must have a valid map projection in use. Only those open onelines that currently have a [map projection](16-oneline-gis-tools.md#geographycoordinates) in use will be listed in the dropdown box and any oneline opened from a file will be checked for a valid map projection. If a valid map projection does not exist, new geographic data view objects will not be added to the oneline.

Create Oneline with Geographic Borders

Click this button to create a new oneline diagram with first being prompted to add geographic borders. A default name will be assigned to the new oneline and that oneline will be added as the selected oneline in the Use Already Open Oneline dropdown.

Setting Attributes for Geographic Data View Display Objects

Before adding new geographic data view objects, the attributes associated with the objects should be set. These attributes are stored in [Geographic Data View Styles](#geographic-data-view-styles).

Create Empty Oneline

Click this button to create a new oneline diagram. A default name will be assigned to the new oneline and that oneline will be added as the selected oneline in the Use Already Open Oneline dropdown.

Create Geo Data View Display and Close Dialog

Click this button to accept all of the option settings, add new geographic data view objects to the selected oneline, and then close the dialog.

Cancel

Click this button to close the dialog without adding and new geographic data view objects.

---

<a id="geographic-data-view-styles-fields-and-attributes"></a>

## Geographic Data View Styles: Fields and Attributes

*Source: [`Content/MainDocumentation_HTML/Geo_Data_View_Styles_Fields_and_Attributes.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Geo_Data_View_Styles_Fields_and_Attributes.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Field and Attributes options associated with Geographic Data View Styles allow the formatting of the geographic data view display objects depending on the values of fields of their linked data objects.

![Geo Data View Style Fields and Attributes](images/Geo_Data_View_Style_Fields_and_Attributes.jpg)

Attribute

Most of the attributes can have a **Default** value or a value that is dependent on the value of a selected field. When the **Use** box is checked for a particular attribute, the field selected in the **Field Lookup** is used to determine the value of the attribute based on either a Color Map or Value Map lookup. Otherwise, the default value will be used. Line Thickness, Total Area, Rotation Angle, and Rotation Rate attributes all use value map lookups. Line Color and Fill Color both use color map lookups. When determining the Field Lookup, either select the field from the drop-down or use the Find button to open the [Find field dialog](#find-dialog-basics) for easy searching.

When an attribute is selected, either by clicking on one of the options settings for that attribute or just clicking the background box for that attribute, the appropriate color map or value map for that attribute will be displayed in the right-hand panel.

Line Thickness

Thickness of the line making up the outside border of the display object.

Line Color

Color of the line making up the outside border of the display object.

Fill Color

Fill color of the display object. The Fill Color will be used only if the **Use Fill** box is checked.

There are two choices of Field Lookup for this attribute. The top choice is enabled regardless of the choice of object [Style](#geographic-data-view-styles-general-display-options). The bottom choice is only enabled when the Kite style is chosen. The Kite style allows two different fields to be displayed in one object. This is useful for displaying fields like Mvar Maximum and Mvar Minimum. The top field indicates what field will be used to format the top half of the Kite, and the bottom field indicates what field will be used to format the bottom half of the Kite.

When using the Kite style, use of the two different Field Lookups can be selected independently and each has a separate color map. When not choosing to use one or both of the Field Lookups, that appropriate half of the Kite shape will use the default Fill Color choice. To switch between color maps for the two Field Lookup choices, either click on the field drop-down for the appropriate half of the Kite or click the ![Geo Data View Style Color Map Arrow](images/Geo_Data_View_Style_Color_Map_Arrow.jpg) button that will appear next to the field choices when the Kite style is selected.

Total Area

This determines the size of the display object. Check the option to **Use Auto Width of Objects** for the width of the objects to be determined automatically. If this option is not checked, the **Width** can be set manually. The height or size is always determined as a function of the width and can be set with the **Size to Width Ratio**. When using the Field Lookup table the total area of the object is determined based on the Characteristic Value returned. The dimensions of the object are then determined based on the total area and the Size to Width Ratio.

There are two choices of Field Lookup for this attribute. The top choice is enabled regardless of the choice of object [Style](#geographic-data-view-styles-general-display-options). The bottom choice is only enabled when the Kite style is chosen. The Kite style allows two different fields to be displayed in one object. This is useful for displaying fields like Mvar Maximum and Mvar Minimum. The top field indicates what field will be used to format the top half of the Kite, and the bottom field indicates what field will be used to format the bottom half of the Kite. Even though two fields can be chosen when using the Kite style, only one value map is used for the Field Lookup. When using the Kite style and using the Field Lookup the total area of the object is based on the sum of the lookup values returned for both fields.

Rotation Angle

Static angle of rotation of a display object in degrees.

Rotation Rate

This value is given in Hz and indicates how many times per second an object should do a full rotation. This is used in conjunction with the [General Option for Animation Control](#geographic-data-view-styles-general-display-options). If animation control is not enabled, the rotation rate has no effect on how the objects are displayed.

Visibility

This attribute can prevent display objects from being shown if certain conditions are not met. ****Choosing the **All Visible** option ****will always show all of the display objects associated with this style. If choosing the option **Only visible if field is non-zero**, select a field from the drop-down box. Only those objects whose selected field is non-zero will be visible. If choosing the option **Only visible if filter is met**, select a filter from the drop-down box or click the Find button to search for an existing filter or create a new one. Only those objects that meet the selected filter will be visible. Note that the visibility attribute is only applied while in Run Mode. All objects will be visible in Edit Mode regardless of how this option is set.****

Color Map

Color maps are used with Line Color and Fill Color attributes. The Field Set Metrics section simply gives some statistics on the values of the selected field for the data objects. These metrics are provided to aid in the setting of the breakpoint values for the color map.

Color Map

Choose from the predefined color maps using the drop-down.

Reverse Color Map Colors

This checkbox reverses the mapping of the color map, converting the colors corresponding to the high values into the colors for the low values, and vice-versa.

Use Discrete Color Map

Check this box to make a discrete color map, that is without having smooth transitions between colors.

Brightness

Modify the brightness track bar to change the brightness of the color map.

Use Absolute Value

Check this box to use the absolute values of the field values when mapping the field values to colors.

Breakpoint Values

The breakpoint values determine how the field values will map to colors.

Set Breakpoints from Metrics

As different fields are chosen for attributes, the Field Set Metrics will be updated to reflect the field values. Click this button to update the breakpoint values based on a new set of Field Set Metrics.

Value Map

Value maps are used with Line Thickness, Total Area, Rotation Rate, and Rotation Angle attributes. The Field Set Metrics section simply gives some statistics on the values of the selected field for the data objects. These metrics are provided to aid in the setting of the Field Values and corresponding Characteristic Values.

The attribute value for a particular display object is set to the Characteristic Value that corresponds to the field value of the corresponding data object. Characteristic values will be interpolated if the field value does not fall exactly on a value that has been defined in the table. To insert entries into the table, right-click on the table grid and choose Insert from the local menu. Choose Delete from the local menu to remove entries.

![Geo Data View Style Value Map](images/Geo_Data_View_Style_Value_Map.jpg)

Attributes for All Objects In Style

These attributes apply to all objects independent of any specific field value.

Layer

Type in the name of an existing layer to assign the objects to an existing layer, or type in the name of a new layer to have that layer created and add the objects to that layer.

Stack Level

An object's stack level dictates what objects it will appear above and which objects it will appear below on a oneline display. For example, circuit breaker and pie chart objects have a default stack level of Top. Therefore, anything with a stack level of Middle, Background, or Base will appear underneath pie charts and circuit breakers on the oneline display. Objects that are within the same stack level and are drawn in the same location will result in the last object drawn being the visible object on the display.

Line Dashed

This determines the appearance of the line making up the outside border of the display object. This line can be solid or one of the dashed options.

Immobile

Check this box to keep the geographic display objects from being moved on the oneline diagram.

Set Font

Click this button to bring up the Select Font Options dialog. The changes to font are limited to Font Name, Font Color, and special Font Effects of Bold, Underline, Italic, and Strikeout. There is no option for setting the font size because this is automatically determined based on the size of the display object.

![Geo Data View Style Font Options](images/Geo_Data_View_Style_Font_Options.gif)

---

<a id="geographic-data-view-styles-general-display-options"></a>

## Geographic Data View Styles: General Display Options

*Source: [`Content/MainDocumentation_HTML/Geo_Data_View_Styles_General_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Geo_Data_View_Styles_General_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The General Display Options associated with Geographic Data View Styles are applied to all geographic data view objects independent of any field value.

![Geo Data View Style General Options](images/Geo_Data_View_Style_General_Options.gif)

Style

The style determines the shape of the geographic data view display object used to represent the selected data records.

Object ID

Each geographic data view display object can be identified by name, number, or a combination of the two. When a choice other than *None* is selected, the appropriate identification for that object will be displayed. When **Prefix ID with Object Type** is selected, the object type will be prefixed along with the main identifier. This option is useful when trying to distinguish between the different types of objects shown on a given display.

Selection Options

Geographic data view display objects can be formatted differently when they are selected as opposed to not selected. Check the option **Can Be Selected** to allow objects to be formatted based on the set options when they are selected. **Line Thickness** determines the thickness of the border line around the outside of the display object when it is selected. **Line Color** determines the color of the border line around the outside of the display object when it is selected.

Animation Control

Geographic data view display objects are capable of being animated if a [Rotation Rate](#geographic-data-view-styles-fields-and-attributes) other than zero is specified with the [attributes](#geographic-data-view-styles-fields-and-attributes). Check the **Enable Animation** box to animate the objects using this style. The **Interval** determines how often the display is refreshed during animation.

---

<a id="geographic-data-view-styles"></a>

## Geographic Data View Styles

*Source: [`Content/MainDocumentation_HTML/Geographic_Data_View_Styles.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Geographic_Data_View_Styles.htm)*

Each geographic data view object has an associated Geographic Data View Style. The style determines how the object is going to be displayed and contains options for setting various attributes associated with the object. Each style refers to a particular type of object. Geographic data view objects cannot be individually formatted; they will always obey the formatting of their associated style.

The **Geographic Data View Options** dialog is used to create and modify styles that will determine the appearance of geographic data view objects. This dialog is part of the [Geographic Data View Customization](#geographic-data-view) dialog when adding new geographic data view objects to a display, but it becomes a stand-alone dialog when modifying the styles for existing objects. To open as a stand-alone dialog, right-click on an existing geographic data view object and choose **View Geographic Data View Options** from the local menu.

Usually, groups of objects share the same geographic data view style. Keep in mind that changing the options in a style will change all of the objects that use this style.

Geographic Data View Options Dialog

The Geographic Data View Options dialog is made up of four main sections and tabs:

Object and Field Display Option Sets

![Geo Data View Style Save Style Options](images/Geo_Data_View_Style_Save_Style_Options.jpg)

This section allows the saving, renaming, and deleting of Geographic Data View Styles. Only those styles for a particular **Object Type** will be displayed in the **Style Name** dropdown box. Style names must be unique within an Object Type. Geographic data view styles can be stored in the standard [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) format. When saving or loading an auxiliary file from this dialog, all geographic data view styles will be stored or loaded regardless of the current object type. The default is to store the information in a data auxiliary file, .AUX, but these objects are also supported in display auxiliary files, .AXD.

[General Display Options](#geographic-data-view-styles-general-display-options)

[Fields and Attributes](#geographic-data-view-styles-fields-and-attributes)

Object Records

The object records tab lists the data objects that are linked to the geographic data view style, through their associated geographic data view display objects, selected when the dialog is opened. The caption of this tab will be updated to reflect the class type of object that is represented. For example, if viewing bus objects, the caption will be *Bus Records* instead of *Object Records*. These are either the data objects selected before creating a new geographic data view or data objects represented by existing geographic data view objects that are using the selected style. The format of the display objects represented by these data objects will be changed based on any changes made to the options. To assign a group of geographic data view display objects to a new style, simply select a different style than the style in place when opening the dialog and click either the **OK** button on the **Geographic Data View Options** dialog (existing data object was selected) or the **Create Geo Data View Display and Close Dialog** button on the **Geographic Data View Customizations** dialog (new geographic data view objects are being created).

To change the style of a single geographic data view display object and assign it to a new style, use the Display Explorer. Within the Display Explorer, [case information displays](15-using-onelines-tools-and-options.md#display-objects-case-information-display) for geographic data view objects are available. The style is given in the field **Geographic Data View Style Name** (variable name GEODATAVIEWSTYLENAME). To change the style, change the name listed in this field to a style that is available for the type of object being changed.****

---

<a id="custom-case-information-display"></a>

## Custom Case Information Display

*Source: [`Content/MainDocumentation_HTML/Custom_Case_Information_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Case_Information_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open the Custom Case Information Displays, go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Custom Case Info** from the **Case Data** ribbon group** **

Custom Case Information Displays can be used to create a display very similar in appearance to a spreadsheet workbook with several worksheets. This display can show any information that can be shown on a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays), but also allows you to customize the layout of the information in any manner.

There are three buttons which allow you to **Rename** the present sheet, add a **New** sheet, or **Delete** the present sheet.

There are three different kinds of cells allowed on this display

  - Blank Cell – contains nothing
  - Plain Text Cell – contains a user-entered string with no link to any data in the model.
  - Model Field Cell – contains a link to model field similar to inserting a [model field](13-building-onelines-graphics-and-insertion.md#generic-model-fields) on a oneline diagram

Each cell of the display will behave differently depending on the Custom Case Info Mode. There are four distinct modes that control the user interaction and operation of the custom case information display. These four modes and the effect they have on the display are described in topics

  - [Define Fields/Strings](#define-fieldsstrings)
  - [Change Field Data](#change-field-data)
  - [Show Fields Primary](#show-fields-primary)
  - [Show Fields Secondary](#show-fields-secondary)

---

<a id="define-fieldsstrings"></a>

## Define Fields/Strings

*Source: [`Content/MainDocumentation_HTML/Define_Fields_Strings.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Define_Fields_Strings.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The "Define Fields/String" mode is the primary mode for use when setting up a new [Custom Case Information Display](#custom-case-information-display). The three kinds of cells behave as follows in this mode.

Blank Cell

To convert to a Plain Text Cell, just type in the cell. To convert to a Model Field Cell, double-click on the cell to open up a dialog for defining the model field.

Plain Text Cell

These cells will appear in the Case Info Display Enterable Color (blue by default). To change them just type on the cell. When pasting into such a cell or editing it directly it will parse the string entered trying to create a Model Field as though the string represents the model fields as shown in the Show Fields modes. If the string does not represent such a field, then it will remain a Plain Text Cell

Model Field Cell

Model Field cells will not be enterable. In order to edit these fields, you must double-click on the cell to open a dialog for defining the model field.

![image\\ebx\_384387013.gif](images/Custom_Case_Information_Display.gif)

---

<a id="change-field-data"></a>

## Change Field Data

*Source: [`Content/MainDocumentation_HTML/Change_Field_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Change_Field_Data.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The "Change Field Data" mode can be used to edit the data referred to by the model fields on a custom case information display. The three kinds of cells behave as follows in this mode.

Blank Cell

Blank cells may not be edited in any manner.

Plain Text Cell

Plain Text cells may not be edited in any manner. It will appear in a special color defined for the custom case information display which may be specified from the [local menu](#custom-case-information-display-local-menu) of the workbook tabs. By default this color is dark gray.

Model Field Cell

Model Field cells will behave according to the field to which they refer. Enterable fields will be enterable, toggleable fields will toggleable, etc… When pasting in the sheet in this mode you will be modifying the model data directly. In the following picture there are three fields in cells C4, C5, and C6 that refer to read-only, enterable, and toggleable field respectively. The fields are labeled using the plain text cells in D4, D5, and D6.

![image\\ebx\_-1806072601.gif](images/Custom_Case_Information_Change_Field.gif)

---

<a id="show-fields-primary"></a>

## Show Fields Primary

*Source: [`Content/MainDocumentation_HTML/Show_Fields_Primary.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Show_Fields_Primary.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The "Show Fields Primary" mode is used for interacting with an external spreadsheet to create the model field links in custom case information displays. The three kinds of cells behave as follows in this mode.

Blank Cell

Blank cells behave the same as for the "[Define Fields/Strings](#define-fieldsstrings) " mode.

Plain Text Cell

Plain Text cells behave the same as for the "[Define Fields/Strings](#define-fieldsstrings) " mode.

Model Field Cell

Model field cells will display a string which represents information about the model field link. The format for this string will be

‘model field name’ ‘variable name’ totaldigits decimalpoints IncludeUnits

The model field string will use the primary key fields.

When pasting into such a cell or editing it directly it will parse the string entered trying to create a Model Field as though the string represents the model fields as shown in the Show Fields modes. If the string does not represent such a field, then it will remain a Plain Text Cell.

![Custom Case Information Display Primary](images/Custom_Case_Information_Display_Primary.gif)

---

<a id="show-fields-secondary"></a>

## Show Fields Secondary

*Source: [`Content/MainDocumentation_HTML/Show_Fields_Secondary.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Show_Fields_Secondary.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This mode is identical to the [Show Fields](#show-fields-primary) mode, except that it will show model fields string using the secondary key fields.

![Custom Case Information Display Secondary](images/Custom_Case_Information_Display_Secondary.gif)

---

<a id="custom-case-information-display-local-menu"></a>

## Custom Case Information Display Local Menu

*Source: [`Content/MainDocumentation_HTML/Custom_Case_Information_Display_Local_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Case_Information_Display_Local_Menu.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

By right-clicking on the tabs representing the various sheets of the [custom case information display](#custom-case-information-display), a local menu appears giving you the following options.

  - Rename Sheet – this is only available if you click directly on a specific tab. Choose it to rename the sheet.
  - Delete Sheet – this is only available if you click directly on a specific tab. Choose it to delete the sheet.
  - New Sheet – Choose this to add a new sheet
  - Save All Sheets… – Choose this save all the information on the sheets to an auxiliary file. For the fields one the display, all information will be saved to the auxiliary file using [Primary Key Fields](#show-fields-primary) unless the Custom Case Info Mode is set to Show Fields Secondary. In this case, they will be saved using the secondary key fields.
  - Custom Case Info Mode – Choose this to open a submenu that allows you to change the mode.
  - Tabs Position – Choose this to open a submenu that allows you to change the location of the tabs relative to the sheets
  - Plain Text Change Data Color – Choose this to change the color which is used to denote Plain Text cells when the Custom Case Info Mode is set to [Change Field Data](#change-field-data). The default color is dark gray.

By right-clicking on one of the Custom Case Information Display sheets, you will open a local menu that has many options which are the same as other [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays). There are a few extra options listed as follows

  - Insert Row – Choose this to insert a new row at the location of the presently selected cell
  - Delete Row – Choose this to delete rows that are part of the present selection
  - Insert Column – Choose this to insert a new column at the location
  - Delete Column – Choose this to delete columns that are part of the present selection
  - Delete Cell – Choose this to delete the presently selected cells
  - Custom Case Info Menu – Choose this to open the same menu available by right clicking on the tabs representing the various sheets

---

<a id="user-defined-case-information-displays"></a>

## User-Defined Case Information Displays

*Source: [`Content/MainDocumentation_HTML/Model_Explorer_User_Defined_CaseInformation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Model_Explorer_User_Defined_CaseInformation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

While it is normally sufficient to customize the case information displays that come with the program, it is sometimes convenient to create different sets of columns, filtering, sorting, etc... for the same object type. One set of generator fields may be convenient for studying voltage regulation problems, while another set of generator fields may be convenient for looking at MW-related information. This ability is provided using the User-Defined Case Information Displays. This provides the ability to switch between different sets of columns, filters, sorting etc... without requiring repeated customizations.

Note: User-Defined Case Information Displays will not show any of the various Record-Specific Actions which often appear in the [Case Information Toolbar Records Menu](04-model-explorer-and-case-information-part1.md#records-menu). To access these special options, the normal case information display must be used instead.

The management of User-Defined Case Information Displays is all done from the [Model Explorer: Explore Pane](04-model-explorer-and-case-information-part1.md#model-explorer).

![Model Explorer User Defined CaseInformation](images/Model_Explorer_User_Defined_CaseInformation.gif)

Inserting User-Defined Case Information Displays

To define a User-Defined Case Information Display, right-click on the [Model Explorer: Explore Pane](04-model-explorer-and-case-information-part1.md#model-explorer). and choose **Insert User-Defined Case Info**. On the dialog which appears click **Find...** to change the **Object Type** and then enter a **Name** for the new display.

![Model Explorer User Defined CaseInformation Add](images/Model_Explorer_User_Defined_CaseInformation_Add.gif)

Viewing User-Defined Case Information Displays

A list of User-Defined Case Information Displays are shown in the folder **User-Defined** at the bottom of the [Model Explorer: Explore Pane](04-model-explorer-and-case-information-part1.md#model-explorer).

Removing User-Defined Case Information Displays

To remove a User-Defined Case Information Display, right-click on its entry under the **User-Defined** folder on the Explore Pane. Then choose **Remove User-Defined Case Info**.

Customizing User-Defined Case Information Displays

The customization of a User-Defined Case Information Display is exactly the same as all other case information displays. See the [Configuring Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) for more information.

Saving Settings for User-Defined Case Information Displays

Settings for the User-Defined Case Information Displays can be saved in the [Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux). To save these, in the Explore Pane, go to the Case Information and Auxiliary/User-Defined Case Info Displays. This will open a case information display showing the user-defined case information displays. Then save to an auxiliary file using the [Case Information Toolbar: Save Auxiliary Files Menu](04-model-explorer-and-case-information-part1.md#save-auxiliary-files-menu).

![Model Explorer User Defined CaseInformation Saving](images/Model_Explorer_User_Defined_CaseInformation_Saving.gif)
