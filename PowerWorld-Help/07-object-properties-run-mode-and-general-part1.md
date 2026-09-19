---
title: "Object Properties — Run Mode and General (Part 1 of 2)"
part: "Viewing Case Data"
chapter_file: "07-object-properties-run-mode-and-general-part1.md"
topics: 12
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Object Properties — Run Mode and General (Part 1 of 2)

Run-mode and general property dialogs, object groups, supplemental data and data maintainers.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (12)**

- [Area, Zone, BalancingAuthority, Owner, and Substations](#area-zone-balancingauthority-owner-and-substations)
- [DataMaintainer](#datamaintainer)
- [Object Groups](#object-groups)
- [Bus Information Dialog](#bus-information-dialog)
- [Substation Information](#substation-information)
- [Generator Information](#generator-information)
- [OPF](#opf)
- [Load Information](#load-information)
- [Line/Transformer Information](#linetransformer-information)
- [Transformer Impedance Correction Tables](#transformer-impedance-correction-tables)
- [Switched Shunt Information](#switched-shunt-information)
- [Zone Information](#zone-information)

---

<a id="area-zone-balancingauthority-owner-and-substations"></a>

## Area, Zone, BalancingAuthority, Owner, and Substations

*Source: [`Content/MainDocumentation_HTML/Data_Aggregation_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Data_Aggregation_Objects.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

There are several aggregation definitions which can group together objects in a particular manner. The treatment in the data structure for these is defined here.

Area, BalancingAuthority, and Zone objects

Area, BalancingAuthority and Zone objects have the same treatment in the data structure.

Defining Area, BalancingAuthority, Zone objects

Each Bus in the model must be assigned to exactly one Area, exactly one BalancingAuthority and exactly one Zone. Note that there does not need to be any relationship at all between Area, BalancingAuthority and Zone objects. Frequently a zone is modeled as a sub-region of an area, but this does not need to be true. In most situations this is the end of the input specification, however, the objects Gen, Load, and Shunt may also be assigned to an Area, BalancingAuthority or Zone that is different than the terminal bus.

Using Area, BalancingAuthority, and Zone objects in Filtering

How the Area and Zone definitions are interpreted will depend on where they are used. For example, when filtering devices Gen, Load, or Shunt objects then they will obey any area/BA/zone assigned to the particular object, or if none is assigned they will use the area/BA/zone designation with the terminal bus.

For devices that have multiple terminals though, such as a Branch or DCTranmissionLine, then the device will be considered inside the area, BA, or zone if any of its terminals is inside. Interfaces will be inside an area, BA, or zone if any of the InterfaceElement devices are inside it.

Using Area, BalancingAuthority, and Zone objects with regard to losses on Tie-lines

When looking at which Area, BalancingAuthority, or Zone object is assigned the losses on a tie-line between two of them, then the device connecting them will have a “MeteredEnd” specified. The losses will then be assigned to the non-metered end.

Substations

Each Bus in the model can be assigned to one substation. This is not a requirement, but an option. For the purposes of filtering, an object is considered to meet the substation filter if any of the terminal buses are in the substation.

Owner

Owners are a slight modification to the aggregation concept because for some devices (Gen, Branch, Shunt), the object can be partially owned by several different Owner objects. When used with filtering the device will be considered “inside” the Owner if any part of it is owned. When showing totals such as total generation MW or Mvar, then a pro-rated portion of the generation output will be shown.

---

<a id="datamaintainer"></a>

## DataMaintainer

*Source: [`Content/MainDocumentation_HTML/DataMaintainerRecords.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DataMaintainerRecords.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

DataMaintainer was added in Version 19

DataMaintainer objects represent entities responsible for maintaining the input data for objects in the model. The DataMaintainer object serves 2 purposes

1.  When a piece of data in a case is suspected to be in error it provides contact information in the form of an email or phone number of someone to contact to ask about this data
2.  Software has features that allow a user to write out only the data that belongs to a particular DataMaintainer. This construct makes it easier to divide a case into chunks that represent the responsibility of maintaining particular data.

The following statements describe how DataMaintainers relate to other objects.

1.  Some objects can be assigned a specified DataMaintainer.
2.  Some objects may inherit their DataMaintainer from a related object.
3.  Not all object types can even be considered to belong to a DataMaintainer.
4.  Ultimately, an object can belong to only *one* DataMaintainer, and the assumption is that all fields associated with that object are the responsibility of the DataMaintainer.
5.  Caveat to statement 4: a DataMaintainer object itself can belong to another DataMaintainer. In this way groups of DataMaintainers can be created.

Each Object Type has 2 YES and NO questions based on the first two statements above.

  - Assign? Can it be assigned a DataMaintainer? YES or NO
  - Inherit? Can it Inherit its DataMaintainer from a related object? YES or NO

This gives us 4 permutations to the Assign/Inherit questions: YES/YES, YES/NO, NO/YES and NO/NO.

Specification of DataMaintainer within Software

Within PowerWorld objects there are potentially 4 different columns associated with a DataMaintainer.

  - **DataMaintainerAssign** column is the column that should be used to directly assign a DataMaintainer to a specific object. If an object does not have a DataMaintainer specified directly then this field is just blank. In addition, to clear the DataMaintainerAssign specification you can set this column to a blank string as well. Only objects that support having a DataMaintainer assigned will have this field.
  - **DataMaintainer** column is the column that will show the active DataMaintainer for the object. This will show the inherited DataMaintainer if one is available. An object that either can have the DataMaintainer assigned or can inherited the DataMaintainer will include this field.
  - (DataMaintainerInherit were added in Version 19, build on December 1, 2016)  
    **DataMaintainerInherit** column is a YES/NO field. A value of YES indicates that inheritance is allowed for this objects
      - For objects listed below which do not allow Inheritance, this field is not enterable and will always show NO.
      - For objects below which AlwaysInherit, this field will also not be enterable and will always show YES.
      - For the small list of objects such as Bus, Gen, Load, Shunt, LineShunt, Branch, 3WXFormer, DFACTS, DCTransmissionLine, MTDCRecord and VSCDCLine which can have their own DataMaintainer assigned, but also can inherit the DataMaintainer, then this field will be enterable and the user may toggle the value between YES or NO. Setting the value to NO will prevent these objects from inheriting a DataMaintainer. See the **purple** dots in the image below for an indication of objects which can toggle this field.
  - DataMaintainerInheritBlock were added in Version 19, build on December 1, 2016)  
    **DataMaintainerInheritBlock** column is a YES/NO field only available for a Bus and a Substation record. See the thick dashed **pink** lines around the incoming inheritance arrows that represent this below.
      - For a Bus, set to YES to block the inheritance of the Data Maintainer for other objects connected to this bus. For example, if this is YES, generators at this bus will not inherit the Data Maintainer from this bus.
      - For a Substation, set to YES to block the inheritance of the Data Maintainer for the buses in this substation.

Objects that don't support DataMaintainer (NO/NO)

There is no need to discuss the NO/NO permutation, but generally these are objects representing one of the following 4 types of ObjectTypes.

1.  Solution options (CTG\_Options, SimSolution\_Options, etc.)
2.  Environment options (RatingSetNameBus, RatingSetNameBranch, etc.)
3.  Objects that are dynamically created and maintained by the software (Island, ZoneTieLine, AreaTieLine, SuperBus)
4.  Results of a software calculation (ViolationCTG)

Objects to Which DataMaintainer can be assigned, but Inheritance is not allowed (NO/YES)

The following is a list of ObjectTypes that can be assigned a DataMaintainer but never Inherit their DataMaintainer from another object (YES/NO).

Area, BalancingAuthority, BGCalculatedField, Contingency, CTGElementBlock, CustomExpression, CustomExpressionStr, CustomMonitor, DataMaintainer, DFACTSCorrection, Direction, DistributionEquivalent, Filter, GlobalContingencyActionsElement, InjectionGroup, Interface, LimitSet, LoadModelGroup, ModelCondition, ModelExpression, ModelFilter, ModelStringExpression, Owner, PlayIn, RemedialAction, StudyMWTransactions, Substation, SuperArea, TSContingency, TSLimitMonitor, VoltageControlGroup, XFCorrection, Zone

Objects that Can Inherit a DataMaintainer (YES/NO and YES/YES)

Adding the ability for objects to inherit their DataMaintainer may seem to add complexity to the concept of a DataMaintainer. However, it is actually crucial to the use the DataMaintainer. This is because without it, it would require every single data record to be assigned a DataMaintainer independently, which would greatly increase the workload for those adding this new assignment. What we expect to occur instead is that each substation in the model will be assigned a DataMaintainer and that the vast majority of network objects will then simply inherit their DataMaintainer definition from the substation. Even if substations are not added to the models, the DataMaintainer could be assigned to a Bus with inheritance occurring from there.

With this explanation for why the inheritance of DataMaintainers is vital, we now cover the final 2 other permutations (YES/YES and NO/YES). For the more complex relationships obtained from the network topology, the following picture illustrates how this inheritance is handled. Boxes which are shaded in light orange represent ObjectTypes which Always Inherit, while boxes that are not shaded represent ObjectTypes which can have a DataMaintainer assigned.

![DataMaintainer Inheritance 771x425](images/DataMaintainer_Inheritance_771x425.png)

This information can always be obtained from within PowerWorld Simulator by going to the Windows ribbon tab and choose Export Case Object Fields \> Send to Excel. In the table exports, in the row representing the ObjectType there are columns which show whether Data Maintainers are supported and whether Data Maintainer Inheritance is supported and how. The table below shows a summary of the objects that existed as of November 2015 in PowerWorld Simulator 19, when the DataMaintainer object was first added. The columns in this table are the ObjectType, whether it can be assigned a DataMaintainer, and finally a precedence of how it inherits its DataMaintainer from a related object.

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td><p>ObjectType</p></td>
<td><p>Data Maintainer Support</p></td>
<td><p>Data Maintainer Inheritance Precedence</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>3WXFormer</p></td>
<td><p>YES</p></td>
<td><p>1. Primary Bus</p>
<p>2. Primary Bus’ Substation</p>
<p>3. Secondary Bus</p>
<p>4. Secondary Bus’ Substation</p>
<p>5. Tertiary Bus</p>
<p>6. Tertiary Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>AreaContingencyReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Area</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>AreaOperatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Area</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>AreaRegulatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Area</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Branch</p></td>
<td><p>YES</p></td>
<td><p>1. NonMetered Bus</p>
<p>2. NonMetered Bus’ Substation</p>
<p>3. Metered Bus</p>
<p>4. Metered Bus’ Substation</p>
<p>(except for windings of a 3WXFormer which inherit from the 3WXFormer)</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Bus</p></td>
<td><p>YES</p></td>
<td><p>Substation</p>
<p>(except for star buses of 3WXFormer which inherit from the 3WXFormer)</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Condition</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Filter</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>ContingencyElement</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Contingency</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>ContingencyMonitoringException</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Contingency</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>CTGElementBlockElement</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>CTGElementBlock</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>DCTransmissionLine</p></td>
<td><p>YES</p></td>
<td><p>1. Rectifier Bus</p>
<p>2. Rectifier Bus’ Substation</p>
<p>3. Inverter Bus</p>
<p>4. Inverter Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>DFACTS</p></td>
<td><p>YES</p></td>
<td><p>1. Branch</p>
<p>2. Branch’s NonMetered Bus</p>
<p>3. Branch’s NonMetered Bus’ Substation</p>
<p>4. Branch’s Metered Bus</p>
<p>5. Branch’s Metered Bus’ Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Gen</p></td>
<td><p>YES</p></td>
<td><p>1. Bus</p>
<p>2. Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>GenBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. Generator</p>
<p>2. Generator’s Bus</p>
<p>3. Generator’s Bus’ Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>InterfaceElement</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Interface</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>LineShunt</p></td>
<td><p>YES</p></td>
<td><p>1. Bus</p>
<p>2. Bus’ Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Load</p></td>
<td><p>YES</p></td>
<td><p>1. Bus</p>
<p>2. Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>LoadBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. Load</p>
<p>2. Load’s Bus</p>
<p>3. Load’s Bus’ Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>ModelConditionCondition</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>ModelCondition</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>ModelFilterCondition</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>ModelFilter</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>MTDCBus</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. MTDCRecord</p>
<p>2. MTDCRecord’s VConv_Bus</p>
<p>3. MTDCRecord’s VConv_Bus’s Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>MTDCConverter</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. MTDCRecord</p>
<p>2. MTDCRecord’s VConv_Bus</p>
<p>3. MTDCRecord’s VConv_Bus’s Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>MTDCRecord</p></td>
<td><p>YES</p></td>
<td><p>1. Voltage Controlling Converter Bus</p>
<p>2. Voltage Controlling Converter Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>MTDCTransmissionLine</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. MTDCRecord</p>
<p>2. MTDCRecord’s VConv_Bus</p>
<p>3. MTDCRecord’s VConv_Bus’s Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PartPoint</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>InjectionGroup</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>PlayInInfo</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>PlayIn</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PlayInSignal</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>PlayIn</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>PVPlotSeries</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>PVPlot</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>PVPlotVertAxisGroup</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>PVPlot</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>PVSubPlot</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>PVPlot</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>ReactiveCapability</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>1. Generator</p>
<p>2. Generator’s Bus</p>
<p>3. Generator’s Bus’ Substation</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>RemedialActionElement</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>RemedialAction</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>SGPlotSeries</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SGPlot</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>SGPlotVertAxisGroup</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SGPlot</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>SGSubPlot</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SGPlot</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Shunt</p></td>
<td><p>YES</p></td>
<td><p>1. Bus</p>
<p>2. Bus’ Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>StudyMWTransactionsBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>StudyMWTransactions</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>SuperAreaContingencyReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SuperArea</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>SuperAreaOperatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SuperArea</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>SuperAreaRegulatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>SuperArea</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>SupplementalDataContainedObject</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>MyObject</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>TSContingencyElement</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>TSContingency</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>TSPlotSeries</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>TSPlot</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>TSPlotVertAxisGroup</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>TSPlot</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>TSSubPlot</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>TSPlot</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>VSCDCLine</p></td>
<td><p>YES</p></td>
<td><p>From/To_Bus&gt;Substation</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>ZoneContingencyReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Zone</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>ZoneOperatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Zone</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>ZoneRegulatingReserveBid</p></td>
<td><p>AlwaysInherit</p></td>
<td><p>Zone</p></td>
</tr>
</tbody>
</table>

---

<a id="object-groups"></a>

## Object Groups

*Source: [`Content/MainDocumentation_HTML/ObjectGroups.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ObjectGroups.htm)*

\[ObjectGroups were added in Version 24\]

ObjectGroups are groupings of objects which can be used for various reporting and filtering in Simulator.

  - ObjectGroups provide a mechanism to show summary information on groups of objects, such as generation MW or load MW summations.

  - An ObjectGroup can be used as a [Device Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-device) on a table to show all the objects that are "contained" in the ObjectGroup (this works on any case information display, or in various [Auxiliary File Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux). Also see the [Auxiliary Format Description](https://www.powerworld.com/WebHelp/Content/Other_Documents/Auxiliary-File-Format.pdf) for a discussion of using Device Filters.

The best way to create and interact with ObjectGroups is to go to the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) choose Aggregations\\Other Aggregations\\Object Groups. This will open a dialog that looks as follows.

![ObjectGroups ModelExplorer](images/ObjectGroups_ModelExplorer.png)

ObjectGroups listed by Name:

ObjectGroups are listed at the top by Name. The Name is the key field for an ObjectGroup. There are also various built-in summary fields available for the objects **contained by** the ObjectGroup which can be investigated by looking at [Configuring the Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays). If you have additional summary fields you would like made available, please email support@powerworld.com to ask. In addition, you can create user-defined calculations across the contained objects by creating [Calculated Fields](04-model-explorer-and-case-information-part1.md#calculated-fields) definitions and using these as columns for an ObjectGroup.

When using ObjectGroups it is important to understand the difference between an object being **assigned** to a group and an object being **contained** by a group. There are tabs to show **Assignments to** and **Contained by** which are related to this.

Assignments to \[South\] - Assigning Object to an ObjectGroup

This tab has a large number of tabs for objects tabs that can be **assigned** to the ObjectGroup: Bus, Generator, Load, etc... and also a Aggregations tab under which more tabs are available for Substation, Area, Zone, etc... Each of these tabs will contain a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) listing rows of that object type. When the checkbox **Show only objects that have been assigned to a group** is checked, then the case info displays are automatically filtered to only show those objects that have been assigned to the selected ObjectGroup (South in the example above). Objects that can be assigned to an ObjectGroup include Bus, Gen, Load, Shunt, LineShunt, Branch, 3WXformer, DCLine, Substation, Area, Zone, Owner, BalancingAuthority, Interface, BusPair, InjectionGroup, and some others. If you ever find an object type in PowerWorld that does not support assignment to an ObjectGroup and you would like to have that ability, please email support@powerworld.com.

The first two columns will default to ObjectGroup and ObjectGroup Append. These are used to assign objects to ObjectGroups. These columns can be [added to any case information display](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) of an object type that can be assigned to an ObjectGroup, but they are only default columns on these tables.

<table>
<tbody>
<tr class="odd">
<td><p>ObjectGroup\Append Names</p>
<p>This field always shows a blank, but when a string is entered into this field, then the object is added to the group with that name. If the group does not exist then a new group is created. You may also enter a comma-delimited list of Names to assign one object to multiple ObjectGroups</p>
<p>ObjectGroup\Assign Names</p>
<p>This field show a comma-delimited list of the names of all ObjectGroups to which an object has been assigned. Objects can belong to any number of groups. When editing this field it will change all ObjectGroups to which the object is assigned. If you want to add one object to one ObjectGroup it is easier to use the <strong>Append Names</strong> field.</p></td>
<td><img src="images/ObjectGroup_Assignments.png" alt="ObjectGroup Assignments" /></td>
</tr>
</tbody>
</table>

Contained by \[South\] - List of Objects Contained by an ObjectGroup

This tab has the same set of tabs as the **Assignments To** Tab, however instead it will show [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) with a list of all objects that are **contained by** the selected ObjectGroup.

Objects that are not directly <span class="underline">assigned</span> to an ObjectGroup can still be **contained** by the ObjectGroup by inheriting containment from the underlying structure of the power system model. For example, consider an ObjectGroup named "MyGroup" with several Areas in the case assigned to "MyGroup". When this ObjectGroup is used as a Device Filter on a list of Areas, the list will only show those Areas that have been assigned to MyGroup. However, if the ObjectGroup is used as a Device Filter on a list of Generator objects, then the list will show any generator that is contained in one of the Areas in MyGroup. The concept of "assigned to" is restricted to exactly what the user defines, while the concept of "contained by" will inherit from the built-in object structure defined in the power system data structure. This is the same behavior used with [Supplemental Data objects](15-using-onelines-tools-and-options.md#supplemental-data) when they are configured to **Inherit**=YES. ObjectGroups are little simpler to use because you don't need to define the classification as you do with Supplemental Data objects, and also assigning an Object to an ObjectGroup that doesn't exist yet just automatically creates a new group. ObjectGroups behave the same way that as SupplementalClassification configured with **Inherit**=YES, **Multiple** = YES, and both **Contain** and **Assign** set to all power-system related model objects. See the [Supplemental Data](15-using-onelines-tools-and-options.md#supplemental-data) for more description of this.

---

<a id="bus-information-dialog"></a>

## Bus Information Dialog

*Source: [`Content/MainDocumentation_HTML/Bus_Information_Dialog_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Information_Dialog_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view information about each bus in the system. It can be displayed by right-clicking on any bus on the oneline and choosing **Bus Information Dialog** or choosing **Show Dialog** from the [Bus Display](05-case-information-displays-by-object-part1.md#bus-display). This dialog can only be reached in Run Mode, but has a similar [Edit Mode](06-object-properties-edit-mode-part1.md#bus-options) counterpart. The Bus Information Dialog has the following fields:

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus. You can use the small arrow immediately to the right of the number to view a list of all buses in the case with valid [display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Or you can use the spin button further to the right of the number to move to the next bus (click the up arrow) or the previous bus (click the down arrow).

Find By Number

To find a bus by its number, enter the number into the **Bus Number** field and then click this button.

Bus Name

Unique alphabetic identifier for the bus. You can use the small arrow immediately to the right of the bus name to view a list of all bus names in the case with [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Find By Name

To find a bus by its name, enter the bus name into the **Bus Name** field (case insensitive) and then click this button.

Find…

If you do not know the exact bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Nom. Voltage

Nominal voltage of the bus.

Labels

Clicking on this button will open the [Label Manager dialog](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) listing all of the labels assigned for the selected bus.

Area Number, Name

Each bus is associated with an Area record. These fields show the number and name of this area. See [Area Records Display](05-case-information-displays-by-object-part1.md#area-display) for more details about areas.

Zone Number, Name

Each bus is associated with a Zone record. These fields show the number and name of the zone. See [Zone Records Display](05-case-information-displays-by-object-part1.md#zone-display) for more details about zones. You can also use the [Zone Dialog](06-object-properties-edit-mode-part3.md#zone-information) to list the buses in a particular zone and to easily move a group of buses from one zone to another.

Substation Number, Name

Each bus can be associated with a Substation record. By default, buses are not assigned to substations, and in that case these fields are blank. See the [Substation Records Display](05-case-information-displays-by-object-part1.md#substation-records-display) topic for more details on adding substations.

Owner Number, Name

Each bus is associated with an Owner record. These fields show the number and name of the owner. See [Owner Records Display](05-case-information-displays-by-object-part3.md#owner-data-information-display) for more information about Owners.

Voltage (per unit)

Bus voltage in per unit notation. You may enter a new per unit voltage magnitude. However, the only effect this has is changing the initial voltage guess used in the iterative solution. If you would like to change the reference voltage for a generator, please see [Generator Information Dialog](#generator-information).

Voltage (kV)

Bus voltage in actual kilovolts.

Angle (deg) and Angle (rad)

Voltage angle at the bus in degrees and radians. You may enter a new voltage angle. However, the only effect this has is changing the initial voltage guess used in the iterative solution EXCEPT AT THE SLACK BUS. Changing the angle for the slack bus will shift the voltage angle for all the buses in the slack bus' island by a similar amount.

Status

Status of the bus, either connected or disconnected. A disconnected bus is not energized. You can use this field to change the status of the bus. When the bus is initially connected, selecting **Disconnected** opens all of the transmission lines incident to the bus, disconnecting the bus from the rest of the system. Selecting **Connected** closes all of the lines incident to the bus unless they attach to another disconnected bus.

View Substation Dialog

Clicking on this button will open the [substation dialog](#substation-information) for the substation the bus is contained in.

View Owner Dialog

Clicking on this button will open the bus’ [owner dialog](05-case-information-displays-by-object-part3.md#owner-dialog).

Slack Bus

Checked only if the bus is a system slack bus. This value can only be changed in the Edit Mode.

View All Flows at Bus

Clicking on this button will open a [quick power flow list](05-case-information-displays-by-object-part1.md#quick-power-flow-list) for the current bus.

Device Info

Generator Information

Displays the total MW and Mvar generation at the bus. You cannot change either of these fields from this display. Select **View/Edit Generator Records** to view the individual generator records for the bus. Selecting this button displays the [Generator Dialog](#generator-information) for the first generator at the bus.

Load Information

Displays the total MW and Mvar load at the bus. You cannot change either of these fields from this display. Select **View/Edit Bus Load Records** to view the individual load records for the bus. Selecting this button displays the [Load Dialog.](#load-information)

Shunt Admittance

Shows the real and reactive components of the shunt admittance to ground. Entered in either MW or Mvar, assuming one per unit voltage. B is positive for a capacitor and negative for a reactor. If B corresponds to a switched device, consider using a [switched shunt](#switched-shunt-information).

Bus Voltage Regulation

This section lists the devices (if any) that are controlling the voltage at the bus. Select **Bus Voltage Regulator Devices** to view the individual devices regulating the voltage for the bus. Selecting this button displays the [Bus Voltage Regulating Devices Dialog.](06-object-properties-edit-mode-part1.md#bus-voltage-regulating-devices)

Desired PU Voltage

If the bus is being regulated by one or more devices, this field will display the desired regulated voltage (in per unit) the devices are attempting to maintain.

Fault Analysis Load Parameters

This page of the display is only available for buses which have one or more load attached to the bus. The parameters on this tab are used when running a fault analysis study. The values represent the total load at the bus for the negative and zero sequence as equivalent admittances. By default, these values are zero. For load buses, these values can be changed by the user, or they can be specified by loading short circuit data from within the [Fault Analysis Dialog](27-fault-analysis.md#fault-analysis-dialog). It is also possible to define these values as non-zero at a bus where no load exists in the load flow, but it is not usually desirable to do so.

OPF

This tab is only available if you have the Optimal Power Flow (OPF) add-on tool for PowerWorld Simulator. This tab displays the MW marginal cost (Locational Marginal Price) for the bus when performing an OPF solution. The page also breaks down the LMP into its cost components.

Geography

The Geography page of the dialog provides information on the geographic location of the bus on the currently active oneline diagram. Also it provides a conversion tool between [Lat/Lon and UTM Coordinates](07-object-properties-run-mode-and-general-part2.md#latitudelongitude-and-utm-coordinates-conversion).

Custom

The Custom page of the dialog contains two sections: custom fields and memo. 

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the bus. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the bus. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

---

<a id="substation-information"></a>

## Substation Information

*Source: [`Content/MainDocumentation_HTML/Substation_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used in the Run Mode to view and modify information associated with a substation record. It displays different information from the [Edit Mode](01-getting-started.md#edit-mode-introduction) version of the [substation dialog](06-object-properties-edit-mode-part1.md#substation-information). To display it from [Run Mode](01-getting-started.md#run-mode-introduction), first select **Aggregation \> Substations** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to bring up the [Substation Records Display](05-case-information-displays-by-object-part1.md#substation-records-display). Right-click on the substation of interest and choose **Show Dialog**. The Run Mode Substation Dialog has the following fields:

Substation Number

An integer identifier for the substation. You can use the spin button immediately to the right of this field to move to either the next substation (click the up arrow) or the previous substation (click the down arrow).

Substation Name and ID

Two alphanumeric identifiers for the substation.

Find By Number

To find a substation by its number, enter the number into the **Substation Number** field, then click this button.

Find By Name

To find a substation by its name, enter the name into the **Substation Name** field, then click this button.

Find By Sub ID

To find a substation by its substation ID, enter the ID into the **Substation ID** field, then click this button.

Find…

If the exact substation number, name and ID are not known, you can use the [Find Dialog](04-model-explorer-and-case-information-part3.md#find-dialog-basics) to search for and select a substation from a list of substations.

Labels

Clicking this button will open a dialog displaying the list of defined labels for the substation. New labels can also be added for the substation from the dialog as well.

View All Flows at Substation

Clicking this button will open a [quick power flow display](05-case-information-displays-by-object-part1.md#quick-power-flow-list) listing the buses contained in the substation.

Information

Load and Generation

Real and reactive load, generation, shunts, losses, and interchange for the substation.

Bus Voltages

Summary information on all buses in the substation, including total number of buses, number of dead (disconnected) buses, and minimum and maximum bus voltage and angle within the substation.

Available Gen MW/Mvar Ranges

Total amount of generation increase or decrease available for all generators in the substation.

Buses

The Buses table identifies the buses in the substation, and provides summary information on each.

Gens

The Gens table identifies the generators in the substation, and provides summary information on each.

Loads

The Loads table identifies the loads in the substation, and provides summary information on each.

Switched Shunts

The Switched Shunts table identifies the switched shunts in the substation, and provides summary information on each.

Tie Lines

The Tie Line Table identifies the flows on all of the substation's ties to other substation.

Custom

This page of the dialog can be used to enter notes about the substation. Any information entered in the memo box will be stored with the case when the case is saved to a PWB file. Custom fields can also be entered for storage with the substation object viewed.

Geography

Displays geographic information about the location of the substation, in Latitude and Longitude. Also it provides a conversion tool between [Lat/Lon and UTM Coordinates](07-object-properties-run-mode-and-general-part2.md#latitudelongitude-and-utm-coordinates-conversion).

---

<a id="generator-information"></a>

## Generator Information

*Source: [`Content/MainDocumentation_HTML/Generator_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to view information about each generator in the system. Many fields on this display can also be changed (except in Viewer). Here we describe the Run Mode version of the Generator Information Dialog. The [Edit Mode](06-object-properties-edit-mode-part1.md#generator-information) version is very similar.

Bus Number

Unique number between 1 and 99,999 used to identify the bus to which the generator is attached. The dropdown list enumerates all generator buses in the case that meet the criteria established by [display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). You may select a bus number directly from the dropdown list, or you may use the spin buttons to cycle through the list of generator buses.

Bus Name

Unique alphabetic identifier for the bus to which the generator is attached, consisting of up to eight characters. Use this dropdown box to view a list of all generator bus names in the case with [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

Two character alphanumeric ID used to distinguish multiple generators at a bus; '1' by default.

Find By Number

To find a generator by its number and ID, enter the number into the **Bus Number** field and the ID into the **ID** field. Then click the **Find By Number** button.

Find By Name

To find a bus by its name and ID, enter the bus name into the **Bus Name** field (case insensitive) and the ID into the **ID** field. Then click the **Find By Name** button.

Find…

If you do not know the exact generator bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Status of the generator, either Closed (connected to terminal bus) or Open (not connected). You can use this field to change the status of the generator.

Energized

Indicates if the generator is energized. This is not the same as the Open or Closed status. A generator may be in-service itself (closed) but not be energized, based on the statuses of other devices around the generator. For example, in a full topology model, it is not uncommon for a generator to have a status of Closed, but the generator is not energized if a branch of type Circuit Breaker connecting the generator to the system has a status of Open.

Area Name

Name of the area in which the generator's terminal bus is located.

Labels

Clicking on this button will open the [Subscribed Aliases dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the labels or aliases assigned for the selected generator.

Same Owner as Terminal Bus

Read-only check-box that indicates whether the generator’s owner is the same than the terminal bus’ owner.

Fuel Type

Type of fuel used by the generator this model represents. In most cases, this field is unnecessary for normal load flow analysis, and hence the default value is Unknown. However, this value can be useful during the [Security Constrained OPF](31-scopf-and-opf-reserves.md#security-constrained-opf-overview) analysis.

Unit Type

The type of unit the generator represents, such as combined cycle, steam, hydro, etc.

There additional sections of generator information available from the Run Mode generator dialog:

[Power and Voltage Control](06-object-properties-edit-mode-part1.md#power-and-voltage-control)

[Generator Cost Information](06-object-properties-edit-mode-part1.md#costs)

[OPF](#opf)

[Fault Parameters](06-object-properties-edit-mode-part1.md#fault-parameters)

[Owner, Area, Zone, Sub](06-object-properties-edit-mode-part1.md#owners-area-zone-sub)

[Custom](01-getting-started.md#memo-display)

[Stability](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs)

---

<a id="opf"></a>

## OPF

*Source: [`Content/MainDocumentation_HTML/Generator_Information_OPF.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Information_OPF.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The fields on this tab display information regarding the generator’s participation in an OPF load flow solution.

OPF MW Control

The type of control the generator is allowed during an OPF solution. The generator can be set to No control during OPF, control only if its AGC property is set to Yes, or to always be controlled by the OPF regardless of the AGC status of the generator.

Fast Start Generator

The generator is being treated as a fast start generator during the OPF solution.

Generator MW limits

The MW limits of a generator can be altered in this location if you wish for the generator to use different limits than originally assigned in the load flow case, without actually changing the original values. Simply change the Current Min MW Limit and Current Max MW Limit to alter the limits observed by the generator during and OPF solution.

MW Marginal Cost for Generator’s Bus

The OPF solved marginal cost at the generator’s terminal bus.

Initial, Final and Delta MW Output

The MW output information for the generator resulting from the OPF run.

Initial, Final and Delta Hourly Cost

The hourly cost information for the generator resulting from the OPF run.

OPF Results

This section shows the results of OPF for the generator.

---

<a id="load-information"></a>

## Load Information

*Source: [`Content/MainDocumentation_HTML/Load_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Load_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Load Information Dialog can be used to inspect and modify the model of a bus load. To view the Load Information Dialog, select the load and choose **Show Dialog** from the [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) or right-click on the load of interest and select **Load Information Dialog** from the resulting local menu. This is very similar to its [Edit Mode](06-object-properties-edit-mode-part1.md#load-options) counterpart. The dialog has the following fields:

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus to which the load is attached. The dropdown box provides a list of all load buses with [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). You can use the spin button to cycle through the list of load buses.

Bus Name

Unique alphabetic identifier for the bus to which the load is attached, consisting of up to eight characters. The dropdown box lists the names of all load buses in the case with [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

ID

Two-character ID used to distinguish multiple loads at a bus. By default, the load id is equal to "1 ." An identifier of '99' is used to indicate an equivalent load.

Find By Number

To find a load by its number and ID, enter the number into the Bus Number field and the ID into the ID field. Then click this button.

Find By Name

To find a load by its name and ID, enter the bus name into the Bus Name field (case insensitive) and the ID into the ID field. Then click this button.

Find…

If you do not know the exact load bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Status of the load, either Closed (connected to terminal bus) or Open (not connected). You can use this status field to change the load's status.

Energized

Indicates if the load is energized. This is not the same as the Open or Closed status. A load may be in-service itself (closed) but not be energized, based on the statuses of other devices around the load. For example, in a full topology model, it is not uncommon for a load to have a status of Closed, but the load is not energized if a branch of type Circuit Breaker connecting the load to the system has a status of Open.

Labels

Clicking on this button will open the [Label Manager](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) dialog listing all the labels assigned for the selected load.

Area Number, Area Name

Number and name of the area the load is a member of.

Zone Number, Zone Name

Number and name of the zone the load is a member of.

Owner Number, Owner Name

Number and name of the owner the load is a member of. Loads DO NOT have to be owned by the same owner as the terminal bus.

Substation Number, Substation Name

Number and name of the substation the load is a member of.

Load Information 

Base Load Model, Current Load

The Base Load Model fields are used to represent the amount of base real and reactive load at the bus. Usually this load is modeled as being "constant power," meaning that the amount of load is independent of the bus voltage magnitude. However, Simulator also permits modeling "constant current" load, for which the load varies in proportion to the bus voltage magnitude, and "constant impedance" load, for which the load varies in proportion to the square of the bus voltage magnitude. Values in these fields are specified in MW and MVR assuming one per unit voltage. All six fields in the Base Load Model section can be changed.

Distributed Generation

Added in Version 19 Distributed Generation MW and Mvar values may be specified with each load record. These values are only used when the Distributed Generation status is set to Closed. When Closed then this represent the distributed generation MW and Mvar represented inside this load. When this is in use, then the net MW and Mvar seen by the power flow solution algorithm will be equal to the Base Load Values minus the Distributed generation.

The Net MW Load is then NetMW=MW - DistMW and NetMvar = Mvar - DistMvar

Load Multiplier

The actual load at the bus is equal to the base value multiplied by the corresponding load multiplier. The load multiplier is a value specifying how the load is scaled. The load multiplier depends upon the area load multiplier and the zone load multiplier. See [Load Modeling](06-object-properties-edit-mode-part1.md#load-modeling) for more details. The load multiplier value cannot be changed on this dialog.

Bus Voltage Magnitude

Voltage magnitude of the load’s terminal bus.

Information about the remaining tabs on the dialog can be found at the following links:

[OPF Load Dispatch](06-object-properties-edit-mode-part1.md#opf-load-dispatch)

[Custom](01-getting-started.md#memo-display)

[Stability](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs)

---

<a id="linetransformer-information"></a>

## Line/Transformer Information

*Source: [`Content/MainDocumentation_HTML/Line_Transformer_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Transformer_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Branch Information Dialog is used to view information about each transmission line and transformer in the system. You may use this dialog also to change many of the properties of lines and transformers (except in Viewer). From this dialog, you can also open dialogs for attached devices.

The Run Mode version of this dialog is very similar in content to its [Edit Mode](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) counterpart.

The Branch Information Dialog sports the following fields:

From Bus Number and Name

*From Bus* number and name. For transformers, the *from bus* is the tapped side.

To Bus Number and Name

*To Bus* number and name.

Circuit

Two-character identifier used to distinguish between multiple lines joining the same two buses. Default is '1'.

Find By Number

To find a line or transformer by its bus numbers, enter the *from* and *to* bus numbers and the circuit identifier. Then click this button. Use the spin button to cycle through the list of lines and transformers in the system.

Find By Name

To find a line or transformer by the names of its terminal buses, enter the *from* and *to* bus names and the circuit identifier. Then click this button.

Find…

If you do not know the exact from and to bus numbers or names you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

From End Metered

This field is only used for lines and transformers that serve as tie lines, which are lines that join two areas. If this field is checked for a tie line, the *from* end of the device is designated as the metered end. Otherwise the *to* end is metered. By default, the *from* end is metered. The location of the metered end is important in dealing with energy transactions because it determines which party must account for transmission losses.

From and To Bus Area Name

Names of the areas in which the From and To buses are located.

From and To Bus Nominal kV

From and To bus nominal voltage levels.

From and To Bus Voltage (p.u.)

The actual terminal bus voltages of the transmission element, in per unit.

Labels

Clicking on this button will open the [Labels dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the labels for the selected branch.

Parameters

Status

Current status of the device.

Energized

Indicates if the branch is energized. This is not the same as the Open or Closed status. A branch may be in-service itself (closed) but not be energized, based on the statuses of other devices around the branch. For example, in a full topology model, it is not uncommon for a branch of type Line has a status of Closed, but the branch is not energized if branches of type Circuit Breaker at both ends of the Line are Open.

Per Unit Impedance Parameters

The resistance, reactance, the total charging susceptance (that is, B, not B/2), and the total shunt conductance of the device (in per unit). Magnetizing conductance and susceptance is included if the branch is a transformer.

Line Shunts

Select to view the [Line Shunt](06-object-properties-edit-mode-part2.md#line-shunts-information) Dialog. This dialog is used to create or modify line shunts. Line shunts cannot be created or deleted while in Run Mode. Line shunts are expressed in terms of the per-unit conductance and susceptance at each end of the line or transformer. If the line has shunts, the check box **Has Line Shunts** is checked.

MVA Limits

Ratings for the transmission line or transformer in MVA. Eight different limits are allowed.

Flows

These next fields show the actual real and reactive power flow at both ends of the device (because of real and reactive losses these numbers may be different), and its percentage MVA loading. The line losses are summarized as well.

D-FACTS Devices on the Line

Select to view the [D-FACTS Information](05-case-information-displays-by-object-part3.md#d-facts-settings-dialog) dialog. This dialog is used to create or modify [D-FACTS devices](05-case-information-displays-by-object-part2.md#d-facts-devices) on the line.

Transformer

The tab is only visible if the branch is a transformer. See the [Transformer Control](06-object-properties-edit-mode-part2.md#transformer-control) help for more information on transformer types and controls.

Series Capacitor

This tab is only visible if the selected branch is a series capacitor. If the branch is a series capacitor, the **Is Series Capacitor** box will be checked. In addition, the **Status** field for series capacitors will be enabled, allowing you to change the Bypassed or In Service status of the series capacitor. The series capacitor status IS NOT the same as the branch status of Open or Closed.

OPF

The OPF tab is only visible if you have the OPF ([Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)) add-on tool for PowerWorld Simulator.

Enforce Line Flow Limit

This check box must be checked if the branch limit is going to be enforced when running an OPF solution. If this box is not checked, the OPF routine will allow the branch to violate its branch limits.

Treat Limit as Equality Constraint

If checked, the OPF solution will attempt to solve the load flow while keeping the flow on the branch at its limit.

Maximum MVA Flow

The largest MVA flow value measured on the line, either at the From or To bus.

Present MVA Limit

The limit enforced by the OPF for the branch. This is set in the [OPF constraint options](30-optimal-power-flow-part1.md#opf-options---constraint-options), and is related to the original branch limits.

Maximum Percentage

The highest percentage of flow measured on the line, either at the From or To bus.

Limit Marginal Cost

The cost of enforcing the branch MVA limit.

Included in LP

Specifies whether or not the branch flow and limit was included as a constraint in the OPF solution. In general, branches that are not near their limit and do not appear to be changing flow dramatically towards their limit will be ignored in the OPF calculation to speed up the solution. **No** and **Yes** indicate whether or not the OPF process determined that the line needed to be included. The user can initially force the branch to be included or not included with these two fields. By choosing **Always**, the branch will be included in the OPF solution constraints regardless of the propensity of the line to be approaching it's limit.

MVA Flow Constraint Status

The constraint status for the line in the OPF solution will be shown here with the corresponding boxes checked by Simulator. These check boxes cannot be changed manually by the user.

From/To Bus MW Marginal Costs

Displays the marginal costs of the branches terminal buses, following the solution of the OPF.

Fault Info

The parameters on this tab are used when running a [fault analysis](27-fault-analysis.md#fault-analysis) study. The values represent the zero sequence impedance and zero sequence line shunt admittances for the analysis. By default, the positive and negative sequence line impedances and line shunt admittances are the same as the load flow impedance. The same fields are used for transformers, along with the configuration field. The configuration field defines the winding type combinations for the transformer (wye, delta, etc.) As a default, Simulator assumes an ungrounded wye to ungrounded wye transformer, which has the same model as an open circuit. Usually transformers are not of this type, and the proper type would need to be defined either manually or loaded from an external file in order for the fault analysis to be accurate.

Owner, Area, Zone, Sub, PTDF

The **Default Owner (Same as From Bus)** read-only check-box indicates whether the line’s owner is the same than the from bus’ owner. Transmission elements can have up to four different owners, each with a certain owner percentage. To add an owner of a transmission element, change one of the Owner fields to a new owner number, and update the owner percentages accordingly. Note that if you do not set the new owner percentages of all specified owners such that the total is 100%, Simulator will normalize the percentages such that the total is 100% when you click **Save** or **OK** on the branch dialog.

The area, zone and substation to which the From and To buses belong, are also shown. If a PTDF calculation has been performed, the PTDF values for the viewed line will be displayed as well.

Custom

This page of the dialog contains two sections: custom fields and memo. 

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the branch. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the branch. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

Stability

This tab is only visible with the [Transient Stability Add-On](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) tool. Any branch-specific transient stability modeling information is contained on this tab. For more information see the [Transient Stability Data: Object Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs).

---

<a id="transformer-impedance-correction-tables"></a>

## Transformer Impedance Correction Tables

*Source: [`Content/MainDocumentation_HTML/Transformer_Impedance_Correction_Tables_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transformer_Impedance_Correction_Tables_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Transformer Impedance Correction Tables dialog is used to view information about the transformer impedance correction tables. These tables are used on some LTC or phase shifting transformers to model the impedance of the transformer as a function of the off-nominal turns ratio or phase shift. The dialog has the following fields:

Transformer Impedance Correction Table Number

Number of the impedance correction table. Use the spin button immediately to the right of this field to step through the list of defined tables. If you have made changes to a particular table, you must click **Save** before moving to another correction table; otherwise, your changes will be lost.

Table Name

The name assigned to the table.

Table Entries

Used to insert/edit/delete the actual entries in the impedance correction table. In the first row, enter either an off-nominal turns ratio for an LTC transformer, or a phase shift in degrees for a phase shifting transformer. The entries in the first row must be entered in strictly ascending form. In the second row, enter the scale factor to apply to the transformer impedance. The transformer's nominal impedance is multiplied by the scale factor to obtain the actual value. To determine the appropriate scaling factor, interpolation will be used based on the current tap or phase angle. At least two columns must be used. Up to 100 points can be specified.

Right-click on the table to invoke its local menu, which allows you to delete and to insert columns. To insert a new column, click on the column before which you want to insert a new column and select **Insert New Point** from the local menu. To delete a column, position the cursor on the column you want to delete and select **Delete Point**.

Table is Used by the Following Transformers

Lists all the transformers in the case that use this impedance correction table. A single table may be used by any number of transformers. To associate a table with a transformer, use the [Transformer AVR Dialog](06-object-properties-edit-mode-part2.md#transformer-avr-dialog) for LTC transformers or the [Transformer Phase Shifting Dialog](06-object-properties-edit-mode-part3.md#transformer-phase-shifting-information) for phase shifters.

---

<a id="switched-shunt-information"></a>

## Switched Shunt Information

*Source: [`Content/MainDocumentation_HTML/Switched_Shunt_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Switched_Shunt_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Switched Shunt Information dialog can be displayed by placing the cursor on a switched shunt display object and right-clicking or right-clicking on a switched shunt record in the [Switched Shunt Display](05-case-information-displays-by-object-part3.md#switched-shunt-display) and choosing **Show Dialog**. This is very similar to its [Edit mode](06-object-properties-edit-mode-part3.md#switched-shunt-information) counterpart. The dialog has the following fields:

Bus Number

Unique number between 1 and 2,147,483,647 (equals 2^31 minus 1) used to identify the bus to which the switched shunt is attached. This drop down list identifies the buses in the case with switched shunts that also have [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Use the spin button to step through the list of shunts in the case. Multiple switched shunts are allowed at a bus but only one is allowed to be on automatic control.

Find By Number

To find a switched shunt by its bus number, enter the number into the Bus Number field. Then click the **Find By Number** button.

Bus Name

Unique alphabetic identifier for the bus to which the switched shunt is attached, consisting of up to eight characters. This dropdown box lists the names of all the switched shunt buses in the case with [valid display filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

Find By Name

To find a switched shunt by its name, enter the bus name into the Bus Name field (case insensitive). Then click the **Find By Name** button.

Shunt ID

Since multiple switched shunts are allowed on a single bus, each shunt is identified by a unique Shunt ID.

Find…

If you do not know the exact switched shunt bus number or name you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Status

Status of the switched shunt, either Closed (connected to terminal bus) or Open (not connected). On the oneline, the switched shunt can be opened by placing the cursor on the (red) circuit breaker box and clicking, and it can be closed by placing the cursor on the (green) box and again clicking. You can also use this status field to change the switched shunt's status. Note that the switched shunt is only available for automatic control when its status is closed.

Status Branch Added in Version 20

Line shunts can be modeled as controllable switched shunts by linking their status to the status of a branch. The Status Branch field specifies a branch whose status will affect the status of a switched shunt. If specified, a switched shunt can only be closed if is has a status of closed and its Status Branch also has a status of closed. If the Status Branch has a status of open, the switched shunt will also have a status of open.

Click the **Choose Branch** button to open a dialog that allows selection of this branch. Click the **Remove** button to no longer associate this switched shunt with a branch.

Energized

Indicates if the switched shunt is energized. This is not the same as the Open or Closed status. A switched shunt may be in-service itself (closed) but not be energized, based on the statuses of other devices around the switched shunt. For example, in a full topology model, it is not uncommon for a switched shunt to have a status of Closed, but the switched shunt is not energized if a branch of type Circuit Breaker connecting the switched shunt to the system has a status of Open.

Added in Version 20 If a switched shunt has a Status Branch assigned, whether or not a switched shunt is energized will be based on the status of this branch. If the branch is open, the switched shunt will not be energized.

Labels

Clicking on this button will open the [Label Manager](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) [Dialog](07-object-properties-run-mode-and-general-part2.md#labels) listing all the [labels](07-object-properties-run-mode-and-general-part2.md#labels) assigned for the selected switched shunt.

Parameters

Nominal Mvar

Amount of reactive power that would be supplied by the switched shunt if its terminal voltage were one per unit (capacitive is positive).

Actual Mvar

Actual reactive power in Mvar being injected into the system by the switched shunt (capacitive is positive). The Actual Mvar field is equal to the Nominal Mvar field multiplied by the square of the terminal bus' per unit voltage.

Nominal MW

This field is only visible when a switched shunt already has a non-zero MW value assigned. This could occur when the switched shunt has been read from an external file as a Bus Shunt with associated MW. The MW value can also be assigned through the [case information display for a switched shunt](05-case-information-displays-by-object-part3.md#switched-shunt-display). The MW component of a switched shunt has no controllability.

Actual MW

This field is only visible when a switched shunt has a non-zero Nominal MW value assigned. The value displayed is the actual real power in MW being injected into the system by the shunt. The Actual MW field is equal to the Nominal MW field multiplied by the square of the terminal bus' per unit voltage.

Control Mode

Information about this option can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Options

In order for a switched shunt to be on automatic control, switched shunt control must be enabled for the area to which it belongs and switched shunt control must be enabled for the case as a whole. The two checkboxes here allow easy access to enabling or disabling shunt control at these two different levels: **Area Shunt Control Enabled** or **Case Shunt Control Enabled**. Keep in mind that changing the options here can impact more that just the current shunt.

Control Regulation Settings

Information about these options can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Switched Shunt Blocks

Information about these settings can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Voltage Control Groups Added in Version 19

Specify if the switched shunt belongs to a voltage control groups. For more information on how voltage control groups work see the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Options: Advanced Options

Information about these options can be found in the [Switched Shunt Control](05-case-information-displays-by-object-part3.md#switched-shunt-control) topic.

Control Options: SVC Control Options

The SVC Control Options tab contains control options parameters specific for the [SVC Shunt Contro](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode)l.

Control Options: SVC Fixed Shunt Options

The SVC Fixed Shunt Options tab contains information of the SVC controlling the shunt ([SVC Shunt Contro](52-additional-linked-topics-part2.md#switched-shunt-svc-control-mode)l).

Control Options: Time Step Options

The [Time Step Options](26-time-step-simulation-part2.md#switched-shunt-control-time-step-options) tab contains control options specific for the [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation) tool.

Fault Information

Typically switched shunts are treated as open circuits in the zero sequence data for fault analysis. However, it is possible to define zero sequence admittance blocks to be used. The blocks work similarly to the load flow Switched Shunt Blocks discussed above. Usually there will be the same number of blocks in the zero sequence data as in the load flow data. Simulator will determine how many blocks were switched in for the power flow solution, and then use the zero sequence block data to calculate the zero sequence admittance for the same number of steps and blocks.

Owner, Area, Zone, Sub

This tab is used to display or change the generator’s owner information, area information, zone, and substation information

Area Number, Area Name

The area number and name to which the switched shunt belongs. The area of the switched shunt can be different than the area of its terminal bus.

Zone Number, Zone Name

The zone number and name to which the switched shunt belongs. The zone of the switched shunt can be different than the zone of its terminal bus.

Owner Number, Owner Name

The owner number and name to which the switched shunt belongs. A switched shunt will belong to the same owner to which its terminal bus belongs.

Substation Number, Substation Name

The substation number and name to which the switched shunt belongs. A switched shunt will belong to the same substation to which its terminal bus belongs.  

Custom 

This page of the dialog contains three sections: Data Maintainer, Custom Fields, and Memo.

A [Data Maintainer](#datamaintainer) may be specified for the switched shunt by clicking on the **Specify** button. Click the **Remove** button to unassign a data maintainer.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the switched shunt. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The [Memo section](01-getting-started.md#memo-display) of the dialog is simply a location to log information about the switched shunt. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

Stability

This tab contains information that is used with the [Transient Stability Add-On](36-transient-stability-overview-and-data-part1.md#transient-stability-overview) tool. Any switched shunt-specific transient stability modeling information is contained on this tab. For more information see the [Transient Stability Data: Object Dialogs](36-transient-stability-overview-and-data-part2.md#transient-tab-of-object-dialogs).

GIC

This tab contains information that is used with the [GIC Add-On](47-geomagnetically-induced-currents.md#gic-analysis) tool.

The following GIC Input Fields are available:

Per Phase Reactor GIC Grounding Resistance (in Ohms, Zero is Treated as Infinite)

Shunts operating as reactors can provide a conducting path for GIC. By default infinite resistance is assumed. Shunts operating as capacitors always have infinite resistance. Use this field to specify a grounding resistance for reactors on a per phase basis. The total resistance for all three phases is then one third this value.

Scale Conductance for Reactors with Multiple Blocks

The specified resistance applies when all inductive blocks are in service. If using this option, the resistance will be scaled based on how many blocks are in service. If half of the available blocks are in service, the resistance is twice as much.

Neutral Resistance (in Ohms)

This models an extra resistance in the switched shunt neutral that is in series with the three phase resistance of the reactor.

---

<a id="zone-information"></a>

## Zone Information

*Source: [`Content/MainDocumentation_HTML/Zone_Information_Run_Mode.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Information_Run_Mode.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used in the Run Mode to view and modify information associated with a zone record. It displays different information from the [Edit Mode version of the zone dialog](06-object-properties-edit-mode-part3.md#zone-information). To view this dialog, open the [Zone Records Display](05-case-information-displays-by-object-part1.md#zone-display) by clicking on **Aggregations \> Zones** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer)****. Right-click on the zone of interest and choose **Show Dialog**. The Run Mode Zone Dialog has the following fields:

Zone Number, Zone Name

Number and name of the associated zone. Use either the combo box or the spin arrows to view the different zones.

Find…

If you do not know the exact zone number you are looking for, you can click this button to open the [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics).

Labels

To assign alternative identifying labels to the zone, click the Labels button, which will open the [Label Manager Dialog](07-object-properties-run-mode-and-general-part2.md#label-manager-dialog) listing all the labels or aliases assigned for the selected zone.

The rest of the Run Mode Zone Dialog is divided into multiple pages:

Information

Load and Generation

Real and reactive load, generation, shunts, losses, and interchange for the zone.

Generation AGC Range

These two fields show the total available MW reserve for generators in the zone **** that are on AGC and have nonzero participation factors. In other words, these fields show the total MW by which the generation in the zone can be increased or decreased using only generation that is presently on-line. The generator status, AGC status, and participation factor can be changed on the [Generator Records Display](05-case-information-displays-by-object-part1.md#generator-display).

Tie Lines

Zone Tie Lines

The Zone Tie Line Table identifies the flows on all of the zone's ties to other zones.

To determine the total loss for a zone, losses for tie-lines between zones are assigned to the zone in which the terminal bus that is NOT the metered bus is contained. The **Metered End** field for a branch determines which of the terminals is metered.

OPF

Average LMP for Zone

The computed average locational marginal price of all buses contained in the zone.

LMP Standard Deviation

The standard deviation of the locational marginal price for all buses contained in the zone.

Minimum LMP

The minimum locational marginal price of all the buses in the zone.

Maximum LMP

The maximum locational marginal price of all the buses in the zone.

Reserve Requirement Curves

These options are only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview). More information about these options can be found in the [Area and Zone OPF Reserve Requirement Curves topic](31-scopf-and-opf-reserves.md#area-and-zone-opf-reserve-requirement-curves).

Zone Buses, Zone Gens, Zone Loads, Zone Switched Shunts

These pages show the case information display with the buses, generators, loads and switched shunts assigned to the zone.

Custom

The Custom Page of the Zone Information dialog displays custom numbers or strings defined with the viewed zone. The [Memo](01-getting-started.md#memo-display) box is simply a location to log information about the zone. To log information about the zone, simply start typing your information or comments about the zone in the memo box.
