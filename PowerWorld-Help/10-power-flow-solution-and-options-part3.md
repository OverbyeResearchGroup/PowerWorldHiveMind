---
title: "Power Flow Solution and Simulator Options (Part 3 of 3)"
part: "Solving"
chapter_file: "10-power-flow-solution-and-options-part3.md"
topics: 4
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Power Flow Solution and Simulator Options (Part 3 of 3)

Power flow solution theory, simulator options, and solution and control settings.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (4)**

- [Voltage and Reactive Equation Choice](#voltage-and-reactive-equation-choice)
- [Voltage Droop Control with Deadband Dialog](#voltage-droop-control-with-deadband-dialog)
- [Area Control](#area-control)
- [Voltage Conditioning Dialog](#voltage-conditioning-dialog)

---

<a id="voltage-and-reactive-equation-choice"></a>

## Voltage and Reactive Equation Choice

*Source: [`Content/MainDocumentation_HTML/Solving The Power Flow Voltage and Reactive Equation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Solving The Power Flow Voltage and Reactive Equation.htm)*

There are many different methods of performing voltage control which impact the inner power flow equation solution in PowerWorld Simulator. [The background on the theory is described elsewhere in the help documentation](10-power-flow-solution-and-options-part1.md#power-flow-solution-theory). The following is a precedence for how PowerWorld chooses the voltage control algorithm to use. This is then followed by the various *fields* of <span class="underline">objects</span> in Simulator which impact how this is done.

Precedence for Generator Voltage Control

1.  A generator will remain at a fixed Mvar output and generally not participating in voltage control under any of the following situations
    1.  *AVR* = NO
    2.  *WindControlMode* = *Follow Min Mvar Capability*
    3.  *WindControlMode* = *Constant Power Factor*
    4.  *MvarMax* = *MvarMin*
    5.  Generator belongs to a **VoltageDroopControl** that is either not enabled or configured in an invalid manner
2.  Else If a generator is set to *UseLineDrop* = YES, then the generator will ignore all other settings and perform line drop compensation. When using line drop compensation, the only other input parameters that matter for the generator are VoltSet, Rcomp, and Xcomp.
3.  Next, if the generator has been assigned to a **VoltageDroopControl** object then it will perform [voltage droop control](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband). When performing voltage droop control, Simulator will automatically group together all generators assigned to the same VoltageDroopControl that also regulate the same bus (or buses connected by very low impedance branches that are below the ZBR Threshold and discussed in the [advanced power flow options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options)).
4.  If none of the other special options are chosen the generator will fall back to regulated the voltage at the specified RegBus including if it is a [remotely regulated bus](10-power-flow-solution-and-options-part1.md#power-flow-remote-voltage-regulation). The VoltSet and VoltSetTol are then used however as specified. Thus [Voltage Setpoint Tolerance](10-power-flow-solution-and-options-part1.md#power-flow-voltage-setpoint-tolerance) may be used.

Objects and Fields the are related to the choice of Voltage and Reactive Equation Choice

**Gen** Object

  - *VoltSet*: This is the desired voltage or setpoint (in per unit) of the regulated bus
  - *VoltSetTol*: This is the tolerance of the desired voltage. By default it is 0.0 meaning that the setpoint is enforced exactly. If non-zero then the [Voltage Setpoint Tolerance](10-power-flow-solution-and-options-part1.md#power-flow-voltage-setpoint-tolerance) equations are used.
  - *RegBus* or *RegBusNum* : This field specifies the regulated bus that is being controlled. It does not need to be the terminal bus of the generator
  - *RegBusNumUsed*: This field shows the number of what bus is actually regulated by this device. It may be different than <span class="underline">RegBusNum</span> due to zero-impedance- branch groupings that are internally determined. See description under Effect of the ZBR Threshold on Voltage Regulation for more information.
  - *AVR*: Set this field to NO and the generator's Mvar output will remain fixed at the present Mvar output. Set this to YES so that the reactive power output can be varied by the various control features.
  - *MvarMax*, *MvarMin*: This represent the maximum and minimum Mvar output of the generator. These can also be made a function of the real power MW output by defining reactive capability curves.
  - *UseCapCurve*: Set to YES to use the capability curve which can be specified by entering point for **ReactiveCapability** objects
  - *UseLineDrop* : Set to YES to set a generator to use [Line Drop compensation](10-power-flow-solution-and-options-part1.md#power-flow-line-drop-compensation).
  - *Rcomp*: this is the resistance of the line drop impedance used when *UseLineDrop* = *YES*.
  - *Xcomp*: this is the reactance of the line drop impedance used when *UseLineDrop* = *YES*.
  - *WindControlMode*: Can be set to either *None*, *Boundary Power Factor*, *Constant Power Factor*, or *Follow Min Mvar Capability*. All of these features simply impact how the *MvarMin* and *MvarMax* are calculated.
      - When set to *None* the generator simply uses the Mvar limits as normal.
      - When set to *Boundary Power Factor* then the maximum and minimum Mvar automatically follow a constant power factor line as defined by the *WindControlModePF* value.
      - When set to *Constant Power Factor*, the generator behaves as a fixed Q during the power flow solution as the Mvar output is simply a function of the MW output and the input value *WindControlModePF*. A positive value means that positive values of MW result in positive values of Mvar.
      - When set the *Follow Min Mvar Capability*, the generator behaves as a fixed Mvar output during the inner power flow solution as the Mvar output is simply a function of the MW according to the capability curves minimum Mvar outputs.
  - *WindControlModePF*: This is the power factor used in conjunction with the *WindControlMode* field.
  - *VoltageDroopControl*: This is the name of the **VoltageDroopControl** object to which the generator belongs.

**VoltageDroopControl** Objects

  - *Enabled*: Set this to YES to enable the Voltage Droop Control for generators assigned to the object. When performing voltage droop control, Simulator will *automatically* group together generators that (1) share the same **VoltageDroopControl** AND (2) regulate the same bus (or buses connected by very low impedance branches that are below the ZBR Threshold and discussed in the [advanced power flow options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options)). See the [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband) topic for more information on how this works.
  - *Qauto*: NO means to use the *Qdb*, *Qmax*, and *Qmin* values directly. If set to YES, then the values of *Qmax* and *Qmin* are automatically calculated based on the summation of generator *Qmax* and *Qmin*, and *Qdb* is assumed to be 0.0
      - If both *Qmax* and *Qmin* are the same sign, then *Qdb* is assumed to be either *Qmax* or *Qmin* depending on which value is closer to 0.0.
  - *Vdeviation*: NO means to use the values of Vlow, Vdblow, Vdbhigh, and Vhigh directly. If set to YES, then the input values of Vlow, Vdblow, Vdbhigh, and Vhigh are interpreted as deviations away from the voltage setpoints of the generators
  - *Qdb, Qmax, Qmin, Vlow, Vdblow, Vdbhigh, and Vhigh*: These fields all define the QV characteristic curve against which the reactive power and voltage are dispatched when performing voltage droop control.

Effect of the ZBR Threshold on Voltage Regulation

Sometimes when looking at the actually achieved voltage at a regulated bus (even when not using a tolerance) you will notice that the voltage is not exactly what the Voltage setpoint was. You may see 1.05021 instead of 1.05000 for instance. Because our equations are enforcing the voltage setpoint exactly, that is actually not expected behavior in general, but it may occur due to regulated buses being connected by very low impedance branches.

When performing voltage control, due to numerical stability different generators can not attempt to regulate buses extremely close to one another <span class="underline">even if the same voltage setpoint is used</span>. This will result in numerical problems and would cause trouble in a real control systems as well. To avoid this situation, PowerWorld automatically detects groups of buses that are connected by very low impedance branches. There is an [advanced power flow option](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) that specifies a ZBR threshold impedance which defines what a very low impedance branch is. By default the value is 0.0002 (so really small\!). Using this ZBR threshold PowerWorld internally builds groups of buses connected by sets of very low impedance branches. From the list of buses that are internally found, a Primary bus is automatically chosen. Any device that regulates a bus within these groups will automatically regulate this internally chosen primary bus instead. This avoids any control conflicts.

Information about choices PowerWorld is making can be seen under the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) under Solution Details\\Bus Zero-Impedance Branch Group case information display. There is a column of a bus called ZBRPrimary which shows which bus is chosen. In addition there is a bus field called ZBRNeighbors which gives a list of all the buses in the local ZBR group. Finally, on the generator case information displays there is a field for "Regulated Bus\\Number (used due to ZBR)" which is called *RegBusNumUsed* which shows the number of the primary bus related to the respective generator's regulated Bus.

---

<a id="voltage-droop-control-with-deadband-dialog"></a>

## Voltage Droop Control with Deadband Dialog

*Source: [`Content/MainDocumentation_HTML/Voltage Droop Control Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Voltage Droop Control Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The ability to use a Voltage Droop Control with Deadband was added in Simulator Version 21

Some generator voltage controls are configured such that the control signals sent to the generator are related to the measurements made at a remote bus instead of the terminal buses. An example of this is renewable generation plants such as a large solar farm or wind generation farm. In a common configuration the power system model for this situation will be as follows. The theory of this setup is described in the help topic [Power Flow: Voltage Droop Control with Deadband](10-power-flow-solution-and-options-part1.md#power-flow-voltage-droop-control-with-deadband).

To configure this type of control for a group of generators you must first create a VoltageDroopControl object and then second assign generators to this VoltageDroopControl. The VoltageDroopControl object defines the QV characteristic curve that will be followed by the group and then assigning generators to that VoltageDroopControl defines the group of generators that will participate in this control. The regulated bus of the generators defines where in the system the QV characteristic control is assigned.

Do define VoltageDroopControl objects, go to the [Model Explorer and under the Network Folder](04-model-explorer-and-case-information-part1.md#model-explorer) choose the Voltage Droop Controls to bring up the Voltage Droop Control Case Information Display. Then right-click on this case information display and choose Insert to add a new VoltageDroopControl. The dialog that appears is as follows.

![VoltageDroopControlDialog](images/VoltageDroopControlDialog.png)

The ability to specify a regulated bus with a VoltageDroopControl was added in the Version 21 build on Febraury 5, 2021.

A VoltageDroopControl object may have a Regulated Bus specified with it. If the Regulated Bus is specified, then all generators assigned to that VoltageDroopControl will automatically use this regulated bus. If the value is unspecified, Simulator will create a unique Voltage Droop Control equation for each set of generators within the voltage droop control which share a regulated bus (or buses connected by low impedance branches). To specify the Regulated Bus, click the **Choose** button or double-click on any of the edit boxes showing information about the regulated bus.

This dialog has three tabs

1.  **Generators**: This tab contains a case information display showing the generators in the case that have been assigned to belong to the VoltageDroopControl on this dialog
2.  **All Generators in Model**: This tab contains a case information display showing all the generators in the entire model. You can go to this tab to assign generators to the Voltage Droop Control
3.  **QV Characteristic**: This tab is where you define the QV characteristic curve by specifying the various per unit voltage and reactive Mvar flow thresholds along the QV characteristic curve. Enter Vlow, Vdblow, VdbHigh, VHIgh, Qmax, Qdb, and Qmin to define the curve. It may also be convenient to specify that the Qdb, Qmax, and Qmin values be automatically calculated based on the summation of generator *MvarMax* and *MvarMin*, and *Qdb* is assumed to be 0.0. (If both *Qmax* and *Qmin* are the same sign, then *Qdb* is assumed to be either *Qmax* or *Qmin* depending on which value is closer to 0.0). When automatically determine the reactive thresholds for this curve, there is no need to actually enforce those limits in the QV Characteristic curve. Instead we can just rely on the individual generators to enforce their Mvar limits. As a result the QV characteristic curve would change as depicted in the following image. When Qauto is chosen then the red line extrapolates out as shown in the green dashed line  
    ![PowerFlow VoltageDroop Curve Qauto](images/PowerFlow_VoltageDroop_Curve_Qauto.png)

---

<a id="area-control"></a>

## Area Control

*Source: [`Content/MainDocumentation_HTML/Area_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

One of the most important aspects of interconnected power system operation is the requirement that each operating area changes its total generation to match changes in the sum of its load plus losses plus power transactions with other areas. This requirement is normally met by Automatic Generation Control (AGC). The purpose of AGC is to ensure that the actual MW output of an area is equal to the scheduled MW output of the area. The AGC system accomplishes this by first calculating the Area Control Error (ACE), which is defined as

 ACE = Pactual - Pscheduled

In Simulator, Pscheduled for an area is made up of the Area’s [MW Transactions](05-case-information-displays-by-object-part3.md#mw-transactions-information-dialog) and the Area’s *Unspecified MW* *Export*. MW Transactions represent the transfer of power between two areas in the power system. This transaction is done presumably under a contract between the two areas. The advantage of using MW transactions to describe these is that it ensures that the total export of all areas is consistent: if one area is exporting 100 then another area is automatically importing that power. However, each area also specifies a value called the Unspecified MW Export which can be entered on the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#informationinterchange). The unspecified MW export represents an export of power from the area that goes to an unspecified other area. When using unspecified MW exports, it is important that the total unspecified MW exports in the system sum to zero. PowerWorld highly recommends that care be taken when using unspecified exports.

Whenever the ACE is greater than zero, it means that the area is over generating and thus needs either to decrease generation or to sell more. Likewise, whenever the ACE is less than zero, the area is under generating and thus needs either to increase generation or to buy more. AGC works to keep the ACE close to zero.

In Simulator, there are six options for implementing AGC:

No area control

The output of the generators does not change automatically. You must manually change the generation to match system load/losses/transaction variation. All change in load/losses/transaction in this area will be made up at the islands slack bus.

Participation Factor Control

The output of all the area’s generators who have their AGC field set to "YES" change automatically to drive the area control error (ACE) to zero. Each generator’s output is changed in proportion to its participation factor. Checking this option enables the **Set Factors** button on the [Area MW Control Options](07-object-properties-run-mode-and-general-part2.md#area-mw-control-options) tab of the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information), which, when pressed, opens the [Generator Participation Factors Dialog](06-object-properties-edit-mode-part1.md#generator-participation-factors). Participation Factor Control only adjusts generation when a change to the system has taken place, such as changing the amount of load in the case, or defining new area to area transactions.

In Participation Factor Control, the ACE is allocated to each AGC generator in the area in proportion to that generator’s participation factor divided by the total of the participation factors for all AGC generators in the area. A generator’s participation factor cannot be negative. By default, a generator’s participation factor equals its current MW setpoint value, but individual participation factors can be changed.

Economic Dispatch Control

The output of all AGC generators in the area changes automatically to drive the area control error (ACE) to zero. Each generator’s output is changed so that the system is dispatched economically, based on cost information entered for the generators in the case. Note that cost data is not generally included in standard load flow data. Without realistic cost data entered into Simulator, the use of the economic dispatch algorithm may not be very useful. Cost data must be obtained from another source and entered into a case in Simulator, either manually or through the use of [Simulator Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux).

With Economic Dispatch (ED) Control, Simulator tries to change the output of the area’s AGC generators economically so that the area’s operating cost is minimized. ED control recognizes that some generators are less expensive than others and tries to use the least expensive generators to the largest extent possible.

To do economic dispatch, we need to know how much it would cost to generate one more MW at a particular generator. This is known as the incremental or marginal cost. For example, for the cubic cost curve model, the incremental cost for each generator is modeled using the formula:

 li = ICi (Pgi) = ( bi + 2ci Pgi + 3di (Pgi) 2 ) \* fuelcost   $/MWH

The plot of ICi(Pgi) as a function of Pgi is know as the incremental-cost curve. The economic dispatch for a system occurs when the incremental costs for all the generators (li) are equal. This value is known as the system l (lambda) or system incremental cost. Its value tells you how much it would cost to generate one more MW for one hour. The system lambda becomes important when trying to determine whether or not an area should buy or sell power. For example, if an area can buy power for cheaper than it can generate it, it might be a good idea for the area to buy power.

Generators that are allowed to participate in economic dispatch control will have their MW limits enforced regardless of how any of the options specifying that MW limits be enforced are set.

Area Slack Bus Control

Only the output of the area’s slack bus changes automatically to drive the area control error (ACE) to zero. This type of generation control is usually only good for small disturbances to the injections and/or transactions in a case, and can often fail to find a solution when larger disturbances are examined.

Injection Group Area Slack Control

Only the Injection Group specified as the Injection Group Area Slack will change to automatically drive the area control error (ACE) to zero. This allows you to be very specific with each area as to which generation (or load) should vary to maintain ACE.

Optimal Power Flow (OPF)

The [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) option will only be available if you have the OPF add-on for PowerWorld Simulator. The OPF control is very similar to the Economic Dispatch control in that it attempts to dispatch generation to minimize costs. The additional function of the OPF is to minimize the costs while also obeying line, transformer, and interface limit constraints. This option is also not useful without realistic generator cost information, which usually must be obtained from another source and entered into Simulator to augment a load flow case.

The OPF control also relies on the cost curve in order to perform an economically optimal power flow. However, the OPF routine makes use of piecewise linear curves in its solution algorithm. This does not prevent you from entering the cost information as cubic cost models, described by the equation above. Rather Simulator’s OPF routine allows you to specify how to break up the cubic curve and model it as a piecewise linear curve for the OPF algorithm.

Generators that are allowed to participate in OPF control will have their MW limits enforced regardless of how any of the options specifying that MW limits be enforced are set.

In addition, you can also enter piecewise linear curves directly instead of the cubic cost curve models. In fact, a mixture of piecewise linear and cubic models is acceptable. For the economic dispatch routine, whichever type of model is entered will be used directly for each generator. For the OPF routine, all piecewise linear curves entered directly will be used as is, and any cubic models entered will be converted to piecewise linear curves internally during the processing of the OPF algorithm.

---

<a id="voltage-conditioning-dialog"></a>

## Voltage Conditioning Dialog

*Source: [`Content/MainDocumentation_HTML/Voltage_Conditioning_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Voltage_Conditioning_Dialog.htm)*

The Voltage Conditioning Tool and Dialog were added in Version 23. This tool is available under on the [Tools Ribbon Tab](02-simulator-ribbon.md#tools-tab-overview), on the [Power Flow Tools Ribbon Group](02-simulator-ribbon.md#simulation-control).

The Voltage Conditioning tool can be used to change the generator voltage set points in your case to approximately match various Substation or Bus voltage targets that you configure, and also move switched shunts in your case to meet these same targets. The Voltage Conditioning tool dialog is shown in the image below. The dialog is divided in the following sections.

Case Voltage Target Tab

The fundamental object for Voltage Conditioning Tool is the **CaseVoltageTarget** which is used to define the target range for voltages at the buses in the case. There can be 8 different targets specified marked as A, B, C, D, E, F, G and H. These objecsts are edited on the Case Voltage Target is described in detail below.

Case Voltage Target Tool Options (at top of the dialog)

There are a options related to how the tool is run which are defined in the **CaseVoltageTargetTool** object. These options are described in the sections below, but they can also be set at the top of the dialog under options for Impedance Threshold, Transmission Nom kV, and so on.

Target Regions Tab

Buses and Substations in the case can be assigned to a **CaseVoltageTargetRegion** object. These objects are described below, but their purpose is only to specify which target (A, B, C, D, E, F, G, or G) should be used from the **CaseVoltageTarget** object.

Substation, Bus, Shunt, and Transformer Tap Tabs

These tabs provide case information displays with default columns associated with the Voltage Conditioning tool. These specified fields are described below as well.

Perform Voltage Conditioning Button

Clicking the Perform Voltage Conditioning button will perform the process of voltage conditioning. This is described in great detail at the end of this help topic. Also clicking this button is the same as running the Auxiliary File script command `VoltageConditioning;`.

Save to AUX

Click this button to open options to save all options related to voltage conditioning to an [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux).

![Voltage Conditioning Dialog](images/Voltage_Conditioning_Dialog.png)

CaseVoltageTarget

The CaseVoltageTarget object is used to specify the target voltages for the power system. A CaseVoltageTarget can be specified either at a specific bus or at a Nominal kV level of a specific substation. Thus the primary keys for the object are unusual as both Bus and Substation are key fields, but only one of them will be entered, while the other will be blank.

**Bus**: A string that specifies the bus at which the target is given. The string may be entered either as the bus Number (primary key), Name\_NomkV (secondary key), or one of the [labels of the bus](07-object-properties-run-mode-and-general-part2.md#labels). Thus the string could be either "12345", "My Bus Name\_230.00" or "My Bus label".

**Substation**: If a Bus is not specified then the CaseVoltageTarget applies to all buses in the specified substation at the Nominal kV entered in the NomkV field.

**NomkV**: If a bus is specified, NomkV will show the Nominal kV of the bus. If the Substation is specified, Nom kV is a key field and used to determine which buses inside the substation to apply the voltage target to.

**Voltage Targets and Deadbands**: There are 8 voltage targets and also a deadbands for both up and down directions. These targets and deadbands can be specified in either PU (per unit) or in kV.

More detailed descriptions of the fields are in the following table.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Bus</p></td>
<td><p>String</p>
<p>(KEY Field)</p></td>
<td><p>A bus to which this desired voltage target applies. The identifiers used are determined by the BusIdentifier field of the CaseVoltageTargetTool object. If this is specified, then the Substation is ignored.</p></td>
</tr>
<tr class="odd">
<td><p>Substation</p></td>
<td><p>String</p>
<p>(KEY Field)</p></td>
<td><p>Substation to which this desired voltage target applies (used only if Bus is empty). The identifiers used are determined by the SubIdentifier field of the CaseVoltageTargetTool object</p></td>
</tr>
<tr class="even">
<td><p>NomkV</p></td>
<td><p>Single Float</p>
<p>(KEY Field)</p></td>
<td><p>Nominal kV of the buses inside a substation that should be considered. If the Bus field is specified however, this will return the nominal kV of the Bus and the value will not be enterable.</p></td>
</tr>
<tr class="odd">
<td><p>Description</p></td>
<td><p>String</p></td>
<td><p>An extra string for the user to describe this entry.</p></td>
</tr>
<tr class="even">
<td><p>BandUpkV</p>
<p>BandUpPU</p></td>
<td><p>Single Float</p></td>
<td><p>Voltage deviation in kV or per unit above the voltage target that is considered acceptable (must be a positive value). Internally a value is stored in per unit, so editing using the kV values will set the per unit value equal to the entered value divided by the NomkV field.</p></td>
</tr>
<tr class="odd">
<td><p>BandDownkV</p>
<p>BandDownPU</p></td>
<td><p>Single Float</p></td>
<td><p>Voltage deviation in kV or per unit below the voltage target that is considered acceptable (must be a negative value). Internally a value is stored in per unit, so editing using the kV values will set the per unit value equal to the entered value divided by the NomkV field.</p></td>
</tr>
<tr class="even">
<td><p>ErrorkV</p>
<p>ErrorPU</p></td>
<td><p>Single Float</p>
<p>(Calculated)</p></td>
<td><p>This fields looks at all buses that are using this CaseVoltageTarget, so for Subsation/NomkV type of Target it may be multiple buses. Over all these buses, this returns the largest magnitude deviation from the voltage band. Buses with voltages inside the band are treated as having an error of 0.0000.</p></td>
</tr>
<tr class="odd">
<td><p>TargetkVA</p>
<p>...</p>
<p>TargetkVH</p>
<p>TargetPUA</p>
<p>...</p>
<p>TargetPUH</p></td>
<td><p>Single Float</p></td>
<td><p>Specify a voltage target in either kV or per unit to use depending on the TargetActive being “A”, “B”, … , “H”</p>
<p>Internally the values are stored in per unit, so editing using the kV values will set the per unit value equal to the entered value divided by the NomkV field.</p>
<p>An example use could be as follows</p>
<p>TargetA = High load times during the Summer</p>
<p>TargetB = Medium load times during the Summer</p>
<p>TargetC = Low load times during the Summer</p>
<p>TargetD = High load time during Winter</p>
<p>TargetE = Medium load times during Winter</p>
<p>TargetF =Low load times during Winter</p>
<p>TargetG and TargetH are not used</p></td>
</tr>
</tbody>
</table>

CaseVoltageTargetTool

The CaseVoltageTargetTool represents all the options associated with the Case Voltage Target tool. These options can be edited at the top of the Voltage Conditioning dialog box.

|                           |        |                                                                                                                                                                                  |
| ------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Field                     | Type   | Type                                                                                                                                                                             |
| TargetActive              | String | User enters A, B, C, D, E, F, G, or H                                                                                                                                            |
| BusIdentifier             | String | Specify which identifier to use when showing the bus in the CaseVoltageTarget objects either *Number*, *Name\_NomkV*, or *Label*                                                 |
| SubIdentifier             | String | Specify which identifier to use when showing the substation in the CaseVoltageTarget objects either *Number*, *Name\_NomkV*, or *Label*                                          |
| ShuntTransformerWeight    | String | A weight to bias shunts to move before transformers                                                                                                                              |
| MinSensitivityShunt       | String | Minimum dV/dB sensitivity to consider for moving a shunt                                                                                                                         |
| MinSensitivityTap         | String | Minimum dVbus/dTap sensitivity to consider for moving a tap ratio                                                                                                                |
| TransmissionNomkV         | String | When searching from a generator terminal to find the closest transmisson level bus, this is the threshold nominal kV of a bus that is considered transmission level              |
| StopSearchImpedanceThresh | String | When searching from a generator terminal to find the closest transmisson level bus, this is the threshold impedance that will indicate we have found a significant system device |
| MaxIterations             | String | How many device moves to do before giving up (oscillation check)                                                                                                                 |
| IncludeShunts             | String | YES or NO. Set to YES to allow processing of switched shunts as well.                                                                                                            |
| IncludeTaps               | String | YES or NO. This is not presently used.                                                                                                                                           |

These options can also be set using the object CaseVoltageTargetTool\_Value instead in an AUX file that looks like the following.

CaseVoltageTargetTool\_Value (Option,Value)

{

"TargetActive" "A"

"BusIdentifier" "Number"

"SubIdentifier" "Name"

"ShuntTransformerWeight" "1"

"MinSensitivityShunt" "1"

"MinSensitivityTap" "0.3"

"TransmissionNomkV" "40"

"StopSearchImpedanceThresh" "0.001"

"MaxIterations" "100"

"IncludeShunts" "NO"

"IncludeTaps" "NO"

}

CaseVoltageTargetRegion (Determining the TargetActive as A, B, ... H)

Every **bus** and **substation** in the power system case can be assigned to a **CaseVoltageTargetRegion**. This will be used to specify which buses and substations belong to regions representing different time-zones.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>String</p>
<p>(KEY Field)</p></td>
<td><p>Name of the CaseVoltageTargetRegion</p></td>
</tr>
<tr class="odd">
<td><p>TargetActive</p></td>
<td><p>String</p></td>
<td><p>TargetActive: A, B, C, D, E, F, G, or H</p>
<p>This is which of the targets to use for a CaseVoltageTarget</p></td>
</tr>
</tbody>
</table>

Each **bus** and **substation** in the power system model can be assigned to a **CaseVoltageTargetRegion** using a new field `CaseVoltageTargetRegion`. A bus will determine the TargetActive field to use based on the following order of precedence.

1\. Use ` CaseVoltageTargetRegion  ` with the Bus

2\. If not assigned with Bus, Use ` CaseVoltageTargetRegion  ` with the **Substation** to which **Bus** belongs

3\. If still not assigned, follow the ` TargetActive  `field of the **CaseVoltageTargetTool** object.

Bus and Substation: CaseVoltageTargetRegion and CaseVoltageTargetRegionUsed

Every bus and substation in the power system has an string field named `CaseVoltageTargetRegion`. This string refers to the name of the **CaseVoltageTargetRegion** to which the bus or substation is assigned. This field can be set to blank to indicate that no region is assigned. The bus also have a field named `CaseVoltageTargetRegionUsed` which will return its own `CaseVoltageTargetRegion`, or if this is not specified it will return the respective field of the substation to which the bus is assigned, or if the subtation is also unassigned it will return a blank.

Gen, Branch, and Shunt: `ConditioningAvailable`

The objects Gen, Branch, and Shunt have a field called `ConditioningAvailable` which is available under a folder Voltage Conditioning Tool in the typical list of fields. This field is a YES/NO field and will indicate if the object is available for modification during the Voltage Conditioning Tool process. Generators may change their voltage setpoints and Shunt objects may change their Mvar values in order to help achieve the case voltage targets.

Gen: `ConditioningRegBus`

It is expected that for many users the **CaseVoltageTargets** will be centered around specifying desired voltages for the transmission level buses in the system. This means case voltage targets will be created for transmission level voltages such as 69, 115, 138, 161, 230, 345, and 500 kV systems. The generators in power system models are sometimes configured to regulate the voltage at their terminal bus (typically 0.300 kV – 40.0 kV). This presents a problem for how to map the desired transmission voltage schedules into the voltage setpoints in the generator power system cases.

To overcome this, PowerWorld Corporation has added a new search to find the closest high voltage transmission bus to the terminal of the generator in hopes of finding the transmission bus that may have the voltage schedule that the generator can be used to enforce. The results of this search can be seen by adding the new field `ConditioningRegBus` to a generator case information display (see [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)). The `ConditioningRegBus`field search is done using a breadth-first search beginning at the terminal of the generator and looking outward for a bus that has a nominal voltage greater than or equal to **CaseVoltageTargetTool**`.TransmissionNomkV`. Once such a bus is found, the algorithm continues searching across buses that have an impedance less than or equal to **CaseVoltageTargetTool**`.StopSearchImpedanceThresh`. This second part of the search is done to look beyond various near zero-impedance branches for the main part of the substation.

As an example, consider the following figure showing a large group of generators at a complicated substation and how they are connected to the 500 kV subnet through various switching devices. The 2 generators in the upper left corner are configured to regulate bus 26209 which is past a breaker and disconnect in series with each generator. The tool will continue searching until it reaches bus 26102 which has a nominal voltage of 500 kV. (Another note, we ignore any buses that we determine are internal “star” buses of three-winding transformers such as bus 26213 in the example below. This is done regardless of the Nominal Voltage assigned to the star bus.) Once the search reaches bus 26102 it then continues to search outward until it finds a branch with an impedance larger than **CaseVoltageTargetTool**`.StopSearchImpedanceThresh`. In this example the search will terminate when it reaches bus 26131 which connects to an transmission line with a larger series X value. The `ConditioningRegBus` is then set to the primary bus in this 500 kV SuperBus which in this example is bus 26104

![Voltage Conditioning ConditioningRegBus](images/Voltage_Conditioning_ConditioningRegBus.png)

Gen: `ConditioningVoltSetkV` and `ConditioningVoltSetkVTol`

Finally there are 4 new fields of the Gen object named ConditioningVoltSetkV, ConditioningVoltSet, ConditioningVoltSetTolkV and ConditioningVoltSetTol.

These fields show the following. The `ConditioningRegBus` is determined. A search looking for a **CaseVoltageTarget** object that has been assigned to this particular Bus. If that is not found, then we instead look for a **CaseVoltageTarget** object that is assigned to the same substation and nominal kV as the `ConditioningRegBus`. If we do not find a **CaseVoltageTarget** object that meets either of these, then these 4 fields will be shown as a blank string. If a **CaseVoltageTarget** object is found, then these 4 fields are populated based on the calculation described shortly.

The TargetActive is determined based either on the **CaseVoltageTargetRegion** to which the `ConditioningRegBus` has been assigned or based on the global option stored in the **CaseVoltageTargetTool**`.TargetActive`. This will determine which Target to use (A, B, … H). With this information, these 4 fields will then be populated with the following calculations.

  - ConditioningVoltSetkV = (BandUpkV + BandDownkV)/2 + TargetkVA

  - ConditioningVoltSetTolkV = (BandUpkV – BandDownkV)/2

  - ConditioningVoltSet = (BandUpPU + BandDownPU)/2 + TargetPUA

  - ConditioningVoltSetTol = (BandUpPU – BandDownPU)/2

These calculations will give what PowerWorld would expect a generator’s `VoltSet` and `VoltSetTol` value should be changed to when being used in the Case Voltage Conditioning Tool. The additional arithmetic is necessary because PowerWorld’s Voltage Tolerance (`VoltSetTol`) is a single value that applies to both the upward and downward tolerance.

Use the Case Voltage Target Tool

To perform voltage conditioning either click the button **Perform Voltage Conditioning** on this dialog, or run the script command named `VoltageConditioning;`

The following process with the objective of conditioning voltages in the case is done when performing voltage conditioning.

1.  Ensure that the existing case has an initial solved power flow solution

2.  Iterate through all generators in the case to build a list of generators that meet the following criteria

    1.  ConditioningAvailable = YES.

    2.  ConditioningRegBus is populated (this will be true for all buses with Online = NO)

    3.  Using ConditioningRegBus, look up a ConditioningVoltSet from the table of CaseVoltageTarget objects. Only include generators that return a value for ConditioningVoltSet. Remember this will look for a CaseVoltageTarget assigned to the bus first and if one is not found it will look for a CaseVoltageTarget assigned to the ConditioningRegBus substation and nominal kV.

3.  A list of generators meeting these requirements is built and then the following information is Cached before the process is begun

    1.  CACHE\_RegBus = RegBus

    2.  CACHE\_AVR = AVR (the YES/NO field)

    3.  CACHE\_VoltSetTol = VoltSetTol

4.  With this cached, Simulator then runs through all the generators in the list created in the previous step and applies the following assignments to those generators.

    1.  RegBus = ConditioningRegBus

    2.  AVR = YES

    3.  VoltSet = ConditioningVoltSet

    4.  VoltSetTol = ConditioningVoltSetTol

5.  A new power flow solution is solved which will use the voltage schedules and tolerances specified.

6.  Look through all the Switched Shunt objects that are marked as ConditioningAvailable = YES which are regulating a bus which is outside of its CaseVoltageTarget range (based on the target and deadbands). Also make sure moving the shunt up or down will not cause the shunt to move all the way across the target range and result it begin outside of the target range on the other side. Among these shunts choose the one with the largest dV/dB (which is at least **CaseVoltageTargetTool**`.MinSensitivityShunt`) and move this shunt by one step up or down.

    1.  While iterating through these changed for repeated power flow solution, also keep track of subsequent changes in the direction of a shunt move. If a shunt changes directions multiple time it may be locked in this process and stop participating

    2.  For example, a shunt may start at 20 Mvar and on subsequent iterations through this step it may move up to 40 MVar, up to 60 MVar. This would not cause the oscillation counter to increase. However, if the shunt then moved back down to 40 Mvar, the oscillation counter would be incremented by 1. After the oscillation counter for an individual shunt reaches 3 then it will be locked for the duration of that VoltageConditioning process.

7.  Go to Step 5 and repeat until no more shunt moves are found. Keep repeating until no more shunt moves are done.

8.  Using the final solved solution with the setpoints and tolerance, reset back to the original regulation settings (but with a new setpoint). Do this by setting the following

    1.  AVR = CACHE\_AVR

    2.  RegBus = CACHE\_RegBus

    3.  VoltSetTol = CACHE\_VoltSetTol

    4.  Set VoltSet to match the new operating point. If a the CACHE\_VoltSetTol is 0.0, then this just means VoltSet = RegBus.Vpu

        Otherwise use the following logic

        If Mvar \>= MvarMax Then VoltSet = RegBus.Vpu-VoltSetTol

        else if Mvar \<= MvarMin Then VoltSet = RegBus.Vpu+VoltSetTol

        else VoltSet = RegBus.Vpu+VoltSetTol–2\*VoltSetTol/(MvarMax-MvarMin)\*(Mvar–MvarMin)
