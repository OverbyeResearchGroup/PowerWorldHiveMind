---
title: "Transient Stability — Analysis Dialog (Part 2 of 3)"
part: "Transient Stability"
chapter_file: "37-transient-stability-analysis-dialog-part2.md"
topics: 16
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Transient Stability — Analysis Dialog (Part 2 of 3)

The Transient Stability Analysis dialog: simulation, options, plots, results and validation.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (16)**

- [Plots](#plots)
- [Plot Designer](#plot-designer)
- [Plot](#plot)
- [Title Block](#title-block)
- [Chart](#chart)
- [Horizontal Axis](#horizontal-axis)
- [Vertical Axis](#vertical-axis)
- [Plot Series List](#plot-series-list)
- [Plot Series](#plot-series)
- [Special Strings for Plot Features (sometimes called "Magic Strings")](#special-strings-for-plot-features-sometimes-called-magic-strings)
- [User Interaction with Plots](#user-interaction-with-plots)
- [Result Analyzer](#result-analyzer)
- [Modal Analysis Theory](#modal-analysis-theory)
- [Result Analysis Time Window](#result-analysis-time-window)
- [Result Analysis Signal Violation](#result-analysis-signal-violation)
- [Result Analysis Signal Statistics](#result-analysis-signal-statistics)

---

<a id="plots"></a>

## Plots

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plots page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog). The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

The Plots page is broken into two sub-tabs that provide the means for creating and modifying plots:

[**Plot Designer**](#plot-designer)

This page is used to create and modify plots.

**Plot Definition Grids**

This page provides summary case information displays of the various components comprising a plot: Plots, Sub Plots, Axis Groups, and Plot Series. Once plots have been created using the [Plot Designer](#plot-designer), they can be modified through the Plot Definition Grids. These grids also provide the format in which plots are stored in auxiliary files.

Once you have created a plot see the [User Interaction with Plots](#user-interaction-with-plots) for many ways to interact with that plot to better view the results.  

Plotting of transient stability results is an integral part of a transient stability tool. It is a primary mechanism through which transient stability results are viewed. Simulator has been designed to give a great deal of flexibility in the design of your plots allowing for multiple charts on a single plot as well as multiple vertical axes on a single chart. To discuss this in detail let us first define four objects which make up a plot definition

  - *Plot* : a single window showing plotted results which may consist of 1 or more subplots
  - *Subplot*: A subplot represents the actual graphical chart. It contains a single horizontal axis which is shared by all plot series contained in the subplot. The subplot contains one or more axis groups which represent vertical axes. For many plots there will be only one subplot
  - *Axis Group* : A single axis group may contain many plot series. A single axis group represents a vertical axis which is shared by all the plot series it contains. For many subplots there will be only one axis group.
  - *Plot Series* : A single plot series is a graphical line representing the trace of one numeric data series. For instance it may be the frequency of a particular bus.

As a simple example, consider the figure on the first figure below showing a plot that contains one subplot, that contains 1 axis group, that contains 1 plot series. Plots may also be much more complex as shown by the second figure below which has multiple subplots and multiple axis groups. Finally, the bottom-right subplot of the third example shows a subplot using a horizontal axis which is different than Time and thus shows a state space plot.

![Transient Stability Plotting Example1](images/Transient_Stability_Plotting_Example1.jpg)

A more complicated example consisting of multiple plots, subplots, axis groups, and plot series is shown below:

![Transient Stability Plotting Example2 808x555](images/Transient_Stability_Plotting_Example2_808x555.jpg)

![Transient Stability Plotting Example3](images/Transient_Stability_Plotting_Example3.gif)

---

<a id="plot-designer"></a>

## Plot Designer

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots_Plot_Designer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots_Plot_Designer.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plot Designer sub-tab is found on [Plots](#plots) page of the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog). The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

Settings on this page determine which results will be plotted and when the plots will be made visible during the transient stability analysis.

The Plot Designer page is broken into three main sections. The left side of the page allows for the selection of devices and fields that should be included in a plot. The middle section defines the plots that are created and how these should be defined in terms of subplots and axis groups. The right section of the page allows modification of all of the plot components. The dialog is shown below.

![Transient Stability Plot Designer](images/Transient_Stability_Plot_Designer.jpg)

Creating a New Plot

A new plot can be created in a number of ways:

  - If no existing plot exists, simply selecting a **Device Type**, **Choose Fields**, and **Choose Objects** and then clicking the **Add \>\>**, **Add \>\> Group Fields**, or **Add \>\> Group Objects** buttons will create a new plot with a default name. (You may also drag a selection of fields over to the middle section listing the plot components to create a new plot).
  - Click the **Add Plot** button found under the **Plots, Subplots, Axis Groups** list. A prompt will appear asking for the name of the plot. Enter the name and click OK. Then use the **Device Type**, **Choose Fields**, and **Choose Objects** options and the **Add \>\>** buttons to add data to a plot.
  - Right-click on the **Plots, Subplots, Axis Groups** list and select Add Plot. A prompt will appear asking for the name of the plot. Enter the name and click OK. Then use the **Device Type**, **Choose Fields**, and **Choose Objects** options and the **Add \>\>** buttons to add data to a plot.
  - Click the **Add Plot** button found on the **Plot** sub-tab that is part of the **Plots, Subplots, Axis Groups** section. A prompt will appear asking for the name of the plot. Enter the name and click OK. Then use the **Device Type**, **Choose Fields**, and **Choose Objects** options and the **Add \>\>** buttons to add data to a plot.
  - Select fields and objects in the [Results to Save](37-transient-stability-analysis-dialog-part1.md#results-storage) tables.
  - From the list of [Transient Limit Monitor Violations](37-transient-stability-analysis-dialog-part3.md#transient-limit-monitors-violations).

Right Section: Editing of Plot Definition

Most of the topic below discusses the creating of plot components. After plot components are created, selecting a particular plot component (plot, subplot, axis group, plot series) from the list in the middle of this portion of the dialog will change the sub-tabs that are available to the right of the list. Each of these sub-tabs allows for modifications of the different plot components as well as the components in which a particular component is contained, e.g. selecting a plot series will allow for modification of that particular series as well as the axis group in which the series is contained, the subplot in which the axis group is contained, and the plot in which the subplot is contained. Options can be changed for a plot before the plot is generated or while the plot is showing. Changing any of the options on the sub-tabs described below will update the current plot. Possible sub-tabs are as follows:

  - [Plot](#plot)
  - [Title Block](#title-block)
  - [Chart](#chart)
  - [Horizontal Axis](#horizontal-axis)
  - [Vertical Axis](#vertical-axis)
  - [Plot Series List](#plot-series-list)
  - [Plot Series](#plot-series)

Device Type

Select the device type from the drop-down of all allowed types. Changing the device type will update the **Choose Fields** and **Choose Objects** accordingly.

Choose Fields

Choose the fields to be added to a plot. Multiple fields can be selected by holding down the CTRL key and selecting individual fields with the mouse, or holding down the Shift key and selecting the beginning and ending of a range with the mouse. You may also left-click and drag a list of fields here over to the middle section showing a list of plot components.

Dynamic States, Other Fields and Inputs (For Transient Stability Only)

At the top of the field list is a list of the common fields which can be saved as part of the [Results Storage](37-transient-stability-analysis-dialog-part1.md#results-storage). For some types of objects, below this are several folders showing either Dynamic Model Input Fields, Dynamic Model Other Fields, or Dynamic Model States. The states represent the actually states of the dynamic equations of the mode. Other field represents other values of interest for the object which are not actually a state variable. Finally the input fields represent special input values to the dynamic model. Examples of input fields are the governor setpoint (Pref) and the exciter setpoint (Vref).

The entries underneath these folders will change as you select different objects from the **Choose Objects** pane. By default the entries will be very generic saying "Input 1", "Other 1", "State 1", "State 2", etc... If the selected object has a dynamic model associated with it then the entries will change to reflect this. If multiple objects are selected then the entries will only change if all objects selected have the same name for the specified State, Input, or Other field.

Choose Objects

Choose the objects to be added to a plot. Multiple fields can be selected by dragging the mouse down a selection, holding down the CTRL key and selecting individual fields with the mouse. The font colors of the objects lists in this list indicate whether any results are available for plotting presently. Black text indicates that there are no results available. Green text indicates that values are stored in RAM for this object. Blue text indicates that values are stored on the Hard Drive for this object.

Add \>\>

When clicked the selected fields and objects will be added to the appropriate plot component. Fields are selected from the **Choose Fields** list and objects are selected from the **Choose Objects** list. This button is enabled under the following conditions if at least one field and one object are selected:

**Plot selected that contains only one subplot and one axis group** - plot series for each field and object will be added to the selected plot in the single axis group and subplot

**Subplot selected that contains only one axis group** - plot series for each field and object will be added to the selected subplot in the single axis group

**Axis group selected** - plot series for each field and object will be added to the selected axis group

In any of these case if a plot series already exists for the selected field and object, a new plot series will not be added.

Add \>\> Group Fields

When clicked the selected fields and objects will be added to the appropriate plot component. Fields are selected from the **Choose Fields** list and objects are selected from the **Choose Objects** list. This button is enabled under the following conditions if at least one object and more than one field are selected:

**Plot selected that contains only one subplot** - axis groups will be created for each of the selected fields and plot series for each of the selected objects will be placed in each new axis group

**Subplot selected** - axis groups will be created in the selected subplot for each of the selected fields and plot series for each of the selected objects will be placed in each new axis group

**Axis group selected** - axis groups will be created in the subplot that contains the selected axis group. A new axis group will be created for each of the selected fields and plot series for each of the selected objects will be placed in each new axis group.

In any of these cases if an axis group for a selected field already exists in the corresponding subplot, a new axis group will not be created, but the plot series will be added to the existing axis group. If a plot series for a selected object already exists in the axis group, a new plot series will not be added. For an axis group to exist for a selected field, the axis group can only contain plot series for that particular field.

Add \>\> Group Objects

When clicked the selected fields and objects will be added to the appropriate plot component. Fields are selected from the **Choose Fields** list and objects are selected from the **Choose Objects** list. This button is enabled under the following conditions if at least one field and more than one object are selected:

**Plot selected that contains only one subplot** - axis groups will be created for each of the selected objects and a plot series for each of the selected fields will be placed in each new axis group

**Subplot selected** - axis groups will be created in the selected subplot for each of the selected objects and plot series for each of the selected fields will be place in each new axis group

**Axis group selected** - axis groups will be created in the subplot that contains the selected axis group. A new axis group will be created for each of the selected objects and plot series for each of the selected fields will be place in each new axis group.

In any of these cases if an axis group for a selected object already exists in the corresponding subplot, a new axis group will not be created, but the plot series will be added to the existing axis group. If a plot series for a selected field already exists in the axis group, a new plot series will not be added. For an axis group to exist for a selected object, the axis group can only contain plot series for that particular object.

Generate Selected Plots

Click this button to generate plots for those selected in the **Plots, Subplot, Axis Groups** list. For a plot to be selected either the plot itself or one of its components needs to be selected. When generating a plot, an attempt will be made to retrieve from the results [stored to RAM](37-transient-stability-analysis-dialog-part1.md#storage-to-ram). If results are not available for a particular plot series in RAM, then results will be retrieved from those values [stored to Hard Drive](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive). If they are still not available then a plot will be generated which omits any plot series for which data can not be retrieved.

Close All Plots

Click this button to close all open plots.

Show/Save Selected Plot Data

Click this button to open a drop down menu:

![Transient Stability Save Selected Plot Data 296x296](images/Transient_Stability_Save_Selected_Plot_Data_296x296.jpg)

The first option is to open a case info display. Also the plot data can be save with the TSGeResults in integrated Header, Single File and Separate files. If the Trasnient Stability tool is in multiple contingencies mode and the Plot Multiple Contingencies option is selected the Save to TSGeResults will save all the plot data of all the contingencies depending on the option the user selects. Other options to save plot data results are to save it as a PlayIn auxiliary file, a WECC JSIS file, and also to save the data in Comtrade 1991 ASCII format, 1999 Binary format and 2013 CFF Binary format.

Save Plot Definitions to Auxiliary File

Click this button to save all of the plot definitions to an auxiliary file. This is useful when running analyses on power system models with common devices.

Plots, Subplots, Axis Groups

This is a listing of all plots that have been created along with associated subplots, axis groups, and data series. The list is arranged as a group of folders. Each plot is contained in its own folder. If there is more than one subplot for a plot, each subplot will be contained in a folder. Each subplot then contains a list of axis groups. If there is more than one axis group for a subplot, each axis group will be contained in a folder. Each axis group then contains a list of the plot series that it contains.

When adding devices and fields to a plot, the plot component selected in this list will determine where the data will be added when clicking one of the **Add \>\>** buttons. The **Add \>\>** buttons will be enabled according to the component selected in this list and the combination of devices and fields selected in **Choose Fields** and **Choose Objects**. Note you may also drag a list of fields from the **Choose Fields** portion of the dialog over to this listing to add new plots or add new plot series to the respective plot component.

There are several buttons located at the bottom of the plot listing. These buttons affect what and how things are shown in the list.

Add Plot

Click this button to add a new plot to the list.

Delete

The caption and functionality of this button will change depending on the particular type of plot component that is selected in the list. Clicking this button will then delete the selected component and any other components that are contained in the selected component. For example, if an axis group is selected and the Delete button is clicked, all plot series contained in the axis group will be deleted along with the axis group.

Note: you may also delete plot components by dragging them from this listing over to the **Choose Fields** pane.

Collapse All

Click this button to collapse all folders in the list.

Expand All

Click this button to expand all folders in the list.

Right-clicking on components in the list will open a local menu that allows various options for adding or deleting plot components. The options that are available will change depending on the component selected.

![Transient Stability Dialog Plot Designer Local Menu](images/Transient_Stability_Dialog_Plot_Designer_Local_Menu.gif)

Components can be moved from one plot to another or from one component to another by simply clicking and dragging the component to the new location. The new location must be a valid component that can contain the component being moved or the parent component for the new location must be able to contain the component being moved. For example, a subplot can be moved and dropped on an axis group with the subplot being placed in the plot containing the axis group.

Note: you may also delete plot components by dragging them from this listing over to the **Choose Fields** pane.

---

<a id="plot"></a>

## Plot

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plot sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the Plot that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab. A plot is selected if any of its corresponding subplots, axis groups, or plot series are selected in the list.

![Transient Stability Dialog Plot Designer Plot](images/Transient_Stability_Dialog_Plot_Designer_Plot.gif)

Plot Name

Name of the currently selected plot.

Rename Plot

Click this button to rename the currently selected plot. A dialog box will open in which the new plot name should be entered. Click OK on this dialog to change the plot name or Cancel to abandon the change.

Add Plot

Click this button to create a new plot. A dialog will open prompting for a name for the new plot. Click OK to create the new plot or Cancel to abandon the addition.

Delete Plot

Click this button to delete the currently selected plot.

When to show the plot (Only available for Transient Stability Plots)

Set this option to determine when a plot should be shown. A plot can automatically be shown at the completion of a stability run or on execution of a stability run. If showing on execution, the plot will be updated as the analysis progresses. If set to be shown manually, the plot must be selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) page and the **Generate Selected Plots** button must be clicked in order to be shown. A plot can be shown manually in this manner at any time even if one of the options to show the plot automatically is selected.

Tile Subplots Mode

This option will only be enabled if a plot contains more than one subplot. This option dictates how the subplots will be placed within the plot window. If choosing **None (user-specified locations)**, the location of the subplot should be specified with the **Location** option found on the [Chart](#chart) sub-tab.

Auto-Save an Image of the Plot (Only available for Transient Stability Plots)

Specify when and how plot images are saved to the Results Storage Hard Drive location. **When** defines when images are stored (can be *Never*, *After each contingency*, *Multiple Plot at the end*, or *Both*). **File Type** defines the format the image being saved (can be a *Metafile \*.EMF*, *JPEG \*.jpg*, *Bitmap \*.bmp*, or a *GIF \*.gif*). **Image Pixel Width/Height** specifies the dimensions of the saved image.

When storing *After each contingency* if ONLY **Save Results to Hard Drive** is checked on the [Result Storage tab](37-transient-stability-analysis-dialog-part1.md#results-storage), make sure the fields that are plotted are also set to be stored to hard drive. Set the fields to be stored under the [Save to Hard Drive Options](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive) on the Result Storage tab. Not doing this could result in empty plots or plots without certain fields plotted.

Added in version 19, build on May 31, 2017. When choosing to auto-save an image of a plot to file and choosing to not store results to RAM, the image will be saved to file and then memory will be cleared of the results needed for the plot. Because nothing is saved to memory after the image is stored to file, the plot cannot be regenerated manually unless the plot information has also been stored to hard drive.

Added in version 20, build on Jun 11, 2020. A file type of PDF (\*.PDF) may also be specified. When choose a PDF file type, then all plots for which PDF file is chosen for the same transient contingency will be saved to a single PDF document. Each page of the PDF document will represent one plot with the pages in the same order as the plots are defined in the user interface. As part of this addition, the **Image Font Scalar** was also added. The image Font Scalar can be set to above 1.0 to ensure when a large Pixel Width/Height is chosen then the fonts can scale to a larger size so they can be read.

---

<a id="title-block"></a>

## Title Block

*Source: [`Content/MainDocumentation_HTML/transient_stability_dialog_plot_designer_title_Block.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/transient_stability_dialog_plot_designer_title_Block.htm)*

The Title Block sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the title block for a given plot.

![Transient Stability Dialog Plot Designer Title Block](images/Transient_Stability_Dialog_Plot_Designer_Title_Block.gif)

Plot Name

Name of the currently selected plot.

Rename Plot

Click this button to rename the currently selected plot. A dialog box will open in which the new plot name should be entered. Click OK on this dialog to change the plot name or Cancel to abandon the change.

Add Plot

Click this button to create a new plot. A dialog will open prompting for a name for the new plot. Click OK to create the new plot or Cancel to abandon the addition.

Delete Plot

Click this button to delete the currently selected plot.

Show Title Block on Plot

Check this box to display the title block on the plot.

Show Date and Time in Title Block

Check this box to include the date and time in the title block on the plot.

Title Block Height %

This defines the portion of the overall window area dedicated to the title block.

Right Memo Width %

This defines the portion of the space dedicated to the title block memos taken up by the right memo. Note that the width this setting references is the combined width of the right and left memos, which is not necessarily the full width of the plot window.

Font Size

Set the font size of the memo text and date/time text here.

Where to show the title block

Set the location of the title block in the plot display window, either **Top of Plot** or **Bottom of Plot**

Left/Right Memos

These contain the text displayed in the memos to the left and right sides of the title block. Special strings may be entered, preceded by a '@' symbol, which will be automatically interpreted as an appropriate string to place in the memo. A short list is below, but a more complete list of options is found in the [Special Strings for Plot Features help topic](#special-strings-for-plot-features-sometimes-called-magic-strings).

@CTGName will display the appropriate contingency name

@CTGEvents will show the transient result event.

@CTGMemo will show the memo of the transient contingency in the plot.

@CASENAME will show the name of the case presently open.

@BUILDDATE will show the Simulator patch build date.

@DATETIME will show the present date and time.

@DATE will show the present date.

@TIME will show the present time.

Show Logo Image in Title Block

Check this box to display an image to the far left of the title block. You can specify an image with the "Logo Image" file browser, or leave the file path blank to use the PowerWorld logo.

---

<a id="chart"></a>

## Chart

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Chart.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Chart.htm)*

The Chart sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the subplot that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab. A subplot is selected if any of its corresponding axis groups or plot series are selected in the list.

![Transient Stability Dialog Plot Designer Chart](images/Transient_Stability_Dialog_Plot_Designer_Chart.gif)

The Chart portion of the subplot is the background, header, and footer of the subplot.

Subplot Number

This is an informational field. Each subplot is assigned a number when it is created. The user cannot change this value.

Add Subplot

Click this button to add a subplot to the currently selected plot.

Delete Subplot

Click this button to delete the currently selected subplot.

Visible

Check this box to make the subplot visible when its corresponding plot is shown.

Background Color

Click the color box or the **Change** button to select a new color for the chart background.

Title

Check the **Visible** box to make a chart title shown. Check the **Specify Color** box and choose an desired color to specify a font color for the title. Specify the **Font Size** and the actual title text in the box provided. Special strings may be entered, preceded by a '@' symbol, which will be automatically interpreted as an appropriate string to place in the title. A short list is below, but a more complete list of options is found in the [Special Strings for Plot Features help topic](#special-strings-for-plot-features-sometimes-called-magic-strings).

@CTGName will display the appropriate contingency name

@CTGEvents will show the transient result event.

@CTGMemo will show the memo of the transient contingency in the plot.

@CASENAME will show the name of the case presently open.

@BUILDDATE will show the Simulator patch build date. @DATETIME will show the present date and time.

@DATE will show the present date.

@TIME will show the present time.

Footer

Check the **Visible** box to make a chart footer shown. Check the **Specify Color** box and choose an desired color to specify a font color for the footer. Specify the **Font Size** and the actual footer text in the box provided. Special strings may be entered, as described above.

Location

Set the **Top**, **Bottom**, **Left**, and **Right** location of the subplot within the plot window if choosing the option for user-specified subplot locations with the **Tile Subplots Mode** option found on the [Plot](#plot) sub-tab.

Advanced Options Filename

There are a number of advanced options associated with a chart that are only accessible through the local menu found on each subplot. This option allows a file containing these advanced options to be associated with the current subplot. If a file is specified, the advanced options contained in that file will be used when generating the subplot. Use the **Browse** button to browse for a file and use the **Clear** button to no longer associate a file with the current subplot. For more information about the advanced options, see the [Navigating Around a Plot, Advanced Options](#plots) section.

---

<a id="horizontal-axis"></a>

## Horizontal Axis

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Horizontal_Axis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Horizontal_Axis.htm)*

The Horizontal Axis sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the subplot that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab. A subplot is selected if any of its corresponding axis groups or plot series are selected in the list.

![Transient Stability Dialog Plot Designer Horizontal Axis](images/Transient_Stability_Dialog_Plot_Designer_Horizontal_Axis.gif)

The horizontal axis is shared by all plot series on the selected subplot.

Subplot Number

This is an informational field. Each subplot is assigned a number when it is created. The user cannot change this value.

Add Subplot

Click this button to add a subplot to the currently selected plot.

Delete Subplot

Click this button to delete the currently selected subplot.

Show Horizontal Axis on Plot

Check this box to show the horizontal axis on the current subplot.

Inverted

Check this box to have the scale on the horizontal axis go from high to low values when moving left to right along the axis.

Logarithmic

Check this box to use a logarithmic scale on the horizontal axis of the current subplot.

Title

Check the **Visible** box to make a horizontal axis title shown. Check the **Specify Color** box and choose an desired color to specify a font color for the title. Specify the **Font Size** and the actual title text in the box provided. Special strings may be entered, preceded by a '@' symbol, which will be automatically interpreted as an appropriate string to place in the title. A short list is below, but a more complete list of options is found in the [Special Strings for Plot Features help topic](#special-strings-for-plot-features-sometimes-called-magic-strings).

@CTGName will display the appropriate contingency name

@CTGEvents will show the transient result event.

@CTGMemo will show the memo of the transient contingency in the plot.

@CASENAME will show the name of the case presently open.

@BUILDDATE will show the Simulator patch build date. @DATETIME will show the present date and time.

@DATE will show the present date.

@TIME will show the present time.

Scale

Maximum

Check the box next to Automatic to have the maximum value on the scale automatically determined based on the results or uncheck this box and specify the value manually. Check the box next to Round to have the maximum value rounded when the Automatic checkbox is also checked.

Increment

Specify the increment between scale markings. If zero is specified, the increment will be determined automatically.

Minimum

Check the box next to Automatic to have the minimum value on the scale automatically determined based on the results or uncheck this box and specify the value manually. Check the box next to Round to have the minimum value rounded when the Automatic checkbox is also checked.

Horizontal Axis Value

The horizontal axis value is normally chosen to be time. This is the default if nothing else is selected. However, the option is allowed to choose a different value for the horizontal axis.

Clear

Click this button to restore the horizontal axis value to the default of Time.

Object Plotted

Select an object to be used for the horizontal axis values.

Field Plotted

Select the field for the associated object to be used for the horizontal axis values.

When no object is specified, this choices are a list of independent values tracked by the tool. For Transient Stability, this is *Time in Seconds*. For the PV analysis, this includes *Nominal Shift*, *Export*, and *Import*.

Plot Pre-Contingency Values

If the Pre-contingency box is checked, the x values for each plotted scenario will come from the base case instead of the results of a given scenario.

---

<a id="vertical-axis"></a>

## Vertical Axis

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Vertical_Axis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Vertical_Axis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Vertical Axis sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the axis group that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab. An axis group is selected if any of its corresponding plot series are selected in the list.

![Transient Stability Dialog Plot Designer Vertical Axis](images/Transient_Stability_Dialog_Plot_Designer_Vertical_Axis.gif)

The vertical axis is shared by all plot series in the selected axis group.

Axis Group Number

This is an informational field. Each axis group is assigned a number when it is created. The user cannot change this value.

Add Axis Group

Click this button to add an axis group to the currently selected subplot.

Delete Axis Group

Click this button to delete the currently selected axis group.

Show Vertical Axis on Plot

Check this box to show the vertical axis for this access group on the current subplot.

Inverted

Check this box to have the scale on the vertical axis go from high to low values when moving bottom to top along the axis.

Logarithmic

Check this box to use a logarithmic scale on the vertical axis of the current axis group.

Title

Check the **Visible** box to make the vertical axis title shown for the current axis group. Check the **Specify Color** box and choose an desired color to specify a font color for the title. Specify the **Font Size** and the actual title text in the box provided. Special strings may be entered, preceded by a '@' symbol, which will be automatically interpreted as an appropriate string to place in the title. A short list is below, but a more complete list of options is found in the [Special Strings for Plot Features help topic](#special-strings-for-plot-features-sometimes-called-magic-strings).

@CTGName will display the appropriate contingency name

@CTGEvents will show the transient result event.

@CTGMemo will show the memo of the transient contingency in the plot.

@CASENAME will show the name of the case presently open.

@BUILDDATE will show the Simulator patch build date. @DATETIME will show the present date and time.

@DATE will show the present date.

@TIME will show the present time.

Scale

Maximum

Check the box next to Automatic to have the maximum value on the scale automatically determined based on the results or uncheck this box and specify the value manually. Check the box next to Round to have the maximum value rounded when the Automatic checkbox is also checked.

Increment

Specify the increment between scale markings. If zero is specified, the increment will be determined automatically.

Minimum

Check the box next to Automatic to have the minimum value on the scale automatically determined based on the results or uncheck this box and specify the value manually. Check the box next to Round to have the minimum value rounded when the Automatic checkbox is also checked.

---

<a id="plot-series-list"></a>

## Plot Series List

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot_Series_List.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot_Series_List.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plot Series List sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the plot series contained in the axis group that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab.

![Transient Stability Dialog Plot Designer Plot Series List](images/Transient_Stability_Dialog_Plot_Designer_Plot_Series_List.gif)

Axis Group Number

This is an informational field. Each axis group is assigned a number when it is created. The user cannot change this value.

Add Axis Group

Click this button to add an axis group to the currently selected subplot.

Delete Axis Group

Click this button to delete the currently selected axis group.

Plot Series List Table

This is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) listing all of the plot series contained in the currently selected axis group. Common options like color, thickness, and style that determine how a plot series is shown are listed in this display and can be modified here. The same fields can be modified for a single selected plot series on the [Plot Series](#plot-series) sub-tab.

---

<a id="plot-series"></a>

## Plot Series

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot_Series.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_Plot_Series.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plot Series sub-tab is available on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog) on the [Plot Designer](#plot-designer) sub-tab of the [Plots](#plots) page. The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation.

This tab provides information about the plot series that is currently selected in the **Plots, Subplots, Axis Groups** list found on the [Plot Designer](#plot-designer) sub-tab.

![Transient Stability Dialog Plot Designer Plot Series](images/Transient_Stability_Dialog_Plot_Designer_Plot_Series.gif)

Object plotted

This shows the object that is represented by the selected plot series. This is for informational purposes only and cannot be changed here.

Field plotted

This shows the field that is represented by the selected plot series. This is for informational purposes only and cannot be changed here.

Delete Plot Series

Click this button to delete the selected plot series.

Plot Series Visible

Check this box for the plot series to be shown on the plot.

Color

Click the color box or the **Change** button to select the color of the line drawn for the plot series.

Plot Series Type

Select whether the plot series should be shown by a *Line Series* or a *Point Series*. If shown by a *Point Series*, the **Point Attributes** options will be enabled allowing selection of the style and size of the points.

Line Attributes

These options will only be enabled if the **Plot Series Type** is a *Line Series*.

Style

*Solid*, *Dashed*, *Dot*, *Dash Dot*, and *Dash Dot Dot* are the valid options for the line style.

Thickness

Set the thickness of the line.

Stairs

Select whether the line series should be drawn with No stairs, Stair, or Inverted stair. The stair options connected successive points in a stair pattern instead of a straight line.

Symbol Every

Set this option to something other than zero if a symbol should be placed on the line for better identification. Making this value larger will make the symbol placing less dense. Use the **Point Attributes** options to define the style and size of the symbols.

Conversion of value to plot

These options will allow to have plots based on the following options: *Actual value*, *Percent of initial value*, *Deviation from initial value*, or *Percent deviation from initial*.

Point Attributes

These options will only be enabled if the **Plot Series Type** is a *Point Series* or choosing to include symbols on a *Line Series* by setting the **Symbol Every** option to something other than zero.

Style

This determines the shape of any plot series symbols.

Height

This sets the vertical size of the plot series symbols.

Width

This sets the horizontal size of the plot series symbols.

---

<a id="special-strings-for-plot-features-sometimes-called-magic-strings"></a>

## Special Strings for Plot Features (sometimes called "Magic Strings")

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_SpecialStrings.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plot_Designer_SpecialStrings.htm)*

Various parts of a plot, such as the [Title Block](#title-block). [Chart](#chart). [Vertical Axis](#vertical-axis). and [Horizontal Axis](#horizontal-axis), have places for title, footer or memo which are specified as a user entered string. These strings are most often simply placed on the plot based on what is entered. However special strings, preceded by a '@' symbol, may be entered and the software will then automatically replace the string with the appropriate special string. The following are special strings that are available for parts of the transient stability plots.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Special String</p></td>
<td><p>What Special String is Replaced With</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@BUILDDATE</p></td>
<td><p>Simulator Patch Build Date</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@VERSION</p></td>
<td><p>Simulator Version Number</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@DATETIME</p></td>
<td><p>present date and time</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@DATE</p></td>
<td><p>present date</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@TIME</p></td>
<td><p>present time</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@CASENAME</p></td>
<td><p>the name of the case presently open (the path and file name)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@CASEFILEPATH</p></td>
<td><p>the directory path on the computer of the case presently open</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@CASEFILENAME</p></td>
<td><p>the file name of the case presently open</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@CTGEVENTS</p></td>
<td><p>all the events in the transient contingency (warning this can be very long)</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@CTGEVENTSUSER</p></td>
<td><p>only the user-defined event in the transient contingency</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@CTGNAME</p></td>
<td><p>name of the contingency</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@CTGMEMO</p></td>
<td><p>memo field of the contingency</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>@CTGvariablename:digits:rod</p></td>
<td><p>Special string for ANY variablename of a TSContingency with the syntax @CTGvariablename:digits:rod</p>
<p>The special string must start with @CTG and this then followed by the variablename and then optionally followed by syntax of :digits:rod to specify the number of digits and the number of decimal places to include.</p>
<p><span class="underline">Example include the following</span></p>
<p>@CTGCategory adds the Category string</p>
<p>@CTGLoadMWIslanded:8:3 adds the LoadMWIslanded field with 8 digits and 3 digits to the right of the decimal.</p>
<p>@CTGGenMWTripped:6:2 adds the GenMWTripped field with 6 digits and 3 digits to the right of the decimal.</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>@MODELFIELD&lt;ObjectType 'key1' 'key2' variablename:digits:rod&gt;</p></td>
<td><p>@MODELFIELD&lt;ObjectType 'key1' 'key2' variablename:digits:rod&gt;</p>
<p>Special string starts with @MODELFIELD followed by a string enclosed by &lt; and &gt; with string identifying an object in the model followed by variablename:digits:rod.</p>
<p><span class="underline">Example</span></p>
<p>@MODELFIELD&lt;Gen '87523' 'AB' MW:6:2&gt; : show a generator MW field with 6 digits and 2 decimal places</p></td>
</tr>
</tbody>
</table>

---

<a id="user-interaction-with-plots"></a>

## User Interaction with Plots

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots_Interactions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Plots_Interactions.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Plots page is found on the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and the [PV Curve dialog](29-pv-and-qv-curves.md#dialog). The vast majority of features for plotting are common to both Transient Stability and PV Curves. In cases where there is a difference in functionality it will be denoted in the help documentation..

A set of common user-interaction features with the plot has been implemented. To Pan on a chart, simply right-click and drag on the plot. This will move the view up, down, left, or right depending on which direction you drag the mouse. To zoom in on the plot, left-click and drag towards to the left and form a square into which the view will zoom. To zoom out on plot left-click and drag towards the right and the view will zoom back out to the default zoomed out view.

Navigating Around a Plot

Pan Around Plot

Right-click on the background portion of a subplot and drag with the mouse.

Zoom In

Left-click on the background portion of a subplot and drag down with the mouse.

Zoom Out

Left-click on the background portion of a subplot and drag up with the mouse. The view will zoom back out to the default zoomed out view of the plot.

Data Information

Left-clicking on a plot series will provide information about the selected point. This will also be shown in a hint which appears as you hover your mouse over a particular plot series.

Making Plot Series Visible

Below each subplot chart there is a key listing all of the plot series on that subplot. Check and uncheck the box next to a plot series to make that plot series visible or not visible. (Note: after a chart has more than 12 plot series, the legend is not drawn by default.)

Chart Local Menu

A local menu is available for the chart by right-clicking below the chart portion of a subplot, right-clicking on a plot series, or clicking the little drop-down arrow found in the bottom right-hand corner of each subplot. (Note: Right-clicking on the region of the chart showing the plot series will not bring up this menu because right-clicking activates the dragging on these charts.) The choices which appear are as follows.

Bus View...

Will automatically open the bus view related to the object associated with the plot series.

Plot Series Information...

Provides information and a summary about the selected plot series.

Print Preview...

Provides the ability to access a print options for the chart

Export...

Provides the ability to export an image of the chart to file types including an Enhanced Metafile, Bitmap, JPEG, PDF, SVG, PNG, VML, or EPS

Copy

Will copy the image as a metafile to the Windows clipboard so that the image can then be pasted into another program.

Export with Options

Provides access to export images, but in addition provides access to export the data behind the plot series to a text file, XML, HTML or Excel. To export data you must go to the **Data** tab on the dialog which appears.

Advanced Options

Remember that the most common options available for plots and associated components are discussed in the [Plot Designer](#plot-designer) section.

There are a number of advanced options that are associated with a subplot. These advanced options are only accessible through a local menu available with each subplot. These advanced options can be saved or loaded from file.

Load Advanced Results

Choose this option to open a file which has the Advanced Options stored in it.

Save Advanced Result

Choose this option to save a file which has the Advanced Options stored in it.

Print All Charts and Title Block

Prints the current plot display

Copy All Charts and Title Block

Loads the current plot display onto the clipboard

Close All Plots

Closes all open plots.

---

<a id="result-analyzer"></a>

## Result Analyzer

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalyzer.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalyzer.htm)*

The Transient Stability Result Analyzer can be found by going to the [Transient Stability Dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog) and choosing the **Result Analyzer-Damping** on the left-hand side of the dialog. Normally you start by choosing the first item under this link for **Time Window Definitions**.

This analyzer allows you to do 2 types of calculations on your transient stability results over a time window which you define.

<table>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Statistical Calculations of time-varying stability results (Maximum, Minimum, Average, and so forth)</p></li>
<li><p>Modal Analysis: determines the frequency and damping of the results</p></li>
</ol>
<p><a href="#modal-analysis-theory">For a more complete description of how the Result Analyzer performs Modal Analysis and what Modal Analysis does see the help topic on the</a> <a href="#modal-analysis-theory">Theory of Modal Analysis.</a></p></td>
<td><img src="images/Transient_Stability_Dialog_ResultAnalysisTimeWindowTheory.png" alt="Transient Stability Dialog ResultAnalysisTimeWindowTheory" /></td>
</tr>
</tbody>
</table>

![Transient Stability Dialog ResultAnalysisTimeWindowGrid](images/Transient_Stability_Dialog_ResultAnalysisTimeWindowGrid.png)

The first step to do this analysis is to define a set of Transient Result Analysis Time Window objects which define what results (which time-varying signals) to study and over what time window to study them. Once these Time Windows are defined clicking the **Analyze Results** button will perform the analysis on the results. Simulator will automatically load these results either from the [results stored in RAM](37-transient-stability-analysis-dialog-part1.md#storage-to-ram) or [results stored on hard drive in \*.TSR files](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive) in the same manner as clicking the [Generate Selected Plots on the Plot Designer](#plot-designer). PowerWorld will simply get the results from wherever you have stored them. You may clear all analysis results as well by clicking the button **Clear Analysis Results**.

Once you have configured time windows you may also check the box **Automatically analyze time windows and keep Signal Violations after running a transient stability simulation**. This will do exactly what it says. Read more about Signal Violations in the Time Window and Violation sections linked below for more information.

The remainder of the dialog consists of the following 5 tabs which have their own help topics describing them.

  - [Time Window Definitions](#result-analysis-time-window): This tab is where you define Transient Result Analysis Time Windows (TSResultAnalysisTimeWindows)

  - [Signal Violations](#result-analysis-signal-violation): This tab will show any signal violations based on options in the time window definition options (TSResultAnalysisViolation):

  - [Signal Statistics](#result-analysis-signal-statistics): This tab will statistical information about value analyzed. (TSResultAnalysisSignal)

  - [Signal Damping and Modes](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes): This tab will show information for each signal shown the contribution of various Frequency/Damping modes to each signal. (TSResultAnalysisSignal and TSResultAnalysisModeMagAngle)

  - [Modes](37-transient-stability-analysis-dialog-part3.md#result-analysis-mode): This tab will show information about each mode found in the signals being analyzed. See this help topic for more information about what a mode is. (TSResultAnalysisMode and TSResultAnalysisModeMagAngle)

---

<a id="modal-analysis-theory"></a>

## Modal Analysis Theory

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisModalAnalysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisModalAnalysis.htm)*

### Modal Analysis (Added in Version 22)

Modal Analysis takes as an input a time-series of a numeric value (we call this a **Signal**) and then does a calculation of a specified time-window to break this time-series up into the summation of a set of damped sinusoidal waves. Each of these damped sinusoidal waves we call a **Mode**.

Signal

A signal is a time-series of a numeric value. In our case for transient stability this is the value of one field for one object over the period of time. For example it may be the Rotor Speed at a generator between 3 and 10 seconds and thus be a numeric representation of the following picture. From this example you can see that this signal is not just one frequency and that it has components of multiple frequencies. We will shortly numerically define an approximation of this signal as a summation of Modes.

![Transient Stability Dialog ResultAnalysisTheorySignal](images/Transient_Stability_Dialog_ResultAnalysisTheorySignal.png)

Mode

In our application, a mode is an exponential multiplied by a sinusoidal. Thus one mode is a time varying signal defined as follows.

![Transient Stability Dialog ResultAnalysisTheoryMode](images/Transient_Stability_Dialog_ResultAnalysisTheoryMode.png)

The exponential term defines the envelope of the sinusoidal. Modes can be either damped or undamped depending on the value in the exponent of the exponential term. Consider as an example a 2 Hz waveform which has either damped or undamped as in the following figure.

![Transient Stability Dialog ResultAnalysisTheoryDampedMode](images/Transient_Stability_Dialog_ResultAnalysisTheoryDampedMode.png)

Damping Ratio Percentage

The value of Lambda is a measure of damping, but the description of how damped a signal is should also depend on the frequency of the oscillation. Engineers frequency define a Damping Ratio Percentage as follows. Notice that when Lambda is negative (meaning the mode is damped), then the damping ratio percentage is positive.

![Transient Stability Dialog ResultAnalysisTheoryDampingRatioPerc](images/Transient_Stability_Dialog_ResultAnalysisTheoryDampingRatioPerc.png)

Approximating a Signal as Multiple Modes

A signal as shown earlier is made up of multiple models. We will define an approximation of our signal as a summation of modes, but the contribution of each mode to each signal is defined by a complex number representing both a magnitude and a phase relationship. As an example consider 3 modes as follows

![Transient Stability Dialog ResultAnalysisTheoryThreeModes](images/Transient_Stability_Dialog_ResultAnalysisTheoryThreeModes.png)

And then approximate our signal x(t) as a summation of those three modes

![Transient Stability Dialog ResultAnalysisTheoryThreeModesSummation](images/Transient_Stability_Dialog_ResultAnalysisTheoryThreeModesSummation.png)

Detrending

PowerWorld will also take into account a "trend" of the signal as well. Consider a signal like that shown in the next figure which is a linear increase with time added to a pure sine wave.

![Transient Stability Dialog ResultAnalysisTheoryDetrend](images/Transient_Stability_Dialog_ResultAnalysisTheoryDetrend.png)

Overall Signal Approximation

Our general modal analysis tool will do either a linear or quadratic detrending, but for now the Transient Result Analyzer always does a linear detrending calculation. The overall signal is then approximated as follows. The greentext parameters are assigned to the [TSResultAnalysisMode objects](37-transient-stability-analysis-dialog-part3.md#result-analysis-mode). The purple text parameters are assigned to the [TSResultAnalysisSignal objects](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes) which the red values are part of the TSResultAnalysisModeMagAngle objects. If we have 5 modes and 10 signals, then we will have 50 ModeMagAngle objects (one for each combination of 1 mode and 1 signal).

![Transient Stability Dialog ResultAnalysisSignalApproximation](images/Transient_Stability_Dialog_ResultAnalysisSignalApproximation.png)

Rank

In addition to the complex number assigned to each TSResultAnalysisModeMagAngle object, we also calculate a numeric value to rank each mode's contribution to the signal. To do this we only want to use the magnitude portion of that contribution as the phase angle simple represents a phase shift (basically a time-shift) of how the mode impacts the signal. The exponential matter too though because even though the pure magnitude may be small relative to other modes, if the mode is undamped then it will grow with time. As a result, to calculate a rank, PowerWorld uses the pure magnitude if the mode is damped and for undamped modes it uses the magnitude multiplied by the exponential at the end of the time window. This is depicted in the next image. The values actually displayed for Rank are then normalized across all modes for 1 signal so that the summation of the Rank values is 100. In this way the Rank can be thought of as a percentage contribution of the mode to a particular signal.

![Transient Stability Dialog ResultAnalysisSignalModeRank](images/Transient_Stability_Dialog_ResultAnalysisSignalModeRank.png)

When making decisions for user display about which signal are damped or undamped, we then use this Rank to determine whether to consider a model as contributing enough (Rank \> **UndampMinRank** specified with the [time window](#result-analysis-time-window)) to the signal that we would consider the signal to be undamped if the model has too low of a damping ratio percentage. This is determined by the value

Choosing the Time Window

When doing a Modal Analysis calculation, special care should be taken when choosing the Start and End Time of the time window. If a time window is chosen which has a large discrete jump (like occurs upon apply or clearing a fault), then the algorithms will still try to fit a set of damped sinusoids to these signals. You may even get what appears to be a decent match, but will not be a useful calculation.

Calculation of Modes using Iterated Matrix Pencil Method

There are many numerical techniques which can be used to calculate the modes within a group of signals. The Transient Result Analyzer uses the Iterated Matrix Pencil method.

Realize that the modes apply to the entire group of signals. Thus if you have 20,000 bus frequencies, there are not 20,000 different modes associated with that group of signals. In most power system signals we're looking at, there are probably only a dozen or less modes within that group of signals. Because of this knowledge that we don't need all the signals to calculate our modes, the Result Analyzer uses the following process to perform modal analysis

1.  Calculate the trend line or quadratic for each signal in your list of 20,000 signals. The curves passed to the algorithm for finding models will then use the numerical values with these trend lines substracted from them (this is called detrending).

2.  Choose one signal from the list in step 1 (This is the **ModalStartObject** and **ModalStartField** as defined in the [time window](#result-analysis-time-window) .

3.  Sample the chosen signals a frequency of 2 times the **ModalMaxHz** as specified with the [time window](#result-analysis-time-window).

4.  Perform a modal analysis calculation using the Matrix Pencil method on the signals in Step \#3. (This creates the [TSResultAnalysisMode objects](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes))

5.  Calculate all the complex numbers that fit the list of all 20,000 signals you have to this short list of modes (this calculation is much faster than the modal analysis so doing it on all signals is very fast). This calculates the [TSResultAnalysisSignal objects](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes) and the [TSResultAnalysisModeMagAngle objects](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes).

6.  Calculate the signal error cost function for each signal by comparing the actual signal numeric values to the approximated signal. Whatever signal has the worse match will now be added to the list of signals to include in the modal calculation

7.  Go back to Step \#3 and repeat the process until you reach the **ModalMaxIterations** as specified with the [time window](#result-analysis-time-window).

---

<a id="result-analysis-time-window"></a>

## Result Analysis Time Window

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisTimeWindow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisTimeWindow.htm)*

[A description of the theory of the calculation of the Transient Result Analyzer Modal Calculation is in a separate topic.](#modal-analysis-theory)

The Transient Stability Analysis Time Window (TSResultAnalysisTimeWindow) is an object created by the user to specify which signals to analyze and between which start and end time. The input dialog for this option is shown below and the case information display showing a list of define time windows follows this.

The Result Analyzer will then calculate [Signal Statistics](#result-analysis-signal-statistics), [Modes](37-transient-stability-analysis-dialog-part3.md#result-analysis-mode), and then the [contribution of each mode to each Signa](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes)l. It will also then record [Signal Violations](#result-analysis-signal-violation) if any.

![Transient Stability Dialog ResultAnalysisTimeWindowDialog](images/Transient_Stability_Dialog_ResultAnalysisTimeWindowDialog.png)

![Transient Stability Dialog ResultAnalysisTimeWindowGrid](images/Transient_Stability_Dialog_ResultAnalysisTimeWindowGrid.png)

Name

Name of the Time Window. This is a unique string identifier for the TSResultAnalysisTimeWindow object.

Include

Set to YES (or check the box on the dialog) to include this time window when doing the statistical and modal analysis

PlotName

Name of the plot which defines which object/fields to perform analysis on. If no plot is defined then the Object Type, Object Filter, and Object Field will determine which object/fields to consider.

ObjectType

When no plot name is specified, this is the type of object included in the analysis

ObjectField

When no plot name is specified, this is the field used in the analysis

ObjectFilter

When no plot name is specified, this is a filter determining which objects of the "Object Type" are used in the analysis

TimeMeaning

Time Meaning determines how the Start and End time are intepreted. Set to **Absolute** to use times exactly. Set to **Delta** to indicate an delay after the the last user-specified contingency event. This makes the start/end time dependent on the contingency definition. On the dialog there is a check box that when checked treats this as **Delta**

TimeStart

Start time in seconds. Note that TimeMeaning affects the use of this value.

TimeEnd

End time in seconds. Note that TimeMeaning affects the use of this value.

Do Modal Analysis (ModalDo)

Set to YES (or check the box on the Modes and Damping portion of the dialog) to also perform Mode and Damping analysis on the signals.

Modal Max Freq (ModalMaxHz)

Maximum frequency considered in the modal analysis. The input object/field time variation is sampled at 2 times this frequency. We do not use the full set of signal times because the speed of calculation for Modal Analysis is a function of the number of time points squared, thus the lower you set this value the faster the calculation will be. Normally we are not concerned with frequencies higher than about 2 - 5 Hz so set it as low as is reasonable for your system.

ModalIterations

The result analyzer uses a mathematical calculation called the Matrix Pencil method and PowerWorld iteratively calls the Matrix Pencil method adding a signal at each step that has the worse match at each iteration. The total number of iterations and thus signals included in the Matrix Panel calculation is thus determined by this option. For more information on this calculation see the [Signal Modes](37-transient-stability-analysis-dialog-part3.md#result-analysis-mode) help documentation.

ModalStartObject

This is the starting object used in the modal analysis calculation. When specified in the case information or AUX file is uses the syntax of the [object ID field](09-auxiliary-files-and-script-commands.md#objectid-field-for-use-in-auxiliary-fiels) used in AUX files.

ModalStartField

This is the starting field used in the modal analysis calculation

UndampMinHz

After getting modal results, modes with a frequency below this frequency will not cause a signal to be considered undamped. This is because modes with extremely low frequency may be calculated by the numerical algorithms. A frequency of 0.05 Hz has a period of 20 seconds, so if you're analyzing a time window of 10 seconds, then this mode is really just providing a shape of the overall response and not some oscillation within the window.

UndampDampPerc

After getting modal results, modes with a damping ratio percentage below this may cause a signal to be considered undamped

UndampMinRank

After getting modal results, for a particular signal only modes with a rank percentage based on magnitude above this threshold percentage will be considered when flagging a signal as undamped. Each signal performs a calculation to assign a ranking of each mode's contribution to that signal. The sum of the ranks are 100, but the expectation is that a signal will not have large contributions from all modes, so we want to judge whether a signal is unstable only on the modes that most contribute to it.

MaxViolStore

Enter an integer number of the maximum violations to store for each type of violation with a particular Time Window/TSContingency pair. The types of violation that are possible are *Undamped*, *MaxDec*, *MaxInc*, *MaxMin*, *MaxDecPerc*, *MaxIncPerc*, and *MaxMinPerc*.

ViolMaxDecrease

Specify a value at which the Maximum Decrease for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxDec*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

ViolMaxIncrease

Specify a value at which the Maximum Increase for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxIncc*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

ViolMaxMin

Specify a value at which the Maximum - Minimum for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxMin*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

ViolMaxDecreasePercent

Specify a value at which the Maximum Percentage Decrease for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxDecPerc*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

ViolMaxIncreasePercent

Specify a value at which the Maximum Percentage Increase for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxIncPerc*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

ViolMaxMinPercent

Specify a value at which the Maximum - Minimum Percentage for a signal will be considered a violation. Violations created due to violating this setting will be considered of type *MaxMinPerc*. Enter zero to never report violations based on this. This is used for determining violations based on the [Signal Statistics](#result-analysis-signal-statistics).

---

<a id="result-analysis-signal-violation"></a>

## Result Analysis Signal Violation

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisViolation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisViolation.htm)*

[A description of the theory of the calculation of the Transient Result Analyzer Modal Calculation is in a separate topic.](#modal-analysis-theory)

Part of defining a [Transient Stability Analysis Time Window](#result-analysis-time-window) (TSResultAnalysisTimeWindows) are options to specify what is considered a violation of a signal for the Time Window. A Signal can be considered a violation if it meet criteria based on the statistics calculated or if the contribution from a mode which is considered undamped is high enough. While recording violations by the transient result analyzer, PowerWorld will limit the number of violations recorded based in the TIme Window option **MaxViolStore**. As violations of a particular type are recorded we will only keep this number of violations. We will however make sure that we keep the violations that have the maximum Rank.

On the Transient Stability Dialog under **Result Analyzer - Damping\\Signal Violations** you will find a table a TSResultAnalysisViolation objects. When looking at the violations, the display is filtered to show only the contingency chosen from the contingency drop-down shown in the red box below. In addition to make filtering by particular time windows, there is a display listing all time windows in the blue box below. By checking or unchecking particular time windows the list of violations is filtered. Each row in the table represents a violation and we call each of these rows a "TSResultAnalysisViolation". The information about the violation are then shown as columns.

![Transient Stability Dialog ResultAnalysisViolation](images/Transient_Stability_Dialog_ResultAnalysisViolation.png)

Undamped Violations

Each [Result Analysis Mode](37-transient-stability-analysis-dialog-part3.md#result-analysis-mode) calculated by the Modal Analysis will have a Frequency and a Damping Ratio Percentage calculated for it. A mode will be considered undamped based on two user-options specified with the Time Window: **UndampMinHz** and **UndampDampPerc**. Thus a Mode is only considered undamped if it meets the condition

**(Mode.Freq \> Window.UndampMinHz) AND (Mode.Damp \< Window.UndampDampPerc)**

We limit the modes based on frequency because low frequency modes. A frequency of 0.05 Hz has a period of 20 seconds, so if you're analyzing a time window of 10 seconds, then this mode is really just providing a shape of the overall response and not some oscillation within the window.

In addition to this a [signal](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes) will only be considered undamped if an undamped Mode has a [large contribution to that particular signal](37-transient-stability-analysis-dialog-part3.md#result-analysis-signal-modes) based on the user-option specified with the Time Window **UndampMinRank**. Thus we will look at all the contributions (TSResultAnalysisModeMagAngle objects) to see if one exists for which the mode is undamped AND Contribution.Rank \> Window.UndampMinRank.

Each signal performs a calculation to assign a ranking of each mode's contribution to that signal. The sum of the ranks are 100, but the expectation is that a signal will not have large contributions from all modes, so we want to judge whether a signal is unstable only on the modes that most contribute to it. This is achieved by specifying the **UndampMinRank**.

If these criteria are met for a particular Signal, after the [Transient Result Analyzer](#result-analyzer) performs its calculations of modes a Transient Result Analysis Violation (TSResultAnalysisViolation) will be recorded which has a Type of *Undamped*.

Statistical Violations

You can view all the details of [signal statistics](#result-analysis-signal-statistics) after Analyzing Results, however a time window also has user input values for **ViolMaxDecrease**, **ViolMaxIncrease**, **ViolMaxMin**, **ViolMaxDecreasePercent**, **ViolMaxIncreasePercent**, and **ViolMaxMinPercent** which will cause violations to be recorded as well. These values specify a threshold for a respective change in the signal over the time window which should be considered a violation. Specifying a value of zero with these values instruct PowerWorld to never record violations. For each of the thresholds that a met for a signal, a Transient Result Analysis Violation (TSResultAnalysisViolation) will be records which has a Type of *MaxDec*, *MaxInc*, *MaxMin*, *MaxDecPerc*, *MaxIncPerc*, or *MaxMinPerc*.

The columns for the list of violation are as follows

Window

The name of the [Time Window](#result-analysis-time-window) for which the violation was recorded

Contingency

The name of the [Transient Contingency](37-transient-stability-analysis-dialog-part1.md#simulation) for which the violation was recorded

Object

Identifying information for the object of the signal related to the violation

Field

The field for the signal related to the violation

Type

Specifies the type of violation as explained above . The possible values are *Undamped*, *MaxDec*, *MaxInc*, *MaxMin*, *MaxDecPerc*, *MaxIncPerc*, or *MaxMinPerc*.

Freq

If the violation is of type Undamped, then this will be the frequency of the undamped mode associated with the signal.

Rank

The rank for the violation. The meaning of this value depends on the type. For Undamped this is the rank of the mode for the respective signal. For the other types this is the same as the Value of the violation.

Value

The value for the violation. The meaning of this value depends on the type. For Undamped this is the damping ratio percentage. For the other values they are the numeric values for the respective field of a signal.

Object Fields (some of these are shown by default such as bus number, Areas, Zones, Owner)

There are various fields to show information about buses, areas, zones, and so forth for the object related the violation

---

<a id="result-analysis-signal-statistics"></a>

## Result Analysis Signal Statistics

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisSignalStatistics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_ResultAnalysisSignalStatistics.htm)*

[A description of the theory of the calculation of the Transient Result Analyzer Modal Calculation is in a separate topic.](#modal-analysis-theory)

When performing results analysis on defined [Transient Stability Result Analaysis Time Windows](#result-analysis-time-window), with every signal being analyzed and PowerWorld will store the original, maximum, minimum, average and standard deviation of the signal. The time at which the minimum and maximum occurred will also be stored. These values can then be presented in the table of Signal Statistics as shown in the first image below. In addition a dialog exists as shown second image below.

When looking at the statistics, the display is filtered to show only the contingency chosen from the contingency drop-down shown in the red box below. In addition to make filtering by particular time windows, there is a display listing all time windows in the blue box below. By checking or unchecking particular time windows the list of signals is filtered. Each row in the table represents a particular field of a particular object and we call each of these rows a "TSResultAnalysisSignal". The statistic values are then shown as columns.

![Transient Stability Dialog ResultAnalysisSignalStatisticsGrid](images/Transient_Stability_Dialog_ResultAnalysisSignalStatisticsGrid.png)

![Transient Stability Dialog ResultAnalysisSignalStatistics](images/Transient_Stability_Dialog_ResultAnalysisSignalStatistics.png)
