---
title: "The Simulator Ribbon"
part: "Getting Started"
chapter_file: "02-simulator-ribbon.md"
topics: 21
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# The Simulator Ribbon

Every ribbon tab, group and button in the Simulator UI.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (21)**

- [Ribbons User Interface](#ribbons-user-interface)
- [Quick Access Toolbar](#quick-access-toolbar)
- [Add Ons Tab Overview](#add-ons-tab-overview)
- [Case Information Tab Overview](#case-information-tab-overview)
- [Draw Tab Overview](#draw-tab-overview)
- [Clipboard Ribbon Group](#clipboard-ribbon-group)
- [Formatting Ribbon Group](#formatting-ribbon-group)
- [Individual Insert Ribbon Group](#individual-insert-ribbon-group)
- [Quick Insert Ribbon Group](#quick-insert-ribbon-group)
- [Select Ribbon Group](#select-ribbon-group)
- [Onelines Tab Overview](#onelines-tab-overview)
- [Active Ribbon Group](#active-ribbon-group)
- [Zoom Ribbon Group](#zoom-ribbon-group)
- [Options Tab Overview](#options-tab-overview)
- [Solution Options Menu](#solution-options-menu)
- [Tools Tab Overview](#tools-tab-overview)
- [Edit Mode  Ribbon Group](#edit-mode-ribbon-group)
- [Other Tools  Ribbon Group](#other-tools-ribbon-group)
- [Run Mode Ribbon Group](#run-mode-ribbon-group)
- [Simulation Control](#simulation-control)
- [Window Tab Overview](#window-tab-overview)

---

<a id="ribbons-user-interface"></a>

## Ribbons User Interface

*Source: [`Content/MainDocumentation_HTML/Ribbons.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbons.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld's user interface consists of a ribbon across the top of the program. Important terminology regarding the ribbon is depicted in the images below.

![Ribbon Terms](images/Ribbon_Terms.gif)

<table>
<tbody>
<tr class="odd">
<td><p>Ribbon</p></td>
<td><p>The entire strip across the top is called the ribbon</p></td>
</tr>
<tr class="even">
<td><p>Ribbon Tab</p></td>
<td><p>The ribbon consists of several ribbon tabs which group together features of the software that are used together. There are seven ribbons which have their own purposes and own help topics listed as follows.</p>
<ul>
<li><a href="#case-information-tab-overview">Case Information Ribbon Tab</a>: primarily used to navigate and look through all the data in your model.</li>
<li><a href="#draw-tab-overview">Draw Ribbon Tab</a>: primarily used to draw new oneline diagrams or edit existing onelines by adding, moving, formatting, or resizing existing oneline objects. Most of the options on the <a href="#draw-tab-overview">Draw</a> ribbon tab are only available in <a href="01-getting-started.md#edit-mode-introduction">Edit Mode</a>.</li>
<li><a href="#onelines-tab-overview">Onelines Ribbon Tab</a>: primarily used after you have already created a oneline diagram. This ribbon provides features for customizing the appearance of your oneline diagram.</li>
<li><a href="#tools-tab-overview">Tools Ribbon Tab</a>: this ribbon provides access to all of the analysis tools that are available in the base package of PowerWorld Simulator. You will use this ribbon when you are performing power flow analysis, contingency analysis, or using the sensitivities tools.</li>
<li><a href="#tools-tab-overview"></a><a href="#options-tab-overview">Options Ribbon Tab</a>: all of the buttons on this ribbon are also available on one of the other ribbons, however this ribbon brings all the options in the software into one place.</li>
<li><a href="#add-ons-tab-overview">Add Ons Ribbon Tab</a>: this ribbon provides access to all of the add-on tools available for Simulator including the OPF, SCOPF, PVQV, ATC, Transient Stability, GIC Calculations, Scheduled Actions, and Topology Processing tools. If you have not purchased these tools then the options will be grayed out.</li>
<li><a href="#window-tab-overview">Window Ribbon Tab</a>: this ribbon provides access to customizing the Windows in the User Interface. It also has some information regarding help topics .</li>
</ul>
<p>The goal in designing these ribbons was to create several task specific ribbons which represent the various ways that the software is used. Our hope is that you will not spend a lot of time flipping back and forth between ribbons. If you find yourself doing this please contact PowerWorld Corporation to help us make the software better for the future.</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>Ribbon Group</p></td>
<td><p>Inside a particular ribbon tab, there are around 4 to 7 groupings called ribbon groups. The following image shows three ribbon groups (Individual Insert, Select, and Formatting) with various buttons and menus available.</p>
<p><img src="images/Ribbon_Buttons.gif" alt="Ribbon Buttons" /></p>
<p>Ribbon groups join sets of buttons and menus that are related to one another. The large buttons and icons are used to draw attention to the most commonly used features of the software. All features are still available through drop-down menus in the same manner as was available previously. Our design goal in creating and laying out the ribbons was to provide the new user with insight about using the software, while at the same time giving the experienced user quick access to common features.</p>
<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Large Button</p></td>
<td><img src="images/Ribbon_Button_Large.gif" alt="Ribbon Button Large" /></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Large Button</p>
<p>Menu</p></td>
<td><img src="images/Ribbon_Button_Large_Menu.gif" alt="Ribbon Button Large Menu" /></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Small Button</p>
<p>With Caption</p></td>
<td><img src="images/Ribbon_Button_Small_Caption.gif" alt="Ribbon Button Small Caption" /></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Small Button</p>
<p>Menu</p></td>
<td><img src="images/Ribbon_Button_Small_Menu.gif" alt="Ribbon Button Small Menu" /></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Small Button</p>
<p>without Caption</p></td>
<td><img src="images/Ribbon_Button_Small_no_Caption.gif" alt="Ribbon Button Small no Caption" /></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Menu</p>
<p>Only Caption</p></td>
<td><img src="images/Ribbon_Button_Menu_Only.gif" alt="Ribbon Button Menu Only" /></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
<tr class="even">
<td><p>Help Button</p>
<p><img src="images/Ribbon_Help_Icon.gif" alt="Ribbon Help Icon" /></p></td>
<td><p> </p>
<p>Clicking the help button on the right edge of the ribbon brings up the online help</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>Quick Access Toolbar</p></td>
<td><p>The quick access toolbar at the top left of the ribbon (near the Application Button) contains small buttons with no caption that are always visible. For more information about how to use and customize this see the <a href="#quick-access-toolbar">Quick Access Toolbar</a> help.</p>
<p><img src="images/Ribbon_Quick_Access_Toolbar.gif" alt="Ribbon Quick Access Toolbar" /></p>
<p> </p></td>
</tr>
<tr class="even">
<td><p>Application Title Bar</p></td>
<td><img src="images/Ribbon_Application_Title_Bar.gif" alt="Ribbon Application Title Bar" /></td>
</tr>
<tr class="odd">
<td><p>File Menu</p>
<p><img src="images/File_Menu_Icon.gif" alt="File Menu Icon" /></p></td>
<td><p>Click on this to bring up the Application File Menu shown below. For more information about using the <a href="03-cases-files-and-formats.md#file-menu">File Menu</a> see the <a href="03-cases-files-and-formats.md#file-menu">File Menu</a> help.</p>
<p><img src="images/File_Menu.gif" alt="File Menu" /></p></td>
</tr>
</tbody>
</table>

---

<a id="quick-access-toolbar"></a>

## Quick Access Toolbar

*Source: [`Content/MainDocumentation_HTML/Ribbon_QuickAccess.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_QuickAccess.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Ribbon Quick Access Toolbar provides you with quick access to the most frequently used buttons. These buttons are found in the top left portion of the Ribbon just above the [File menu](03-cases-files-and-formats.md#file-menu). The default buttons that appear in the Quick Access Toolbar are shown in the figure below.

![Ribbon Quick Access Toolbar](images/Ribbon_Quick_Access_Toolbar.gif)

The eight default buttons are as follows from left to right.

  - [Save Case](03-cases-files-and-formats.md#saving-cases)
  - [Open Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)
  - [Display Bus View](08-view-case-data-tools.md#bus-view-display)
  - [Message Log](01-getting-started.md#message-log)
  - [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options)
  - [Solve Power Flow](#simulation-control)
  - [Abort](#tools-tab-overview)

The Quick Access Toolbar can also be customized very simply. If you find a button that you would like quicker access to, simply right-click on the button and then choose **Add to Quick Access Toolbar**. The small icon version of the button will then immediately appear up in the Quick Access Toolbar. This is depicted in the image below.

![Ribbon Add to Quick Access Toolbar](images/Ribbon_Add_to_Quick_Access_Toolbar.gif)

The Quick Access Toolbar can also be modified to **Show the Toolbar Below the Ribbon** providing more space for specifying buttons.

The **Minimize the Ribbon** option can be useful when computer screen size is limited.

---

<a id="add-ons-tab-overview"></a>

## Add Ons Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Add_Ons.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Add_Ons.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Add Ons ribbon consists of buttons and menus that provide access to the various Simulator Add On Tools. The ribbon is shown below when configured for the OPF, SCOPF, PVQV, ATC, Transient Stability, GIC Calculations, Scheduled Actions, and Topology Processing add on tools.

![Ribbon Add Ons](images/Ribbon_Add_Ons.gif)

 The Add Ons ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Log Ribbon Group

> ![Ribbon Tools Abort](images/Ribbon_Tools_Abort.gif)Abort 
> 
> Terminates the current Power Flow Solution. If the application is performing a timed simulation, pressing the abort button will pause the simulation. See [PowerWorld Simulation Control](#simulation-control) for more details.
> 
> ![Ribbon Tools Log](images/Ribbon_Tools_Log.gif)Log
> 
> Toggles the display of the [message log](01-getting-started.md#message-log) window. The log window shows what is going on with the Power Flow Solution process and may prove useful when you are trying to track down a problem with a non-converging model.
> 
> ![Ribbon Tools Script](images/Ribbon_Tools_Script.gif) Script
> 
> Opens the Script dialog, which can be used to call script commands or open [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) containing script commands and data modifications. Note that the drop-down next to the Script button give convenient access to the [Quick Auxiliary Files](09-auxiliary-files-and-script-commands.md#quick-auxiliary-files-dialog).

 Optimal Power Flow (OPF) Ribbon Group

> Primal LP 
> 
> Click this button to solve the OPF. A more detailed description of what this does is found in the topic [OPF LP Primal](30-optimal-power-flow-part1.md#opf-primal-lp).
> 
> Security Constrained OPF
> 
> Click this button to open the [Security Constrained OPF Dialog](31-scopf-and-opf-reserves.md#scopf-dialog).
> 
> OPF Options and Results
> 
> Click this button to open the [OPF Options and Results Dialog](30-optimal-power-flow-part1.md#opf-options).
> 
> OPF Case Info Menu
> 
> The OPF Case Info Menu provides direct access to several case information displays that show default columns related to input and output of the Optimal Power Flow. Instead of using this menu, PowerWorld encourages you leave the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) open and navigate using the Explore Pane on the Model Explorer. All of these options are available under the Optimal Power Flow folder on the Model Explorer.
> 
> ![Ribbon Add Ons OPF Case Info](images/Ribbon_Add_Ons_OPF_Case_Info.gif)

 PV and QV Curve (PVQV) Ribbon Group 

> PV Curves 
> 
> Click this button to open the [PV Curves dialog](29-pv-and-qv-curves.md#dialog).
> 
> QV Curves
> 
> Click this button to open the [QV Curves dialog](29-pv-and-qv-curves.md#qv-curves).
> 
> Refine Model
> 
> Click this button to open the [Refine Model Dialog](29-pv-and-qv-curves.md#pvqv-refine-model).

Available Transfer Capability Ribbon Group

> Available Transfer Capability
> 
> Click this button to open the [Available Transfer Capability Dialog](32-available-transfer-capability.md#available-transfer-capability-dialog).

Transient Stability (TS) Ribbon Group 

> Transient Stability
> 
> Click this button to open the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog).
> 
> Stability Case Info Menu
> 
> The [Stability Case Info Menu](36-transient-stability-overview-and-data-part2.md#case-info-menu) provides direct access to several case information displays that show default columns related to input and output of the transient stability tool.

GIC Calculations Ribbon Group

> GIC Calculations
> 
> Click this button to open the [GIC Analysis Form](47-geomagnetically-induced-currents.md#gic-analysis-dialog). This dialog is used for performing [GIC Analysis](47-geomagnetically-induced-currents.md#gic-analysis).

Schedule Ribbon Group

> Scheduled Actions....
> 
> Click this button to open the [Scheduled Actions Dialog](48-scheduled-actions.md#scheduled-actions-dialog). This dialog is used for looking at [Scheduled Actions](48-scheduled-actions.md#scheduled-actions-tool).

Topology Processing Ribbon Group 

> Topology Processing
> 
> Click this button to open the [Topology Processing Dialog](35-integrated-topology-processing.md#integrated-topology-processing-dialog).

---

<a id="case-information-tab-overview"></a>

## Case Information Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Case_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Case_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Case Information ribbon consists of buttons and menus that provide access to the information about the power system model. The ribbon is shown below:

![Ribbon Case Information](images/Ribbon_Case_Information.gif)

 The Case Information ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Case Information Ribbon Group

> Model Explorer 
> 
> ![ModelExplorerButton](images/ModelExplorerButton.gif) Opens the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) giving access to all the [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) for the model.
> 
> Area/Zone Filters   
> 
> ![AreaZoneFilterButton](images/AreaZoneFilterButton.gif)Opens the [Area/Zone/Owner Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) display which allows filtering of the case information displays by Area, Zone, and Owner.
> 
> Limit Monitoring
> 
> Opens the [Limit Monitoring Settings and Limit Violations Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog) which allows you to specify what to monitor in the various analysis tools.
> 
> Menus for Network, Aggregation, and Solution Details
> 
> These three menus all perform the same action as opening the Model Explorer, except that they automatically set the Explore Pane of the Model Explorer to show the respective case information display. Instead of using these menus, PowerWorld encourages you leave the Model Explorer open and navigate using the Explore Pane on the Model Explorer.

Case Data Ribbon Group

> Difference Flows Menu
> 
> ![Ribbon Tools Difference Flows](images/Ribbon_Tools_Difference_Flows.gif)
> 
> Difference Case: Opens the [Difference Case Dialog](08-view-case-data-tools.md#difference-case)
> 
> Present Topological Differences From Base: Opens the [Present Topological Differences From Base Dialog.](08-view-case-data-tools.md#present-topological-differences-from-base-case)
> 
> The remaining options in this menu all replicate the same behavior available on the [Difference Case Dialog](08-view-case-data-tools.md#difference-case). For more details go to that help topic.
> 
> Data Check Added in Version 20 patch on April 9, 2018
> 
> Opens the [Data Check Overview](08-view-case-data-tools.md#data-check-overview) .
> 
> Simulator Options 
> 
> Opens the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options).
> 
> Case Description
> 
> Opens the [Case Description Dialog](05-case-information-displays-by-object-part1.md#case-description).
> 
> Case Summary
> 
> Opens the [Case Summary Dialog](05-case-information-displays-by-object-part1.md#case-summary).
> 
> Custom Case Info
> 
> Opens the [Custom Case Information Display.](04-model-explorer-and-case-information-part3.md#custom-case-information-display)
> 
> Power Flow List 
> 
> Opens the [Power Flow List.](05-case-information-displays-by-object-part1.md#power-flow-list)
> 
> Quick Power Flow List 
> 
> Opens the [Quick Power Flow List.](05-case-information-displays-by-object-part1.md#quick-power-flow-list)
> 
> AUX Export Format Desc 
> 
> Opens the [Auxiliary File Export Format Description Dialog](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system) for Power System Objects.

Views Ribbon Group

> Bus View
> 
> Opens the [Bus View Oneline](08-view-case-data-tools.md#bus-view-display) which provides a graphical display that allows you to quickly browse information about a bus and everything connected to that bus.
> 
> Substation View
> 
> Opens the [Substation View Oneline](08-view-case-data-tools.md#substation-view-display) which provides a graphical display that allows you to quickly browse information about a bus and everything connected to that substation.
> 
> Oneline Viewer
> 
> Opens the [Oneline Viewer dialog](52-additional-linked-topics-part1.md#oneline-viewer) which provides a convenient way to browse available onelines.
> 
> Data View Added in Version 20
> 
> Opens the [](52-additional-linked-topics-part1.md#oneline-viewer) [Data View](08-view-case-data-tools.md#data-view) which provides a convenient way to sbrowse the fields of one object.
> 
> Open Windows Menu
> 
> The Open Windows Menu provides a convenient method of switching between open windows. This includes User Interface Dialogs, Case Information Displays, and Oneline diagrams.
> 
> ![Ribbon Case Information Open Windows](images/Ribbon_Case_Information_Open_Windows.gif)

---

<a id="draw-tab-overview"></a>

## Draw Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Draw.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Draw.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Draw ribbon tab is primarily used to draw new oneline diagrams or edit existing onelines by adding, moving, formatting, or resizing existing oneline objects. Most of the options on the Draw ribbon tab are only available in [Edit Mode](01-getting-started.md#edit-mode-introduction). The Draw ribbon tab is shown below.

![Ribbon Draw](images/Ribbon_Draw.gif)

The Draw ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Quick Insert Ribbon Group

> The Quick Insert ribbon group contains buttons for creating a oneline diagram for a system model you have already read into Simulator. If you are building out your network (or even substation, area, or zone diagram), using the Insert Palettes along with the Auto Insert routines is most efficient. For detailed help see the [Quick Insert](#quick-insert-ribbon-group) ribbon group. If you would instead like help on inserting a single object on your oneline diagram see the [Individual Insert](#individual-insert-ribbon-group) ribbon group topic.

Individual Insert Ribbon Group 

> The Individual Insert ribbon group contains menus which provide access to buttons for inserting individual oneline objects to the oneline diagram. If you are building out your network (or even substation, area, or zone diagram), it is much more efficient to use the [Quick Insert](#quick-insert-ribbon-group) ribbon group. However, for complete access to all objects including those that can not be "quick - inserted", see the help under the [Individual Insert](#individual-insert-ribbon-group) ribbon group topic.

Select Ribbon Group 

> The Select ribbon group contains options to help select multiple oneline objects simultaneously. For more detailed help see the [Selection](#select-ribbon-group) ribbon group topic for more detailed help.

Formatting Ribbon Group

> The Format ribbon group contains options for formatting the selected objects on your active oneline. For more detailed help see the [Formatting](#formatting-ribbon-group) ribbon group topic for more detailed help.

Clipboard Ribbon Group

> The Clipboard ribbon group contains options for copying and pasting oneline display objects. For more detailed help see the [Clipboard](#clipboard-ribbon-group) ribbon group topic for more detailed help.

 Zoom Ribbon Group

> The Zoom ribbon group contains buttons for navigating a oneline diagram. For more detailed help see the [Zoom](#zoom-ribbon-group) ribbon group topic

---

<a id="clipboard-ribbon-group"></a>

## Clipboard Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Draw_Clipboard.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Draw_Clipboard.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Clipboard ribbon group contains options for copying and pasting oneline objects while you are in [Edit Mode](01-getting-started.md#edit-mode-introduction). It also provides access to the Undo drawing feature. This ribbon group is on the [Draw](#draw-tab-overview) ribbon tab. The Group is shown below.

> ![Ribbon Group Draw Clipboard](images/Ribbon_Group_Draw_Clipboard.gif)
> 
> Undo
> 
> The Undo command is used in the edit mode to undo the last change made on the oneline diagram. The Undo command will only undo graphical changes, and will not undo any data changes in the power system model. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for information on the display/model relationships.
> 
> Paste
> 
> The paste command copies the contents of the paste buffer (if any) onto the display at the current cursor location. Use the **Paste** command from the Edit Menu. Note that the paste buffer may contain both display objects and the underlying power system records. When pasting, the display objects are pasted regardless of whether an identical display object already exists on the oneline. In contrast, duplicate power system records are never pasted. This is because, for example, it is acceptable to have two display objects referring to the same generator, but the generator exists only as a single entity in the power system model. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for further details.
> 
> Paste Special
> 
> Paste Special works the same as Paste, however it will also show a dialog asking you to choose between
> 
> **Absolute Coordinates** : objects will be pasted using the exact same x/y coordinate as the copied objects had. This is useful when copying objects between two different oneline diagrams which contain the same geographic background.
> 
> **Coordinates Relative to Cursor** : objects will be pasted relative to cursor instead of using the exact x/y coordinates as the copied objects.
> 
> Copy
> 
> The Copy Command copies the currently selected object(s) into the paste buffer without deleting them. For power system objects, such as buses, generators or transmission lines, you are given an option of whether to copy just the display object(s), or copy both the display object(s) and their underlying power system records. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for further explanation of these choices. To copy only the display object(s) and never the power system records from now on, select the **Always Copy Object(s) Only** option. You will not be prompted again. You can disable this selection on the [Default Drawing Options Dialog](14-editing-onelines.md#default-drawing-values).
> 
> Cut
> 
> The Cut Command is used in the Edit Mode to delete the currently selected object(s). To delete a set of objects, first select the objects. Then select the Cut command from the Edit Menu. For power system objects, such as buses, generators or transmission lines, you are given an option of whether to delete just the display object(s), or delete both the display object(s) and their underlying power system records. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for further explanation of these choices. To delete only the display object(s) and never the power system records from now on, select the **Always Delete Object(s) Only** option. You will not be prompted again. You can disable this selection on the [Default Drawing Options Dialog](14-editing-onelines.md#default-drawing-values). 
> 
> Unlike Delete, Cut also copies the selection into the paste buffer.
> 
> Delete
> 
> The Delete Command is used in the Edit Mode to delete the currently selected object(s). To delete a set of objects, first select the objects. Then select the Delete command from the **Edit** menu. For power system objects, such as buses, generators or transmission lines, you are given an option of whether to delete just the display object(s), or delete both the display object(s) and their underlying power system records. See [Relationship Between Display Objects and the Power System Model](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model) for further explanation of these choices. To delete only the display object(s) and never the power system records from now on, select the **Always Delete Object(s) Only** option. You will not be prompted again. You can disable this selection on the [Default Drawing Options Dialog](14-editing-onelines.md#default-drawing-values). 
> 
> Unlike Cut, Delete does not copy the selection into the paste buffer.

---

<a id="formatting-ribbon-group"></a>

## Formatting Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Draw_Formatting.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Draw_Formatting.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Formatting** ribbon group contains options for formatting the selected objects on your active oneline. This group is on the [Draw](#draw-tab-overview) ribbon tab and its options are available only in Edit mode. The options allow you to control such display object attributes as font, color, line styles, zoom-dependent vissibility, and display layer level. The group is shown below.

![Ribbon Group Draw Formatting](images/Ribbon_Group_Draw_Formatting.gif) 

A description of the actions on this group are as follows.

** ** ![Ribbon Draw Format](images/Ribbon_Draw_Format.gif)**Format Buttons**

Clicking this button will open the [Format Dialog](14-editing-onelines.md#format-selection-dialog). The dialog which opens will have five tabs as follows.

> Font 
> 
> Select this option to change the font with which the selected objects are displayed. The [Font Tab](14-editing-onelines.md#font-properties) of the Format Selection Dialog is displayed.
> 
> Line/Fill
> 
> Select this option to change the line thickness and style with which a display object is drawn, or the fill color for closed shapes. The [Line/Fill Tab](14-editing-onelines.md#linefill-properties) of the Format Selection Dialog is displayed.
> 
> Levels/Layers
> 
> Select this option to change the stack level of an object, the layer the object is contained in, and optional settings for when an object should resize. The [Levels/Layers Tab](14-editing-onelines.md#levelslayers-options) of the Format Selection Dialog is displayed.
> 
> Display/Size
> 
> Simulator can change the attributes of the way multiple objects are displayed using this option, which opens the [Display/Size page](14-editing-onelines.md#other-display-object-properties) of the Format Selection Dialog. The size of the objects can be adjusted, as well as the orientation of the object(s) from their terminal buses. Objects can also be Anchored to their terminal buses or devices, or marked as Immobile, meaning the object(s) cannot be moved on the oneline diagram.
> 
> Field
> 
> Select this option to change the attributes related to object text fields which are selected. The [Field Tab](14-editing-onelines.md#format-field-properties) of the Format Selection Dialog is displayed.

**Anchors**

Invokes a command to [refresh anchors](14-editing-onelines.md#refreshing-anchors) on all oneline objects.

**** ![Ribbon Draw Format Copy](images/Ribbon_Draw_Format_Copy.gif)**Copy Format and Paste Format Buttons**

The button on the left is the **Copy Format** button. After selecting an object this will copy all the format properties of that object into an internal buffer. When you then subsequently select other objects, you can click on the button on the right which is the **Paste Format** button. Clicking the **Paste Format** button will bring up the [Paste Format Dialog](14-editing-onelines.md#paste-format-dialog).

**** ![Ribbon Draw SendBackBringFront](images/Ribbon_Draw_SendBackBringFront.gif)**Send to Back, Bring to Front Buttons**

After selecting a group of oneline objects using any of the methods described on the [Select](#select-ribbon-group) ribbon group, you may then click the **Send to Back** button to cause all the objects selected to move to underneath other objects. Click the **Bring to Front** button to bring objects to the top.

The Send to Back and Bring to Front menu options govern the visibility of display objects that occupy the same screen stack level. All objects have an associated screen stack level, which may be one of Base, Background, Middle, or Top. Objects having a screen stack level of Top obscure all objects having stack levels of Middle, Background, or Base that occupy the same region of the screen. They may or may not obscure objects having the same stack level of Top depending on the order in which the objects having the same stack level are drawn. Selecting Send to Back for a selected object will cause it to be obscured by all other same-level objects that occupy its location. Selecting Bring to Front for a selected object will cause it to be drawn above all other same-level objects that occupy the same region of the screen. The Send to Back and Bring to Front menu options govern relative placement of objects only *within* stack levels. The Send to Back and Bring to Front options do not affect the relative placement of objects having different stack levels.

Alignment Menu

The alignment menu provides access to the [Alignment Dialog](14-editing-onelines.md#align-group-objects) and direct access to options to align the selected objects as specified in the menu items.

Grouping Menu

Grouping is only available for background oneline objects (background lines, ellipses, text, etc...). This menu provides button to Group and Un-Group objects.

Layers Menu 

The Layers Menus provide access for opening the [Define Layers Dialog](14-editing-onelines.md#screen-layers) for the presently active oneline diagram.

Underneath the button for defining layers is a list of the presently defined layers. You may check or uncheck the various layers to hide or show the objects in those layers.

![Ribbon Onelines Screen Layers](images/Ribbon_Onelines_Screen_Layers.gif)

---

<a id="individual-insert-ribbon-group"></a>

## Individual Insert Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Draw_IndividualInsert.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Draw_IndividualInsert.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Individual Insert ribbon group contains menus which provide access to buttons for inserting individual oneline objects to the oneline diagram. If you are building out your network (or even substation, area, or zone diagram), then it is much more efficient to use the [Quick Insert Group](#quick-insert-ribbon-group). The Individual Insert group is shown below.

![Ribbon Group Draw Individual Insert](images/Ribbon_Group_Draw_Individual_Insert.gif)

The six menus available on the group categorize the objects that can be placed on the oneline diagrams. A summary of what is in each menu is described blow along with a picture of each of the six menus.

Network Menu

The objects in this menu represent network model objects. Generally these represent actual physical devices such as a generator or transmission line. They are similar to the model objects found in the **Network** Folder on the Explore Pane of the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

Aggregation Menu

The objects in this menu represent model objects that represent an aggregation of other model objects such as interfaces or injection groups. They are similar to the data objects found in the **Aggregation** Folder on the Explore Pane of the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

Background Menu

The objects in this menu represent objects that are only background text and do not link to any of the objects you would look at in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). Some of the objects link to external objects such as documents, but not to elements of the model.

Pies/Gauges Menu

The objects in this menu represent pie charts or gauges which link to the model data found in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)

Field Menu

The objects in this menu represent fields which link to the model data found in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)

Indication Menu

The objects in this menu represent indications of status or flow for objects that are found in the model data found in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)

|                                                                                                      |                                                                                      |                                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| ![Ribbon Draw Individual Network](images/Ribbon_Draw_Individual_Network.gif)                         | ![Ribbon Draw Individual Aggregation](images/Ribbon_Draw_Individual_Aggregation.gif) | ![Ribbon Draw Individual Background](images/Ribbon_Draw_Individual_Background.gif) |
| ![Ribbon Draw Individual Individual PieGauge](images/Ribbon_Draw_Individual_Individual_PieGauge.gif) | ![Ribbon Draw Individual Field](images/Ribbon_Draw_Individual_Field.gif)             | ![Ribbon Draw Individual Indication](images/Ribbon_Draw_Individual_Indication.gif) |

---

<a id="quick-insert-ribbon-group"></a>

## Quick Insert Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Draw_QuickInsert.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Draw_QuickInsert.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Quick Insert ribbon group contains buttons for creating a oneline diagram for a system model you have already read into Simulator. If you are building out your network (or even substation, area, or zone diagram), then using the Insert Palettes along with the Auto Insert routines is most efficient. If you would instead like help on inserting a single object on your oneline diagram see the [Individual Insert](#individual-insert-ribbon-group) ribbon group topic. Both of the ribbon groups are on the [Draw](#draw-tab-overview) ribbon tab. The Quick Insert ribbon group is shown as follows.

![Ribbon Group Draw Quick Insert](images/Ribbon_Group_Draw_Quick_Insert.gif)

<table>
<tbody>
<tr class="odd">
<td><img src="images/Ribbon_Draw_Quick_Insert_Show_Pallette.gif" alt="Ribbon Draw Quick Insert Show Pallette" /></td>
<td><p>Palette for Menu</p>
<p>Choosing any of the first four items in the Show Insert Palette for Menu will open up its respective Insert Palette. This Insert palettes show a list of all objects that are already shown on the oneline diagram as well as a list of objects which are not. For more information see the <a href="13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes">Using the Insert Palettes</a> help topic.</p>
<p>The <strong>Insert Connected</strong> option will be enabled if a single bus object is selected on the oneline. This submenu provides options to automatically insert any buses not already shown on the oneline that are connected to the selected bus. Additional options allow inserting the connected buses along with connected transmission lines or inserting connected buses along with connected transmission lines, generators, loads, and shunts.</p></td>
</tr>
<tr class="even">
<td><img src="images/Ribbon_Draw_Quick_Insert_Auto_Insert.gif" alt="Ribbon Draw Quick Insert Auto Insert" /></td>
<td><p> Auto Insert Menu</p>
<p>The first six options are used to automatically insert network display objects that are connected to bus objects that have already been drawn on the oneline.</p>
<p><strong>Lines</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-transmission-lines">Automatically Insert Lines Dialog</a></p>
<p><strong>Interfaces</strong> : Shows the <a href="12-building-onelines-branches-and-devices.md#automatically-inserting-interface-display-objects">Automatically Insert Interfaces Dialog</a></p>
<p><strong>Generators</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-generators">Automatically Insert Generators Dialog</a></p>
<p><strong>Loads</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-loads">Automatically Insert Loads Dialog</a></p>
<p><strong>Switched Shunts</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-switched-shunts">Automatically Insert Switched Shunts Dialog</a></p>
<p><strong>Lines, Gens, Loads, Shunts</strong> : Shows a dialog for auto-inserting lines, generators, loads, and shunts simultaneously.</p>
<p><strong>Reset Stub Locations</strong> : Will completely redo the positioning of objects anchored to buses and substations in the manner done when auto-inserting lines, gens, load, and switched shunts.</p>
<p> </p>
<p>The next four options provide methods for adding pie charts, fields, circuit breakers and line flow objects around objects that have already been drawn on the oneline diagram.</p>
<p><strong>Line Flow Pie Charts</strong> : Select this to automatically insert <a href="12-building-onelines-branches-and-devices.md#line-flow-pie-charts-on-onelines">line flow pie charts</a> on the transmission lines or transformers objects that are selected.</p>
<p><strong>Circuit Breakers</strong> : Select this to automatically insert <a href="12-building-onelines-branches-and-devices.md#circuit-breakers-on-onelines">circuit breakers</a> on the transmission lines or transformers objects that are selected.</p>
<p><strong>Line Flow Objects</strong> : Select this option to automatically insert line flow objects on the transmission lines or transformers objects that are selected.</p>
<p><strong>Interface Flow Objects</strong> : Select this option to automatically insert Interface flow objects on the interface objects. The Interface Flow Arrow Object which behaves very similar to the Line Flow Object show an arrow to represent the MW flow direction and then shown text for MW value and Mvar value with a sign relative to the MW flow direction.</p>
<p><strong>Add Fields Around</strong> : Select this option to insert fields around the presently selected objects. It will then bring up the <a href="11-building-onelines-network-objects.md#inserting-and-placing-multiple-display-fields">Inserting and Placing Multiple Display Objects Dialog</a></p>
<p> </p>
<p>The follow two options provide a mechanism for auto-inserting bus or substation oneline objects. You must have geographic longitude/latitude information in order to use these options.</p>
<p><strong>Buses</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-buses">Automatically Insert Buses Dialog</a></p>
<p><strong>Substations</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-substations">Automatically Insert Substations Dialog</a></p>
<p> </p>
<p>The last two options provide a mechanism for inserting background lines that represent geographic borders or from a Shapefile.</p>
<p><strong>Borders</strong> : Shows the <a href="13-building-onelines-graphics-and-insertion.md#automatically-inserting-borders">Automatically Insert Borders Dialog</a></p>
<p><strong>Insert GIS Data From Shapefile</strong> : Shows the <a href="16-oneline-gis-tools.md#shape-file-import">Shapefile Import Dialog</a></p></td>
</tr>
</tbody>
</table>

---

<a id="select-ribbon-group"></a>

## Select Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Draw_Select.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Draw_Select.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Select ribbon group contains options to help select multiple oneline objects simulateously. The features in this topic are only available when you are in [Edit Mode](01-getting-started.md#edit-mode-introduction). This ribbon group is on the [Draw](#draw-tab-overview) ribbon tab. The Group is shown below.

![Ribbon Group Draw Select](images/Ribbon_Group_Draw_Select.gif)

The features available on this ribbon group are described below.

![Ribbon Draw Select By Criteria](images/Ribbon_Draw_Select_By_Criteria.gif)Select by Criteria 

Click on the Select by Criteria button to open the [Select by Criteria Dialog](14-editing-onelines.md#select-by-criteria-dialog). On oneline diagrams of even a modest size, this is an extremely useful feature and PowerWorld highly encourages you to use this feature.

**Select Region**

Use to select all objects in a particular region of the oneline. When the **Region Type** is **Rectangle** or **Ellipse**, then after clicking the button, click and hold the left mouse button on the oneline at the point where you would like to begin the selection. Then, drag the mouse to size the selection shape. Finally, let go of the mouse button once every object you need to select has been selected by the selection rectangle. When the Region Type is Polygon, then after clicking this button single click on your oneline diagram for each vertex of the polygon. Finally, finish the selection by double-clicking the mouse after which all objects inside your polygon will be selected.

Depending on the **Select Mode** below, every object located entirely **Inside** the region, or if you have chosen **Touching**, then every object inside or partially touched will be selected. Selected objects will have handles appear indicating that they have been selected.

**Region Type**

Specify a **Rectangle**, **Polygon**, or **Ellipse**. This controls the shape used to select objects on the oneline diagram when using the **Select Region** button above.

**Select Mode**

This combo box specifies how the **Select Region** button above works. Choose **Inside** in order to select only the objects completely inside the selection rectangle. Choose **Touching** in order to select every object either partially touched by or completely inside the selection rectangle.

There are also other ways to select multiple objects

  - You can also select multiple objects manually by holding down the SHIFT key which clicking on objects in Edit Mode. This will also add to your selection.
  - If you hold down the SHIFT and CTRL keys simultaneously and then click on your oneline diagram and select a region it has the same affect as click on the **Select Region** button and selecting a region on your oneline

---

<a id="onelines-tab-overview"></a>

## Onelines Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Onelines ribbon tab generally consists of buttons and menus that provide access to modifying the appearance of a oneline diagram you have already created. For access to features regarding adding, moving, resizing, and formatting objects, see the Draw ribbon tab. The Oneline ribbon is shown below.

![Ribbon Onelines](images/Ribbon_Onelines.gif)

The Options ribbon consists of buttons and menus that provide access to customizing the software options. The ribbon is shown below.

 Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Active Ribbon Group

> The Active ribbon group contains basic methods for customizing the appearance of basic analysis tools for customizing an existing oneline diagram. For more detailed help see the [Active](#active-ribbon-group) ribbon group topic

Zoom Ribbon Group

> The Zoom ribbon group contains buttons for navigating a oneline diagram. For more detailed help see the [Zoom](#zoom-ribbon-group) ribbon group topic

General Options Ribbon Group

> Dynamic Formatting Menu
> 
> This menu provides access to setting the [Dynamic Formatting Options](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog) that apply to the active oneline, as well as formatting that applies to all onelines and Case Information Displays.[ ](03-cases-files-and-formats.md#auxiliary-file-format-aux)
> 
> ![Ribbon Onelines Dynamic Formatting](images/Ribbon_Onelines_Dynamic_Formatting.gif)
> 
> Custom Hint Values
> 
> Provides access to setting the [Custom Hint Values](15-using-onelines-tools-and-options.md#custom-hint-values) that apply to all oneline objects..
> 
> Default Drawing Values
> 
> Provides access to the [Default Drawing Values](11-building-onelines-network-objects.md#setting-default-drawing-options).
> 
> Toggle Full Screen
> 
> Click this button to cause the presently active oneline to be toggled to full screen.
> 
> Keyboard Shortcuts 
> 
> Click on this button to open the dialog for defining [Keyboard Shortcuts](17-oneline-view-printing-and-contouring.md#keyboard-short-cut-actions-dialog) which allow you to open a oneline or auxiliary file directly from a function key.
> 
> Find Text in Oneline
> 
> Click on this button to open the dialog to [Find Text in Oneline](52-additional-linked-topics-part1.md#find-text-in-oneline-dialog) which will allow you to search for a text in the oneline or its oneline record objects.

 Views Ribbon Group

> Bus View
> 
> Opens the [Bus View Oneline](08-view-case-data-tools.md#bus-view-display) which provides a graphical display which allows you to quickly browse information about a bus and everything connect to that bus.
> 
> Substation View
> 
> Opens the [Substation View Oneline](08-view-case-data-tools.md#substation-view-display) which provides a graphical display which allows you to quickly browse information about a bus and everything connect to that substation.
> 
> Oneline Viewer
> 
> Opens the [Oneline Viewer dialog](52-additional-linked-topics-part1.md#oneline-viewer) which provides a convenient way to browse available onelines.
> 
> Data View Added in Version 20
> 
> Opens the [](52-additional-linked-topics-part1.md#oneline-viewer) [Data View](08-view-case-data-tools.md#data-view) which provides a convenient way to browse the fields of one object.
> 
> Open Windows Menu
> 
> The Open Windows Menu provides a convenient method of switching between open windows. This includes User Interface Dialogs, Case Information Displays, and Oneline diagrams.
> 
> ![Ribbon Case Information Open Windows](images/Ribbon_Case_Information_Open_Windows.gif)

---

<a id="active-ribbon-group"></a>

## Active Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Onelines_Active.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Onelines_Active.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Active ribbon group contains basic methods for customizing the appearance of basic analysis tools for customizing an existing oneline diagram.

![Ribbon Group Onelines Active](images/Ribbon_Group_Onelines_Active.gif)

Oneline Display Options 

Opens the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Contouring and Menu

Click the top part of the button to open the [Contouring Dialog](17-oneline-view-printing-and-contouring.md#contouring-options).

Otherwise, click the drop-down to provide direct access to many of the Contouring Options.

![Ribbon Onelines Contouring](images/Ribbon_Onelines_Contouring.gif)

GIS Tools Menu

Provides access to many Geographic Information System related tools that have been built into the software.

![Ribbon Onelines GIS Tools](images/Ribbon_Onelines_GIS_Tools.gif)

**Insert GIS Data From Shapefile** : Opens the [Shapefile Import dialog](16-oneline-gis-tools.md#shape-file-import).

**Export Oneline as Shapefile** : Choose this to [Export the Oneline as a Shapefile.](16-oneline-gis-tools.md#export-oneline-as-shapefile)

**Import/Export Oneline as KML** : Choose the appropriate option to either create a oneline from or save a oneline to the Keyhole Markup Language (KML). This is a file format used to display geographic data in an earth browser such as Google Earth or Google Maps.

**Populate Lon,Lat with Display X,Y** : Choose this to populate the Bus records latitude and longitude information based on the locations on the present oneline diagram. For more information see the [Populate help topic](16-oneline-gis-tools.md#populate-lonlat-with-display-xy).

**Closest Facilities to Point** : Choose this to bring up the [Closest Facility to Point feature](16-oneline-gis-tools.md#closet-facilities-to-point).

**Great Circle Distance** : Choose this to calculate the [Great Circle Distance between two points](16-oneline-gis-tools.md#great-circle-distance-calculation).

**Insert Measure Line** : Provides access to the [Insert Measure Line Feature](16-oneline-gis-tools.md#insert-measure-line).

**Delete All Measure Lines** : Provides access to the [Delete All Measure Lines feature](16-oneline-gis-tools.md#delete-all-measure-lines).

List Displays Menu

Contains access to several ways of viewing the oneline objects inside of "[case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays)". Of course instead of seeing case information, you instead see information about the oneline objects.

![Ribbon Onelines List Display](images/Ribbon_Onelines_List_Display.gif)

**All Display Objects**: Opens the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display) providing access to all objects on the active oneline.

**Unlinked Display Objects** : Opens the [Unlinked Display Objects Dialog](15-using-onelines-tools-and-options.md#unlinked-display-objects).

**Ony Selected Display Opbjects** : Opens the [Display Explorer](15-using-onelines-tools-and-options.md#display-objects-case-information-display) providing access to objects on the active oneline, but defaults that explorer to only show the presently selected objects.

**Browse Open Onelines**: Brings up the [Browse Open Onelines dialog](18-general-tools.md#browse-open-onelines).

**Display Objects Export Format Description** : Opens a [Display Objects Export Format Description](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system) dialog.

Layers Menu

The Layers Menus provide access for opening the [Define Layers Dialog](14-editing-onelines.md#screen-layers) for the presently active oneline diagram.

Underneath the button for defining layers are options to either Hide All or Show All which will apply the specified action to all objects in all layers. Underneath these options is a list of the presently defined layers. You may check or uncheck the various layers to hide or show the objects in those layers.

![Ribbon Onelines Screen Layers](images/Ribbon_Onelines_Screen_Layers.gif)

Save View

Choose this option to open the [Save Views Dialog](17-oneline-view-printing-and-contouring.md#save-view-level-dialog) or switch between existing views. If a view is named using a back-slash, a subfolder will be created in the list of views. As an example, "New Folder\\View Name", will create a subfolder with the name "New Folder" and this folder will contain the view with the name "View Name".

2D View / 3D View

Toggle between 2D and 3D to change the presently active oneline between the 2D and 3D modes.

---

<a id="zoom-ribbon-group"></a>

## Zoom Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Onelines_Zoom.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Onelines_Zoom.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Zoom Ribbon Group is on both the [Onelines](#onelines-tab-overview) ribbon tab and the [Draw](#draw-tab-overview) ribbon tab. To display large detailed power systems, Simulator’s onelines possess zooming and panning capabilities. The Zoom Ribbon Group enables you to prescribe a zoom level either by directly specifying a zoom value or by selecting a rectangular region of the diagram on which to focus. There is also a button to open a dialog box from which you can select a bus on which to center the display. See [Zooming and Panning](17-oneline-view-printing-and-contouring.md#oneline-zooming-and-panning) for more information.

![Ribbon Group Draw Onelines Zoom](images/Ribbon_Group_Draw_Onelines_Zoom.gif)

This toolbar contains the following several buttons for zooming the presently active oneline.

  - **Zoom Area In /Out** : The top two buttons can be clicked to zoom or out on a particular area of the oneline. When you click these buttons, the cursor will change to a cross-hair waiting for you to choose the region to zoom into (or out of)
  - **Zoom In / Out** : The middle two buttons can be clicked to change your mouse into a zooming tool. After choosing the button with a plus sign, each time you click on the oneline you will zoom in on that location. When choosing the button with a negative sign you will zoom out instead.
  - **Present Zoom Level**: the number represents the present zoom level and can be manually changed to modify the zoom level.
  - **Show Full** : Automatically zooms and pans the presently active oneline diagram so that all objects on the oneline diagram can be seen.
  - **Find**: Provide access to the [Find Object on Oneline Dialog](14-editing-onelines.md#zoom-pan-and-find)

---

<a id="options-tab-overview"></a>

## Options Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Options ribbon consists of buttons and menus that provide access to customizing the software options. All of the buttons on this ribbon are also available on one of the other ribbons, however this ribbon brings all the options in the software into one place. The ribbon is shown below.

![Ribbon Options](images/Ribbon_Options.gif)

The Options ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Case Options Ribbon Group

> Simulator Options  
> 
> Opens the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options).
> 
> Misc. Power Flow Menu
> 
> Provides more direct access to some miscellaneous options that are also found on the Opens the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options).
> 
> Solution Menu
> 
> Provides more direct access to some options related to the power flow solution algorithm. These options are all also available on the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options).
> 
> Case Info Options Menu
> 
> Provides more direct access to some options related to the appearance of case information displays. These options are all also available on the [Case Information Display Options](10-power-flow-solution-and-options-part2.md#case-information-display-options) on the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options).

Oneline Options Ribbon Group

> Oneline Display Options
> 
> Opens the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).
> 
> Pie Chart Menu
> 
> Provides more direct access to options related to Pie Charts. These options are all also available on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog)on the [Pie Charts/Gauges](15-using-onelines-tools-and-options.md#pie-chartgauge-options) page.
> 
> Animation Menu
> 
> Provides more direct access to options related to Animated Arrows. These options are all also available on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) on the [Animated Flows](15-using-onelines-tools-and-options.md#animated-flows-options) page.
> 
> Thumb Nail Menu
> 
> Provides more direct access to options related to Thumb Nail View. These options are all also available on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) on the [ThumbNail View](15-using-onelines-tools-and-options.md#thumbnail-view) page.
> 
> Draw Grid Menu
> 
> Provides more direct access to options related to the Draw Grid. These options are all also available on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).
> 
> Misc. Options Menu
> 
> Provides more direct access to miscellaneous options related to oneline diagrams. These options are all also available on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).
> 
> Saved Options Menu
> 
> This menu provides direct access to the for toggling between different sets of options. These different sets of options are defined on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) by clicking on the **Save Options to Case** button on that dialog..

General Options Ribbon Group

> Dynamic Formatting Menu
> 
> This menu provides access to setting the [Dynamic Formatting Options](17-oneline-view-printing-and-contouring.md#dynamic-formatting-dialog) that apply to the active oneline, as well as formatting that applies to all onelines and Case Information Displays.[ ](03-cases-files-and-formats.md#auxiliary-file-format-aux)
> 
> Custom Hint Values
> 
> Provides access to setting the [Custom Hint Values](15-using-onelines-tools-and-options.md#custom-hint-values) that apply to all oneline objects..
> 
> Default Drawing Values
> 
> Provides access to the [Default Drawing Values](11-building-onelines-network-objects.md#setting-default-drawing-options).
> 
> Toggle Full Screen
> 
> Click this button to cause the presently active oneline to be toggled to full screen.
> 
> Keyboard Shortcuts 
> 
> Click on this button to open the dialog for defining [Keyboard Shortcuts](17-oneline-view-printing-and-contouring.md#keyboard-short-cut-actions-dialog) which allow you to open a oneline or auxiliary file directly from a function key.
> 
> Find Text in Oneline
> 
> Click on this button to open the dialog to [Find Text in Oneline](52-additional-linked-topics-part1.md#find-text-in-oneline-dialog) which will allow you to search for a text in the oneline or its oneline record objects.

Log Ribbon Group

> ![Ribbon Tools Abort](images/Ribbon_Tools_Abort.gif)Abort 
> 
> Terminates the current Power Flow Solution. If the application is performing a timed simulation, pressing the abort button will pause the simulation. See [PowerWorld Simulation Control](#simulation-control) for more details.
> 
> ![Ribbon Tools Log](images/Ribbon_Tools_Log.gif)Log
> 
> Toggles the display of the [message log](01-getting-started.md#message-log) window. The log window shows what is going on with the Power Flow Solution process and may prove useful when you are trying to track down a problem with a non-converging model.
> 
> ![Ribbon Tools Script](images/Ribbon_Tools_Script.gif) Script
> 
> Opens the Script dialog, which can be used to call script commands or open [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) containing script commands and data modifications. Note that the drop-down next to the Script button give convenient access to the [Quick Auxiliary Files](09-auxiliary-files-and-script-commands.md#quick-auxiliary-files-dialog).

---

<a id="solution-options-menu"></a>

## Solution Options Menu

*Source: [`Content/MainDocumentation_HTML/Solution_Options_Menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Solution_Options_Menu.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Solution Options Quick Menu provides access to most of the solution options contained in the [Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options) dialog in an individual manner through menu commands.

![Solution Options Menu](images/Solution_Options_Menu.gif)

This quick menu contains the following default options:

  - Solution Convergence Tolerance (MVA)
  - Maximum Solution Iterations
  - Maximum Outer Control Loop Iterations
  - Enable/Disable Only One Iteration
  - Enable/Disable Optimal Multiplier
  - Enable/Disable Enforcing Generator MW Limits
  - Enable/Disable Automatic Generation Control (ACE)
  - Enable/Disable Generator MVAR Checking
  - Enable/Disable Checking Generator MVAR Immediately
  - Enable/Disable Switched Shunt Control (does not include SVCs)
  - Enable/Disable SVCs
  - Enable/Disable Transformer LTC Control
  - Enable/Disable Phase Shifter Control
  - Enable/Disable Modeling Phase Shifters as Discrete Controls
  - Enable/Disable Preventing Controller Oscillations
  - Set Island-Based AGC Control Type
  - Set Island-Based AGC Tolerance (MW)

---

<a id="tools-tab-overview"></a>

## Tools Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Tools.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Tools.htm)*

The Tools ribbon consists of buttons and menus that provide access to the analysis tools that come with all versions of PowerWorld Simulator. Note: Features related to the various add-on tools including OPF, SCOPF, PVQV Curve, and ATC are found on the [Add Ons](#add-ons-tab-overview) ribbon tab. The tools ribbon is shown below.

![Ribbon Tools](images/Ribbon_Tools.gif)

The Tools ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Log Ribbon Group

> ![Ribbon Tools Abort](images/Ribbon_Tools_Abort.gif)Abort 
> 
> Terminates the current Power Flow Solution. If the application is performing a timed simulation, pressing the abort button will pause the simulation. See [PowerWorld Simulation Control](#simulation-control) for more details.
> 
> ![Ribbon Tools Log](images/Ribbon_Tools_Log.gif)Log
> 
> Toggles the display of the [message log](01-getting-started.md#message-log) window. The log window shows what is going on with the Power Flow Solution process and may prove useful when you are trying to track down a problem with a non-converging model.
> 
> ![Ribbon Tools Script](images/Ribbon_Tools_Script.gif)Script
> 
> Opens the Script dialog, which can be used to call script commands or open [auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) containing script commands and data modifications. Note that the drop-down next to the Script button give convenient access to the [Quick Auxiliary Files](09-auxiliary-files-and-script-commands.md#quick-auxiliary-files-dialog).

Power Flow Tools Ribbon Group

> This group represents the basic solution actions for solving the power flow.
> 
> For more detailed help see the [Power Flow Tools](#simulation-control) ribbon group topic.

Run Mode Ribbon Group

> The Run Mode Ribbon Group contains basic analysis tools that are only available in [Run Mode](01-getting-started.md#run-mode-introduction).
> 
> For more detailed help see the [Run Mode Ribbon Group](#run-mode-ribbon-group) topic.

Other Tools Ribbon Group

> The Other Tools Ribbon Group contains basic analysis tools that are normally available in both [Run Mode](01-getting-started.md#run-mode-introduction), and [Edit Mode](01-getting-started.md#edit-mode-introduction).
> 
> For more detailed help see the [Other Tools Ribbon Group](#other-tools-ribbon-group) topic.

Edit Mode Ribbon Group

> The Edit Mode ribbon group contains basic analysis tools that are only available in [Edit Mode](01-getting-started.md#edit-mode-introduction).
> 
> For more detailed help see the [Edit Mode Ribbon Group](#edit-mode-ribbon-group) topic.

---

<a id="edit-mode-ribbon-group"></a>

## Edit Mode  Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Tools_EditMode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Tools_EditMode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Edit Mode ribbon group contains basic analysis tools that are only available in [Edit Mode](01-getting-started.md#edit-mode-introduction). The Group is shown below.

|                                                                          |                                                                            |                                                            |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------- | ---------------------------------------------------------- |
| ![Ribbon Group Tools Edit Mode](images/Ribbon_Group_Tools_Edit_Mode.gif) | ![Ribbon Tools Edit Modify Case](images/Ribbon_Tools_Edit_Modify_Case.gif) | ![Ribbon Tools Renumber](images/Ribbon_Tools_Renumber.gif) |

Equivalencing

Click this button to open the [Equivalencing Dialog](19-edit-mode-tools.md#equivalents-display).

Modify Case Menu

 The Modify Case Menu contains actions related to modifying the network model.

**Tap Transmission Line**: Opens the [Tap Transmission Line Dialog](19-edit-mode-tools.md#tapping-transmission-lines).

**Move Bus Equipment**: Opens the [Move Bus Equipment Dialog.](19-edit-mode-tools.md#equipment-mover)

**Split Bus**: Open the [Split Bus Dialog.](19-edit-mode-tools.md#split-bus-dialog)

**Merge Buses**: Opens the [Merge Buses Dialog.](19-edit-mode-tools.md#merging-buses)

**Create Composite Load Model**: Opens the [Create Composite Load Models Dialog.](19-edit-mode-tools.md#create-composite-load-models-dialog)

**List of Unused Bus Numbers**: Clicking this button to get a [list of unused bus numbers](18-general-tools.md#unused-bus-numbers) in the model.[ ](18-general-tools.md#branches-that-create-islands)

**Append Case**: Provides access to [opening a case while appending](19-edit-mode-tools.md#appending-a-case).

Renumber Menu

The Renumber Menu contains actions related to renumbering data in the model.

**Renumber Areas/Zones/Substations**: Opens the [Renumber Areas, Zones and Substations Dialog](19-edit-mode-tools.md#renumber-areaszonessubstations-dialog).

**Renumber Buses**: Opens the [Renumber Buses Dialog.](19-edit-mode-tools.md#bus-renumbering-dialog)

**Renumber Multi-Section Line Dummy Buses**: Allows user-specification of dummy bus numbers for multi-section lines. See the section **Multi-Section Line records \> Renumber Dummy Buses** with the [Multi-Section Lines Display](05-case-information-displays-by-object-part2.md#multi-section-lines-display) topic for more information.

**Renumber Three-Winding Transformer Star Buses**: Allows user-specification of three-winding transformer star bus numbers. See the section **3W Transformers records \> Renumber Star Buses** with the [Three Winding Transformer Display](05-case-information-displays-by-object-part2.md#three-winding-transformer-display) topic for more information.

---

<a id="other-tools-ribbon-group"></a>

## Other Tools  Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Tools_OtherTools.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Tools_OtherTools.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Other Tools ribbon group contains basic analysis tools that are normally available in both [Run Mode](01-getting-started.md#run-mode-introduction) and [Edit Mode](01-getting-started.md#edit-mode-introduction). The group is shown below.

![Ribbon Group Tools Other Tools](images/Ribbon_Group_Tools_Other_Tools.gif)

Limit Monitoring Settings

Opens the [Limit Monitoring Settings Dialog](18-general-tools.md#limit-monitoring-settings).

Difference Case Menu

![Ribbon Tools Difference Flows](images/Ribbon_Tools_Difference_Flows.gif)

Difference Case: Opens the [Difference Case Dialog](08-view-case-data-tools.md#difference-case)

Present Topological Differences From Base: Opens the [Present Topological Differences From Base Dialog.](08-view-case-data-tools.md#present-topological-differences-from-base-case)

The remaining options in this menu all replicate the same behavior available on the [Difference Case Dialog](08-view-case-data-tools.md#difference-case). For more details go to that help topic.

Scale Case

Opens the [System Scaling Dialog](18-general-tools.md#scaling).

Weather Menu

Added in Version 23

The Weather Menus provide access to the [weather-related features](28-weather.md#weather-related-features) including [weather dependent limits](28-weather.md#weather-dependent-limits).

Model Explorer

Opens the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) giving access to all the [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) for the model.

Connections Menu

The Connection Menus contains actions related to analyzing the interconnectedness of the network model. These may be considered Graph Theory routines.

![Ribbon Tools Connections](images/Ribbon_Tools_Connections.gif)

**Determine Path Distances to Buses**: Opens the [Determine Patch Distances to Buses Dialog](16-oneline-gis-tools.md#path-distances-from-bus-or-group).

**Determine Shortest Path Between**: Opens the [Determine Shortest Path Between Dialog.](06-object-properties-edit-mode-part1.md#shortest-path-between-buses)

**Find Radial Bus Paths**: Open the[Find Radial Bus Paths](18-general-tools.md#find-radial-bus-paths) (Added in Version 23, build on October 4, 2024)

**Find Circulating MW or Mvar Flows**: Opens the [](18-general-tools.md#find-circulating-mw-or-mvar-flows)[Mvar and MW Flow Cycle Dialog](18-general-tools.md#find-circulating-mw-or-mvar-flows).

**Facility Analysis**: Open the [Facility Analysis Dialog.](18-general-tools.md#facility-analysis-dialog)

**Branches that Create Islands**: Opens the [Branches that Create Islands Dialog.](18-general-tools.md#branches-that-create-islands)

**Set Selected Field for Network Cut**: Opens the [Set Selected Field for Network Cut Dialog](18-general-tools.md#set-selected-field-for-network-cut)

**Set Bus Field From Closest Bus**: Opens the [Set Bus Field From Closest Bus](18-general-tools.md#set-bus-field-from-closest-bus)

**Find Parallel AC Branches**: Opens the [Find Parallel AC Branches](52-additional-linked-topics-part1.md#find-parallel-ac-branches)

**Breaker Isolated Groups**: Open the [Breaker Isolated Groups dialog](18-general-tools.md#breaker-isolated-groups).

Other Menu

The Other Menu contains other miscellaneous features.

![Ribbon Tools Other Tools Other Menu](images/Ribbon_Tools_Other_Tools_Other_Menu.gif)

**Governor Power Flow**: Opens the [Governor Power Flow Dialog](18-general-tools.md#governor-power-flow).

**Set Generator Part. Factors**: Opens the [Set Generator Participation Factors Dialog](06-object-properties-edit-mode-part1.md#generator-participation-factors)

**Set Selected Field for Network Cut:** Opens the [Set Selected Field for Network Cut Dialog](18-general-tools.md#set-selected-field-for-network-cut)

**Set Selected From Selection**: When a selection is chosen in [Edit Mode](01-getting-started.md#edit-mode-introduction), click this to set the Selected? field to YES for that selection.

**Create new Areas from Islands**: When selected, new areas will be created for areas that span multiple electrical islands to help facilitate area interchange control. A new area will be created for the buses of an original area that are not in the main island but are in another island that only contains the original area. This process is temporarily done when the power flow is solved, but the buses return to their original area at the end of the solution. This option will make a permanent change to the case.

**Browse PWB File Headers**: When selected, Simulator will prompt you to specify a directory containing PWB files for which you wish to preview the header (case description) text. Once the directory has been specified, Simulator will obtain the case description for each PWB file in the directory, and write them all into the Simulator message log.

**Real-Time Monitor Definitions**: Open a dialog to view, modify, and create real-time monitor definitions. Real-time monitors are only active in Retriever and Trainer, where they can trigger alarms when the monitor conditions are met.

**Clear Small Islands**: This action identifies the largest island and de-energizes all other islands. The largest island is the island with the most buses. Small islands are de-energized by setting the status of all generators in those islands to open.

**Anonymize Names in Case**: \[ Added in Version 24\]This action will change all the names for Bus, Substation, Area, Zone, Balancing Authority, Owner, SuperAreas, Interface, Injection Group, and DataMaintainers to be names based on numbers only. Also will delete all object labels in the case. Generally removes all identifying information in the case.

---

<a id="run-mode-ribbon-group"></a>

## Run Mode Ribbon Group

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Tools_RunMode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Tools_RunMode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Run Mode ribbon group contains basic analysis tools. All of these are only available in [Run Mode](01-getting-started.md#run-mode-introduction) except for the **RAS + CTG Case Info** dropdown. The group is shown below.

![Ribbon Group Tools Run Mode](images/Ribbon_Group_Tools_Run_Mode.gif)

Contingency Analysis

Click this button open the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) providing access to the automated processing of a list of contingencies.

CTG Combo Analysis

Added in Version 22

Click this button open the [Contingency Combination Analysis Dialog](25-ctg-combo-analysis.md#ctg-combo-contingency-analysis-dialog) providing access to the automated processing of combinations of Primary Contingencies and contingencies.

RAS + CTG Case Info

This menu contains options that are relevant for defining contingencies and remedial actions and running contingency analysis.

![Ribbon Tools RAS CTG Case Info](images/Ribbon_Tools_RAS_CTG_Case_Info.gif)

The following entries will open case information displays for the following objects:

[Remedial Actions](21-contingency-analysis-overview-and-records.md#remedial-actions)

[Model Expressions](04-model-explorer-and-case-information-part2.md#model-expressions)

[Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog)

[Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog)

[Contingency Records](22-contingency-analysis-options.md#contingency-definition-display)

Legacy [Contingency Blocks](21-contingency-analysis-overview-and-records.md#contingency-blocks) and [Global Actions](21-contingency-analysis-overview-and-records.md#global-actions)

**Contingency Analysis**

Click this option to open the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) and switch to Run mode.

**Contingency Modeling**

This dropdown provides access to case information displays containing contingency modeling options.

![Ribbon Tools RAS CTG Case Info Modeling](images/Ribbon_Tools_RAS_CTG_Case_Info_Modeling.gif)

[Area Makeup Power](52-additional-linked-topics-part1.md#make-up-power-sources)

Contingency Analysis Options will open a case information display for settings found on the [Options](22-contingency-analysis-options.md#options-tab) tab of the Contingency Analysis dialog

[Bus Load Throw Over](22-contingency-analysis-options.md#bus-load-throw-over)

[Generator AGC Response in Post-Contingency](22-contingency-analysis-options.md#generator-post-contingency-agc)

[Generator Line Drop and RCC](22-contingency-analysis-options.md#contingency-generator-line-drop-and-reactive-current-compensation)

[Generator Maximum MW Response](22-contingency-analysis-options.md#generator-maximum-mw-response)

[Contingency Options: Switched Shunt Response](22-contingency-analysis-options.md#switched-shunt-post-ctg)

**Dependency Explorer**

Click this button to open the [Dependency Explorer](21-contingency-analysis-overview-and-records.md#dependency-explorer).

**Load Contingency Data**

This dropdown provides easy access loading files containing information for running contingencies. The only option is to load the Areva HDBexport file containing data from the RASMOM database.

![Ribbon Tools RAS CTG Case Info Load Contingency Data](images/Ribbon_Tools_RAS_CTG_Case_Info_Load_Contingency_Data.gif)

**Update Allow Open or Close Breakers**

Click this button to run the [Update Allow Open or Close Breakers](05-case-information-displays-by-object-part2.md#update-allow-open-or-close-breakers) process.

Sensitivities Menu

The Sensitivities Menu contains a list that provides access to all the sensitivity calculations available.

![Ribbon Tools Sensitivities](images/Ribbon_Tools_Sensitivities.gif)

[Power Transfer Distribution Factors (PTDFs) opens its associated dialog.](20-sensitivities.md#power-transfer-distribution-factors-dialog)

[Shift Factors opens its associated dialog](20-sensitivities.md#shift-factor-sensitivities-dialog). (In Version 21 and earlier, this was called "TLR Sensitivities / Generation Shift Factors")

[Line Outage Distribution Factors (LODFs) opens its associated dialog](20-sensitivities.md#line-outage-distribution-factors-dialog).

[Flow and Voltage Sensitivities opens its associated dialog.](20-sensitivities.md#flow-and-voltage-sensitivities)

[Loss Sensitivities opens its associated dialog.](20-sensitivities.md#loss-sensitivities)

[LODF Screening opens its associated dialog](20-sensitivities.md#lodf-screening)

[Driving Point Impedances opens its associated dialog](52-additional-linked-topics-part1.md#driving-point-impedances)

Fault Analysis

Click this button to open the [Fault Analysis Dialog](27-fault-analysis.md#fault-analysis-dialog).

Time Step Simulation

Click this button to open the [Time Step Simulation Dialog](26-time-step-simulation-part1.md#time-step-simulation-dialog).

Line Loading Replicator

Click this button to open the [Line Loading Replicator Dialog](20-sensitivities.md#line-loading-replicator).

---

<a id="simulation-control"></a>

## Simulation Control

*Source: [`Content/MainDocumentation_HTML/RibbonGroup_Tools_PowerFlow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/RibbonGroup_Tools_PowerFlow.htm)*

The main function of PowerWorld Simulator is to simulate the operation of an interconnected power system. The simulation is accomplished by selecting **Solve Power Flow – Newton** from either the [Quick Access Toolbar](#quick-access-toolbar) or the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab. This activity performs a single Power Flow Solution. See [Solving the Power Flow](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) for more information.

The following tasks are also available from the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab.

![Ribbon Group Power Flow Tools](images/Ribbon_Group_Power_Flow_Tools.gif)

Solve Power Flow – Newton  

The main function of PowerWorld Simulator is to simulate the operation of an interconnected power system. The simulation is accomplished by selecting **Solve Power Flow – Newton** from the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab. This activity performs a single Power Flow Solution. See [Solving the Power Flow](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) for more information. Also note that if presently in Edit Mode, you will be automatically taken to Run Mode when choosing this.

 Simulator Options

When choosing any of the solution methods, the options as specified in the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) will affect what calculation is performed. You can solve the power flow usin either the Full Newton AC load flow or the DC Approximation load flow, as specified in the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Voltage Conditioning

Added in Version 23

Click this button to open the [Voltage Conditioning Dialog](10-power-flow-solution-and-options-part3.md#voltage-conditioning-dialog)

Play Button

Click this button to cause repeated solutions of the system and to cause the animation of oneline diagrams

Pause/Stop Button

Click this button to stop the action of the Play button.

Restore Menu

The Restore menu offers option to either Restoring a Previous Solution or a Restore a Previous State.

![Ribbon Tools Restore](images/Ribbon_Tools_Restore.gif)

Sometimes a power flow attempt won't converge to a solution. When this occurs, the voltages and angles calculated by the solution engine will not satisfy the real and reactive power balance constraints at each bus. The state currently stored in memory will not be an actual system operating point. It is often very difficult to coax the system to solve once it has failed to converge.

To help you recover from a solution attempt that has failed to converge (both timed simulations and single solutions), Simulator offers you two options.

After Simulator solves a system successfully, it will store the voltages and angles it found in memory. If the changes that you then make to the system result in a system that can't be solved, you can select **Restore \> Last Successful Solution** from the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab to reload the results of the last converged solution. After reloading this information, Simulator will re-solve the system and refresh all displays.

In addition to restoring the last converged solution, Simulator also gives you the ability to restore the state of the system as it was just prior to the unsuccessful solution attempt. This can be thought of as "un-doing" the effect of the solution attempt. Before attempting a solution, Simulator stores the state of the system in memory. If it solves the power flow successfully, Simulator will discard this pre-solution state. However, it the power flow fails to converge, Simulator will keep the state in memory. To recover it, select **Restore \> State Before Solution Attempt** from the ****Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab**. Simulator will replace the non-converged post-solution state with the pre-solution state and refresh the displays. You can then play with the system to try to make it easier to solve.

If you are working with large systems, you should be aware that saving these system states can consume a lot of memory. Therefore, Simulator offers you the option to disable one or both of these features. To do this, select **Simulator Options** from the **Case Options** ribbon group on the [Options](#options-tab-overview) ribbon tab to open the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), and then go to the Storage sub-tab of the Solution tab. You will see two checkboxes there that can be modified to control whether or not these extra system states are saved.

Solve Menu

> ![Ribbon Tools Solve](images/Ribbon_Tools_Solve.gif)
> 
> Solve Power Flow – Newton  
> 
> The main function of PowerWorld Simulator is to simulate the operation of an interconnected power system. The simulation is accomplished by selecting **Solve Power Flow – Newton** from the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab, or from the [Quick Access Toolbar](#quick-access-toolbar). This activity performs a single Power Flow Solution. See [Solving the Power Flow](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) for more information. Also note that if presently in Edit Mode, you wil be automatically taken to Run Mode when choosing this.
> 
> Polar NR Power Flow
> 
> This perform a Newton-Raphson power flow solution using polar coordinates instead of rectangular coordinates as is normally done in Simulator.
> 
> DC Power Flow
> 
> This automatically change the Simulator Options to use the [DC Approximation](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options) and then immediately performs the DC power flow solution.
> 
> Reset to Flat Start
> 
> Select **Solve \> Reset to Flat Start** from the **Power Flow Tools** ribbon group on the [Tools](#tools-tab-overview) ribbon tab to initialize the Power Flow Solution to a "flat start." A flat start sets all the voltage magnitudes to either 1.0 or generator setpoint voltages and all the voltage angles to the system slack angle. Usually, a flat start should be used only if the power flow is having problems converging. You can also use the flat start option on the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options) to initialize every solution from a flat start.
> 
> Robust Solution Process
> 
> The Robust Solution Process provides a method to attempt to reach a solution when the standard load flow (Newton-Raphson) solution fails. The robust process performs a solution in a series of steps.
> 
> First, the robust solution will turn off all controls in the case. Then the load flow will be solved using a fast decoupled power flow. If the fast decoupled power flow reaches a solution, Simulator then immediately solves the load flow using the Newton-Raphson load flow, still keeping the controls turned off. If the Newton-Raphson solution is also successful, Simulator will begin adding controls back into the solution process, one type of control at a time. Thus the generator MVAR controls are added back in, and the load flow is resolved. Then the switched shunt controls are restored, and the load flow is again resolved. Simulator will continue in this manner by reintroducing next the LTC control, followed by the area interchange control, and lastly the phase shifter control. Furthermore, when reintroducing the phase shifter control, the controls are added one at a time for each phase shifter, with a load flow solution occurring after each.

---

<a id="window-tab-overview"></a>

## Window Tab Overview

*Source: [`Content/MainDocumentation_HTML/Ribbon_Window.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ribbon_Window.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Window ribbon consists of buttons and menus that provide access to customizing the windows in the user interface. It also provides access to help topics and topics regarding the Auxiliary File Format. The ribbon is shown below.

![Ribbon Window](images/Ribbon_Window.gif)

The Case Information ribbon is broken into the following ribbon groups:

Mode Ribbon Group

> Edit Mode
> 
> Switches the program to [Edit Mode](01-getting-started.md#edit-mode-introduction), which can be used to build a new case or to modify an existing one.
> 
> Run Mode
> 
> Switches the program to [Run Mode](01-getting-started.md#run-mode-introduction), which can be used to perform a single Power Flow Solution or a timed simulation with animation.

Window Ribbon Group

> Open Windows Menu 
> 
> The Open Windows Menu provides a convenient method of switching between open windows. This includes User Interface Dialogs, Case Information Displays, and Oneline diagrams.
> 
> ![Ribbon Case Information Open Windows](images/Ribbon_Case_Information_Open_Windows.gif)
> 
> Switch to Free-Floating Windows (Switch to Standard Container Window)
> 
> Choosing this option toggles the program from between two different window environments
> 
> 1\. All diagrams and dialogs are contained within the Simulator program shell
> 
> 2\. All diagrams and dialogs are free-floating on your monitor
> 
> For more information see the [Window Basics](01-getting-started.md#windows-basics).
> 
> Reset to Defaults
> 
> The program keeps track of dialog Free-Floating/Contained Style, Size, and Position. Clicking this button will reset all these to the factory default settings. Nearly all dialogs will then be reset back to Contained with a default size and position as well. For more information on Style, Size and Position, see [Window Basics](01-getting-started.md#windows-basics).
> 
> Refresh Displays
> 
> Redraws (refreshes) each of the open windows. Simulator usually automatically refreshes the open windows as necessary. However, this action allows you to trigger the refresh when you want it.
> 
> Ribbon Settings Menu
> 
> This menu contains options for customizing your ribbon. Change the color scheme of Simulator's dialogs to either **Black, Blue, Carmel, Green, Pink,** or **Silver**.
> 
> ![Ribbon Window Ribbon Settings](images/Ribbon_Window_Ribbon_Settings.gif)
> 
> Arrange Windows
> 
> The options under Arrange Windows are Tile Horizontally, Tile Vertically, and Cascade. Tile rearranges the open oneline diagrams such that the total window area is divided equally among all of them and each is completely visible. Cascade rearranges all open windows such that all they appear on top of each other while leaving the title bars visible.
> 
> Toggle Full Screen
> 
> Toggle full screen makes the currently selected diagram window switch to full screen mode. Full screen mode will dedicate the screen to the window, with all other windows, including the Simulator menus and toolbars, hidden. To get back to normal mode, right-click on the diagram in full screen mode and select Toggle Full Screen from the popup menu.

Help Ribbon Group

> Contents
> 
> Opens the Simulator help file.
> 
> Set Help File
> 
> When Simulator is installed it will be set to point to a help file location on the PowerWorld website. This is located at [http://www.powerworld.com/WebHelp](https://www.powerworld.com/WebHelp/WebHelp). The help may also be installed locally on a user's computer. Use this option to point to the directory location of the help file. Only the location needs to be specified as Simulator will automatically determine the name of the help file. If specifying the location on the website, the address will need to be typed in.
> 
> Help files are automatically installed locally with the Simulator installation file. They are placed in a Help subfolder under the folder that is selected as the PowerWorld installation folder.
> 
> About
> 
> Click this to open the About dialog. The About dialog contains information about the software as well as showing you the Build Date of your version of Simulator. PowerWorld releases patch versions of Simulator on our website. These patch versions are named by date as shown on the About dialog.
> 
> There is also an option on the About dialog to Change License Key. This allows selection of a new license key file. Add ons are controlled through the license key. If you are using different versions of Simulator with different add ons, this option provides the mechanism for switching between the different versions of Simulator. You will need a different license key file if you are using different licenses for Simulator that have different add ons.
> 
> PowerWorld Website
> 
> Click this to open your default web browser to the PowerWorld Corporation Website.
> 
> Check for Updates
> 
> This button will check the PowerWorld website to determine if there is a new patch available by comparing the latest patch date with the date of your current patch. You will be informed if there is a newer patch available. If so, you can have Simulator take you to the PowerWorld patch download website.

Auxiliary File Ribbon Group

> Load Auxiliary 
> 
> Choose this option to load an [Auxiliary File.](03-cases-files-and-formats.md#auxiliary-file-format-aux)
> 
> Load Display Auxiliary File
> 
> Choose this option to load a [Display Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux) to append to the active oneline.
> 
> Auxiliary File Format
> 
> Opens the PDF document that describes the [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) Data and Script sections.
> 
> Export Display Object Fields Menu
> 
> Export Case Object Fields Menu
> 
> Choose these options to export a list of fields for each type of object in a case (or a Oneline Display). The list also indicates which fields are [key fields](04-model-explorer-and-case-information-part3.md#key-fields) and [required fields](04-model-explorer-and-case-information-part3.md#required-fields) for each object. You can output this list of fields as either a text file or into Excel.
> 
> ![Ribbon Window Export Object Fields](images/Ribbon_Window_Export_Object_Fields.gif)
