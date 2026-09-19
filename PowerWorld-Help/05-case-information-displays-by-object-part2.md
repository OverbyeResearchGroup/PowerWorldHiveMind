---
title: "Case Information Displays by Object Type (Part 2 of 3)"
part: "Viewing Case Data"
chapter_file: "05-case-information-displays-by-object-part2.md"
topics: 17
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Case Information Displays by Object Type (Part 2 of 3)

The per-object case information displays: buses, generators, loads, lines, transformers, shunts, interfaces, ownership and more.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (17)**

- [Generator Cubic Cost Display](#generator-cubic-cost-display)
- [Generator Piecewise Linear Cost Display](#generator-piecewise-linear-cost-display)
- [Load Display](#load-display)
- [Load Benefit Models Display](#load-benefit-models-display)
- [Line and Transformer Display](#line-and-transformer-display)
- [Merge Line Terminals](#merge-line-terminals)
- [Long Line Voltage Profile](#long-line-voltage-profile)
- [Open Ended Voltage Fields](#open-ended-voltage-fields)
- [Update Allow Open or Close Breakers](#update-allow-open-or-close-breakers)
- [Multi-Section Lines Display](#multi-section-lines-display)
- [Transformer Display](#transformer-display)
- [Three Winding Transformer Display](#three-winding-transformer-display)
- [Line Shunts Display](#line-shunts-display)
- [DC Lines Display](#dc-lines-display)
- [Multi-Terminal DC Record Display](#multi-terminal-dc-record-display)
- [D-FACTS Devices](#d-facts-devices)
- [D-FACTS Display](#d-facts-display)

---

<a id="generator-cubic-cost-display"></a>

## Generator Cubic Cost Display

*Source: [`Content/MainDocumentation_HTML/Generator_Cubic_Cost_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Cubic_Cost_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Cubic Cost Display presents detailed cost information for each generator in the case set to use a cubic cost model. The Generator Cubic Cost Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) of its associated generators. The [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) tools are available for finding more information on the generator’s terminal bus. You can also sort the generator records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Generator Cubic Cost Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, you can use the local menu’s *Insert* and *Delete* options when the application is in [Edit Mode](01-getting-started.md#edit-mode-introduction) to insert a new generator into the case or to delete an existing generator.

To show the generator cubic cost display, select **Network \> Generators \> Cost Curves Cubic** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the generator records display contains the following fields:

Number, Name

Number and name of bus to which the generator is attached.

Area Name of Gen

Name of the area to which the generator belongs. The generator can belong to an area which is different than the area of which its terminal bus is a member.

ID

Alphanumeric ID used to distinguish multiple generators at the same bus; ‘1’ by default.

Status

The Open / Closed status of the generator. This is a toggleable field.

AGC

Designates whether the generator’s real power output is governed by automatic generation control. If the AGC field is set to *Yes*, the generator is on automatic generation control (AGC). When a generator is on AGC, its real power output can be varied automatically. Usually the purpose for AGC is to keep the area interchange at a desired value. You can click on this field to toggle its value (except in Viewer). Please see [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details.

Gen MW

Current real power output of the generator.

IOA, IOB, IOC, IOD

Parameters used to model the cost characteristic of the generator. Please see [Generator Cost Information](06-object-properties-edit-mode-part1.md#generator-cost-description) for details. Please note that these values can be saved/loaded using the [Generator Cost Data](03-cases-files-and-formats.md#auxiliary-file-format-aux) auxiliary file.

Fuel Cost

The fuel cost of the type of fuel for the generator.

Variable O\&M

Operations and Maintenance costs for the generator.

Fuel Type

An informational field that can be set to the type of fuel the generator uses.

Unit Type

An informational field that can be set to reflect the type of unit the generator is, such as combined cycle, steam, hydro, etc.

Cost Shift $/MWh, Cost Multiplier

The cost shift and cost multiplier allow you to easily apply a shift to the cost function for the purpose of assessing how variations in bids impact profit. The cost function is affected based on the following equation:

(Original Cost Function + Cost Shift) \* Cost Multiplier

Cost $/Hr

Operating cost for the generator in $/hr.

IC

Incremental cost to produce an additional MWh. This can be expressed as dC(Pgi)/dPgi, where C denotes the generator’s cost of operation in $/hr and Pgi expresses the current MW output of the unit. In a lossless system, the incremental dispatch is equal to the generator’s lambda value.

LossSens

Area loss sensitivity - This field is **only calculated when the generator’s area is on economic dispatch control.** This field specifies the incremental change in area losses if this generator were to produce one more MW, **with the excess generation absorbed by the system slack.** This may be expressed as ¶Ploss/¶Pgi. The loss sensitivity is used in calculating the generator’s lambda value for the economic dispatch activity.

Generator MW Marg. Cost

The marginal cost of the generator supplying an additional MW of power to the system.

---

<a id="generator-piecewise-linear-cost-display"></a>

## Generator Piecewise Linear Cost Display

*Source: [`Content/MainDocumentation_HTML/Generator_Piecewise_Linear_Cost_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Piecewise_Linear_Cost_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Piecewise Linear Cost Display presents detailed cost information for each generator in the case set to use a piecewise linear cost model. The Generator Piecewise Linear Cost Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) of its associated generators. The [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) tools are available for finding more information on the generator’s terminal bus. You can also sort the generator records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Generator Piecewise Linear Cost Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, you can use the local menu’s *Insert* and *Delete* options when the application is in [Edit Mode](01-getting-started.md#edit-mode-introduction) to insert a new generator into the case or to delete an existing generator.

To show the generator piecewise linear cost display, select **Network \> Generators \> Cost Curves Linear** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the generator records display contains the following fields:

Number, Name

Number and name of bus to which the generator is attached.

Area Name of Gen

Name of the area to which the generator belongs. The generator can belong to an area which is different than the area of which its terminal bus is a member.

ID

Alphanumeric ID used to distinguish multiple generators at the same bus; ‘1’ by default.

Status

The Open / Closed status of the generator. This is a toggleable field.

AGC

Designates whether the generator’s real power output is governed by automatic generation control. If the AGC field is set to *Yes*, the generator is on automatic generation control (AGC). When a generator is on AGC, its real power output can be varied automatically. Usually the purpose for AGC is to keep the area interchange at a desired value. You can click on this field to toggle its value (except in Viewer). Please see [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details.

Gen MW

Current real power output of the generator.

Min MW

Minimum MW output of the generator.

Max MW

Maximum MW output of the generator.

Fuel Cost

The fuel cost of the type of fuel for the generator.

Fuel Type

An informational field that can be set to the type of fuel the generator uses.

Unit Type

An informational field that can be set to reflect the type of unit the generator is, such as combined cycle, steam, hydro, etc.

Cost Shift $/MWh, Cost Multiplier

The cost shift and cost multiplier allow you to easily apply a shift to the cost function for the purpose of assessing how variations in bids impact profit. The cost function is affected based on the following equation:

(Original Cost Function + Cost Shift) \* Cost Multiplier

Fixed Cost

The fixed operating cost of the generator.

MWh Break x, MWh Price x

The remainder of the display is populated with MWh Break and MWh Price pairs. These pairs define the break points of the piecewise linear curve. The MWh Break value is a MW output value of the generator. The MWh Price value is the corresponding marginal cost of producing an additional MW of power at that MW output level. Therefore entering the break points of the piecewise linear curve in this manner defines the slopes of the next section of the curve, starting at the current MW Break point and up to but not including the next defined break point. The last MWh Break and MWh Price pair defined will define the marginal price of the unit from that break point location to the maximum output of the generator.

An example is as follows:  

|  MW | $/MWh |                                                 |
| --: | ----: | :---------------------------------------------- |
|   0 |    50 | (row could be omitted)                          |
| 100 |    50 | (this value is used if previous row is omitted) |
| 200 |    80 |                                                 |
| 250 |   300 |                                                 |
| 300 |   400 |                                                 |

![gen cost curve](images/gen-cost-curve.svg)

---

<a id="load-display"></a>

## Load Display

*Source: [`Content/MainDocumentation_HTML/Load_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Load Display presents data describing each load in the case. The Load Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#load-information) of its associated loads. The toolbar also affords the opportunity to insert new loads into the model or to delete existing ones. Moreover, it enables you to invoke the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) for the load’s terminal bus. You can also sort the load information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Load Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the load display, select **Network \> Loads** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The load display contains the following fields by default:

Number, Name

Number and name of bus to which the load is attached.

ID

Two-character ID used to distinguish multiple loads at the same bus; ‘1’ by default.

Status

Either Closed if the load is connect to its bus, or Open if it is not. You can click on this field to toggle its value. If the load is open, the entire load record is dimmed.

MW, Mvar, MVA

Total real, reactive, and complex power for the load. Loads may be voltage dependent. The total load is the sum of the constant power, constant current, and constant impedance components. See [Load Information](07-object-properties-run-mode-and-general-part1.md#load-information) and [Load Modeling](06-object-properties-edit-mode-part1.md#load-modeling) for more information.

S MW, S MVAR, I MW, I MVR, Z MW, Z MVR

These six fields describe the composition of the load at the bus assuming 1 pu bus voltage. The SMW and SMVAR fields indicate the constant power portion of the load, the component that does not vary with bus voltage magnitude. The IMW and IMVR fields express the constant current part of the load, which varies in proportion to the bus voltage magnitude. Finally, ZMW and ZMVR indicate the constant impedance portion of the load, which varies with the square of the voltage. The sum of the SMW, IMW, and ZMW fields yields the base MW load at the bus (assuming 1 pu voltage), and the sum of the SMVR, IMVR, and ZMVR fields provides the base MVR load at the bus (assuming 1 pu voltage). Please see [Load Modeling](06-object-properties-edit-mode-part1.md#load-modeling) for more details on how bus load is modeled.

DistMW, DistMvar, DistStatus

Added in Version 19 Distributed Generation MW and Mvar values may be specified with each load record. These values are only used when the Distributed Generation status is set to Closed. When Closed then this represent the distributed generation MW and Mvar represented inside this load. When this is in use, then the net MW and Mvar seen by the power flow solution algorithm will be equal to the Base Load Values minus the Distributed generation. Please see [Load Modeling](06-object-properties-edit-mode-part1.md#load-modeling) for more details on how bus load is modeled.

---

<a id="load-benefit-models-display"></a>

## Load Benefit Models Display

*Source: [`Content/MainDocumentation_HTML/Load_Benefit_Models_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Benefit_Models_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Load Benefit Models Display presents detailed cost information for each load in the case set to use a piecewise linear benefit model. The Load Benefit Models Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) of its associated loads. The [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) tools are available for finding more information on the load’s terminal bus. You can also sort the load records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Load Benefit Models Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, you can use the local menu’s *Insert* and *Delete* options when the application is in [Edit Mode](01-getting-started.md#edit-mode-introduction) to insert a new load into the case or to delete an existing load.

To show the generator piecewise linear cost display, select **Network \> Loads \> Benefit Curves Linear** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the generator records display contains the following fields:

Number, Name

Number and name of bus to which the load is attached.

Area Name of Gen

Name of the area to which the load belongs. The load can belong to an area which is different than the area of which its terminal bus is a member.

ID

Alphanumeric ID used to distinguish multiple generators at the same bus; ‘1’ by default.

Status

The Open / Closed status of the load. This is a toggleable field.

AGC

Designates whether the generator’s real power output is governed by automatic generation control, since effectively dispatching a load can be viewed as dispatching negative generation. If the AGC field is set to *Yes*, the load is on automatic generation control (AGC). When a load is on AGC, its real power output can be varied automatically. Usually the purpose for AGC is to keep the area interchange at a desired value. You can click on this field to toggle its value (except in Viewer). Please see [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details.

Gen MW

Current real power demand of the load.

Min MW

Minimum MW demand of the load.

Max MW

Maximum MW demand of the load.

Fixed Benefit

The fixed benefit of the load.

Benefit Model

The type of model this load is currently using. Can be either Piecewise Linear or None.

MWh Break x, MWh Price x

The remainder of the display is populated with MWh Break and MWh Price pairs. These pairs define the break points of the piecewise linear curve. The MWh Break value is a MW demand value of the load. The MWh Price value is the corresponding marginal benefit of extracting an additional MW of load at that MW output level. Therefore entering the break points of the piecewise linear curve in this manner defines the slopes of the next section of the curve, starting at the current MW Break point and up to but not including the next defined break point. The last MWh Break and MWh Price pair defined will define the marginal benefit of the load from that break point location to the maximum demand of the load.

A requirement of the piecewise linear benefit curve is that it must be concave, meaning the next MWh Price must be lower than the previous MWh Price. In other words, as more load is supplied, the less the benefit it is providing. This is how a load can be dispatched along with generation, according to marginal costs (and marginal benefits.)

These fields will be disabled unless the Cost Model type is set to Piecewise Linear.

---

<a id="line-and-transformer-display"></a>

## Line and Transformer Display

*Source: [`Content/MainDocumentation_HTML/Line_and_Transformer_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_and_Transformer_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line/Transformer Display presents data describing each transmission line and transformer in the case. The Line/Transformer Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) of its associated branches. The local menu also affords the opportunity to insert new lines or transformers into the model or to delete existing ones. Moreover, it enables you to invoke the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) for each branch’s terminal buses. You can also sort the line and transformer information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Line/Transformer Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the line/transformer display, select **Network \> Branches Input** or **Network \> Branches State** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The contents of the display depends upon the application’s operating mode.

The line/transformer display shows the following fields by default:

From Bus Number and Name

*From Bus* number and name. For transformers, the *from* *bus* is the tapped side. Right-clicking on either of these fields brings up the display’s local menu from which you may select [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to obtain more information about the *from bus*.

To Bus Number and Name

*To Bus* number and name. Right-clicking on either of these fields brings up the display’s local menu from which you may select [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to obtain more information about the *to bus*.

Circuit

Two-character identifier used to distinguish between multiple lines joining the same two buses. Default is ‘1’.

Status

The service status of the branch. This field is toggleable.

Branch Device Type

Identifier for the type of branch. Options are: Line, Series Cap, Breaker, Load Break Disconnect, Disconnector, ZBR, Fuse, and Ground Disconnect. The type of branch can be changed through this field except that a line cannot be changed from or to a Transformer. To make that change, use the [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) in Edit mode. The type of branch becomes very important when using [Integrated Topology Processing](35-integrated-topology-processing.md#topology-processing-overview). Breakers and Load Break Disconnects are treated as special switching devices which can be controlled automatically through special actions, such as "Open with Breakers" and "Close with Breakers".  

Xfrmr

Yes or no field signifying if the branch is a transformer or transmission line. This field cannot be changed.

MW From, Mvar From, MVA From (State display default)

Real, reactive, and complex power flowing into the line at the *from bus*.

In versions of Simulator prior to version 14, these values were always calculated based on the present voltage at a bus and other branch parameters each time they were displayed. This means that a user could change the bus voltage, or impedance, and see a corresponding change in the line flow values. These values are no longer calculated each time that they are displayed. They are updated following a power flow solution, loading in a case, following an update to the system due to OPF control changes, and after creating an equivalent. The exception to this is that when loading in a PowerWorld Binary (\*.pwb) file and the flows are stored in the file, the stored flows will be retained instead of updating them based on the present system state. The MW and Mvar values can be set to user-specified values using an auxiliary file or pasting from Excel. This will allow the contouring of flows based on some external source.

Four additional fields have been added that will update each time they are displayed. This means that they will be updated following a voltage change for a bus or other relevant parameter (i.e. impedance) change for a branch. These fields take on the functionality of the flow fields prior to version 14 and are calculated each time that they are displayed. These fields are MW From (Calculated), MW To (Calculated), Mvar From (Calculated), and Mvar To (Calculated). These fields cannot be changed by the user.

Lim MVA, % of MVA Limit (Max) (State display default)

The current MVA limit of the branch, and the amount of the actual flow as a percentage of the MVA limit.

MW Loss, Mvar Loss (State display default)

Real and reactive power losses on the transmission line or transformer. Since reactive power losses include the effect of line charging, the reactive power losses may be negative.

R, X, B (Input display default)

Indicates the branch’s resistance, reactance, line charging susceptance in per unit on the system base.

Lim A MVA, Lim B MVA, Lim C MVA (Input display default)

Identifies the first three limit settings. Five additional limits can be set, for which the columns can be added using the Display/Column options from the local popup menu. All limits are expressed in MVA.

See [Transformer Display](#transformer-display) for viewing transformer specific fields.

---

<a id="merge-line-terminals"></a>

## Merge Line Terminals

*Source: [`Content/MainDocumentation_HTML/Merge Line Terminals.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Merge Line Terminals.htm)*

A transmission line can be removed from a load flow case without losing the electrical connectivity of the line's two terminal buses by merging the line terminals into a single bus. The command to merge line terminals can be performed in two ways, and can only be invoked when Simulator is in Edit mode.

First, a MergeLineTerminals script command can be invoked in Script mode or from an auxiliary file. The only parameter of the script command is a filter parameter, which must be populated with either the name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) (with the name in quotation marks) or with the text SELECTED (no quotation marks.) If an advanced filter is given, Simulator will find all transmission lines that meet the advanced filter definition, and will individually merge the line terminals of each line one at a time. Simulator will retain the From bus information as the new merged bus information for each line, with one exception. If a line was removed by merging its terminals that was the first or last segment of a [multi-section line](06-object-properties-edit-mode-part2.md#multi-section-line-information), the multi-section line terminal bus information will always be retained as the new merged bus.

The second way a line or lines can be chosen to have their line terminal buses merged is to select a set of lines in the branches table of the [model explorer](04-model-explorer-and-case-information-part1.md#model-explorer), and to then right-click in the table and bring up the popup menu. The option to Merge Terminals is located under the Branch Records submenu.

---

<a id="long-line-voltage-profile"></a>

## Long Line Voltage Profile

*Source: [`Content/MainDocumentation_HTML/LongLineVoltageProfile.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LongLineVoltageProfile.htm)*

Normally when using a power flow solution tool, you only look at the voltages at the terminal buses of transmission lines. However, for transmission lines which have large shunt charging susceptance (B) terms, the voltages at intermediate points of the transmission line can become much higher (or even lower) than the terminal bus values. To see these voltages directly, Simulator provides a tool for showing the Long Line Voltage Profile of a transmission line (or multi-section line).

<table>
<tbody>
<tr class="odd">
<td><p>You may show the voltage profile along the length of a transmission line in two ways. First on any oneline diagram (including the Bus View), you may right-click on a transmission line and choose <strong>Show Long Line Voltage Profile</strong>.</p>
<p> </p>
<p>Second on the Records menu of any case information display showing transmission branches, the will be an option to <strong>Show Long Line Voltage Profile</strong>. If you select multiple transmission lines, then the dialog will show the voltage profile on each transmission line.</p>
<p> </p>
<p>After you have chosen to show the voltage profile, a dialog will appear showing a graph of the voltage profile for each line selected. There will be a legend with check boxes that allow you to hide or show particular curves. The horizontal axis will represent the percent length of the transmission line. The vertical axis will represent the per unit voltage at each particular point along the transmission line. A per unit voltage is calculated at 101 points along the transmission line starting at 0%, 1%, ... up to 100% of the length of the transmission line. The voltage shown at 0% represents the voltage at the FROM bus of the transmission line. The voltage shown at 100% represents the voltage at the TO bus of the transmission line. This is shown in the figure below.</p>
<p> </p>
<p>When showing show the voltage profile across a multi-section line, each line section is represented separately on the plot and is shown in one of the "100 ranges" on the x-axis. For instance the third line section will appear between 200% and 300%. Also series caps and transformers are shown as dotted lines on these plots. This is shown in the second figure below.</p></td>
<td><img src="images/LongLineVoltageProfileRecordsMenu.gif" alt="LongLineVoltageProfileRecordsMenu" />
<p> </p>
<p><img src="images/LongLineVoltageProfileOneline.gif" alt="LongLineVoltageProfileOneline" /></p>
<p> </p></td>
</tr>
</tbody>
</table>

![LongLineVoltageProfile](images/LongLineVoltageProfile.gif)

![LongLineVoltageProfileMSLine](images/LongLineVoltageProfileMSLine.gif)

To get exact details of what the voltage profile can be shown by clicking on the **Show Profile Details** button. This will display a dialog as shown next.

![LongLineVoltageProfileSeriesOptions](images/LongLineVoltageProfileSeriesOptions.gif)

Of particular interest on the dialog that appears is the ability to export this data to Excel or text. This can be done by going to Export and then choosing the Data tab as shown next. Clicking on the **Save** button will then save the data to a CSV file.

![LongLineVoltageProfileExportOptions](images/LongLineVoltageProfileExportOptions.gif)

You may also play with this dialog to see all the possibilities for customizing your plots as well as printing them.

---

<a id="open-ended-voltage-fields"></a>

## Open Ended Voltage Fields

*Source: [`Content/MainDocumentation_HTML/Line_OpenEndedVoltages.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_OpenEndedVoltages.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 18, build on July. 30, 2015

Open Ended Voltage Fields are available for all AC branches (both lines and transformers). These values are not effected by the present system voltages and flows at all, but instead are calculated from the impedance properties of the AC branch. Using the assumption that voltages at the terminals of the branch are 1.0 per unit, these fields show the following.

  - The per unit voltage magnitude at the open ended side of the line
  - The charging Amps at the non-open end sided of the line (the end still closed)

There end up being 4 quantities because the line can be open ended at either the FROM or TO side. This can be a useful quantity for screening how much current will still need to be broken after one end of a line is open. The four fields are then available.

|                                                |                                                                                                                                                                |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Field                                          | Description                                                                                                                                                    |
| Open Ended\\At From Charging Amps at To        | When the branch is open at the FROM bus, this is the charging amps seen at the TO end of the branch assuming the TO bus is operating at 1.0 per unit voltage   |
| Open Ended\\at From Per Unit Magnitude at From | When the branch is open at the FROM bus, this is the per unit voltage at the FROM bus assuming the TO bus is operating at 1.0 per unit voltage                 |
| Open Ended\\At To Charging Amps at From        | When the branch is open at the TO bus, this is the charging amps seen at the FROM end of the branch assuming the FROM bus is operating at 1.0 per unit voltage |
| Open Ended\\at To Per Unit Magnitude at To     | When the branch is open at the TO bus, this is the per unit voltage at the TO bus assuming the FROM bus is operating at 1.0 per unit voltage                   |

---

<a id="update-allow-open-or-close-breakers"></a>

## Update Allow Open or Close Breakers

*Source: [`Content/MainDocumentation_HTML/Update_Allow_Open_Or_Close_Breakers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Update_Allow_Open_Or_Close_Breakers.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in version 20

This functionality can be accessed from several places within the software. These include:

  - [RAS + CTG Case Info](02-simulator-ribbon.md#run-mode-ribbon-group) dropdown found on the Tools ribbon tab in the Run Mode ribbon group
  - [Branch case information display](#line-and-transformer-display) on the local menu when the selected field is **Allow Open or Close Breakers**
  - [Integrated Topology Processing Dialog](35-integrated-topology-processing.md#integrated-topology-processing-dialog) found on the Add Ons ribbon tab
  - Automatically done when loading a case in the [Areva HDBExport format](03-cases-files-and-formats.md#case-formats)

When this process is run, the **Allow Open or Close Breakers** field for every branch will be updated based on the present system. By default this field will be set to *YES*. This field only affects branches with a **Branch Device Type** that indicates that it can be automatically switched when identified as part of a search using [open with breakers](35-integrated-topology-processing.md#open-with-breakers) or [close with breakers](24-contingency-element-dialog.md#contingency-element-close-breakers) algorithms. When this field is set to *NO*, a switching device will not be allowed to automatically switch even if it meets all of the other criteria required for either the open with breakers or close with breakers algorithms.

The process of updating the **Allow Open or Close Breakers** field identifies switching devices that are not appropriate for automatically being switched, and the field is set to *NO* for these switching devices. The user can also manually update the **Allow Open or Close Breakers** field if necessary. This process will reset this field for all branches. If there are fields that have been manually set that need to be retained as *NO*, care should be taken prior to running this process to retain these values so that they can be set correctly after the process completes.

This process will identify any branches with **Branch Device Type** equal to *Breaker*, *Load Break Disconnect*, or *Disconnect* that are in parallel to a *Series Capacitor* or a series of branches including only *Series Capacitors*, *Disconnects*, *Fuses*, and *ZBRs*. If this topology is found, the branch that is in parallel will be marked with **Allow Open or Close Breakers** = *NO* as will the series branches that it is parallel with.

The following are some examples of switching devices that will have their **Allow Open or Close Breakers** field set to *NO* during this update process. This process ignores the status of the switching devices.

![UpdateAllowOpenOrCloseBreakers](images/UpdateAllowOpenOrCloseBreakers.GIF)

---

<a id="multi-section-lines-display"></a>

## Multi-Section Lines Display

*Source: [`Content/MainDocumentation_HTML/multi_section_lines_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/multi_section_lines_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To show this display select **Aggregations \> Multi-Section Lines** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The Multi-Section Line Display lists the multi-section lines that exist in the case. The Multi-Section Line Display is used to functionally group a number of transmission lines together. They are usually used to model very long transmission lines that require the use of multiple individual transmission line information to be modeled accurately. Simulator then treats each multi-section line as a single device with regard to line status. That is, changing the status of one line in the record changes the status of the other lines in the record as well.

Each multi-section line record consists of the "from" bus, one or more "dummy" buses and the "to" bus. Each dummy bus must have only two lines connected to it, each of which are members of the multi-section line record. See [Multi-Section Line Information](06-object-properties-edit-mode-part2.md#multi-section-line-information) for details.

The Multi-Section Line Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](06-object-properties-edit-mode-part2.md#multi-section-line-information) of its multi-section line information. The local menu also affords the opportunity to insert new multi-section lines into the model or to delete existing ones when the application operates in the Edit Mode. Moreover, it enables you to invoke the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) for the line’s terminal buses. You can also sort the multi-section line information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Multi-Section Line Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

While in Edit mode, the local menu allows three options that are specific to multi-section lines. The options are found under the **Multi-Section Line records** menu item.

Show Long Line Voltage Profile

For more information on this see the [Long Line Voltage Profile](#long-line-voltage-profile) topic.

Merge Sections

Select this option to eliminate the selected multi-section line record. If possible, the individual sections will be merged into a single line record between the from and to bus and the multi-section line record will be removed. If a multi-section line contains series capacitors or transformers, the multi-section line record will be retained.

Renumber Dummy Buses

This option allows renumbering/renaming the dummy buses that are part of a multi-section line by loading a file that has the new designations. The file containing the renumbering should be a text file in the following format:

frombus, tobus, circuit // this identifies the multi-section line

// frombus and tobus can either be bus numbers or name\_nomkV combinations

dummybusnumber1, dummybusname1

dummybusnumber2, dummybusname2

frombus, tobus, circuit // this identifies another multi-section line

dummybusnumber1, dummybusname1

dummybusnumber2, dummybusname2

dummybusnumber3, dummybusname3

The file can either be space or comma delimited. A double slash can be used for a comment. A line with three entries is assumed to be a multi-section line and any two entry lines following that are assumed to be the dummy bus identifiers belonging to that multi-section line. Dummy buses are read for a multi-section line until another three entry line is found, meaning that a new multi-section line has been specified. Dummy buses are identified starting at the from bus of the multi-section line going to the to bus and that is the way that they should be entered in the file. If a multi-section line matching the given identifiers cannot be found, all dummy buses after that multi-section line record are ignored until a new multi-section line specification is found. If an incorrect number of dummy buses is entered for a multi-section line, none of the dummy buses will be updated. If the a dummy bus number is specified that matches an existing bus that is not another dummy bus, no changes will be made for that dummy bus. If a dummy bus number is specified that matches an existing bus that is another dummy bus, the other dummy bus will be assigned to a new bus number and the current dummy bus will be assigned to the number specified in the file.

Dummy buses can also be renumbered using the BUSRENUMBER SUBDATA section for a multi-section line in an aux file. The format of the SUBDATA section is the same as the file format given above for renumbering the individual bus numbers and the same rules apply. The benefit is that a separate text file does not need to be maintained with the renumbering. Dummy bus renumbering can only be done while in Edit mode. An aux file with the BUSRENUMBER SUBDATA section can be saved based on the existing dummy bus numbers using the SaveData [script command](03-cases-files-and-formats.md#auxiliary-file-format-aux) or an [Aux Export Format Description](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system) and specifying the SUBDATA section. Example SUBDATA sections for dummy bus renumbering are shown below:

DATA (MULTISECTIONLINE, \[BusNum, BusNum:1, LineCircuit\])

{

1 2 "1"

\<SUBDATA BUSRENUMBER\>

3 "BUS 3"

4 "BUS 4"

5 "BUS 5"

\</SUBDATA\>

22 33 "1"

\<SUBDATA BUSRENUMBER\>

14 "BUS 14"

15 "BUS 15"

\</SUBDATA\>

}

NOTE: When using the tool to renumber multi-section line dummy buses, either through the GUI or script, a new bus that does not exist no longer needs to have a bus name specified. By default the bus name will be the same as the bus number.

The display contains the following fields by default:

NumberFrom, NameFrom

Number and name of the multi-section lines *from bus*. Right-clicking on one of these fields invokes the display’s local menu from which you can select either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to find more information about the *from bus*.

NumberTo, NameTo

Number and name of the multi-section lines *to bus*. Right-clicking on one of these fields invokes the display’s local menu from which you can select either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to find more information about the *to bus*.

Circuit

Two-character circuit identifier for the multi-section line.

Sections

Number of individual lines within the multi-section line record.

Allow Mixed Status

This value defaults to NO and means that all branches in the multi-section line must have the same status. Setting this value to YES essentially means that the multi-section line is disabled so that opening/closing a branch in the multi-section line will no longer automatically open or close the other lines in the record.

Status

Current status of the record. Note, the status is *Closed* only if **all** the lines in the record are closed, and is *Open* only if **all** the lines in the record are open. Otherwise the status is *Mixed*.

---

<a id="transformer-display"></a>

## Transformer Display

*Source: [`Content/MainDocumentation_HTML/Transformer_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transformer Display identifies all transformers in the case. The data presented in the Transformer Display supplements the data presented in the [Line/Transformer Display](#line-and-transformer-display) by presenting transformer-specific information. Consult the Line/Transformer Display for the transformer flows.

The Transformer Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) of its associated transformer. You can find a specific transformer using the names or numbers of its terminal buses, and you can learn more about a particular transformer’s terminal buses by choosing either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display). When in Edit Mode, you can delete an existing transformer from the case. You can also sort the transformer information by clicking on the heading of the field by which you want to sort.

To show this display select **Network \> Transformers Controls** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The Transformer Display contains the following fields by default:

From Bus Number and Name

*From Bus* number and name. The *From Bus* is the tapped side. You may view either the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or the [bus view display](08-view-case-data-tools.md#bus-view-display) for the *From Bus* from the local menu.

To Bus Number and Name

*To Bus* number and name. You may view either the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or the [bus view display](08-view-case-data-tools.md#bus-view-display) for the *To Bus* from the local menu.

Circuit

Two-character identifier used to distinguish between multiple transformers joining the same two buses.

Status

The service status of the transformer. This field is toggleable.

Type

Type of transformer. Possible values include

**Fixed  **The tap positions are fixed

**LTC  **The tap ratio changes to regulate bus voltage

**Mvar **The tap ratio changes to regulate reactive power flow

**Phase  **The phase angle changes to regulate real power flow

Tap/Phase

Indicates the tap ratio for LTC and fixed transformers and the phase shift angle in degrees for phase-shifting transformers.

XF Auto

If the value of this field is *Yes*, the transformer will automatically change its tap or phase angle to keep the regulated value within the specified regulation range, provided that the *Auto XF* field of its associated area is set to *Yes* and transformer tap/phase control has not been disabled for the entire case. The *Auto XF* field of individual areas is set from the [Area Display](05-case-information-displays-by-object-part1.md#area-display), and case-wide transformer control can be set from the Power Flow Solution tab of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) Dialog. Click on this field to toggle its values.

Reg Bus

For an LTC transformer, this is the number of the bus whose voltage is controlled by the transformer. For phase shifting transformers, the real power is always controlled at the tapped bus.

Reg Value

For an LTC transformer, this is the present per unit voltage at the regulation bus. For a phase shifting transformer, this is the present real power flow through the transformer measured on the "from" (tapped) side.

Reg Error

The error is the difference between the regulated value and the respective limit of the regulation range specified by Reg Min and Reg Max. If the regulated value is within the regulation range, then the error is zero. The error is negative if the regulated value falls below the regulation range, and it is positive if the regulated value exceeds the regulation range.

Reg Min, Reg Max

Minimum and maximum values for the regulation range. For LTC transformers, these fields represent per unit voltage at the regulated bus. For phase shifting transformers, these fields represent actual MW flow through the transformer measured on the "from" (tapped) side. Because transformers use discrete control, the maximum regulation value must be somewhat greater than the minimum value.

Tap Min, Tap Max

For LTC transformers, these fields specify the minimum and maximum tap ranges for the transformer. For phase shifting transformers, these fields specify the minimum and maximum phase shift angle in degrees.

Step Size

The per unit step size for tap changing transformers. This step size is usually determined by dividing the total range of transformer operation by the number of tap positions available.

---

<a id="three-winding-transformer-display"></a>

## Three Winding Transformer Display

*Source: [`Content/MainDocumentation_HTML/Three_Winding_Transformer_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Three_Winding_Transformer_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Three Winding Transformer Display shows information about all the three winding transformer devices in the case. Three winding transformers are modeled in Simulator as a grouping of two winding transformers, connected at a common midpoint or "Star" bus. The Three Winding Transformer Display is a way to view all the terminal connection points for the three winding transformers and the power delivered at each of the terminals.

Depending on how the three winding transformer was loaded into Simulator, the star bus may be dynamically created for the three winding transformer, with Simulator choosing the star bus number and name. If the star bus numbers and names of three winding transformers need to be changed, an option exists to load the new star bus numbers and names from a file. This option can be selected from the Three-Winding Transformer display in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) by right-clicking on the table and choosing **3W Transformer Records \> Renumber Star Buses** while in [edit mode](11-building-onelines-network-objects.md#edit-mode-overview). The format for the text file is one record per row, with six fields for each record. The first four fields are primary bus number, secondary bus number, tertiary bus number, and circuit ID. These fields identify for which three winding transformer the star bus is being changed for that record. The last two fields for each record will be the new star bus number and new star bus name. If the new bus number specified is already in use in the case, the record will be ignored and the star bus will not be renumbered for that three winding transformer record. Note that the first three fields can be specified as the "name\_kv" of each of the three winding transformer terminal buses instead of the bus numbers.

The Three Winding Transformer Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](06-object-properties-edit-mode-part3.md#three-winding-transformer-information) of its associated three winding transformers. When in Edit Mode, you can define new three winding transformers using the **Insert** option, or delete existing three winding transformers using **Delete**. You can also sort the three winding transformer information by clicking on the heading of the field by which you want to sort.

To show this display, open the [model explorer](04-model-explorer-and-case-information-part1.md#model-explorer) and click on **Network \> Three Winding Transformers**.

This display contains the following fields by default:

Pri Bus Num, Sec Bus Num, Ter Bus Num

These are the primary winding, secondary winding and tertiary winding terminal bus numbers for the three winding transformer connections.

Circuit 

The circuit identifier for the three winding transformer.

Pri, Sec and Ter MW and MVAr

These fields display the real and reactive power delivered at each of the three winding transformer terminals.

Star Bus Number and Name

These two fields provide the number and name of the internal node star bus used in the three winding transformer equivalent model.

While in Edit mode, the local menu allows an option that is specific to three-winding transformers. The option is found on the **3W Transformers records \>** menu item:

Renumber Star Buses...

This option allows renumbering the star buses of three-winding transformers to user-specified values. This is done via a text file that is loaded with the new designations. The format of the text file is the following:

*Primary bus*, *Secondary bus*, *Tertiary bus*, *circuit*, *new star bus number*, *new star bus name*

Either the bus number or name\_nominal kV (secondary key field) combination may be used to identify the buses. Each bus may be identified using either method even for the same three-winding transformer. Use double slashes (//) to indicate a comment in the file. Any text past the double slashes will be ignored. The file may be either space or comma delimited. If the tertiary bus does not exist, this entry should be either a 0 or empty string enclosed in double quotes. If the new star bus number already exists and is the star bus of another three-winding transformer, the star bus number of the other three-winding transformer will be reassigned and the current transformer will take the specified number. If the specified new star bus number already exists and is not taken by another star bus, the three-winding transformer will not be updated with the specified new star bus number.

---

<a id="line-shunts-display"></a>

## Line Shunts Display

*Source: [`Content/MainDocumentation_HTML/Line_Shunts_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Shunts_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Line Shunts Display identifies all line shunt devices in the case. Line shunts are similar to [switched shunts](06-object-properties-edit-mode-part3.md#switched-shunt-information) in that they are used in power systems either to inject additional MVR into the system (capacitive shunts) or to absorb excess reactive power (inductive shunts). However instead of being connected to a bus directly, they are instead shunt connected to one of the terminals of a transmission line. As a result they can only be in-service if the actual transmission line is in-service. Also, Simulator also does not allow the automatic regulation of a bus voltage using Line Shunts as is possible using a switched shunt. Simulator does however allow line shunts to be individually taken in and out of service. This must be done manually however using the status field of the line shunt.

The Line Shunts Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) of its associated line shunts. You can find a specific line shunt using its bus name or number, and you can learn more about a particular shunt’s terminal bus by choosing either [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display). When in Edit Mode, you can insert a new line shunt into the case or delete an existing shunt. You can also sort the line shunt information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Line Shunts Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To call up the Line Shunts Display, click **Network \> Line Shunts** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The Line Shunts Display contains the following fields by default:

From Number and To Number

Numbers of from and to bus of the transmission branch to which the line shunt is attached. Use the right menu options to inspect either the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or the [Bus View Display](08-view-case-data-tools.md#bus-view-display) for the terminal buses.

Circuit

Circuit identifier for the transmission branch to which the line shunt is attached.

Bus Number Located At

Either the From or To Bus number. Specified the end of the transmission branch to which the line shunt is attached.

ID

A circuit identifier for the actual line shunt. This is needed because there can be multiple line shunts at the same end of the same transmission line.

G, B

Indicates the line shunts nominal conductance and susceptance in per unit on the system base.

Status

Line shunts can be individually taken in and out of service. Do this by changing the status field to Open or Closed.

---

<a id="dc-lines-display"></a>

## DC Lines Display

*Source: [`Content/MainDocumentation_HTML/DC_Lines_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Lines_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The DC Line Display presents data describing each dc line in the case. The DC Line Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](06-object-properties-edit-mode-part3.md#dc-transmission-line-options) of its associated dc lines. You can also sort the dc line records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the DC Line Records Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the dc line records display, select **Network \> DC Transmission Lines** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer), and click on the DC Lines tab.

By default, the dc line records display contains the following fields:

Number

Each dc line must be assigned a unique number, typically between 1 and 40.

Rect AC Number, Rect AC Name, Rect MW, Rect Mvar

Number and name of the rectifier bus, and the real and reactive power flow from the rectifier into the dc line. You may right-click on any of the rectifier-related fields and select [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display) from the local menu to view additional information about the rectifier bus.

Inv AC Number, Inv AC Name, Inv MW, Inv Mvar

Number and name of the inverter bus, and the real and reactive power flow from the inverter into the dc line. You may right-click on any of the inverter-related fields and select [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display) from the local menu to view additional information about the inverter bus.

Control Mode

Specifies how flow on the dc line is controlled. If this field is set to *Power*, then the line’s MW flow is the control parameter. If the control mode is defined as *Current*, then the line’s current is the control parameter.

Setpoint Magnitude, Setpoint Location

Specifies the initial value of the control parameter, which is expressed either in MW or in amps depending on the dc line’s control mode. The Setpoint Location indicates if the setpoint should be set at the Inverter or Rectifier end of the DC line.

Set kV

Specifies the voltage of the dc line in kV.

---

<a id="multi-terminal-dc-record-display"></a>

## Multi-Terminal DC Record Display

*Source: [`Content/MainDocumentation_HTML/Multi_Terminal_DC_Record_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multi_Terminal_DC_Record_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Multi-terminal DC Line Display presents data describing each multi-terminal DC line in the case. The Multi-Terminal DC Line Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) of its associated records. The local menu also affords the opportunity to insert multi-terminal DC line records into the model or to delete existing ones.

To show the Multi-Terminal DC Line display, select **Network \> DC Lines** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer), and click on the Multi-terminal DC Lines tab of the transformer case information display.

The Multi-terminal DC Line display shows the following fields by default:

Number

The record number of each multi-terminal DC record.

Num Conv

The total number of converters in each multi-terminal DC network.

Num Buses

The total number of DC buses in each multi-terminal DC network.

Num Lines

The total number of DC lines in each multi-terminal DC network.

Mode

The control mode of the multi-terminal DC network: 0 is Blocked control, 1 is Power control, and 2 is Current control.

V. Cont. Bus

The number of the AC converter bus at which the DC voltage is controlled.

---

<a id="d-facts-devices"></a>

## D-FACTS Devices

*Source: [`Content/MainDocumentation_HTML/DFACTS_Devices.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DFACTS_Devices.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

D-FACTS Device Overview

Distributed Flexible AC Transmission System (D-FACTS) devices or "smart wires" change the effective line impedance of the transmission line on which they are installed **\[1\]**. Simulator supports the response of D-FACTS devices respond based on line current. This functionality is described in **\[2\]** and **\[3\]**.

For each line with D-FACTS devices, it is necessary to specify the number of modules and the amount of reactive impedance per module. The activation current I<sub>0</sub> and the maximum current I<sub>lim</sub>must also be specified. Below I<sub>0</sub>, the D-FACTS devices are inactive. Above I<sub>lim</sub>, the cumulative impedance injection of the D-FACTS devices on the line is at its maximum value. In Simulator, each module can be switched on or off. The D-FACTS device operation characteristic is represented by a function of the following form:

![DFACTS Characteristic](images/DFACTS_Characteristic.gif)

To view or insert D-FACTS devices on a transmission line, the [D-FACTS Settings Dialog](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog) may be used. This dialog can be accessed from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) or from the Parameters tab of the [Branch Options](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) dialog. In addition to saving D-FACTS devices in the PowerWorld binary file, full [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) support is available. This allows D-FACTS devices to be read in from an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) or [imported from Excel](04-model-explorer-and-case-information-part1.md#copy-paste-and-send-menu).

PowerWorld Support of D-FACTS Devices

[D-FACTS Case Information Displays](#d-facts-display)

[D-FACTS Power Flow Modeling](05-case-information-displays-by-object-part3.md#d-facts-control)

[D-FACTS OPF Control](05-case-information-displays-by-object-part3.md#d-facts-control)

[D-FACTS Oneline Displays](15-using-onelines-tools-and-options.md#relationship-between-display-objects-and-the-power-system-model)

[Sensitivity Analysis](20-sensitivities.md#multiple-meters-multiple-control-change)

**\[1\]** D. M. Divan, W. E. Brumsickle, R. S. Schneider, B. Kranz, R. W. Gascoigne, D. T. Bradshaw, M. R. Ingram, and I. S. Grant, “A distributed static series compensator system for realizing active power flow control on existing power lines,” IEEE Transactions on Power Delivery, vol. 22, no. 1, pp. 642-649, Jan 2007.

**\[2\]** H. Johal and D. Divan, “Design considerations for series-connected distributed FACTS converters,” IEEE Transactions on Industry Applications, vol. 43, no. 6, pp. 1609-1618, Nov./Dec. 2007.

**\[3\]** H. Johal and D. Divan, “Current limiting conductors: A distributed approach for increasing T\&D system capacity and enhancing reliability,” in 2005/2006 IEEE PES Transmission and Distribution Conference and Exhibition, pp.1127-1133, May 2006.

---

<a id="d-facts-display"></a>

## D-FACTS Display

*Source: [`Content/MainDocumentation_HTML/DFACTS_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DFACTS_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The D-FACTS Display presents data describing each [D-FACTS](#d-facts-devices) record in the case and is accessed from **Network\>Line D-FACTS Devices** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The D-FACTS Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a right-click [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog)[D-FACTS Information Dialog](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog) for the associated object. The [D-FACTS Information Dialog](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog) may also be opened from the Parameters tab of the [Branch Options](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) dialog. The local menu also affords the opportunity to insert new D-FACTS objects into the model or to delete existing ones. Moreover, it enables you to invoke the Pan to Object on Open Oneline function, if an associated D-FACTS display object is present on the oneline. You can also sort the D-FACTS records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the D-FACTS Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

D-FACTS Commonly Used Fields

The most commonly used D-FACTS are described below, grouped according to their purpose. **All numbers of modules, impedances, and inductances shown are per phase.** The key fields for a D-FACTS device object are the same as those of the transmission line on which it is located.

Key Field Identifiers

From Bus Number and Name

*From Bus* number and name for the transmission line.

To Bus Number and Name

*To Bus* number and name for the transmission line.

Circuit

Two-character identifier used to distinguish between multiple lines joining the same two buses. Default is ‘1’.

Actual Operating Point

Xinj (pu, mH)

The actual value of impedance injected on the line from D-FACTS devices which can be shown in both per unit and mH.

Num Modules Used

The actual number of modules used per phase. This is Xinj divided by X per Module.

Operational Characteristics

Num Modules

The total number of modules per phase available on the line.

X per Module (pu, mH)

Amount of impedance that each module injects.

Response

A toggleable field used to set the D-FACTS on this line to respond. The response may be set to "Limit" to use the current characteristic to look up the value for **Xinj**. The "Regulate" mode can be used to allow D-FACTS devices to maintain the flow on the line within a pre-specified range. The response may also be set to "Bypass" which takes the D-FACTS out of service, or "Fixed" which allows any fixed **Xinj** value to be used. See [D-FACTS Control](05-case-information-displays-by-object-part3.md#d-facts-control) for more information.

I0 (pu, Amps)

Minimum activation current. Below **I0**, no D-FACTS devices are turned on.

Ilim (pu, Amps)

Above the value of **Ilim** , no additional D-FACTS devices are available. **Ilim** is the current at which all available D-FACTS are turned on.

Auto-Configuration Settings

Auto Set Num Modules

A true/false value indicating whether to auto-configure the number of D-FACTS modules available based on a maximum compensation of line impedance as specified in the **Max Percent Line X** field.

Auto Set I0

A true/false value indicating whether to auto determine the value to use for I<sub>0</sub>. If this is set to true, Simulator will determine I<sub>0</sub> based on the **I0 Percent Rating** field.

Auto Set Ilim

A true/false value indicating whether to auto determine the value to use for I<sub>0</sub>. If this is set to true, Simulator will determine I<sub>lim</sub> based on the **Ilim Percent Rating** field.

Max % of Line X

Maximum compensation allowed as a percentage of line impedance. This value is only used if **Auto Set Num Modules** is set to True.

I0 % of Line Rating

Specifies the percent of the line rating to use for **I0** setting. This value is only used if **Auto Set I0** is set to True.

Ilim % of Line Rating

Specifies the percent of the line rating to use for **Ilim** setting. This value is only used if **Auto Set Ilim** is set to True.
