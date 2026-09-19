---
title: "Getting Started with Simulator"
part: "Getting Started"
chapter_file: "01-getting-started.md"
topics: 14
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Getting Started with Simulator

Orientation, the Simulator interface, what's new, and how to get help.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (14)**

- [About this Manual](#about-this-manual)
- [Introduction to PowerWorld Simulator](#introduction-to-powerworld-simulator)
- [Introduction to Simulator Add-On Tools](#introduction-to-simulator-add-on-tools)
- [What's New](#whats-new)
- [Getting Help](#getting-help)
- [Windows Basics](#windows-basics)
- [Touchscreen Interaction](#touchscreen-interaction)
- [PowerWorld Simulator: Getting Started](#powerworld-simulator-getting-started)
- [Edit Mode Introduction](#edit-mode-introduction)
- [Run Mode Introduction](#run-mode-introduction)
- [Script Mode Introduction](#script-mode-introduction)
- [Message Log](#message-log)
- [Memo Display](#memo-display)
- [Status Bar](#status-bar)

---

<a id="about-this-manual"></a>

## About this Manual

*Source: [`Content/MainDocumentation_HTML/about_this_manual.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/about_this_manual.htm)*

PowerWorld provides comprehensive, context-sensitive on-line help. By default this information is available on the PowerWorld website at [http://www.powerworld.com/WebHelp](https://www.powerworld.com/WebHelp/WebHelp). Any page of this manual can be printed for your own off-line reference. Occasionally updates to the on-line help are posted on the PowerWorld website.

This help documentation was last updated on 9/14/2026.

---

<a id="introduction-to-powerworld-simulator"></a>

## Introduction to PowerWorld Simulator

*Source: [`Content/MainDocumentation_HTML/Introduction_to_PowerWorld_Simulator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Introduction_to_PowerWorld_Simulator.htm)*

PowerWorldÒ Simulator (Simulator) is a power system simulation package designed from the ground up to be user-friendly and highly interactive. Simulator has the power for serious engineering analysis, but it is also so interactive and graphical that it can be used to explain power system operations to non-technical audiences. With [each new version](#whats-new) we’ve continued to make Simulator more powerful and easier to use with the addition of a number of major new features and hundreds of smaller enhancements.

Simulator consists of a number of integrated products. At its core is a comprehensive, robust Power Flow Solution engine capable of efficiently solving very large systems. This makes Simulator quite useful as a stand-alone power flow analysis package. Unlike other commercially available power flow packages, however, Simulator allows the user to visualize the system through the use of full-color [animated oneline diagrams](15-using-onelines-tools-and-options.md#oneline-diagram-overview) complete with [zooming and panning](17-oneline-view-printing-and-contouring.md#oneline-zooming-and-panning) capability. System models can be either modified on the fly or built from scratch using Simulator’s full-featured graphical case editor. Transmission lines can be switched in (or out) of service, new transmission or generation can be added, and new transactions can be established, all with a few mouse clicks. Simulator’s extensive use of graphics and animation greatly increases the user’s understanding of system characteristics, problems, and constraints, as well as how to remedy them.

The base package of Simulator is capable of solving power systems comprised of up to 250,000 buses. Please [contact PowerWorld](#getting-help) if you need to model more buses than this. The base package also contains all the tools necessary to perform integrated economic dispatch, area transaction economic analysis, power transfer distribution factor (PTDF) computation, short circuit analysis, and contingency analysis. All of the above features and tools are easily accessible through a consistent and colorful visual interface. These features are so well integrated that you will be up and running within minutes of installation.

In addition to the features of the base Simulator package, various add-on tools are available, including the new transient stability feature. Please see [Introduction to Simulator Add-On Tools](#introduction-to-simulator-add-on-tools) for more information.

---

<a id="introduction-to-simulator-add-on-tools"></a>

## Introduction to Simulator Add-On Tools

*Source: [`Content/MainDocumentation_HTML/Introduction_to_Simulator_Add_On_Tools.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Introduction_to_Simulator_Add_On_Tools.htm)*

In addition to the features of the base Simulator package, various add-on tools are available. A brief introduction to each follows:

Available Transfer Capability Analysis Tool (ATC)

ATC analysis determines the maximum MW transfer possible between two parts of a power system without violating any limits. For more information, see the [ATC Analysis Overview](32-available-transfer-capability.md#available-transfer-capability-atc-analysis).

Distributed Computing

Distributed computing allows the use of multiple computers to speed up analysis by splitting the work among a user-specified list of computers. For more information, see the [Distributed Computing Add-Ons](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons) topic.

GIC

GICs are induced in the electric power grid when coronal mass ejections (CMEs) on the sun send charged particles towards the earth. These particles interact with the Earth’s magnetic field causing what is known as a geomagnetic disturbance (GMD). For more information, see the [GIC Analysis](47-geomagnetically-induced-currents.md#gic-analysis) topic.

Integrated Topology Processing (ITP)

Integrated Topology Processing allows you to solve EMS-type, full-topology models in a numerically robust and transparent manner. Integrated Topology Processing extends Simulator applications traditionally used by planners so they can operate in an operations real-time environment. For more information, see the [Integrated Topology Processing Overview](35-integrated-topology-processing.md#topology-processing-overview).

Optimal Power Flow Tool (OPF)

The purpose of an OPF is to minimize an [objective (or cost) function](30-optimal-power-flow-part1.md#opf-objective-function) . In Simulator OPF the Linear Programming OPF algorithm (LP OPF) determines the optimal solution by iterating between solving a standard power flow and solving a linear program to change the system controls thereby removing any limit violations. For more information, see the [OPF Overview](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview).

Optimal Power Flow Reserves (OPFR)

Simulator OPF Reserves is the tool used to simulate Ancillary Services Reserve Markets. For more information, see the [Optimal Power Flow Reserves Overview](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview).

Scheduled Actions (Schedule)

The Scheduled Actions Analysis tools provide the ability to visualize the combined effects of planned equipment outages. For more information, see the [Scheduled Actions Analysis](48-scheduled-actions.md#scheduled-actions-tool) topic.

Security Constrained Optimal Power Flow Tool (SCOPF)

The OPF tool minimizes an objective function (usually total operation cost) by changing different system controls while meeting power balance constraints and enforcing base case operating limits. The SCOPF tool takes it one step further by considering contingencies that may arise during system operation and ensuring that in addition to minimizing the objective function, no unmanageable contingency violations occur. For more information, see the [SCOPF Overview](31-scopf-and-opf-reserves.md#security-constrained-opf-overview).

Simulator Automation Server (SimAuto)

SimAuto provides PowerWorld customers the ability to access PowerWorld Simulator functionality within a program written externally by the user. The Simulator Automation Server acts as a COM object, which can be accessed from various programming languages that have COM compatibility. Examples of programming tools with COM compatibility are Borlandâ Delphi, Microsoftâ Visual C++, Microsoftâ Visual Basic, Python, and Matlabâ (among others). For more information on SimAuto, see the [SimAuto Overview](33-simauto-overview-and-setup.md#automation-server).

Transient Stability (TS)

Transient Stability analysis allows the analysis of system dynamic response to a fault on the system. For more information, see the [Transient Stability Overview](36-transient-stability-overview-and-data-part1.md#transient-stability-overview).

Voltage Adequacy and Stability Tool (PVQV)

The purpose of the PVQV add-on is to allow the user to analyze the voltage stability characteristics of a system. After the PVQV simulation is complete, the user can graph various system parameters. For more information, see the [PVQV Overview](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview).

---

<a id="whats-new"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New.htm)*

PowerWorld Simulator Version 24 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

The following is a select list of the important changes in Simulator Version 24. This is then followed by a very long list of other changes.

  - New SimAuto functions for getting data out of Simulator are highly recommended
      - [GetParamsRectTyped Function](34-simauto-functions.md#getparamsrecttyped) brings back results are a specified type (float, integer, string) instead of bringing all results back as string
      - [GetParamsTypedCols](34-simauto-functions.md#getparamstypedcols) function brings back results specified by type and allows different types to be assigned for each field
  - Transient Stability
      - [Ability to specify a Power Flow Contingency associated with a TSContingency](37-transient-stability-analysis-dialog-part3.md#simulating-multiple-contingencies). This result of the power flow contingency becomes the initial condition for the transient stability run. This allows you to setup multiple TSContingency events that have different initial conditions determines by the PowerFlowContingency
      - Continued expansion of new dynamic models as well as ability to read and write more dynamic models
  - New [Distributed Computing add-on for the QV Curve tool](29-pv-and-qv-curves.md#distributed-computing)
  - Support for defining [FixedNumBus](08-view-case-data-tools.md#fixednumbus-features) designations and using them
      - Used when reading RAW version 34 and 35 files with substation sections
      - Ability to [Save Merged FixedNumBus Case](08-view-case-data-tools.md#save-merged-fixednumbus-case)
      - Support for defining [oneline diagrams with Bus display objects that act as a FixedNumBus](17-oneline-view-printing-and-contouring.md#displaybus-property-allowfixednum).
      - Support for loading other files using FixedNumBus integers as identifiers from AUX files, CON files, MON files
  - Added ability to define a Region which contains polygons of RegionGeoPoint objects. Simulator can then automatically populate a Region with all the bus objects that are contained inside the Region based on whether the latitude/longitude coordinate of the bus is inside the polygon defined by the RegionGeoPoints. Summary information and oneline can the be created with this Region information.
  - More Support for reading time-varying weather information and assigning this to the time-step simulation tools
  - New [Connections Tools](02-simulator-ribbon.md#other-tools-ribbon-group) to go with existing connections tools
      - [Find Radial Bus Paths](18-general-tools.md#find-radial-bus-paths) connection tool is new
      - [Set Bus Field From Closest Bus](18-general-tools.md#set-bus-field-from-closest-bus) connection tool is new
      - Existing tools are very useful and you are encouraged to revisit these
          - [Find Circulating MW and Mvar flows](18-general-tools.md#find-circulating-mw-or-mvar-flows) can help you find conflicting transformer tap settings
          - [Find Parallel AC Branches](52-additional-linked-topics-part1.md#find-parallel-ac-branches) can help with identifying parallel transformers with conflicting tap orientation
          - Check out all the [connections tools](02-simulator-ribbon.md#other-tools-ribbon-group)

To see a list of what was new in previous Simulator Versions choose links for [Simulator 23](52-additional-linked-topics-part3.md#whats-new-4), [Simulator 22](52-additional-linked-topics-part3.md#whats-new-2), [Simulator 21](52-additional-linked-topics-part3.md#whats-new-3), [Simulator 20](52-additional-linked-topics-part3.md#whats-new), and [Simulator 19](52-additional-linked-topics-part3.md#whats-new-1).

What follows is a more detailed list of the changes in Simulator Version 24.

[Auxiliary Files, Display Auxiliary Files and Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux)

  - For syntax and usage details, please refer to the latest Auxiliary File Format PDF, available at:

    [https://www.powerworld.com/knowledge-base/auxiliary-file-format-10](https://www.powerworld.com/WebHelp/knowledge-base/auxiliary-file-format-10)

  - Added more support for using special & and @ syntax to specify a particular object and field as a value in script commands. See [https://www.powerworld.com/knowledge-base/auxiliary-file-format-10](https://www.powerworld.com/WebHelp/knowledge-base/auxiliary-file-format-10) for details

  - Added ability to specify a [ColorBackgroundAlternating for case information displays](10-power-flow-solution-and-options-part2.md#case-information-display-options). This will show alternating rows with a slightly different color.

  - Added ability to use Device filters in UseAnotherFilter conditions for Advanced Filters

  - With the Auxiliary File Export Format Description there is an option to build a format description for the complete case and various categories of objects can be user selected. A new selection for "Contingency Combination" is now available that will include Contingency Primary definitions and solution options with the format description.

  - With the Auxiliary File Export Format Description there is an option to build a format description for the complete case and various categories of objects can be user selected. A new selection for "Scheduled Actions" is now available.

  - Added built-in AUX Export Format Description for Geomatically Induced Current. This is found under the Create Format for Complete Case button.

  - Modified all script commands that have a parameter "filtername" to specify an advanced filter or device filter. These parameters can now also use a special string with the syntax "MW \>= 50" to do a single condition filter without actually needing to create a named filter. The syntax is Variablename Comparison Value1 Value2. Examples are: "NomkV between 220 550", "MW \>= 50"

  - The following Script Commands were added:

      - SetBusFieldFromClosest() will set a bus field equal to another bus' values that is closest to the bus. This was first added to help users assign buses that do not belong to a substation equal to the substation closest to the bus. To do this the command would be SetBusFieldFromClosest(SubNumber, "Sub Number IsBlank", "SubNumber IsBlank", All, Z);

      - TIMESTEPSaveInputCSV()

      - CreateLineDeriveExisting() which creates a branch with the same RXGB values but scaled up/down related to line lengths

      - TSAutoSavePlots which will mimic the option to save plots to file that can be configured ahead of time with plots. This will allow you to create plots programmatically from existing results.

      - TimeStepLoadPWWRange

      - TimeStepAppendPWWRange

      - TimeStepSavePWWRange

      - GICReadFilePSLF, GICReadFilePTI, GICWriteFilePSLF, and GICWriteFilePTI

      - ApplyScheduledActionsAt

      - GICSetupTimeVaryingSeries

      - FaultAutoInsert

      - RevertScheduledActionsAt

      - InterfacesCalculatePostCTGMWFlows

      - Added CTGWriteAuxUsingOptions script command. This uses the CTGWriteAux\_Options object to specify which contingency related information should be stored in the aux file and how objects should be identified.

      - BranchMVALimitReorder

      - CustomFieldDescriptionModify(ObjectType, CustomType, Location, FieldString, HeaderString, IncludeInDiff);

      - CustomFieldDescriptionAppend(objecttype, CustomType, FieldString, HeaderString, IncludeInDiff); This command behaves the same as calling ModifyCustomFieldDescription with a negative Location. This creates a new CustomFieldDescription by incrementing the CustomMaxOfType.

      - TIMESTEPDeleteAll

      - TIMESTEPLoadPWW

      - TIMESTEPAppendPWW

      - TIMESTEPSavePWW

      - InterfaceAddElementsFromContingency(interface name, contingency name). It creates interfaces elements from valid contingency actions and adds them to the named contingency. If the interface does not exist, it will be created.

      - TSPlotSeriesAdd("PlotName", SubPlotNum, AxisGroupNum, ObjectType, FieldType, "Filter", "Attributes"); (use to create plot series programatically)

      - InterfaceFlattenFilter(filtername);

      - EnumerateDDLOnelines

      - TSJoinActiveCTGs

      - Added CTGConvertToPrimaryCTG(filter, KeepOriginal, "Prefix", "Suffix") script command that converts regular/secondary contingencies to primary contingencies.

      - FindRadialBusPaths(IgnoreStatus, TreatParallelAsNotRadial, BusOrSuperBus);

      - TSAutoSavePlots(\[PlotNames\], \[ContingencyNames\], FileType, theWidth, theHeight, theFontScalar, IncludeCaseName, IncludeCategory);

      - SaveMergedFixedNumBusCase("filename", FileType);

  - The following Script Commands were modified:

      - Added more filtering options for InterfaceCreate script command to include SELECTED, AREAZONE, device filters and filters as a single filter condition

      - Modified the TSSavePTI, TSSaveGE, and TSSaveBPA script commands to use special keywords: @DATETIME, @DATE, @TIME, @BUILDDATE, @VERSION, @CASENAME, @CASEFILENAME, and @CASEFILEPATH for the file names.

      - When using SaveCase() script command if the filename variable omits a file extension, the Simulator will automatically add the appropriate file extension

      - Added new option with CTG\_Options called "Save unlinked contingency and remedial action element objects in auxiliary files" that will enable saving unlinked action objects when saving aux files outside of the Save button on the contingency analysis dialog or the CTGWriteResultsAndOptions script command. When using the Save button on the contingency dialog the option on the resulting dialog will be used for saving unlinked objects or not. The script command also has its own input parameter to indicate this.

      - Added three new parameters to the CTGWriteResultsAndOptions script command: Opt20 = Save Primary Contingency Options for Combo Analysis, Opt21 = Save Primary Contingencies for Combo Analysis, and Opt22 = Save CTG Combo Results. All of these parameters are NO by default and NO when used with the CTGWriteAllOptions script command.

      - Added the optional parameter PreferenceFilter to the commands InterfaceRemoveDuplicates(PreferenceFilter) and InjectionGroupRemoveDuplicates(PreferenceFilter);

      - When specifying values for field in the SetData() script commmand, we will now look for special strings @CASENAME, @CASEFILEPATH, and @CASEFILENAME special strings. The particular user request was to add the ability to set the folder to which to store Transient stability hard-drive results to.

      - Modified the a script command to have an additional optional parameter SetSensitivitiesAtOutOfServiceToClosest("FilterName", BranchDistMeas);

      - Modified the CalculateShiftFactors() in the same way. It now has parameters as follows with the BranchDistMeas a new optional paramter. CalculateShiftFactors(\[flow element\], direction, \[transactor\], LinearMethod, SetOutOfServiceBuses, filter, AbortOnError, BranchDistMeas)

      - Added SetSelected field to DoFacilityAnalysis script command. This is an optional parameter that is NO by default. DoFacilityAnalysis("filename", SetSelectedField). When set to YES the Selected field for branches that are part of the minimum cut will be set to YES. Prior to running the script command the Selected field should be set to desired values for all branches. The script command only sets the Selected field for branches in the minimum cut to YES and does not reset other branches.

      - Added NewBusName parameter at end of TapTransmissionLine script command to specify the name of the new bus created at the tap point.

      - Added fields with the TLR\_Options object to specify whether Breakers and Load Break Disconnects should be used to close disconnected buses that contain generators or loads so that shift factors can be calculated at these devices. [These options were only available on the user interface dialog, but can now be changed using script commands and AUX files too](20-sensitivities.md#shift-factor-sensitivities-dialog).

      - There is a new optional parameter at the end of the Move() script command called AbortOnError. It will default to YES in which case if the Move command can not be done the auxiliary script will be aborted. By setting it to NO you can tell the script keep running even if an error occurs.

[Available Transfer Capability](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)

  - Ratings/Load [Multiple ATC Scenarios](32-available-transfer-capability.md#scenarios) now include specifying load by InjectionGroup

  - Added a field to Direction object called [ATCValidation](20-sensitivities.md#directions-display) which is a string indicating if any errors occurred while processing multiple-Direction ATC

  - Added Latitude and Longitude fields for Direction object to show coordinates for the Seller and Buyer

  - Added "Use Options for Heatmap from FERC Order 2023" option with ATC analysis. This will set the ATC options necessary for producing the Transfer Limiter results based on the FERC Order 2023 heatmap requirements.

  - Added new fields to a TransferLimit object which show results in a manner that forces a positive OTDF Sensitivity and a positive Limit Used. This added fields are under a folder "Positive" in the list of available fields. The variable names are Pos\_ValuePreTrans, Pos\_PercentPreTrans, Pos\_Object, Pos\_ObjectDesc, Pos\_Limit, and Pos\_Sensitivity.

  - Added more options for auto inserting multiple directions for ATC and PTDF analysis. Options are now available to insert from Area, Zone, Injection Group, and Bus source objects to a specified sink object of type Area, Zone, Injection Group, or Slack. The source objects can be filtered using standard filtering methods.

  - Added bus field **ATC Min Trans MW** to provide a field for creating heatmap contours for multiple direction ATC with buses as the source. This field will look through the list of Transfer Directions and if a transfer exists with the Seller object set equal to a Bus, then this bus field will return the minimum TransferLimiter TransLim MW for that bus' transfer direction.

Bus View Onelines

  - Forward and backward mouse buttons now work for moving backward and forward in bus views and substation views.

  - Modified Bus View Onelines to allow a Consolidated SuperBus , Consolidated FixedNumBus, and Consolidated SubNet view

[Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)

  - Added definition of generic [ObjectGroups](07-object-properties-run-mode-and-general-part1.md#object-groups) that provide a mechanism to show summary information on groups of objects, such as generation MW or load MW summations. Also can be used as Device Filters.

  - Added ability to show summary information on generation and load summations for objects that are contained by [Supplemental Data Objects](15-using-onelines-tools-and-options.md#supplemental-data)

  - Changed the Color Scheme for selecting multiple cells to make it easier to read the text that remains

  - Changed how toolbars and selection highlighting works when using Dark Color schemes in case information dipslays to make text easier to read.

  - [Added DataCheckExemption objects](08-view-case-data-tools.md#data-check-definitions). These pair an Object with a particular DataCheckName and signify that this object will never meet the DataCheck because it is exempt. The user may specify a Reason why the object is exempt.

  - Changed the entries in the Explore Pane of the Model Explorer. Aggregations folder was getting too long, so a subfolder for lesser-used Aggregations was added under Aggregations\\Other Aggregations. Also added the folder for Conditions, Filters and Expressions.

  - Added a new entry under Aggregations to show a Case Summary which shows an object representing the entire case and summary summation fields. This has been available for more than 15 years but users needed to add a User-Defined Case Information display to see them.

  - For Branch object case information displays [added a special filtering user-interface to allow the user to select with check boxes which types of BranchDeviceType are shown](08-view-case-data-tools.md#user-interface-interactions).

  - For Bus object case information displays [added a special filter user-interface to allow the user to select to see all buses, Only FixedNumBus or Only SuperBus](08-view-case-data-tools.md#user-interface-interactions).

  - When sorting on Case Information Displays now if the present view of the display is not near the top of bottom of the list of objects, Simulator will now automatically navigate to the presently selected object in the table after completing the sort.

  - When Ctrl-Clicking on a column header to sort a column Simulator will now "maintain selected row in view". When using the [Advanced Sort dialog](04-model-explorer-and-case-information-part1.md#sorting-records) there is now an option that says "Maintain Selected Row in View"

  - On case information displays, the option [to SetAllValuesTo so for numeric fields](04-model-explorer-and-case-information-part1.md#set-toggle-and-columns-menus) the user can scale and/or shift all the values.

  - Adding additional geography fields to areas and zones, including min/max latitude/longitude values.

  - Added ability to use Device filters in UseAnotherFilter conditions for Advanced Filters

  - When right-clicking in a case information display showing Gen, Shunt, LineShunt, Branch and Load objects there is now a special option under the Save As submenu for Save As "TS models AUX format (only model of selected records". This will save any stability models associated with the objects selected in the case information display.

  - In Case Information Displays the Plot Columns now allows just a subset of the rows to be plotted. If the user selects one row then all rows are plotted (as before); the new functionality is if more than one row is sleected then just those rows are plotted. The Column Plot dialog now also allows the plotted rows to be changed, with a button to easily select all.

  - Case Info Column Metrics dialog now has a page making it easy to get a histogram plot of the data.

  - Changed the MouseWheel up and down behavior on Case Information Displays to better match what is done in spreadsheet software tools. If CTRL key is down we will zoom in and out (same as CTRL + Up/Down arrow keys) If SHIFT key is donw we will move the selected cell up/down (this was the old default) Otherwise we will scroll the viewed window up or down by 1 row.

  - When using the local pop up menu to Copy/Send to Clipboard or Spreadsheet (MS Excel, Open Office), there is now an option to always include the key field column, even if it is not currently being displayed as part of the case information display. This option is stored with the registry, and not stored with the PWB case.

  - When adding new columns to a Case Information Display from Fields Pane or the Display/Column Options dialog, we now have internal defaults for the decimal places to show for some fields. In the past the Fields Pane would always add field with 3 decimals and the dialog would always add decimals based on the presently selected column in the dialog. It will now always use 3 decimal places unless there is a hard-coded different number specified by PowerWorld staff. For now this hard-coded list is small and consists of: Latitude, Longitude, and Per Unit volt field: 6 decimals and Various MW, Mvar, and MVA fields: 2 decimals. This is cosmetic as it only impacts the default value when adding fields in the user interface. The user can and always has been able to customize them. This was primarily done to ensure the Latitude/Longitude fields always had 6 decimals by default as the prior default of 3 decimals was not precise enough.

  - New Fields for Objects

      - Added a generator MW range percentage used (MWRangePercent). This calculates the percentage of the entire range, namely: MWRangePercent = (MW - MinMW) / (MaxMW - MinMW). This ensures that negative MinMW values actually expand the range instead of being ignored like with the traditional MWPercent field.

      - Added 4 more new generator fields the folder for "Mvar Output\\Capability Curve Range\\" named CapCurveMvarMinAtMWMin, CapCurveMvarMinAtMWMax, CapCurveMvarMaxAtMWMin, CapCurveMvarMaxAtMWMax

      - Some additional generator fields for showing the retirements and inservice dates, and the EIA860 identifiers.

      - For PartPoint object type changed the column header "Initial Value" to "AutoCalc Method" because this more accurately reflects how this field is used. "Initial Value" will continue to work as a legacy column header for pasting information from Excel or loading a CSV

      - Added field for Bus, Area, Zone, and Substation for showing MWRangePercent field

      - added Bus fields for GenMvarMaxOnline, GenMvarMinOnline, GenMWMaxOnline, and GenMWMinOnline

      - Added support for Custom String Expressions to PartPoint objects

Connections Tools

  - Under the [Connections drop-down on the Tools Ribbon Tab](02-simulator-ribbon.md#other-tools-ribbon-group), added the option [Find Radial Bus Paths](18-general-tools.md#find-radial-bus-paths). This looks for groups of buses connected in a radial network and presents them as a list of buses and branches that are in this grouping. Groups are identified by the final bus in the Radial Path. Options exist about whether to traverse open branches, how to treat parallel branches, and whether to search by Bus or SuperBus.

  - Under the [Connection drop-down on the Tools Ribbon Tab](02-simulator-ribbon.md#other-tools-ribbon-group), add the option [Set Bus Field From Closest Bus](18-general-tools.md#set-bus-field-from-closest-bus)

  - Added option to use branch Normal Status when determining Breaker Isolated Groupings as a standalone or as part of auto inserting contingencies

[Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)

  - Modified the All Violations portion of the Results Tab of the Contingency Analysis dialog. There are now separate Tabs for showing All, Branch, Bus, Interface, BusPair, Island, and Other. This will automatically restrict the list ViolationCTG objects to those that are violations of particular object types. This will also allow different columns to be shown for violations of different object types.

  - Added a new field with [CTGOutageIntertie field with an InjectionGroup object](22-contingency-analysis-options.md#injectiongroup). During the AC contingency solutions that if all generators, loads, and shunts become opened by the various contingency actions then the solution will automatically open the Branch or Interface object specified as the CTGOutageIntertie for the InjectionGroup.

  - Added a new field to TSContingency object named AUXElementErrors. This field is a comma-delimited list of any error strings that gets populated when you load an AUX file. After loading the AUX file is is then just a comma-delimited string the user can edit with notes about fixing the TSContingency definition.

  - Modified the Contingency analysis action for OPEN Bus so that if the bus specified has Number = FixedNumBus, then the contingency action will open all AC branches connected to any bus that connects between the FixedNumBus and a different FixedNumBus.

  - When saving options from the Save button on the Contingency Analysis dialog there are now options to Save Primary Contingencies for Combo Analysis, Save Primary Contingency Options for Combo Analysis, and Save CTG Combo Results.

  - Added new field "Reference Percent" for contingency limit violations (ViolationCTG object). This calculates (Reference State Value)/Limit\*100.

  - Added ability to show more fields with LimitViol and ViolationCTG (All Violation) objects. New fields were numbers of Areas, Zones, BA, and Substation.

[Difference Case](08-view-case-data-tools.md#difference-case)

  - Added OPFFastStart field for a generator to be part of the Difference Case Tool

[Distributed Computing](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)

  - Greatly sped up retrieving large amounts of results back from Distributed ATC simulations

  - Added the [Distributed QV](29-pv-and-qv-curves.md#distributed-computing) curve calculation

File Formats

  - Continued support for reading and writing [case data formats](03-cases-files-and-formats.md#case-formats)

  - Modified code when reading an EPC or RAW file for catching when a transformer is almost certainly a phase shifter even though the user has not designated it as a phase shifter. We were using the fact that TapMin and TapMax where greater than 2.0 per unit to indicate it must be a phase shifter. When a transformer is off control however, a user may not be careful how those are set. Added some more checks to make sure we are getting this assumption correct. Also, simulator will now write log messages saying "Info: Transformer \*\*\* looks like a phase shifter. It is set as Type=Phase and AutoControl=NO"

  - Completed support for reading and writing the PSSE \*.raw 34 and 35 formats that write substation sections.

  - Added support for reading more parts of the PSSE \*.con files. In particular actions to SET, CHANGE, ALTER, MODIFY, INCREASE, RAISE, DECREASE, or REDUCE values for Shunt, Load, Machine/Unit objects

  - Added support for reading \*.con files that have an ID specified with the SWSHUNT object.

  - Modified to allow opening multiple files when choose to load files from the Contingency Analysis load button and from the Load Contingency Data under the RAS + CTG Case Info dropdown on the Tools Ribbon tab. Previously you could only open one file at a time.

  - Both GMD data files, and GMD data in an EPC file can now filtered using the Area/Zone filters.

  - When loading \*.otg files to create either Contingency or TSContingency definitions, modified to read the Category and the Skip flag from the OTG format.

  - Modified writing to PTI \*.CON contingency files so that the full name of the contingency is written out regardless of the length of the string. Various versions of CON files have had 8, 12, 32, etc... character restrictions. It will now be up to the user to truncate names appropriately for the version of PTI they are using.

  - When writing the end of some section in a RAW file we were writing a ' 0' (space before the 0). This was causing a problem in other 3rd party software tools, so we have removed the space as it was not necessary.

  - Added the use of the RAW file option to keep duplicates with new ID's to the Loads section of reading the RAW file.

  - Modified read of correction table records. Now if we read a tap/scale pair of 0,0 we stop reading the rest of that record, and move on to the next one. Any points read up to the 0,0 will be kept and added to that correction table. Also modified that if the tap or scaling factor are not valid numbers, we also abort and keep only the valid points read up to the errant value.

  - Added new Sim\_Environment\_Options field called UnlinkedElementsSaveForce. This option is stored with the PWB case and when set to YES it overrides the windows registry option called UnlinkedElementsSave. This can be set to YES to always store unlinked elements of Contingency, Interface, and InjectionGroup objects when saving a particular case as a PWB file.

  - Modified reading \*.otg and \*.otgd files so that delimiters between fields can be either a comma OR white space (spaces, tabs, etc...). Newer OTGD files are space delimited and older ones were a mix of both spaces and commas. Changes were made to Simulator in 2023 to support reading the newer OTGD format, but older OTGD files must be read as well. This change was made to allow any of these to function.

  - hdbexport Areva CSV files

      - When reading the hdbexport netmom CSV file, we now read the ND.ELIGIBLE field: if it is FALSE, then we set the respective Simulator's Bus field Monitor = NO.

      - Added ability to [load Areva hdbexport Dynamic Line Ratings (DLR) records](28-weather.md#load-areva-dynamic-line-ratings-dlr-csv-as-weather-dependent-limits). These convert DYNELE, SEG, SEGWST, RATING, and WST records into analogous structures of XYCurve, XYCurveX, XYCurvePoint, and WeatherStation objects in Simulator. This then creates weather-dependent limits in Simulator. Also added a new Sim\_Environment\_Options\_Value option called HDBExportTempUnits which can be set to either Fahrenheit or Celsius. This determines the assumed units of temperature provided in the RATING and WST records in the CSV file.

      - Added ability to read the TEID field for the records ST, ND, LD, CP, UN, SVS, LN, ZBR, XF, PS, CB, INTRFC, AUX. This field represents the "Transmission Equipment ID". We will read the field and create an object label with the syntax "TEID\_12345" where the value 12345 is what is populated in the TEID field in the CSV file.

      - Added a new object called HDB\_BRLIMS\_RateSet which allows you to specify where BRLIMS ratings read are placed into the model. These decisions are made based on the fields: BRLIMS.ID field and LNLIMA.BRLIMS. The HDB\_BRLIMS\_RateSet object specifies a SearchString which is used to match the BRLIMS string ID. If a match is found then the HDB\_BRLIMS\_RateSet object specifies to either push limits into the DEF, GHI, JKL, or MNO RateSets. We would expect that only one HDB\_BRLIMS\_RateSet would have a SearchString that matches, but if multiple do, then the one with the lowest Order field will be used.

      - When reading the hdbexport CSV file, addded support for having user-specified labels for 3WXFormer object records based on the primary winding XF record.

      - Added 2 new options to Sim\_Environment\_Options called HDBExportCTGLREDEF and HDBExportCTGLRAS. These options are used when reading an hdbexport CSV file with CTGL records. There are flags on CTGL records for CTGL.REDEF : indicates that the record was dynamically created in the EMS by the REDEF process which is enabled by the CTG.ENREDEF flag and CTGL.RAS: indicates that the record was dynamically created in the EMS by the RAS process. The 2 new options can be set to either "Ignore" or "OPEN". Ignore indicates that the CTGL record will be ignored. OPEN indicates that the CTGL record will create a ContingencyElement that is an OPEN action.

      - Modified reading of hdbexport \*.CVS file for Contingency Information. If the CTG.ENREDEF=T, then CTGL records which refer to a TYPE=CB will only be read as an OPENCBS ("open with breakers") action if the CTGL.CBF=T is set. CTGL records refering to a CB record need this special permission to model a "CB failure".

      - Added error checking when loading the Areva hdbexport CSV for a case. If records such as UN, LD, CP, LN, ZBR, XF, NDPAIR, or DCCNV reference another ND record but it is an index higher than the largest ND record index then appropriate warning messages are written to the log indicating a problem in the file. If this is the ND record at which the device is connected we will ignore the device. If this is the ND record for a regulated bus, we will use the terminal bus of the device as the regulated bus. These are error in the CSV however and the user should fix these problem in the CSV export (probably by redoing the hdbexport process in the EMS). These fixed in PowerWorld Simulator however will at least allow us to load the file and see what is wrong in the CSV export.

General

  - Added a new option under the [Tools Ribbon Tab, under the Other Tools dropdown to Anonymize Names in Case](02-simulator-ribbon.md#other-tools-ribbon-group) which does exactly that.

  - Added more information stored at the beginning of a PWB file so that summary information can be seen the General File Browser for (1) number of substations and buses with valid lat/lon values and (2) number of stability models and (3) number of power flow weather models.

Geography

  - Added ability to specify a Route which is a sequence geographic RoutePoint objects that store a latitude/longitude sequence. A Branch object in Simulator can then be assigned to a Route.

  - Added ability to define a Region which contains polygons of RegionGeoPoint objects. Simulator can then automatically populate a Region with all the bus objects that are contained inside the Region based on whether the latitude/longitude coordinate of the bus is inside the polygon defined by the RegionGeoPoints. Summary information and oneline can the be created with this Region information.

  - Every object that has a geographic location (or can estimate one from the underlying objects), now has available fields named RefDistanceMile and RefDistancekm which shows the distance of an object from a user-specified reference point. The reference point can be set on a dialog available from the right-click menu of a case information display under the Geographic Data View submenu. This can be used with objects such as a generator or load which obtain their geographic location from either the bus or substation object, or from more abstract objects such as a RemedialAction or Interface that obtain their geographic location from the average value of objects that they contain.

  - The ac and dc line dialogs now have buttons on their geography papers to open the external maps; this is the same as what buses and substations already had.

[GIC](47-geomagnetically-induced-currents.md#gic-analysis)

  - Added support for integration for GICHarm tool from EPRI

  - In Time Step simulation allow the state to be stored when doing just a GIC solution; also fixed bud with Time Step Playback dialog when there are either no playback values or the dialog is closed while playing results.

  - Added ability to manage multiple GIC efield events.

[Oneline Diagrams](15-using-onelines-tools-and-options.md#oneline-diagram-overview)

  - Added generator display object rotor shapes to include a Battery and

  - [Memo Text Background objects have features to treat the contents of the Memo as an AUX file](13-building-onelines-graphics-and-insertion.md#memo-text). Users can then click on the oneline object to "Load Memo Text as AUX file". Also words to "Load Memo Text as AXD file".

  - Modified drawing of a SwitchedShunt objects on Discrete control to show a stair-step line through them to indicate control is on. Control Modes Continuous and SVC have always shown a diagonal line indicating control.

  - Cleaned up the right-click local menus for Bus, Branch and Substation objects because they had become very long. There are now sub menus for (1) Insert Connected Buses, (2) Auto Insert/Edit Oneline , (3) Format and various other changes.

  - Modified right-click local menus on most display objects to show identifying information about the linked object at the top of the drop-down list.

  - The ImageDialog now has the ability to automatically update the image when one clicks on the crop/size/position fields. The functionality is fast on simple onelines, but it needs to be optional since on a complex oneline it might be too slow.

  - Added support for PNG images on oneline diagrams

  - Added ability from the Oneline Options to quickly change the fill color of the base objects (with the filled states an example). The button to do the change is right below the background color field and is called the "Most Common Base Object Color"

  - In various places when right-clicking on a oneline diagram or on the Geography tab of the Bus and Substation dialogs there are ways to "Open Google Maps". This feature has been extended to offer a drop down to Open Google Maps, Bing Maps, or Open Infrastructure Maps. These are the websites: https://www.google.com/maps, https://www.bing.com/maps, https://openinframap.org/

  - Modified oneline diagrams so that when pressing Ctrl+G while the mouse cursor is hovering above a oneline diagram, then a string is copied to the Windows Clipboard of the format "Latitude, Longitude" with 7 decimal places for the coordinates.

  - When loading a KML file, users have encountered ill-formed KML files that have omitted commonly used namespaces. PowerWorld will now look for errors related to 3 commonly used namespace definitions and automatically include them when reading a KML file if those namespaces are used but not declared. These namespaces are as follows.: xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"; xmlns:gx="http://www.google.com/kml/ext/2.2"; xmlns:kml="http://www.opengis.net/kml/2.2"

  - Added support for images now having a fixed aspect ratio. When this option is true, when they are resized by the diagonal handles the width and height change proportionally. The image dialog also now shows the rotation angle.

  - Added oneline option to scale the size of all the gen/load/shunt object Circuit Breakers symbols.

  - Added the ability to select an [angle from which pie chart/gauge styles start filling pie charts and the direction in which they fill](13-building-onelines-graphics-and-insertion.md#pie-chart-gauge-style-dialog---pie-chart-parameters-tab).

  - Adding new option for OpenOneline script command. The fullscreen parameter can now have 3 values (yes, no, and max). When max is used the oneline is maximized after opening

[Optimal Power Flow (OPF)](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)

  - Changed the maximum LP iteration default limit from 9999 to 50000. The default was too small for large cases.

[Powerflow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-theory)

  - When EvalSolutionIsland = YES, a solution only terminates if ALL viable islands in the case fail to converge. Added a new option EvalSolutionIslandRequireLargest that when set to YES also requires that the island with the largest number of buses in it must converge.

  - In older versions of Simulator, when switching to Edit Mode, all system states are destroyed. This includes the Last Successful Solution State, State Before Failed Solution Attempt, Contingency/ATC/PV References, User State, and Named States. This patch modifies this behavior so that the "User State" and "Named States" are no longer destroyed when switching to Edit Mode. This allows you to continue using the User and Named States even after switching to Edit Mode and deleting or adding objects. These states will not be "solved states" after you have made deletions or additions in Edit Mode, but they still can be useful states.

  - Improved how bus voltages are estimated when particular types of topology changes are made. In particular, when deleting objects that affect topology (Bus, Branch, Gen, and Load), it was important to update the connected bus topology so that buses that are then in disconnected islands are marked as such. Then if new branches are added to reconnect these buses, the reconnected buses need new voltages estimates based on the new connections before a power flow solution is attempted. This greatly improved power flow performance under these situations

  - Modified the [Generator Mvar Limit checking algorithm when (NOT using Check Immediately) AND (Using Check Backoff Immediately)](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options). For very low generator terminal voltages are see we will still force minimum Mvar limits to be checked and for very high terminal voltage we will force maximum Mvar limits to be checked.

  - Improved power flow convergence when a branch is being closed and at the same time another branch in parallel is being opened. The angle-smoothing pre-solution processing was not working effectively in that situation

  - Improved coordination of parallel tap transformers to catch more situations where they are parallel to prevent poor solutions

[PV QV Curves](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)

  - QV Curves can utilize [QV Distributed Computing](29-pv-and-qv-curves.md#distributed-computing) features.

[Scheduled Actions](48-scheduled-actions.md#scheduled-actions-tool)

  - Added a read-only Log field to Scheduled Action objects to display any issues that arise when the action is applied.

  - Update PowerWorld Outage CSV to allow for unmapped actions with unknown device types

  - Added TimeProfile to Scheduled Action Groups, which can be Continuous or Daily (Continuous groups are active continuously between the StartTime and EndTime), (Daily groups are active every day from the day of StartTime to the day of EndTime, between the time of StartTime and the time of EndTime)

  - Added "Apply Only Filtered Actions" to the Scheduled Actions Options tab; if enabled, the Advanced Filter settings on the Scheduled Actions grid will determine which Actions are actually applied to the case.

  - Added "Fit Window To Schedules" button to automatically set the Start and End times in the Scheduled Action Dialog to fit the currently configured Schedules.

  - Added buttons to the Scheduled Actions dialog to Revert/Restore outages at the ViewTime, added Current Action Status field to Scheduled Action objects showing the action's own Current Status (separately from the governing Group Current Status)

  - Added log messages when the Outage system state is stored/restored

  - Changed Scheduled Action Group case info display to include a sub-grid with the Actions associated with the selected Group.

Sensitivity Analysis

  - Modified the LikelyLowSolution field for a Bus so that it only returns YES if a bus meets all the following (1) dV/dQ \< 0, (2) Not connected to any branch with a negative (excluding 3-winding transformer windings), and (3) Has at least one closed generator, load, or shunt. Criteria \#3 was added to eliminate falsely flagged buses in some situations. A bus must have some load, gen, or shunt in order for those injections to push the local system to voltage collapse.

SimAuto

  - SimAuto instances now run at Below Normal priority level to allow all cores on a machine to be used without danger of locking up the user interface.

  - Added support for single-condition filter strings in SimAuto commands

  - Modified the SimAuto command called RunScriptCommand2 so that the error string can include information such as "23 objects not found" while reading objects from the data section of an auxiliary file.

  - Simulator COM automation (i.e., SimAuto) distributed process threads are now assigned in a manner that prevents them from being power throttled by the Windows layer. This issue affected newer Intel CPUs that have p/e-cores technology, in which background Simulator distributed processes would get assigned to e-cores (that have lower processing speed). This did not change the quality of results from Simulator, but some users running distributed tools (like Transient Stability, ATC) would have noticed a significant increase in processing duration, because p-cores (that have higher processing speed) were inadvertently not being used. This issue only affected those users using distributed tools from a primary SimAuto instance (from VBA, Python, Matlab, etc), and not those using a primary graphical Simulator instance. It has been remedied.

  - Modified the [GetParametersMultipleElement functions in SimAuto](34-simauto-functions.md#getparametersmultipleelementrect) so that when in DiffCaseMode = Change, we will only return objects that have input parameters which have at least one non-key field that has changed.

[Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation)

  - Added features throughout for supporting more use of time-varying weather data

[Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)

  - Ability to specify a Power Flow Contingency associated with a TSContingency. This result of the power flow contingency becomes the initial condition for the transient stability run. This allows you to setup multiple TSContingency events that have different initial conditions determines by the PowerFlowContingency

  - Modified all the case information tables for showing transient stability dynamic models so that any display/columns options modifications are maintained and remembered. Previously on these tables any modifications would be forgotten as soon as you moved away from that table. They now persist in Simulator and also are saved to the PWB file format.

  - Added new fields for [TSContingency named ResultFileName and ResultDirectory](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive)

  - Added a new column for a TSContingency object called ResultDirectoryUsed which shows the directory to which results for this contingency will be saved. If ResultDirectory field is blank then it will show the global stability option folder, otherwise it will show ResultDirectory

  - Improved Algebraic Network Boundary equation solutions at the time of fault or fault clearing for the REGC\_B, REGC\_C, REGFM\_A1 and DER\_A machine models.

  - Modified the dialog that opens to show TSContingency objects with the multiple transient plot settings so it can be open while interacting with other dialogs. The dialog however will remain on top of the main transient stability dialog.

  - Added ability to see stability results on the Generator Dialog boxes. Shows Results from RAM, but only results related to the generator for that dialog.

  - Added new option for [Transient Stability under Options\\Power System Model\\Common which allows the user to specify two new options called MOD\_IslandNewCountBus and MOD\_IslandNewCountGen](37-transient-stability-analysis-dialog-part1.md#power-system-model). During a transient stability dynamic simulation, any newly created island must have at least that many buses and that many online generators to continue simulating. If a NEW island is small, then it will be numerically ignored and no longer simulated.

  - Added new fields to Area and Zone transient stability result storage to show the total Gen MW loss for the area or zone. This can be caused by tripping generation or by the generation becoming separated in a dead island.

  - Added a new feature to the TSGetResults() script command. When parsing the portion of that script command looking for specific Object | Field pairs or Plot Names, you may now also specify the syntax "ObjectName FilterName | FieldName". For this syntax anything after the first space and before the | character is considered a FilterName. The FilterName can be All indicating that all objects of the type ObjectName are used, or it can use the syntax available for defining a FilterName in all the other script commands. Examples would include "Bus All | TSFrequency" : exports Frequency for all buses, or "Bus NomkV \> 300 | TSFrequency" : exports frequency for all buses with a Nominal kV above 300

  - Updated Stability saving two bus equivalents to also store the substation to provide access to geographic information. Saving two bus equivalents for all generators and buses also now supports the use of area/zone filters.

  - Added the ability to open the BusView from the Solution Details tab in Transient Stability. It will open the BusView of the first Mismatch Bus (Mismatch Bus 1).

  - Customer had reported a long duration of Simulator window not responding, at the end of a distributed transient stability run. This was because contents of the AUX file produced during a transient contingency were ALL being loaded back into memory of the primary Simulator program. The amount of time for this can be significant, and this operation has now been threaded to allow results to be loaded back into memory as the results are returned from the distributed processes.

  - Added new script command TSPlotSeriesAdd("PlotName", SubPlotNum, AxisGroupNum, ObjectType, FieldType, "Filter", "Attributes"); (use to create plot series programatically)

  - Added new right-click option on the TSContingency Case Information Display to "Join Active Contingencies". This allows you to join two lists of TSContingency objects with a specified time delay in seconds. The options on the dialog that appears when choose this are the same as those for the new Script command TSJoinActiveCTGs(TimeDelay,DeleteExisting,JoinWithSelf,FileName,FirstCtg);

  - Continue to add support for reading and write both DYD and DYR file formats as we find new models in those formats which match PowerWorld's models

  - Transient Contingency Element Changes

      - Added the ability for a TSContingencyElement action to ChangeBy, Set, or Ramp the Pref, QVrefFrom, and QVrefTo of a VSCDCLine stability model as part of a contingency event. This allows the user to change the MW setpoint of a VSCDCLine as part of a simulation.

      - Modified the PlayInGen stability model to respond to the TSContingencyElement action for changing or setting the "rotor angle" of a generator so that it sets/changes the internal phase angle state of the PlayInGen. This can be used to simulate an instantaneous phase angle change in the system as described in NERC PRC-029-1

      - Added TSContingencyElement action for changing QVRef or Pref on a Bus controller object

      - Added a new Stability Generator event that allows an event to set the playin voltage magnitude and speed values. The event is valid for the Gen, Set Values to or Change Values Type. Set the Action Type to PlayIn Voltage Mag, Speed.

      - Added new transient stability TSContingencyElement actions for DC Lines. SET/CHANGEBY/RAMP actions for Vref/Iref/Pref with values specified in kV, Amps, MW or as a percentage of the initial condition value.  
        SET Vref 505 kV // Set Vref to 505 kV (DC voltage reference)  
        CHANGEBY Iref -100 Amps // change Iref by -100 Amps  
        RAMP Pref 1200 MW 10 // ramp Pref up to 1200 MW over 10 seconds

  - The following models were added:

      - PAUXSS1A

      - REEC\_E

      - REGFM\_A1 grid-forming converter model (it can accept inputs from Plant controllers such as REPC\_A)

      - REGC\_D

      - REGFM\_B1 model for modeling a Virtual Synchronous Machine grid forming machine model.

      - Added and Over-frequency and Over-voltage relay similar to the under-frequency and under-voltage relay TLIN1. The name of the relay is TLIN1O.

  - The following models were modified:

      - Added other fields Efdmax and Efdmin for exciter models EEST1A, ESST1A\_GE and ST1C, which show the dynamic limits \[(Vt \* Vrmax - Kc \* Ifd), (Vt \* Vrmin)\] on the output signal

      - Transient Stability model WT1P\_B is now translated to/from USRMDL WT12A1U\_B when writing/reading a DYR file

      - Transient Stability model WT2G is now translated to WT2G1 when writing a DYR file. This translation is exact only when Ra=0 in the original WT2G model.

      - When writing out a DYR file, added ability to translation from the models (WT2G + WT2E) to (WT2G1 + WT2E1)

      - Modified the INDMOT1P model to include new parameter Bpgas and Tpgas the add an additional term to the Mechanical Torque Equation equal to Bpgas\*Speed/(1+s\*Tpgas).

      - Added ability to read the cmp\_mo1ph model as a load component. Model is the same as a MOTORC model.

      - Signal E\_FE for exciter AC8C is now available for plotting in the transient stability plot designer

      - Added the Efe value to be shown in the Other Fields for Exciter AC7C

      - Modified the PVD1 machine model so that it will respond to TSContingencyElement actions which change the generator "Governor" or "Exciter" setpoints. The Pref in PVD1 will be treats as the governor setpoint and the Qref will be treated as the exciter setpoints. The PVD1 model itself should be used as a stand-alone model only however without an actual governor or exciter defined. This allows TSContingencyElement to change the MW and Mvar output of a generator with a PVD1 machine model.

      - Completed full implementation of current-dependent resistance and reactance for a Series Capacitor Metal Oxide Varistor (SCMOV) device. Previously SCMOV functioned but it either completely bypassed the device or operated in normal mode

      - Added ability to read/write HYG3 model from DYR files

      - For exciter model IEEET2, VE is now available as a signal in the "Exciter Other" folder in transient stability plot designer.

      - Added more descriptive information for transient events related to tripping of portions of the composite model induction model. The message will now make clear why the motor is tripping. The percentage and MW tripped will still show up as before.

User Interface Dialogs

  - Added a Limits tab to the Bus dialogs to show Bus-Specific Limits and Limit Monitoring Options

  - Choosing on the Window Ribbon Tab to "Reset to Defaults" now also resets the size and location of the Message Log dialog.

  - Refined the user interface for the Connections, Find Parallel Branches dialog. This is particularly helpful for finding parallel transformers with conflicting tap orientation

  - Enhanced the File Browser to return all file dates: created and last modified

  - The Island Dialog now shows the DC tielines. DCLines also can now show the rectified and inverter bus island numbers.

  - Added ability to show area fields on the SuperArea dialog case information display showing the list of areas inside the SuperArea.

  - Modified General File Browswer to open more file types (pptx, docx, xlsx, csv, and several image/movie foramats); it also now indicates why it can't open a file type.

  - Added "Set Selected Field for Branches" checkbox on the Facility Analysis (Minimum Cut) dialog. When this is checked the Selected field for branches that are part of the minimum cut will be set to YES. Prior to finding the minimum cut the Selected field should be set to desired values for all branches. Only the Selected field for branches in the minimum cut will be set to YES and other branches will not be reset.

  - In the General File Browser there is now 1) support for loading axd files and 2) an option to view the contents of the aux and axd files without loading them; with this option they are viewed in the computer's default text editor (what is associated with the \*.txt files).

  - Modified generator dialogs so that cubic cost function can not be entered which are non-convex functions between the MWMin and MWMax range of the generator. If specified that way the cost model will be changed to None and the cost function ignored for this generator.

  - When showing a transient stability plot, if the there were already plots open and the form that contained the plots was minimized then the newly created plot would be added to the minimized form and it was difficult for the user to realize the plot had been generated. Now when generating a plot we force the existing form showing plots to become un-minimized to you can see the plot immediately.

Weather

  - Added XYCurveX objects for providing the X value lookup for an XYCurve directly with the curve instead of passing the value from another object. This was added to support the structure needed when reading Areva hdbexport Dynamic Line Ratings (DLR) records.

---

<a id="getting-help"></a>

## Getting Help

*Source: [`Content/MainDocumentation_HTML/Getting_Help.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Getting_Help.htm)*

On-line help is available in PowerWorld Simulator via the **Help** ribbon group on the [Window](02-simulator-ribbon.md#window-tab-overview) ribbon tab, or by pressing the **F1** key on many dialogs and displays. Context-sensitive help is available on the oneline diagrams. To obtain object specific help, position the mouse over the object in question on the oneline and press the **F1** key.

Sample power flow cases and other information are available at the PowerWorld web site: [http://www.powerworld.com](https://www.powerworld.com/WebHelp/)

Contact technical support at <support@powerworld.com> for answers to your questions regarding any PowerWorld product. Or call us at (217) 384-6330.

**PowerWorld Corporation**

2001 S. First Street

Suite 203

Champaign, IL 61820

---

<a id="windows-basics"></a>

## Windows Basics

*Source: [`Content/MainDocumentation_HTML/Windows_Basics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Windows_Basics.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Operating System

Simulator runs under all Windows XP and later Microsoft Windows Operating Systems.

Mouse Conventions

Since much of the interaction between Simulator and the user is accomplished by using the mouse, we have designed the interface to obey consistent conventions for mouse usage. In general, the left-mouse button is used to affect some sort of immediate change or control over a power system element, while the right mouse button is used to gain more information about a power system element or to view a list of available options. More details on mouse usage are provided throughout this manual.

Dialog Window Position, Size Tracking

As various dialogs are opened, PowerWorld will keep track of the Free-Floating/Contained style as well as the position and size of each dialog. When that dialog is then opened again it will open to the same style, size, and position as it was previously. These settings are stored in the Windows registry so that they are remembered when the program is opened again. You can always reset all these settings to their factory defaults by clicking the **Reset to Default** button on the Window Ribbon Group in the [Windows Ribbon Tab](02-simulator-ribbon.md#window-tab-overview).

Dialog Window Styles (Free-Floating, Free-Floating On Top, and In Container)

By default, most dialogs or windows when opened are contained inside the main program window. (The only general exception to this are dialogs that are opened as "modal" windows which you must close before continuing to use the software.) You can change this default globally by choosing **Switch to Free-Floating Windows** on the Window Ribbon Group in the [Windows Ribbon Tab](02-simulator-ribbon.md#window-tab-overview). Alternatively, you can leave most windows in the container and individually choose to make specific windows Free-Floating. This is done by left clicking on the icon in the upper left of the dialog to open the windows system menu. This is allowed for all windows except for oneline diagrams. (Oneline diagrams always appear inside the main container window.) For windows that we allow this for, three choices will appear as shown below.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><img src="images/Windows_SystemMenu.gif" alt="Windows SystemMenu" /></td>
<td><p>In Container Window</p>
<p>In Container Window is the same as the default behavior for most windows. The dialog will be contained inside the main program shell and can not be moved outside of it.</p>
<p>Free-Floating on Top</p>
<p>Setting a window or dialog to Free-Floating on Top will make the window float independent of the main program shell. The dialog will also always remain on top of the main program shell and thus can not get lost behind the main program shell. The <a href="#message-log">message log</a> window is one of a small number of windows that defaults to this behavior.</p>
<p>Free Floating</p>
<p>This style is the same as Free-Floating on Top, however the dialog will become hidden behind the main program window when the main program window becomes active.</p></td>
</tr>
</tbody>
</table>

Example Windows Styles

![Window Floating](images/Window_Floating.gif)

![Window Contained](images/Window_Contained.gif)

---

<a id="touchscreen-interaction"></a>

## Touchscreen Interaction

*Source: [`Content/MainDocumentation_HTML/Touchscreen_Features.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Touchscreen_Features.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator supports interactions using the Microsoft Windows Touch features on a multi-touch monitor. Interactions using the touch screen augment the interaction possible with the more traditional mouse and keyboard. The actually interactions on the touchscreen are referred to as *Gestures* with the following representing typical gestures. After the list of gestures is a list of where these can presently be using the PowerWorld Simulator Interface.

Touchscreen Gestures

The combination of a few simple patterns in different contexts allow for a variety of complex interactions with a diagram on a multi-touch screen. The following are the basic gestures used in the Simulator interface.

Tap

A finger is touched to the screen briefly, and removed

Press

A finger is touched to the screen and held for the duration of the gesture

Two-finger Tap

Two fingers are tapped simultaneously. This is distinct from a "double-tap", which is like a double-click with a mouse.

Press-Tap

One finger is pressed on a point of interest; while the first finger is held in place, another finger taps elsewhere.

Press-and-Hold

One finger is pressed on a point of interest and held for one full second. By default, this is interpreted as a mouse right-click.

One-finger Pan

One finger is pressed and dragged, similar to a drag-drop movement with a mouse.

Two-finger Pan

Two fingers are pressed and dragged together. In some areas this operates the same as a One-finger Pan.

Pinch

Two fingers are pressed simultaneously, and dragged toward or away from each other.

Rotate

Two fingers are pressed simultaneously, and one is dragged in a circular motion around the other.

Oneline Diagram Navigation

On a oneline diagrams, the following features are enabled

Panning

Simple **One-finger Pan** interface; operates exactly the same as clicking and dragging with the mouse

Zooming

A **Pinch** operation – moving the pressed points together zooms out, dragging them apart zooms in. Additionally, a **Two-finger Tap** zooms to display the entire oneline (operates like the "Show Full" button)

Accessing Local Menu

The oneline local menu normally accessible with a click of the right-mouse-button can be brought up with a **Press-and-Hold** gesture on the oneline background. The menu will open upon release.

Finding Oneline Elements

Oneline navigation is facilitated by making the "Find Element" dialog easily accessible at any time. A **Press-Tap** gesture on the oneline background will bring up this dialog

Oneline Element Interaction

Oneline diagrams can provide easy access to information on specific elements of the system. The following are some ways in which this access can be enhanced with a touchscreen interface.

Tap Correction

Tapping is an imprecise interface, and getting an exact tap on a small oneline element can be very difficult. In touchscreen mode, a tap or press which lands on the oneline background (but close to a displayed element) is interpreted as a tap or press on that element. The amount of correction desired can be set with the Tap Correction slider on the [Simulator Options Dialog under Environment.](10-power-flow-solution-and-options-part2.md#environment-options)

Local Menu

The oneline local menu normally accessible with a click of the right-mouse-button on an oneline element can be brought up with a **Press-and-Hold** gesture on the desired oneline element. The menu will open upon release.

Opening Object Dialogs

A **Double-Tap** (just like a double click in the keyboard/mouse interface) on an element of the oneline opens that element's dialog.

Bus View

A **Press-Tap** gesture on a bus will open a new Bus View window for the specified bus.

Additional Oneline Navigation Options

An additional navigation bar is available in fullscreen oneline diagrams if the **Use Touchscreen Menu**checkbox on the [Simulator Options Dialog under Environment](10-power-flow-solution-and-options-part2.md#environment-options) is enabled. This menu-bar appears at the bottom of the screen with large, easily tapped buttons. Four context buttons are displayed on the lower left corner of the screen, which are used to populate the rest of the touchscreen menu bar.

Open Onelines

This populates the touchscreen menu bar with a collection of buttons similar to the "Open Windows" dropdown menu in the Ribbon Bar. This allows for fast, easy navigation between diagrams

Saved Views

Tapping this button brings up a collection of buttons corresponding to any saved views associated with the active display.

Screen Layers

This button gives quick access to a list of screen layers in the active display, allowing easy control over the level of detail displayed.

Saved Hotkeys

Tying common actions to a hotkey through the normal Simulator interface allows those actions to be executed quickly and easily; this button populates the touchscreen menu bar with buttons corresponding to all custom hotkey actions.

3D Oneline Navigation

A number of touchscreen gestures are available to facilitate navigation in 3D space.

Center View On Point

Some of the following gestures act in reference to the view's center-point. To center the view on a point of interest, simply **Press-Tap** on that point.

Transformational Panning

Just as a drag-and-drop movement with the mouse moves the 3D camera view over the oneline, a simple **One-finger Pan** gesture will change the location of the camera without altering the angle of view.

Rotational Panning

A **Two-finger Pan** gesture controls the view-angle of the 3D camera without changing its location.

Zoom

A **Pinch** gesture moves the 3D camera toward or away from the view center point.

Spin

A **Rotate** gesture holds the view center constant while spinning the 3D camera around that point.

Overhead View

A **Two-finger Tap** gesture returns the 3D view to its default overhead orientation, positioned over the current view center-point.

Local Menu

The oneline local menu normally accessible with a click of the right-mouse-button can be brought up with a **Press-and-Hold** gesture. The menu will open upon release.

Case Information Display Navigation

Case information displays are a major part of the Simulator interface, but the small cells can be difficult to manipulate with a touchscreen. Some gestures have been implemented to ease that interaction.

Zoom

A **Pinch** gesture will change the magnification level of a case information display. A **Two-finger Tap** anywhere on the case information display will restore the zoom level to 100%

Reorder Columns

Using a **One-finger Pan** on a column header allows for drag-drop re-ordering similar to Ctrl-Left Mouse Drag.

Local Menu

The case information display local menu normally accessible with a click of the right-mouse-button can be brought up with a **Press-and-Hold** gesture. The menu will open upon release.

Sort

A **Press-Tap** gesture on a column will sort all rows based on the values in that column. Depending on the location of the tap, different sorting methods can be specified or toggled. A tap on the same horizontal or vertical level as the press point will toggle between sorting methods, while a tap on a diagonal corresponds to a specific sorting method. A taps on an upward diagonal sorts in an ascending order, a lower diagonal sorts in descending order; a taps on a right diagonal sorts by actual value, a tap on a left diagonal sorts by absolute value:

![TapLocations](images/TapLocations.gif)

---

<a id="powerworld-simulator-getting-started"></a>

## PowerWorld Simulator: Getting Started

*Source: [`Content/MainDocumentation_HTML/Powerworld_Simulator_Getting_Started.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Powerworld_Simulator_Getting_Started.htm)*

The key to using Simulator is to recognize that it has two distinct modes **Edit Mode** and **Run Mode**. The Edit Mode is used to construct new simulation cases or to modify existing cases, while the Run Mode is used to perform the actual power system simulation. You can easily switch between the modes using the **Edit Mode** and **Run Mode** buttons in the **Mode** ribbon group.

If you are new to Simulator and seek a quick means of familiarizing yourself with it, we recommend starting with the tutorials; see [Tutorial Links](49-distributed-computing-and-tutorials.md#tutorials)

Sample cases are provided with the software installation in the C:\\Users\\Public\\Documents\\PowerWorld\\*Simulator version*\\Sample Cases directory. If you are interested in learning by doing, you may wish to [open one of the sample cases](03-cases-files-and-formats.md#opening-a-simulation-case) and try the different Simulator features.

---

<a id="edit-mode-introduction"></a>

## Edit Mode Introduction

*Source: [`Content/MainDocumentation_HTML/Edit_Mode_Introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Edit_Mode_Introduction.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Edit Mode is used to create a new case or to modify existing cases. To switch to Edit Mode, click on the **Edit Mode** button in the **Mode** ribbon group on any of the ribbon tabs.

Here is a sampling of things you can do in Edit Mode:

  - Create a new case; see [New Case](03-cases-files-and-formats.md#building-a-new-case) for details.
  - Create a new oneline diagram; see [New Oneline](03-cases-files-and-formats.md#building-a-new-oneline) for details.
  - Add new components graphically to an existing case; see [Draw](02-simulator-ribbon.md#draw-tab-overview) ribbon tab.
  - Modify the appearance of the oneline objects; see [Formatting](02-simulator-ribbon.md#formatting-ribbon-group) ribbon group for details.
  - View and modify a case using non-graphical lists displays; see [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) for details.
  - Equivalence a case; see [Equivalencing](19-edit-mode-tools.md#equivalents-display) for details.
  - Append a subsystem to an existing case; see [Appending a Case](19-edit-mode-tools.md#appending-a-case) for details.

For more details on the Edit Mode please see [Edit Mode Overview](11-building-onelines-network-objects.md#edit-mode-general-procedures).

---

<a id="run-mode-introduction"></a>

## Run Mode Introduction

*Source: [`Content/MainDocumentation_HTML/Run_Mode_Introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Run_Mode_Introduction.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Run Mode is used to solve a single Power Flow Solution, run one of the available load flow tools, or run a time-domain simulation of the power system. To access Run Mode, click on the **Run Mode** button in the **Mode** group of the Simulator Ribbon.

The key ribbon group associated with the Run Mode is the [Tools](02-simulator-ribbon.md#simulation-control) ribbon group. This ribbon group allows you to perform a single Power Flow Solution (however, it is quicker to use the [Quick Access](02-simulator-ribbon.md#quick-access-toolbar) toolbar).

Other key components of Run Mode include:

  - The oneline diagrams, which allow you to view the case graphically. See [Oneline Diagram Overview](15-using-onelines-tools-and-options.md#oneline-diagram-overview) for details.
  - The Case Information Displays, which allow you to view the entire power system case using list displays. See [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) for details.
  - Dialogs to change the simulation options and the Power Flow Solution. See [Simulation Options](10-power-flow-solution-and-options-part1.md#simulator-options) for details.
  - Scaling to allow easy variation in the load, shunts, and generation at any number of buses. See [Scaling](18-general-tools.md#scaling) for details.
  - Contouring, which shows a color contour representing the variation in any power system parameter across a system. See [Contouring](17-oneline-view-printing-and-contouring.md#contouring) for details.
  - Run [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - Transfer distribution factor calculations. See [Power Transfer Distribution Factors](20-sensitivities.md#power-transfer-distribution-factors) for details.
  - Perform a fault analysis. See [Fault Analysis](27-fault-analysis.md#fault-analysis) for details.
  - Run [Available Transfer Capability](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) studies.
  - Perform an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) (OPF) or [Security Constrained Optimal Power Flow](31-scopf-and-opf-reserves.md#security-constrained-opf-overview) (SCOPF) analysis.
  - Generate [PV and QV curves](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview).

---

<a id="script-mode-introduction"></a>

## Script Mode Introduction

*Source: [`Content/MainDocumentation_HTML/Script_Mode_Introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Script_Mode_Introduction.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Script Mode is used to access the Script Command window. Simulator scripting allows a method of grouping multiple commands for sequential processing by Simulator. From the [Script Command Execution](09-auxiliary-files-and-script-commands.md#script-command-execution-dialog) window, the user can manually enter script commands for processing, or load an [auxiliary file](03-cases-files-and-formats.md#auxiliary-file-format-aux) containing multiple script commands and data modification commands. This dialog is useful for debugging script commands while creating an auxiliary file.

Some features in Simulator are meant to be used in either [RUN](#run-mode-introduction) mode or [EDIT](#edit-mode-introduction) mode. This functionality is preserved in the script language. If the Script Command Execution Dialog is opened from Edit Mode, Simulator defaults to **EDIT** mode. If the Script Command Execution Dialog is opened from Run Mode (or when a script is initially started), Simulator defaults to the **RUN** mode.

To switch modes, use the EnterMode (mode) script command. Simulator will switch to RUN mode automatically for script commands that require that mode. EDIT mode is required to create new objects for most object types.

See the [Auxiliary Files and Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux) topic for more details.

---

<a id="message-log"></a>

## Message Log

*Source: [`Content/MainDocumentation_HTML/Message_Log.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Message_Log.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Message Log displays detailed results of each Power Flow Solution, chronicling the solution process iteration by iteration. It also reports messages raised by Simulator in performing various operations, such as opening or validating a case. The Message Log can be helpful when you run into problems solving a particular simulation case. The Message Log is not used with Viewer.

To display the Message Log, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and click the button ![Ribbon Tools Log](images/Ribbon_Tools_Log.gif)**Log** on the **Log** ribbon group. This button is also available on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab.

The Message Log is one of the few windows that is set by default to be **Free-Floating On Top**. This means that the dialog floats independently of the main program window and always remains on top of the main container window. If you would like to change this style to make the message log contained inside the container window, see the [Window Basics](#windows-basics) help for more information.

Message Log Local Menu

Right-clicking on the Message Log displays its local menu. To change the font characteristics of the log, select **Change** **Font**.

To suppress or change color of [certain messages associated with the power flow case](10-power-flow-solution-and-options-part2.md#message-log-options) select either **Suppress** **Messages** or **Color** **Messages** and then the desired message whose characteristics want to change. For more information about the colors and messages see the [Message Log Options.](10-power-flow-solution-and-options-part2.md#message-log-options)

You can find certain text by clicking on **Find**, and then entering the text in the dialog displayed. Also, you can highlight all the text in the log, or inversely unselect all the highlighted text by clicking on **Select All (CTRL+A)**, or **Unselect All**, respectively. To print or copy the contents to the Windows clipboard of a highlighted section of the message log, select **Print Selection** or **Copy Selection to Clipboard (CTRL+C)**. You can also clear the contents of the log by selecting **Clear Window**. Lastly, you will find some log options available, such as **Change Maximum Lines**, **Disable Logging**, **Disable Time Stamp**, and **Save Log to File** options which allow automatically saving the log to a file during load flow analysis.

Message Log Color Outlines and Color Background

When solving the power flow, there are several loops which occur that are discussed the [Solving the Power Flow](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) Topic. These loops will generate **Red**, **Purple**, **Green**, and **Blue** outlines on the message log to visually indicate which loop the message text is generated by. This helps in determining which part of a the power flow solution may be having difficulty solving.

Additionally, when the various tools and add-ons send message text to the log the background of the text will be colored to indicate this. For instance, contingency analysis actions originating from the contingency will be highlighted with a light blue background, while PV, QV, ATC, and OPF add-on message text will be highlighted with a light yellow background.

---

<a id="memo-display"></a>

## Memo Display

*Source: [`Content/MainDocumentation_HTML/Memo_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Memo_Display.htm)*

The Custom tab is now available on many dialogs and displays in Simulator. The purpose of the custom tab is to allow the user to add their own custom information and comments to data and objects in the load flow case. Simply switch to the Memo or Custom page on a display and start typing in the memo box, or add values or text in the custom fields. The information added to these memo pages is stored with the objects in the load flow case and saved to [PWB](03-cases-files-and-formats.md#case-formats) files.

The custom fields section allows access to setting and changing the values for custom fields that have been defined for the object. Defining custom fields is detailed in [Custom Field Descriptions](04-model-explorer-and-case-information-part1.md#custom-field-descriptions).

The custom section also contains a **Selected** check box. This is a special field that is associated with most objects in Simulator. In many of the places where filtering is allowed, filtering can be done based on the **Selected** field. Additional information about this field can be found under the [Set Selected Field](18-general-tools.md#set-selected-field) topic.

The memo section of the dialog is simply a location to log information about the object. Any information entered in the memo box will be stored with the case when the case is saved to a [PWB](03-cases-files-and-formats.md#case-formats) file.

---

<a id="status-bar"></a>

## Status Bar

*Source: [`Content/MainDocumentation_HTML/Status_Bar.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Status_Bar.htm)*

The Status Bar is displayed across the bottom of the PowerWorld Simulator window. The left-most field of the status bar displays the current Simulator mode (Edit or Run). The remaining fields vary depending on which mode of operation Simulator is currently in. The status bar displays Tool Tips when the cursor is positioned over a toolbar button or menu item. The tool tip is also shown next to the cursor after a short time delay.

Edit Mode

The Edit Mode status bar displays the [Screen Coordinates](17-oneline-view-printing-and-contouring.md#oneline-screen-coordinates) of the cursor when positioned over a oneline diagram.

![image\\ebx\_-24542984.gif](images/ebx_-24542984_190x18.gif)

Edit Mode Status Bar

Run Mode

The left side of the Run Mode status bar displays simulation status ("Solution Animation Stopped" or "Solution Animation Running"), AC or DC depending on solution options and the [Difference Case Mode](https://www.powerworld.com/WebHelpRelatedTopic0.Click\(\)) ("Present", "Base", "Difference", or "Change").

![image\\ebx\_926401207.gif](images/ebx_926401207_522x18.gif)

**Run Mode Status Bar (Left Side)**
