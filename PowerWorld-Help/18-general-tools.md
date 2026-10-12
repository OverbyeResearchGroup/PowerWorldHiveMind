---
title: "General Tools"
part: "Tools"
chapter_file: "18-general-tools.md"
topics: 22
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# General Tools

Limit monitoring, difference case, scale case, connections tools and other general-purpose tools.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (22)**

- [Limit Monitoring Settings](#limit-monitoring-settings)
- [Limit Monitoring Settings and Limit Violations Dialog](#limit-monitoring-settings-and-limit-violations-dialog)
- [Limit Group Dialog](#limit-group-dialog)
- [Scaling](#scaling)
- [Find Radial Bus Paths](#find-radial-bus-paths)
- [Find Circulating MW or MVAr Flows](#find-circulating-mw-or-mvar-flows)
- [Overview of Facility Analysis](#overview-of-facility-analysis)
- [Facility Analysis Dialog](#facility-analysis-dialog)
- [Augmenting Path Max Flow Min Cut Algorithm](#augmenting-path-max-flow-min-cut-algorithm)
- [Graph Flow](#graph-flow)
- [Branches that Create Islands](#branches-that-create-islands)
- [Set Selected Field for Network Cut](#set-selected-field-for-network-cut)
- [Set Bus Field From Closest Bus](#set-bus-field-from-closest-bus)
- [Breaker Isolated Groups](#breaker-isolated-groups)
- [Governor Power Flow](#governor-power-flow)
- [Generator Options Tab](#generator-options-tab)
- [Options Tab](#options-tab)
- [Set Selected Field](#set-selected-field)
- [Create New Areas for Islands](#create-new-areas-for-islands)
- [Browse PWB File Headers](#browse-pwb-file-headers)
- [Browse Open Onelines](#browse-open-onelines)
- [Unused Bus Numbers](#unused-bus-numbers)

---

<a id="limit-monitoring-settings"></a>

## Limit Monitoring Settings

*Source: [`Content/MainDocumentation_HTML/Limit_Monitoring_Settings.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Limit_Monitoring_Settings.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator offers many tools to study the capabilities of a power system. Examples include:

  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - [Available Transfer Capability (ATC)](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)
  - [Optimal Power Flow (OPF)](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)
  - [Security Constrained OPF (SCOPF) Overview](31-scopf-and-opf-reserves.md#security-constrained-opf-overview)
  - [PV Curve and QV Curve Tool](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)

All of these tools make extensive use of power system limits. Limits for various power system elements include:

  - MVA (or Amp) limits on transmission lines and transformers
  - MW limits on Interfaces
  - Angle limits on Bus Pairs Added in Version 20
  - High and low voltage limits for Buses

The accuracy of all these limits is very important, as is the specification of which limits should be monitored. While ensuring the accuracy of input data such as power system limits must be left to the user, PowerWorld Simulator provides several ways to specify which limits should be monitored. Limit Monitoring is specified according to settings for the Area, Zone and Limit Group to which the power system element belongs. A power system element is monitored only if ALL of the following conditions are met.

Conditions for Monitoring an Element’s Limit

  - Its Monitor field is set to **YES**
  - Its Limit Group is Enabled
  - Its Area is set to Report Limits and it meets the KV range for reporting
  - Its Zone is set to Report Limits and it meets the KV range for reporting

The [Limit Monitoring Settings Dialog](#limit-monitoring-settings-and-limit-violations-dialog) gives you ability to specify all these settings to setup the limits you want to monitor, and thus enforce in the various tools that Simulator provides.

---

<a id="limit-monitoring-settings-and-limit-violations-dialog"></a>

## Limit Monitoring Settings and Limit Violations Dialog

*Source: [`Content/MainDocumentation_HTML/Limit_Monitoring_Settings_and_Limit_Violations_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Limit_Monitoring_Settings_and_Limit_Violations_Dialog.htm)*

The Limit Monitoring Settings Dialog is accessed from several locations.

Limit Monitoring Settings button on either the [Case Information ribbon tab](02-simulator-ribbon.md#case-information-tab-overview)

Limit Monitoring Settings button on the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group) of the [Tools ribbon tab](02-simulator-ribbon.md#tools-tab-overview).

Many different tool dialogs such as the [Contingency Analysis Dialog](22-contingency-analysis-options.md#limit-monitoring) and [Available Transfer Capability Dialog](32-available-transfer-capability.md#common-options),

The Limit Monitoring Settings Dialog gives you ability to specify which limits you want to monitor, and thus enforce in the various tools that Simulator provides. In general, keep in mind that a bus, transmission line/transformer, or interface’s limit is monitored only if the following conditions are met.

Conditions for Monitoring an Element’s Limit

  - Its Monitor field is set to **YES**
  - Its Limit Group is Enabled
  - Its Area is set to Report Limits and it meets the KV range for reporting
  - Its Zone is set to Report Limits and it meets the KV range for reporting

The following fields are shown on the display:

Elements To Show

Change this value to modify which elements are displayed in the Buses, Lines, and Interfaces. Set it to…

**All Elements** to show all Buses, Lines and Interfaces regardless of monitoring settings.

**Monitored Elements **to only display Buses, Lines and Interfaces that meet the conditions for monitoring. See [Limit Monitoring Settings](#limit-monitoring-settings) for more information on setting which values are monitored.

**Violating Elements **to only display Buses, Lines and Interfaces that are violating. See [Limit Monitoring Settings](#limit-monitoring-settings) for more information on setting what is considered a violation.

Number of Violations

The following fields provide summary information on the types of violations that are currently present in the case:

High Voltage Buses and Low Voltage Buses

Shows the total number of bus voltage magnitude violations. These violations are shown on the **Bus Voltage Magnitude Limit Violations Display**.

Low Voltage Suspects

Shows the total number of buses whose voltages have fallen below a designated internal threshold to indicate a low voltage solution is being reached in some location in the system.

Line/Transformer Violations

Shows the total number of line/transformer violations.  These violations are shown on **Line and Transformer Limit Display**.

Interface Violations

Indicates the total number of interface violations. These violations are shown on the **Interface Violations Display**.

Bus Pair ViolationsAdded in Version 20

Indicates the total number of bus pair violations. These violations are shown on the **Bus Pair Violations Display**.

Limit Group Values

This part of the dialog shows information about the Limit Groups with greater description shown below.

Save/Load Monitoring Settings

The Save and Load Monitoring Settings buttons allow the user to save the current set or load a previously saved set of Limit Monitoring Settings options. The options are saved in a [PowerWorld Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux) text format.

Do not monitor radial lines and buses

Check this box to ignore limits on radial lines and buses throughout the case. In this instance a radial bus is defined as a bus that is connected to the rest of the power system by a single in-service transmission line. A radial line is the defined as a line connected to a radial bus. This means that in a 5 lines in series that connect to a radial load, only the last bus and last line will be considered radial.

If you would like to better determine which lines are "radial" in a more traditional sense, use the feature [Branches that Create Islands](#branches-that-create-islands) that allows you to easily generate a list of branches that if taken out of service will split an existing island into two. These represent lines which may be considered radial.

Radial lines and buses are always monitored when using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), and this option is ignored.

**Tabs on the Limit Monitoring Dialog**

The tabs on the Limit Monitoring Settings Dialog allow you to change these settings. These tabs contain tables showing lists of the respective elements. Since these tables are another variety of the [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays), you may interact with it in a familiar manner. Click on any of the field headings to sort by that field. Right-click on the display to call up the display’s [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options). From the local menu, you can print the violations, [copy the violation records](04-model-explorer-and-case-information-part3.md#copying-simulator-data-to-and-from-other-applications) to the Windows clipboard for use with another application, modify the format and content of the violations listing, view the information dialog of the respective element, and view the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display).

Buses Tab

Each tab shows a list of the respective type of power system element. The important columns include:

**Number, Name:**Bus number between 1 and 99,999, and its alphanumeric identifier.

**Area Name:**Alphanumeric identifier of the bus’ area.

**Monitor:** toggle this between **YES** and **NO** to set whether the specific element should be monitored.

**Limit Group:** toggle this value to specify which Limit Group the element belongs to

**PU Volt:**Bus’ per unit voltage magnitude.

**Volt (kV):** Bus’ actual voltage magnitude in kV. This is the per unit voltage magnitude multiplied by the bus’ nominal voltage.

**Limit Low PU Volt:** Bus' individual low voltage limit used when the bus is set to use specific voltage limits other than the default voltage limit defined in the bus' limit group. This field is not enabled unless the "Use Specific Limits" option for the bus is set to YES. The value will then reflect the low per unit voltage limit specified in one of the eight low voltage limit sets that can be defined with the bus. Which voltage limit set's value is displayed depends on which limit set is specified as the "Bus Low Rate Set" in the limit group to which the bus is assigned.

**Limit High PU Volt:** Bus' individual high voltage limit used when the bus is set to use specific voltage limits other than the default voltage limit defined in the bus' limit group. This field is not enabled unless the "Use Specific Limits" option for the bus is set to YES. The value will then reflect the high per unit voltage limit specified in one of the eight high voltage limit sets that can be defined with the bus. Which voltage limit set's value is displayed depends on which limit set is specified as the "Bus High Rate Set" in the limit group to which the bus is assigned.

**Contingency Limit Low PU Volt:** Bus' individual low voltage limit used during a contingency when the bus is set to use specific voltage limits other than the default voltage limit defined in the bus' limit group. This field is not enabled unless the "Use Specific Limits" option for the bus is set to YES. The value will then reflect the contingency low per unit voltage limit specified in one of the eight contingency low voltage limit sets that can be defined with the bus. Which contingency voltage limit set's value is displayed depends on which limit set is specified as the "Bus CTG Low Rate Set" in the limit group to which the bus is assigned.

**Contingency Limit High PU Volt:** Bus' individual high voltage limit used during a contingency when the bus is set to use specific voltage limits other than the default voltage limit defined in the bus' limit group. This field is not enabled unless the "Use Specific Limits" option for the bus is set to YES. The value will then reflect the contingency high per unit voltage limit specified in one of the eight contingency high voltage limit sets that can be defined with the bus. Which contingency voltage limit set's value is displayed depends on which limit set is specified as the "Bus CTG High Rate Set" in the limit group to which the bus is assigned.

Note: If **Elements to Show** is set to *Monitored Elements*, then only elements which meet the conditions for monitoring will be displayed in these lists.

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), the **Only show the primary bus for each superbus** checkbox will be available. Checking this box will limit the buses shown to only those that are primary buses. This provides a quick means of removing the clutter of redundant data. The primary buses and superbuses are determined from the base case topology. In addition to monitoring the primary bus for each superbus, the bus with the highest low voltage limit and the bus with the lowest high voltage limit will also be monitored so as not to miss any possible violations.

Lines Tab

Each tab shows a list of the respective type of power system element. The important columns include

**From Bus Number and Name:**Bus number at name at the from terminal of the line. For transformers, the from bus is the tapped side. Right- clicking on either of these fields allows you to see all the flows measured at the "from" bus using the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) local menu options.

**To Bus Number and Name:**Bus number at name at the to terminal of the line. For transformers, the to bus is the untapped side. Right-clicking on either of these fields allows you to see all the flows into the "to" bus using the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display) local menu options.

**Circuit:**Two-character identifier used to distinguish between multiple lines joining the same two buses.

**Monitor:** toggle this between **YES** and **NO** to set whether the specific element should be monitored.

**Limit Group:** toggle this value to specify which Limit Groups the element belongs to

**Used Limiting Flow, Limit, Used % of Limit:**The flow at the end of the branch selected for measurement, and its MVA or Amp limit. The percentage equivalent of the flow to it’s limit is given in the Used % of Limit column.

**MVA or Amps?:** Units used with the Max Flow and the Limit field. All flows are expressed either in MVA or amps.

Note: If **Elements to Show** is set to *Monitored Elements*, then only elements which meet the conditions for monitoring will be displayed in these lists.

Interfaces, Bus Pairs, and Nomograms Tab

Similar to the Buses and Lines Tabs shown above. The important columns are the **Monitor** and **Limit Group** columns

Area Reporting and Zone Reporting Tabs

These tabs display all the Areas and Zones in the system. The important columns are

**Report Limits:**toggle this between **YES** and **NO** to set whether the specific element should be monitored.

**Report Min kV and Report Max kV:**Only buses and lines within this kV range will be monitored.

Modify/Create Limit Group Tab

Every power system elements belongs to a single Limit Group. By default, all power system elements are in the same Limit Group that is named "**Default**". New limit groups can be added by right-clicking in the table and choosing **Insert** from the popup menu. Additional limit groups give the flexibility of assigning devices to different groups, where each group can have its own set of defined limit information.

The limit group stores important values regarding the enforcement and monitoring of the power system elements within the Limit Group. The values are:

**Disabled: **Set the value to **YES** to ignore all power system element limits in the Limit Group. Set the value to **NO** to monitor limits according to the settings of the Limit Group.

**Branch Percentage:** The percentage to which Simulator’s study tools will limit a line or transformer. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), then lines will be flagged as violated if they exceed this percentage. In performing an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview), all attempts will be made to keep the line below this percentage.

**Line Rate Set: **You may define eight different ratings to transmission lines or transformers (for more information see [Line/Transformer Information](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options)). Change this value to specify which rating set should be used for lines/transformers in the limit group.

**Contingency Line Rate Set:**  This field specifies the rating set used for post-contingency monitoring of Lines/Transformers.

**Amps or MVA:**  Limits for transmission lines and transformers are always entered in MVA. However, when reporting limit violations, it is common to check transmission line limits in terms of their amp loading. If the Treat Line Limits As Equivalent Amps is checked, the limits for transmission lines are reported in amps rather than MVA. If this box is not checked, limits for both transmission lines and transformers are expressed in MVA.

 For reference, note that the amp rating of a line is derived from the MVA rating using the formula 

![AmpRating](images/AmpRating.gif)

Also note that the reported Amp% and MVA% will be different by a factor of the per unit voltage at the bus terminal at which the limiting flow is determined. This is often a point of confusion as the expectation might be that the percent loading would be the same regardless of which reporting method is used: **Amp%** = **MVA%**/**(Per Unit Voltage)**

When doing contingency analysis and the Power Flow Solution Options are set to [Use the DC Approximation in Power Flow](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options), this option will be ignored. Line limits will always be reported in MVA when using the DC approximation.

**Interface Percentage:** The percentage to which Simulator’s study tools will limit an interface. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), then interfaces will be flagged as violated if they exceed this percentage. In performing an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview), all attempts will be made to keep the interface below this percentage.

**Interface Rate Set: **You may define 15 different ratings to an interface. Change this value to specify which rating set should be used for interfaces in the limit group.

**Interface Contingency Rate Set:** This field specifies the rating set used for post-contingency monitoring of Interfaces during Contingency Analysis.

**Bus Pair Percentage:**Added in Version 20 The percentage to which Simulator’s study tools will limit an bus pair. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), then bus pairs will be flagged as violated if they exceed this percentage of their limit..

**Bus Pair Rate Set: **Added in Version 20You may define 4 different ratings to an bus pair. Change this value to specify which rating set should be used for bus pair in the limit group.

**Bus Pair Contingency Rate Set:**Added in Version 20 This field specifies the rating set used for post-contingency monitoring of bus pairs during Contingency Analysis.

**Low PU Volt:** Buses will be flagged as violated if they fall below this per unit voltage.

**High PU Volt: **Buses will be flagged as violated if they go above this per unit voltage.

**Contingency Low PU Volt:** Buses will be flagged as violated during contingencies if they fall below this per unit voltage.

**Contingency High PU Volt: **Buses will be flagged as violated during contingencies if they go above this per unit voltage.

**Bus Low Rate Set: **This field value indicates which bus voltage rating set should be used for normal (non-contingency) low voltage violation reporting.

**Bus High Rate Set: **This field value indicates which bus voltage rating set should be used for normal (non-contingency) high voltage violation reporting.

**Bus Contingency Low Rate Set: **This field value indicates which bus voltage rating set should be used for low voltage contingency violation reporting.

**Bus Contingency High Rate Set: **This field value indicates which bus voltage rating set should be used for high voltage contingency violation reporting.

**Nomogram Percentage: **The percentage to which Simulator’s study tools will limit a nomogram.

**Limiting End: **Specified as higher or lower, this field determines whether the higher or the lower flow amount on the element is used for reporting a limit violation. If you use higher, it is possible that the lower flow is not violating the line limit. If you use lower, then you are guaranteed that the element limit is being violated at both ends of the element.

**Use Limit Cost:** If this field is set to yes, you are enabling the capability to have a cost function associated with enforcing constraints. This cost function can be viewed as similar to a generator cost function, in that as the constraint becomes overloaded by larger amounts, the marginal cost of enforcing the constraint will increase. For setting the piecewise linear limit cost curve, right-click and choose show dialog from the popup menu to access the Limit Group Dialog.

Often monitoring elements according to Area and/or Zone is all that you need. However, if you need to monitor specific groups of power system elements and not others then you need to create some new Limit Groups.

---

<a id="limit-group-dialog"></a>

## Limit Group Dialog

*Source: [`Content/MainDocumentation_HTML/Limit_Group_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Limit_Group_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Limit Group Dialog reflects much of the same information that is summarized in the [Limit Monitoring Settings](#limit-monitoring-settings-and-limit-violations-dialog) dialog’s **Modify/Create Limit Groups** page. The same information can be changed here as on the previously mentioned display. One important feature that is unique to this dialog is the ability to define a piecewise linear limit cost curve, which can be used for setting up "soft" constraints used in the [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview).

To access this dialog, right-click on one of the limit groups defined on the **Modify/Create Limit Groups** page of the Limit Monitoring Settings dialog and choose **Show Dialog**.

The dialog contains the following options regardless of the tab that is selected:

Limit Group Name

Identifies the name of the Limit Group that is currently selected. Select a different limit group from the dropdown to modify parameters for that group.

Disabled

Check this option to ignore all power system element limits in the Limit Group. Leave the box unchecked to monitor limits according to the settings of the Limit Group.

Add New Limit Group

Clicking this button will create a new limit group, displaying a dialog in which the name for the new limit group can be specified.

Rename Limit Group

Clicking this button will display a dialog in which a new name for the current limit group can be specified.

The following tabs containing the described options are available on the dialog.

Lines/Interfaces

% of Limit for Reporting (Branches)

The percentage to which Simulator’s study tools will limit a line or transformer. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), lines will be flagged as violated if they exceed this percentage. In performing an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview), all attempts will be made to keep the line below this percentage.

Line/Transformer Rating Set

You may define 15 different ratings to transmission lines or transformers (for more information see the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) or [Branch Options dialog](06-object-properties-edit-mode-part2.md#transmission-linetransformer-options)). Change this value to specify which rating set should be used for lines/transformers in the limit group.

Line/Transformer Contingency Rating Set

This field specifies the rating set used for post-contingency monitoring of Lines/Transformers.

Treat Transmission Line Limits as Equivalent Amps

Limits for transmission lines and transformers are always entered in MVA. However, when reporting limit violations, it is common to check transmission line limits in terms of their amp loading. If the Treat Line Limits As Equivalent Amps is checked, the limits for transmission lines are reported in amps rather than MVA. If this box is not checked, limits for both transmission lines and transformers are expressed in MVA.

For reference, note that the amp rating of a line is derived from the MVA rating using the formula 

 ![AmpRating](images/AmpRating.gif)

When doing contingency analysis and the Power Flow Solution Options are set to [Use the DC Approximation in Power Flow](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options), this option will be ignored. Line limits will always be reported in MVA when using the DC approximation.

Limiting End of Line

Specified as higher or lower, this field determines whether the higher or the lower flow amount on the element is used for reporting a limit violation. If you use higher, it is possible that the lower flow is not violating the line limit. If you use lower, then you are guaranteed that the element limit is being violated at both ends of the element.

% of Limit for Reporting (Interfaces)

The percentage to which Simulator’s study tools will limit an interface. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), interfaces will be flagged as violated if they exceed this percentage. In performing an [Optimal Power Flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview), all attempts will be made to keep the interface below this percentage.

Interface Rating Set

You may define 15 different ratings to an interface. Change this value to specify which rating set should be used for interfaces in the limit group.

Interface Contingency Rating Set

This field specifies the rating set used for post-contingency monitoring of Interfaces during Contingency Analysis.

% of Limit for Reporting (Nomograms)

The percentage to which Simulator’s study tools will limit a nomogram.

Use Limit Cost

If this field is checked, you are enabling the capability to have a cost function associated with enforcing constraints. This cost function can be viewed as similar to a generator cost function, in that as the constraint becomes overloaded by larger amounts, the marginal cost of enforcing the constraint will increase.

Once the box is checked, the table for defining the limit cost function will become enabled. The starting point (% Flow) must be at or above 100%. You can then begin inserting additional points in the piecewise linear curve by right-clicking in the table and selecting Insert Point from the popup menu, followed by entering the new percent flow and marginal cost. Note that the cost function must be strictly increasing, meaning the next marginal cost value must be equal to or greater than the immediately previous value.

When constraints are given the ability to use this limit cost curve, it effectively gives the optimal power flow the ability to "dispatch" the limit of the elements according to the marginal costs of the limit cost curve. You are determining the point on the limit cost curve where the shadow price of enforcing the constraint is met. Thus the OPF routine will determine how much you will allow the element to be overloaded by giving the element the piecewise linear curve. The OPF will solve the problem, and optimize the constraints as it determines shadow prices for each constraint and adjusts the limit accordingly during the iterations of the routine. Since these are somewhat flexible limit assignments to the elements, they are sometimes considered "soft" constraints.

Buses/Summary

Low Per Unit Limit

Buses will be flagged as violated if they fall below this per unit voltage.

High Per Unit Limit

Buses will be flagged as violated if they fall below this per unit voltage.

Low-voltage solution flag

Enter a per unit value at which you wish to measure a voltage and consider the solution to be a low voltage solution.

Include Out-Of-Service Buses

Check this check-box to include out-of-service buses.

Bus Low Rating Set and Bus High Rating Set

Individual buses may either take their limit values from the Low/High Per Unit Limits specified, or they may use their own bus-specific limits. Buses that have their own bus-specific limits defined will use the rating sets specified with these settings. In order for the bus-specific limits to be used for a particular bus, the **Use Bus-Specific** field for the bus must be set to YES.

Elements using Limit Group

Lists the number of elements that are members of the selected limit group.

% of Limit for Reporting (Bus Pair) Added in Version 20

The percentage to which Simulator’s study tools will limit a bus pair. Typically this is 100%, but it can be modified. In [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview), bus pairs will be flagged as violated if they exceed this percentage.

Bus Pair Rating Set Added in Version 20

You may define 4 different ratings to an bus pair. Change this value to specify which rating set should be used for bus pair in the limit group.

Bus Pair Contingency Rating Set Added in Version 20

This field specifies the rating set used for post-contingency monitoring of bus pairs during Contingency Analysis.

Contingency Options

Contingency analysis options allow the monitoring of elements based on how they are impacted by a contingency relative to base case flows or voltages. Options are available to **Never report violations if the** change due to the contingency is not great enough or **Always report as a violation if the** change is considered significant enough. These options are also available with Limit Group specific settings along with options to **Report as a violation if a bus becomes disconnected** during a contingency and select **How to Monitor Voltage Changes**(either per unit or percentage changes). To use these options as specified with the Limit Group, check the **Use group specific contingency options** checkbox. When running contingency analysis, these settings will override the ones that are specified with the contingency options on the [Advanced Limit Monitoring](22-contingency-analysis-options.md#advanced-limit-monitoring) tab.

Contingency Screening Added in Version 20

The contingency screening options are only used during contingency analysis during the screening process. Specifics of how these options are used with the screening can be found with the [screening process topic](22-contingency-analysis-options.md#dc-and-screening-options).

Tolerances in % of Limit

Tolerances can be specified for Branch, Interface, and Bus Pair device types. These tolerances are applied to the limits of each type of device to determine if a device is exceeding that percentage of the limit during the contingency screening process. If the device is exceeding the percentage of the limit during a particular contingency, it is included in the screening rank for that contingency.

Tolerances in Per Unit Voltage

These tolerances are applied to the specified limits during the contingency screening process. Bus voltages exceeding limits can occur if the voltage is higher than the high limit, lower than the low limit, or has changed by more than a specified amount. These tolerances will adjust the low voltage limit by increasing the low voltage limit by the low voltage tolerance, adjust the high voltage limit by decreasing the high voltage limit by the high voltage tolerance, and adjust the change limit by reducing it by the change voltage tolerance. The change limits are determined by the contingency analysis [Advanced Limit Monitoring](22-contingency-analysis-options.md#advanced-limit-monitoring) settings and the **Contingency Options** specified on the Limit Group dialog described above.

Voltage Multiplier

The **Low Bus Voltage** multiplier is applied to the ranking found for any buses that are exceeding their low voltage screening limit. This allows the ranking for low bus voltages to be weighted higher than the ranking for high bus voltages.

---

<a id="scaling"></a>

## Scaling

*Source: [`Content/MainDocumentation_HTML/Scaling_Topic.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scaling_Topic.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Use the **Power System Scaling Dialog** to scale the load, generation, or bus shunts uniformly for either the entire case or a group of selected buses. This display allows you to scale any of the following values:

  - Bus real power load
  - Bus reactive power load
  - Generator real power output
  - Real component of the bus shunt admittance
  - Capacitive component of the bus shunt admittance
  - Reactive component of the bus shunt admittance

To display the Power System Scaling Dialog, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Scale Case** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group. When the dialog appears, you may begin to select the buses to be scaled. Buses can be selected individually or in a group by areas or zones. In addition, if you already have specific groups of devices defined as an injection group, you can choose to scale values associated with the injection group.

Specification of Scale Amount to Scale By

The Scale tool allow specifying the new value or scale factor through a **Number**, **Field Factor** or **Field Value** with the object type to scale. When using the **Field Factor** or **Field Value** rather than the **Number**, the scaling will be done by individual object rather than the aggregation of all objects selected for scaling.

Scale by Bus

The button on the left labeled **Bus** enables selection of loads, generators and shunts by the bus to which the devices are attached. Selection of the buses can be done individually, by their area grouping, by their zone grouping, or by their super area grouping. Scaling is done on the buses chosen regardless of the area, zone, or super area specification. Options for areas, zones, and super areas are included only to aid in selecting and unselecting buses to be scaled. This is important to keep in mind if loads or generators are assigned to a different area or zone than their terminal bus.

The **Buses Table** lists the name and number of all buses in the system and whether or not each bus will participate in the scaling. Similarly, the **Areas, Zones,** and **Super Area** tables **** list the names and numbers of all areas, zones or super areas in the system and whether or not each area will participate in the scaling. Simulator initially assumes that no buses are to be scaled. The Power System Scaling Dialog furnishes a number of ways to select the subset of buses to be scaled:

  - Use the **Add to Scaling** fields to enter either a [range of areas, zones and/or buses](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) to scale.
  - Use the **Remove from Scaling** fields to enter either a [range of areas, zones and/or buses](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) to omit from the scaling.
  - Use the **Select buses using a network cut** button to define a [Network Cut](#set-selected-field-for-network-cut) to choose a custom set of buses within a portion of the system to be scaled or omitted from the scaling.
  - Use the **Buses,Areas, Zones and Super Areas** tables to change the scaling status of individual buses. Simply double-click on the **Scale** ** field for a bus, area, zone or super area to toggle its value.
  - Click the **Set All to Yes** button to scale the entire case. Click the **Set All to No** button to remove the entire case from scaling.

Changing the scaling for an area, zone or super area changes the scaling status for all *buses* in the grouping. For example, to scale all the buses in a single area, first click **Set All to No**. Then, click on the **Scale** field for the desired area in the Area Table. To scale all buses in an area except for a select few, repeat the above process, but then click on the **Scale** field for the buses not to scale.

As you select the buses to be scaled, the fields in the **Totals for Selected Buses** are updated to indicate the total load, generation, or shunt compensation that will be scaled.

Once you have selected the buses, you can either use the **Scale By** fields to enter a new scaling factor for each of the quantities or use the **New Value** fields to specify a new value directly. If you do not wish to scale a particular type of device, such as bus shunts, simply leave the **Scale By** field as unity.

To ensure that the reactive power is scaled proportionately to maintain the current load power factor, click the **Constant P/Q Ratio** option. To enforce generator limits when scaling generation, check the **Enforce Gen MW Limits** option. To scale generation and load to enforce ACE, check **Scale Gen to Keep ACE Constant**. When Simulator scales generation, all generator power outputs at the selected buses are scaled by the specified factor, regardless of area control. To scale only generators whose AGC field is set to *YES*, check **Scale Only AGCable Generation** **and Load**. To scale both in-service and out-of-service loads, check **Scale Out-Of-Service Loads**.

Finally, click **Do Scaling** to scale the load, generation, or shunt compensation.

Scale by Area

The button on the left side of the dialog labeled **Area** enables the selection of loads, generators and shunts based on the area designation of the device itself. Loads, generators and shunts can have a different area designation than the terminal bus to which the device is attached. In these cases, it is sometimes necessary to use the **Scale by Area** option to choose only the devices that are designated within a certain area, instead of all devices at a particular bus.

To specify the devices within certain areas to be scaled, toggle the **Scale** property of the areas desired in the Areas table, or use the **Add to Scaling** and **Remove from Scaling** fields to enter [ranges](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) of area numbers to be included or excluded from the scaling.

Scale by Zone

The button on the left side of the dialog labeled **Zone** enables the selection of loads, generators and shunts based on the zone designation of the device itself. This is identical to the concept described immediately above in the discussion on **Scale by Area**. As was the case with the area designation, loads, generators and shunts can have a different zone designation than the terminal bus to which the devices are attached.

To specify the devices within certain zones to be scaled, toggle the **Scale** property of the zones desired in the Areas table, or use the **Add to Scaling** and **Remove from Scaling** fields to enter [ranges](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) of zone numbers to be included or excluded from the scaling.

Scale by Injection Group

If injection groups have been defined for the case, you can scale the generation, load, and switched shunt values for the injection group by first clicking on the **Injection Groups** button. The **Buses Table** will be replaced with a new table listing the Injection Groups in the case. To choose the injection groups to scale, double-click the **Scale** field to toggle the value between *No* and *Yes*. As **Scale** fields are toggled to *Yes*, the **Net Injection** fields will update to display the totals for the selected injection groups. When all of the desired injection groups have been selected, either the **Scale By** or the **New Value** fields can be modified for a desired new value for the selected injection groups. Keep in mind that the scaling is done based on net injection and will be done in proportion to the defined [participation points](07-object-properties-run-mode-and-general-part2.md#participation-points-overview).

To ensure that the reactive power is scaled proportionately to maintain the current load power factor, click the **Constant P/Q Ratio** option. To enforce generator limits when scaling generation, check the **Enforce Gen MW Limits** option. When Simulator scales generation, all generator power outputs at the selected buses are scaled by the specified factor, regardless of area control.

Check the **Scale Only AGCable Generation and Load**option to scale only those generators and loads whose AGC field is set to *YES*. If the **Ignore AGC flag to calculate participation but use AGC flag to scale individual loads or generators**option is checked, the **Scale Only AGCAble Generation and Load** is not enabled and will be ignored. If this option is checked, then all generators and loads, regardless of their AGC status, will be used to calculate the participation percentages for all participating elements. Only those generators and loads whose AGC field is set to *YES* will actually be scaled. Normally, if choosing to scale only AGCable generation and load, only those elements whose AGC status is *YES* will be used to calculate the participation percentages.

The choice of **Scale Starting Point** impacts the reference point from which the scaling starts. **Scale from Present Value** scales by adding an incremental change to the present MW values based on the difference between the **New Value** and **Original Value**. **Scale from Zero** sets all participating elements to zero injection (0 MW load or generation) and then scales to the **New Value** from that starting point. When using the **Scale from Zero** option, only a single injection group can be scaled at a time. The following example explains the difference between these two options:

Suppose that Load 1 is 800 MW and Load 2 is 700 MW. These two loads are the only elements in an injection group and they both have a participation factor of 0.5. The desired **New Value** is 1600 MW. Choosing **Scale from Present Value** will result in Load1 being 850 MW and Load 2 being 750 MW. The incremental change in the total load is 100 MW and both loads pick up half of this change. Choosing **Scale from Zero** will result in Load 1 being 800 MW and Load 2 being 800 MW. Both loads have been scaled to 0 MW initially and they each pick up half of the desired 1600 MW total load.

The **Scale Load Field** options provide a way of scaling load that is out-of-service. Selecting **Actual MW (MW Column)** will scale only those loads that are in-service. (The MW column in the [load case information display](05-case-information-displays-by-object-part2.md#load-display) reflects the total in-service load at a bus.) Selecting **Modeled MW (ignore load and bus status)** will scale all load regardless of the load and bus status.

Injection Group Scaling Options Modified in version 19, build on Aug. 10, 2016

Several different injection group scaling methods are available for injection groups:

Proportional

The MW output for generators and loads in the injection group will be adjusted in proportion to their specified participation factors. These factors will be normalized for all generators and loads participating in the dispatch. Mvar load will be adjusted according to the **Constant P/Q Ratio** or specified Mvar injection options.

Merit Order

This will scale generators and loads in the order of highest to lowest normalized participation factor. This means that each generator and load participating in the injection group will be moved to either its maximum or minimum limit, depending on the direction of the scaling, before the output of the next element in the list is changed, until the total scale amount is achieved. If this option is checked, generator MW limits will be enforced regardless of the status of the **Enforce Gen MW Limits** option. Load limits will always be enforced, but loads that have both their minimum and maximum MW limits set to zero will not be allowed to increase. They can only decrease to 0 MW.

Economic Merit Order

This method involves dispatching generators so that they are dispatched within an economic range. Details about how economic merit order dispatch is performed can be found under the [Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the MW portion of loads will be adjusted in proportion to their participation factors and economic merit order dispatch will not be used. Mvar load will be adjusted if maintaining a **Constant P/Q Ratio**. Otherwise, no Mvar adjustments will be made.

Merit Order Close Added in version 19, build on Aug. 4, 2016

This method will dispatch generators in a merit order determined by their specified participation factors. Economic generator limits will be enforced during this process regardless of how the **Enforce Gen MW limits** option is set. Details about this method can be found under the [Generator Merit Order Close Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the loads will be adjusted in proportion to their participation factors and merit order close dispatch will not be used. Mvar load will be adjusted if maintaining a **Constant P/Q Ratio**. Otherwise, no Mvar adjustments will be made.

Click **Do Scaling** to scale the selected injection groups.

Injection groups have their own set of options that can override the options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

Scale by Owners

You can scale the generation and load values by ownership by first clicking on the **Owners** button. The **Buses Table** will be replaced with a new table listing the Owners in the case. To choose the owners to scale, double-click the **Scale** field to toggle the value between *No* and *Yes*. As **Scale** fields are toggled to *Yes*, the Generator and Load MW and Mvar fields will update to display the totals for the selected owner. When all of the desired owners have been selected, either the **Scale By** or the **New Value** fields can be modified for a desired new value for the selected owners.

To ensure that the reactive power is scaled proportionately to maintain the current load power factor, click the **Constant P/Q Ratio** option. To enforce generator limits when scaling generation, check the **Enforce Gen MW Limits** option. To scale generation and load to enforce ACE, check **Scale Gen to Keep ACE Constant**. When Simulator scales generation, all generator power outputs at the selected buses are scaled by the specified factor, regardless of area control. To scale only generators whose AGC field is set to *YES*, check **Scale Only AGCable Generation**. To scale both in-service and out-of-service loads, check **Scale Out-Of-Service Loads**.

Finally, click **Do Scaling** to scale the load and generation for the selected owners.

Note: When scaling generators with multiple owners, the scaling will be done on the entire output of these generators, regardless of the fact that not all of the owners have been set to scale. If this is not a desired behavior, you can define multiple generators at the bus, each with 100% ownership.

Note: When scaling loads using the Scale Only AGCAble Generation and Load option, only the AGCable loads will scale, but the non-agcable loads will figure into the total. The user sets the scaling factor/total load that is desired and internally Simulator determines the new scaling factor for the AGCAble load only so that the AGCAble load is adjusted. When the AGCable load is then added to the non-agcable load, the result will be the desired scaling factor/total load.

---

<a id="find-radial-bus-paths"></a>

## Find Radial Bus Paths

*Source: [`Content/MainDocumentation_HTML/Find_Radial_Bus_Paths.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find_Radial_Bus_Paths.htm)*

Added in the October 4, 2024 patch of Version 23

To access the Radial End Dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \>Find Radial Bus Paths**from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group. This dialog is shown here.

![Connections FindRadialBusPaths Dialog](images/Connections_FindRadialBusPaths_Dialog.png)

Click the **Clear Radial Paths** button to delete any Radial Bus Paths already calculated.

Click the **Calculate Radial Paths** button to perform a calculation that finds are sets of a Radial Bus Paths for the system based on the 3 options

Options for Calculation

Path Traverses Open Branches

Check this box to traverse open branches while searching for radial paths.

Treat Parallel Branch as Not Radial

Check this box to treat branches in parallel as a termination of a radial path. Uncheck the box to treat parallel branches as part of a radial path

Traverse Path by Bus or SuperBus

Choose to traverse by either Bus or SuperBus grouping. When traversing by SuperBus, then any branch that has terminal buses in the same Superbus will always show blank results for itself because the branch is not part of the path. Any Bus that

Bus and Branch Fields showing results of calculation

Once Calculate Radial Paths is chosen there will be entries in three fields for both a Bus and a Branch Object. These 3 fields are as follows

Neighbors\\Radial Path\\End Number (RadialEndBusNum)

If the bus is in a series path of buses (or Superbuses) connected to a radial bus, this will show the bus number of the final bus in the series.

Neighbors\\Radial Path\\Index (RadialEndIndex)

If the bus is in a series path of buses (or Superbuses) connected to a radial bus, this will show the index of it in this series of buses. The final radial bus will show a 1 as will branches connected to that final bus. The index will be one higher for each bus further away from the final bus.

Neighbors\\Radial Path\\Length (RadialEndLength)

If this bus is in a series path of buses (or Superbuses) connected to a radial bus, this will show the number of buses in the series path.

Example System

Consider the example below. Bus 51 and 31 are the primary bus inside their respective SuperBus groupings.

![Connections FindRadialBusPaths](images/Connections_FindRadialBusPaths.png)

For this example we assume that all the branches in the image are closed as we assume the option for not traversing branches that are open is easy to understand.

The tables below however show what the RadialEndBusNum, RadialEndIndex, and RadialEndLength fields will show for the Bus objects in the first table, and the Branch objects in the second table. The columns show what these will under different options for the Traverse by Bus or SuperBus and how handle parallel branches.

<table>
<tbody>
<tr class="odd">
<td><p>Bus</p></td>
<td><p>Parallel is Radial</p>
<p>Traverse by SuperBus</p></td>
<td><p>Parallel is NOT Radial</p>
<p>Traverse by SuperBus</p></td>
<td><p>Parallel is Radial</p>
<p>Traverse by Bus</p></td>
<td><p>Parallel is NOT Radial</p>
<p>Traverse by Bus</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>End = 11; Index = 1; Length = 5</p></td>
<td><p>End = 11; Index = 1; Length = 2</p></td>
<td><p>End = 11; Index = 1; Length = 4</p></td>
<td><p>End = 11; Index = 1; Length = 3</p></td>
</tr>
<tr class="odd">
<td><p>21</p></td>
<td><p>End = 11; Index = 2; Length = 5</p></td>
<td><p>End = 11; Index = 2; Length = 2</p></td>
<td><p>End = 11; Index = 2; Length = 4</p></td>
<td><p>End = 11; Index = 2; Length = 3</p></td>
</tr>
<tr class="even">
<td><p>31</p></td>
<td><p>End = 11; Index = 3; Length = 5</p></td>
<td><p> </p></td>
<td><p>End = 11; Index = 3; Length = 4</p></td>
<td><p>End = 11; Index = 3; Length = 3</p></td>
</tr>
<tr class="odd">
<td><p>32</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>End = 11; Index = 4; Length = 4</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>41</p></td>
<td><p>End = 11; Index = 4; Length = 5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>51</p></td>
<td><p>End = 11; Index = 5; Length = 5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>52</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>53</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>54</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

<table>
<tbody>
<tr class="odd">
<td><p>Branch</p></td>
<td><p>Parallel is Radial</p>
<p>Traverse by SuperBus</p></td>
<td><p>Parallel is NOT Radial</p>
<p>Traverse by SuperBus</p></td>
<td><p>Parallel is Radial</p>
<p>Traverse by Bus</p></td>
<td><p>Parallel is NOT Radial</p>
<p>Traverse by Bus</p></td>
</tr>
<tr class="even">
<td><p>11-21 ckt 1</p></td>
<td><p>End = 11; Index = 1; Length = 5</p></td>
<td><p>End = 11; Index = 1; Length = 2</p></td>
<td><p>End = 11; Index = 1; Length = 4</p></td>
<td><p>End = 11; Index = 1; Length = 3</p></td>
</tr>
<tr class="odd">
<td><p>21-31 ckt 1</p></td>
<td><p>End = 11; Index = 2; Length = 5</p></td>
<td><p>End = 11; Index = 2; Length = 2</p></td>
<td><p>End = 11; Index = 2; Length = 4</p></td>
<td><p>End = 11; Index = 2; Length = 3</p></td>
</tr>
<tr class="even">
<td><p>31-32 ckt 1</p></td>
<td> </td>
<td> </td>
<td><p>End = 11; Index = 3; Length = 4</p></td>
<td><p>End = 11; Index = 3; Length = 3</p></td>
</tr>
<tr class="odd">
<td><p>32-41 ckt 1</p></td>
<td><p>End = 11; Index = 3; Length = 5</p></td>
<td><p> </p></td>
<td><p>End = 11; Index = 4; Length = 4</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>32-41 ckt 2</p></td>
<td><p>End = 11; Index = 3; Length = 5</p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>41-52 ckt 1</p></td>
<td><p>End = 11; Index = 4; Length = 5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>41-54 ckt 1</p></td>
<td><p>End = 11; Index = 4; Length = 5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>51-52 ckt 1</p></td>
<td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>51-53 ckt 1</p></td>
<td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>53-54 ckt 1</p></td>
<td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td><p>52-54 ckt 1</p></td>
<td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>51-61 ckt 1</p></td>
<td><p>End = 11; Index = 5; Length = 5</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>

The following image shows the radial path Buses and Branches when **Traverse by SuperBus** is chosen and **Treat Parallel Branch as NOT radial** is unchecked.

![Connections FindRadialBusPaths Example](images/Connections_FindRadialBusPaths_Example.png)

---

<a id="find-circulating-mw-or-mvar-flows"></a>

## Find Circulating MW or MVAr Flows

*Source: [`Content/MainDocumentation_HTML/Find Circulating MW or MVAr Flows.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find Circulating MW or MVAr Flows.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);) 

To access the Circulating Mvar and MW Flow Cycle Dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose**Connections \> Find Circulating MW or Mvar Flows...** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group.

Circulating power flows are possible in power systems and can lead to unnecessary power losses and voltage drops in the transmission system. The most common example is circulating Mvars caused by transformers with unbalanced tap ratios. This dialog provides a tool to detect and highlight the circulating real and reactive flows in a power system and also provides a metric to rank the severity of these circulating flows.

A *Flow Cycle* is defined as a series of transmission branches with positive flows that can be traversed to form a loop. Normally these types of cycles are not possible in a power system, but certain configurations of transformer tap ratios or phase shifts can results in circulating Mvar or MW flows. The detailed theory behind this tool is completely described in the follow paper: C. Davis, James Weber, and Kyle Johnson, “Circulating MW and Mvar flows in large systems,” in North American Power Symposium, Oct. 2009. You may also email PowerWorld for more details.

Dialog Options

Find Cycles

Click this button to recalculate the list of Flow Cycles after making changes in the other options.

Cycle Type to Find

Choose whether to locate circulating Mvars (much more common) or circulating MWs. Changing this option will automatically recalculate the list of Flow Cycle

Flow Threshold

When searching for flow cycles, enter a threshold below which flows will be ignored. This is needed to remove trivial flow cycles which are below the solution tolerance and are just generally of little interest.

Maximum Related Cycles

It is possible (and quite common) for many *related* cycles to be found in one power system. A group of *related* cycles is defined as a group of cycles which can all be mutually reached by from one another by traversing a series of positive branch flows. (Mathematicians would call this grouping a *Strongly Connection Component* of a *directed graph*). Groups of cycles which can be reach from one another can be combined in many ways to form many new cycles. To prevent the results in Simulator from displaying millions of cycles, this value is entered limit the number of related cycles which will be returned by entering this value. Simulator will return the cycles which have the largest minimum flow.

After finding the Flow Cycles, the lists at the bottom of the dialog show the flow cycle results. The top list shows the list of **Flow Cycles**. As you click on a particular flow cycle, the bottom list will show the **Branches in Selected Flow Cycle** (or Buses). There are also tabs which show **Branches in any Cycle** and **Buses in Any Cycle**. You can use these case information displays to mark all the branches that are in a cycle and then use a visualization tool such as [Dynamic Formatting](17-oneline-view-printing-and-contouring.md#dynamic-formatting-overview) or [Contouring](17-oneline-view-printing-and-contouring.md#contouring) to show visually show the Flow Cycles on a one-line diagram. Example pictures of this are shown at the bottom of this topic.

![CirculatingFlows](images/CirculatingFlows.gif)

Flow Cycle List Display Results

The Flow Cycle List has the following columns by default.

Related Cycle Group

Related Cycle Group Number will be the same for that which can be reached from one another. These cycles are likely related to one another.

Area Names

Comma delimited list of area names which are traversed by the cycle.

Loss Mvar Reduction, Loss MW Reduction

Estimate of the reduction in Mvar (or MW) losses in the entire cycle if the circulating flow is removed. The larger this number is, the more severe the circulating flow is. The list is sorted by the Loss Mvar Reduction by default.

Cycle X-Weighted Average

Shows the weighted average flow in the cycle weighted by the series reactance (X) values.

Cycle Min Flow

Shows the minimum flow on any branch in the cycle. The larger this number is, the more severe the circulating flow is.

Lines in Cycle

Number of lines (branches) in the cycle.

Min Bus Num, Max Bus Num

Shows the Minimum and Maximum bus number traversed in the cycle

Min Tap Ratio, Max Tap Ratio

Show the minimum and maximum tap ratio on any branch in the cycle.

Max Percentage MVA Flow

Shows the maximum percent MVA flow on any branch in the cycle.

Branches in Selected Flow Cycle

The Branches in Selected Flow Cycle list has the following columns by default.

Cycle Flow

Magnitude of branch's flow for the cycle (the minimum of the from and to flow).

Cycle Flow Direction

Direction of flow in cycle relative to line's direction

Loss Mvar Reduction, Loss MW Reduction

Estimate of the reduction in MW and Mvar losses on this branch if the circulating flow is removed

Tap Ratio

Tap Ratio of the branch

Phase (Deg)

Phase Shift of the branch

Example Visualizations show circulating Mvar Flows

![CirculatingFlowsSmallExample](images/CirculatingFlowsSmallExample.gif)

![CirculatingFlowsLargeExample](images/CirculatingFlowsLargeExample.gif)

---

<a id="overview-of-facility-analysis"></a>

## Overview of Facility Analysis

*Source: [`Content/MainDocumentation_HTML/Facility_Analysis_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Facility_Analysis_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Facility Analysis is used to study the topological redundancy of interconnect-specific electric facilities. This application determines the minimum set of AC transmission lines and transformers that, when opened or removed from the system, would electrically isolate a set of Facility buses from a set of External buses.

The tool is an application of the [augmenting path max flow min cut algorithm](#augmenting-path-max-flow-min-cut-algorithm) with modifications to handle electric networks.

The Facility analysis process has two steps:

1.  The [Select the Buses](19-edit-mode-tools.md#bus-selection-page) dialog is used to specify the External and Facility buses. Multiple selections of the External buses can be done using any of the area or zone selectors. The Facility buses are specified by setting the **Selected** field of buses to *YES*.
2.  The [Facility Analysis dialog](#facility-analysis-dialog) is used to determine the Min Cut and visualize the branches that belong to the min cut.

The Facility analysis application runs in Edit Mode and takes into consideration the open or closed status of the branches. Open lines are considered as not present in the system. The figure below illustrates the functionality of the Facility Analysis tool.

![image\\ebx\_1428961269.gif](images/ebx_1428961269_432x326.gif)

---

<a id="facility-analysis-dialog"></a>

## Facility Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/Facility_Analysis_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Facility_Analysis_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog is used to determine the branches that would isolate the Facility from the External region as specified in the [Select the Buses](19-edit-mode-tools.md#bus-selection-page)dialog. When switching to the Facility Analysis page, the application builds a graph data structure and reports information regarding the External Region and the Facility.

To access the Facility Analysis Dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \> Facility Analysis Dialog** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group.

Select the Buses

The options and use of this page are described in their entirety in the topic titled [Bus Selection Page](19-edit-mode-tools.md#bus-selection-page).

Facility Analysis

External Region

The external region is a set of buses from which the Facility would be isolated. Although the buses in the external region may not be adjacent to each other, the algorithm will assume that any of these buses can supply electricity to the Facility and thus the buses in the External region are considered to be connected. The External region is defined using the [Select the Buses](19-edit-mode-tools.md#bus-selection-page)dialog.

External Region - Number of Buses

Indicates the number of buses in the External region. This number is equal to the number of buses in the system that were labeled as External in the [Select the Buses](19-edit-mode-tools.md#bus-selection-page) dialog. There should be at least one bus in the external region.

External Region - Capacity

Indicates the number of branches that connect the external buses to study buses in the system. This is the outgoing [graph flow](#graph-flow) capacity from the External region toward the Facility.

Facility

Is the set of buses that constitute the Facility. Although the buses in the Facility may not be adjacent to each other, the algorithm will assume that any of these buses may receive power from the External region, and thus the Facility buses are considered to be connected to each other.

Facility - Number of Buses

Indicates the number of buses in the Facility. This number is equal to the number of buses in the system that were labeled as *Study* and whose **Selected** field is set to *YES*. There should be at least one bus in the Facility.

Note that if a bus was specified to be *External* and its **Selected** field is *YES*, then the application will issue an error, since Facility buses cannot be in the External region. In such cases the status will indicate that the graph structure is incomplete.

Facility - Capacity

Indicates the number of branches that connect Facility buses with study buses. This number is equal to the outgoing [graph flow](#graph-flow) capacity from the Facility toward the External region.

Status

Shows the status of the Facility Analysis application. If the External region and the Facility are specified, the status will indicate that the graph structure is ready. During execution of the Min Cut algorithm, the status shows the number of the augmenting paths found so far and the number of branches in the current path.

Find Minimum Cut

Press this button to initiate the [Min Cut algorithm](#augmenting-path-max-flow-min-cut-algorithm). The button is inactive if the graph structure is incomplete, i.e., there is either no external bus or facility bus, or facility buses were found inside the External region.

Show Paths

Toggle this button to visualize the augmenting paths at the bottom of the form. The augmenting paths are listed in the order in which they were found. Note that the first path has fewer nodes, since the algorithm uses a shortest (least number of nodes) path routine. For each augmenting path the number of buses in the path, as well as the corresponding bus numbers are listed in the dialog. This button is enabled only if a min cut has been found.

---

<a id="augmenting-path-max-flow-min-cut-algorithm"></a>

## Augmenting Path Max Flow Min Cut Algorithm

*Source: [`Content/MainDocumentation_HTML/Augmenting_Path_Max_Flow_Min_Cut_Algorithm.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Augmenting_Path_Max_Flow_Min_Cut_Algorithm.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The augmenting path max flow – min cut algorithm is used to identify the minimum number of branches that need to be opened or removed from the system in order to isolate the Facility (power system device) from an External region.

The algorithm is an application of the Max Flow - Min Cut theorem, which states that the maximum flow that can be transferred from a set of source nodes to a set of sink nodes across a graph equals the capacity of the minimum cut. The facility analysis in Simulator finds a min cut, although this cut may not be unique.

The application consists of three stages:

1.  **Convert the electric network to a graph structure**  
    In this stage, each branch of the system is converted to an undirected arc with [graph flow](#graph-flow) capacity equal to one. Thus, only one unit of [graph flow](#graph-flow) can be sent through a branch. The Facility buses and the External buses are converted to Facility and External supernodes, respectively. This effectively reduces the problem to finding the min cut between these two supernodes.  

    The number of nodes and capacities of the Facility and the External region are also computed during this stage.

2.  **Find the Max Flow using the Augmenting Path Algorithm**  
    This is an iterative process. At each step, the algorithm finds a new augmenting path from the Facility to the External region and augments the [graph flow](#graph-flow) along this path in one unit. Consequently, the branches in the path won’t be available for flow augmentation in the next step. Each new path is determined using a shortest path routine.  

    The algorithm stops when no augmenting path from the Facility to the External region can be found. The number of units transferred from the Facility to the External region (path augmentations) reaches the number of branches in a certain cut. Note that the number of branches in the min cut can not exceed the capacity of either the Facility or the External region.

3.  **Determine the branches in the min cut**  
    The identification of the branches that constitute the min cut consists in tracking down labels in the buses and branches used during each path augmentation.

---

<a id="graph-flow"></a>

## Graph Flow

*Source: [`Content/MainDocumentation_HTML/Graph_Flow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Graph_Flow.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Most network and graph theory applications use the concept of flow to represent any object that can be transported, such as communication packets or trucks, but also connectivity properties of graphs. In the [augmenting path max flow min cut algorithm](#augmenting-path-max-flow-min-cut-algorithm) the flow is an artificial concept used to represent topological connectivity of buses. Two buses are adjacent if flow can be sent from one to the other through a branch.

Graph Flow Capacity of a Branch

Networks that transport some flow are said to be capacitated if its arcs (here synonym of "branches") have some limit associated to the flow transportation. For instance, capacity of a communication channel, or number of trucks that can be simultaneously on a certain road. The algorithm used in the Facility Analysis assigns a capacity of one to each branch. This means that the branch can be used only once for "connecting" two nodes.

Graph Flow Capacity of a Cut

The capacity of a topological cut is equal to the sum of the capacities of its arcs. In the Facility Analysis, the capacity of the min cut is equal to the number of branches in the min cut, since each branch has a capacity of one.

---

<a id="branches-that-create-islands"></a>

## Branches that Create Islands

*Source: [`Content/MainDocumentation_HTML/Find_Branches_that_Create_Islands.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Find_Branches_that_Create_Islands.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Find Branches that Create Islands, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \> Find Branches that Create Islands** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group.

There are several options for selecting which ac lines to process.

Line Processing Options

**All ac Lines**

All ac lines in the power system model will be processed.

**Use Area/Zone/Owner Filter**

All ac lines that meet the defined Area/Zone/Owner Filters will be processed.

Select Area/Zone… to display the Area/Zone/Owner Filters dialog.

**Use Selected**

All ac lines that have the Selected? field set to ‘YES’ will be processed.

Click Select Lines… to display all ac lines and change the Selected? field.

**Meets Filter**

All ac lines that meet a selected advanced filter will be processed.

Use the drop down box to select a defined [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) or click Define Filter to display the Advanced Filters for Branch Dialog. This dialog will allow you to define a new advanced filter for a branch or update an existing filter.

By checking **Do not display radial lines creating a single bus island** **** those lines that only island a single bus will not be displayed with the results.

Click **Determine Branches** to start the processing once all options have been set.

Because the processing of ac lines in a large power system may take some time, there is an **Abort** button that is enabled once the line processing has started that will stop the processing at any point.

The list of resulting ac lines that create islands will be displayed under **Branches that** **Create** **** **Islands.** To show the list of buses that are islanded by an outage of any line in the list, select a line and the **Islanded Buses** list will be populated. **** Both the Branches that Create Islands list and the Islanded Buses list are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) and have the same [local menu options](04-model-explorer-and-case-information-part1.md#local-menu-options) and characteristics of other case information displays.

---

<a id="set-selected-field-for-network-cut"></a>

## Set Selected Field for Network Cut

*Source: [`Content/MainDocumentation_HTML/Network_Cut.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Network_Cut.htm)*

The Network Cut tool is another method for choosing sets of buses for such features as [Scaling](#scaling) or [Equivalencing](19-edit-mode-tools.md#equivalents).

The use of the network cut method is to define a set of branches as the "cut" plane, then choose a bus on one side or the other of the cut to indicate which side of the cut you are interested in. The network cut dialog provides the functionality necessary for defining the network cut.

Defining Network Cut

The first step in defining the network cut is to choose the branches which define the cut plane in the system. The one caution is to be sure you select a closed loop cut plane. In other words, you must select a set of branches which completely topologically separates two portions of the system. If you only choose a partial cut plane, which does not completely cut the system in two distinct pieces, then attempted use of the ill-defined cut plane will fail.

To choose the branches which define the cut plane, simply highlight the branches by clicking on them in the list. For each branch you highlight, you must click on arrow button (pointing to the box on the right) to add the branch to your cut plane definition. You can make use of the control (Ctrl) and shift keys to select multiple branches at one time in the list of branches. Note that you can also select a cut plane similarly using interfaces or DC lines.

Once you have the branches (or interfaces or DC lines) selected which form the cut plane, you then need to choose a bus on either side of the cut plane to indicate which side you are interested in. The bottom panel on the display allows you to locate and select this bus.

Require Paths to be Energized

Check this option to only include branches with a closed status when traversing branches to determine which side of the network cut each bus is on. This option does not apply to the branches that are specified to define the network cut. Those branches will not be traversed regardless of their status.

Include How Many Tiers of Neighbors

Once the network cut has been defined by a set of branches and the bus defining which side of the cut is being examined has been chosen, this option will then include buses within so many tiers of the network cut boundary, on the opposite side of the cut as the specified bus. If the number of tiers is set to zero, then the buses examined will only be those on the same side of the cut as the bus selected.

Setting the Field

Once the network cut has been defined and the side of the cut to be examined has been chosen, the appropriate field for each bus in the area of interest can be set. If the network cut is for the equivalencing tool, then the field to set is the **Which System** property, which defines if a bus is in the external or study system when creating an equivalent. If the network cut is for the scaling tool, then the field to set is the **Scale** property, which defines if a bus is to be included in a scaling action.

Filter by KV

The buses within the network cut can be filtered by nominal voltage level before the field(s) are set. Only buses that are within the network cut and are within the nominal KV level specified will have their fields set to the desired value.

Use Area/Zone Filters

The buses within the network cut can be filtered by the area or zone in which they are contained before the field(s) are set. Only buses that are within the network cut and whose area meets the defined Area/Zone filter specified will have their fields set to the desired value.

---

<a id="set-bus-field-from-closest-bus"></a>

## Set Bus Field From Closest Bus

*Source: [`Content/MainDocumentation_HTML/Set_BusField_FromClosest.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Set_BusField_FromClosest.htm)*

Added in Version 24

To access the Set Bus Field From Closest dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Connections \> Set Bus Field To Closest** from the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group. This dialog provides a way to choose a list of Bus that you would like to **Set a Value** by finding the closest bus from you would like to **Copy From**.

After clicking the **Copy Field**button, all buses that meet the filter chosen from the **Specify a Filter for Buses to Set a Value** will calculate the bus closest to them that is within the buses that meet the filter chosen from the **Specify a Filter Buses to Copy From**. The field specified under the **Bus Field to Populate** will then by copied onto the "Set A Value" buses based on the bus closest to it.

The options on the dialog are described below.

Distance Measure

Choose the distance measure that will be used to determine distances between nodes. Each branch will be treated as having a length based on the choice below. Note: negative values are not allowed, therefore negative values will be treated as extremely small lengths instead.

**X** - Per unit series reactance.

**|Z|** - Magnitude of the series impedance (based on the per unit reactance and resistance).

**Length** - Length field for each branch.

**Number of Nodes** - Length of 1.0 is used for all branches.

**Other** - When choosing Other, click the **Find..** button to choose any numeric field of a branch.

Lines to Process

Regardless of the Distance Measure above, you can choose which branches allowed to be traversed when finding the shortest path.

**All** - All branches are allowed to be traversed.

**Only Closed** - Only branches that are presently closed can be traversed.

**Filter** - Only branches that meet the advanced filter specified can be traversed. Click **Define...** to choose or create and advanced filter.

**Selected** - Only branches whose Selected? field is set to *YES* can be traversed.

Bus Field to Populate

Choose a field that will be copied between the buses.

---

<a id="breaker-isolated-groups"></a>

## Breaker Isolated Groups

*Source: [`Content/MainDocumentation_HTML/Breaker_Isolated_Groups.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Breaker_Isolated_Groups.htm)*

Breaker Isolated Groups are groupings of buses that are bounded by any combination of explicit breakers, implicit breakers, and open branches. These groupings can be accessed on a standalone dialog or used to auto-insert contingencies. The following describes how the groupings are identified and how they can be used.

Determining Breaker Isolated Groups

Breaker isolated groups are groupings of buses that are bounded by any combination of explicit breakers, implicit breakers, and open branches. The boundary branches are defined as follows:

Explicit Breakers

These are branches that have **BranchDeviceType** = *Breaker*.

Implicit Breakers

Each bus record has an **Implicit Breakers** field that can be found in the **Topology** folder in the list of available fields. This field is used to indicate where breakers are located when explicit breakers have not been modeled. If **Implicit Breakers** = *YES* for a bus, it is assumed that any device connected to that bus will have a breaker in series with it. For a branch that is connected to an implicit breaker bus, the algorithm to identify bus groupings will behave as though that branch itself is a breaker.

Open Branches

When based on the current system state an open branch is one where **Status** = *Open*. The normal status of branches can also be used. When determining the groupings either through the dialog or when auto-inserting contingencies, there is an option to **Use Branch Normal Status for Groupings**. When this option is used, an open branch is one where **Normal Status** = *Open*.

To determine the groupings, the connections to a bus that has not already been examined are traversed. Buses are accumulated into a new group until there are no remaining connections to unexamined buses that can be traversed from the starting bus. Boundary branches are found when an explicit breaker, implicit breaker bus, or open branch is encountered. These are the boundaries that connect one bus group to another. The boundary branch when an implicit breaker bus is encountered is the branch with one terminal bus in the current group and the other terminal bus defined as having implicit breakers. DC line connections are assumed to have breakers and these are not traversed. This process is repeated until all buses in the case have been examined.

Groupings are identified by assigning a **Breaker Group Number** to each bus with the groupings formed by buses with the same number.

Breaker Isolated Groups Dialog

The Breaker Isolated Groups dialog can be found on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab in the [Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group) ribbon group under **Connections \> Breaker Isolated Groups**.

Breaker Isolated Groups are defined as described in the **Determining Breaker Isolated Groups** section. The dialog contains tabs for showing groupings based on bus, generator, load, switched shunt, and branch. Regardless of object type, the groupings are always determined by bus and an object's terminal bus or buses will determine its group.

Checking the **Use Branch Normal Status for Groupings** option will consider open branches to be those where **Normal Status** = *Open*. If this option is not used, open branches are those where **Status** = *Open*.

Click the **Find Isolated Groups** button to determine the groupings and populate the **Breaker Group Number** field.

The **Filter Display Below By Range** box takes an integer range list that can be used to filter the list of devices by **Breaker Group Number**. Click the **Update Filter** button to update the filtering after specifying the group numbers by which to filter.

Auto Inserting Contingencies by Breaker Isolated Groups

On the [Auto Insertion of Contingency Records](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) dialog the **Bus grouping** option will use breaker isolated groups of buses to create new contingencies. When auto-inserting contingencies, the same methodology as described in the **Determining Breaker Isolated Groups** section is used for determining the breaker isolated bus groupings as when displaying the groupings in the dialog, but not all groupings will result in contingencies being created.

The boundary branches and other devices (lines, transformers, series capacitors, generators, and loads) internal to bus groups are used for defining contingency actions and naming contingencies. Here are the different naming conventions and included contingency actions based on the type of boundary branches. Additionally, contingencies will not be created for some groupings.

At Least One Implicit Breaker

  - The boundary branches are the result of at least one implicit breaker
      - Contingency element actions are the boundary branches defined as OPEN actions
      - Contingency is named based on the concatenation of bus numbers and names of the buses at the boundaries of the bus group (buses on the outside of the group) used to form the contingency
      - Open branches are included as actions in the contingency, but their boundary buses will not be used in the naming of the contingency
      - If a bus group contains generators or loads at internal buses, the generators and loads will be included as OPEN actions
      - Generators and loads at implicit breaker buses are not included as actions in the contingency
  - For purposes of creating contingencies, branches that connect two buses defined with implicit breakers can form their own grouping
      - These groupings have a single line and no buses
      - Element action is defined as an OPEN on the single branch in the group
      - The contingencies are named for the single branch in the group

All Explicit Breakers

  - The boundary branches are all explicit breakers with no implicit breakers
      - Contingency element action is OPEN WITH BREAKERS for the internal group device with the highest priority
      - Internal device priority is branch (line, transformer, or series capacitor) with the largest absolute reactance, generator with the largest MW Max, and load with the largest MW output
      - Contingency is named for the internal device with the highest priority that is also selected as the device for the contingency action

At Least One Explicit Breaker and No Implicit Breakers

  - The boundary branches are a combination of explicit breakers and open branches that are not explicit breakers with no implicit breakers
      - Contingency element actions are the boundary branches defined as OPEN action
      - Contingency is named for the internal group device with the highest priority
      - Internal device priority is branch (line, transformer, or series capacitor) with the largest absolute reactance, generator with the largest MW Max, and load with the largest MW output

Contingencies Not Created

  - Groupings that have more than 20 generators. This is to prevent creating a contingency for most of the system when dealing with a case that only has implicit or explicit breakers in part of the system.
  - Separate generator or load contingencies for generators and loads that are attached to implicit breaker buses
  - Open branches are treated as boundary branches for finding the groupings. No contingency will be created if all boundary branches are open.
  - Groupings created by all explicit breakers for which there are no internal group devices
  - Groupings created by boundary branches with at least one explicit breaker and no implicit breakers for which there are no internal group devices

---

<a id="governor-power-flow"></a>

## Governor Power Flow

*Source: [`Content/MainDocumentation_HTML/Governor_Power_Flow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Governor_Power_Flow.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Governor Power Flow dialog shows all information related to solving a governor power flow. The dialog is accessed by selecting **Other** **\> Governor Power Flow** from the **[Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab. Using this dialog, you can modify settings related to solving the case while on Governor or "Island-Based Automatic Generation Control (AGC)".

The Governor Power Flow Dialog has two tabs, Options and Generator Options, which are described below.

Generator Options Tab

This tab sheet presents a case information display with all the generators of the case. The columns shown in the display are helpful when looking at solving a Governor Power Flow.

Options Tab

> This section describes the options available on the Options tab of the Governor Power Flow dialog. The dialog is accessed by selecting **Other \> Governor Power Flow** from the **[Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.
> 
> This tab sheet presents the following controls:
> 
> Disable Automatic Generation Control
> 
> Disables automatic MW generation changes during the power flow solution.
> 
> Island AGC Tolerance
> 
> The ACE mismatch tolerance allowed for the Island to be considered solved in terms of generation dispatch.
> 
> Island-Based Automatic Generation Control
> 
> Select how the generations should be controlled for the dispatch.
> 
>   - Disabled: The area and super area dispatch settings from the case will be used
>   - Use Participation Factors of individual generators: Each generator will have it’s own participation factor, and will contribute according to its participation factor divided by the sum of all participation factors of all other generators in the same island.
>   - Calculate Participation Factors from Area Make Up Power Values: Each area is assigned a "factor" as to how it should participate towards the generation dispatch in the island. This is similar to participation factors for generators. The total percentage the area contributes towards the generation change needed in the island is equal to its individual factor divided by the sum of all area make up power factors. Then within each area, the generator participation factors determine how the area’s percentage is made up of available generation within the area. The area make up power values can be set in the table of areas on the right hand side of the dialog.
>   - Dispatch using an Injection Group: The island dispatch will be made up by a combination of generators and loads, defined in an [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) that can be selected from the dropdown list.
> 
> How should reactive power load change as real power load is ramped?
> 
> If you are using an injection group with load as part of the dispatch, then you can specify how the reactive power load should respond as the real power demand of loads changes with the dispatch. The reactive power can either be kept at the starting ratio of real and reactive power of the load, or the MVAR amount can change at each load by a specified power factor.

---

<a id="generator-options-tab"></a>

## Generator Options Tab

*Source: [`Content/MainDocumentation_HTML/Governor_Power_Flow_Generator_Options_Ignore_Area_Zone_Owner_filter_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Governor_Power_Flow_Generator_Options_Ignore_Area_Zone_Owner_filter_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This tab sheet presents a case information display with all the generators of the case. The columns shown in the display are helpful when looking at solving a Governor Power Flow.

---

<a id="options-tab"></a>

## Options Tab

*Source: [`Content/MainDocumentation_HTML/Governor_Power_Flow_Options_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Governor_Power_Flow_Options_Tab.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This section describes the options available on the Options tab of the Governor Power Flow dialog. The dialog is accessed by selecting **Other** **\> Governor Power Flow** from the **[Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab. ****

This tab sheet presents the following controls:

Disable Automatic Generation Control

Disables automatic MW generation changes during the power flow solution.

Island AGC Tolerance

The ACE mismatch tolerance allowed for the Island to be considered solved in terms of generation dispatch.

Island-Based Automatic Generation Control

Select how the generations should be controlled for the dispatch.

  - Disabled: The area and super area dispatch settings from the case will be used
  - Use Participation Factors of individual generators: Each generator will have it’s own participation factor, and will contribute according to its participation factor divided by the sum of all participation factors of all other generators in the same island.
  - Calculate Participation Factors from Area Make Up Power Values: Each area is assigned a "factor" as to how it should participate towards the generation dispatch in the island. This is similar to participation factors for generators. The total percentage the area contributes towards the generation change needed in the island is equal to its individual factor divided by the sum of all area make up power factors. Then within each area, the generator participation factors determine how the area’s percentage is made up of available generation within the area. The area make up power values can be set in the table of areas on the right hand side of the dialog.
  - Dispatch using an Injection Group: The island dispatch will be made up by a combination of generators and loads, defined in an [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) that can be selected from the dropdown list.

How should reactive power load change as real power load is ramped?

If you are using an injection group with load as part of the dispatch, then you can specify how the reactive power load should respond as the real power demand of loads changes with the dispatch. The reactive power can either be kept at the starting ratio of real and reactive power of the load, or the MVAR amount can change at each load by a specified power factor.

---

<a id="set-selected-field"></a>

## Set Selected Field

*Source: [`Content/MainDocumentation_HTML/Set_Selected_Field.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Set_Selected_Field.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Set Selected Field option is an often unused featured in Simulator, but can at times prove very useful. Each object in Simulator has a property called **Selected**, which does nothing in Simulator other than allow the user to choose a specialized set of objects for some other purpose, such as [advanced filtering](04-model-explorer-and-case-information-part2.md#advanced-filtering) a display. The user can add a column to most types of [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) which shows the value of the **Selected** property for the type of object being observed. By default, this field is always set to *No*. However, the user can change the value of this field, and then sort the column, filter the display, or any other action that can normally be performed on a column of a Yes/No type.

Set Selected Field to YES from a Oneline diagram

If you right-click on a group of selected oneline objects, one of the local menu options that appears is Set Selected Field to YES. Choose this option to change the Selected field for all the underlying data objects' Selected field to YES.

![SetSelected](images/SetSelected.gif)

Set Selected Field for Network Cut

In addition to modifying the **Selected** property manually in a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays), it is also possible to define a group of buses' **Selected** property by defining a [network cut](#set-selected-field-for-network-cut) on the system. Choosing the **Set Selected Field** **for Network Cut** option from the **Tools** menu will open the [network cut](#set-selected-field-for-network-cut) dialog automatically for setting the **Selected** property of a group of objects according to a desired cut plane chosen.

---

<a id="create-new-areas-for-islands"></a>

## Create New Areas for Islands

*Source: [`Content/MainDocumentation_HTML/Create New Areas for Islands.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Create New Areas for Islands.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When an area spans multiple electric islands, area MW interchange control may not be possible.

Consider two scenarios shown below. The scenario on the left has Area \#1 that spans three islands while Area \#2 is contained within a single island. Island C contains both Area \#1 and Area \#2. Because Area \#1 only spans one island that contains more than one area, area interchange control is allowed. When balancing the area interchange in Island C, it can easily be determined what generators will respond. Only those generators in Area \#1 in Island C will respond with interchange between Area \#2. Internally when the power flow solution is solved, Simulator creates temporary areas for the portion of Area \#1 that is in Island A and the portion that is in Island B. This ensures that only those generators that are in Island C will respond to interchange with Area \#2. In this scenario, both Area \#1 and Area \#2 are allowed to be on area interchange control.

The scenario on the right has Area \#2 that spans two islands and Area \#1 that spans three islands. Because both of the areas are contained in islands that have more than one area, area interchange control is not allowed for both Area \#1 and Area \#2. Control is not allowed because Simulator does not have enough information to determine in which islands the area transactions are supposed to occur. In this scenario, Simulator will turn off AGC for areas that meet these conditions.

![New Areas For Islands 671x334](images/New_Areas_For_Islands_671x334.jpg)

With the Create New Areas for Islands option, permanent areas can be created that match the areas that Simulator creates temporarily while solving the power flow. New areas will get created if an area is on AGC, spans multiple viable islands, and only one of those islands has more than one area in it. An island is considered viable if it has closed non-zero load and an online generator or it has an online generator that is connected to the rest of the system via a DC line. For an area meeting these criteria, new areas will get created for the portion of the area in islands that contain only one area. If an area spans multiple islands and each island contains only a single area, new areas will get created for the islands that have the fewest buses. New areas will only get created if there are generators on AGC or online load in more than one of the islands in which the area has buses. New areas will use the same AGC method as their original area unless that area in on area slack bus control. In that case, the new areas will be on no AGC. New areas will be names with the original area name with the slack bus for the island appended.

---

<a id="browse-pwb-file-headers"></a>

## Browse PWB File Headers

*Source: [`Content/MainDocumentation_HTML/Browse PWB File Headers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Browse PWB File Headers.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Browse PWB File Headers is accessed by selecting **Other** **\> Browse PWB File Headers**from the **[Other Tools](02-simulator-ribbon.md#other-tools-ribbon-group)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab.

When selected, Simulator will prompt you to specify a directory containing PWB files for which you wish to preview the header (case description) text. Once the directory has been specified, Simulator will obtain the case description for each PWB file in the directory, and write them all into the Simulator message log.

---

<a id="browse-open-onelines"></a>

## Browse Open Onelines

*Source: [`Content/MainDocumentation_HTML/Browse_Open_Onelines.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Browse_Open_Onelines.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

All the objects in all the open .pwd files can be listed in the Browse Oneline Environment dialog. To do so, go to the [Onelines](02-simulator-ribbon.md#onelines-tab-overview) ribbon tab, [Active](02-simulator-ribbon.md#active-ribbon-group) ribbon group and choose **List Display \> Browse open onelines** in Edit Mode or Run Mode. The power system objects are listed on tabs according to their type. For instance, all the buses and bus fields are listed in the **Buses** tab while all the generators and generator fields are listed in the **Generators** tab. The **Others** tab lists all the objects on the onelines which are not associated with power system elements, e.g. background lines or images. The **All** tab lists all the objects in all the open onelines. The default display columns for each grid include the oneline file name of the object and the type of the object. Objects that are linked to case elements also have identifying information about the data element that they represent. The **Others** and **All** pages include the default display columns for generic display objects.

The oneline displays can be panned to the selected object. To do so, select one object from the Browse Oneline Environment dialog and right click to invoke the local popup menu. Click **ScreenObject Records \> Pan** **to Object on Open Onelines**. This will bring the oneline with the selected object to the front and pan to the selected object. When panning, the browsing dialog can be kept on top if **Keep browsing dialog on the top when choosing Pan Oneline to Object** is checked. Otherwise, the dialog will be sent to back when panning.

---

<a id="unused-bus-numbers"></a>

## Unused Bus Numbers

*Source: [`Content/MainDocumentation_HTML/Unused_Bus_Numbers.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Unused_Bus_Numbers.htm)*

When making changes to a power system case, it is often beneficial to know which bus numbers are still available. To save a list of unused bus numbers to a text file, while in [Edit Mode](01-getting-started.md#edit-mode-introduction), go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Modify Case \> List of Unused Bus Numbers** from the [Edit Mode](02-simulator-ribbon.md#edit-mode-ribbon-group) ribbon group. Enter a [range of bus numbers](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) in the dialog and click **OK**. In the Save As Dialog, specify the text file where the list of bus numbers should be written and click **Save**. Only those unused bus numbers in the specified range will be listed in the file. Clicking **Cancel** at any point will abort saving the list to a file.
