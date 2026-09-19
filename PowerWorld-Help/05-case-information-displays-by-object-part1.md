---
title: "Case Information Displays by Object Type (Part 1 of 3)"
part: "Viewing Case Data"
chapter_file: "05-case-information-displays-by-object-part1.md"
topics: 18
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Case Information Displays by Object Type (Part 1 of 3)

The per-object case information displays: buses, generators, loads, lines, transformers, shunts, interfaces, ownership and more.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (18)**

- [Case Description](#case-description)
- [Case Summary](#case-summary)
- [Power Flow List](#power-flow-list)
- [Quick Power Flow List](#quick-power-flow-list)
- [Outages](#outages)
- [Area Display](#area-display)
- [Zone Display](#zone-display)
- [Tie Lines between Areas Display](#tie-lines-between-areas-display)
- [Tie Lines between Zones Display](#tie-lines-between-zones-display)
- [Super Area Display](#super-area-display)
- [Bus Display](#bus-display)
- [Bus Mismatches Display](#bus-mismatches-display)
- [Remotely Regulated Bus Display](#remotely-regulated-bus-display)
- [Substation Records Display](#substation-records-display)
- [Generator Display](#generator-display)
- [Generator Economic Curves](#generator-economic-curves)
- [Generator/Load Cost Models](#generatorload-cost-models)
- [Generator Cost Models Display](#generator-cost-models-display)

---

<a id="case-description"></a>

## Case Description

*Source: [`Content/MainDocumentation_HTML/Case_Description.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Description.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Case Description Dialog is broken into two sub-tabs described below.

In addition, Added in Version 23, the Case Date and Time may be specified at the top of this dialog. There is also a place to specify the UTC Hour Offset to signify the time-zone.

**Case Description**

The Case Description Tab allows you to enter a text description of a case. The portion of the description that is saved with the case varies with case type:

PowerWorld Binary (\*.pwb) an unlimited number of lines are allowed

PTI Raw Data format (\*.raw) Two lines of text

GE EPC Data format (\*.epc) The case title and all the pre-title comments are read in as the case description

PowerWorld Case (\*.pwc) No case description supported

IEEE Common Format (\*.cf) No case description supported

In PowerWorld Viewer, these descriptions are read-only.

**Case Comments**

The Case Comments Tab allows you to read comments previously added to a particular case. It shows a Case Information type of table with the Date, Time, User and Comment. This info is useful to track particular changes to a case or any information that need it to be commented after saving a case.

**Clear Comments** will clear all of the comments associated with the respective case.

Checking the *Prompt for comment when saving case* checkbox will force saving the case with comments by popping a dialog every time a case is saved. The portion of the description that is saved with the case varies with case type. The Add a comment dialog is shown below:

![Add Comments Dialog](images/Add_Comments_Dialog.gif)

**Add Comment** will add the comment to the particular case.

**Skip** will skip the adding of the comment for the case at this particular time is saved.

**Always Skip** will disable this dialog from appearing in future savings. To re-enable the dialog prompt, the **Allow to prompt for comment when saving case** option can be set with [Environment Options](10-power-flow-solution-and-options-part2.md#environment-options).

The Comment can be written in the white box and the Name can be modified also.

The dialog is slightly modified if [forcing the saving of comments when saving a case](03-cases-files-and-formats.md#saving-cases). A **Prompt for comment when saving case** checkbox will be available to set this option instead of doing that with the Environment Options.

To display the Case Description Dialog to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Case Description** from the **Case Data** ribbon group.

---

<a id="case-summary"></a>

## Case Summary

*Source: [`Content/MainDocumentation_HTML/Case_Summary.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Summary.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Case Summary Display provides a summary of the current case. Note that there are no enterable fields on the display. To display the Case Summary, go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Case Summary** from the **Case Data** ribbon group. The fields shown on this display include:

**Number of Devices in Case** shows the number of each of the following device types:

Buses

Total number of buses in the case. Use the [Bus Display](#bus-display) to see a listing of these buses.

Generators

Total number of generators in the case. Use the [Generator Display](#generator-display) to see a listing of these generators.

Loads

Total number of loads in the case. Use the [Load Display](05-case-information-displays-by-object-part2.md#load-display) to see a listing of these loads.

Switched Shunts

Total number of switched shunts in the case. Use the [Switched Shunt Display](05-case-information-displays-by-object-part3.md#switched-shunt-display) to see a listing of these switched shunts.

Trans. Lines (AC)

Total number of transmission lines in the case. Use the [Line/Transformer Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display) to see a listing of these lines.

LTCs (Control Volt)

Total number of Load Tap Changing transformers in the case. Use the [Transformer Control Display](05-case-information-displays-by-object-part2.md#transformer-display) to see a listing of these transformer controls.

Phase Shifters

Total number of Phase Shifting transformers in the case. Use the [Transformer Control Display](05-case-information-displays-by-object-part2.md#transformer-display) to see a listing of these transformer controls.

Mvar Controlling

Total number of Mvar Controlling transformers in the case. Use the [Transformer Control Display](05-case-information-displays-by-object-part2.md#transformer-display) to see a listing of these transformer controls.

Series Capacitors

Total number of Series Capacitors in the case. These devices are treated the same as any other transmission line, and therefore can be found listed as a transmission element in the [Line/Transformer Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display).

2 Term. DC Lines

Total number of two-terminal dc transmission lines in the case. Use the [DC Transmission Line Display](05-case-information-displays-by-object-part2.md#dc-lines-display) to see a listing of these dc lines.

N-Term. DC Lines

Total number of multi-terminal dc transmission lines in the case. Use the [DC Transmission Line Display](05-case-information-displays-by-object-part2.md#dc-lines-display) to see a listing of these dc lines.

Areas

Total number of areas in case. Use the [Area Display](#area-display) to see a listing of these areas.

Zones

Total number of zones in the case. Use the [Zone Display](#zone-display) to see a listing of these zones.

Islands

Total number of islands in the case. An island is a group of buses that are interconnected through ac transmission lines or transformers but are isolated from the rest of the system. Each island must have a slack bus. In Simulator, use the Power Flow Solution tab of the [Simulator Options display](10-power-flow-solution-and-options-part1.md#simulator-options) to specify whether multiple islands are allowed.

Interfaces

Total number of interfaces in the case. An interface is a grouping of tie line objects between area objects. In Simulator, use the [Interfaces Display](05-case-information-displays-by-object-part3.md#interface-display) to open the [Interface Dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) to define and modify interface objects.

Injection Groups

Total number of injection groups in the case. An injection group is a collection of loads and generators (objects that inject power into a network). In Simulator, use [Injection Groups Display](05-case-information-displays-by-object-part3.md#injection-group-display) to open the [Injection Groups Dialog](05-case-information-displays-by-object-part3.md#injection-group-dialog) to define and modify injection groups.

Case Totals

Summarizes the total load, generation, shunt compensation, and losses for the case. Positive shunt compensation denotes shunt load, whereas negative shunt compensation indicates a shunt injection (such as shunt capacitance). The case totals fields are valid only when the current case is solved.

Generator Spinning Reserves

The total difference between the present total generator output versus the total maximum possible output of all in-service generation.

Slack Buses:

The slack bus or buses are listed showing the bus name, number, and area name and number. One slack bus is required for each island.

Case Pathname

Full file name of the current case.

---

<a id="power-flow-list"></a>

## Power Flow List

*Source: [`Content/MainDocumentation_HTML/Power_Flow_List.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_List.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Power Flow List shows detailed information about the system’s power flows in a more traditional text-based form. This information is intended for users who would like detailed flow information about the power flow. Including the per unit voltage at the bus, the bus’ load and generation, and flows on all lines and transformers emanating from the bus. The content of this display (i.e. which buses are included in the list) is governed by the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To show this display go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Power Flow List** from the **Case Data** ribbon group.

To view flows at just a few select buses you may want to use the [Quick Power Flow List](#quick-power-flow-list) instead. For large systems with no area/zone filtering set, it may take Simulator a long time to generate the complete Power Flow List. Note also that this display can show a maximum of 32,767 lines of text. If this limit is exceeded, Simulator will generate a resource error. Either use the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) to limit the number of devices shown on this display, or use the Quick Power Flow List to focus on a few selected buses of interest.

The Power Flow List allows you to navigate through the system’s buses rather easily. You can also use the display to show the flows for a bus’ neighbor by double-clicking on the line that reads "TO nnnnn…," where nnnnn is the number of the bus you would like to see. The display is then positioned at this bus. If the bus is in an area and/or zone whose area/zone filter is not set, the area/zone filter is set automatically. In this way, you can inspect the system bus by bus.

The Power Flow List also has its own local menu, which can be viewed by clicking the right mouse button on the display. Select **Change Font** to modify the style and size of the display’s font. Select **Refresh** to ensure that the display’s contents concur with the current system state. To skip to particular bus in the list, click **Find Bus**, which will open the [Find Bus Dialog](04-model-explorer-and-case-information-part1.md#finding-records). To display the information dialog for the currently selected branch, bus, generator, load, or switched shunt, select **Show Dialog**. To print the display, choose the **Print** local menu option. **** Choosing **Copy** enables you to copy the display into the Windows clipboard, from where the information can be pasted into another application. Finally, select **Close** to close the display.

When printing the display you can either send the results directly to the printer or save them to a text file. To save the results in a text file on the Print Dialog select the **Save to File** option shown in the lower left corner of the dialog.

For each bus, the following items are shown:

Bus

Shows the bus’ number, name, and nominal voltage in kV. The next four fields are the MW, MVar, MVA and percentage headers for subsequent rows. The next fields specify the per unit voltage magnitude, voltage angle in degrees, the bus’ area number and the bus’ area name.

Generator

For each generator at the bus, the Power Flow List shows the generator’s ID (immediately after the keyword GENERATOR) and the power output of the generator in MW. Following this is generator’s reactive power output in Mvar. A single character is shown immediately after the Mvar field. An ‘R’ indicates that the generator is regulating the bus voltage, ‘H’ indicates that the generator is at its high reactive power limit, ‘L’ indicates that the generator is at its low reactive power limit, and a blank suggests that the generator is set off of AVR. The last field in the GENERATOR item is the MVA output of the generator. If no generators are connected to the bus, this item will be absent from the display.

Load

Shows the total power consumed by each load at the bus. If no loads are present at the bus, this item will be absent from the display.

Shunt

Shows the total power for the fixed shunts at the bus. Positive shunt values denote shunt load, while negative shunt quantities indicate injection. If no shunts are connected to the bus, this item will be absent from the display.

Switched Shunt

Shows the total power for the switched shunts at the bus. If no switched shunts are located at the bus, this item will be absent from the display.

Lines and Transformers

For each line or transformer coming into the bus, the Power Flow List shows the line’s flow and percentage loading. For transformers, the off-nominal tap ratio and phase shift angle in degrees are also shown. Immediately to the right of the off-nominal tap ratio is a two-character designation indicating the tapped side of the transformer: ‘TA’ indicates that the bus is on the tapped side, while ‘NT’ identifies the bus as residing on the side without the tap. You can left- click on this field to immediately reposition the bus to the other end of the line or transformer.

---

<a id="quick-power-flow-list"></a>

## Quick Power Flow List

*Source: [`Content/MainDocumentation_HTML/Quick_Power_Flow_List.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Quick_Power_Flow_List.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Quick Power Flow List provides a convenient means of viewing a listing of the flows at individual buses in the system. The format and control of the Quick Power Flow List is generally the same as that of the [Power Flow List](#power-flow-list), except that the Quick Power Flow List displays results for just the desired bus or [range of buses](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers).

You can access this Quick Power Flow List in a number of different ways:

  - Go to the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Quick Power Flow List** from the **Case Data** ribbon group** **
  - From most of the Case Information Displays, right-click to invoke the display’s local menu, and select *Quick Power Flow List*.
  - From the [Bus Information Dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) click on the *View All Flows at Bus* button.
  - From the oneline diagram, right-click on the [bus symbol](11-building-onelines-network-objects.md#bus-display-objects) to display the bus’ local menu, and select *Quick Power Flow List*.
  - From the oneline diagram, right click on the [shunt](12-building-onelines-branches-and-devices.md#switched-shunt-display-objects), [gen](11-building-onelines-network-objects.md#generator-display-objects), [lines](05-case-information-displays-by-object-part2.md#line-and-transformer-display) and [DC lines](05-case-information-displays-by-object-part2.md#dc-lines-display) symbol and under Bus Information select *Quick Power Flow List*.

This display is automatically created if it is not already shown. Information on subsequent buses appears at the bottom of the display.

As with the Power Flow List, you can navigate through the system bus-by-bus by double-clicking on the lines that begin with "TO nnnnn …," where *nnnnn* is the number of the bus you would like to investigate. Information for that bus will appear at the bottom of the display.

Like the Power Flow List, the Quick Power Flow List has a local menu that is accessed by right-clicking on the display. Among the things you can do from the local menu is to display the bus, branch, generator, load, or shunt corresponding to the currently selected record by selecting **Display Object Dialog**. You can also navigate through the system bus-by-bus just as you can do through double-clicking by choosing **Goto** **Line Bus** from the local menu.

---

<a id="outages"></a>

## Outages

*Source: [`Content/MainDocumentation_HTML/Outages_Topic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Outages_Topic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The outages display, available by choosing **Solution Details \> Outages** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer), presents a tabular listing of devices that are currently out-of-service in the load flow model. The display contains case information pages for [branches](05-case-information-displays-by-object-part2.md#line-and-transformer-display), [generators](#generator-display), [loads](05-case-information-displays-by-object-part2.md#load-display), [switched shunts](05-case-information-displays-by-object-part3.md#switched-shunt-display), [buses](#bus-display), and [Multi-section lines](05-case-information-displays-by-object-part2.md#multi-section-lines-display). All devices listed in the pages on this display are the out-of-service elements.

---

<a id="area-display"></a>

## Area Display

*Source: [`Content/MainDocumentation_HTML/Area_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Area_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Area Display houses data about each area in the case. The Area Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) from which you can print, copy, or modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#area-information) of its associated areas. You can also sort the area records by clicking on the heading of the field by which you want to sort.

To show the area records display, select **Aggregations \> Areas** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) or Aggregation \> Areas from the Case Information ribbon group under the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab.

By default, the area records display contains the following fields:

Number, Name

Area’s number, between 1 and 9999, and its alphanumeric identifier. Simulator supports names of any character length. However, when writing out names to file formats with limitations on name length, the area names will be truncated at their maximum supported length.

AGC Status

Area’s automatic generation control status. This field indicates whether or not the area’s generation is changing automatically to control the area interchange. See [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details. You can toggle the value of the area’s AGC Status (except in Viewer) by left clicking on the entry. Valid entries in this field include:

**Off AGC** Area is off AGC. Generation must be adjusted manually to meet changes in load and losses. If it is not, the system slack will be forced to pick up the balance.

**Part AGC** Area is on AGC, with generation dispatch controlled by its units’ [participation factors](06-object-properties-edit-mode-part1.md#generator-participation-factors).

**ED** Area is on economic dispatch control so that generation is dispatched in order of least cost.

**OPF** Area is on OPF control (only used with Simulator OPF). This option is only used with Simulator OPF. When the case is solved using the OPF the area controls are changed by the OPF to maintain area power balance. During non-OPF solutions this option is equivalent to Off AGC.

**Area Slack **Area is on Area Slack control. This option is only available for an area if you have already specified an area slack bus number in the area’s [information dialog](07-object-properties-run-mode-and-general-part2.md#area-information). ****

Gen MW

Total real power generation in the area in MW.

Load MW

Total real power load in the area in MW.

Tot Sched MW

The net of the base and scheduled transactions between the area and all other areas, with exporting power indicated as a positive value. The interchange for an area is set on the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information); the MW transactions for an area can be viewed using the specified [MW Transactions display](05-case-information-displays-by-object-part3.md#mw-transactions-display).

Int MW

The actual interchange between this area and all other areas, with exporting power positive. If an area is on AGC control, its actual interchange should match its scheduled interchange.

ACE MW

The area control error in MW. This is the amount of MW flow difference between the actual MW interchange and the desired MW interchange. A positive value means the super area is generating and exporting excess MW's, and a negative value means the super area is under-generating and importing too many MW's.

Lambda

The area’s marginal cost. This marginal cost is relevant only when an Economic Dispatch (not OPF) solution has been run. Theoretically, if losses are ignored, an area operates most economically if all generators operate at the same incremental cost. This common incremental cost is the area’s *lambda*, or marginal cost.

The local menu of the area records display has an additional option labeled *All Area Gen IC Curves*. Select this activity to generate a plot showing the incremental cost curves for all units located in a particular area.

Loss (MW)

Total real power losses for the area.

Losses for tie-lines between areas are assigned to the area in which the terminal bus that is NOT the metered bus is contained. The **Metered End** field for a branch determines which of the terminals is metered.

Auto Shunts

Determines whether switched shunts for the area are available for automatic control. You can use this field to disable all the switched shunts in an area. Click on this field to toggle its value. Click on the *Toggle All Yes* or *Toggle All No* local menu options to set the auto shunts property for all switched shunts. Note that a switched shunt is available for automatic control only if it meets three conditions: 1) its control mode property is set to *Automatic* (see [Switched Shunt Information Dialog](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information)); 2) its associated area’s *Auto Shunts* property is set to *Yes*; and 3) the *Disable Switched Shunt Control* option on the Power Flow Solution tab of the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options) must not be checked.

Auto XF

Determines whether tapped transformers for the area are available for automatic control. You can use this field to disable all the transformers in an area. Click on this field to toggle its value. Click on the *Toggle All Yes* or *Toggle All No* local menu options to set all entries in this column. Note that three conditions must be met for a transformer to be used for automatic control: 1) its *Auto* field must be set to *Yes* (see [Transformer Modeling](06-object-properties-edit-mode-part2.md#transformer-control) for details); 2) its associated area’s *Auto XF* property is set to *Yes*; and 3) the *Disable Transformer Control* option on the Power Flow Solution tab of the [Simulator Options dialog](10-power-flow-solution-and-options-part1.md#simulator-options) must not be checked.

Unspec. MW Inter.

Shows the total amount of interchange for the area that is listed as Unspecified. This means that some of the interchange is known in magnitude and direction (import or export) but not which other area(s) is involved in the interchange. The sum of all area’s unspecified interchange in the case must equal 0 for a balanced system.

---

<a id="zone-display"></a>

## Zone Display

*Source: [`Content/MainDocumentation_HTML/Zone_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Zone_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Zone Display provides information about all the zones in the case. Similar to the [Area Display](#area-display), the Zone Display provides a means of dividing up a power system. System results can then be summarized by zones using this display. Buses can be assigned to zones independent of their area assignments. Thus a single area could contain multiple zones, or a single zone could span multiple areas. The zone number for each bus is shown on the [Bus Dialog.](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) In the Edit Mode, groups of buses can be easily moved from one zone to another using the [Zone Dialog](06-object-properties-edit-mode-part3.md#zone-information).

The Zone Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](06-object-properties-edit-mode-part3.md#zone-information) of its associated zones. You can call up the [Quick Power Flow List](#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to obtain more information about a representative bus in the zone. ** You can also sort the zone records by clicking on the heading of the field by which you want to sort.

To show this display, click on **Aggregations \> Zones** in the [model explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The display contains the following fields by default:

Zone Number, Zone Name

Zone’s number, between 1 and 9999, and its alphanumeric identifier. Simulator supports names of any character length. However, when writing out names to file formats with limitations on name length, the zone names will be truncated at their maximum supported length.

Load MW, Load MVR

Total real and reactive power load in the zone.

Gen (MW), Gen (Mvar)

Total real and reactive power generation in the zone.

Loss MW, Loss MVR

Total real and reactive power loss in the zone. Losses are computed by summing the losses of the individual transmission lines and transformers in the zone. Because of shunt charging, these devices can also generate reactive power. Therefore, reactive power losses may actually be negative.

Losses for tie-lines between zones are assigned to the zone in which the terminal bus that is NOT the metered bus is contained. The **Metered End** field for a branch determines which of the terminals is metered.

Int MW, Int Mvar

Net interchange of real and reactive power with all other zones. Exported power is assumed to be positive.

Load Mult MW

Shows the current load MW multiplier for the zone. All load in the area is scaled by this multiplier.

---

<a id="tie-lines-between-areas-display"></a>

## Tie Lines between Areas Display

*Source: [`Content/MainDocumentation_HTML/Tie_Lines_between_Areas_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Tie_Lines_between_Areas_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Tie Lines between Areas Display identifies all area tie lines in the case. Tie lines are not a separate data record that can be created in Simulator, but instead provide a look at all the devices that connect two areas together in the power system model. Tie lines are important because the [Area Control](10-power-flow-solution-and-options-part3.md#area-control) algorithms used by Simulator often enforce a constraint which requires that the sum of the flow on the tie lines must equal the net export scheduled by the area (This is often called the ACE equation).

There are several types of devices that can represent tie lines. These include the following:

  - Transmission branch (Branch) : a transmission line or transformer that connects two buses that belong to two different areas is a tie line.
  - Two-terminal DC transmission lines (DCLine) : a DC transmission line that connects two buses that belong to two different areas is a tie line.
  - Multi-terminal DC transmission line (MTDCRecord) : For every multi-terminal DC transmission line that has converters connected to more than one area is a tie line.
  - Load (Load): A load can be assigned to a different area than its terminal bus. This is not typical but is sometimes done to model loads at lower voltage level where more than one entity has load that connects to the same power system bus. In such a situation this load represents a tie line.
  - Generator (Gen): Similarly to the load, a generator can be assigned to a different area than its terminal bus. Again this is considered a tie line.
  - Switched Shunt (Shunt): Similarly to the load, a switched shunt can be assigned to a different area than its terminal bus. Again this is considered a tie line.

Note: The easiest way to see which loads, generators, or switched shunts are assigned in this way is to use this Tie Lines between Areas Display. You can also, however, add separate columns using the display/column options on the Load, Generator or Switched Shunt Case Information Display. For instance, for loads there are columns for Area Num of *Bus* and Area Num of *Load*. Normally these are equal, but they will not be for tie line loads.

Note: Be careful when working with cases opened as RAW files in which there are loads that represent tielines. See PTI RAW Transactions due to tie-line load in [Simulator Options: File Management](10-power-flow-solution-and-options-part2.md#file-management-options) for more information.

The Tie Lines between Areas Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#switched-shunt-information) of its associated device type. You can learn more about a particular shunt’s terminal bus by choosing either [Quick Power Flow List](#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display). You can also sort the tie line information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Tie Lines Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To call up the Tie Lines between Areas Display, select **Aggregation \>** **Tie Lines between Areas** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The Tie Lines between Areas Display contains the following fields by default:

Tie Type

Indicates type of device that the tie line represents: Branch, Load, Gen, Shunt, MTDCRecord, or DCLine.

Near Area Name, Near Number, Near Name

The Bus Number, Name and Area Name of the bus to which the device is attached. For transmission lines this is the near end of the device.

Far Area Name, Far Number, Far Name

The Bus Number, Name and Area Name of the other end of the device.

Ckt

The circuit ID for transmission lines or DC Lines, the device ID for generators, loads, and switched shunts.

Meter MW and Mvar

The MW and Mvar flow from the point represented by Near Number/Name towards the Far Number/Name. For transmission lines and DC lines the metered point on the line is determined by the Metered End which is stored with the device. For instance on a transmission line, there is a check box for From End Metered which is available on the [Branch Options (Edit Mode)](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options) dialog. Changing this setting with the device will affect the Meter values slightly.

Status

This is the Open/Closed status of the tie line device.

Lim MVA

For tie lines that represent transmission lines this is the limit (rating) of the device.

MW and Mvar Loss

For tie lines that represent transmission lines this is the MW and Mvar loss across the device.

---

<a id="tie-lines-between-zones-display"></a>

## Tie Lines between Zones Display

*Source: [`Content/MainDocumentation_HTML/Tie_Lines_between_Zones_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Tie_Lines_between_Zones_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Tie Lines between Zones Display is essentially identical to the [Tie Lines between Areas Display](#tie-lines-between-areas-display). The only difference is that it displays devices that connect two zones together instead of areas. See the [Tie Lines between Areas Display](#tie-lines-between-areas-display) for more details.

---

<a id="super-area-display"></a>

## Super Area Display

*Source: [`Content/MainDocumentation_HTML/super_area_records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/super_area_records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Super Area Display identifies any super areas that have been defined for the case. Super areas are groups of areas whose generators are dispatched as a coordinated group. Super areas can thus be useful for modeling the operation of independent system operators or power pools.

Super areas cannot be inserted into a case from the ** [Individual Insert](02-simulator-ribbon.md#individual-insert-ribbon-group) ribbon group on the [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab. Instead, a super area can be defined when modifying or creating an area simply by typing the name of a new super area in the *Super Area* dropdown box on the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information).

The Super Area Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#super-area-information) of its associated super areas. You can call up the [Quick Power Flow List](#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) to obtain more information about representative bus in the super area. ** You can also sort the super area records by clicking on the heading of the field by which you want to sort.

To show this display select **Aggregation \> Super Areas** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

The display contains the following fields by default:

Super Area

The name of the super area.

AGC Status

The Super Area may operate without automatic generation control (AGC Status = *Off AGC*), with participation factor control (AGC Status = *Part. AGC*), or according to an economic dispatch (AGC Status = *ED*). This is a toggleable field.

Use Area PF

Indicates whether to use the areas participation factors when the super area is to operate with participation factor control (Part. AGC).

Num Areas

Indicates the number of areas defined as being part of the super area. Areas are added to super areas using the Super Area dropdown box on the [Area Information Dialog](07-object-properties-run-mode-and-general-part2.md#area-information).

Gen MW

Total MW injection from all the generators in the super area.

Load MW

Total MW load demanded in the super area.

Tot Sched MW

Total scheduled MW interchange with other areas or super areas.

ACE MW

The area control error in MW. This is the amount of MW flow difference between the actual MW interchange and the desired MW interchange. A positive value means the super area is generating and exporting excess MW's, and a negative value means the super area is under-generating and importing too many MW's.

Lambda

The super area’s marginal cost.

Loss MW

Indicates the real power losses incurred within the super area.

ED Use PF

Indicates whether the power flow engine will calculate loss penalty factors in computing the economic dispatch solution for the super area. If loss penalty factors are not calculated, then the economic dispatch is calculated assuming that the super area is lossless. Otherwise, the economic dispatch solution incorporates losses. The penalty factors gauge the sensitivity of the area’s losses to changing injection at specific generators. The option to calculate loss penalty factors is relevant only when the super area operates according to *Economic Dispatch Control*. Usually, if the system’s cost curves are relatively flat, the inclusion of losses in the solution will not have much of an effect on the dispatch.

---

<a id="bus-display"></a>

## Bus Display

*Source: [`Content/MainDocumentation_HTML/Bus_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus Display presents data describing each bus in the case. The Bus Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) from which you can print, copy, and modify its records as well as view the [information dialog](06-object-properties-edit-mode-part1.md#bus-options) of its associated bus. You can also sort the bus records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Bus Records Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, when Simulator is in [Edit Mode](01-getting-started.md#edit-mode-introduction), the case information toolbar allows you to add new buses to or remove existing buses from the system.

To show the bus records display, select **Network \> Buses** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) or from the Case Information ribbon group under the [Case Information](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab.

By default, the bus records display contains the following fields:

Number and Name

Bus number between 1 and 2,147,483,647 (equals 2^31 minus 1), and its alphanumeric identifier.

Area Name

Alphanumeric identifier of the bus’ area.

Nom kV

The nominal base voltage of the bus in kV.

PU Volt

Bus’ per unit voltage magnitude.

Volt (kV)

Bus’ actual voltage magnitude in kV. This is the per unit voltage magnitude multiplied by the bus’ nominal voltage.

Angle (Deg)

Bus’ voltage angle in degrees.

Load MW, Load Mvar

Total real and reactive load at the bus. If no loads are located at the bus, these fields are blank.

Gen MW, Gen Mvar

Total real and reactive generation at the bus. If no generators are located at the bus, these fields are blank.

Switched Shunt Mvar

Total switched shunt device reactive power injection at the bus.

Act G Shunt MW, Act B Shunt Mvar

Total real and reactive fixed bus shunt injections.

Area Num

The area number in which the bus is located.

Zone Num

The zone number in which the bus is located.

---

<a id="bus-mismatches-display"></a>

## Bus Mismatches Display

*Source: [`Content/MainDocumentation_HTML/Bus_Mismatches_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Bus_Mismatches_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus Mismatches Display lists the real and reactive mismatches at each bus. The bus mismatches are defined as the difference between the power entering the bus and the power leaving the bus. A power flow case is considered solved when all the bus mismatches are below the convergence tolerance specified on the Power Flow Solution page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog.

Most of the time you will not need to be concerned about the bus mismatches. If the power flow solves, the mismatches are guaranteed to be below the desired tolerance. However, advanced users will find this display useful in determining the cause when a power flow diverges.

The Bus Mismatch Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [case information toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) from which you can print, copy, and modify its information as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) of its associated bus. You can find a specific bus mismatch using the name or number of the bus, and you can learn more about the bus by choosing either [Quick Power Flow List](#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display). You can also sort the bus mismatch information by clicking on the heading of the field by which you want to sort.

To show this display select **Solution Details \> Mismatches** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer). You can view bus mismatches only when the application is in Run Mode.

Also note that there is a special feature in the Records menu of the case information toolbar for the mismatch display. This option is **Zero-Out Mismatches**. Choosing this options will cause Simulator to insert fictitious B and G Bus Shunt values to force the mismatch at every bus to zero.

The Bus Mismatch Display contains the following fields by default:

Number, Name, Area Name

The number and name of the bus and the name of the area in which it is located.

Type

This is the BusCat or category of the bus. This is a string that denotes what equations are being solved at this particular bus inside the inner power flow loop of the power flow solution. A complete description of the [theory of the power flow equation](10-power-flow-solution-and-options-part1.md#power-flow-solution-theory) and [possible BusCat categories](10-power-flow-solution-and-options-part1.md#power-flow-bus-category-possibilities) are found in other topics.

MW Mismatch, MVR Mismatch, MVA Mismatch

The real and reactive mismatches at each bus, and the total complex power mismatch.

---

<a id="remotely-regulated-bus-display"></a>

## Remotely Regulated Bus Display

*Source: [`Content/MainDocumentation_HTML/Remotely_Regulated_Bus_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Remotely_Regulated_Bus_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Remotely Regulated Bus Display provides information about all buses that are remotely regulated by one or more generators, transformers, or switched shunts. The bus that a generator regulates is specified in the Edit Mode using the [Generator Dialog](06-object-properties-edit-mode-part1.md#generator-information). Whenever a generator is regulating a bus that is not its terminal, it is considered to be remotely regulating that bus. The bus that is remotely regulated, along with the regulating generators, will appear on this display. The same logic is true for transformers and switched shunts which may regulate remote buses also.

The Remotely Regulated Bus Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its information as well as view [the information dialog](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) of its associated buses. You can find a specific remotely regulated bus, and you can learn more information about a particular remotely regulated bus by choosing either [Quick Power Flow List](#quick-power-flow-list) or [Bus View](08-view-case-data-tools.md#bus-view-display). You can also sort the remotely regulated bus information by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the information shown by the Load Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters).

To call up the Remotely Regulated Bus Display, open the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) and select **Remotely Regulated Buses** under the Solution Details folder.

This Remotely Regulated Bus Display contains the following fields by default:

Number, Name, Area Name

Number, name, and area name for the bus that is being remotely regulated.

PU Volt

Per unit voltage magnitude for the bus.

Set Volt

Setpoint voltage for the bus. When a bus is being remotely regulated by a set of generators, the generators vary their reactive power output to maintain the voltage at the bus at the setpoint value. You can enter a new value for this field. Changing the setpoint voltage here changes the setpoint voltage for all the generators that are remotely regulating this bus.

Volt Diff

Per unit difference between the actual voltage magnitude and the set point voltage magnitude.

AVR

Combined automatic voltage regulation (AVR) status for all the generators remotely regulating this bus. If AVR is *No*, no generators regulate voltage; if AVR is *Yes*, all the available generators are regulating; if AVR is *Mixed*, some generators regulate voltage and some do not. Regulation of individual generators can be specified using the [Generator Display](#generator-display) . You can toggle this field between "Yes" and "No" by clicking on it.

Total Mvar

Total of the reactive power being supplied by all the generators remotely regulating the bus.

MVR Min, MVR Max

Total of the minimum and maximum reactive power limits for all the generators remotely regulating the bus.

Remote Regs (gen)

Provides a comma-separated list of all the generators which regulate this bus.

Rem Regs (XFMR)

Provides a comma-separated list of all the transformers which regulate this bus.

Rem Regs (SS)

Provides a comma-separated list of all the switched shunts which regulate this bus.

---

<a id="substation-records-display"></a>

## Substation Records Display

*Source: [`Content/MainDocumentation_HTML/Substation_Records_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Substation_Records_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Substation Records Display presents data describing each substation in the case. The Substation Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the information dialog of its associated substation. You can also sort the substation records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Substation Records Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, when Simulator is in [Edit Mode](01-getting-started.md#edit-mode-introduction), the local menu allows you to add new substations to or remove existing substations from the system. Note: a substation is considered in an area/zone if any single bus in the substation is in the area/zone.

To show the substation records display, select **Aggregation \> Substations** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the substation records display contains the following fields:

Sub Num

An integer identifier for the substation.

Sub Name, Sub ID

Two alphanumeric identifiers for the substation.

Area Name, Zone Name

The names of the area and zone of the buses in the substation. If some of the buses in the substation are in different areas or zones, then this is the most common area or zone.

\# of Buses

The number of buses inside the substation.

Nom kV

Nominal kV of the highest voltage bus(es) in the substation.

Gen MW, Gen MVR

Total real and reactive generation at the substation. If no generators are located at the substation, these fields are left blank.

Load MW, Load MVR

Total real and reactive load at the substation. If no loads are located at the substation, these fields are left blank.

Shunt MW, Shunt MVR

Total real and reactive shunt values at the substation. If no shunts are located at the substation, these fields are left blank.

---

<a id="generator-display"></a>

## Generator Display

*Source: [`Content/MainDocumentation_HTML/Generator_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Display presents data describing each generator in the case. The Generator Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) of its associated generators. The [Quick Power Flow List](#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) tools are available for finding more information on the generator’s terminal bus. You can also sort the generator records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Generator Records Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, you can use the local menu’s *Insert* and *Delete* options when the application is in [Edit Mode](01-getting-started.md#edit-mode-introduction) to insert a new generator into the case or to delete an existing generator.

To show the generator records display, select **Network \> Generators** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the generator records display contains the following fields:

Number, Name

Number and name of the bus to which the generator is attached. The display’s local menu offers you the opportunity to view the [Quick Power Flow List](#quick-power-flow-list) and the [Bus View Display](08-view-case-data-tools.md#bus-view-display) for the bus.

ID

Single character ID used to distinguish multiple generators at the same bus. This default value for this field is ‘1’.

Status

Displays the Open / Closed status of the generator. This field is a toggleable field.

Gen MW, Gen Mvar

The real and reactive power output of the generator. If the generator is on AVR control, the reactive power is set automatically.

Set Volt

Per unit setpoint voltage for the generator. When a generator is on AVR control, the reactive power output of the generator is varied automatically in order to maintain the regulated bus voltage at this value. The regulated bus is usually, but not always, the generator’s terminal bus. Use the [Generator Dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) to see the regulated bus number.

AGC

Designates whether the generator’s real power output is governed by automatic generation control. If the AGC field is set to *Yes*, the generator is on automatic generation control (AGC). When a generator is on AGC, its real power output can be varied automatically. Usually the purpose for AGC is to keep the area interchange at a desired value. You can click on this field to toggle its value (except in Viewer). Please see [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details.

AVR

Designates whether the generator will vary its reactive power output to maintain a constant terminal voltage. If the *AVR* property is set to *Yes*, the generator is on automatic voltage regulation (AVR) control. When a generator is on AVR control, its reactive power output is varied automatically to keep the regulated bus voltage at the **Set Volt** value. AVR is limited by the generator’s reactive power limits. You can click on this field to toggle its value (except in Viewer).

Min MW, Max MW

Minimum and maximum allowable real power output of the generator.

Min Mvar, Max Mvar

Minimum and maximum allowable reactive power output of the generator.

Cost Model

The type of cost model the generator is currently set to use. Cost models are necessary for performing economic analysis, such as Economic Dispatch or [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview).

Part. Factor

Generator’s participation factor. Participation factors are used to determine how AGC generators participate in area control when their area is on participation factor control. Please see [Area Control](10-power-flow-solution-and-options-part3.md#area-control) for more details.

---

<a id="generator-economic-curves"></a>

## Generator Economic Curves

*Source: [`Content/MainDocumentation_HTML/Generator_Economic_Curves.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Economic_Curves.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Four characteristic curves describe the efficiency and resulting costs associated with operating a particular generating unit. These four curves plot

  - Fuel Cost
  - Heat Rate
  - Input-Output
  - Incremental Cost

Simulator can display plots of all these curves. To display a particular plot for a generator, right-click on the generator in Run Mode to display its local menu, and then select the plot you wish to see. The plot will be presented in its own window. The windows for all plots exhibit identical characteristics. For example, the current operating point is identified by a red filled circle. Right clicking on an open area of the window displays the plot’s local menu which allows you to print the plot, save it to a file, or copy it to the clipboard for use in other programs. To adjust the length and number of intervals shown on an axis, right-click on the *axis* (not on the *numbers*) then specify the min and max display values and number of intervals. To close a plot window, simply click the X button in its top right corner.

The Run Mode generator local menu also provides access to a fifth type of plot curve - the "All Area Gen IC Curves" plot. This plot simply shows the incremental cost curves and present operating points of all generators in the same area as the generator on which you clicked.

Fuel Cost Curve

The fuel cost curve specifies the cost of fuel used per hour by the generating unit as a function of the unit’s MW output. This is a monotonically increasing convex function.

Heat-rate Curve

The heat rate curve plots the heat energy required per MWH of generated electrical output for the generator as a function of the generator’s MW output. Thus, the heat rate curve indicates the efficiency of the unit over its operating range. Generally, units are least efficient at the minimum and maximum portions of their MW output capability and most efficient somewhere in the middle of their operating range. The vertical axis is plotted in MBtu/MWH and the horizontal axis is plotted in MW. You may interpret the heat rate for a generator producing X MW as follows: the heat rate indicates the amount of heat input energy per MWH of generation required to produce X MW of power. The lower this number, the less input energy is required to produce each MWH of electricity.

Input-Output Curve

The input-output curve is derived simply from the heat-rate curve by multiplying it by the MW output of the unit. This yields a curve showing the amount of heat input energy required per hour as a function of the generator’s output.

Incremental Cost Curve

By multiplying the input-output curve by the cost of the fuel in $/MBTU, one obtains the cost curve for the unit in $/hr. By taking the derivative of the cost curve, one obtains the incremental cost curve, which indicates the marginal cost of the unit: the cost of producing one more MW of power at that unit.

---

<a id="generatorload-cost-models"></a>

## Generator/Load Cost Models

*Source: [`Content/MainDocumentation_HTML/Generator_Load_Cost_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Load_Cost_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator/Load Cost Models option from the Case Information menu allows you to choose to view detailed information on generator cost curves or load benefit curves. This cost information can be very important when solving an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) or [Security Constrained Optimal Power Flow](31-scopf-and-opf-reserves.md#security-constrained-opf-overview) solution.

The Generator/Load Cost Models option has four submenu options to choose from:

[Generator Cubic Cost Models](05-case-information-displays-by-object-part2.md#generator-cubic-cost-display)

[Generator Piecewise Linear Cost Models](05-case-information-displays-by-object-part2.md#generator-piecewise-linear-cost-display)

[All Generator Cost Models](#generator-cost-models-display)

[All Load Benefit Models](05-case-information-displays-by-object-part2.md#load-benefit-models-display)

---

<a id="generator-cost-models-display"></a>

## Generator Cost Models Display

*Source: [`Content/MainDocumentation_HTML/Generator_Cost_Models_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Cost_Models_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Generator Cost Models Display presents detailed cost information for each generator in the case, regardless of what type of cost curve has been entered for the generator. The Generator Cost Models Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with all other case information displays. It has a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, and modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) of its associated generators. The [Quick Power Flow List](#quick-power-flow-list) and [Bus View Display](08-view-case-data-tools.md#bus-view-display) tools are available for finding more information on the generator’s terminal bus. You can also sort the generator records by clicking on the heading of the field by which you want to sort. Additionally, you can choose to restrict the records shown by the Generator Cost Models Display according to the constraints of the [area/zone/owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). Finally, you can use the local menu’s *Insert* and *Delete* options when the application is in [Edit Mode](01-getting-started.md#edit-mode-introduction) to insert a new generator into the case or to delete an existing generator.

To show the generator piecewise linear and cubic cost model display, select **Network \> Generators \> Cost Curves All** from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer).

By default, the generator records display contains the following fields:

Number, Name

Number and name of bus to which the generator is attached.

Area Name of Gen

Name of the area to which the generator belongs. The generator can be assigned to an area different than the area to which its terminal bus is assigned.

ID

Single character ID used to distinguish multiple generators at the same bus; ‘1’ by default.

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

Cost Model

The type of model this generator is currently using. Can be Cubic, Piecewise Linear or None.

IOA, IOB, IOC, IOD

Parameters used to model the cost characteristic of the generator. Please see [Generator Cost Information](06-object-properties-edit-mode-part1.md#generator-cost-description) for details. Please note that these values can be saved/loaded using the [Generator Cost Data](03-cases-files-and-formats.md#auxiliary-file-format-aux) auxiliary file.

These fields will be disabled unless the Cost Model type is set to Cubic.

Fuel Cost

The fuel cost of the type of fuel for the generator.

Variable O\&M

Operations and Maintenance costs for the generator.

This field will be disabled unless the Cost Model type is set to Cubic.

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

A requirement of the piecewise linear cost curve is that it must be convex, meaning the next MWh Price must be higher than the previous MWh Price.

These fields will be disabled unless the Cost Model type is set to Piecewise Linear.
