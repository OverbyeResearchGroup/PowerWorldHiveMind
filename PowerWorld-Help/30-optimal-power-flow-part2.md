---
title: "Optimal Power Flow (OPF) (Part 2 of 2)"
part: "Add-Ons"
chapter_file: "30-optimal-power-flow-part2.md"
topics: 14
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Optimal Power Flow (OPF) (Part 2 of 2)

Optimal Power Flow: formulation, dialogs, controls, constraints and results.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (14)**

- [OPF Bus Records](#opf-bus-records)
- [OPF Generator Records](#opf-generator-records)
- [OPF Interface Records](#opf-interface-records)
- [OPF Nomogram Records](#opf-nomogram-records)
- [OPF Line/Transformer Records](#opf-linetransformer-records)
- [OPF DC Lines Records](#opf-dc-lines-records)
- [OPF Load Records](#opf-load-records)
- [OPF Super Area Records](#opf-super-area-records)
- [OPF Controls](#opf-controls)
- [OPF Phase Shifter Controls](#opf-phase-shifter-controls)
- [OPF Example Page 1](#opf-example-page-1)
- [OPF Example Page 2](#opf-example-page-2)
- [OPF Example Page 3](#opf-example-page-3)
- [OPF Example Page 4](#opf-example-page-4)

---

<a id="opf-bus-records"></a>

## OPF Bus Records

*Source: [`Content/MainDocumentation_HTML/OPF_Bus_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Bus_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each bus record with a valid [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). To show this display select **Optimal Power Flow \> Results \> Buses** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The OPF Bus Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the display. The columns can also be sorted by right-clicking on the heading of the field.

By default the display contains the following fields

Number, Name

Bus’s number, between 1 and 2,147,483,647 (equals 2^31 minus 1), and its alphanumeric identifier.

Area Name

Name of the bus's area.

Specified Angle

If enforcing bus angle constraints, this is the desired angle at this bus in degrees. The angle will only be enforced if the Angle Tolerance is greater than a minimum threshold of 0.001 degrees.

Angle Tolerance

If enforcing bus angle constraints, this is the tolerance at which the Specified Angle will be enforced. The angle will only be enforced if the tolerance is greater than a minimum threshold of 0.001 degrees.

MW Marg. Cost

Marginal change in the objective function for a one MW change in the real power load at the bus.

MVR Marg. Cost

Marginal change in the objective function for a one Mvar change in the reactive load at the bus.

Volt Marg. Cost

Marginal change in the objective function for a 0.01 per unit change in the voltage setpoint for the bus. This field is only valid at bus’s whose terminal voltage is controlled by one or more generators.

*Note from the* *developers* *– this field is still under construction – do not use it yet.*

---

<a id="opf-generator-records"></a>

## OPF Generator Records

*Source: [`Content/MainDocumentation_HTML/OPF_Generator_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Generator_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each generator record with a valid [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). To show this display select **Optimal Power Flow \> Results \> Generator Records** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The OPF Generator Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the display.

By default the display contains the following fields:

Number, Name

Number and name of the bus to which the generator is attached. The display's local menu offers you the opportunity to view the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and the [Bus View Display](08-view-case-data-tools.md#bus-view-display) for this bus. You can also use the local men to view the [generator's dialog](07-object-properties-run-mode-and-general-part1.md#generator-information).

ID

Alphanumeric ID used to distinguish multiple generators at the same bus.

Area Name of Gen

Name of the generator's area.

AGC

Designates whether the generator's real power output is governed by automatic generation control (AGC). If the AGC field is set to Yes the generator is on AGC in the standard power flow. When a generator is on AGC its real power output is varied automatically, provided the generator is part of an area or super area that is also on automatic control.

In Simulator OPF the default operating mode is that only generators on AGC control are eligible to be OPF controls. In addition, the generator's area or super area must have **AGC Status** of "OPF". However in rare instances you may wish to always make a generator available for control or never make the generator available for control. This value is specified using **OPF MW Control** field.

Fast Start

Designates whether the generator is available as a Fast Start generator during the OPF solution process. Fast start generators are another type of control available to the Optimal Power Flow solution routine. The OPF routine can determine if a generator labeled as a fast start generator would be beneficial in reducing the overall system costs of generation dispatch. If a fast start generator is off-line, but could reduce the cost of the system, then the OPF routine will turn on the generator, and increase the generator's dispatch towards optimizing the system generating cost. Conversely, if a fast start generator is on-line, and the OPF routine determines that reducing the generator's output to 0 would reduce the total generation cost, then the OPF routine will shut off the generator.

Generally speaking, the fast start options should only be used with units with zero Minimum MW limits.  Hence it is really aimed at hydro units, or small units which do not need a non-zero minimum MW output for valid operation.  This requirement is needed because changing a unit's status is only valid in the OPF routine if it is determined that the unit should dispatch 0 MW to optimize the generating costs of the system.

OPF MW Control

Designates whether the generator's real power output should be included as a control variable in the OPF. This field, which can be toggled, has three possible values:

  - "If AGCable" - Generator's control availability depends upon its AGC status.
  - "Yes" - Generator is available as a control, regardless of its AGC status.
  - "No" - Generator is NOT available as a control, regardless of its AGC status.

**Note:** in order to be a control the generator must also be in an area or super area on "OPF" control.

Gen MW

The real power output of the generator.

Cost Shift $/MWh, Cost Multiplier

The cost shift and cost multiplier allow you to easily apply a shift to the cost function for the purpose of assessing how variations in bids impact profit. The cost function is affected based on the following equation:

(Original Cost Function + Cost Shift) \* Cost Multiplier

Cost $/Hr

The total cost of the generator, including the impact of the cost shift and cost multiplier.

MW Marg. Cost

Tells the marginal cost, in $ / MWhr, to supply one additional MW of load at this bus. If a generator is available as a control and is not at either its minimum or maximum limit or a cost model breakpoint, then the **MW Marg. Cost** field will be identical to the generator's current marginal cost. However the usual case is for the generator to be at either a limit or a cost model breakpoint so the usual situation is that the **MW Marg. Cost** field values IS NOT equal to the generator's marginal cost.

IC for OPF

Incremental cost of the generator at its current operating point.

Initial MW

The initial real power output of the generator at the beginning of the OPF solution. You can reset the case back to these values by selecting the LP OPF, Restore Previous Control Settings **** menu item. This menu item is only available following a successful OPF solution.

Initial Cost

The initial generator cost at the beginning of the OPF solution.

Delta MW

Change in the generator's real power output as a result of the OPF.

Delta Cost

Change in the generator's cost as a result of the OPF.

Min MW, Max MW

Minimum and maximum real power output of the generator.

Cost Model

The current cost model being used for the generator. The field value is either "Cubic", indicating that the generator's operating costs are being modeled using a cubic cost function, or "Piecewise Linear", indicating the operating costs are being modeled using a piecewise linear cost function. Toggle the field to change the model. Note that a generator may simultaneously have a cubic model and a piecewise linear model.

Because the OPF uses a linear programming approach, the generator's operating costs are ALWAYS modeled using the piecewise linear model. Generators with an existing cubic cost model are either 1) ignored as OPF controls, or 2) have a piecewise linear cost model automatically created from the cubic model, depending upon the values specified on the [OPF Options and Results Dialog](30-optimal-power-flow-part1.md#opf-options).

\# Cost Curve Points

Shows the number of segments in the piecewise linear model. If no piecewise linear model exists then this field is zero; the generator's costs are being modeled using the cubic function. For such generators you can automatically setup a piecewise linear model simply by entering a non-zero value for the number of points. A piecewise linear model is created that matches as closely as possible the existing cubic model.

Fuel Type

Specifies the fuel type of the generator, if it is known; double-click to toggle through the options. Options are Unknown, Coal, Gas, Hydro, Hydro Pumped, Nuclear, Petroleum, Solar, Wind, and Other.

Profit $/hr

Shows the profit of the generator. Profit is calculated using this equation:

Profit = (GenMW \* MW Marg Cost ) – \[ Evaluation of the Generator Cost Function \]

---

<a id="opf-interface-records"></a>

## OPF Interface Records

*Source: [`Content/MainDocumentation_HTML/OPF_Interface_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Interface_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about the interface records in the case. To show select **Optimal Power Flow \> Results \> Interfaces** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This display is actually a page of a display showing all the potential inequality constraints in the power system. The top portion of the display repeats the fields shown on the [Constraint Options page](30-optimal-power-flow-part1.md#opf-options---constraint-options) of the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options).

To view the Interface records click on the Interfaces tab. This displays the interfaces page which is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the page.

By default the Interface Records page contains the following fields:

Name

Name of the interface.

Monitor

Specifies whether or not the interface MW limit is enforced in the OPF solution.

Interface MW

The amount of MW flow on the interface.

MW Limit

The interface MW limit.

Percent

The amount of MW flow on the interface as a percentage of the limit.

Monitor Direction

The direction on the interface in which the flow is being monitored.

Monitor Both Directions

If set to **YES**, then the interface flow will be monitored in both directions. Otherwise, it will only be monitored in the **Monitor Direction**.

MW Marg. Cost $ / MWh

The marginal cost of enforcing the limit on the interface.

Constraint Status

This field will be set to Binding if the interface limit is a binding constraint in the OPF solution, or Unenforceable if the interface limit is unenforceable with the available control set.

---

<a id="opf-nomogram-records"></a>

## OPF Nomogram Records

*Source: [`Content/MainDocumentation_HTML/OPF_Nomogram_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Nomogram_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This list displays OPF specific information about the nomogram records in the case. To show the list, select **Optimal Power Flow \> Results \> Nomograms** in the**** [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This display is actually a page of a display showing all the potential inequality constraints in the power system. The top portion of the display repeats the fields shown on the [Constraint Options page](30-optimal-power-flow-part1.md#opf-options---constraint-options) of the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options).

To view the nomogram records click on the Nomogram Interfaces tab. This displays the nomogram interfaces page which is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the page.

By default the Interface Records page contains the following fields:

Nomo. Name

Name of the nomogram.

Nomo. Seg.

The segment of the nomogram. Each segment of the nomogram is treated as a separate constraint in the OPF, and therefore is listed individually in the OPF nomogram table.

Monitor

This field will be set to YES if the nomogram segment is monitored during the OPF.

Interface MW Flow

The total MW flow for the segment of the nomogram.

MW Limit

The segment MW limit.

Percent

The amount of MW flow on the segment as a percentage of the segment’s limit.

Monitor Direction

The direction on the segment in which the flow is being monitored.

Monitor Both Directions

Yes or No field indicating if both directions should be monitored at the same time.

MW Marg. Cost $ / MWh

The marginal cost of enforcing the limit on the segment.

Constraint

This field will be set to Binding if the nomogram limit is a binding constraint in the OPF solution, or Unenforceable if the nomogram limit is unenforceable with the available control set.

---

<a id="opf-linetransformer-records"></a>

## OPF Line/Transformer Records

*Source: [`Content/MainDocumentation_HTML/OPF_Line_Transformer_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Line_Transformer_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about the line and transformer records in the case. To show the display select **Optimal Power Flow \> Results \> Branches** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This display is actually a page of a display showing all the potential inequality constraints in the power system. The top portion of the display repeats the fields shown on the [Constraint Options page](30-optimal-power-flow-part1.md#opf-options---constraint-options) of the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options).

To view the Line and Transformer records click on the Line/Transformers tab. This displays the Line/Transformer page which is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the display.

By default the display contains the following fields:

From Number, From Name, From Area Name

Number, Name, and Area Name of the From bus.

To Number, To Name, To Area Name

Number, Name, and Area Name of the To bus.

Circuit

Circuit identifier for the branch.

Monitor

Specifies whether or not the branch's MVA limit will be enforced in the OPF solution.

Max MVA

The maximum MVA flow on the branch. Value is determined based on the end of the branch with the higher MVA flow.

% of MVA Limit (Max)

The maximum MVA flow as a percentage of the branch MVA limit. Value is determined based on the end of the branch with the higher MVA flow.

Lim MVA

The MVA limit for the branch.

MVA Marg. Cost ($/MVAhr)

The marginal cost of changing the MVA flow on the branch (i.e., if the line rating were to increase by 1 MVA, what savings could be had).

Constraint

This field will be set to Binding if the branch limit is a binding constraint in the OPF solution, or Unenforceable if the branch limit is unenforceable with the available control set.

---

<a id="opf-dc-lines-records"></a>

## OPF DC Lines Records

*Source: [`Content/MainDocumentation_HTML/OPF_DC_Lines_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_DC_Lines_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about the DC lines in the case. To show select **Optimal Power Flow \> Results \>** **DC Lines** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the display.

By default the display contains the same fields as the normal [DC Line Records](05-case-information-displays-by-object-part2.md#dc-lines-display) case information display, with the following additional fields:

OPF Control

Set to **YES** if the DC line is to be controlled during the OPF. To be controlled, at least one of the terminals of the DC line must lie in an area that is on OPF control and this must be set to **YES**.

Min MW or amps, Max MW or amps

The minimum and maximum power (or current) setpoints allowed for the DC line.

---

<a id="opf-load-records"></a>

## OPF Load Records

*Source: [`Content/MainDocumentation_HTML/OPF_Load_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Load_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each load record with a valid [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). To show this display select **Optimal Power Flow \> Results \> Loads** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The OPF Load Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), which can be accessed by right-clicking on any field in the display.

By default the display contains the following fields:

Number, Name

Number and name of the bus to which the load is attached. The display's local menu offers you the opportunity to view the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) and the [Bus View Display](08-view-case-data-tools.md#bus-view-display) for this bus. You can also use the local menu to view the [generator's dialog](07-object-properties-run-mode-and-general-part1.md#generator-information).

ID

Alphanumeric ID used to distinguish multiple loads at the same bus.

Area Name of Load

Name of the load’s area.

AGC

Designates whether the load’s real power demand is governed by automatic generation control (AGC). If the AGC field is set to Yes the load is on AGC in the standard power flow. When a load is on AGC its real power output is varied automatically during an OPF or SCOPF solution ONLY, provided the load is part of an area or super area that is also on OPF control. Loads will not be dispatched if the area is on some other form of AGC control.

In Simulator OPF the default operating mode is that only loads on AGC control are eligible to be OPF controls. In addition, the load’s area or super area must have **AGC Status** of "OPF", and the area must have its Load MW Dispatch set to YES.

MW

The real power output of the load.

Cost Shift $/MWh, Cost Multiplier

The cost shift and cost multiplier allow you to easily apply a shift to the cost function for the purpose of assessing how variations in bids impact profit. The cost function is affected based on the following equation:

(Original Cost Function + Cost Shift) \* Cost Multiplier

Hourly Benefit

The total benefit of the load, including the impact of the cost shift and cost multiplier.

MW Marg. Cost

Tells the marginal cost, in $ / MWhr, to reduce one additional MW of load at this bus. If a load is available as a control and is not at either its minimum or maximum limit or a cost model breakpoint, then the **MW Marg. Cost** field will be identical to the load’s current marginal cost. However the usual case is for the load to be at either a limit or a cost model breakpoint so the usual situation is that the **MW Marg. Cost** field value IS NOT equal to the load’s marginal cost.

Inc. Benefit

Incremental benefit of the load at it’s current operating point.

Initial MW

The initial real power demand of the load at the beginning of the OPF solution.

Initial Cost

The initial load cost at the beginning of the OPF solution.

Delta MW

Change in the load's real power output as a result of the OPF.

Delta Cost

Change in the load's cost as a result of the OPF.

Min MW, Max MW

Minimum and maximum real power demand of the load.

\# of Benefit Curve Points

Shows the number of segments in the piecewise linear model. If no piecewise linear model exists then this field is zero.

Profit $/hr

Shows the profit of the load.

---

<a id="opf-super-area-records"></a>

## OPF Super Area Records

*Source: [`Content/MainDocumentation_HTML/OPF_Super_Area_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Super_Area_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each super area record in the case. To show this display select **Optimal Power Flow \> Results \> Super Areas** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The OPF Super Area Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the local menu, which can be accessed by right-clicking on any field in the display.

By default the display contains the following fields:

Super Area

Alpha-numeric identifier of the super area.

AGC Status

Super area's automatic generation control status. This is the same field shown on the Super Area Records display. The field indicates whether or not the super area's generation is changing automatically to control the super area's interchange.

The super area AGC Status field always overrides the AGC Status for the individual areas, except when it is set to "Off AGC".

To be included in the OPF this field MUST be "OPF". In that case the generation costs for all the areas in the super area are included in the OPF objective function. Otherwise they are only included if the super area AGC Status is "Off AGC" and their particular area's AGC Status is on "OPF". Double-click on the field to toggle its value.

Num Areas

Number of areas in the super area. To see the individual areas use the local menu to view the Super Area dialog.

Include Marg. Losses

Specifies whether or not to include marginal losses in OPF calculations for this super area.

MW Marg. Cost Ave.

If the super area is on "OPF" control then for a solved case this field shows the average of the bus MW marginal costs for all the buses in the super area. If there is no congestion then all of the marginal costs should be equal.

MW Marg. Cost St. Dev.

Standard deviation of the bus MW marginal costs for the buses in the super area.

ACE MW

Area control error for the super area.

Gen MW, Load MW

Total real power generation and load in the super area.

Total Sched MW, Int MW

Scheduled and actual interchange real power interchange between the super area and the rest of the system. Both of these fields are the algebraic summation of the scheduled and actual interchange for the areas in the super area.

Loss MW

Total real power losses for the super area.

MW Marg. Cost Min, MW Marg. Cost Max

Minimum and maximum of all the bus MW marginal costs for the buses in the super area.

---

<a id="opf-controls"></a>

## OPF Controls

*Source: [`Content/MainDocumentation_HTML/OPF_Controls.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Controls.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following classes of controls are available during the OPF solution. Note, individual classes of controls can be enabled/disabled for the entire case using the OPF Options and Results dialog and for particular areas using the OPF Area Records display. Also, all classes of controls have associated minimum/maximum limits which are always enforced.

Generator MW output and Fast Start commitment

The generator MW outputs are the major control for controlling the MW flow in the network and for minimizing the objective function. Only generators in areas or super areas that are on "OPF" control are eligible for control; otherwise the generator's MW output remains fixed at its initial value. Whether a particular generator is available for control also depends upon the status of its AGC and OPF MW Control fields. These fields are set on the [OPF Generator Records](#opf-generator-records) display. For Fast Start Generators, it is also possible to use the startup and shutdown of these generators as a control. See [OPF Options: Control Options](30-optimal-power-flow-part1.md#opf-options---control-options) for more details.

Phase shifting Transformer tap position

Phase shifting transformers are used primarily to control the flow of real power in the network. When phase shifting transformers are controlled in the OPF routine, the phase angle is allowed to move anywhere within the phase angle range of the device in order to help alleviate violations on other branches in the system. The flow on the phase shifter is allowed to violate the prescribed MW range given for the phase shifter, but is NOT allowed to violate the MVA rating of the device.

Additionally, in order for a phase shifter to be included in the OPF solution dispatch, the XF Phase property of the area must be set to YES. Each individual phase shifter also has a property for being included in the OPF control that must be turned on in order for the phase shifter to participate in the OPF dispatch. This option can be set for a phase shifting transformer by opening its [Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) and checking the OPF Phase Shifter Control options on the OPF page of the dialog.

D-FACTS Devices on the Line Xinj

[D-FACTS devices](05-case-information-displays-by-object-part2.md#d-facts-devices) are primarily real power flow controls that work by changing the effective line impedance. The Xinj values of D-FACTS can be included as controls for dispatch during an OPF solution. The concept of controlling D-FACTS devices in the OPF is very similar to controlling a phase shifting transformer. See [D-FACTS Control](05-case-information-displays-by-object-part3.md#d-facts-control) .

Load MW Dispatch

The load MW demands can also be included as controls for re-dispatch during an OPF solution. The concept of controlling a load is generally the same as controlling a generator. Loads can be assigned piecewise linear benefit curves, and included in the OPF dispatch algorithm. Only areas whose AGC control is set to "OPF" are eligible for control. Furthermore, the OPF area’s Load MW Dispatch property must also be set to YES. Each area load that is to be included for OPF dispatch must have a benefit model defined, and have its Available for AGC field set to YES. These fields can be set in the [OPF Load Records](#opf-load-records) display.

DC Line MW setpoint

DC Line MW setpoints can be used as controls in the OPF. See [OPF DC Lines Records](#opf-dc-lines-records).

Island Slack Bus Angles

When enforcing [bus angle constraints](30-optimal-power-flow-part1.md#opf-inequality-constraints), island slack bus angles are automatically included as control variables. These controls have no associated cost, so moving these instead of other control variables is often the least costly solution to bring bus angles within tolerance. When the island slack bus angle is changed, all bus angles in the same island are moved by the same amount. There is no user option that will allow disabling or enabling island slack bus angles as controls. The island slack bus angle control will be added for each island that contains a bus that is enforcing its angle.

---

<a id="opf-phase-shifter-controls"></a>

## OPF Phase Shifter Controls

*Source: [`Content/MainDocumentation_HTML/OPF_Phase_Shifter_Controls.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Phase_Shifter_Controls.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each phase shifter record in the case. To show this display, select **Optimal Power Flow \> Results \> Phase Shifters** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The OPF Phase Shifter Records display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the local menu, which can be accessed by right-clicking on any field in the display. The columns can also be sorted by right-clicking on the heading of the field.

By default the display contains the following fields:

From Number, From Name

The name and number of the bus at the From end of the phase shifter.

To Number, To Name

The name and number of the bus at the To end of the phase shifter.

Circuit

The circuit identifier for the phase shifter.

OPF Control

Specifies whether or not the phase shifter is available for control during an OPF solution.

Area PS Control

Specifies if automatic phase shifter control has been enabled for the area containing the particular phase shifting transformer. If the area phase shifter control is disabled, all phase shifting transformers within the area will remain fixed at their initial settings during the entirety of the OPF solution process. This setting overrides the individual automatic control settings of each phase shifting transformer within the area.

XF Auto

Specifies if the transformer automatic control is enabled. If an individual transformer's automatic control is disabled, it will remain at it's initial settings during the entirety of the OPF solution process.

Phase (Deg)

The actual phase shift of the phase shifter, in degrees.

Initial Degrees

The initial phase angle before the OPF solution was calculated.

Delta Degrees

The change in the phase angle during the OPF solution.

Tap Min, Tap Max

The minimum and maximum tap positions allowed for the phase shifter operation.

---

<a id="opf-example-page-1"></a>

## OPF Example Page 1

*Source: [`Content/MainDocumentation_HTML/OPF_Example_Page_1.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Example_Page_1.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

As a simple example of using the OPF, consider the seven bus, three area system contained in the file B7OPF.pwb (included with the PowerWorld Simulator). For this case all three areas are initially on Economic Dispatch (ED) AGC control and hence by default would not be included in the OPF solution. Also, the initial interchange between the areas is equal to zero and the generators are modeled using cubic cost functions.

To initially solve the case using the standard power flow, select **Solve Power Flow** in the **[Power Flow Tools](02-simulator-ribbon.md#simulation-control)** ribbon group**** on the **[Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab**. The case should look like the following figure:

![image\\ebx\_515249793.gif](images/ebx_515249793_498x374.gif)

B7OPF Case Solved using Economic Dispatch

Now we'll modify the case to set the three areas for OPF control. To do this, select **Optimal Power Flow \> Results \> Areas** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to display the [OPF Area Records display](30-optimal-power-flow-part1.md#opf-area-records). Toggle the AGC status for each of the three areas to change it to "OPF". Now select **Primal LP** in the **OPF** ribbon group**** on the **[Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab** to solve the case using the LP OPF. The results should look similar to the figure below. The one-line shows the hourly cost for each area and the total case hourly cost, equal to $ 16,888 / hr.

![image\\ebx\_-1639172225.gif](images/ebx_-1639172225_498x374.gif)

B7OPF Case Solved using LP OPF

Note that the results are very similar but not identical to the economic dispatch case. We would expect the cases to be similar since for cases with no congestion the OPF solution should be (ideally) equal to the economic dispatch solution. The difference between the two is because in the LP OPF the generator cost functions are converted from a cubic model to a piece-wise linear model using a user specified number of segments, which is 5 segments by default. This value can be viewed/modified from the Control Options page of the [OPF Options and Results display](30-optimal-power-flow-part1.md#opf-options---common-options).

Change the **Total Points Per Cost Curve** field to 100 and resolve. The results are shown in the figure below, which now are almost identical to the economic dispatch results. The disadvantage in using a large number of cost segments is that it degrades the performance of the LP OPF slightly on larger cases.

![image\\ebx\_1089218349.gif](images/ebx_1089218349_498x374.gif)

B7OPF Case Solved using LP OPF with 100 Cost Segments for Generators

---

<a id="opf-example-page-2"></a>

## OPF Example Page 2

*Source: [`Content/MainDocumentation_HTML/OPF_Example_Page_2.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Example_Page_2.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Using the OPF solution from the previous page, select **Optimal Power Flow \> Results \>** **Buses** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to view the bus marginal costs and **Optimal Power Flow \> Results \>** **Areas** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to view the area marginal costs. The results should be as shown below.

![Seven Bus Marginal Cost](images/Seven_Bus_Marginal_Cost.gif)

Seven Bus Case Bus Marginal Costs

![Seven Bus Area Marginal Cost](images/Seven_Bus_Area_Marginal_Cost.gif)

Seven Bus Case Area Marginal Costs

Note that the marginal costs for all the buses in an area are identical to the area's MW marginal cost. This is the expected result for systems without any line congestion. The area MW marginal costs are not identical. This is because currently each area is independently enforcing its own MW interchange. In the next example we'll jointly dispatch the three areas by combining them into a single [super area](#opf-super-area-records).

---

<a id="opf-example-page-3"></a>

## OPF Example Page 3

*Source: [`Content/MainDocumentation_HTML/OPF_Example_Page_3.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Example_Page_3.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To jointly dispatch the three areas we'll first combine them into a single super area. To setup the super area first select **Optimal Power Flow \> Super Areas** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to display [the OPF Super Area Records display](#opf-super-area-records) (alternatively you could also use the **Aggregations \> Super Areas** display). To enter a new super area, right click on the "None Defined" entry in the first row of the display to show the display's local menu. Select **Insert**. This displays the [super area dialog](07-object-properties-run-mode-and-general-part2.md#super-area-information). Select **Rename** and enter a name for the new super area, "ThreeAreas." To add the three areas to the new super area enter "1-3" in the **New Area \#'s** field and then select **Add New Areas by Number** (alternatively you could select the areas from the **New Area Name** list). Also, to enable the super area for control, set the **Super Area Control Options** field (AGC Status) to Optimal Power Flow Control. Select the **Ok** button to save the new super area.

Before resolving the OPF, let’s temporarily disable enforcement of line MVA constraints. You can do this from the [Constraint Options page](30-optimal-power-flow-part1.md#opf-options---constraint-options) of the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options). Check the **Disable Line/Transformer MVA Limit Enforcement.**

Also, now would be a good time to save the changes. To avoid overwriting the existing B7OPF file, select **Save Case As** from the [File menu](03-cases-files-and-formats.md#file-menu) to save the case (pwb and pwd files) with a different name, say B7OPFSA (SA for super area).

Select **Primal LP** from the **OPF **ribbon group on the **[Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab** to resolve the OPF. The results should be as shown below.

![image\\ebx\_731777159.gif](images/ebx_731777159_498x374.gif)

OPF Solution with Super Area WITHOUT Enforcing Line MVA Constraints

With the super area the individual area interchange constraints are no longer enforced. This permits the free interchange of power between the areas, resulting in an overall decrease in the total case hourly cost from $ 16,887 / hr to $ 16,227 / hr. View the OPF Bus Records display to verify that all the bus marginal costs are identical, equal to $ 17.10 / MWh. Of course the key problem with solving the system using the super area is that now there are line violations. These violations will be removed next by enforcing the line MVA constraints.

---

<a id="opf-example-page-4"></a>

## OPF Example Page 4

*Source: [`Content/MainDocumentation_HTML/OPF_Example_Page_4.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Example_Page_4.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To remove the line MVA violations go back to the [Constraint Options Page](30-optimal-power-flow-part1.md#opf-options---constraint-options) of the [OPF Options and Results](30-optimal-power-flow-part1.md#opf-options) dialog. Uncheck the **Disable Line/Transformer MVA Limit Enforcement.**

Now resolve the LP OPF, enforcing the line constraints. The resultant solution is shown below.

![New 7 Case Line Limits 520x367](images/New_7_Case_Line_Limits_520x367.gif)

OPF Solution with Super Area WITH Line MVA Constraint Enforcement

With line constraint enforcement active the OPF optimally redispatches the generation taking into account the line MVA limits. However, enforcing these line constraints comes at a cost. Notice that the total case hourly cost has increased from $ 16,227 / hr to $ 16,661 / hr, which is still substantially less than the $ 16,887 / hr figure we had for the case without the superarea.

Enforcing the line constraints also has an impact on the bus marginal costs, shown below.

![New 7 Case Line Limits Bus Records](images/New_7_Case_Line_Limits_Bus_Records.gif)

Impact of Line MVA Enforcement on the Bus Marginal Costs

The actual marginal cost of enforcing the line constraint can also be viewed on the [OPF Line/Transformer MVA Records](#opf-linetransformer-records) display. The MVA Marg. Cost tells the marginal cost of enforcing the constraint, expressed in units of $ / MVA / hr. Left-click on the **MVA Marg Cost** field header to sort the display using this field.

![New 7 Case Line Limits Dialog 717x377](images/New_7_Case_Line_Limits_Dialog_717x377.gif)
