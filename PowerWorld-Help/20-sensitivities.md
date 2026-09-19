---
title: "Sensitivities"
part: "Analysis"
chapter_file: "20-sensitivities.md"
topics: 23
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Sensitivities

PTDFs, LODFs, shift factors, loss sensitivities, flow and voltage sensitivities, line loading replicator and LODF screening.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (23)**

- [Power Transfer Distribution Factors](#power-transfer-distribution-factors)
- [Power Transfer Distribution Factors Dialog](#power-transfer-distribution-factors-dialog)
- [Directions Display](#directions-display)
- [Directions Dialog](#directions-dialog)
- [Auto Insert Directions](#auto-insert-directions)
- [Calculate MW-Distance](#calculate-mw-distance)
- [MW-Distance Options](#mw-distance-options)
- [Line Outage Distribution Factors (LODFs)](#line-outage-distribution-factors-lodfs)
- [Line Outage Distribution Factors Dialog](#line-outage-distribution-factors-dialog)
- [Advanced LODF Calculation Dialog](#advanced-lodf-calculation-dialog)
- [Shift Factor Sensitivities](#shift-factor-sensitivities)
- [Shift Factor Sensitivities Dialog](#shift-factor-sensitivities-dialog)
- [Shift Factor Multiple Device Type](#shift-factor-multiple-device-type)
- [Transmission Loading Relief Sensitivies](#transmission-loading-relief-sensitivies)
- [Loss Sensitivities](#loss-sensitivities)
- [Flow and Voltage Sensitivities](#flow-and-voltage-sensitivities)
- [Single Meter, Multiple Transfers](#single-meter-multiple-transfers)
- [Single Transfer, Multiple Meters](#single-transfer-multiple-meters)
- [Self Sensitivity](#self-sensitivity)
- [Multiple Meters, Single Control Change](#multiple-meters-single-control-change)
- [Multiple Meters, Multiple Control Change](#multiple-meters-multiple-control-change)
- [Line Loading Replicator](#line-loading-replicator)
- [LODF Screening](#lodf-screening)

---

<a id="power-transfer-distribution-factors"></a>

## Power Transfer Distribution Factors

*Source: [`Content/MainDocumentation_HTML/Power_Transfer_Distribution_Factors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Transfer_Distribution_Factors.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Power Transfer Distribution Factors (PTDF) indicate the incremental change in real power that occurs on transmission lines due to real power transfers between two regions. These regions can be defined by areas, zones, super areas, single buses, injection groups or the system slack. These values provide a linearized approximation of how the flow on the transmission lines and interfaces change in response to a transaction between the Seller (source) and the Buyer (sink). These values can then be visualized on the onelines using animated flows (see below for details).

When considering areas, zones, or super areas as part of the transaction, the transaction for which the PTDFs are calculated is modeled by effectively scaling the output of all generators on [AGC](10-power-flow-solution-and-options-part3.md#area-control) in the source and sink areas in proportion to their relative [participation factors](06-object-properties-edit-mode-part1.md#generator-participation-factors). Generators in the source area effectively increase their output, while generators in the sink area effectively decrease their output.

When including injection groups as part of the transaction, the AGC status of any participating generators does not matter. All generators in the injection group with non-zero participation factors will be included in the transaction. When loads are included in injection groups, loads in the Seller would be effectively decreased in order to effect a transaction and loads in the Buyer would be effectively increased in order to effect a transaction. Buses in the injection group are also allowed to participate in the transaction even if the bus has no generation or load. Buses are modeled as an increase in injection if in the seller and a decrease in injection if in the buyer.

Of course, the PTDF calculation is a linear calculation and no changes are actually made to the output of generators, loads, or buses to study the impact of the transaction regardless of the type of seller or buyer.

An important aspect to consider in calculating the PTDF is how the losses associated with the transfer are allocated. Simulator assumes that the Seller increases its injection by 100% of the transfer amount (generators increase and loads decrease), while the Buyer decreases its injection (generators decrease and loads increase) by 100% of the transaction **minus any change in system losses**. In other words, the Buyer accounts for the entire change in the system losses. Of course it is possible that a transfer may result in decreased system losses; for that case, the Buyer’s change in injection will be greater than 100% of the transfer.

To Calculate the Power Transfer Distribution Factors:

  - Perform an initial Power Flow Solution.
  - In Run Mode, click on the Tools ribbon tab and select **Power Transfer Distribution Factors (PTDFs)** from the **Sensitivities** menu on the **Run Mode** ribbon group to open the [Power Transfer Distribution Factors dialog](#power-transfer-distribution-factors-dialog).
  - Supply the requested information on the [Power Transfer Distribution Factors dialog](#power-transfer-distribution-factors-dialog) and click the **Calculate PTDFs** button. The distribution factors are calculated and displayed for the element set of your choice in the table at the bottom of the dialog.

The animated flows that appear on the oneline diagram may represent either actual flows or PTDF values. To specify that the display should show distribution factors, click the button labeled **Visualize PTDFs** on the Power Transfer Distribution Factors dialog. Once this button is clicked, the flow arrows on all open onelines will represent distribution factors, any [transmission line pie charts](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-lines) will show PTDF values, and the caption of the button will change to **Visualize Actual Power Flows**. Click the button again to visualize actual power flows instead of distribution factors.

Note that when calculating PTDF values for interfaces that include contingent elements, the PTDF values reported are actually what are referred to as an Outage Transfer Distribution Factor (OTDF). See [Line Outage Distribution Factors (LODFs)](#line-outage-distribution-factors-lodfs) for more information.

---

<a id="power-transfer-distribution-factors-dialog"></a>

## Power Transfer Distribution Factors Dialog

*Source: [`Content/MainDocumentation_HTML/Power_Transfer_Distribution_Factors_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Transfer_Distribution_Factors_Dialog.htm)*

The PTDF dialog enables you to control and view the results of [power transfer distribution factor calculations](#power-transfer-distribution-factors). To access this dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Power Transfer Distribution Factors** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

Two PTDF dialogs can be open simultaneously, but when doing this Simulator forces one dialog to show **Single** directions, while the second dialog shows **Multiple** directions.

The dialog has the following options:

Linear Calculation Method

PTDFs may be calculated using either the full power flow Jacobian or only a portion of it. If you select the **Linearized AC Approximation** option, the sensitivity of the monitored element’s flow will be calculated as a function of both its real and reactive power components to the voltage magnitude and angle of its terminal buses. When using the AC method, losses are included in the calculation. Simulator assumes that the change in losses is taken care of by the Buyer.

If you instead select the **Lossless DC Approximation** option, branch flow sensitivity is calculated by estimating the real power that flows through the monitored element only from the difference in angles measured across its terminals. This method assumes that there are no losses.

The **Lossless DC with Phase Shifters Approximation** option is similar to the **Lossless DC**, except additional constraints are placed on the calculations that assume that the change in flow across active phase-shifting transformers is zero.

The Lossless DC methods will be affected by the **DC Power Flow Model** settings in [Power Flow Solution: DC Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options). Click on the **DC Model Options** button to open the dialog that sets these options.

Assumed Location of Injection for Bus

This option is used when calculating PTDFs when one end of the transaction is a Bus, interfaces contain contingency actions that open generators or loads, and these outages need to be reflected in the PTDFs for the interfaces. The location of the injection can be modified to assume that the generator or load that is being outaged is the injector rather than the Bus. When the transactor is not a Bus, the outage of generators or loads in the interface is handled automatically.

The following choices are available for modifying the PTDF results:

Always Bus

This is the default option. No change is made to PTDFs because of outages that occur in interfaces.

Online Generator

This will take into account the outage of generators that occur with interfaces. Regardless of how many generators there are at a particular bus, if any generator at the transactor bus is outaged due to an interface contingency, the PTDF will be adjusted to reflect this outage. The impact of load outages will not be reflected in the PTDF.

Online Load

This will take into account the outage of loads that occur with interfaces. Regardless of how many loads there are at a particular bus, if any load at the transactor bus is outaged due to an interface contingency, the PTDF will be adjusted to reflect this outage. The impact of generator outages will not be reflected in the PTDF.

Online Gen or Load

This will take into account the outage of generators or loads that occur with interfaces. Regardless of how many generators and loads there are at a particular bus, if any generator or load at the transactor bus is outaged due to an interface contingency, the PTDF will be adjusted to reflect this outage.

When adjusting PTDFs for generator or load outages, make-up power is used to determine how those outages are balanced. The make-up power specified with contingency analysis is used. One might expect the PTDF to go to zero for the outage of the element used for the assumed injection location for a bus, but this might not be the case depending on the make-up power.

Directions

This option allows you to choose to define a single direction PTDF using the **Seller** and **Buyer Type** related fields, or to define multiple transfer directions between many different entities. If you choose to use multiple directions, the **Seller** and **Buyer Type** fields are replaced by the [Direction Records display](#directions-display) for viewing and defining directions.

For Single Direction: Seller Type, Buyer Type

Distribution factors can be calculated for power transfers between combinations of areas, zones, super areas, participation groups, or to the system slack bus. Use the **seller type** and **buyer type** options to indicate the type of the selling and buying entities. These fields are only present for single direction PTDFs. When choosing Area, Zone, or Super Area, this really means all generators in the Area, Zone or Super Area weighted by the generator participation factor.

For Single Direction: Seller, Buyer

These drop-down boxes allow you to select the selling and buying entities. Their contents are filled when you select the seller and buyer types. These fields are only present for single direction PTDFs.

For Single Direction: Reverse Buyer/Seller

Click this button to re-calculate PTDFs for the direction that is the reverse of the direction currently shown. For example, if you have just calculated PTDFs for a transaction from area A to area B, press this button to calculate and display PTDFs for a transaction from area B to area A. This option is only present for single direction PTDFs.

Calculate PTDFs

Click on this button to update the PTDF values. The results table will reveal the latest calculations.

Automatically Recalculate

If checked, the PTDFs are automatically recalculated every time the power flow is solved.

Calculate MW-Distance

Click this button to open the **MW \* Distance Calculations** form. This form allows you to calculate MW \* Distance values for the transaction for which you calculated PTDFs. See [MW-Distance Calculations](#calculate-mw-distance) for more information.

Increase in Losses

This is a read-only field that indicates the change in system losses caused by the transfer from the seller to the buyer. The change is expressed as a percentage of the transfer amount. This will only be non-zero when using the **Linearized AC** calculation method.

Use Area/Zone Filters

If this box is checked, then the results table at the bottom of the dialog will include only records associated with devices located in areas or zones included in the [area/zone/owner filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) set.

Only Show Above %

Restricts the result set to show only those PTDFs that exceed a specified value.

Visualize Actual Power Flows, Visualize PTDFs

Click to toggle the onelines between showing the actual power flows and the PTDF flows. Selecting this button changes the Flow Visualization field for all the visible onelines. You can also change this field manually using the [Oneline Display Options](15-using-onelines-tools-and-options.md#oneline-display-options-dialog) Dialog. When choosing to visualize PTDFs, the animated flow arrows will represent PTDF values, and any [transmission line pie charts](13-building-onelines-graphics-and-insertion.md#pie-chartsgauges-lines) will also be changed to show PTDFs.

Tables of Results

The tables of results occupy the bottom of the PTDF dialog. They are a set of [case-information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus share many characteristics common to all other case information displays. The tables will show results for lines/transformers, interfaces, areas, zones, generators, and phase shifters. The tables feature a [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options) from which you can print, copy, or modify its records as well as view the [information dialog](07-object-properties-run-mode-and-general-part2.md#area-information) of its associated element. You can also sort the area records by clicking on the heading of the field by which you want to sort.

Lines/Transformers

Shows the transaction distribution factors for the lines and transformers. The following fields are shown:

From Number, From Name, To Number, To Name, Circuit

Identifiers for the transmission line or transformer.

% PTDF From

Distribution factor associated with the MW flow at the "from bus" end of the line or transformer, specified as a percentage of the transaction amount.

% PTDF To

Distribution factor associated with the MW flow at the "to bus" end of the line or transformer, specified as a percentage of the transaction amount.

% Losses

Shows the percentage of the PTDF assigned as losses.

Nom KV (Max) and Nom KV (Min)

Displays the maximum and minimum nominal voltages for the line. This is useful for identifying transformers and which end of the PTDF relates to which nominal voltage.

Interfaces

Shows the transaction distribution factors for the [interface records](05-case-information-displays-by-object-part3.md#interface-display). The following fields are shown:

Name

Alphanumeric identifier for the interface.

Number

Numeric identifier for the interface.

% PTDF

Distribution factor associated with the MW flow through the interface, specified as a percentage of the transaction amount. A positive value indicates the transaction would result in an increase in the flow through the interface.

Interface MW Flow

Amount of real power flowing on the interface.

Has Contingency

Signifies if an interface contains a contingent element.

When an interface has a contingency element of a generator or load, the PTDF will include the impact of this outage if the outaged element is part of the Seller or Buyer. See the **Assumed Location for Injection for Bus** option to specify how to include this impact if the Seller or Buyer is a Bus.

Areas and Zones

Shows the impact the transaction has on the losses for the area or zone. The following fields are shown:

Area/Zone Number and Name

Number and name identifiers for the area or the zone

Losses %

Change in the losses in the area or zone, specified as a percentage of the transaction amount. A **positive number** indicates that the transaction would result in **increased** losses in the area or zone, while a **negative number** indicates that the transaction would result in **decreased** losses.

Gen Chg %

Total change in all of the generators in area or zone, specified as a percentage of the transaction amount. For areas, this field should show 100% in the selling area, and 100% minus the change in system losses in the buying area.

Generators

Shows the marginal participation of each generator in the transaction. The following fields are shown:

Number of Bus, Name of Bus, ID

Generator’s terminal bus number and alphanumeric identifier, and the id for the generator.

Area Num of Gen, Area Name of Gen

Name and number of the generator’s area.

Gen Chg %

Assumed participation of the generator in the transaction, specified as a percentage of the transaction amount. This value is directly proportional to the participation factor for the generator, provided the generator is available for AGC and is free to move in the specified direction (i.e., is not at a MW limit). The generator’s participation factor and AGC status are modified on the [Generator Dialog](07-object-properties-run-mode-and-general-part1.md#generator-information), which can be displayed by right-clicking anywhere in the record’s row in the table and selecting the **Show Dialog** option.

Phase Shifters

Shows the transaction distribution factors for the phase shifters. This applies when using the Lossless DC with Phase Shifters calculation method. The following fields are shown:

From Number, From Name, To Number, To Name, Circuit

Identifiers for the phase shifter.

Status

Indicates whether or not the phase shifter is in-service.

Phase (Deg)

The current phase angle of the transformer.

XF Auto

Indicates if the phase shifter is currently enabled for automatic control.

Deg per MW

This field indicates the amount of angle change, in degrees, that would be required to keep the flow across the transformer constant for a one MW transfer between the seller and the buyer.

Tap Min, Tap Max

The minimum and maximum tap positions for the phase shifter.

---

<a id="directions-display"></a>

## Directions Display

*Source: [`Content/MainDocumentation_HTML/Directions_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Directions_Display.htm)*

Multiple directions can be studied in both the [Power Transfer Distribution Factors (PTDF) tool](#power-transfer-distribution-factors-dialog) and the [Available Transfer Capability (ATC) tool](32-available-transfer-capability.md#multiple-directions-available-transfer-capability-dialog). The Directions Display will appear in each tool when the options are set for studying multiple directions. The Directions Display is a [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) that allows you to insert, delete, and modify directions using options available from the display's [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options). When directions are modified or inserted individually, the Directions Dialog will be displayed for entering the information. In addition to individually defining directions, they can also be automatically inserted by selecting the **Direction records \> Auto Insert Directions** option and using the [Auto Insert Directions dialog](#auto-insert-directions).

The following available fields are of note:

Name

A unique name given to the defined direction. This is the key field used to identify each direction.

Source, Source Name

The object type and name of the source.

Sink, Sink Name

The object type and name of the sink.

Include

Set to YES to include this direction when used with multiple direction PTDF or ATC calculations. Set to NO to ignore this direction.

Processed Multiple PTDF

Specifies if the direction has been processed for a multiple direction PTDF analysis. This field is only applicable when running multiple direction PTDF analysis and will not be changed when running multiple direction ATC analysis.

ATC Validation

When running multiple direction ATC analysis, this field will contain any errors encountered while validating directions prior to running the analysis. Only directions with the Include field set to YES will be validated. If any direction has an error, the entire ATC analysis will not run until all errors have been corrected or the directions with errors are set to Include = NO. \[ Added in February 18, 2025 patch of Version 23 \]

---

<a id="directions-dialog"></a>

## Directions Dialog

*Source: [`Content/MainDocumentation_HTML/Directions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Directions_Dialog.htm)*

Directions are objects that are used with the [Power Transfer Distribution Factor (PTDF) tool](#power-transfer-distribution-factors-dialog) and the [Available Transfer Capability (ATC) tool](32-available-transfer-capability.md#multiple-directions-available-transfer-capability-dialog) when calculating multiple directions.

The **Directions Dialog** can be used to insert a new direction or to modify the information for an existing direction. This dialog can be called by choosing **Insert** or **Show Dialog** from the [Directions Display](#directions-display) local menu.

The options that can be set from this dialog include:

Name of Direction

The name of the direction. If you are entering a new direction, you can enter a new direction name. If you are modifying an existing direction, the name of the currently viewed direction will be displayed. The Find button can be used to open a chooser dialog to find a specific direction. Selecting a direction will display that direction's information in the dialog.

Source Type

Select the type of object for the direction source. The chooser to the right of the type will update with all available objects of the selected type. Select a specific object from the chooser to set the direction source.

Sink Type

Select the type of object for the direction sink. The chooser to the right of the type will update with all available objects of the selected type. Select a specific object from the chooser to set the direction sink.

Include in list of monitored directions

Check this box to include the direction in analysis that allows multiple directions. The status of this box sets the Include field of the direction.

OK, Save, Cancel, Delete

Click the **OK** button to save any changes and close the dialog. Click the **Save** button to save any changes but leave the dialog open. Click the **Cancel** button to ignore any changes and close the dialog. Click the **Delete** button to delete the currently selected direction.

---

<a id="auto-insert-directions"></a>

## Auto Insert Directions

*Source: [`Content/MainDocumentation_HTML/Auto_Insert_Directions.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auto_Insert_Directions.htm)*

Multiple directions can be automatically inserted for PTDF and ATC studies using the **Auto Insert Directions** dialog. This option can be selected from the local menu of the [Directions Display](#directions-display) by choosing the **Direction Records \> Auto Insert Directions** option.

The layout of the dialog is as follows:

Type of Direction

The following are the types of directions that can be automatically defined:

Area to Reference

Create directions with the areas that meet the **Source Filter When Using Sink Reference** filter as the Source and the object selected as the **Sink Reference**. The directions are named using area names and the name of the sink object.  

Zone to Reference

Create directions with the zones that meet the **Source Filter When Using Sink Reference** filter as the Source and the object selected as the **Sink Reference**. The directions are named using zone names and the name of the sink object.

Injection Group to Reference

Create directions with the injection groups that meet the **Source Filter When Using Sink Reference** filter as the Source and the object selected as the **Sink Reference**. The directions are named using injection group names and the name of the sink object.

Bus to Reference

Create directions with the buses that meet the **Source Filter When Using Sink Reference** filter as the Source and the object selected as the **Sink Reference**. The directions are named using bus names and the name of the sink object.

Area to Area

Create directions for combinations of areas in the case. If the option **Use Area/Zone Filter...** is checked, only areas meeting the filter are considered, otherwise all areas are considered. Each area meeting the filter criteria is sorted in a list from low to high area number. Each area is combined with every other area with a higher area number. The directions are created with the area with the lowest area number being the Source. The name of the direction is comprised of the names of the areas.

Zone to Zone

Create directions for combinations of zones in the case. If the option **Use Area/Zone Filter...** is checked, only zones meeting the filter are considered, otherwise all zones are considered. Each zone meeting the filter criteria is sorted in a list from low to high zone number. Each zone is combined with every other zone with a higher zone number. The directions are created with the zone with the lowest zone number being the Source. The name of the direction is comprised of the names of the zones.

Injection Group to Injection Group

Create directions for combinations of injection groups in the case. The injection groups are sorted alphabetically, and the directions are created my going through the list from beginning to end and matching each injection group with all other injection groups below it in the list. The injection group that comes first in the alphabetical list is the Source. The name of the direction is comprised of the names of the injection groups.

Sink Reference

This is used to select a single object of type **Area**, **Zone**, or **Injection Group** to be the Sink of the direction(s) or select the system **Slack** to be the Sink. This is used when the **Type of Direction** is set to one of the options with **to Reference**. When selecting an object other than **Slack**, click the **Select Sink** button to open a chooser that allows selection of a specific object. All directions will be created with this object as the Sink, with the Source being the type of object selected with the **Type of Direction** option. The **Source Filter When Using Sink Reference** option determines the objects to use as the Source when creating directions.

Source Filter When Using Sink Reference

When the **Type of Direction** is set to one of the **to Reference** options, this is used to filter the objects to be used as the Source when creating new directions. Directions are created for combinations of the objects that meet this filter used as the Source and the single object selected as the **Sink Reference**.

The filter options include: **All** to use all objects, [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters), **Selected** where the Selected field is YES, and **Meets Filter** where an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) is specified.

Delete Existing Directions

When checked, any previously defined directions will be deleted before the new directions are automatically inserted. If not checked, then automatically inserted directions will be added to the list of previously defined directions. By not deleting existing directions before automatically inserting new directions, it is possible to have more than one direction defined with the same source and sink.

If the name of a new direction is the same as an existing direction, the Source and Sink will be updated to match those meeting the criteria of the auto inserted direction.

Use Area/Zone Filter for Area to Area or Zone to Zone

If checked, then only Areas and Zones with their [Area/Zone/Owner Filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) set to **Yes** will be used when automatically inserting directions. This option is only used when inserting the **Area to Area** or **Zone to Zone** type of direction.

Insert Directions

**Insert Directions** will perform the automatic insertion routine for the directions, according to the defined options.

Cancel

Close the dialog without inserting any directions.

---

<a id="calculate-mw-distance"></a>

## Calculate MW-Distance

*Source: [`Content/MainDocumentation_HTML/calculate_mw_distance.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/calculate_mw_distance.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can estimate MW \* Distance quantities for the system’s areas and zones that result from a specified transaction. Given a transaction from a specified source to a specified sink, Simulator uses [power transfer distribution factors (PTDFs)](#power-transfer-distribution-factors) to estimate the change in flow for each line in the system that results from the transaction. For each line, multiplying the line’s change in flow by its length then gives the MW \* Distance index for that line. Simulator then sums the MW \* Distance indices by area and by zone to obtain the total MW \* Distance for each area and zone in response to the specified transaction.

Because the MW \* Distance calculations use PTDFs, you must access the MW \* Distance functionality from the PTDF Dialog. Once you have calculated PTDFs for a particular transaction by pressing the **Calculate PTDFs** button, click the **Calculate MW \* Distance** button to bring up the **MW \* Distance Calculations Dialog**.

The top portion of the MW \* Distance Calculations Dialog is used to set the lengths of the lines in the case. Although line length is represented as a data element in the power flow case, it often is left blank. However, Simulator needs line length information if it is to calculate MW \* Distance indices. Simulator offers a few options regarding the source of line length information. If you do not have access to line lengths, either from the existing case or an external text file, Simulator can estimate line lengths for you. It does this by using the Ohms/Length values you specify in the table for lines of various kV. Simply indicate the voltage levels in the first row of the table, and the corresponding ohms or reactance per length in the second column. You do not need to differentiate here between English and metric units, because the calculation is independent of the measurement system. If you want the length estimates calculated using this table to overwrite any line lengths that may already be present in the case, be sure to check the **Always Estimate Length** checkbox; otherwise, the new estimates will set the lengths only of lines whose pre-defined length isn’t greater than zero. If you want the estimates to populate the lengths of lines in the model so that, when you save the model, the estimated lengths are saved as part of the model, check the **Save Estimates With Case**. (This provides a handy way to set line lengths for a case that might not have any defined.) Note that, in performing these estimates, transformers are defined as having zero length. If you do not want Simulator to estimate line lengths but instead want to use the line lengths that are currently stored in memory, check the **Do Not Use Length Estimates** box. Finally, if you want to load line lengths from a text file, click the **Load Line Lengths from File** button. This file can be either comma- or space-delimited, and each line must have the following fields in the order specified:

 From\_Bus\_Number  To\_Bus\_Number  Circuit\_ID Length

Once Simulator knows how to calculate line lengths, it can calculate MW\*distance indices for each area and zone. Specify the amount of MW that will be transacted in the **Size of Transaction** textbox. You may use the arrows to increase or decrease the size of the transaction. Simulator assumes that the transaction is to occur between the source and sink groups for which you just calculated PTDFs. Press the button labeled **Calculate** to compute the indices. Two tables are populated with the results of the calculation, one for areas, and another for zones. Use the tabs to switch between the two tables. These tables are [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus share[characteristics and controls](https://www.powerworld.com/WebHelpvoid\(0\);) common to all case information displays. Thus, you can sort the tables, add or delete columns, access the area and zone dialogs, print the tables, and save their content as HTML.

Several options can be set to customize the calculation of MW\*Distance. These options are reached from the [MW\*Distance Options Dialog](#mw-distance-options)**.**

---

<a id="mw-distance-options"></a>

## MW-Distance Options

*Source: [`Content/MainDocumentation_HTML/MW_Distance_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/MW_Distance_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The calculation of MW\*Distance quantities can be customized in a number of ways. These options are set from the MW\*Distance Options Dialog.

Include Tie Lines Only

If this box is checked, then the only branches that contribute to the MW\*Distance calculation are those that tie two areas together. Otherwise, both tie lines and lines internal to areas and zones are included in the calculation. In the latter case, tie lines are assumed to belong to the area that owns the metered end of the branch.

Internal Flows

If you choose to include both tie line flows and flows internal to areas and zones in calculating MW\*Distance quantities, you have two options for how to treat internal flows. You can ignore flows resulting from the transaction that flow in the reverse direction of the existing flow on a branch by checking the **Include flow increases only** checkbox. You can also choose to treat all such counterflows as negative contributions to an area or zone’s MW \* Distance value by checking the **Deduct flow reductions** checkbox.

Omit Branches

To omit branches for which the PTDF corresponding to the transaction is less than a specified value, specify a nonzero percentage in this textbox.

---

<a id="line-outage-distribution-factors-lodfs"></a>

## Line Outage Distribution Factors (LODFs)

*Source: [`Content/MainDocumentation_HTML/Line_Outage_Distribution_Factors_LODFs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Outage_Distribution_Factors_LODFs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Line Outage Distribution Factors (LODFs) are a sensitivity measure of how a change in a line’s status affects the flows on other lines in the system. On an energized line, the LODF calculation determines the percentage of the present line flow that will show up on other transmission lines after the outage of the line. For example, consider an energized line, called LineX, whose present MW flow is 100 MW. If the LODFs are found to be

LODFs for LineX outage

LineX  -100%

LineY  + 10%

LineZ  - 30%

This means that after the outage of LineX, the flow on LineX will decrease by 100 MW (of course), LineY will increase by 10 MW, and LineZ will decrease by 30 MW. The "flow on Line X" here means the flow at the *from* bus going toward the *to* bus.

Similarly, sensitivities can be calculated for the insertion of a presently open line. In this case, the LODF determines the percentage of the post-insertion line flow that will come from the other transmission line after the insertion. The "LODF" is better named a Line Closure Distribution Factor (LCDF) in this case.

To calculate the LODFs:

  - Perform an initial [Power Flow Solution](10-power-flow-solution-and-options-part2.md#solving-the-power-flow).
  - In [Run Mode](01-getting-started.md#run-mode-introduction), select **Sensitivities \> Line Outage Distribution Factors (LODFs)** from the **Run Mode** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab to open the [Line Outage Distribution Factors Dialog](#line-outage-distribution-factors-dialog).
  - Supply the requested information on the [Line Outage Distribution Factors Dialog](#line-outage-distribution-factors-dialog) and click the **Calculate LODFs** button.

What else are LODFs used for?

LODFs are used extensively when modeling the linear impact of contingencies in Simulator. This is true for the calculation of [PTDFs](#power-transfer-distribution-factors) for interfaces which contain a contingent element, as well as when performing Linear [ATC analysis](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) that includes branch contingencies.

When calculating "PTDF" values for interfaces that include [contingent elements](24-contingency-element-dialog.md#contingency-element-dialog), the PTDF values reported are actually what are referred to as an Outage Transfer Distribution Factor (OTDF). An OTDF is similar to PTDF, except an OTDF provides a linearized approximation of the *post-outage* change in flow on a transmission line in response to a transaction between the Seller and the Buyer. The OTDF value is a function of PTDF values and LODF values. For a single line outage, the OTDF value for line x during the outage of line y is

OTDFx = PTDFx + LODFx,y \* PTDFy

where PTDFx and PTDFy are the PTDFs for line x and y respectively, and LODFx,y is the LODF for line x during the outage of line y. More complex equations are involved when studying contingencies that include multiple line outages, but the basic idea is the same.

When performing Linear [ATC analysis](32-available-transfer-capability.md#available-transfer-capability-atc-analysis) along with calculating OTDFs, Simulator determines the linearized approximation of the post-outage flow on the line. This is similarly determined as

OutageFlowX = PreOutageFlowX + LODFx,y\* PreOutageFlowY

where PreOutageFlowX and PreOutageFlowY are the pre-outage flow on lines x and y.

---

<a id="line-outage-distribution-factors-dialog"></a>

## Line Outage Distribution Factors Dialog

*Source: [`Content/MainDocumentation_HTML/Line_Outage_Distribution_Factors_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Outage_Distribution_Factors_Dialog.htm)*

The LODF Dialog enables you to control and to view the results of Line Outage Distribution Factor calculations. You access this dialog by selecting **Sensitivities \> Line Outage Distribution Factors (LODFs)** from the **Run Mode** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab in [Run Mode](01-getting-started.md#run-mode-introduction) only.

Two LODF dialogs are allowed to be opened simultaneously, but when doing this Simulator forces one dialog to show a **Single LODF** calculation, while the second dialog shows the **LODF Matrix**.

The dialog has the following options:

Output Option

Choose *Single LODF* to calculate only the sensitivities related to the status change of a single transmission line. Choose *LODF Matrix* to calculate a matrix of sensitivities.

For Single LODF: Specify Near Bus, Far Bus

Specify the line whose status modification you would like to determine sensitivities to. The direction of the near/far chosen is important. Switching the near and far bus around will change the sign of all the LODF sensitivities.

For Single LODF: Action

Check **Outage Sensitivities** to determine sensitivities for the outage of a line.

Check **Closure Sensitivities** to determine sensitivities for the closure of a presently outaged line. The LODF might better be named a Line Closure Distribution Factor (LCDF) in this case.

For LODF Matrix: Specify Lines to Process (Outage or Closure) and Lines to Monitor

Lines to Process and Lines to Monitor

Choose which lines to process and which lines to monitor by choosing either all AC lines, only those that meet the area/zone/owner filters, only lines with Selected field set to YES, or only those lines that meet an [Advanced Filter](04-model-explorer-and-case-information-part2.md#advanced-filtering). The lines to monitor can also be set the same as the lines selected for processing.

**Do not monitor lines that are open** can be checked to exclude lines that are presently open from the monitoring. This option only affects that lines that are being monitored.

Monitor Branches in Interfaces

Check the **Monitor Interfaces (will add branches to the Lines to Monitor)** checkbox to include interfaces in the monitoring. By including interfaces, the individual lines that are monitored as part of the interface will be added to the list of monitored lines. Contingency elements within interfaces are ignored. This option does not change the format of how the results are reported.

After choosing **Calculate LODFs**, each row of the results represents the line being outaged/closed. Each column of the results represent the line begin monitored and the corresponding LODF/LCDF for that line.

Linear Calculation Method

Linearized AC

This calculation method is not available for LODF sensitivities.

Lossless DC

Uses the DC power flow approximation.

Lossless DC with Phase Shifters

Check this to include the impact of phase shifter controllers with the Lossless DC calculation. By checking this, it is assumed that operating phase shifters will maintain their control requirements after the line outage.

The Lossless DC methods will be affected by the **DC Power Flow Model** settings in [Power Flow Solution: DC Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options). Click on the **DC Model Options** button to open the dialog that sets these options.

Line Closure Options

Status Options Added in version 20

This drop down will only be enabled if the power flow case has branches with Branch Device Type of *Breaker* or *Load Break Disconnect*. Line closure sensitivities are calculated by modeling power injections at the terminals of the line being closed. These calculations can only be done if the terminals are in energized islands. When using a full topology case that models switching devices such as *Breakers* and *Load Break Disconnects* to open and close branches, the terminals of the branch being studied in a line closure sensitivity will never be energized. This means that the line closure sensitivities cannot be determined. If the calculations are modified to model the power injections at the energized terminals of the switching devices instead, the line closure sensitivities can be calculated. This option allows selection of where the power injections are modeled for line closure sensitivities:

**Line Status**

This option means that the branch being studied will change its own status to open it rather than using other switching devices. This occurs in a case without switching devices or when studying the closure of a switching device. Use the terminals of the branch being studied for closure sensitivities. If the branch is open because breakers or other switching devices have been opened to disconnect the branch, the line closure sensitivities cannot be calculated and will all be 0.

**Breaker Status**

Use this option to transfer the calculation of line closure sensitivities to the energized terminals of *Breakers*that have been opened to disconnect a line. This calculation can only be done if breakers are strictly in series with the line being studied.

**Breaker and Load Break Disconnect Status**

Use this option to transfer the calculation of line closure sensitivities to the energized terminals of *Breakers*and *Load Break Disconnects* that have been opened to disconnect a line. This calculation can only be done if switching devices are strictly in series with the line being studied.

Calculate based on post-closure flow (LCDF) and Calculate based on pre-closure flow (MLCDF)

Added in version 19, build on May 31, 2017

A line closure sensitivity determines the percentage of the post-closure flow on a line that will show up on another line. Because these sensitivities are calculated while the line is open, it is often more convenient when linearly determining the impact of a line closure, or multiple line closures, to use a sensitivity that is based on the pre-closure flow on the line. The pre-closure flow on a line is just the line flow calculation using existing system voltages and angles and ignoring the status of the line.

If comparing a linear sensitivity calculation and resulting flow changes against actual system changes, it is often most convenient to use the sensitivity based on the post-closure flow. This value is referred to as the Line Closure Distribution Factor (LCDF). This value will also correspond to the LODF of the line once it is closed and the linear impact of opening the line is calculated. When doing calculations that determine the actual flow changes on other lines caused by closing a line, it is often most convenient to use the sensitivity based on the pre-closure flow of the line. This can be easily calculated from the present voltages and angles in the case. This value is referred to as the Modified Line Closure Distribution Factor (MLCDF).

Calculate LODFs

Click this to calculate the LODFs and update the display.

Advanced LODF Calculation

Opens the [Advanced LODF Calculation](#advanced-lodf-calculation-dialog) dialog for setting additional options for the calculation.

LODFs Tab

After calculating a LODF Matrix, each row of the results represents the line being outaged/closed. Each column of the results represent the line being monitored and the corresponding LODF/LCDF for that line.

When calculating LODFs for a single branch, This tab contains a table showing a list of the lines in the case. Since this table us another variety of the [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays), you may interact with it in a familiar manner. Click on any of the field headings to sort by that field. Right-click on the display to call up the display’s [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options). From the [local menu](04-model-explorer-and-case-information-part1.md#local-menu-options), you can print the violations, copy the violation records to the Windows clipboard for use with another application, modify the format and content of the listing, view the information dialog of the respective element, and view the [Quick Power Flow List](05-case-information-displays-by-object-part1.md#quick-power-flow-list) or [Bus View Display](08-view-case-data-tools.md#bus-view-display).

The default fields for the tab are as follows:

From Bus Number and Name

From bus number and name of the monitored line.

To Bus Number and Name

To bus number and name of the monitored line.

Circuit

Two-character identifier used to distinguish between multiple lines joining the same two buses.

% LODF

The LODF value for the monitored line.

From MW, To MW

The present MW flows on the monitored line at the from bus and the to bus.

From CTG MW, To CTG MW

The projected MW flows after the change in line status on the monitored line at the from bus and the to bus.

Interface LODFs

This tab lists LODFs for interfaces. These LODFs are calculated based on the LODFs of the individual branches that comprise the interface. Only monitored branches are included, and any contingency elements within the interface are ignored.

After calculating a LODF Matrix, each row of the results represents the line being outaged/closed. Each column of the results represent the interface being monitored and the corresponding LODF/LCDF for that interface.

The default fields for this tab when calculating a single LODF/LCDF are as follows:

Number

This is the number of the given interface.

Name

This is the name of the given interface.

% LODF

This is the LODF value for the interface. This is calculated from the LODFs of the individual branches that comprise the interface. This is simply a sum of the branch LODFs based on the direction that the branch is defined in the interface and the monitored direction of the branch in the interface. Any contingency elements within the interface are ignored.

Interface MW Flow

The present MW flow on the interface.

This flow will include the impact of contingency elements within the interface if the **Monitor/Enforce Contingent Interface Elements** option found with the [General](10-power-flow-solution-and-options-part2.md#power-flow-solution-general) tab of the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog is set to enforce interface contingent elements during the power flow solution.

CTG MW

The projected MW flow on the interface based on outaging the specified branch.

This flow ignores the impact of any contingency elements within the interface. It only includes the estimated post-contingency flow on branches that are monitored as part of the interface.

---

<a id="advanced-lodf-calculation-dialog"></a>

## Advanced LODF Calculation Dialog

*Source: [`Content/MainDocumentation_HTML/Advanced_LODF_Calculation_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Advanced_LODF_Calculation_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Advanced LODF Calculation Dialog can be opened by clicking on the Advanced LODF Calculation button found on the [Line Outage Distribution Factors (LODFs) dialog](#line-outage-distribution-factors-dialog). The advanced calculation dialog allows you to calculate the [LODFs](#line-outage-distribution-factors-lodfs) for several different contingent lines in one batch process. First, you need to use the [Contingency Analysis Tool](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) to define which contingent lines to use (all contingencies that contain a single branch outage will be used.) Also, only lines that are being monitored will have their LODFs calculated. See [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) to change which lines are monitored.

The output from the advanced LODF calculation process is saved to a file for import into another program for analysis. This dialog defines how to save the Advanced LODF results to a file for importing in another program.

Format to Save in

You can choose to save the advanced LODF results as "Monitored Branch, Contingency" pairs for PROMOD, or as a matrix in a comma-delimited text file. The comma-delimited text file is useful for loading the results into a spreadsheet program.

Only save pairs with an LODF whose absolute value is greater than

This field allows you to filter out elements whose LODF is below a certain value.

Only Include Monitored Branches whose MW flow increases

This field allows you to filter out monitored elements whose MW flow did not increase in the LODF calculation.

Maximum Columns Per Text File

This field is important when you are saving a matrix in a comma-delimited text file. Most spreadsheet programs have limits on the number of columns they can display. The default is 256, which happens to be the maximum number of columns allowed in Excel.

LODF Number Format

You can choose to have the LODF values stored in either scientific notation, or as a specified length decimal number.

File Name

You must enter a file name and location or **Browse** for a file for saving the LODF data.

Include Contingencies Creating Islands Added in version 20, build on April, 27, 2018

LODF values cannot be calculated for contingencies that will cause a new island to be created. When including these contingencies in the results, the LODF will be reported as a very large number to indicate that these values were not actually calculated. If choosing to not include these contingencies in the results, these contingencies will be completely omitted from the results.

---

<a id="shift-factor-sensitivities"></a>

## Shift Factor Sensitivities

*Source: [`Content/MainDocumentation_HTML/Transmission_Loading_Relief_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transmission_Loading_Relief_Sensitivities.htm)*

(In Version 21 and earlier this was called the TLR Sensitivities or Generation Shift Factors)

Shift Factor Sensitivities are similar to the [Power Transfer Distribution Factors](#power-transfer-distribution-factors). Both Shift Factor Sensitivities and PTDFs measure the sensitivity of the flow on a device to a transaction. To calculate PTDFs, you specify a source group and a sink group, and Simulator determines the percentage of a single transfer between the source and sink that flows on each of several monitored elements. For Shift Factor Sensitivities, you specify a single device, such as a transmission line, to monitor, and a group that serves either as source or as sink. Simulator then determines the sensitivity of the flow on the single monitored element to many different transactions involving the group you specified as the source or sink. To summarize, PTDFs express the sensitivity of many monitored elements to a single transaction, whereas Shift Factor Sensitivities gauge the sensitivity of a single monitored element to many different power transfers.

Shift Factors can be useful for determining which transactions may cause problems when a particular element is overloaded. Suppose we use the Shift Factor Sensitivity tool to determine where area A can purchase power from while a particular overloaded element is in place. We specify area A as the buyer area, identify the overloaded line, and tell Simulator to perform the calculation. Simulator will then list the sensitivity of the flow on the overloaded line to power exchanges between all other generators, areas, and buses to area A. Any transaction for which the sensitivity exceeds some threshold percentage you choose might be a problem and those below might be OK.

To calculate Shift Factor Sensitivities, select **Tools \> Sensitivities \> Shift Factors** from the main menu. This will open the [Shift Factor Sensitivities dialog](#shift-factor-sensitivities-dialog), which will allow you to set Shift Factor Sensitivities options and then calculate the sensitivities.

---

<a id="shift-factor-sensitivities-dialog"></a>

## Shift Factor Sensitivities Dialog

*Source: [`Content/MainDocumentation_HTML/TLR_Sensitivities_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TLR_Sensitivities_Dialog.htm)*

(In Version 21 and earlier this was called the TLR Sensitivities or Generation Shift Factors)

The Shift Factors dialog allows you to calculate [Shift Factor Sensitivities](#shift-factor-sensitivities) for the load flow case at its solved load flow point. To access this dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Shift Factors** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

Two Shift Factor dialogs can be opened at the same time, but when doing this Simulator forces one dialog to show the **Line/XFMR or Interface** device type, while the second dialog shows **Multiple Elements** device type.

The following describes the sections of the dialog:

Device Type

Select whether you want to calculate the sensitivities for a transmission **Line/XFMR**, **Interface**, or for **Multiple Elements**. To calculate sensitivities for an interface, you must have the [interface defined](05-case-information-displays-by-object-part3.md#interface-display) in the case.

When you choose an individual line/transformer or interface, you need to specify the device by selecting it from the list of devices. In this case you specify the From Bus, To Bus, and circuit identifier for a branch, or the interface name or number. When you select the Multiple Elements option, the device selection area of the dialog changes to allow you to select a [Multiple Device Type](#shift-factor-multiple-device-type). The dialog results display changes accordingly in order to accommodate Shift Factor sensitivities for multiple elements.

Interfaces can have contingency actions that outage generators or loads. These outages will be reflected in the shift factor calculations automatically if either end of the transaction is an object type other than Bus. To include the impact of these outages when a bus is part of the transaction, use the **Assumed Location of Injection for Bus** options.

Line/XFMR or Interface Only: Choose device

Specify the From Bus, To Bus, and circuit identifier for a branch, or the interface name, number, and monitored flow direction.

For multiple elements, specify the multiple device type. Choices are: selected lines/transformers, selected interfaces, overloaded lines/transformers in the base case, overloaded interfaces in the base, overloaded lines/transformers during the set of contingencies, and overloaded interfaces during the set of contingencies.

Multiple Elements Choosing Which Devices

See the [Multiple Device Type](#shift-factor-multiple-device-type) topic for details on selecting which devices to study when selecting multiple elements.

Transactor Type

Specify if the sensitivities will be calculated for the transactor being the buyer or the seller. Sensitivities are calculated between each bus in the system individually and the transactor with this field determining the direction of the transfer.

Transactor Object

Specify what the transactor will be. The choices are [Area](05-case-information-displays-by-object-part1.md#area-display), [Zone](05-case-information-displays-by-object-part1.md#zone-display), [Super Area](05-case-information-displays-by-object-part1.md#super-area-display), [Slack](05-case-information-displays-by-object-part1.md#case-summary), [Injection Group](05-case-information-displays-by-object-part3.md#injection-group-display), and [Bus](05-case-information-displays-by-object-part1.md#bus-display). When choosing Area, Zone, or Super Area, this really means all generators in the Area, Zone or Super Area weighted by the generator participation factor.

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), an **Only show the primary bus for each superbus** checkbox will be available on the Buses tab. Checking this box will limit the buses shown on that tab and the list of Bus transactors to only those that are primary buses. This provides a quick means of removing the clutter of redundant data. The primary buses and superbuses are determined from the base case topology.

PTDF Calculation Method

Choose the solution method to use for calculating the sensitivities similar as done on the [Power Transfer Distribution Factors dialog](#power-transfer-distribution-factors-dialog).

Note: The Lossless DC methods will be affected by the **DC Power Flow Model** settings in [Power Flow Solution: DC Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options). Click on the **DC Model Options** button to open the dialog, which sets these options.

Assumed Location of Injection for Bus

This option is used when calculating shift factors for interfaces that contain contingency actions that open generators or loads and these outages need to be reflected in the shift factor values. Shift factor calculations are done by default with one end of the transfer being a bus. The shift factors that are reported for generators and loads show the same shift factors as their terminal buses. This means for example if an interface contingency opens a generator, the shift factor for that generator could be a non-zero value because the outage is not reflected in the shift factor calculation. For that outage to be reflected in the shift factor, the assumed location of the injection must be modified.

In addition to the shift factors being calculated on a per-bus basis, the Transactor Object can be a Bus. These same options are applied when calculating the impact of the transactor bus object on the shift factor.

The following choices are available for modifying the shift factor results:

Always Bus

This is the default option. No change is made to shift factors because of outages that occur in interfaces.

Online Generator

This will take into account the outage of generators that occur with interfaces. Regardless of how many generators there are at a particular bus, there is only a single shift factor value that is applicable to the bus and all generators at that bus. If any generator at the shift factor bus is outaged due to an interface contingency, the shift factor will be adjusted to reflect this outage assuming that the shift factor is effected by this generator only. The impact of load outages will not be reflected in the shift factor.

Online Load

This will take into account the outage of loads that occur with interfaces. Regardless of how many loads there are at a particular bus, there is only a single shift factor value that is applicable to the bus and all loads at that bus. If any load at the shift factor bus is outaged due to an interface contingency, the shift factor will be adjusted to reflect this outage assuming that the shift factor is effected by this load only. The impact of generator outages will not be reflected in the shift factor.

Online Gen or Load

This will take into account the outage of generators or loads that occur with interfaces. Regardless of how many generators and loads there are at a particular bus, there is only a single shift factor value that is applicable to the bus and all generators and loads at that bus. If any generator or load at the shift factor bus is outaged due to an interface contingency, the shift factor will be adjusted to reflect this outage assuming that the shift factor is effected by the outaged generator or load only.

When adjusting shift factors for generator or load outages, make-up power is used to determine how those outages are balanced. The make-up power specified with contingency analysis is used. One might expect the shift factor to go to zero for the outage of the element used for the assumed injection location for a bus, but this might not be the case depending on the make-up power.

Shift Factor Sensitivities

Specify if the next set of calculated shift factor sensitivities should replace the currently calculated values, or be appended to the current values. The normal option is to **Clear before Calculate**. When choosing to **Append on Calculate**, then as new calculations are performed, the results will only replace the existing sensitivity value stored if the new value is larger than the old value. (Note: in this situation, negative values are considered smaller than positive values).

Disconnected Device Options

To calculate a shift factor, the terminal buses of generators and loads must be connected. These options allow shift factors to be calculated for buses containing generators or loads if the bus can be connected through a series switching device. The shift factor will then be used from the energized terminal of the switching device instead of reporting 0 for the sensitivity. This makes it possible for calculating shift factors that can be used to determine the impact of closing in generators or loads. The possible choices are the following:

Close Breaker

Any bus that is disconnected and has either generation or load will attempt to find a breaker, Branch Device Type = *Breaker*, that can be closed to energize the bus. The network of branches between the breaker that needs to be closed and the bus that is being connected must be in series. The resulting shift factor is the value from the connected side of the identified breaker.

This option will only be enabled if the power flow has at least one branch with Branch Device Type of *Breaker*.

Close Load Break Disconnect

Any bus that is disconnected and has either generation or load will attempt to find a load break disconnect, Branch Device Type = *Load Break Disconnect*, that can be closed to energize the bus. The network of branches between the switching device that needs to be closed and the bus that is being connected must be in series. The resulting shift factor is the value from the connected side of the identified switching device.

This option will only be enabled if the power flow has at least one branch with Branch Device Type of *Load Break Disconnect*.

DC Model Options

Click this button to open the [DC Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options) page. Here you can adjust the DC options you want used if you are computing the PTDFs with a Lossless DC approximation.

Include only AGCAble Generators

If checked, then only generators available for automatic generation control (AGC = YES) will be included in the calculations for the Transactor object. This impacts Transactor object types of Area, Zone, Super Area, and Injection Group. For Injection Groups, loads can also participate as part of the Transactor. If this option is used, loads in the injection group must also have their AGC field set to YES.

Calculate Shift Factor Sensitivities 

Click this button to calculate the sensitivities. The calculation processes through each bus and determines the sensitivity of the MW flow of the selected device with respect to a change of real power at each bus. When the **Transactor Type** is Buyer, then the assumption is that power is injected at each bus and absorbed at the **Transactor Object**. When the **Transactor Type** is Seller, then the assumption is that power is injected at each transactor object and absorbed at each bus.

Set Sensitivities At Out-Of-Service Buses Equal to Closest

After shift factors have been calculated, click this button to set the sensitivities of out-of-service buses. If this option is not used, the sensitivities of out-of-service buses will be 0. When this button is clicked a dialog will open with additional options. The **Use Closest** checkbox is checked by default and the default algorithm will be used. The default method finds the closest energized buses and uses the average of the sensitivities at these buses. When Use Closest is not checked, **Distance Measure** options become available. The Distance Measure options are the same options that are used with the [Determine Path Distances to Buses tool](16-oneline-gis-tools.md#path-distances-from-bus-or-group).

Line/XFMR or Interface Only: Bus, Generator, Load, Injection Group, and Area Sensitivities

The Bus Sensitivities show the values calculated at each bus. Generator sensitivities show the same information but have only a list of generators with the P Sensitivity column showing the sensitivity calculated at the terminal bus. The Load sensitivities are similar to the generator sensitivities in that they show the same information as the bus sensitivities but only show the list of loads with the P Sensitivity column giving the sensitivity calculated at the terminal bus. The Injection Group sensitivities represent averages of the bus sensitivities weighted by the participation factors of each generator, load, or switched shunt in the group. All participation factors are included in this calculation regardless of the AGC status of any included generators. The Area Sensitivities calculated represent a weighted average of the generator buses in the area with the weighting done by generator participation factor.

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), an **Only show the primary bus for each superbus** checkbox will be available on the Buses tab. Checking this box will limit the buses shown on that tab and the list of Bus transactors to only those that are primary buses. This provides a quick means of removing the clutter of redundant data. The primary buses and superbuses are determined from the base case topology.

Multiple Elements Only: Multiple Bus, Generators, Loads, and Injection Group Sensitivities

The Multiple Bus Sensitivities show the values calculated at each bus for each device examined during the analysis. Multiple Generator and Load Sensitivities show the same information but have only a list of either generators or loads with the P Sensitivity column showing the sensitivity calculated at the terminal bus. The Multiple Injection Group Sensitivities represent averages of multiple bus sensitivities weighted by the participation factor of each generator, load, or switched shunt in the group. All participation factors are included in this calculation regardless of the AGC status of any included generator.

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), an **Only show the primary bus for each superbus** checkbox will be available on the Buses tab. Checking this box will limit the buses shown on that tab and the list of Bus transactors to only those that are primary buses. This provides a quick means of removing the clutter of redundant data. The primary buses and superbuses are determined from the base case topology.

The results of the multiple element analysis can be accessed using script commands or [SimAuto](33-simauto-overview-and-setup.md#automation-server) by using the variable **SensdValuedPinjMult** with the appropriate data object: Bus, Gen, Load, or InjectionGroup. There will be as many variables with the **SensdValuedPinjMult**name and appropriate location number as there are elements that were studied. The location numbers start at 0. The results are assigned in the order that the elements are included in the list of branches or interfaces to be studied. For example, if the list of branches includes five branches defined in the case in the following order: 1 to 2, 2 to 4, 4 to 3, 3 to 1, 2 to 3, and branches 2 to 4 and 4 to 3 are selected for inclusion in the multiple element TLR calculation, **SensdValuedPinjMult:0** will correspond to branch 2 to 4 and **SensdValuedPinjMult:1** will correspond to branch 4 to 3 for all sets of results. When selecting devices to study based on them being overloaded or contingency-overloaded, the results will appear in the order that the overloaded elements are defined with the case. To determine which elements are overloaded in the base case, use the **Percent** field with Branch data objects and the **Percent** field with Interface data objects. If these fields are greater than 100 percent then the element is overloaded. The **CTGVIOL** variable can be used with the Branch or Interface data type to determine if an element is overloaded due to a contingency. This field will be non-zero for any element that has overloads due to contingencies.

---

<a id="shift-factor-multiple-device-type"></a>

## Shift Factor Multiple Device Type

*Source: [`Content/MainDocumentation_HTML/TLR_Multiple_Device_Type.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/TLR_Multiple_Device_Type.htm)*

(In Version 21 and earlier this was called the TLR Sensitivities or Generation Shift Factors)

The Multiple Device Type selector allows you to specify a group of elements for which shift factor sensitivities will be calculated. The Multiple Device Type selection is accessible only when you choose the **Multiple Elements** option from the **Device Type** in the [Shift Factor Sensitivity dialog](#shift-factor-sensitivities-dialog).

Selected Devices

Select Lines/XFMRs

Select the Selected Devices option, and click on this button to open a dialog to choose the lines and transformers to be included in the calculation. Toggle the Selected field in the Lines and Transformer [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) to Yes for the branches you wish to include. If the Selected field is not available in the information display, add that column to the display by right-clicking in the display and selecting [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays). The ETLR of selected Lines/XFMRs is the algebraic sum of the Shift Factors of each individual element. The WTLR uses as weight the current MW flow in the element.

Select Interfaces

Select the Selected Devices option, and click on this button to open a dialog to choose the interfaces to be included in the calculation. Toggle the Selected field in the interfaces [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) to Yes for the interfaces you wish to include. If the Selected field is not available in the information display, add that column to the display by right-clicking in the display and selecting [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays). The ETLR of the selected interfaces is the sum of the Shift Factors of the interfaces that have a limit different from zero. The WTLR uses as weight the MW flow in the interface.

Overloaded Devices

Select this option to include in the multiple element shift factor calculation the branches and/or interfaces that are overloaded in the present case based on the [Limit Monitoring Settings and Limit Violations Dialog](18-general-tools.md#limit-monitoring-settings). The list of the overloaded branches and interfaces is available in the [Limit Monitoring Settings and Limit Violations](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog) information display.

CTG Overloaded Devices

Select this option to include in the multiple element shift factor calculation the branches and/or interfaces that were identified as overloaded by the [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview) tool. A branch or interface is included in the calculation if it has been overloaded during at least one contingency. The list of branches and interfaces identified as overloaded can be accessed from the [View Results By Element page](23-contingency-analysis-running-and-results.md#view-results-by-element) in the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog).

The ETLR of the CTG overloaded lines and transformers is the algebraic sum of the individual shift factors. The WTLR uses as weight the Aggregate MVA Overload of each transmission line and transformer, which is defined as the sum of the MVA overload in the line or transformer across the contingencies that caused a violation in that particular line or transformer. The Aggregate MVA Overload and a related field, the Aggregate Percent Overload of a line or transformer, are measures of the weakness of that transmission line on the grid. The Aggregated MVA Overload and the Aggregate Percent Overload are line and transformer fields that can be displayed in the [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), used in [Contouring](17-oneline-view-printing-and-contouring.md#contouring), etc.

The ETLR of the CTG overloaded interfaces is the algebraic sum of the individual shift factors. The WTLR uses as weight the Aggregate MW Overload of each interface, which is defined as the sum of the MW overload of the interface across the contingencies that caused a violation in that interface. The Aggregate MW Overload and a related field, the Aggregate Percent Overload of an interface are measures of the weakness of the interface. These two interface fields can be displayed in the [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), used in [Contouring](17-oneline-view-printing-and-contouring.md#contouring), etc.

Effective Transmission Loading Relief (ETLR)

In the same manner as the shift factors represents the MW increase in an element per MW transfer, the ETLR column in the Mult. Bus Sensitivity table represents the total MW increase in all the elements in the set per MW increase of the transaction. Let us suppose that the set contains two transmission lines: A and B and assume that for a 1 MW transfer from bus i to the transactor, the flow in line A increases in 0.5 MW and the flow in line B decreases in -0.3. Then the ETLR of bus i is +0.2 since that is the total MW increase in the elements in the set. The ETLR provides a measure of the simultaneous MW change in multiple elements, and thus the overall effect in flows on the element of the set. The ETLR is a bus field that can be included in the bus [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), used in [Contouring](17-oneline-view-printing-and-contouring.md#contouring), etc.

Weighted Transmission Loading Relief (WTLR)

The WTLR column in the Mult. Bus Sensitivity table weights the sensitivities based on the flow or overload flow values of the element. It is a measure of the value of a certain bus to relief transmission loading. The buses with the highest WTLR (or lowest WTLR, depending on the transactor type) are identified as the most effective buses to mitigate transmission loading considering multiple elements. The WTLR is a bus field that can be included in the bus [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), used in [Contouring](17-oneline-view-printing-and-contouring.md#contouring), etc.

---

<a id="transmission-loading-relief-sensitivies"></a>

## Transmission Loading Relief Sensitivies

*Source: [`Content/MainDocumentation_HTML/Generation_Shift_Factor_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generation_Shift_Factor_Sensitivities.htm)*

(In Version 21 and earlier, the concept of "Shift Factors" was instead called either "TLR Sensitivities" or "Generation Shift Factors:)

They have been renamed simply Shift Factors starting in Version 22. See [Shift Factor Sensitivities](#shift-factor-sensitivities) for more information.

Generation Shift Factor (GSF) Sensitivities are a specific kind of shift factor. GSFs always involve a transfer with the slack bus being the Buyer. Other than this, GSF and Shift Factor calculations are *identical*.

---

<a id="loss-sensitivities"></a>

## Loss Sensitivities

*Source: [`Content/MainDocumentation_HTML/Loss_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Loss_Sensitivities.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Loss Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Loss Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The **Bus Marginal Loss Sensitivities Dialog** is used to calculate and display the sensitivity of a real power loss function, PLosses, to bus real and reactive power injections. Stated mathematically, the display calculates d PLosses/d Pi and d PLosses/d Qi , where Pi and Qi are the real and reactive power injections at bus i, respectively.

Stated less formally, the display indicates how losses would change if one more MW or Mvar of power were injected at bus i. Simulator can calculate the losses for a bus relative to losses in the bus’ island or area, to losses in a select group of areas, or, if the bus belongs to a super area, to losses in the bus’ super area. How Simulator computes the losses is governed by the value of the **Loss FunctionType** option.

The Loss Function Type may assume one of the following six values:

Do Not Calculate Bus Loss Sensitivities

No Losses are calculated because a loss function is not specified.

Each Electrical Island 

**Existing loss Sensitivities:** Losses are calculated with respect to the losses in bus’ island. If the power system consists of only one island, losses are computed with respect to the total system losses.

**Island Loads:**  Losses are calculated with respect to the losses in the island load buses.

**Injection Group:**. Losses are calculated with respect to the losses in island load buses that correspond to the injection group buses of the participation objects that correspond to the island.

Each Area 

Losses are calculated with respect to the total losses for the area containing bus i. This is probably the most common loss function because usually one is concerned with minimizing losses for a particular area rather than for the entire case.

**Use Area Loss Reference:**  Losses are calculated as explained before but with respect to a reference. The choices are Existing loss sensitivities directly, Area’s Bus’ Loads, [Injection Group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview), or a specific bus.

Each Area or Super Area 

Losses are calculated with respect to the total losses for the area containing bus i if bus i does not belong to a super area, and with respect to the total losses for the super area containing bus i if bus i does belong to a super area. When a case contains Super Areas this is more commonly done. When Simulator calculates loss sensitivities internally for use in the Economic Dispatch or the Optimal Power Flow calculation, this is the option which is used.

**Use Super Area Loss Reference:**  Losses are calculated as explained before but with respect to a reference. The choices are Existing loss sensitivies directly, Super Area’s Bus’ Loads, [Injection Group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview), or a specific bus.

Areas Selected on Loss Sensitivity Form

Losses are calculated with respect to the total losses for a group of areas, specified in the Selected Areas table.

User-Specified

If you select User-Specified as the loss function type, the values last calculated using a different loss function type will become fixed. Thus you can force the loss sensitivities to remain constant when used in other features and tools of Simulator.

In steady-state power system operation, total generation must always equal total load plus losses. Therefore, the real power injection at a single bus cannot be changed arbitrarily; it must be met by a corresponding change somewhere else in the system so that the total power remains balanced. In other words, the change in power injection must somehow be absorbed. How the injection is absorbed depends on the Loss Function Type. If the Loss Function Type is **Each Island**, the injection is absorbed by the island slack. For the **Each Area** and **Selected Areas** loss functions, the injection is absorbed at the area tie-lines.

The loss sensitivities are calculated by modeling an injection of power at a bus and then assuming that this injection is absorbed by the island slack bus. The sensitivity then shows how much the losses (for the region of interest) increase when you transfer 1 MW at the injection bus to the island slack. The "region of interest" is what was chosen as Island, Each Area, or Selected Areas.

Therefore, the "absolute numbers" given by the loss sensitivity dialogs are not directly meaningful because we are always assuming that the absorbing point is the island slack bus. What is meaningful is the "difference" between sensitivity numbers.

Example:

 Assume the sensitivities are calculated to be

 Bus A Loss MW Sensitivity = -0.04 = Asens

 Bus B Loss MW Sensitivity = -0.02 = Bsens

 Bus C Loss MW Sensitivity = +0.03 = Csens

Using these we can then look at the sensitivity of generic transfers between these buses by using "superposition".

Consider the following change in injections modeling a transfer of power from Bus A to Buses B and C.

 Bus A injection = +10 MW = AMW

 Bus B injection = - 6 MW = BMW

 Bus C injection = - 4 MW = CMW

An estimate of the change in losses can then be calculated as

 Loss Change  = (AMW)(Asens) + (BMW)(Bsens) + (CMW)(Csens)

   = (+10)(-0.04) + (- 6)(-0.02) + (- 4)(+0.03)

   = -0.4 MW

The Bus Marginal Loss Sensitivities Dialog houses the following controls:

Selected Areas Table

This table is used only when the **Loss Function Type** is set to *Selected Areas*; otherwise, it is ignored. Left-click on the *Include* field to include or exclude areas from the loss function.

Calculate Marginal Loss Sensitivities Button

Once the loss function type has been specified, click this button to calculate the bus marginal loss sensitivities and update the Bus Marginal Loss Sensitivities table.

Bus Marginal Loss Sensitivities Table

This table shows the bus marginal loss sensitivities for all buses with valid [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). The Bus Marginal Loss Sensitivities Table is a type of Case Information Display and thus exhibits features and behavior similar to all other case information displays. It has a local menu from which you can choose to find out more about a particular bus. You can sort records by any of the listed fields by clicking on the column headings. The table contains the following fields:

**Number, Name:** Number and name of the bus.

**Area Number, Area Name:**  Number and name of the bus’ area.

**Loss MW Sens:**. Sensitivity of the loss function to an increase in the real power injection (generated power assumed positive) at the bus.

**Penalty Factors: **Computed penalty factor of each bus.

**MVR Sens:**.  Sensitivity of the loss function to an increase in the reactive power injection (generated power assumed positive) at the bus.

If using the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview), an **Only show the primary bus for each superbus** checkbox will be available for this table. Checking this box will limit the buses show to only those that are primary buses. This provides a quick means of removing the clutter of redundant data. The primary buses and superbuses are determined from the base case topology.

Just Generators Marginal Loss Sensitivities Table

This table shows the bus marginal loss sensitivities for only the generator terminal buses with valid [Area/Zone/Owner filters](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters). This table is otherwise identical to the displayed values and table operation as the Bus Marginal Loss Sensitivities Table described above.

Areas Marginal Loss Sensitivities Table

This table shows the Areas Energy/Loss ref String and Energy/Loss Ref Type used for the losses references when the **Use Area Loss Reference** option is selected.

Super Areas Marginal Loss Sensitivities Table

This table shows the Super Areas Energy/Loss ref String and Energy/Loss Ref Type used for the losses references when the **Use Super Area Loss Reference** option is selected.

---

<a id="flow-and-voltage-sensitivities"></a>

## Flow and Voltage Sensitivities

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

This dialog is split up into 5 separate tabs allowing the calculation of various sensitivity combinations. These tabs are as follows and separate help topics are written for each tab.

  - [Single Meter, Multiple Transfers](#single-meter-multiple-transfers)
  - [Single Transfer, Multiple Meters](#single-transfer-multiple-meters)
  - [Self Sensitivity](#self-sensitivity)
  - [Multiple Meters, Single Control Change](#multiple-meters-single-control-change)
  - [Multiple Meters, Multiple Control Changes](#multiple-meters-multiple-control-change)

Click **Close** to close the Flows and Voltages Dialog.

---

<a id="single-meter-multiple-transfers"></a>

## Single Meter, Multiple Transfers

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SingleMeterMultTrans.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SingleMeterMultTrans.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

Single Meter, Multiple Transfers

The Single Meter, Multiple Transfers tab shows the effect an additional injection of real or reactive power at a bus has on various parameters. If a bus is a PV bus, instead of determining the impact that additional injection of reactive power at the bus has, the impact of changing the voltage setpoint at the bus is determined. Additionally, the sensitivities of the Flow Type will be determined due to phase shifter phase, transformer tap, and switched shunt nominal injection changes.

Device Type and Associated Flow Type

The following device types can be selected with their associated Flow Type.

**Line/XFMR**

MW - real power flow on the branch

Mvar - reactive power flow on the branch

MVA - apparent power flow on the branch

**Interface**

MW - real power flow on the interface

Mvar - reactive power flow on the interface

MVA - apparent power flow on the interface

**Bus**

Magnitude - voltage magnitude in per unit at the bus

Mvar - reactive power injection at the bus

**Generator**

Mvar - reactive power injection at the generator. When determining this sensitivity, the sensitivity of the total Mvar injection at the generator bus is determined. This is the same value that would be returned if picking Device Type of *Bus* and Flow Type of *Mvar*. This total is apportioned to specific generators at a bus based on their proportion of the total Mvar range for the bus. Only generators that are online and on AVR control are included in the calculation.

After selecting a Device Type, a particular device must be selected from the object chooser.

Whenever you make a change to any of these settings, click **Calculate Sensitivities** to update the grids with the new sensitivities.

Buses Tab

The buses tab provides sensitivities for injecting real or reactive power at a bus or changing the voltage setpoint at a bus. All injections assume that the power is absorbed at the island slack bus.

The bus fields (to add see [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)) of interest after this calculation include:

  - *Sensitivity: Injection dValue/dP --\>(P Sensitivity)* gives the sensitivity of the selected Flow Type to an injection of real power at the bus selected in the row of the results
  - *Sensitivity: Injection dValue/dQ --\> (Q Sensitivity)* gives the sensitivity of the selected Flow Type to an injection of reactive power at the bus in the row of the results. This value is only calculated for PQ buses.
  - *Sensitivity: Injection dValue/dVsetpoint (for PV bus) --\> (V Sensitivity)* gives the sensitivity of the selected Flow Type to a change in voltage setpoint at the bus in the row of the results. This value is only calculated for PV buses.
  - *Sensitivity:* *Injection dAngle/dP (radians/MW) --\> (AngleP Sensitivity)* gives the sensitivity of voltage angle to an injection of real power at the bus in the row of the results. This value is only calculated when the **Device Type** is *Bus* and the **Flow Type** is *Magnitude*.
  - *Sensitivity: Injection dAngle/dQ (radians/Mvar) --\> (AngleQ Sensitivity)* gives the sensitivity of voltage angle to an injection of reactive power at the bus in the row of the results. This value is only calculated when the **Device Type** is *Bus* and the **Flow Type** is *Magnitude*.

The option labeled **Set Out-Of-Service** allows you to approximate the sensitivities at out-of-service buses with the sensitivity of the closest bus. Otherwise the out-of-service buses will display sensitivities of 0 when the sensitivities are calculated.

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data. This option also limits the buses that appear in the chooser list when the **Device Type** is *Bus*.

Generators Tab

The generators tab provides the same sensitivity information that is available on the Buses Tab except that only generator buses are listed. This provides an easy way to filter out only generator buses.

Loads Tab

The loads tab provides the same sensitivity information that is available on the Buses Tab except that only load buses are listed. This provides an easy way to filter out only load buses.

Phase Shifters Tab

This tab provides a listing of all phase shifters in the case. The *Sensitivity: Flow/Voltage with respect to Phase --\> Sensitivity/Degree* field gives the sensitivity of the **Flow Type** to a change in phase shifter phase.

LTC Transformers Tab

This tab provides a listing of all transformers in the case. The *Sensitivity: Flow/Voltage with respect to Tap --\> LTC Sensitivity* field gives the sensitivity of the **Flow Type** to a change in transformer tap.

Switched Shunts Tab

This tab provides a listing of all switched shunts in the case. The *Sensitivity: Q Nominal Injection --\> Q Sensitivity* field gives the sensitivity of the **Flow Type** to a change in nominal Mvar injection at a switched shunt.

---

<a id="single-transfer-multiple-meters"></a>

## Single Transfer, Multiple Meters

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SingleTransMultMeter.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SingleTransMultMeter.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

Single Transfer, Multiple Meters

The Single Transfer, Multiple Meters tab shows the effect of a single transfer of real or reactive power on all the voltages in the system. To specify the transfer, choose the **Seller** and **Buyer** in the same manner done on the [Power Transfer Distribution Factors](#power-transfer-distribution-factors-dialog) dialog. Then specify whether the calculation of **Real Power (P)**, **Reactive Power (Q)**, or both are of interest.

Click **Calculate Sensitivities** to perform the calculations.

After clicking **Calculate Sensitivities**, each row of the results gives the sensitivity of voltage at the respective bus to the power transfer defined by the seller and buyer. The bus columns (to add see [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)) of interest after this calculation include:

  - *Sensitivity: Transfer dV/dP (per unit/MW) --\> VP Sensitivity* gives the sensitivity of voltage to a real power transfer
  - *Sensitivity: Transfer dV/dQ (per unit/Mvar) --\> VQ Sensitivity* gives the sensitivity of voltage to a reactive power transfer
  - *Sensitivity: Transfer dAngle/dP (radians/MW) --\> AngleP Transfer Sensitivity* gives the sensitivity of voltage angle to a real power transfer
  - *Sensitivity: Transfer dAngle/dQ (radians/Mvar) --\> AngleQ Transfer Sensitivity* gives the sensitivity of voltage angle to a reactive power transfer

The check box option **Set generators off AVR and continuous switched shunts to fixed at buses participating in the transfer** is also available. Selecting this option will turn off AVR control for generators and continuous switched shunts at buses containing generators participating in the transfer with a non-zero participation factor, resolve the power flow, calculate the voltage sensitivities, turn the AVR control back on for those generators and switched shunts for which it was changed, and then resolve the power flow. Stated another way, this option assumes that all generators and switched shunts at buses participating in the transfer maintain a constant reactive power output and do not maintain their voltage setpoint. With this option, affected buses become PQ buses instead of PV buses in the Jacobian. PV buses will have a zero sensitivity to injection changes because the voltage is fixed at the regulated setpoint, so in order to actually determine the impact of the injection at these buses, they need to be made into PQ buses.

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data. This option also limits the buses that appear in the transactor lists when either the **Seller** or **Buyer** type is *Bus*.

Self Sensitivity

The Self Sensitivity tab shows the effect of an injection of real or reactive power at a bus on its own voltage (assuming everything is absorbed at the island slack bus). It processes through each bus calculating its own self-sensitivity only.

Each row of the results gives the sensitivity of voltage at the respective bus to a power injection at the same bus. dV/dP gives the sensitivity of voltage to real power injection and dV/dQ gives the sensitivity of voltage to reactive power injection. To speed up the calculation, sensitivities are calculated only for the buses displayed in the Bus Sensitivities grid. The bus columns (to add see [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)) of interest after this calculation include:

  - *Sensitivity: Self dV/dP (per unit/MW) --\> dV/dP* gives the sensitivity of voltage magnitude to an injection of real power
  - *Sensitivity: Self dV/dQ (per unit/Mvar) --\> dV/dQ* gives the sensitivity of voltage magnitude to an injection of reactive power
  - *Sensitivity: Self dAngle/dP (radians/MW) --\> dAngle/dP* gives the sensitivity of voltage angle to an injection of real power
  - *Sensitivity: Self dAngle/dQ (radians/Mvar) --\> dAngle/dQ*gives the sensitivity of voltage angle to an injection of reactive power

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data.

---

<a id="self-sensitivity"></a>

## Self Sensitivity

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SelfSensitivity.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_SelfSensitivity.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

Self Sensitivity

The Self Sensitivity tab shows the effect of an injection of real or reactive power at a bus on its own voltage (assuming everything is absorbed at the island slack bus). It processes through each bus calculating its own self-sensitivity only.

Each row of the results gives the sensitivity of voltage at the respective bus to a power injection at the same bus. dV/dP gives the sensitivity of voltage to real power injection and dV/dQ gives the sensitivity of voltage to reactive power injection. To speed up the calculation, sensitivities are calculated only for the buses displayed in the Bus Sensitivities grid. The bus columns (to add see [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)) of interest after this calculation include:

  - *Sensitivity: Self dV/dP (per unit/MW) --\> dV/dP* gives the sensitivity of voltage magnitude to an injection of real power
  - *Sensitivity: Self dV/dQ (per unit/Mvar) --\> dV/dQ* gives the sensitivity of voltage magnitude to an injection of reactive power
  - *Sensitivity: Self dAngle/dP (radians/MW) --\> dAngle/dP* gives the sensitivity of voltage angle to an injection of real power
  - *Sensitivity: Self dAngle/dQ (radians/Mvar) --\> dAngle/dQ*gives the sensitivity of voltage angle to an injection of reactive power

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data.

---

<a id="multiple-meters-single-control-change"></a>

## Multiple Meters, Single Control Change

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_MultMeterSingleControl.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_MultMeterSingleControl.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

Multiple Meters, Single Control Change

The Multiple Meters, Single Control Change tab shows the impact on various quantities to a change in a control setpoint in the system.

The **Control Types** that can be selected:

  - **Generator Voltage Setpoint** - sensitivity of changing the voltage setpoint at a generator in pu. Control unit is pu.
  - **Transformer Tap Ratio** - sensitivity of changing the transformer's tap ratio. Control unit is the tap ratio.
  - **Phase Shifter Phase Shift** - sensitivity of change the phase shifter phase angle. Control unit is degrees expect when calculating angle sensitivities and then it is radians.
  - **Switched Shunt Nominal Mvar** - sensitivity of changing the nominal Mvar injection at a switched shunt. Control unit is Mvar.
  - **Line Impedance Xinj** - sensitivity of changing the per unit series X value on a branch. Control unit is per unit.

Once the Control Type is selected, the specific device must be selected from the object chooser.

Click **Calculate Sensitivities** to perform the calculations.

The sensitivities that are calculated show up on the various tabs:

**Buses**

  - *Sensitivity: dV/dControl (per unit/control unit) --\> dV/dControl*gives the sensitivity of the bus voltage in per unit to the selected Control Type
  - *Sensitivity: dAngle/dControl (radians/control unit) --\> dAngle/dControl* gives the sensitivity of the bus angle in radians to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the bus Mvar injection to the selected Control Type

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data.

Generators

  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the generator Mvar injection to the selected Control Type. When determining this sensitivity, the sensitivity of the total Mvar injection at the generator bus is determined. This total is apportioned to specific generators at a bus based on their proportion of the total Mvar range for the bus. Only generators that are online and on AVR control are included in the calculation.

Branches

  - *Sensitivity: dP/dControl (MW/control unit) --\> dP/dControl*gives the sensitivity of the branch MW flow to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the branch Mvar flow to the selected Control Type

Interfaces

  - *Sensitivity: dP/dControl (MW/control unit) --\> dP/dControl*gives the sensitivity of the interface MW flow to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the interface Mvar flow to the selected Control Type

---

<a id="multiple-meters-multiple-control-change"></a>

## Multiple Meters, Multiple Control Change

*Source: [`Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_MultMeterMultControl.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Flow_and_Voltage_Sensitivities_MultMeterMultControl.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To access the Flows and Voltages Sensitivities dialog, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Sensitivities \> Flows and Voltages Sensitivities** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

The grids that occupy all of the tabs on this dialog list each device of the particular type in the system, subject to the [Area/Zone/Owner Filter](04-model-explorer-and-case-information-part2.md#areazoneowner-and-datamaintainer-filters) settings. These grids are [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays), and thus share properties and controls common to all other case information displays.

Multiple Meters, Multiple Control Change

The Multiple Meters, Multiple Control Change tab shows the impact on a specific field for each device type to a change in a control setpoint in the system.

The **Control Types** that can be selected:

  - **Generator Voltage Setpoint** - sensitivity to changing the voltage setpoint at a generator in pu. Control unit is pu.
  - **Transformer Tap Ratio** - sensitivity to changing the transformer's tap ratio. Control unit is the tap ratio.
  - **Phase Shifter Phase Shift** - sensitivity to change the phase shifter phase angle. Control unit is degrees expect when calculating angle sensitivities and then it is radians.
  - **Switched Shunt Nominal Mvar** - sensitivity to changing the nominal Mvar injection at a switched shunt. Control unit is Mvar.
  - **Line Impedance Xinj** - sensitivity to changing the per unit series reactance X value on a branch. Control unit is per unit.

The available **Control Devices** depend on the selected Control Type. Control devices must be chosen by toggling the "Selected?" field to YES in the list of control devices.

Finally, you must select a **Metered Field** for each metered object type. The metered object types are Buses, Generators, Branches, and Interfaces. By default, *None* is selected.

Click **Calculate Sensitivities** to perform the calculations.

The calculated sensitivities show up in a matrix display on the various tabs, where each tab corresponds to a metered object type. On each tab, each row corresponds to a specific metered data object, and each column corresponds to a selected control device. For each metered object type, results are only shown for one **Metered Field**at a time, and the field choices are the following:

**Buses**

  - *None*calculates no sensitivities for Buses
  - *Sensitivity: dV/dControl (per unit/control unit) --\> dV/dControl*gives the sensitivity of the bus voltage in per unit to the selected Control Type
  - *Sensitivity: dAngle/dControl (radians/control unit) --\> dAngle/dControl* gives the sensitivity of the bus angle in radians to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the bus Mvar injection to the selected Control Type

If the [Integrated Topology Processing add-on](35-integrated-topology-processing.md#topology-processing-overview) is available, the **Only show the primary bus for each superbus** checkbox will be available. When checked, the buses that show up in the table will be limited to only those that are primary nodes. The determination of primary nodes is based on the base case topology. This provides an easy filter to eliminate redundant data.

Generators

  -  *None*calculates no sensitivities for Generators
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the generator Mvar injection to the selected Control Type. When determining this sensitivity, the sensitivity of the total Mvar injection at the generator bus is determined. This total is apportioned to specific generators at a bus based on their proportion of the total Mvar range for the bus. Only generators that are online and on AVR control are included in the calculation.

Branches

  -  *None*calculates no sensitivities for Branches
  - *Sensitivity: dP/dControl (MW/control unit) --\> dP/dControl*gives the sensitivity of the branch MW flow to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the branch Mvar flow to the selected Control Type

Interfaces

  -  *None*calculates no sensitivities for Interfaces
  - *Sensitivity: dP/dControl (MW/control unit) --\> dP/dControl*gives the sensitivity of the interface MW flow to the selected Control Type
  - *Sensitivity: dQ/dControl (Mvar/control unit) --\> dQ/dControl* gives the sensitivity of the interface Mvar flow to the selected Control Type

SimAuto and Script Command Compatibility

The results of the sensitivity analysis can be accessed using script commands or [SimAuto](33-simauto-overview-and-setup.md#automation-server) by using the variable MULTMETERMULTCONTROLSENS with the appropriate metered data object: Bus, Gen, Branch, Interface. There will be as many columns with the MULTMETERMULTCONTROLSENS name and appropriate location number as there are control devices that were studied. There will be as many rows as there are metered data objects. The location numbers start at 0. The results are assigned in the order that the control devices are selected. For example, if the case defines five branches in the following order: 1 to 2, 2 to 4, 4 to 3, 3 to 1, 2 to 3, and branches 2 to 4 and 4 to 3 are selected, MULTMETERMULTCONTROLSENS :0 will correspond to branch 2 to 4 and MULTMETERMULTCONTROLSENS :1 will correspond to branch 4 to 3 for all sets of results.

---

<a id="line-loading-replicator"></a>

## Line Loading Replicator

*Source: [`Content/MainDocumentation_HTML/Line_Loading_Replicator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Line_Loading_Replicator.htm)*

The Line Loading Replicator will attempt to set the loading on a transmission line or interface to a desired real power flow amount. This is accomplished by calculating distribution factors for a selected group of loads and generators to determine how the real power injection of these elements can be adjusted to produce the desired flow. If the desired flow cannot be met, the new flow amount that can be achieved and the injection changes required to meet this flow will be reported. Minimum and maximum MW limits for loads and generators will be enforced when calculating the injection changes.

To open the Line Loading Replicator, go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose ****Line Loading Replicator**** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).

Select Device

**Device Type**

Select whether to adjust the flow on a transmission line/transformer or an interface. All devices must already be defined in the case.

**Device Identifier**

Specify the near bus, far bus, and circuit identifier for a branch or the interface name and number for an interface. Branches will be monitored in the near bus to far bus direction and interfaces will be monitored in the direction in which they are defined to be monitored.

**Present Flow**

Present real power flow on the selected device.

**Desired Flow**

Desired real power flow on the selected device. The difference between the Desired Flow and the Present Flow (Desired Flow – Present Flow) will be the flow change for which injection changes will be calculated.

Available Injection Groups

**Injection Group Identifier**

Specify the injection group name and number that contains the loads and generators whose injection can be changed to reach the Desired Flow. The injection group must already be defined in the case. The injection group definition is used simply for selecting the group of elements to be used in the calculations; the participation factors defined with the participation points in the injection group are not used in the Line Loading Replicator tool.

**Only Include AGCAble Generation and Load**

If checked, only those loads and generators in the selected injection group whose AGC status is *YES* will be included in the calculations.

Calculation Method

Select the method used to calculate the distribution factors used to determine real power injection changes.

Max and Min Load Limits for Injection Changes

**Use Max and Min Load Values**

If checked, the maximum and minimum load values will come from the maximum and minimum values defined with each individual load record.

**Set Max and Min Load Values**

Click this button to show the [Load Records Case Information Display](05-case-information-displays-by-object-part2.md#load-display). The maximum and minimum load values can be defined by displaying the **Max MW** and **Min MW** fields and setting the values as appropriate.

**Use Multiplier on Present Value**

If checked, the minimum and maximum value for each load will be determined by applying the **Min Multiplier** and **Max Multiplier** to the present load value.

Calculate Injection Changes

Click this button to calculate the injection changes required to meet the Desired Flow on the selected device.

Injection Changes

This is a case information display that will provide a summary of the injection changes needed, and the elements that can effect these changes, in order to meet the Flow Achieved on the selected device. The Flow Achieved will differ from the Desired Flow if there are not enough injection changes available to meet the Desired Flow.

The results are reported in terms of injection. For generators, a positive injection means an increase in generator output and a negative injection means a decrease in generator output. For loads, the opposite is true; a positive injection means a decrease in load and a negative injection means an increase in load.

**Injection Change**, **Present Injection**, and **New Injection** fields will be shown by default. These Present Injection and New Injection fields are both calculated based on the present injection of the given element with the New Injection value also being dependent on the Injection Change value. The Present Injection and New Injection values will be updated any time that the present injection for an element changes in the power system. This is important to keep in mind if making any changes to the power flow case while the Line Loading Replicator dialog is open.

Injection changes are calculated so that generator and load limits are enforced. Which load limits are used is determined in the **Max and Min Load Limits for Injection Changes** option settings. The generator limits used are the minimum and maximum limits defined with each generator. These limits can be accessed from the [Generator Case Information Display](05-case-information-displays-by-object-part1.md#generator-display). The load and generator limits can also be displayed in the Injection Changes table by adding the **Min MW** and **Max MW** fields to the table.

Total Injection Increase/Decrease

This value is the amount of injection increase and decrease required to meet the Flow Achieved. The net injection will be zero.

Flow Achieved

Flow amount that can be achieved by implementing the Injection Changes listed. This value will differ from the Desired Flow if there are not enough injection changes available to meet the Desired Flow.

Implement Injection Changes

Click this button to make changes to the power flow case to match the calculated Injection Changes. Automatic generation control (AGC) and phase shifter control are disabled for the entire case when choosing to implement changes.

Implement Injection Changes and Solve Power Flow

Click this button to make changes to the power flow case to match the calculated Injection Changes and then solve the power flow. The power flow is solved with the settings that are specified in the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) specified with [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options). When choosing to implement changes, these options are updated so that automatic generation control (AGC) and phase shifter control are disabled globally for the case. The Present Flow value is updated after the completion of the power flow solution.

---

<a id="lodf-screening"></a>

## LODF Screening

*Source: [`Content/MainDocumentation_HTML/LODF_Screening.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/LODF_Screening.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This tool is found on the [Tools ribbon tab](02-simulator-ribbon.md#tools-tab-overview) in the [Run Mode ribbon group](02-simulator-ribbon.md#run-mode-ribbon-group) under **Sensitivities \> LODF Screening**.

The goal of this tool is to create pairs of contingencies that are significant without actually solving all of the contingencies. The methods are based on the technical paper - C. Matthew Davis and Thomas J. Overbye, "Multiple Element Screening," *IEEE Transactions on Power Systems*, vol. 26, no. 3, pp. 1294-1301, Aug. 2011.

The **Lines to Process (Outage)** and **Lines to Monitor** options determine how the LODFs will be calculated. For each line that is processed as an outage, the impact of that outage (LODF) will be determined for each of the monitored lines. Optionally, LCDFs will be calculated for lines that are open. For brevity, the term *outage* will mean any line that is being processed regardless of its status.

Lines to Process (Outage)

This option determines which lines will be considered as outages when calculating LODFs.

All ac Lines

All branches in the case will be taken as outages.

Defined Contingencies

Branch elements contained in contingencies of action type OPEN or CLOSE will be taken as single outages.

Limit Monitoring Settings

Only branches meeting the limit monitoring settings options for monitoring will be taken as outages.

Use Area/Zone/Owner Filter

Only branches meeting the Area/Zone/Owner filter will be taken as outages.

Use Selected

Only branches where the **Selected** field is *YES* will be taken as outages.

Meets Filter

Only branches that meet the specified advanced filter will be taken as outages.

Lines to Monitor

This option determines which lines will be considered as lines to monitor when calculating LODFs. Only branches that are online are monitored.

Same as Lines to Process

The same set of lines that will be treated as outages will also be monitored.

All ac Lines

All branches in the case will be monitored.

Limit Monitoring Settings

Only branches meeting the limit monitoring settings options for monitoring will be monitored.

Use Area/Zone/Owner Filter

Only branches meeting the Area/Zone/Owner filter will be monitored.

Use Selected

Only branches where the **Selected** field is *YES* will be monitored.

Meets Filter

Only branches that meet the specified advanced filter will be monitored.

Options

The following options will determine how the resulting contingency combinations are determined.

Include Phase Shifters

Checking this option will assume that phase shifters are allowed to operate to maintain their desired flow. This results in no change in flow on a phase shifter due to a line outage, i.e. LODF = 0.

Include Open Lines

Checking this option will include lines that are open as lines to process. This will result in LCDF values being calculated on any open lines.

LODF Threshold

Check this option to use the Impact Tracking Structure (ITS) screening method. The threshold value specifies what is considered a significant LODF during this screening method. The minimum value that can be specified is 1%.

The ITS screening method uses LODFs to determine significant single contingencies for monitored elements based on the magnitude of the LODF. Pairs of significant contingencies are created from single contingencies that impact a single monitored line.

The following example shows how contingency pairs are formed. LODFs are calculated for each of the monitored lines for each of the outages. The monitored lines are indicated by the rectangles on the left. A significant outage is one for which the absolute value of its LODF is greater than the specified LODF Threshold for that monitored line. Each of the CTG bubbles next to a monitored line indicates a line that was processed and results in a significant LODF for that monitored line. New contingency pairs are formed by combining pairs of significant contingencies for each monitored line.

![LODF Screening ITS 626x406](images/LODF_Screening_ITS_626x406.gif)

Overload Threshold

Check this option to use the Outage Tracking Structure (OTS) screening method. The range of values specifies the minimum and maximum range for percent loading of a monitored line. Only outages that cause loadings on the monitored lines within this range are considered significant for a particular monitored line. LODFs and LCDFs are used to determine the loadings on monitored lines. Pairs of significant contingencies are created from significant single contingencies that impact any monitored line and all other outages being studied.

The following example shows how contingency pairs are formed. LODFs are calculated for each of the monitored lines for each of the outages. The monitored lines are indicated by the rectangles on the left. The LODFs are used to calculate the flow on the monitored line during the outage. A significant outage is one in which the loading on the monitored line is within the specified percent loading range. Each of the CTG bubbles next to a monitored line indicates a significant outage. New contingency pairs are formed by combining pairs of significant outages for any monitored line and all other outages being studied. In this example CTG 1 through 6 are studied outages and are combined with each of the significant outages that cause loadings on the monitored lines.

![LODF Screening OTS 620x389](images/LODF_Screening_OTS_620x389.gif)

To calculate the line loadings, Limit Monitoring Settings are used to determine the contingency limit for each monitored line. If a monitored line is part of a multi-section line, the most limiting contingency limit is used for all segments.

To calculate the line flows, contingency DC Method Options that determine whether to calculate based on amps and how to model reactive power are used.

Calculate LODFs

Click this button to do the calculations. The progress bar will show the relative amount of time left in the calculation and the message box will indicating any errors.

File Information

The **File Location** will specify a directory in which an aux file containing the contingency definitions will be saved. Clicking the **Browse** button will open a dialog from which the file location can be selected. A file will be saved at this location with *LODFScreening.aux* as the name. Click the **Save to File** button to actually save the file. Contingencies can only be created by saving them to file.

When naming the contingencies, the [Auto Insert Contingencies](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) options for naming contingencies will be used by default. If the **Use Available Contingency Names for New Contingency Names** option is checked and an outage is part of an existing contingency, the new contingency name will incorporate the name of the existing contingency.

Summary Information

This section is for information only. How many lines to process and monitor are shown. **Number of Combinations without Screening** indicates how many pairs of contingencies would be created if simply combining all studied outages in pairs. **Number of CTG Combinations** indicates how many pairs are determined based on the selected screening options.

Assign Summary to Branch Custom Fields

Information in the **Summary Table** only exists while the LODF Screening dialog is open and cannot be accessed through auxiliary files or script commands. To make this information accessible, it can be saved to custom floating point or custom string fields with Branch records. The branch record to which the information is stored corresponds to the **Contingency Line** specified in the summary table. Use each dropdown to select the custom field to which the corresponding value will be assigned. For **Highest LODF Value** and **Highest Overload Value**, custom floating point fields can be selected. For **Original CTG Name**, **Highest LODF Line** and **Highest Overload Line**, custom string fields can be selected. Click the Populate button to actually assign the values once the fields have been selected.

Summary Table

This table provides information for the highest LODF and highest loading for monitored lines under each outage, **Contingency Line**, that is studied for which a monitored line has a significant LODF or loading. If using the **LODF Threshold** option, the **Highest LODF** field shows the absolute value of the highest LODF greater than the LODF Threshold, and **Highest LODF Line** indicates the monitored line for which this LODF is calculated. If using the **Overload Threshold** option, the **Highest Overload** field shows the highest percent loading between the specified range, and the **Highest Overload Line** indicates the monitored line with this loading.

The **Original Contingency Name** field indicates the contingency from which the single line studied as **Contingency Line** originated. This is only populated if using the **Lines to Process (Outage)** option of **Defined Contingencies**.

The key fields used for identifying objects in this table will change depending on the [Key Fields to Use in Subdata Sections option](10-power-flow-solution-and-options-part2.md#case-information-display-options) specified with Case Information Display Options.
