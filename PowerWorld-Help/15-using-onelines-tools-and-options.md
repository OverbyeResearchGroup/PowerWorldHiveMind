---
title: "Using Onelines — Tools and Options"
part: "Oneline Diagrams"
chapter_file: "15-using-onelines-tools-and-options.md"
topics: 19
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Using Onelines — Tools and Options

How display objects relate to the power system model; oneline tools, options and custom hints.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (19)**

- [Oneline Diagram Overview](#oneline-diagram-overview)
- [Relationship Between Display Objects and the Power System Model](#relationship-between-display-objects-and-the-power-system-model)
- [Custom Hint Values](#custom-hint-values)
- [Oneline Local Menu](#oneline-local-menu)
- [Oneline Display Options Dialog](#oneline-display-options-dialog)
- [Display Options](#display-options)
- [Pie Chart/Gauge Options](#pie-chartgauge-options)
- [Animated Flows Options](#animated-flows-options)
- [Thumbnail View](#thumbnail-view)
- [Thumbnail View Options Menu](#thumbnail-view-options-menu)
- [Display Object Options](#display-object-options)
- [Substation Display Options](#substation-display-options)
- [Oneline Animation](#oneline-animation)
- [Copying Onelines to Other Programs](#copying-onelines-to-other-programs)
- [Display Objects Case Information Display](#display-objects-case-information-display)
- [Unlinked Display Objects](#unlinked-display-objects)
- [All Display Objects](#all-display-objects)
- [Supplemental Data](#supplemental-data)
- [Movie Maker](#movie-maker)

---

<a id="oneline-diagram-overview"></a>

## Oneline Diagram Overview

*Source: [`Content/MainDocumentation_HTML/Oneline_Diagram_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Diagram_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The purpose of the oneline diagram is to show information about the power system graphically. Such displays are called oneline diagrams (onelines) because the actual three-phase power system components are represented using a single line. Simulator onelines "come alive" via:

  - [Animation](#oneline-animation)
  - [Contouring](17-oneline-view-printing-and-contouring.md#contouring)
  - [Zooming and panning](17-oneline-view-printing-and-contouring.md#oneline-zooming-and-panning) capability and
  - [Conditional display of objects](17-oneline-view-printing-and-contouring.md#oneline-conditional-display-of-objects)

Additionally, a key aspect of Simulator is the ease with which it allows the user to examine and modify many of the[objects](https://www.powerworld.com/WebHelpvoid\(0\);) shown on the oneline diagram.

The user may open any number of oneline diagrams, including multiple copies of the same oneline.

---

<a id="relationship-between-display-objects-and-the-power-system-model"></a>

## Relationship Between Display Objects and the Power System Model

*Source: [`Content/MainDocumentation_HTML/Relationship_Between_Display_Objects_and_the_Power_System_Model.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Relationship_Between_Display_Objects_and_the_Power_System_Model.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Display Object:**

An item shown on a oneline diagram. Display objects typically have an associated model object. Examples include buses, transmission lines, transformers, generators and loads. Display objects not associated with a model object are called unlinked objects.

Model Object:

A power system element contained in a case.

A key strength of the Simulator is its ability to allow users to manipulate a power system model graphically. This capability greatly simplifies the work involved in developing or maintaining a power system case for both novice and advanced users. However, it is important to keep in mind the distinction between the[display objects](https://www.powerworld.com/WebHelpvoid\(0\);) shown on the onelines and the actual power system model, consisting of model objects. A key concept is that any number of display objects, including none at all, can be associated with a single model element.

Simulator uses a bus-oriented model. In other words, the model objects are either the buses themselves, objects that are radially attached to a bus (i.e., loads, generators and switched shunts), or objects that join two buses (i.e., transmission lines, transformers or dc lines). As long as there is a one-to-one mapping between display objects and model objects, the distinction between the two could be made entirely transparent to the user.

It is reasonable, and often quite useful, to use more than one display object to represent a single model object. For example, by using the [Conditional display of objects](17-oneline-view-printing-and-contouring.md#oneline-conditional-display-of-objects) feature, two bus display objects could be used on a single oneline to represent the same bus. One bus might be visible over a particular zoom range, while another, with perhaps a different size/thickness, is visible over another range. Alternatively, the same bus could be represented using display objects drawn on separate onelines.

An ambiguity arises when the user uses the Cut command to delete an object. Is he or she deleting just the Display Object or both the Display Object and the Model Object? To alleviate the problem, Simulator prompts you when you are deleting a display object with an associated model object to delete both the Display Object and its associated model object record, delete just the display object, or cancel the delete.

In addition, there is no requirement that model objects have a corresponding display object. Thus, you could use the oneline diagram to show just a fraction of the total system buses and other devices. You can use the [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) menu to view the model objects directly regardless of whether or not they are shown on a oneline.

---

<a id="custom-hint-values"></a>

## Custom Hint Values

*Source: [`Content/MainDocumentation_HTML/Custom_Hint_Values.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Hint_Values.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can be configured to show a short hint string when the mouse is hovered over objects on the oneline diagrams. This hint string will appear in a yellow box as shown below.

![image\\ebx\_-231832791.gif](images/ebx_-231832791_321x214.gif)

This option must be set first by opening the [Simulator Options dialog](10-power-flow-solution-and-options-part1.md#simulator-options) and then going to the **Oneline** category and finally checking the **Show Oneline Hints** . The user may then customize what text and values appear in the hint by choosing **Custom Hint Values** on the **General Options** ribbon group of the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab. These **General Options** are also available on the [Oneline](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.

This brings up a dialog on which customizations are made for each type of display object that can show a hint.

![Custom Hints Values Dialog](images/Custom_Hints_Values_Dialog.gif)

Choose the type of object on the left side of the dialog. With this display object chosen, choose which fields of this dialog you would like to include as part of the custom hint. Click the **Add**, **Remove**, or **Modify** buttons to add, remove, or modify a field to the hint. Click the **Up** and **Down** buttons to change the order in which the fields appear. On the dialog that appears after clicking Add or Modify, you may customize the field with a prefix, modify the digits and decimal points, and specify whether to show the units as a suffix. The Example column shows an example of what text will appear for the hint.

The *Object Identifier* is also available that will appear as the first line of the hint if chosen. To remove this identifier, click the **Remove ID** button. When the object identifier is not being shown the **Remove ID** button caption will change to **Add ID**. Click the **Add ID** button to add the object identifier back to the hint. You may specify the format of the object identifier by setting the **Show Object Identifier with the following Identifier Type** option appropriately.

The **Delay before showing hints (ms)** is to set the milliseconds time that the hint will show up after you hover over an object and the **Delay before hiding hints (ms)** is the milliseconds time before the hints are going to be hide. The **Maximum hint width (pixels)** is the maximum pixels width that the yellow box of the hint will have.

By selecting the **Set Hint Font** a dialog will open to select the font type, font style and size of the text in the hint box. Selecting **Set Font to Window Default** will set the text fonts to the Window defaults values.

The hint customizations are stored with the PowerWorld Binary file (PWB) and in the Windows Registry. The customizations affect all oneline diagrams (including the Bus View and Substation View). The customizations may also be stored in an [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux) for use in moving the customizations between computers and cases. Click the **Save All to Aux File** button to save all these customizations to an Auxiliary File or click the **Load All From Aux File** to load all the custom hints from an Auxiliary File.

---

<a id="oneline-local-menu"></a>

## Oneline Local Menu

*Source: [`Content/MainDocumentation_HTML/Oneline_Local_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Local_Menu.htm)*

The local menu provides access to a number of options and tools directly from the oneline. To display the local menu, position the cursor on an empty portion of the oneline then click the right mouse button. While most options are always available on the popup menu, a few options are only available on the popup menu in run mode.

Find Object on Oneline (Edit and Run Modes)

Displays the Find Object on Oneline tab of the [Zoom, Pan, and Find Objects](14-editing-onelines.md#zoom-pan-and-find) dialog.

Find Text in Oneline (Edit and Run Modes)

Displays the [Find Text on Oneline](52-additional-linked-topics-part1.md#find-text-in-oneline-dialog) dialog.

Oneline Display Options (Edit and Run Modes) 

Displays the [Oneline Display Options](#oneline-display-options-dialog) dialog. This dialog allows you to customize the appearance of the oneline.

Pan/Zoom Control (Edit and Run Modes) 

Displays the Zoom/Pan tab of the [Zoom, Pan, and Find Objects](14-editing-onelines.md#zoom-pan-and-find) dialog.

Edit Screen Layers (Edit and Run Modes) 

Opens the [Screen Layers case information display](14-editing-onelines.md#screen-layers).

Show Layer (Edit and Run Modes)

Allows activation of any saved screen layer.

Save/Edit/Delete View (Edit and Run Modes)

Displays the [Save View Level Dialog](17-oneline-view-printing-and-contouring.md#save-view-level-dialog). This dialog is used to set defined locations on the oneline for recalling specific views from a list of saved views.

Go To View (Edit and Run Modes)

Allows the user to go to a specific location and zoom level on the oneline by choosing from a list of saved views. This option does nothing if no views are saved.

Contouring (Run Mode Only)

Displays the [Contour Options Dialog](17-oneline-view-printing-and-contouring.md#contouring-options). This dialog allows you to contour the system voltage magnitudes or angles.

Difference Case

Displays the [Difference Case Dialog](08-view-case-data-tools.md#difference-case). This dialog is used to compare two power system operating points.

Dynamic Formatting (Active Oneline) (Edit and Run Modes in Oneline Diagrams)

Displays the [Dynamic Formatting Dialog](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog). This dialog is used to change the rendering of objects in oneline diagrams according to the state of the represented object in the power system.

Dynamic Formatting (All Views) (Edit and Run Modes in Bus and Substation Views)

Displays the [Dynamic Formatting Dialog](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog). This dialog is used to change the rendering of objects in bus and substation views according to the state of the represented object in the power system.

All Display Objects (Edit and Run Modes)

Opens the [Display Object case information display](#display-objects-case-information-display), showing all the objects contained in the oneline diagram.

Only Selected Display Objects (Edit Mode Only)

Opens the [Display Object case information display](#display-objects-case-information-display), showing only the currently selected objects in the oneline diagram, by automatically checking the **Show Only Objects Selected on Display** box.

Load Display Auxiliary File (Edit and Run Modes)

Loads a [display auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux).

Print Oneline (Edit and Run Modes)

Sends a copy of the oneline diagram to the printer. Selecting this option has the same affect as selecting **File, Print Oneline** from the main menu. See [Printing Oneline Diagrams](17-oneline-view-printing-and-contouring.md#printing-oneline-diagrams) for more information.

Copy Image to Clipboard (Edit and Run Modes)

Copies the oneline file into the Windows clipboard using the Windows Metafile format (\*.wmf). You can then paste the oneline into another program, such as a word processor. See [Copying Onelines to Other Programs](#copying-onelines-to-other-programs) for details.

Export Image to File (Edit and Run Modes) 

Saves a copy of the entire oneline diagram image to a file. Oneline image files can be saved in bitmap (\*.BMP), Windows Metafile (\*.WMF, \*.EMF), JPEG (\*.jpg), or GIF format (\*.gif).

Toggle Full Screen (Run Mode Only)

Sets the oneline diagram display window to full screen size. This option hides all toolbars and status bars. To return the window to normal, right-click on the oneline diagram and un-check the Full Screen option.

Embed a Display (Run Mode Only)

Clicking on this option allows you to open another oneline diagram (or the same one) and embed the new display inside the existing display. You can choose what percentage size the embedded display should be, and where within the existing window the embedded window should be placed.

Form Control \> (Edit and Run Modes)

Options on this submenu allow you to resize the window, shift the window, or close the window.

---

<a id="oneline-display-options-dialog"></a>

## Oneline Display Options Dialog

*Source: [`Content/MainDocumentation_HTML/Oneline_Display_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Display_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Oneline Display Options dialog allows you to customize the display of the oneline diagram. You can access this display by right-clicking anywhere on an empty portion of a oneline and selecting **Oneline Display Options** from the resulting [oneline local menu](#oneline-local-menu).

This dialog can also be display by going to the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab and choosing **Oneline Display Options** from the **Oneline Options** ribbon group.

This dialog houses pages that govern various aspects of the oneline display. See [Animated Flows](#animated-flows-options), [Display Object Options](#display-object-options), [Display Options](#display-options), [Grid/Highlight Unlinked Objects](14-editing-onelines.md#gridhighlight-unlinked-objects), [Geography/Coordinates](16-oneline-gis-tools.md#geographycoordinates), [Memo](01-getting-started.md#memo-display), [Pie Charts / Gauges](#pie-chartgauge-options), [Thumbnail View](#thumbnail-view), or [Substations](#substation-display-options) for information on the respective tabs. Older versions of Simulator used to support a movie maker tool useful with the onelines. See the [Movie Maker](#movie-maker) topic for suggestions on what tools to use instead.

Save Options to Case

Of important note is the general option at the bottom of this dialog labeled **Save Options to Case**. What this allows you to do is define a set of oneline options in the dialog, and then save that definition of options *in the case* by giving the definition a name. Once you have named that set of options, you can recall it later by coming back to this dialog and choosing the name from the list of option set names that appears near the bottom of the dialog. You can define as many different sets of custom options as you wish. You can also use an option set saved with the case when you create a oneline view using the [Save Views](17-oneline-view-printing-and-contouring.md#save-view-level-dialog) dialog.

Also note that once you have defined these sets of Saved Oneline Options, you can then quickly apply them to the active oneline diagram by using the **Saved Options Menu** on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab.

---

<a id="display-options"></a>

## Display Options

*Source: [`Content/MainDocumentation_HTML/Display_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Display_Options.htm)*

The Display Options page is found on the [Oneline Display Options](#oneline-display-options-dialog) dialog. This page contains the following option settings:

Display Detail

The Display Detail box allows you to control how much information is shown on the oneline display. This option is available only in run mode. All elements on a oneline diagram are automatically visible in edit mode. There are four choices for run mode detail filtering:

**Minimal** Show the oneline background, branch circuit breakers, generator MW output, and load MW/MVR.

**Moderate** Show all Minimal information, along with bus voltages and all line flow pie charts.

**Complete** Show all information.

**Custom **Selecting this option and then clicking the **Set…**button opens the Custom Detail Dialog, which allows you to customize the oneline diagram to hide objects that do not meet your desired specifications. This dialog looks and works very similar to the [Select By Criteria](14-editing-onelines.md#select-by-criteria-dialog) tool, allowing you to choose objects filtered by area, zone, voltage, and screen layer.

Of course, in order for a certain display object to appear, it must have been placed there by the person who designed the oneline.

Emphasize Specific Objects

This option allows you to choose to "emphasize" desired elements on a oneline diagram. The emphasis is in the form of the emphasized elements being in full color, with de-emphasized elements being muted colors.

To choose emphasis of certain elements, first check the box labeled **Do Emphasis**. When you first check this box, it will open the Emphasis Filter dialog, which looks and works very similar to the [Select By Criteria](14-editing-onelines.md#select-by-criteria-dialog) tool. You can choose the oneline elements you wish to emphasize, and include filtering by area, zone, voltage, and screen layer.

The degree of emphasis (muting of de-emphasized elements) can be controlled by the **Emphasis Amount** slide bar.

Background Color

Select **Change Background Color** to select a different color for the oneline diagram background color. Select the **Set as Default Background Color** option to set the background color as the default for all oneline diagrams.

Use Absolute Values for MW Line Flows

If checked, this option will cause all MW flow text fields for lines to be displayed as the absolute value of the flow. Otherwise, the MW flow text fields will be positive near the source end of the line and negative near the sink end of the line. The value of this option is stored in the system registry, and will be used by bus view and substation view diagrams when a oneline diagram with saved oneline options is not available.

Use Absolute Values for Mvar Line Flows

If checked, this option will cause all Mvar flow text fields for lines to be displayed as the absolute value of the flow. Otherwise, the Mvar flow text fields will be positive near the source end of the line and negative near the sink end of the line. The value of this option is stored in the system registry, and will be used by bus view and substation view diagrams when a oneline diagram with saved oneline options is not available.

Use Absolute Values for MW Interface Flows

If checked, this option will cause all MW flow text fields for interfaces to be displayed as the absolute value of the flow. Otherwise, the MW flow text fields will be positive near the source end of the interface and negative near the sink end of the interface. The value of this option is stored in the system registry, and will be used by bus view and substation view diagrams when a oneline diagram with saved oneline options is not available.

Enable Mouse Wheel Zooming

When this box is checked, zooming can be done with a mouse wheel. The default is off.

This option applies to all onelines instead of just the presently selected oneline.

Show Oneline Hints

When this box is checked, hovering the cursor over an object will briefly display information about the object in a popup hint.

This option applies to all onelines instead of just the presently selected oneline.

Visualizing Out-of-Service Elements

Out-of-service elements can have optional visualization settings that makes them "stand out" in relation to in-service devices on the oneline diagram. The options for out-of-service devices includes **Use Dashed Lines**, **Draw and X Through Off-Line Generators**, and **Blink**. Additional controls for the Blink option are available, for setting the blink interval and color. Any combination of these options can be used for out-of-service elements, although the **X** option only applies to out-of-service generators.

Browsing Path for Oneline Diagrams

This option applies when you have [Oneline Links](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files) included on a oneline diagram. Rather than specify the full path and name of a oneline diagram as a oneline link, you can specify the file name only. When the link is clicked in Run Mode, Simulator will check all directories listed here, in order, to try and find the oneline file name stored with the link.

---

<a id="pie-chartgauge-options"></a>

## Pie Chart/Gauge Options

*Source: [`Content/MainDocumentation_HTML/Pie_Chart_Gauge_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Pie_Chart_Gauge_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The options listed below are found on the [Oneline Display Options dialog](#oneline-display-options-dialog).

Show Pie Charts/Gauges in Run Mode

When this option is checked, the pie charts and line gauges will be visible during Run Mode. Otherwise, they will be visible only during Edit Mode.

Only Show Pie Charts/Gauges if relevant data exists

The relevancy of pie charts and gauges depends on the style of the pie chart or gauge. For MVA, MW, Mvar and Amp styles, the pie charts are considered irrelevant if the limits on the line or interface are 0. For max percent loading under contingency, the pie chart is irrelevant if no violation(s) under contingency occurred on the element. For the PTDF style, the pie chart is invalid if the PTDF value has not been calculated for the line or interface.

The options for pie charts and gauges are split into four sections, discussed in the additional topics:

[Pie Charts/Gauges: Lines](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-lines)

[Pie Charts/Gauges: Interfaces](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-interfaces)

[Pie Charts/Gauges: Pie Chart/Gauge Styles](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-pie-chartgauge-styles)

[Pie Charts/Gauges: General Options](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-general-options)

Many of these same options are available on the Pie Chart menu found on the [Options ribbon tab](02-simulator-ribbon.md#options-tab-overview).

![Pie Chart Ribbon Options](images/Pie_Chart_Ribbon_Options.gif)

---

<a id="animated-flows-options"></a>

## Animated Flows Options

*Source: [`Content/MainDocumentation_HTML/Animated_Flows_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Animated_Flows_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The fields on the Animated Flows page of the [Oneline Display Options](11-building-onelines-network-objects.md#oneline-display-options) dialog are used to customize the appearance of the animated flows on the oneline diagram.

Show Flow Symbols

Determines whether power flows are animated on the onelines. If this option is not checked, then no flow symbols appear on the oneline.

Show Flows On

Allows you to choose whether or not to display animated flows individually on Branch, Load, Generator and Shunt objects. Uncheck the box(es) for the objects that you do not wish to display animated flows.

Base Flow Scaling on

Animated flows on onelines may depict either actual power flows or [power transfer distribution factors](20-sensitivities.md#power-transfer-distribution-factors), depending on what you choose here. You can also choose to animate both the MW and MVAR flows or the MW and PTDF flows simultaneously. The Custom Float 1 option allows user specification of a value to depict in the flow animation. To use this option, values should be entered in the Custom Floating Point 1 field for the appropriate devices.

Animate

This option determines whether or not the flow arrows are mobile or stationary on the oneline diagram. **** Unchecking this box will cause the flow arrows to remain stationary on the diagram.

Scale Speed of Flow

Checking this box will cause the arrows to flow at a speed proportional to the represented quantity. When it is not checked, all of the flows will be at the same speed.

Scale Size of Flow 

If checked, the size of the animation symbols will vary to represent the magnitude of flow on the element (respective of the **Animation Parameter**.) Otherwise, the symbol size will be the same on all devices regardless of the magnitude represented.

Reset Animated Flow Offsets

This button allows the user to reset the animated flows to start at a specified offset position. Mostly this would be used to reset the offset to 0, which would cause the animated flows to start at the beginning of the line or element. Since the animation moves the flow arrows every time the load flow is resolved, resetting flows to a specific offset could be useful for comparing different load flow solutions by looking at differences in the animated flow objects.

Set Size, Density, and Reference Values for this oneline

Simulator detects the current zoom level and object parameters of the selected oneline diagram, and automatically adjusts the animation settings in an attempt to optimize the animation quality.

Size

Determines the relative size of the animated flows on the devices. Increasing this number increases the size of the flow symbols. This field may range from 1 to 999.

Density

Determines the relative density of the animated flows on the devices. Increasing this value causes Simulator to display a greater number of flow symbols per unit distance on the oneline. This value may range from 1 to 999.

Scaling Based on 

Determines whether the size and speed of animated flows represent actual flow or percentage loading. This option applies only to transmission lines and transformers as flows on other devices, such as loads and generators, always represent actual flow.

Max. Zoom Level to Scale Size

As a oneline is zoomed, the animated flow symbols increase in size. The value of Max. Zoom Level to Scale Size caps the size of the animated flows so that zooming beyond this level results in no further increase to the size of the flow symbols.

Maintain Density above Maximum Zoom Level

As a oneline is zoomed, the animated flow symbols decrease in density. Checking this box maintains the density of the animated flows after the maximum zoom level has been reached.

Minimum Size in Pixels for In-service Elements

Allows the specification of a minimum size for the animated flow objects for power systems elements that are in-service. The flow objects are sized based on the flow through the element. For elements with very small flows, it is often difficult to see the flow objects, and the minimum size can be set to make these flow objects more visible. The larger the minimum size value becomes, the more uniform the flow objects will become as elements are no longer sized based on their actual flow but rather the minimum size.

Reference Values for Scaling

Maximum flow reference for sizing the animated flows. The lower the MVA reference, the larger the animated flows appear on the oneline diagram as the actual flow value is compared to the reference value for scaling.

Symbol Shape

Simulator can display animated flows using directional arrows, circles, squares, or triangles.

Animation Rate

If the oneline animation is too fast or too slow, the animation rate can be adjusted by moving the slide bar.

Symbol Fill Color 

Shows the fill color used for the animated flows if **Use Fill Color** is checked. Double-click on these fields to change the colors of the six different types of animated flows.

Use Fill Color

Checked if animated flow symbols should be filled using the **Fill Color**.

Show PTDF Counter Flow

Check this option if you wish for PTDF values that are in the opposite direction of the actual flow to be displayed using a different symbol color when visualizing PTDFs.

Many of these same options are available on the Animation Menu found on the [Options ribbon tab](02-simulator-ribbon.md#options-tab-overview).

![Animated Flow Ribbon Options](images/Animated_Flow_Ribbon_Options.gif)

---

<a id="thumbnail-view"></a>

## Thumbnail View

*Source: [`Content/MainDocumentation_HTML/Thumbnail_View.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Thumbnail_View.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The thumbnail view allows the user to see an overview of the oneline diagram in a smaller window in a specified location on the oneline diagram. The thumbnail view is useful when the user has zoomed in to a specific area of the oneline diagram, but still wants to see what part of the system they are observing on a larger scale as they pan around the diagram. The other application is to observe a more detailed part of the system in the thumbnail view as the user moves the cursor over the oneline diagram. The thumbnail view is not visible by default, but can be set up and displayed from the [Oneline Display Options](#oneline-display-options-dialog) dialog. The options for the thumbnail view are:

Show ThumbNail View

If checked, the thumbnail view will be visible in the specified corner of the oneline diagram.

Size of ThumbNail View

The size of the thumbnail view as a percentage of the size of the oneline diagram.

Zoom level of Thumbnail View

The amount to multiply the oneline diagram zoom level for display in the thumbnail view. The higher the multiplier, the more of the diagram you will see in the thumbnail view. You can instead indicate that the thumbnail view should display the diagram at a specified zoom level rather than a dynamically scaled zoom level based on the current diagram's zoom level.

Location

Choose the location on the oneline diagram in which the thumbnail view is to appear.

Border Width in Pixels

The pixel thickness of the border around the thumbnail view.

Background Color

If **Use One-line Background Color** is checked, the thumbnail background color will be the same as the oneline diagram. If it is not checked, then a different thumbnail background color can be selected by clicking on the colored box next to the **Use Custom Background Color** label.

Thumbnail view follows mouse cursor

This setting is very useful when is combined with the Zoom Level. Using a low multiplier and checking the Thumbnail view follows mouse cursor box will show a more detailed part of the system over which the cursor is being moved.

Percent Transparent

This setting allows you to make the thumbnail window completely opaque, completely transparent, or some measure in between. The more transparent the thumbnail window, the more detail of the underlying oneline diagram is visible through the thumbnail window.

Many of these same options are available on the [Thumb Nail](#thumbnail-view-options-menu) options menufound on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab.

---

<a id="thumbnail-view-options-menu"></a>

## Thumbnail View Options Menu

*Source: [`Content/MainDocumentation_HTML/Thumbnail_View_Options_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Thumbnail_View_Options_Menu.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Thumbnail View Options quick menu provides access to most of the options contained in the [Thumbnail View Options](#thumbnail-view) dialog in an individual manner through menu commands. Select the **Thumb Nail** option from the **Oneline Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab to access the menu.

![Thumb Nail Menu](images/Thumb_Nail_Menu.gif)

This quick menu contains the following default buttons, in order from top to bottom:

  - Show thumbnail on the screen
  - Thumbnail location on the screen
  - Size of Thumbnail View, as a percentage of the window size
  - Zoom out type (divide or zoom level)
  - Zoom out factor, defining the ratio of the diagram seen in the thumbnail relative to what is visible in the diagram itself.
  - Enable/Disable Thumbnail View to follow mouse cursor
  - Enable/Disable Using the Same Background as the main window
  - Background Color, if not the same as the main window
  - Line width of the border around the thumbnail window

---

<a id="display-object-options"></a>

## Display Object Options

*Source: [`Content/MainDocumentation_HTML/Display_Object_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Display_Object_Options.htm)*

The Display Object Options page is found on the [Oneline Display Options](#oneline-display-options-dialog) dialog. This page contains options for formatting various display objects, displaying circuit breakers on loads, generators, and switched shunts, and formatting circuit breakers for transmission branches.

General Options (All) Tab

Percent of Injection Group/Owner object height used by name

This option allows the user to specify the height of the name with respect to the rectangle of the injection group graphical objects.

Display Circuit Breakers in Generators, Loads and Switched Shunts

Uncheck this box to hide circuit breakers from appearing in generators, loads, and switched shunts. If this option is checked, the user can use **Display breakers on…** to select individually what elements can display circuit breakers.

These options dictate only if circuit breakers will be shown on elements that are closed, i.e. Status = *Closed* for the individual element. Circuit breakers will always be shown for devices that are open, i.e. Status = *Open* for the individual element. This is useful in identifying possible data errors especially for cases where breakers are explicitly modeled. In these cases, the explicitly modeled breakers are used to open and close generators, loads, and switched shunts rather than changing the Status of the device. An open circuit breaker symbol at the individual elements would then indicate that the Status of the device needs to be set to *Closed*.

Circuit Breaker Size ScalarAdded in version 23 patch on April 19, 2024

Change this scalar to make the circuit breakers on loads, generators, and shunts larger or smaller. A value of 1.000 is the traditional size.

Transformer Symbol

This option allows the selection of *Coils* or *Circles* to represent a transformer. This option allows a different specification of how transformers should be displayed for each individual oneline diagram. There is also an option that is applied by default for all onelines. Use the *Default* selection to use the setting found with the [Simulator Options: Oneline](10-power-flow-solution-and-options-part2.md#oneline-options) options.

Display Rotors in Generators

Uncheck this box to hide the rotors of the generators.

The shape of the rotor can be changed by using the Rotor Shape option found with the [generator display options](06-object-properties-edit-mode-part1.md#display) on the generator dialog in Edit mode or the Shape option found on the [Display/Size tab](14-editing-onelines.md#other-display-object-properties) of the [Format Multiple Objects dialog](14-editing-onelines.md#format-selection-dialog).

Change in Gen Rotor Angle per Refresh (degrees)

This value specifies the change in the rotor angle every time the animated flows refresh. This means that the greater the angle value, the faster the rotor will seem to rotate when the oneline is animated. Entering a negative number will cause the rotor to spin counter-clockwise.

Show Field Inside Generator

Fields can be shown inside generator objects. Select a field from the drop-down box or use the Find button to search through the list of fields available for a generator. Set the field to *No Field* to not display any field inside generator objects. Set the **Digits** and **Decimals** for floating point fields. Adjust the **Relative Font Size** to change the size of the font relative to the generator object size. To ensure that the field fits entirely inside each generator object, check the option to **Dynamically decrease the font size so that the field fits inside the generator**.

Multi-Section Line Display Objects

**Intermediate Bus Rotation Angle**

Normally, the intermediate buses are perpendicular to the line. The value entered here can rotate the intermediate bus with respect to the original position. Therefore, a value of 0 degrees, will keep the intermediate buses perpendicular to the line, while a value of 90 degrees will set the intermediate buses aligned to the line.

**Intermediate Bus Relative Size**

This option is actually a multiplier for the size of the intermediate buses specified for each multi-section display object.

Bus Field Voltage Option

This option allows the user to specify in which units the bus fields with *Bus Voltage* as type of field will be displayed. This setting is only valid when the type of field selected is *Bus Voltage* in the [Bus Field Information](06-object-properties-edit-mode-part1.md#bus-field-information) dialog. Choosing a voltage field in the Select Field will return the voltage value in the specific units of the field.

Circuit Breakers Tab

Circuit Breaker Display Objects \> Normally Closed 

This section is used to specify the colors for all the circuit breakers normally closed in the oneline diagram. The colors that can be modified are the border and fill colors for presently closed and open circuit breakers. In order to change a color, click on the color box or on the **Change** button. Check **Use** **Fill** to use the specified fill color.

Circuit Breaker Display Objects \> Normally Open

This section is used to specify the colors for all the circuit breakers normally open in the oneline diagram. The colors that can be modified are the border and fill colors for presently closed and open circuit breakers. In order to change a color, click on the color box or on the **Change** button. Check **Use** **Fill** to use the specified fill color.

Shape

Specify the shape of circuit breakers on transmission lines and transformers. The breakers shown on loads, generators, and switched shunts will always be the default rectangle shape.

---

<a id="substation-display-options"></a>

## Substation Display Options

*Source: [`Content/MainDocumentation_HTML/Substation_Display_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Display_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Substations** tab of the [Oneline Display Options](#oneline-display-options-dialog) dialog provides parameters for customizing the appearance of [Substation](11-building-onelines-network-objects.md#substation-display-objects) display objects. This tab is only available if the case contains at least one substation.

The upper right-hand corner of the Substation page displays a template of the substation object’s appearance in terms of locations or "zones" where information can be displayed on the object. The rest of the page can be used to describe the appearance of the object and the information that appears in the substation objects.

Upper % of Height

This percentage indicates how much of the object is populated by the "upper" zone of the object. This includes the *Upper Field*, *Upper Left (UL)* and *Upper Right (UR)*. As you decrease this percentage, the upper zone will get smaller, increasing the Identifer (middle) zone automatically, and vice-versa if you increase the percentage of the upper zone.

Identifier % of Height

This is the percentage of the height of the substation object that is occupied by the identifier or "middle" zone. This is the substation identifier section of the object.

Lower % of Height

This is the percentage of the substation object that is occupied by the "lower" zone of the object. This includes the *Lower Field*, *Lower Left (LL)* **** and *Lower Right (LR)*. Unlike the previous two percentages, this percentage cannot be directly modified. Instead, it is automatically determined based on the settings of the *Upper* and *Identifier* percentages.

Left % of Width

This percentage indicates how much of the object is populated by the "left" zone of the object. This includes the *Upper Left (UL) and Lower Left (LL)*. As you decrease this percentage, the left zone will get smaller, increasing the Identifier (middle) zone automatically, and vice-versa of you increase the percentage of the left zone.

Identifier % of Width

This is the percentage of the width of the substation object that is occupied by the identifier or "middle" zone. This is the substation identifier section of the object.

Right % of Width

This percentage indicates how much of the object is populated by the "right" zone of the object. This includes the *Upper RIght (UR) and Lower Right (LR)*. As you decrease this percentage, the right zone will get smaller, increasing the Identifier (middle) zone automatically, and vice-versa of you increase the percentage of the right zone.

Buffer Percent

The buffer width for the height settings provide a buffer zone of the percentage width specified horizontally between the Identifier section and the upper / lower field sections. Similarly, the buffer width for the left and right width fields indicates a percentage buffer vertically between the upper / lower field zones and the four corner zones.

Substation Identifier

Choose how the identifier will be displayed for the substation. Choose to display by name, by number, or by combinations of name and number. The identifier will be displayed in the *Identifier* or "middle" zone of the substation object.

Shape

Select the shape used for substations that are not overriding the [Substation Layout Settings](14-editing-onelines.md#other-display-object-properties).

What should be done when identifier text does not fit inside the width

As the name of this option suggest, you can choose how the text in the identifier section of the object should be modified if resizing of the substation object causes the text to be too large for the modified size.

Extra Substation Fields

These four fields, two of which are represented as the *Upper Field* and *Lower Field* on the template, can be customized to display any substation field of your choosing. Use the drop-down arrow of the appropriate box to choose a field, or use the Find button to pull up a list of fields to choose from. Once the field has been chosen, set the digits and number of decimal places for the field. Also check *Units?* to show the units if the extra fields.

Upper-Left Symbol (UL)

Choose what symbol to display in the upper-left zone of the substation object. You can choose from None, Switched Shunt, Generator, Number of Buses, and Load. If the substation contains at least one type of the chosen object, a symbol representing that type of object will be displayed in the Upper-Left location of the object to indicate such a presence. By default, the Upper-Left zone will display the Generator symbol.

Upper-Right Symbol (UR)

Choose what symbol to display in the upper-right zone of the substation object. You can choose from None, Switched Shunt, Generator, Number of Buses, and Load. If the substation contains at least one type of the chosen object, a symbol representing that type of object will be displayed in the Upper-Right location of the object to indicate such a presence. By default, the Upper-Right zone will display the Load symbol.

Lower Left Symbol (LL)

Choose what symbol to display in the lower-left zone of the substation object. You can choose from None, Switched Shunt, Generator, Number of Buses, and Load. If the substation contains at least one type of the chosen object, a symbol representing that type of object will be displayed in the Lower-Left location of the object to indicate such a presence. By default, the Lower-Left zone will display the number of buses in the substation.

Lower-Right Symbol (LR)

Choose what symbol to display in the lower-right zone of the substation object. You can choose from None, Switched Shunt, Generator, Number of Buses, and Load. If the substation contains at least one type of the chosen object, a symbol representing that type of object will be displayed in the Lower-Right location of the object to indicate such a presence. By default, the Lower-Right zone will display the Switched Shunt symbol.

---

<a id="oneline-animation"></a>

## Oneline Animation

*Source: [`Content/MainDocumentation_HTML/Oneline_Animation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Animation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

An important feature of PowerWorld Simulator is its support of animated onelines. The use of efficient display algorithms allow animation rates that are typically greater than several times per second, even on large cases and on onelines with a significant number of objects. The extensive use of animation makes the display "come alive" so that system conditions can be ascertained more easily.

In Simulator, animation is started from Run Mode by selecting the **Play** button in the **[Power Flow Tools](02-simulator-ribbon.md#simulation-control)** ribbon group**** on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab. In Viewer, animation is started automatically when you load a case.

The animation can be controlled and customized from the [Animated Flows Tab](#animated-flows-options) of the [Oneline Display Options](#oneline-display-options-dialog) dialog. To access this dialog, select **Oneline Display Options** from the **Oneline Options** ribbon group**** on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab, or right-click on an empty area of the oneline diagram and select **Oneline Display Options** from the resulting [local menu](#oneline-local-menu).

---

<a id="copying-onelines-to-other-programs"></a>

## Copying Onelines to Other Programs

*Source: [`Content/MainDocumentation_HTML/Copying_Onelines_to_Other_Programs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Copying_Onelines_to_Other_Programs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The onelines can be easily copied to other programs. This allows you to add PowerWorld onelines to your word processor documents or slide presentations. The simplest way to copy a oneline diagram to another program is to use the Windows Clipboard. This is accomplished as follows:

  - In Simulator or Viewer, zoom and/or pan the display to the portion of the oneline diagram you would like to copy.
  - Right-click on an empty portion of the oneline to display the [local menu](#oneline-local-menu).
  - Select **Copy** **Image** **to Clipboard** menu item. This places a copy of the oneline into the Window's clipboard.
  - In the other program, use **Paste** or **Paste Special** to copy the contents of the clipboard into that program. The oneline is pasted into the program using the Metafile format.

In addition, oneline diagrams can also be [saved as image files](03-cases-files-and-formats.md#exporting-onelines-in-different-graphic-formats) by right-clicking on an empty portion of the diagram and choosing **Export Image to File**.

---

<a id="display-objects-case-information-display"></a>

## Display Objects Case Information Display

*Source: [`Content/MainDocumentation_HTML/Display_Objects_Case_Information_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Display_Objects_Case_Information_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Display Objects case information display presents data describing each graphical object in the oneline diagram. This display functions in the exact same manner as the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) and is thus called the **Display Explorer** instead. The Display Explorer contains [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) from which you can print, copy, and modify its records as well as view the information dialog of its associated power system object if it has any. You can also sort the object records by clicking on the heading of the field by which you want to sort. Additionally, when Simulator is in [Edit Mode](01-getting-started.md#edit-mode-introduction), the toolbar **Records** menu allows you to remove existing objects from the oneline diagram.

To show the Display Objects case information display, go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group select **List Display** **\>** **All Display Objects**.

As mentioned above, the Display Explorer functions identically to the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The only differences in functionality are due to additional options found on the bottom left of the dialog. This offers the following additional features.

Show Only Objects Selected

By checking this box, only the selected display objects currently selected in the oneline diagram will be shown.

How to List Grouped Objects

This specifies how to list grouped objects if there are any in the oneline diagram. The choices are to list individually the components of the group, to list only the groups, or to list both the individual elements and the groups. If there are not grouped objects in the oneline diagram, this control is disabled.

Save Complete Display to AXD

By clicking this button, all the objects that are shown in the case information display will be saved to a [display auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux).

By default, the display object records case information display contains the following fields:

Type

The type of display object.

X/Longitude Location, Y/Latitude Location

The x and y coordinates of the object’s location.

Center X/Longitude Location, Center Y/Latitude Location

The x and y center coordinates of the center location of an object. Changing these values will update the X/Longitude and Y/Latitude fields.

Layer Name

The layer name to which the display object is assigned.

Layer Shown, Selectable in Edit Mode, Low Zoom Level, High Zoom Level

These fields only display information about the layer to which the display object belongs. Therefore, the values for these fields can only be modified through the [Screen Layer case information dialog](14-editing-onelines.md#screen-layers) or the [Screen Layer dialog](14-editing-onelines.md#screen-layer-options).

Anchored

This field indicates whether or not the display object is an [anchored object](11-building-onelines-network-objects.md#anchored-objects). If the display object can not be an anchored object, then the field is empty.

Font Size

For text objects, this field shows the font size.

---

<a id="unlinked-display-objects"></a>

## Unlinked Display Objects

*Source: [`Content/MainDocumentation_HTML/List_Unlinked_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/List_Unlinked_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

An unlinked object is a display object not linked to a record in the power system model (model object). The existence of unlinked display objects on a oneline diagram can be misleading because they have zero flows and zero bus voltages associated with them. See [Object Relationships](#relationship-between-display-objects-and-the-power-system-model) for more information.

Go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **List Display** **\>** **Unlinked Display Objects** from the main menu in Edit Mode to identify unlinked objects.

![List Unlinked Display Objects Dialog](images/List_Unlinked_Display_Objects_Dialog.gif)

Unlinked Display Objects Dialog

Total Number of Unlinked Display Objects

Indicates the total number of unlinked objects on the display. Ideally, this number should be zero. If nonzero, the unlinked objects are identified in the table by type, screen location, and zoom range over which the object is visible.

Delete Unlinked Objects

Click on this button to permanently remove all unlinked objects from the display. Exercise this option carefully. Generally, you will want to do this either when you have substantially modified a power flow case, such as by creating an equivalent, or when you are using the oneline with a new power system case.

View Options for Highlighting Unlinked Objects on the Oneline

Click on this button will open the [Grid/Highlight Unlinked Objects](14-editing-onelines.md#gridhighlight-unlinked-objects) tab of the [Oneline Display Options Dialog](#oneline-display-options-dialog).

Type, X/Y Location

The remainder of the display shows the type, location, identification, layer, applicable zoom level, anchored property, and font size for each unlinked object. This table is a type of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus behaves similarly to all other case information displays. Right-click on a record in this table to invoke the local menu. Select **Pan** **to Object on Open Onelines** **** to locate and select the unlinked object on the oneline diagram.

---

<a id="all-display-objects"></a>

## All Display Objects

*Source: [`Content/MainDocumentation_HTML/All Display Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/All Display Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This display works in the exact same manner as the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) and is thus called the [Display Explorer](#display-objects-case-information-display) instead. This show all of the Display Objects information.

---

<a id="supplemental-data"></a>

## Supplemental Data

*Source: [`Content/MainDocumentation_HTML/Supplemental_Data.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Supplemental_Data.htm)*

Supplemental Data can be used to identify display objects that do not represent power system elements. User defined data types can be created and linked to display objects for use in filtering, dynamic formatting, Select by Criteria, and custom hints.

Supplemental Classification Definition

A Supplemental Classification is used to group Supplemental Data records into categories. As an example, if using Supplemental Data records to identify geographical borders, a Supplemental Classification could be *Country*. Each Supplemental Data record uses exactly one Supplemental Classification record.

Supplemental Classification records are defined by one key field: Classification. The remaining fields are all optionally specified and can be used for creating user-defined groups for reporting purposes.

<table>
<tbody>
<tr class="odd">
<td><p>Classification</p>
<p>This field uniquely identifies the classification and cannot be blank.</p>
<p>Contain</p>
<p>Comma-delimited list of object types that are contained by Supplemental Data of this Classification.</p>
<p>Assign</p>
<p>Comma-delimited list of object types that can be assigned to Supplemental Data of this Classification.</p>
<p>Multiple</p>
<p>If YES, An object can belong to more than one Supplemental Data of this Classification.</p>
<p>Inherit</p>
<p>Set to YES to allow objects to inherit which supplemental data they are contained by from the model structure. For example, if a classification only is assigned buses, you may want a generator to inherit from its terminal bus which supplemental data it belongs to. The Inheritance hierarchy is as shown to the right. For example, a Gen will look to its Bus, then Substation, any Injection Group it belongs to, any interface, and so on. Once it finds a hierarchy level at which a supplemental data object has been assigned, then it will act as though it belongs to all Supplemental data objects at that level.</p>
<p>Description</p>
<p>This is just a string that is a user description of this Classification</p>
<p>ObjectType</p>
<p>Object Type: this is what will be used in AUX files as the field names to assign objects to a SupplementalData objects of this classification. It is the same as the classification name, but all spaces are removed and all of the following characters are replaced by an underscore \/:*?"&lt;&gt;',|. (so really just don't use these characters).</p></td>
<td><p><img src="images/SupplementalData_Contained_Inheritance.png" alt="SupplementalData Contained Inheritance" /></p>
<p> </p></td>
</tr>
</tbody>
</table>

Supplemental Data Definition

Supplemental data records are defined by two required key fields:

**Classification**

This is the Supplemental Classification Name. This field cannot be blank.

**Name**

This is a unique identifier used to further define the Classification. If using supplemental data records to identify geographical borders, the Name could be *United States* to go with a Classification of *Country*. This field cannot be blank.

In addition to the Classification and Name, geographic information, expressions, and custom strings, integers, and floating point values can be assigned to supplemental data records. This information can be entered in the Supplemental Data Case Information Display discussed below.

Displaying Supplemental Data Records

Supplemental Data records are displayed in the Supplemental Data Case Information Display found on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) under **Case Information and Auxiliary \> Supplemental Data**. This display consists of two tabs, **Supplemental Classification** and **Supplemental Data**. The table on the Supplemental Classification tab lists all of the Classifications that have been defined. The table on the Supplemental Data tab lists all of the Supplemental Data records that have been defined and provides the means for creating new Supplemental Data records AND Supplemental Classification records. Supplemental Classification records cannot be created under the Supplemental Classification tab.

Creating Supplemental Data Records

To create a new Supplemental Data record, from the **Supplemental Data** tab, right-click on the table and choose **Insert** from the local menu. The **Define Supplemental Data** dialog will open.

![Define Supplemental Data Dialog](images/Define_Supplemental_Data_Dialog.gif)

Either select an existing **Classification** from the drop-down box or create a new Classification by clicking **New**. (If creating a new Classification,another dialog box will open with a prompt for the Classification Name.) Type in a **Name** for the record. To create the record and close the dialog click ****OK**. To create the record without closing the dialog click **Save**.To exit the dialog without creating the record click **Cancel**.**

Assigning Objects to a Supplemental Data Definition

If Supplemental Classification objects are created to allow Contain and Assign types, then additional fields will appear on the related object types. The fields will appear in a folder called Supplemental Data and the field names will start with the Name of the Classification.

**Classification Name**

Lists all of the Supplemental Data to which an object belongs. Field is available for any object types that can be contained in or assigned to Supplemental Data.

**Classification Name Append**

Add the name of new Supplemental Data to which an object is assigned. Field is available for any object types that can be assigned to Supplemental Data.

**Classification Name Assign**

List the name of ALL Supplemental Data to which an object belongs. Field is available for any object types that can be assigned to Supplemental Data.

The following figure displays these relationships

![SupplementalClassificationAssign 614x273](images/SupplementalClassificationAssign_614x273.png)

Linking Display Objects to Supplemental Data

Display objects that cannot be linked to a power system element can be linked to a Supplemental Data record. These display objects include Background Line, Background Rectangle, Background Arc, Background Ellipse, Background Picture, Text, Case Information Memo, Oneline Field, Oneline Link, Document Link, and Memo Text.

Linking any of these objects to supplemental data must be done through the **Display Explorer** found under **Onelines \> All Display Objects**. From the **Explore** tab, choose the display object type to link. If they are not already displayed, the **Supplemental Data Classification** and **Supplemental Data Name** fields must be added to the list of fields in the table. Simply enter the appropriate Classification and Name in the fields to link a particular display object to a Supplemental Data record.

Once a display object is linked to a supplemental data record, the information in the supplemental data record can be used to filter, dynamically format, Select by Criteria, and display custom hints for that display object.

Because there is no requirement to link display objects that cannot be linked to power system elements to supplemental data records, these objects will not be highlighted along with other unlinked elements when they are not linked to a supplemental data record.

Automatic Linking of Supplemental Data When Inserting Geographic Information

Background objects (lines and ellipses) created from inserting objects from borders included with Simulator and shapefiles can be linked automatically to supplemental data records.

When [auto inserting borders](13-building-onelines-graphics-and-insertion.md#automatically-inserting-borders) included with Simulator, the option to **Automatically link county and state borders to supplemental data** needs to be checked for this to occur.

When inserting background objects from shapefiles, there are several options that need to be set for proper linking to supplemental data. These options are available on the **Identify** tab of the [GIS Shapefile Data Dialog](16-oneline-gis-tools.md#shape-file-import).

---

<a id="movie-maker"></a>

## Movie Maker

*Source: [`Content/MainDocumentation_HTML/Movie_Maker.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Movie_Maker.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator does not include a built-in tool for video capture or movie making. Commercial and freeware tools are available from other sources to capture video from PowerWorld Simulator, Retriever, and any other desktop applications. Current offerings may be found at the link below, or by simply searching online for video capture software.

Suggesting Link for Video Capture Software: <http://download.cnet.com/windows/video-capture-software>
