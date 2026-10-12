---
title: "Editing Oneline Diagrams"
part: "Oneline Diagrams"
chapter_file: "14-editing-onelines.md"
topics: 19
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Editing Oneline Diagrams

Selecting, moving, formatting and editing existing oneline objects.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (19)**

- [Select by Criteria Dialog](#select-by-criteria-dialog)
- [Local Menu for Selected Objects](#local-menu-for-selected-objects)
- [Grid/Highlight Unlinked Objects](#gridhighlight-unlinked-objects)
- [Using the Oneline Alignment Grid](#using-the-oneline-alignment-grid)
- [Setting Background Color](#setting-background-color)
- [Zoom, Pan and Find](#zoom-pan-and-find)
- [Default Drawing Values](#default-drawing-values)
- [Format Selection Dialog](#format-selection-dialog)
- [Paste Format Dialog](#paste-format-dialog)
- [Font Properties](#font-properties)
- [Line/Fill Properties](#linefill-properties)
- [Levels/Layers Options](#levelslayers-options)
- [Screen Layers](#screen-layers)
- [Screen Layer Options](#screen-layer-options)
- [Format Field Properties](#format-field-properties)
- [Other Display Object Properties](#other-display-object-properties)
- [Align Group Objects](#align-group-objects)
- [Refreshing Anchors](#refreshing-anchors)
- [Undo Command](#undo-command)

---

<a id="select-by-criteria-dialog"></a>

## Select by Criteria Dialog

*Source: [`Content/MainDocumentation_HTML/Select_by_Criteria_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Select_by_Criteria_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**![Ribbon Draw Select By Criteria 32x32](images/Ribbon_Draw_Select_By_Criteria_32x32.gif)**To open the Select By Criteria Dialog go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Select By Criteria** from the [Select](02-simulator-ribbon.md#select-ribbon-group) ribbon group.

The Select By Criteria Dialog provides a way of selecting objects that meet a specific set of criteria. The criteria may include Area Numbers, Zone Numbers, Voltage Levels, Zoom Levels, and Object Type.

Use the dialog's controls to specify the selection criteria. Use the **Area** and **Zone** fields to select the areas and zones in which you want to select display objects. [Ranges of area and zone numbers](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) can be entered in the usual way, or you can check the **All Areas** or **All Zones** boxes to select all areas and all zones. You can also use the **Area** and **Zone** tab pages to check or uncheck areas or zones in which you want to select display objects.

Specify the max and min voltage levels for selected objects using the boxes that are provided, keeping in mind that all voltages are in kV.

Specify the [layers](#screen-layers) for selected objects in the **Layers** tab. If not all layers are selected, the **Layers Range** option will be selected. If the **All Layers** option is clicked, then all the layers will be selected.

Next, select the type of object in which you are interested from the supplied list. To select items from this list, check the box next to the type of field(s) you desire. Display object types that are followed by a right-arrow, such as *Area Fields*, are expandable, meaning that they have several associated subtypes. If you checked a field type that has subtypes, you can highlight the type in the list to see the available subtype list. You can then more specifically select subtypes that you wish to include. By default, all subtypes of a general object type are selected. You also have the option for the list to display all fields available for a particular object type, or to display only the most commonly selected fields.

You can also choose to associate an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) with a particular type of object in the list for selecting only objects of that type that meet the filter. To do so, right-click in the Filter column next to the object type for which the filter applies, or click on **Add/Modify Filter…** Some objects cannot be associated with an advanced filter, and the option will be disabled when that is the case for an object selected in the dialog.

Checking the option **Group By Object Type** will consolidate all the items by categories. All subtypes will automatically be included as a consequence. The filters are still available.

If the box **Only Show Objects in Display or Already Selected** is checked, only the items or categories (depending on whether the Group By Object Type option is checked) of objects existing or selected in the respective oneline diagram will be shown in the supplied list.

The buttons **Check All** and **Uncheck All** are useful to select/unselect all the items/groups in the list. The button **Check Only Text Fields** is available only when the Group by Object Type is unchecked, and when clicked on all the items that have text associated to them are selected, and the rest of the items are unselected. Clicking on the **Reset To Defaults** button will remove all the current selections and reset them to the default settings.

If you wish to select objects that *do not* have the chosen criteria, then check **Select All Except What Meets the Above Criteria**.

If you wish to only select objects that are currently visible on the diagram (due to layering, etc.), check the box labeled **Select only currently visible objects** to apply the criteria settings only to objects on the diagram that are currently visible.

If the Select by Criteria Dialog is open and some display objects have already been selected, an advanced selection option becomes available. If the box labeled **Use as a filter on presently selected objects** is checked, the criteria chosen in the Select by Criteria Dialog *will only* affect the previously selected objects. In other words, only the objects that were previously selected AND that match the chosen criteria will remain selected when the OK button is pressed. For example, you could use all the options available on the [Select](02-simulator-ribbon.md#select-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to select a group of objects on the oneline. Then using the Select by Criteria Dialog, choose the Bus criteria and check **Use as a filter on presently selected objects** to select only the buses from the rectangular selected group of objects.

Once you have selected the criteria and pressed *OK*, all objects that satisfy ALL the criteria will be chosen. If the Select All Except What Meets the Above Criteria is unchecked, then the selected objects will lie within the specified areas AND zones, the specified voltage level, and the specified zoom levels, and will be of one of the drawing types specified.

You can save your settings for your Select by Criteria session with the case by clicking **Save As** to save with a new name or **Save** to save with the current name. This allows you to re-open the Select by Criteria dialog, and quickly recover settings you may have previously used. Use the **Rename** to rename an already saved set, or **Delete** to remove a previously saved set of criteria.

If you have saved different criteria sets, you can export them all to an [Auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) by choosing **Save to AUX file**. The **Load All from AUX file** will load an entire auxiliary file, regardless of whether it contains Select by Criteria settings or not.

If you wish to clear all settings you have modified on the dialog, click the **Reset to Defaults** button.

Using this dialog in conjunction with the [Format Selection Dialog](#format-selection-dialog), can be a very fast and easy way to customize your displays.

NOTE: When choosing to select all tie lines, all objects associated with the tie line will also be selected. This includes all line fields for the line as well as the two buses that are the endpoints of the line.

---

<a id="local-menu-for-selected-objects"></a>

## Local Menu for Selected Objects

*Source: [`Content/MainDocumentation_HTML/Oneline_Local_Menu_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Local_Menu_Objects.htm)*

When several objects are all selected on a oneline diagram and the right-click mouse button is clicked on top of that selection, a local menu appears with options to operate on the selected objects. This menu has the

following options, most of which are self-explanatory. Some of the options are described in more depth below.

  - **Format Selection** : [Brings up the Format Dialog](#format-selection-dialog)

  - **Add New Fields around Selection..**.: [Brings up a dialog to insert multiple fields](11-building-onelines-network-objects.md#inserting-and-placing-multiple-display-fields)

  - **Apply Default Draw Values..**.: Brings up the [Default drawing options dialog](11-building-onelines-network-objects.md#setting-default-drawing-options)

  - **Copy Format / Paste Format** : These two options will copy the format or paste whatever format has been copied before - similar to what is done on the [Formatting Group on the Draw Ribbon Tab](02-simulator-ribbon.md#formatting-ribbon-group).

  - **Set Selected Field to YES**: Will modify the Selected Field for all data objects linked to the Display object selected as described in [Set Selected Field](18-general-tools.md#set-selected-field)

  - **Snap Selection To Grid...** : Will snap all selected to objects to align to the grid as described in [Grid/Highlight Unlinked Objects](#gridhighlight-unlinked-objects)

  - **Align Group Objects...** : Opens the [Align Dialog](#align-group-objects).

  - **Open External Maps** : For a diagram configured with a Map Projection on the [Oneline Display Options Geography Tab](16-oneline-gis-tools.md#geographycoordinates), this will automatically open either Google Maps, Bing Maps, or the Open Infrastucture Maps (openinframap.org) to the geographic location.

  - **Auto Insert Line Flow Objects on Selection...** : Click to auto insert [Line Flow Arrows on Onelines](12-building-onelines-branches-and-devices.md#line-flow-arrows-on-onelines)

  - **Auto Insert Line Flow Pie Chart Objects on Selection...** : auto insert [Line Flow Pie Charts on Onelines](12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines)

  - **Auto Insert Circuit Breaker Objects on Selection...** : auto insert [Circuit Breakers on Onelines](12-building-onelines-branches-and-devices.md#circuit-breakers-on-onelines)

  - **Create Injection Group From Selection...** : [Creating Injection Groups](07-object-properties-run-mode-and-general-part2.md#creating-injection-groups)

  - **Create Interface From Selection...** : Create [interface definition](07-object-properties-run-mode-and-general-part2.md#interface-information) from the selected Branch objects

  - **Merge Selected Buses...** : [Merging Buses](19-edit-mode-tools.md#merging-buses)

  - **Move Buses and Substations to record's Latitude/Longitude** : Any Bus or Substation Display objects that are selected will be moved to match the latitude/longitude coordinate stored with the data object Bus and Substation latitude/longitude information.

  - **Convert lines to background lines...** : will convert any selected Transmission LIne, Transformer, or Interface Display objects into a simple background line instead.

  - **Create a Case Information from Selection** : For all display objects selected, a dialog will open with tabs for each different type of data object to which the display objects are linked. Each tab will then have a case information display with those objects.

---

<a id="gridhighlight-unlinked-objects"></a>

## Grid/Highlight Unlinked Objects

*Source: [`Content/MainDocumentation_HTML/Grid_Highlight_Unlilnked_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Grid_Highlight_Unlilnked_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Grid/Highlight Unlinked Objects tab is only available in Edit mode. It controls the appearance of a grid in the oneline. A grid is not visible by default, but can be setup from the Grid/Highlight Unlinked Objects page of the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) dialog. Additional options are available from this dialog for disabling anchors and highlighting unlinked objects on oneline diagrams.

Snap Objects to Grid

If checked, new objects placed on the oneline will be aligned with the grid; the grid does not need to be visible on the oneline to align objects to it.

X Grid Spacing, Y Grid Spacing

These determine the horizontal and vertical spacing of the grid.

Display Grid Lines on Oneline

If checked, the grid lines will appear on the oneline

Horizontal Show Every, Vertical Show Every

These numbers determine the density of the visible gridlines; for fewer lines enter higher numbers.

Gridline Color

Click in the rectangle to choose the color of the gridlines. The default is grey.

Anchor Options

A check box is available for temporarily disabling anchors on a oneline diagram. This option will disable the anchor properties of all objects on the oneline diagram.

Do not prompt regarding relinking objects after dragging

Check this check-box to avoid being prompted whether to relink a graphical object after this has been dragged.

Highlighting of Unlinked Objects

Highlight Unlinked Objects with Color

Checking this box allows for any objects on all open oneline diagrams that are currently not linked to any data in the case to be highlighted using the highlight color. To change the highlight color used, left-click in the color box to choose a different color.

Minimum Highlighted Object Pixel Size

The minimum size, in pixels, of the highlight image. This is to prevent the highlight from being unnoticeable when the zoom level is very low.

Extra Width for Highlighted Lines (pixels)

Sets an extra width parameter, in pixels, for highlighting line objects. This will make line object highlights appear wider than other highlighted objects.

Display Unlinked Elements in Run Mode

This option allows the highlighting of unlinked elements when you switch to run mode. By default the highlighting of unlinked elements is restricted to edit mode, to avoid confusion in run mode, particularly when drawing [contours](17-oneline-view-printing-and-contouring.md#contouring).

---

<a id="using-the-oneline-alignment-grid"></a>

## Using the Oneline Alignment Grid

*Source: [`Content/MainDocumentation_HTML/Using_the_Oneline_Alignment_Grid.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Using_the_Oneline_Alignment_Grid.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The oneline alignment grid allows for buses and other objects to be easily aligned when placed onto a oneline diagram. The alignment grid for a oneline diagram can be configured in the Oneline Display Options dialog under the [Grid/Highlight Unlinked](#gridhighlight-unlinked-objects) page. You can open this display by selecting **Oneline Display Options** from the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.

When the alignment grid is enabled most objects will snap to the grid while being moved on the oneline. Depending on whether snap to grid is enabled or disabled, objects can individually be made to do the *opposite* of the snap to grid setting by holding down the Alt key while dragging the object.

---

<a id="setting-background-color"></a>

## Setting Background Color

*Source: [`Content/MainDocumentation_HTML/Setting_Background_Color.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Setting_Background_Color.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Background Color Dialog changes the background color for the display. To view this dialog, select **Oneline Display** **Options** from the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, or right-click in the background of the oneline and select **Oneline Display Options** from the local menu. Switch to the [Display Options](15-using-onelines-tools-and-options.md#display-options) tab, click **Change Background Color**, or click on the colored rectangle to bring up the Color Dialog, which you can then use to select the new background color. Click OK to register the new color. The Oneline Display Options dialog will provide a preview of the color you selected. To define this color as the default background color to use in all new onelines you create, click the **Set as Default Background Color**. Finally, click OK to save your color selection.

---

<a id="zoom-pan-and-find"></a>

## Zoom, Pan and Find

*Source: [`Content/MainDocumentation_HTML/Zoom_Pan_and_Find.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zoom_Pan_and_Find.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Zoom, Pan, and Find Options Dialog is used to specify a desired zoom level and screen location or to locate a particular bus or area/zone on the oneline. The dialog can be opened by right-clicking on the background of the diagram and choosing **Pan/Zoom Control** from the oneline popup menu, or by clicking on the **Find** button in the [Zoom](02-simulator-ribbon.md#zoom-ribbon-group) ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab. The dialog has the following fields:

Find Objects on Oneline

The Find Object on Oneline section of the dialog is used to pan to any desired [bus object](11-building-onelines-network-objects.md#bus-display-objects) , [area/zone object](11-building-onelines-network-objects.md#area-display-objects) , [branch object](12-building-onelines-branches-and-devices.md#transmission-line-display-objects), [interface object](12-building-onelines-branches-and-devices.md#interface-display-objects), or [substation object](11-building-onelines-network-objects.md#substation-display-objects) on the oneline. The dialog makes use of the advanced find functionality of Simulator to locate a device.

Only Include Objects Visible at Current Zoom Level

If checked (the default), then the **Object ID** combo box only lists those objects that are visible at the current zoom level.

Object Type

Select the type of object to find: *Buses, Areas or Zones, Interfaces, Substations* and *Lines/Transformers.*

Sort By

Specify whether you are entering the object by its number or by its name by choosing either **Sort by Name** or **Sort by Number**. This option also determines how the entries in the list of objects are sorted (either by number or by name).

Object ID

Enter the object’s number or name (depending on the sort type chosen) or select the object from the list.

Allow Auto Updating on Selection

Check this box to automatically pan to the specified object. The object will be located at the center of the oneline diagram.

Pan to Object on Oneline

Click this button to pan to the specified object if the Auto Updating box is not checked. The object will be located at the center of the oneline diagram.

Auto-Zoom when Panning

Check this box to automatically change the zoom when panning to the specified object.

Zoom / Pan

The Oneline Zoom / Pan tab on this dialog is used to allow the user to specify either a new zoom level and/or screen center and to define these as the new display default settings. The zoom level and screen center can also be changed from the keyboard. Please see [Oneline Zooming and Panning](17-oneline-view-printing-and-contouring.md#oneline-zooming-and-panning) for details.

Zoom Level

Enter the desired percentage zoom level (nominal is 100%).

Horizontal, Vertical

Enter a desired location for the center of the screen. The nominal screen center is 50 horizontal and 50 vertical.

Pan/Zoom to New Location

Changes the screen center and zoom level to the values specified in the above fields.

Restore Default Values

Resets the zoom level and screen center to the default values.

---

<a id="default-drawing-values"></a>

## Default Drawing Values

*Source: [`Content/MainDocumentation_HTML/Default_Drawing_Values.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Default_Drawing_Values.htm)*

The [Default Drawing Options Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options) allows you to see and change the various default values used to create new objects. To show this dialog select **Default Drawing Values**from the **[Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

---

<a id="format-selection-dialog"></a>

## Format Selection Dialog

*Source: [`Content/MainDocumentation_HTML/Format_Multiple_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Format_Multiple_Objects.htm)*

The Format Multiple Objects dialog features five tabs of controls for modifying the display attributes of selected object(s). Even though the dialog is very useful for formatting multiple objects, there is no requirement than more than one object be selected to use the formatting dialog. To open the Format Multiple Options dialog you must first use some of the options available on the [Select](02-simulator-ribbon.md#select-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to select a group of objects. Next, right-click on any of the selected objects and select **Format Selection** from the local menu. You may also bring up the Format Multiple Objects dialog by going to the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

The options on the following tabs will be updated to reflect the types of objects selected. All options will not be available for all objects. If multiple objects of different types are selected, options will only be available if they are relevant for any of the types of objects selected.

Line/Fill

The [Line/Fill tab](#linefill-properties) is used to change the line size, color, and style and the fill color with which the selected objects are drawn.

Levels/Layers

The [Levels/Layers tab](#levelslayers-options) is used to change the stack level of an object, the layer the object is contained in, and optional settings for when an object should resize.

Display/Size

The [Display/Size tab](#other-display-object-properties) controls the size and orientation of the selected objects.

Font

The [Font tab](#font-properties) is used to change the font used in text/font objects.

Field

The [Field tab](#format-field-properties) is used to change selected fields on the diagram to a different field designation. If all of the selected fields are for the same type of object and field, you can select a different field to be represented by the selected objects from the **Field** selection. You can also set the options for including a suffix, the total digits in the field for numeric values, and the number of digits to the right of the decimal.

---

<a id="paste-format-dialog"></a>

## Paste Format Dialog

*Source: [`Content/MainDocumentation_HTML/Format_Paste_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Format_Paste_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Paste Format Dialog appears when you use the Paste Format button on the **[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. The dialog looks as follows

![Paste Format Dialog](images/Paste_Format_Dialog.gif)

On this dialog check the attributes you would like to paste to the selected objects. Note that attributes which are disabled in the Paste Format Dialog represent one of two things

  - The attribute was not relevant to the objects whose format was copied
  - The attribute was not the same for the objects whose format was copied

---

<a id="font-properties"></a>

## Font Properties

*Source: [`Content/MainDocumentation_HTML/Font_Properties.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Font_Properties.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Font Tab allows you to define the font for the selected objects by choosing Font type, size, color and effects. The page also allows you to control the default display font using the **Make Default** button.

By clicking on **Make Default,** the current font name, size, and effects will be set as the default font for the display. This has the same effect as opening the [Default Drawing Values](#default-drawing-values) and setting the default font.

---

<a id="linefill-properties"></a>

## Line/Fill Properties

*Source: [`Content/MainDocumentation_HTML/Line_Fill_Properties.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Fill_Properties.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line/Fill tab of the [Format Multiple Objects](#format-selection-dialog) dialog is used to customize the line size/color and the fill color of selected objects. You can view this tab by selecting **![Line Fill Icon](images/Line_Fill_Icon.jpg)** from the **[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab after object(s) have been selected on the oneline. This tab’s controls can be used to change the appearance of most, but not all, screen objects. Only options that are relevant for the types of objects selected will be enabled. The Line/Fill tab has the following fields/commands:

Line Thickness

Thickness of the line in pixels. Line can mean either an actual transmission line or background line object, the lines used to draw objects like loads and switched shunts, or the border line that surrounds objects like generators and buses.

Dashed

Allows setting a line to appear as a dashed line on the diagram. There are three types of line dashing to choose from in the drop down menu for this option.

Line Color

This field shows the current line color. To change the line’s color, click on the box displaying the current line color, or click the **Change** button next to the Line Color box. This displays the Color dialog. Select the desired color and select OK to change the color, or click Cancel if you do not wish to change the color.

Line Color 2

The Line Color 2 field applies only to transformer and generator objects. Check the **Use Color 2** field to implement use of the color and specify the color through the color box. The color can be changed in the same manner as described above for **Line Color**.

Transformers can be represented by different colors on each side of the transformer coils. This is commonly used to color match each side of the transformer with the color used to represent the voltage level of the transmission system on each particular side of the transformer. However, you can customize the colors for selected transformers by modifying them here. The Line Color 2 field ALWAYS applies to the high voltage side of the transformer.

The rotor image selected for generator objects can be filled with Line Color 2.

Use Background Fill

Click on this box to toggle whether or not to fill the background for the selected objects with the selected background fill color. Text objects such as [Text](13-building-onelines-graphics-and-insertion.md#general-text-on-onelines), [Bus Fields](11-building-onelines-network-objects.md#bus-fields-on-onelines), [Generator Fields](11-building-onelines-network-objects.md#generator-fields-on-onelines), [Load Fields](11-building-onelines-network-objects.md#load-fields-on-onelines), [Switched Shunt Fields](12-building-onelines-branches-and-devices.md#switched-shunt-fields-on-onelines), [Line Fields](12-building-onelines-branches-and-devices.md#transmission-line-fields-on-onelines), [Transformer Fields,](12-building-onelines-branches-and-devices.md#transformer-fields-on-onelines) [Area Fields](11-building-onelines-network-objects.md#area-fields-on-onelines), background objects such as [Background Lines](13-building-onelines-graphics-and-insertion.md#background-lines-on-onelines) and [Background Rectangles](13-building-onelines-graphics-and-insertion.md#background-rectangles-on-onelines), [Background Triangles](52-additional-linked-topics-part1.md#background-rectangles-on-onelines) and [generator objects](11-building-onelines-network-objects.md#generator-display-objects) can be filled.

Fill Color

This field shows the current fill color. To change the fill color, click on the box that displays the current fill color, or click the **Change** button next to this box. This displays the Color dialog. Click on the desired color and the select OK to change the color, or click Cancel if you do not wish to change the color.

---

<a id="levelslayers-options"></a>

## Levels/Layers Options

*Source: [`Content/MainDocumentation_HTML/Levels_Layers_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Levels_Layers_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Levels/Layers Tab is used to customize the stack level or layer an object is contained in. To set layers for objects, select the objects on the oneline diagram (edit mode only) and then choose ****![Levels Layers Icon](images/Levels_Layers_Icon.jpg). The Levels/Layers Options page of the [Format Multiple Objects](#format-selection-dialog) dialog will be displayed, with the following settings available.

Stack Level

An object’s stack level dictates what objects it will appear above, and which objects it will appear below on a oneline diagram. For example, circuit breaker and pie chart objects have a default stack level of Top. Therefore anything with a stack level of Middle, Background or Base will appear underneath pie charts and circuit breakers on the oneline diagram. Objects that are within the same stack level and are drawn in the same location will result in the last object drawn being the visible object on the diagram. You can toggle which elements within the same stack level at the same location is visible using the Send to Back and Bring to Front buttons in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

Layers

Layers are different than stack levels in that layers are designed to allow the user to filter the elements visible on a diagram (in run mode). Initially all diagram objects are in the same layer, called Default. This default layer cannot be modified or deleted. However, you can introduce additional layers using either the **Add New…** or **Define…** buttons. Clicking on **Add New…** will open a dialog to name the new layer, and will automatically add the new layer to the case and change the Layer name in the drop down list to the new layer. Clicking on **Define…** will open the [Screen Layers](#screen-layers) list display, which will allow you to manage the full list of layers defined for the diagram. Once layers have been defined, you can choose which layer the selected objects belong to by choosing the Layer name from the drop-down list by clicking on the down arrow to the right of the layer name.

Settings for resizing when zooming

You can modify the maximum and minimum zoom levels at which the selected text fields will no longer resize. Thus when zooming in or out on the diagram, text fields will resize according to the zoom level until the minimum or maximum zoom level are reached. At that point, text fields will no longer resize, but will stay fixed at their current size as you continue to zoom.

Maintain Fixed Screen Location (do not pan)

This option is available for text fields. When checked for selected text fields, these text fields will no longer pan when you pan the rest of the diagram. This allows you to place text that will always be visible, regardless of what part of the diagram you are observing. You can still move the individual text field itself in edit mode.

Maintain Fixed Screen Size (do not resize on zoom)

This option is available for text fields. When checked for selected text fields, these text fields will no longer resize when the zoom level of the diagram is changed. This allows you to place text that will always be visible at a constant size, regardless of what zoom level you are currently observing on the oneline diagram. You can still select the text fields themselves in edit mode and change their font size.

---

<a id="screen-layers"></a>

## Screen Layers

*Source: [`Content/MainDocumentation_HTML/Screen_Layers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Screen_Layers.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Screen Layers display can be invoked from either the [Levels/Layers](#levelslayers-options) button in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group in Edit Mode, or by right-clicking on the oneline diagram background and choosing Edit Screen Layers.

Screen layers provide a method to filter objects on a oneline diagram based on either zoom level or to which layer the objects are assigned. Initially each object is in a common layer called Default, which cannot be modified or deleted. You can create new layers using the Screen Layers display.

Since the Screen Layers display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), it shares the[characteristics and controls](https://www.powerworld.com/WebHelpvoid\(0\);) of other case information displays. You can access many case information display features by right-clicking on the display to invoke the local popup menu. Most importantly, this menu contains the options to Insert and Delete screen layers.

To delete a screen layer, right-click on that layer in the display and select Delete from the popup menu. The one exception is the Default layer, which cannot be deleted.

To insert a new screen layer, right-click on a record in the display and choose Insert from the popup menu. This will open the [Screen Layer Options](#screen-layer-options) dialog for defining the options of the new layer you are inserting.

You can also define a new layer by going to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **Screen Layer \> Define Screen Layer.**

To Hide all layers from the Oneline go to **Screen Layer \> Hide All.**

To Show all layers in the Oneline go to **Screen Layer \> Show All.**

---

<a id="screen-layer-options"></a>

## Screen Layer Options

*Source: [`Content/MainDocumentation_HTML/Screen_Layer_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Screen_Layer_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Screen Layer Options are used to define options for new layers, or modify options for existing layers. Devices can be added to a layer by choosing the layer name from the drop-down list on the [Levels/Layers Tab](#levelslayers-options) of the [Format Multiple Objects](#format-selection-dialog) dialog.

Name

Layers can have any name desired to describe the layer. The default naming convention is "Layer \#".

Show Layer

If this box is checked, any objects on the diagram which are contained in this layer *may* be visible. This depends on the settings for low and high zoom level, described below. If the box is unchecked, however, then any objects contained in this layer will be hidden. Only objects that are visible will be used when calculating contours. Unlike [Custom Display Detail](15-using-onelines-tools-and-options.md#display-options), layers can be applied in both edit mode and run mode.

Selectable in Edit Mode

By unchecking this box the user prevents the objects contained in this layer of being with the mouse during Edit Mode. This is behavior is particularly desirable for elements (such as borders which are pretty much already fixed) when editing oneline diagrams.

Use Conditional Display by Zoom Level

Objects can be displayed or hidden based on the Screen Layer to which they are assigned and the current zoom level of the oneline diagram. Checking this box, and setting the Low Zoom Level and High Zoom Level fields, dictates at what zoom range the objects contained in the zoom level will be visible. If the zoom level is outside the range defined, any objects belonging to the screen layer will be hidden. This also applies to both edit mode and run mode.

Memo

This tab allows the user to enter text in order to describe this layer.

---

<a id="format-field-properties"></a>

## Format Field Properties

*Source: [`Content/MainDocumentation_HTML/Format_Field_Properties.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Format_Field_Properties.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Field tab of the [Format Multiple Objects](#format-selection-dialog) dialog can be used to modify the format of the selected fields, or to change a set of selected fields from one field representation to another. Use the [Select by Criteria](#select-by-criteria-dialog) dialog to select fields of a particular type, right-click on any of the selected fields and choose **Format Selection** from the popup menu.

Note that this option also applies to objects which display information related to specific object fields, such as [Line](12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines) and [Interface](12-building-onelines-branches-and-devices.md#interface-pie-charts-on-onelines) Pie Charts.

Object Type

This field will be filled in automatically based on the type of object the selected field(s) apply to. You cannot change this field, which means that you can only change the selected field(s) to another field for the same type of object.

Field

The field type of the selected field(s). To change the selected fields to a new field type, click on the drop-down arrow of the combo box, or click on the **Find…** button, and select a new field from the list of fields for the Object Type.

Include Suffix

Checking this option will add the unit suffix to the selected fields.

Total Digits in Field

Modify the number of digits to display in the field. This number includes the decimal and the numbers to the right of the decimal.

Digits to Right of Decimal

Modify the number of the total digits that should appear to the right of the decimal.

Include Field Arrow

Checking this option will display an arrow next to the field for at-a-glance visualization. The [orientation](#other-display-object-properties) of the arrow must be specified to indicate the positive direction of the value that the field is representing. As an example for line MW flow fields, positive flow can be considered to be out of the bus at the end of the line to which the field is assigned. The orientation should be set to match this. The arrow will automatically point in the opposite direction if the flow on the line is actually into the bus.

---

<a id="other-display-object-properties"></a>

## Other Display Object Properties

*Source: [`Content/MainDocumentation_HTML/Display_Size_Properties.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Display_Size_Properties.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Use the Display/Size tab of the [Format Multiple Objects](#format-selection-dialog) dialog to change the display size, orientation, anchor property of the selected object(s).

Size

This field will change the characteristic display size of the selected object(s). The characteristic size is normally the vertical size or height of display objects. In objects with different orientation choices, the size is the most distinctive dimension of the object (e.g. in buses with right or left orientations, the size is the horizontal dimension of the bus bar, but in buses with up or down orientations, the size is the vertical dimension of the bus bar).

Width

This field will change the characteristic display width of the selected object(s). Similarly to the size, the width represents the horizontal dimension or width of display objects. In objects with different orientation choices, the width is the least distinctive dimension of the object (e.g. in buses with right or left orientations, the width is the vertical dimension of the bus bar, but in buses with up or down orientations, the width is the horizontal dimension of the bus bar).

Anchored

To toggle whether or not the selected object(s) are [anchored](11-building-onelines-network-objects.md#anchored-objects) , check or uncheck this option

Immobile

To force the selected object(s) to stay in the same position, check this option.

Orientation

This group will modify the orientation setting of the selected object(s). The possible settings will change depending on the type of object selected. Some object types do not have an orientation.

Shape

Use this group to modify the shape of the selected display objects. Possible shape settings will change depending on the type of objects selected. If objects of different types are selected and these types do not have a common set of shapes possible, the shape option will be blank and the shape cannot be changed.

For Substation objects, the Use Substation Layout Settings specifies that the shape selected in the [Substation Display Options](15-using-onelines-tools-and-options.md#substation-display-options) will be used.

When generator objects are selected, the shape selection determines the shape of the rotor inside the generator. The selections include images that represent possible generator fuel types including: coal, hydro, natural gas, nuclear, oil, solar, and wind. The other images include a dog bone, sine wave, or no rotor image. If selecting a rotor shape that can be filled, **Line Color 2** on the [Line/Fill tab](#linefill-properties) determines the fill color for the inside of the shape.

Number of Selected Objects

This field shows the number of objects that are currently selected on the oneline.

---

<a id="align-group-objects"></a>

## Align Group Objects

*Source: [`Content/MainDocumentation_HTML/Align_Group_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Align_Group_Objects.htm)*

The Align Group feature allows for selecting multiple objects on a oneline diagram and aligning them in a specified manner. There are a couple of ways to perform the alignment.

First, select the objects on the diagram that you wish to align. Once you have selected all objects, you can 1) right click on a selected object and choose **Align Group Objects** from the local popup menu or 2) use the **Alignment** menu found in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

The **Align Group Objects** option from the local menu will open the Align Dialog, which allows for specifying the type of alignment desired. Alignment can be performed horizontally, vertically, or both. In addition to alignment of the top, bottom, left and right edges of the selected objects, you can also choose to have the objects snap to the [drawing grid](#gridhighlight-unlinked-objects) in the horizontal and/or vertical directions as well.

These alignment actions can also be selected directly from the **Alignment** menu found on the Formatting ribbon group on the Draw ribbon tab.

---

<a id="refreshing-anchors"></a>

## Refreshing Anchors

*Source: [`Content/MainDocumentation_HTML/Refresh_Anchors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Refresh_Anchors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Refresh Anchors** option of the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab allows you to update or reset the anchoring of objects on a oneline diagram to their respective anchor. It can be advantageous to use the Refresh Anchors option when opening onelines that were created by another case, copying and pasting data between onelines, or renumbering objects on the oneline. This ensures the anchoring of objects to the appropriate anchor on the oneline diagram.

---

<a id="undo-command"></a>

## Undo Command

*Source: [`Content/MainDocumentation_HTML/Undo_Command.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Undo_Command.htm)*

The Undo command is used in the edit mode to undo the last change made on the oneline diagram. The Undo command will only undo graphical changes, and will not undo any data changes in the power system model. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for information on the display/model relationships.
