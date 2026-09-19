---
title: "Building Onelines — Network Objects"
part: "Oneline Diagrams"
chapter_file: "11-building-onelines-network-objects.md"
topics: 28
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Building Onelines — Network Objects

Inserting areas, zones, owners, buses, substations, generators and loads onto a oneline.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (28)**

- [Edit Mode Overview](#edit-mode-overview)
- [Edit Mode General Procedures](#edit-mode-general-procedures)
- [Oneline Display Options](#oneline-display-options)
- [Anchored Objects](#anchored-objects)
- [Inserting and Placing Multiple Display Fields](#inserting-and-placing-multiple-display-fields)
- [Setting Default Drawing Options](#setting-default-drawing-options)
- [Area Display Objects](#area-display-objects)
- [Area Display Options Dialog](#area-display-options-dialog)
- [Zone Display Objects](#zone-display-objects)
- [Zone Display Options Dialog](#zone-display-options-dialog)
- [Super Area Display Objects](#super-area-display-objects)
- [Super Area Display Options Dialog](#super-area-display-options-dialog)
- [Owner Display Objects](#owner-display-objects)
- [Owner Display Options Dialog](#owner-display-options-dialog)
- [Area Fields on Onelines](#area-fields-on-onelines)
- [Zone Fields on Onelines](#zone-fields-on-onelines)
- [Super Area Fields on Onelines](#super-area-fields-on-onelines)
- [Owner Fields on Onelines](#owner-fields-on-onelines)
- [Bus Display Objects](#bus-display-objects)
- [Bus Fields on Onelines](#bus-fields-on-onelines)
- [Old Voltage Gauges](#old-voltage-gauges)
- [Old Voltage Gauge Options Dialog](#old-voltage-gauge-options-dialog)
- [Substation Display Objects](#substation-display-objects)
- [Substation Fields on Onelines](#substation-fields-on-onelines)
- [Generator Display Objects](#generator-display-objects)
- [Generator Fields on Onelines](#generator-fields-on-onelines)
- [Load Display Objects](#load-display-objects)
- [Load Fields on Onelines](#load-fields-on-onelines)

---

<a id="edit-mode-overview"></a>

## Edit Mode Overview

*Source: [`Content/MainDocumentation_HTML/Edit_Mode_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Edit_Mode_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Edit Mode is used to create and/or modify cases and onelines. You can use the Edit Mode to create a case from scratch or to modify existing power flow cases stored in PowerWorld PWB or AUX files, in the PTI Raw data format, GE PSLF EPC data format, or the IEEE Common Format. New users will find additional information with the [Tutorial Links](49-distributed-computing-and-tutorials.md#tutorials).

To enter the Edit Mode, select the **Edit Mode** button in the **Mode** ribbon group on any of the ribbon tabs.

A powerful capability of the Simulator is its ability to [create or modify](https://www.powerworld.com/WebHelpvoid\(0\);) a case by graphically placing/editing [display objects](https://www.powerworld.com/WebHelpvoid\(0\);) on a oneline diagram. These display objects consist of both power system devices, such as buses, generators, and transmission lines; and [additional objects](https://www.powerworld.com/WebHelpvoid\(0\);) that show various system parameters, provide descriptive text, or function as a static background.

Simulator’s oneline diagrams illustrate the current state of the components of the power system. Most display objects correspond to records in the underlying power system model, but not all records in the power system model need to have an associated display object. In fact, for large system models, it may be that most of the system will not be illustrated. In such cases, you will want to devote more detail to the more critical areas of the system so as not to clutter the view. Furthermore, it is possible to associate more than one oneline with a single power flow case, and a single oneline may be associated with multiple cases. This great flexibility can prove to be a big time-saver. Please see [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for a more thorough discussion.

---

<a id="edit-mode-general-procedures"></a>

## Edit Mode General Procedures

*Source: [`Content/MainDocumentation_HTML/Edit_Mode_General_Procedures.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Edit_Mode_General_Procedures.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In order to simplify the process of graphically constructing a power flow case, Simulator’s drawing interface obeys the following conventions for most objects:

Inserting a New Object

  - Go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and use the menus on the [Individual Insert](#) ribbon group to add a single oneline object type you would like to add to the oneline.
  - Left-click on the location on the display where you would like to position the object.
  - Once the object is placed, Simulator displays a dialog box that allows you to specify various options for the object.
  - If desired, use all the options available on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the appearance of the object once it has been placed.

Moving, Resizing, and Rotating an Existing Object

  - Select the object by clicking on the object with the left mouse button. Handles are displayed around the object to indicate it has been selected.
  - To move the position of the object, place the mouse anywhere on the object except at a handle location. Then drag the object around the screen by holding the left mouse button down.
  - To change the size of an object using the mouse, first select the object. Then place the mouse on one of the object’s resizing (white) handles. The cursor will change to either a horizontal, vertical or diagonal two-headed arrow shape. Then drag the mouse to change the object’s size. You can also specify the size of most objects using their dialog boxes.
  - To rotate an object, first select the object. Then place the mouse over the rotation (green) handle in the upper left corner of the selected object. The cursor will change to a rotation symbol. Clicking and dragging will then rotate the object. Note that if an object (e.g., a pie chart or transmission line) does not have a rotation handle in the upper left, the object cannot be rotated.

Viewing/Modifying Object Parameters

  - To view and/or change the options associated with a single object, right-click on the object. This either displays the object’s dialog box directly, or it display’s the object[local menu](https://www.powerworld.com/WebHelpvoid\(0\);), from which you can elect to see the object’s dialog box.

Selecting Several Objects to Modify Their Appearance

Hold down the Shift key while clicking objects on the screen to select several objects at once. You may then change the objects’ attributes, such as [Font, Line/Fill, etc.](https://www.powerworld.com/WebHelpvoid\(0\);), by using all the options available on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

To move the objects that are selected, click and hold down the left mouse button on any of the selected objects, drag the selected objects to a new location, and release the mouse button to place them. You can also move the selected objects by holding the SHIFT key and simultaneously using the UP, DOWN, LEFT, or RIGHT arrow keys (or use the Home, End, Page Up and Page Down keys to move objects).

To select a set of objects use the many options available on the [Select](02-simulator-ribbon.md#select-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to select a group of objects using a [rectangle, ellipse or polygon selector](02-simulator-ribbon.md#select-ribbon-group). You can also select only objects that meet some given criteria by using [Select by Criteria](14-editing-onelines.md#select-by-criteria-dialog)****. As an example, you can use Select By Criteria to select all the 345 kV transmission lines in a case. See [Select](02-simulator-ribbon.md#select-ribbon-group) ribbon group for more detailed help.

Changing An Object’s Screen Appearance

Use all the options available on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the screen appearance of either a selection of objects or the entire display.

---

<a id="oneline-display-options"></a>

## Oneline Display Options

*Source: [`Content/MainDocumentation_HTML/Oneline_Display_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Display_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) allows you to customize the appearance of the presently selected oneline diagram. To view this dialog, either select **Oneline Display Options** from the **Oneline Options** ribbon group**** on the **[Options](02-simulator-ribbon.md#options-tab-overview)** ribbon tab, or choose **Oneline Display Options** from the oneline’s [local menu](15-using-onelines-tools-and-options.md#oneline-local-menu) . Please see the [Oneline Display Options Dialog](#owner-display-options-dialog) help for more information.

---

<a id="anchored-objects"></a>

## Anchored Objects

*Source: [`Content/MainDocumentation_HTML/Anchored_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Anchored_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

While in [Edit Mode](#edit-mode-overview), Simulator allows certain objects to be attached, or *anchored*, to another object, called the *anchor*. When an object that functions as an anchor is moved, all objects that are anchored to it will move with it. This feature can be very useful when you move objects around the oneline diagram in Edit Mode.

Anchoring has the property of "stacking" in Simulator. In other words, one object is anchored to another, which is in turn anchored to yet another. The best way to describe this is by example. A generator text field can be anchored to a generator. The generator, in turn, can be anchored to its terminal bus. If you move the terminal bus, both the generator and its anchored fields also move with the bus. However, if you just move the generator itself, only the generator fields will move with it. The bus and all other objects anchored directly to the bus remain in their original location.

If anchors are deleted it is generally necessary to reset anchors on anchored objects go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Refresh Anchors** on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group.

There are several types of anchored objects:

[Buses](#bus-display-objects)

[Loads](#load-display-objects), [generators](#generator-display-objects), [switched shunts](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects), [bus fields](#bus-fields-on-onelines), [interfaces](12-building-onelines-branches-and-devices.md#interface-display-objects), [transformers](12-building-onelines-branches-and-devices.md#transformer-display-objects), [transmission lines](12-building-onelines-branches-and-devices.md#transmission-line-display-objects) and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) may be anchored to their associated bus. When the anchor bus is moved, these anchored objects will move with it.

[Substations](#substation-display-objects)

Similar to buses, any [loads](#load-display-objects), [generators](#generator-display-objects), [switched shunts](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects), [bus fields](#bus-fields-on-onelines), [interfaces](12-building-onelines-branches-and-devices.md#interface-display-objects), [transformers](12-building-onelines-branches-and-devices.md#transformer-display-objects), [transmission lines](12-building-onelines-branches-and-devices.md#transmission-line-display-objects), and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) may be anchored to their associated substations. When the anchor substation is moved, these anchored objects will move with it.

[Generators](#generator-display-objects)

[Generator fields](#generator-fields-on-onelines) and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) may be anchored to their associated generator. When the anchor generator is moved, these anchored fields will move with it.

[Loads](#load-display-objects)

[Load fields](#load-fields-on-onelines) may be anchored to their associated load. When the anchor load is moved, these anchored fields will move with it.

[Switched Shunts](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects)

[Switched shunt fields](12-building-onelines-branches-and-devices.md#switched-shunt-fields-on-onelines) and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) may be anchored to their associated switched shunt. When the anchor switched shunt is moved, these anchored fields will move with it.

[Area/Zone/Super Area Objects](#area-display-objects)

[Interfaces](12-building-onelines-branches-and-devices.md#interface-display-objects) and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) can be anchored to area/zone/super area objects.

[Lines and Transformers](12-building-onelines-branches-and-devices.md#transmission-line-display-objects)

[Circuit breakers](12-building-onelines-branches-and-devices.md#circuit-breakers-on-onelines), [line flow pie charts](12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines), [line fields](12-building-onelines-branches-and-devices.md#transmission-line-fields-on-onelines), and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) may be anchored to their associated line/transformer. When the line/transformer is moved, these anchored objects will move with it.

[Interfaces](12-building-onelines-branches-and-devices.md#interface-display-objects)

[Interface fields](12-building-onelines-branches-and-devices.md#interface-fields-on-onelines), [interface pie charts](12-building-onelines-branches-and-devices.md#interface-pie-charts-on-onelines), and [pie chart/gauges](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-dialogs) can be anchored to their associated interface.

---

<a id="inserting-and-placing-multiple-display-fields"></a>

## Inserting and Placing Multiple Display Fields

*Source: [`Content/MainDocumentation_HTML/inserting_and_placing_multiple_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/inserting_and_placing_multiple_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator provides a convenient method of adding display fields to a variety of oneline display objects and placing them in default positions relative to the display object. Unlike the field placement implemented by selecting **Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, the method described here allows you to place multiple fields around a display object in a single operation. This option is available for several different types of objects, including buses, generators, lines and transformers, shunts, and loads. The option can always be accessed by right clicking the display object of interest and selecting the **Add New Fields** **Around** **…** option from the resulting local menu. This brings up the **Insert New Fields around Selected Objects Dialog**. This dialog is divided into several tabs by object type. Only tabs that correspond to the type of objects you have selected will be available.

The tabs for inserting and placing multiple display fields for the various display objects (buses, generators, lines/transformers, shunts, and loads) are virtually identical in content. The tab illustrates the possible locations of the display fields for the various orientations of the display object. For example, since buses may be oriented either horizontally or vertically, the dialog shows how each of the eight possible bus fields would be positioned for each of the two orientations. Generators, loads, and shunts each have four possible orientations, so the dialog identifies the locations for the possible fields for each of the four orientations. Transmission lines and transformers can assume only one orientation, and the dialog will thus show the possible field locations for that single orientation.

Each field location is identified on the illustrations with a label of the form Pos \#. In order to modify the settings, move your mouse over the position on the dialog you want to change and click. This will bring up the appropriate Field Options Dialog such as the [Bus Field Options](06-object-properties-edit-mode-part1.md#bus-field-information), [Generator Field Options](06-object-properties-edit-mode-part1.md#generator-field-information), [Load Field Options](06-object-properties-edit-mode-part1.md#load-field-information), [Switched Shunt Field Options](06-object-properties-edit-mode-part3.md#switched-shunt-field-information), or the [Line Field Options](06-object-properties-edit-mode-part2.md#line-field-information). Simply select the field you want and choose **OK**. If you would like to set a default field to "none", click **Remove Field** instead of **OK**.

Click **OK** to implement your choices for field additions and placement, or click **Cancel** to discard the changes.

This help topic has gone over how to add new fields to existing display objects. It should be noted from this discussion that all objects have an associated set of default fields that will be added to the oneline when the objects are originally inserted. You may redefine the default fields selecting **Default Drawing Values** from the **[Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and modifying the [Default Drawing Options Dialog](#setting-default-drawing-options).

---

<a id="setting-default-drawing-options"></a>

## Setting Default Drawing Options

*Source: [`Content/MainDocumentation_HTML/Setting_Default_Drawing_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Setting_Default_Drawing_Options.htm)*

The Default Drawing Options dialog is used to define the default sizes of new display objects, as well as various other display parameters.

To open this dialog choose **Default Drawing Values **on the **General Options** ribbon group of the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab. These General Options are also available on the [Oneline](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.

The Default Drawing Values dialog is organized using a list showing the types of objects that can be added to onelines. To view information about a particular type of object, select that object type from the list and tables which describe the defaults available for that object will be populated. Two tabs will be available. One will contain the majority of default options that are available for the selected display object type, and the other will contain the default positions of fields that will be inserted when the object is inserted.

Generally, the Default Drawing Values apply when you insert *new* objects on an oneline diagram. Changing the Default Drawing Values does not automatically affect the *existing* objects already drawn on the diagram. However, you can select multiple objects on a oneline diagram, and right-click on any one object to invoke the object's popup menu. You will find the option **Apply Default Draw Values**, which will modify the formatting of the selected objects to meet the default drawing value specifications.

Variable Defaults depending on Voltage Level

Many kinds of objects can have more than one set of defaults specified depending on their voltage level. When more than one set of defaults is specified, the table is always sorted by Nom kV.

A new object is inserted with properties corresponding to the default with the lowest Nom kV that the object's nominal kV is larger than. If the object's nominal kV is smaller than all defaults, then it will be set according to the default with the lowest nominal kV.

For instance, assume 4 sets of defaults are defined for buses roughly as follows

Nom kV Size

\>400  15

\>300  10

\>200  8

\>100  5

A new bus with nominal voltage of 345 kV is inserted with size 10.

A new bus with nominal voltage of 299 kV is inserted with size 8.

A new bus with nominal voltage of 69 kV is inserted with size 5.

In order to add another set of defaults for a kind of object, right-click on the table and choose **Insert** from the local menu. In order to delete a set of defaults, right-click on the table and choose **Delete**. Once you have inserted a new default, specify the new Nom kV for the default along with the new defaults.

Notes: When you change the Nom kV of a default, the list always sorts itself according to Nom kV. **Insert** will not be enabled in the local menu for objects that cannot have more than one set of defaults. **Delete** will not be enabled if only one set of defaults is defined.

Modifying Values in the Default Drawing Values Dialog

The font colors in tables of this dialog follow the conventions of the [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays). Most default values are enterable and can be modified by selecting the value you want to change and then typing in the new value. Other values are toggleable and can be changed by double-clicking on the value. For reference regarding what the various "size" defaults mean, when the zoom level is at its nominal value (100%), the size of the screen is 100 by 100. There are also some special kinds of fields in this dialog which are discussed next.

Editing Colors and KV-Based Color Coding

In order to modify a color value, double-click on the colored rectangle to bring up the Color Dialog. Then specify the color you want. For some defaults, such as fill color, it is possible to specify the default color to be *none*. In order to set a color default to *none*, select the colored rectangle and press the Delete key.

At times, a user may want to see the kV level of screen objects directly from the oneline diagam, without having to open a text display. One way to do this is to color code the elements on the oneline diagram according to kV level. Right-click on the table and choose **Insert** from the local menu. Specify the Nom kV and color.

Editing Default Field Positions ("Pos1", "Pos2", etc…)

Many objects allow you to specify some default fields to be automatically added when a new object is drawn. For example, you may want to insert the bus name next to all new Bus Objects. For objects that allow the insertion of fields, a tab with field position diagrams will be available when that object type is selected. In order to specify the default positions of fields, click on the tab showing the field positions and click on the table row corresponding to the Nom kV of the defaults of interest. For object types that do not allow specifying the defaults by Nom kV, simply update the given position diagram. The position diagram will show the present settings for the new fields. Positions that have a default specified will be highlighted and the name of the default field will be shown. Positions with no default field will not be highlighted and will say "Pos1", "Pos2", etc…. For objects that have more than one possible orientation (e.g. generators can be up, right, left or down), there are multiple position diagrams showing the positions for each orientation.

In order to modify the settings, move your mouse over the position on the dialog you want to change and click. This will bring up the appropriate Field Options Dialog such as the [Bus Field Options](06-object-properties-edit-mode-part1.md#bus-field-information), [Generator Field Options](06-object-properties-edit-mode-part1.md#generator-field-information), [Load Field Options](06-object-properties-edit-mode-part1.md#load-field-information), [Switched Shunt Field Options](06-object-properties-edit-mode-part3.md#switched-shunt-field-information), [Line Field Options](06-object-properties-edit-mode-part2.md#line-field-information), [Interface Field Options](07-object-properties-run-mode-and-general-part2.md#interface-field-information), [Substation Field Options](06-object-properties-edit-mode-part1.md#substation-field-options), [Area Field Options](07-object-properties-run-mode-and-general-part2.md#area-field-information), [Super Area Field Options](07-object-properties-run-mode-and-general-part2.md#super-area-field-information), or the [Zone Field Options](#zone-fields-on-onelines). Simply select the field you want and choose **OK**. If you would like to set a default field to "none", click **Remove Field** instead of **OK**. You can also modify default fields by double-clicking on the table for "Pos1", "Pos2", etc… This brings up the appropriate Field Options Dialog as well. If you press the Delete key while on a "Pos" field in the table, it will set the default field to "none".

Editing Stub Size and Stub Space

When utilizing the [Automatically Insert Transmission Lines](13-building-onelines-graphics-and-insertion.md#automatically-inserting-transmission-lines) feature, the **Stub Size** and **Stub Space** values are used. Simulator will draw each automatically inserted branch such that it emerges from both its terminal buses at right angles. To accomplish this, Simulator draws each automatically inserted branch in three segments: two stubs perpendicular to the terminal buses having a length specified by the value supplied for **Stub Size**, and a third segment joining the two stubs. The amount of space between lines as they converge into a bus is set by **Stub Space**.

If you do not want transmission line stubs to be inserted, then set **Stub Size** to *none* or to a negative number. Note in order to set a value for **Stub Space**, **Stub Size** must be set to a positive number first.

Note: When specifying a Stub Size of 0 with Default Drawing Values for transmission lines, auto-inserted lines will be spaced appropriately at the bus instead of all being drawn from the middle of the bus.

Editing CB Size

When you insert new transmission lines or transformers, circuit breakers will automatically be inserted on the branch with their size specified by CB Size. If you do not want Circuit Breakers inserted for a particular voltage level, then set CB Size to *none* or a negative number.

Editing Pie Size

When you insert new transmission lines or transformers, pie charts will automatically be inserted on the branch with their size specified by Pie Size. If you do not want pie charts inserted for a particular voltage level, then set Pie Size to 'none' or a negative number.

Set Default Font

Click on this button to set the default font used for new text fields. This is the font which will be used for all new text fields. Note however that the default font size set using this dialog is not used *unless* the option **Use the default font size for new text objects** is selected. Otherwise, the specific kind of object and voltage level specifies what the font size should be. For example, in the Interface tab, one of the defaults is Font Size. New Interface Fields will use this font size.

Only Cut/Copy Display Objects, Not Power System Records

When you cut or delete an object from the oneline, Simulator needs to know whether you simply want to delete the display object from the oneline or to purge the definition of the power system object from the model. Check this box to tell Simulator to assume that it should always delete objects just from the oneline display, not from the power system model.

Oneline / Bus View Background Color

To change the default oneline background color, click on the Change button to select a new color. This color applies to both new oneline diagrams and the background color of the [bus view oneline](08-view-case-data-tools.md#bus-view-display) diagram.

Recommended Multi-KV Level Defaults

Click this button to change the default options back to Simulator recommended values. Multiple sets of default options will be specified based on voltage level for objects for which it is beneficial to do this (i.e. transmission lines).

Recommended Single-KV Level Defaults

Click this button to change the default options back to Simulator recommended values. A single set of default options will be specified for each object type.

Save All to Aux File and Load All From Aux File

The Default Drawing Options may also be stored in an Auxiliary File by Clicking the Save All to Aux File button to save all these customizations to an Auxiliary File or by clicking the Load All From Aux File to load all the custom hints from an Auxiliary File.

---

<a id="area-display-objects"></a>

## Area Display Objects

*Source: [`Content/MainDocumentation_HTML/Area_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Area records in the load flow data can be displayed as objects on a Simulator oneline diagram. This can be useful for building a diagram on which you also want to include representations of groups of devices by area.

To insert an Area object, select **Aggregation \>** **Area** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then left-click on a oneline diagram in the location where the Area object should be placed. This will open the [Area Display Options](#owner-display-options-dialog) dialog, which will allow you to choose the area information to display, and set parameters for the displayed object. It is important to note that area records, unlike other objects like buses and transmission lines, cannot be added to the load flow data graphically. To add a new area record to the load flow case, you need to change the area designation of a device in the load flow case to a new area number, or you need to insert a new area from the [Area Records](05-case-information-displays-by-object-part1.md#area-display).

Area objects can also be added by using the [Area insert palette](13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes).

---

<a id="area-display-options-dialog"></a>

## Area Display Options Dialog

*Source: [`Content/MainDocumentation_HTML/area_display_options_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/area_display_options_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When you insert an area display object on a oneline diagram, Simulator opens the Area Display Options dialog. This dialog is used to control various display and identity attributes of the area display object. The dialog contains the following fields:

Number

This dropdown box lists the number of all areas in the case. Use this control to associate the display object with the correct area.

Name

If you would prefer to search through areas by name rather than by number, use the *Name* dropdown box to see a list of names of all the areas in the case.

Show Record Type Prefix

Check this box if you wish to place the prefix **Area** before the name/number caption in the object.

Prefix Text

Specify additional prefix text to be added before the Record Type prefix.

The remainder of the choices presented on the *Area Display Options* dialog pertain to the object’s display appearance.

Style

Choose whether the display object should appear as a rectangle, rounded rectangle, or an ellipse.

Caption

Indicate how the display object should be identified to the user: by name, number, or both.

Width, Height

The dimensions of the new display object.

Click **OK** to save your selections and add the object to the oneline, or choose **Cancel** to terminate the addition.

---

<a id="zone-display-objects"></a>

## Zone Display Objects

*Source: [`Content/MainDocumentation_HTML/Zone_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Zone records in the load flow data can be displayed as objects on a Simulator oneline diagram. This can be useful for building a diagram on which you also want to include representations of groups of devices by zone.

To insert a Zone object, select **Aggregation \> Zone** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then left-click on a oneline diagram in the location where the Zone object should be placed. This will open the [Zone Display Options](#zone-display-options-dialog) dialog, which will allow you to choose the zone information to display, and set parameters for the displayed object. It is important to note that zone records, unlike other objects like buses and transmission lines, cannot be added to the load flow data graphically. To add a new zone record to the load flow case, you need to change the zone designation of a device in the load flow case to a new zone number, or you need to insert a new zone from the [Zone Records](05-case-information-displays-by-object-part1.md#zone-display).

---

<a id="zone-display-options-dialog"></a>

## Zone Display Options Dialog

*Source: [`Content/MainDocumentation_HTML/Zone_Display_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Display_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When you insert a zone display object on a oneline diagram, Simulator opens the Zone Display Options dialog. This dialog is used to control various display and identity attributes of the zone display object. The dialog contains the following fields:

Number

This drop down box lists the number of all zones in the case. Use this control to associate the display object with the correct zone.

Name

If you would prefer to search through zones by name rather than by number, use the *Name* drop down box to see a list of names of all the zones in the case.

Show Record Type Prefix

Check this box if you wish to place the prefix **Zone** before the name/number caption in the object.

Prefix Text

Specify additional prefix text to be added before the Record Type prefix.

The remainder of the choices presented on the *Zone Display Options* dialog pertain to the object’s display appearance.

Style

Choose whether the display object should appear as a rectangle, rounded rectangle, or as an ellipse.

Caption

Indicate how the display object should be identified to the user: by name, number, or both.

Width, Height

The dimensions of the new display object.

Click **OK** to save your selections and add the object to the oneline, or choose **Cancel** to terminate the addition.

---

<a id="super-area-display-objects"></a>

## Super Area Display Objects

*Source: [`Content/MainDocumentation_HTML/Super_Area_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Super_Area_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Super area records in the load flow data can be displayed as objects on a Simulator oneline diagram. This can be useful for building a diagram on which you also want to include representations of groups of devices by super areas.

To insert a Super Area object, select **Aggregation \> Super Area** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then left-click on a oneline diagram in the location where the Super Area object should be placed. This will open the [Super Area Display Options](#super-area-display-options-dialog) dialog, which will allow you to choose the super area information to display, and set parameters for the displayed object. It is important to note that super area records, unlike other objects like buses and transmission lines, cannot be added to the load flow data graphically. To add a new super area record to the load flow case, you need to insert a new super area from the [Super Area Records](05-case-information-displays-by-object-part1.md#super-area-display).

---

<a id="super-area-display-options-dialog"></a>

## Super Area Display Options Dialog

*Source: [`Content/MainDocumentation_HTML/Super_Area_Display_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Super_Area_Display_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When you insert a super area display object on a oneline diagram, Simulator opens the Super Area Display Options dialog. This dialog is used to control various display and identity attributes of the super area display object. The dialog contains the following fields:

Number

This field is unused for super area objects. Super areas are identified by a unique super area name instead.

Name

Use the *Name* dropdown box to see a list of names of all the super areas in the case.

Show Record Type Prefix

Check this box if you wish to place the prefix **Super Area** before the name/number caption in the object.

Prefix Text

Specify additional prefix text to be added before the Record Type prefix.

The remainder of the choices presented on the *Super Area Display Options* dialog pertain to the object’s display appearance.

Style

Choose whether the display object should appear as a rectangle, a rounded rectangle, or an ellipse.

Caption

Indicate how the display object should be identified to the user: by name, number, or both.

Width, Height

The dimensions of the new display object.

Click **OK** to save your selections and add the object to the oneline, or choose **Cancel** to terminate the addition.

---

<a id="owner-display-objects"></a>

## Owner Display Objects

*Source: [`Content/MainDocumentation_HTML/Owner_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Owner_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Owner records in the load flow data can be displayed as objects on a Simulator oneline diagram. This can be useful for building a diagram on which you also want to include summary objects by owner, in which information about the generation and load of the owner are indicated with the object.

To insert an Owner object, select **Aggregation \> Owner** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the **[Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab**. Then left-click on a oneline diagram in the location where the owner object should be placed. This will open the [Owner Display Options](#owner-display-options-dialog) dialog, which will allow you to choose the owner information to display, and set parameters for the displayed object.

---

<a id="owner-display-options-dialog"></a>

## Owner Display Options Dialog

*Source: [`Content/MainDocumentation_HTML/Owner_Display_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Owner_Display_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When you insert an owner display object on a oneline diagram, Simulator opens the Owner Display Options dialog. This dialog is used to control various display and identity attributes of the owner display object. The dialog contains the following fields:

Number

The owner number.

Name

The owner name.

Show Record Type Prefix

Check this box if you wish to place the prefix **Owner** before the name/number caption in the object.

Prefix Text

Specify additional prefix text to be added before the **Owner** prefix.

The remainder of the choices presented on the *Owner Display Options* dialog pertain to the object's display appearance.

Style

Choose whether the display object should appear as a rectangle or as an ellipse.

Caption

Indicate how the display object should be identified to the user: by name, number, or both.

Width, Height

The dimensions of the new display object.

Click **OK** to save your selections and add the object to the oneline, or choose **Cancel** to terminate the addition.

---

<a id="area-fields-on-onelines"></a>

## Area Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Area_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Area fields are used to show various values associated with a particular area of the power system. Right clicking on the area field displays the [Area Field Dialog.](07-object-properties-run-mode-and-general-part2.md#area-field-information)

Edit Mode

To enter a new area field, first select **Field \> Area Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then, click on or near the area object or a bus in the area for which you want to add a field. This calls up the [Area Field Dialog.](07-object-properties-run-mode-and-general-part2.md#area-field-information) Verify that the area number is correct. By default, this value is the number of the area associated with the closest area object, or if there are no area objects, the closest bus. Enter the total number of digits the field should display as well as the number of digits to the right of the decimal point. Depending on what the field is designed to display, you may need to enter an additional area number. Finally, select the field type. Click **OK** to save the field or **Cancel** to abort the operation.

With most types of area fields, an ****Area Number** ** of 0 is valid and defines the field as showing values for the entire system.

To modify the parameters of an existing area field, position the cursor anywhere on the area field and right-click. This again brings up the [Area Field Dialog.](07-object-properties-run-mode-and-general-part2.md#area-field-information) Use the ****[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)options to change various display attributes for the area field, including its font and background color.

---

<a id="zone-fields-on-onelines"></a>

## Zone Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Zone_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Zone field display objects are used to show different values associated with zones and the system on onelines. This Zone Field Options dialog is used to view (and in a few cases modify) the parameters associated with these zone fields. To reach this dialog, select **Field \> Zone Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and click the desired field location on a oneline diagram in Edit Mode, or right-click on an existing zone field on a oneline diagram. If in run mode, select the **Zone Field Dialog** option when right-clicking on the zone field.

Zone Number

Zone number associated with the field. When you insert fields graphically, this field is automatically set to the zone number associated with the closest bus on the oneline. With most types of zone fields, a **Zone Number** of 0 is valid and defines the field as showing values for the entire system.

Find…

If you do not know the exact zone number you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Total Digits in Fields

Total number of digits to show in numerical fields.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point in numerical fields.

Rotation Angle in Degrees

The angle at which the text is to appear on the oneline diagram.

Other Zone Number

Some of the fields, such as **MW Flow to Other Zone**, require that a second zone be specified. If applicable, enter the second (other) zone here.

Delta per Mouse Click

This value is used only with the **Load Schedule Multiplier** field type. When there is a non-zero entry in this field, and the field type is **Load Schedule Multiplier**, a spin button is shown to the right of the zone field. When the up spin button is clicked, the multiplier is increased by this amount; when the down button is clicked, the multiplier is decreased by this amount.

Field Value

Shows the current output for the zone field. Whenever you change the **Type of Field** selection, this field is updated.

For the **Sched Flow to Other Zone** field type only, you can specify a new value in MW. Exports are assumed to be positive.

Field Prefix

An optional string that precedes the field value.

Anchored

If the field is associated with a Zone Object on the diagram, the field can be anchored to the object so that if the object gets moved on the diagram, the field will move with it.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of zone field to show.

Name 

Zone name.

Number 

Zone number.

MW Load, Mvar Load

If the **Zone Number** is non-zero, then these fields show Total MW or Mvar load for the zone. If the zone number is zero, these fields show the total load in the entire system.

MW Generation, Mvar Generation 

If the **Zone Number** is non-zero, then these fields show Total MW or Mvar generation for the zone. If the Zone Number is zero, these fields show the total generation in the entire system.

MW Shunts, MVR Shunts

If the **Zone Number** is non-zero, then these fields show Total MW or Mvar shunt compensation for the zone. If the Zone Number is zero, these fields show the total shunt compensation in the entire system.

MW Flow to Other Zone, Mvar Flow to Other Zone

Total MW or Mvar flow from the zone specified in the **Zone Number** field to the zone specified in the **Other Zone Number** field. The Zone Number field must correspond to a valid zone. If the Other Zone Number field is zero, this field shows the zone's total MW or Mvar exports.

MW Losses, MVAr Losses

If the **Zone Number** is non-zero, then these fields show Total MW or Mvar losses for the zone. If the Zone Number is zero, these fields show the total real or reactive losses in the entire system.

Load Schedule Multiplier

Indicates the current value of the MW multiplier applied to the zone's loads.

Select a Field 

Choose from any of the available zone fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Checking the **Draw Sparkline** checkbox will display a [sparkline](52-additional-linked-topics-part2.md#sparklines) instead of a field value on the oneline and list only those fields that are available for representation as a sparkline.

Select **OK** to save changes and close the dialog or **Cancel** to close dialog without saving your changes.

---

<a id="super-area-fields-on-onelines"></a>

## Super Area Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Super_Area_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Super_Area_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To display certain information about a super area, such as MW Load or MVAR losses, insert a super area field. This can be done in Edit Mode by selecting **Field \> Super Area Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This will bring up the [Super Area Field Information](07-object-properties-run-mode-and-general-part2.md#super-area-field-information). From here you can choose which super area to describe, how many digits in the field, and how many digits to the right of the decimal. There are also 12 different field options to choose from. If a field value is not defined, question marks will be shown.

---

<a id="owner-fields-on-onelines"></a>

## Owner Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Owner_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Owner_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Owner field display objects are used to show different values associated with owners on onelines. To insert an Owner field, click on **Field \> Owner Field** in the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This dialog will be opened for specifying the parameters associated with the new field. This dialog can also be opened by right-clicking on an existing owner display field.

This dialog is used to view and modify the parameters associated with these fields.

Owner Number

Owner number associated with the field. When you insert fields graphically, this field is automatically set to the owner number associated with the closest bus on the oneline.

Find by Number

To switch to a different owner in the field options dialog, you can enter the number in the **Owner Number** field, and press the **Find by Number** button to update the dialog with information for the new owner.

Owner Name

Name of the owner whose information is presently being displayed in the dialog.

Find by Name

To switch to a different owner in the field options dialog, you can enter the name in the **Owner Name** field, and press the **Find by Name** button to update the dialog with information for the new owner.

Total Digits in Fields

Total number of digits to show in the field.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Prefix

An optional string that precedes the field value.

Rotation Angle in Degrees

The angle at which the text is to appear on the oneline diagram.

Field Value

Shows the current output for the owner field. Whenever you change the **Type of Field** selection, this field is updated.

Include Suffix

If this checkbox is checked, the corresponding field units will be displayed after the current value. Otherwise, only the value without units will be shown.

Type of Field

Used to determine the type of line field to show. The following choices are available:

Name

Name of the owner.

Number

Number of the owner.

MW Load

Total MW load of all loads belonging to this owner.

Mvar Load

Total Mvar load of all loads belonging to this owner.

MW Generation

Total MW generation of all generators belonging to this owner.

Mvar Generation

Total Mvar generation of all generators belonging to this owner.

Select a Field 

Choose from any of the available owner fields. Use the **Find Field** button to open a dialog from which the field can be selected.

Select **OK** to save changes and close the dialog or **Cancel** to close the dialog without saving your changes.

---

<a id="bus-display-objects"></a>

## Bus Display Objects

*Source: [`Content/MainDocumentation_HTML/Bus_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Display_Objects.htm)*

In power system analysis, the term "bus" is used to refer to the point where a number of electrical devices, such as lines, loads or generators, join together. On the oneline diagram, buses are usually represented with either a thick horizontal line or a thick vertical line. The bus thickness and color can be customized.

Right-clicking on the bus will display its local menu. The local menu offers you the chance to view the corresponding [Bus Dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog), the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list), and the [Bus View Display](08-view-case-data-tools.md#bus-view-display). When the application is in Edit Mode, the local menu will also allow you to add bus fields to the bus and to insert any undrawn buses connected to the selected bus. [Bus Fields](#bus-fields-on-onelines) are often placed close to the bus to indicate its voltage magnitude, voltage angle, and other relevant information. A more complete description of

Edit Mode

To add a new bus to the case graphically, follow this simple procedure:

  - Select **Network \> Bus** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group of the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This prepares Simulator to insert a new bus.
  - Left-click on the oneline background at the location where you want to place the new bus. This invokes the [Bus Option Dialog](06-object-properties-edit-mode-part1.md#bus-options).
  - Use the Bus Option Dialog to specify the number, name, size, thickness, orientation, area, zone, and nominal voltage of the bus, as well as the load and shunt compensation connected to it. Every bus must have a unique number.
  - The Bus Option Dialog will include a message just above the Bus Number field indicating that a new bus will be inserted into the power system data model. This will appear as long as the Bus Number that is selected does not already exist in the power system case.
  - Click **OK** on the Bus Option Dialog to finish creating the bus and to close the dialog. ** If you do not wish to add the bus to the case, click ****Cancel***.*

If you are simply adding a symbol to the oneline diagram for a bus that has already been defined in the case, many of the parameters you are asked to specify in step three will be filled in for you.

To modify the parameters for an existing bus, position the cursor on the bus and right-click to invoke the bus' local menu. From the local menu, choose **Bus Information Dialog** to view the associated [Bus Dialog.](06-object-properties-edit-mode-part1.md#bus-options) You may change any of the parameters specified there. When a bus' number is changed, the bus numbers associated with all of the devices attached to that bus are also automatically changed. To renumber several buses simultaneously, please see [Bus Renumbering Dialog](19-edit-mode-tools.md#bus-renumbering-dialog).

To modify any aspect of a bus' appearance, first select the bus, and then click any of the format buttons found in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. You can change the length of the bus (but not its thickness) by dragging the bus' resizing handles.

In order to delete an existing bus after selecting it, use either the **Cut** button, found in the [Clipboard](02-simulator-ribbon.md#clipboard-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, to preserve a copy of the bus on the Windows clipboard, or **Delete** button, found in the [Clipboard](02-simulator-ribbon.md#clipboard-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, to remove the bus without copying it to the clipboard. You will be asked whether you want to remove both the display object and its associated bus record, or merely the display object, leaving the bus in the power flow model. If you will never be deleting a record from the power system model, you may also choose the option labeled **Always Delete Objects Only**. Be careful when deleting existing buses with attached devices. An error will occur during validation if you do not also delete the attached devices or attach them to other buses.

Local Menu for Bus Display Objects

When right-clicking of a single Bus Display object in Edit mode a very large drop-down menu appears as shown in the image below. The first entry in this menu can not be clicked on and will show the Name of the Bus and then the Number of the bus enclosed in parantheses. Under this there are several options

<table>
<tbody>
<tr class="odd">
<td><ul>
<li><p><strong>Insert Connected Buses</strong> : has a submenu that will insert buses connected to the selected bus as well as options for <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-transmission-lines">Lines</a>, <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-generators">Gens</a>, <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-loads">Loads</a>, and <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-switched-shunts">Shunts</a>. There is also an option to setting the options related to these features. This feature will be impacted by the whether the DisplayBus has been flagged as AllowFixedNum = YES as described in <a href="17-oneline-view-printing-and-contouring.md#displaybus-property-allowfixednum" class="MCXref xref">AllowFixedNum property of a DisplayBus</a>.</p></li>
<li><p><strong>Auto Insert / Edit Oneline</strong> : An option to use the <a href="13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes" class="MCXref xref">Using the Insert Palettes</a>, <a href="19-edit-mode-tools.md#equipment-mover">Equipment Mover</a>, and <a href="19-edit-mode-tools.md#splitting-buses">Split Bus Tool</a>. Choosing the option to Move by Geographical Coordinates means that the Bus will be moved on the oneline diagram to the latitude/longitude coordinates specified with the bus data object (or the substation object if the bus does not have valid latitude/longitude coordinates.</p></li>
<li><p><strong>Bus Information Dialog</strong> : will open the Bus Information Dialog for either <a href="07-object-properties-run-mode-and-general-part1.md#bus-information-dialog">Run Mode</a> or <a href="06-object-properties-edit-mode-part1.md#bus-options">Edit Mode</a>.</p></li>
<li><p><strong>Show Data View</strong> : Will open the <a href="08-view-case-data-tools.md#data-view">Data View</a> dialog for the bus</p></li>
<li><p><strong>Open Model Explorer</strong> : Will open the <a href="04-model-explorer-and-case-information-part1.md#model-explorer">Model Explorer</a> and navigate to this Bus.</p></li>
<li><p><strong>Bus View</strong> : Will open the Bus View oneline and navigate to this bus.</p></li>
<li><p><strong>Bus or Substation Spatial View Oneline</strong>: Will open the <a href="08-view-case-data-tools.md#spatial-view-oneline">Bus Spatial View Oneline</a></p></li>
<li><p><strong>Quick Power Flow List</strong> : opens the <a href="05-case-information-displays-by-object-part1.md#quick-power-flow-list" class="MCXref xref">Quick Power Flow List</a></p></li>
<li><p><strong>Create Contingency</strong> : will create a new <a href="23-contingency-analysis-running-and-results.md#contingency-analysis-dialog">Power Flow Contingency</a> that opens the selected bus</p></li>
<li><p><strong>Add New Fields Around</strong> : will bring up a dialog for <a href="#inserting-and-placing-multiple-display-fields" class="MCXref xref">Inserting and Placing Multiple Display Fields</a></p></li>
<li><p><strong>Format</strong> : has a subment to bring up the <a href="14-editing-onelines.md#format-selection-dialog">Format Dialog</a>, Apply <a href="#setting-default-drawing-options">Default Draw Values</a>, Copy/Paste Format as described on the <a href="02-simulator-ribbon.md#formatting-ribbon-group">Formatting Group on the Draw Ribbon Tab</a> and Snap Bus to Grid as described in <a href="14-editing-onelines.md#gridhighlight-unlinked-objects" class="MCXref xref">Grid/Highlight Unlinked Objects</a></p></li>
<li><p><strong>Create Case Info Display</strong>: Will open up a Case Information Display with only this bus in it</p></li>
<li><p><strong>Open External Maps</strong>: For a diagram configured with a Map Projection on the <a href="16-oneline-gis-tools.md#geographycoordinates">Oneline Display Options Geography Tab</a>, this will automatically open either Google Maps, Bing Maps, or the Open Infrastucture Maps (openinframap.org) to the geographic location.</p></li>
</ul>
<p> </p>
<p> </p>
<p> </p></td>
<td><img src="images/Oneline_LocalMenu_Bus.png" alt="Oneline LocalMenu Bus" /></td>
</tr>
</tbody>
</table>

---

<a id="bus-fields-on-onelines"></a>

## Bus Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Bus_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Fields_on_Onelines.htm)*

Bus field objects are used primarily to indicate various quantities associated with bus devices. Furthermore, some bus field types, which are distinguished by an integrated spin button, may be used to easily change bus device properties.

Run Mode

Right clicking on a bus field gives you the option to open the [Bus Field Dialog](06-object-properties-edit-mode-part1.md#bus-field-information) or the [Bus Information Dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog).

Left-clicking on either the Bus Number or the Bus Name field in Run Mode will open the [Bus View Display](08-view-case-data-tools.md#bus-view-display) oneline.

Edit Mode

Simulator offers two options for adding bus fields to a oneline in Edit Mode. If you need to enter only a single field, the easier approach may be to choose **Field \> Bus Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and then select the bus to which you want to add the field. This invokes the [Bus Field Dialog.](06-object-properties-edit-mode-part1.md#bus-field-information) Enter the bus number associated with the device (the default is the closest bus to the field), the total number of digits to show, and the number of digits to the right of the decimal point. An optional Field Prefix can be used. Choosing to Include Suffix will include relevant units for the type of field selected. The field can be Anchored to the bus that it represents and the field can be rotated by a specified Rotation Angle in Degree. Finally, select the type of field to show.

The second approach for adding new bus fields entails right-clicking the bus and selecting **Add New Fields Around Bus** from the resulting local menu. See [Inserting and Placing Multiple Display Fields](#inserting-and-placing-multiple-display-fields) for more details.

To modify the parameters of an existing bus field, position the cursor anywhere on the object and right-click. This brings up the [Bus Field Dialog.](06-object-properties-edit-mode-part1.md#bus-field-information) Choose any of the format buttons on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change various display attributes of the field, including its font and background color.

---

<a id="old-voltage-gauges"></a>

## Old Voltage Gauges

*Source: [`Content/MainDocumentation_HTML/Old_Voltage_Gauges.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Old_Voltage_Gauges.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Voltage gauges provide a way to visualize the voltage of a bus relative to its high- and low-voltage alarm limits. A gauge looks very much like a thermometer. As the temperature changes, the height of the mercury in the thermometer moves up and down. One reads the temperature measured by the thermometer by noting the marking that matches the top of the mercury. Voltage gauges in Simulator work the same way. A voltage gauge has three markings on its side, each of which identifies a key per-unit voltage level. Specifically, these three markings locate the minimum, maximum, and target per-unit voltages. Often, the target voltage level is the nominal voltage, but this is not a requirement. Inside the gauge is a filled region. The default color of the filled region is blue, but this can be changed. When you create the voltage gauge, you associate it with a bus, and you specify its fill color and its minimum, maximum, and target voltage levels. Once the gauge has been placed on a display, it will reveal changes in its associated bus’s voltage by varying the height of its filled region. This tool was introduced to provide an alternative to voltage contours to show the variation of voltage across a region. [Contouring](17-oneline-view-printing-and-contouring.md#contouring) can reveal the variation of only a single quantity at a time. For example, it is impossible to contour bus voltage magnitude and bus voltage phase angle simultaneously. Voltage gauges are helpful because they allow you to show the voltage profile superimposed on a contour of some other quantity.

To add a voltage gauge to a display, switch to Edit Mode and select ** Pies / Gauges \> Old** **Gauges \> Bus** from the **Individual Insert Ribbon Group** on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. The cursor will become a crosshair. Click on the oneline diagram where you would like the new voltage gauge to appear. The [Voltage Gauge Options Dialog](#old-voltage-gauge-options-dialog) will appear. Use this dialog to define the minimum, maximum and target voltages for the voltage gauge, as well as its fill color and whether it should be anchored to its associated bus. After you click the "OK" button, the Voltage Gauge Options Dialog will close, and the new voltage gauge will appear.

Once a gauge has been placed on the oneline, the height of its filled region will change as the voltage of its associated bus changes. To modify any of the characteristics of the gauge, such as its key voltage levels, fill color, and anchor setting, simply right-click on the bus voltage gauge to open the Voltage Gauge Options Dialog again.

---

<a id="old-voltage-gauge-options-dialog"></a>

## Old Voltage Gauge Options Dialog

*Source: [`Content/MainDocumentation_HTML/Old_Voltage_Gauge_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Old_Voltage_Gauge_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Voltage Gauge Options Dialog is used to define and configure a [bus voltage gauge](#old-voltage-gauges). A bus voltage gauge is associated with a particular bus and reveals the bus’s voltage relative to specified minimum, maximum, and target per-unit voltage levels. The height of the colored column in the voltage gauge indicates the bus’s voltage relative to these markings.

The dialog has the following controls:

Number, Name, and Find

Use the **Number** and **Name** dropdown boxes to identify the bus to which you want the gauge to correspond. Select a bus number from the Number dropdown box to identify the bus by number, and a bus name from the Name dropdown box to identify a bus by name. It may be more convenient to press the **Find** to open the [Find Dialog](04-model-explorer-and-case-information-part3.md#find-dialog-basics), which allows you to specify a bus by either name or number using wildcards. When you first open the Bus Voltage Gauge Dialog, the bus name and number will correspond to the bus object that was closest to the point where you clicked.

Minimum, Target, and Maximum

Use these three spin edit boxes in the **Voltage levels** group box to specify the minimum, maximum, and target per-unit voltage levels. These settings determine where on the gauge its three markings will be drawn.

The Minimum and Maximum value will be taken from the Limit Monitoring settings for the current bus, unless you uncheck the option "*Set Limits According to Current Limit Monitoring Settings*".

Fill color

The Fill color box reveals the color that will be used to paint the filled region of the gauge. Click on the Fill color box to open a Color Dialog, which you may then use to specify a different color.

Anchored

A bus voltage gauge is said to be [anchored](#anchored-objects) if, when you move its associated bus object, it moves with it. Check the Anchored check box to ensure that the gauge will move with its associated bus. Otherwise, when you move its associated bus object, the gauge will stay in its current position.

OK, Help, and Cancel

Click OK to finalize your settings. This will create a new voltage gauge object if you are trying to create one from scratch, or it will modify the appearance and settings of an existing one if you have chosen to modify one that has already been defined. Click Cancel to dispose of your changes. Click the Help button to reveal this help text.

---

<a id="substation-display-objects"></a>

## Substation Display Objects

*Source: [`Content/MainDocumentation_HTML/Substation_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Substations in Simulator define a group of buses that are closely connected. Each bus can belong to either one substation or no substation (called unassigned). By default in Simulator, all buses are not assigned to a substation. This is done because all traditional text file power flow formats do not include information regarding a bus' substation.

Substations are represented on the oneline as a rectangle with the name of the substation inside it. Other information about the substation is also displayed on the rectangle:

  - The upper left corner displays a generator symbol if generation exists in the substation.
  - The upper right corner displays a load symbol if load exists in the substation.
  - The lower right corner displays a shunt symbol if shunts exist in the substation.
  - The lower left corner displays the number of buses inside the substation.
  - The lower middle displays the maximum voltage level in the substation.

You can also customize the size, colors, and font name and style of a substation object. Note however that the font size of the substation object is automatically changed by Simulator as you change the size of the rectangle.

Right-clicking on the substation will display its local menu. The local menu offers you the chance to view the corresponding [Substation Information Dialog](06-object-properties-edit-mode-part1.md#substation-information) and the [Substation View Display](08-view-case-data-tools.md#substation-view-display).

---

<a id="substation-fields-on-onelines"></a>

## Substation Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Substation_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To display certain information about a substation, such as MW Load or MVAR losses, insert a substation field. This can be done in Edit Mode by selecting **Fields \>** **Substation** **Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This will bring up the [Substation Field Options](06-object-properties-edit-mode-part1.md#substation-field-options) dialog. From here you can choose which substation to describe, how many digits in the field, and how many digits to the right of the decimal. There are also 8 different field options to choose from. If a field value is not defined, question marks will be shown.

---

<a id="generator-display-objects"></a>

## Generator Display Objects

*Source: [`Content/MainDocumentation_HTML/Generator_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Display_Objects.htm)*

Generators are represented on the oneline as circles with a rotor symbol inside. The default rotor symbol is a "dog bone," but other symbols can be selected. Multiple generators at a bus are allowed, with each being distinguished by a unique character identifier.

Each generator symbol (except that corresponding to the slack) can be equipped with a circuit breaker (see that can be used to change the status of the generator. You may toggle the generator status by clicking on the circuit breaker while in Run Mode.

[Generator fields](#generator-fields-on-onelines) are often placed close to the generator on the oneline to indicate the generator's MW/Mvar output or other information associated with the generator.

Run Mode

When [animation](15-using-onelines-tools-and-options.md#oneline-animation) is active, the default flow of the arrows emerging from the generator is proportional to its MW output. You can customize the appearance of this flow using the Animated Flows Tab of the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right clicking on the generator brings up the generator submenu. This menu is used to display a variety of information about the generator, including

  - [Generator Information Dialog](07-object-properties-run-mode-and-general-part1.md#generator-information)
  - [Input-output curve](05-case-information-displays-by-object-part1.md#generator-economic-curves)
  - [Fuel cost curve](05-case-information-displays-by-object-part1.md#generator-economic-curves)
  - [Incremental cost curve](05-case-information-displays-by-object-part1.md#generator-economic-curves)
  - [Heat-rate curve](05-case-information-displays-by-object-part1.md#generator-economic-curves)
  - [Reactive capability curve](06-object-properties-edit-mode-part1.md#generator-reactive-power-capability-curve)

Edit Mode

To add a new generator to the case, select **Network \> Generator** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then, place the cursor on the bus where you would like to attach the generator, and click with the left mouse button. This calls up the [Generator Dialog.](06-object-properties-edit-mode-part1.md#generator-information) The bus number is automatically determined from the bus to which you attached the generator. The ID field contains a an alphanumeric ID used to distinguish multiple generators at a bus. The default is '1'.

Enter the size, the thickness of the lines (in pixels) used to display the device, orientation, rotor symbol, and other parameters for the generator. Each generator can optionally contain a circuit breaker for connecting or disconnecting the device in Simulator. Use options found with the [Display Object Options](15-using-onelines-tools-and-options.md#display-object-options) on the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) dialog to specify if a circuit breaker should be shown. Select OK to add the generator. If you do not want to add the generator to the case, select Cancel.

To modify the parameters for an existing generator, position the cursor on the generator and right-click. This again brings up the Generator Dialog. You can then change any parameter (be careful in renumbering an existing generator). Use the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group commands to change the color, line thickness, and other display parameters.

---

<a id="generator-fields-on-onelines"></a>

## Generator Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Generator_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generator field objects are used primarily to indicate various quantities associated with generation devices. Furthermore, some generator field types, which are distinguished by an integrated spin button, may be used to change generation device properties.

Run Mode

For generator fields with an associated spin button, clicking on the up/down arrows will change the value of the associated field.

Right clicking on a generator field gives you the option to open the [Generator Field Dialog](06-object-properties-edit-mode-part1.md#generator-field-information) or the [Generator Information Dialog](07-object-properties-run-mode-and-general-part1.md#generator-information).

Edit Mode

Simulator offers two options for adding generator fields to a oneline in Edit Mode. If you need to enter only a single field, the easier approach may be to choose **Field \> Generator Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and click near generator for which you want to add the field. This invokes the [Generator Field Dialog.](06-object-properties-edit-mode-part1.md#generator-field-information) Enter the bus number associated with the device (the default is the bus associated to the closest generator to the field), the ID field, the total number of digits to show, and the number of digits to the right of the decimal point. Next, select the type of field to show. For generator actual MW and Setpoint MW types and load MW and Mvar fields, specify a nonzero value in the *Delta per Mouse Click* to design a bus field with an integrated spin control. The Gen AGC Status field is used to display the automatic generation control status of the generator. The user can toggle this status in Simulator by clicking on the field. Likewise, the Gen AVR Status field is used to display the automatic voltage regulation status of the generator. Again, the user can toggle this status by clicking on the field.

The second approach for adding new generator fields entails right-clicking the bus and selecting *Add New Fields Around Generator* from the resulting local menu. Please see [Inserting and Placing Multiple Display Fields](#inserting-and-placing-multiple-display-fields) for more details.

To modify the parameters of an existing generator field, position the cursor anywhere on the object and right-click. This brings up the [Generator Field Dialog.](06-object-properties-edit-mode-part1.md#generator-field-information) Choose **![Levels Layers Icon](images/Levels_Layers_Icon.jpg) **, or **![Display zoom icon](images/Display_zoom_icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group to change various display attributes of the field, including its font and background color.

---

<a id="load-display-objects"></a>

## Load Display Objects

*Source: [`Content/MainDocumentation_HTML/Load_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator models aggregate load at each system bus. Multiple loads at a bus are allowed. Each load object on the oneline comes equipped with a circuit breaker. The status of the load corresponds to the status of its circuit breaker. A circuit breaker is closed if it appears as a filled red square, and it is open if it appears as a green square outline. In Run Mode, you may toggle the status of the load by clicking on its associated circuit breaker.

[Load fields](#load-fields-on-onelines) are often placed close to the loads on the oneline to indicate their MW/Mvar value.

Run Mode

When [animation](15-using-onelines-tools-and-options.md#oneline-animation) is active, the flow of the arrows into the load is proportional to its current MW load. You can customize the appearance of this flow using the Animated Flows Tab of the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right clicking on a load (bus) field gives you the option to open the [Load Field Dialog](06-object-properties-edit-mode-part1.md#load-field-information) or the [Load Dialog.](07-object-properties-run-mode-and-general-part1.md#load-information)

Edit Mode

To add a new load to the case, select **Network \> Load** from [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. **** Then, select the bus to which you want to attach the load with the left mouse button. This calls up the [Load Dialog](06-object-properties-edit-mode-part1.md#load-options). The bus number is automatically determined from the bus to which you attached the load. The ID field contains a two-character ID used to distinguish multiple loads at a bus. The default ID is 1.

Enter the size, the thickness of the lines \[in pixels\] used to display the device, the orientation, and the base MW and Mvar load values for the device. Usually, only the Constant Power fields are specified as nonzero. The Constant Current and Constant Impedance fields are used to specify loads that vary with voltage. Constant current loads vary proportionally with bus voltage, while constant impedance loads vary with the square of the voltage. Specify the constant current and constant impedance values assuming one per-unit voltage.

Select OK to add the load. If you do not want to add the load to the case, select Cancel. ****

To modify the parameters for an existing load, position the cursor on the load and right-click. Select *Load Information Dialog* from the local menu to invoke the [Load Dialog](06-object-properties-edit-mode-part1.md#load-options). You can then change any parameter as desired. You can select **![Display zoom icon](images/Display_zoom_icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the drawing parameters of the load.

---

<a id="load-fields-on-onelines"></a>

## Load Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Load_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Load field objects are used primarily to indicate various quantities associated with load devices. Furthermore, some load field types, which are distinguished by an integrated spin button, may be used to change load device properties.

Run Mode

For load fields with an associated spin button, clicking on the up/down arrows will change the value of the associated field.

Right clicking on a load field gives you the option to open the [Load Field Dialog](06-object-properties-edit-mode-part1.md#load-field-information) or the [Load Information Dialog](07-object-properties-run-mode-and-general-part1.md#load-information).

Edit Mode

Simulator offers two options for adding load fields to a oneline in Edit Mode. If you need to enter only a single field, the easier approach may be to choose **Field \> Load Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and then select the load to which you want to add the field. This invokes the [Load Field Dialog.](06-object-properties-edit-mode-part1.md#load-field-information) Enter the bus number associated with the device (the default is the bus associated to the closest load to the field), the ID field, the total number of digits to show, and the number of digits to the right of the decimal point. Next, select the type of field to show.

The second approach for adding new generator fields entails right-clicking the bus and selecting *Add New Fields Around Load* from the resulting local menu. Please see [Inserting and Placing Multiple Display Fields](#inserting-and-placing-multiple-display-fields) for more details.

To modify the parameters of an existing load field, position the cursor anywhere on the object and right-click. This brings up the [Load Field Dialog.](06-object-properties-edit-mode-part1.md#load-field-information) Choose ![Font Btn Icon](images/Font_Btn_Icon.jpg), or **![Display zoom icon](images/Display_zoom_icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change various display attributes of the field, including its font and background color.
