---
title: "Building Onelines — Branches and Devices"
part: "Oneline Diagrams"
chapter_file: "12-building-onelines-branches-and-devices.md"
topics: 26
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Building Onelines — Branches and Devices

Inserting transmission lines, transformers, series capacitors, switched shunts, interfaces, injection groups and oneline links.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (26)**

- [Transmission Line Display Objects](#transmission-line-display-objects)
- [Transmission Line Fields on Onelines](#transmission-line-fields-on-onelines)
- [Circuit Breakers on Onelines](#circuit-breakers-on-onelines)
- [Line Flow Pie Charts on Onelines](#line-flow-pie-charts-on-onelines)
- [Line Flow Gauges](#line-flow-gauges)
- [Line Flow Gauge Options Dialog](#line-flow-gauge-options-dialog)
- [Line Flow Arrows on Onelines](#line-flow-arrows-on-onelines)
- [DC Transmission Line Display Objects](#dc-transmission-line-display-objects)
- [Multi-section Transmission Line Display Objects](#multi-section-transmission-line-display-objects)
- [Transformer Display Objects](#transformer-display-objects)
- [Transformer Fields on Onelines](#transformer-fields-on-onelines)
- [Three Winding Transformer Display Objects](#three-winding-transformer-display-objects)
- [Series Capacitor Display Objects](#series-capacitor-display-objects)
- [Series Capacitor Fields on Onelines](#series-capacitor-fields-on-onelines)
- [Switched Shunt Display Objects](#switched-shunt-display-objects)
- [Switched Shunt Fields on Onelines](#switched-shunt-fields-on-onelines)
- [Interface Display Objects](#interface-display-objects)
- [Automatically Inserting Interface Display Objects](#automatically-inserting-interface-display-objects)
- [Interface Fields on Onelines](#interface-fields-on-onelines)
- [InterArea Flow Options Dialog](#interarea-flow-options-dialog)
- [Interface Pie Charts on Onelines](#interface-pie-charts-on-onelines)
- [Loading NERC Flowgates](#loading-nerc-flowgates)
- [Saving NERC Flowgates](#saving-nerc-flowgates)
- [Injection Group Display Objects](#injection-group-display-objects)
- [Links to Onelines and Auxiliary Files](#links-to-onelines-and-auxiliary-files)
- [Document Links on Onelines](#document-links-on-onelines)

---

<a id="transmission-line-display-objects"></a>

## Transmission Line Display Objects

*Source: [`Content/MainDocumentation_HTML/Transmission_Line_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Line_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transmission lines are represented on the onelines using multiple segment lines drawn between buses. Transmission lines may be equipped with circuit breakers that can be used to change the line's status. You can also add [pie charts](#line-flow-pie-charts-on-onelines) and [line fields](#transmission-line-fields-on-onelines) to transmission lines to indicate how heavily loaded the line is. The appearance of transmission lines, including line thickness and color, may also be customized.

Run Mode

Simulator's [animation](15-using-onelines-tools-and-options.md#oneline-animation) feature can be used to indicate the magnitude of the flow on the transmission line, either in MW or in terms of the line's percentage loading. You can customize the line flow animation using the **Animated Flows Options** on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on a transmission line displays the line's local menu, from which you can choose to inspect the [Branch Information Dialog.](07-object-properties-run-mode-and-general-part1.md#linetransformer-information)

Edit Mode

To add a new transmission line to the case, first select **Network \> Transmission Line** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the first bus for the transmission line (the *from* bus) and click the left mouse button. Add more segments to the line by moving the cursor and clicking with the left mouse button. To complete adding a new line, place the cursor on the second bus for the line (the *to* bus) and double-click with the left mouse button. This calls up the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options). The *from* and *to* bus numbers are set automatically provided the line starts and ends on existing buses. If there is just one line between the buses, the circuit number should be "1." For multiple lines between buses, you must give each a unique circuit number. Enter the thickness of the lines \[in pixels\] used to display the transmission line. Enter the per unit (100 MVA base by default) resistance, reactance, total charging susceptance (that is B not B/2) for the line, and an MVA rating. Select OK to add the line. If you do not want to add the line to the case, select **Cancel**.

To modify the parameters for an existing line, position the cursor anywhere on the line and right-click. This brings up the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options), which you can use to change various line parameters.

To change the physical appearance of the line (i.e. line color, line thickness, etc.), make use of the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group.

To change the shape of the line, first left-click on the line to select it. This causes handles to appear at each vertex. You can then move any vertex clicking and holding the left mouse button down on the vertex, dragging it to a new location, and then releasing the mouse button. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the line where you would like to add a vertex.

To convert a transmission line to a background line, right-click on the line and select "Convert to background line..." from the local menu.

---

<a id="transmission-line-fields-on-onelines"></a>

## Transmission Line Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Line_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Line field objects are used to show values associated with Transmission Lines, DC Transmission Lines, and Multi-Section Transmission Lines. The objects are different for each type of line object, but adding and editing them are very similar.

Run Mode

Right clicking on the line field gives you the option to open either the dialog for the field or the dialog for the object associated with the field. The following options are available depending on the type of line object being clicked on:

Transmission Line

Options are available for opening either the [Line Field Information Dialog](06-object-properties-edit-mode-part2.md#line-field-information) or the [Line/Transformer Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information).

DC Transmission Line

Options are available for opening either the [DC Line Field Information Dialog](52-additional-linked-topics-part1.md#dc-line-field-options-dialog) or the [DC Line Dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options).

Multi-Section Transmission Line

Options are available for opening either the [Multi-Section Line Field Information Dialog](52-additional-linked-topics-part1.md#multi-section-line-field-options) or the [Multi-Section Line Dialog](06-object-properties-edit-mode-part2.md#multi-section-line-information).

Edit Mode

To enter a new line field, select the following options based on the type of line field being inserted. These options are found on the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab:

Transmission Line

**Field \> Transmission Line Field**

DC Transmission Line

**Field \> DC Transmission Line Field**

Multi-Section Transmission Line

**Field \> MS Transmission Line Field**

After selecting the appropriate option, then click near the line object to which you want to add the field. You can also add a field without a corresponding display object being present. The appropriate line field dialog will open. Enter the *near* and *far* bus number associated with the device (the default values for these fields correspond to the device on which you clicked) and the circuit number of the device.

To modify the parameters of an existing line field, position the cursor anywhere on the object and right-click. This again brings up the appropriate line field dialog. Select ![Display zoom icon](images/Display_zoom_icon.jpg) from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the Draw ribbon tab to change many of the line field's display attributes.

Another way to add line fields to the oneline entails right-clicking the line and selecting *Add New Fields Around Line* from the resulting local menu. Please see [Inserting and Placing Multiple Display Fields](11-building-onelines-network-objects.md#inserting-and-placing-multiple-display-fields) for more details.

---

<a id="circuit-breakers-on-onelines"></a>

## Circuit Breakers on Onelines

*Source: [`Content/MainDocumentation_HTML/Circuit_Breakers_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Circuit_Breakers_on_Onelines.htm)*

Circuit breakers are used to open or close transmission lines and transformers. They are also used to place generators, loads and switched shunts in or out of service. By default, closed circuit breakers are shown as solid red squares, while open circuit breakers are shown as a green square outline. The color and filled or unfilled properties of circuit breakers can be modified in the [Oneline Display Options](11-building-onelines-network-objects.md#oneline-display-options) under [Display Object Options](15-using-onelines-tools-and-options.md#display-object-options). Only those circuit breakers that are set to use the default shape will abide by the shape specified with the Oneline Display Options. Circuit breakers for generators, loads, and switched shunts always use the rectangle shape. Circuit breakers that are automatically inserted for transmission lines and transformers will use the default shape unless the user specifies a different shape.

To change the status of a breaker, left-click on the breaker while in run mode. A circuit breaker directly controls the status of its associated display object. One breaker is shown on the line connecting a generator, load, or shunt to its associated bus. Two breakers are shown by default on transmission lines and transformers. Opening either of the line's circuit breakers opens the transmission line or transformer; you do not have to open circuit breakers at both ends of the line.

Note: Circuit breakers cannot be placed on dc transmission lines.

Edit Mode

By default, when you add a new display object to a oneline diagram, the necessary circuit breakers are automatically added at each end of the branch.

To add a new circuit breaker to the oneline, select **Indication \> Circuit Breaker** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and then click the line to which you want to add the breaker. The Circuit Breaker Options dialog will appear with the *from* and *to bus* numbers, and the circuit number automatically set to identify the line you selected. Specify the size for the switch and its initial status, as well as whether it will be anchored to the line so that it will move with the line. Click **OK** to add the circuit breaker, or click **Cancel** to abort the process. To add more circuit breakers to the line, simply repeat this procedure.

The shape of a branch circuit breaker can be user-specified on the Circuit Breaker Options dialog. If the option to *Use Default* is selected for the **Shape**, the shape is dictated by the default circuit breaker shape specified with the [Oneline Display Options](11-building-onelines-network-objects.md#oneline-display-options) under the [Display Object Options](15-using-onelines-tools-and-options.md#display-object-options). If a non-default shape is specified that requires an orientation, the **Orientation** option will be enabled.

To modify the parameters for an existing breaker, position the cursor anywhere on the device and right-click. This invokes the Circuit Breaker Options Dialog, from which you can change many of the breaker's parameters. Additional display settings for the circuit breaker can be accessed by selecting **![Display zoom icon](images/Display_zoom_icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group.

You can toggle the status of Transmission Line and Transformer circuit breakers while in Edit Mode by right-clicking on the associated line or transformer and selecting **Open Line** or **Close Line** from the local menu.

Run Mode

Circuit Breaker status can be toggled in Run Mode by Left-Clicking on a breaker to place its associated object either in or out of service. If the simulation is currently running, any effects of changing a circuit breaker’s status are immediately shown on the oneline.

---

<a id="line-flow-pie-charts-on-onelines"></a>

## Line Flow Pie Charts on Onelines

*Source: [`Content/MainDocumentation_HTML/Line_Flow_Pie_Charts_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Flow_Pie_Charts_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The line flow pie charts are used to indicate the percentage MVA, MW, or Mvar loading of a transmission line or a transformer. The degree to which the pie chart is filled shows how close the device is to its limit (provided the device has a nonzero limit). A line flow pie chart becomes completely filled when the device's flow meets or exceeds 100% of its rating.

For pie charts for objects that are not associated with line flows, see [Pie Charts / Gauges](https://www.powerworld.com/WebHelpRelatedTopic1.Click\(\)).

Use the *Pie Chart Options* tab of the [Oneline Display Options Dialog](11-building-onelines-network-objects.md#oneline-display-options) to customize various attributes of all pie charts. The tab allows you to define a warning level at which the size and color of the pie charts will change to a size and color you specify. The tab also allows you define a limit percent as well as the size and color to which to change the pie charts when their corresponding devices violate their limits. You can also specify whether the pie charts should reveal total power flow (MVA), real power flow (MW), or reactive power flow (MVR). The oneline display options dialog can be invoked either by selecting **Oneline Display Options** from the **Oneline Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab or by right-clicking on the background of the oneline diagram and selecting *Oneline Display Options* from the resulting local menu.

Right clicking on the pie chart displays the Line Flow Pie Chart Options Dialog. This dialog allows you to view the *from* and *to bus* numbers and the circuit number of the line/transformer associated with the pie chart. You can change the pie chart's size and the MVA rating of the line/transformer associated with the pie chart.

Edit Mode

To enter a new line flow pie chart, select **Pies/Gauges \> Line Flow Pie Chart** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab[](02-simulator-ribbon.md#individual-insert-ribbon-group) and click on the line or transformer to which you want to add the pie chart. This opens the Line Flow Pie Chart Options Dialog box. Enter the near and far bus number associated with the device (these fields default to the terminal bus numbers of the device on which you clicked), the circuit number of the device, and the desired size of the pie chart. The field will display the flow value at the *near end* of the device. Enter the size of the device. Select *OK* to insert the line flow pie chart. Otherwise, select **Cancel**.

To modify the parameters of an existing line flow pie chart, position the cursor anywhere on the object and right-click. This again brings up the Line Flow Pie Chart Options Dialog box.

---

<a id="line-flow-gauges"></a>

## Line Flow Gauges

*Source: [`Content/MainDocumentation_HTML/Old_Line_Flow_Gauges.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Old_Line_Flow_Gauges.htm)*

Line flow gauges provide a way to visualize the flow of a transmission line or transformer relative to its thermal rating. A gauge looks very much like a thermometer. As the temperature changes, the height of the mercury in the thermometer moves up and down. One reads the temperature measured by the thermometer by noting the marking that matches the top of the mercury. Line flow gauges in Simulator work the same way. A line flow gauge has two markings on its side, one for the designated minimum flow, and one for the designated maximum flow (the branch's rating). Inside the gauge is a filled region. The default color of the filled region is blue, but this can be changed. When you create the line flow gauge, you associate it with a transmission element, and you specify its fill color and its minimum and maximum flow levels. Once the gauge has been placed on a display, it will reveal changes in its associated branch's flow by varying the height of its filled region. This tool was introduced to provide an alternative to [line flow pie charts](#line-flow-pie-charts-on-onelines).

To add a line flow gauge to a display, switch to Edit Mode and select **Pies / Gauges \> Old Gauges \>** **Line** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Click on the oneline diagram where you would like the new line flow gauge to appear. The [Line Flow Gauge Options Dialog](#line-flow-gauge-options-dialog) will appear. Use this dialog to define the minimum and maximum flows for the line flow gauge, as well as its fill color and whether it should be anchored to its associated transmission element. After you click the "OK" button, the Line Flow Gauge Options Dialog will close, and the new line flow gauge will appear.

Once a gauge has been placed on the oneline, the height of its filled region will change as the flow of its transmission element changes. To modify any of the characteristics of the gauge, such as its key flow levels, fill color, and anchor setting, simply right-click on the line flow gauge to open the Line Flow Gauge Options Dialog again.

---

<a id="line-flow-gauge-options-dialog"></a>

## Line Flow Gauge Options Dialog

*Source: [`Content/MainDocumentation_HTML/Old_Line_Flow_Gauge_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Old_Line_Flow_Gauge_Options_Dialog.htm)*

The Line Flow Gauge Options Dialog is used to define and configure a [Line Flow gauge](#line-flow-gauges). A line flow gauge is associated with a particular line and reveals the line’s flow relative to specified minimum and maximum thermal flow levels. The height of the colored column in the line flow gauge indicates the line’s flow relative to these markings.

The dialog has the following controls:

Number, Name, and Find

Use the **Number** and **Name** dropdown boxes, in addition to the **Circuit** field, to identify the terminal buses to which the branch desired corresponds. It may be more convenient to press the **Find** button to open the [Find Dialog](04-model-explorer-and-case-information-part3.md#find-dialog-basics), which allows you to specify the line by either bus names or numbers using wildcards. When you first open the Line Flow Gauge Dialog, the bus names and numbers will correspond to the transmission line object that was closest to the point where you clicked.

Minimum and Maximum

Use these two spin edit boxes in the **MW Rating values** group box to specify the minimum and maximum flow levels. These settings determine where on the gauge its two markings will be drawn.

The Minimum and Maximum value will be taken from the Limit Monitoring settings for the current transmission line, unless you uncheck the option "*Set Limits According to Current Limit Monitoring Settings*".

Anchored

A line flow gauge is said to be [anchored](11-building-onelines-network-objects.md#anchored-objects) if, when you move its associated line object, the gauge moves with it. Check the Anchored check box to ensure that the gauge will move with its associated line. Otherwise, when you move its associated line object, the gauge will stay in its current position.

OK, Help, and Cancel

Click OK to finalize your settings. This will create a new line flow gauge object if you are trying to create one from scratch, or it will modify the appearance and settings of an existing one if you have chosen to modify one that has already been defined. Click Cancel to dispose of your changes.

---

<a id="line-flow-arrows-on-onelines"></a>

## Line Flow Arrows on Onelines

*Source: [`Content/MainDocumentation_HTML/Line_Flow_Arrows_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Flow_Arrows_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There is a separate object, called a Line Flow Arrow, that can be added to a transmission line or transformer. This object is different than the animated flow arrows that can be added to all transmission branches through settings with the [Oneline Display Options](11-building-onelines-network-objects.md#oneline-display-options). The Line Flow Arrow is a single static arrow that indicates the direction of MW flow on a transmission branch. The direction that the arrow points indicates the direction of MW flow, and there are additional options that allow the MW, Mvar, and MVA flow values to be displayed with the object.

To add a Line Flow Arrow to a transmission branch, select **Indication \> Line Flow Arrow** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab while in Edit mode, then left-click on the branch to which the Line Flow Arrow should be added. The Line/Transformer Flow Object dialog will open.

The dialog contains the following options:

FromBus, ToBus, Circuit

The from bus, to bus, and circuit of the branch the arrow represents. The from bus indicates the side of the branch at which the flow will be reported. The **Find** button can be used to open a dialog that allows the selection of a branch.

Size

Size of the object.

Angle

Angle indicating how the object will be drawn. Enter this in degrees.

Anchored

Check this box to anchor the flow arrow to the branch that it represents. If anchored, the flow arrow will move accordingly any time that the branch is moved.

Auto-determine angle when anchored

Check this box to have the angle of the flow arrow determined by the branch to which it is anchored rather than using the user-specified value. The angle is determined by how the branch is drawn and the direction of MW flow on the branch. It is a good idea to use this option by default. This will ensure that the arrow is drawn correctly with the direction of flow.

Show MW, Show Mvar, Show MVA, Show Units

Check the appropriate box to show the selected flow value in text along with the flow arrow object. Check the Show Units box to include units along with the value.

Flow Text Position

Select to place any flow text either **Above Arrow** or **Below Arrow**.

Total Digits in Field, Digits to Right of Decimal

Use these fields to indicate the total digits and digits to the right of the decimal for any values that are shown in the flow text.

By default, line flow arrows will be drawn with a lime color. The color and other attributes can be changed while in edit mode. To change how the line flow arrow is drawn, select the object to change and then select **Format** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This will open the Format Multiple Objects dialog and any attributes that can be modified will be enabled on this dialog.

---

<a id="dc-transmission-line-display-objects"></a>

## DC Transmission Line Display Objects

*Source: [`Content/MainDocumentation_HTML/DC_Transmission_Line_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Transmission_Line_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

DC transmission lines are represented on the onelines using multiple segment lines drawn between two buses. [Line fields](#transmission-line-fields-on-onelines) are often placed close to dc transmission lines on the oneline to indicate the power flow through the device.

Note that, unlike ac transmission lines, dc transmission lines cannot be equipped with circuit breakers.

Run Mode

Simulator's [animation](15-using-onelines-tools-and-options.md#oneline-animation) feature can be used to indicate the magnitude of the flow on the dc transmission line, either in MW or in terms of the line's percentage loading. You can customize the line flow animation using the *Animated Flows Options* on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on a dc transmission line displays the line's local menu, from which you can choose to inspect the [DC Transmission Line Dialog.](06-object-properties-edit-mode-part3.md#dc-transmission-line-options)

Edit Mode

To add a new dc transmission line to the case, first select **Network \> DC Transmission Line** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the bus you desire to be the rectifier bus for the line and click the left mouse button. Add more segments to the line by moving the cursor and clicking with the left mouse button. To complete the new line, place the cursor on the second bus for the line, which will serve as the inverter bus, and double-click the left mouse button. This calls up the [DC Transmission Line Dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options). If you successfully selected the rectifier and inverter buses, their numbers will be automatically filled in for you when the dialog opens.

The DC Transmission Line Record Dialog has four separate pages: Line Parameters, Rectifier Parameters, Inverter Parameters, and Actual Flows. The separate pages can be accessed using the tabs shown at the top of the dialog. These pages are used to set the modeling parameters associated with the dc lines.

To modify the parameters for an existing dc transmission line, position the cursor anywhere on the line and right-click. This will provide access to the corresponding [DC Transmission Line Dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options), from which you can modify any of the dc line's parameters. Select **![Line Fill Icon](images/Line_Fill_Icon.jpg) ** **** from the **[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to change the color and/or line thickness of the dc line.

To change the shape of the line, first left-click on the line to select it. This causes handles to appear at each vertex. You can then move any vertex by clicking and holding the left mouse button down, dragging the vertex to a new location, and releasing the mouse button. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the line where you would like to add a vertex.

---

<a id="multi-section-transmission-line-display-objects"></a>

## Multi-section Transmission Line Display Objects

*Source: [`Content/MainDocumentation_HTML/Multi_section_Line_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_section_Line_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Multi-section lines are represented on the onelines using a line segment with intermediate or "dummy" bus representations. These objects are not the same as a normal transmission line. They do display animated flows in run mode, but do not have pie charts, circuit breakers, or text fields currently associated with the objects.

Run Mode

Simulator's [animation](15-using-onelines-tools-and-options.md#oneline-animation) feature can be used to indicate the magnitude of the flow on the transmission line, either in MW or in terms of the line's percentage loading. You can customize the line flow animation using the *Animated Flows Options* on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on a multi-section line displays the [Multi-section Line Information Dialog.](06-object-properties-edit-mode-part2.md#multi-section-line-information)

The Right -click option, *Convert MS-lines into background lines...* converts the MS Line display object into a background line. You can convert the background back to a MS-line by [right clicking on the background line](13-building-onelines-graphics-and-insertion.md#converting-background-lines).

Edit Mode

Unlike transmission lines and transformers, multi-section lines CANNOT be inserted in a case by adding the mult-section line graphically. Therefore, when inserting a multi-section line object, the data for the object must already exist in the case. A list of currently defined multi-section lines is found in the model explorer under **Aggregations \> MS Transmission Lines**. Right-clicking and selecting **Insert…** in the table that opens will allow you to add new multi-section line information via the [Multi-Section Line Information](06-object-properties-edit-mode-part2.md#multi-section-line-information) dialog.

To insert the multi-section line object, first select **Network \>** **MS** **Transmission Line** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the first bus for the transmission line (the "from" bus) and click the left mouse button. Add more segments to the line by moving the cursor and clicking with the left mouse button. To complete adding a new line, place the cursor on the second bus for the line (the "to" bus) and double-click with the left mouse button. Completing the multi-section line opens the [Multi-section Line Information](06-object-properties-edit-mode-part2.md#multi-section-line-information) dialog. At the bottom of this dialog are display options for the line, such as line pixel thickness, symbol size (for the series capacitor representations, if any,) anchored, and options for drawing the buses.

To change the shape of the line, first left-click on the line to select it. This causes handles to appear at each vertex. You can then move any vertex clicking and holding the left mouse button down on the vertex, dragging it to a new location, and then releasing the mouse button. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the line where you would like to add a vertex.

---

<a id="transformer-display-objects"></a>

## Transformer Display Objects

*Source: [`Content/MainDocumentation_HTML/Transformer_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transformers are represented as transmission lines with two opposing coils drawn on one of the segments. The transformer's line thickness, color, and symbol segment can be customized using the [Branch Options](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) Edit mode dialog. Optionally, [circuit breakers](#circuit-breakers-on-onelines) and [pie charts](#line-flow-pie-charts-on-onelines) can be placed on the transformer. Clicking on the circuit breakers changes the status of the transformer.

[Line fields](#transmission-line-fields-on-onelines) are often placed close to transformers on the oneline to indicate the power flow through the device. [Transformer fields](#transformer-fields-on-onelines) are often placed close to transformers on the oneline to indicate and control their tap positions. See [Transformer Modeling](06-object-properties-edit-mode-part2.md#transformer-control) for details on modeling either LTC or phase shifting transformers.

Run Mode

Simulator's [animation](15-using-onelines-tools-and-options.md#oneline-animation) feature can be used to indicate the magnitude of the flow through the transmission line, either in MW or in terms of the transformer's percentage loading. You can customize the line flow animation using the **Animated Flows Options** on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on a transformer displays the line's local menu, from which you can choose to inspect the [Branch Information Dialog.](07-object-properties-run-mode-and-general-part1.md#linetransformer-information)

Edit Mode

New transformers are inserted in much the same way as transmission lines. To add a new transformer to the case, first select **Network \> Transformer** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the first bus for the transformer (the *from bus*) and click the left mouse button. Add more segments to the transformer by moving the cursor and clicking with the left mouse button. To complete the new transformer, place the cursor on the transformer's other terminal (the *to bus*) and double-click with the left mouse button. This calls up the [Branch Options dialog.](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) The *from* and *to* bus numbers for the transformer should have been set automatically. If there is just one transformer between the buses, the circuit number should be "1." For multiple transformers between buses, you must give each a unique circuit number. Enter the thickness of the lines \[in pixels\] used to display the transformer, the number of the line segment in which you would like the transformer symbol drawn, and the size of the transformer symbol.

Enter the per unit (100 MVA base by default) resistance, reactance and charging susceptance for the transformer, and an MVA rating. Enter the off-nominal tap ratio and the phase shift angle in degrees. (For a transformer without tap or phase control, the off-nominal tap should be 1.0 and the phase shift angle should be 0 degrees.)

Select the appropriate Automatic Control Option. If the transformer does not have tap control, select *No Automatic Control* (this is the default). Select *AVR* (Automatic Voltage Regulation) if the transformer changes its tap ratio to control the voltage at user specified regulation bus. Select *Reactive Power Control* if the transformer changes its tap ratio to control the reactive power through the transformer. Finally, select *Phase Shift Control* if the transformer changes its phase shift to control the MW flow through the transformer. If you need any of the last three options, select the Automatic Control Options button to set the parameters associated with the automatic control. When the transformer is in automatic control an automatic control symbol is drawn when drawing transformer symbol using circles.

For AVR control, enter the number of the bus whose voltage is to be controlled, the allowable range for the controlled voltage (in per unit), the minimum and maximum tap ratios (typical values are 0.9 and 1.1), and the step size for the discrete changes in the tap ratio (typical value is 0.00625).

For reactive power control, the control variable is always the reactive power measured at the *from bus* (i.e., the tapped side) of the transformer. Positive flow is assumed to be going through the transformer to the *to bus*. Enter the minimum and maximum allowable flows, the minimum and maximum tap ratios (typical values are 0.9 and 1.1), and the step size for the discrete changes in the tap ratio (typical value is 0.00625).

For phase shift control, the MW flow through the transformer is the controlled value. Enter the bus number of the terminal whose flow is controlled, the allowable range for the controlled flow (positive flow is assumed to be into the transformer at the terminal entered in the previous field), the minimum and maximum phase angles (typical values are -30° and 30°), and the step size in degrees (typical values are between 1° and 2°).

Select **OK** to save the values and return to the Transformer Options Dialog; otherwise select **Cancel**.

If you would like the transformer to be initially modeled as being on automatic control at the start of the case, select the **Automatic Control Active** checkbox.

If you do not want to add the transformer to the case, select Cancel.

To modify the parameters for an existing transformer, position the cursor anywhere on the device and right-click. This brings up the local menu from which you can choose to view the Line Information Dialog. This will open the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options). Use this dialog to adjust many of the transformer's electrical properties. The [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group provides tools to change the transformer's color and/or line thickness.

See [Transformer Modeling](06-object-properties-edit-mode-part2.md#transformer-control) for details on modeling either LTC or phase shifting transformers.

---

<a id="transformer-fields-on-onelines"></a>

## Transformer Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Transformer_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Transformer fields are used to show field values specific to transformers, such as tap position, phase angle, and more.

Run Mode

If there is a spin control integrated with the field, you can click on the spinner to change the field's value by the associated *Delta Per Mouse Click*.

Right clicking on the transformer field gives the option to display the [Transformer Field Dialog](06-object-properties-edit-mode-part3.md#transformer-field-options) or the [Line/Transformer Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information).

Edit Mode

To enter a new transformer field, select **Field \> Transformer Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, and then click on the transformer object to which you want to add the new field. This calls up the [Transformer Field Dialog.](06-object-properties-edit-mode-part3.md#transformer-field-options) Enter the *from* and *to* bus numbers associated with the device (the default values for these fields correspond to the transformer on which you clicked), and the circuit number of the device. Enter the total number of digits that the field should display, as well as the number of digits to the right of the decimal point. Finally, specify what the field should display: the off-nominal tap ratio, the off-nominal tap position, or the phase shift angle in degrees.

To modify the parameters of an existing transformer field, position the cursor anywhere on the object and right-click to bring up the [Transformer Field Dialog](06-object-properties-edit-mode-part3.md#transformer-field-options). Use the tools of the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group to change various display attributes for the transformer field, including its font and background color.

---

<a id="three-winding-transformer-display-objects"></a>

## Three Winding Transformer Display Objects

*Source: [`Content/MainDocumentation_HTML/Three_Winding_Transformer_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Three_Winding_Transformer_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Three winding transformer display objects do not currently have as much functionality as other display objects. They do provide a graphical representation for identifying where three winding transformers are located in the network, but the display objects do not provide access to additional control information for the transformer. Three winding transformer display objects cannot be anchored to buses like other objects can, meaning that they will not move as other objects in the display are moved around.

A three winding transformer can be added to a oneline display while in Edit mode by selecting **Network \> Three-Winding Transformer** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This will change the mouse cursor to a cross-hair. Place the cross-hair on the oneline background at the location where the new transformer should be placed and then left-click. This will open the Three-Winding Transformer dialog.

The Three-Winding Transformer dialog contains information about the display of the three winding transformer only. Use the [Three Winding Transformer Display](05-case-information-displays-by-object-part2.md#three-winding-transformer-display) to view and change control parameters and other information about the transformer. The dialog contains the following parameters:

Primary Number, Name, and Area

Number, name, and area number of the primary winding bus.

Secondary Number, Name, and Area

Number, name, and area number of the secondary winding bus.

Tertiary Number, Name, and Area

Number, name, and area number of the tertiary winding bus.

Circuit

Circuit ID of the three winding transformer.

When creating a new three winding transformer on the display, the primary, secondary, and tertiary bus numbers and circuit ID must be provided that correspond to a three winding transformer that already exists in the power flow case data model. The creation of a new three winding transformer in the data model is not allowed by graphically inserting a transformer. The bus names and area numbers are provided for informational purposes only and do not have to be entered when creating a new display object.

Click the **Find** button next to the winding specifications to open a dialog that can be used to search for an existing three winding transformer in the data model.

An existing three winding transformer display object can be assigned to a new three winding transformer data object by changing the Primary, Secondary, Tertiary, and Circuit to match an existing three winding transformer data object.

Labels

Optionally, create a label to identify the three winding transformer that the display object represents. Assigning a label here will associate a label with three winding transformer in the data model. See the [Labels](07-object-properties-run-mode-and-general-part2.md#labels) topic for more information about labels.

This entry is an exception for this dialog. All other fields are associated with the display object only. This is the only field that is associated with the underlying data object that the display object represents.

Display Size

This is the vertical size of the object when displayed using Orientation Up or Down. This is the horizontal size of the object when displayed using Orientation Left or Right. This is in Simulator units.

Display Width

This is the vertical size of the object when displayed using Orientation Left or Right. This is the horizontal size of the object when displayed using Orientation Up or Down. This is in Simulator units.

Pixel Thickness

Thickness in pixels of the lines used to draw the object.

Anchored

This option is permanently disabled. Currently, three winding transformer objects cannot be anchored to other objects.

Orientation

Options are Right, Left, Up, and Down. The option selected determines the side of the object that the secondary and tertiary windings are on relative to the primary winding.

Tertiary Orientation

This option determines the placing of the tertiary winding relative to the secondary winding. If the **Orientation** is either Right or Left, the Tertiary Orientation options are either Up or Down. If the **Orientation** is either Up or Down, the Tertiary Orientation options are either Right or Left.

Colors

Different colors can be specified for the Primary, Secondary, and Tertiary windings. Either left-click on the color or click the **Change** button next to the appropriate winding to open a dialog that will allow color selection.

OK, Cancel, Help

Click **OK** to apply any changes and close the dialog. Click **Cancel** to close the dialog without applying any changes. Click **Help** to open this help topic.

---

<a id="series-capacitor-display-objects"></a>

## Series Capacitor Display Objects

*Source: [`Content/MainDocumentation_HTML/Series_Capacitor_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Series_Capacitor_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Series capacitors are represented as transmission lines with two opposing parallel bars drawn on one of the segments. The series capacitor’s line thickness, color and symbol segment can be customized using the [Branch Options](06-object-properties-edit-mode-part2.md#display) Edit mode dialog. If the series capacitor branch is operating, but the series capacitor status is set to **Bypassed**, a low impedance segment will be drawn around the series capacitor symbol to indicate the capacitor has been bypassed. The capacitor status of **Bypassed** or **In Service** can be toggled in run mode if the Series Capacitor Status field is displayed on the oneline diagram. When a left-click is registered on the Series Capacitor Status field when in Run Mode, the capacitor status is toggled. Note that this is not the same as the overall branch status of **Open** or **Closed**.

Optionally, [circuit breakers](#circuit-breakers-on-onelines) and [pie charts](#line-flow-pie-charts-on-onelines) can be placed on the series capacitor. Clicking the circuit breakers changes the branch status of the series capacitor.

Run Mode

Simulator's [animation](15-using-onelines-tools-and-options.md#oneline-animation) feature can be used to indicate the magnitude of the flow through the series capacitor, either in MW or in terms of the transformer's percentage loading. You can customize the line flow animation using the **Animated Flows Options** on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on a series capacitor displays the line's local menu, from which you can choose to inspect the [Branch Information Dialog.](07-object-properties-run-mode-and-general-part1.md#linetransformer-information)

Edit Mode

New series capacitors are inserted in much the same way as transmission lines. To add a new series capacitor to the case, select **Network \> Series Capacitor** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the first bus for the series capacitor (the *from bus*) and click the left mouse button. Add more segments to the series capacitor by moving the cursor and clicking with the left mouse button. To complete the new series capacitor, place the cursor on the series capacitor's other terminal (the *to bus*) and double-click with the left mouse button. This calls up the [Branch Options dialog.](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) The *from* and *to* bus numbers for the series capacitor should have been set automatically. If there is just one branch between the buses, the circuit number should be "1." For multiple branches between buses, you must give each a unique circuit number. Enter the thickness of the lines \[in pixels\] used to display the series capacitor, the number of the line segment in which you would like the series capacitor symbol drawn, and the size of the series capacitor symbol.

Enter the per unit (100 MVA base by default) resistance, reactance and charging susceptance for the series capacitor, and an MVA rating. On the Series Capacitor tab, check the box labeled **Is Series Capacitor** to indicate that the branch model is a series capacitor device.

If you do not want to add the series capacitor to the case, select Cancel. Otherwise click **OK** to add the series capacitor to the case.

To modify the parameters for an existing series capacitor, position the cursor anywhere on the device and right-click. This brings up the local menu from which you can choose to view the Line Information Dialog. This will open the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options). Use this dialog to adjust many of the series capacitor's electrical properties.

See [Series Capacitor Information](06-object-properties-edit-mode-part2.md#series-capacitor) for more details on modeling series capacitors.

---

<a id="series-capacitor-fields-on-onelines"></a>

## Series Capacitor Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Series_Capacitor_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Series_Capacitor_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Series capacitor fields are used to show field values specific to series capacitors.

Run Mode

If the Series Capacitor field for capacitor status is displayed, the capacitor status can be toggled in run mode when you left-click on the field.

Right-clicking on the series capacitor field gives the option to display the [Line Field Information Dialog](06-object-properties-edit-mode-part2.md#series-capacitor-field-options) or the [Line/Transformer Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information).

Edit Mode

To enter a new series capacitor field, select **Field \> Series Capacitor Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, and then click on or near the series capacitor object for which you want to add the new field. This calls up the [Series Capacitor Field Options dialog](06-object-properties-edit-mode-part2.md#series-capacitor-field-options). Enter the *from* and *to* bus numbers associated with the device (the default values for these fields correspond to the series capacitor on which you clicked), and the circuit number of the device. Enter the total number of digits that the field should display, as well as the number of digits to the right of the decimal point. Finally, specify what the field should display: the capacitor status or the series capacitance.

To modify the parameters of an existing series capacitor field, position the cursor anywhere on the object and right-click to bring up the [Series Capacitor Field Options dialog](06-object-properties-edit-mode-part2.md#series-capacitor-field-options).

---

<a id="switched-shunt-display-objects"></a>

## Switched Shunt Display Objects

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched shunts are either capacitors that supply reactive power to the system or reactors that absorb reactive power. Simulator represents switched shunts as a number of blocks of admittance that can be switched in a number of discrete steps or over a continuous range. Switched shunt display objects come equipped with a circuit breaker that indicates the shunt's status. If the switched shunt is closed, the circuit breaker appears as a filled red square. If the switched shunt is open, the circuit breaker appears as a green square outline. To change the status of the switched shunt, click the corresponding circuit breaker.

[Switched shunt fields](#switched-shunt-fields-on-onelines) are often placed next to switched shunts to indicate the amount of reactive power supplied by the device. For switched shunts with such a field, you can manually increase the reactive power supplied by the device (provided its control mode is discrete) by clicking on the up-arrow associated with the device's reactive power field. Likewise, you can decrease the reactive power supplied by the device by clicking on the down-arrow. To make the up/down arrows visible, set the *Delta per Mouse Click* on the [switched shunt field](#switched-shunt-fields-on-onelines) to a nonzero value.

Right-clicking on the switched shunt displays the [Switched Shunt dialog.](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) Use the Switched Shunt dialog to inspect or modify the model of the switched shunt.

You can add a new switched shunt to the case in Edit Mode. Select **Network \> Switched Shunt** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Click the bus where you would like to attach the device. The [Switched Shunt dialog](06-object-properties-edit-mode-part3.md#switched-shunt-information) will appear. The bus number is automatically determined from the bus to which you attached the capacitor. A switched shunt can also be added without connecting it to a bus, but the bus information must be entered manually. Enter the size, the thickness of the pen \[in pixels\] used to draw the device, and its orientation. The Nominal Mvar field gives the amount of reactive power the device would supply if its terminal voltage were 1.0 per unit. The Control Mode field determines whether the switched shunt has a fixed value or will vary discretely or continuously within its operating limits to maintain its terminal voltage within the voltage range specified in the Voltage Regulation field. A line will be drawn through a switched shunt display object if Control Mode is *Continuous* or *SVC*.

The amount of shunt admittance is specified in the Switched Shunt Blocks table. The columns in this field correspond to different blocks of admittance. The first row indicates the number of steps in each block, and the second row gives the amount of nominal Mvars per step. The switched shunts are always switched in the order specified in this field.

Select **OK** to add the device. If you do not want to add the switched shunt to the case, select **Cancel**.

To modify the parameters for an existing switched shunt, position the cursor on the device and right-click. This again brings up the [Switched Shunt dialog](06-object-properties-edit-mode-part3.md#switched-shunt-information). You can then change any parameter of the switched shunt. Make use of the tools in the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group to change the color and/or line thickness.

To delete an existing switched shunt, use the **Cut** or **Delete** commands in the [Clipboard](02-simulator-ribbon.md#clipboard-ribbon-group) ribbon group.

---

<a id="switched-shunt-fields-on-onelines"></a>

## Switched Shunt Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched Shunt field objects are used primarily to indicate various quantities associated with switched shunt devices. Furthermore, some switched shunt field types, which are distinguished by an integrated spin button, may be used to change switched shunt device properties.

Run Mode

For switched shunt fields with an associated spin button, clicking on the up/down arrows will change the value of the associated field.

Right clicking on a switched shunt field gives you the option to open the [Switched Shunt Field Dialog](06-object-properties-edit-mode-part3.md#switched-shunt-field-information) or the [Switched Shunt Information Dialog](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information).

Edit Mode

Simulator offers two options for adding switched shunt fields to a oneline in Edit Mode. If you need to enter only a single field, the easier approach may be to choose **Field \> Switched Shunt Field** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, and then select the switched shunt to which you want to add the field. This invokes the [Switched Shunt Field Dialog.](06-object-properties-edit-mode-part3.md#switched-shunt-field-information) Enter the bus number associated with the device (the default is the bus associated to the closest switched shunt to the field), the ID field, the total number of digits to show, and the number of digits to the right of the decimal point. Next, select the type of field to show.

The second approach for adding new switched shunt fields entails right-clicking the switched shunt and selecting *Add New Fields Around Switched Shunt* from the resulting local menu. Please see [Inserting and Placing Multiple Display Fields](11-building-onelines-network-objects.md#inserting-and-placing-multiple-display-fields) for more details.

To modify the parameters of an existing switched shunt field, position the cursor anywhere on the object and right-click. This brings up the [Switched Shunt Field Dialog](06-object-properties-edit-mode-part3.md#switched-shunt-field-information). Make use of the tools on the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group to change various display attributes of the field, including its font and background color.

---

<a id="interface-display-objects"></a>

## Interface Display Objects

*Source: [`Content/MainDocumentation_HTML/Interface_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Interface display objects are used on the onelines to visualize the flow of power through an [interface record](05-case-information-displays-by-object-part3.md#interface-display). Interface records are used to show the net real power (MW) flow on a group consisting of one or more of the following devices: 1) transmission lines and/or transformers, 2) total tie-lines between two adjacent areas, and 3) total tie-lines between two adjacent zones. Only area-area and zone-zone interface records can be displayed using interface display objects.

Interfaces, like transmission lines, are represented as multi-segment lines, except that they may be drawn between [area/zone objects](11-building-onelines-network-objects.md#area-display-objects) in addition to buses. Drawing interface display objects involves the same steps as drawing transmission lines and transformers. The line thickness and color of interface objects may be customized by selecting ![Display zoom icon](images/Display_zoom_icon.jpg) from the **[Formatting](02-simulator-ribbon.md#formatting-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.

[Interface Fields](#interface-fields-on-onelines) and [Interface Pie Charts](#interface-pie-charts-on-onelines) are often placed close to or on the interface to indicate the power flow through the device.

Run Mode

When animation is active, the flow of the arrows on the interface object may represent either the MW flow through the interface or the currently calculated power transfer distribution factor ([PTDF](20-sensitivities.md#power-transfer-distribution-factors)) pertaining to that interface. You can customize the appearance of the animated flows using the *Animated Flows Tab* of the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) available using the local menu.

Right-click on the interface to view the [Interface Dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) for the interface.

Edit Mode

The quickest method of inserting new interface objects is to use the **Auto Insert \> Interfaces** from the **[Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Please see [Automatically Inserting Interfaces](#automatically-inserting-interface-display-objects) for details.

To manually add a new interface object to the case, first select **Aggregation \> Interface** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then place the cursor on the starting location for the interface (usually an area/zone object or a bus object) and left-click. Add more segments to the interface by moving the cursor and the left-clicking at the end of the segment. To finish adding an interface, place the cursor on the terminal object for the interface and double-click. This then calls up the [Interface Dialog](07-object-properties-run-mode-and-general-part2.md#interface-information). Either select an existing interface, or define a new interface (see [Interface Dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) for details).

Interfaces can be [anchored](11-building-onelines-network-objects.md#anchored-objects) to either area/zone objects or bus objects.

To change the shape of the interface, first left-click on the object to select it. This causes handles to appear at each vertex. You can then move any vertex by dragging it with the left mouse button down. To remove a vertex, hold down the CTRL key and then click the vertex you would like to delete. To add a vertex, hold down the CTRL key and then click on the interface where you would like to add the vertex.

---

<a id="automatically-inserting-interface-display-objects"></a>

## Automatically Inserting Interface Display Objects

*Source: [`Content/MainDocumentation_HTML/automatically_inserting_interface_display_objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/automatically_inserting_interface_display_objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Insertion of Interfaces Dialog is used to automatically insert [interface objects](#interface-display-objects) on the oneline diagram between existing [area/zone display objects](11-building-onelines-network-objects.md#area-display-objects). [Interface pie chart objects](#interface-pie-charts-on-onelines) can also be inserted as part of this process. The automatic insertion of interface display objects greatly accelerates the construction of interface diagrams, which are particularly useful for animating the results of [PTDF](20-sensitivities.md#power-transfer-distribution-factors) calculations. Area-area and zone-zone interface records can be displayed using interface display objects as well as interfaces comprised only of transmission branches.

Inserting interface objects on a oneline diagram does NOT add interface objects to the load flow case. The interface definitions need to be added to the load flow case prior to automatically inserting the graphical interface objects on a oneline diagram. The quickest way to add area to area or zone to zone interface definitions in the load flow case is to [automatically insert the definitions](07-object-properties-run-mode-and-general-part2.md#automatically-inserting-interfaces-in-case) in the interface case information display.

Once you have the interface definitions defined in the case, you can automatically insert the interface objects on a diagram using the following procedure:

  - On a oneline diagram (either an already open diagram or a brand new one created by choosing **New Oneline** from the [File menu](03-cases-files-and-formats.md#file-menu)), place [area/ zone objects](11-building-onelines-network-objects.md#area-display-objects) at the desired locations if inserting area-area or zone-zone interface records. Otherwise, the terminal buses for the branch elements in the interface should be inserted at the desired locations on the oneline diagram.
  - **** Go to the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab and choose **Auto Insert \> Interfaces** on the [Quick Insert](02-simulator-ribbon.md#quick-insert-ribbon-group) ribbon group.
  - Check the **Insert Pie Charts on Interfaces** box to automatically insert interface pie chart objects when the interfaces are inserted. If this option is selected, change the **Default Size of Interface Pie Charts** to specify their size.
  - Choose the type of interfaces to insert. **Area to Area or Zone to Zone Interfaces** and **Line/Transformer Interfaces** can be inserted. Area-area and zone-zone interfaces will be drawn between the respective area and zone objects displayed on the oneline. Line/transformer interfaces will be drawn based on the average location of the terminal buses of all transmission lines comprising the interface. If inserting line/transformer interfaces, the option **Minimum Length of Line/Transformer Interfaces** can be set to prevent interfaces that are too short from being inserted.
  - Select **OK** to insert the new oneline objects. New interface objects are automatically inserted based on the selected criteria for any corresponding interface record that is not already represented.

Note that you can do this automatic insertion as often as you like. The **Number of Interfaces Not Shown** field indicates how many interfaces still need to be added to the diagram to represent all defined area-area, zone-zone, or line/transformer interfaces. It is a read-only field.

---

<a id="interface-fields-on-onelines"></a>

## Interface Fields on Onelines

*Source: [`Content/MainDocumentation_HTML/Interface_Fields_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Fields_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Interface field objects are used to show values associated with [interface records](05-case-information-displays-by-object-part3.md#interface-display).

Run Mode

Right clicking on the interface field displays the [Interface Field Dialog](07-object-properties-run-mode-and-general-part2.md#interface-field-information).

Edit Mode

To enter a new interface field, select **Field \> Interface Field** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab, and then click on the background of the oneline diagram where you want the field placed. This calls up the [Interface Field Dialog](07-object-properties-run-mode-and-general-part2.md#interface-field-information). Enter the name of the interface, the total number of digits desired in the field, and the type of field.

To modify the parameters of an existing interface field, position the cursor anywhere on the object and right-click. This again brings up the Interface Field Dialog.

---

<a id="interarea-flow-options-dialog"></a>

## InterArea Flow Options Dialog

*Source: [`Content/MainDocumentation_HTML/InterArea_Flow_Options_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/InterArea_Flow_Options_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is outdated in PowerWorld Simulator version 5 and later. See help on the [Interface Field Information Dialog](07-object-properties-run-mode-and-general-part2.md#interface-field-information) for the updated dialog.

When viewing an area diagram containing inter-area objects created using PowerWorld Simulator version 4.2 or older, this dialog allows you to set text fields displaying either the actual or scheduled MW flow on the inter-area object.

---

<a id="interface-pie-charts-on-onelines"></a>

## Interface Pie Charts on Onelines

*Source: [`Content/MainDocumentation_HTML/Interface_Pie_Charts_on_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Pie_Charts_on_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Interface pie charts are used to graphically show the percentage loading on an [interface record](05-case-information-displays-by-object-part3.md#interface-display). The amount of shaded region of the pie chart indicates how close the interface is to its limit (provided the interface has a nonzero limit). The appearance of the interface pie charts, including their color and the ability to automatically change size based upon loading level, can be customized on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

Right-clicking on the interface pie chart displays the [Interface Pie Chart Dialog](07-object-properties-run-mode-and-general-part2.md#interface-pie-chart-information). This dialog can be used to customize the size of the pie chart, or change the interface's limit.

Edit Mode

To enter a new interface pie chart, select **Pies/Gauges \> Interface Pie Chart** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then, click the left mouse on the interface object with which you want to associate the pie chart. This calls up the [Interface Pie Chart Dialog](07-object-properties-run-mode-and-general-part2.md#interface-pie-chart-information), which is used to customize the appearance of the pie chart.

---

<a id="loading-nerc-flowgates"></a>

## Loading NERC Flowgates

*Source: [`Content/MainDocumentation_HTML/loading_nerc_flowgates.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/loading_nerc_flowgates.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This command reads flowgates from an Excel file and inserts them as interface records. The format for this file should be similar to the files found at http://www.nerc.com/\~oc/dfwg.html. To access this file you must have a NERC-supplied username and password. At the time of writing we have not seen an official description of the format -- currently Simulator just mimics the format found in this file. Flowgates are used by NERC (under Policy 9) as proxies for transmission limitations and transmission service usage on the interconnected electric power network. Simulator models flowgates using the interface records. Interface records MAY include contingency elements.

The **Load NERC** **Book of** **Flowgates** **from Excel** option is available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the [Interface Records](05-case-information-displays-by-object-part3.md#interface-display) display.

---

<a id="saving-nerc-flowgates"></a>

## Saving NERC Flowgates

*Source: [`Content/MainDocumentation_HTML/saving_nerc_flowgates.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/saving_nerc_flowgates.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This command writes all the interfaces to an Excel spreadsheet using the NERC flowgate format. See the files found at http://www.nerc.com/\~oc/dfwg.html for an example of the NERC format. To access this file you must have a NERC-supplied username and password.

The **Send NERC Book of Flowgates to Excel** option is available from the **Save As** option of the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) of the [Interface Records](05-case-information-displays-by-object-part3.md#interface-display) display.

---

<a id="injection-group-display-objects"></a>

## Injection Group Display Objects

*Source: [`Content/MainDocumentation_HTML/Injection_Group_Display_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Injection_Group_Display_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Injection group display objects are used on onelines to show a summary of the total injection of an [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) from generation and load. The summary shows only the MW injection.

An injection group display object can be added to a oneline by choosing **Aggregation \> Injection Group** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. After selecting this option, place the cursor at the location on the oneline where the injection group object should be placed and left-click. This will open the Injection Group Display Options dialog with the following options available:

Name

Select the name of the injection group represented by the current display object. The drop-down will contain the names of all currently defined injection groups. New injection groups cannot be created through the injection group display object.

Style

The style dictates how the object will be drawn on the oneline. The injection group object is a simple object that is either a Rectangle or Rounded Rectangle.

Caption

This option is used to determine how the injection group will be identified on the display object. Currently, only the Name can be used as the identifier.

Width, Height

Specify the size of the object through these two options.

After an object has been created, the Injection Group Display Options dialog can be opened while in Edit mode by right-clicking on the object. If in Run mode, the [Injection Groups Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) will open when right-clicking on an injection group display object.

An injection group display object uses the same [Default Drawing Values](14-editing-onelines.md#default-drawing-values) as those specified for an area display object. To change how the object is drawn after it has been created, select the object to change and then select **Format** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. This will open the Format Multiple Objects dialog, and any attributes that can be modified will be enabled on this dialog. These format changes can only be done while in Edit mode.

---

<a id="links-to-onelines-and-auxiliary-files"></a>

## Links to Onelines and Auxiliary Files

*Source: [`Content/MainDocumentation_HTML/Links_to_Onelines_and_Auxiliary_Files.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Links_to_Onelines_and_Auxiliary_Files.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Run Mode

**Oneline Links**

Oneline links are one of the mechanisms used in Simulator to allow you to view multiple oneline diagrams on the same screen. By default, the oneline links are shown as blue rectangles surrounding a text identifier of the linked oneline diagram. Double-clicking the left mouse button anywhere within the oneline link object will display the linked oneline diagram, even if it has not already been opened.

The ability to associate multiple oneline diagrams with a single case may prove particularly helpful when dealing with large cases. If a single oneline diagram is used to display a case having many buses, the diagram may become cluttered, and it will be difficult to analyze the case in sufficient detail. The ability to associate additional onelines with the case and to call up those additional onelines using one-links can significantly enhance your view of the system.

Oneline Links can be used to open oneline diagrams saved in either the PowerWorld Display file (\*.pwd) or Display Auxiliary file (\*.axd). Instead of opening a oneline diagram with an \*.axd link, the file can optionally be applied to the open oneline that contains the link.

Oneline Links can be used to open [Bus View](08-view-case-data-tools.md#bus-view-display) and [Substation View](08-view-case-data-tools.md#substation-view-display) Display.

Note that you can also use the **Open Oneline** command from the [File menu](03-cases-files-and-formats.md#file-menu) to open any oneline diagram (\*.pwd, \*.axd) file directly. See [Opening a Oneline Diagram](03-cases-files-and-formats.md#opening-a-oneline-diagram) for further details.

**Auxiliary File Links**

Auxiliary (\*.aux) file links are one of the mechanisms used in Simulator to allow you to load auxiliary files by simply clicking on a oneline object. By default, auxiliary file links are shown as blue rectangles surrounding a text identifier of the linked auxiliary file. Double-clicking the left mouse button anywhere within the auxiliary file link object will load the associated auxiliary file.

Note that you can also use the **Load Auxiliary File** command from the [File menu](03-cases-files-and-formats.md#file-menu) to open any auxiliary file (\*.aux) directly. See [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) for further details.

Script Command Links

Script command links are similar to Auxiliary File Links in that they allow you to apply script commands, but they do not require that an auxiliary file be maintained. By default, script command links are shown as blue rectangles surrounding a text identifier of the linked auxiliary file. Clicking the left mouse button anywhere within the link object will apply the specified scripts.

To apply script commands to the oneline display instead of the case data, start the list of script commands with the keyword \<ONELINE\>. Script commands that are applied to both the oneline and the case cannot be specified in the same oneline link. If the list of script commands start with the keyword \<ONELINE\>, it is assumed that all of the script commands are applicable to the oneline.

Edit Mode

Regardless of the type of link that is being created, the procedure for creating a Oneline, Auxiliary File, or Script Command link is the same. To add a new oneline link to a oneline diagram, first select **Background \> Oneline Link** from the [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then, click the left mouse button at the location where you would like to display the new link. The Insert Oneline or Auxiliary Link dialog box will open. The following options are available:

File or Action

This will determine the type of link that is being created. This field must be a Oneline File name, Auxiliary File (AUX or AXD) name, or string of Script Command(s).

**Oneline Links**

Specify a oneline diagram in the PowerWorld Display format (\*.pwd) or Display Auxiliary format (\*.axd). The **Browse** button can also be used to open a dialog that will allow searching for the file. Note that you can enter simply the name of the oneline file in this location or the complete directory path and name. Simulator will look in the same directory as the case file by default. However, you can also specify additional directory locations to search for oneline diagrams by opening the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) (via **Oneline Display Option** from the **Oneline Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab, or from the **[Active](02-simulator-ribbon.md#active-ribbon-group)** ribbon group on the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab), switching to **Display Options** on the left, and using the **Edit Oneline Browsing Path** option to add additional search locations for oneline diagrams.

If using a Display Auxiliary format (\*.axd) file, the browsing path will not be used to find the file. The file must exist in the current directory or the full directory path of the file must be specified.

**Auxiliary File Links**

Specify an auxiliary file with the \*.aux extension. The **Browse** button can be used to open a dialog that will allow searching for the file. If you enter the only the name of the auxiliary file without a directory path, Simulator will look in the same directory as the case file.

**Script Command Links**

Specify a list of script commands separated by semi-colons.

To apply the script commands to the oneline, start the list of commands with the keyword \<ONELINE\>. All script commands will then be applied to the oneline. Script commands that are applied to both the oneline and the case cannot be specified in the same oneline link.

**Bus View and Substation View Display Links**

In the File or Action box write BUSVIEW or SUBVIEW and then Number, or Name\_KV, or Label.

Saved View

This option will only be available if the File or Action is specified to be a oneline display file with the \*.pwd extension. This allows the specified view to be applied when the oneline is opened via the link.

Link Caption Text

This is the text that will appear on the oneline indicating the link.

Rotation Angle

Angle at which the link text will be drawn on the oneline.

Load AXD into open oneline

This option is only applied if the File or Action is specified to be a oneline display file with the \*.axd extension. If this is checked the axd file will be applied to the oneline that contains the link instead of opening the file as its own oneline.

**Modifying Existing Links**

To modify the parameters of an existing link, position the cursor anywhere on the object and right-click. This invokes the Insert Oneline or Auxiliary Link dialog, allowing you to change any of the parameters of the link. Select **![Display zoom icon](images/Display_zoom_icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab to modify various display attributes of the oneline link, including font size and background color.

---

<a id="document-links-on-onelines"></a>

## Document Links on Onelines

*Source: [`Content/MainDocumentation_HTML/Document_links_on_onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Document_links_on_onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Just as you can link to other oneline displays from a oneline diagram using [oneline link objects](#links-to-onelines-and-auxiliary-files), you can also link to documents and data on the world-wide web using Document Link Objects. When you click on Document Link Objects in Run Mode, your system's default browser will be launched to retrieve the linked URL address. This feature is not only for web URL's, though. Any file can be linked and its associated application will automatically open. This means that presentations, documents and spreadsheets can also be linked.

In addition to linking to objects online via a URL, it’s also possible to put in a local file name and have that open when the document link is clicked. The behavior is the same as if you were to click on the Windows Start button, then select Run.., then type in the file name.

To add a Document link to a oneline diagram, select **Background \> Document Link** from the **[Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group)** ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Then, click the left mouse on the oneline diagram at the position where you would link to insert the Document link. The Document Link Options Dialog box will appear, asking you to specify the world-wide web address to which to link as well as a clickable caption to display on the oneline diagram. Enter the requested information and press *OK* to add the Document link object to the oneline.

To modify the caption or address for a Document link object, right-click anywhere on its text. Specify its new parameters in the Document Link Options Dialog and press *OK*. You may also modify various aspects of its appearance, including the font size, by choosing **![Font Btn Icon](images/Font_Btn_Icon.jpg)** from the [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group.

Note that Document links are active only in Run Mode. Clicking on a Document link object from the Edit Mode will have no effect other than to select the object for placement, formatting, etc.
