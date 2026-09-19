---
title: "Fault Analysis"
part: "Analysis"
chapter_file: "27-fault-analysis.md"
topics: 9
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Fault Analysis

Fault analysis dialog, per-object fault records and mutual impedance.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (9)**

- [Fault Analysis](#fault-analysis)
- [Fault Analysis Dialog](#fault-analysis-dialog)
- [Fault Analysis Bus Records](#fault-analysis-bus-records)
- [Fault Analysis Generator Records](#fault-analysis-generator-records)
- [Fault Analysis Line Records](#fault-analysis-line-records)
- [Mutual Impedance Records](#mutual-impedance-records)
- [Mutual Impedance Record Dialog](#mutual-impedance-record-dialog)
- [Fault Analysis Load Records](#fault-analysis-load-records)
- [Fault Analysis Switched Shunt Records](#fault-analysis-switched-shunt-records)

---

<a id="fault-analysis"></a>

## Fault Analysis

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Fault analysis can only be performed when Simulator is in [Run Mode](01-getting-started.md#run-mode-introduction). There are three ways to start a fault analysis study:

  - Go to the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, and choose **Fault Analysis** from the [Run Mode](02-simulator-ribbon.md#run-mode-ribbon-group) ribbon group. This is only available in [Run Mode](01-getting-started.md#run-mode-introduction).
  - Right click on a bus and choose **Fault…** to perform a fault analysis at that bus
  - Right click on a line and choose **Fault…** to perform a fault analysis at that point on the line

All of these options will open the [Fault Analysis](#fault-analysis-dialog) dialog. If you opened the dialog by right-clicking on a bus or line, the fault information on that bus or line will already be filled in. If you selected the **Fault Analysis…** option from the ****[Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab, the information about the location of the fault will need to be provided.

---

<a id="fault-analysis-dialog"></a>

## Fault Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Fault Analysis** dialog can be used to perform a fault analysis study on the currently loaded power system. A fault study can only be performed while Simulator is in [run mode](01-getting-started.md#run-mode-introduction), since the load flow must be validated and solved before a fault study can be calculated.

![Faul Analysis Dialog 812x328](images/Faul_Analysis_Dialog_812x328.gif)

If you are observing single fault analysis results in the fault analysis dialog and switch to [edit mode](01-getting-started.md#edit-mode-introduction), the dialog will automatically be closed and the single fault analysis results will be cleared from memory. Multiple fault results displayed in the Fault Definitions table are maintained when switching to edit mode, but may no longer be relevant when switching back to run mode, depending on what was done to the power system data in edit mode.

The fault analysis has two choices for calculating fault results. The first option is calculating the fault current at multiple defined points for a general summary of [several faults](52-additional-linked-topics-part1.md#fault-analysis-dialog-fault-definitions), and the second is calculating detailed fault results and fault current flows for a [single fault](52-additional-linked-topics-part1.md#fault-analysis-dialog-single-fault) point.

Simulator stores fault data in the PowerWorld binary file along with the load flow data, but by default most other load flow formats store fault data in separate files. The fault data can be stored in and loaded from an external file, but if no fault data is present in a PowerWorld binary file or loaded from an external file before a fault analysis is run, Simulator will use the load flow data as default values for the analysis. Fault data values can also be modified for specific devices by opening a specific device's information dialog and looking at the **Fault…** tab. Devices that require sequence specific data for fault analysis are [buses](07-object-properties-run-mode-and-general-part1.md#bus-information-dialog) (for sequence load injections), [generators](07-object-properties-run-mode-and-general-part1.md#generator-information), [switched shunts](05-case-information-displays-by-object-part3.md#switched-shunt-display), [transmission lines](07-object-properties-run-mode-and-general-part1.md#linetransformer-information), and [transformers](07-object-properties-run-mode-and-general-part1.md#linetransformer-information).

Phase shifts in a fault analysis calculation can be very important for calculating the correct fault currents and voltages throughout the system. The phase shifts that are applied for transmission lines and transformers are taken from the load flow values of phase entered with each specific transmission element. While transformers can have their transformer configurations specified (i.e. Delta-Wye, Grounded Wye-Delta, etc.), these configurations are **NOT** used to determine phase shift angles, **ONLY** to determine the proper grounding on each side of the transformer. The phase shifts that are applied are taken from the load flow data phase values for the transmission elements. If no phase shifts are entered in the load flow data, the fault analysis will treat all elements as having zero phase shift. Phase shift values can be entered manually for each transmission element, but are also included in most load flow formats and will be read into Simulator when loading a load flow data file.

Note that the bus chosen for the fault is always set to a 0 degree reference, and all other buses are shifted according to this reference.

Auto Insert...

Auto-Insert faults options similar to those in [Auto Insert Contingencies](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) in the Contingency Analysis dialog. Choose between a *Single transmission line* or a *Single Bus*. Then hit *Do Insert Fault Records* to insert the faults.**

Load Data.../Save Data...

These two buttons allow loading from and saving to external files. Currently the two types of files supported are PSS/E Sequence Data files (.seq) and [PowerWorld Simulator Auxiliary files](03-cases-files-and-formats.md#auxiliary-file-format-aux) (.aux). Either one of these formats can be loaded and saved.

Note that typically Simulator assumes that if no zero sequence data is given for a branch that the zero sequence impedance is defaulted to 2.5 times the positive sequence impedance. However, in the case of reading in data from a PSS/E sequence data file, you are given the option to instead treat branches with now explicitly given zero sequence data as open circuits in the zero sequence network.

Also can optionally append sequence data when loaded from the Fault Analysis dialog. A prompt will be given to clear all sequence data first or append if opening an auxiliary file or a PTI \*.seq file where the \*.seq file contains a 0 indicator for new data. If the \*.seq file contains a 1 indicating that data should be appended, no prompt is given and the data is just appended.

Units

Select p.u. or Amps to show the current results in the selected units.

Inserts a temporary bus to represent the fault location in a Branch.

When defining multiple faults (like when using Auto Insert...) you have the option to specify the position of the fault along the line. To save computation time, by default a location \>= 50 assumes a fault at the To Bus and \< 50 assumes a falut at the from bus. Selecting the checkbox will add a dummy bus at the actual fault location.

---

<a id="fault-analysis-bus-records"></a>

## Fault Analysis Bus Records

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Bus_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Bus_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog has the same functionality available as [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) displays. The purpose of this display is to tabulate the results of the fault analysis calculations. By default, the phase voltage magnitudes and angles are displayed. In addition, the sequence voltages and angles can also be added by modifying the display using the [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog.

---

<a id="fault-analysis-generator-records"></a>

## Fault Analysis Generator Records

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Generator_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Generator_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog has the same functionality available as [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) displays. The purpose of this display is to tabulate the results of the fault analysis calculations. By default, the phase current magnitudes are displayed for the terminal end of the generator. The phase current angles, as well as the sequence current magnitudes and angles, can be added by modifying the display using the [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog. The magnitude and angle direction reference is always given as out of the generator and into the terminal bus.

---

<a id="fault-analysis-line-records"></a>

## Fault Analysis Line Records

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Line_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Line_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog has the same functionality available as [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) displays. The purpose of this display is to tabulate the results of the fault analysis calculations. By default, the phase current magnitudes are displayed for each end of the branch. The phase current angles, as well as the sequence current magnitudes and angles, can be added by modifying the display using the [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog. The magnitude and angle direction reference is always given as out of or away from a bus.

---

<a id="mutual-impedance-records"></a>

## Mutual Impedance Records

*Source: [`Content/MainDocumentation_HTML/Mutual_Impedance_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Mutual_Impedance_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Mutual Impedance Records** table is a [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and can be customized like any other case information display. The zero sequence mutual impedance records displayed in this table can be either read from a sequence data file, or created manually by choosing **Insert…** from the local menu.

The common fields displayed on the Mutual Impedance Records display are:

L1 From Bus, L1 To Bus, and L1 Ckt ID

These fields represent the from bus number, to bus number, and circuit identifier for the first mutually coupled line.

L2 From Bus, L2 To Bus, and L2 Ckt ID

These fields represent the from bus number, to bus number, and circuit identifier for the second mutually coupled line.

Mutual R, Mutual X

The mutual impedance, in terms of the resistance and reactance (per unit). The dot convention of the mutual impedance assumes the From bus of each line to be the dotted terminal, with the sign of the mutual impedance values being set according to this convention.

L1 Mut. Start, L1 Mut. End

The starting point and ending point of the mutually coupled portion of the first mutually coupled line. The values are between 0 and 1, and represent a position on the line as a percentage of the total line length. These fields are only used when evaluating an in-line fault to determine the affect of the mutual impedance on each side of the fault point on the line.

L2 Mut. Start, L2 Mut. End

The starting point and ending point of the mutually coupled portion of the second mutually coupled line. The values are between 0 and 1, and represent a position on the line as a percentage of the total line length. These fields are only used when evaluating an in-line fault to determine the affect of the mutual impedance on each side of the fault point on the line.

---

<a id="mutual-impedance-record-dialog"></a>

## Mutual Impedance Record Dialog

*Source: [`Content/MainDocumentation_HTML/Mutual_Impedance_Record_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Mutual_Impedance_Record_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Mutual Impedance Record** dialog can be used to modify or add zero sequence mutual impedance records to the sequence data for a case. When the dialog is opened using the **Show Dialog…** option from the [Mutual Impedance Records](#mutual-impedance-records) table local menu, the information for the record selected in the table will automatically be displayed. The information for that record can be modified, or a different record can be selected by selecting different lines in the Line 1 and Line 2 Identifier sections. Note that the drop down list of buses for the From Bus fields always contain all the buses in the case. However, once the From Bus has been selected, the drop down list of the corresponding To Bus field will only contain bus numbers of buses that are connected to the From Bus. If a mutual impedance record already exists for the lines selected, the information for that record will be displayed. If a mutual impedance record does not exist for the selected lines, then the mutual impedance fields will display default values. When the default values are changed, and either Save or OK are selected, a new mutual impedance record is added to the data.

---

<a id="fault-analysis-load-records"></a>

## Fault Analysis Load Records

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Load_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Load_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This dialog has the same functionality available as [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) displays. The purpose of this display is to tabulate the results of the fault analysis calculations. By default, the phase current magnitudes are displayed for the terminal end of the load. The phase current angles, as well as the sequence current magnitudes and angles, can be added by modifying the display using the [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog. The magnitude and angle direction reference is always given as out of the bus and into the load.

---

<a id="fault-analysis-switched-shunt-records"></a>

## Fault Analysis Switched Shunt Records

*Source: [`Content/MainDocumentation_HTML/Fault_Analysis_Switched_Shunt_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Fault_Analysis_Switched_Shunt_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This display has the same functionality available as [Case Information](04-model-explorer-and-case-information-part1.md#case-information-displays) displays. The purpose of this display is to tabulate the results of the fault analysis calculations. By default, the phase current magnitudes are displayed for the terminal end of the switched shunt. The phase current angles, as well as the sequence current magnitudes and angles, can be added by modifying the display using the [Display/Column Options](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) dialog. The magnitude and angle direction reference is always given as out of the bus and into the switched shunt.
