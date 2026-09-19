---
title: "Case Information Displays by Object Type (Part 3 of 3)"
part: "Viewing Case Data"
chapter_file: "05-case-information-displays-by-object-part3.md"
topics: 23
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Case Information Displays by Object Type (Part 3 of 3)

The per-object case information displays: buses, generators, loads, lines, transformers, shunts, interfaces, ownership and more.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (23)**

- [D-FACTS Settings Dialog](#d-facts-settings-dialog)
- [D-FACTS Control](#d-facts-control)
- [Switched Shunt Display](#switched-shunt-display)
- [Switched Shunt Control](#switched-shunt-control)
- [Interface Display](#interface-display)
- [Nomogram Display](#nomogram-display)
- [Bus Pair Display](#bus-pair-display)
- [Injection Group Display](#injection-group-display)
- [Injection Group Dialog](#injection-group-dialog)
- [Participation Point Records Display](#participation-point-records-display)
- [Island Display](#island-display)
- [MW Transactions Display](#mw-transactions-display)
- [MW Transactions Information Dialog](#mw-transactions-information-dialog)
- [Owner Data Information Display](#owner-data-information-display)
- [Owner Dialog](#owner-dialog)
- [Owned Bus Records Display](#owned-bus-records-display)
- [Owned Load Records Display](#owned-load-records-display)
- [Owned Generator Records Display](#owned-generator-records-display)
- [Owned Line Records Display](#owned-line-records-display)
- [Owned Three-Winding Transformer Records Display](#owned-three-winding-transformer-records-display)
- [Jacobian Display](#jacobian-display)
- [Ybus Display](#ybus-display)
- [Voltage Droop Control Display](#voltage-droop-control-display)

---

<a id="d-facts-settings-dialog"></a>

## D-FACTS Settings Dialog

*Source: [`Content/MainDocumentation_HTML/DFACTS_Settings_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DFACTS_Settings_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

D-FACTS Information Dialog

The D-FACTS dialog is used to modify and view the D-FACTS response characteristics.

To display this dialog, right-click on a D-FACTS record in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) and choose "Show Dialog." The dialog can also be displayed from the [Branch Options](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) dialog by clicking the "D-FACTS Devices on the Line" button on the Parameters tab. **All numbers of modules, impedances, and inductances shown are per phase.**

See [D-FACTS Display](05-case-information-displays-by-object-part2.md#d-facts-display) to view a complete list of the commonly used D-FACTS fields.

Calculated Values

**Num Modules per Phase**: The total number of modules per phase present and available on the line.

**Total Available X per Phase**: The total inductance per phase available on the line.

**Present Value of Xinj**: The actual inductance per phase that is presently being injected on the line.

**I0**: The minimum activation current.

**Ilim**: The maximum current for impedance injection. At this value, all available impedance is injected.

**Present Value of Iline**: The value of the line current presently on the line.

D-FACTS Profile

The D-FACTS Profile window shows the characteristic used in "Limit" mode to set the D-FACTS devices based on line current. This curve is determined based on **Inductance per Module**, **Num Modules per Phase**, **I**<sub>0</sub>, and **I**<sub>lim</sub>. As line current increases between **I**<sub>0</sub> and **I**<sub>lim</sub>, a greater number of D-FACTS modules become active. When **I**<sub>lim</sub> is reached, the total number of available modules are active.

Inputs Tab

The Inputs tab of the D-FACTS Information Dialog shows the common parameters required for defining a D-FACTS device record on the transmission line.

Direct Input of Characteristic Curve Parameters

**Num Modules per Phase**: The total number of modules per phase present and available on the line. The user can enter this value here.

**Inductance per Module**:The user can enter this value here. The default is 47 micro Henries. A value must be specified.

**Activation Current I0**: The minimum activation current. The user can enter this value, or it can be calculated from the Auto Configuration settings.

**Max Current Ilim**: The maximum current for impedance injection. At this value, all available impedance is injected. The user can enter this value, or it can be calculated from the Auto Configuration settings.

Auto Configure Characteristic Curve Parameters

These options allow the user to let Simulator determine the number of available modules automatically based on the**Max Percentof Line X** field. These options also allow Simulator to calculate values for **I**<sub>0</sub> and **I**<sub>lim</sub> based on the **Percent of Line Rating** field.

![DFACTS Dialog LimitMode InputTab](images/DFACTS_Dialog_LimitMode_InputTab.jpg)

Control Info Tab

This tab shows options related to automatic control.  Automatic control of the D-FACTS on the line is performed within the voltage control loop of the power flow, where phase shifting transformers and LTCs are also handled. If automatic control is disabled for the D-FACTS on the line, the fields on the dialog will be grayed out. In this case, the operating point of the D-FACTS devices is not determined by the limit characteristic but is determined by the control objective.

![DFACTS Dialog RegMode](images/DFACTS_Dialog_RegMode.jpg)

---

<a id="d-facts-control"></a>

## D-FACTS Control

*Source: [`Content/MainDocumentation_HTML/DFACTS_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DFACTS_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator supports four operational modes of D-FACTS devices within the power flow. PowerWorld also supports D-FACTS devices as controls in the OPF ([Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)) and the SCOPF ([Security Constrained OPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview)) tools.

Power Flow Modeling of D-FACTS Devices

PowerWorld Simulator implements the control of the D-FACTS devices in the voltage control loop of the power flow solution. That is, after the inner power flow loop is solved to determine the state variables, the line current is calculated, and the D-FACTS values are adjusted, if necessary. The D-FACTS adjustment needed is computed according to their predefined piecewise linear lookup functions in **Limit** mode or according to their automatic control settings when in **Regulate** mode. If the D-FACTS values are changed, an additional power flow inner loop is solved.

Within the power flow, Simulator supports four D-FACTS operational modes:

Bypass

Takes the D-FACTS on the line out of service and sets its **Xinj** to zero.

Limit

Uses a fixed value of **Xinj** for the D-FACTS on the line. This fixed value can be set externally. In particular, values can be set manually by the user, or by an external source such as SimAuto, script commands, an aux file, etc.

Fixed

Uses any fixed value of **Xinj** for the D-FACTS on the line. This fixed value can be set in a variety of ways. For example, values can be set manually by the user, or through an external source via SimAuto, script commands, an aux file, etc. Simulator also uses this mode when solving the OPF with D-FACTS as controls, so the OPF is being treated like an external program which determines the optimal values for**Xinj** and then fixes the D-FACTS settings at those values. Additionally, if D-FACTS devices are cycling on and off within the power flow solution, they will be placed into this mode to prevent further oscillation. This problem can be avoided by adjusting the defined limit characteristic settings or the control range.

Regulate

Uses sensitivities to adjust D-FACTS devices on the line to keep the line's flow within a user-specified range.

Optimal Power Flow Control of D-FACTS Devices

The capability of D-FACTS devices to respond as controls during the OPF solution has been added. The OPF is only available if you have the OPF ([Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)) add-on tool for PowerWorld Simulator. D-FACTS devices can be treated as a control variable by the OPF so that lines with D-FACTS devices can be coordinated to relieve overloads and achieve minimal cost. D-FACTS can relieve line violations, therefore avoiding the need to re-dispatch more costly generators.

Setting up OPF Control

As with all controls in PowerWorld Simulator, there are three places D-FACTS OPF response has to be enabled in order to use D-FACTS as an OPF control. First, D-FACTS control should be enabled at the case level from the Common Options tab of the LP OPF Dialog by unchecking “Disable D-FACTS Controls.” “D-FACTS Cost” specifies the cost of D-FACTS operation, which is assumed to be very low or negligible.

![DFACTS OPF CommonOptions](images/DFACTS_OPF_CommonOptions.jpg)

D-FACTS are also enabled on a per-area basis and a per-line basis. On the **Areas** tab of the Model Explorer, the **DFACTS Xinj Control** field should be set to **YES**.

![DFACTS OPF AreaRecords](images/DFACTS_OPF_AreaRecords.jpg)

D-FACTS devices have a group of OPF-related fields. These fields are within the "OPF" folder and can be seen using the "Fields" view in the Model Explorer or from "Display/Column Options." Within this folder is the **Include in OPF** field.

On a per-line basis, D-FACTS devices are enabled by setting **Include in OPF** to **YES** and **Response** to **Fixed Xinj**. The **Fixed Xinj** response mode tells Simulator to handle setting **Xinj** for the D-FACTS on the line from an external source (in this case, the OPF) and not to respond based on the line current characteristic.

![DFACTS OPF DFACTSOPFRecords](images/DFACTS_OPF_DFACTSOPFRecords.jpg)

Cost Model

The cost is zero for D-FACTS to be off, with a slight positive cost as D-FACTS turn on. Outside of the limits, the cost is infinite. This is the out-of-limits D-FACTS cost which is $2,000,000 per unit X.

![DFACTS OPF CostModel](images/DFACTS_OPF_CostModel.jpg)

OPF Results

Results can be viewed under “OPF LP Solution Details.” The display shows the amount of change that occurred in the OPF for each D-FACTS device that responded.

![DFACTS OPF LPDetails](images/DFACTS_OPF_LPDetails.jpg)

---

<a id="switched-shunt-display"></a>

## Switched Shunt Display

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Switched Shunt Display identifies all [switched shunt](06-object-properties-edit-mode-part3.md#switched-shunt-information) devices in the case. Switched shunts are used in power systems either to inject additional Mvar into the system (capacitive shunts) or to absorb excess reactive power (inductive shunts). They may also be used to regulate bus voltage within some specified range.

The Switched Shunt Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) of its associated switched shunts. You can find a specific switched shunt using its bus name or number, and you can learn more about a particular shunt’s terminal bus by looking at the [Bus View](08-view-case-data-tools.md#bus-view-display). When in Edit Mode, you can insert a new shunt into the case or delete an existing shunt. You can also sort the switched shunt information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Load Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To call up the Switched Shunt Display, select **Network \> Switched Shunts** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The Switched Shunt Display contains the following fields by default:

Number, Name

Number and name of terminal bus to which the switched shunt is attached. Multiple switched shunts are allowed at a bus and are allowed to have a Control Mode that is not fixed.

ID

Unique identifier for the switched shunt device used in conjunction with its bus identifier to fully identify the switched shunt.

Reg Bus Num

Number of the bus whose voltage is regulated by the switched shunt.

Status

The service status of the switched shunt.

Status Branch Added in Version 20

Line shunts can be modeled as controllable switched shunts by linking their status to the status of a branch. The Status Branch field specifies a branch whose status will affect the status of a switched shunt. If specified, a switched shunt can only be closed if is has a status of closed and its Status Branch also has a status of closed. If the Status Branch has a status of open, the switched shunt will also have a status of open.

To update this field, select the dialog button that appears to the far right of the cell. This will open a dialog that allows the selection of the associated branch.

Control Mode

Control Mode for the switched shunt. A switched shunt may operate either as: *Fixed*, *Discrete*, *Continuous*, *Bus Shunt*, or *SVC*.

See the [Switched Shunt Control](#switched-shunt-control) topic for more information on how switched shunt output is automatically adjusted during power flow solutions.

Regulates

Can be set to regulate bus voltage, generator Mvar, wind generator Mvar output, or custom control that sets the output of the switched shunt based on the result of a Model Expression.

Actual Mvar

The reactive power currently supplied by the switched shunt.

Volt High

Per unit high-voltage limit for the regulation range. It is important for discrete shunt control that Volt High exceed Volt Low by a nontrivial amount; otherwise, the output of the shunt may oscillate during the power flow solution.

Volt Low

Per unit low-voltage limit for the regulation range.

Reg Volt

Actual per unit voltage at the regulated bus. When Control Mode is either *Discrete* or *Continuous*, this voltage should be between Volt Low and Volt High.

Deviation

Deviation of the regulated bus’ actual per unit voltage from the desired regulation voltage. If the actual voltage is within the regulation range, this field is zero. If the voltage is greater than Volt High, the deviation is positive. It is negative if the actual voltage is less than Volt Low.

Nominal Mvar

The Nominal Mvar field gives the initial amount of reactive power the device would supply (in Mvars) if its terminal voltage were 1.0 per unit.

Max Mvar, Min Mvar

The maximum and minimum Mvar range for the switched shunt.

---

<a id="switched-shunt-control"></a>

## Switched Shunt Control

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Switched shunt control parameters can be set from the Switched Shunt Information dialog in either [Edit](06-object-properties-edit-mode-part3.md#switched-shunt-information) mode or [Run](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) mode. They can also be set from the [Switched Shunt Display](#switched-shunt-display).

Parameters (page on the Switched Shunt Information dialog)

Control Mode

Determines whether the switched shunt has a fixed value, or whether the amount of reactive power supplied by the device changes either in discrete steps or continuously in order to maintain its regulated value within the regulation range specified in the **Control Regulation Settings**. This field can be changed. However, for a switched shunt to be used for automatic control, the following fields must be set correctly:

1.  The **Control Mode** field must be set to either *Discrete*, *Continuous,* or *SVC* and the shunt must not be controlled by an SVC. If a shunt is being controlled by an SVC but the SVC is currently not on control, the shunt will be controlled based on its own control mode.
2.  The corresponding area's **Auto Shunts** property must be true
3.  The case-wide **Disable Switched Shunt Control** option, which can be set on the **Power Flow Solution tab** of the [Simulator Options dialog](10-power-flow-solution-and-options-part1.md#simulator-options) must not be checked. If the Control Mode is *SVC*, the case-wide option **Disable SVC Control** also found on the Power Flow Solution tab of the Simulator Options dialog must not be checked.
4.  The **Auto Control** option for the switched shunt must be true

**Note: Automatic control of switched shunts is disabled if the regulation high value is not greater than the low value; they should not be equal unless in continuous mode.**

Note the additional control mode called *Bus Shunt (Fixed)*. This is analogous to the shunt MW and MVAR values that can also be stored at the bus level. The difference is that bus shunts stored directly with the bus cannot be turned on and off in the load flow; rather they are always included in the load flow solution. Bus shunts that are represented as switched shunt objects on *Bus Shunt* control, however, are mathematically exactly the same and can be turned on or off. The reason for the differentiation of the *Bus Shunt* versus normal *Fixed* control is that the *Bus Shunt* control type is intended to identify the difference between a bus shunt and a switched shunt that MAY have controllability, but is currently turned of off control by being set to a Fixed value.

*SVC* control mode is intended to simulate controlled VAR devices with one continuous or discrete element that can control up to 8 fixed shunts (these shunts do not have to have a control mode that is fixed but they are treated as fixed as long as they are being controlled by an SVC). Information about these options can be found in the [SVC Control Mode](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode).

Multiple shunts at the same bus may have a control mode other than *Fixed* or *Bus Shunt (Fixed)*. More information about how multiple shunts coordinate control when regulating the same bus can be found in the **Switched Shunt Control Coordination** section below.

Control Regulation Settings

Voltage Regulation

When the switched shunt is on automatic control, its reactive power is changed in discrete steps or continuously to keep the voltage at the regulated bus within the per unit voltage range defined by **High Value** and the **Low Value**.

In the case of discrete control, the amount of reactive power supplied by this device changes in discrete amounts, thus the High Value should be greater than the Low Value. The necessary voltage range depends upon the size of the switched shunt blocks. In addition to a voltage range for discrete control, a specific **Target Value** can be specified as well. The target voltage will try to be met, either approximately under discrete control, or exactly under continuous control (either true continuous or discrete with a continuous shunt correction element.) The number of the regulated bus is shown in the **Reg. Bus \#** field.

Generator Mvar Regulation

This option allows switched shunts to control generator Mvar output to better enable full var range inside the [inner power flow loop](10-power-flow-solution-and-options-part2.md#solving-the-power-flow). During the first inner power flow loop, generator var limit checking is disabled for generators whose Mvar output is controlled by switched shunts. This will enable the use of the full reactive range of the switched shunts before generators hit their reactive limits. This corrects a problem in which the power flow fails to solve because generators are at their Mvar limits even though there is still reactive support available from switched shunts.

The **High Value** and **Low Value** specify the Mvar regulation range which limits the total Mvar output of all generators controlling the specified **Reg. Bus \#**. If the regulated value is outside of the regulation range, the switched shunt will attempt to set the regulated value to the specified **Target Value**.

Custom Control

This option allows switched shunts output to be tied to the results of a Model Expression. It is intended for a Model Expression tied to the MW Output of a single or multiple generators. Otherwise it could lead to wrong solutions if used incorrectly.

Wind Mvar

This option allows switched shunts to control the Mvar output of generators that are on AVR control and are operating with a [Wind Control Mode](06-object-properties-edit-mode-part1.md#power-and-voltage-control) of either *Constant Power Factor* or *Follow Min Mvar Capability Curve*. This control type works to control the sum of the Mvar injection for generators on valid Wind Control that are regulating the specified **Reg. Bus \#** plus the output of the controlling switched shunt plus any other switched shunts connected to the same bus as the controlling switched shunt. The allowed range of the Mvar injection sum is specified by the **High Value** and **Low Value**. If the Mvar injection sum is outside of the regulation range, the switched shunt will attempt to set the Mvar injection sum to the specified **Target Value**.

Var Regulation Sharing

Determines the priority for how a shunt should operate within its control group. Discrete shunts are operated in the order of highest to lowest sharing value, while continuous shunts are operated in proportion to their sharing parameter. More information is provided in the **Switched Shunt Control Coordination** section below.

Reg. Bus PU Voltage to Mvar Sensitivity

This field is only available while in Run mode. This provides information about how sensitive the voltage is at the regulated bus, **Reg. Bus \#**, to a Mvar change at the switched shunt. This field gives an indication if the shunt can be effective in controlling within the desired regulation range.

Switched Shunt Blocks

The amount of shunt reactive power (susceptance) is specified in the Switched Shunt Block field. The columns in this field correspond to different blocks of reactive power. The first row indicates the number of steps in each block, and the second row gives the amount of nominal Mvars per step (assuming 1.0 per unit voltage). You may model both capacitors and reactors. The reactors should be specified first, in the order in which they are switched in, followed by the capacitors, again in the order they are switched in. The sign convention is such that capacitors are positive and reactors negative. Shunt blocks are switched in order from left to right.

Status Branch Added in Version 20

Line shunts can be modeled as controllable switched shunts by linking their status to the status of a branch. The Status Branch field specifies a branch whose status will affect the status of a switched shunt. If specified, a switched shunt can only be closed if is has a status of closed and its Status Branch also has a status of closed. If the Status Branch has a status of open, the switched shunt will also have a status of open.

Control Options: Advanced Options (page on the Switched Shunt Information dialog)

Single Largest Step

This option only applies when a switched shunt is set on discrete control. If checked the switched shunt will switch in EITHER all of the available reactor blocks OR all of the capacitor blocks at once when the voltage falls outside the given range. Whether the reactor or capacitor blocks switch is determined by which limit is violated. A switched shunt with this option checked will only switch ONCE during a load flow solution, and then remains fixed at the new output for the remainder of the same solution calculation.

Allow switching in the inner power flow loop

This option is available for individual discrete shunts only. If this option is set, discrete shunts are treated as continuous in the [inner power flow loop](10-power-flow-solution-and-options-part2.md#solving-the-power-flow). This means that they are treated as PV buses in the inner power flow loop. After the first inner power flow loop, the shunt nominal Mvar setting is rounded to positive infinity to the next discrete step. If any shunts exist that are allowed to switch in the inner power flow loop, the inner power flow loop is repeated again with the shunts being treated as discrete in the subsequent inner power flow loop. Shunts that are allowed to switch in the inner power flow loop will only switch if the global option to **Disable Treating Continuous SSs as PV Buses** is not checked.

Shunts that are allowed to switch in the inner power flow loop must not be part of a switched shunt control group (see **Switched Shunt Control Coordination** section below). This means that a particular shunt can be the ONLY shunt regulating its regulated bus and only one shunt at the shunt's terminal bus can be on control.

Use Continuous Element

If this option is checked, then Simulator will use a continuous element to fine-tune a discrete controlled switched shunt by injecting or absorbing additional MVARs to try and obtain the target voltage of the controlled bus.

Minimum and Maximum Susceptance

The minimum and maximum susceptance range for the continuous correction element.

Use High Target Voltage 

Check this box to use the target value specified in the **High Target Value** edit box when the regulated point goes above the High Value. This option can be used when regulating either voltage or Mvar. This will give a different target value if the regulated value goes out of range on the high end than the low end. If the regulated value goes out of range on the low end, the original Target Value on the Parameters page will be used. If this box is unchecked, only the target value on the Parameters page will be used, whether the violation is high or low.

Switched Shunt Control Coordination

Multiple switched shunts may regulate the same bus. When this occurs, control groups are formed internally in Simulator to share the control amongst all of the switched shunts in the group. A control group is determined based on switched shunts that regulate the same bus or buses that are the same due to being connected via very low impedance branches (X \<= 0.0002 pu). This grouping of buses can be referred to as a ZBR group. Only shunts that are on either discrete or continuous control will be included in control groups.

There is a requirement that all of the switched shunts in a control group be contained within the same ZBR group. If there are multiple shunts that control the same bus, multiple control groups will be created if these shunts are contained in different ZBR groups. Within a ZBR group, only one control group can exist, i.e. all switched shunts in the same ZBR group must regulate the same bus. If multiple control groups exist within a ZBR group, automatic control will be turned off for all of the control groups within that ZBR group. All switched shunts within the same control group must also have the same regulation type, e.g. Voltage, Generator Mvar, or Wind Mvar. If not, automatic control will be turned off for the control group.

The total desired Mvar output for the control group is divided among the shunts in the control group by first assigning Mvar output to all discrete shunts in the order of highest **Var Regulation Sharing** to lowest. When specifying the order, all values of **Var Regulation Sharing** are acceptable whether they be positive, negative, or zero. The shunt with the highest priority will have its Mvar output set to the remaining desired amount until it hits either its low or high limit. If there is any remaining desired Mvar amount, the shunt with the next highest **Var Regulation Sharing** is then set. This is continued until there are no more discrete shunts with available Mvar output or the total desired Mvar output for the group has been met. If after all discrete shunts have been processed and the total desired Mvar output has not been met, the remaining desired Mvar is proportioned to the continuous shunts based on their **Var Regulation Sharing**. In this process the **Var Regulation Sharing** acts as a participation factor, and only values greater than zero will cause a continuous shunt to be set to an output other than zero. If continuous shunts hit limits during this process, their remaining proportion will be distributed to the other shunts in the group that are not already at limits.

Within a control group, the output of individual shunts will either be all reactive or all capacitive based on the total desired Mvar amount, i.e. if the total desired Mvar output is capacitive only capacitive blocks will be used.

Shunts that are allowed to switch in the inner power flow loop, i.e. continuous shunts or discrete shunts that are allowed to switch in the inner power flow loop, cannot be part of a switched shunt control group. This means that a particular shunt can be the ONLY shunt regulating its regulated bus and only one shunt at the shunt's terminal bus can be on control.

Closing Breakers to Energize Switched Shunts

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), the **Close Breakers to Energize Switched Shunts** option can be found on the Simulator Options dialog on the [Power Flow Solution Common Options page](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options). Using this option will attempt to close breakers in order to energize switched shunts and allow them to actively be on control. Only breakers will be closed for switched shunts that are on either discrete or continuous control and are needed to meet the total desired Mvar output of the control group or regulated value of the individual shunt if the shunt is not part of a group.

When selecting which breakers can be closed to energize a particular switched shunt, breakers are only selected if in the process of closing them they would ONLY energize the particular switched shunt. Breakers that would energize additional devices will not be selected as valid for energizing the shunt. If no appropriate breakers can be found, a switched shunt will remain de-energized.

Branches with **Branch Device Type** of *Breaker* and *Load Break Disconnect* are included when searching for switching devices to energize switched shunts. *Disconnects* are not included.

See the [Close Breakers Overview](24-contingency-element-dialog.md#contingency-element-close-breakers) topic for more information on how the close with breakers process works.

Voltage Control Groups Added in Version 19

Switched shunts can be assigned to a voltage control group. Each voltage control group has two fields

<table>
<tbody>
<tr class="odd">
<td><p>Voltage Control</p>
<p>Group Field</p></td>
<td><p>Description of the Field</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>The name of the control group which will be used to refer to it from the switched shunt records.</p></td>
</tr>
<tr class="odd">
<td><p>Status</p>
<p> </p>
<p> </p>
<p> </p></td>
<td><p>This field determines how switched shunt control will behave for this group.</p>
<p><strong>ON</strong> : Normal behavior where the Control Group acts as described above as long as the global options for moving shunts is enabled.</p>
<p><strong>OFF</strong> : Means that the control group is ignored and the individual shunts in the group revert back to their own individual control behavior</p>
<p><strong>FORCEON</strong> : Ignore the global option (or Area record option) to disable switched shunt control and always force control enabled for this group. The <strong>FORCEON</strong> status makes it easy for the user to disable switched shunt control globally in the contingency analysis tool and then override this disabling by setting the status to <strong>FORCEON</strong> for the Voltage Control Group.</p></td>
</tr>
</tbody>
</table>

There will also be a new field added for a switched shunt object called Voltage Control Group. A switched shunt will only be permitted to belong to one voltage control group, but it may also not have a voltage control group assigned. A switched shunt without a Voltage Control Group will simply obey the default behavior and will behave the same as shunts have always behaved in power flow contingency analysis tools.

Within power flow solution software, discrete capacitor switching is already modeled outside of the internal solution of the power flow equations in the [controller loop](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) (: Green Loop). This is where switched shunt control is implemented.

When voltage control groups are present, the following process is done.

1.  Process shunts in each “Voltage Control Group” as follows
    1.  Determine the switched shunt that has the largest deviation below Vlow (call this shunt “LowShunt”)
    2.  Determine the switched shunt that has the largest deviation above Vhigh (call this shunt “HighShunt”)
    3.  Measure largest deviation in kV not per unit (thus regulated buses with a higher nominal voltage have a higher precedence)
    4.  Only switched shunts that are marked as Control Mode = Discrete participate in these control groups. Any marked as Continuous, SVC, Fixed, or BusShunt will be ignored and will not switch at all (including in Step 2 below)
    5.  If the terminal bus of the switched shunt or the regulated bus of the switched shunt is being regulated by a generator or a generator that is on AVR control is connected to the terminal bus of the switched shunt , that shunt will be ignored
    6.  If LowShunt was found, then move that switch shunt UP by one step  
        Else if HighShunt was found move this shunt DOWN by one step
2.  Once all voltage control groups are processed simply perform the rest of the switched shunt as has always been done, but ensure we don’t move any shunts that are part of a Voltage Control Group.

Note you can use the **FORCEON** feature of the Voltage Control Group to force shunts on control even when all of the global options to disable shunts are chosen.

---

<a id="interface-display"></a>

## Interface Display

*Source: [`Content/MainDocumentation_HTML/Interface_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Interface Display is used to show the net real power (MW) flow on a group consisting of one or more of the following devices: 1) transmission lines (AC and DC) and/or transformers, 2) total tie-lines between two adjacent areas, 3) total tie-lines between two adjacent zones, 4) Generators and Loads, 5) Injection Groups, 6) multi-section lines, 7) other interfaces and 8) Contingency Actions . Interface information is useful because secure power system operation often requires that the flow on such groups be less than some limit value. For example, interface information could be used as "proxies" for other types of security constraints, such as voltage or transient stability limitations. Another major potential use for interfaces is in the [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) solution to monitor flows on groups of devices, such as a set of transmission lines, generation leaving a plant, load demanded in a certain region, etc. Interface information can also be extremely useful for summarizing the flows occurring on a large network. Interface flows can be monitored using the [Limit Monitoring Settings Display](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog).

The Interface Display presents more detailed information for each interface that has been defined for the case. The Interface Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) of its associated interfaces. The local menu also affords the opportunity to insert new interface definitions either singly (**Insert**) or as a group ([Automatic Insertion](07-object-properties-run-mode-and-general-part2.md#automatically-inserting-interfaces-in-case)) into the model or to delete existing ones. In addition, PowerWorld has also added options for reading NERC flowgate files ([Load NERC Flowgates](12-building-onelines-branches-and-devices.md#loading-nerc-flowgates)) and writing NERC flowgate files ([Save NERC Flowgates](12-building-onelines-branches-and-devices.md#saving-nerc-flowgates)) to the local menu.

You can sort the interface information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Interface Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the interface display, select **Aggregations \> Interfaces** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

Interface information can be saved in the "\*.aux" auxiliary file format. See [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) for details.

The interface Display is divided into two tabs: **Interface** and **Interface Elements**.

**Interface** **Elements** **Tab**

The **Interfaces Elements tab** has a list of tabs which lists each types of element that can belong to an interface. There is a check-box below in the middle of the display which allows you to **Only show elements that belong to at least one interface**. As you select an element in the top half of the display, the bottom half of the display will list each interface which contains the selected element. Again, these provide a nice way to look through the elements that make up each interface.

**Interface Tab**

The **Interfaces tab** has a list of interfaces at the top of the display. When on the Interface tab, in the bottom half of the tab is a set of subtabs which display all the elements of the presently selected interface from the top half of the display. This set of sub tabs starts with the **Elements** tab which lists all the elements of the interface regardless of the type of element. The remainder of the tabs each lists the interface elements of a specific type of interface element such as Branches, Branch Open/Close, DC Lines, Generators, Loads, Injection Groups, Multi-Section Lines and other interfaces. These subtabs provide a nice way to look through the elements that make up each interface. The top half of the Interface display contains the following fields:

Number

Numeric identifier for the interface.

Name

Alphanumeric identifier for the interface (24 characters maximum).

Interface MW

Current MW flow on the interface. This flow is the sum total of the Base MW Flow and the Contingent MW Flow.

MW Limit

Current rating for the interface in MW.

Percent

The actual MW flow on the interface as a percentage of the MW limit.

Monitor Direction

The current direction in which the MW flow is being monitored. The possibilities are From - To or To - From.

Monitor Both

Toggle this field to Yes in order to monitor the flow on the interface in both directions, instead of a single direction as designated by the Monitor Direction field.

Lim MW A, Lim MW B, Lim MW C

These three fields display the values of the three possible limits for the interface.

Has Contingency

This is a Yes or No field that will be set to Yes if any of the elements making up part of the interface are at a device limit.

Contingent MW Flow

If the interface defined contains a contingency action, the Contingent MW Flow is the approximated flow amount that would be added to the interface should the contingency occur.

Base MW Flow

The base MW flow is the flow on the interface prior to any considered contingency elements.

---

<a id="nomogram-display"></a>

## Nomogram Display

*Source: [`Content/MainDocumentation_HTML/Nomogram_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Nomogram_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Nomogram Display is used to modify and create Nomogram definitions. Nomograms are combinations of two [interfaces](#interface-display) for monitoring combined flows on the interfaces concurrently. These Nomogram interfaces will have a limit definition that defines a region of allowed flow on the interfaces, and can be monitored in many tools in Simulator as potential constraints, such as the contingency analysis reporting of interface violations. Another major potential use for nomograms is in the [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) solution to monitor the flow on a pair of interfaces. Nomogram information can also be extremely useful for summarizing the flows on a pair of interfaces whose operation and allowed flow are closely tied together. Nomogram flows can be monitored using the Limit Monitoring Settings Display.

The Nomogram Display presents more detailed information for each nomogram that has been defined for the case. The Nomogram Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) of its associated nomograms.

You can sort the nomogram information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Interface Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the interface display, select **Aggregations \> Nomograms** in the Model Explorer.

Nomogram information can be saved in the "\*.aux" auxiliary file format. See [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) for details.

The Nomogram display contains the following fields:

Name

Alphanumeric identifier for the nomogram.

Int A Flow

Current MW flow on the first interface of the interface pair forming the nomogram. This flow is the sum total of the Base MW Flow and the Contingent MW Flow.

Int B Flow

Current MW flow on the second interface of the interface pair forming the nomogram. This flow is the sum total of the Base MW Flow and the Contingent MW Flow.

% Limit, Max Nomo-interface

The actual MW flow on the nomogram as a percentage of the combined nomogram limit.

Monitor

Indicates whether or not the nomogram should be monitored either for violations or as a constraint in the [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview).

Limit Group

The name of the limit group the nomogram is a member of for [limit monitoring](18-general-tools.md#limit-monitoring-settings).

---

<a id="bus-pair-display"></a>

## Bus Pair Display

*Source: [`Content/MainDocumentation_HTML/BusPair_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/BusPair_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Added in Version 20

The Bus Pair Display is used to show the angle difference between two buses in the system.

Bus Pair information is useful because secure power system operation some times requires that the angle difference between two buses not become too large. For example, bus pair information could be used as "proxies" for other types of security constraints, such as voltage or transient stability limitations. Bus Pair information can also be extremely useful for summarizing the angle differences occurring on a large network. Bus Pairs can be monitored using the [Limit Monitoring Settings Display](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog).

The Bus Pair Display presents more detailed information for each bus pair that has been defined for the case. The Bus Pair Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) of its associated bus pairs. The local menu also affords the opportunity to insert new bus pair definitions into the model or to delete existing ones.

You can sort the bus pair information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Bus Pair Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show the Bus Pair display, select **Aggregations \> Bus Pairs** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

Bus Pair information can be saved in the "\*.aux" auxiliary file format. See [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) for details.

The fields associated with a bus pair are as follows.

Name

An alphanumeric identifier for the Bus Pair. This is the key field for the object.

BusNumFrom, BusNumTo

Bus number for the From and To bus of the Bus Pair.

BusFrom, BusTo

Object ID String for the From and To bus of the Bus Pair.

Description

Text description of what the Bus Pair is which is informational

Angle

The present angle difference equal to the Angle at the From Bus minus the Angle at the To Bus (in degrees)

LimitAngleUsed

This is Angle limit which is presently active. It will be either LimitAngleA, LimitAngleB, LimitAngleC, or LimitAngleD depending on the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog).

LimitAngleUsedCTG

This is the Angle limit which would be active during a contingency.

Monitor

Set to YES to allow this bus pair to be monitored. Set to NO to always ignore violations of this Bus Pair angle limit.

LimitSet

Specify the name of the LimitSet to which this bus pair belongs.

LimitAngleA..LimitAngleD

Bus pairs may have 4 separate limits defined. Only 2 will be active (a normal and contingency rating). The choice of which rating is active is controlled by the Limit Set to which the Bus Pair belongs.

---

<a id="injection-group-display"></a>

## Injection Group Display

*Source: [`Content/MainDocumentation_HTML/injection_group_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/injection_group_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Injection Group Records Display presents data describing each injection group in the case. This display is available by selecting **Aggregations \> Injection Groups** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). This display is organized into two tabs with various sections available under each of the tabs. The tabs and sections provide options for displaying information about injection groups and their associated participation points in a manner in which it is most useful to the user. Injection groups can be displayed with their associated participation points or participation points can be displayed with the injection group to which they belong.

Injection Groups Tab

This tab is organized into a top and bottom section. The top section contains the Injection Groups [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) that lists all of the defined injection groups. The [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) is available by right-clicking on the display and contains options available for most case information displays as well as the option to **Show Dialog** to view the [Injection Group Dialog](#injection-group-dialog).

By default, the Injection Groups Case Information Display contains the following fields:

Name

The name of the injection group. To change the name of an injection group, simply type a new name in the corresponding cell.

Number of Gens

Identifies the number of generators contained in the injection group.

% MW Gen ParFac

Indicates the degree to which generators will contribute to the MW output of the injection group relative to loads. An injection group that has a % MW Gen ParFac value of 100% receives all of its output from generator points; an injection group that has a % MW Gen ParFac of 50% and a % MW Load ParFac of 50% receives equal MW contributions from its constituent loads and generators.

Number of Loads

Identifies the number of loads contained in the injection group.

% MW Load ParFac

Indicates the degree to which MW loads will contribute to the MW output of the injection group relative to generators. An injection group that has a % MW Load ParFac value of 100% receives all of its output from load points; an injection group that has a % MW Load ParFac of 50% and a % MW Gen ParFac of 50% receives equal MW contributions from its constituent loads and generators.

% Mvar Load ParFac

Indicates the degree to which Mvar loads will contribute to the Mvar output of the injection group relative to switched shunts. An injection group that has a % Mvar Load ParFac value of 100% receives all of its Mvar output from load points; an injection group that has a % Mvar Load ParFac of 50% and a % Mvar Shunt ParFac of 50% receives equal Mvar contributions from its constituent loads and switched shunts.

Number of Shunts

Identifies the number of switched shunts contained in the injection group.

% Mvar Shunt ParFac

Indicates the degree to which switched shunts will contribute to the Mvar output of the injection group relative to Mvar loads. An injection group that has a % Mvar Shunt ParFac value of 100% receives all of its Mvar output from switched shunt points; an injection group that has a % Mvar Shunt ParFac of 50% and a % Mvar Load ParFac of 50% receives equal Mvar contributions from its constituent loads and switched shunts.

Total MW Injection

Indicates the current total MW injection of all elements in the injection group.

Total Mvar Injection

Indicates the current total Mvar injection of all elements in the injection group.

The bottom section contains additional tabs: **Participation Points (All), Generators, Loads, Switched Shunts, Injection Groups** and **Buses**. These tabs contain tables, which are variations of the [Participation Point Records Display](#participation-point-records-display), that list all of the individual participation points for the selected injection group by element type. Participation points can be added, deleted, or modified for the selected injection group from any of the tables on these tabs. The **Participation Points (All)** table lists only the fields that are relevant for defining participation points while the specific element tables also make available the fields that are specific to that element type.

The **Generators, Loads, Switched Shunts, Injection Groups** and **Buses** tabs have the option to **Show points that are contained by other injection group points**. This option is only relevant if an injection group contains a participation point that is another injection group. When this option is checked, the individual participation points that are contained in the injection group point will also be displayed. The **Contained by** field will list the name of the injection group that contains a particular participation point. When this option is not checked, the points displayed will be points that are contained in the selected injection group only and no additional information will be provided about the points contained inside any injection group points belonging to the selected injection group. If the **Contained by** field is empty, this means that the participation point is explicitly defined with the selected injection group and does not belong to it through an injection group point.

Participation Points Tab

This tab is organized into a top and bottom section. The top section contains tabs for **Generators, Loads, Switched Shunts, Injection Groups**and **Buses**. Tables on these tabs will list power system elements of each particular type. If the option to **Only show elements that belong to at least one injection group** is not checked, then all elements of each type in the case will be listed on one of these tabs. If this option is checked, then only those elements that belong to an injection group will be listed. The tables on these tabs are [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) for each particular type and have the full functionality of case information displays.

The bottom section is an Injection Groups Case Information Display. When an element from one of the tables in the top section of the tab is selected, this table will be populated with the list of injection groups to which the selected element belongs.

Injection Group Specific Scaling Options

Various tools can use injection groups to scale the system or ramp transfers between injection groups: [Scaling](18-general-tools.md#scaling), [PV](29-pv-and-qv-curves.md#injection-group-ramping-options), [ATC](32-available-transfer-capability.md#advanced-options), [Time Step Simulation](26-time-step-simulation-part1.md#input-page), [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc), and [Injection Group Area Slack](07-object-properties-run-mode-and-general-part2.md#area-mw-control-options). These tools have options that specify how injection groups should be scaled. There are also options that can be specified with each injection group that dictate how that particular injection group should be scaled and these options override those with the particular tools. These injection group specific options can be accessed from the Injection Group Display through the list of available fields. There is a Scale folder with all relevant fields. The **Use Scale Options** field must be set to *YES* for the injection group specific options to be used. The different tools that use injection groups have different options on how injection groups should be scaled, only the injection group specific options relevant for a particular tool will be used.

---

<a id="injection-group-dialog"></a>

## Injection Group Dialog

*Source: [`Content/MainDocumentation_HTML/injection_group_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/injection_group_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Injection Group Dialog provides information about injection groups and allows their modification. Specifically, the Injection Group Dialog lists the number of generators, loads, and switched shunts contained in the group and the percentage contribution of generators, loads, and switched shunts to the injection group’s output. The Injection Group Dialog also houses the Participation Points Records display, from which points can be added and deleted from the injection group’s list of participants and the various attributes of the points can be changed.

To view the Injection Group Dialog for a particular injection group, open the [Injection Group Display](#injection-group-display) by selecting **Aggregations \> Injection Groups** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). Find the injection group of interest in the Injection Groups Case Information Display and right-click on it. Then select **Show Dialog** from the resulting local menu.

The Injection Group Dialog contains the following fields and controls:

Name

Identifies the injection group whose information is currently displayed. Selecting a different name from this dropdown box will display information for another injection group.

New, Delete

To insert a new injection group from this dialog, press **New**, and supply the name for the new injection group. To delete the injection group that is currently being shown, click **Delete**.

Save

Changes made to injection groups through the Injection Group Dialog are not immediately saved with the power system case. This allows the option of canceling any changes without impacting the case. Click the **Save** button to store any updates with the case.

Rename

Change the name of the currently selected injection group.

\# Gens

Displays the number of generators contained in the injection group.

\# Loads

Displays the number of loads contained in the injection group.

\# Shunts

Displays the number of switched shunts contained in the injection group.

% MW Gen Part., % MW Load Part., % MVR Load Part., % MVR Shunt Part.

Displays the relative contributions of generators, loads, and switched shunts to the output of the injection group.

OK, Cancel

Changes made to the injection groups through the Injection Group Dialog are not immediately saved with the power system case. This allows the option of canceling any changes without impacting the case. Click **Cancel** to close the dialog without saving the changes. Click **OK** to close the dialog and save the changes.

Participation Points

The tab on the bottom of the Injection Group Dialog lists the points that make up the injection group. This display is called the [Participation Point Records Display](#participation-point-records-display). By right-clicking on this display, points can be added and deleted from the injection group. Properties of specific points can be changed by entering changes directly in the table. The **Insert Points** button will open the [Add Participation Points Dialog](07-object-properties-run-mode-and-general-part2.md#add-participation-points-dialog) that can also be used for modifying the points.

---

<a id="participation-point-records-display"></a>

## Participation Point Records Display

*Source: [`Content/MainDocumentation_HTML/Participation_Point_Records_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Participation_Point_Records_Display.htm)*

The Participation Point Records Display shows information about the points that comprise a particular injection group. This display can be accessed for a particular injection group from the [Injection Group dialog](#injection-group-dialog) or the [Injection Group Display](#injection-group-display).

The Participation Point Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which participation points can be deleted or added to the injection group through the [Add Participation Points dialog](07-object-properties-run-mode-and-general-part2.md#add-participation-points-dialog). Selecting **Insert** from the local menu will open the Add Participation Points dialog that will allow the addition, deletion, and modification of participation points in the injection group.

The Participation Point Records Display shows the following fields by default:

Point Type

Every participation point is a generator (GEN), load (LOAD), switched shunt (SHUNT), bus (BUS), or injection group (INJECTIONGROUP).

Bus participation points will be ignored in tools that actually make system changes. These include [Scaling](18-general-tools.md#scaling), [PV](29-pv-and-qv-curves.md#injection-group-ramping-options), [ATC](32-available-transfer-capability.md#advanced-options), [Time Step Simulation](26-time-step-simulation-part1.md#input-page), [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc), and [Injection Group Area Slack](07-object-properties-run-mode-and-general-part2.md#area-mw-control-options). Bus participation points will be allowed in linear sensitivity calculations and [ATC calculations using only the Single Linear Step method](32-available-transfer-capability.md#single-linear-step-sl).

Number

Identifies the number of the bus to which a generator, load, or switched shunt is connected or the bus itself.

Name

Identifies the name of the bus to which a generator, load, or switched shunt is connected or the bus itself.

ID

Identifies the ID of the generator, load, or switched shunt or the name of the injection group.

AutoCalc

If the value of **AutoCalc** is *YES*, the participation factor of the point is re-calculated with every use according to the **AutoCalc Method** setting. If the value of **AutoCalc** is *NO*, the participation factor is assumed fixed at its present value.

AutoCalc Method

Indicates how the participation factor of the point should be re-calculated. This re-calculation of the point is done with every use if **AutoCalc** is *YES*. For generators, the possible values of this field are :

**SPECIFIED**  The participation factor is specified as a constant.

**MAX GEN INC  **The participation factor is calculated as the difference between the generator’s maximum MW output and its present MW output. This option will not allow negative participation factors. If the present MW output is greater than the maximum MW output, the participation factor will be zero.

**MAX GEN DEC**  The participation factor is calculated as the difference between the generator’s present MW output and its minimum MW output. This option will not allow negative participation factors. If the present MW output is less than the minimum MW output the participation factor will be zero.

**MAX GEN MW**  The participation factor is set the same as the maximum MW output of the generator.

*Field or Model Expression* The participation factor is the value of the Field or Model Expression named as the AutoCalc Method.

For loads, the **AutoCalc Method** property can assume these possible values:

**SPECIFIED**  The participation factor is specified as a constant.

**LOAD MW**  The participation factor is set the same as the size of the load in MW.

*Field or Model Expression* The participation factor is the value of the Field or Model Expression named as the AutoCalc Method.

For switched shunts, the **AutoCalc Method** property can assume these possible values:

**SPECIFIED**  The participation factor is specified as a constant.

**MAX SHUNT INC**  The participation factor is calculated as the difference between the maximum Mvar output of the switched shunt and its present nominal Mvar output.

**MAX SHUNT DEC** The participation factor is calculated as the difference between the present nominal Mvar output and the minimum Mvar output of the switched shunt.

**MAX SHUNT MVAR** The participation factor is set the same as the maximum Mvar output of the switched shunt.

*Field or Model Expression* The participation factor is the value of the Field or Model Expression named as the AutoCalc Method.

For injection groups, the **AutoCalc Method** property can assume these possible values:

**SPECIFIED**  The participation factor is specified as a constant.

*Field or Model Expression* The participation factor is the value of the Field or Model Expression named as the AutoCalc Method.

For buses, the **AutoCalc Method** property can assume these possible values:

*Field or Model Expression* The participation factor is the value of the Field or Model Expression named as the AutoCalc Method.

The **AutoCalc Method** field is important if the **ParFac** values should be updated automatically as changes are made to the case affecting the participation point object. If the **AutoCalc** field is set to *YES*, the rule defined by the **AutoCalc Method** field is used to recalculate the participation factor with every use. For example, if the **AutoCalc Method** is *MAX GEN INC* and **AutoCalc** is *YES*, the point’s participation factor will be updated to match the generator’s MW reserve every time the point is accessed.

This field is also useful if saving injection groups to an auxiliary file and using them with another case that might have a different generation dispatch or load profile. If the **AutoCalc Method** for a point is specified as *GEN MAX INC*, for example, and the point is loaded from an auxiliary file into another case, Simulator will re-calculate the point’s participation factor to match the generator’s positive MW reserve in that case if the **AutoCalc** field is set to *YES*.

When the value of the **AutoCalc Method** field is toggled, the point’s participation factor, shown in the **ParFac** field, will update to match the new definition. This happens regardless of how the **AutoCalc** field is set.

If **AutoCalc** is *NO* and the injection group is not intended to be used with any other case, then the **AutoCalc Method** field should either be ignored or set to *SPECIFIED*. When **AutoCalc** is *NO*, the **ParFac** field is enterable and can be changed.

ParFac

Indicates the participation factor of the participation point. The participation factor defines the relative contribution of the point to the total output of the injection group. The load, generation, or switched shunt change associated with each point is calculated based on the value of the participation factor, with values for points having the largest participation factors experiencing the greatest change.

The participation factor for injection group participation points indicates the relative contribution of the entire injection group to the total output of the injection group to which it belongs. The participation factors of the individual points in the injection group point further define the relative contribution of these points to the total output of the injection group. The following two injection groups provide an example of how injection group points impact the injection group to which they belong when the points are normalized for use:

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><strong>Injection Group 1</strong></td>
<td><strong>Injection Group 2</strong></td>
<td> </td>
</tr>
<tr class="even">
<td> </td>
<td><p>Gen 1, ParFac = 50</p>
<p>Gen 2, ParFac = 30</p>
<p>InjectionGroup 2, ParFac = 20</p></td>
<td><p>Gen 5, ParFac = 40</p>
<p>Load 1, ParFac = 20</p>
<p>Load 2, ParFac = 20</p></td>
<td> </td>
</tr>
<tr class="odd">
<td> </td>
<td><strong>ParFac Total = 100</strong></td>
<td> <strong>ParFac Total = 80</strong></td>
<td> </td>
</tr>
</tbody>
</table>

When Injection Group 1 is used, the participation factors are normalized so that each element provides the following contribution:

Gen 1, Normalized ParFac = 50/100 = 0.5

Gen 2, Normalized ParFac = 30/100 = 0.3

Gen 5, Normalized ParFac = 20/100 \* 40/80 = 0.1

Load 1, Normalized ParFac = 20/100 \* 20/80 = 0.05

Load 2, Normalized ParFac = 20/100 \* 20/80 = 0.05

Total Normalized = 1.0

To add points to the injection group, right-click on the Participation Point Records Display and select **Insert** from the local menu. This opens the [Add Participation Points dialog](07-object-properties-run-mode-and-general-part2.md#add-participation-points-dialog).

---

<a id="island-display"></a>

## Island Display

*Source: [`Content/MainDocumentation_HTML/Island_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Island_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Island Display presents information on the system’s islands. Users of the software do not directly create and maintain islands, but instead islands are automatically created by PowerWorld Simulator as the users changes the system. For more information about how the islands are created see the help topic on [Island Creation](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-creation).

An island consists of a group of buses that are electrically connected via ac transmission lines and transformers and thus operate in synchronism with one another. Multiple islands can be connected together via dc transmission lines. Each island requires a slack bus. All systems have at least one island, which may encompass the entire system.

The Island Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information. You can also sort the islands information by clicking on the heading of the field by which you want to sort.

To show this display select **Aggregations \> Islands** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). The display is only available in run mode.

You cannot modify any fields on this display.

The display has the following fields for each island:

Slack Bus Number, Slack Bus Name, Slack Bus Area

Number, name and area of the slack bus for the island. Each island requires at least one slack bus.

Total Buses

Total number of buses in the island.

Energized

Indicates whether the island is connected to a source of power.

Gen MW, Gen Mvar

Total real and reactive generation for the island.

Load MW, Load Mvar

Total real and reactive load for the island.

Scheduled Exports

The power scheduled to be provided by the island to other regions of the system. Because the island is isolated from the rest of the system, this export requirement is currently not met.

DC MW Exports

The power provided by the island to other regions of the system across a DC line.

---

<a id="mw-transactions-display"></a>

## MW Transactions Display

*Source: [`Content/MainDocumentation_HTML/MW_Transactions_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/MW_Transactions_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The MW Transactions Display is a quick way to view the defined base transactions between areas within the load flow case.

The **Matrix of Transactions** display is set up as a matrix of transactions, with the areas listed as both the column and row identifiers. It is important to note that the direction of the transaction is such that the area represented by the **row** is assumed the exporting area, and the area represented by the **column** is assumed the importing area. For example, if there is a 50 MW transaction from area one to area two, you will see a +50 in the matrix in row 1, column 2. However, if you look at row 2, column 1, you will see a – 50. This is because the grid is displaying the EXPORT from area two to area one, but since area two is importing, not exporting, the value is represented as negative.

Each row and column position, with the exception of the diagonal positions (it does not make sense for an area to export to itself), can be directly modified by the user in this information display. As you type a value in one of the matrix positions, Simulator automatically fills the symmetric matrix position with the negative of the value you enter. This makes for a quick and easy location for adding and removing transactions from the case.

Note that you cannot modify **Unspecified** transactions in the MW Transactions display. This makes sense, as the unspecified transactions have only one associated area. To modify unspecified transaction amounts, you must open the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information) for the area you wish to modify, and change the Unspecified transaction amount.

The **List of Transactions** is just another way of showing the transactions between areas. The List of Transactions Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, or modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#area-information) of its associated areas. You can also sort the area records by clicking on the heading of the field by which you want to sort.

Note that a special feature is available in the right-click local menu called **Clear Transactions and auto-insert tieline transactions**. By choosing this option all MW transactions in the case will be deleted, and all Unspecified MW transactions for each area will be set to zero. Then new MW transactions will be created between each pair of areas that area directly connect to one another. The amount of the new MW transactions will be set equal to the actual sum of the flow on the tielines between the connected areas.

By default, the List of Transactions display contains the following fields:

Export Area Number, Export Area Name

Exporting area number and alphanumeric identifier.

Other Area Number, Other Area Name

Importing area number and alphanumeric identifier.

MW Transfer

Value of the transfer in MW.

---

<a id="mw-transactions-information-dialog"></a>

## MW Transactions Information Dialog

*Source: [`Content/MainDocumentation_HTML/Transaction_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transaction_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transaction Dialog can be used to modify or create Base Interchange Transactions between two areas. This dialog can be opened by right-clicking in the Base Interchange table of the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#informationinterchange) and choosing Show Dialog to see an existing transaction definition, or Insert to add a new transaction.

The transaction dialog is divided into two pages of controls:

Information

Transacting Area

This is the "from" area for the transaction. For an export from this area, the transaction value will be positive. For an import into the Exporting Area, the transaction value specified would be negative. Flow out (export) of the exporting area is always considered positive.

Transaction To Area

This is the "to" area for the transaction.

Transaction ID

New in Simulator version 10 is the ability to have multiple transactions defined between the same two areas. Because of this, it is now required that transactions also have a Transaction ID.

Rename Transaction ID

If you wish to change the transaction ID for a particular transaction, enter the new value in the **Transaction ID** field, and press this button.

Switch Directions

Press this button if you wish to reverse the defined Exporter and Importer for the transaction.

Transaction MW Amount

The MW amount of the transaction being defined. This value should be positive for an export from the Exporting area to the Importing area. The value can also be entered as negative to define a transaction into the Exporting area from the Importing area.

Transaction Minimum MW

The minimum transaction amount between the two areas. This field is only enabled if the check box labeled **Transaction Dispatchable in OPF** is checked.

Transaction Maximum MW

The maximum transaction amount between the two areas. This field is only enabled if the check box labeled **Transaction Dispatchable in OPF** is checked.

Exports/Imports Transmission Charge

The cost to transfer power, in $/MWh. This adds an economic penalty for making the transfer, making the transfer less likely to take place. Half the charge is assigned to the buyer and half to the seller.

Transaction Enabled

Transaction can now be defined and either enabled or disabled. Any disabled transactions will be ignored in both a standard power flow solution and an OPF solution.

Transaction Dispatchable in OPF

Checking this box enables the transfer to be dispatched by the OPF algorithm. Dispatching the transaction makes the two areas of the transaction appear to be one area for the purpose of economically dispatching the generation in the two areas. The transaction can have a maximum and minimum transfer amount when dispatchable, and a transmission charge associated with the transaction.

Determine Price in OPF

Checking this box allows the OPF algorithm to determine the cost associated with the transfer. The cost is determined by the marginal cost of enforcing the power balance constraint for the combined areas. This is the typical way to implement a transfer if *both* areas are on OPF control. If only one of the two areas are on OPF control, then the area which is off of OPF control needs to specify a price for the transfer. This is done by explicitly defining a piecewise linear cost curve.

Piecewise Linear Transaction Cost Curve

These two curves are only enabled if the option **Transaction is Dispatchable in OPF** is checked and the option **Determine Price in OPF** is unchecked. These two curves can be defined for the purpose of assigning a price to the transfer of power between one area on OPF control and another area which is not on OPF control. Separate curves can be defined for export transactions (from the Exporter to the Importer) and import transactions. To add points to the curves, simply right-click in the grid and choose Insert from the local menu. Enter the MW value and corresponding marginal cost for the inserted breakpoint of the piecewise linear curve you are defining. To delete a point, right-click on that row in the grid and choose Delete from the local menu.

Custom

The Custom page of the Transaction dialog is simply a location to log information about the transaction in the Memo box, and to see the values (if any) stored in some of the custom fields for the transaction. To log information about the transaction, simply switch to the Custom page on the dialog, and start typing your information or comments about the transaction in the page, or enter custom values in one of the custom fields.

---

<a id="owner-data-information-display"></a>

## Owner Data Information Display

*Source: [`Content/MainDocumentation_HTML/owner_data_information_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owner_data_information_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owner Data display will display the owners sorted by owner number, and show the total number of devices, as well as a breakdown of the number of specific devices. The owner display will also summarize the total device output or demand for the owned devices, such as generator output and load demand.

You can right click on the owner grid to open the local menu, from which you can perform various actions and view an informational regarding the owner selected in the grid. Once an [owner dialog](#owner-dialog) is displayed for a particular owner, you can browse through information on all the owners.

---

<a id="owner-dialog"></a>

## Owner Dialog

*Source: [`Content/MainDocumentation_HTML/owner_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owner_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owner Dialog displays summary information about the devices designated as owned by the selected owner.

The dialog for an individual owner displays each of the elements for that owner, along with the percentage of ownership, in the device pages labeled [Buses](#owned-bus-records-display), [Loads](#owned-load-records-display), [Generators](#owned-generator-records-display), [Lines](#owned-line-records-display), and [Three-Winding Transformers](#owned-three-winding-transformer-records-display).

The dialog also contains a [memo](01-getting-started.md#memo-display) page for making comments or notes about the selected owner.

General Info

Load and Generation

The information in the Load and Generation section provides a summary of the total injections of the owned devices. This includes a total of all the load, generation, and shunt injections owned.

Summary of Owner Objects

This information section simply lists a total number of all owned devices. Note that buses and loads do not currently have fractional ownership. However, generators and transmission lines do have the capability to be partially owned by more than one owner. Therefore it is possible to see fractional ownership amounts for the number or generators or lines.

Generator Costs and OPF Results

This information provides a summary of LMP and cost information determined by running an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) solution. The information provided is determined only for devices owned by the selected owner.

---

<a id="owned-bus-records-display"></a>

## Owned Bus Records Display

*Source: [`Content/MainDocumentation_HTML/owned_bus_records_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owned_bus_records_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owned Bus Records display, found on the [Owner Dialog](#owner-dialog), is a [Bus case information display](05-case-information-displays-by-object-part1.md#bus-display) that has been modified to show the ownership information for each listed bus. In addition to the information available for viewing from the [Bus Display](05-case-information-displays-by-object-part1.md#bus-display), the Owned Bus Records Display also shows the owner number and percentage of ownership. Currently, Simulator only allows one owner per bus, so by default the ownership percent is always 100%.

---

<a id="owned-load-records-display"></a>

## Owned Load Records Display

*Source: [`Content/MainDocumentation_HTML/owned_load_records_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owned_load_records_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owned Load Records display, found on the [Owner Dialog](#owner-dialog), is a [Load case information display](05-case-information-displays-by-object-part2.md#load-display) that has been modified to show the ownership information for each listed load. In addition to the information available for viewing from the [Load Display](05-case-information-displays-by-object-part2.md#load-display), the Owned Load Records Display also shows the owner number and percentage of ownership. Currently, Simulator only allows one owner per load, so by default the ownership percentage is always 100%.

---

<a id="owned-generator-records-display"></a>

## Owned Generator Records Display

*Source: [`Content/MainDocumentation_HTML/owned_generator_records_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owned_generator_records_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owned Generator Records Display, found on the [Owner Dialog](#owner-dialog), is a [Generator case information display](05-case-information-displays-by-object-part1.md#generator-display) that has been modified to show the ownership information for each listed generator. In addition to the information available for viewing from the [Generator Display](05-case-information-displays-by-object-part1.md#generator-display), the Owned Generator Records Display also shows the owner number and percentage of ownership. Currently, Simulator allows up to four owners for one generator, with a total percentage ownership between 0 and 100%.

---

<a id="owned-line-records-display"></a>

## Owned Line Records Display

*Source: [`Content/MainDocumentation_HTML/owned_line_records_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/owned_line_records_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owned Line Records Display, found on the [Owner Dialog](#owner-dialog), is a [Line and Transformer case information display](05-case-information-displays-by-object-part2.md#line-and-transformer-display) that has been modified to show the ownership information for each listed line. In addition to the information available for viewing from the [Line and Transformer Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display), the Owned Line Records Display also shows the owner number and percentage of ownership. Currently, Simulator allows up to four owners for one transmission line, with a total percentage ownership between 0 and 100%.

---

<a id="owned-three-winding-transformer-records-display"></a>

## Owned Three-Winding Transformer Records Display

*Source: [`Content/MainDocumentation_HTML/Owned_3W_Transformer_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Owned_3W_Transformer_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Owned Three-Winding Transformer Records Display, found on the [Owner Dialog](#owner-dialog), is a [Three-Winding Transformer case information display](05-case-information-displays-by-object-part2.md#three-winding-transformer-display) that has been modified to show the ownership information for each listed transformer. In addition to the information available for viewing from the [Three-Winding Transformer Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display), the Owned Three-Winding Transformer Records Display also shows the owner number and percentage of ownership. Currently, Simulator allows up to four owners for one transformer, with a total percentage ownership between 0 and 100%.

---

<a id="jacobian-display"></a>

## Jacobian Display

*Source: [`Content/MainDocumentation_HTML/Jacobian_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Jacobian_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Jacobian display is a matrix showing the system Jacobian matrix for the currently loaded Simulator case. This display can be very useful for educational purposes. Keep in mind that for a large case, this display can contain a very large matrix. It is possible to right-click on this display and save the grid to a Matlab formatted file, or to export the grid to an Excel spreadsheet. Be aware that a Jacobian matrix from a large will often exceed the size limitations of an Excel spreadsheet.

---

<a id="ybus-display"></a>

## Ybus Display

*Source: [`Content/MainDocumentation_HTML/Ybus_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Ybus_Display.htm)*

The Ybus display (bus admittance matrix) is a matrix showing the system Ybus for the currently loaded Simulator case. This display can be very useful for educational purposes. Keep in mind that for a large case, this display can contain a very large matrix. It is possible to right-click on this display and save the grid to a Matlab formatted file, or to export the grid to an Excel spreadsheet. However, Excel does have limitations on the number of rows and columns that could quickly be exceeded with a Ybus from a large case.

---

<a id="voltage-droop-control-display"></a>

## Voltage Droop Control Display

*Source: [`Content/MainDocumentation_HTML/Voltage Droop Control Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Voltage Droop Control Display.htm)*

The Voltage Droop Control case information Display shows a list of Voltage Droop Control objects. For an explanation of the theory of Voltage Droop control see [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband). For information on defining and editing one Voltage Droop Control object see the [Voltage Droop Control with Deadband Dialog](10-power-flow-solution-and-options-part3.md#voltage-droop-control-with-deadband-dialog).

The Voltage droop Control case information display is shown in the following figure.

![VoltageDroopControlDisplay](images/VoltageDroopControlDisplay.png)

This display has three tabs which are described below.

Voltage Droop Controls Tab

This is a list of all the VoltageDroopControl objects defined in the case. You can edit the various input parameters for the QV characteristic curve direction on this tabl (Qauot, Vdeviation, Qdb, Qmax, Qmin, Vlow, Vdblow, Vdbhigh, and Vhigh just as you are able to do on the [Voltage Droop Control Dialog](https://www.powerworld.com/WebHelp/Content/Images/VoltageDroopControlDialog.png) box. There are also several convenient summary information about the Voltage Droop Control

**Validation**: This is an indication of whether the VoltageDroopControl has been configured in a valid manner. See [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband) under the heading "Detection of invalid Voltage Droop Control" for information on how a VoltageDroopControl can be invalid.

**Equation Count:** This is the number of different regulated buses that are using this VoltageDroopControl. Normally this is only 1, but you can have multiple sets of generators that share the same QV characteristic, but regulate different remote buses.

The remaining fields list next are only populated if EquationCount = 1.

**Droop Curve Mvar**: This field shows an evaluation of the QV characteristic curve at the present regulated bus voltage.

**Branch Mvar Regbus**: This is a summation of the Mvar arriving at the regulated bus on arriving branches. Arriving Branches are branches directly connected to the regulated bus which are on paths that connected the generators in the VoltageDroopControl to the regulated bus. As discussed in the [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband) topic these branches are automatically determined by PowerWorld.

**Gen Mvar Regbus**: This is a summation of the Mvar for generators that belong to the VoltageDroopControl and are connected to the RegBus directly.

**Droop Curve Mismatch**: This is showing you the control error mismatch in the VoltageDroopControl. It is equal to **Droop Curve Mvar - BranchMvarRegBus - Gen Mvar RegBus**. There may be a mismatch in the final power flow solution when generators within the VoltageDroopControl are hitting there Mvar limits.

**Reg Bus Num** and **Reg Bus**: Shows the regulated bus number of the generators that belong to this Voltage Droop Control

When you click on a row of Voltage Droop Control list the bottom left portion will show all the generators that have been assigned to that Voltage Droop Control. In addition the bottom right image of the VoltageDroopControl QV Characteristic will be updated. On the image of the QV characteristic, the Red circle denotes the present operating point.

Also in the bottom left there is also a tab for Regulated Buses which will show a list of all the regulated bus for generators assigned. Normally there will only be one bus listed there, but there can be multiple regulated buses. If a Voltage Droop control has generators assigned to it which regulated completely different regulated buses, then within the power flow solution there will be separate treatment as described in the [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband) topic.

All Generators Tab

This is a list of all the generators in the case and provides you with convenient columns to assign generators to VoltageDroopControl objects. Also as you choose rows in this list the bottom left list of Generators assigned to selection will update showing you generators assigned to the same VoltageDroopControl as the generators selected. In addition the bottom right image of the VoltageDroopControl QV Characteristic will be updated.

All Regulated Buses Tab

This is a list of all buses that are regulated by generators which belong to a VoltageDroopControl. As you click on the regulated bus the bottom right portion will show the QV characteristic for all VoltageDroopControl objects that contain generators that regulate this bus. It is possible for multiple VoltageDroopControl objects to regulate the same bus as well. In this case the QV characteristic will show two QV characteristics and two Red circles as shown in the image below.

![VoltageDroopControlDisplayMult](images/VoltageDroopControlDisplayMult.png)
