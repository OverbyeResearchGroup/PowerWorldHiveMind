---
title: "Integrated Topology Processing (ITP)"
part: "Add-Ons"
chapter_file: "35-integrated-topology-processing.md"
topics: 21
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Integrated Topology Processing (ITP)

Full-topology modelling, consolidation, breaker-to-device conversion and ITP in applications.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (21)**

- [Topology Processing Overview](#topology-processing-overview)
- [Full-Topology Model](#full-topology-model)
- [Superbuses](#superbuses)
- [Subnets](#subnets)
- [Consolidation](#consolidation)
- [Primary Bus Priority Scheme](#primary-bus-priority-scheme)
- [Illustration of Process](#illustration-of-process)
- [Consolidated Representation](#consolidated-representation)
- [Consolidated Superbus View](#consolidated-superbus-view)
- [Integrated Topology Processing Dialog](#integrated-topology-processing-dialog)
- [Power Flow Using Topology Processing](#power-flow-using-topology-processing)
- [Ill-Conditioned Jacobian](#ill-conditioned-jacobian)
- [Contingency Analysis Using Integrated Topology Processing](#contingency-analysis-using-integrated-topology-processing)
- [Incremental Topology Processing](#incremental-topology-processing)
- [Integrated Topology Processing in Applications](#integrated-topology-processing-in-applications)
- [Saving the Planning Case](#saving-the-planning-case)
- [Planning Cases](#planning-cases)
- [Primary Bus Mapping](#primary-bus-mapping)
- [Breaker-to-Device Contingency Conversion](#breaker-to-device-contingency-conversion)
- [Device Derived Status](#device-derived-status)
- [Open with Breakers](#open-with-breakers)

---

<a id="topology-processing-overview"></a>

## Topology Processing Overview

*Source: [`Content/MainDocumentation_HTML/Topology_Processing_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Topology_Processing_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**The Integrated Topology Processing tool is available only if you have purchased the Integrated Topology Processing add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for details about ordering Integrated Topology Processing for Simulator.****

Integrated Topology Processing is a Simulator add-on, which allows you to solve EMS-type, full-topology models in a numerically robust and transparent manner. Planning cases, traditionally used in the planning environment by tools such as Simulator, correspond to a less-detailed, electrically equivalent snapshot of the full-topology model.

Integrated Topology Processing extends Simulator applications traditionally used by planners so they can operate in an operations real-time environment.

Integrated Topology Processing is fully integrated with the functions of the Simulator base package including power flow, contingency analysis, and sensitivity calculations, as well as with the [OPF](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview), [SCOPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview), [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview), [ATC](32-available-transfer-capability.md#available-transfer-capability-atc-analysis), and [PVQV](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview) add-ons.

Simulator's Integrated Topology Processing is different from traditional EMS topology processing, which requires converting the [full-topology model](#full-topology-model) into a consolidated, planning case, to numerically solve network applications such as power flow and state estimation. Simulator's Integrated Topology Processing dynamically obtains an equivalent [consolidated representation](#consolidated-representation) of the full-topology model by dynamically reassigning the connection pointers of all of the devices. In Simulator, no "case conversion" takes place. The consolidated representation has the same topology and is electrically equivalent to the corresponding planning case.

Only the full-topology model is stored in memory. We call this novel implementation "Single-Model" Integrated Topology Processing.

Simulator's Integrated Topology Processing allows complete unification of power system planning and operations unification regarding network models and application environment. Typical uses of Integrated Topology Processing are:

  - In the real-time production environment through [SimAuto](33-simauto-overview-and-setup.md#automation-server) automation, yielding implementations of true real-time applications: real-time power flow, real-time contingency analysis (Security Assessment - SA), real-time transient stability (Dynamic Security Assessment - DSA), PVQV (Voltage Stability Assessment - VSA), real-time SCOPF (Security-Constrained Economic Dispatch - SCED).
  - In near real-time operations by allowing simulation of real-time full-topology cases from the EMS.
  - In the planning environment by allowing extensive study of the real-time system.

Simulator's Integrated Topology Processing consists of two main features:

  - An algorithm that takes place behind the scenes that is used internally during numeric solutions such as power flow, ATC, etc.
  - A tool to convert the real-time model to a traditional planning case that can be consumed by planning software not able to operate on full-topology models.

We invite you to continue reading the following Integrated Topology Processing topics:

[Full-Topology Model](#full-topology-model)

[Superbuses](#superbuses)

[Subnets](#subnets)

[Consolidation](#consolidation)

[Primary Bus Priority Scheme](#primary-bus-priority-scheme)

[Illustration of Consolidation Process](#illustration-of-process)

[Consolidated Representation](#consolidated-representation)

[Consolidated Superbus View](#consolidated-superbus-view)

[Integrated Topology Processing Dialog](#integrated-topology-processing-dialog)

[Power Flow Using Topology Processing](#power-flow-using-topology-processing)

[Ill-Conditioned Jacobian](#ill-conditioned-jacobian)

[Contingency Analysis Using Integrated Topology Processing](#contingency-analysis-using-integrated-topology-processing)

[Incremental Topology Processing](#incremental-topology-processing)

[Integrated Topology Processing in Applications](#integrated-topology-processing-in-applications)

[Saving the Planning Case](#saving-the-planning-case)

[Planning Cases](#planning-cases)

[Primary Bus Mapping](#primary-bus-mapping)

[Breaker-to-Device Contingency Conversion](#breaker-to-device-contingency-conversion)

[Device Derived Status](#device-derived-status)

---

<a id="full-topology-model"></a>

## Full-Topology Model

*Source: [`Content/MainDocumentation_HTML/TP_Full_Topology_Model.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Full_Topology_Model.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Real-time applications require modeling the power network at a level of detail that includes all the switching devices such as circuit breakers and disconnects and other very low-impedance branch devices. For instance, an operator must have information about specific breaker statuses to coordinate device maintenance procedures.

These detailed models are referred to as “node-breaker” or “full-topology” models. This type of model cannot be solved directly in conventional planning applications because of the large number of very low-impedance branches resulting from the switching devices. The power flow would be forced to use an [Ill-Conditioned Jacobian](#ill-conditioned-jacobian) matrix if these low-impedances were directly modeled. In order to solve the power flow on a full-topology model, Simulator dynamically obtains a [Consolidated Representation](#consolidated-representation) of the power network by dynamically moving the device connection pointers.

Simulator models all type of branch objects as transmission line records. To aid in the consolidation, additional input parameters are necessary to properly identify the type of branch object that is being modeled and determine whether or not that branch can be eliminated during consolidation. These fields are accessible from the Topology group in the Available Fields for the [Line and Transformer Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display) in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). Two relevant input fields needed for Topology Processing are:

Branch Device Type

Type of branch specified can be specified as in the table below

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Transformer</p></td>
<td><p>A 2-winding transformer (user can not change)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>TransformerWinding</p></td>
<td><p>Part of a 3-winding transformer (user can not change)</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>SeriesCap</p></td>
<td><p>Either a series capacitor or a series reactor</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Line</p></td>
<td><p>Transmission line</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>ZBR</p></td>
<td><p>Zero-impedance branch. Represents a branch with negligible impedance <span class="underline">that is not a switching device</span>. Examples include</p>
<p>(1) Wires that connect bus segments in different parts of the same substation,</p>
<p>(2) Wires that connect 2 substations across the street from one another, possible owned by different companies,</p>
<p>(3) A short transmission segment connecting a hydro generation substation another substation at the top of the hill</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Breaker</p></td>
<td><p>Circuit breaker is a switching device that can be opened during a fault condition with very high current. (these are used in special algorithms in Simulator)</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Load Break Disconnect</p></td>
<td><p>A special disconnect that can be opened under load, but not during a fault. They are very common for switching in and out capacitor or reactor banks (these are used in special algorithms in Simulator)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Disconnect</p></td>
<td><p>Disconnect can be opened but not while current is flowing. They are often placed around Breakers. After a breaker is opened, these are opened to completely isolate the breaker so maintenance can safely be done. (these are used in special algorithms in Simulator)</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Fuse</p></td>
<td><p>Added to support the IEEE CIM definition. Have not seen it used much</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Ground Disconnect</p></td>
<td><p>Some EMS models include Disconnects that connect to radial buses with nothing attached and these radial buses represent ground. These disconnects are then normally open. They are used in an EMS environment to show visualizations of ground disconnects. This is not important for numerical simulations, but very important for the safety of those operating the system.</p></td>
</tr>
</tbody>
</table>

Allow Consolidation of Branch

This is a *YES* or *NO* field, which tells Simulator to eliminate closed switching devices and other very low-impedance branches from the network model during consolidation. Only branches that have a **Branch Device Type** equal to *Breaker*, *Load Break Disconnect*, *Disconnect*, *ZBR*, *Fuse*, or *Ground Disconnect* can be consolidated. If an element is of this type and is set not to be consolidated, it will be preserved in the model and its default impedance value will be used in the power flow equations. In the context of consolidation, the term *breaker*or *switching device* can be used to include any of the device types that can be consolidated.

There are other instances in which a branch that is marked as allowed to be consolidated will not be consolidated:

  - Branches that are area tie lines
  - Branches that are connected to a multi-terminal dc line converter
  - Branches that are part of a [Model Condition](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog)
  - Branches that are part of a [Model Expression](04-model-explorer-and-case-information-part2.md#model-expressions)
  - Branches that are part of a [Post Power Flow Solution action](10-power-flow-solution-and-options-part2.md#post-power-flow-solution-actions-dialog)
  - Branches that are part of [Transient Stability event](37-transient-stability-analysis-dialog-part1.md#transient-contigency-element-dialog)
  - Branches that are part of a contingency action if not using [Incremental Topology Processing](#incremental-topology-processing)
  - Branches that are part of an interface unless the branch is in series with a device that cannot be consolidated, e.g. transformer, line, load, generator, etc. The interface will be automatically modified to monitor the series device instead of the branch so that the branch can be consolidated.

Simulator models all of the system connection points: Busbars, Junctions, Terminals, etc. as buses.

Topology Bus Type

Type of connection point. Valid entries include *BusbarSection*, *Junction*, *Internal\_3WND*, *Ground*.

Topology Processing provides an optional input field for buses to aid in the consolidation:

Node Priority

Priority level of the bus to become a primary bus. This overrides the default Primary Bus Priority Scheme level for this bus.

Topology Processing determines two bus fields as part of the consolidation:

**Primary Node**

Bus to which all the device connection pointers in a Superbus will point to during Consolidation.

**Node Neighbor List**

If this is a Primary Bus, this contains a list of all buses that belong to the superbus in which this bus is contained. This entry is blank for buses that are not primary buses.

These four bus fields are available under the Topology group in the Available Fields for the [Bus Display](05-case-information-displays-by-object-part1.md#bus-display) found on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

---

<a id="superbuses"></a>

## Superbuses

*Source: [`Content/MainDocumentation_HTML/TP_Superbuses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Superbuses.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A SuperBus in the [Full-Topology Model](#full-topology-model) is a group of buses connected through CLOSED switching devices or other CLOSED very low-impedance branch devices. All the buses in a Superbus have the same voltage phasor, i.e., they correspond to the same electric point. As the status of switching devices change, superbuses change correspondingly, sometimes resulting in superbus merging or splitting.

Superbuses are set automatically when the case is read from the binary or aux file and they are updated at the beginning of a power flow solution or sensitivity calculation to capture possible changes in the status of switching devices. The details of the Superbus records is available in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) under **Solution Details \> Superbuses**.

Consolidation of superbuses iteratively remove superbuses that contain ONLY switching devices that are connected to other superbus only by open switching devices. These are of no significance so merging into a superbus removes the clutter.

A superbus in the [Full-Topology Model](#full-topology-model) would correspond to a bus in the electrically equivalent bus/branch planning case.

Each Superbus in a system belongs to only one [Subnet](#subnets).

---

<a id="subnets"></a>

## Subnets

*Source: [`Content/MainDocumentation_HTML/TP_Subnets.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Subnets.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A Subnet is a group of buses connected through switching devices or other very low-impedance branches devices regardless of their open or closed status. Subnets are bounded by transmission line and transformer terminals. Subnets on a system hence do not depend on the status of breakers, but only on the presence of devices. Subnets do not change unless equipment is added or removed from the physical model.

A Subnet can contain one or more [Superbuses](#superbuses).

A [Superbus](#superbuses) belongs to only one subnet.

Subnets and Superbuses are set automatically when the case is read from the binary or aux file.

The list of subnets and the details of subnet records can be seen on the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) under **Solution Details \> Subnets.**

The example below shows a subnet that has four nodes. The shown breakers statuses results in two superbuses. If either breaker is closed, the two superbuses will merge.

![TP Subnet Superbuses](images/TP_Subnet_Superbuses.jpg)

---

<a id="consolidation"></a>

## Consolidation

*Source: [`Content/MainDocumentation_HTML/TP_Consolidation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Consolidation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Consolidation consists in moving the connection pointers of all the devices within a Superbus to a specially selected bus called the Primary Bus, and hiding not needed switching devices and buses. The Primary Bus is selected based on a default [Primary Bus Priority Scheme](#primary-bus-priority-scheme).

Prior to consolidation, all the power system devices in a superbus, such as generators, loads, shunts and transmission line terminals are connected to their actual terminal buses in the physical system. After consolidation all the devices are connected to their corresponding Primary Bus. This makes the status and actually, the presence of switching devices in a superbus irrelevant, allowing the application to disregard them during the numerical solutions. A list of the branch device types that are allowed to be consolidated and exceptions to when these branch device types are not consolidated can be found in the [Full-Topology Model](#full-topology-model) topic. We say that the full-topology model is in a consolidated state and we call the representation of the system after consolidation, the [Consolidated Representation](#consolidated-representation).

A switching device that is directly in parallel (between exact same buses) with a non-switching device is internally flagged to prevent consolidation due to this switch. This is done to prevent series capacitors from being removed from the model when they are bypassed by their bypass circuit breaker. Note that the series cap can still be completely consolidated if the more complex network typically involving a disconnect causes their terminals to be at the same super bus, but prevent the obvious parallel switch is helpful.

After consolidation, the topology of the full-topology model is identical to that of an equivalent planning case and the models are electrically identical. However, in Simulator no case conversion takes place. Only the full-topology model exists in memory.

The following link contains an example illustrating the consolidation process: [Illustration of Process](#illustration-of-process).

The user is never allowed to interact with the model while it is in a consolidated state.

The user does not have access to the Consolidated Representation unless it is saved as a planning case as described in the section [Saving the Planning Case](#saving-the-planning-case).

---

<a id="primary-bus-priority-scheme"></a>

## Primary Bus Priority Scheme

*Source: [`Content/MainDocumentation_HTML/TP_Consolidation_Primary_Bus_Priority_Scheme.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Consolidation_Primary_Bus_Priority_Scheme.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

During [Consolidation](#consolidation), the devices connected to the buses of a [superbus](#superbuses) change their connection pointers to point to the Primary Bus. In this manner, all the devices appear to be connected to primary buses only.

By default, the selection of the primary bus takes place using the following priority scheme, in descending order of priority:

1.  Slack bus (highest priority)
2.  Multi-Terminal DC Line Terminals
3.  Generator Regulated Bus
4.  Switched Shunt Regulated Bus
5.  LTC Regulated Bus
6.  DC Line Terminal
7.  Generator Terminal
8.  Switched Shunt Terminal
9.  Load Terminal
10. Branch with Device Type = Series Capacitor
11. Branch with Device Type = Transformer
12. Branch with Device Type = Line
13. Branch with Device Type = ZBR
14. Branch with Device Type = Breaker
15. Branch with Device Type = Load Break Disconnect
16. Branch with Device Type = Disconnect
17. Branch with Device Type = Fuse
18. Branch with Device Type = Ground Disconnect

In case of ties, the minimum bus number is selected as the primary bus.

There is also an optional integer field available with each bus called **Topology\\Node Priority**. When this is specified for a bus, the bus with the highest Node Priority is chosen as the primary node. By default this Node Priority is 0 for all buses, and thus the priority defaults to the scheme specified above.

A dead bus is consolidated to its neighbors if all three of the following conditions are met:

1.  It has no gens, loads, or shunts
2.  It is connected to the rest of the system only by open AC branches
3.  It is only connected to ONE other SuperBus through these AC branches

The objective here is to consolidate a disconnect and dead auxiliary bus.

---

<a id="illustration-of-process"></a>

## Illustration of Process

*Source: [`Content/MainDocumentation_HTML/TP_Consolidation_Illustration of Process.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Consolidation_Illustration of Process.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Consider the following 11-bus, [full-topology model](#full-topology-model). Given the breaker statuses, this system would contain 4 [superbuses](#superbuses) shown in the next figure.

![TP Consolidation Illustration of Process 1](images/TP_Consolidation_Illustration_of_Process_1.jpg)

We apply [consolidation](#consolidation) to the system above considering that the primary buses of each superbus are buses 1, 4, 7 and 10. The system topology at this point (which is never seen by the user) would looks as follows.

![TP Consolidation Illustration of Process 2](images/TP_Consolidation_Illustration_of_Process_2.jpg)

At this consolidated state, the breakers and the non primary bus buses could be removed without affecting the power flow solution.

---

<a id="consolidated-representation"></a>

## Consolidated Representation

*Source: [`Content/MainDocumentation_HTML/TP_Consolidated_Representation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Consolidated_Representation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A consolidated representation of a full-topology model is one obtained when the system is in a consolidated state. In this state all the connection pointers of devices and device terminals have been moved to the primary buses of the [Superbuses](#superbuses) as part of the [Consolidation](#consolidation) process.

The user does not have access to the Consolidated Representation records unless it is saved as a planning case as described in the section [Saving the Planning Case](#saving-the-planning-case). However, the Consolidated Representation can be navigated using the [Consolidated Superbus View](#consolidated-superbus-view).

---

<a id="consolidated-superbus-view"></a>

## Consolidated Superbus View

*Source: [`Content/MainDocumentation_HTML/TP_Consolidated_Superbus_View.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Consolidated_Superbus_View.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator’s Bus View provides a feature that allows a [Full-Topology Model](#full-topology-model) to be navigated using the [Consolidated Representation](#consolidated-representation), in which only the primary buses are shown. This gives the appearance to the user of navigating the electrically equivalent planning case.

The Consolidated Superbus View is accessed from the [Bus View Display](05-case-information-displays-by-object-part1.md#bus-display). If the current case is set up such that [superbuses](#superbuses) can be identified, there will be a drop-down box at the top of the Bus View Display that will allow switching between the Full Topology representation and the Consolidated Superbus representation.

The Consolidated Superbus View has the following conventions:

  - Shows radial-connected generator, load, and switched shunt buses above the main (primary) bus
  - For series connections of buses, the main branch shown will be the first branch that is marked as NOT available for consolidation (i.e. AllowConsolidation = *NO*)
  - All generator, load, and switched shunt devices will appear connected to their Primary Bus instead of the actual bus
  - Only branches that connect different superbuses will be shown. This means that closed circuit breaker will not appear on the consolidated superbus view because they connect two buses that are in the same superbus.

When saving a Consolidated Case or when viewing the Consolidated Superbus in the Bus View, generally open switching devices are maintained in the model to show where they are. If a CLOSED switching device is parallel with a open switching device it will not display the open switching device. CLOSED switching devices in this situation are unusual as they must be specified as Consolidate=NO or part of an interface or tie-line, so this is a special situation.

An example full-topology model is shown below. Each gray region represents a superbus. The large buses and numbers in each superbus represent the primary bus for that superbus.

![TP Consolidated Superbus View 1 474x237](images/TP_Consolidated_Superbus_View_1_474x237.jpg)

The associated full-topology bus view and the consolidated superbus view for the above model is shown below:

![TP Consolidated Superbus View 2 714x443](images/TP_Consolidated_Superbus_View_2_714x443.jpg)

---

<a id="integrated-topology-processing-dialog"></a>

## Integrated Topology Processing Dialog

*Source: [`Content/MainDocumentation_HTML/Topology_Processing_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Topology_Processing_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open the Topology Processing Dialog select **Topology Processing** found on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab in the **Topology Processing** ribbon group. This dialog includes options to solve the [Power Flow Using Topology Processing](#power-flow-using-topology-processing), perform [Contingency Analysis Using Topology Processing](#contingency-analysis-using-integrated-topology-processing), and for [Saving the Consolidated Case](#saving-the-planning-case).

![Topology Processing Dialog](images/Topology_Processing_Dialog.gif)

Power Flow Solution Options

Use Consolidation (This is a Full-Topology Model)

This option is used for all Simulator [applications](#integrated-topology-processing-in-applications): power flow, contingency analysis, sensitivity calculations, etc. This option should ALWAYS be checked for real-time cases, while it should be unchecked for planning cases. If a full-topology model was read and this option is not checked, the power flow will try to solve the model without removing the switching devices resulting in a very large [ill-conditioned Jacobian](#ill-conditioned-jacobian). This option is also found on the [Power Flow Solution Common Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog.

Breaker Options Added in version 20

Click the **Update Allow Open or Close Breakers** button to set the **Allow Open or Close Breakers** field for branches based on the current power flow case. When this field is set to NO, a switching device is not allowed to be selected when using processes that automatically determine breakers and other switching devices that operate to isolate or energize a device. See the [Update Allow Open or Close Breakers](05-case-information-displays-by-object-part2.md#update-allow-open-or-close-breakers) topic for more information on how this field is set.

Contingency Analysis

These options are shown on this dialog for informational purposes only. These can be accessed and set from the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) on the [Options](22-contingency-analysis-options.md#options-tab) tab and [Modeling](22-contingency-analysis-options.md#basics) sub-tab. These options are described in more detail in the [Contingency Analysis Using Topology Processing](#contingency-analysis-using-integrated-topology-processing) topic.

Consolidated Case Save Options

These options allow the saving of the consolidated representation as a traditional planning case. More detail about these options is provided in the [Saving the Planning Case](#saving-the-planning-case) topic.

Options found on the **Primary Bus Mapping** tab are described in the [Primary Bus Mapping](#primary-bus-mapping) topic.

---

<a id="power-flow-using-topology-processing"></a>

## Power Flow Using Topology Processing

*Source: [`Content/MainDocumentation_HTML/TP_Power_Flow_Using_Topology_Processing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Power_Flow_Using_Topology_Processing.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In order to perform numerical solutions using Integrated Topology Processing, Simulator does the following:

[Consolidates](#consolidation) the system relocating the devices and removing not needed breakers and non primary buses.

Performs the numerical calculation.

De-consolidates the system by restoring breakers and relocating the devices to their original buses. This step also maps the values of the primary buses to all the buses in the [superbus](#superbuses).

This is transparent to the user, who only needs to tell Simulator to use consolidation. The option that needs to be set to use consolidation is found on the [Topology Processing Dialog](#integrated-topology-processing-dialog) and also on the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog.

---

<a id="ill-conditioned-jacobian"></a>

## Ill-Conditioned Jacobian

*Source: [`Content/MainDocumentation_HTML/TP_Ill_Conditioned_Jacobian.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Ill_Conditioned_Jacobian.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Matrix **A** in the linear equation **Ax** = **b** is ill-conditioned if small changes in the entries of the vector **b** radically change the solution vector **x**. Ill-conditioned matrices are particularly troublesome in iterative solvers such as AC power flow algorithm implementations. One iteration of the AC power flow solves the linear equations **J Δx** = **Δy** where **J** is the Jacobian matrix, **Δx** is the vector of voltage magnitude and angle differences and **Δy** is the vector of real and reactive power mismatches.

A power flow Jacobian can become ill-conditioned if the system branches present reactances that differ in orders of magnitude, such as very short lines or zero impedance branches. Because the reactance of switching devices is negligible compared to that of transmission lines and transformers, modeling but a short number of switching devices in the Jacobian is prohibitive. The lower the value of the reactance, the more ill-conditioned the Jacobian will become. On the other hand, if the assumed reactance value is not too low, the solution would be inaccurate resulting in larger bus voltage angles. In Simulator switching devices that are present in [Full-Topology Models](#full-topology-model) are handled by [Integrated Topology Processing](#topology-processing-overview), producing an exact and robust numerical solution.

---

<a id="contingency-analysis-using-integrated-topology-processing"></a>

## Contingency Analysis Using Integrated Topology Processing

*Source: [`Content/MainDocumentation_HTML/TP_Contingency_Analysis_Using_Topology_Processing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Contingency_Analysis_Using_Topology_Processing.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator Integrated Topology Processing allows solving contingencies in the [Full-Topology Model](#full-topology-model).

EMS systems model contingencies through a list of real system actions. For instance, opening a line involves opening the set of breakers that electrically isolate the device. The same contingency action in a planning environment would be modeled as a single contingency action: OPEN LINE. Simulator provides a special contingency action called [Open with Breakers](24-contingency-element-dialog.md#contingency-element-open-breakers) which enables this type of modeling. There is also a [Close with Breakers](24-contingency-element-dialog.md#contingency-element-close-breakers) contingency action that enables modeling breakers to energize a device instead of using a planning-type contingency action to change the status of the device itself.

There is an option to determine whether to monitor all buses or only the primary node in each superbus during contingency analysis, **When using Integrated Topology Processing, monitor only the primary bus for each superbus**. This is found on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) on the [Options](22-contingency-analysis-options.md#options-tab) tab on the [Limit Monitoring](22-contingency-analysis-options.md#limit-monitoring) page.

The option to determine how contingencies should be modeled within topology processing is found on the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) on the [Options](22-contingency-analysis-options.md#options-tab) tab and [Modeling\\Basics](22-contingency-analysis-options.md#basics) page in the **Topology Processing Mode** grouping.

![TP Contingency Analysis Options](images/TP_Contingency_Analysis_Options.gif)

Preserve All Breakers Included in Contingencies

If this option is selected, contingency analysis will not treat contingency breakers as zero impedance branches and will keep all of them in the model. Hence, the consolidated representation is obtained only once upfront before the first contingency, and this representation is used to solve all the contingencies. Using this option, the consolidated representation is smaller than the full model, but is not the smallest possible. If the number of contingencies and breaker actions is large, many breakers will be preserved in the case. If the percentage of preserved breakers is significant, this may result in an [Ill-Conditioned Jacobian](#ill-conditioned-jacobian) during the contingency solution.

Use Incremental Topology Processing Mode

In this option, contingency analysis uses an [Incremental Topology Processing](#incremental-topology-processing) approach to solve each contingency. Since usually the number of contingency actions in a contingency is small (usually around 4 to 10), only a small number of [Subnets](#subnets) are affected by a contingency. The topology of all the other subnets remains unchanged. When this option is used, Simulator does a full consolidation before the first contingency and then for each contingency, the topology of just the affected subnets is re-processed (determining superbuses and primary buses, and updating the connection pointers). Incremental Topology Processing provides a more robust solution and should be used whenever possible.

Incremental Topology Processing cannot be used for applications that use linearization and that require a constant size of the bus array, such as sensitivity analysis. For instance, ATC will automatically use the contingency analysis **Preserve Breakers Included in Contingencies** option.

NOTE: Consolidated branches flows (Breakers, Disconnects, ZBRs, etc.) are monitored during contingency analysis.

---

<a id="incremental-topology-processing"></a>

## Incremental Topology Processing

*Source: [`Content/MainDocumentation_HTML/TP_Incremental_Topology_Processing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Incremental_Topology_Processing.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Incremental Topology Processing is a technique used to update the [Consolidated Representation](#consolidated-representation) of the system in a very fast manner. It is particularly useful during [Contingency Analysis](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog), where it does the following:

Consolidate entire case

For each contingency do

Apply switching device actions and identify subnets with changed topology

Expand affected subnets to full-topology detail

Reconsolidate affected subnets with post-contingency topology

Solve post-contingency power flow

Determine and store limit violations

Reset affected subnets to pre-contingency topology

Restore pre-contingency power system state

End

Deconsolidate entire case

Incremental Topology Processing is very fast, taking on the order of a few milliseconds.

---

<a id="integrated-topology-processing-in-applications"></a>

## Integrated Topology Processing in Applications

*Source: [`Content/MainDocumentation_HTML/TP_Topology_Processing_In_Applications.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Topology_Processing_In_Applications.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator applications such as ATC and OPF use a hierarchical scheme where [Consolidation](#consolidation) takes place only at the beginning of the numerical solution process. Consolidation in lower functions takes place only if it has not taken place already in higher-level functions.

![TP Topology Processing in Applications 710x335](images/TP_Topology_Processing_in_Applications_710x335.jpg)

Following completion of the application, de-consolidation occurs in the function level in which the consolidation originally occurred. This process is very similar to the one described for [solving the power flow using integrated topology processing](#power-flow-using-topology-processing). There can be some exceptions to this when using Contingency Analysis. The [Contingency Analysis Using Integrated Topology Processing](#contingency-analysis-using-integrated-topology-processing) topic provides more details on this.

Once the input data is set in the [Full-Topology Model](#full-topology-model) fields, the applications work in the same manner as with regular [Planning Cases](#planning-cases).

---

<a id="saving-the-planning-case"></a>

## Saving the Planning Case

*Source: [`Content/MainDocumentation_HTML/TP_Saving_the_Planning_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Saving_the_Planning_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Integrated Topology Processing allows you to save the [Consolidated Representation](#consolidated-representation) of the [Full-Topology Model](#full-topology-model) as a traditional [Planning Case](#planning-cases) (bus/branch model), in any of the [formats](03-cases-files-and-formats.md#case-formats) supported by Simulator.

Although the saved case can be reopened in Simulator as a regular case, the user should note that the topology of this case will depend on the statuses of the breakers in the Full-Topology Model. If the statuses of the switching devices in the Full-Topology Model are continuously changing as is the case when the case comes from a real-time Retriever implementation, then the topology of the saved cases will be slightly different minute to minute.

The saving tool is available on the [Topology Processing Dialog](#integrated-topology-processing-dialog) in the Consolidated Case Save Options section.

![TP Saving the Planning Case](images/TP_Saving_the_Planning_Case.jpg)

Save Consolidated Case Now

Click this button to save the case in any of the supported [formats](03-cases-files-and-formats.md#case-formats).

Open Non-Energized Branches

If the terminal buses of a transmission line or transformer are not energized, then assume the element is open.

Convert Shunts to Blocks

Some systems have several shunts in a superbus, and some formats support only one shunt per bus. This option allows modeling those shunts as an aggregate device.

Do not save contingencies (will make smallest case size)

Use this option if contingency analysis will not take place on the saved case.

Save contingencies (must preserve all elements including breakers)

All the contingencies, the contingency actions, and all the switching devices included in contingency actions will be preserved and saved in the consolidated case. It makes a big difference to perform a [Breaker-to-Device Contingency Conversion](#breaker-to-device-contingency-conversion) before saving the case. Usually most of the breaker contingencies can be converted to device contingencies requiring just a small number of breakers to be preserved in the case.  Some planning tools have limitations regarding the number of low impedance branches that can be modeled and will not be able to read and solve the [Planning Case](#planning-cases) if it contains a large number of switching devices.

---

<a id="planning-cases"></a>

## Planning Cases

*Source: [`Content/MainDocumentation_HTML/TP_Planning_Cases.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Planning_Cases.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Planning Cases are a high-level, simplified view of the actual network, in which all the switching devices have been removed. Planning Cases use a bus/branch model that uses the bus numbers as key fields for all the system elements. [Full-Topology Models](#full-topology-model) on the other hand, are detailed representations of the physical system that include circuit breakers and disconnects. Simulator Topology Processing allows complete model unification and provides a unified application environment to simulate both types of models.

---

<a id="primary-bus-mapping"></a>

## Primary Bus Mapping

*Source: [`Content/MainDocumentation_HTML/TP_Primary_Bus_Mapping.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Primary_Bus_Mapping.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Sometimes, it is necessary to explore or export the topology relations between [superbuses](#superbuses) and buses in the [Full-Topology Model](#full-topology-model) and its [Consolidated Representation](#consolidated-representation). Because different sets of switching devices can be preserved by Simulator when solving the [Power Flow Using Topology Processing](#power-flow-using-topology-processing), when solving the [Contingency Analysis Using Topology Processing](#contingency-analysis-using-integrated-topology-processing), and when [Saving the Planning Case](#saving-the-planning-case), there will be different mappings for each one of these actions.

Primary Bus Mapping options are available on the **Primary Bus Mapping** tab of the [Topology Processing Dialog](#integrated-topology-processing-dialog).

![TP Primary Bus Mapping](images/TP_Primary_Bus_Mapping.gif)

This display shows a detailed mapping of superbuses to buses. By changing the selection for which mapping to view, the corresponding mapping that would take place is shown in this [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays).

Power Flow Solution

Provides the mapping used when solving the power flow.

Contingency Analysis

Provides the mapping used when solving contingencies.

Saved Consolidated Case

Provides the corresponding topology relations between the full-topology model and the consolidated case to be saved.

This mapping can be saved as an auxiliary file from the local menu of the display (right-click and choose **Save As \> Auxiliary File...**) or from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar).

---

<a id="breaker-to-device-contingency-conversion"></a>

## Breaker-to-Device Contingency Conversion

*Source: [`Content/MainDocumentation_HTML/TP_Breaker_to_Device_Contingency_Conversion.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TP_Breaker_to_Device_Contingency_Conversion.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

While operation contingencies are defined using breaker actions, planning cases use simplified device [contingency actions](24-contingency-element-dialog.md#contingency-element-dialog). For instance, the outage of a single transmission line is modeled in EMS systems as the set of the actual circuit breaker actions that physically de-energize the transmission line. On the planning side, the same contingency is modeled as a single contingency action related to the transmission device: OPEN LINE.

A feature of PowerWorld’s [Integrated Topology Processing](#topology-processing-overview) is the ability to convert operations-type, circuit breaker contingencies to their electrically equivalent device contingencies for single outage, multiple outages, or complex post-contingency topologies. While both the breaker contingencies and the device contingencies can be solved on the [Full-Topology Model](#full-topology-model), breaker contingencies MUST be converted to device contingencies in order to solve them on the consolidated [Planning Case](#planning-cases).

Some complex breaker contingencies cannot be converted to electrically equivalent topologies by simply changing the energization status of devices. A subset of the breakers involved in those contingencies may need to be preserved in the case to entirely reproduce the electric topology.

The Breaker-to-Device Contingency Conversion is launched from the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) \> **Other** button \> **Convert to Device Contingencies**. This routine will convert all the contingencies in the list. The contingency analysis status box will indicate the progress of the contingency conversion process. The log will also provide messages during the conversion.

![TP Convert Breaker to Device Contingencies](images/TP_Convert_Breaker_to_Device_Contingencies.jpg)

The new list of converted device contingencies will replace the original list of breaker contingencies previously displayed on the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). The list of device contingencies can be solved directly on the [Full-Topology Model](#full-topology-model). On average, device contingencies include less device actions per contingency compared to breaker actions. For instance, a single line outage usually requires opening several circuit breakers, whereas the device contingency equivalent requires a single OPEN LINE contingency action.

In order to reflect the conversion process, the actions in the [Contingency Definitions](22-contingency-analysis-options.md#contingency-definition-display) include device actions with the name of the device: *Line*, *Transformer*, *Load*, *Gen*, etc. and also *Breaker* if breakers need to be preserved for a given contingency.

---

<a id="device-derived-status"></a>

## Device Derived Status

*Source: [`Content/MainDocumentation_HTML/Device_Derived_Status.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Device_Derived_Status.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following describes the determination of derived status in version 20. To see derived status as it was in version 19 click [here](52-additional-linked-topics-part1.md#device-derived-status-version-19).

Differences exist between planning models and full-topology EMS models when it comes to determining if a device is energized and what the status is of the device.

With planning software and bus-branch models, two distinct fields exist: **Status** and **Online**. The **Status** field is an explicit field that exists to determine if a device is open or closed. This is needed because breakers are not modeled. The **Online** field indicates if the device is actually energized which will be affected by the status of branches.

With full-topology EMS models, breaker or disconnect status determines the status of other devices, i.e. whether or not they are energized. No explicit status field exists for other devices like generators, loads, lines, transformers, etc. Typically when using a full-topology model in Simulator, the **Status** of non-switching devices (generators, loads, lines, etc.) will be set to *Closed*. A hybrid model with only parts of the system modeled with breaker detail can still use the **Status** field for non-switching devices.

The actual status of a device can be confusing, especially for those accustomed to a planning model. To eliminate confusion, the **Derived Status** field will be used to indicate the status with which planning model users are accustomed.

**Derived Status** is determined by the following:

  - **Status** = *Open* --\> **Derived Status** = *Open*
  - Else
      - Search starting at the device terminals traverse branches with **Status** = *Closed* looking for closed breakers or generators (loads and switched shunts are excluded here)
          - If search successful at all terminals --\> **Derived Status** = *Closed*
          - Else If search successful at FROM end only (if two terminal device) --\> **Derived Status** = *Open To*
          - Else If search successful at TO end only (if two terminal device) --\> **Derived Status** = *Open From*
          - Else --\> **Derived Status** = *Open*
  - Whether or not a device is **Online** has no impact on the **Derived Status**
  - For switching devices (Breaker, Load Break Disconnect, Disconnect, Fuse, and Ground Disconnect) **Derived Status** = **Status**

When searching for the closed breakers, finding a generator is treated the same as finding a closed breaker. This is needed for hybrid cases where all switching devices are not completely defined. It is expected in a full-topology model with all switching devices defined that this will not interfere with identifying the derived status.

The following provides examples of how the **Derived Status** field is set for various breaker settings:

![Derived Status 1 653x368](images/Derived_Status_1_653x368.gif)

**Derived Online** is another field that is available for branches. This combines the **Online** field and the **Derived Status** field.

Derived Online is determined by the following:

  - **Online** = *NO* --\> **Derived Online** = *Open*
  - Else
      - **Derived Online** = **Derived Status**

When determining if a branch end is *CLOSED* as part of the **Derived Status** check, several conditions must be met:

  - A closed circuit breaker must be found. A breaker is a branch whose **Branch Device Type** = *Breaker*
  - Beyond the closed breaker there must be a device of consequence such as:
      - Closed branch (this is any **Branch Device Type**)
      - Generator
      - Load
      - Switched shunts
  - Breakers directly in parallel with a Line, Transformer, or Series Capacitor are excluded
  - If no closed breakers can be found, but a generator, load, or switched shunt is found without finding an open switching device in the search path

The following are examples of **Derived Status** = *Closed* lines:

![Derived Status 2 876x298](images/Derived_Status_2_876x298.gif)

The following are examples of **Derived Status** = *Open To* lines:

![Derived Status 3 880x299](images/Derived_Status_3_880x299.gif)

---

<a id="open-with-breakers"></a>

## Open with Breakers

*Source: [`Content/MainDocumentation_HTML/Open_Breakers_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Open_Breakers_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are several places in Simulator where functionality is available to open breakers in order to isolate a particular device or devices. This functionality is generally available when breakers, or other branch devices that are allowed to be automatically switched, are defined in the case. For some functionality, the [Integrated Topology Processing add-on](#topology-processing-overview) is required in addition to having breakers defined.

This overview is intended to provide information on which branch device types can be automatically switched, how breakers are selected, and the tools in Simulator that make use of open with breakers functionality. Additional information about how this functionality might work differently with specific tools will be described with those particular topics.

Branch Device Types that will Automatically Operate

The **Branch Device Type** field for a branch must be set to one of the following options in order for a branch to be considered a device that can automatically operate when using open breaker functionality:

  - Breaker
  - Load Break Disconnect
  - Disconnect
  - Fuse
  - Ground Disconnect

Not all of the types listed above can be used for automatic switching with all tools that allow this. The different tools will indicate which types are allowed. For brevity, the term *breaker* will be used throughout this discussion to indicate branch devices that can be automatically switched.

Added in version 20

For a branch to be considered for automatic switching it must also have its **Allow Open or Close Breakers** field set to *YES*. This field can be changed by the user, and there are several options that will update this field based on the present case. For more information on how this field can be updated by Simulator, see the [Update Allow Open or Close Breakers](05-case-information-displays-by-object-part2.md#update-allow-open-or-close-breakers) topic. When **Allow Open or Close Breakers** = *NO* and a branch is closed, it will be traversed when looking for breakers to open regardless of its Branch Device Type instead of being included in the devices to switch.

Algorithm Description for Open with Breakers

This algorithm is applied to each terminal bus of the device specified. For generators, loads, shunt, and buses this is done on a single bus only. For an Injection Group, each generator, load, and switched shunt in the injection group will be processed in turn. For an interface, each line in the interface is processed in turn. For substations, each ac line or dc line in the substation connected to another substation are processed in turn. Starting at each terminal bus of the device and marching outwards, the algorithm traverses closed branches (except for breakers), dc lines, and multi-terminal DC lines and will flag any closed breakers at buses that are visited. The buses that are visited are also flagged. (Note: the algorithm will NOT traverse across the breakers unless for an exception noted below). When buses are visited that have online generators, a list of generators is maintained that must be opened as well. In order to prevent the degenerate case where breakers do not fully isolate any portion of the network, only 10 buses with online generation are permitted for visitation. If more than 10 buses are encountered with online generation, the algorithm will immediately abort and a log message is written saying that the device "cannot be isolated from online generation".

If this part of the algorithm completes it will have obtained a list of flagged breakers and a list of visited buses (as well as a list of generators to open). The list of flagged breakers is then examined to ensure that each breaker actually isolates the original device. Each flagged breaker will be examined and if a flagged breaker has a terminal bus that is NOT in the list of visited buses, then this breaker disconnects the device from another part of the system and will be maintained. Breakers for which both terminal buses have been visited will be discarded because these breakers do not actually isolate anything. If at least one flagged breaker is maintained then the process is deemed successful and the contingency will outage the list of maintained flagged breakers. If all the flagged breakers are discarded, then the breakers do not isolate anything, and therefore a log message is written saying that "no part of the system can be isolated," and nothing is done.

Open Normally Open Disconnects Added in version 20

Some tools allow normally open disconnects that are currently closed to be open during the process of identifying breakers. The tools that allow this will have an option for using this feature. Disconnects are considered to be only branches where **Branch Device Type** is *Disconnect*.

This option will modify the open with breakers algorithm slightly. Without this option, the open with breakers algorithm searches across closed branches until a closed breaker is found along a traversal path. That breaker is then included in switching devices to open and the search terminates along that path. When using this option, any disconnects along a traversal path that are encountered that are presently closed but normally open will be included in the switching devices to open, and the search for breakers and disconnects will terminate along that path.

The normal status of a branch is determined by the **Normal Status** field.

Breakers in Series with Shunt Devices (Switched Shunts, Generators, and Loads) Added in version 20

When attempting to isolate any device except for a switched shunt during the process of searching for breakers and disconnects to open, any breaker or disconnect that is strictly in series with only switched shunts and disconnects will be excluded from the switching devices that can close. This check effectively looks for switched shunts that are connected radially by a breaker or disconnect. This will prevent switched shunt breakers from operating inappropriately when opening a line that has a tap point with switched shunts.

Modified in version 20, build on May 18, 2018

In addition to switched shunts, generators and loads are included in the series check for breakers and disconnects when identifying which switching devices can open. If a particular switched shunt, generator, or load should be disconnected, only that particular device will be disconnected if other radially connected shunt devices are found.

Tools that Use Open Breakers Functionality

[Contingency Analysis](24-contingency-element-dialog.md#contingency-element-open-breakers)

Local menu option for display objects and [case information displays](04-model-explorer-and-case-information-part1.md#records-menu)

Several objects (buses, branches, dc lines, generators, loads, and switched shunts) have a special local menu option, **Open Breakers to Isolate**, that allows them to be open using breakers. This option is present on both the local menu for display objects and the local menu of case information displays for the specified types. This option does not require having the [Integrated Topology Processing add-on](#topology-processing-overview) to work. When using this option, a dialog will open indicating which breakers have been identified and are being opened.

There are three sub-options available:

**Only Breakers**

Only **Branch Device Type** of *Breaker* will be included as valid switching devices.

**Breakers and Load Break Disconnects**

Only **Branch Device Types** of *Breaker* and *Load Break Disconnect* will be included as valid switching devices.

**With Options**

A dialog will open that allows for user input on the **Branch Device Types** that are included for valid switching devices. There is also an option **Open Normally Open Disconnects**. If this option is selected, *Disconnects* will be included in the search algorithm as described in the **Open Normally Open Disconnects section** above.

[OpenWithBreakers script command](03-cases-files-and-formats.md#auxiliary-file-format-aux)

Scheduled Actions
