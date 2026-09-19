---
title: "Building Onelines — Graphics and Insertion"
part: "Oneline Diagrams"
chapter_file: "13-building-onelines-graphics-and-insertion.md"
topics: 36
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Building Onelines — Graphics and Insertion

Background objects and text, pie charts and gauges, palettes and automatic object insertion.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (36)**

- [Background Lines on Onelines](#background-lines-on-onelines)
- [Background Lines Dialog](#background-lines-dialog)
- [Background Rectangles on Onelines](#background-rectangles-on-onelines)
- [Background Arc On Onelines](#background-arc-on-onelines)
- [Background Ellipses on Onelines](#background-ellipses-on-onelines)
- [Background Pictures on Onelines](#background-pictures-on-onelines)
- [Converting Background Lines](#converting-background-lines)
- [Converting Background Ellipses](#converting-background-ellipses)
- [Converting Background Rectangles](#converting-background-rectangles)
- [General Text on Onelines](#general-text-on-onelines)
- [Memo Text](#memo-text)
- [Oneline Text Fields](#oneline-text-fields)
- [Case Information Memo Field](#case-information-memo-field)
- [Generic Model Fields](#generic-model-fields)
- [Supplemental Data Fields on Onelines](#supplemental-data-fields-on-onelines)
- [Pie Charts/Gauges: Lines](#pie-chartsgauges-lines)
- [Pie Charts/Gauges: Interfaces](#pie-chartsgauges-interfaces)
- [Pie Charts/Gauges: Pie Chart/Gauge Styles](#pie-chartsgauges-pie-chartgauge-styles)
- [Pie Charts/Gauges: General Options](#pie-chartsgauges-general-options)
- [Pie Chart / Gauge Dialogs](#pie-chart-gauge-dialogs)
- [Pie Chart / Gauge Style Dialog](#pie-chart-gauge-style-dialog)
- [Pie Chart / Gauge Style Dialog - Standard Parameters Tab](#pie-chart-gauge-style-dialog---standard-parameters-tab)
- [Pie Chart / Gauge Style Dialog - Open Parameters Tab](#pie-chart-gauge-style-dialog---open-parameters-tab)
- [Pie Chart / Gauge Style Dialog - Pie Chart Parameters Tab](#pie-chart-gauge-style-dialog---pie-chart-parameters-tab)
- [Pie Chart / Gauge Style Dialog - Gauge Parameters Tab](#pie-chart-gauge-style-dialog---gauge-parameters-tab)
- [Pie Chart / Gauge Example](#pie-chart-gauge-example)
- [Palette Overview](#palette-overview)
- [Using the Insert Palettes](#using-the-insert-palettes)
- [Automatically Inserting Buses](#automatically-inserting-buses)
- [Automatically Inserting Transmission Lines](#automatically-inserting-transmission-lines)
- [Automatically Inserting Generators](#automatically-inserting-generators)
- [Automatically Inserting Loads](#automatically-inserting-loads)
- [Automatically Inserting Switched Shunts](#automatically-inserting-switched-shunts)
- [Automatically Inserting Substations](#automatically-inserting-substations)
- [Automatically Inserting Borders](#automatically-inserting-borders)
- [Custom Left-Click Behavior](#custom-left-click-behavior)

---

<a id="background-lines-on-onelines"></a>

## Background Lines on Onelines

*Source: [`Content/MainDocumentation_HTML/Background_Lines_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Background_Lines_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of an oneline diagram can display added lines, polylines, and filled polygons among other items.

Edit Mode

To add a new background line, first go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Background \> Background Line** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Then to draw a series of straight line segments on the background, follow these steps:

  - Position the mouse cursor where you want the series to begin and click and release the left mouse button.
  - Move the mouse to the desired termination point of the first line segment. A straight segment will follow your mouse movements. Click and release the left mouse button to complete the line segment and prepare for drawing the next line segment, or double-click if this line segment is the last segment you wish to draw.

To draw a freehand shape rather than a series of straight line segments, click and hold the left mouse button where you would like the freehand shape to begin and drag the mouse to trace the shape you desire (while holding the left mouse button down). Release the left mouse button to complete the section of the freehand shape you have been drawing. At this point, you can add either another freehand section or a straight line segment. When you have finished drawing in the background, double click the mouse button.

Note that background display objects composed of straight line segments display significantly faster than lines drawn freehand. Lines draw freehand (holding down mouse button) leave a vertex point at every point on the screen, where a line composed of straight-line segments (left-clicking only where you want a vertex point) takes considerably less effort for the PC to draw.

To change the color, line thickness, and fill color associated with the line, make use of the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group.

To change the shape of the line, first left-click on the line to select it. This causes handles to appear at each vertex. You can then move any vertex by holding the left mouse button down and dragging the vertex to a new location. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the line where you would like to add a vertex. Note that freehand lines are nothing more than a continuous series of vertices.

---

<a id="background-lines-dialog"></a>

## Background Lines Dialog

*Source: [`Content/MainDocumentation_HTML/Background_Lines_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Background_Lines_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line Options Dialog is available while in edit mode by right-clicking on a background line and selecting **Open Dialog…** This dialog contains options for formatting the selected background line. Many of the options listed in this dialog can also be updated on the [Format](14-editing-onelines.md#format-selection-dialog) dialog.

**Line Thickness**

This field gives the thickness of the line in pixels.

**Line Color**

This field shows the current line color. To change the line’s color, click on the box displaying the current color or click the **Change** button next to the line color. This will display the Color Dialog. Select the desired color and select OK to change the color.

**Use Background Fill**

When this option is checked, the selected Fill Color will be used to fill the background of the line.

**Fill Color**

This field shows the current fill color. To change the fill color, click on the box that displays the current fill color or click the **Change** button. This will display the Color Dialog. Select the desired color and select OK to change the color.

**Immobile**

When this option is checked, the background line will be forced to stay in the same position and cannot be moved by dragging it with the mouse.

**List of Vertices**

This grid lists the x,y coordinates for the vertices of the line in the order in which the line is drawn. The coordinates will be displayed as longitude,latitude if the [option to show coordinates in longitiude,latitude](16-oneline-gis-tools.md#geographycoordinates) is selected on the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) dialog and a valid map projection is in use. The values for the coordinates can be changed by entering new values in the appropriate position in the grid.

**Shift X/Y Values**

These options provide a means of updating all of the x and/or y values. The **X Shift Value** is the offset by which all of the x values will be shifted. The **Y Shift Value** is the offset by which all of the y values will be shifted. The resulting values will be the original values plus the value entered for the shift. The **Shift All Values** button must be selected for the values entered in the shift fields to be applied to the x,y values. After this button is selected, the coordinates shown in the grid will be updated with the new values.

**Scale X/Y Values**

These options provide a means of updating all of the x and/or y values. The **X Scale Value** is the value by which all of the x values will be scaled. The **Y Scale Value** is the values by which all of the y values will be scaled. The resulting values will be the original values multiplied by the value entered for the scale. The **Scale All Values** button must be selected for the values entered in the scale fields to be applied to the x,y values. After this button is selected, the coordinates shown in the grid will be updated with the new values.

**OK, Save and Update Display, and Cancel**

**OK** saves the changes and closes the dialog. **Save and Update Display** saves the changes and updates the display without closing the dialog. **Cancel** closes the dialog without saving any changes.

---

<a id="background-rectangles-on-onelines"></a>

## Background Rectangles on Onelines

*Source: [`Content/MainDocumentation_HTML/background_rectangles_on_onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/background_rectangles_on_onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of a oneline diagram can display rectangles among other items. ****

Edit Mode

To add a new rectangle, first go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Insert \> Background Rectangle** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Position the cursor where you would like to place the upper left-hand corner of the rectangle and click with the left mouse button. A rectangle having the default size is inserted. Drag the rectangle's resizing handles to resize/reshape the rectangle.

To resize or reshape an existing rectangle, click on it to select it. The resizing handles will appear, which you can then drag to reshape or resize the rectangle.

To change the color, line thickness or fill color of the rectangle, first select the rectangle by clicking on it on the diagram, and then use the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, or right-click on it and select **Format Background Rectangle** from the local menu.

---

<a id="background-arc-on-onelines"></a>

## Background Arc On Onelines

*Source: [`Content/MainDocumentation_HTML/Background_Arc_On_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Background_Arc_On_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of a oneline diagram can display arcs among other items.

Edit Mode

To add a new ellipse, first go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Background \> Background Arc** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Then position the cursor where you would like to place the upper left-hand corner of the arc and click with the left mouse button. An ellipse having the default size and shape is inserted. Drag the arc's resizing handles to resize/reshape it.

To resize or reshape an existing arc, click on it to select it. The resizing handles will appear, which you can then drag to resize the arc. The reshape handles will appear inside the resize handles, which you can then drag to reshape the arc.

Right-click on the arc and choose **Format Background Ellipse**, or select the arc and use the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group found on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the color, line thickness and fill color of the ellipse.

---

<a id="background-ellipses-on-onelines"></a>

## Background Ellipses on Onelines

*Source: [`Content/MainDocumentation_HTML/background_ellipses_on_onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/background_ellipses_on_onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of a oneline diagram can display ellipses among other items.

Edit Mode

To add a new ellipse, first go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Background \> Background Ellipse** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Then position the cursor where you would like to place the upper left-hand corner of the ellipse and click with the left mouse button. An ellipse having the default size and shape is inserted. Drag the ellipse's resizing handles to resize/reshape it.

To resize or reshape an existing ellipse, click on it to select it. The resizing handles will appear, which you can then drag to reshape or resize the ellipse.

Right-click on the ellipse and choose **Format Background Ellipse**, or select the ellipse and use the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group found on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the color, line thickness and fill color of the ellipse.

---

<a id="background-pictures-on-onelines"></a>

## Background Pictures on Onelines

*Source: [`Content/MainDocumentation_HTML/background_pictures_on_onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/background_pictures_on_onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The background of an oneline diagram can display a variety of objects, including lines, filled polygons, and even pictures. The latter will be discussed in this section.

Edit Mode

Simulator can insert bitmaps, jpegs, enhanced and standard metafiles, and icons from files into the oneline diagram. These pictures may either serve as a background or appear above other objects on the oneline.

To add a picture object to the oneline diagram, go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and select **Background \> Picture** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group. Then, click the oneline diagram at the point where you would like the top left corner of the graphic to be placed. The Open Picture Dialog will open, asking you to select the graphic file that you want to insert. When you select a file from the dialog, the dialog displays a preview image so that you can be sure that you are selecting the right file. When you have identified the file to insert, click *OK*. The image will then appear on the oneline. It may be resized by dragging its resizing handles.

By default, pictures are inserted at the middle stack level. Thus, they hide most other oneline display objects. To change the stack level of the picture, click it to select it, and then select the Levels/Layers button ****![Levels Layers Icon](images/Levels_Layers_Icon.jpg) found in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group of the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. From the *Levels/Layers Tab*, select the stack level of your choice. The *Base* stack level places the picture below all other oneline display objects, while the *Top* stack level will cause the picture to obscure all other display objects.

To resize or reshape an existing picture object, click on it to select it and then drag its resizing handles.

---

<a id="converting-background-lines"></a>

## Converting Background Lines

*Source: [`Content/MainDocumentation_HTML/Converting_Background_Lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Converting_Background_Lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Background lines can be converted to other objects by splitting, merging, or converting to power system objects. This can be done while in Edit mode. To convert a background line, right-click on a selected background line on the oneline display and the local menu will be displayed with the conversion options. Most options are available if only a single background line has been selected and no other objects are selected. The following options are available for converting a background line:

Split Background Line

A background line can be split at a vertex or anywhere along the line. Click the point on the line where the split should be made and then right-click and select the **Split Background Line…** option from the local menu. Two background lines will result. This option is available only if exactly one background line has been selected and no other objects have been selected.

Merge Background Lines

This option is only available if exactly two background lines have been selected. The two selected background lines will be merged at the two closest ends and a single background line will result.

Convert to ac Transmission Line

After selecting this option, the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) will be displayed. The dialog options can be set the same as they would be set when inserting an ac transmission line from the Insert menu. This option is available only if exactly one background line has been selected and no other objects have been selected.

Convert to Multi-Section Line

After selecting this option, the [Multi Section Line dialog](12-building-onelines-branches-and-devices.md#multi-section-transmission-line-display-objects) will be displayed. The dialog options can be set the same as they would be set when inserting a multi-section line from the Insert menu. This option is available only if exactly one background line has been selected and no other objects have been selected.

Convert to Bus

After selecting this option, the [Bus Information dialog](06-object-properties-edit-mode-part1.md#bus-options) will be displayed. The dialog options can be set the same as they would be set when inserting a bus from the Insert menu. This option is available only if exactly one background line has been selected and no other objects have been selected.

Convert to Substation

After selecting this option, the [Substation Information Dialog](06-object-properties-edit-mode-part1.md#substation-information) will be displayed. The dialog options can be set the same as they would be set when inserting a substation from the Insert menu. This option is available only if exactly one background line has been selected and no other objects have been selected.

---

<a id="converting-background-ellipses"></a>

## Converting Background Ellipses

*Source: [`Content/MainDocumentation_HTML/Converting_Background_Ellipses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Converting_Background_Ellipses.htm)*

Background ellipses can be converted to power system objects. To convert a background ellipse, right-click on a selected background ellipse on the oneline display and the local menu will be displayed with the conversion options. The following options are available for converting a background ellipse:

Convert to Bus

After selecting this option, the [Bus Information Dialog](06-object-properties-edit-mode-part1.md#bus-options) will be displayed. The dialog options can be set the same as they would be set when inserting a bus from the Insert menu. This option is available only if exactly one background ellipse has been selected and no other objects have been selected.

Convert to Substation

After selecting this option, the [Substation Information Dialog](06-object-properties-edit-mode-part1.md#substation-information) will be display. The dialog options can be set the same as they would be set when inserting a substation from the Insert menu. This option is available only if exactly one background ellipse has been selected and no other objects have been selected.

---

<a id="converting-background-rectangles"></a>

## Converting Background Rectangles

*Source: [`Content/MainDocumentation_HTML/Converting_Background_Rectangles.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Converting_Background_Rectangles.htm)*

Background rectangles can be converted to power system objects. To convert a background rectangle, right-click on a selected background line on the oneline display and the local menu will be displayed with the conversion options. The following options are available for converting a background rectangle:

Convert to Bus

After selecting this option, the [Bus Information Dialog](06-object-properties-edit-mode-part1.md#bus-options) will be displayed. The dialog options can be set the same as they would be set when inserting a bus from the Insert menu. This option is available only if exactly one background rectangle has been selected and no other objects have been selected.

Convert to Substation

After selecting this option, the [Substation Information Dialog](06-object-properties-edit-mode-part1.md#substation-information) will be display. The dialog options can be set the same as they would be set when inserting a substation from the Insert menu. This option is available only if exactly one background rectangle has been selected and no other objects have been selected.

---

<a id="general-text-on-onelines"></a>

## General Text on Onelines

*Source: [`Content/MainDocumentation_HTML/Text_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Text_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Text display objects are used to show single lines of text on the oneline.

Edit Mode

To add descriptive text to the oneline, select **Background \> Text** in the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, and click the oneline where you would like the text to appear. The Text Options Dialog will open, asking you to enter the desired text string, and the angle at which the text is to appear on the oneline diagram.

To modify an existing text object, position the cursor anywhere on the text and right-click. The New Text Options Dialog will appear, allowing you to edit the text. Use the font option ![Font Btn Icon](images/Font_Btn_Icon.jpg) of the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group to control the font and background color of the text object.

---

<a id="memo-text"></a>

## Memo Text

*Source: [`Content/MainDocumentation_HTML/Memo_Text.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Memo_Text.htm)*

Memo Text display objects are used to show several lines of text on the oneline within an enclosing box.

Edit Mode

To add a Memo Text object to the oneline, select **Background \> Memo Text** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the **[**Draw**](02-simulator-ribbon.md#draw-tab-overview)** ribbon tab. Then click and drag to create a rectangle on the oneline; this rectangle will contain the lines of text you enter.

To modify the contents of a Memo Text object, position the cursor anywhere on the object and right-click and choose the option to **Edit Memo Text**. To change the formatting of a Memo Text object, select the object with a left-click, then select **![Font Btn Icon](images/Font_Btn_Icon.jpg) **from the **[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab; this will bring up the [Font Properties](14-editing-onelines.md#font-properties) tab of the [Format Multiple Objects](14-editing-onelines.md#format-selection-dialog) dialog box.

Enabled Load Memo Text as AUX file or AXD File (For use in Run Mode)

Special features were added in December 16, 2024 patch of Version 23 that allow you to specify that the contents of the Memo Text can then be loaded as an AUX or AXD file. To configure this option you must right-click on the Memo in Edit Mode and then check either the box **Enable Load Memo Text as AUX file** or **Enable Load Memo Text as AXD file**. When either of these are checked there is then another option available to **Immediately Load Memo Text on Run Mode Left-Click** which will make the left-click behavior in Run Mode be to open the contents of the Memo Text as though it is an AUX file or an AXD file. If the **Immediately Load Memo ...** option is not checked then the right and left-click behavior in Run Mode will both open up a drop-down menu giving you the option to **Load Memo Text as AUX file**. These special flags with the Memo are stored inside the field **TextObjectFullText** when looking at the Background\\Text Boxes in the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display).

There are also options in the Edit Menu drop down to **Load Memo Text as AUX file** (or AXD file) as well as an option to **Edit the ScriptCommand** that provides access to editing the [special custom left-click action available with many display objects](#custom-left-click-behavior).

![Memo Text LoadAsAUXAXD](images/Memo_Text_LoadAsAUXAXD.png)

---

<a id="oneline-text-fields"></a>

## Oneline Text Fields

*Source: [`Content/MainDocumentation_HTML/Oneline_Text_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Text_Fields.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Oneline Fields are fields that can be placed on an oneline diagram that display values specific to the current display of the diagram, such as x and y coordinate of the mouse cursor, animation rate, zoom percentage, and x and y coordinate of the center of the diagram at the center of the screen. These fields can be inserted on a oneline diagram by choosing **Field \> Oneline Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the **[Draw](02-simulator-ribbon.md#draw-tab-overview)** ribbon tab.

---

<a id="case-information-memo-field"></a>

## Case Information Memo Field

*Source: [`Content/MainDocumentation_HTML/Case_Information_Memo_Field.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Memo_Field.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Case Information Memo Fields are text fields that can be placed on an oneline diagram that display information including the Case Description, Local Path, build date of the Simulator executable, Add Ons installed with Simulator, Simulator Software Version, System Data and Time, System Slack buses and their output, and Transient Stability run time. These fields can be inserted on a oneline diagram by choosing **Field \> Case Information Memo Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the **[Draw](02-simulator-ribbon.md#draw-tab-overview)** ribbon tab.

---

<a id="generic-model-fields"></a>

## Generic Model Fields

*Source: [`Content/MainDocumentation_HTML/Generic_Model_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generic_Model_Fields.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generic Model Fields are fields that can be placed on an oneline diagram that display any value for any object in the case on the diagram. These fields can be inserted on an oneline diagram by choosing **Field \> Generic Model Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

This type of field comes in handy when you want to place a variety of fields on the diagram, without inserting specific object-type fields. All fields of data are available in one location for placement on a diagram.

---

<a id="supplemental-data-fields-on-onelines"></a>

## Supplemental Data Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Supplemental_Data_Fields.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Supplemental_Data_Fields.htm)*

Supplemental Data Field objects represent information about [Supplemental Data](15-using-onelines-tools-and-options.md#supplemental-data) records. The information that can be represented in these fields is the same in either Edit or Run Mode.

Supplemental Data Fields can be added to a oneline while in Edit Mode from **Draw \> Field \> Supplemental Data Field**. After selecting this option, move the cursor to the location on the oneline where the new field should be placed and left-click. The Supplemental Data Field Options dialog will open.

The **Supplemental Data Field Options** dialog can be used to modify the properties of individual supplemental data fields on the diagram. This dialog contains the following fields:

Classification

Select the Supplemental Classification from the drop-down list of available classifications.

Name

Select the Name of the Supplemental Data record from the drop-down list of available names. This list is populated with the appropriate names based on the selected Classification.

Total Digits in Field

Total number of digits to show in the field.

Field Prefix

A prefix that can be specified and displayed with the selected value.

Digits to Right of Decimal

Number of digits to show to the right of the decimal point.

Field Value

The current value of the field being displayed.

Rotation Angle in Degrees

The angle at which the text will be displayed on the diagram.

Type of Field

Select a field from the drop-down list of available fields or click **Find Field** to search through the list of available fields.

Select **OK** to close the dialog and save the changes, or click **Cancel** to close the dialog without saving the changes.

---

<a id="pie-chartsgauges-lines"></a>

## Pie Charts/Gauges: Lines

*Source: [`Content/MainDocumentation_HTML/Pie_Charts_Gauges_Lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Charts_Gauges_Lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The options listed below are found on the [Oneline Display Options dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) on the [Pie Charts/Gauges page](15-using-onelines-tools-and-options.md#pie-chartgauge-options) on the Lines tab.

Pie Chart / Gauge Style

The Pie Chart Style box determines whether the [line flow pie charts](12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines) show the percentage loading of the line based upon the MVA flow, the MW flow, the MVR flow, the line amp/transformer MVA flow, the maximum percentage loading under contingency, or the PTDF value. The Line Gauge Style box has the same setting options as the line flow pie charts.

Always Use Limiting Flow

Typically, the flow at opposite ends of a transmission line is slightly different due to losses across the line. If this option is checked, the pie chart will correspond to limiting MVA value of the line, independent of which end of the line that value occurs. Otherwise, the pie chart will always show the MVA value at the from bus for the line.

Display Gauge Values in Percent

Check this option to display values in the line gauges as percent of loading instead of actual flow values.

Color, Size and Percentage

This section of the options dialog allows you to customize the appearance of the line flow pie charts on the diagram. The default options for the line flow pie charts are set on the MVA tab, and are always in force for at least the MVA pie chart / gauge style. However, you can choose different settings for the other styles by selecting the corresponding tab under the Color, Size and Percentage section. Each of the other five styles can be set to use the same settings as defined for MVA by checking the given option on the page. If this option is unchecked for a particular style, then any pie chart on the diagram of that style type will use the specifically defined appearance options for that style type.

The following parameters are all available on each of the six style tab pages:

Show Value Percent

When a branch's loading exceeds the value specified in the **Show Value Percent** field, the percentage loading is shown as text within the pie chart. The default is 80%.

Normal Size Scalar, Normal Color

The standard, pre-warning fill color and scaling factor for pie charts.

Use Discrete Map

When this option is checked, the color of the pie chart/gauge will be the colors listed in the **Warning/Limit Scalars and Colors** when the loading on the line has reached the specified percentage and has not yet met the next higher percentage. If this option is not checked, the color of the pie chart/gauge will be a blend of the colors for the loading range in which the line loading falls, with the color providing an indication of where it falls in the loading range.

Warning / Limit Scalars and Colors

The table in this section allows you to choose different settings for the pie chart size and color, based on the percentage value represented by the pie chart or gauge. Thus you can set up visual clues as to when the flow on lines exceeds specified warning or limit levels. You can add and remove points from this table by right-clicking in the table and using the Insert and Delete options from the popup menu.

To modify the Percent and size Scalar for a record in the table, simply click on the value in the cell and type in a new value. To change the color associated with the percent value, double click in the Color cell to open the Color Chooser dialog.

Make normal color the same as the line to which the pie chart or gauge is anchored (if any)

If checked, this option will cause the pie charts to assume the same normal colors as the transmission lines to which they are anchored. This may be useful if the transmission lines are colored according to their nominal voltage level.

Only Apply Warning/Limit Colors and Resizing to Monitored Elements

If this option is checked, then only those pie charts that correspond to branches selected using the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) will change appearance to reflect warning and limit loading levels. If this option is not checked, then all pie charts will obey the options prescribed in this dialog.

Some additional options are available for pie chart appearance in situations where the line itself is out of service. Clicking on the tab labeled **Open Parameters** will display these options. You can choose to have special formatting for open devices by checking the available option, and then defining the appearance options for the pie charts on the open lines. The available options include scaling the size, width of the border, border color, pie chart background color, and drawing an "X" symbol through the pie chart.

---

<a id="pie-chartsgauges-interfaces"></a>

## Pie Charts/Gauges: Interfaces

*Source: [`Content/MainDocumentation_HTML/Pie_Charts_Gauges_Interfaces.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Charts_Gauges_Interfaces.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The options listed below are found on the [Oneline Display Options dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) on the [Pie Charts/Gauges page](15-using-onelines-tools-and-options.md#pie-chartgauge-options) on the Interfaces tab.

Pie Chart Style

The Pie Chart Style box determines whether the interface pie charts show the percentage loading of the line based upon the MW flow, the maximum percentage loading under contingency, or the PTDF value.

Color, Size and Percentage

This section of the options dialog allows you to customize the appearance of the interface flow pie charts on the diagram. The default options for the interface flow pie charts are set on the Lines MVA tab. However, you can choose different settings for the interface styles by selecting the corresponding tab under the Color, Size and Percentage section. Each of the styles can be set to use the same settings as defined for Lines MVA by checking the given option on the page. If this option is unchecked for a particular style, then any interface pie chart on the diagram of that style type will use the specifically defined appearance options for that style type.

The following parameters are all available on each of the three style tab pages:

Show Value Percent

When an interface's loading exceeds the value specified in the **Show Value Percent** field, the percentage loading is shown as text within the pie chart. The default is 80%.

Normal Size Scalar, Normal Color

The standard, pre-warning fill color and scaling factor for pie charts.

Use Discrete Map

When this option is checked, the color of the pie chart will be the colors listed in the **Warning/Limit Scalars and Colors** when the loading on the interface has reached the specified percentage and has not yet met the next higher percentage. If this option is not checked, the color of the pie chart will be a blend of the colors for the loading range in which the interface loading falls, with the color providing an indication of where it falls in the loading range.

Warning / Limit Scalars and Colors

The table in this section allows you to choose different settings for the pie chart size and color, based on the percentage value represented by the pie chart or gauge. Thus you can set up visual clues as to when the flow on interfaces exceeds specified warning or limit levels. You can add and remove points from this table by right-clicking in the table and using the Insert and Delete options from the popup menu.

To modify the Percent and size Scalar for a record in the table, simply click on the value in the cell and type in a new value. To change the color associated with the percent value, double click in the Color cell to open the Color Chooser dialog.

Make normal color the same as the line to which the pie chart or gauge is anchored (if any)

If checked, this option will cause the pie charts to assume the same normal colors as the interface to which they are anchored. This may be useful if the interfaces are colored differently on the diagram.

Only Apply Warning/Limit Colors and Resizing to Monitored Elements

If this option is checked, then only those pie charts that correspond to interfaces selected using the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) will change appearance to reflect warning and limit loading levels. If this option is not checked, then all interface pie charts will obey the options prescribed in this dialog.

---

<a id="pie-chartsgauges-pie-chartgauge-styles"></a>

## Pie Charts/Gauges: Pie Chart/Gauge Styles

*Source: [`Content/MainDocumentation_HTML/Pie_Charts_Gauges_Pie_Chart_Gauge_Styles.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Charts_Gauges_Pie_Chart_Gauge_Styles.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This section shows the Pie Chart/Gauge styles in a case information display. The user can edit several of the fields directly. Otherwise, by right-clicking on any part of the case information display and selecting on **Show Dialog** in the popup menu, the [Pie Chart/Gauge Style dialog](#pie-chart-gauge-style-dialog), where all the values can be modified.

---

<a id="pie-chartsgauges-general-options"></a>

## Pie Charts/Gauges: General Options

*Source: [`Content/MainDocumentation_HTML/Pie_Charts_Gauges_General_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Charts_Gauges_General_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Show Limit Set in Header

If this option is checked, the pie chart will display a text field showing the letter of the limit set presently being used for the element.

Show Style in Footer

When checked, the pie chart will display a text field showing the style (MVA, MW, etc) that the pie chart is set to (refer to the Style property described above.)

Max. Zoom Percentage for Full Resizing

The pie charts dynamically resize when you are zooming in and out on a oneline diagram. However, you can limit the point at which the pie charts resize when zooming in by setting a zoom level in this field. This helps prevent the pie charts from getting so large that they occupy the entire screen.

Min. Pie Chart Font Size for Warning/Limit

Specifies a minimum font size for displaying text in the pie chart object. This is useful when zooming out on the diagram, to keep the text visible by setting a minimum font size.

Background Color

The background color for the pie charts is automatically set to be the same as the online background. For a different color, select Specific color from the drop-down menu, and then click on the rectangle to the right to select the color. For a clear background, select Clear from the dropdown menu.

Pie Chart Relative Font Size

Slide the slider bar to select the font size for the pie chart. This will determine the size of the font indicating the percentage on the pie chart.

Pie Chart Font Color

Slide the slider bar to select the font size for the pie chart. This will determine the size of the font indicating the percentage on the pie chart.

---

<a id="pie-chart-gauge-dialogs"></a>

## Pie Chart / Gauge Dialogs

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Dialogs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Dialogs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are a number of pie chart/gauge objects that can be added to one-line diagrams. These objects are inserted via the **Pies/Gauges** menu in the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the **[Draw](02-simulator-ribbon.md#draw-tab-overview)** ribbon tab and include Areas, Buses, Generators, Injection Groups, Owners, Substations, Super Areas, Switched Shunts, Transformers, and Zones. The dialogs for these objects contain a common set of options that are required regardless of the object type. These common options as well as specific settings for the different object types are detailed below.

The [Pie Chart / Gauge Example](#pie-chart-gauge-example) shows how the fields in this dialog affect the pie chart or gauge display. The items shown in the diagram are explained in more detail throughout this section and in the [Pie Chart / Gauge Style Dialog](#pie-chart-gauge-style-dialog) description.

**Identification**

All dialogs have a section at the top that identify the pie chart/gauge object based on the type of device that the pie chart/gauge represents. The **Find…**button is available on most dialogs to open the Find tool that can be used to advanced search for a device. Specific identifying information for the different dialogs is given below:

  - **Area  
    **The area that the pie chart/gauge represents is identified based on **Area Number** or **Area Name**. To change the area that is represented, select an **Area Number** or **Area Name** from the dropdown boxes or click the **Find** button. The dropdown boxes are populated with all areas in the case.
  - **Bus  
    **The bus that the pie chart/gauge represents is identified based on **Bus Number** or **Bus Name**. To change the bus that is represented, select a **Bus Number** or **Bus Name** from the dropdown boxes or click the **Find** button. The dropdown boxes are populated with all buses in the case with valid area/zone/owner filters.
  - **Generator  
    **The generator that the pie chart/gauge represents is identified based on **Bus Number** and **Gen ID** or **Bus Name** and **Gen ID**. To change the generator that is represented, select a **Bus Number** or **Bus Name** from the dropdown boxes and change the **Gen ID** in the edit box or click the **Find** button. The dropdown boxes are populated with all buses in the case with valid area/zone/owner filters.
  - **Injection Group  
    **The injection group that the pie chart/gauge represents is identified based on the **Injection Group Name**. To change the injection group that is represented, select a new name from the dropdown box. The dropdown box is populated with all injection groups in the case.
  - **Owner  
    **The owner that the pie chart/gauge represents is identified based on **Owner Number** or **Owner Name**. To change the owner that is represented, select an **Owner Number** or **Owner Name** from the dropdown boxes or click the **Find** button. The dropdown boxes are populated with all owners in the case.
  - **Substation  
    **The substation that the pie chart/gauge represents is identified based on **Substation Number**, **Substation Name**, or **Substation ID**. To change the substation that is represented, select a **Substation Number**, **Substation Name**, or **Substation ID** from the dropdown boxes or click the **Find** button. The dropdown boxes are populated with all substations in the case.
  - **Super Area  
    **The super area that the pie chart/gauge represents is identified based on **Super Area Name**. To change the super area that is represented, select a new name from the dropdown box or click the **Find** button. The dropdown box is populated with all super areas in the case.
  - **Switched Shunt  
    **The switched shunt that the pie chart/gauge represents is identified based on **Bus Number** and **ID** or **Bus Name** and **ID**. To change the switched shunt that is represented, select a **Bus Number** or **Bus Name** from the dropdown boxes and change the **ID** in the edit box or click the **Find** button. The dropdown boxes are populated with all switched shunts in the case with valid area/zone/owner filters.
  - **Transformer  
    **The transformer that the pie chart/gauge represents is identified based on **Near Bus Number**, **Far Bus Number**, and **Circuit** or **Near Bus Name**, **Far Bus Name**, and **Circuit**. To change the transformer that is represented, click on the Find button to use the **Find** tool.
  - **Zone  
    **The zone that the pie chart/gauge represents is identified based on **Zone Number** or **Zone Name**. To change the zone that is represented, select a **Zone Number** or **Zone Name** from the dropdown boxes or click the **Find** button. The dropdown boxes are populated with all zones in the case.
  - **Model Expression**  
    The Expression that the pie chart/gauge represents is identified by its **Name**. To change the Model Expression that is represented, select a Model Expression from the dropdown box, which is populated with all Model Expressions in the case.

**Type of Field**

Use this option to select the field to display in the pie chart/gauge. Fields that are deemed of more common interest are listed for easy access. Any field associated with a particular device can be selected by first choosing **Select a Field** and then finding the particular field in the dropdown listing all available fields or by clicking **Find Field** and searching for the field of interest.

**Current Value**

**Percent**

This is the percent value calculated from the current value of the selected field. How the percent is calculated is based on the selection of limits and deadband and options associated with the Style. Details of the percent calculation are given in the **Pie Chart/Gauge Style Dialog** description.

**Value**

This is the current value of the selected field.

**In-Service**

When checked, the device represented by the pie chart/gauge is in-service. This is given for informational purposes only, as the status of devices cannot be changed from this dialog.

**Display Information**

**Type**

Select to display either a Pie Chart or Gauge.

**Gauge Orientation**

If **Type** option of Gauge is selected, set this option to draw either a Vertical or Horizontal gauge.

**Anchored **

When checked, the pie chart/gauge will be anchored to the display object representing the selected device.

**Size, Width, Use Fixed Gauge Width/Size Ratio**

**Size** determines the size of a pie chart and the vertical side length of a vertical gauge or horizontal side length of a horizontal gauge. **Width** is not applicable to a pie chart but determines the horizontal side length of a vertical gauge or the vertical side length of a horizontal gauge. **Width** is not enterable if the option of **Use Fixed Gauge Width/Size Ratio** is checked. This option is checked if the **Gauge Width is Always a Fixed Proportion of Size** option is checked on the Style dialog. The fixed width/size ratio is also set on the **Style** dialog.

**Ignore Dynamic Sizing**

When checked, any sizing based on the calculated percent will be ignored and the pie chart/gauge will stay at the defined size. Options to set the sizing based on calculated percent can be found on the **Style** dialog.

**Ignore Dynamic Open Sizing**

When checked, any sizing of pie chart/gauges based on the device that is represented being out-of-service will be ignored and the object will stay at the defined **Size**. Options to set the sizing for open devices can be found on the **Style** dialog.

**Always Show Value (Percent)**

When checked, the options set on the **Style** dialog to display the percent on pie chart/gauges are ignored and the percent value is always shown.

**Style, Show Style Dialog**

The **Style** defines the set of generic options that can be applied to any pie chart/gauge. An already defined style can be selected from the dropdown. Click **Show Style Dialog** to modify an existing style or to create a new style; this opens up the [Pie Chart / Gauge Style Dialog](#pie-chart-gauge-style-dialog).

**Limits**

**Low Limit, High Limit**

Determines the low and high values from which the percent will be calculated and the gauge fill will be drawn. These values are not enterable if the limits are determined from the **Style** or based on device limits. More information on how these limits are used in calculating the percent is given in the **Pie Chart Parameters Tab** and **Gauge Parameters Tab** sections in the **Pie Chart/Gauge Style Dialog** description.

**Use Device Low Limit**

When checked, the low limit will be determined from the low limit defined for the device for the selected field type. If device limits are not defined for the selected field, this option will not be enabled. If not enabled, the low limit will be based on the value entered in the **Low Limit** box.

**Use Device High Limit**

When checked, the high limit will be determined from the high limit defined for the device for the selected field type. If device limits are not defined for the selected field, this option will not be enabled. If not enabled, the high limit will be based on the value entered in the **High Limit** box.

**Override with Limits from Style**

When checked, the high and low limits from the selected **Style** will be used.

**Zero Percent Deadband**

**Use Style Zero Percent Deadband**

When checked, the zero percent high limit and zero percent low limits from the selected **Style** will be used.

**Zero Percent Low Limit, High Limit**

Determines the low limit and high limit for the zero percent deadband from which the percent will be calculated and the gauge fill will be drawn. These values are not enterable if the deadband is determined from the **Style.** The deadband represents the range of values for which the calculated percent will be zero. More information on how the deadband limits are used in calculating the percent is given in the **Pie Chart Parameters Tab** and **Gauge Parameters Tab** sections in the **Pie Chart/Gauge Style Dialog** description. ****

---

<a id="pie-chart-gauge-style-dialog"></a>

## Pie Chart / Gauge Style Dialog

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Pie Chart/Gauge Style Dialog** is available from any of the pie chart/gauge dialogs by selecting **Show Style Dialog** or from **Options \> Oneline Display Options… \> Pie Charts/Gauges** on the **Pie Charts/Gauge Styles** tab**.**

This dialog lists options that can be commonly applied to pie chart/gauge objects so that these same options do not have to be set for every individual object. The defined styles can be applied to any of the new pie chart/ gauge objects that include Areas, Buses, Generators, Injection Groups, Owners, Substations, Super Areas, Switched Shunts, Transformers, and Zones. These styles are currently not applicable to Lines and Interfaces. Some options are related to options that are set for individual pie chart/gauges. More information about individual object settings can be found in the **Pie Chart/Gauge Dialogs** section.

The [Pie Chart / Gauge Example](#pie-chart-gauge-example) shows how the fields in this dialog affect the pie chart or gauge display. The items shown in the diagram are explained in more detail throughout this section and in the [Pie Chart / Gauge Dialogs](#pie-chart-gauge-dialogs) description.

**Creating and Saving Styles**

**Style Name**

Drop-down box lists all currently defined pie chart/gauge styles. Select **Add New** to create a new style. Select **Rename** to change the name of an existing style. Select **Delete** to remove an existing style.

**Save AXD**

Save all currently defined pie chart/gauge styles to a Display Auxiliary file.

**Load AXD**

Load pie chart/gauge styles from a Display Auxiliary file.

**Hide all Style Objects (except in edit mode)**

When checked, the pie chart/gauge will not be visible in run mode.

**Show Header (Object ID)**

When checked, the header of the pie chart/gauge will contain identifying information about the device that the pie chart/gauge represents.

**Show Footer (Field Type)**

When checked, the field type that is being used in the pie chart/gauge will be displayed in the footer of the pie chart/gauge.

**Default Style**

When checked, this style is one of the default styles that are defined. Default styles cannot be renamed or deleted. This is an informational field and cannot be changed by the user.

**Limits and Zero Percent Deadband Values**

Define the High and Low Limits to use when the option **Override with Limits from Style** is selected for the pie chart/gauge that is using this style and the High and Low Zero Percent Deadbands to use when the option **Use Style Zero Percent Deadband** is selected for the pie chart/gauge that is using this style. The deadband represents the range of values for which the calculated percent will be zero. More information is given in the [Pie Chart Parameters Tab](#pie-chart-gauge-style-dialog---pie-chart-parameters-tab) and [Gauge Parameters Tab](#pie-chart-gauge-style-dialog---gauge-parameters-tab) sections on how the limits are used in calculating the percent.

The remainder of the dialog is broken down into four tabs:

  - [Standard Parameters](#pie-chart-gauge-style-dialog---standard-parameters-tab)
  - [Open Parameters](#pie-chart-gauge-style-dialog---open-parameters-tab)
  - [Pie Chart Parameters](#pie-chart-gauge-style-dialog---pie-chart-parameters-tab)
  - [Gauge Parameters](#pie-chart-gauge-style-dialog---gauge-parameters-tab)

---

<a id="pie-chart-gauge-style-dialog---standard-parameters-tab"></a>

## Pie Chart / Gauge Style Dialog - Standard Parameters Tab

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Standard_Parameters_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Standard_Parameters_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Normal Scalar, Normal Fill Color**

These are the standard, pre-warning scaling factor and fill color for pie chart/gauges. To change the color, click on the color to open the Color dialog.

**Font Color**

Font color of the text displayed in the pie chart/gauge. To change the color, click on the color to open the Color dialog.

**Border Width**

Width of any border portion of the pie chart/gauge. The border of a pie chart encloses the entire pie chart as well as the filled portion of the pie chart. The border of a gauge encloses the entire gauge. The border width also impacts the width of the lines marking the limits and deadband on the gauge.

**Border Color**

Color of any border portion of the pie chart/gauge. The border of a pie chart encloses the entire pie chart as well as the filled portion of the pie chart. The border of a gauge encloses the entire gauge. The border color also is the color used for the lines marking the limits and deadband on the gauge. To change the color, click on the color to open the Color dialog.

**Border Color Same as Fill Color**

When checked, the border color will be the same color as the fill color and the color selected in the Border Color will be ignored.

**Background Color**

The drop-down box allows selection of three options for the background color: Oneline Background, Specific Color, and Clear. Oneline Background will color the pie chart/gauge background the same color as the selected background color for the oneline. Specific Color will allow the selection of a user specified color. To specify a color, click the box to the right of the drop-down to open the Color dialog. The Clear option will not use a background color and objects underneath the pie/chart gauge will be visible through the unfilled portions of the pie chart/gauge.

**Relative Font Size**

Modify the track bar to adjust the size of the font relative to the size of the pie chart/gauge.

**Max Zoom Percent for Full Resize**

Pie chart/gauges dynamically resize when zooming in and out on oneline diagrams. A limit can be placed on the point at which the pie chart/gauges resize when zooming in by setting a zoom level in this field. This helps prevent the pie chart/gauges from getting so large that they occupy the entire screen.

**Warning/Limit Scalars and Colors**

The table in this section allows the definition of different settings for pie chart/gauge size and fill color based on the percent value represented by the pie chart/gauge. Points can be added or removed from this table by right-clicking in the table and using the Insert and Delete options from the popup menu.

To modify the Percent and size Scalar for a record in the table, click on the value in the cell and type in a new value. To change the color associated with the percent value, double click in the Color cell to open the Color dialog.

**Use Discrete Map**

When checked, discrete colors will be used for the pie chart/gauges based on the colors specified in the table. Otherwise, colors will be blended if the percentage represented in the pie chart/gauge falls between percentages defined in the table.

---

<a id="pie-chart-gauge-style-dialog---open-parameters-tab"></a>

## Pie Chart / Gauge Style Dialog - Open Parameters Tab

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Open_Parameters_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Open_Parameters_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Open parameters are applied to any pie chart/gauges when the device that they represent is out-of-service.

**Special Formatting for Open Devices**

When checked, the **Open Size Scalar**, **Open Border Width**, and **Open Border Color** options are applied when a device is out-of-service.

**Use Special Open Background Color**

When checked, the **Open Background Color** option is applied.

**Open Symbol**

When an **Open Symbol** other than None is selected, the symbol will be drawn in the selected **Open Symbol Color**.

---

<a id="pie-chart-gauge-style-dialog---pie-chart-parameters-tab"></a>

## Pie Chart / Gauge Style Dialog - Pie Chart Parameters Tab

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Pie_Chart_Parameters_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Pie_Chart_Parameters_Tab.htm)*

Options given on this tab only apply to how pie charts are displayed.

**Show Value Percent**

When the percent of the pie chart/gauge exceeds the value specified in this field, the percent is shown as text within the pie chart/gauge. The default is 80%.

**Display of Values Below the Zero Percent Deadband**

The selection of this option determines how to calculate the percent represented in pie charts. Four parameters are required for determining this: low limit, high limit, zero percent low limit, and zero percent high limit. These four limits are determined from options set with individual pie charts and/or options set with the style. In general, the zero percent low limit and zero percent high limit define the deadband in which the percent is zero. The percent is then determined based on where the selected field value falls within the high limit and zero percent high limit and the low limit and zero percent low limit. The specific calculations used for determining the percent is given for the options below. In all cases if the limits are not defined correctly (i.e., none of the If..then statements below apply), the percent will be returned as zero.

  - **Allow negative percent values**
      - If (field value) \> (zero percent high limit) and (high limit) \> (zero percent high limit) then  
        Percent = ((field value) – (zero percent high limit))/((high limit) – (zero percent high limit))
      - If (field value) \< (zero percent low limit) and (low limit) \< (zero percent low limit) then  
        Percent = ((field value) – (zero percent low limit))/((zero percent low limit) – (low limit))
  - **Use absolute value** (i.e., percent always \>= 0)
      - Same calculations as in **Allow negative percent values** except that the absolute value of the calculated percentage is reported.
  - **Low limit is zero percent**
      - The zero percent deadband limits are ignored in this option and the percent is calculated based on the low and high limits only
      - If (high limit) \> (low limit) then  
        Percent = ((field value) – (low limit))/((high limit) – (low limit))
  - **Treat values below zero deadband as zero**
      - If (field value) \> (zero percent high limit) and (high limit) \> (zero percent high limit) then  
        Percent = ((field value) – (zero percent high limit))/((high limit) – (zero percent high limit))
      - If (field value) \< (zero percent low limit) and (low limit) \< (zero percent low limit) then  
        Percent = 0

Fill Options: Fill counter-clockwise(added in version 23 patch on June 4, 2024)

Specify whether pie charts fill up in a counter clock-wise or clock-wise fashion

Fill Options: Fill start angle (degrees)(added in version 23 patch on June 4, 2024)

Specify the start angle in degrees where 0.0 degrees represent a horizontal line

---

<a id="pie-chart-gauge-style-dialog---gauge-parameters-tab"></a>

## Pie Chart / Gauge Style Dialog - Gauge Parameters Tab

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Gauge_Parameters_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Style_Dialog_Gauge_Parameters_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Options given on this tab only apply to how gauges are displayed.

**Show Limit Labels**

When checked, text labels will be drawn with the gauge showing the four limits in use.

**Include Units in Limit Labels**

When checked, units will be included when the limit labels are shown.

**Numeric Value Type**

This option allows the numeric value to either be displayed as the **Actual Value** or the calculated **Percent** value.

**Display of Numeric Value**

This option determines when the value of the field is displayed with the gauge. **Never** will not show the value, **Always** will always show the value, and **If Violating Warning/Limit Value** will only show the value if it is outside of the limit range that is currently in use.

**Digits to Right of Decimal**

This parameter determines how many digits to the right of the decimal are displayed in the limit labels and the numeric value when they are shown with the gauge.

**Gauge Width is Always a Fixed Proportion of Size**

When checked, the **Gauge Fixed Width/Size Ratio** is used to determine the width of the gauge as a proportion of the size (height). Note: the size of gauges is specified for individual gauges on the pie chart/gauge dialogs.

**Gauge Fixed Width/Size Ratio**

Specifies the ratio of the gauge width to the size when the **Gauge Width is Always a Fixed Proportion of Size** option is checked.

**Percent Overhang on Top of Gauge**

The overhang at the top of the gauge is the region above the high limit line. The size of this region is defined as a percentage of the total size of the gauge.

**Percent Overhang on Bottom of Gauge**

The overhang at the bottom of the gauge is the region below the low limit line. The size of this region is defined as a percentage of the total size of the gauge.

**Gauge Fill and Percent Calculation**

These options determine how the calculated percent will be displayed and how the gauge will be filled. Four parameters are required for determining these: low limit, high limit, zero percent low limit, and zero percent high limit. These four limits are determined from options set with individual gauges and/or options set with the style. In all cases if the limits are not defined correctly, the percent will be returned as zero.

**Use Absolute Value for Percent**

When checked, the displayed percent will be the absolute value of the calculated percent. This option does not impact how the gauge will be filled.

**Gauge Fill Options (Zero Percent Reference)**

This option determines how the gauge will be filled. If **Fill up or down from deadband** is selected, the fill will begin at the low or high deadband limit and continue up or down depending upon where the field value falls within the defined limits. If **Fill up from bottom** is selected, the fill will begin at the bottom of the gauge and fill up to the field value.

Regardless of which fill option is selected, the following equations will be used to calculate the percent based upon where the field value falls within the defined limits:

If (field value) \> (zero percent high limit) and (high limit) \> (zero percent high limit) then

Percent = ((field value) – (zero percent high limit))/((high limit) – (zero percent high limit))

If (field value) \< (zero percent low limit) and (low limit) \< (zero percent low limit) then

Percent = ((field value) – (zero percent low limit))/((zero percent low limit) – (low limit))

**Ignore Deadband**

When checked, deadband limits are ignored. This effectively forces the fill to start from the bottom of the gauge and fill up to the field value. The percent is calculated based on the following equation and will always be reported as the absolute value:

If ((high limit) – (low limit)) \<\> 0 then

Percent = ((field value) – (low limit))/((high limit) – (low limit))

**Override Low Limits with a Value of Zero**

When checked, the low limit value will be set to zero when determining the fill and calculating the percent. This option is only applied if the **Ignore Deadband** check box is also checked. The percent is calculated based on the following equation and will always be reported as the absolute value:

If ((field value) \> 0) and ((high limit) \<\> 0) then

Percent = (field value)/(high limit)

---

<a id="pie-chart-gauge-example"></a>

## Pie Chart / Gauge Example

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Example.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Example.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

![image\\ebx\_-1970246517.gif](images/ebx_-1970246517_668x363.gif)

---

<a id="palette-overview"></a>

## Palette Overview

*Source: [`Content/MainDocumentation_HTML/palette_overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/palette_overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The display object palettes are designed to help you lay out a new oneline diagram for a pre-existing power flow model as quickly as possible. Display object palettes exist for [Areas](11-building-onelines-network-objects.md#area-display-objects), [Buses](11-building-onelines-network-objects.md#bus-display-objects), [Substations](11-building-onelines-network-objects.md#substation-display-objects) and [Zones](11-building-onelines-network-objects.md#area-display-objects). Palettes list the display objects that you have already added to the oneline, the display objects that have not yet been drawn that neighbor those displayed objects, and the set of all display objects that have not yet been added to the drawing. By selecting and dragging a display object name from either the **Undisplayed** **Neighbors** list or the **All Undisplayed** **** list to a location on the oneline diagram where you would like that object to appear, you can add that display object to the drawing with very little effort.

To see which elements neighboring a particular device are already on the oneline diagram and which are not, highlight a device in either the **Displayed** or **All Undisplayed** list. The **Displayed Neighbors** and **Undisplayed Neighbors** columns will list the corresponding neighboring devices for the selected device, allowing you to drag the undisplayed neighbors to the diagram if you wish.

The display object palettes, in conjunction with the [auto-insert capabilities](https://www.powerworld.com/WebHelpvoid\(0\);) of other devices, are especially useful for adding a large region of an interconnection in relatively little time.

To display one of the four available [palettes](#using-the-insert-palettes), select **Show Insert Palette For** from the **[Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. To display the palette with the focus set to an object already displayed, right-click on that object on the diagram and select **\*\*\* Palette** (where \*\*\* is the name of the object type) from the popup menu.

---

<a id="using-the-insert-palettes"></a>

## Using the Insert Palettes

*Source: [`Content/MainDocumentation_HTML/Using_the_Insert_Palettes.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Using_the_Insert_Palettes.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

<table>
<tbody>
<tr class="odd">
<td><img src="images/Ribbon_Draw_Quick_Insert_Show_Pallette.gif" alt="Ribbon Draw Quick Insert Show Pallette" /></td>
<td><p>The display object palettes are designed to help you lay out a new oneline diagram for a pre-existing power flow model as quickly as possible. Display object palettes exist for <a href="11-building-onelines-network-objects.md#area-display-objects" id="aanchor269">Areas</a>, <a href="11-building-onelines-network-objects.md#bus-display-objects" id="aanchor270">Buses</a>, <a href="11-building-onelines-network-objects.md#substation-display-objects" id="aanchor271">Substations</a> and <a href="11-building-onelines-network-objects.md#area-display-objects" id="aanchor272">Zones</a>. To open one of the palettes you must be in <a href="01-getting-started.md#edit-mode-introduction">Edit Mode</a>and then go to the <a href="02-simulator-ribbon.md#draw-tab-overview">Draw</a> ribbon tab, and choose the <strong>Show Insert Palette For Menu</strong> from the <a href="02-simulator-ribbon.md#quick-insert-ribbon-group">Quick Insert</a> ribbon group.</p>
<p> </p>
<p>The Insert Palettes can be used in conjunction with the various auto-insert capabilities also found on the <a href="02-simulator-ribbon.md#quick-insert-ribbon-group">Quick Insert</a> ribbon group. These features allow for the creation of oneline diagrams much more quickly than inserting oneline objects one at a time using the <a href="02-simulator-ribbon.md#individual-insert-ribbon-group">Individual Insert</a> ribbon group.</p>
<p>When you choose one of the palettes the dialog which appears will look like the image below. The following image shows the Bus Palette.</p></td>
</tr>
</tbody>
</table>

![Palette Insert](images/Palette_Insert.gif)

Palettes list the display objects that you have already added to the oneline, the display objects that have not yet been drawn that neighbor those displayed objects, and the set of all display objects that have not yet been added to the drawing.

The display object palettes feature the following controls:

Displayed

Lists those objects defined in the power flow case that have already been added to the oneline diagram. When you click on an entry in the **Displayed** list, the contents of the **Displayed Neighbors** and **Undisplayed** **Neighbors** lists will be refreshed to identify all objects that neighbor the display object you selected. Only the display objects matching the type of Insert Palette opened will be shown in the list.

Double click on an entry in this list to pan to it so that the selected display object appears in the center of the screen. If you are looking at the Insert Palette for Buses, you can right-click on an entry and choose either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display) to learn more about the selected bus.

Displayed Neighbors

Lists those objects defined in the power flow case that neighbor the display object selected in the **Displayed** list that have already been drawn on the oneline diagram. You can make a "Displayed Neighbor" the selected "Displayed" object by right-clicking on a display object in the **Displayed Neighbor List** and selecting **Make Current Displayed** from the local menu. Only the display objects matching the type of Insert Palette opened will be shown in the list.

Undisplayed Neighbors

Lists those display objects defined in the power flow case that neighbor the object selected in the **Displayed** list that have not yet been drawn. To add the undrawn display object to the oneline diagram, select its name with the left mouse button and keep the left mouse button pressed as you move the mouse to the point on the oneline where you would like to drop the object. When you let go of the left mouse button, the **Information Dialog** box for that display object will appear. (If you do not want the information Dialog box to appear the use the right-click local menu to uncheck the option to regarding showing the information dialog). Use the Information Dialog to change display parameters for the object and click **OK** to finish dropping the object onto the oneline. The display object you have just added will be appended to the end of the **Displayed** list and will also be added to the **History List** so that you can identify its own undrawn neighbors quickly. Only the display objects matching the type of Insert Palette opened will be shown in the list.

If you are looking at the Insert Palette for Buses, you can right-click on an entry and choose either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to learn more about the selected bus.

All Undisplayed

Lists those display objects defined in the power flow case that have not yet been added to the oneline diagram, regardless of whether the object neighbors a displayed object or not. This list functions identically to the **Undisplayed Neighbors List**. To add the undrawn display object to the oneline diagram, select its name with the left mouse button and keep the left mouse button pressed as you move the mouse to the point on the oneline where you would like to drop the object. When you let go of the left mouse button, the **Information Dialog** box for that display object will appear. (If you do not want the information Dialog box to appear the use the right-click local menu to uncheck the option to regarding showing the information dialog). Use the Information Dialog to change display parameters for the object and click **OK** to finish dropping the object onto the oneline. The display object you have just added will be appended to the end of the **Displayed** list and will also be added to the **History List** so that you can identify its undrawn neighbors quickly. Only the display objects matching the type of Insert Palette opened will be shown in the list.

If you are looking at the Insert Palette for Buses, you can right-click on an entry and choose either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to learn more about the selected bus.

History List

Identifies the display objects you have added to the oneline diagram using the insert palettes since the last time you opened the display object palette. Select a name from this list to display the undrawn neighbors of the corresponding display object. Only the display objects matching the type of Insert Palette opened will be shown in the list.

Define a Filter

The **Define a Filter** button opens the [Advanced Filters](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) dialog. This dialog allows you to customize which display objects appear in the various lists. This can be helpful, for example, if you wish to add objects to the oneline that reside only in particular areas, or if you don't want objects less than a certain voltage level to be listed.

When you click **OK** on the [Advanced Filters](04-model-explorer-and-case-information-part2.md#advanced-filters-dialog) dialog, the display object palette's lists will automatically be updated to reflect the filter settings.

Close

Click **Close** when you are done using the display object palette.

Right-Click Local Menu of the Palette 

There are several options available on the Right-Click

**Search for** : Click this option to search through the lists for a particular object. It will open the familiar [Find Object dialog](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

**Auto-Zoom When Panning** : When double-clicking on the displayed objects in the palette, you will automatically be panned so that object is in the center of the screen. Check this option to also automatically zoom in/out to a reasonable level at the same time.

**Export All Undisplayed List** : Choose this option to export this list of undisplayed objects to a text file.

**Refresh Status** : Choose this option to ensure that the list of Displayed/Undisplayed objects is correct.

**Show Dialog after Inserting** : check or uncheck this option to control whether the information dialog for the object will appear when using the palette

---

<a id="automatically-inserting-buses"></a>

## Automatically Inserting Buses

*Source: [`Content/MainDocumentation_HTML/Automatically_Inserting_Buses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatically_Inserting_Buses.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can automatically insert buses on your oneline diagram if you have data regarding their spatial or geographic location. To achieve this, go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Buses** ****on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group. This opens the Auto Insert Bus Dialog.

**Note:** Auto-insert buses is only for inserting bus objects on the diagram representing existing data. In other words, you cannot use the auto-insert buses routine to add new buses to the load flow model. See topics on loading data from [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) or from [Excel](04-model-explorer-and-case-information-part1.md#case-information-displays) for creating new buses (or other objects) in an existing load flow case.

Insert by longitude, latitude

If you have stored latitude and longitude information with the Bus records in Simulator, you can use that information to automatically insert the buses on a oneline diagram. Select the option on the dialog for finding bus locations based on **Longitude and Latitude stored with data records**. When selected, the [Map Projection](16-oneline-gis-tools.md#map-projections) option will become enabled. Choose the type of projection you would like to be used for placing the buses on the diagram.

Insert by locations specified in a file

You must first specify the file which contains the location data. You must also specify whether the file contains x,y coordinates or longitude, latitude coordinates. The format of the location data text file is as follows:

The first line of this text file is ignored by Simulator. The following lines consist of three numbers: Bus Number, X location, and Y location. If you are reading longitude, latitude, then X signifies longitude and Y signifies latitude.

Num, X Location, Y Location

1, 24001.46, 19715.15 

3, 24001.46, 19715.15 

16, 24130.91, 19638.99

17, 24007.31, 19093.09

21, 23649.27, 18439.07

22, 23649.27, 18439.07

etc...

Simulator will place the buses on the oneline diagram at the X, Y locations given. If you specified that the file contained longitude, latitude information, then select the **[**Map Projection**](16-oneline-gis-tools.md#map-projections)** to use when converting the longitude, latitude values from the file. The buses will be drawn according to default bus object information defined in the Default Drawing Values for New Objects dialog.

If you would like Simulator to **Autoinsert transmission lineswhen finished** with the auto insertion of your buses, check the box. Transmission lines and transformers will be automatically drawn based on the Line/XFMR default options defined in the [Default Drawing Values for New Objects](11-building-onelines-network-objects.md#setting-default-drawing-options) dialog.

Check the **Insert bus only if not already shown on the oneline** to ensure that multiple display objects are not inserted for the same element.

Clicking the **OK** button will instruct Simulator to continue by placing the buses according to the specified settings on the dialog. Click **Cancel** to exit the process without inserting the buses.

---

<a id="automatically-inserting-transmission-lines"></a>

## Automatically Inserting Transmission Lines

*Source: [`Content/MainDocumentation_HTML/automatically_inserting_lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/automatically_inserting_lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Insertion of Lines/Transformers Dialog is used to automatically draw transmission lines and transformers on the oneline diagram between existing bus display objects. Only branches that are already defined in the power flow case can be added automatically; if you need to define a brand new branch, see [Transmission Line Display Objects](12-building-onelines-branches-and-devices.md#transmission-line-display-objects). Thus, this option is useful only when you are starting with an existing power flow case, not building a case from scratch.

To insert lines and transformers automatically, you must first have drawn the buses for each end of the device. Simulator then draws the branch display objects connecting the buses for each transmission line/transformer in the power flow case not already shown on the oneline.

To display the dialog, in the Edit Mode ****go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Lines** on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.

The dialog has the following options:

Minimum kV Level

Simulator will automatically draw line and transformer display objects between terminals whose nominal voltages meet or exceed the minimum kV level specified in this field. For a branch object to be drawn, either one of its terminals must satisfy this criterion. This option is useful for suppressing the automatic addition of generator step-up transformers if that kind of detail is not warranted.

Default Drawing Values

This button opens the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options). Options such as the automatic insertion of transmission line stubs, text fields, circuit breakers, and pie charts are specified in the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options).

Insert Text Fields

If this box is checked, the default fields associated with the transmission line will appear around the transmission line.

Insert Equivalenced Objects

If this option is checked, [equivalenced](19-edit-mode-tools.md#equivalents) objects modeled as lines will also be automatically inserted with the real transmission lines.

Use Only Selected Buses

Instead of having Simulator automatically insert line and transformer display objects throughout the oneline diagram, you can force it to insert the new objects only between the [bus display objects](11-building-onelines-network-objects.md#bus-display-objects) that are currently selected. This option is enabled only when two or more bus display objects are currently selected on the oneline.

Insert Pie Chart for Lines with No Limit and Bus Ties

If this option is checked, Simulator will add [pie chart objects](12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines) to the lines that have no given limit or are bus ties as they are auto-inserted. Typically if a line is a bus tie or has no given limit, it is meaningless to include a pie chart on the element, since no relevant information about the transmission element can be gained from the pie chart object.

Insert Multi Section Lines

Check this option if you wish for Simulator to automatically insert lines designated as [multi-section lines](05-case-information-displays-by-object-part2.md#multi-section-lines-display) as well.

Identifying Bus Ties

This area deals with lines used as ties between breakers. These lines are modeled as zero impedance connections. The identification of a branch as a bus tie depends on the value specified as the **Maximum P.U. Impedance for Bus Ties**. Branches with total P.U. impedance below this value will be considered bus ties when auto-inserted.

In this area two choices are given for how to insert the bus tie breakers: **Do not insert stubs for bus ties** and **Only insert a single circuit breaker**. The first choice allows you to decide if line stubs will be drawn when the tie breaker is inserted. The second sets whether or not only one circuit breaker is inserted on the tie breaker. This could be useful for determining real lines from bus tie breakers.

---

<a id="automatically-inserting-generators"></a>

## Automatically Inserting Generators

*Source: [`Content/MainDocumentation_HTML/automatically_inserting_generators.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/automatically_inserting_generators.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Insertion of Generators Dialog is used to automatically draw generators on the oneline diagram on existing bus-display objects. Only generators that are already defined in the power flow case can be added automatically; if you need to define a new generator, see [Generator Display Objects](11-building-onelines-network-objects.md#generator-display-objects). Thus, this option is useful only when you are starting with an existing power flow case, not building a case from scratch.

To insert generators automatically, you must first have drawn the terminal bus for each device. Simulator then draws the generator display objects connected to the buses for each generator in the power flow case not already shown on the oneline.

To display the dialog, in the Edit Mode **** go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Generators** on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.

The dialog has the following options:

Minimum kV Level

Simulator will automatically draw generator display objects at terminal buses whose nominal voltages meet or exceed the minimum kV level specified in this field. For a generator object to be drawn, its terminal must satisfy this criterion.

Default Drawing Values

This button opens the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options). Options such as the automatic insertion of text fields are specified in the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options).

Insert Text Fields

When this box is checked, the default fields associated with the generator will appear around the generator, such as voltage, name, and/or MW.

Insert Equivalenced Objects

This field is not used when automatically inserting generators.

Use Only Selected Buses

Instead of having Simulator automatically insert generator display objects throughout the oneline diagram, you can force it to insert the new objects only between the bus display objects that are currently selected. This option is enabled only when two or more bus display objects are currently selected on the oneline.

---

<a id="automatically-inserting-loads"></a>

## Automatically Inserting Loads

*Source: [`Content/MainDocumentation_HTML/automatically_inserting_loads.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/automatically_inserting_loads.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Insertion of Loads Dialog is used to automatically draw loads on the oneline diagram on existing bus display objects. Only loads that are already defined in the power flow case can be added automatically; if you need to define a brand new load, see [Load Display Objects](11-building-onelines-network-objects.md#load-display-objects). Thus, this option is useful only when you are starting with an existing power flow case, not building a case from scratch.

To insert loads automatically, you must first have drawn the terminal bus for each device. Simulator then draws the load display objects connected to the buses for each load in the power flow case not already shown on the oneline.

To display the dialog, in the Edit Mode **** go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Loads** ****on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.

The dialog has the following options:

Minimum kV Level

Simulator will automatically draw load display objects at terminal buses whose nominal voltages meet or exceed the minimum kV level specified in this field. For a load object to be drawn, its terminal must satisfy this criterion.

Default Drawing Values

This button opens the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options). Options such as the automatic insertion of text fields are specified in the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options).

Insert Text Fields

When this box is checked, the default fields associated with the load will appear with the loads, such as MVAR and/or MW.

Insert Equivalenced Objects

If this option is checked, [equivalenced](19-edit-mode-tools.md#equivalents) objects modeled as loads will also be automatically inserted with the real transmission lines.

Use Only Selected Buses

Instead of having Simulator automatically insert load display objects throughout the oneline diagram, you can force it to insert the new objects only between the bus display objects that are currently selected. This option is enabled only when two or more bus display objects are currently selected on the oneline.

---

<a id="automatically-inserting-switched-shunts"></a>

## Automatically Inserting Switched Shunts

*Source: [`Content/MainDocumentation_HTML/Automatically_Inserting_Switched_Shunts.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatically_Inserting_Switched_Shunts.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Insertion of Switched Shunts Dialog is used to automatically draw switched shunts on the oneline diagram on existing bus-display objects. Only switched shunts that are already defined in the power flow case can be added automatically; if you need to define a brand new switched shunt, see [Switched Shunt Display Objects](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects). Thus, this option is useful only when you are starting with an existing power flow case, not building a case from scratch.

To insert switched shunts automatically, you must first have drawn the terminal bus for each device. Simulator then draws the switched shunt display objects connected to the buses for each switched shunt in the power flow case not already shown on the oneline.

To display the dialog, in the Edit Mode **** go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Switched Shunts** ****on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.

The dialog has the following options:

Minimum kV Level

Simulator will automatically draw switched shunt display objects at terminal buses whose nominal voltages meet or exceed the minimum kV level specified in this field. For a switched shunt object to be drawn, its terminal must satisfy this criterion.

Default Drawing Values

This button opens the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options). Options such as the automatic insertion of text fields are specified in the [Default Drawing Values Dialog](11-building-onelines-network-objects.md#setting-default-drawing-options).

Insert Text Fields

When this box is checked, the default fields associated with the switched shunt will appear around the switched shunt, such as nominal MVAR.

Use Only Selected Buses

Instead of having Simulator automatically insert switched shunt display objects throughout the oneline diagram, you can force it to insert the new objects only at the bus display objects that are currently selected. This option is enabled only when two or more bus display objects are currently selected on the oneline.

---

<a id="automatically-inserting-substations"></a>

## Automatically Inserting Substations

*Source: [`Content/MainDocumentation_HTML/Automatically_Inserting_Substations.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatically_Inserting_Substations.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can automatically insert substations on your oneline diagram if you have data regarding their spatial or geographic location. To achieve this, go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Substations** ****on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group. This opens the Auto Insert Substation Dialog.

Insert by longitude, latitude

If you have stored latitude and longitude information with the Substation records in Simulator, you can use that information to automatically insert the substations on a oneline diagram. Select the option on the dialog for finding substation locations based on **Longitude and Latitude stored with data records**. When selected, the **[Map Projection](16-oneline-gis-tools.md#map-projections)** option will become enabled. Choose what type of projection you would like to be used for placing the substations on the diagram.

Insert by locations specified in a file

You must first specify the file which contains the location data. You must also specify whether the file contains x,y coordinates or longitude, latitude coordinates. The format of the location data text file is as follows

The first line of this text file is ignored by Simulator. The following lines consist of three numbers: Substation Number, X location, and Y location. If you are reading longitude, latitude then X signifies longitude and Y signifies latitude.

Num, X Location, Y Location

1, 24001.46, 19715.15

3, 24001.46, 19715.15

16, 24130.91, 19638.99

17, 24007.31, 19093.09

21, 23649.27, 18439.07

22, 23649.27, 18439.07

etc...

Simulator will place the substations on the oneline diagram at the X, Y locations. If you specified that the file contained longitude, latitude information, then select the **[Map Projection](16-oneline-gis-tools.md#map-projections)** you would like to be used when converting the longitude, latitude values from the file. The substations will be drawn according to default substations object information defined in the Default Drawing Values for New Objects dialog.

Finally, if you would like Simulator to **Auto insert transmission lines when finished** with the auto insertion of your substations, check this box. Transmission lines and transformers will be automatically drawn based on the Line/XFMR default options defined in the [Default Drawing Values for New Objects](11-building-onelines-network-objects.md#setting-default-drawing-options) dialog.

Check the **Insert substation only if not already shown on the oneline** to ensure that multiple display objects are not inserted for the same element.

Clicking the **OK** button will instruct Simulator to continue by placing the substations according to the specified settings on the dialog. Click **Cancel** to exit the process without inserting the substations.

---

<a id="automatically-inserting-borders"></a>

## Automatically Inserting Borders

*Source: [`Content/MainDocumentation_HTML/Automatically_Inserting_Borders.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatically_Inserting_Borders.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator allows you to automatically insert geographic borders, which PowerWorld Corporation has drawn. These include the states in the United States of America and several international borders as well. You may also define a border in a text file and insert this User-Defined border. It is highly recommended that you create a diagram and insert borders before you begin adding power system objects to the diagram.

To bring up the **Auto Insert Borders Dialog**, go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Borders** ****on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.

Options

The Options tab allows you to set characteristics of the border lines when they are inserted on the oneline diagram. Most of these options are available from the Format menu in Edit Mode, and can be changed for a border by selecting the border(s) in Edit Mode and then selecting the appropriate option from the Format menu to change the desired option(s).

Make border lines immobile

This option is very useful for preventing you from inadvertently moving the border lines in Edit Mode once they have been placed.

Automatically link county and state borders to supplemental data

Background lines created from inserting borders can be linked to [Supplemental Data](15-using-onelines-tools-and-options.md#supplemental-data) records for purposes of further identifying these objects. This is useful when applying filters, applying dynamic formatting, using Select By Criteria, or defining custom hints with display objects created from inserting the borders. This option is only available when inserting United States borders.

When this option is checked, background lines created for the borders will be automatically linked to Supplemental Data records. If necessary, Supplemental Data records will be created with the Classification being either *State* or *County*, depending on the Border Type selected when inserting United States borders, and the Name being the name of either the state or county.

Line Options

Choose the line thickness and line color for the border lines.

Fill Options

Choose the fill options if you wish to "fill in" the border regions with a background fill color.

Stack Level

Choose the stack level for the border lines. The stack level affects which objects appear "over" or "under" other objects on the diagram. Typically background lines are either placed in the Background or Base levels, so that they appear beneath power system objects on the diagram. Further we would recommend that if you are using background fill colors for the borders that you choose a stack level of Base. The only difference between the Background and Base levels is that the Base level objects can be right-clicked on in Run Mode and allows the default diagram popup menu to appear. Right-clicking on Background level objects in Run Mode will not display the default popup menu.

Layers

When Borders are automatically inserted on a diagram using this tool, a *Borders* [screen layer](14-editing-onelines.md#screen-layers) will be added to the layer drop-down box, if a *Borders* layer does not already exist for the oneline diagram. You can choose to leave the borders in the standard *Default* layer, to place the borders in the new *Borders* layer, or you can [create a new custom layer](14-editing-onelines.md#screen-layers) by clicking the **Define Layers** button. If no default borders layer has been previously established (borders were previously inserted on the oneline), the *Borders* layer or selected user created layer will be set as the default Borders layer. The default Borders layer is different than the standard *Default* layer for objects. The default Borders layer information is stored in the system registry, and is only used to recall which layer borders were assigned to the previous time borders were automatically inserted.

Apply Default Drawing Values

Click this button to apply the Background line settings from the [Default Drawing Values](14-editing-onelines.md#default-drawing-values).

Border File Path

Designate the border file location.

PowerWorld Library

Pre-Defined Selections

Choose between North America, USA State Borders, Canadian Province Borders, or Entire World to insert the selected region. These options make things quicker than selecting from the individual menus if entire countries or continents are to be inserted.

Once you have selected the regions that you want to insert, Click **OK**.

United States

This tab allows you to select states in the United States that you want to insert. (Note: to select several states to insert at once, use the Ctrl and Shift keys while clicking with your mouse.) These states will be placed on the screen such that as you add new states they will be placed geographically appropriately.

**Include Hawaii and Alaska:**Select all or any of these items to place these states on the screen.

**Border Types:** Select the type of border. *State* will only show the state border and the *County* will show the state border as well as the counties of the state.

Once you have selected the states you want to insert, Click **OK**.

Canada

This tab allows you to select provinces in Canada that you want to insert. (Note: to select several provinces to insert at once, use the Ctrl and Shift keys while clicking with your mouse.) These provinces will be placed on the screen such that as you add new provinces they will be placed geographically appropriately.

Once you have selected the provinces you want to insert, Click **OK**.

World

This tab allows to insert borders which PowerWorld Corporation has acquired for countries around the world. PowerWorld Corporation will continue to add more border files as we receive them. Note: if you have drawn a oneline which contains a geographic border you would like us to include in future version of Simulator, please contact us at support@powerworld.com and we'll add it to our next release.

[Map Projection](16-oneline-gis-tools.md#map-projections)

This setting is important for anyone including border files outside of North America. By default, Simulator draws borders using a simple conic projection referenced to North America. This can result in border files of other countries being drawn incorrectly if based on this reference. To correctly draw borders of other countries around the world, select the Entire World setting, which uses a Mercator projection.

User-Defined Borders

This tab allows you to read in a border from a text file that you create. The first row of this text file is a comment row and is ignored when reading it in. After this it reads in the description of each background line. This description starts with the number of points in the line followed by a list of x, y coordinates. The file ends when the number of points for a line is read as -1. An example file follows:

Comment row

5

59, 60 

10, 20 

40.3, 95.20 

89.3, 22.11 

79.5, 34.56 

45

40, 66 

etc… 

\-1 this signifies the end of the file

To read the data, first specify the file name and location containing the data using the Browse button. Next indicate if the file contains data in Longitude, Latitude or in converted Simulator X,Y coordinates. If the data is Longitude and Latitude, then also specify if the map projection to use should be North America (simple conic) or Entire World (Mercator).

---

<a id="custom-left-click-behavior"></a>

## Custom Left-Click Behavior

*Source: [`Content/MainDocumentation_HTML/Oneline_Display_Object_CustomActions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Display_Object_CustomActions.htm)*

PowerWorld oneline diagram objects have default behavior of what to do when the object is left-clicked on in Run Mode.

Most oneline display objects do not respond to a left mouse button click while in Run Model. There are a small number of exceptions such as the following

1.  [Circuit Breaker Objects on onelines](12-building-onelines-branches-and-devices.md#circuit-breakers-on-onelines) will change the status the device when left clicked on.

2.  [Generator, Load, and Shunt objects](15-using-onelines-tools-and-options.md#display-object-options) can optionally have a circuit breaker symbol added that when clicked on it will change the device status

3.  [Bus Fields](11-building-onelines-network-objects.md#bus-fields-on-onelines) which show either the Bus Name or Bus Number will respond by opening the Bus View when you click on those fields

4.  [Links to Onelines and Auxiliary Files](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files) provide a way to open another Oneline to a particular Saved View, open and AUX file, or run a script command

5.  [Document Links on Onelines](12-building-onelines-branches-and-devices.md#document-links-on-onelines) provide a way to open a URL address or any kind of file associated with applications on your Windows system

6.  [Memo Text Background objects](#memo-text) have special features for running script commands or load an AUX file which were added in added in December 16, 2024 patch of Version 23

There are some other custom-behavior which can be defined for some display objects

SOToggledField and ScriptCommand

You can customize the left-click behavior in very generic ways for most Display Objects. To do this you must edit special fields of the Display Object that are only available for editing via an AXD file or by accessing fields of the Display Objects using the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display). There are 2 special fields available under the folder**Left click Options** called **SOToggledField** and **ScriptCommand**. These are shown in the image below. If the Display object is linked to an object (such as a generator display object in this example), then the **SOToggledField** is the variablename of a [toggleable field](04-model-explorer-and-case-information-part1.md#colors-and-cell-styles) for the object. When left-clicking on the display object in Run mode this field would then be toggled. Alternatively, you may specify the text of an Auxiliary file script command in the **ScriptCommand** field. When left clicking on the display object in Run Mode this script command would then be executed.

![Oneline Display Object CustomActions](images/Oneline_Display_Object_CustomActions.png)
