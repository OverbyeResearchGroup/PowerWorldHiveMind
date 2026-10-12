---
title: "Oneline View, Printing and Contouring"
part: "Oneline Diagrams"
chapter_file: "17-oneline-view-printing-and-contouring.md"
topics: 17
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Oneline View, Printing and Contouring

Changing the view, printing, contouring, dynamic formatting and difference flows.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (17)**

- [Oneline Screen Coordinates](#oneline-screen-coordinates)
- [Oneline Zooming and Panning](#oneline-zooming-and-panning)
- [Save View Level Dialog](#save-view-level-dialog)
- [Oneline Conditional Display of Objects](#oneline-conditional-display-of-objects)
- [Keyboard Short Cut Actions Dialog](#keyboard-short-cut-actions-dialog)
- [Printing Oneline Diagrams](#printing-oneline-diagrams)
- [Print Options Dialog](#print-options-dialog)
- [Printer Setup](#printer-setup)
- [Contouring](#contouring)
- [Contouring Options](#contouring-options)
- [Contour Type](#contour-type)
- [Contour Type Options](#contour-type-options)
- [Custom Color Map](#custom-color-map)
- [Functional Description of Contour Options](#functional-description-of-contour-options)
- [Dynamic Formatting Overview](#dynamic-formatting-overview)
- [Dynamic Formatting Dialog](#dynamic-formatting-dialog)
- [DisplayBus property AllowFixedNum](#displaybus-property-allowfixednum)

---

<a id="oneline-screen-coordinates"></a>

## Oneline Screen Coordinates

*Source: [`Content/MainDocumentation_HTML/oneline_screen_coordinates.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/oneline_screen_coordinates.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Onelines can be any size and can contain any number of objects. The size and position of objects on the screen are specified in terms of x-y "oneline screen coordinates." When the zoom level is 100% the size of the oneline in screen coordinates is 100 by 100. More generally, the size of the oneline is 1002 divided by the zoom level in both the x and y directions.

The default screen center is the point (50,50) but this can be easily changed (See [Oneline Panning and Zooming](#oneline-zooming-and-panning).) Negative screen coordinates are allowed. Usually you will not have to be concerned about an object's location in screen coordinates.

The [Status Bar](01-getting-started.md#status-bar) displays the current cursor screen coordinates while in Edit Mode.

![image\\ebx\_-24542984.gif](images/ebx_-24542984_190x18.gif)

Status Bar Showing Screen Coordinates

---

<a id="oneline-zooming-and-panning"></a>

## Oneline Zooming and Panning

*Source: [`Content/MainDocumentation_HTML/Oneline_Zooming_and_Panning.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Zooming_and_Panning.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

All oneline diagrams permit zooming and panning. Zooming and panning are very important tools for building and investigating large oneline diagrams that occupy more than a single screen of viewing area. Moreover, the display of various objects can be set to depend on the zoom level. See [Oneline Conditional Display of Objects](#oneline-conditional-display-of-objects) for more information on this feature.

The following mechanisms are provided for zooming or panning a oneline:

Line Navigation Arrows

For transmission lines whose end-points are not visible at the present pan/zoom level, small Line Navigation Arrows will appear where the line exits the present window. If you click on these arrows, the oneline will automatically pan over to the other end of the transmission line. The oneline will zoom out as it moves away from the present position and zoom back in until it finishes at the same zoom level with the endpoint in the middle of the oneline. On the [Oneline Tab](10-power-flow-solution-and-options-part2.md#oneline-options) of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog you can control three attributes for these arrows

1.  The size in pixels (default is 9)
2.  How fast the program pan/zooms to the new location in seconds. (Making this shorter gets you there faster, but you lose some of the overview information of where you're going as you pan to the new location.)
3.  Whether to show hints as you move the mouse over the arrows.

![Line Navigation Arrows](images/Line_Navigation_Arrows.gif)

Zooming on Onelines

Zooming involves adjusting the oneline diagram's display area by changing the magnification of the view. Zoom in on a oneline to have the screen display less of the complete oneline diagram, and zoom out on a oneline to have the screen display more of the complete oneline diagram.

To zoom on a oneline diagram using the keyboard, follow these instructions:

  - Use CTRL-up arrow to zoom in
  - Use CTRL-page up to zoom in quickly
  - Use CTRL-down arrow to zoom out
  - Use CTRL-page down to zoom out quickly
  - The **[Zoom](02-simulator-ribbon.md#zoom-ribbon-group)** ribbon group offers additional zooming options:
  - Use the **Zoom in on Area** button of the [Zoom](02-simulator-ribbon.md#zoom-ribbon-group) ribbon group to select a region on which to zoom.
  - Use the **Show Full** button of the [Zoom](02-simulator-ribbon.md#zoom-ribbon-group) ribbon group to zoom the display out to show the entire oneline.
  - Use the **Find** button of the **[Zoom](02-simulator-ribbon.md#zoom-ribbon-group)** ribbon group to display the [Pan/Zoom Dialog](14-editing-onelines.md#zoom-pan-and-find).
  - Use the **Save View** button of the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group to display the [Save View Dialog](#save-view-level-dialog), or click on the drop down arrow on the Save View button to choose from a list of saved views.
  - Use the **Rectangular Zoom Selector** to select a section of the diagram to zoom into using a selection box. After clicking button (symbolized with a magnifying glass over a dashed rectangle,) left click and hold the mouse button down on the diagram, drag the mouse to select part of the diagram inside a box, then release the mouse button. Simulator will zoom into the region selected inside the box.

Panning on onelines

Panning moves the screen's focus point around the oneline diagram. You can pan left, right, up, or down to view different portions of the complete oneline diagram.

To pan around the oneline using the keyboard, follow these instructions:

  - Use the arrow keys to move in the desired direction
  - Use page up to move up quickly
  - Use page down to move down quickly
  - Use the Home key to move left quickly
  - Use the End key to move right quickly
  - Left-click and hold the mouse button down anywhere on the *background* of the diagram. Make sure you do not click on an object on the diagram. While holding the left mouse button down, drag the mouse in any direction to "drag" the diagram in that direction.

You can also use the [Pan/Zoom Dialog](14-editing-onelines.md#zoom-pan-and-find) to pan to a specific location, or even to a specific bus. You can display the Pan/Zoom Dialog either by pressing the **Find** button on the Zoom ribbon group of the Onelines ribbon tab or by selecting**Pan/Zoom Control** from the oneline diagram's [local menu](15-using-onelines-tools-and-options.md#oneline-local-menu).

---

<a id="save-view-level-dialog"></a>

## Save View Level Dialog

*Source: [`Content/MainDocumentation_HTML/save_view_level_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/save_view_level_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Save View Level Dialog** is used to save an (x,y) location and zoom level, contour description, and/or hidden layer application for a oneline diagram in an easily accessible list for quick recall and application to the diagram. This dialog can be called by selecting the **Save/Edit/Delete View** option from the [oneline local menu](15-using-onelines-tools-and-options.md#oneline-local-menu).

You can also define a new layer by going to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, then on the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group choose **Save View \>** **Save View**.

Recalling a saved view can be done by either right-clicking on the background to access the [oneline local menu](15-using-onelines-tools-and-options.md#oneline-local-menu) and choosing a view from the **Go To View** list, or by clicking on the drop down arrow on the **Save View** button and selecting a view from the resulting list. Selecting a saved view automatically moves the oneline diagram location to the (x,y) coordinates and zoom level, applies a stored contour, and/or applies hidden layers stored with the selected view.

This dialog can be used for creating a new view, editing an existing view, or deleting an existing view. The **Save View Level Dialog** has the following options:

View Name

This is the name that the view will be stored under in the saved view list. This must be a unique name for each view saved with the oneline diagram. By default this field is blank. To edit an existing view, choose the desired view from the drop down list.

If a view is named using a back-slash, a subfolder will be created in the list of views that is shown on the [Onelines ribbon](02-simulator-ribbon.md#active-ribbon-group) under the Save View dropdown. As an example, "New Folder\\View Name", will create a subfolder with the name "New Folder" and this folder will contain the view with the name "View Name".

Save Display Information in View

When checked, the view will store an x-y coordinate and zoom level to associate with the view. When the view is selected for display, the diagram will center on the x-y coordinate at the defined zoom level.

X-Coordinate

The x-coordinate for the view. This value will default to the current x-coordinate for the oneline diagram, or will change to a saved value if a saved view is chosen from the **View Name** drop down list. This value can be modified by the user.

Y-Coordinate

The y-coordinate for the view. This value will default to the current y-coordinate for the oneline diagram, or will change to a saved value if a saved view is chosen from the **View Name** drop down list. This value can be modified by the user.

Zoom Level

The zoom level for the view. This value will default to the current zoom level for the oneline diagram, or will change to a saved value if a saved view is chosen from the **View Name** drop down list. This value can be modified by the user.

Save Contour Information in View

If a contour is being displayed when the view is created, you can choose to save the [contour](#contouring) information with the view by checking this box. Saving a contour with a view will display that contour when you switch to that view. You also have the option of saving a blank contour with the view. This is indicated by a Contour Object of ‘None’ and a Contour Field of ‘None.’ If you save a blank contour, no contour will be displayed when switching to that view. If you don’t save any contour with the view, then any existing contour will be applied when switching to that view.

Contour Object

This section displays the type of object the stored contour pertains to. This field cannot be changed from this location.

Contour Field

Displays the type of value the stored contour pertains to. This field cannot be changed from this location.

Link to Oneline Display Options Settings

In the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) in Simulator, you can save various sets of options with a case for quickly recalling oneline diagram settings by name. This option allows you to include a custom defined option set by name with the current view. Note that you first must have created and saved a custom set of options for a diagram from the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) dialog before this option on the Save Views dialog will be enabled.

Save Hidden Layers

Since Simulator allows the use of [layers](14-editing-onelines.md#levelslayers-options) to display or hide objects on the diagram, views also can optionally store the layer settings when the view is created. The window below this checkbox will list the layers that are presently hidden on the diagram. When this view is recalled, the layers in this list will be hidden if they were stored with the view.

Save

This button will save a new view or modify the values for an existing view of the name in the **View Name** field. If a view is named using a back-slash,\\, a subfolder will be created in the list of views. As an example, New Folder\\View Name, will create a subfolder with the name New Folder and this folder will contain the view with the name View Name.

Delete

This button will delete the currently open view from the saved view list. The dialog information will default to the saved view information of the previous view in the list.

OK

This button will save a new view or modify the values of an existing view of the name in the **View Name** field, and will close the **Save View Level Dialog**.

Save to AXD

By clicking this button, all the views will be saved to a [display auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux).

Load from AXD

This button will load all the views saved in a [display auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux).

---

<a id="oneline-conditional-display-of-objects"></a>

## Oneline Conditional Display of Objects

*Source: [`Content/MainDocumentation_HTML/Oneline_Consitional_Display_of_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Consitional_Display_of_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Along with supporting zooming and panning, the onelines permit the conditional display of objects. That is, it is possible to specify display objects so they are visible only at particular zooming ranges. This enables the oneline to show additional details as the user zooms in and fewer details when the user zooms out.

Please note that the zoom levels are defined as percentages. If you want an object to display only between 50% and 150%, you must select 50 and 150 as the zoom level boundaries.

This option is available by assigning objects on the diagram to a [Layer](14-editing-onelines.md#levelslayers-options). Layers can be defined and set to objects on the [Format Multiple Objects](14-editing-onelines.md#format-selection-dialog) dialog.

---

<a id="keyboard-short-cut-actions-dialog"></a>

## Keyboard Short Cut Actions Dialog

*Source: [`Content/MainDocumentation_HTML/Keyboard_Short_Cut_Actions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Keyboard_Short_Cut_Actions_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Keyboard Short Cut Actions dialog allows the user to associate a keyboard shortcut to a determined oneline diagram, and even to a particular [view](#save-view-level-dialog) of that diagram. When the keyboard shortcut is pressed, the oneline diagram is opened (if it was closed) and brought to the front. When a view is also associated, then the user is taken to such a [view](#save-view-level-dialog).

To open the Keyboard Short Cut Actions Dialog, select **** ****Keyboard Shortcuts**** on the **General Options** ribbon group of the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab. These General Options are also available on the [Oneline](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.

The dialog has the following controls:

Keyboard Shortcuts

Lists all the keyboard shortcuts. When selecting a keyboard shortcut, it will show the *oneline* and the *view* associated to the selected keyboard shortcut. If your keyboard has an extra row of function keys, then you can check the box labeled **Include F13-F24**. If a shortcut has been defined for the respective key, then it will be highlighted and a string will summarize the action of the shortcut

Clear All

Clicking this button will delete all the associations of all the listed shortcuts.

Save Shortcut

Click this button after entering a oneline diagram and eventually a view so they can be associated with the selected keyboard shortcut.

Delete Shortcut

Click this button to delete the associations of the selected keyboard shortcut with any oneline diagram and view.

Create Shortcut

This indicates the keyboard shortcut to which the below actions will be assigned. The available actions are to Open a Oneline and to Open an Auxiliary File

Open Oneline

The following options are available for opening oneline actions:

Oneline and View: Oneline

Shows the path and the name of the oneline diagram which will be opened when the selected keyboard shortcut is pressed. If the field is blank, then no oneline diagram is associated to the keyboard shortcut. You can click **Browse** to find the oneline diagram.

Oneline and View: View

Shows the name of the view belonging to the associated oneline diagram to which the user will be taken when the selected keyboard shortcut is pressed. If the field is blank, then no view is associated to the keyboard shortcut.

Action for already open onelines

If the oneline being requested by the shortcut key is already open, then this option determines what should be done. Choices are to close the oneline, bring the oneline to the front, or to open a new oneline.

Where to open oneline

When opening a oneline via a shortcut key, you may do one of the following:

  - Separate Window (open the oneline as normal)
  - Separate Window – [Toggle Full Screen](15-using-onelines-tools-and-options.md#oneline-local-menu) (open normal and then toggle it to full screen)
  - Embed the Active Oneline Window (opens the oneline and embeds it inside the presently active oneline diagram)

Note: if onelines already exist which have been toggled to full screen, and a short cut key is used to open a window that will not be toggled to full screen, then all other onelines present open will be switched to normal mode instead of full screen mode.

Size and Location

This specifies the relative size and location you would like the oneline to be opened at. When opening the oneline normally, the percentage is relative to the size of the container window. When opening the oneline embedded in the active oneline, the percentage is relative to the size of the active oneline.

Make embedded oneline borderless

When [embedding](15-using-onelines-tools-and-options.md#oneline-local-menu) the oneline inside the presently active oneline, this option will make the embedded oneline borderless.

Open Auxiliary File

The following options are available for opening auxiliary file action:

Filename

Shows the path and the name of the auxiliary file which will be opened when the selected keyboard shortcut is pressed. If the field is blank, then no auxiliary file is associated to the keyboard shortcut. You can click **Browse** to find the auxiliary file.

Section name

Shows the name of the script or data section belonging to the associated [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) which will be executed when the selected keyboard shortcut is pressed. If the field is blank, then no specific section is associated to the keyboard shortcut, so all script and data sections will be loaded.

Create objects if they do not already exist

Check this box to indicate that new objects in the auxiliary file should automatically be created.

Save/Load shortcuts to/from an Auxiliary File

Click the **Save** button to save all the shortcuts to an auxiliary file. Click the **Load** button to load the shortcuts saved in an auxiliary file. The shortcuts saved in the auxiliary file will replace the shortcuts saved in the dialog.

Close

Closes this dialog.

In addition to the shortcuts displayed on this dialog, Simulator also offers standard windows editing shortcuts such as:

**Ctrl + x** – Cut Command

**Ctrl + c** – Copy Command

**Ctrl + v** – Paste Command

---

<a id="printing-oneline-diagrams"></a>

## Printing Oneline Diagrams

*Source: [`Content/MainDocumentation_HTML/Printing_Oneline_Diagrams.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Printing_Oneline_Diagrams.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To print a oneline diagram, select **Print Oneline** from the [File menu](03-cases-files-and-formats.md#file-menu) or right-click on the oneline background and select **Print Window** from the popup menu. This opens the [Print Options Dialog](#print-options-dialog), which you can use to configure the print job, including its size, orientation, border, and title bar. You can even choose to print a oneline to multiple pages using Simulator's multi-page printing.

---

<a id="print-options-dialog"></a>

## Print Options Dialog

*Source: [`Content/MainDocumentation_HTML/print_options_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/print_options_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Print Options Dialog is used to configure the printing of oneline diagrams (including bus view displays) and of strip charts. To print a oneline diagram, select **Print Oneline** from the [File menu](03-cases-files-and-formats.md#file-menu). To print a strip chart, right-click on it to invoke its local menu, and then select **Print Window**. In both cases, Simulator will open the Print Options Dialog.

The Print Options Dialog has two tabs:

Page Layout

This tab sheet contains options for how the diagram will appear on the printed page. It presents the following controls:

Margins

Specify the horizontal and vertical margins in either inches or centimeters.

Scaling

Set this option to **Proportional** to print the oneline diagram or strip chart such that the screen’s aspect ratio is maintained. Set this option to **Fit to Page** to force the printout to take up all available space on the page in both horizontal and vertical directions, or **DPI** to specify a dots per inch scaling.

Draw Border

Places a border to be drawn around the oneline diagram or strip chart.

Print Title Bar

Check this box to print a title bar at the bottom of the diagram. Checking this box displays a number of options that allow you to specify various items to include in the title bar. If you don’t want to include certain items on the plot, simply leave those fields blank.

The title bar is split horizontally into three sections. If you specify values for all requested items, they will be arranged in the title bar as follows:

Company | Description Line 1 | Date

Department | Description Line 2 | Drawing \#

Author | Description Line 3 | Title

Multi-Page

This tab allows the oneline diagram to be "divided" into a specified number of sections for printing the oneline to several pages. A multi-page oneline can be useful for including "close-up" views of areas of a diagram in a report, or the multiple pages can be cut and combined to form a larger printed oneline if a plotter is not available. The **Multi-Page** tab presents the following controls:

Grid Size

Choose this value to subdivide the oneline into an N by N grid. You can then choose which sections of the oneline to print based on the grid overlay. The maximum size is 10 x 10.

Choosing What to Print

A low resolution picture of your oneline is shown on the **Multi-Page** tab. Gridlines are drawn over the diagram to show where the oneline has been subdivided based on the **Grid Size** chosen.

To remove a grid section from the printout, click on the oneline image in the corresponding section of the grid (Please note that the grid size should be more than 1 to select a grid section). The selected section of the grid will become dark to indicate you wish to prevent the section from printing.

To add a grid section back into the print job, click on a darkened section of the grid to allow that section of the oneline to be printed.

The number of pages you have chosen to print will be shown on the dialog. When printing out a multi-page oneline with a title bar, the page number will appear on the title bar in the form "Column Letter"-"Row Number". For example, if the Grid Size is 4, the pages are numbered **A-1** through **D-4**.

Click **Print** to send the document to the printer, or **Cancel** to abort the print. Click **Setup** to view the default Windows printer dialog, which will allow you to specify whether to print the figure in portrait or landscape modes and to set various printer-specific properties.

---

<a id="printer-setup"></a>

## Printer Setup

*Source: [`Content/MainDocumentation_HTML/printer_setup.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/printer_setup.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Choose **Printer Setup** from the [File menu](03-cases-files-and-formats.md#file-menu) to configure the printer using the standard Windows printer setup dialog. This dialog allows you to define which printer to use for printing from Simulator, the size of the printed page, the page’s orientation, and additional properties that are specific to the printer you are using.

---

<a id="contouring"></a>

## Contouring

*Source: [`Content/MainDocumentation_HTML/Contouring_Topic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contouring_Topic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can create and animate a contour map of various system quantities, such as voltage magnitudes and angles, MW transactions, transmission loading, and real and reactive load. Such displays resemble a contour map of temperatures like you might see shown on a weather forecast. Contouring can significantly improve understanding of a large interconnected system, helping identify congestion pockets and Mvar-deficient regions and providing an overview of how power flows through the bulk power system.

The [Contour Options Dialog](#contouring-options) **** controls Simulator’s contouring capabilities. To access it, click the right mouse button on an empty area of the oneline and choose **Contouring** from the resulting [local menu](15-using-onelines-tools-and-options.md#oneline-local-menu), or choose **Contouring** from the **[Active](02-simulator-ribbon.md#active-ribbon-group)** ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.

Contouring is available in both [Run Mode](01-getting-started.md#run-mode-introduction) and [Edit Mode](01-getting-started.md#edit-mode-introduction), however when you switch from Run Mode back to Edit Mode, Simulator automatically removes the contour from the oneline diagrams. You can still choose to reapply the contour while in edit mode however.

---

<a id="contouring-options"></a>

## Contouring Options

*Source: [`Content/MainDocumentation_HTML/Contouring_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contouring_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Contour Options Dialog allows you to draw contour maps of many system quantities, such as bus voltages or angles, transmission line and interface MVA loadings, and transmission line and interface [PTDFs](20-sensitivities.md#power-transfer-distribution-factors).

To access this dialog, click the right mouse button on an empty area of the oneline and choose **Contouring** from the resulting [local menu](15-using-onelines-tools-and-options.md#oneline-local-menu), or choose **Contouring \> Contouring** from the [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab. The Contour Options Dialog has three tabs: the [Contour Type](#contour-type) Tab, the [Contour Type Options](#contour-type-options) Tab, and the [Custom Color Map](#custom-color-map) Tab.

---

<a id="contour-type"></a>

## Contour Type

*Source: [`Content/MainDocumentation_HTML/Contour_Type.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contour_Type.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Contour Type options can be set from the Contour Type tab on the [Contour Options dialog](#contouring-options).

Object

Simulator can contour several different values. To specify what Simulator should contour, first choose the type of display object; the options are Bus, Line, Interface, Area, Generator, Substation, Zone or Injection Group. Once the object is chosen, you must then choose the numerical value to be contoured by specifying it in the **Value** dropdown box.

Note: to contour a value for a type of object, representations of that type of object must be present on the oneline diagram. Choosing to contour an object type that is not represented on the diagram will result in no contour being drawn on the diagram.

Value

Select the quantity to contour from the Value dropdown box or click the **Find…** button to find the desired field (it is normally easier to use the Find button). See NOTE at the end of this help topic.

Filter Object Values

The name of the advanced filter that is currently applied to the contour. Click Define to create a new Advanced Filter to use during contouring. Applying a filter means that *only* objects that meet the filter will affect the contour image. Objects which do not meet the filter will be ignored.

Data Points per Line

This specifies the number of data points used to represent the graphical line. The contouring algorithm is based on values at specific coordinates in the oneline space. When contouring transmission line or interface objects, the line is represented by a series of points spaced equally along the graphical line.

No Data Color

This setting allows you to choose the contour color used for parts of the contour for which there are not objects nor data for the type of contour selected. The choices for No Data Color are Specific Color, Color Map Percentage,Background Color, and Transparent. By default, Specific Color is selected and set to white. If you wish to change the specific color to use, click on the color box to the right and choose a different color from the popup dialog. If you select Color Map Percentage, the Color Map % field will become enabled, and you can select a value from 0 to 100. The value you enter will associate the No Data Color with the color located at that percentage in the selected color map. If Background Color is chosen, the No Data Color will always be whatever color has been set as the normal background color for the oneline diagram. Lastly, if Transparent is chosen, the parts of the contour for which there are not objects nor data for the type of contour selected will be transparent and any objects on the oneline diagram will be displayed as usual.

Draw Color Key

Checking this box will cause the contour to draw a color key showing which colors are mapped to which values. You can also give the color key a title, unit label, and specify the number of digits to display in numerical values.

Title

Title for the color key.

Entry Labels

Units of the contoured value displayed on the color key.

Dec. Pts.

Number of decimal places of the contoured value displayed on the color key.

Scalar

Multiplication factor that can be applied to the values when drawing the color key. Normally this value should be 1.0.

Use Equal Spacing For Discrete Maps

This option will draw the color key with equal spacing for all colors in the map, regardless of how close or distant the values the colors represent. This option only applies to discrete color maps.

Color Map

Choose from various predefined color maps using the color map combo-box. A color map, along with the values specified, defines how values are mapped to a color on the contour image.

If a color map showing both high and low values is desired (such as for bus voltages), use of "Blue = Low, Red = High" is recommended. If a color map showing only high values is desired (such as for line flows), use of "Weather Radar, Nominal to High" is recommended.

A user may also define additional color maps by going to the [Custom Color Map](#custom-color-map) Tab.

Reverse Color Map Colors

Check this check-box to reverse the colors of the selected color map, so the low color becomes the high color, and vice versa.

Brightness

Modify the brightness track bar to change the brightness of the color map.

Use absolute value

Check this check-box to use the absolute values of the quantity selected at the Value dropdown box (above).

Ignore Above Max

Check this check-box to completely ignore values above the maximum percentage. This means that data which is larger than the Max % will not be used in calculating the contour image. This is similar to using an Advanced Filter to Filter Object Values, but provides a quick way to do so.

Values

For all color maps that come with PowerWorld by default, the conversion of a value to a color is done in two steps. The value is first interpolated to a percentage by using up to 5 user-specified values (maximum, break high, nominal, break low and minimum) that correspond to specific percentages (100%, 75%, 50%, 25%, and 0%). This percentage is then interpolated through the color map and a color is determined.

![image\\ebx\_-80459367.gif](images/ebx_-80459367_640x89.gif)

User may define their own color maps which convert percentage to color, but they may also define color maps which directly translate values into colors without the intermediate calculation of a percent. For more information on this see the creation of a [Custom Color Map](#custom-color-map).

The value range values are described as follows:

**Maximum**  The largest value allowed in the contour. All values above this will be mapped to the highest color. This value corresponds to 100% in the color map.

**Break High** This value is used by some color maps to highlight a lower limit. This value corresponds to 75% in the color map.

**Nominal**  This value is the nominal value for the contour. Values around this will be mapped to the middle color. This value corresponds to 50% in the color map.

**Break Low** This value is used by some color maps to highlight a lower limit. This value corresponds to 25% in the color map.

**Minimum** The smallest value allowed in the contour. All values below this will be mapped to the lowest color. This value corresponds to 0% in the color map.

Note: a representation of the color map is shown to the right of the values.

Ignore Below Min

Check this check-box to completely ignore values below the minimum percentage. This means that data which is smaller than the Min % will not be used in calculating the contour image. This is similar to using an Advanced Filter to Filter Object Values, but provides a quick way to do so.

Ignore Zero Values

Check this box to completely ignore zero values in the contour. This is similar to using an Advanced Filter to Filter Object Values, but provides a quick way to do so. If there is a need to ignore values that are almost but not exactly zero, then create an Advanced Filter to Filter Object Values.

Interpretation

This combo box specifies how to interpret the values of the data points. The options are:

**Fixed Values**  The data point values are not modified. The maximum, minimum, nominal, and break values are the ones entered directly in the units of the value being contoured. This is what should normally be used.

**Dynamic Values**  The data point values are not modified. However the maximum, minimum, nominal, and break values are determined dynamically from the data point values as follows: Maximum = Maximum data point value; Minimum = Minimum data point value; Nominal = Average data point value; Break High = (Max + Average)/2; and Break Low = (Min + Average)/2.

**Standard Deviations** All the data point values will be used to determine a mean and standard deviation. The data point values will then be converted to represent the number of standard deviations they are from the mean. Thus a value equal to the mean will be changed to a 0, a value 1.5 standard deviations higher than the mean will be changed to 1.5, and so on.

**Percentiles**  All the data point values will be sorted from lowest to highest. The value will then be set equal to the 100 times the sort location divided by the number of data points. Thus the highest value will be given a value of 100 and the lowest a value of 1.

Save Contour Image with Oneline

Checking this box will allow a displayed contour to be saved with a oneline diagram. If a contour is saved with a oneline diagram, the next time the oneline diagram is opened the contour will automatically be redrawn as well. The displayed contour is saved as a Bitmap image.

Continuously Update Contours

Normally contouring is only done on a snap shot of the power system state. However, you can also set Simulator to automatically update the contour every time the display is redrawn. In this way, an animation of the contour can be created. If you would like to create this animation, simply check the Continuously Update Contours checkbox. Note, however, that this will slow down the animation of the display, as the program must recalculate the contour at each step. If this slows down your display too much, try lowering the contour resolution to speed it up.

Note Regarding Values

Contours of most values create an image where the color around a data object is primarily related to the value of only that object. Some values however create "density-like" contours, where the color is related to the sum of the data object's values nearby. These include:

  - Bus / Load MW
  - Bus / Load Mvar
  - Bus / Load MVA
  - Bus / Cust Expr (Density)
  - Area / Pos Spin Reserve
  - Area / Neg Spin Reserve

---

<a id="contour-type-options"></a>

## Contour Type Options

*Source: [`Content/MainDocumentation_HTML/Contour_Type_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Contour_Type_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Object

Simulator can contour several different values. To specify what Simulator should contour, first choose the type of display object; the options are Bus, Line, Interface, Area, Generator, Substation, Zone or Injection Group. Once the object is chosen, you must then choose the numerical value to be contoured by specifying it in the **Value** dropdown box.

If multi-section lines objects exist on the oneline diagram and the type of object to contour is Line, the contour for the multi-section line object will reflect the series of AC lines that it represents. If the type of object to contour is Bus, the locations of intermediate buses will be contoured.

Note: to contour a value for a type of object, representations of that type of object must be present on the oneline diagram. Choosing to contour an object type that is not represented on the diagram will result in no contour being drawn on the diagram.

Value

Select the quantity to contour from the Value dropdown box or click the **Find…** button to find the desired field (it is normally easier to use the Find button). Note: see [Contour Type](#contour-type) for more information.

Filter Object Values

The name of the advanced filter that is currently applied to the contour. Click Define to create a new Advanced Filter to use during contouring. Applying a filter means that *only* objects that meet the filter will affect the contour image. Objects which do not meet the filter will be ignored.

Influence Region

This track bar determines how far away each data point influences the contour image. A larger influence region results in each data point influencing more of the contour at the expense of longer screen refresh times.

Use Dynamic Influence Region

Dynamic influence distance determines how far out the contour should go when determining which buses influence the contour value for a screen point.  The actual distance is the minimum of either 1) a common value for all screen points that depends upon user parameters \[e.g., the dynamic region points value\]), and now 2) the distance that includes the number of buses associated with the dynamic influence field.  The primary reason for this option is speed, particularly when zoomed in on dense portions of the display.  You should not see much impact on the contour itself.

Kind of Value

This option allows you to choose to contour based on the Actual Value or the Density Value. The Actual Value uses the weighted average of the data for computing the contour. The Actual Value method is most commonly used for contouring in Simulator. On occasion, the Density of Values method does not work as well. One example is contouring generator MW values. If you have four buses in close proximity, each with 100 MW of generation, and compare the contour with a single bus with 400 MW of generation, the contour based on the weighted average will look drastically different, despite the amount of generation being the same in each region. Using the Density Value option will correct the disparity, and the contour around these two different groups of generation would look basically the same.

Use Fade to Value

Checking this check box will allow to use the Fade to Value and Begin Fade Percentage options.

Fade to Value

The value to which a data point's value fades as it moves away from its location.

Begin Fade Percentage

While moving away from a data point, the data point’s value decays towards the "Fade to" Value. The Begin Fade Percentage specifies when the contour starts to fade as a percentage of the largest distance for which this data point influences the contour.

Contour Resolution

This value determines the relative resolution of the contour. Increasing the contour resolution increases the level of detail represented on the map but will lengthen screen refresh times. Reducing the screen refresh time will yield less detail and shorter screen refresh times.

Low Resolution Display when Zooming or Panning

Do Low Resolution Speedup

Check this option to enable drawing contours in low resolution while zooming or panning. Low resolution images are drawn much faster than high resolution images.

Low Resolution Normalized Percent

Set a percentage of resolution between 0.01 (1%) and 1 (100%). A smaller value translates to a lower resolution image.

Time Delay in Seconds before Redrawing at Full Resolution

Set the number of seconds Simulator will pause before returning the contour to full resolution following zooming and panning.

Minimum Resolution in Pixels for Low Resolution Displays

Specify the minimum resolution allowed (in pixels) when Simulator draws the low resolution image.

Use GPU to accelerate contour calculation

As it describes, checking this option will use the GPU processor to perform contour calculations that will accelerate computation time.

Use 32 bit texture format

As it describes, checking this option will use a 32 bit texture format for countours.

When Animating, Only Update Contour if Something Changed

As it describes, checking this option will suppress redrawing the contour during animation unless one or more of the contoured values changes.

---

<a id="custom-color-map"></a>

## Custom Color Map

*Source: [`Content/MainDocumentation_HTML/Custom_Color_Map.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Custom_Color_Map.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Custom Color Maps can be defined from the Custom Color Map tab found on the [Contour Options dialog](#contouring-options). Custom color maps allow you to define completely new color maps for create new color maps from existing default color maps.

Color Map

Choose from various predefined color maps using the color map combo-box. A color map, along with the values specified, defines how values are mapped to a color on the contour image.

If a color map showing both high and low values is desired (such as for bus voltages), use of "Blue = Low, Red = High" is recommended. If a color map showing only high values is desired (such as for line flows), use of "Weather Radar, Nominal to High" is recommended.

Reverse Color Map Colors

This check-box reverse the mapping of the color map, converting the colors corresponding to the high values into the colors for the low values, and vice-versa.

Brightness

Modify the brightness track bar to change the brightness of the color map.

Make Discrete Color Map

Check this check-box to make a discrete color map, that is without having smooth transitions between colors.

Contour Type Values to Use

These check-boxes signify which values from the Contour Type Values Tab are used by the Color Map. There must be at least two contour type values checked.

Color Grid

The color grid on the right side of this page allows you to change the colors for each percentage breakpoint. In addition, you can add or delete breakpoints as well.

To change the color for a specific breakpoint, simply left-click on the color for the breakpoint you want to change. The Color dialog will open, and you can choose a new color for that breakpoint. Setting the Transparent field to YES will make the contour transparent for data values that meet the specified percentage breakpoint. Setting the Transparent field to NO will show the data values with the specified color. To change a value in the Transparent field, left-click on the value and it will toggle between YES and NO.

To add a breakpoint, right-click on a breakpoint position above or below where you would like the new breakpoint inserted. A popup menu will open, and you can select Add Above or Add Below, depending on where you wish the new breakpoint to be. Simulator will insert the breakpoint, and will automatically set the color and percentage at the midpoint between the two breakpoints above and below the inserted breakpoint. You can then click on the color to change it, or click on the percentage to type in a new value. The new percentage value should be between the values of the adjacent breakpoints.

To delete a breakpoint, right-click on the breakpoint you wish to delete, and choose Delete from the popup menu.

Color By…

This option allows the user to interpret the breakpoints values as percentage values or as direct values.

For all color maps that come with PowerWorld by default, the conversion of a value to a color is done in two steps. The value is first interpolated to a percentage by using up to 5 user-specified values (maximum, break high, nominal, break low and minimum) that correspond to specific percentages (100%, 75%, 50%, 25%, and 0%). This percentage is then interpolated through the color map and a color is determined.

![image\\ebx\_-80459367.gif](images/ebx_-80459367_734x103.gif)

Color maps which directly translate values into colors without the intermediate calculation of a percent may also be created. This is done by setting Color By to *Value*.

Save As…

To save the present color map as a new color map, click this button. Then specify a name for the new color map.

Save

To save changes that have been made to the present color map, click this button.

Rename

To rename the present color map, click this button.

Delete

To delete the present color map, click this button.

Store Color Maps in File

To store all custom color maps in a file for loading into another case, click this button. If you have saved any custom color maps with the current case, you will be prompted to choose a file name and location for saving the custom color maps. Color Maps are saved in the [Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux).

Load Color Maps from File

If you have created custom color maps in a different case and saved them to a file, you can click this button to load those color maps into your current case. Color Maps are loaded in the [Auxiliary File Format](03-cases-files-and-formats.md#auxiliary-file-format-aux).

---

<a id="functional-description-of-contour-options"></a>

## Functional Description of Contour Options

*Source: [`Content/MainDocumentation_HTML/Functional_Description_of_Contour_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Functional_Description_of_Contour_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Functional Description of the Contour Options**

The previous help topics discussed basic contour options in the order they are arranged on the dialog. The dialog is arranged so that the most important options are on the first tab and other on the Contour Type Options tab. This help topic discusses the options in a manner which better describes how the contour is actually created. A contour is calculated generally by a five-step process

1.  Build a list of all possible data points (graphical locations)
2.  Remove items that meet criteria from the list of data points
3.  Assign a value to each data point
4.  Calculate "virtual values" on a grid of points
5.  Convert each "virtual values" into a color to create the contour image

Step 1: Build a list of data points (graphical locations)

The following options determine a list of potential data points (could also be called graphical locations) which will be used to calculate the contour image.

**Object** - Simulator can contour several different values. To specify what Simulator should contour, first choose the type of object. This corresponds to the type of display object that is drawn on the oneline diagram. For instance if you want to contour a substation value, then you must have substations drawn on your diagram. This selection narrows the set of quantities that can be contoured, which is specified in the Value dropdown box.

**Data points Per Line** - The contouring algorithm for lines is no different than for points, except that each line is represented by several points. For objects which are represented by graphical lines, this option will specify the number of data point which should be used to represent the line.

Step 2: Remove items that meet criteria from the list of data points

After a complete list of potential data points is made, there are then several options for filtering out things from this list which you do not want to effect the calculation of the contour image.

**Filter** - If you wish for the contour to be limited to only certain devices that meet specific criteria, click on this button to define an Advanced Filter for the contour

**Ignore Above Max** - Check this check-box to completely ignore values above the maximum percentage. This means that data which is larger than the Max % will not be used in calculating the contour image

**Ignore Above Min** - Check this check-box to completely ignore values below the minimum percentage. This means that data which is smaller than the Min % will not be used in calculating the contour image

**Ignore Zero Values** - Check this check-box to completely ignore values that are zero.

Step 3: Assign a value to each data point

After Step 2, a list of potential data points has been created and a value must now be assigned to each data point. The following options specify how this is done.

Value - select the quantity to contour from the Value dropdown box or click the Find Value button to find the desired field.

Use absolute value - This check-box will modify the Value specified so that it uses the absolute value.

Interpretation – When interpretation is set to either Standard Deviations or Percentiles, then the value of the data point will be modified.

If **Standard Deviations** is chosen, then all the data point values will be used to determine a mean and standard deviation. The data point values will then be converted to represent the number of standard deviations they are from the mean. Thus a value equal to the mean will be changed to a 0, a value 1.5 standard deviations higher than the mean will be changed to 1.5, and so on. Similar,

If **Percentiles** is chosen, then all the data point values will be sorted from lowest to highest. The value will then be set equal to the 100 times the sort location divided by the number of data points. Thus the highest value will be given a value of 100 and the lowest a value of 1.

Step 4. Calculate "virtual values" on a grid of points

After Step 3, we now have a list of data points and a value assigned to each data point. We now must create a grid of points that represents "virtual values" throughout the entire graphical space. The values on this grid will be calculated based on the data point values

**Contour Resolution** - setting determine the size of the grid of points which will be superimposed on the present oneline diagram. The higher the resolution the more number of grid points will be used to represent the contour (and thus make the calculation of the contour image slower)

**Influence Region** - each data point value will effect only the grid locations that are "near" it. The distance that is considered "near" is determined by the Influence Region. Setting the influence region higher will result in each data point effecting a larger portion of the contour image (and thus making the calculation of the contour image slower)

**Kind of Value** - The calculation of the virtual value at a particular grid point is done by first building a list of data points that are within the "influence distance" of the grid point. The Kind of Value setting determines what process is used to calculate the virtual value from this list of values.

**Actual Value (Weighted Average)** - The virtual value is calculated as the weighted average value, weighted by the distance from the grid point. This means that virtual value half-way between two data points will be the average of the two data point values.

**Density of Values (Weighted Sum)** - The virtual value is calculated as the sum of value that within the influence region. This means that virtual value half-way between two data points will be the sum of the two data point values.

**Actual Value (Only Closest)** - The virtual value is assigned as the value of the closest data point.

![image\\ebx\_-904390779.gif](images/ebx_-904390779_462x328.gif)

**Fade to Value and Begin Fade Percentage** - In the middle of a contour image the colors look consistent because the virtual values are calculated using a good number of data points which surround it. Sometimes at the edge of a contour image however, the colors can become skewed because there are very few data points influencing it. Using a fade to value can help this situation, but will skew the entire contour image in general instead. Without using the fade to value, the raw data point values will be used when calculating virtual value.

When using the fade to value, while moving away from a data point, the data point’s value decays towards the "Fade to" Value. The Begin Fade Percentage specifies when the contour starts to fade as a percentage of the largest distance for which this data point influences the contour.

Step 5. Convert each "virtual values" into a color to create the contour image

After Step 4, a grid of virtual values has been calculated. At this point, must specify how these numbers map to colors. This done through the user of a Color Map.

**Color Map** - Choose from various predefined color maps using the color map combo-box. A color map, along with the values specified, defines how values are mapped to a color on the contour image. A user may also define additional color maps by going to the Custom Color Map Tab.

**Brightness** - this value is used to brighten or darken the colors specified in the color map.

**Values** - These values along with the color map define how to convert your values into a color for the contour. The values are:

**Maximum** - The largest value allowed in the contour. All values above this will be mapped to the highest color. This value corresponds to 100% in the color map.

**Break High** - This value is used by some color maps to highlight a lower limit. This value corresponds to 75% in the color map.

**Nominal** - This value is the nominal value for the contour. Values around this will be mapped to the middle color. This value corresponds to 50% in the color map.

**Break Low** - This value is used by some color maps to highlight a lower limit. This value corresponds to 25% in the color map.

**Minimum** - The smallest value allowed in the contour. All values below this will be mapped to the lowest color. This value corresponds to 0% in the color map.

**Interpretation** - Most frequently this option will be set to **Fixed Values** meaning values for maximum, break high, etc… are entered directly in the units of the value being contoured. If Interpretation is set to **Standard Deviations** or **Percentiles** then as mentioned earlier the values mean something different. The options **Dynamic Values** will process this list of data point values and automatically set the values as follows: Maximum = Maximum data point value; Minimum = Minimum data point value; Nominal = Average data point value; Break High = (Max + Average)/2; and Break Low = (Min + Average)/2.

**No Data Color** - It is likely that some the grid points will not be within the influence of any of the data points. The color of these points is determined by no data color setting.

---

<a id="dynamic-formatting-overview"></a>

## Dynamic Formatting Overview

*Source: [`Content/MainDocumentation_HTML/Dynamic_Formatting_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Dynamic_Formatting_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [Dynamic Formatting dialog](#dynamic-formatting-dialog) will allow the specification of how a graphical object will be rendered depending on the power system object that is representing. The graphical object refers to objects in the oneline diagram, in bus and substation views, as well as to some parameters of the case information displays.

The case and the one-line diagrams will have each a list of Dynamic Formatting settings. The Dynamic Formatting settings defined in the case are always applied to bus and substation views, and optionally they can be applied to the case information displays. The one line diagrams will use its own settings, but optionally can use the general settings defined with the case.

In general, the oneline dynamic formatting settings have a higher priority, followed by the case dynamic formatting settings, and this can't be reversed. Also, inside each of the list of dynamic formatting settings, a priority can be specified, so that objects can be rendered according to the settings with the highest priority.

In the case of the oneline diagrams, the dynamic formatting settings will only be applied during Run Mode. However, these settings can be modified at any time, without regard for the mode.

---

<a id="dynamic-formatting-dialog"></a>

## Dynamic Formatting Dialog

*Source: [`Content/MainDocumentation_HTML/Dynamic_Formatting_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Dynamic_Formatting_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Dynamic Formatting dialog for the active oneline can be accessed by:

  - Selecting **Dynamic Formatting \> ![image\\ebx\_-650576347.gif](images/ebx_-650576347_23x22.gif)Active Oneline** on the **General Options** ribbon group of the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab. These General Options are also available on the [Oneline](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.
  - Selecting **Dynamic Formatting (Active Oneline)** from the [oneline local menu](15-using-onelines-tools-and-options.md#oneline-local-menu), or

The Dynamic Formatting dialog for the general case information displays, bus and substation views, and for all onelines can be accessed by:

  - Selecting **Dynamic Formatting \> **![image\\ebx\_1944232010.gif](images/ebx_1944232010_23x22.gif)Case Info / All Views And Onelines**** on the **General Options** ribbon group of the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab. These General Options are also available on the [Oneline](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab.
  - Selecting **Dynamic Formatting (All Views)** from the [bus view local menu](15-using-onelines-tools-and-options.md#oneline-local-menu) or the [substation view local menu](15-using-onelines-tools-and-options.md#oneline-local-menu), or

This dialog presents the following options:

Set Format Priority

It is possible to have multiple dynamic format definitions created and stored with a case and/or active oneline diagram. This option allows you to set a format priority order for all of the dynamic format definitions, so that any diagram objects that meet more than one dynamic filter will use the settings of the dynamic filter with the highest set priority.

Allow Oneline to use dynamic formatting defined with case

This option will only be available when the dynamic formatting settings correspond to an active oneline. It indicates whether or not the oneline diagram will use the dynamic formatting definitions specified in the case.

Object Type

The type of power system object with graphical representation, such as a bus, a load, a generator, etc.

Filter Criteria

The filter that applies to the object type defined. The Dynamic Formatting settings will apply to the graphical object only if the corresponding power system object meets the specified filter. If the criteria box is empty, the Dynamic Formatting settings will assume that all the objects of the specified type meet the criteria.

Formatting Active

If this option is unchecked, the dynamic formatting definition will be ignored when the objects are rendered. Otherwise, it will be applied if there are graphical objects whose characteristics match the rest of the characteristics defined in this dialog.

Force visibility

When this option is checked, the objects will be displayed (assuming the dynamic formatting applies to them) independently of the visibility of the layer to which such objects belong, and with no regards of the low and high zoom levels.

Show Lookup Tables

Checking this box will display the **Use Lookup** options with the characteristic settings. The **Use Lookup** option with certain field characteristics allow you to define a table of different field values and corresponding characteristic values. If you check Show Lookup tables, and then check the Use Lookup field next to one of the characteristics, you will open the Lookup definition table. This table allows you to select a field for the Object Type you have selected. This field is the field that you define values for in the left column of the lookup table. To insert entries in the lookup table, right-click in the table grid and choose Insert from the popup menu. This will place a default record in the table. Modify the Field Value that Simulator should look for in the table, and a corresponding Characteristic Value that should be used for the field value given. For example, you could use a lookup table with Line Thickness for transmission line objects, where the thickness of the line would vary based on the amount of flow on the line. Different thicknesses could be assigned to different levels of flow using a lookup table.

Context

In the Context Objects, the user will specify what specific type of graphical objects the dynamic formatting will apply to. This list view will be populated with the Case Information Display object (if the dynamic formatting definitions set correspond to the general case), plus the several graphical objects related to the Object Type. (For buses, for example, it will include the graphical bus, the bus fields, and the bus gauge).

Fields

In the Fields list view, the user will be able to select which fields the dynamic formatting settings will apply to. This view will be populated only for those context objects with fields, such as the Case Information Display and the Object Fields. This list is only visible when you choose certain types of context objects in the context objects list.

Show Only Commonly Used Fields

If this option is checked, only a reduced list of selected fields will be displayed. Otherwise, all the fields belonging to the object will be shown.

Characteristics

The characteristics that the user will be allowed to modify dynamically. These include line thickness, style, color, and background color; font name, size, color, and style; highlight color; surround shape, color and thickness; color and magnification of the ‘X’ on top of the objects; and blinking color and interval.

---

<a id="displaybus-property-allowfixednum"></a>

## DisplayBus property AllowFixedNum

*Source: [`Content/MainDocumentation_HTML/FixedNumBusOneline_AllowFixedNum_DisplayBus.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FixedNumBusOneline_AllowFixedNum_DisplayBus.htm)*

Added in Version 24

[DisplayBus objects](11-building-onelines-network-objects.md#bus-display-objects) on a oneline diagram represent a Bus object in the case. There are many features on a oneline diagram that can then be used to insert other objects connected to buses already on the oneline. These include the [Bus Palette](13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes), [Insert Connected Buses](02-simulator-ribbon.md#quick-insert-ribbon-group), [Auto-Insertion of Lines](13-building-onelines-graphics-and-insertion.md#automatically-inserting-transmission-lines), [Auto-Insertion of Gens](13-building-onelines-graphics-and-insertion.md#automatically-inserting-generators), [Auto-Insertion of Loads](13-building-onelines-graphics-and-insertion.md#automatically-inserting-loads), and [Auto-Insertion of Shunts](13-building-onelines-graphics-and-insertion.md#automatically-inserting-switched-shunts), as well as the behavior of [anchoring other display objects](11-building-onelines-network-objects.md#anchored-objects) to the DisplayBus.

A DisplayBus which represents a Bus that has been [designated the FixedNumBus](08-view-case-data-tools.md#fixednumbus-features) by another Bus can be modified to act as though it represents all the Buses within the FixedNumBus grouping. This is done by checking a box on the Bus Information Dialog that says "Allow to act as a Fixed Number Bus (impacts auto insertion routines). This may be also set if the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display) or by an AXD file by setting the AllowFixedNum field for a DisplayBus object to YES.

![FixedNumBusOneline AllowFixedNum](images/FixedNumBusOneline_AllowFixedNum.png)

The various features that auto insert devices on oneline diagrams will behave differently when this flag is set. This concept has been around in PowerWorld Simulator since about 2000 when PowerWorld first introduced the concept of a Substation object to the power system model. When you are adding a generator to a oneline the software will search for a DisplayBus, and if this is not found, then a DisplaySubstation object will be search for. Similarly when you auto insert generators, loads, shunts or lines on a oneline diagram simulator will first look for the terminal DisplayBus, and if that is not found the Substation will be looked for. These concepts will be extended with the addition of the field AllowFixedNum for the DisplayBus. The priority will now be three levels so that when a device is being added it looks for its terminal buses using the following priority.

1.  If a DisplayBus representing the device's terminal bus exists and AllowFixedNum = NO, then the DisplayBus is used.

2.  Otherwise, if a DisplayBus representing the FixedNumBus of the device's terminal bus exists and AllowFixedNum = YES, then the DisplayBus is used.

3.  Otherwise, if a DisplaySubstation representing the Substation of the device's terminal bus exists, then the DisplaySubstation is used.

Users have always been able to create onelines that contain a mixture of DisplayBus and DisplaySubstation objects, but in practice users typically do one or other. Our expectation is similar with onelines that user AllowFixedNum = YES, so the default behavior of dialogs will act differently depending on what is on the oneline. When a DisplayBus has been set with AllowFixedNum=YES, then the following features will change.

<table>
<tbody>
<tr class="odd">
<td><p>DisplayBus Feature</p></td>
<td><p>Modified Behavior when AllowFixedNum= YES</p></td>
</tr>
<tr class="even">
<td><p>Bus Palette</p>
<p><a href="13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes" class="MCXref xref">Using the Insert Palettes</a></p></td>
<td><p>A checkbox on the palette for Only Show FixedNumBus will be available. When checked the Displayed and Undisplayed bus lists will show only buses with FixedNumBus = BusNum. Also, Neighbor lists show connections between 2 FixedNumBus groupings.</p>
<p>The new display objects added from the Bus Palette will set the AllowFixedNum based on the Only Show FixedNumBus checkbox.</p>
<p>When the Bus Palette is opened by right-clicking on a DisplayBus then the checkbox will be set according to the DisplayBus's AllowFixedNum field. When the Bus Palette is opened from the Ribbon Menu, then an internal calculation is done and if more than half of the DisplayBus objects already on the online have AllowFixedNum = YES then the checkbox is checked. If oneline does not have any DisplayBus objects on it yet, then the box will be checkeds if more than 5% of the buses in the case have been assigned to FixedNumBus other than itself.</p></td>
</tr>
<tr class="odd">
<td><p>Insert Connected Buses</p>
<p><a href="02-simulator-ribbon.md#quick-insert-ribbon-group" class="MCXref xref">Quick Insert Ribbon Group</a></p></td>
<td><p>New DisplayBuses are added for buses with Number=FixedNumBus only with connections between the 2 FixedNumBus groupings. New DisplayBus objects added to the oneline will have the same AllowFixedNum setting as the bus that was clicked on to activate this action.</p></td>
</tr>
<tr class="even">
<td><p>Auto-Insertion of Lines, Loads, Gens, and Shunts</p>
<p><a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-transmission-lines" class="MCXref xref">Automatically Inserting Transmission Lines</a></p>
<p><a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-generators" class="MCXref xref">Automatically Inserting Generators</a></p>
<p><a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-loads" class="MCXref xref">Automatically Inserting Loads</a></p>
<p><a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-switched-shunts" class="MCXref xref">Automatically Inserting Switched Shunts</a></p></td>
<td><p>Auto-insertion routines look first for terminal buses and insert at those locations if they are present. If terminals are not present, routines look for the FixedNumBus instead.</p></td>
</tr>
<tr class="odd">
<td><p>Anchoring of Lines, Gens, Loads and Shunts</p></td>
<td><p>Same as for auto-insert. Preference is for the actual terminal bus, but FixedNumBus is also allowed</p></td>
</tr>
</tbody>
</table>

Bus Palette Only Show FixedNumBus

Consider as an example opening the Bus Palette for a full topology as depicted in the image below. The Blue regions represent the FixedNumBus groupings.

![FixedNumBus FixedNumBus](images/FixedNumBus_FixedNumBus.png)

The bus palette behavior will appear differently depending on the **Only Show FixedNumBus**.

![FixedNumBusOneline BusPalette](images/FixedNumBusOneline_BusPalette.png)
