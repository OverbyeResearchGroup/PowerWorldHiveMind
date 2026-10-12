---
title: "Cases, Files and Formats"
part: "Files & Cases"
chapter_file: "03-cases-files-and-formats.md"
topics: 31
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Cases, Files and Formats

Opening, creating, closing and saving cases; every supported file format; project files.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (31)**

- [File Menu](#file-menu)
- [Case Formats](#case-formats)
- [Aux File Browser](#aux-file-browser)
- [General File Browser](#general-file-browser)
- [Auxiliary File Format (*.aux)](#auxiliary-file-format-aux)
- [GE EPC File Load Options](#ge-epc-file-load-options)
- [PTI RAW File Load Options](#pti-raw-file-load-options)
- [Opening a Simulation Case](#opening-a-simulation-case)
- [Opening a Oneline Diagram](#opening-a-oneline-diagram)
- [Recently Opened Cases](#recently-opened-cases)
- [Building a New Case](#building-a-new-case)
- [Building a New Oneline](#building-a-new-oneline)
- [Saving Cases](#saving-cases)
- [Saving a Oneline](#saving-a-oneline)
- [Close Oneline](#close-oneline)
- [Generator Capability Curves Format (*.gcp)](#generator-capability-curves-format-gcp)
- [Generator Cost Data Format (*.gcd)](#generator-cost-data-format-gcd)
- [Injection Groups Format (*.inj)](#injection-groups-format-inj)
- [Interface Data Format (*.inf)](#interface-data-format-inf)
- [Sequence Data Format](#sequence-data-format)
- [Exporting Onelines in Different Graphic Formats](#exporting-onelines-in-different-graphic-formats)
- [Saving Images As Jpegs](#saving-images-as-jpegs)
- [Saving Admittance Matrix and Jacobian Information](#saving-admittance-matrix-and-jacobian-information)
- [Working With GE EPC Files](#working-with-ge-epc-files)
- [Differences In File Formats](#differences-in-file-formats)
- [Overview of PowerWorld Simulator Project Files](#overview-of-powerworld-simulator-project-files)
- [PowerWorld Project Initialization Script](#powerworld-project-initialization-script)
- [Associating Project Files With Simulator](#associating-project-files-with-simulator)
- [Creating a New Project File](#creating-a-new-project-file)
- [Create Project Dialog](#create-project-dialog)
- [Opening an Existing Project](#opening-an-existing-project)

---

<a id="file-menu"></a>

## File Menu

*Source: [`Content/MainDocumentation_HTML/File_menu.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/File_menu.htm)*

The File menu is used to open and save either full cases or oneline diagrams, to create new cases, to open and load auxiliary files, to print and to exit Simulator. To access this menu you must click on the File tab in the left corner of the [Ribbon](02-simulator-ribbon.md#ribbons-user-interface).

On the right-hand side of the file menu is a list of recently opened cases you may also choose from. Other useful option on the file menu are

[Aux File Browser: Click on this to open a special dialog that can be used to browse for Auxiliary Files and open them quickly. See the help topic on the Aux File Browser for more information.](#aux-file-browser)

[General File Browser: Click on this to open a special dialog that can be used to browse for various power system files, peek inside those files at the header information stored in them, and open them quickly. See the help topic on the Aux File Browser for more information.](#general-file-browser)

![File Menu](images/File_Menu.gif)

---

<a id="case-formats"></a>

## Case Formats

*Source: [`Content/MainDocumentation_HTML/Case_Formats.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Formats.htm)*

Simulator supports a number of case formats. You can both open and save cases using most of the following formats:

PowerWorld Binary (\*.pwb) (Preferred Format)

For most users, the best choice of power flow case formats is the PowerWorld Binary format. This format stores the most complete set of case information but requires the smallest file sizes. Information stored in this format includes power flow data, economic parameters, case time variation/options values, and screen customizations. The only potential disadvantage of this format is that it is stored in binary form, which means that it cannot be viewed using a standard text editor. All the other formats are ASCII and thus readable in text editors such as Notepad.

One additional benefit of using the Powerworld Binary format is that with this format the case can be password-protected. This setting is available under **Misc. Power Flow \> Set Case Username and Password** in the **Case Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab.

PowerWorld Auxiliary File (\*.aux)

Simulator can save and load cases using the PowerWorld defined auxiliary file format. When the aux file format is chosen as the save file type in Simulator, the data describing the entire case is written to a text file described by Simulator’s auxiliary file format. These files can be considerably larger than PowerWorld Binary files, and generally should not be used unless otherwise necessary. Note that not all auxiliary files represent an entire case, and in fact in most cases do not. Only when an auxiliary file is created using the **Save Case As** option in the [File menu](#file-menu)[ ](02-simulator-ribbon.md#ribbons-user-interface) in Simulator does the auxiliary file contain all necessary information for loading the complete case in Simulator as an auxiliary file.

The [Complete Case Auxiliary File Export Format Description](09-auxiliary-files-and-script-commands.md#complete-case-auxiliary-file-export-format-description) can also be used for saving a case in the auxiliary file format. This is a newer preferred method of saving in this format and provides options for what type of data to save.

PowerWorld Auxiliary File - Secondary Keys (\*.aux)

This option is the same as choosing PowerWorld Auxiliary File *except* for the key identifiers for each record. Instead of using the primary keys (i.e. bus numbers) to identify devices in the data, the secondary keys (i.e. combination of bus name and nominal voltage) will be used as the identifiers in the saved file.

PowerWorld Auxiliary File - Labels (\*.aux)

This option is the same as choosing PowerWorld Auxiliary File *except* for the key identifiers for each record. Instead of using the primary keys (i.e. bus numbers) to identify devices in the data, the device primary [labels](07-object-properties-run-mode-and-general-part2.md#labels) will be used as the identifiers in the saved file.

PTI Raw Data Format (\*.raw)

This format is included primarily for interchange of power flow data with other packages. The PTI Raw Data format only contains power flow data.

PTI Raw Data Format (\*.raw) (with options)

This format is the same as the PTI Raw Format except that the [PTI RAW File Load Options](#pti-raw-file-load-options) dialog will be opened to allow user input for various options.

GE PSLF Format (\*.epc)

This format is included primarily for importing load flow data saved from GE's PSLF program. The EPC format is a text file format. This format does contain excess information that Simulator does not use, however Simulator does store this information for editing and writing back out to EPC format files.

GE PSLF Format (\*.epc) (with options)

This format is the same as the GE PSLF Format except that the [GE EPC File Load Options](#ge-epc-file-load-options) dialog will be opened to allow user input for various options.

Areva HDBExport Format (\*.csv)

Customers who use the Areva EMS system are able to use a command in the Areva EMS called HDBExport to save a comma-delimited file containing a complete description of the network model in the EMS system. The CSV file must be exported using appropriate flags and a specific *pattern file* in order to generate the format required by PowerWorld. Simulator cannot save files in this format. The resulting file will be a full-topology representation of the network model appropriate for use with the [Integrated Topology Processing](35-integrated-topology-processing.md#topology-processing-overview) add-on. For more information, please contact PowerWorld Corporation offices.

Simulator can also load display files created from an Areva EMS system. Please contact PowerWorld for more information.

BPA IPF Format (\*.net)

The BPA IPF Format is another format which can be read from our customers in China.

IEEE Common Format (\*.cf)

The IEEE Common Format is used to specify only power flow information. CAUTION: IEEE common format does not support many of the formats used in the PowerWorld packages, such as multiple loads and generators at a bus. Usually, IEEE Common Format is used only for inputting cases.

PowerWorld Simulator Project Files (\*.pwp)

Project files are described in [Overview of PowerWorld Simulator Project Files](#overview-of-powerworld-simulator-project-files).

ABB Spider EMS (\*.dat)

Text format that is exported from an ABB Spider EMS.

UCTE Data Exchange (\*.uct)

This is a format adopted by a number of European countries for the exchange of power flow and short circuit studies. Simulator cannot save files in this format.

Advanced settings for opening cases are available under the [File Management settings](10-power-flow-solution-and-options-part2.md#file-management-options).

Special Data Handling

Some special handling of data may occur when loading, appending, or saving data in the various formats. The following details some of what occurs in these situations but is not an all-inclusive list.

PowerWorld Binary (\*.pwb)

**Appending**

  - Appended data completely overwrites an existing record corresponding to the same bus number(s).
  - Branch elements are appended to a case only if both of their terminal buses exist.

PTI RAW Data Format (\*.raw)

**Reading**

  - Voltages at any radial buses are set to the voltages of the bus at the other end of the radial branch. This is done as long as there is no shunt charging or conductance on the branch, the branch is not a transformer, and not generators, loads, bus shunts, or switched shunts online at the radial bus. This is done to facilitate power flow convergence.
  - The participation factors of generators are set to the PMax MW of the unit and not the generator MVA Base.
  - When reading a RAW file that has comments on a given line, the comments will be loaded into the Memo field of the corresponding data record. However, the Memo field will not be written back out when saving a RAW file.
  - When reading switched shunt records, a mode of 3 will now be interpreted as controlling the Mvar output of generation. Mode 4 and 5 to not correlate to features in Simulator, so these are treated as shunts with a constant Mvar.
  - Will flag any non-transformer branch with R=0, B=0, and X\<0 as a series capacitor. This is especially important when using the Geomagnetically Induced Currents Add-on (GIC) as series caps will block the DC GIC flows.
  - When reading a RAW file there is a process to check the voltage magnitude and angle of star buses at the end of the RAW file read, and evaluate the mismatches at the three terminal buses of the three winding transformer. If it is determined that PowerWorld own estimate of what the voltage and angle should be at the star bus results in improved mismatches at the three terminal buses, the estimated voltage values to the star bus will be applied, otherwise the voltage magnitude and angle as read from the RAW file for the star bus will be kept.
  - When reading of the RAW file format if comments are found for data records of the format /\* \[ my label, my second label \] \*/, then labels will automatically be created for the object. The string parsing removes all leading and trailing /, \*, or space characters. Then if the remaining string starts with a \[ and ends with a \], PowerWorld will assume that what is inside the bracket is a comma-delimited list of strings representing labels.
  - When reading a RAW file, the options to specify the starting bus number of star buses are now stored in the computer registry.
  - When reading VSC DC Lines from a RAW file so that the DC MW Setpoint is interpreted as the "AC side" MW.
  - Modified reading of RAW file records for Bus, Gen, Load, Line and Transformer so that if an extra field is at the end of a record which is not expected, then we will try to read this in as a memo or label.
  - When reading a RAW file set the 'Default' Limit Set for contingency voltage rating set to B to match how bus specific limits are loaded; the Normal bus ratings are put in rating set A and the Contingency bus ratings are put in rating set B.

**Appending**

  - Appended data completely overwrites an existing record corresponding to the same bus number(s).
  - Branch elements are appended to a case only if both of their terminal buses exist.
  - Any new buses or branches that are created are now flagged as having just been added. This flag is then used as part of the pre-processing feature in the power flow solution to automatically estimate appropriate voltage magnitudes and angles for any existing or new branches and buses that become newly energized.
  - A field, **EPC File\\EPC Modification Status**, is populated to indicate whether an object is new or modified while reading. Even though this is a field that is normally associated with loading in an EPC file, the meaning is the same so the same field is used.

**Saving**

  - When saving a case as a PTI RAW files the switched shunt records will always write out at least one block. If none exists, a single block with 1 step and size equal to the present MVar output is written.
  - If a generator is using line drop or reactive current compensation, it will be set to regulate its own terminal bus with the setpoint set to the voltage of the terminal bus. Line drop and reactive current compensation is not supported in the RAW format.
  - The Simulator software version number and build date is added to a comment at the top of an exported PTI RAW file.
  - When saving a case as a PTI RAW format, if the option in Simulator is set to "DC Side", then the appropriate AC flow will be calculated and written out to the RAW file instead.
  - When writing to a RAW file labels can optionally be written as comments in the format /\* \[ my label, my second label \] \*/.
  - Generator records will be written out with WMOD = 1 when the FuelType =SUN (Solar) OR Unit Type = PV (Photovoltaic) within Simulator

GE PSLF Format (\*.epc)

**Reading**

  - If the latitude and longitude values are both zero when loading an EPC file, both entries will be ignored as invalid.
  - A designation of the area and zone of a GE branch and transformer will be stored when loading from an EPC file.
  - When loading multi-terminal dc lines from an EPC file, current limits for dc converters will not be enforced. This is set via a field, **Enforce Current Limit**, available with dc converters.
  - When reading in a GE EPC file, the "aloss" parameter is usually rounded to one bus or the other to be expressed in terms of the "From End Metered" field (except in the case of Multi-Terminal DC converters and two-terminal DC lines).
  - Simulator does not consider load IDs to be case sensitive. If multiple loads are found with the same ID that vary only by the case of the characters, Simulator will attempt to create a unique ID for each load. An appropriate message will appear in the message log.
  - Voltages at any radial buses are set to the voltages of the bus at the other end of the radial branch. This is done as long as there is no shunt charging or conductance on the branch, the branch is not a transformer, and not generators, loads, bus shunts, or switched shunts online at the radial bus. This is done to facilitate power flow convergence.
  - The IDs of bus shunts (Bus Shunt Fixed Control Mode in Simulator) will be changed to new unique IDs if SVDs are read in with the same ID at the same bus. Previously, switched shunts with the same ID at the same bus would just be overwritten. SVDs with the same ID can still overwrite each other and Bus Shunt Fixed with the same ID can still overwrite each other.
  - If an area's slack bus is specified to be a bus that is not inside the area, the area will be set off AGC and the area slack designation ignored.
  - If the generators at an area slack bus are not assigned to the same area as their terminal bus, the generator area designations are changed to the area of the terminal bus.
  - The option for using GE Base Load Flag \> 0 to prevent Post-CTG response in Simulator is used by default.
  - The participation factors of generators are set to the PMax MW of the unit and not the generator MVA Base.
  - The scheduled voltage for devices controlling the voltage at a bus is set with the bus in the EPC file. In Simulator this is specified with individual devices, i.e. switched shunts and generators. The voltage setpoints for these devices will be set to the scheduled voltage specified with the bus.
  - The ID field for Breaker data will be used as the circuit ID for the breaker if the length of this field is 1 or 2. If the ID field is blank or greater than two characters, the circuit ID will be dynamically assigned. The ID field will always populate the EMS ID field in Simulator. When writing an EPC file, the ID field for Breaker data will be written using the EMS ID field if this is not blank. If this is blank the circuit ID field will populate the ID field in the EPC.
  - When reading transformer records in the EPC file will now recognize a negative "type" as an indication that control on this device is disabled.

**Appending**

  - Appended data completely overwrites an existing record corresponding to the same bus number(s).
  - Branch elements are appended to a case only if both of their terminal buses exist.
  - Any new buses or branches that are created are now flagged as having just been added. This flag is then used as part of the pre-processing feature in the power flow solution to automatically estimate appropriate voltage magnitudes and angles for any existing or new branches and buses that become newly energized.
  - A field, **EPC File\\EPC Modification Status**, is populated to indicate whether an object is new or modified while reading.
  - If a new three-winding transformer is entered which uses a bus number which is already used as a star bus by another three-winding transformer this will not be allowed and a new bus number will automatically be chosen.
  - If appending an EPC file causes a transformer branch to be converted to a normal branch, a log warning message will show this.
  - If the scheduled voltage for a bus is specified, the voltage setpoints for switched shunts and generators that are regulating this bus are also properly updated.
  - Elements with a status value of -4 will have the **EPC File\\Flagged for Delete in EPC** flag set to YES. Simulator will default these elements to in service.

**Saving**

  - When saving a case as a GE EPC file the Multi-Terminal DC converters will write out the "aloss" parameter in a manner consistent with the EPCL file mtTAP.p
  - When using the [Present Topological Differences from Base Case](08-view-case-data-tools.md#present-topological-differences-from-base-case) tool and the removed elements are saved in the GE EPC file format the elements are saved with a status value of -4.
  - If a generator is using line drop or reactive current compensation, it will be set to regulate its own terminal bus with the setpoint set to the voltage of the terminal bus. Line drop and reactive current compensation is not supported in the EPC format.
  - When saving a switched shunt that is on either Generator Mvar or Wind Mvar control, the shunt will be written as fixed (locked) control.
  - If the GE Ohmic Data Flag for branches is set to 1, R and X will be written in ohms and B in microMhos.
  - Saving a removed multi-section line in the EPC format should correctly write the sections of the multi-section line with a status of -4. GE flagged for delete flag for multi-section line will be true if any section is flagged for delete.
  - The brktype field will be written based on the Branch Device Type specified in Simulator. When writing a Disconnect the EMS CBTyp field in Simulator will be used if it is not blank. The brktype field in an EPC file has more options for different types of disconnects that are only identfied as Disconnects within Simulator and the EMS CBTyp field might contain a more specific type.
  - When writing out transformers to an EPC file, if transformer is Fixed we will now always write type = 1. PowerWorld has a separate field indicating if a transformer's control is enabled and if it's disabled we write a negative sign on the type. However in EPC file type=1 means there is no control at all, so writing a -1 is strange as it means the transformer's control is disabled, but it has no control anyway. To avoid confusion, we just write a 1 instead.

Areva HDBExport Format (\*.csv)

**Reading**

  - When loading the hdbexport file, modified to automatically add two labels to each transmission line. One label starts with the "from" substation name and the other label starts with the "to" substation name.
  - At the end of reading in an hdbexport CSV file, if any CBTyp values were encountered that were not recognized a dialog box will appear prompting the user to designate a Branch Device Type for each CBTyp (See the **hdbexport Files** section in [File Management](10-power-flow-solution-and-options-part2.md#file-management-options) for more explanation on this).
  - Additional bus labels are added when reading the MEAS records.
  - When loading the hdbexport file, will read three-winding transformer records using the XF record's ID\_XFMR field.
  - When loading the hdbexport file, will read NDLIM records and the entries are read into a bus record's bus-specific limit monitoring settings allowing to be specific high/low voltage for particular nodes.
  - When reading the hdbexport CSV file there is an option about whether or not to create 3-winding transfomers.
  - When reading the hdbexport CSV file there is the ability to choose the default label delimiter.
  - Added Primary field to specify which label specification should be used as the primary label with the custom Areva label definitions used with hdbexport files. This will be assigned when loading hdbexport files.
  - Modified reading of CP records from hdbexport CSV files when VTARGET is not defined. We now set the RegHigh/RegLow = 1.4/0.6 for shunts and also set AutoControl = NO.

---

<a id="aux-file-browser"></a>

## Aux File Browser

*Source: [`Content/MainDocumentation_HTML/AuxFileBrowser.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/AuxFileBrowser.htm)*

Added in Version 21

Choose **AUX File Browser** from the [File Menu](#file-menu) to open the Aux File Browser. The Aux File Browser is a very simple dialog on which you may define file paths on your computer to search for [PowerWorld Auxiliary files](#auxiliary-file-format-aux). After creating the list of Auxiliary Files, you may then double-click on a particular AUX files to open it. This makes a very simple dialog that you can leave open in Simulator and conveniently double-click to open commonly used AUX file. Another useful dialog is the [General File Browser](#general-file-browser) which can be used to search for PWB, PWD, AUX, AXD, TSR, EPC, and RAW files. See that [File Browser](#general-file-browser) topic for more information on this.

An image of the dialog is shown below. The buttons on the right of the dialog all exist to help define the list of File Paths in which you would like to search for AUX files. The buttons are as follows.

Load AUX

Click this button after selecting one of the auxiliary files on the left of the dialog to open the selected AUX file.

Add Path

Click on Add Path to choose another directory of your computer in which you would like to search for AUX files.

Forget Path

Click this button after selecting one of the paths on the left of the dialog to forget (remove) this path from the search for AUX files.

Change Name

Click this button to give your own name to the folder on the left showing the list of file paths

Change Path

Click this button after selecting one of the paths on the left of the dialog to assign a different path in its place

Forget Invalid Paths

Some file paths may not be valid locations on your computer. Click this button to remove those paths from the AUX file Browser

Refresh

Click this button to refresh of available AUX files contained in the search paths specified

Cancel Refresh

Click this button to cancel the refresh of available AUX files contained in the search paths specified.

Auto Refresh check box

Check this box to automatically refresh the list of files whenever the list of paths is updated.

![FileBrowserAux](images/FileBrowserAux.png)

---

<a id="general-file-browser"></a>

## General File Browser

*Source: [`Content/MainDocumentation_HTML/FileBrowserGeneral.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/FileBrowserGeneral.htm)*

Added in Version 22

Choose **General File Browser** from the [File Menu](#file-menu) to open the File Browser. The File Browser is a special dialog that can be used to choose a list of file paths on your computer in which you would like to search for PowerWorld related files. The File Browser dialog is shown at the end of this help topic. The first thing to do when using the File Browser it to choose a list of paths in which to search for files. This is done in the exact same manner as done with the [Auxiliary File Browser](#aux-file-browser) dialog. For help on the buttons at the top of the File Browser which are used to specify the search pathsee the [Auxiliary File Browser](#aux-file-browser) help topic.

After this is a row of check boxes which allow you to choose which file types to search for with choices of PWB, PWD, AUX, AXD, TSR, RAW, and EPC. We expect to add additional file types in the future, but these are the available file types as of the release of Simulator Version 22. After choosing a list of search paths, Simulator will search all the files in those search paths for files with the extensions chosen.

Once the list of files is populated in the table, you may right-click on this list and choose options either **Open Selected File** or **Delete Selected Files**.

There are certain fields which are available for all file types and these fields are self-explanatory and listed next: **File Date Modified**, **File Directory**, **File Extension**, **File Name**, **File Path**, **File Size (KB)**.

For PWB, EPC, and RAW files, while searching PowerWorld peeks inside the files to collect summary information about each file. The File Browser can then provide special summary information which can then be [searched](04-model-explorer-and-case-information-part3.md#search-for-text-dialog), [sorted](04-model-explorer-and-case-information-part1.md#sorting-records), and [filtered](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) to help you find files of interest to you. A descriptions of each file type any special features for that file type is described in the next table.

Type

Description

Special Features

**Special Fields Available for PWB Files saved in Version 22 or later**

PWB

[PowerWorld Binary Case](#case-formats)

The [Case Description](05-case-information-displays-by-object-part1.md#case-description) will be shown at the bottom of the dialog in the Header Section

Any [Case Comments](05-case-information-displays-by-object-part1.md#case-description) will be shown on the bottom right portion of the dialog when choose a PWB file.

In addition to these, you may [configure the case information displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays) to show columns that will be populate for PWB files as follows:

  - **Header** field will show the Case Description in the form of a field which will allo you to use either [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) the contents of the Header or use the case information [Search for Text](04-model-explorer-and-case-information-part3.md#search-for-text-dialog) feature to help find the file you're interested in

  - **EXE Build Date when saved** field will show the EXE file creation date of the pwrworld.exe file used to save the PWB file.

  - **Onelines** field will show a list of PWD files that are configured to automatically open when load this PWB file.

  - **Dozens of other Fields**: Starting with the PWB format of PowerWorld Version 22, we also store a large amount of summary information at the beginning of the PWB file which can then be parsed by the File Browser to show information in columns of the case information display. These include the columns shown to the right which mimic the same fields available on the [Case Summary Dialog](05-case-information-displays-by-object-part1.md#case-summary). Using the [sort features](04-model-explorer-and-case-information-part1.md#sorting-records) of the case information displays can be especially helpful.

![FileBrowserCaseFields](images/FileBrowserCaseFields.png)

PWD

[PowerWorld Oneline Diagram](15-using-onelines-tools-and-options.md#oneline-diagram-overview)

none

AUX

[PowerWorld Auxiliary File](#auxiliary-file-format-aux)

none

AXD

[PowerWorld Display Auxiliary](#auxiliary-file-format-aux)

none

TSR

[PowerWorld Transient Stability Results File](37-transient-stability-analysis-dialog-part1.md#storage-to-hard-drive)

These are files written to file by the transient stability simulation. The files can get very large when a large case is storing a large amount of simulation results. The File Browser can be a convenient location to find these files and delete the ones you no longer need.

RAW

[PSS/E Case](#case-formats)

The first three rows of text in a RAW file represent a case header. The File Browser will peek inside these files and show these in the Header section in the bottom left portion of this dialog.

  - **Header** field will show the this same text in the form of a field which will allo you to use either [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) the contents of the Header or use the case information [Search for Text](04-model-explorer-and-case-information-part3.md#search-for-text-dialog) feature to help find the file you're interested in

EPC

[PSLF Case](#case-formats)

The first part of the EPC file represent a case header. The File Browser will peek inside these files and show these in the Header section in the bottom left portion of this dialog.

  - **Header** field will show the this same text in the form of a field which will allo you to use either [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering-advanced) the contents of the Header or use the case information [Search for Text](04-model-explorer-and-case-information-part3.md#search-for-text-dialog) feature to help find the file you're interested in

![FileBrowser](images/FileBrowser.png)

---

<a id="auxiliary-file-format-aux"></a>

## Auxiliary File Format (*.aux)

*Source: [`Content/MainDocumentation_HTML/Auxiliary_Files.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Auxiliary_Files.htm)*

PowerWorld has incorporated the ability to import data from data sources other than power flow models into PowerWorld Simulator. The text file interface for exchanging data, as well as for executing batch script commands, is represented by the auxiliary files. The script language and auxiliary data formats are incorporated together.

Script/Data files are called auxiliary files in Simulator and typically have the file extension .AUX. These files mostly contain information about power system elements and options for running the various tools in Simulator. They do not contain any information about the individual display objects contained on a one-line diagram. There are separate files called display auxiliary files that are available for importing display data/to from Simulator in a text format. These files are distinguished from the data auxiliary files by using the extension .AXD. The format syntax for these two types of files is identical, but different object types and script commands are supported by each and require that the files be read separately.

Both file types will generically be referred to as auxiliary files. An auxiliary file may be comprised of one or more DATA or SCRIPT sections. A DATA section provides specific data for a specific type of object. A SCRIPT section provides a list of script actions for Simulator to perform. Additionally, there are places in Simulator where script commands can be used outside the confines of an auxiliary file.

A complete description of the DATA and SCRIPT sections for both case auxiliary (.AUX) and display auxiliary (.AXD) files can be found in a separate PDF document. This document is included with the installation of Simulator and can be opened from the **Window ribbon tab** by selecting **Auxiliary File Format**. If the file does not open for some reason, the file can obtained in the help directly .

There are a few options within the user interface which directly relate to the AUX and AXD files. These options are available on both the [Case Information Toolbar](04-model-explorer-and-case-information-part1.md#case-information-toolbar) and on the [Simulator Options Dialog under the Case Information Category](10-power-flow-solution-and-options-part2.md#case-information-display-options). The import options are as follows

  - **Key Fields to Use** : specifies how various fields that refer to an object are written or displayed. For example the ObjectID field available with most object.
  - **Use Concise Variable names and Auxiliary File Headers** : Specifies if the concise variable names are used as well as new concise AUX file headers when writing to an auxiliary file or when showing variable names in the column headers of case information displays

The following Auxiliary DATA seconds are written using the legacy variable names and using the older auxiliary file header using the keyword DATA.

DATA (Gen, \[BusName\_NomVolt, GenID, GenPostCTGPreventAGC, GenParFac:1, CTGMakupGen, GenUseLDCRCC, GenXLDCRCC\],

AUXDEF, YES)

{

"Gen 'Texan\_69.0' '1'" "NO" same 22.0 "NO" 0.0001

"Gen 'Jet\_69.0' '1'" "YES" 88.0 "" "PostCTG" 0.0512

}

DATA (Gen, \[BusNum, GenID, GenPostCTGPreventAGC, GenParFac:1,

CTGMakupGen, GenUseLDCRCC, GenXLDCRCC\], AUXDEF, YES)

{

"Gen 77 '1'" "RESPOND" same 0.0 "NO" 0.0001

"Gen 55 '1'" "NO" same "" "NO" 0.0001

}

By changing to use the concise header format, concise variable names, and the special field ObjectID, the same information can be written in an Auxiliary file as follows instead.

Gen (ObjectID, CTGPreventAGC, CTGPartFact, CTGMaxResp, UseLineDrop, Xcomp)

{

"Gen 'Texan\_69.0' '1'" "NO" same 22.0 "NO" 0.0001

"Gen 'Jet\_69.0' '1'" "YES" 88.0 "" "PostCTG" 0.0512

"Gen 77 '1'" "RESPOND" same 0.0 "NO" 0.0001

"Gen 55 '1'" "NO" same "" "NO" 0.0001

}

---

<a id="ge-epc-file-load-options"></a>

## GE EPC File Load Options

*Source: [`Content/MainDocumentation_HTML/GE_EPC_File_Load_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GE_EPC_File_Load_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The GE EPC File Load Options dialog will open when choosing to open or save a GE EPC case "with options".

![GE EPC File Load Options](images/GE_EPC_File_Load_Options.gif)

EPC File Version

Set this to determine what version of the EPC file is being read or saved.

What To Do With Multi-Section Lines

This option is only relevant when loading in data. This option allows multi-section lines to be maintained as they are defined in the file or have their sections merged into a single equivalent line.

Assumed Generator Var Limit Deadband

This option is only relevant when loading in data. This options specifies a deadband used to determine if generators should be on or off AVR control. If the difference between the Max and Min Mvar output of a generator is less than this deadband, Simulator will set the AVR flag for a generator to NO.

GE Base Load Flag Setting

When opening a file, the GE Base Load Flag setting will be used to set the Post-CTG Prevent AGC Response field in Simulator. The caption will be the following: **if GE Base Load Flag \> 0, then Post-CTG Prevent Response = YES, else Post-CTG Prevent Response = NO**. Note: This is the default setting.

When loading an EPC file, the GE Base Load Flag is used to set the **Governor Response Limits** field with a generator. This field is used to determine governor response settings during a transient stability run. This field is set directly to the GE Base Load Flag regardless of the input option setting. The possible settings are 0 = Normal, 1 = Down Only, and 2 = Fixed.

When saving a file, the caption will be the following: **if Post-CTG Prevent Response = YES, then set GE Base Load Flag = 2, else set GE Base Load Flag = 0 (Only done if Governor Response Limits = Normal)**. The Post-CTG Prevent AGC Response field in Simulator will be used to set the Base Load Flag setting in the EPC file only if the Governor Response Limits field is set to Normal for a generator. Otherwise, the GE Base Load Flag will be set to the number corresponding to the Governor Response Limits field: Down Only = 1 or Fixed = 2.

Estimate voltages at new buses and smooth angles across new lines

This option is only available when appending data to an existing case. By default, Simulator assumes that the voltages and angles in the new data are not known and must be estimated based on existing voltages already in the case. This assumption could be wrong if appending large sections of a case, i.e. such as a new island, or providing voltages that are already good estimates in the appended data. There is no way to determine for sure if the voltages provided in the appended data are "good" or not, thus the user can decide this.

Filter By

If desired, only data in with specific areas, zones or owners can be loaded from the EPC file by using this option. Checking the Area/Zone/Owner Filters box will display the edit boxes for entering the Area, Zone, and Owner numbers. You can also check the Include Tie Lines box to read in branches for which only one of the two terminal buses is designated with the specified area, zone or owner. Leaving this box unchecked will force the requirement that BOTH branch terminal buses meet the specified areas, zones or owners for it to be read from the EPC file.

See the [Case Formats](#case-formats) topic for information on special handling of data that occurs when loading a case using the GE EPC file format.

---

<a id="pti-raw-file-load-options"></a>

## PTI RAW File Load Options

*Source: [`Content/MainDocumentation_HTML/PTI RAW File Load Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PTI RAW File Load Options.htm)*

This dialog contains options related how Simulator reads (or writes) the PTI RAW file. The following options are on the dialog:

RAW File Version

This option is available for both reading and writing the RAW file. Simply choose the appropriate version number from the drop-down menu.

Add comments for object labels at the end of RAW file records

This option is available for both reading and writing the RAW file. Simply check to append object labels as comments to the end of data records.

Creation of transactions for loads in a different area than their terminal bus

This is only relevant when loading a RAW file. The option allows the user to select if transactions should be created for loads that are in different areas than their terminal buses.

Loads may be assigned to a different area than the load’s terminal bus. PTI offers an option that allows the user to ignore this assignment when calculating the tie-line flow for an area.

(AREA INT CODE = 1 FOR LINES ONLY)

(AREA INT CODE = 2 FOR LINES AND LOADS)

Simulator does not allow you to define a load this way and then choose to ignore it. Most RAW files that PowerWorld has seen seem to be solved ignoring the loads that are in different areas than their terminal bus by using the "lines only" option. To overcome this, when PowerWorld reads a RAW file, [MW Transactions](05-case-information-displays-by-object-part3.md#mw-transactions-display) can be automatically created with the ID "RAW\_LOAD". These transactions are between the load’s area and its terminal bus and are created so that the export from each area correctly matches a case solved using "lines only". If you know that your case was solved using "lines and loads", then you would not want to add the transactions. There are three options for how to deal with these possible interchange differences. The default is to let Simulator determine what is best based on the input data. If it is known what option was used in PTI, then the user can choose to either create the MW transactions or not create them. See the topic **Add and Remove transactions due to tie-line loads** with **[File Management Options](10-power-flow-solution-and-options-part2.md#file-management-options)** for more information about adding or removing these transactions after the case has been loaded.

If not loading the RAW file with options, Simulator will determine based on the input data whether or not the transactions representing loads that are in different areas than their terminal buses need to be created.

When loading the RAW file with options, the user can select how to number the star buses of three-winding transformers. The options are to use a number that is near the primary bus number, start numbering above the maximum bus number, or specify a number at which to start the numbering.

When reading a RAW file that has comments on a given line, the comments will be loaded into the Memo field of the corresponding data record. However, the Memo field will not be written back out when saving a RAW file.

Three-Winding Transformer Star Bus Numbering.

The PTI RAW format does not include separate buses which represent the internal star buses of a three-winding transformer. When loading a RAW file, Simulator will automatically create buses for these star buses. This option provides the user a choice of how these star buses are numbered.

Estimate voltages at new buses and smooth angles across new lines

This option is only available when appending data to an existing case. By default, Simulator assumes that the voltages and angles in the new data are not known and must be estimated based on existing voltages already in the case. This assumption could be wrong if appending large sections of a case, i.e. such as a new island, or providing voltages that are already good estimates in the appended data. There is no way to determine for sure if the voltages provided in the appended data are "good" or not, thus the user can decide this.

---

<a id="opening-a-simulation-case"></a>

## Opening a Simulation Case

*Source: [`Content/MainDocumentation_HTML/Opening_a_Simulation_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Opening_a_Simulation_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The most common first step in using Simulator is to open a case. When a case is opened, any associated oneline files are also opened. To open a case, either select it from the [list of recently opened cases](#recently-opened-cases) in the file menu or

  - Select **Open Case** from the [File menu](#file-menu) to display the Open Dialog.
  - In the **Type of Files** box, select the desired file type. By default, the PowerWorld Binary type is selected (\*.PWB). The PowerWorld Binary is the preferred file type, providing the most comprehensive power system information along with the smallest size and quickest load time. Other file types include the PowerWorld Case type, PowerWorld Auxiliary file, PTI Raw Data formats, GE EPC text format, and IEEE Common Format. Please see [Case Formats](#case-formats) for more details.
  - In the list of cases, click on the desired case.
  - Click OK.

When opening an existing Simulator case, you may see one or more oneline diagrams pop up. When opening a power flow case created with another program, a oneline may not be available. However, you can easily create a oneline for such a case using the [Edit Mode](11-building-onelines-network-objects.md#edit-mode-general-procedures).

The Bus Records table of the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) will be displayed by default when opening a case that does not have any associated oneline diagrams.

If you are in the Edit Mode, you can modify the case. See [Edit Mode Overview](11-building-onelines-network-objects.md#edit-mode-overview) for details.

If the case has validation errors, the mode is immediately switched to Edit Mode. You must correct the validation errors shown in the message log before you can use the Run Mode to solve the case.

---

<a id="opening-a-oneline-diagram"></a>

## Opening a Oneline Diagram

*Source: [`Content/MainDocumentation_HTML/Opening_a_Oneline_Diagram.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Opening_a_Oneline_Diagram.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator supports oneline diagrams that have been developed using its Edit Mode tools.

When a case is opened, any associated onelines are usually opened, as well. Additionally, oneline diagrams can be opened directly from any existing onelines using [oneline links](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files). However, you may also directly open a oneline diagram using the following procedure:

  - Select **Open Oneline** from the [File menu](#file-menu).
  - Choose the file type you would like to open by using the drop-down in the bottom right-hand corner of the Open dialog. The **Available File Type Options for Opening a Oneline** section details how the different file types work.
  - Alternately, you can use the file menu choices to open a oneline using a particular linking. The file menu choices are available on the submenu when selecting **Open Oneline** from the Application Button. The linking choices listed in the **Available File Type Options for Opening a Oneline** section found below are available with this option (except for the PTI Draw File format). When you select a particular linking option, you will be prompted if you want to save this as your default type. You can override the default by selecting a different linking option the next time that you open a oneline.
  - In the list of available oneline files, click on the desired oneline.
  - Click OK.

Available File Type Options for Opening A Oneline

  - **Oneline Display File (\*.pwd)** - This is the standard binary file used to store oneline diagrams. When this option is selected, oneline display objects involving buses will be linked to their corresponding case data objects through bus numbers.
  - **Oneline Display File (Name\_kV linking) (\*.pwd)** - This is the standard binary file used to store oneline diagrams, but a special table stored with the file is used to link the oneline display objects involving buses to their corresponding case data objects using bus name and nominal kV combinations instead of bus numbers and renumber the bus numbers of the display objects to match the current case. This option is useful when opening a oneline that was created with a different case than the one currently in memory and the current case has undergone some bus renumbering, but the bus names and nominal kV levels remain the same as in the original case.
  - **Oneline Display File (Label linking) (\*.pwd)** - This is the standard binary file to store oneline diagrams, but a special table stored with the file is used to link the oneline display objects by [label](07-object-properties-run-mode-and-general-part2.md#labels) to their corresponding case data objects. Only objects that allow the use of labels will be linked in this manner. If a linking via label cannot be found, the oneline object will be unlinked. This option is useful when opening a oneline that was created with a different case than the one currently in memory and the current case has undergone bus renumbering, but the labels remain the same as in the original case.
  - **PTI Draw File (\*.drw)** - File format supported by PSS/E. All functionality of that file format may not be fully supported in Simulator.
  - [Display Auxiliary File](#auxiliary-file-format-aux) **(\*.axd)** - This is a text file used to store the oneline display objects.
  - **Areva Dispaly File (\*.ddl)**- Simulator can load display files created from an Areva EMS system. Please contact PowerWorld for more information.

You may open as many onelines as you like, and even multiple copies of the same oneline.

The following topics may be helpful when opening onelines created with a different case:

[Refresh Anchors](14-editing-onelines.md#refreshing-anchors)

[Bus Renumbering Dialog](19-edit-mode-tools.md#bus-renumbering-dialog)

Three-Winding Transformer Star Bus Automatic Renumbering

When opening a oneline diagram by using one of the PWD options, the star buses of three-winding transformers will automatically be renumbered to match the current power flow case. This is done without any input from the user. This is done because some power flow case file formats do not require that star bus numbers remain constant, therefore, if opening a oneline diagram with a power flow case other than the one with which is was created, there is a good possibility that the star bus numbers will be different. The renumbering is accomplished using a table saved with the PWD file that contains the three-winding transformers. If using the name\_kV linking to open a oneline, the three-winding transformers in the internal table are identified by name\_kV when doing the star bus updates. If the transformer cannot be found when using either the number or name\_kV linking, its star bus will not be renumbered.

---

<a id="recently-opened-cases"></a>

## Recently Opened Cases

*Source: [`Content/MainDocumentation_HTML/Recently_Opened_Cases.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Recently_Opened_Cases.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A numbered list of the most recently opened cases appears in the Recent Files list when you click on the [File menu](#file-menu). Simply choose a case from the list to open the case.

---

<a id="building-a-new-case"></a>

## Building a New Case

*Source: [`Content/MainDocumentation_HTML/Building_a_New_Case.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Building_a_New_Case.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To create a new case in Simulator, select **New Case** from the [File menu](#file-menu). After asking you whether or not to save the current working case (if one exists), Simulator will automatically switch to Edit Mode. The screen will turn to the default background color, indicating that you can begin to build the new case.

New users may wish to view the [Tutorial Links](49-distributed-computing-and-tutorials.md#tutorials) for further guidance.

---

<a id="building-a-new-oneline"></a>

## Building a New Oneline

*Source: [`Content/MainDocumentation_HTML/Building_a_New_Oneline.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Building_a_New_Oneline.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This option enables you to create a new oneline diagram. It is accessible from either the Edit or Run modes by choosing **New Oneline** from the [File menu](#file-menu). When you select it, the application will automatically switch to Edit Mode, from which you can construct the new oneline.

New users may wish to view the [Tutorial Links](49-distributed-computing-and-tutorials.md#tutorials) for further guidance. Additionally, the following topics may be of some assistance:

[Using the Insert Palettes](13-building-onelines-graphics-and-insertion.md#using-the-insert-palettes)

[Oneline Conditional Display of Objects](17-oneline-view-printing-and-contouring.md#oneline-conditional-display-of-objects)

[Using the Oneline Alignment Grid](14-editing-onelines.md#using-the-oneline-alignment-grid)

---

<a id="saving-cases"></a>

## Saving Cases

*Source: [`Content/MainDocumentation_HTML/Saving_Cases.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Cases.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator allows users to save case information in several different formats. To call up the Save As dialog, select **Save Case As** from the [File menu](#file-menu). The format in which the file will be saved depends upon the value of the **Save as Type** field of the dialog. Simulator can save cases in PowerWorld binary format (the default), PowerWorld Auxiliary file format, PTI raw data, GE PSLF format, BPA IPF format, and the IEEE common format. Please see [Case Formats](#case-formats) for more details on the various case formats available.

To force saving a case with comments, a submenu exists for the **Save Case** and **Save Case As** menu items. Select the **... with Comment...** to open the comment dialog. More information about Case Comments can be found in the [Case Description](05-case-information-displays-by-object-part1.md#case-description) topic.

To convert a case to a different format, follow this procedure: 

  - Select **Open Case** from the [File menu](#file-menu).
  - In the **Files of Type** box, select the desired file type. By default, the PowerWorld Binary type is selected (\*.PWB).
  - Select the name of the desired case and click *OK*.
  - Select **Save Case As** from the [File menu](#file-menu).
  - Change the **Save as Type** setting to match the desired file type, designate the name with which to save the file, and click *OK*.

To simply save the case with its current name and format, select either **Save Case** from the [File menu](#file-menu) or the **Save Case** button on the Quick Access toolbar.

---

<a id="saving-a-oneline"></a>

## Saving a Oneline

*Source: [`Content/MainDocumentation_HTML/Saving_a_Oneline.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_a_Oneline.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Select **Save Oneline** from the [File menu](#file-menu) to save the currently selected oneline file.

Select **Save Oneline As** from the [File menu](#file-menu) to save the currently selected oneline file with a different name or format. You may overwrite existing files.

For both the Save Oneline and Save Oneline As options, only the oneline diagram is saved; the case (i.e. the power flow model) is not written to disk.

---

<a id="close-oneline"></a>

## Close Oneline

*Source: [`Content/MainDocumentation_HTML/close_oneline.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/close_oneline.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To close a oneline diagram, select **Close Oneline** from the [File menu](#file-menu), right-click on the background of the oneline diagram and select **Form Control \>** **Close** from the local menu, or click the Close button on the oneline itself. This will prompt you to save the oneline if changes have been made since the last save. Note that this does not close the current case, just the oneline diagram. The power system data is still loaded, and case simulations can be run with the oneline closed.

---

<a id="generator-capability-curves-format-gcp"></a>

## Generator Capability Curves Format (*.gcp)

*Source: [`Content/MainDocumentation_HTML/Generator_Capability_Curves_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Capability_Curves_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These files are outdated for Simulator version 8.0 and later. Their descriptions are still maintained here as they can still be read into Simulator. However, they can no longer be saved. These records are now stored in [Auxiliary Script/Data Files](#auxiliary-file-format-aux).

The generator capability curves are used to model the dependence of the generator reactive power limits and the generator’s real power output. The generator reactive capability curves files have the following format, with one generator per line:

**num or name, ID, P1, Q1,max,Q1,min, P2, Q2,max, Q2,min** **... Pn, Qn,max, Qn,min**

where

**num/name** the generator’s bus number or the bus’ name in single quotes,

**ID**  the generator’s single character id,

**Pi**  a generator MW output value,

**Qi,max** **and Qi,min**  the associated maximum and minimum reactive power limits.

Version 11 and later of Simulator allow for an unlimited number of capability curve points to be read from the gcp file. Up to 10 different P/Qmax/Qmin values may be specified in older versions of Simulator.

---

<a id="generator-cost-data-format-gcd"></a>

## Generator Cost Data Format (*.gcd)

*Source: [`Content/MainDocumentation_HTML/Generator_Cost_Data_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Generator_Cost_Data_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These files are outdated for Simulator version 8.0 and later. Their descriptions are still maintained here as they can still be read into Simulator. However, they can no longer be saved. These records are now stored in [Auxiliary Script/Data Files](#auxiliary-file-format-aux).

The generator cost data file contains the parameters used to model the generator operating costs. Each record in the generator cost data file specifies the operating cost model for a single generator. The cost model may be either a cubic polynomial or a piecewise linear curve. When reading a file of generator cost data records, Simulator will open the **Cost Curve Data Options Dialog** below. This dialog gives you additional control over the input and process of generator cost information.

Each generator cost data record begins with the fields

**num or name, ID,**

where

**num/name**  the generator’s bus number or the bus’ name in single quotes,

**ID**  the generator’s single character id,

Following the ID field is an optional single-character field **CostModel** that specifies the type of cost model. If **CostModel** is ‘**CUBIC**’ or is not specified, the record describes a cubic cost model and thus concludes with the following fields:

 **ai, bi, ci, di, FuelCost ParFac**

where

**ai, bi, ci, di** input-output curve coefficients; see [Generator Cost Information](06-object-properties-edit-mode-part1.md#generator-cost-description) for details,

**fuelcost **fuel cost, expressed in price per Mbtu,

****ParFac**** ****generator participation factor**.**

If, on the other hand, **CostModel** is ‘**PLIN**’, the record describes a piecewise linear cost model. The remainder of the record specifies pairs of generator output and corresponding generator cost:

 **FixedCost MW1** **IncCost1** **MW2** **IncCost2** **… MWn** **IncCostn** **MWneg ParFac**

where

**FixedCost **Operation cost independent of the generator’s MW output; expressed in $/Hr,

**MWi, IncCosti**  Output/incremental cost data point pairs that define the incremental cost model for the generator (note IncCosti has the units $/MWhr),

**MWneg** An arbitrary negative value used to terminate the record,

**ParFac** ****generator participation factor.

Cost Curve Data Options Dialog

The **Cost Curve Data Options Dialog** gives you additional control over the input and processing of generator cost information. It appears when you try to read generator cost information from an [auxiliary data file](#auxiliary-file-format-aux) (either [.aux](#auxiliary-file-format-aux) or [.gcd](#)). 

To command Simulator to turn all units onto automatic generation control (AGC) for which it reads a cost data record, check the first checkbox. This box has the rather lengthy label "If a unit for which a cost curve is read is not on AGC, Simulator should set it on AGC." In other words, if a cost curve is read for a particular generator, that generator will be set on AGC if this box is checked.

Cross-compound is a generator architecture sporting a single boiler and two turbines, one operating at high pressure and the other operating at low pressure. The existence of cross-compound units may complicate the modeling of generator cost characteristics, because sources for this information tend to describe the cost associated with the tandem, whereas Simulator’s economic dispatch will try to dispatch the two parts of the cross-compound unit as two separate units. To address this problem, Simulator gives you the option to lump the properties of the high- and low-pressure turbines into a single unit. It consolidates the two components by adding together their maximum MW outputs, minimum MW outputs, and present output levels, assigning these quantities to one of the units, and setting the other unit off AGC and at 0 MW of output. To have Simulator perform this function for you, check the box in the *Cross Compound Units* panel.

To tell Simulator how to identify units that belong to the same cross-compound generator, click the box labeled "How To Identify…". This will open the **How to Identify Cross-Compound Dialog** described next.

How to Identify Cross-Compound Dialog

Simulator regards cross-compound units as those that are connected to the same bus and that have generator id’s that match any of a number of specified pairs. You must define for Simulator the pairs of generator id’s that should be used to identify cross-compound units. Use the "**How to identify cross-compound units**" dialog to do this. 

Specify the pair of generator id’s in the small text boxes below the text labeled "Specify a new pair of id’s that identify two units that belong to the same cross-compound set." Then, click the **Add** button to include the pair of id’s you just entered in Simulator’s cross-compound identification procedure. The box on the right lists all the pairs of identifiers Simulator will use to identify parts of a cross-compound set. To remove a pair of identifiers from this list, select it from the box and click the Delete key.

The list of cross-compound identifier pairs is stored in the pwrworld.ini file, so there is no need to specify these pairs each time you load in a new case.

---

<a id="injection-groups-format-inj"></a>

## Injection Groups Format (*.inj)

*Source: [`Content/MainDocumentation_HTML/Injection_Groups_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Injection_Groups_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These files are outdated for Simulator version 8.0 and later. Their descriptions are still maintained here as they can still be read into Simulator. However, they can no longer be saved. These records are now stored in [Auxiliary Script/Data Files](#auxiliary-file-format-aux).

The injection group files store the information for defined injection groups (also referred to as participation groups). The files have the following format:

 **GROUP groupname**

** POINTS**

** Devtype busnum id participation pointtype**

** .**

 **.**

** .**

** END**

where

**groupname **the name of the injection group, in single quotes,

**devtype **either GEN or LOAD,

**busnum **bus number of the device,

**id **the device’s single character ID,

**participation **relative amount each device will contribute during a transfer,

**pointtype **either FIXED or DYNAMIC.

Multiple GROUP sections can be put in the file, each marked with END to signify the end of that group’s data.

---

<a id="interface-data-format-inf"></a>

## Interface Data Format (*.inf)

*Source: [`Content/MainDocumentation_HTML/Interface_Data_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Interface_Data_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These files are outdated for Simulator version 8 and later. Their descriptions are still maintained here as they can still be read into Simulator. However, they can no longer be saved. These records are now stored in [Auxiliary Script/Data Files](#auxiliary-file-format-aux).

The interface data files store the interface data. The files have the following format:

 **INTERFACE intname lima limb limc**

** Elemtype from to id checktoend fromto**

** .**

** .**

** .**

where

**intname **the interface name, in single quotes,

**lima, limb, limc **the three limits for the interface, in MW,

**elemtype **one of three valid element types: AREA, LINE, or ZONE

**from **for AREA and ZONE, the first area or zone number; for LINE, the from bus number,

**to **for AREA and ZONE, the second area or zone number; for LINE, the to bus number,

**id **only included for LINE, the two character circuit identifier; otherwise left blank,

**checktoend **only included for LINE, if this field equals 1, the flow is checked at the to bus, otherwise the flow is checked at the from bus; otherwise left blank,

**fromto **only included for LINE, if this field equals 1, the positive flow is assumed to be from the from bus to the to bus, otherwise the flow is assumed to be in the opposite direction; otherwise left blank.

Multiple interface records can be listed in the file, and multiple interface elements can be listed in each interface record.

---

<a id="sequence-data-format"></a>

## Sequence Data Format

*Source: [`Content/MainDocumentation_HTML/Sequence_Data_Format.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Sequence_Data_Format.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These files are outdated. Their descriptions are still maintained here as they can still be read into Simulator. However, they can no longer be saved. These records are now stored in [Auxiliary Script/Data Files](#auxiliary-file-format-aux).

The sequence data files store the sequence data needed to run a fault analysis. The sequence data format has the following five different types of records:

  - Generator
  - Load
  - Branch
  - Switched Shunt
  - Mutual Impedance

Each of these four types of sequence data records has a different format, since they each store different information for the sequence data. The format of each record is given below:

Generator

**GEN busnum ID Rpos Xpos Rneg Xneg Rzer Xzer RN XN**

where

**busnum **generator terminal bus,

**id **generator identifier,

**Rpos, Xpos **positive sequence resistance and reactance,

**Rneg, Xneg **negative sequence resistance and reactance,

**Rzer, Xzer **zero sequence resistance and reactance,

**RN, XN **neutral-to-ground resistance and reactance.

Load

**LOAD busnum Gneg Bneg Gzer Bzer**

where

**busnum **load terminal bus,

**Gneg, Bneg **negative sequence total conductance and susceptance for all loads at bus,

**Gzer, Bzer **zero sequence total conductance and susceptance for all loads at bus.

Branch

**BRANCH fbusnum tbusnum ckt Rzer Xzer Czer fGzer fBzer tGzer tBzer Xftype**

where

**fbusnum, tbusnum **from and to bus numbers for the branch,

**ckt **branch circuit identifier,

**Rzer, Xzer **zero sequence branch resistance and reactance,

**Czer **total zero sequence line charging,

**fGzer, fBzer **zero sequence line shunt conductance and susceptance at the from bus end of the branch,

**tGzer, tBzer **zero sequence line shunt conductance and susceptance at the to bus end of the branch,

**Xftype **Transformer configuration, entered as an integer based on the following table. Note that the default for a transmission line is 3, since a grounded wye - grounded wye transformer connection has the same equivalent model as a transmission line.

** **0 Wye - Wye

** **1 Grounded Wye - Wye

** **2 Wye - Grounded Wye

** **3 Grounded Wye - Grounded Wye

** **4 Wye - Delta

** **5 Delta - Wye

** **6 Grounded Wye - Delta

** **7 Delta - Grounded Wye

** **8 Delta - Delta

Switched Shunt

**SSHUNT busnum numblocks Bzer1 Bzer2 …**

where

**busnum **terminal bus number,

**numblocks **number of different zero sequence admittance blocks,

**Bzer\# **zero sequence susceptance for each admittance block, maximum of 8.

Mutual Impedance

**MUTIMP from1 to1 ckt1 from2 to2 ckt2 RM XM start1 end1 start2 end2**

where

**from1, to1 **from and to bus numbers of the first mutually coupled branch,

**ckt1 **circuit identifier of the first mutually coupled branch,

**from2, to2 **from and to bus numbers of the second mutually coupled branch,

**ckt2 **circuit identifier of the second mutually coupled branch,

**RM, XM **zero sequence mutual resistance and reactance,

**start1, end1 **start and end locations of the section of the first line affected by the mutual coupling, with each point represented as a percentage of the total line length (between 0 and 1),

**start2, end2 **start and end locations of the section of the second line affected by the mutual coupling, with each point represented as a percentage of the total line length (between 0 and 1).

---

<a id="exporting-onelines-in-different-graphic-formats"></a>

## Exporting Onelines in Different Graphic Formats

*Source: [`Content/MainDocumentation_HTML/Exporting_onelines_in_different_graphic_formats.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Exporting_onelines_in_different_graphic_formats.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can export oneline diagrams and other graphical displays as bitmaps, metafiles, jpegs, or gifs. Select **Export Oneline** from the [File menu](#file-menu). A save file dialog appears where the dropdown menu for files type offers four choices: JPEG, BITMAP, METAFILE, GIF. Select the file type and choose he name before clicking the save button.

Exporting an image as a jpeg also requires you to set the compression ratio for the picture. See [Saving Images as Jpegs](#saving-images-as-jpegs) for more information.

Exporting an image as a gif provides the option to save an animated image. Upon saving, you are given the option to specify the number of frames to save and the time delay between frame changes during playback. You are also given the ability to scale the image before saving.

---

<a id="saving-images-as-jpegs"></a>

## Saving Images As Jpegs

*Source: [`Content/MainDocumentation_HTML/Saving_Images_As_Jpegs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Images_As_Jpegs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator can save oneline diagrams, bus view displays, and strip charts as jpeg images. To save a oneline diagram or bus view display as a jpeg, select **Export Oneline** from the [File menu](#file-menu). This brings up the save file dialog. Choose jpeg as the file type, type the file name, and press save. This brings up the Jpeg Options Dialog where you decide the picture's resolution. Adjust the resolution control to specify the compression ratio at which to save the diagram as a jpeg. The greater the resolution you specify, the larger the resulting file will be. Click **Save** to save the image or click **Cancel** to terminate the process without saving the image as a jpeg.

To save a strip chart as a jpeg image, right-click on the background of the strip chart and select **Export Image** from the resulting local menu. This brings up the save file dialog. Choose jpeg as the file type, type the file name, and press save. Specify the compression/resolution in the Jpeg Options Dialog. Click **Cancel** to terminate the process, or click **Save** to save the jpeg.

---

<a id="saving-admittance-matrix-and-jacobian-information"></a>

## Saving Admittance Matrix and Jacobian Information

*Source: [`Content/MainDocumentation_HTML/Saving_Admittance_Matrix_and_Jacobian_Information.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Saving_Admittance_Matrix_and_Jacobian_Information.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The **Save Ybus or Power Flow Jacobian** dialog is used to store the power system bus admittance matrix (Ybus) and/or the power flow Jacobian in a text format that can be easily read into other programs such as MATLABÒ. This dialog is primarily designed for users doing power system analysis research. The dialog has the following fields.

Ybus in MATLAB Format

YBus Save File

Enter the name of the file in which to store the Ybus data. The Ybus data is stored using the MATLAB sparse matrix format in the matrix **Ybus**. If the **Include Bus Voltages** field is checked, then the bus voltages are also stored, but in the vector **V**.

Save Ybus in MATLAB Format

Click this button to save the Ybus.

Power Flow Jacobian in MATLAB Format

Jacobian Save File

Enter the name of the file in which to store Jacobian data. The Jacobian is stored using the MATLAB sparse matrix format in the matrix **Jac**.

Jacobian ID Save File

Enter the filename to store the text identifier information. This information is used to translate the bus numbering convention used in the Jacobian and Ybus files with the actual bus number and name in the case.

File Type

Choose the type of MATLAB file you wish to save as. The **MATLAB .M Format** is the more common text format used for directly loading MATLAB information. The **Text for MATLAB Ascii** is for use with MATLAB’s ability to read Ascii files. The Ascii file type can be read into MATLAB much faster than the traditional .M files. The **MATLAB .M Format in Scientific Notation**is the same as in Matlab .M format but the values are presented in scientific notation and will show up to seven significant digits (for example: 1.234567E-2 for 0.01234567)

Jacobian Form

Select **Rectangular** to store the rectangular form of the Jacobian, or **Polar** to store the polar form of the Jacobian.

Save Jacobian

Click this button to save the Jacobian and object identifier information.

---

<a id="working-with-ge-epc-files"></a>

## Working With GE EPC Files

*Source: [`Content/MainDocumentation_HTML/Working_With_GE_EPC.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Working_With_GE_EPC.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator can open and export to GE EPC files, but as with any format conversion there are some quirks to keep in mind. Many of these are described in a number of pages throughout these help files.

  - [Differences in File Formats](#differences-in-file-formats)
  - [Appending a Case](19-edit-mode-tools.md#appending-a-case)
  - [Case Formats](#case-formats)
  - [File Management Options](10-power-flow-solution-and-options-part2.md#file-management-options)
  - [GE EPC File Load Options](#ge-epc-file-load-options)
  - [Present Topological Differences from Base Case](08-view-case-data-tools.md#present-topological-differences-from-base-case)
  - [Script General Actions](#auxiliary-file-format-aux)
  - [Transient Stability Data from External Files](36-transient-stability-overview-and-data-part2.md#data-from-external-files)
  - [Transient Stability Overview: Generator Models](36-transient-stability-overview-and-data-part1.md#generator-models)

---

<a id="differences-in-file-formats"></a>

## Differences In File Formats

*Source: [`Content/MainDocumentation_HTML/Differences_In_File_Formats.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Differences_In_File_Formats.htm)*

PowerWorld Simulator supports loading from and saving to a number of different external formats, including EPC and PSS/E files. There are a number of points where Simulator's handling of a power system is not precisely represented in other formats, so some care must be taken when working with these other files.

GE EPC Files

Buses

Bus names are limited to 12 characters. When writing out to PSLF files, Simulator will truncate names in a way that ensures unique names remain unique.

PSLF specifies the specific voltage setpoint with a Bus record, and then specifies a range with the device (Vband for a shunt, Vmin/Vmax for a transformer)

Generators

GE Baseload Flag is an extra flag used by PSLF in transient simulation only (user-written EPCL code might also use this). Simulator allows you to interpret this field as a Post-Contingency AGC status (Simulator has a separate field for Transient Simulation use).

Simulator has an AVR flag which is set to YES or NO. PSLF uses (Qmax-Qmin) to determine AVR. By default ranges at 2.0 Mvar or less are considered AVR=NO.

Shunts

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td style="text-align: center;"><p>GE PSLF</p></td>
<td style="text-align: center;"><p>PTI PSS/E</p></td>
<td style="text-align: center;"><p>PowerWorld Simulator</p></td>
</tr>
<tr class="even">
<td><p>Controllable Shunt</p></td>
<td style="text-align: center;"><p><strong>SVD</strong></p>
<p>(Multiple allowed per bus)</p></td>
<td style="text-align: center;"><p><strong>Switched Shunt</strong></p>
<p>(Multiple allowed per bus)</p></td>
<td style="text-align: center;"><p><strong>Switched Shunt</strong></p>
<p>Control Mode = <em>Fixed</em>, <em>Discrete</em>, <em>Continuous</em>, or <em>SVC</em></p>
<p>Multiple allowed per bus</p>
<p>(coordinated control as of version 16)</p></td>
</tr>
<tr class="odd">
<td><p>Fixed Bus Shunt</p></td>
<td style="text-align: center;"><p><strong>SHUNT</strong></p>
<p>(Multiple allowed per bus)</p></td>
<td style="text-align: center;"><p><strong>Fixed Bus Shunt</strong></p>
<p>(Multiple allowed per bus)</p></td>
<td style="text-align: center;"><p><strong>Switched Shunt</strong></p>
<p>Control Mode = <em>Bus Shunt</em></p>
<p>(Multiple allowed per bus)</p></td>
</tr>
<tr class="even">
<td><p>Fixed Line Shunt</p></td>
<td style="text-align: center;"><p><strong>SHUNT</strong></p>
<p>Assigned to a line.</p>
<p>IDs must start with an <em>f</em> or <em>t</em></p></td>
<td style="text-align: center;"><p>No special record.</p>
<p>Fields with AC Line <em>GI</em>, <em>BI</em>, <em>GJ</em>, <em>BJ</em> specify the total at each end</p></td>
<td style="text-align: center;"><p><strong>Line Shunt</strong></p>
<p>Each end of line can have multiple shunts. IDs assigned for multiple shunts.</p></td>
</tr>
<tr class="odd">
<td><p>G and B for equiv</p></td>
<td style="text-align: center;"><p>None</p></td>
<td style="text-align: center;"><p>None</p></td>
<td style="text-align: center;"><p><strong>Bus</strong> fields</p>
<p><em>Nom G Shunt</em> and <em>Nom B Shunt</em></p></td>
</tr>
</tbody>
</table>

Transformers

PSLF allows a tertiary bus number of zero (0). Simulator supports this exclusion of the tertiary bus, but will write it as two 2-winding transformers when exporting to a RAW file.

Multi-Section Lines

In PSLF, intermediate buses are not defined and thus loads, generators, and shunts at these points are not allowed. When writing out to an EPC file, the multi-section line record is ignored if intermediate buses have objects.

Area/Zones for Shunt Objects

PSLF allows area and zone designations for specific branches and transformers. Simulator reads this into EPC specific fields, but does not use them for anything.

Area MW Transactions

PSLF includes tables showing Transactions. The actual scheduled values are informational only. PSLF does not use these MW Transactions in the power flow solution; instead, it includes a field with an area specifying the net MW export. When loading an EPC file, Simulator's area field "Unspecified MW Interchange" is assigned as the "leftover" which isn't included in the transactions table.

DC Lines

In Simulator, there are distinct container objects for both a two-terminal DC line and a multi-terminal DC line (MTDC). In PSLF, there are only definitions of the DC Buses, AC/DC converter, and DC line objects. The groupings are then determined by the topology of the DC line links. PSLF requires that all DC buses throughout the entire model have a unique DC bus number, which Simulator supports.

Super Areas

In Simulator, Super Area objects can be created and each area can be assigned to one super area. This is useful in studying groups of areas which are dispatched together (Electricity Markets). PSLF does not support Super Areas.

Nomograms

In Simulator, Nomogram objects can be created which specify two interfaces and then a two-dimensional limit region. Nomogram limit violation can then be monitored or enforced in Contingency Analysis, ATC, OPF and SCOPF studies. PSLF does not support Nomograms.

PSS/E Files

Buses

PSS/E bus names are limited to 12 characters. When writing out to PSS/E files, Simulator will truncate names in a way that ensures unique names remain unique.

Generators

While Simulator specifies the capability curve explicitly, PSS/E has a separate input file called "GCAP" which specifies the capability (Simulator can read this file).

PSS/E specifies a "bus type" to signify the generator is not on AVR control, while Simulator uses an AVR flag set to YES or NO.

Shunts

See shunt format comparison table above.

Transformers

PSS/E does not support a fixed tap definition on the same side as the variable tap (FROM), thus Fixed tap is always assumed as 1.00.

PSS/E does not specify the intermediate Star Bus of a 3-winding transformer explicitly. The voltage and angle at this point are part of the transformer record.

PSS/E does not allow the tertiary of a 3-winding transformer to be excluded. Simulator allows this, though we do not consider it good practice.

Area/Zones for Shunt Objects

Simulator allows Generators, Loads and Switched Shunts to have a different area or zone than the terminal bus. PSS/E only allows this for Loads. These objects are then treated as tie-lines in area and zone interchange calculations. PSS/E has a specoal solition option to specify whether to include the interchnge as "LINES ONLY" or "LINES AND LOADS". Simulator always uses Lines and Loads.

Area MW Transactions

PSS/E includes tables showing Transactions. The actual scheduled values are informational only. PSS/E does not use these MW Transactions in the power flow solution; instead, it includes a field with an area specifying the net MW export. When loading an EPC file, Simulator's area field "Unspecified MW Interchange" is assigned as the "leftover" which isn't included in the transactions table.

DC Lines

PSS/E requires that all DC buses of a particular MTDC grouping be numbered from 1 to the number of DC buses. Simulator supports this when exporting to PSS/E.

Interfaces

PSS/E has a monitor functionality (MON file) which allows definition of an interface which includes AC branches and Line Open of Close contingent elements.

Injection Groups

Simulator supports the definition of an injection group which represents a group of generators, loads, or switched shunts (and can contain other injection groups). This can bus used for summary calculations, sensitivity-based calculations, or as a source and sink for a transfer. PSS/E has a similar concept called a "subsystem", which you may find in a SUB file.

Super Areas

In Simulator, Super Area objects can be created and each area can be assigned to one super area. This is useful in studying groups of areas which are dispatched together (Electricity Markets). PSS/E does not support Super Areas.

Nomograms

In Simulator, Nomogram objects can be created which specify two interfaces and then a two-dimensional limit region. Nomogram limit violation can then be monitored or enforced in Contingency Analysis, ATC, OPF and SCOPF studies. PSS/E does not support Nomograms.

---

<a id="overview-of-powerworld-simulator-project-files"></a>

## Overview of PowerWorld Simulator Project Files

*Source: [`Content/MainDocumentation_HTML/overview_of_powerworld_simulator_project_files.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/overview_of_powerworld_simulator_project_files.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Performing a simulation using PowerWorld Simulator sometimes requires using a number of different files. In addition to the case file that stores the model of the system, there may be one or more oneline diagrams depicting various regions of the system. These oneline diagrams might feature [document links](12-building-onelines-branches-and-devices.md#document-links-on-onelines) that connect to files that were created using other applications, as well as [oneline links](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files), which open other oneline diagrams when they are clicked. For these links to function properly, the documents and oneline displays to which they connect must be available. A simulation might also employ a template file that is used to load in a predefined set of solution, environment, and display options. Furthermore, the simulation might make use of data stored in [auxiliary data files](#auxiliary-file-format-aux) to supplement the data stored in the case file. Finally, a simulation might utilize a [script file](#auxiliary-file-format-aux) to perform some automated sequence of tasks, or even to display a movie of system conditions. Having to deal with so many files may make it difficult to transfer the case to another computer, or to share the model with a colleague. PowerWorld Simulator Project files provide a solution.

PowerWorld Simulator Projects have the extension \*.pwp. A project serves as a container for all the files that might comprise a simulation, including the case file, one or more oneline diagrams, a script file, one or more auxiliary data files, and a case template, as well as any other support files you may wish to include. A project is actually a compressed file archive that is compatible with the widely available PKZip and WinZip file compression utilities. It is strongly recommended, however, that you work with project files strictly within the PowerWorld Simulator environment, as Simulator can automatically perform the file compression and extraction functions and process the contents of the included files in a single step. (Note: Simulator performs file compression and extraction using software components available from http://www.cdrom.com/pub/infozip/ and http://www.geocities.com/SiliconValley/Orchard/8607/ main.html).

---

<a id="powerworld-project-initialization-script"></a>

## PowerWorld Project Initialization Script

*Source: [`Content/MainDocumentation_HTML/powerworld_project_initialization_script.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/powerworld_project_initialization_script.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Included in every project file is an initialization script file called OPENPWB.SCP. This is a special type of PowerWorld script file that is used to unload the contents of the project that are used in the simulation. This file must begin with the keyword "INITIALIZATION" and terminate with the keyword "END". Between these two lines, OPENPWB.SCP identifies the name of the case, any oneline diagrams that should be opened immediately, a template file (if any), a script file (if any), and one or more auxiliary data files (if any) to open and read into memory after extracting the files. The file might also contain the keyword "AUTOSTART", indicating that the simulation of the system described by the project file should commence immediately after it is read into memory. The OPENPWB.SCP is generated for you automatically when you save a new project file. Here is an example that loads the case B7FLAT.PWB (in PowerWorld binary format) along with oneline diagram B7FLAT.PWD, the template B7FLAT.PWT, the script B7FLAT.SCP, and the auxiliary file B7FLAT.AUX, and then starts the simulation immediately after all contents are extracted and read:

INITIALIZATION

CASE PWB B7FLAT.PWB

ONELINE B7FLAT.PWD

TEMPLATE B7FLAT.PWT

SCRIPT B7FLAT.SCP

DATAFILE B7FLAT.AUX

AUTOSTART

END

Again, all projects must contain the file OPENPWB.SCP. If a project does not contain this file, an error message will be shown. Simulator automatically includes an OPENPWB.SCP file with every project it creates. Therefore, unless you try to create a project file outside of Simulator, you will not have to worry about this requirement.

---

<a id="associating-project-files-with-simulator"></a>

## Associating Project Files With Simulator

*Source: [`Content/MainDocumentation_HTML/associating_project_files_with_simulator.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/associating_project_files_with_simulator.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld Simulator can automatically open and load the contents of a project if the proper file associations have been made. When Simulator is installed on a computer, it registers the file extension \*.pwp in the Windows registry. Then, whenever you double-click on an icon for a project file or download a project file from a web site, Simulator will start, extract the contents of the project file, and read them into memory. The power system will then be displayed exactly as the author of the project file intended it to be displayed.

If the file association is somehow destroyed (i.e. Windows no longer recognizes that \*.pwp files should be associated with and opened by Simulator), you can re-establish the association manually using the following procedure:

  - Windows 95/98/NT
      - Open Windows Explorer.
      - Select View \> Folder Options from Windows Explorer’s main menu.
      - Switch to the tab labeled "File Types."
      - Click the button labeled "New Type."
      - For "Description of Type," specify "PowerWorld Project."
      - For "Associated Extension," specify "PWP".
      - For "ContentType (MIME)," specify "application/powerworld\_project."
      - For "Default Extension," specify ".PWP".
      - Under "Actions," click the button labeled "New."
      - Specify the "Action" as "open."
      - Specify the "Application used to perform action" as the path to the Simulator executable file, followed by a space and the string "%1" (including the quotation marks). For example, if the path of the PowerWorld Simulator executable is "c:\\program files\\PowerWorld\\pwrworld.exe," then you should specify the following string:  
          c:\\program files\\PowerWorld\\pwrworld.exe "%1"
      - Click OK to close the Action dialog.
      - Click OK to complete the definition of the file association.
  - Windows XP
      - Open Windows Explorer
      - Select Tools \> Folder Options from Windows Explorer’s main menu.
      - Switch to the tab labeled "File Types"
      - Click the button labeled New
      - For "File Extension", enter "PWP", then click OK.
      - Find the PWP entry in the Registered file types list, then click on it.
      - Next, with the PWP entry selected, click on Advanced.
      - In the box to the left of the "Change Icon…" button, type in "PowerWorld Project"
      - Click on the "New…" button on the right-hand side of this dialog, which will pop up a "New Action" dialog
      - In the New Action dialog, click "Browse…"
      - Navigate to and select the PowerWorld program binary (pwrworld.exe); the default location is c:\\Program Files\\PowerWorld\\pwrworld.exe
      - In the New Action dialog, enter "Open the project" in the field labeled "Action"
      - Click OK in the New Action dialog and in the Edit File Type dialog
      - Click Close when you are back to the main File Types dialog.
  - For future Windows versions, refer to the Windows help on changing file type associations.

The \*.pwp file type will now be recognized on your system as being associated with PowerWorld Simulator. Again, you will need to perform this procedure only if the association somehow gets removed.

---

<a id="creating-a-new-project-file"></a>

## Creating a New Project File

*Source: [`Content/MainDocumentation_HTML/creating_a_new_project_file.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/creating_a_new_project_file.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Creating a new project file in Simulator is fairly simple. First, make sure that the case for which you want to create the project is open in Simulator, as well as any oneline diagrams that you wish to open automatically whenever the user opens the project. Then select **Save As Project** from the [File menu](#file-menu). This opens the [Create Project Dialog](#create-project-dialog), which you can use to specify the contents of the project file. When you click OK on the Create Project Dialog, the files you identified will be compressed into a single file, along with the [project initialization script](#powerworld-project-initialization-script) that tells Simulator how it should import the contents of the project.

---

<a id="create-project-dialog"></a>

## Create Project Dialog

*Source: [`Content/MainDocumentation_HTML/create_project_dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/create_project_dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Create Project Dialog enables you to create a new [PowerWorld Simulator Project](#overview-of-powerworld-simulator-project-files) by specifying the files that should be included in the project. To open the Create Project Dialog, select **Save As Project** from the [File menu](#file-menu). When it opens, the dialog will automatically include the case file, all open oneline diagrams, all documents and onelines linked to the display by [document links](12-building-onelines-branches-and-devices.md#document-links-on-onelines) and [oneline links](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files), the current case template file, and the current script in its list of files to add to the project. You can then use this dialog to add files to or delete files from the list of project contents.

The Create Project Dialog features the following controls:

Case

Identifies the name of the case file that is currently open in Simulator. The case file may be in PowerWorld binary format, in PTI Version 23 - 33 .raw format, or in GE PSLF .epc format. You cannot change this field, because it must be set to whatever case is currently open.

Open these oneline diagrams automatically

Lists the names of the oneline diagrams that will automatically open whenever a user opens the project file. This is also a read-only control and lists the names of all oneline diagrams that are currently open in Simulator. Therefore, before you start to create a project using the Create Project dialog, make sure that only those oneline diagrams you wish to open automatically with the project are currently open in Simulator.

Use this script file

Identifies a [script file](#auxiliary-file-format-aux) that should be opened automatically when the project is open. Scripts are text files that contain commands in [PowerWorld's scripting language](#auxiliary-file-format-aux) that Simulator interprets to perform a predefined set of tasks during the simulation. If a script file is in use when you try to create the project, its name will automatically appear in this text box. To specify a different script file, either type its full path in the text box, or press the adjacent *Browse* button to search for it on your machine.

Load data from auxiliary files

Lists the [auxiliary data files](#auxiliary-file-format-aux) that should be automatically read when the project is open. Auxiliary data files are text files that contain data that supplement or supersede the information in the case file. You may include as many automatically loading auxiliary data files in the project as you like. To add an auxiliary file to the project contents, click the adjacent Add button and locate the file on your machine. To remove an auxiliary file from the list, select it and click the adjacent Remove button.

Also include these files

Lists any other files you may wish to include in the project. Use this control to include supplementary documents, pictures, or even other PowerWorld project files, in the project. To add a file to the contents, click Add a File. To remove a file from the list, select it and press the adjacent Remove button.

Automatically start the simulation after opening the project

Check this button to cause Simulator to start the simulation immediately after opening the project. This saves the user who opens the project the step of switching to run mode and clicking the play button in the **[Power Flow Tools](02-simulator-ribbon.md#simulation-control)** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab. This option is particularly effective, for example, if you want to display a "movie" of system conditions when the project is open. By including a script file in the project that tells Simulator how to modify the system and view over time, you create a project that, when opened or downloaded, animates the scenario you are trying to model.

Save this project as

Identifies the name of the project that should be saved. By default, the project name is the same as that of the case except that it has the extension "pwp". To specify a different name, either type it directly in the text box, or click the adjacent Browse button and specify the full path.

When you have finished specifying the contents of the project file, click the **OK,save the project** button. If you wish to cancel the operation without creating the project, click **Cancel**.

---

<a id="opening-an-existing-project"></a>

## Opening an Existing Project

*Source: [`Content/MainDocumentation_HTML/opening_an_existing_project.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/opening_an_existing_project.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open an existing [PowerWorld Simulator Project file](#overview-of-powerworld-simulator-project-files), select **Open Project** from the [File menu](#file-menu), and select the name of the project you wish to open. Alternatively, you may select **Open Case** from the [File menu](#file-menu), change the *Files of Type* setting to "PowerWorld Project (\*.pwp)," and select the project you wish to open. Simulator will extract the contents of the project file into the project file’s folder and input the information it needs to display the case, oneline diagrams, and other associated files.
