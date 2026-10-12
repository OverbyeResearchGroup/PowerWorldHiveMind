---
title: "Available Transfer Capability (ATC)"
part: "Add-Ons"
chapter_file: "32-available-transfer-capability.md"
topics: 23
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Available Transfer Capability (ATC)

ATC analysis, the ATC dialog and the ATC solution methods.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (23)**

- [Available Transfer Capability (ATC) Analysis](#available-transfer-capability-atc-analysis)
- [Available Transfer Capability Dialog](#available-transfer-capability-dialog)
- [Options](#options)
- [Common Options](#common-options)
- [Transfer Result Reporting Options](#transfer-result-reporting-options)
- [Advanced Options](#advanced-options)
- [ATC Extra Monitors Dialog](#atc-extra-monitors-dialog)
- [Result](#result)
- [Analysis](#analysis)
- [Multiple Scenario Available Transfer Capability Dialog](#multiple-scenario-available-transfer-capability-dialog)
- [Distributed Computing](#distributed-computing)
- [Scenarios](#scenarios)
- [Results](#results)
- [Local Menu Options](#local-menu-options)
- [Combined Results](#combined-results)
- [Min/Max By Groupings](#minmax-by-groupings)
- [Multiple Directions Available Transfer Capability Dialog](#multiple-directions-available-transfer-capability-dialog)
- [Result](#result-1)
- [Transfer Limiters Display](#transfer-limiters-display)
- [Solution Methods](#solution-methods)
- [Single Linear Step (SL)](#single-linear-step-sl)
- [Iterated Linear Step (IL)](#iterated-linear-step-il)
- [Iterated Linear Step (IL) then Full CTG Solution](#iterated-linear-step-il-then-full-ctg-solution)

---

<a id="available-transfer-capability-atc-analysis"></a>

## Available Transfer Capability (ATC) Analysis

*Source: [`Content/MainDocumentation_HTML/ATC_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Analysis.htm)*

**The ATC Analysis tool is only available if you have purchased the ATC add-on to the base Simulator package. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for details about ordering the ATC version of Simulator.**

Available Transfer Capability (ATC) analysis determines the maximum incremental MW transfer possible between two parts of a power system without violating any specified limits. This transfer can be between two areas in the system and can also be customized to specific groups of system devices.

Simulator’s ATC analysis makes use of several tools that are available elsewhere in Simulator. These include:

  - [Power Transfer Distribution Factors (PTDFs)](20-sensitivities.md#power-transfer-distribution-factors): determine the linear impact of a transfer (or changes in power injection) on the elements of the power system.
  - [Line Outage Distribution Factors (LODFs)](20-sensitivities.md#line-outage-distribution-factors-lodfs): determine the linear impact of a line outage on the elements of the power system.
  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview): studies the impact of a list of contingencies on the power system.
  - [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings): control which elements of the system are monitored for limit violations.

You do not directly use these other tools when using Simulator’s ATC analysis tool, but Simulator uses the settings and algorithms in the background to determine ATC. Thus, it is helpful to be knowledgeable on their use, as it will help you in interpreting the results of an ATC analysis.

  - Simulator provides three methods of determining the ATC for a transfer direction. See : [ATC Solution Methods](#solution-methods)

For information on how to use the Simulator ATC tool, see [Available Transfer Capability Dialog](#available-transfer-capability-dialog).

---

<a id="available-transfer-capability-dialog"></a>

## Available Transfer Capability Dialog

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog.htm)*

The Available Transfer Capability dialog provides an interface for performing and viewing the results of [Available Transfer Capability Analysis](#available-transfer-capability-atc-analysis). ATC analysis is typically only done on the present power system state or scenario (called Single Scenario ATC Analysis). Click [here](#multiple-scenario-available-transfer-capability-dialog) for information on performing [multiple scenarios](#multiple-scenario-available-transfer-capability-dialog) analysis.

To open the ATC dialog, go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **Available Transfer Capability (ATC)** from the **ATC** ribbon tab. The dialog opens to the Single Scenario ATC Analysis version with the Options page, Common Options sub-tab visible. Starting in Version 22 you can also choose to add multiple directions ATC.

![ATC Dialog](images/ATC_Dialog.jpg)

The ATC dialog is divided in three pages: [Options](#options), [Analysis](#analysis), and [Result](#result). If **Analyze Multiple Scenarios** and/or **Multiple Directions** has been checked, the layout of the ATC dialog is slightly different—see [Multiple Scenarios ATC Dialog](#multiple-scenario-available-transfer-capability-dialog) and [Multiple Directions ATC Dialog](#multiple-directions-available-transfer-capability-dialog). There are more options in the [Advanced Options sub-tab](#advanced-options) of the [Options](#options) page.

In addition, the following buttons can be used to save/load ATC analysis settings:

Save/Load Settings

ATC Analysis settings and results can be saved by selecting **Save Settings** on the ATC dialog. This allows you to repeat the analysis without having to reconfigure the settings. Select **Load Settings** to retrieve previously saved settings.

---

<a id="options"></a>

## Options

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_Options_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_Options_Tab.htm)*

The Options page is available on the [Available Transfer Capability dialog](#available-transfer-capability-dialog). This page is subdivided into the following sub-tabs:

![ATC Dialog Options tab](images/ATC_Dialog_Options_tab.jpg)

[Common Options](#common-options)

[Advanced Options](#advanced-options)

Define Contingencies

This sub-tab is similar to the [Contingencies Tab](22-contingency-analysis-options.md#contingencies-tab) of the [Contingency Analysis Dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). The user can insert, auto-insert, define and/or delete contingency records. See [Contingency Analysis](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) for detailed information on defining contingencies.

[Distributed Computing](#distributed-computing)

This tab is available when choosing to study Multiple Directions or Analyze Multiple Scenarios.

Memo

Notes related to the ATC analysis, or anything else for that matter, can be entered on this sub-tab. These notes will be saved to an auxiliary file if choosing to save the ATC settings.

---

<a id="common-options"></a>

## Common Options

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_Options_Common_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_Options_Common_Options.htm)*

The Common Options sub-tab is found on the [Options](#options) page of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

![ATC Dialog](images/ATC_Dialog.jpg)

The following parameters can be set on the Common Options page:

Seller Type, Buyer Type

For the [ATC Solution Method of Single Linear Step (SL)](#single-linear-step-sl), transfer limits can be calculated for transfers between combinations of areas, zones, [super areas](05-case-information-displays-by-object-part1.md#super-area-display), [injection groups](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview), buses, or to the system slack bus. For the iterated linear step ATC Solution Methods ([IL](#iterated-linear-step-il) and [IL then full contingency solution](#iterated-linear-step-il-then-full-ctg-solution)), transfer limits can be calculated for transfers between areas, [super areas](05-case-information-displays-by-object-part1.md#super-area-display) or [injection groups](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview) only. Use the seller type and buyer type options to indicate the type of the selling and purchasing entities.

When using Multiple Directions the top portion of this page is replaced with a case information display that allows the definition of [multiple directions](#multiple-directions-available-transfer-capability-dialog).

Seller, Buyer

Clicking the **Find Seller** and **Find Buyer** buttons allows you to use Simulator’s [Advanced Search Engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics) to locate the desired entities.

The Seller defines where power is injected into the system and the Buyer defines where power is taken out of the system. The transfer is simulated by increasing generation or decreasing load in the Seller and decreasing generation or increasing load in the Buyer. The [ATC Analysis Methods - Solution Methods](#solution-methods) go into greater detail about how the impact of the transfer is actually determined. Depending on the type of Buyer or Seller, different rules apply:

Area, Zone, or Super Area

  - Only on-line generators in the defined group that are on AGC control are allowed to participate in the transfer.
  - Each generator participates in the transfer in proportion to its participation factor.

**Injection Group**

  - Only on-line generators and loads defined with the injection group are allowed to participate in the transfer unless using one of the iterated methods and choosing to use [Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) for either the Seller or Buyer.
  - When using the [Single Linear Step](#single-linear-step-sl) method, on-line buses can be included as part of an injection group. Buses will be ignored for either of the iterated solution methods.
  - Each element participates in the transfer in proportion to the participation factor defined with its [participation point](07-object-properties-run-mode-and-general-part2.md#participation-points-overview) in the injection group.

**Bus**

  - All of the power injection change needed for the transfer comes from that bus.
  - It does not matter if there is a generator or load at that bus.

**Slack**

  - When the slack is selected for the Seller, then all of the power injection change needed for the seller side of the transfer comes from the island slack bus for the island in which the Buyer belongs.
  - When the slack is selected as the Buyer, then all of the power injection change needed for the buyer side of the transfer comes from the island slack bus for the island in which the Seller belongs.

For the [Single Linear Step](#single-linear-step-sl) method, generator and load MW limits are not enforced regardless of the type of buyer and seller unless using the option to [Allow Generator MW Limit Enforcement in Single Linear Step](#advanced-options). Error messages will be displayed if the Seller and Buyer are not both completely contained within the same electrical island.

Reverse Buyer/Seller Button

Click this button to reverse the direction currently shown. The buyer becomes the seller, and the seller the buyer.

Linear Calculation Method

The ATC analysis tool can use either a **Lossless DC** or **Lossless DC with Phase Shifters** calculation method for obtaining the ATC results.

If you select the Lossless DC option, branch flow sensitivity is calculated by estimating the real power that flows through the monitored element only from the difference in angles measured across its terminals.

The Lossless DC with Phase Shifters method, a modification to the lossless dc approximation, takes into account phase shifter operation. It is especially useful when the ATC tool continually reports overloads on branches that obviously will not overload because of the operation of a phase shifting transformer. This method assumes that the phase shifter angles may change to any value to ensure that the line flow on those lines does not change.

The Linearized AC method is not yet available.

Enable Phase Shifters Post-Contingency

This option becomes enabled when you choose the **Lossless DC with Phase Shifters** linear calculation method. It allows you to choose whether or not phase shifter control should be enforced during post-contingency ATC calculations. When this option is checked, it is assumed that phase shifter angles may change to keep the line flow from changing after the contingency has been applied. Otherwise, it is assumed that phase shifters only maintain the flow in the pre-contingency state and the angles do not change in the post-contingency state. Base case (pre-contingency) transfer limiters will still be determined with phase shifters enforced, regardless of the setting of this option when the Lossless DC with Phase Shifters option is checked.

Assumed Location of Injection for Bus

This option is used when calculating PTDFs and one end of the transaction (either Seller or Buyer) is a Bus. Contingencies can outage generators or loads at the transaction bus, and interfaces can contain generator or load outages at the transaction bus. Use this option to modify the location of the injection point so that the generator or load being outaged is the injector rather than the Bus, which in turn will modify the resulting PTDF to reflect this outage. When the transactor is not a Bus, the outage of generators or loads that are contained in the transactor is handled automatically.

The following choices are available for modifying the PTDF results:

Always Bus

This is the default option. No change is made to PTDFs because of generator or load outages at a Bus transactor.

Online Generator

This will take into account the outage of generators that occur at a Bus transactor. Regardless of how many generators there are at a particular bus, if any generator at the transactor bus is outaged, the PTDF will be adjusted to reflect this outage. The impact of load outages at a Bus transactor will not be reflected in the PTDF.

Online Load

This will take into account the outage of loads that occur at a Bus transactor. Regardless of how many loads there are at a particular bus, if any load at the transactor bus is outaged, the PTDF will be adjusted to reflect this outage. The impact of generator outages at a Bus transactor will not be reflected in the PTDF.

Online Gen or Load

This will take into account the outage of generators or loads that occur at a Bus transactor. Regardless of how many generators and loads there are at a particular bus, if any generator or load at the transactor bus is outaged, the PTDF will be adjusted to reflect this outage.

When adjusting PTDFs for generator or load outages, make-up power is used to determine how those outages are balanced. The make-up power specified with contingency analysis is used. One might expect the PTDF to go to zero for the outage of the element used for the assumed injection location for a bus, but this might not be the case depending on the make-up power.

Limit Monitoring Settings Button

Click this button to open the [Limit Monitoring Settings Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). Limiting Elements will only be reported for those elements that are selected to be monitored. Note that minimizing the number of monitored power system elements greatly improves solution speed as well as computer memory requirements for doing ATC Analysis.

[Monitoring Exceptions](22-contingency-analysis-options.md#monitoring-exceptions) can be used to include or exclude specific monitored elements on a contingency-by-contingency basis.

Save Results in PWB File

Check this box to save the ATC results in a PWB file. The settings are always saved.

Transfer Result Reporting Options

The options in this section of the ATC dialog are discussed in detail in the topic on [Transfer Result Reporting Options](#transfer-result-reporting-options).

---

<a id="transfer-result-reporting-options"></a>

## Transfer Result Reporting Options

*Source: [`Content/MainDocumentation_HTML/Transfer_Result_Reporting_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transfer_Result_Reporting_Options.htm)*

These options are found in the Transfer Result Report Options section on the [Common Options](#common-options) sub-tab of the [Options](#options) page found on the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

Transfer Limiters To Save

This value tells Simulator how many total Transfer Limiters to save. Simulator will save those Transfer Limiters with the lowest Transfer Limitation. An explanation of a Transfer Limiter follows:

During Linear ATC Analysis, Simulator determines the Transfer Limitation (See [Available Transfer Capability Analysis](#available-transfer-capability-atc-analysis)) for each transmission line and interface during each contingency and the base case. From this Simulator develops a list of Transfer Limiters. A Transfer Limit contains three key pieces of information:

  - Transfer Limit in MW
  - Limiting Element: Transmission branch (or interface) that causes the limit
  - Limiting Contingency: Contingency that is applied to cause the Limiting Element to overload (if it is a limit without any contingency applied, then the contingency will say *Base Case*)

Thus if we are monitoring 1000 transmission lines during 99 contingencies plus 1 base case, there would be 100,000 Transfer Limiters calculated. We are not concerned with all 100,000 limitations, therefore, only the limitations with the smallest Transfer Limit in MW are reported.

Max Limiters per CTG

When analyzing a long list of contingencies, the worst transfer limitations may all occur during the same contingency. Set this value to limit the number of Transfer Limiters saved that are associated with a given contingency.

Max Limiters per Element

When analyzing a long list of contingencies, the worst transfer limitations may all be overloads of the same limiting element. Set this value to limit the number of Transfer Limiters saved that are associated with a given Limiting Element.

Max MW Limitation

This value defines the maximum transfer to report between the buyer and seller. Simulator will compute the ATC analysis results until the transfer amount reaches the value in this field and only report the results meeting the other reporting criteria up to this MW limitation.

When using one of the iterated methods, this option is only applied during the initial Single Linear Step portion of the method. Once individual limiters are being iterated on, this option will be ignored.

Ignore Elements with OTDFs below

Simulator will only report Transfer Limitations for elements with [OTDF](20-sensitivities.md#line-outage-distribution-factors-lodfs) values greater than this user-specified value. The default value is 0.5%, meaning that for a 100 MW transfer, there would be only a 0.5 MW increase in flow on the Limiting Element. The OTDF cutoff is only used with transfer limitations that include contingencies.

Ignore Elements with PTDFs below

Simulator will only report Transfer Limitations for elements with [PTDF](20-sensitivities.md#power-transfer-distribution-factors) values greater than this user-specified value. The default value is 0.5%. The PTDF cutoff is only used with transfer limitations that do not include contingencies, i.e. base case limitations.

For interfaces that include contingent elements, no additional contingencies will be studied on top of the contingencies that are part of the interface. The cutoff value to use for the OTDF is the minimum of the OTDF and PTDF cutoff values.

The transfer limitation functions involve dividing by the [PTDF](20-sensitivities.md#power-transfer-distribution-factors) or [OTDF](20-sensitivities.md#line-outage-distribution-factors-lodfs) values for each branch or interface to calculate the Transfer Limit. This leads to two facts:

  - The accuracy of the transfer limitation is less for lines that have very small [PTDF](20-sensitivities.md#power-transfer-distribution-factors) or [OTDF](20-sensitivities.md#line-outage-distribution-factors-lodfs) values.
  - A very small [PTDF](20-sensitivities.md#power-transfer-distribution-factors) or [OTDF](20-sensitivities.md#line-outage-distribution-factors-lodfs) value means that the transfer has very little impact on the line.

These two facts often result in Linear ATC analysis reporting inaccurate transfer limitations for lines that are largely unaffected by the transfer. It is not uncommon to have a transfer limitation report an extremely negative transfer limit (e.g. -1.9E28 MW). A branch which is overloaded by a very small percentage, but which has a very small OTDF value often causes this. If the OTDF value is 0.001%, then a branch overloaded by 1 MW will result in a transfer limitation of -100,000 MW.

This motivates the usefulness of ignoring elements with small [PTDFs](20-sensitivities.md#power-transfer-distribution-factors) and [OTDFs](20-sensitivities.md#line-outage-distribution-factors-lodfs).

All of these options work together to determine the list of limiters that shows up in the results. The [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) determine elements that will be considered for monitoring. The [list of defined contingencies](22-contingency-analysis-options.md#contingencies-tab) determines the contingencies. Every combination of monitored elements and contingencies will be tested. [Monitoring exceptions](22-contingency-analysis-options.md#monitoring-exceptions) can also be used to include or exclude monitored elements on a contingency-by-contingency basis. If the PTDF and/or OTDF cutoffs, as appropriate, are met for the monitored element/contingency pair, the monitored element and contingency are then checked against the **Max Limiters per Element** and **Max Limiters per CTG** conditions.

For each monitored element, a maximum, X, of **Max Limiters per Element** is kept during the initial processing. Only the most limiting X limiters for that element are retained. The transfer limiter with the highest transfer limit value will get pushed out of the list for an element if a new combination of monitored element/contingency is more limiting than what is currently in the list. For each contingency, a maximum, Y, of **Max Limiters per CTG** is kept during the initial processing. Only the most limiting Y limiters that for contingency are retained. The transfer limiter with the highest transfer limit value will get pushed out of the list for a contingency if a new combination of monitored element/contingency is more limiting that what is currently in the list. Once all monitored element/contingency pairs have been processed, all of the individual lists for limiting elements and contingencies are merged into one big list that is sorted by transfer limit, limiting element, and contingency. This sorted list is then traversed in the order of increasing transfer limit to create the final list that enforces the **Max Limiter per Element**, **Max Limiters per CTG**, **Transfer Limiters to Save**, and **Max MW Limitation** conditions. If there are no monitored element/contingency pairs that are below the Max MW Limitation, the monitored element/contingency pair with the lowest transfer limit value will be the only record reported in the results.

The following is an example of how this process works:

Max Limiters per CTG = 2, Max Elements per Limiter = 1

Limiting Element Lists

Line A contains transfer limiter for CTG B with ATC = 500

Line B contains transfer limiter for CTG B with ATC = 50

Line C contains transfer limiter for CTG X with ATC = 125

Line D contains transfer limiter for CTG A with ATC = 750

Line H contains transfer limiter for CTG B with ATC = 10

Line Z contains transfer limiter for CTG D with ATC = 10

Contingency Lists

CTG A - Line B with ATC = 1500, Line C with ATC = 1750

CTG B - Line H with ATC = 10, Line Z with ATC = 25

CTG C - Line D with ATC = 1000

CTG D - Line Z with ATC = 10

CTG X - Line C with ATC = 125

Now combine the lists and sort based on ATC, limiting element, and contingency. Duplicate entries can exist in the list because the same limiting element/contingency pair can be stored in both the limiting element list and the contingency list.

10 Line H/CTG B

10 Line H/CTG B

10 Line Z/CTG D

10 Line Z/CTG D

25 Line Z/CTG B

50 Line B/CTG B

125 Line C/CTG X

125 Line C/CTG X

500 Line A/CTG B

750 Line C/CTG A

1000 Line D/CTG A

1500 Line B/CTG A

1750 Line C/CTG A

Now go through the sorted list above to produce the final results list that abides by all conditions.

10 Line H/CTG B

10 Line Z/CTG D

50 Line B/CTG B

125 Line C/CTG X

1000 Line D/CTG A

Include Contingencies Check Box

Check this box to include contingencies (inserted or loaded using the [Contingency Analysis Tool](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)) in the ATC analysis. Note that minimizing the number of contingencies considered greatly improves solution speed as well as computer memory requirements for doing ATC Analysis. Therefore, be careful in choosing which contingencies to use with the ATC tool. Setting the **Skip** field to *YES* for a particular contingency will exclude it from the ATC analysis.

The ATC tool uses the same contingency records as the contingency analysis tool. Contingency results may be invalid following ATC analysis. If necessary, save contingency results to an auxiliary file prior to running the ATC analysis.

Contingency elements have an associated [Status](22-contingency-analysis-options.md#contingency-definition-display) that determines under what conditions a particular action will be implemented. When ATC values are calculated using linear methods, contingency actions are not actually implemented. Because contingency actions are not actually implemented, *POSTCHECK* and *TOPOLOGYCHECK* actions cannot be applied after other actions have been performed and the power flow has been solved. By default, *POSTCHECK* and *TOPOLOGYCHECK* actions act as *CHECK* actions during [linear ATC analysis (Single Linear Step Method)](#single-linear-step-sl). During linear ATC analysis whether or not model criteria are met for *CHECK*, *POSTCHECK*, AND *TOPOLOGYCHECK* contingency actions will be determined at the base transfer level rather than at the transfer level that determines the limiting transfer. The base transfer level is the transfer level at which the linear ATC values are actually determined. In most cases this will be the zero transfer level, but this can be different if using one of the iterated ATC methods.

There [Iterate on Action Status](22-contingency-analysis-options.md#basics) option that can be set with contingency options, will allow conditional actions to be treated more accurately as part of the linear step calculations. Instead of treating all *TOPOLOGYCHECK* and *POSTCHECK* as *CHECK* actions, these actions are processed after other actions have been linearly implemented. See the [Contingency Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis) topic for details on this process.

Report Base Case Limitations Check Box

When checked, the ATC tool will report transfer limitations from the base case (pre-contingency).

Report Generation Reserve Limitations Check Box

When checked, the ATC tool will report transfer limitations from generation reserve.

Generator and load MW limits are not enforced when calculating linear sensitivities used to determine the transfer MW limits. However, checking this option provides an indication of when power transfers are limited based on generator maximum or minimum MW limits or the amount of load that is on-line. When this option is checked and there are limitations to how much power can be transferred because of max/min generator limits or the on-line load, additional Transfer Limiters will be present in the [results](#transfer-limiters-display). The Limiting Element will indicate either the Buyer or Seller and the Transfer Limit in MW will be the amount of transfer that can be achieved before the Buyer or Seller exceeds some limitation to generation or load. When considering reserve limits for the Seller, generators will be included in the reserve limit by taking the difference between the generator maximum MW limit and the present output and loads will be included in the reserve limit by the present amount of on-line load. When considering reserve limits for the Buyer, generators will be included in the reserve limit by taking the difference between the present output of the generators and the minimum MW limit and loads will be included by an arbitrary value of 9999.9 MW. Loads are included in this manner because maximum and minimum limits on loads are not currently used in the ATC tool.

For example, assume than an area that currently has 200 MW on-line and a total maximum MW output of 250 MW for all on-line generators that are on AGC control is defined as the Seller. A 50 MW generation reserve limitation will be reported for this area. As another example, assume that an injection group currently has 50 MW of on-line generation with a total maximum MW output of 150 MW and 50 MW of on-line load is defined as the Seller. A 150 MW reserve limitation will be reported for this injection group.

No generation reserve limitations are reported when the seller or buyer type is a bus or the slack.

If using one of the iterated methods, this option will be ignored except during the first single linear step. Reserve limitations may be reported from this step, but limitations of this type will not be iterated on during the individual iteration process. If choosing to enforce generator MW limits appropriately with the type of transactors that are defined, reserve limits will still be reported, regardless of this option setting, if they are hit during any step of the iterative process when ramping is occurring. See the detailed descriptions of either the [Iterated Linear Step (IL)](#iterated-linear-step-il) or [Iterated Linear Step (IL) then Full CTG Solution](#iterated-linear-step-il-then-full-ctg-solution) method for more information about how reserve limits are checked during the iterated methods.

Use Options for Heatmap from FERC Order 2023

FERC Order 2023 has a requirement for providing heatmap information to allow prospective interconnection customers to see available interconnection capacity. Part of this requirement is to calculate "incremental injection capacity... under N-1 conditions". The ATC tool can be used for the calculation of the incremental injection capacity, given as the Trans Lim value in the ATC results, with the appropriate setting of the Transfer Result Reporting Options within the tool. Checking this option will set the other options appropriately for this calculation.

Using this option assumes the following: Modified in version 23, build on Oct. 10, 2024

  - The**Single Linear Step (SL)** method is the only **ATC Solution Method** that is available
  - **ATC Extra Monitors** are ignored
  - **Limit Monitoring Settings** are used to determine which lines are monitored
  - Interfaces are not monitored
  - **Include Contingencies** is always checked
  - For a line to be reported while including a contingency it must have an OTDF above the **Ignore Elements with OTDFs below** threshold
  - **Report Base Case Limitations** can optionally be checked to include base case limits
  - For a line to be reported as a base case limit it must have a PTDF above the **Ignore Elements with PTDFs below** threshold
  - The option to **Report Generation Reserve Limitations** is not used
  - **Max Limiters per Element** is used to specify the number of times a particular Limiting Element can appear in the results
  - Only the limiters with the lowest **Trans Lim** values will appear in the results
  - There is no limitation on how many times a particular contingency can appear in the results and **Max Limiters per CTG** is assumed infinite
  - **Transfer Limiters to Save** specifies how many total results will be available
  - **Max MW Limitation** specifies the maximum **Trans Lim** value that will be reported

The **ATC Min Trans Lim** field with a bus can be used to define a contour representing the heatmap. This field shows the minimum **Trans Lim** value of the transfer limiters calculated for the transfer direction with the respective bus as the Source. Multiple Directions calculations must be used for this field to be populated. The Sink of the transfer direction does not matter, but only a single transfer direction for each bus can be defined.

---

<a id="advanced-options"></a>

## Advanced Options

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_Options_Advanced_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_Options_Advanced_Options.htm)*

The Advanced Options sub-tab is found on the [Options](#options) page of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

![ATC Dialog Advanced Options](images/ATC_Dialog_Advanced_Options.gif)

The following parameters can be set on the Advanced Options sub-tab:

ATC Solution Method

One of the [solution methods](#solution-methods) for determining the ATC of a specified transfer direction.

If using either the Iterated Linear Step (IL) or (IL) then Full CTG Solution method, and the seller and buyer are either areas or super areas, and the automatic generation control method for the case is not set to area/super area control, an error message will be produced and the analysis will not continue. In the ATC analysis, transfers between areas are implemented by adding a transaction between areas which requires them to be on area interchange control in order to meet the ACE requirement. If the case was just switched to this control method without the areas already being on area control, the dispatch for the case could drastically change. The burden is left on the user to ensure that control methods are set up correctly. If the case is not already on area interchange control, but one of the island-based methods, and putting it on area control would drastically change the case, the ATC analysis can still be done between areas if injection groups are created to represent the areas and the analysis is then done using these injection groups as the seller and buyer.

Linearize Makeup Power Calculation

When doing the linear ATC calculations, any contingencies that cause a MW change (e.g. dropping generation or changing load) require makeup power to compensate for the change in MW. When this option is checked, a precalculation is done at the beginning of each linear step calculation that determines the impact of makeup power on line flows. When a particular contingency is processed, the effect of makeup power on all monitored lines will be determined by multiplying the precalculated effect of makeup power on a line by the total amount of makeup power needed for the contingency. This calculation is slightly faster than calculating the impact of the makeup power separately for each contingency, but it will not take into account the fact that larger amounts of required makeup power may cause generators to hit their limits.

Define Extra Monitors

Simulator’s ATC tool determines the maximum amount of MW transfer between the seller and buyer. If you would like to also determine the flow on additional lines or interfaces at the transfer levels determined by the ATC tool, you can utilize Extra Monitors. Click the **Define Extra Monitors** button to open the [ATC Extra Monitors dialog](#atc-extra-monitors-dialog). The flow on the extra monitors will be reported for each transfer limiter determined.

Analyze Multiple Scenarios

Check Analyze Multiple Scenarios to perform ATC Analysis on several scenarios. See [ATC Dialog for Multiple Scenarios](#multiple-scenario-available-transfer-capability-dialog) for more information on Multiple Scenario Analysis.

Model Reactive Power for Linear Methods By…

The linearized methods used in the ATC tool are based only on the changes in real power MW in the system, thus an assumption needs to be made about the reaction of the Mvar flows during the linear calculations. The chosen assumption allows a MW limit to be calculated from the defined MVA limit for use in determining the ATC values. Before applying the option for handling reactive power, the specified MVA limit for a branch is used to determine the starting MVA limit. The [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog) can cause an adjustment the defined MVA limit based on the **Branch Percentage** specified. The modified limit that is used in the calculations is then:

*![ATC Equation1](images/ATC_Equation1.jpg)*

The choices for adjusting the MVA Limit for reactive power are then:

**Ignoring** **** **reactive** **** **power** – reactive power is completely ignored. The MW limit of a line is assumed to be the modified MVA limit of the line:

![ATC Equation2](images/ATC_Equation2.jpg)* *

**Assuming** **** **constant** **** **voltage** **** **magnitude** – reactive power is adjusted to hold voltage magnitudes constant. This option uses the intersection of a branch's operating circle and limiting circle to adjust the limit. The operating circle defines a circle of valid MW and Mvar values for a branch as a transfer takes place across the system. The limiting circle has a radius equal to the modified MVA limit of the branch.

**Assuming reactive power does not change** – reactive power is held at pre-ATC solution levels. The MW limit for each line is calculated from the MVA limit and the reactive power at the pre-ATC solution level:

*![ATC Equation3](images/ATC_Equation3.jpg)*

For Linear Methods, Allow Amp Limits by Assuming a Constant Voltage Magnitude

If checked, Simulator will allow converting MVA limits to Amp limits by assuming constant voltage magnitudes based on the base case full AC load flow operating point just prior to the ATC linear calculations. This option will only be used if the [Limit Monitoring Settings Option of Treat Line Limits as Equivalent Amps](18-general-tools.md#limit-group-dialog) is checked.

This option will cause the ATC tool to internally use a modified MVA limit which is equal to the user-specified MVA rating multiplied by the actual terminal voltages of the line. This results in a modified MVA rating which is higher than the user-specified MVA rating when the voltage on the line is higher than nominal and lower when the voltage is lower than nominal. For purposes of calculating the ATC values, a MW limit is determined from the MVA rating based on how this option is set and how the reactive power is modeled.

**Ignoring reactive power**

*![ATC Equation4](images/ATC_Equation4.jpg)*

**Assuming reactive power does not change**

*![ATC Equation5](images/ATC_Equation5.jpg)*

where *V* is the voltage at the end of the branch from which the limit is taken. The Transfer Limit is calculated at each end of a branch and the most limiting value is reported as the Transfer Limit for a given branch.

Allow Generator MW Limit Enforcement in Single Linear Step

If checked and all of the other relevant options that must be specified to enforce generator MW limits depending on the Seller and Buyer types are set, only generators that are not already at their limits are allowed to participate. For the Seller, generators that are at their maximum limit will not participate. For the Buyer, generators that are at their minimum limit will not participate. If using a injection group for the Seller or Buyer the options to allow only AGC units to vary and not allow negative loads will also be enforced.

This option applies when using the [Single Linear Step](#single-linear-step-sl) method either as a standalone method or part of one of the iterated methods. When using the Economic Merit Order Dispatch method with injection groups, limits will be enforced regardless of this option setting provided that all other options necessary to enforce limits are also set appropriately.

Iterate on Action Status (Do NOT Treat All Status As Check)

This option affects how conditional actions are modeled with contingencies when using linear analysis. This is an option is specified with contingency options, but is available here because it impacts the ATC results. See the [Contingency Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis) topic for details.

Transfer Calculation Options

The Transfer Calculation Options section is disabled if the [Single Linear Step](#single-linear-step-sl) Solution Method is selected.

Transfer Tolerance

This is the tolerance used during the [Iterated Linear Step](#iterated-linear-step-il) or [(IL) then Full CTG Solution](#iterated-linear-step-il-then-full-ctg-solution) methods. The iterated methods will finish if the transfer step amount for the next iteration is less than this tolerance. The default is 10 MW.

When Iterating, Ignore Limiters below

The iterated techniques perform additional analysis on individual transfer limitations in the order of increasing Transfer Limit in MW. When using one of the iterated techniques, transfer limitations with Transfer Limit values below a certain threshold can be ignored for the iterated portion of the process. Transfer limitations with Transfer Limit values equal to or below the value set with this option may still appear in the results, but they will not be iterated on individually.

Once an individual limiter is being iterated on, this value will no longer be used. This means that during the individual iteration process, the transfer level for a limiter can fall below this threshold.

Transfer Limiters to Iterate on

This is the number of transfer limiters to iterate on in the [Iterated Linear Step](#iterated-linear-step-il) or [(IL) then Full CTG Solution](#iterated-linear-step-il-then-full-ctg-solution) methods. The default is 1. The transfer limiters actually iterated on are determined by selecting the number of limiters set in this option in ascending order of Transfer Limit with the Transfer Limit at or above the value set in the **When Iterating, Ignore Limiters below** option.

Power Flow Solution Options

This button brings up the [Power Flow Solution Options Dialog](10-power-flow-solution-and-options-part1.md#power-flow-solution-options). This allows the specification of the solution options to use for solving pre-contingency cases and the options used when no contingency-specific solution options are defined. Changing these options affects all power flow computations, even those outside the ATC process.

Because the goal is to stress the system while performing the ATC analysis, there are two power flow solution options that are set internally as part of the ATC process. These are the options that specify the minimum per unit voltage for constant power and constant current loads. These options are both set to 0 pu and override any user-specified settings.

![PV Setup Common Options Min PU Volt](images/PV_Setup_Common_Options_Min_PU_Volt.jpg)

These options are both set to 0 pu during both the base case solution and any contingency case solution.

Injection Group Options

This button brings up a dialog from which options associated with injection groups can be set. These are the same options that get set for injection groups when using [Island-based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) and dispatching using an injection group except for two additional options; the ATC process switches to using an island-based AGC when iterating and using injection groups for the seller and buyer. The options that can be set are **Island AGC Tolerance**, **Allow only AGC units to vary**, **Enforce unit MW limits**, **Do not allow negative loads**, and how reactive power load should change as real power load is changed.

The buyer injection group is set as the injection group to use in the dispatch. When implementing the transfer ramping, the source injection group is ramped to the required amount and then the power flow is solved with the buyer injection group picking up any required changes. These changes include adjusting injection in response to change in the seller injection group as well as any changes in losses due to the transfer.

**Ramping Method**Modified in version 19, build on Aug. 4, 2016

Different ramping methods can be set independently for the Seller and Buyer.

**Proportional**

The MW output for generators and loads in the injection group will be adjusted in proportion to their specified participation factors. These factors will be normalized for all generators and loads participating in the dispatch. Mvar load will be adjusted according to the options used for setting how reactive power load should change as real power load is ramped.

**Economic Merit Order**

This method involves dispatching generators so that they are dispatched within an economic range. Details about how economic merit order dispatch is performed can be found under the [Generator Economic Merit Order Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the loads will be adjusted in proportion to their participation factors and economic merit order dispatch will not be used.

**Merit Order Close** Added in version 19, build on Aug. 4, 2016

This method will dispatch generators in a merit order determined by their specified participation factors. Economic generator limits will be enforced during this process regardless of how the **Enforce unit MW limits** option is set. Details about this method can be found under the [Generator Merit Order Close Dispatch](52-additional-linked-topics-part1.md#generator-economic-merit-order-and-merit-order-close-dispatch) topic.

If using this option and an injection group contains ONLY loads, the loads will be adjusted in proportion to their participation factors and merit order close dispatch will not be used.

During the linear step portion of the iterated methods when using one of the merit order ramping methods, only generators will be included in the linear PTDF calculations. Only online generators in the Buyer injection group will be allowed to participate if the Buyer is using one of the merit order dispatch methods. If the Seller injection group is using one of the merit order dispatch methods, all generators in the injection group will be allowed to participate in the linear calculation as long as they are online or could be energized by closing breakers. When using the proportional method, only online generators in either the Seller or Buyer injection group are allowed to participate.

Injection groups have their own set of options that can override the options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

Define Contingency Solution Options

Click this button to open the [Contingency Solution Options Dialog](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options). These are the same options that are set with the contingency analysis options.

Use Specific Solution Options

When checked, the ATC tool will use the solution options defined by pressing the **Define Contingency Solution Options** button for contingency analysis. When not checked, all solutions will use the options defined by pressing the **Power Flow Solution Options** button.

Regardless of the specific contingency solution option settings, there are two options that will be set internally by the ATC process and will override any user-specified settings. These are the options for minimum per unit voltage for constant power and constant current loads. These options are described in more detail in the Power Flow Solution Options section above.

Force all transfer ramping to occur in pre-contingency states and repeat full CTG solutions

When using the iterated solution methods, the typical iterated operation is to solve for the transfer step amount in the post-contingency state, and then apply the transfer step amount to the post-contingency state and resolve for the next transfer step amount. When this option is checked, the transfer step amount for each iteration is calculated in the post-contingency state, but the power flow state is restored to the pre-contingency state before the transfer step amount is applied. The contingency is then applied after the transfer step amount has been ramped and the transfer step amount for the next iteration is calculated after the contingency has been applied. The purpose of this is to take into account the possibility of conditional actions in the contingency definitions that may not be active in the early steps of the iterated calculations, but may become active at some point during the application of the iterated steps.

Iterate on failed contingency

This option is only enabled when the option to **Force all transfer ramping to occur in pre-contingency states and repeat full CTG solutions** is selected. When this option is checked and the power flow fails to solve after the contingency has been applied, a new iteration loop is entered to determine the highest transfer level at which the contingency can be solved. This loop attempts to determine a more accurate transfer level at which the contingency fails to solve rather than simply reporting the transfer level at which the last power flow was successful regardless of the current step size. To start the iterative process, the current step size is reduced by half. The ramping is performed and the contingency is solved. The step size will remain the same as long as the contingency can be solved. If the contingency fails to solve, the step size will be reduced by half again. The ramping will continue until the contingency no longer solves, the accumulated transfer during the process meets the original step size, or the step size becomes smaller than the step size tolerance.

An additional check is done during the iterative process on the failed contingency. When the contingency does solve, the flow on the monitored element is checked to determine if it exceeds its limit. If it is overloaded, the step size will be reduced by half until the monitored element is no longer over its limit. While this check is being done on the monitored element limit, the ramping continues out to the specified amount and the contingency is solved.

During the entire iterative process on a failed contingency solution, the step size is limited to be between zero and the step size which was ramped when the contingency failed to solve for the first time.

Tolerances in ATC Tool

When using one of the iterated methods, tolerances must be set correctly with the ATC tool or injection changes will end up being picked up by the system slack instead of the seller and buyer or no injection changes will be made at all. When studying a transfer between injection groups, the **Transfer Tolerance** will dictate what the **MVA Convergence Tolerance**, set with the [Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options) on the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), and the **Island-Based AGC Tolerance** can be. Before the analysis starts, the MVA Convergence Tolerance will be checked to make sure that it is less than 0.1\*(Transfer Tolerance). If not, the MVA Convergence Tolerance will be set to 0.1\*(Transfer Tolerance). The Island-Based AGC Tolerance will also be checked to make sure that it is less than 0.5\*(Transfer Tolerance). If not, the Island-Based AGC Tolerance will be set to 0.5\*(Transfer Tolerance). The MVA Convergence Tolerance will then be checked to make sure that it is less than 0.2\*(Island-Based AGC Tolerance). If not, the MVA Convergence Tolerance will be set to 0.2\*(Island-Based AGC Tolerance). This will order the tolerances such that (MVA Convergence Tolerance) \< (Island-Based AGC Tolerance) \< (Transfer Tolerance). The original tolerances will be restored when the initial state stored with the ATC tool is restored.

When studying a transfer between areas or super areas, there are two AGC tolerances to deal with. These are both checked to make sure that they are less than 0.5\*(Transfer Tolerance) and are set to that value if they are not. Both of these tolerances should also be greater than the MVA convergence tolerance. The smaller of the two tolerances in multiplied by 0.2 and the MVA convergence tolerance must be less than this value. If not, the MVA convergence tolerance is set to 0.2\*(smaller of the two area/super area AGC tolerances). All tolerances will be restored to their original values when the initial state stored with the ATC tool is restored.

---

<a id="atc-extra-monitors-dialog"></a>

## ATC Extra Monitors Dialog

*Source: [`Content/MainDocumentation_HTML/ATC_Extra_Monitors.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Extra_Monitors.htm)*

Simulator’s ATC tool determines the maximum amount of MW transfer between the seller and buyer. If you would like to also determine the flow on additional lines or interfaces at the transfer levels determined by the ATC tool, you can utilize ATC Extra Monitors. To open the Extra Monitors dialog, click the **Define Extra Monitors** button on the [Advanced Options](#options) tab of the ATC Analysis Dialog.

The ATC Extra Monitors Display lists all of the ATC Extra Monitors defined. This list display is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays), and therefore has the same functionality as other common displays. See **Adding and Removing Extra Monitors** below.

![ATC Extra Monitors1](images/ATC_Extra_Monitors1.gif)

Extra Monitors Dialog

The default fields shown on this display are:

ATC ExMon Desc

This is a description of the monitored value. Presently, this is always MW flow.

ATC ExMon Obj

The power system element that is being monitored. This will be either a transmission branch or an interface.

Monitor Limit

This is the MW limit of the element being monitored.

Relative Monitor

Set this to a positive value to further filter the Transfer Limitations reported on the [Transfer Limiters Display](#transfer-limiters-display). By default, Relative Monitor is set to *none*, and no additional filtering of limitations is performed. If this value is greater than zero, only Transfer Limitations that meet the following condition are included in the results.

![ATC Extra Monitors2](images/ATC_Extra_Monitors2.gif)

This provides a measure of how much an interface or branch is affected by the transfer relative to its MW limit.

The relative monitor sensitivity check is not done if using one of the [iterated ATC methods](#solution-methods) and in the process of iterating on individual limiters. The assumption is that once a limiter meets the initial check and it is being iterated on that the limiter should be kept regardless of its relative monitor sensitivity.

Adding and Removing Extra Monitors

To delete an Extra Monitor, right-click on the desired record on the list display and select **Delete**.

To insert an Extra Monitor, right-click on the list display and select **Insert**. This opens the insert dialog.

Insert Extra Monitors Dialog

![ATC Extra Monitors3](images/ATC_Extra_Monitors3.gif)

Choose whether you want to monitor an Interface or Line MW flow. Next choose the interface or branch to be monitored. Note that the insert dialog allows the use of Simulator’s [advanced search engine](04-model-explorer-and-case-information-part3.md#find-dialog-basics) and filtering techniques to aid in locating the desired interface or branch. Click **OK** to insert the record.

---

<a id="result"></a>

## Result

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_Result_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_Result_Tab.htm)*

The Result page is found on the [Available Transfer Capability dialog](#available-transfer-capability-dialog). This page is visible when performing ATC analysis on a single system state, i.e., not analyzing Multiple Scenarios. The Result page consists of two sections: a [Transfer Limiters Display](#transfer-limiters-display) and a [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display).

![ATC Dialog Result Tab](images/ATC_Dialog_Result_Tab.png)

The Transfer Limiters Display contains tabbed pages containing information on Branch, [Interface](07-object-properties-run-mode-and-general-part2.md#interface-information), and [Nomogram](05-case-information-displays-by-object-part3.md#nomogram-display) Limiters. The user can also choose to display All Limiters. See [Transfer Limiters](#transfer-limiters-display) for more information.

The Contingency Definition section displays information on the limiting contingency for selected transfer limiter if the user checked **Include Contingencies** on the [Common Options](#common-options) tab.

---

<a id="analysis"></a>

## Analysis

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_Analysis_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_Analysis_Tab.htm)*

The Analysis page, found on the [Available Transfer Capability dialog](#available-transfer-capability-dialog), is used to control the analysis process. The scrollable window displays a record of user-initiated actions relating to the analysis.

![ATC Dialog Analysis Tab](images/ATC_Dialog_Analysis_Tab.gif)

The Analysis page has the following controls:

Start Analysis

The **Start Analysis** button begins the ATC Analysis using the settings and options defined by the user in the ATC Analysis Dialog. Progress of the ATC Analysis is shown in the scrollable pane of the ATC dialog – Analysis page window. Note that you can still interact with other features of Simulator when the ATC dialog is open, and care must be taken while actually running the ATC solution, as any changes to the data while the ATC solution is calculating will invalidate the results.

Abort Calculation

When using one of the iterative ATC Solution Methods, or while analyzing Multiple Scenarios, click this button to abort the calculation.

Note: This does not immediately abort the solution. Simulator must restore the system state before completing the abort. Also, after aborting the solution, it should be assumed that the results are not valid. The exception could be if multiple scenarios have fully completed before hitting the abort button. Any study or scenario in progress when Abort is clicked should definitely be considered not valid.

Store Initial State

Click this button to store the initial state. The initial state is the state in memory when the ATC analysis is started. If an initial state has not already been stored, the initial state is stored automatically when doing analysis that requires a full ac power flow solution such as using one of the iterated ATC Solution Methods, analyzing Multiple Scenarios, or manually ramping a transfer. If an initial state has already been stored, this state is restored before doing any analysis for iterated methods or multiple scenarios. When manually ramping a transfer, the initial state is not restored automatically. When the ATC dialog is opened after an initial state has already been stored, the user will be prompted about updating the initial state to the state in memory or keeping the existing initial state. If the dialog is not closed and changes are made to the case that need to be reflected in the ATC analysis, the Store Initial State button will allow setting the initial state to override any stored state in memory.

Restore Initial State

Click this button to restore the system state to the initial state. The initial state is the state in memory when the ATC analysis is started and is restored at the end of analysis. The initial state is stored if using one of the iterated ATC Solution Methods or analyzing Multiple Scenarios, opening the ATC dialog if an initial state has already been stored, or when manually using the button to Store Initial State.

Increase Transfer

Click this button to open the Ramp Transfer Up dialog in order to increase (or decrease) the transfer level manually. This transfer remains in the system state if the dialog is closed without restoring the initial state.

Additional analysis can be done on a case that has had the transfer increased by using the ATC tool; however, the control method used in the ATC tool may differ from that in use once the ATC tool has been exited. When injection groups are used to increase the transfer, the AGC method that is used is island-based AGC. The AGC method is then restored to what it was prior to increasing the transfer. If this same method is not used for subsequent analysis, the dispatch and system state will be modified from the state with the transfer applied. When using areas or super areas for increasing the transfer, the area or super area is put on participation factor control for the ramping. Areas/super areas participating in the transfer will remain on participation factor control following the ramping, but the same problem can exist as with the injection groups if the same AGC method is not in use with subsequent analysis after the transfer ramping.

If using areas or super areas for increasing the transfer, a transaction is added to the [MW Transactions](05-case-information-displays-by-object-part3.md#mw-transactions-display) to implement the transfer. This transaction can be identified by the special ID that is assigned to it, *TEMP\_ATC\_TRANSACTION*. This transaction will remain in the case if closing the ATC dialog without restoring the initial state.

When increasing the transfer, the rules for the various tolerances involved in the transfer and power flow solution described in the **Tolerances in ATC Tool** section described in the [Advanced Options](#advanced-options) topic apply. The only exception is that the original tolerances are not restored at the end of the transfer increase because the initial state is not restored.

---

<a id="multiple-scenario-available-transfer-capability-dialog"></a>

## Multiple Scenario Available Transfer Capability Dialog

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_Available_Transfer_Capability_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_Available_Transfer_Capability_Dialog.htm)*

To perform [Available Transfer Capability Analysis](#available-transfer-capability-atc-analysis) for several system scenarios, check **Analyze Multiple Scenarios** on the **Advanced Options** tab of the [Available Transfer Capability dialog](#available-transfer-capability-dialog). When Analyze Multiple Scenarios is not checked, the available pages are [Options](#options), [Analysis](#analysis) and [Result](#result). When Analyze Multiple Scenarios is checked then the following changes occur:

  - [Distributed Computing](#distributed-computing) page appears
  - [Scenarios](#scenarios) page appears
  - [Results](#results) page appears
  - Result page is removed (replaced by Results)
  - [Combined Results](#combined-results) page appears

![ATC Multiple Scenarios Dialog](images/ATC_Multiple_Scenarios_Dialog.jpg)

By defining multiple scenarios, Simulator allows you to calculate ATC values for several different power system states automatically. Scenarios can be modified along three axes:

  - Line Rating/Load Scenarios (weather-related scenarios)
  - Generation Scenarios (generation profiles)
  - Interface constraints

See [Scenarios](#scenarios) page for more information.

---

<a id="distributed-computing"></a>

## Distributed Computing

*Source: [`Content/MainDocumentation_HTML/ATC_Dialog_DistributedComputing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Dialog_DistributedComputing.htm)*

**The Distributed Available Transfer Capability tool is available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for more details.****

These options are all available on the [Available Transfer Capability Dialog](#available-transfer-capability-dialog) under the Distributed Computing Grouping.

Distributed Computing is available for use in distributing [multiple scenario ATC simulations](#multiple-scenario-available-transfer-capability-dialog) and [multiple directions ATC simulations](#multiple-directions-available-transfer-capability-dialog). In order to use distributed computing you must first configure a list of remote computers which can be utilized along with appropriate authentication information for those computers. The computer list and authentication information is common to all the distributed computing tools in Simulator and can be found in the [Simulator Options Dialog](10-power-flow-solution-and-options-part1.md#simulator-options), or reached with the Distributed Computing Options button. They are described in [Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)[ ](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons).

The options to specify to ATC Analysis for Distributed Computing are the following:

Use Distributed Computing

Check this box to signify that when processing [multiple scenario ATC simulations](#multiple-scenario-available-transfer-capability-dialog) and [multiple directions ATC simulations](#multiple-directions-available-transfer-capability-dialog) distributed computing should be used.

Number of Directions per Process

Select the number of directions per process when [multiple directions ATC simulations](#multiple-directions-available-transfer-capability-dialog) distributed computing is used.

---

<a id="scenarios"></a>

## Scenarios

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Scenarios_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Scenarios_Tab.htm)*

The Scenarios page of the Multiple Scenario ATC Analysis is available on the [Available Transfer Capability Dialog](#available-transfer-capability-dialog) when selecting the option to **Analyze Multiple Scenarios** on the [Advanced Options](#advanced-options) tab of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

By defining multiple scenarios, Simulator allows you to calculate ATC values for several different power system states automatically. Scenarios can be modified along three axes:

  - Line Rating/Load Scenarios (weather-related scenarios)
  - Generation Scenarios (generation profiles)
  - Interface constraints

![ATC Multiple Scenarios Dialog](images/ATC_Multiple_Scenarios_Dialog.jpg)

Each of the different scenario types can be defined on its own tab. Each tab contains a list of the power system elements that will be modified during different scenarios. These lists are a familiar [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) providing the same functionality as other displays.

To insert a new power system element into the list, right-click on the list (below the headings) and choose **Insert**.

If a power system element does not show up in one of the lists of elements for a particular scenario, then it will retain its base case value during that scenario.

When saving or loading scenario elements in an auxiliary file, the elements are usually identified by primary key fields. Optionally, these elements can be identified by label. See the [Label](07-object-properties-run-mode-and-general-part2.md#labels) topic for more information about this.

Line Ratings/Loads Tab

Use this tab to define Line Ratings, Zone Loads, and InjectionGroup Load scenarios.

Line Ratings, Zone Loads, and InjectionGrup Loads are varied together when analyzing scenarios. This was chosen because they often vary together as a function of the weather. Notice that four sub-tabs (labeled Line Ratings A, Line Ratings B, Zone Loads, and InjectionGroup Loads) appear at the top of the Line Ratings/Loads tab.

Line Ratings A and B

The A rating is typically used as a base case rating, whereas the B limit is typically used as a line rating under contingency. The way line ratings are utilized is defined in [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).

A checkbox, **Only Monitor Scenarios Limits**, appears on both of these sub-tabs. Check this box to override the normal Limit Monitoring Settings and monitor only the lines that are defined as part of either the Line Ratings A or Line Ratings B lists. When this option is in use, rating A will be used for base case limitations, and rating B will be used for contingency limitations. If a line is not in both lists, the rating that is specified will be used for both base case and contingency limitations. During the ATC calculations, Limit Monitoring Settings will be modified internally to only monitor the specified lines. Once the analysis is complete, the Limit Monitoring Settings will be their original settings.

Zone Loads

The Zones sub-tab has additional options used to specify how Mvar load should vary as the MW load is updated. Only MW load is specified in the scenarios. To specify how the Mvar load should vary, select either **Assume Constant Power Factor** to have the Mvar load vary with the MW by the same power factor that exists in the base case or **No Change in Mvar** to keep the Mvar load constant.

When determining how zone loads should be modified during each scenario, the AGC status of each load is used to determine how the MW portion of the load should be modified. For each zone to be modified, the Total MW load for all connected loads in the zone is determined regardless of AGC status. The Total AGC MW load for all connected loads in the zone is determined for only those loads where AGC = YES. If Total AGC MW \> 0 then only those loads where AGC = YES will be modified. The multiplier for load changes becomes, multiplier = 1 + (Load MW Change)/(Total AGC MW). If Total AGC MW = 0, all loads in the zone will be modified during the scenario regardless of the AGC status and the multiplier becomes multiplier = 1 + (Load MW Change)/(Total MW). Load MW Change is determined by taking the new MW load value specified with the scenario and subtracting off the Total MW, (Load MW Change) = (New MW Load Value) - (Total MW). If Total MW = 0 meaning that there is presently no connected load in the zone, no load changes will be made. If Total AGC MW \> 0, only those loads where AGC = YES that are in-service will be modified with the new MW load at each load becoming the present MW load multiplied by the multiplier (1 + (Load MW Change)/(Total AGC MW)). If Total AGC MW = 0, all loads that are in-service will be modified with the new MW load at each bus becoming the present MW load multiplier by the multiplier (1 + (Load MW Change)/(Total MW)).

InjectionGroup Loads Added in version 24

When scaling by InjectionGroup, only load objects participation points will be scaled. The scaling will be done following the methods described in the [Scaling](18-general-tools.md#scaling) topic under the InjectionGroup heading. The ATC tool will use three fields specified with an InjectionGroup if the InjectionGroup field **ScaleOverrideToolOptions** = YES. These fields for an InjectionGroup are under the Scale folder in the InjectionGroup list of fields and the parameters important for the ATC tool InjectionGroup Load scaling are as follows

**ScaleEnforcePosLoad**: Set to YES so that load MWs must always be positive.

**ScaleOnlyAGC**: Set to YES so that only loads which have a field of AGC=YES will be moved.

**ScaleUseConstantPowerFactor**: Set to YES to scaled reactive power by the same factor as the real power to maintain a constant power factor.

If the InjectionGroup field **ScaleOverrideToolOptions**=NO, then the ATC tool option mentioned above for Zone Loads regarding **Assume Constant Power Factor** or **No Change in Mvar** will be used to determine how to change Mvars. The choice for OnlyAGC and EnforcePosLoad will obey the options regarding Island-Based AGC on the [Power Flow Solution: Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) options on the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Creating both Zone Load and InjectionGroup load scenarios that have an overlap in the Load objects is highly discouraged. Also specifying multiple InjectionGroups that have overlapping Load participation points is discouraged. The ATC tool will make no attempt to harmonize these scaling requests and results will be confusing.

Generator Outputs Tab

Use this tab to define scenario changes for generator MW output. Specify a zero output to take a generator off-line. Specifying a non-zero output will force the status of the generator to be closed, meaning that a generator that is currently off-line can be brought on-line during a scenario. The AGC status of a scenario generator will be set to NO so that any changes made via a scenario will not be undone by any automatic generation control schemes. If the bus to which the generator is connected is not in-service, simply changing the generator status to closed will not put the generator in-service. If the case has breakers defined, an attempt will be made to ensure that a generator is truly in-service by closing any open breakers that would cause it to be out-of-service. This is done whenever breakers have been defined in the case. Transmission branches can be identified as breakers by using the **Branch Device Type** field on the [Line and Transformers Display](05-case-information-displays-by-object-part2.md#line-and-transformer-display).

Interface Ratings Tab

Use this tab to define scenario changes for interface MW ratings.

Applying Scenarios

When scenarios are applied, all of the changes specified in the scenario are not applied at once. Generator and load changes that cause injection changes will force the power flow to solve if the injection change exceeds a certain threshold. Currently this threshold is 500 MW. Changes will accumulate until this condition is met and then the power flow will be solved. If the power flow fails to converge at any point during this process, the process for making changes for that type of scenario change is aborted, e.g. if there are 10 load changes to be made and accumulated change for the first 5 changes exceeds 500 MW the power flow is solved. If it fails to converge, the changes for the last 5 load changes will not be applied. The system state that remains will not be a state that contains all of the changes for the scenario. Over all scenario types changes are applied in the following order: Line Rating A, Line Rating B, Generator, Load, and Interface. The power flow will only be applied for the changes that affect injection, i.e. generators and loads. If the power flow fails at any step during this process, the remaining changes will not be applied.

The Scenarios page has these additional controls:

Number of Defined Scenarios per Element Type

On each tab, you may enter how many different scenarios should be defined for that kind of power system element. For instance if you set Generation Scenarios to 5, then list display on the Generation Tab will provide 5 columns labeled G0, G1, G2, G3, and G4. Generation outputs should then be entered into each cell representing the generation output in each scenario.

Total Scenarios

Once you have specified the scenarios, Simulator is able to perform ATC Analysis on every combination of the axes. For example, assume you have the following:

  - 10 sets of line ratings and zones load
  - 8 sets of generation profiles
  - 3 interface constraints

This yields a total of 240 different scenarios to calculate (10\*8\*3 = 240 ). Be warned that the more scenarios you analyze the longer the computation will take.

Set Scenario Names

This button will bring up the Scenario Names dialog, where a different name can be assigned to each scenario.

---

<a id="results"></a>

## Results

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Results_Tab.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Results_Tab.htm)*

The Results page of the Multiple Scenario ATC Analysis is available on the [Available Transfer Capability dialog](#available-transfer-capability-dialog) when selecting the option to **Analyze Multiple Scenarios** on the [Advanced Options](#advanced-options) tab of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

Once you have defined your scenarios and started the ATC Analysis, you can switch to the Results page to see the progress that ATC Analysis is making.

![ATC Multiple Scenarios Results Tab](images/ATC_Multiple_Scenarios_Results_Tab.jpg)

The primary part of the Results page contains a spreadsheet-like look-up table display. The layout of the display is dictated by the **Axis Order** selected. Note that because there are three axes possible, the row and column entries represent the first two axes while the third axis is represented by tabs at the top of the table. See [Local Menu Options](#local-menu-options) for information regarding the options available when right-clicking within the table.

This dialog has the following controls:

Axis Order

This menu is used to select the desired axis order. The three axes correspond to the three [Scenarios tabs](#scenarios).

  - One axis has heading labels G0, G1, … for the Generation Scenarios,
  - Another with heading labels RL0, RL1, … for the Rating/Load Scenarios,
  - A third with heading labels I0, I1, … for the Interface Scenarios.

Field to Show

Use this dropdown to select which field is shown in the **Results Display**. By default this is set to Transfer Limit, but any field associated with a transfer limiter can be displayed. Click the **Find** button to open a dialog that allows search options for determining which field to select.

Show Transfer Limiters

Click the **Show Transfer Limiters** button to view the [Transfer Limiters](#transfer-limiters-display) found under each scenario. This will open a separate dialog that displays a list of the Transfer Limiters. To see the Transfer Limiters for a particular scenario, click on the workbook cell that represents the scenario you are interested in and the separate dialog will update appropriately.

Write to Excel

This button will send the results to an Excel spreadsheet.

Save to Text Files

This option will allow the user to save the results in an auxiliary file.

Results Display

The primary part of the Results tab contains a spreadsheet-like look-up table display. The values shown in the table for each scenario are for the field selected with the **Field to Show** option. By default this is the Transfer Limit. The value that is reported corresponds to the transfer limiter with the most limiting Transfer Limit. If using one of the iterated methods, the most limiting Transfer Limit is determined from all limiters that have been iterated on.

---

<a id="local-menu-options"></a>

## Local Menu Options

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Analysis_Results_Tab_Local_Menu_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Analysis_Results_Tab_Local_Menu_Options.htm)*

The [Results](#results) page of the Multiple Scenario ATC Analysis is available on the [Available Transfer Capability dialog](#available-transfer-capability-dialog) when selecting the option to **Analyze Multiple Scenarios** on the [Advanced Options](#advanced-options) tab of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

Right-clicking on the table contained on the Results page will bring up a local menu containing several other options. The first several options are only enabled if a cell that represents a scenario is right-clicked. These options will perform an operation with respect to the Scenario:

Take me to Scenario …

Implements the changes in the Scenario resulting in a modified system state. Transfer limits are not calculated.

Determine Transfer Limit For Scenario …

Calculates the ATC for the Scenario, and then sets the system state back to the Initial State.

Determine Transfer Limit for Selected Scenarios

This option is available if multiple scenarios are selected. Multiple scenarios can be selected by holding down the CTRL key and left-clicking on the desired scenarios. When this option is selected, transfer limits for all of the highlighted scenarios will be calculated. The system state will be restored to the Initial State upon completion of all calculations.

Take me to the Transfer Limit For Scenario …

Performs ATC analysis for the Scenario, and then ramps the transfer to the lowest transfer limit found. If using one of the iterated methods, the transfer limit used for the ramping is the lowest one that is iteratively found.

Other options on this local menu are not related to the Scenario that has been clicked.

Increase Transfer for Present System State

Increments the transfer level for the present system state by a user-defined amount.

Return to Initial State

Returns the system state to the Initial State. The initial state is the state in memory when the ATC analysis is started. The initial state is only stored if using one of the iterative ATC Solution Methods or analyzing Multiple Scenarios. The initial state is also stored when opening the ATC dialog if an initial state has already been stored.

---

<a id="combined-results"></a>

## Combined Results

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Combined_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Dialog_Combined_Results.htm)*

The Combined Results page of the Multiple Scenario ATC Analysis is available on the [Available Transfer Capability dialog](#available-transfer-capability-dialog) when selecting the option to **Analyze Multiple Scenarios** at the top of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

![ATC Multiple Scenarios Combined Results](images/ATC_Multiple_Scenarios_Combined_Results.jpg)

The tables on the Combined Results page show the transfer limitations under ALL scenarios. The scenarios are identified by the default fields ATCLineZoneChanges, ATCGenChanges, and ATCInterfaceChanges. When defining [scenarios](#scenarios) for Line Ratings/Loads, Generator Outputs, and Interface Ratings each corresponding scenario is given an integer identifier. The entries in the table fields correspond to these integer identifiers. Transfer limitations can be filtered based on the type of limitation by switching between the All Limiters, Branch Limiters, Interface Limiters, and Nomogram Interface Limiters sub-tabs, but the tables on any of these sub-tabs will still contain the relevant type of limiters from all scenarios. The transfer limiter results and remaining fields correspond to those described in the [Transfer Limiters Display](#transfer-limiters-display) section.

Special scenario filtering can be done on the Min/Max By Groupings page. More details are provided in the [Min/Max By Groupings](#minmax-by-groupings) topic.

The ATCLineZoneChanges, ATCGenChanges, and ATCInterfaceChanges fields can be used when interacting with the ATC results using auxiliary files and SimAuto to get access to the multiple scenario results. These fields should be used with the TRANSFERLIMITER data type to specify the ATC scenario to which a transfer limitation corresponds. These fields are extra key fields for this data type. If these fields are blank or omitted from input data, the limitations are assumed to go with the standard single set of ATC results.

---

<a id="minmax-by-groupings"></a>

## Min/Max By Groupings

*Source: [`Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Min_Max_By_Groupings.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Scenario_ATC_Min_Max_By_Groupings.htm)*

Added in version 22, build on June 8, 2022

The Min/Max By Groupings page is available on the [Combined Results](#combined-results) page of Multiple Scenario ATC Analysis on the [Available Transfer Capability dialog](#available-transfer-capability-dialog) when selecting the option to **Analyze Multiple Scenarios** at the top of the [Available Transfer Capability dialog](#available-transfer-capability-dialog). Through the options on this page the reporting of minimum or maximum limiters can be done over a selection of ATC scenarios and groupings. The results that are reported are the limiters that meet the chosen operation for the selected groupings. Multiple scenario ATC results must be calculated before using the options on this page. This page only affects the reporting of results and does no new TransferLimiter calculations.

The following image shows the options that are available for displaying min/max limiters:

![Multiple Scenario ATC Min Max Groupings](images/Multiple_Scenario_ATC_Min_Max_Groupings.jpg)

When choosing groupings that include multiple directions, additional options that become available are shown below:

![Multiple Scenario ATC Min Max Groupings2](images/Multiple_Scenario_ATC_Min_Max_Groupings2.jpg)

Directions

Single

The result grouping is done based on the single direction results. Scenario groupings will also apply.

Multiple

The result grouping is based on multiple direction results. If the **Show All Directions** checkbox is checked, all directions will be considered for the grouping. If the checkbox is not checked, only the direction selected in the **Show Direction** dropdown will be considered. The **Group By Direction** option determines how the groupings will be formed based on the selected directions. Scenario groupings for each direction grouping will also apply.

Grouping Scenario

Possible entries are:

None

The results will not be grouped by the scenarios. All scenario results will be included as one group. Direction grouping will also apply.

RL

The results will be grouped by RL scenario. For each RL scenario, all results for the G and I scenarios will be included. Direction grouping will also apply.

G

The results will be grouped by G scenario. For each G scenario, all results for the RL and I scenarios will be included. Direction grouping will also apply.

I

The results will be grouped by I scenario. For each I scenario, all results for the RL and G scenarios will be included. Direction grouping will also apply.

Group By Direction

This option is only relevant if using the **Multiple Directions** option. If checked, results will be reported by direction in addition to being grouped by the scenario options. If not checked, all directions will be considered together and only grouped by the scenario options. The reporting will only include directions that have been selected by using the **Show All Directions** checkbox and specific direction selected with the **Show Direction** dropdown.

Operation

This specifies the operation that is performed on each grouping.

Min

For each grouping a single limiter will be reported that has the minimum value of the selected **Operation Field**. Nothing will be reported for a grouping if there are no results in that grouping.

Max

For each grouping a single limiter will be reported that has the maximum value of the selected **Operation Field**. Nothing will be reported for a grouping if there are no results in that grouping.

Min/Max

For each grouping up to two limiters can be reported: one that has the minimum value of the selected **Operation Field** and another that has the maximum value of the selected **Operation Field**. Nothing will be reported for a grouping if there are no results in that grouping. It is possible that only one result is reported if that same result is both the minimum and maximum for a grouping.

Operation Field

Specifies the field on which the operation is applied. Possible options are the *Transfer Limiter* field and any of the *ATC Extra Monitor* fields.

Filtering by RL, G, and I

This filtering determines which scenarios are included in the calculations. If left blank, all scenarios are included for a particular type. The format of these filters is an integer range list as described in the [Entering a Range of Numbers](04-model-explorer-and-case-information-part3.md#entering-a-range-of-numbers) topic. These entries will be ignored if an **Advanced Filter** is specified.

Advanced Filter

Specify the name of an advanced filter that will be applied to all multiple ATC scenario transfer limiter results (object type TransferLimiter). Click the **Find** button to open a dialog for the filter selection. Only TransferLimiters that meet this filter will be considered when determining the groupings. The **Filtering by RL, G, and I** will be ignored, but all other grouping options will apply.

Prefer Iteratively Found

When checked, transfer limiters that have been iteratively found will take precedence when determining the limiter that meets the selected **Operation** for each grouping. If there are no limiters that have been iteratively found or this option is not checked, the first limiter that is found that meets the **Operation** will be reported for each grouping.

Filter TransferLimiter Results and Apply Operation on Groupings

Click this button to update the results once all of the options have been set. The results will also update as individual options are changed, but this button can be used to make sure everything has refreshed once all options are set.

Example 1

Directions = Single

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

With the following options there is only a single result. There is only one direction that is being run for 35 (5 RL scenarios and 7 G scenarios = 35 total) scenario results. The minimum Transfer Limiter for all scenarios is determined based on the limiters that have been iteratively found.

![Multiple Scenario ATC Min Max Groupings Example 1](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_1.jpg)

Example 2

Directions = Single

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

With the following options there is a result for each RL scenario. There is only one direction that is being run for 35 scenario results. The minimum Transfer Limiter for each RL scenario is found by including all G scenarios within each RL scenario and considering the limiters that have been iteratively found.

![Multiple Scenario ATC Min Max Groupings Example 2](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_2.jpg)

Example 3

Directions = Single

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

For this example the settings are the same as Example 2 except **Prefer Iteratively Found** is not checked here.

With the following options there is a result for each RL scenario. There is only one direction that is being run for 35 scenario results. The minimum Transfer Limiter for each RL scenario is found by including all G scenarios within each RL scenario and considering the limiters whether or not they have been iteratively found.

![Multiple Scenario ATC Min Max Groupings Example 3](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_3.jpg)

Example 4

Directions = Single

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

For this example the settings are the same as Example 2 except the **Operation** is set to *Min/Max*.

With the following options there is a result for each RL scenario. There is only one direction that is being run for 35 scenario results. The minimum and maximum Transfer Limiter for each RL scenario is found by including all G scenarios within each RL scenario and considering the limiters that have been iteratively found.

![Multiple Scenario ATC Min Max Groupings Example 4](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_4.jpg)

Example 5

Directions = Single

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

This example is similar to Example 2 except that **RL Filtering** is used to only consider RL scenarios 1, 3, and 4. The **Grouping** is set to be done by RL scenario, which means that there will be a minimum result for only these RL scenarios.

![Multiple Scenario ATC Min Max Groupings Example 5](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_5.jpg)

Example 6

Directions = Multiple with 5 directions defined

RL Scenarios: 0 through 4

G Scenarios: 0 through 6

With the following options there is a result for each RL scenario under each direction (5 RL scenarios under 5 directions = 25 results). The minimum Transfer Limiter for each grouping is found considering the limiters that have been iteratively found.

![Multiple Scenario ATC Min Max Groupings Example 6](images/Multiple_Scenario_ATC_Min_Max_Groupings_Example_6.jpg)

---

<a id="multiple-directions-available-transfer-capability-dialog"></a>

## Multiple Directions Available Transfer Capability Dialog

*Source: [`Content/MainDocumentation_HTML/Multiple_Directions_Available_Transfer_Capability_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Directions_Available_Transfer_Capability_Dialog.htm)*

To perform [Available Transfer Capability Analysis](#available-transfer-capability-atc-analysis) for all defined directions, check **Multiple** for the **Directions** option of the [Available Transfer Capability dialog](#available-transfer-capability-dialog).

When calculating multiple directions the same methodologies are used as when calculating a single direction. The transfer capability results are calculated for each direction independently of every other direction, but there are some sensitivity values used for calculating the linear impact of contingencies that are only calculated once at the beginning of the entire process. This can help with speeding up the analysis compared to processing each transfer direction using the Single Directions option. Options are available to show the results for all directions together or to examine one direction at a time; this can be useful for comparing the impacts of different transfer directions.

The following changes occur to the dialog:

  - [Directions Display](20-sensitivities.md#directions-display) used to define multiple directions is shown at the top of the Common Options tab
  - [Distributed Computing](#distributed-computing) page appears

![ATC Multiple Directions Dialog](images/ATC_Multiple_Directions_Dialog.png)

---

<a id="result-1"></a>

## Result

*Source: [`Content/MainDocumentation_HTML/Multiple_Directions_Available_Transfer_Capability_Result.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Multiple_Directions_Available_Transfer_Capability_Result.htm)*

The Multiple Directions Available Transfer Capability Result page is found on the [Available Transfer Capability dialog](#available-transfer-capability-dialog). This page is visible when performing ATC analysis when the **Directions** option is set to **Multiple** and using a single system state, i.e., not analyzing Multiple Scenarios. The Result page consists of two sections: a [Transfer Limiters Display](#transfer-limiters-display) and a [Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display).

The results that are shown in the Transfer Limiters Display can be filtered by direction by using the options found at the top of the dialog:

Show All Directions

Check this box to display all of the results for all directions. Uncheck this box to display only the direction selected in the **Show Direction** dropwdown.

Show Direction

When not showing the results for all directions (**Show All Directions**is not checked), use this dropdown to select the direction for which results should be shown. Click the **Choose** button to use the [object chooser](04-model-explorer-and-case-information-part3.md#find-dialog-basics) to select the direction.

![Multiple Directions Available Transfer Capability Result](images/Multiple_Directions_Available_Transfer_Capability_Result.png)

---

<a id="transfer-limiters-display"></a>

## Transfer Limiters Display

*Source: [`Content/MainDocumentation_HTML/Transfer_Limiters_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transfer_Limiters_Display.htm)*

The Transfer Limiters Display shows the results of [ATC Analysis](#available-transfer-capability-atc-analysis). This display appears on the [Result page](#result), [Multiple Direction Result page](#result-1), or [Combined Results page](#combined-results) of the [Available Transfer Capability dialog](#available-transfer-capability-dialog) or as a separate window when performing [Multiple Scenario Available Transfer Capability Analysis](#multiple-scenario-available-transfer-capability-dialog).

![ATC Transfer Limiters Display](images/ATC_Transfer_Limiters_Display.png)

Transfer Limiters Display

The Transfer Limiters Display has the following controls:

All Limiters Tab

The All Limiters tab shows a list of all the transfer limitations found. This includes limitations on branches, interfaces, areas, zones, etc.

Branch Limiters Tab

The Branch Limiters tab only shows those limitations with a transmission line or transformer as the limiting element. The limiting element description for the Branch Limiters tab is replaced by the bus numbers and names of the limiting element.

Interface Limiters Tab

The Interface Limiters tab only shows those limitations with an interface as the limiting element. The limiting element description is replaced by the name of the interface.

Nomogram Interface Limiters Tab

The Nomogram Interface Limiters tab only shows those limitations with a nomogram interface as the limiting element. The limiting element description is replaced by the name and segment of the nomogram interface.

Limiters Fields

Fields Used for Identification of Results

The following fields are used to identify TransferLimiter objects based on the different options for analyzing multiple scenarios and directions. These fields will be included by default when shown on tabs relevant for the different options.

**Direction Name**

Identifies the direction when using Multiple Directions to calculate the results. This field will be blank when Single Directions options are used for the calculation.

**Line/Zone Scenario Number/Name**

Identifies the Line Ratings/Loads scenario when using the option to Analyze Multiple Scenarios. This will be blank when not analyzing multiple scenarios.

**Gen Scenario Number/Name**

Identifies the Generator Outputs scenario when using the option to Analyze Multiple Scenarios. This will be blank when not analyzing multiple scenarios.

**Interface Scenario Number/Name**

Identifies the Interface Ratings scenario when using the option to Analyze Multiple Scenarios. This will be blank when not analyzing multiple scenarios.

Transfer Limit (shown by default)

The Transfer Limit Field shows the Transfer Limit in MW for the Limiting Element during the Limiting Contingency. This value depends on the ATC Solution Method Used:

  - Single Linear Step (SL): Only one Linear ATC step is performed. The Transfer Limit values are those found during this step.
  - Iterated Linear Step (IL): The Single Linear Step method is iterated during this method.  The Transfer Limiters shown are those found during the final step performed.  The actual Transfer Limit values are the values found at the last step plus the accumulated amount the transfer has been ramped.  The Transfer Limitation(s) that were iterated on individually are highlighted in yellow.
  - Iterated Linear Step (IL) then Full CTG: The Transfer Limits shown for the Transfer Limitation(s) that were used when iterating are equal to the accumulated amount that the transfer was ramped during the initial Iterated Linear Step and then the contingency analysis step.  These limitations are highlighted in cyan.  The Transfer Limits shown for all other limiters are the results of the initial Iterated Linear Step calculation performed before iterating on individual limitations for the contingency analysis.

For the iterated methods the Iteratively Found field, Limiting Element field, and color indicators are used to highlight the Transfer Limitations when certain situations are encountered. Unless otherwise indicated, the keyword listed below will show up in the Iteratively Found field:

  - **INIT\_RESERVE\_LIMIT (yellow)** Added in version 22, build on October 18, 2021- Indicates that the transfer is not able to increase beyond the reported Transfer Limit because the participating elements in either the Seller or Buyer hit MW limits in the initial step that occurs at the beginning of either iterated method when all limiters are being iterated on to determine the order in which individual limiters will be iterated on. If this occurs, the entire process will stop and no individual limiters will be iterated on. The limiter that was being used to determine the next ramping step size when the MW limit was hit will be marked with this keyword. An additional transfer limitation will be added to the results indicating if the Seller or Buyer is at MW limits.
  - **YES (yellow)** - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) method or Iterated Linear Step (IL) then Full CTG method when studying base case limitations. The Transfer Limit that is reported is the thermal limitation.
  - **YES\_RESERVE\_LIMIT (yellow)** - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) method or Iterated Linear Step (IL) then Full CTG method when studying base case limitations and the transfer was not able to increase beyond the reported Transfer Limit because either the participating elements in the Seller or Buyer hit MW limits. An additional transfer limitation will be added to the results indicating if the Seller or Buyer is at MW limits.
  - **YES\_INFINITE (light yellow)** - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) method or Iterated Linear Step (IL) then Full CTG method when studying base case limitations or calculating the contingency impact linearly and the PTDF or OTDF fell below the cutoff causing the limiting element to no longer be limiting. The Transfer Limit that is reported is a very large value. Added in version 22, build on May 25, 2021
  - **FULL (aqua)** - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) then Full CTG method. The Transfer Limit that is reported is the thermal limitation.
  - **FULL\_INFINITE (light aqua)**- Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) then Full CTG method and the OTDF fell below the cutoff causing the limiting element to no longer be limiting. The Transfer Limit that is reported is a very large value. Added in version 22, build on May 25, 2021
  - **FULL\_RESERVE\_LIMIT (aqua)** - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) then Full CTG method and the transfer was not able to increase beyond the reported Transfer Limit because either the participating elements in the Seller or Buyer hit MW limits. An additional transfer limitation will be added to the results indicating if the Seller or Buyer is at MW limits.
  - **FULL\_CTG\_SELLER\_LOST (aqua)** Added in version 20, build on January 9, 2019 - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) then Full CTG method when the implementation of the contingency causes all participating elements in the Seller to become disconnected; the contingency solves, but the next step size cannot be determined. The Transfer Limit that is reported is the total amount that could be ramped before the contingency caused the loss of the Seller. The ramped transfer could come from either modeling the contingency only linearly or the contingency may have actually been implemented at a different transfer level without causing the loss of the Seller. If conditional actions such as Remedial Action Schemes are modeled with contingencies, it is possible that the contingency could be solved at one transfer level without causing a loss of the Seller while causing the loss of the Seller at a different transfer level.
  - **FULL\_CTG\_BUYER\_LOST (aqua)** Added in version 20, build on January 9, 2019 - Indicates the Transfer Limitation(s) that were iterated on individually during the Iterated Linear Step (IL) then Full CTG method when the implementation of the contingency causes all participating elements in the Buyer to become disconnected; the contingency solves, but the next step size cannot be determined. The Transfer Limit that is reported is the total amount that could be ramped before the contingency caused the loss of the Buyer. The ramped transfer could come from either modeling the contingency only linearly or the contingency may have actually been implemented at a different transfer level without causing the loss of the Buyer. If conditional actions such as Remedial Action Schemes are modeled with contingencies, it is possible that the contingency could be solved at one transfer level without causing a loss of the Buyer while causing the loss of the Buyer at a different transfer level.
  - **OSCILLATING (lime green)** - This keyword will show up in the Limiting Element field. This indicates that the number of iterations has exceeded the maximum number of allowed iterations. This is set at 100 internally. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution. It is very unlikely that this limitation should occur because there are other mechanisms in place to prevent oscillations in the process.
  - **POWERFLOW\_DIVERGENCE (fuchsia)** - If the Limiting Element field also contains *POWERFLOW DIVERGENCE* this indicates that this type of limit was encountered when iterating on all limiters at the start of the process. If the Limiting Element lists an actual limiting element, this indicates that this type of limit was encountered during the process where an individual limiter is being iterated on. If using the Iterated Linear Step (IL) then Full CTG method this is the step that occurs before actually applying the contingency. The Transfer Limit that is reported is the total amount that could be ramped before the power flow failed to converge. This transfer limitation means that the full desired transfer amount cannot be achieved.
  - **RAMP\_FAIL\_IN\_FULL (fuchsia)** - If using the Iterated Linear Step (IL) then Full CTG method and forcing the transfer ramping to occur pre-contingency, this type of limiter will occur only when iterating on individual limiters. This indicates that the power flow was not able to solve while ramping the transfer and not because the contingency failed to solve. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution at which the contingency solved.
  - **RAMP\_FAIL\_IN\_BASE (gray)** - This type of limiter will not be reported for new studies run with Simulator version 16 or later. It is being retained for the purposes of reporting limiters that were saved with Simulator version 15 and earlier. This type of limitation is the same as a *POWERFLOW\_DIVERGENCE* limiter and would only be reported for a transfer limitation for the base case or when using the Iterated Linear Step (IL) method.
  - **RAMP\_FAIL\_IN\_FULL\_AFTER\_CTG (gray)** - This type of limiter would only be reported if using the Iterated Linear Step (IL) then Full CTG method and ramping the transfer post-contingency when the full ramping amount cannot be achieved. The Transfer Limit that is reported is the total amount that could be ramped before the power flow failed to converge.
  - **CTG\_FAIL\_IN\_FULL (orange)** - Indicates that the contingency failed to solve at some point during the Iterated Linear Step (IL) then Full CTG method. This type of limiter would be reported when NOT using the option to iterate on failed contingencies. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution in which the contingency solved. If the contingency fails to solve immediately following the completion of the iterated process on the individual limiter without the contingency implemented, the Transfer Limit that is reported is the accumulated transfer amount achieved from that process without the contingency implemented.
  - **CTG\_FAIL\_ITERATED (red)** - Indicates that the contingency failed to solve at some point during the Iterated Linear Step (IL) then Full CTG method and using the option to iterate on failed contingencies. The Transfer Limit that is reported is the accumulated amount that is possible without overloading the monitored element and in which the contingency solves. Using the iterated method attempts to get as close as possible (within specified tolerances) to the highest transfer amount at which the contingency will solve. This is very similar to a PV nose point.
  - **CTG\_FAIL\_ITERATED\_OVERLOAD (red)**Added in version 22, build on November 9, 2021 - Indicates that the contingency failed to solve at some point during the Iterated Linear Step (IL) then Full CTG method and using the option to iterate on failed contingencies. The Transfer Limit that is reported is the accumulated amount that is possible for which the contingency solves, but the monitored element is overloaded, as determined by a linear step calculation, at this transfer level. Using the iterated method attempts to get as close as possible (within specified tolerances) to the highest transfer amount at which the contingency will solve. This is very similar to a PV nose point.
  - **CTG\_FAIL\_IN\_BASE (purple)** - Indicates that the contingency failed to solve at zero transfer level (base case failure) when using the Iterated Linear Step (IL) then Full CTG method and choosing to iterated on failed contingencies. The Transfer Limit that is reported is the accumulated transfer amount that was ramped during the iterated process on the individual limiter without the contingency implemented.
  - **CTG\_ABORTED\_LINEAR **(orange)****- Indicates that a contingency was aborted due to an Abort contingency action being implemented during the step where an individual limiter is iterated on when using one of the iterated methods. This is the step where the impact of the contingency is determined using linear calculations and the contingency is not actually implemented. The Transfer Limit that is reported is the accumulated transfer amount achieved from this linear iteration process prior to the Abort action being linearly implemented.
  - **CTG\_ABORTED\_AFTER\_LINEAR **(orange)**** - If using the Iterated Linear Step (IL) then Full CTG method and forcing the transfer ramping to occur post-contingency, this type of limiter will occur if the contingency cannot be solved because an Abort contingency action was implemented. The Transfer Limit that is reported is the accumulated transfer amount achieved from the process where the individual limiter is iterated on without the contingency implemented.
  - **CTG\_ABORTED\_IN\_FULL **(orange)**** - If using the Iterated Linear Step (IL) then Full CTG method and forcing the transfer ramping to occur pre-contingency, this type of limiter will occur if the contingency cannot be solved because an Abort contingency action was implemented. This type of limiter would be reported when NOT using the option to iterate on failed contingencies. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution in which the contingency solved. If the contingency is aborted immediately following the completion of the iterated process on the individual limiter without the contingency implemented, the Transfer Limit that is reported is the accumulated transfer amount achieved from that process without the contingency implemented.
  - **CTG\_ABORTED\_ITERATED **(red)**** - Indicates that the contingency cannot be solved because the Abort contingency action was implemented. This type of limiter will occur when using the Iterated Linear Step (IL) then Full CTG methed on using the option to iterate on failed contingencies. The Transfer Limit that is reported is the accumulated amount that is possible for which the contingency is not aborted. An attempt is made to find the highest transfer level at which the monitored element is not overloaded. Using the iterated method attempts to get as close to possible (within the specified tolerances) to the highest transfer amount at which the contingency is not aborted.

Limiting Element (shown by default)

Shows a text description of the limiting element. This will contain either the actual limiting element or some additional information about a limiter. Special keywords that can appear are *OSCILLATING* and *POWERFLOW DIVERGENCE*. There are described in more detail above in the **Transfer Limit** description. If reporting reserve limits and either the source or sink will hit a reserve limit at a particular transfer level, the name of the source or sink will appear as the limiting element.

Limiting CTG (shown by default)

Shows the name of the limiting contingency.

% OTDF (shown by default)

This is the OTDF (or PTDF if the Limiting CTG is *Base Case*) on the Limiting Element for the transfer direction that is being studied. In other words, this is a linear estimate of the percent of the transfer that will appear on the Limiting Element if the Limiting CTG occurs.

**Note**: For iterated techniques, this is the PTDF or OTDF at the last Linear Iteration.

Pre-Transfer Value Estimate (shown by default)

If a contingency is not included in the Limiter, this is equal to the Initial Value. When a contingency is included in the Limiter, this is the linear estimate of the post-contingency flow before any transfer occurs. See [Available Transfer Capability Analysis](#available-transfer-capability-atc-analysis).

**Note**: For iterated techniques, this is the estimate at the last Linear Iteration.

Limit Used (shown by default)

This is the value of the Limit being used by the ATC for the Limiting Element during the Limiting CTG. It reflects what is specified in [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) and options set on the [Advanced Options](#advanced-options) tab.

MVA the Limit Used is based on

This is the unaltered MVA limit that is defined with a particular limiting element. This is the starting point for determining the **Limit Used** that reflects [Limiting Monitoring Settings](18-general-tools.md#limit-monitoring-settings) and options that are set on the [Advanced Options](#advanced-options) tab.

Iteratively Found

String indicating if the limitation was found using one of the [iterated methods](#solution-methods). Additional information about the possible entries of this field and what the different entries mean is given above in the **Transfer Limit** description.

Contingency Definition Display

This display shows information on the defined contingency that caused the limitation selected from one of the tabbed pages of limiters. For more information on this display, see [Contingency Analysis - Contingency Definition Display](22-contingency-analysis-options.md#contingency-definition-display).

---

<a id="solution-methods"></a>

## Solution Methods

*Source: [`Content/MainDocumentation_HTML/ATC_Analysis_Methods_Solution_Methods.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Analysis_Methods_Solution_Methods.htm)*

Simulator provides three methods of determining ATC.

  - [Single Linear Step (SL)](#single-linear-step-sl)
  - [Iterated Linear Step (IL)](#iterated-linear-step-il)
  - [Iterated Linear Step (IL) then Full Contingency Solution](#iterated-linear-step-il-then-full-ctg-solution)

---

<a id="single-linear-step-sl"></a>

## Single Linear Step (SL)

*Source: [`Content/MainDocumentation_HTML/ATC_Analysis_Methods_Single_Linear_Step_SL_.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Analysis_Methods_Single_Linear_Step_SL_.htm)*

The Single Linear Step approach is the most common ATC method. This method of ATC analysis uses only information about the present system state and sensitivities (mathematical derivatives) about the present system state. These sensitivities are embodied in the [PTDF](20-sensitivities.md#power-transfer-distribution-factors) and [LODF](20-sensitivities.md#line-outage-distribution-factors-dialog) calculations.

Consider a transmission line with a limit of 10 MW, present loading of 5 MW and a PTDF of 10%. The estimated maximum transfer without causing an overload on the line is

*Transfer Limitation = (Limit – Present Loading) / PTDF = (10 – 5) / 0.1 = 50 MW*

When including contingency analysis, the [OTDF (Outage Transfer Distribution Factor)](20-sensitivities.md#line-outage-distribution-factors-dialog) and linearized estimates of post-contingency flows are used to determine the Transfer Limitation.

*Transfer Limitation = (Limit – Post-Contingency Loading) / OTDF*

If we find the Transfer Limitation for every transmission branch (and interface) during each contingency, then the ATC is equal to the smallest Transfer Limit value.

Contingency elements have an associated [Status](22-contingency-analysis-options.md#contingency-definition-display) that determines under what conditions a particular action will be implemented. When ATC values are calculated using the single linear step method, contingency actions are not actually implemented. Because contingency actions are not actually implemented, *TOPOLOGYCHECK* and *POSTCHECK* actions cannot be applied after other actions have been performed and the power flow has been solved. By default, *TOPOLOGYCHECK* and *POSTCHECK* actions act as *CHECK* actions during the single linear step method. Whether or not model criteria are met for *CHECK*, *TOPOLOGYCHECK*, and *POSTCHECK* contingency actions will be determined at the zero transfer level rather than at the transfer level that determines the limiting transfer.

There [Iterate on Action Status](22-contingency-analysis-options.md#basics) option that can be set with contingency options, will allow conditional actions to be treated more accurately as part of the linear step calculations. Instead of treating all *TOPOLOGYCHECK* and *POSTCHECK* as *CHECK* actions, these actions are processed after other actions have been linearly implemented. See the [Contingency Iterated Linear Analysis](23-contingency-analysis-running-and-results.md#iterated-linear-analysis) topic for details on this process.

**Note:** Simulator also monitors the possibility that a transfer will reduce the flow on a line until the line reaches its limit for flow in the opposite direction.

---

<a id="iterated-linear-step-il"></a>

## Iterated Linear Step (IL)

*Source: [`Content/MainDocumentation_HTML/ATC_Analysis_Methods_Iterated_Linear_Step_IL_.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Analysis_Methods_Iterated_Linear_Step_IL_.htm)*

The Single Linear Step is an extremely fast method for determining the ATC. However, because it only uses present operating point information, controller changes are not taken into account. The linearization assumes that all controllers are fixed. The Iterated Linear Step (IL) method provides an alternative to the Single Linear Step that allows controller changes, but still performs its analysis in a reasonable amount of time. The (IL) method operates as follows:

  - Perform Single Linear Step
      - During the process where limiters are individually iterated on, it is possible that the single linear step calculation cannot be performed because the contingency aborts due to an Abort contingency action.
          - If this occurs when using the iterated method Iterated Linear Step (IL) and not implementing the full contingency, the Iteratively Found string will be set to *CTG\_ABORTED\_LINEAR* and the iterative process will stop. The Transfer Limit that is reported is the accumulated transfer amount achieved from this linear iteration process prior to the Abort action being linearly implemented.
          - If this occurs when using the Iterated Linear Step (IL) then Full CTG method, the linear iterated method will stop and the process will continue on with the full contingency actually being implemented at this transfer level.
      - If generator limits are being enforced for the selected transactors, generators will be excluded from participating in the linear calculations if they are in the seller and they are at their maximum limit or if they are in the buyer and they are at their minimum limit. It is possible that there are no available participation points during the linear step and the reserve limit is encountered. If a reserve limit is encountered during the step where all transfer limiters are iterated on together, the entire ATC process will stop. If a reserve limit is encountered during the step where a limiter is being iterated on individually, the iterations will only stop for that limiter; other limiters will be processed if they do not hit a reserve limit as well. The reserve limit will be reported in the results.
  - Set the Stepsize = Minimum Transfer Limitation found in Single Linear Step which is greater than the specified **When iterating, Ignore Limiters below** value
  - If \[Iterations \>= 100\] then stop
      - If the maximum 100 number of iterations is reached, a transfer limitation will be reported highlighted in lime green with the Iteratively Found field set to *OSCILLATING* indicating that the iterated process is oscillating. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution. The maximum number of iterations is a value that is set internally. It is unlikely that this limit will ever be reached because other mechanisms are in place to prevent oscillations.
      - The iteration count is reset at the beginning of the iteration process.
  - Implement transfer by amount of Stepsize and resolve power flow
      - The power flow is solved according to the options set with the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options).

      - When calculating a transfer between injection groups, the [Island-Based AGC Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) applicable to dispatch using an injection group are used when determining which generators and loads will participate in the transfer. These options include whether or not AGC status should be considered when determining which units will participate in the ramping, whether or not to enforce generator MW limits, and whether or not to allow negative loads. The power factor to use when adjusting load is also specified with these options.

      - To prevent oscillation of the solution, the Stepsize may be limited if the sign of the Stepsize changes throughout the iterations. At each iteration, the direction of the Stepsize is checked and the Stepsize is bounded based on the accumulated transfer at each iteration. The accumulated transfer is the total amount that the transfer between the seller and buyer has been ramped. The accumulated transfer is updated with the current Stepsize once it has been determined that Stepsize can be achieved. At the start of the iterated process, LowBound is initialized to a large negative number and HighBound is initialized to a large positive number. At each iteration the following checks are performed:

        If Stepsize \> 0 then LowBound = (Accumulated Transfer)

        Else If Stepsize \< 0 then HighBound = (Accumulated Transfer)

        If Stepsize \>= (HighBound - Accumulated Transfer)\*0.7

        Then Stepsize = (HighBound – Accumulated Transfer)\*0.7

        Else If Stepsize \<= (LowBound - Accumulated Transfer)\*0.7

        Then Stepsize = (LowBound – Accumulated Transfer)\*0.7
    <!-- end list -->
      - During the implementation of the transfer, if the full Stepsize cannot be achieved, an attempt is made to implement as much of the transfer as possible in smaller stepsizes by reducing the stepsize by half. The stepsize reduction continues until a stepsize is found at which the power flow will solve. Once this stepsize is found, an attempt will be made to ramp to the original full stepsize using the smaller reduced stepsize. If at any point in this process a stepsize cannot be ramped, an iterative process will be used to reduce the stepsize so as much as possible of the full original stepsize can be ramped. The user specified Transfer Tolerance is used to prevent the stepsize from becoming too small.
      - If the power flow fails to converge at this point without being able to implement the full Stepsize transfer, a transfer limitation will be reported highlighted in fuchsia with the Iteratively Found field set to *POWERFLOW\_DIVERGENCE*. The Transfer Limit that is reported is the total amount that could be ramped before the power flow failed to converge. This transfer limitation means that the full desired transfer amount cannot be achieved.
          - If the full transfer amount cannot be achieved in this process when all limiters are being iterated on, the iterative process will continue and iterate on individual limiters.
          - When all limiters are being iterated on, the Limiting Element will show *POWERFLOW DIVERGENCE* in addition to the Iteratively Found field showing *POWERFLOW\_DIVERGENCE*. This indicates exactly where in the process the ramping could not be achieved.
          - If the full transfer amount cannot be achieved in this process when individual limiters are being iterated on, the analysis method selected will dictate how the process continues. If using the Iterated Linear Step (IL) method, a Transfer Limit will be reported that is the total amount that could be ramped before the power flow failed to converge and this limiter will be highlighted in fuchsia with the Iteratively Found field set to *POWERFLOW\_DIVERGENCE*. If the Iterated Linear Step (IL) method is being used as part of the Full CTG Solution method, the process will continue into the contingency solution step unless the limiter that is being iterated on is a base case limitation. If the limiter is a base case limitation, a Transfer Limit will be reported the same as if using the Iterated Linear Step (IL) method.
          - If using the [Iterated Linear (IL) then Full CTG](#iterated-linear-step-il-then-full-ctg-solution) method and ramping post-contingency, e.g. the option to **Force all transfer ramping to occur in pre-contingency states and repeat full CTG solutions** is NOT checked, and the full transfer amount cannot be achieved, a transfer limitation will be reported highlighted in gray with the Iteratively Found field set to *RAMP\_FAIL\_IN\_FULL\_AFTER\_CTG*. The Transfer Limit that is reported is the total amount that could be ramped before the power flow failed to converge.
      - The ramping of the transfer is done so that each step adjusts injection from a common starting point so that the ramping is effectively done in the same direction even if the Stepsize backs off the transfer. At the start of the iterated process, the base case generation and load values are stored. At each step where transfer ramping occurs, the generation and load values are returned to their base case levels and the transfer ramping is implemented from that point. As an example, take the situation where 1000 MW is ramped. The next Stepsize is calculated to be -100 MW. The total transfer amount achieved is then 900 MW. If ramping does not proceed in the same direction, generators that hit maximum limits when ramping out to 1000 MW will back off from these limits when ramping the -100 MW Stepsize. Ramping out to the total transfer amount of 900 MW in one step causes generators to hit their limits and stay there. If the ramping does not proceed in the same direction, ramping out by the total amount in one step and ramping by backing off the transfer will yield different results because some generators will no longer be at limits when ramping in steps. Ramping in the same direction is intended to prevent this discrepancy with generators at limits.
    <!-- end list -->
      - Reserve limits on generators and loads participating in the transfer will be checked if the option to enforce limits is active for the selected transactors. Reserve limits are checked regardless of how the option to **Report Generation Reserve Limits** is set with the [Common Options](#options). For areas and super areas this means that the global enforcement of generator limits is active, the area enforcement of limits is active, and there is at least one generator whose enforcement of limits is active and this generator is on AGC control. For injection groups this means that the enforcement of limits for the injection group is active. When a reserve limit is found, the current iterations will stop and a transfer limit will be reported with the reserve limit and the area, super area, or injection group that is at a limit. If a reserve limit is encountered during the step where all transfer limiters are iterated on together, the entire ATC process will stop. If a reserve limit is encountered during the step where a limiter is being iterated on individually, the iterations will only stop for that limiter; other limiters will be processed if they do not hit a reserve limit as well.
  - If \[abs(Stepsize) \<= Tolerance\] then stop
  - At new operating point, go back to first step and repeat

As the initial iteration process is performed, the transfer limiter may be different (i.e. the contingency and limiting element pair may be different) during each iteration. Once the Stepsize is determined to be less than or equal to the tolerance (or the maximum number of iterations is met) the order of the limiters is set.

At this point, the first user specified **Transfer Limiters to Iterate On** are taken from the list of limiters and the above process is repeated for each limiter individually, with the contingency and limiting element pair of each limiter remaining set as determined in the initial process. Some limiters that will appear in the list of limiters are not valid for iterating on individually. These limiters include those indicating the full transfer amount could not be ramped in the initial process and those indicating that a reserve limitation has been met on the source or sink. These type of limiters will be skipped when choosing those to iterate on individually. Transfer limitations for transfer limits found by iterating on them individually will be highlighted in yellow in the results and the Iteratively Found field will be set to *YES*.

This method takes into account controller changes that occur as you ramp out to the transfer level, but still avoids the full simulation of contingencies.

This method can be applied between combinations of areas and super areas, OR between two injection groups. Combinations of areas/superareas and injection groups are not allowed.

---

<a id="iterated-linear-step-il-then-full-ctg-solution"></a>

## Iterated Linear Step (IL) then Full CTG Solution

*Source: [`Content/MainDocumentation_HTML/ATC_Analysis_Methods_Iterated_Linear_Step_IL_then_Full_CTG_Solution.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/ATC_Analysis_Methods_Iterated_Linear_Step_IL_then_Full_CTG_Solution.htm)*

This method takes the solution process a step further than just the Iterated Linear (IL) method. Instead of using linear sensitivities to calculate the impact of contingencies on the transfer limits, full contingencies are implemented and solved with a full power flow solution. Be aware however, that this calculation method can be extremely slow.

The initial iteration process of (IL) then Full CTG Solution method starts by performing the steps outlined in the [Iterated Linear (IL)](#iterated-linear-step-il) process. As the initial iteration process is performed, the transfer limiter may be different (i.e. the contingency and limiting element pair may be different) during each iteration. Once the Stepsize is determined to be less than or equal to the tolerance (or the maximum number of iterations is met) the order of the limiters is set.

At this point, the first user specified **Transfer Limiters to Iterate On** are taken from the list of limiters and the steps outlined in the [Iterated Linear (IL)](#iterated-linear-step-il) process are repeated for each limiter individually, with the contingency and limiting element pair of each limiter remaining set as determined in the initial process. Some limiters that will appear in the list of limiters are not valid for iterating on individually. These limiters include those indicating the full transfer amount could not be ramped in the initial process and those indicating that a reserve limitation has been met on the source or sink. These type of limiters will be skipped when choosing those to iterate on individually.

Once the iterated process has been repeated for an individual limiter, there are two different ways that the processing of the full contingency can proceed. If choosing to NOT **Force all transfer ramping to occur in pre-contingency states and repeat full CTG solutions**, the contingency of each transfer limiter is then enforced in the power flow topology, and a power flow solution is performed to give a new contingency power flow solution to use as the base for each transfer limiter. If the option to **Use Specific Solution Options for Contingencies** is checked, then the power flow is solved with the options defined with the [Contingency Solution Options](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options). Otherwise, the power flow is solved with the options specified with the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options). In either case, the [Make-Up Power](22-contingency-analysis-options.md#basics) option specified with the contingency analysis options is used when applying the contingency. The iterative process outlined in the [Iterated Linear (IL)](#iterated-linear-step-il) method is then repeated again for each individual transfer limiter with the specified contingency of each limiter actually in place in the power flow solution. If the contingency solution fails to converge, the transfer limitation will be reported highlighted in orange with the Iteratively Found field set to *CTG\_FAIL\_IN\_FULL*, and the Transfer Limit that is reported will be the value determined from the iterated process performed on the individual limiter before the contingency was applied. If the contingency fails to solve because a contingency Abort action has been implemented, the Iteratively Found field is set to *CTG\_ABORTED\_AFTER\_LINEAR*, and the Transfer Limit that is reported will be the value determined from the iterated process performed on the individual limiter before the contingency was applied.

If choosing to **Force all transfer ramping to occur in pre-contingency states and repeat full CTG solutions**, after the iterated process is complete for an individual limiter, the contingency of each transfer limiter is fully implemented in the following steps:

  - Store the system state following the iterated process on the individual limiter
      - At this point the accumulated transfer amount is the total amount that has been transferred following completion of the iterated process on the individual limiter.
      - The Stepsize is zero for the first iteration.
  - Apply the contingency and perform full power flow solution
      - If the option to **Use Specific Solution Options for Contingencies** is checked, then the power flow is solved with the options defined with the [Contingency Solution Options](21-contingency-analysis-overview-and-records.md#contingency-analysis-power-flow-solution-options). Otherwise, the power flow is solved with the options specified with the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options). In either case, the [Make-Up Power](22-contingency-analysis-options.md#basics) option specified with the contingency analysis options is used when applying the contingency.
      - If the option to **Iterate on failed contingency** is NOT checked and the power flow fails to solve, the iterated process for the individual limiter will stop and a transfer limitation will be reported highlighted in orange with the Iteratively Found field set to *CTG\_FAIL\_IN\_FULL*. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution in which the contingency solved. If the contingency fails to solve immediately following the completion of the iterated process on the individual limiter without the contingency implemented, the Transfer Limit that is reported is the accumulated transfer amount achieved from that process without the contingency implemented.
          - If the contingency fails because a contingency Abort action has been implemented, the Iteratively Found field is set to *CTG\_ABORTED\_IN\_FULL*. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution in which the contingency solved. If the contingency is aborted immediately following the completion of the iterated process on the individual limiter without the contingency implemented, the Transfer Limit that is reported is the accumulated transfer amount achieved from that process without the contingency implemented.
      - If the option to **Iterate on failed contingency** IS checked and the power flow fails to solve, a new iteration loop is entered to determine the highest transfer level at which the contingency can be solved. This loop attempts to determine a more accurate transfer level at which the contingency fails to solve rather than simply reporting the transfer level at which the last power flow was successful regardless of the current Stepsize. To start the iterative process, the current Stepsize is reduced by half. The ramping is performed and the contingency is solved. The Stepsize will remain the same as long as the contingency can be solved. If the contingency fails to solve, the Stepsize will be reduced by half again. The ramping will continue until the contingency no longer solves, the accumulated transfer during the process meets the original Stepsize, or the Stepsize becomes smaller than the Stepsize tolerance, which is the user specified Transfer Tolerance.
          - An additional check is done if the contingency does solve during this process; the flow on the monitored element is checked to determine if it exceeds its limit. If it is overloaded, the Stepsize will be reduced by half until the monitored element is no longer over its limit. While this check is being done on the monitored element limit, the ramping continues out to the specified amount and the contingency is solved. During this entire process, the Stepsize is limited to be between zero and the Stepsize that was ramped when the contingency failed to solve for the first time. When the iterative process on the failed contingency completes, the iterations are done for this particular limiter. The Transfer Limit that is reported is the accumulated amount that is possible without overloading the monitored element and in which the contingency solves. The limiter will be reported highlighted in red with the Iteratively Found field set to *CTG\_FAIL\_ITERATED* if the monitored element is not loaded to its limit. If during this process, the monitored element is at its thermal limit, within the specified stepsize tolerance, and the contingency solves, the Iteratively Found field is set to *FULL* and the limiter will be highlighted in aqua.
              - Modified in version 22, build on November 9, 2021 It is also possible that the monitored element is still overloaded when the contingency is solved. If so, the limiter will be reported highlighted in red with the Iteratively Found field set to *CTG\_FAIL\_ITERATED\_OVERLOAD*.
              - Modified in version 22, build on November 9, 2021If the Stepsize is negative when the monitored element is overloaded this means that the Stepsize needs to become more negative to reduce the overload. Instead of reducing the Stepsize by half, the Stepsize remains at the current amount until the contingency does not solve or the monitored element is no longer overloaded.
              - If the contingency fails because a contingency Abort action has been implemented, the Iteratively Found field is set to *CTG\_ABORTED\_ITERATED*. An attempt is made to find a transfer level at which the monitored element is not overloaded, but this might not be possible within the constraints of the original Stepsize. The Transfer Limit that is reported is the accumulated amount that is possible at which the contingency is not aborted.
          - If the contingency fails to solve at any transfer level (base case failure), the limiter will be reported highlighted in purple with the Iteratively Found field set to *CTG\_FAIL\_IN\_BASE*. The Transfer Limit that is reported is the accumulated transfer amount that was achieved from the iterated process on the individual limiter without the contingency implemented.
      - If the power flow solution is successful, update the accumulated transfer with the Stepsize.
  - Perform Single Linear Step on the individual limiter
      - The Stepsize is the Transfer Limit found for the individual limiter. If the Stepsize is less than the specified **When iterating, Ignore Limiters below** value minus the accumulated transfer amount, it is set to zero.
      - If generator limits are being enforced for the selected transactors, generators will be excluded from participating in the linear calculations if they are in the seller and they are at their maximum limit or if they are in the buyer and they are at their minimum limit. It is possible that there are no available participation points during the linear step and the reserve limit is encountered. If a reserve limit is encountered during the step where all transfer limiters are iterated on together, the entire ATC process will stop. If a reserve limit is encountered during the step where a limiter is being iterated on individually, the iterations will only stop for that limiter; other limiters will be processed if they do not hit a reserve limit as well. The reserve limit will be reported in the results.
  - If \[abs(Stepsize) \<= Tolerance\] or \[Iterations \>= 100\] then stop
      - If the maximum 100 number of iterations is reached, a transfer limitation will be reported highlighted in lime green with the Iteratively Found field set to *OSCILLATING* indicating that the iterated process is oscillating. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution. The maximum number of iterations is a value that is set internally. It is unlikely that this limit will ever be reached because other mechanisms are in place to prevent oscillations.
      - The iteration count is reset at the beginning of the contingency iteration process for each individual limiter.
  - Restore system to the state stored in the first step
      - This step removes the contingency that was implemented so that the transfer ramping occurs prior to the contingency being applied.
  - Implement transfer by amount of Stepsize and resolve power flow
      - The power flow is solved according to the options set with the [Power Flow Solution Options](10-power-flow-solution-and-options-part1.md#power-flow-solution-options).

      - When calculating a transfer between injection groups, the [Island-Based AGC Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc) applicable to dispatch using an injection group are used when determining which generators and loads will participate in the transfer. These options include whether or not AGC status should be considered when determining which units will participate in the ramping, whether or not to enforce generator MW limits, and whether or not to allow negative loads. The power factor to use when adjusting load is also specified with these options.

      - To prevent oscillation of the solution, the Stepsize may be limited if the sign of the Stepsize changes throughout the iterations. At each iteration, the direction of the Stepsize is checked and the Stepsize is bounded based on the accumulated transfer at each iteration. The accumulated transfer is the total amount that the transfer between the seller and buyer has been ramped. The accumulated transfer is updated with the current Stepsize once it has been determined that Stepsize can be achieved. At the start of the iterated process, LowBound is initialized to a large negative number and HighBound is initialized to a large positive number. At each iteration the following checks are performed:

         If Stepsize \> 0 then LowBound = (Accumulated Transfer) 

        Else If Stepsize \< 0 then HighBound = (Accumulated Transfer)

        If Stepsize \>= (HighBound - Accumulated Transfer)\*0.7

        Then Stepsize = (HighBound – Accumulated Transfer)\*0.7

        Else If Stepsize \<= (LowBound - Accumulated Transfer)\*0.7

        Then Stepsize = (LowBound – Accumulated Transfer)\*0.7

      - During the implementation of the transfer, if the full Stepsize cannot be achieved, an attempt is made to implement as much of the transfer as possible in smaller stepsizes by reducing the stepsize by half. The stepsize reduction continues until a stepsize is found at which the power flow will solve. Once this stepsize is found, an attempt will be made to ramp to the original full stepsize using the smaller reduced stepsize. If at any point in this process a stepsize cannot be ramped, an iterative process will be used to reduce the stepsize so as much as possible of the full original stepsize can be ramped. An internal tolerance is used to prevent the stepsize from becoming too small.

      - The ramping of the transfer is done so that each step adjusts injection from a common starting point so that the ramping is effectively done in the same direction even if the Stepsize backs off the transfer. Additional details about this are provided in the steps of the [Iterated Linear (IL)](#iterated-linear-step-il) process.

      - If the power flow fails to solve at this point without being able to implement the full Stepsize transfer, the iterated process for the individual limiter will stop and a transfer limitation will be reported highlighted in fuchsia with the Iteratively Found field set to *RAMP\_FAIL\_IN\_FULL*. The Transfer Limit that is reported is the accumulated transfer amount that has been ramped as of the last successful solution at which the contingency solved. The Transfer Limit reported does not indicate the portion of the Stepsize that could be ramped before the power flow fails to solve.

      - Reserve limits on generators and loads participating in the transfer will be checked if the option to enforce limits is active for the selected transactors. Reserve limits are checked regardless of how the option to **Report Generation Reserve Limits** is set with the [Common Options](#options). For areas and super areas this means that the global enforcement of generator limits is active, the area enforcement of limits is active, and there is at least one generator whose enforcement of limits is active and this generator is on AGC control. For injection groups this means that the enforcement of limits for the injection group is active. When a reserve limit is found, the current iterations will stop and a transfer limit will be reported with the reserve limit and the area, super area, or injection group that is at a limit.
  - Go back to second step and repeat

Transfer limitations found by implementing the full contingency solution are highlighted in aqua in the results with the Iteratively Found field set to *FULL*.

This method can be applied between combinations of areas and superareas, OR between two injection groups. Combinations of areas/superareas and injection groups are not allowed.

When using this method, the PTDF and OTDF cutoff values are set to (Modified in version 22, build on May 25, 2021) 0.1 times their specified values internally by the ATC process when iterating on individual limiters. Once limiters are in the list as having acceptable distribution factors following the process where all limiters are iterated on as a whole, they should not be eliminated during the process when they are being iterated on individually. Actual implementation of the contingency as opposed to the linear determination of the impact of the contingency could lead to some large differences in the distribution factor post-contingency for some contingency scenarios. The only time that these differences could be a problem is if implementation of the contingency actually causes the monitored element to no longer be limiting, i.e. the distribution factor goes to zero. If this happens for any limiter, that limiter will be marked internally as having an infinite transfer amount, will show up in the results with a very large transfer limiter value, and will be excluded from the count of the number of limiters that have been iterated on. (Modified in version 22, build on May 25, 2021) Additionally, the Iteratively Found field will be set to *YES\_INFINITE* if the full contingency solution was not implemented or *FULL\_INFINITE* if the full contingency solution was implemented. The next limiter in the list will then be processed until the number of **Transfer Limiters to Iterate on** has been met or there are no more limiters.
