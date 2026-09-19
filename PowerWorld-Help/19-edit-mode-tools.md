---
title: "Edit Mode Tools"
part: "Tools"
chapter_file: "19-edit-mode-tools.md"
topics: 16
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Edit Mode Tools

Equivalencing, case modification tools and renumbering.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (16)**

- [Equivalents](#equivalents)
- [Equivalents Display](#equivalents-display)
- [Bus Selection Page](#bus-selection-page)
- [Appending a Case](#appending-a-case)
- [Merging Buses](#merging-buses)
- [Splitting Buses](#splitting-buses)
- [Split Bus Dialog](#split-bus-dialog)
- [Create Composite Load Models Dialog](#create-composite-load-models-dialog)
- [Equipment Mover](#equipment-mover)
- [Potential Misplacements Dialog](#potential-misplacements-dialog)
- [Tapping Transmission Lines](#tapping-transmission-lines)
- [Automatic Line Tap Dialog](#automatic-line-tap-dialog)
- [Bus Renumbering Dialog](#bus-renumbering-dialog)
- [Bus Renumbering: Automatic Setup of Bus List Options](#bus-renumbering-automatic-setup-of-bus-list-options)
- [Bus Renumbering: Bus Change Options](#bus-renumbering-bus-change-options)
- [Renumber Areas/Zones/Substations Dialog](#renumber-areaszonessubstations-dialog)

---

<a id="equivalents"></a>

## Equivalents

*Source: [`Content/MainDocumentation_HTML/Equivalents_Topic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Equivalents_Topic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

An equivalent power system is a power system model of smaller dimension than the original system that approximates the behavior of the original system reasonably well. In reality, most power system models are actually an "equivalent" of a much larger interconnected network. When performing power system studies, it may be desirable to reduce the size of the system model even further so that it may be solved more quickly.

To bring up the [Equivalents Display](#equivalents-display), while in [Edit Mode](01-getting-started.md#edit-mode-introduction), go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Equivalencing...** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.

The most important part of constructing an equivalent is determining which buses should be explicitly retained in the equivalent, and which buses should be *equivalenced*, or removed from the case. Several definitions are useful here:

Study System

The buses that are to be retained.

External System

The buses that are to be equivalenced.

Boundary Buses

Any buses in the study system that are connected to buses in the external system.

How well the equivalent system approximates the behavior of the original system depends upon which buses are retained in the study system. Retaining more buses yields results that more closely match those of the original case, but at the expense of greater computation time. The number of buses to retain in the study system depends upon how the equivalenced system will be used. Building system equivalents is as much an art as it is a science, with few solid rules of thumb. However, to improve accuracy, you should retain as many generator units as possible.

The actual equivalent is constructed by performing a matrix reduction on the bus admittance matrix. A result of this process is the creation of "equivalent" transmission lines that join boundary buses equipped with equivalent shunts or loads. Equivalent lines typically have a circuit identifier of *99*, but have also been seen to have other numerical values between 90 and 99, or an alphanumeric identifier of *EQ*. Since many of the equivalent lines created during the matrix reduction have very high impedance values, an option is provided to ignore equivalent lines with impedances exceeding a specified threshold value. Additionally, an option is provided to convert the equivalent shunts added at the boundary buses to constant PQ loads. These PQ loads will be given circuit identifiers similar to those given to equivalent transmission lines.

---

<a id="equivalents-display"></a>

## Equivalents Display

*Source: [`Content/MainDocumentation_HTML/equivalents_display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/equivalents_display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Equivalents Display** is used to construct equivalent systems. An *Equivalent System* is a system of smaller dimension that exhibits similar power flow properties. Equivalent systems are constructed to help accelerate computation time without sacrificing a significant amount of accuracy. For more information, please see [Equivalents](#equivalents).

To bring up the Equivalents Display, while in [Edit Mode](01-getting-started.md#edit-mode-introduction), go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Equivalencing...** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group. This display contains two pages, the **Select The Buses Page**and the **Create The Equivalent Page**. Use the Bus Selection Page to partition the power system into the study system and the external system. Use the Create Equivalent Page to

  - Save the external system in a file
  - Extract the external system
  - Build an Equivalent

Each of these tasks is described below.

Select The Buses Page

To perform any of the tasks described on the Create Equivalent Page, you first need to specify the study system and the external system. Do this by directly assigning buses to the desired system. The [Select The Buses Page](#bus-selection-page) has been designed to provide a number of powerful and complimentary ways of accomplishing this task.

The most important point to keep in mind when using this page is that membership in the study system and the external system is on a bus-by-bus basis (as opposed to by areas or zones). Thus, each bus is either in the study system or the equivalent system. Each bus’ current assignment is indicated in the Buses list, which is shown on the bottom left corner of the page. The Buses list is a [Case Information display](04-model-explorer-and-case-information-part1.md#case-information-displays) and can be manipulated similar to other displays. By default, all buses initially reside in the study system. Please see [Select The Buses Page](#bus-selection-page) for more details.

Create The Equivalent Page

The Create Equivalent Page allows you to save the external system in a file, to delete the external system, and to build the power system equivalent.

Build Equivalent

This procedure constructs an equivalent system. For background on equivalents, please see [Equivalents](#equivalents). The following sections contain the options for building an equivalent.

Delete All External Generators or Retain Generators with Max MW Ratings Above

If the **Delete All External Generators** checkbox is checked, the equivalencing routine will remove all external generators from the case, regardless of their MW rating. Otherwise, the equivalencing routine will add to the study system any generators originally in the external system whose real power output exceeds the specified value. Retaining large generators often makes an equivalent significantly more accurate. If you do not wish to retain any additional generators, check the **Delete All External Generators** checkbox.

Retain Remotely Regulated Buses

Some generators and transformers regulate buses other than their terminals. When this box is checked, these remotely regulated buses are automatically included in the equivalent if the regulating generator or transformer is included. If the box is not checked, the regulated bus is set to the terminal of the retained object. It is strongly recommended that you leave this box checked at all times.

Retain Branch Terminals For

This section allows you to customize the retention of branch terminals for special-case types of branches. You may choose to retain terminal buses for transformers, zero impedance ties, area tie lines, and/or zone tie lines.

Max Per Unit Impedance for Equivalent Lines

During the equivalencing process, a number of equivalent lines are created joining the boundary buses. All equivalent lines with per unit impedance values above this threshold are ignored.

Two Character Circuit ID for New Equivalent Lines

Choose the circuit identifier to be used for the equivalent lines that are created. Choose between *97*, *98*, *99* or *EQ* for circuit IDs of equivalent lines.

Remove External Objects from Onelines

This feature removes display objects associated with the external system from any open onelines.

Convert Equivalent Shunts to PQ Loads

During the equivalencing process, shunt elements are added at the boundary buses. Check this box if you would like these equivalent shunts converted to constant PQ loads. If this option is checked, equivalent loads are created with a [load ID](07-object-properties-run-mode-and-general-part1.md#load-information) of *99*.

Remove Radial Systems

Checking this option results in all radial connections in the network to be reduced to their nearest non-radial bus (i.e. node.) The equivalencing routine will iteratively reduce the network when this option is checked, until no more radial connections exist in the system.

Delete Empty Areas/Zones/Substations that occur from Equivalencing

Since equivalencing is a process which ultimately removes buses from the system, and Areas, Zones and Substations are system devices which are groups of buses, this option will automatically remove the definition of these types of objects when all buses within them are removed from the case during the creation of the equivalent.

Adjust Area Unspecified Interchange to Zero Out ACE

Selecting this option will allow Simulator to automatically change the unspecified MW interchange amounts of each area to remove any non-zero ACE discrepancies caused by the equivalencing. This will help prevent these discrepancies from being assigned to the system slack bus.

Include Generator Dynamic Equivalents

Selecting this option will allow Simulator to automatically create dynamic equivalents of generators.

Minimum PU H for New Equivalent Generators

During the equivalencing process, a number of equivalent generators are created. All equivalent generators with per unit impedance values below this threshold are ignored.

Two Character Circuit ID for New Equivalent Generators

Enter the circuit identifier to be used for the equivalent generators that are created. Default is EQ.

Select **Build Equivalent System** to construct the equivalent system. Constructing an equivalent system permanently removes the external system from the case and adds a number of equivalent lines and shunts/loads.

Saving the External System in a File

This procedure allows an external system to be saved in a file **without deleting** the external system. This option is useful for allowing you to save a portion of the system in a file, modify it using perhaps another program, and then use [Append Case](#appending-a-case) to append the modified file to the original case.

When saving the external case, there are two options: 1) save just the external case, or 2) save the external case and any ties to the original case. Option one just saves the external case, while option two saves the external case and any transmission lines or transformers that connect the external system to the rest of the system. Save just the external case if you are planning to use the external case as a standalone case. Save the external case and its ties if you are planning to modify the external case and then to append it back to the original case.

Click **Save External System** to save the external system in a file. You will be prompted for the desired [case format](03-cases-files-and-formats.md#case-formats).

Deleting the External System

This procedure deletes the external system from the original case. All devices in the external system are removed, including any buses and lines/transformers in the external system and any lines/transformers that join the external system to the study system. Check the **Remove External Objects from Onelines** to remove any display objects linked to the external system from the open onelines.

This command **permanently removes** the external system from the case; an equivalent system is **not** created. Select **Delete External System** to actually delete the system.

Merge Bus Shunts Across Zero Impedance Branches

This procedure merges bus shunts that are across zero-impedance branches.

Merge Bus Shunt Values Above

During the merging process, only will merge bus shunts values above this threshold.

Merge Across Branches

During the merging process, only will merge bus shunts across branches with *X, R* less than the specified threshold.

Merge Shunts

Press the button to merge the shunt buses as specified by the previous options.

---

<a id="bus-selection-page"></a>

## Bus Selection Page

*Source: [`Content/MainDocumentation_HTML/bus_selection_page.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/bus_selection_page.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus Selection page is currently used with two displays:

  - The [Equivalencing Display](#equivalents-display), to partition the system into the study subsystem ("Study") and the external subsystem ("External").
  - The [Facility Analysis Dialog](18-general-tools.md#facility-analysis-dialog), to determine the buses in the external subsystem from which the buses in the facility would be isolated.

The following description concerns the Equivalencing Display, but the functionality of the Bus Selection Page is similar for both applications.

Buses, Areas, and Zones lists

For both equivalencing and facility analysis, use these lists to manually change the system designation of individual buses, areas, or zones. Note that changing the system designation on the area or zone tab is just another form of changing the designation of study / external system of individual buses. Click on the **Which System?** field in each of these tables to toggle the object’s affiliation with the study or external systems, subject to the values of the **Filter by kV** option and the **Include how many tiers of neighbors?** field.

In addition, the bus selection table for [facility analysis](18-general-tools.md#overview-of-facility-analysis) contains one additional column labeled **Selected**. This Yes or No field indicates which buses in the Study system belong to the Facility being analyzed. Double-clicking one of the fields in this column will toggle the value of the field between *Yes* and *No*.

External

Use these fields to specify a [range of areas, zones, or buses](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) to be added to the external system. The **Filter by kV** and **Include how many tiers of neighbors?** controls will also shape the selection of buses to add to the external system.

Study

Use these fields to specify a [range of areas, zones, or buses](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) to be added to the study system. The **Filter by kV** and **Include how many tiers of neighbors?** controls will also shape the selection of buses to add to the study system.

Include how many tiers of neighbors?

This value indicates the number of tiers of neighbors to carry with each selected bus when adding the selected bus to either the study or external system. For example, if Neighbor Tiers is 1 and we elect to add bus X to the external system, both bus X and its first tier of neighbors will be added to the external system. If Neighbor Tiers is 0, only bus X will be added to the external system.

Filter by kV

If the **Filter by kV** box is checked, then only buses having a nominal voltage level between the values given in the **Max kV** and **Min kV** fields can be selected.

Set All As External

Click this button to assign all buses to the external system.

Set Branch Terminals External or Study

Clicking either of these two buttons allows setting advanced filter criteria which define a branch or group of branches. Once the criteria are set, clicking **Filter** will select the terminal buses of all branches meeting the filter criteria, and set those buses to either the External or Study system, depending on which button was pressed.

Select Buses using a Network Cut

A custom [network cut](18-general-tools.md#set-selected-field-for-network-cut) can be defined for choosing which buses should remain in either the Study or External system.

Save Buses to File

Once the system has been partitioned, this command allows you to store the numbers of the buses of the study system in a text file.

Load Buses from File

Click on this button to load a listing of the buses to be included in the study system from a text file. You will be prompted to select the text file. The format of this text file is such that one bus number occupies each line. Any buses not identified in this file are defined as being in the external system.

Example

Assume you would like to create an equivalent containing all the buses in areas 1-5 and 10, plus any tie buses, and bus number 2050.

  - Since initially all buses are in the study system, first enter 1-1000 in the **Areas** field of **Add to External System**. Since the area of every bus is within this range, this places all the buses in the external system. **** Alternatively, click **Set All as External** to accomplish the same objective.
  - Set **Include how many tiers of neighbors?** to 1. This indicates that all subsequent selections will affect the specified buses and their first tier of neighbors.
  - In the **Areas** field of **Add to Study System,** enter 1-5,10. This places all the buses in these areas, plus any tie buses (since Neighbor Tiers is 1), into the study system.
  - In the **Buses** list, double-click in the **Which System** field for bus 2050 to change its status from *External* back to *Study*.

---

<a id="appending-a-case"></a>

## Appending a Case

*Source: [`Content/MainDocumentation_HTML/Appending_a_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Appending_a_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Append Case command allows you to append additional power system components to an existing case. Unlike the [Open Case](03-cases-files-and-formats.md#opening-a-simulation-case) command, Append Case does not delete the existing case (if any) before loading the selected case. To append a case to the existing case, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab and choose **Modify Case \> Append Case** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.

The Append Case command can be useful when used in conjunction with the [Equivalencing Display](#equivalents-display).

See the [Case Formats](03-cases-files-and-formats.md#case-formats) topic for information on special handling of data that occurs when appending a case using specific file formats.

---

<a id="merging-buses"></a>

## Merging Buses

*Source: [`Content/MainDocumentation_HTML/Merging_Buses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Merging_Buses.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Two or more buses can be merged to a new bus in Edit Mode with the loads, generators, and shunts of the buses merged moved to the new bus. The transmission lines among the buses merged will be deleted while the transmission lines connecting the merged buses and buses which are not selected to merge will be moved to the new bus.

To join two or more buses together using the oneline display, select at least two power system elements (at least one of them being a bus), then right click on one of the selected elements to invoke the popup menu and select **Merge selected buses**. In the Bus Merging Dialog**,** specify the buses to merge further if needed by clicking **Add** and/or **Delete** button. To add buses to merge, click **Add** and select all the needed buses in the **Choose a Bus** dialog and click **OK**. To delete from already selected buses, select the buses to delete and click the **Delete** button.

Once you have the elements to merge selected, enter the number, name, nominal voltage, zone number, area number and substation number for the new bus. These properties can be set to be the same as one of buses to merge by selecting it in the **Specify buses to merge** box and pressing the **Set new bus properties same as selected bus**.

Buses can also be merged in the [Bus Case Information Display](05-case-information-displays-by-object-part1.md#bus-display). To do so, select a cell and right click to popup the local menu. Select **Merge selected buses**. The buses to merge and the properties of the new bus can be edited in the Bus Merging Dialog.

When buses are merged from the oneline diagram, the selected buses will be joined in both the PWB case and the oneline. When buses are merged from the bus grid, the selected buses will be joined only in the PWB case but not in the oneline. This might result in bus objects not connected to bus records in the oneline.

**NOTE:**Special consideration is taken when merging buses that are part of a multi-section line. If a) all buses are part of a multi-section line, b) all buses are contiguous within the multi-section line definition (all connected in series), c) include at most only one of the two multi-section line's terminal buses, and d) the resulting merge would leave at least two remaining sections of the multi-section line, then the multi-section line record will remain defined and be modified to reflect the changes incurred by merging buses and removing line sections within the record. If ANY of the above criteria are NOT met when one or more buses within a multi-section line grouping are being merged, the merge will be performed but the multi-section line record will be removed. The actual system devices will remain (in their post-merged state) but there will no longer be a multi-section line record grouping any of the devices for multi-section line reporting.

---

<a id="splitting-buses"></a>

## Splitting Buses

*Source: [`Content/MainDocumentation_HTML/Splitting_Buses.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Splitting_Buses.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator assists you in transforming one bus into two connected buses. This process is called splitting a bus. In performing the split, the user is able to decide which equipment to keep connected to the original bus and which equipment to move to the new bus. Because this activity impacts the structure of the power flow equations, bus splitting can be performed only in [Edit Mode](01-getting-started.md#edit-mode-introduction).

To split a bus from the oneline diagram, right click on the bus you wish to split, and click **Split** **Bus** from the resulting local menu. To split a bus from the [Bus Case Information Display](05-case-information-displays-by-object-part1.md#bus-display), right-click on its corresponding record and again click **Split** **Bus** from the resulting local menu. In either case, the [Split Bus Dialog](#split-bus-dialog) will appear.

[Multi-section lines](06-object-properties-edit-mode-part2.md#multi-section-line-information) merit special consideration during bus split operations. These are the rules Simulator follows when you try to split a bus that is part of a multi-section line. If the original bus is the endpoint bus of a multi-section line and the ending line segment was transferred to the new bus, then the new bus becomes the new ending terminal of the multi-section line. If the original bus was a dummy bus of the multi-section line, and if exactly one of the branches connected to the original bus is rerouted to the new bus, then both the new bus and the original bus will be dummy buses in the reconstituted multi-section line. If neither or both of the lines connected to the original dummy bus were rerouted to the new bus, then the multi-section line definition is eliminated, since Simulator has no way to determine how the multi-section line should be redefined.

A final consideration involving bus splits is how [sequence data](27-fault-analysis.md#fault-analysis) is treated. If you have defined sequence data for fault analysis, Simulator will recalculate the sequence data for the original and new buses after the split. In this case, the zero sequence impedance for the new branch that connects the original and the new bus will be set to j0.0001.

---

<a id="split-bus-dialog"></a>

## Split Bus Dialog

*Source: [`Content/MainDocumentation_HTML/Split_Bus_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Split_Bus_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Split Bus dialog contains two sections labeled **Existing Bus** and **New Bus**. These sections enable you to designate the bus you want to split and the name and number of the new bus created by the bus split operation. If you opened the Split Bus Dialog from either the [Bus Case Information Display](05-case-information-displays-by-object-part1.md#bus-display) or an oneline diagram, the Existing Bus Name and Number fields will be read-only and will identify the bus you selected. However, if you opened the Split Bus Dialog from the **Modify Case Menu** on the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, you will first have to choose a bus to split. In this case, use the **Find…** speed button located next to the **Existing Bus** label to select the bus to split, or simply type its number in the Existing Bus Number field. Then, provide the name and number for the new bus to create using the New Bus Name and Name fields. The number you specify in the New Bus Number field must be unique; it cannot be a number that identifies another bus in the case. If you do specify an existing number, Simulator will issue an error message and require you to specify a different number. If you choose not to specify a name for the new bus, Simulator will set the name of the new bus to be the same as the bus’s number.

Once you have identified the bus to split and the name and number for the new bus resulting from the split, you may then specify whether a bus tie should be inserted between the existing bus and the soon-to-be-created new bus. By checking the **Insert bus tie between existing and new buses** checkbox, you command Simulator to place a very low-impedance bus tie between the bus to split and its offspring. The new branch will have an impedance of 0.0000 + j0.0001 ohms. If the bus tie should be inserted as an open branch, check the **Normally open** checkbox. This option becomes available, of course, only if you elect to have Simulator automatically add the new bus tie.

After you have finished making your selections, click **OK**. Simulator will create the new bus, assign its electrical attributes to match those of the existing bus, and add the bus to the power system model. If a oneline diagram is currently active and the existing bus is represented on it, Simulator will add a symbol for the new bus to the diagram, placing it immediately to the right of the existing bus’s symbol. If you elected to create a bus tie between the existing and new buses, Simulator will also add a symbol for the bus tie to the diagram.

Finally, Simulator will automatically open the [Equipment Mover Dialog](#equipment-mover) to help you manage the transfer of equipment from the existing bus to the new bus.

---

<a id="create-composite-load-models-dialog"></a>

## Create Composite Load Models Dialog

*Source: [`Content/MainDocumentation_HTML/Create_Composite_Load_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Create_Composite_Load_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The create composite load model command allows you to transform the original transmission bus load wthat has a transient stability load model of CMPLDW into a distribution equivalent inside the power flow case. To append a case to the existing case, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab and choose **Modify Case \> Create Composite Load Model...** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.

Below is a picture of how the original transmission bus load with a CMPLDW Transient Model is converted into a distribution equivalent inside the power flow case:

![Modify Case Create Composite Load 732x474](images/Modify_Case_Create_Composite_Load_732x474.gif)

When creating the new element in the power flow and calculating the parameters of the distribution equivalent the following calculations are done

The Low Side Bus will have a bus numer of 800,000 + the Original Transmission Bus number.

The Load Side Bus will have a bus numer of 900,000 + the Original Transmission Bus number.

The created load records IDs to now be "MA", "MB", "MC", "MD" for the motors, "C1" for static load, and "PE" for the electronic load.

A Distribution Equivalent MVA Base is determined based on the parameter **MVABase**.

  - If (**MVABase** \> 0) then DistEquivMVABase = **MVABase**

<!-- end list -->

  - If (**MVABase** \< 0) then DistEquivMVABase = Pinit/**MVABase**

<!-- end list -->

  - If (**MVABase** = 0) then DistEquivMVABase = Pinit/0.8;

The six impedance parameters (**Bss, Rfdr, Xfdr, Xxf, Rcmp, Xcmp**) of the Distribution Equivalent Type are assumed to be on this DistEquivMVABase and are converted the to the System MVA Base. For example, Xxf = Xxf \* SystemMVABase/DistEquivMVABase.

Transformer Taps and impedances are converted to the System MVA Base based on the fixed taps. (Note that the variable tab is assumed to be at the Low Side Bus).

  - **Xxf** = **Xxf** \* (**Tfixhs**)2

<!-- end list -->

  - **Step** = **Step**/**Tfixhs**

<!-- end list -->

  - **Tmin** = (**Tmin** + **Tfixls** - 1)/**Tfixhs**

<!-- end list -->

  - **Tmax** = (**Tmax** + **Tfixls** - 1)/**Tfixhs**

The transformer tap ratio is assumed to be set such that the voltage at the Low Side Bus is equal to the average of **Vmin** and **Vmax**. The tap ratio is then rounded to the nearest discrete step and brought back within the **Tmin** - **Tmax** range if necessary.

Using the impedances and taps now available, the Low Side Bus voltage is calculated exactly and the resulting flow on the Low Side Bus of the feeder is calculated exactly (**PLS** + j**QLS**).

We now initially assume that Bf1 and Bf2 are both zero, and from this an estimate of the resulting flow reaching the Load Bus of the feeder is calculated as **Pnew** + j**Qnew** and the resulting Load Bus Voltage as well.

If the Load Bus voltage falls below 0.95 per unit, then the feeder impedances **Rfdr** and **Xfdr** are reduced by a factor that results in a Load Bus Voltage of 0.95 per unit. (Note: if the Low Side Bus Voltage is less than or equal to 0.95, then **Rfdr** and **Xfdr** are set to the minimum impedance values of 0.0000001 + j0.00001)

The perfectly initialized voltage at the Load Bus and the values of **Pnew** + j**Qnew** cannot be immediately calculated. This is because they will depend on the initialization of the transient load model that is assigned to this load record. During the initialization of the load model the resulting extra Mvar values calculated due to motor initialization will be assigned to the feeder shunt values **Bf1** and **Bf2** according to the parameter **Fb**. In the simplest case when **Fb** = 0, all the extra Mvars are assigned at the Load Bus (**Bf2**) and thus the estimate of the voltage at the Load Bus will not change. When **Fb** \> 0 however, this means that some of the Mvars are assign to the Low Side Bus (**Bf1**) and this will slightly impact the calculation of the Load Bus voltage and the values of **Pnew** + j**Qnew**. To accommodate the splitting of this admittance the initialization routine must iteratively perform load initialization and the allocation of the split of **Bf1** and **Bf2** until it converges to a consistent solution. Throughout this iteration the restriction that the Load Bus voltage not fall below 0.95 per unit must also be maintained. This is all done internally by Simulator.

---

<a id="equipment-mover"></a>

## Equipment Mover

*Source: [`Content/MainDocumentation_HTML/Equipment_Mover.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Equipment_Mover.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator provides a convenient tool for transferring equipment between buses. Simulator allows you to move bus shunts, loads, generators, switched shunts, and transmission lines between buses. For loads, generators, and both varieties of shunts, Simulator offers you the ability to transfer all or part of the equipment from the origin bus to the destination bus.

Equipment may be transferred between buses using the Equipment Mover Dialog. The Equipment Mover Dialog can be opened in any of four ways:

  - Go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab and choose **Modify Case \< Move Bus Equipment...** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.** **
  - On the oneline display right-click on the bus from which you want to move equipment and select **Move Equipment…** from the resulting local menu.
  - From a [Bus Case Information Display](05-case-information-displays-by-object-part1.md#bus-display), right-click on the record corresponding to the bus from which you want to move equipment and select **Move Equipment …** from the resulting local menu.
  - As the final step of the [Split Bus](#splitting-buses) operation.

Regardless of the approach you take, Simulator will then open the Equipment Mover Dialog. The Equipment Mover Dialog consists of three sections. The top portion of the dialog is split in two sections that identify the bus from which equipment will be transferred (on the left) and the bus equipment will be transferred to (on the right). If the dialog was opened as the final operation of the [Split Bus](#splitting-buses) operation, these two buses will be hard-coded to identify the original bus and the bus resulting from the split. If the dialog was opened from the main menu, you must select both the origin and destination buses from lists that are reminiscent of [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays). If the dialog was opened using one of the other two methods, the origin bus will be set to the bus you selected, and you will then have to choose the destination bus. To select a bus to be an origin or destination bus, simply select the corresponding record from the appropriate list.

Once the origin and destination buses have been identified, you must then select the equipment to transfer from the origin to the destination bus using the case information display that occupies the bottom of the dialog. To move a particular piece of equipment, toggle the value of the **Move Object?** field to *YES***.** To move just portions of loads, generators, or shunts from the origin to the destination bus, adjust the value of the **Move %** field from 100.0 to the percentage you desire.

Once you have selected the equipment you wish to transfer, click the **Move equipment** button. Simulator will adjust the power system model to reflect your equipment transfer requests. Furthermore, Simulator will provide you an opportunity to manually adjust all open oneline diagrams to reflect the equipment transfers. To facilitate this activity, Simulator will open a [Potential Misplacements Dialog](#potential-misplacements-dialog) for each oneline that displays the origin bus. The Potential Misplacements Dialog lists the display objects associated with the equipment that had just been transferred from the origin to the destination bus. By clicking on an entry in this list, you can pan the associated oneline diagram to focus on that object. This allows you to identify display objects that perhaps should be relocated to reflect their new bus associations. Once you have finished addressing these potentially misplaced display objects, click the **OK** button to close the Potential Misplacements Dialog.

If you find that you would like to reopen the [Potential Misplacements Dialog](#potential-misplacements-dialog) after you have closed it, click the **List most recent transfers** button. This will reopen the Potential Misplacements Dialog associated with the most recent equipment transfer operation.

To conclude the equipment transfer operation, click the **Close** button.

---

<a id="potential-misplacements-dialog"></a>

## Potential Misplacements Dialog

*Source: [`Content/MainDocumentation_HTML/Potential_Misplacements_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Potential_Misplacements_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In the wake of an equipment transfer operation using the [Equipment Mover Dialog](#equipment-mover), some oneline display objects may be out of place. To ease the task of correcting these misplacements, Simulator provides the Potential Misplacements Dialog. Simulator opens a Potential Misplacements Dialog for each oneline that displays the bus that served as the origin for equipment transfer. The Potential Misplacements Dialog lists the display objects associated with the equipment that had just been transferred from the origin to the destination bus. By clicking on an entry in this list, you can pan the associated oneline diagram to focus on that object. This allows you to identify display objects that perhaps should be relocated to reflect their new bus associations. Once you have finished addressing these potentially misplaced display objects, click the **OK** button to close the Potential Misplacements Dialog.

---

<a id="tapping-transmission-lines"></a>

## Tapping Transmission Lines

*Source: [`Content/MainDocumentation_HTML/Tapping_Transmission_Lines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Tapping_Transmission_Lines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator eases the process of inserting a bus at some location along an existing transmission line. This feature can be extremely useful when you want to add a new generation site to a model, for example. Rather than having to delete an existing line, place the bus, and draw two new transmission lines, Simulator simplifies the task to a one-step process.

A line can be tapped from a oneline diagram, the transmission line case information display, or by going to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab and choosing **Modify Case \> Tap Transmission Line** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group. From the oneline diagram, right-click on a transmission line and select **Insert Line Tap** from the popup menu. From the [case information display](05-case-information-displays-by-object-part2.md#line-and-transformer-display), simply right-click on the corresponding branch record and select **Tap Transmission Line** from the popup menu. Any of these methods will open the [Automatic Line Tap Dialog](#automatic-line-tap-dialog) for setting up and inserting the new bus.

Note that transmission lines may be split only from [Edit Mode](11-building-onelines-network-objects.md#edit-mode-overview). You cannot access this functionality from [Run Mode](01-getting-started.md#run-mode-introduction).

---

<a id="automatic-line-tap-dialog"></a>

## Automatic Line Tap Dialog

*Source: [`Content/MainDocumentation_HTML/Automatic_Line_Tap_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Automatic_Line_Tap_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Automatic Line Tap Dialog will allow you to define the settings to use for inserting a new bus along a transmission line. The transmission line to tap will be represented in the panel at the top of the dialog, displayed as a **Near Bus** and **Far Bus**. If the Automatic Line Tap Dialog was opened by right-clicking a line on a oneline diagram, or by right-clicking on a record in the case information display, the line will already be selected in the panel. You can change the line selection by first choosing the **Near Bus** you desire, and then selecting the **Far Bus** from the list of possible connections to the chosen **Near Bus**. Note that the percentage entered in the **Position along line** field will be in relation to the selected **Near Bus**. The inserted bus and new sections of the tapped line will adhere to the following settings:

Position along line

The field labeled **Position along line** will indicate the point where you right-clicked the mouse relative to the location of the Near Bus to the mouse-click in terms of a percentage of the total line length. In other words, if the line is 10 units long, and you clicked the right mouse at location 7 units from the Near Bus end of the line, the **Position along line** will indicate 70%. If you opened the Automatic Line Tap Dialog from the case information display or the **Tools** ribbon tab, the **Position along Line** will be set to 50%. In either case, you can adjust this setting to place the new bus more precisely. The placement of the new bus controls how the impedances of the new lines are set, as the impedance of each section will equal the section’s corresponding percentage length multiplied by the impedance of the original line. Note that the original charging capacitance of the line will be reassigned as determined by the selection under the **Shunt Model** option.

New Bus Number

By default, Simulator will find and set an unused bus number for you, but you can specify the number to be used for the new bus, between 1 and 2147483647. If you enter a bus number that already exists, you will be prompted to enter a different number when you click the **Tap** button.

New Bus Name

Specify a name to be assigned to the new bus. By default this field is blank, and if left blank Simulator will set the name of the bus the same as the new bus number.

New Bus Area

You can specify the area for the new bus to be the same as the **Near Bus**, the **Far Bus**, or another value of your specification. If you select the **Specify** option, the edit box and find button will become enabled. You can then enter an area number manually, or click **Find** to locate an area from the list of areas currently in the case. If you want a new area to be assigned to the case for this bus, simply enter an unused area number manually in the box, and Simulator will automatically set up the new area record for the case. You can then open the [Area Information Display](05-case-information-displays-by-object-part1.md#area-display) and set the name and other values for the new area.

New Bus Zone

You can specify the zone for the new bus to be the same as the **Near Bus**, the **Far Bus**, or another zone of your specification. If you select the **Specify** option, the edit box and find button will become enabled. You can then enter a zone number manually, or click **Find** to locate a zone from the list of zones currently in the case. If you want a new zone to be assigned to the case for this bus, simply enter an unused zone number manually in the box, and Simulator will automatically set up the new zone record for the case. You can then open the [Zone Information Display](05-case-information-displays-by-object-part1.md#zone-display) and set the name and other values for the new Zone.

Shunt Model

Options determines how the charging B and G values of the transmission line are handled. By default, Simulator will use the long-line PI equivalent equations to determine appropriate values for B and G for the two new lines. Alternatively, you can assign the original charging capacitance as line shunts at the original terminal bus ends of the two new line segments in which case the charging capacitance of the two new branch elements will be set to 0.

Treat sections as a multi-section line

Check the box labeled **Treat sections as a multi-section line** to force the status of the two new line sections to be controlled in unison. Checking this box will cause a multi-section line to be created comprised of the two new line sections. See [Multi-Section Line Information](06-object-properties-edit-mode-part2.md#multi-section-line-information) for details.

Click the **Tap** button to close the Automatic Line Tap Dialog and perform the line tap. If a value on the dialog is not set properly, a warning message will appear, and you will need to either change the specified value or cancel the process.

---

<a id="bus-renumbering-dialog"></a>

## Bus Renumbering Dialog

*Source: [`Content/MainDocumentation_HTML/bus_renumbering_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/bus_renumbering_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Renumber Buses Display allows you to change the bus numbers for either the entire power system case, and/or for any open oneline diagrams. To show this display, while in [Edit Mode](01-getting-started.md#edit-mode-introduction), go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Renumber \> Renumber Buses** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.

The bus renumbering feature is provided because it is sometimes necessary to renumber buses in the power system model, either to make room for new buses or to move buses to a different zone or area that has a different numbering scheme. It may also be necessary to renumber bus display objects on the oneline if you want to use the oneline with a case other than the one for which it was originally designed. The bus renumbering feature provides a convenient way of accomplishing this.

The table at the bottom of the Bus Renumbering Dialog is used to manage the lists of current bus numbers and any desired changes to the numbering scheme. You can specify the bus numbers to change and their new values by directly typing them into the table. Alternatively, you can generate the bus list automatically by selecting one of the [Automatic Setup of Bus List Options](#bus-renumbering-automatic-setup-of-bus-list-options) and clicking the **Setup Bus Swap List** button. The Automatic Setup options allow you to add to the list all buses in the case, all buses in the case subject to the [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) constraints, all buses currently displayed on the oneline, or a set of numbers from a text file.

The table behaves just like a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) that can be invoked by clicking the right mouse button. Select **Insert** from the local menu to insert a new bus number to change, or select **Delete** to delete a bus number that is currently in the list. Select **Show Dialog** to display the [Bus Information Dialog](06-object-properties-edit-mode-part1.md#bus-options) corresponding to the bus number on which you right-clicked. You may clear the entire list by pressing the **Clear Bus List** button.

Once you have indicated which buses you would like to renumber in the table, select an option from **Bus Change Options** to specify where you would like to implement the changes (in both the case and the oneline, in the case only, or in the oneline only). Make the changes by pressing the **Change Bus Numbers** button. Close the dialog by pressing **Close**.

The Automatic Setup of Bus List and Bus Change options deserve further discussion. See[Bus Renumbering Options](https://www.powerworld.com/WebHelpvoid\(0\);) for further details or click [NEXT](#bus-renumbering-automatic-setup-of-bus-list-options).

---

<a id="bus-renumbering-automatic-setup-of-bus-list-options"></a>

## Bus Renumbering: Automatic Setup of Bus List Options

*Source: [`Content/MainDocumentation_HTML/Bus_Renumbering_Automatic_Setup.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Renumbering_Automatic_Setup.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This section of the [Bus Renumbering Dialog](#bus-renumbering-dialog) is used to generate automatically a list of the buses to be renumbered. Select an option from the list and click on the **Setup Bus Swap List** button to generate the list, or **Clear Bus Swap List** to clear the list.

Load All Buses in Cases

Creates entries in the table for every bus in the system. By default the new bus number is the same as the old bus number. Of course you do not have to renumber every bus. If you would like a bus to keep its same number, either add that bus to the table, or simply have an entry with the old and new bus numbers identical.

Load Buses with Valid Area/Zone Filters

Same as the **Load All Buses In Case** option except only those buses with valid [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) are added. This allows you to easily modify the bus numbers in just an area or zone.

Load Only Buses on Oneline

Creates entries in the table only for those buses on the current oneline. This option is most useful when you are just changing the buses on the onelines.

Load Buses From Text File

Creates entries in the table using an external text file. The format of this file is as follows:

1 11  Specifies converting from old bus number 1 to new bus number 11

2 22  Specifies converting from old bus number 2 to new bus number 22

etc.

Freshen Current Oneline

The Freshen Current Oneline option is designed to help you quickly renumber an existing oneline to work with a new numbering scheme. You will find this method helpful if you have been using the oneline with a case and now must use it with a different case having a different set of bus numbers, but the same bus names. Freshen Current Oneline will try to match the buses on the oneline with the buses in the new case by matching bus names and kV, rather than by number (which is how Simulator usually tries to link bus display objects with bus records in the case). The best way to learn how to use Freshen Current Oneline is to consider the following example:

To update an old oneline to work with a new bus numbering scheme:

  - Open the oneline and the old case with which it was used.
  - Choose **Renumber \>** **Renumber Buses** from the **[Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.
  - Select **Load Only Buses on Oneline** and press the **Setup Bus Swap List** button.
  - Change the **Swap?** field values all to *Yes*.
  - Right click on the table and choose **Save List to File**. Give the file a name. For this example, we'll name the file "oldscheme.txt." This file will contain the list of buses represented on the oneline, specifying each bus's number, name, kV, and area.
  - Close the old case.
  - Open the new case and the oneline you wish to renumber. If any other onelines open with the case, close them. You want only the oneline you wish to renumber to be shown.
  - Choose **Renumber \>** **Renumber Buses** from the **[Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.
  - Select **Freshen Current Oneline** and specify the file "oldscheme.txt" (for this example). Click the **Setup** **Bus** **Swap List** button. Simulator will match the old numbering scheme used in the oneline with elements in the new case by name and kV. If it finds more than one match, it will use the element's area name as a tie breaker. If it still can't reconcile the multiple matches, it will add both renumbering options to the table.
  - Go through the new list and make sure that you want to swap the buses that are listed. If you do, change the **Swap?** field value for each to *Yes* (you can do this quickly for all buses by right-clicking on the **Swap?** column and choosing **Toggle All Yes**). Be sure to reconcile any duplicate bus renumbering suggestions. These are cases for which Simulator could not determine how to renumber the buses because a bus on the diagram matches more than one bus in the case by name, kV, and area.
  - Click the **Change Bus Numbers** button at the bottom of the form.

Once the oneline has been renumbered, save it with the case by selecting **Save** **Case** (or **Save** **Case** **As** if you wish to give it a different name) from the [File menu](03-cases-files-and-formats.md#file-menu). See [Bus Change Options](#bus-renumbering-bus-change-options) for additional details.

---

<a id="bus-renumbering-bus-change-options"></a>

## Bus Renumbering: Bus Change Options

*Source: [`Content/MainDocumentation_HTML/Bus_Renumbering_Bus_Change_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Renumbering_Bus_Change_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This option is used to specify which buses to change.

Change Both Case and Onelines (default)

Renumbers the buses in both the case and any open oneline diagrams.

Change Only Case

Only renumbers the buses in the case. The oneline bus numbers are not changed.

Change Only Onelines

Only renumbers the buses on the onelines. The case itself is not changed. You would want to select this option if you have already changed the case (or loaded a different one), but now have several onelines based on that case that also need to be changed. See [Automatic Setup of Bus List Options](#bus-renumbering-automatic-setup-of-bus-list-options) for more details. This is the most commonly used option.

---

<a id="renumber-areaszonessubstations-dialog"></a>

## Renumber Areas/Zones/Substations Dialog

*Source: [`Content/MainDocumentation_HTML/Renumber_Areas_Zones_Substations_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Renumber_Areas_Zones_Substations_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Renumber Areas/Zones/Substations Dialog is available while in [Edit Mode](01-getting-started.md#edit-mode-introduction), by going to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choosing **Renumber \> Renumber Areas/Zones/Substations** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group.This dialog allows the renumbering of areas, zones, and substations for either the entire power system, and/or for any open oneline diagrams. This dialog is similar to the [Renumber Buses Dialog](#bus-renumbering-dialog).

This feature is provided because it is sometimes necessary to renumber areas, zones, or substations in the power system model, either to make room for new elements or to move elements to different area, zones, or substations that have a different numbering scheme. It may also be necessary to renumber display objects on the oneline if the oneline is used with a case other than the one for which it was originally designed. The areas/zones/substations renumbering feature provides a convenient way of accomplishing this.

The table at the bottom of the Renumber Areas/Zones/Substations Dialog is used to manage the list of areas, zones, and substations available for renumbering. This list is populated by selecting one of the **Automatic Setup of Swap List** options. The Automatic Setup options allow the addition of all areas, zones, or substations in the case or only those on the oneline. An option is also available to read the swap information from a file or to setup the swap list based on the current oneline. The **Types to Insert** option is available for specifying whether or not to add areas, zones, and substations to the swap list. Once the swap list option and types to insert have been selected, click the **Setup Swap List** to populate the table.

The table behaves just like a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) that can be invoked by clicking the right mouse button. Select one of the **Insert** options from the local menu to insert a new area, zone, or substation number to change, or select **Delete** to delete an element number that is currently in the list. The entire list may be cleared by clicking the **Clear** **Swap** **List** button. The **Present Number** for the element is specified in the list. Change the **New Number** field to specify the updated number of the area, zone, or substation.

The **Renumber Options** allows the specification of where the renumbering changes should be implemented. The changes can be applied to the power system case only, the oneline only, or both the case and the oneline.

Once the elements to renumber have been specified and the **New Number** fields have been set appropriately, implement the changes by pressing the **Renumber** button. The changes will be applied to the case and/or oneline as specified in the **Renumber** **Options**. Close the dialog by pressing **Close**.
