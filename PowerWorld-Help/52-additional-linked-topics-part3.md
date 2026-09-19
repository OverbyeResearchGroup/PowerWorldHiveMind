---
title: "Additional Linked Topics (Part 3 of 3)"
part: "Reference"
chapter_file: "52-additional-linked-topics-part3.md"
topics: 9
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Additional Linked Topics (Part 3 of 3)

Topics reachable from links inside the manual but not listed in the help system's table of contents.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (9)**

- [Transient Stability Angle Reference](#transient-stability-angle-reference)
- [Transient Stability Dialog Options: User Defined Models](#transient-stability-dialog-options-user-defined-models)
- [Transient Stability Numerical Integration Sub-Interval Models](#transient-stability-numerical-integration-sub-interval-models)
- [What's New](#whats-new)
- [What's New](#whats-new-1)
- [What's New](#whats-new-2)
- [What's New](#whats-new-3)
- [What's New](#whats-new-4)
- [WriteAuxFile Function (version 9)](#writeauxfile-function-version-9)

---

<a id="transient-stability-angle-reference"></a>

## Transient Stability Angle Reference

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_AngleReference.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_AngleReference.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

All angle values have a meaning only when stated with respect to a reference. Two such quantities are the angle of the bus terminal voltage and the angle of the generator's (machine's) rotor.

For all buses, the terminal voltage angle (that has a physical significance) can be specified in two forms. Both forms have the units of degrees, but with different references.

**"V Angle No Shift"**: It is with respect to a fictitious synchronous reference that is rotating at 50 or 60 Hz (the system nominal frequency), and It is also the actual voltage angle algebraic state of each bus terminal during a simulation.

**"V Angle"**: It is defined with respect to the chosen Angle Reference in Transient Stability \> Options \> Results Options \> Angle Reference Options, i.e., "V Angle No Shift" — "Angle Reference".

Additionally, for all synchronous generators, the angle of the machine's rotor can be specified in three forms. All forms also have the units of degrees and refer to the same physical dynamic state of a machine, but have different references.

**"Rotor Angle No Shift"**: It is with respect to a fictitious synchronous reference that is rotating at 50 or 60 Hz (the system nominal frequency), and it is also the actual rotor angle dynamic state that is present in each simulated machine model.

**"Rotor Angle"**: It is defined with respect to the chosen Angle Reference in Transient Stability \> Options \> Results Options \> Angle Reference Options, i.e., "Rotor Angle No Shift" — "Angle Reference".

**"Power Angle**": It is defined with respect to the Terminal "V Angle No Shift" or "V Angle", i.e., "Rotor Angle No Shift" — "V Angle No Shift", which is equivalent to "Rotor Angle" — "V Angle"

"V Angle No Shift" and "Rotor Angle No Shift" generally do not return to a constant value after a "new steady state" has been reached during a dynamic simulation. Instead, these quantities will have a constant positive/negative slope in a time-series plot, where the slope will be equal to "new steady state" frequency minus the "initial steady state" frequency in Hz, assuming of course that a "new steady state" was in fact reached.

"V Angle" and "Rotor Angle" generally do return to a constant value after a "new steady state" has been reached during a dynamic simulation. Depending on the chosen "Angle Reference", it is sometimes possible that it might skew the angle at all buses/generators. Consequently, be advised to not solely rely on "V Angle" and "Rotor Angle" to assess the stability of a simulation, but also check other signals like voltage magnitude and frequency to verify the overall system condition.

"Power Angle" tends to be a better indicator of a generator's stability, and it does return to a constant value after a "new steady state" has been reached during a dynamic simulation, except a few rare situations (such as during faults). In most undergraduate or graduate courses, a single-machine model is first discussed where the rotor angle dynamic state is defined with respect to the terminal voltage. It is in fact the same as "Power Angle", and is neither "Rotor Angle" nor "Rotor Angle No Shift" in PowerWorld's terminology. In large-scale power system simulations, it becomes essential to distinguish between the "Power Angle" and "Rotor Angle, and this write-up has explained the differences.

---

<a id="transient-stability-dialog-options-user-defined-models"></a>

## Transient Stability Dialog Options: User Defined Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_User_Defined_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Dialog_Options_User_Defined_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The User Defined Models sub-tab is found on the [Options](37-transient-stability-analysis-dialog-part1.md#options) page of the [Transient Stability Analysis dialog](37-transient-stability-analysis-dialog-part1.md#transient-stability-analysis-dialog). The User Defined Models sub-tab shows all information related to the [User Defined Models](36-transient-stability-overview-and-data-part2.md#user-defined-models) (UDMs) present in the case.

![Transient Stability Dialog Options User DefinedModels](images/Transient_Stability_Dialog_Options_User_DefinedModels.jpg)

The **Edit Browsing Path** button tells Simulator the folder(s) to monitor for user defined model DLLs. Simulator automatically populates the rest of the dialog based on the models found. As with built-in models, Simulator keeps track of the model instances that have been inserted.

The **User Defined Models** panel on the left lists all of the [User Defined Model](36-transient-stability-overview-and-data-part2.md#user-defined-models) types, as found by Simulator in the browsing path.

The panel on the right is a Case Information Display that changes to show all model instances of the selected type. If **All** is selected, a summary is shown. If a single model type is selected, a third panel in the bottom right appears and lists specific information for that model.

The bottom panel (shown below for a user defined exciter model) contains the DLL location, the model type recognized by Simulator, the model name chosen by the developer, and several lists. **DLL Functions**are names of the functions exported by the DLL which depend on the model type. **Extra Objects** are the object types and descriptions of any other objects whose signals to be used by the model. **Parameters** are the names and default values of the model parameters. **States** are the dynamic states of the model.**Hard-Coded Signals** are the variables which are automatically available to the DLL and change based on the model type. **Algebraics** are any additional variables required by the model that are not in the hard-coded signals list.

![Transient Stability Dialog Options UDM Signals](images/Transient_Stability_Dialog_Options_UDM_Signals.jpg)

---

<a id="transient-stability-numerical-integration-sub-interval-models"></a>

## Transient Stability Numerical Integration Sub-Interval Models

*Source: [`Content/MainDocumentation_HTML/Transient_Stability_Integration_Subinterval_Models.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Transient_Stability_Integration_Subinterval_Models.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Sub-Interval Integration Models**

The user can set the Sub-Interval of any dynamic model by selecting the *Sub-Intervals* (*TSSubintervals*) field for the desired model in the Transient Stability folder in Model Explorer. You can specify the numbers if sub-interval integration steps to use.

A blank value will let Simulator use an automatically determined sub-interval count for that particular model type. For most models, the automatically determined value is Sub-Intervals = 1, which means that a time-step will not divided into sub-intervals during integration.

The sub-interval value must be either blank, 1 , 2, 4, 8, 16, 32, 64 or 128.  
If the value entered does not belong to this list, it is modified as follows:  

    If     (Sub-Intervals ≤  0) Then Sub-Intervals = blank
    ElseIf (Sub-intervals ≤  1) Then Sub-Intervals =     1
    ElseIf (Sub-intervals ≤  2) Then Sub-Intervals =     2
    ElseIf (Sub-intervals ≤  4) Then Sub-Intervals =     4
    ElseIf (Sub-intervals ≤  8) Then Sub-Intervals =     8
    ElseIf (Sub-intervals ≤ 16) Then Sub-Intervals =    16
    ElseIf (Sub-intervals ≤ 32) Then Sub-Intervals =    32
    ElseIf (Sub-intervals ≤ 64) Then Sub-Intervals =    64
    Else                             Sub-Intervals =   128

The models that will cause Simulator to use a default step if a blank value is used for the model are:

*DC Models:*

\-[CHVDC2](45-ts-models-hvdc-part1.md#chvdc2)

\-[CONV\_CELILO\_E](45-ts-models-hvdc-part1.md#conv-celilo-e)

\-[CONV\_CELILO\_N](45-ts-models-hvdc-part1.md#conv-celilo-n)

\-[CONV\_IntMtnPP](45-ts-models-hvdc-part1.md#conv-adelanto)

\-[CONV\_SYLMAR](45-ts-models-hvdc-part1.md#conv-sylmar)

\-[MTDC\_IPP](45-ts-models-hvdc-part1.md#mtdc-ipp)

\-[MTDC\_PDCI](45-ts-models-hvdc-part1.md#mtdc-pdci)

\-[VHVDC1](45-ts-models-hvdc-part2.md#vhvdc1)

*Exciters Models:*

\-[EMAC1T](39-ts-models-exciters-part1.md#emac1t)

\-[ESAC2A](39-ts-models-exciters-part1.md#esac2a)

\-[ESAC5A](39-ts-models-exciters-part2.md#esac5a)

\-[ESAC7B](39-ts-models-exciters-part1.md#ac7b)

\-[ESST1A and ESST1A\_GE](39-ts-models-exciters-part2.md#esst1a)

\-[EXAC1](39-ts-models-exciters-part2.md#exac1a)

\-[EXAC2](39-ts-models-exciters-part2.md#exac2)

\-[EXAC8B](39-ts-models-exciters-part2.md#exac8b)

\-[EXBAS](39-ts-models-exciters-part2.md#exbas)

\-[EXDC2GE](39-ts-models-exciters-part2.md#exdc2-ge)

\-[EXST3](39-ts-models-exciters-part3.md#exst3)

\-[EXST3A](39-ts-models-exciters-part3.md#exst3a)

\-[IEEET2](39-ts-models-exciters-part3.md#ieeet2)

\-[REXS](39-ts-models-exciters-part4.md#rexs)

\-[REXSY1](39-ts-models-exciters-part4.md#rexsy1)

\-[REXSYS](39-ts-models-exciters-part4.md#rexsys)

\-[BPA\_FK](39-ts-models-exciters-part5.md#bpa-fk)

*Induction Models:*

\-All of them

*Governors Models:*

\-[HYG3](40-ts-models-governors-part2.md#hyg3)

\-[HYGOV](40-ts-models-governors-part2.md#hygov)

\-[HYGOVR](40-ts-models-governors-part2.md#hygovr)

\-[HYGOVRU](40-ts-models-governors-part3.md#hygovru)

\-[HYPID](40-ts-models-governors-part3.md#hypid)

\-[WSHYGP](40-ts-models-governors-part4.md#wshygp)

*Machine Models:*

\-[GENCLS](38-ts-models-machine.md#gencls)

\-[STCON](38-ts-models-machine.md#stcon)

*Stabilizers Models:*

\-[IEEEST](41-ts-models-stabilizers.md#ieeest)

\-[PSS2A](41-ts-models-stabilizers.md#pss2a)

\-[PSS2B](41-ts-models-stabilizers.md#pss2b)

\-[PSSSB](41-ts-models-stabilizers.md#psssb)

---

<a id="whats-new"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New_v20.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New_v20.htm)*

Simulator Version 20 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

To see a list of what was new in Simulator Version 19 click [here](#whats-new-1).

  - Installation and Simulator Executable
  - 64-bit beta-quality version of the software is included as part of the standard installation
  - Zip files for patches will no longer be available. The installation MSI file is used for both the full installation and patches.
  - [Auxiliary Files and Display Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - Option to *Use Concise Variable Names and Headers* is now set to true by default
  - Multiple auxiliary files can be loaded simultaneously when loading using the *File \> Load Auxiliary* option or the *Load \> Auxiliary File* option on the local menu of case information displays
  - [Auxiliary File SCRIPT](03-cases-files-and-formats.md#auxiliary-file-format-aux) and [SimAuto](33-simauto-overview-and-setup.md#automation-server) 
  - New Script Commands and SimAuto Functions
  - ClearPowerFlowSolutionAidValues
  - CTGSaveViolationMatrices
  - DeleteDevice
  - DiffFlowWriteRemovedEPC
  - EMPCalculate
  - ExportOneline
  - IdentifyBreakersForScheduledActions
  - ImportDDLAsTranslation
  - InjectionGroupCreate
  - LoadAuxDirectory
  - LoadEMS
  - MessageBox
  - ObjectFieldsInputDialog
  - OpenBusView
  - OpenSubView
  - OpenDataView
  - RelinkAllOpenOnelines
  - SaveDataEPC
  - SetScheduleView
  - SetScheduleWindow
  - TSAutoInsertDistRelay
  - TSAutoInsertZPOTT
  - TSCalculateCriticalClearTime
  - TSLoadRDB
  - TSLoadRelayCSV
  - UpdateIslandsAndBusStatus
  - UIVisible SimAuto property will allow Simulator to be visible while running SimAuto
  - New pwrworld 20.0 type library contains this property
  - Changes to Existing Script Commands and SimAuto Functions
  - Added optional parameter PostClosureLCDF to CalculateLODF script command. This option specifies if line closure sensitivities should be calculated relative to the post-closure flow (LCDF) or pre-closure flow (MLCDF) on the line being closed.
  - Added optional parameter PostClosureLCDF to the CalculateLODFMatrix script command. This option specifies if line closure sensitivities should be calculated relative to the post-closure flow (LCDF) or pre-closure flow (MLCDF) on the line being closed.
  - Added optional parameter SaveDependencies to CTGWriteResultsAndOptions to specify if all objects needed to define selected objects are also saved
  - Added optional parameter SaveDependencies to CTGWriteAllOptions to specify if all objects needed to define selected objects are also saved
  - Added AbortOnError parameter to CalculateTLR script command that indicates if the TLR calculation fails whether the auxiliary file containing the command should cease processing or continue
  - Added parameter CloseNormallyClosedDisconnects to CloseWithBreakers script command that will close any disconnect that is normally closed but currently open when searching for breakers
  - DiffFlowMode can also be specified as CHANGE
  - For the OpenOneline script command wildcards are allowed in the filename when opening DDL files
  - Added parameter OpenNormallyOpenDisconnects to OpenWithBreakers script command that will open any disconnect that is normally open but currently closed when searching for breakers
  - Added Delimiter parameter to Renumber3WXFormerStarBuses script command
  - Added Delimiter parameter to RenumberMSLineDummyBuses script command
  - Added parameter UseRight to ReassignIDs script command that will use the last two characters of the specified field that contains the new IDs
  - For the SetCurrentDirectory script command the FileDirectory can now be specified using special keywords starting with @. The & format that allows specification of a Model Expression or model field can also be used.
  - @MODELFIELD\<objecttype 'key1' 'key2' 'key3' variablename:digits:rod\> can be used as special keyword to insert the value of a model field as parts of filenames and other text specified in script commands
  - When using the LoadAXD script command and the oneline is not open, a new oneline will be created even if calling the script command from Simulator. Previously, this would only happen when calling from SimAuto or Retriever.
  - Added new parameter MaxOption to the CTGCreateContingentInterfaces(filtername, MaxOption) script command that will allow specification of whether interfaces should be created for all violations or based on the highest overload of a branch, highest overload of a contingency, or union of the branch and contingency overloads.
  - The OpenOneline script command will now open a oneline if called from Simulator. Previously, this would only work when calling from SimAuto or Retriever.
  - When using the special syntax in a script command to force an Open or Save Dialog to appear, Simulator will now automatically set the initial directory of the Open or Save Dialog to whatever the presently CurrentDirectory is as managed by the script command SetCurrentDirectory().
  - In the SetScheduledVoltageForABus script command, the objecttype BUS is no longer required when identifying the bus. Appropriate key fields can simply be used without the objecttype. If the bus cannot be found, the script command will not result in a fatal error that will prevent other script commands in the same aux file from processing.
  - Modified the script command CalculateLODFMatrix() to add an optional sixth parameter for "FilterMonitorInterface". The syntax for this parameter is the same as FilterMonitor which defines the which Branch objects to monitor. FilterMonitorInterface will instead define which Interfaces to monitor and calculate LODFs on.
  - Modified RestoreState script command to take optional parameter that can be USER, LASTSUCCESSFUL, or BEFOREFAILED. USER will restore the user specified state stored by the script command StoreState. LASTSUCCESSFUL will restore the state from the last successful power flow solution. BEFOREFAILED will restore the state before a failed power flow solution. This will work with power flow solved through the GUI or using the SolvePowerFlow script command.
  - Modified so that when creating a generator from an AUX file we default the EnforceMWLimit field to YES. Previously it was defaulted to NO.
  - Added a new field for a Branch called MeteredBus. This shows the same information as MeteredEnd bus instead you enter the number of the bus which is metered. This make coordination of field when reading/writing from an AUX file or another database easier because the order in which key fields are listed doesn't matter then. The existing field MeteredEnd will say FROM or TO, but this must be coordinated with the how the From/To bus of the branch are defined.
  - [Aux Export Format Description](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system)
  - Added more built-in formats for creating auxiliary files for various tools
  - [Available Transfer Capability (ATC)](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)
  - Merit Order Close Ramping is now an injection group ramping option to simulate the transfer
  - Added field Transfer Limiter Result to ATCScenario object type that allows access to the value that is shown in the Results table in the GUI
  - [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays)
  - Added support for filtering on DateTime fields
  - Quick Filter dropdown on Case Information Toolbar provides direct access to options for more quickly building a quick filter without needing to open the dialog
  - When copying the value of one field to another field, floating point values can be copied into integer fields. This is done by truncating the floating point field.
  - Added the DataMaintainerInherit YES/NO field which is enterable for the following objects: Bus, Gen, Load, Shunt, LineShunt, Branch, 3WXFormer, DFACTS, DCTransmissionLine, MTDCRecord and VSCDCLine. Setting this value to NO will prevent these objects from inheriting their DataMaintainer from their terminal bus objects.
  - Added the DataMaintainerInheritBlock YES/NO field for a Bus and Substation object. For a Bus, set to YES to block the inheritance of the Data Maintainer for other objects connected to this bus. For example, if this is YES, generators at this bus will not inherit the Data Maintainer from this bus. For a Substation, set to YES to block the inheritance of the Data Maintainer for the buses in this substation.
  - Modified so that one can edit the intermediate bus numbers of MultiSectionLine objects while in Edit Mode directly on the fields shown the intermediate bus numbers on the MSLine case information display.
  - Added ability to edit the Star Bus Number of a three-winding transformer while in edit mode. This has the effect of renumbering the star bus.
  - Allow the number of generator cost curve bid points to be set to 0. When this is done, all of the curve points are deleted. If the cost model is PiecewiseLinear, it will be set to None.
  - Added dc line status as a field that is available with the dc line case information display.
  - Added Bus kV Actual, Bus Per Unit Magnitude, and Bus Angle (degrees) fields for Line Shunts for the bus at which the shunt is located.
  - Added additional fields to 3WXformer objects for MW, Mvar, MVA, Amps, PercentMVA, and Percent (with variations of Pri, Sec, and Ter on each)
  - Added new field to Island records to show the Number of Generators, Number of Loads, and Number of Switched Shunts in an island. This can be helpful in determining which islands are of any interest.
  - Added two new functions to the Expression for looking for sub-strings inside other strings. These mimic the Microsoft Excel functions Find and Search. Find(Find\_Text, Within\_Text, \[Start\_Num\]). Returns the integer position of the sub-string Find\_Text looking inside the string Within\_Text. You may optionally instruct us to start the search at character position Start\_Num. If Start\_Num is not specified, then we start at position 1. The search is case-sensitive. You may not use wildcard characters \* or ?. Search(Find\_Text, Within\_Text, \[Start\_Num\]). Returns the integer position of the sub-string Find\_Text looking inside the string Within\_Text. You may optionally instruct us to start the search at character position Start\_Num. If Start\_Num is not specified, then we start at position 1. The search is not case-sensitive. Also the Find\_Text may include a ? to indicate any single character of an \* to indicate any number of characters.
  - Allow insert of a new Branch on the Transformer Controls table.
  - Modified how Simulator determines the tap integer position for transformers. Previously Simulator would treat the 0 position as the tap in the middle of the TapMax/TapMin range. This has been changes so that the 0 position is always represented by 1.0000 on the TRANSFORMER BASE. Positive tap positions then move upwards from there and negative tap positions move downwards from there.
  - Added the ability to edit the variable transformer tap ratio (or phase) by editing the Integer Tap Position directly instead of by editing the TapRatio or Phase.
  - Added new fields for Branch objects to show the Maximum Integer Tap Position and Minimum Integer Tap Position. These are calculated from the the TapMax and TapMin values (just as the TapMaxxfbase and TapMinxfbase are calculated). Also added the ability to edit these fields which will modify the TapMax and TapMin field as appropriate.
  - Added 2 new user-entered fields to a transformer for use in translating Simulator's integer tap position into an integer that uses the EMS convention. One field is TapPosEMSNom which specifies the integer considered to be at the nominal tap (1.0000 on transformer base or 0 degrees for a phase shifter). The second field is the TapPosEMSStepSign which is either +1 or -1. TapPosEMSStepSign = +1 indicates that a positive TapPosEMS means an increasing tap ratio going up to TapMax. TapPosEMSStepSign = -1 indicates that a positive TapPosEMS means a decreasing tap ratio going down to TapMin. The translation is as follows: TapPosEMS=TapPosEMSNom+(TapPosEMSNom\*TapPosEMSStepSign)
  - Added a new field to show the integer tap position using the EMS convention. The tap or phase can then be edited using this field as well. The EMS convention uses the following conversion: TapPosEMS=TapPosEMSNom+(TapPos\*TapPosEMSStepSign). When editing this field the Tap or Phase of the transformer will be edited as appropriate.Added a new field to show the integer max tap position using the EMS convention. If TapPosEMSStepSign = +1, then TapPosEMSMin = TapPosEMSNom + TapPosMin. If TapPosEMSStepSign = -1, then TapPosEMSMin = TapPosEMSNom - TapPosMax. Notice that when TapPosEMSStepSign = -1 then TapPosEMSMin is related to TapPosMax. When editing this field the respective TapMin or TapMax are edited as appropriate.
  - Added a new field to show the integer min tap position using the EMS convention. If TapPosEMSStepSign = +1, then TapPosEMSMax = TapPosEMSNom + TapPosMax. If TapPosEMSStepSign = -1, then TapPosEMSMax = TapPosEMSNom - TapPosMin. Notice that when TapPosEMSStepSign = -1 then TapPosEMSMax is related to TapPosMin. When editing this field the respective TapMin or TapMax are edited as appropriate.
  - Added a column to the Branch table of the Lines that Create Islands dialog to show a list of the buses islanded if the branch is open, as bus numbers separated by commas.
  - Added support for filtering across objecttypes for the BalancingAuthority objects. This impacts the following objects: Bus, Gen, Load, Shunt, Branch, DCTransmissionLine, VSCDCLine, Zone, Area, SuperArea, Substation, SuperBus, Subnet, ReactiveCapability, 3WXFormer, MultiSectionLine objects.
  - For a MultisectionLine object, added new fields BusInt, BusInt:1, BusInt:2 ... BusInt:20 which list the intermediate buses of a multisection line. This permits the creation of multi-section lines with up to 21 intermediate buses (22 intermediate branches) without using the section.
  - Added the ability to turn on hints on Case Info Displays that display column metrics for selected cells. Settings for these hints are on the Case Information Display tab of the Simulator Options dialog.
  - Added fields for three-winding transformers to show MonitorPri, MonitorSec, MonitorTer, LimitSetPri, LimitSetSec, and LimitSetTer.
  - Added new Interruptible field for loads. This is an information only field.
  - Added a new generator field "UnitTypeCode" that shows the two character code for the UnitType. The field is the same as UnitType, just shorter.
  - Added a field with generators called Number of Mvar Capability Curve Points.
  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - When using the Solve and Set as Reference option, a prompt will now appear asking if the user wants to continue with this operation.
  - *When using Integrated Topology Processing, monitor only the primary bus for each superbus* option will now monitor the primary bus for each superbus, bus with the highest low voltage limit, and bus with the lowest high voltage limit.
  - Added Dependency Explorer to analyze all of the objects being used by contingencies and remedial actions
  - Added action to Close a specified Number of Elements in an Injection Group
  - Added Injection Group action for Set To and Change By Best Fit Open
  - Added Interface action for Set To and Change By Merit Order Open
  - Added Interface action for Set To and Change By MW Effect Open
  - Added Interface action for Set To and Change By Best Fit Open
  - Added Substation actions for Set To and Change By in MW and Percent to adjust the online generators in the substation
  - Added Phase Shifter actions for Set To and Change By in Degrees to adjust the phase shifter angle
  - Added Script action that will allow specifying a list of script commands as a contingency action
  - Power flow solution option *Evaluate Power Flow Solution for Each Island* will prevent a failed contingency solution if at least one island solves
  - Contingency Processed field now has PARTIAL as an option if solving based on multiple islands and some of the islands converge and some do not
  - *Prevent new island without enough controllable generation* option will not allow new islands to be considered viable during the contingency solution if they do not have enough controllable generation to meet the load and losses in the island
  - *Report Violations for Islands* option allows monitoring islands during the contingency solution
  - If a contingency has been processed, contingency records are highlighted based on the Solved field
  - When choosing to save a case, a check is done to help ensure that a user does not save a post-contingency system state accidentally
  - New options added in various tools to save objects used by other objects (dependencies) when saving contingency definitions and associated objects to file
  - New option to save using Area/Zone filters for contingency options and limit monitoring settings related to area, bus, gen, and shunt objects
  - Added Model Result Override object that allows overriding the result of Model Conditions and Model Expressions
  - Remedial Actions and Remedial Action Elements have an Arming Criteria and Arming Status that determine if they are armed
  - Added screening process that uses linear analysis to screen contingencies prior to running full AC analysis on contingencies that pass the screening
  - Added *Ignore Remedial Action Elements if Model Criteria is True in Contingency Reference State* option
  - Added options for saving contingency results to file instead of computer memory
  - New contingency violation category of Unsolved indicates if the contingency solution did not converge
  - Contingency records can be filtered by filters created for object type LimitViol. This is useful for finding contingencies that have violations of specific elements.
  - Added ability for LimitViol and ViolationCTG object types to return EMS identifying information from the violated element
  - Percent field for a voltage violation will now show a value that is based on the voltage limit
  - New Source List field for LimitViol object type used to indicate the origin of the violation when comparing two lists of results
  - Added fields to LimitViol and ViolationCTG object types for showing Reference State fields in the Comparison Case
  - Violations have fields showing scaled results that determine the limit and percent for any of the possible limits for an object. This allows storing the limit violations against the most restrictive rating set and still show what the percentage would be against all limit sets.
  - Include Remedial Action field allows exclusion of remedial actions for specified contingencies
  - Calculation Method field with contingency records indicates how the contingency was solved
  - Post Contingency Solution Auxiliary File can be specified with contingency options. This is loaded after the contingency is solved.
  - New object type ContingencyActive allows access to fields associated with the currently active contingency
  - CTG\_Options object has Active Contingency field that provides the name of the active contingency
  - Auto inserting contingencies can be done by Line Shunts
  - Auto inserting contingencies can be done by Bus Groupings
  - Bus Groupings determined by explicitly defined breakers and Implicit Breakers defined with buses that allow the user to indicate where breakers exist in the case without all actual breakers defined
  - Custom Monitors have options for tripping an element if it meets a tripping filter or aborting the entire simulation
  - Violation CTG Note object added to stores notes for contingency violations
  - Added new field called Voltage Reduce Load MW to contingency results that returns the amount of total load MW that has been reduced because of the solution options for Minimum Voltage for Constant Power and Constant Current Load
  - For contingency actions using Open with Breakers, the flow on the element being opened as well as the flow on the breakers being opened dynamically are included in the What Actually Occurred information
  - Time delays are enforced when using the Iterated Linear Contingency process
  - Added local menu to the list of Contingency Violation List (shows all violations for all contingencies) to Solve Selected Contingency and Contingency Show Dialog
  - Interface Open actions will open generators and loads in addition to the ac branches in the interface
  - Added a new field to a LimitViol named "SourceList" that will be useful when comparing two lists of contingencies results. This field will indicate which list of results this violation existed in. It will either show Both, Comparison, or Controlling.
  - Added 7 new fields for a LimitViol object which give information about the violated end of the violated element. (BusNumViolEnd, BusNameViolEnd, NomkVViolEnd, AreaNameViolEnd, BANameViolEnd, ZoneNameViolEnd, SubNameViolEnd). These fields are then available in the ViolationCTG object as well with the field names LV\_BusNumViolEnd, LV\_BusNameViolEnd, LV\_NomkVViolEnd, LV\_AreaNameViolEnd, LV\_BANameViolEnd, LV\_ZoneNameViolEnd, LV\_SubNameViolEnd.
  - Added option with Contingency Violation Matrices to include unsolvable contingencies. When this is true the Solved field will be automatically added to the contingency matrix. Added optional parameter with CTGSaveViolationMatrices script command to IncludeUnsolvableCTGs for the same functionality.
  - Modified so that the "Object" field of a ContingencyElement, RemedialActionElement, CTGElementBlockElement, PostPowerFlowActionsElement for any elements related to changing branch impedance, bypass, phase shift angle, or MW setpoint, the "Object" field could start with either "SERIESCAP" or with "PHASESHIFTER". The Object field will now always start with the string "BRANCH" instead to make it consistent with the treatment of other objects.
  - Modified so that the WhatOccurredDuringContingency objects have the ability to define CustomExpressions and CustomExpressionStrings.
  - Added ability for the LimitViol and ViolationCTG object to return the EMS Topology related strings from the Violated Element such as EMSID and EMSType. Also, for the Branch objects returns the EMSLineID, EMSID2From, EMSID2To, EMSPSID, and EMSCBTyp.
  - Added fields to a LimitViol and thus the ViolationCTG object for showing the Reference State fields in the Comparison Case. Also added fields for the difference between the Comparison and Controlling case for the reference state values.
  - Modified the various Contingency fields showing the number of violations so that if the Solved field is equal to "RESERVE LIMITS", then we now show the number of violations that were recorded anyway. Previously we showed the string "All make-up power at limits". We will now assume the user can look at the Solved field to know this. The violations are still recorded when "RESERVE LIMITS" is listed, so showing the user this count is useful.
  - When a contingency solution results in the change in MW injection (usually loss of generation) such that the generators in the island are unable to make-up for this change, then Simulator will return the string "RESERVE LIMITS" in the Violations columns for a particular contingency. This is done to indicate that the contingency result may not be reliable because all the additional make-up power has gone to the island slack bus. This has been modified so that if the island has ZERO generators which are set to (AGC=YES) and (PartFact\>0) then we do not bother returning the RESERVE LIMITS flag.
  - Multi-section lines are now supported by Custom Monitors.
  - Added Area, Zone and Balancing Authority fields to Contingency Elements and increased the numbers to include up to 8 of them instead of 4.
  - Contingency Violation Matrices tables now allow access to the fields associated with the object type displayed in the row of the table.
  - When running contingency analysis from the GUI and results already exist, the user will be prompted if all results should be cleared or only if the results for contingencies that are not skipped should be cleared. Added another optional parameter to CTGSolveAll script command called ClearAllResults that will accomplish the same prompting as what is done in the GUI. Script command is now CTGSolveAll(DoDistributed, ClearAllResults) with both parameters optional. ClearAllResults = YES by default.
  - [Difference Case](08-view-case-data-tools.md#difference-case)
  - This tool has been renamed from being previously named Difference Flows
  - Many improvements to include more fields in the comparison and make it clearer which fields are included
  - *Change Case* is a new mode that will only show values that have changed
  - *Show Present|Base In Difference and Change* option that will show the actual values instead of the difference or change when viewing in Difference or Change modes
  - Color coding to better indicate differences
  - Improvements when saving differences to auxiliary files for use in replicating the changes in other cases
  - Pages for accessing differences by Type in addition to objects in New/Removed/Both sets of data
  - Added support for showing differences on all transient stability model input data
  - [Fault Analysis](27-fault-analysis.md#fault-analysis)
  - Additional fields for sequence resistance and reactance secondary and zero sequence neutral resistance and reactance
  - [File Formats](03-cases-files-and-formats.md#case-formats) 
  - EPC Format
  - Version 21 supported for reading and writing
  - Modified reading area records to set the area control to Off AGC if the absolute value of the difference between desired Pnet and actual Pnet defined with the area record is greater than 5 times the tolerance given with the area record
  - When loading an EPC file, we now automatically use the advanced solution option to "Model Phase Shifters as Discrete Controls" as this represents how EPC files treat phase shifters.
  - Modified how the "ta" field of a z table record is written out to an EPC file. If the first transformer used by the z table was FIXED then Simulator was always setting the "ta=0". We now only set the z table based on the existing of a transformer which has a mode of Phase, LTC, or Mvar. Otherwise we base it on the average absolute value of taps specified in the impedance correction table.
  - Added reading and writing of data maintainer with GE EPC files for most objects. DC buses, DC lines, and DC converters have not been completed yet. Data maintainer is supported in GE EPC version 21. There are now options to write in version 21.
  - When reading in an EPC file we no longer ask for the version number because it doesn't matter. We can read the file regardless and will read any data that is there.
  - Modified writing switched shunts that are now set to AutoControl = NO so that they are written to the EPC file as FIXED control. This prevents them from being read back in on some other form of control and moving, when their autocontrol = no really meant they were at fixed output. This will lose whatever type of control the switched shunt may have been set to in Simulator, but prevents the VAR output from changing to something else when read in from the EPC file.
  - Added support for reading the Balancing Authority information from the EPC file format
  - Modified to read the DistMW, DistMvar and DistStatus fields from the EPC Version 19 files
  - When reading an EPC file, if the Sum of Ownership participation for an object sums to a value which is not 1.000 then Simulator will automatically scale the values so they do sum to 100%. Log messages have been added when summations are not near 1.000 to help flag potential discrepancies in the input data. If the summation is greater than 3.00 or less than 0.50 then a log message is written. Also, if the summation is 0.000 then a log message is not written because Simulator will then simply default the ownership based on the terminal buses of the device.
  - RAW Format
  - When writing out RAW files to version 31 and later, now write out 8 decimal places for per unit voltages and 6 decimal places for voltage angles
  - When loading an RAW file, we now automatically disable the advanced solution option to "Model Phase Shifters as Discrete Controls" as this represents how RAW files treat phase shifters.
  - When loading RAW files, added option to specify a default switched shunt ID.
  - hdbexport CSV Format
  - POLE, DCCNV, VSC, DCND, and DCLN records in the hdbexport file can now be translated into multi-terminal dc lines and VSC dc lines within Simulator. This translation is optional. By default the user will be prompted when these records are found and asked if they want to do the translation. Options can then be set to never translate, always translate, or prompt to translate on subsequent loads of a CSV file.
  - RASMOM loading is now supported
  - The option to *Close Breakers to Energize Switched Shunts* is set to be used by default when loading hdbexport case file
  - Added the ability to save known fields to a pattern file
  - Store additional EMS identifying fields for various objects. These are found in the Topology folder in the list of available fields for each type of object.
  - When reading an hdbexport CSV file, we have frequently encountered in-service branch that have a large angle difference and are radially connect to a superbus that has no load, generation or shunts connect to them. This should not happen, so to prevent large power flow mismatches we will automatically change the radially connect super bus voltage angles to be consistent. This is done at the start of a power flow solution.
  - Several years ago, we modified reading the CB record so that if the TYPE field existed, then we would use that to determine whether a branch was a breaker, disconnect, etc. from this field. This was fine, but we then also modified so that we stored the "EMSCBTyp" string of the branch as this value. This was causing trouble when reading the RAS and Contingency records because the proper identifier for use in linking elements of RAS and Contingency records is to use the CBTyp.ID which had been lost by the changes made several years ago. The TYPE field will be used to determine what type of a device the CB is, however the field EMSCBTyp will now always be populated with CBTyp.ID.
  - A file with a combination of records using a pattern file and using no pattern file can now be loaded without error. Appropriate warning messages are written to the log.
  - When reading the hdbexport CSV file modified to interpret the VARMAN\_UN field for a UN record to indicate whether to use the Capability Curve. If the value is TRUE, then the Capability Curve will not be used.
  - When reading the Areva hdbexport case file, modified reading of CP (switched shunt) records so that the AVR\_CP field toggles the Field AutoControl in Simulator to either YES or NO. Previously the AVR\_CP determined whether the switched shunt was set to a Distcrete or Fixed mode.
  - ABB Spider
  - The option to *Close Breakers to Energize Switched Shunts* is set to be used by default when loading a file
  - KML Format
  - Added ability to open KML files by number, name\_kv, or label
  - GIC Format
  - Added support for loading the GMD information used in PSS/E
  - MatPower Format
  - Added ability to write the \*.M files used for input to the MatPower MATLAB function.
  - WebFG Definition
  - This menu format can be loaded into the Oneline Viewer to create a custom menu
  - Modified to initialize the generator field EnforceMWLimits for all the various file types. Previously this was only handled for RAW and EPC files, but it really needed to be handled for hdbexport CSV, MatPower, UCTE, Siemens, IPF etc. as well. Now after reading all non-PowerWorld file formats any generator that meets both of the following criteria will enforce be set to EnforceMWLimits = NO. 1. Generator is online (both CLOSED and attached to a connected bus) 2. Generator is more than 5 MWs outside of it's limits: \[MW \< (MWMin - 0.5\] OR \[MW \> (MWMax + 0.5)\]. The thinking is that if the generator is clearly outside its limits then limit enforcement is not expected. The 0.5 MW tolerance is used to bias the decision to continue enforcing MW limits.
  - General 
  - 15 negative interface limits can be specified. These have been integrated into Contingency Analysis, ATC, and OPF tools.
  - *Status Branch* field added to switched shunts that links a switched shunt to a particular branch. The status of the switched shunt is then affected by the status of the specified branch.
  - SVCs can control any switched shunt except for other SVCs
  - New object Bus Pair that will monitor the angle difference between two different buses
  - Model Result Override object has been added. This allows overriding the result of a Model Condition, Model Filter, or Model Expression by ignoring the defined logic and specifying the result directly. These are useful with RAS modeling when real-time information is available to determine if an action is armed.
  - Scaling using an injection group can now be done using Merit Order Close method
  - Auto Control field added to switched shunts that determines if a shunt is allowed to be automatically controlled
  - Added a new generator Unit Type of "SV (Static Var Compensator)" to be used when a generator is representing an SVC
  - Added 9 new Unit Types based on updated DOE FORM EIA-860. New options are: BA (Energy Storage, Battery) CP (Energy Storage, Concentrated Solar Power) FW (Energy Storage, Flywheel) ES (Energy Storage, Other) HA (Hydrokinetic, Axial Flow Turbine) HB (Hydrokinetic, Wave Buoy) HK (Hydrokinetic, Other) BT (Turbines Used in a Bnary Cycle, including those used for geothermal applications) WS (Wind Turbine, Offshore)
  - Added additional generator unit type codes of W1, W2, W3, and W4. These are useful for those building WECC base cases to match the designation used there to distinguish between Type 1, 2, 3, and 4 wind turbines.
  - Added Implicit Breaker field to buses to indicate that a breaker exists between the bus and all attached devices. This is used when identifying objects by Bus Grouping.
  - Model Conditions and Model Expressions can be defined for DC Converters
  - Added new fields for an island showing Max/Min Generator MW/Mvar
  - Equivalencing tool now has an option to Model Generation and Load as Current Injections
  - When showing base case voltage violations for areas and zones, bus voltage violations can now be separated into low and high voltage violations
  - Alpha and Gamma angle fields have been added for MTDC converters
  - Switched shunt Auto Control can be set to FORCE which will ignore the global options for enabling switched shunts or SVCs as appropriate
  - Modified to allow an owner percentage of zero (0). Previously we would completely remove this designation. Obviously we would not recommend doing this, but some users specify these percentages (likely accidentally) and wanted to be able to not completely lose the fact that the owner was a partial owner of the object.
  - Added options to filter by "string contains", "not string contains", "string starts with", and "not string starts with" for numeric fields.
  - Geographic Data View
  - Supported with Supplemental Data
  - [GIC Analysis](47-geomagnetically-induced-currents.md#gic-analysis)
  - High-Altitude Electromagnetic Pulse (HEMP or EMP) modeling
  - Added the ability to show GIC transformer losses by substation.
  - Added ability to show GICXFormer NeutralR on case info, and change LineShunt GIC R values.
  - For GICs added DoShowDialog for lines from voltage input display.
  - Added field to show GIC substation electric field direction.
  - Added new fields for specifying DC GIC resistance for SwitchedShunt and LineShunt objects.
  - Added a new field for an extra transformer neutral resistance
  - Integrated Topology Processing
  - Open or Close with Breakers local menu options on case information displays and onelines have additional options for what should be switched including options to open or close disconnects based on their normal status
  - Switched shunts are now included as connected objects indicating that a line is closed at one end when determining Derived Status
  - The open and close with breaker algorithms will exclude switching breakers that connect switched shunts when looking for breakers for a transmission line
  - *OpenOrCloseBreakersAllow* field added to branches that must be set to YES for a switching device to be allowed to switch in any of the algorithms that determine which breakers and other switching devices are needed to open or close a device
  - *Update Allow Open or Close Breakers* tool added to update the *OpenOrCloseBreakersAllow* field for branches
  - [Limit Monitoring](18-general-tools.md#limit-monitoring-settings)
  - *Only show the primary bus for each superbus* option will now monitor the primary bus for each superbus, bus with the highest low voltage limit, and bus with the lowest high voltage limit.
  - Option *Do not monitor radial lines and buses* is ignored if using Integrated Topology Processing
  - Added options for monitoring Bus Pairs in base case and during contingencies
  - Added a new field *Limit Monitoring\\Violated Using Normal Limits* for bus, branch, interface, and bus pair objects. This field will show *YES* if the device is presently both monitored and violated according to all of the limit monitoring setting options and evaluated against normal limits.
  - Oneline Diagrams
  - New translations have been added for Areva diagram import to render overview diagrams
  - Oneline Viewer performance has been greatly improved along with the addition of history buttons and custom menus
  - Paths defined in the Oneline Browsing Path will be searched in the order in which they are defined when looking for onelines and Areva DDL files to open
  - Added Windows DPI Setting option to the Bus View Layout Options that is useful with higher resolution monitors to prevent scaling options with the bus view text
  - Script command can be attached to a background object so that clicking on the object executes the script command
  - Can now execute script commands through oneline links on the oneline instead of the power system. All that needs to be done is to prepend \<ONELINE\> before the script command to be executed.
  - Background objects can be linked to data objects. If they are linked, the data dialogs for the linked object can be open while in run mode.
  - When inserting new Circuit Breaker objects to a oneline diagram the Shape is normally set the "Use Default". This has been changed so that 1. For a branch with BranchDeviceType = Disconnect or Load Break Disconnect, then a Shape is set to "Switchgear" 2. For a branch with BranchDeviceType = Ground Disconnect, the Shape is set to "Earthing Switch
  - Added various support throughout for rotating background objects. Also modified so that objects can be rotated about their center instead of always around the upper left corner.
  - Added new dialog to show Objects Not on Oneline. This will display data objects that are not currently represented on the oneline. There is also an option to show objects that are NOT on the oneline that are connected to buses that ARE on the oneline.
  - Modified contour dialog so that the enabling/disabling of the items to contour can consider Geographic Data Views.
  - Added ability for showing dialogs for Generators, Loads, and Branches when right-clicking on the various background lines shown on Areva DDL oneline diagrams inside Simulator.
  - OPF
  - Added OPF option to "Include only online devices in Injection Group calculation". The default behavior has always been to exclude offline devices. This option will allow you to include them.
  - Power Flow Solution
  - *Check Back Off Immediately* option for generator Mvar limits is checked by default
  - Added *Evaluate Power Flow Solution for Each Island* option that will cause the solution for a particular island to be abandoned if it is not converging but the solution for other islands will continue as long as at least one island converges
  - When using the bus integer field "Priority" to influence the slack buses chosen, Simulator was using that integer even if the bus did not have any CLOSED generators. This meant that if the bus with the highest priority integer did not even have a closed generator then the island would end up being disconnected because no viable slack bus was chosen. This has been fixed so that any bus without any closed generation is ignored in the choice of a slack bus regardless of the Priority specified.
  - The automatic choice of a system slack bus presently prefers generators with a maximum MW of less than 5000 MW. This is so that fake generators are not chosen as a system slack bus. This has been modified so that we also prefer generators which do not have a negative Minimum MW as well.
  - Modified Simulator's check for performing Angle Smoothing when closing in a series of branches. If more than 5 sets of series-connected branches are found at the same time, then we will no longer perform angle smoothing. This avoids situations where appending cases together results in a large number of new closed in branches at the same time. Using angle smoothing in these situations is not helpful.
  - SVC type switched shunts which had a minimum and maximum control range of 0.0 and 0.0 were being treated as though the control range was infinite (limits ignored). This has been changed so that the SVC will instead leave the min/max values as 0.0 and just never move instead.
  - [PV and QV Curve](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)
  - Merit Order Close Ramping is now an injection group ramping option to simulate the transfer
  - Added new option with PV tool to Restore Initial State on Completion of Run. The default is NO because this is what we had been doing.
  - Scheduled Actions
  - Many new features that allow better management and analysis of scheduled outages
  - Sensitivity Calculations
  - LODF dialog now has an option to calculate line closure sensitivities for full topology cases considering breakers and load break disconnects
  - LODF dialog now has an option to report line closure sensitivities relative to post-closure (LCDF) or pre-closure (MLCDF) flow on the line being closed
  - Driving Point Impedances can be calculated for each bus in the case
  - With the LODF and LODF matrix calculations, a value of 100,000,000% is returned if the line outage would cause a new island to be formed or a line closure would connect two different islands
  - Added option with TLR sensitivity dialog to calculate sensitivities for disconnected buses that contain generators or loads by transferring the sensitivity to the in-service bus on the other side of an open breaker that will energize the bus
  - [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation)
  - When changing the injection of an Injection Group and using Merit Order Dispatch, loads will now be included in the dispatch. Previously, any loads in the injection group were ignored. Loads will move towards either their minimum or maximum MW limit as appropriate. If both the minimum and maximum limits are 0, loads will only be allowed to decrease to 0 MW. Mvar load will be adjusted by keeping a constant power factor.
  - Merit Order Close Ramping is now an option for scaling injection groups
  - [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)
  - Transient Stability Options
  - Changed the default time step from 0.5 cycle to 0.25 cycle
  - Changed the default MVA convergence tolerance from 0.1 MVA to 0.01 MVA
  - When *Using PlayIn Models Set Initial Hz to First Value* option added that will initialize models assuming that system is at the first frequency value in the PlayIn information rather than initializing at nominal frequency
  - Added network equations solution option to *Abort after number of failed solutions* determines the number of times that the network boundary equations are allow to fail consecutively before the entire simulation is aborted
  - Options added for specify Minimum Load P (MW), Minimum Load P/Q Ratio, and Minimum Initial per unit voltage under which loads are allowed to use complex load models
  - Distribution equivalent model option for *Min Nom kV for Transformer* below which the transformer impedance will be treated as 0
  - Frequency measurement options to *Calculate Bus ROCOF (Rate of Change of Frequency)*
  - Island synchronization options that specify what happens to angles and frequency in the islands when a line is closed that connects two energized islands
  - Transient Stability Solution
  - For transient stability, modified induction machine generators so that they are not allowed to be the only type of generator in an isolated island. Previous a few type 2 wind turbines could get isolated in a small island giving very strange numerical results. Now that island will not be considered viable.
  - Improved the network boundary convergence for handling current injection machine models
  - Improved network boundary equation solution for loads which use the Distribution Equivalent.
  - Transient Limit Monitor
  - WECC 2016 voltage criteria monitoring is now built-in to Simulator
  - Modified so that when showing the Transient Limit Monitor Dialog we automatically show the Limit Duration in Cycles if it is with 0.02 cycles of being at an integer multiple of a cycle up to 60 cycles. Thus at 1, 2, 3, 4, ... 59, and 60 cycles. Also modified so that if we're within 0.02 cycles of being at 0.5, 1.5 and 2.5 cycles the dialog will show the Limit Duration in cycles. Otherwise, it will automatically show the dialog in seconds instead. Internally within Simulator, we store this value as a floating point number of seconds, but this makes it convenient for viewing on the dialog.
  - Transient Models
  - When selecting models to assign to devices, alternate names of models as they are named in other software are shown as well as the names within Simulator
  - OEL4C - Over Excitation Limiter
  - UEL2\_PTI - Under Excitation Limiter
  - LDTRPMON measurement model
  - Machine Models
  - REGC\_B
  - DER\_A
  - Load Characteristics
  - BRAKE
  - CompLoad
  - CMLD
  - Modified or added models to build up the pieces inside the CMPLDW model including: MOTOR\_CMP, LD1PAC\_CMP, LDELEC, IEEL, and MOTORX
  - Removed the MOTORWCL model. The MOTORW model can now also be closed during a simulation so the need for MOTORWCL as a special separate model. Any old PWB or AUX files that defined MOTORWCL models will continue to read fine and we will automatically translate those into MOTORW models now.
  - Added validation check to the LD1PAC, CMPLDW, and CMPLDWNF models to check if Vstall \> Vbrk. This is considered a validation error that the user must correct to run the simulation.
  - For CMPLDW and CMLD model, added check for power factor parameters PFs and PFel to not be zero. If zero then take the power factor from the attached load. If it is a model group it will set the values to default.
  - Modified so that the State and Other Fields listed for the motors of the CMPLDW and CMPLDWNF models will show the name related to the type of motor (MtypA, MtypB, MtypC, and MtypD). Previously the string would show something like "\[Type 3 Speed wr\]; \[Type 1 Bus Freq\]". It will now show either "Speed wr" or "Bus Freq" depending on what the model motor parameter types are for that load model.
  - Added the ability with the CMPLDW and CPMLDWNF models to show the Static MW, Static Mvar, Electronic MW, and Electronic MVar as OtherFields for reporting.
  - Add the field to show the tap ratio of the transformer which is part of the Distribution Equivalent for a Load. This field is available on under the Feeder Other fields.
  - Line Relay
  - TICORSRF
  - DISTRelayITR
  - DISTRelayRF
  - SCGAP
  - ZLINW
  - Added support to have multiple ZLINW models.
  - Added support for reading the system wide ZLINW line relay model
  - Added ability to add more than on DISTRELAY model at each end of a branch
  - Added a new parameter to Distrelay, Reclose if Fault persists.
  - Added the ability to let the TICORS and TICRSRF to have multiple devices in each end.
  - DC Line Model
  - CDC6T
  - CHVDC2
  - Switched shunts being controlled by SVSMOx models can have their own switched shunt transient models, i.e. MSC1, MSR1, etc., that are ignored when the SVSMOx model is inservice but will we allowed to operate when the SVSMOx model is out of service
  - USRMDL from DYR read into Simulator models
  - WTDTAU1/WTDTA1 (WTDAT1)
  - WTARAU1/WTARA1 (WTARA1)
  - WTTQAU1/WTTQA1 (WTTQA1)
  - WTPTAU1/WTPTA1 (WTPTA1)
  - REECAU1/REECA1 (REEC\_A/REECA1)
  - REECBU1 (REEC\_B/REECB1)
  - REGCAU1/REGCA1 (REGC\_A)
  - REPCAU1/REPCA1 (REPCA1)
  - REPCTA1 (REPCTA1)
  - UHSRG (UHSRG)
  - UCBGT (UCBGT)
  - UCCPSS (UCCPSS)
  - GENTPJU1 (GENTPJ)
  - HYGOVRU (HYGOVR1)
  - Added field *DistEquivMVABase* to load objects to specify directly with the load the MVA Base upon which the distribution equivalent is based
  - DYD CMPLDW2 model read and written using Simulator CompLoad and LoadComponent structures
  - Distribution equivalent models can be assigned to Owner, Zone, Area, and Load Model Group objects
  - Added the ability with the CMPLDW and CPMLDWNF models to show the Static MW, Static Mvar, Electronic MW, and Electronic MVar as OtherFields for reporting.
  - Added error check on Vac\_ref in CHVDC2. If the initial AC voltage at either the rectifier or inverter is less than this value, then the value of Vac\_ref is modified at initialization. This model doesn't make any sense if the initial voltage is below Vac\_ref.
  - Added validation error message for the IEEEG1 model if the parameters K1+K2+K3+K4\<=0. That input makes no sense.
  - Modified the ATRRelay to add a new parameter for the model at the end called “GenNum”. The default value will be 1. Valuse of either 2, 3, or 4 will switch which generators are called “1, 2, 3 and 4”. Normally the unit to which the ATRRelay model is assigned is always considered "Gen 1". By setting the GenNum parameter to 2, 3, or 4, the generator to which the ATRRelay is assigned is considered the be "GenNum" instead. The original “GenNum” generator will then become Gen 1.
  - Added initial limit violation check on the ST6B exciter for the Ilr and Va limits.
  - Modified the PIDGOV governor model to return an initial limit violation of the final point on the non-linear Gate versus Power lookup function (P3) was a power that was less than the initial mechanical power.
  - Modified the PIDGOV, WPIDHY, IEEEG1, IEEEG3\_GE, TGov3, WSIEG1, URGS3T, WSHYDD, WSHYGP, G2WSCC, GPWSCC, GAST\_GE governor models so that when setting the option of "Handling of Initial Limit Violations" to "Modify Limits and Run", Simulator will modify the final value of the nonlinear gain input curve if the initial output of the block is larger than the final value of the nonlinear gain.
  - Transient Plots
  - Value Type when plotting can now be *Derivative* which is the difference between the present point and the previous point divided by the time difference
  - When choosing to auto-save an image of a plot to file AND choosing to NOT store results to RAM, the image will be saved to file and then memory will be cleared of the results needed for the plot
  - Modified so that PlayIn signals values can be shown in the Case Information table when plotted with Time Results from RAM. Previously they could be plotted, but they would not show up when showing the values in the case information tables.
  - Added ability to specify any TSContingency object's variablename using a special string @CTGvariablename:digits:rod. This will be replaced with the value of that TSContingency field. The special string must start with @CTG and this then followed by the variablename and then optionally followed by syntax of :digits:rod to specify the number of digits and the number of decimal places to include. Example include the following 1. @CTGCategory would add the Category string 2. @CTGLoadMWIslanded:8:3 would add the LoadMWIslanded field with 8 digits and 3 decimal points 3. @CTGGenMWTripped:6:2 would add the GenMWTripped field with 6 digits and 3 decimal points Previously this was limited to the values for @CTGMemo and @CTGName. This extends this syntax to all variablename of a TSContingency object.
  - Added the load encroachment in the zones plot in DistRelays.
  - When showing a hint or dialog showing information about a plot series on a transient stability plot, we previously would show the maximum and minimum Y value experienced by the plot series. We now also show the time (x-value) at which the maximum or minimum value are achieved.
  - Modified the floating window that contains Plots for transient stability can be minimized and maximized.
  - Modified captions of plot series when showing a value that represents the %, Dev, %Dev, or d/dx of the a particular value.
  - Added a new Conversion of value to plot option for Derivative. This automatically calculated the digital derivative of the signal by taking differences between values and dividing by the time difference.
  - [Transient Stability File Format Support](36-transient-stability-overview-and-data-part2.md#data-from-external-files)
  - When reading a DYD file, we previously did checks to ensure the order in which dynamic models were read from the DYD. In older versions of other software, if a machine model was not the first model for a generator then subsequent models for that generator were ignored. Simulator had previously opened a dialog asking the user if they wanted to disable these models. This dialog has been removed so that models read from the DYD file are no longer disabled for this reason.
  - Added ability to read another PSS/E DYR Helper file for reading BAT\_PLMOD\_REMOVE commands to disable various dynamic models.
  - When reading the PIDGOV model from a DYD file, modified to ignore the MWCap value in the DYD file if it is different than the generator MVABase. The MWCap value is not used by PSLF or PSSE for this model and a value of MVABase is always assumed in those software tools. To be consistent with how the DYD format expresses the PIDGOV parameters, when reading a PIDGOV model Simulator will now always set the TRate value equal to the generator MVABase.
  - Transient Stability Contingency Definitions
  - Closing a generator through transient contingency action with options to specify Angle Difference, Voltage Setpoint, and Governor Setpoint to be used in initializing model states
  - Added Open and Close Line Shunt contingency types
  - Modified transient stability so that using the TSContingencyElement actions for changing the exciter setpoint or governor reference will do something even when used on a machine model that doesn't have an associated exciter (or governor). When no exciter exists, changing the "exciter setpoint" will change the place holder floating point number that stores the assumed output of the exciter (or electrical model for renewable plants). When no governor exists, change the "governor setpoint" will change the place holder floating point that stores the mechanical power of the generator.
  - Modified so that a TSContingency object can use a Calculated Field. It presently can only operate on the list of TSLimitViolation or the the TSResultEvent. As an example, this gives the user a way to get a count of the number of events that meet a filter on the TSContingency record
  - Added Area, Zone, Owners and Balancing Authority fields to Transient contingency and elements.
  - Transient Stability User Dialogs and Auxiliary File Support
  - Show Dialog option is available from the local menu of the Transient Stability State Limit Violations table
  - For dynamic model tables, added ability to show Custom String, Custom Float, Custom Integer, Custom Expression, Custom String Expression and Calculated fields of the object to which the dynamic model is assigned
  - Added the ability to look at the Area, Zone, Balancing Authority, Substation, and Owner information with all the various transient stability dynamic models.
  - Added Save Two Bus Equivalent button to the Terminal and State tab under Transient Stability on the Generator dialog.
  - Added ability to see the present interface flow information when viewing the transient stability state information in the user interface.
  - Added Gen MVABase field to SMIB eigenvalue display.
  - Added ability on the transient stability dialog to show only state limit violations that are "modified" or those which are "not modified". There are now three tabs to show either All, Modified, or Not Modified.
  - Transient Stability Storage
  - ROCOF (Hz) - Rate of Change of Frequency for a bus
  - Weight Avg. Speed - Area and Zone
  - GIC Mvar Losses - Area
  - GIC EField Magnitude - Substation
  - GIC EField Direction - Substation
  - GIC Total Mvar Losses - Case Information
  - GIC Maximum Transformer Ieffective (Amps) - Case Information
  - User Interface Dialogs
  - Added Data View dialog that allows user customization of data dialogs
  - Many dialogs for data objects have options to save the object to an auxiliary file
  - Added normal status of branches to the branch dialogs
  - Added buttons on the transformer tab of the branch dialogs to "Edit Integer Tap Positions" and "EMS Edit Integer Tap Positions". These buttons bring up a dialog on which which the user may edit the tap/phase, TapMax, TapMin and StepSize using the either the integer positions based around 1.0000 tap and 0.0000 phase, or using the integer positions using the EMS convention.
  - Added a button to Edit Impedances and Taps on the Transformer Voltage and MVABase to the Run Model Branch Dialog. Added notes to make it more clear that the branch dialog shows values on the system MVA and Voltage bases.
  - Increased the digits in the Generator dialog for generator voltage setpoint and generator regulated bus voltage from 4 decimals to 6 to ensure we show what input data truly is

---

<a id="whats-new-1"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New_v19.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New_v19.htm)*

Simulator Version 19 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

  - [Auxiliary Files and Display Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - Use Concise Variable Names and Headers option to show new variable names and allow saving an auxiliary file without excess information
  - Modified reading the BusSlack field of an Area and the Voltage Controlling Converter Bus for a multi-terminal DC line so that they can also read the bus by label.
  - Added ability to save out Dynamic Formatting defined for a specific oneline to an AXD file.
  - Added the Time Delay field for ContingencyElement and RemedialActionElement to the WECC Contingency AUX format.
  - Added the Time Delay field to the SUBDATA format for Contingency Elements, Global Actions, and Remedial Actions.
  - Cleaned up how the creation of a star bus is handled when creating a three-winding transformer from an AUX file. Previously you had to input a star bus that was an existing bus in the case, and thus had to create this bus ahead of time and know its number. Now the user may optionally enter special strings for BusIDStar (BusIdentifier:3).
  - Number : enter an unused bus number and Simulator will create this bus as part of creating the three-winding transformer
  - STAR : enter this and Simulator will create a star bus by starting at the primary bus number and incrementing by 1 until a unique number is found
  - STARMAX : enter this and Simulator will create a star bus with a number equal to the maximum bus number plus 1
  - STAR98765 : enter this and Simulator will create a star bus by starting at the number given after STAR and incrementing by 1 until a unique number is found
  - Syntax Note: You may optionally put a spaces between "STAR MAX" or "STAR 98765”. If the string starts with STAR but doesn’t match this syntax we default to treating it as though it said STAR only.
  - When choosing to save settings to an auxiliary file from the Contingency Analysis Dialog, we now automatically append ", AUXDEF, YES" to the DATA section headers of the following objects so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this: LimitSet, ModelExpression, ModelCondition, ModelFilter, CustomMonitor, various Contingency Definition objects.
  - When choosing to save settings to an auxiliary file from the Transient Stability Dialog, we now automatically append ", AUXDEF, YES" to the DATA section headers of the following objects so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this: TSLimitMonitor, TSContingency, TSContingencyElement, TSPlotSeries, TSPlotVertAxisGroup, TSSubPlot, TSPlot.
  - When choosing to save the PV Curve Plot definitions to an auxiliary file from the PV Curve Dialog, we now automatically append ", AUXDEF, YES" to the DATA section headers of the following objects so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this: PVPlotSeries, PVPlotVertAxisGroup, PVSubPlot, PVPlot.
  - When choosing to save Limit Monitoring setting to an Auxiliary File from the Limit Monitoring Dialog, we now automatically append ", AUXDEF, YES" to the DATA section header of the LIMITSET object so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this.
  - When choosing to save settings to an auxiliary file from the Available Transfer Capability Dialog, we now automatically append ", AUXDEF, YES" to the DATA section headers of the following objects so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this: TransferLimiter, ATCLineChange, ATCLineChangeB, ATCGeneratorChange, ATCZoneChange, TATCInterfaceChange, ATCScenario.
  - When choosing to save settings to an auxiliary file from the Default Drawing Values for New Objects Dialog, we now automatically append ", AUXDEF, YES" to the DATA section headers of all the option objects so that those objects are always created when loading the auxiliary file and a dialog does not appear prompting the user about this.
  - When using the special string \&ModelExpression or \&objecttype key key variable:loc:digits:decimals,, if no digits or decimals are specified then we use 7 decimal places. We will now also remove any trailing zeros if no decimals are specified.
  - Added new ability when pasting a string into a field (or by using the SetData() script command). The string can start the character & and then be followed by the objecttype, key fields, and then a variablename. When using a string of this type Simulator will parse to find the object referred to and then evaluate the variable name for that object and convert the string to the result of this evaluation. This feature can also be used in the Extra Strings in the SaveDataWithExtra() script command. An example of such as string is "\&Gen '563' 'ab' GenMW:0:8:3"This would instruct that the MW output of with 8 characters and 3 decimal points for the generator at bus 563 with an genid 'ab' be used.
  - Allow string expressions to be referenced by name in addition to location number.
  - [Auxiliary File SCRIPT](03-cases-files-and-formats.md#auxiliary-file-format-aux) and [SimAuto](33-simauto-overview-and-setup.md#automation-server) 
  - When closing an instance of Simulator using SimAuto, previously the various options in Simulator which are normally stored to the Windows registry were not stored. This includes settings like Distributed Computing and Keyboard shortcuts, but other things as well. Now when closing an instance of Simulator in SimAuto the behavior will be the same as though you closed from the traditional graphical interface.
  - New Script Commands and SimAuto Functions
  - Added script command CTGWriteAllOptions("filename", KeyField, UseSelectedDataMaintainers)
  - Added script command EditMultipleOnelineAction(path, LinkType, FileType)
  - Added script command CTGCreateContingentInterfaces(filter)
  - Added script command ATCCreateContingentInterfaces(filter)
  - Added script command ExpandBusTopology(BusIdentifier, TopologyType)
  - Added script command ExpandAllBusTopology
  - Added script command CTGReadFilePTI("filename") that will load a PTI CON file
  - Added script command CTGReadFilePSLF("filename") that will load a PSLF OTG file
  - Added script command CTGClearAllResults that does what the name implies. This does the same thing as the Other \> Clear All Contingency Results button on the contingency analysis dialog.
  - Added CTGApply("ContingencyName") script command to apply the actions in a contingency without solving the power flow.
  - Added two script commands, StoreState and RestoreState, that will allow user to store and restore a system state while in Run Mode.
  - Added script command CalculateLODFAdvanced(IncludePhaseShifters, FileType, MaxColumns, MinLODF, NumberFormat, DecimalPoints, OnlyIncludingLinesIncreasing, FileName) to mimic what is done on the Advanced LODF Calculation dialog in the GUI.
  - Added script command CTGCreateStuckBreakerCTGs(filter, AllowDuplicates, PrefixName, IncludeCTGLabel, BranchFieldName, SuffixName, PrefixComment, BranchFieldComment, SuffixComment).
  - Added script command CTGCreateExpandedBreakerCTGs.
  - Added script command CalculateLODFScreening(FilterNameProcess, FilterNameMonitor, IncludePhaseShifters, IncludeOpenLines, UseLODFThreshold, LODFThreshold, UseOverloadThreshold, OverloadLow, OverloadHigh, DoSaveFile, FileLocation, CustomFieldHighLODF, CustomFieldHighLODFLine, CustomFieldHighOverload, CustomFieldHighOverloadLine).
  - Added script command OpenWithBreakers(ObjectType,filter or \[object identifier\], \[SwitchingDeviceTypes\]).
  - Added the MergeMSLineSections(Filter). It does the same as the Merge Lines right click in Model Explorer.
  - Added the script command: RenameInjectionGroup("Oldname","Newname").
  - Added script command Remove3WXFormerContainer(filter) to delete 3 winding transformers matching the specified filter while leaving the internal 2 winding transformer structures intact. It takes one optional parameter, if you have a filter that specifies which 3-winding transformers you wish to delete.
  - Added script command ReassignIDs(objecttype, field, filter, UseRight) to automatically set the ids of specified Branches, Gens, Loads, or Shunts to the first two characters of a specified field. It takes each object of a specified type (currently "Branch", "Load", "Shunt", and "Gen" are supported), and sets that object's ID to the first two characters of a specified field. An optional filter parameter allows you to use a filter to only run the command on a specific group of elements. If UseRight is YES, then the last two characters of the specified field will be used to create the new id rather than the first two characters. The parameter defaults to NO.
  - Added new script command PVWriteInadequateVoltages("filename", AppendFile, InadequateType) that will write the inadequate voltages stored during a PV run to a comma separated file (CSV).
  - Added new script command CTGCompareTwoListsofContingencyResults("Controllingfilename","Comparisonfilename"); A filename may be replaced with the word PRESENT to mean the presently open contingency list.
  - Added script command DoFacilityAnalysis("filename') that will perform the Minimum Cut and create an auxiliary file with separate bus DATA sections corresponding to each path and the minimum cut.
  - Changes to Existing Script Commands and SimAuto Functions
  - Added optional parameter filter to the end of SetSensitivitiesAtOutOfServiceClosest and CalculateTLR script commands to specify a bus filter for the out of service buses that should have their sensitivities set.
  - Added optional parameter to the end of the SaveData and SaveDataWithExtra script commands to Transpose the results. Input is either YES or NO and default is NO. The transpose will only be done when writing CSV type files and will be ignored for all others.
  - Modified the SplitBus script command to specify an optional BranchDeviceType parameter that determines the type of the bus tie that is created. Full script command is now SplitBus(\[element\], NewBusNumber, InsertBusTieLine, LineOpen, BranchDeviceType).
  - In the TapTransmissionLine script command the first bus entered is now the nearbus and this will be used as the reference for the PosAlongLine. Previously, we were always using the frombus of the line as the reference.
  - Made some changes to how the user-specified extra headers and values are read when using the SaveDataWithExtra script command. Any strings enclosed in double quotes will be stripped of the enclosers. Any strings containing double double quotes will have them replaced with single double quotes. The input should be formatted in a manner to indicate how it should be written to the CSV.
  - OpenWithBreakers and CloseWithBreakers script commands now allow the specification of any branch device type that can be switched in the SwitchingDeviceTypes parameter.
  - Added new parameter "EstimateVoltages" to AppendCase script when appending either an EPC or RAW file. Set this to YES (this is the default) to estimate voltages for newly created buses and to smooth angles across newly created lines or NO not to do this.
  - Modified new feature for script commands using the magic string "@CASENAME" so that the string is replaced with the present name of the case file. It now will NOT include the file extension of the case file.
  - Modified so that the SaveData and any other script commands that save something to a file now allow you to embed the NAME of the open case file to a file being saved using a script using the magic string "@CASENAME".
  - Added "Simulation: Successful Power Flow Solution (but may have converged to a low-voltage solution)" and "Simulation: Power Flow did no Converge\!" to the message log when running a power flow using script commands.
  - Modified "Move" script action to allow moving a 3WXFormer record.
  - Added two optional parameters to the SendToExcel script command, \[Header\_List\] and \[Header\_Value\_List\]. These allow user specified headers and values to be included with the object fields.
  - Added optional parameter, SetOutOfServiceBuses, to the CalculateTLR script command. If set to YES, this will set the sensitivities of out of service buses to the sensitivity of the closest in-service buses. Default value is NO.
  - The SendToExcel script command now allows an optional parameter SortFieldList to specify the order in which the fields should be sent to Excel. The script command parameters are now SendToExcel(objecttype,\[fieldlist\],filter,UseColumnHeaders,"workbookname","worksheetname",\[SortFieldList\]).
  - Added DoDistributed parameter to the TSSolveAll(DoDistributed) script command.
  - Added command line parameters to write out the machine ID and also to load a license. Allows for scripting.
  - Added Left, Top, Width, and Height parameters to OpenOneline script command to specify form position when opening one line diagram. Syntax of script is now OpenOneline("filename", "view", FullScreen, ShowFull, LinkMethod, Left, Top, Width, Height).
  - Added the ability to use the special string @ to the file name to the DeleteFile script and to any script that uses the function InterpretFileNameIsOpenDialog to interpret the filename.
  - Scale script command now allows you not to scale LOAD MW or Mvar while scaling the other value. The \[parameters\] entries can now be specified as NO. Scale(LOAD, MW, \[-250, NO\], AREA) will only scale MW and will not scale Mvar. Scale(LOAD, MW, \[NO, -250\], AREA) will only scale Mvar and will not scale MW.
  - Return an error message when using the SimAuto OpenCaseType function with an ArevaHDB export file and the file load fails due to an unexpected error in the file.
  - [Available Transfer Capability (ATC)](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)
  - Added local menu option on the Transfer Limiters display to "Create Contingent Interface for Selection." This will create interfaces with a monitored branch being the Limiting Element in the Transfer Limiter and the contingent element in the interface being the Contingency Element of the Transfer Limiter.
  - ATC option to Allow Generator MW Limit Enforcement in Single Linear Step is now used when using the iterated methods instead of just automatically enforcing the limits if all other options are set to enforce limits. This option is not applicable if using the Economic Merit Order option with injection group ramping.
  - [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays)
  - Added options to right-click on objects in case information displays or onelines to "Open or Close with Breakers and All Disconnects".
  - Added Gen MW Setpoint field for generators to allow access to the output of the generator regardless of it being online or not
  - Eliminated the option of whether or not to highlight column headers. This is now always done.
  - When saving to a CSV file from a case information display, now have the option to save using Variable Names or Column Headers.
  - [Added 4 new fields to a BRANCH object to show the open ends charging and per unit voltage.](05-case-information-displays-by-object-part2.md#open-ended-voltage-fields)
  - Added field for bus Type (PV, PQ, etc.) to generator records.
  - Made some changes to impedance correction table fields with a transformer. Now have two fields: Correction Table Used and Correction Table Specified. The Used value might be different than the Specified value if the table that the user specifies cannot be found. If the user changes either of these fields as input to a case information display or through an auxiliary file, the Specified value will change. This should allow the retention of what the user specified but still notify if that table cannot be used. This will allow transformers to keep their impedance correction table settings if they are set prior to the impedance correction tables themselves actually being created.
  - Added new Injection Group fields to show the "Number of Gens Online", "Number of Loads Online", and "Number of Shunts Online".
  - Added new fields with branches to show the from and to MW and Mvar flows calculated from voltages and also ignoring the branch status. Fields will contain "(Calculated from voltages ignoring status)" in their name. If either of the terminal buses is disconnected, nothing will be calculated.
  - Added fields for displaying Near Bus, Far Bus and Element ID for interface elements.
  - Added a new field for branch objects to the "MWSurge Impedance Loading". This will show the surge impedance loading on the line.
  - Added field called Limit Group Percentage to branches and interfaces to return the percentage that is being used in each object's Limit Group settings.
  - Added the ability to use filtering across other object types for the InterfaceElements. They can now use Branch, Gen, Load, Interface, Injection Group, and MSLine filters directly.
  - When using the Find Text in Oneline tool, the case information table listing all of the display objects found with the specified text now has the Layer Name available for the objects.
  - Added a new field for BRANCH, GEN, and SHUNT objects called "RegBus by ObjectID". When showing this field, the option that is used to specify which key field to use in SUBDATA sections is used to identify the regulated bus by either primary, secondary, or label identifiers. When reading from an AUX file any of these identifiers can be used to identify the regulated bus.
  - With Branch and Transformer tables can now show the regulated bus for a transformer due to ZBR (very low impedance branches) groupings. The ZBR bus is the bus that is actually regulated.
  - Removed the "-CE" from the end of the column header string for custom expressions that have names.
  - Modified so that the Selected field can be edited or toggled while in Difference or Base Case mode for the Difference Flows tool.
  - The YBus case information table now allows you to change the number of digits after the decimal point.
  - Added new field to Switched Shunts, "Controlling SVC Object ID", that will allow identifying an SVC that controls a fixed shunt by any of the available key fields. Previously, the controlling SVC could only be identified by a bus number and shunt ID.
  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - Added Switched Shunt Post CTG options that will allow specification of a Control Mode for any type of switched shunt. For switched shunts that are designated as continuous during contingency analysis, the low and high voltage target range and the min and max Mvar outputs can be changed.
  - Added SOLUTIONFAIL Status type. The criteria will be evaluated only after a power flow solution failure occurs during the contingency process.
  - Injection Group MW Effect action
  - Persistent option for actions with TOPOLOGYCHECK, POSTCHECK, and SOLUTIONFAIL status
  - Time Delay has been added to a Model Filter Condition for use during contingency analysis
  - What Actually Occurred includes the order in which actions were implemented
  - When using Merit Order Open contingency actions with injection groups that contain other injection groups, the contained injection groups will be treated as a single entity and be dropped completely.
  - Greatly enhanced the dialog to save options, results, and objects from the Save button on the Contingency Anaylsis dialog.
  - Contingency Sensitivity Analysis tool that allows sensitivity analysis on a particular contingency and violation
  - Tool to convert power flow contingencies into transient stability contingencies
  - Contingency actions that refer to expression and fields will use a string that contains the special \<Expression\> or \<Field\> tags.
  - Contingency violations can now access the Monitor field for their elements so that this can be set directly from the contingency results instead of going to the Limit Monitoring Settings.
  - Added fields to display owner names and numbers with contingency elements.
  - Added ability of Limit Violations to show the Custom Float, Integer, and String fields associated with the overloaded object. This is available on both of the following tables:
  - 1\. Table showing the violations for only one contingency (on Contingency tab of dialog)
  - 2\. Table showing all contingency violations (on Results tab of dialog)
  - Added new field with branches, "Contingency ResultsMax % Ld Loading Direction", that shows the direction of flow for the branch at the maximum loading level under all contingencies for which this branch is a violation.
  - Added support with LHVRT transient stability model to trip generators in the power flow (steady state) contingency analysis if the voltage thresholds of the LHVRT are met during the contingency process.
  - Injection Group contingency actions using Merit Order or Merit Order Open now include loads in addition to generators. If using Merit Order Open and both gens and loads exist in the injection group, only loads will be opened if the change is to increase injection and only generators will be opened if the change is to decrease injection. When using Merit Order, both gens and loads will move to their appropriate limits. Loads where both the Min and Max limit are 0 can only move to 0 MW. If using Merit Order Open and the change is to increase injection and no loads exist in the injection group, generators will be moved toward their max limits instead. If the change is to decrease injection and no generators exist, loads will be moved toward their max limits instead. You may need to modify your injection groups if you have been using Merit Order with injection groups containing both loads and generators and you want to maintain the same functionality.
  - Added option to create stuck breaker contingencies. This will process each contingency that has explicit breaker outages defined and create new contingencies by treating each breaker as stuck in turn. The new contingencies will be comprised of all existing elements, minus the stuck breaker outage, plus open actions for breakers that are identified to isolate the stuck breakers.
  - Added option to create expanded breaker contingencies. This will convert any "Open with Breakers" or "Close with Breakers" contingeny actions into Open actions on explicit breakers. This will permanently modify the contingency definitions.
  - Time Delays can now be specified with power flow contingency actions. This serves as a relative ordering for the implementation of actions. Actions with the smallest time delay will be applied first during the TOPOLOGYCHECK, POSTCHECK, and SOLUTIONFAIL solution steps.
  - Added accounting of Total Dropped Load during a contingency. This shows the MW amount of load that was islanded due to a contingency action or opened due to a direct contingency action to the load.
  - Added the ability to auto-insert a list of substation outages.
  - Added a new contingency element for "Substation OPEN". This will open all AC Branches, DC Lines, and multi-terminal DC lines connected to the substation.
  - Added a new contingency element for "Substation OPEN with Breakers". This will open all breakers necessary to isolate all AC Branches and DC Lines which have exactly one terminal in this substation. Note: this will not open breakers necessary to isolate devices completely inside the substation, such as transformers.
  - Added a new contingency element for setting the resistance of a DC Line.
  - Added contingency action that will set the contingency rating of a line.
  - Added options to open the Bus View or Substation View by right-clicking on a contingency violation.
  - New option with Injection Group actions to "Evaluate Part Points In Reference State." If this option is selected and the Participation Point is set to AutoCalc = YES, the ParFac for the Participation Point will be evaluated in the contingency reference state and used wherever the ParFac is needed as part of the contingency action.
  - Added new contingency action with Injection Groups to drop a specified number of elements in the group.
  - Added option with Injection Group contingency action to specify when using Merit Order Open if the total MW dropped is allowed to exceed the desired amount or not. Previously, the default was to never exceed the desired amount.
  - Added an option to auto-insert contingencies and name them by label.
  - Modified the layout of the Contingency Definitions folder on the Options tab of the Contingency Dialog. Previously entries for All Contingency Elements, Remedial Actions, Contingency Blocks, Model Filters/Conditions/Expressions, etc. were all under one folder. They have now been split up into folders to make "Remedial Action Definitions" more prominent and also to add Contingency Blocks and Global Actions to a "Legacy Definitions" folder to discourage their future use.
  - [Difference Flows](08-view-case-data-tools.md#difference-case)
  - Started work on including input data for stability models in the Difference Flows
  - [Fault Analysis](27-fault-analysis.md#fault-analysis)
  - When defining multiple faults you now have the option to specify the position of the fault along the line. To save computation time, by default a location \>= 50 assumes a fault at the To Bus and \< 50 assumes a falut at the from bus. A checkbox has been added to instead add a dummy bus at the actual fault location.
  - Added additional locations on the Fault Analysis Dialog to specify that current values be shown in per unit or Amps.
  - Added an option to auto-insert faults and name them by label.
  - [File Formats](03-cases-files-and-formats.md#case-formats) 
  - PWB Format
  - When loading a PWB file, the message log will indicate that we are "Validating Case". This is the point at which things such as a topology check on the system to verify slack buses are defined is done. Previously this validation was done BEFORE we had actually read the case option indicating if slack buses can be dynamically added/removed. As a result, if the PWB case had been saved to NOT allow this, during an interim point in reading the PWB slack buses would created and viable islands would be created. However immediately after doing this, the option would be read indicating that slack buses should not be dynamically created. Simulator would properly remove the slack buses as soon as the user did something to cause a topology check to occur (such as solving the case or even just looking at the list of islands). However, until this happened the various case information displays may show additional viable islands and thus different amounts of MW and Mvar injections as well. This interim situation with the extra slacks was causing confusion. We have fixed this by simply doing the "Case Validation" AFTER reading the option regarding slacks.
  - PowerWorld Text Formats
  - Added special parsing when reading text descriptions of a branch to recognize special versions for an individual winding of a three-winding transformer or an individual section of a multi-section line. This is done when reading:
  - 1\. INTERFACEELEMENT objects or when reading
  - 2\. Various objects that refer to a specific object (Model Condition, Model Expressions, Custom Monitor, etc.)
  - 3\. ObjectID of a BRANCH
  - Normally a branch is identified with the string "BRANCH num1 num2 ckt" or "BRANCH 'name\_kv1' 'name\_kv2', ckt". For a multi-section line section we can now accept "BRANCH msnum1 msnum2 ckt sec" or "BRANCH 'msname\_kv1' 'msname\_kv2' ckt sec" where the msnum1 and msnum2 represent the terminal of the multi-section line aggregation and the sec represents which section of that aggregation to use.
  - For a three-winding transformer, we can now accept "BRANCH num1 num2 num3 ckt" or "BRANCH 'name\_kv1' 'name\_kv2' 'name\_kv3' ckt" where the identifiers represent the three-winding transformer key fields, but we interpret this as the BRANCH which is attached to the first terminal listed (num1 or name\_kv1).
  - Also note that when reading these special interpretations for an interface, the order of the multi-section line terminals will determine the direction being monitors and for three-winding transformer windings we will always monitor in the direction going into the transformer.
  - PTI CON Format
  - When writing out contingency containing any section of a multi-section line in the PTI CON format, write out the from bus, to bus, and circuit of the multi-section line rather than the section.
  - When loading unlinked elements from a PTI CON file, keep the unlinked element with the contingency definition. This will NOT be able to be relinked, but a record of the error will exist.
  - When loading three-winding transformers from a PTI CON file, all three winding buses must be specified. If not, there is an error and the contingency element will be unlinked.
  - PSLF OTG Format
  - Added code when reading OTG format files that will look for the keyword "newbase" in the file, and treat the rest of the contingencies in the file as n-1-1 contingencies that get combined with the first contingency read after the newbase keyword, until another newbase keyword is encountered to signify the base contingency will change from that point to the next newbase.
  - When reading contingency OTG files, added ability to read three-winding transformer outages and DC converter outages.
  - Added reading the description portion of the OTG file as comments.
  - Made parsing of name kV portions of OTG files more generic.
  - Lshunt actions, which cause a line shunt to be opened or closed or have a new susceptance value, are now supported when reading the OTG format.
  - Isolate actions, which cause a bus to be opened, are now supported when reading the OTG format.
  - EPC Format
  - Added support for reading and writing version 19 EPC files.
  - Added a new pop-up message to question the user it they want to save the bus records when saving an individual shunt, gen or transformer to an EPC file.
  - When saving selected generator records to an EPC file, bus records will also be saved so that the generator setpoint information is available.
  - When using the case information display options from a table of switched shunts or transformers to save the records to the EPC format we now also save the bus records automatically as well. The EPC format embeds the voltage regulation information for the shunts and transformers in bus records. Saving the bus records additionally helps avoid some confusion, though the user still must be careful.
  - When reading an EPC file, a generator Mvar output that is within 0.1% of the Minimum Mvar or Maximum Mvar output will now be initialized to assume that the generator is stuck at its min/max Mvar limit (it will be initialized to a PQ bus instead of a PV bus). Consider an example generator set at 29.98 Mvar which has MvarMin = -20.00 and MvarMax = 30.00. This means that it is within 0.04% of it's upper limit: (30 - 29.98)/(30 - (-20))\*100. When Simulator reads this we will assume the generator is stuck at it's maximum Mvar limit and we will change the value to 30.00 instead.
  - RAW Format
  - Modified reading of a RAW file so that when a BusType = 4 is read we enforce that this bus is dead after reading the file. We were encountering RAW files with BusTypes that were inconsistent with the line statuses that were contained in the RAW file. A bus would appear in PowerWorld Simulator to be in a viable and online island due to the fact that the bus was connected by CLOSED branches to online generation. However, in the RAW file the BusType was marked as 4 indicating it was dead. Previously PowerWorld had obeyed the branch statuses. This has been modified so that in this situation all branches that connect to this bus will be opened and an appropriate log message indicating the input file inconsistency will be written.
  - A log warning message is written if duplicate generators are encountered when reading a RAW file.
  - When reading in a 2-winding transformer in a RAW file, the cosmetic storage of the Fixed Tap ratio on the to-bus side was not being done properly when the flag CZ=2 and when the nominal kV of the secondary winding was different than the nominal kV of the bus. This has been fixed so that you can see the values on the transformer base correctly inside Simulator. Note, this did not affect the solution as we were still converting and storing everything in Simulator on the System MVA base correctly. This only effecting viewing input data on the transformer base.
  - Added process to check the voltage magnitude and angle of star buses at the end of the RAW file read, and evaluate the mismatches at the three terminal buses of the three winding transformer. If we determine that our own estimate of what we think the voltage and angle should be at the star bus results in improved mismatches at the three terminal buses, we will apply our estimated voltage values to the star bus, otherwise we will keep the voltage magnitude and angle as read from the RAW file for the star bus.
  - Added the Simulator software version number and build date to a comment at the top of an exported PTI RAW file.
  - When loading a RAW file if a bus is marked as a slack bus, but does not have any generators connected to it, Simulator will now automatically remove the slack bus designation and write a warning to the message log.
  - Modified reading of the RAW file format so that if comments are found for data records of the format /\* \[ my label, my second label \] \*/, then labels will automatically be created for the object. The string parsing removes all leading and trailing /, \*, or space characters. Then if the remaining string starts with a \[ and ends with a \], we assume that what is inside the bracket is a comma-delimited list of strings representing labels.
  - When reading a RAW file, the options to specify the starting bus number of star buses are now stored in the computer registry.
  - EPC and RAW Format
  - When loading a text file format (such as RAW or EPC file) if the file has only line feeds and not carriage returns, then a dialog appears asking if you'd like to fix the file. When loading a case from a script command however, this dialog is not wanted so we will now automatically assume that the file should be converted to Carriage Return/Line Feed pairs.
  - hdbexport CSV Format
  - Added new fields to objects when reading an hdbexport file to retain the native key fields from that file format. This will allows Simulator to directly find objects when reading in data associated with hdbexport cases without requiring the user to create labels in a consistent format. This included the following new fields. Bus: EMSType, EMSID Gen: EMSType, EMSID Load: EMSType, EMSID Shunt: EMSType, EMSID Branch: EMSType, EMSID, EMSLineID, EMSCBTyp
  - Added button to clear hdbexport cbtype mapping table.
  - Added option to create custom labels when loading an hdbexport file. Can choose whether or not to create the default labels as well.
  - Updated hdbexport file parser so that it will use the TYPE\_CB record to set the cb type when it's available (rather than following the P\_\_CBTYP and using the information on the CBTYP records).
  - Changed the parser for hdbexport files so that it supports the reverse direction of some pointers, namely: LNLIM -\> LN XFLIM -\> XF ZBLIM -\> ZBR LNSEG -\> INTRFC XFSEG -\> INTRFC ZBRSEG -\> INTRFC TABVAL -\> TABPT -\> TAB
  - Added support for PRIO field on CP records (putting it in the VarRegulationSharing property).
  - Added support pointers in either direction from XFs to PSs or PSs to XFs.
  - When loading in Areva HDBExport files, the EMS ID and EMS CBTyp fields are now in their own fields with branches instead of being added as custom strings.
  - When reading the hdbexport CSV file, fixed SVS parsing code so that AVR status is used properly.
  - When reading hdbexport CSV files, modified the prompt regarding unrecognized CBTyp entries. Dialog will appear but check-box on dialog will be available to specify if user choices should be saved to registry for use when loading future CSV files. This will be checked by default. In addition, an extra confirmation prompt appears if the user choices will result in a case with no Breakers.
  - Adding options to read limit options from hdbexport files. The fields below on the ITEM record indicate whether or not to treat the line limits as AMPS instead of MVA. The transformer option doesn't make much sense so a message will be printed to the log if it is ever true. LNAMP=T,XFAMP=F,ZBRAMP=T,EQLNAMP=F.
  - Modified to include option about whether to create 3-winding transformers when reading the hdbexport file.
  - Added AUX file support for setting the Delimiter used for creating labels when reading the hdbexport CSV file.
  - Added the ability to choose the default label delimiter when reading in HDB export CSV files.
  - Areva Contingency Format
  - Can now read the contingency CSV file that is exported by an Areva EMS
  - KML Format
  - Added ability when loading the KML file for ERCOT to have it create parallel transmission lines between the same 2 buses if there are duplicate entries in the KML file.
  - UCTE Format
  - For UCTE format, added reading the regulated voltage for tap-changing transformers and regulated MW flow for phase shifting transformer. For tap-changers regulated voltage is read as the value specified +/- 0.01 per unit. For phase-shifting transformers regulated MW flow is read as the value specified +/- 5 MW.
  - When reading a UCTE file, added ability to read the phase angle shift values from the \#\#R records. Previously they were being ignored and all phase shifts were being set to zero. One important note when comparing angles you see in Simulator. Simulator always assumes the variable phase is on the FROM bus side of the transformer while the UCTE file assumes it is always on the TO side, so the angles read in Simulator will have the opposite sign convention.
  - When reading a UCTE file, modified how the tap ratios were begin calculated from the \#\#R records in a UCTE file. Previously for tap ratios, if the \#\#T record "Rated Voltage 1" and "Rated Voltage 2" did not match the terminal bus nominal voltages, then the tap ratios being read were not handle quite correct. The Simulator "Tap Ratio" column shows the tap ratio converted to the system base, while the UCTE file tap ratios described in the \#\#R records are the transformer base voltages. These were not being properly scaled when reading the \#\#R record. Also keep this mind if you compare the tap ratios you calculated in the UCTE file to those shown in Simulator. When doing this comparison you need to keep two things in mind:
  - 1\. Simulator always assumes the variable tap is on the FROM bus side of the transformer. The UCTE file assume it is always on the TO bus side, so that tap ratios will be the reciprocal of one another.
  - 2\. Ratios will only match if you compare the "Transformer BaseTap Ratio" value in Simulator which shows the tap ratio of the transformer on the transformer base instead of the system base.
  - PROMOD Format
  - Modified reading the "Promod" format for defining interfaces so that we look for the keyword "BASECASE" and treat it the same as "BASE" was treated before.
  - WECC Switch Data Format
  - Parse fault impedance with FB record
  - Use OPEN BOTH action when parsing FL record that opens both ends of the line at the same time
  - Use solid fault if impedance values are all 0.0
  - General 
  - Added support for a new logic operator XOR with Filter and ModelFilter objects. This will return true if an odd number of the inputs is true.
  - Added support for a new logic operator with Filter and ModelFilter objects called "OneTRUE". This feature will return true if exactly one of the inputs is true.
  - Generators and Branches now support up to 8 owners
  - Switched Shunts and Line Shunts now support up to 4 owners
  - All of the components of multi-terminal DC lines now support up to 8 owners
  - Two-terminal DC lines now support up to 8 owners
  - VSC DC Lines now support up to 8 owners
  - Data Maintainer object that represents the entity responsible for maintaining the input data for an object
  - Balancing Authority object to which buses, generators, and loads can be added. It functions as a container object similar to a zone.
  - Supplemental Data and Supplemental Classification objects can be used for user-defined containers for objects
  - 15 limits are now available with each branch and interface
  - Rating sets can be given name which is useful for identifying different rating sets for different purposes. These can be specified on a branch, interface, or bus basis and the names will then appear in column headers.
  - Distributed generation can be defined with loads. This is used with steady-state and transient stability analysis.
  - Modified so that when loading a Branch from an auxiliary file or via copy/paste to/from Excel that either the R/X on the system base OR the R/X on the transformer base can be used as required fields when creating a new transformer
  - Line B field is no longer a required field to create a Branch
  - Vhigh and Vlow are no longer required fields to create a Switched Shunt
  - R can be defined in addition to X as part of generator line drop compensation impedance.
  - Evaluating Model Expressions that are interlinked could become very slow. This will make it impossible to view the expressions or do any calculations with them like contingency analysis, ATC, PV, and QV. This evaluation process has been sped up.
  - Three-winding transformers can now be used as part of Model Conditions and Model Expressions.
  - ViolationCTG and LimitViol object types can now be filtered using secondary object filters.
  - Store Auto XF and Auto Shunt for areas to the system state. This will make it possible to set these in the Post Contingency Auxiliary File.
  - The number of limits that can be defined with branches has been increased to 15. If using the Scale tool to scale an Injection Group and using Merit Order Dispatch, loads will now be included in the dispatch. Previously, any loads in the injection group were ignored. Loads will move towards either their minimum or maximum MW limit as appropriate. If both the minimum and maximum limits are 0, loads will only be allowed to decrease to 0 MW. Mvar load will be adjusted by keeping a constant power factor. \*\*\* You may need to modify your injection groups if you have been using Merit Order with injection groups containing both loads and generators and you want to maintain the same functionality. \*\*\*
  - Added button to open Monitors dialog so that they can a now be defined in Simulator. Monitors are used with the Trainer tool and allow for the triggering of alarms when specified events occur.
  - Speed increase in expression parsing.
  - Added Left(), Right() and Mid() functions to expression parser for string expressions.
  - Added options with individual Participation Points for Injection Groups to specify the ParFac based on a field of the participant or a Model Expression.
  - When renumbering Multi-section Line dummy buses, either through the special text file or through a SUBDATA section, the default will now be to keep the original bus name instead of renaming to the new bus number if no bus number is specified.
  - Geographic Data View
  - Sparklines which are small character-sized graphics can be displayed when specifying transient stability data
  - Contouring is allowed on geographic data view objects based on the object type that they represent
  - Up to three lines of information can be displayed within a geographic data view object including identifying information such as name and/or number, selected field value, or a sparkline
  - More options for managing the geographic data view objects on a oneline
  - Added options to make it easier to create a new oneline for adding geographic data view objects including the option to insert geographic borders
  - [GIC Analysis](47-geomagnetically-induced-currents.md#gic-analysis)
  - Hot spot analysis
  - Now have the ability to automatically incorporate scaling factors for geomagnetic latitude and earth resistivity according to the NERC Benchmark Geomagnetic Disturbance Event Description (Draft: April 21, 2014).
  - Integrated Topology Processing
  - Modified consolidation of superbuses to iteratively remove superbuses that contain ONLY switching devices that are connected to other superbus only by open switching devices. These are of no significance so merging into a superbus removes the clutter.
  - Modified consolidation so that if a switching device that is directly in parallel (between exact same buses) with a non-switching device then the switching device is internally flagged to prevent consolidation due to this switch. This is done to prevent series capacitors from being removed from the model when they are bypassed by their bypass circuit breaker. Note that the series cap can still be completely consolidated if the more complex network typically involving a disconnect causes their terminals to be at the same super bus, but prevent the obvious parallel switch is helpful.
  - When saving a Consolidated Case or when viewing the Consolidated Superbus in the Bus View, generally open switching devices are maintained in the model to show where they are. We have modified it so that if a CLOSED switching device is parallel with a open switching device we do not display the open switching device. CLOSED switching devices in this situation are unusual as they must be specified as Consolidate=NO or part of an interface or tie-line, so this is a special situation.
  - Modified so that we consolidate a dead bus to its neighbors if all three of the following conditions are met:
  - 1\. It has no gens, loads, or shunts
  - 2\. It is connected to the rest of the system only by open AC branches
  - 3\. It is only connected to ONE other SuperBus through these AC branches
  - The objective here is to consolidate a disconnect and dead auxiliary bus.
  - Model Explorer
  - Show the "Branches By Type" folder in the Model Explorer regardless of whether the Integrated Topology Processing add-on has been purchased.
  - Oneline Diagrams
  - Added options to right-click on objects in case information displays or onelines to "Open or Close with Breakers and All Disconnects".
  - Sparklines which are small character-sized graphics can be displayed when specifying transient stability data in display object fields
  - Option to select objects on a oneline diagram and open case information displays of the selected objects
  - Contouring color key can be pulled outside of a oneline window. It will still retain its relative position to the oneline when the oneline is moved.
  - Added ability to re-load active display in the Oneline Viewer by double-clicking on its tree node.
  - Added the ability to search for text inside Background Text.
  - Added the ability to convert multi-section line display objects to background lines.
  - Added a new map projection that uses an Albers Conic Projection useful for Alaska.
  - Added drawing of automatic control symbol when drawing transformer symbol using circles.
  - A line will be drawn through a switched shunt display object if it is on continuous control or an SVC.
  - While in Run Mode, left clicking on a bus name or number field will open the Bus View for that bus.
  - Power Flow Solution
  - Check Back Off Immediately option for generator Mvar limits. Choosing this option will mean that during the inner power flow loop a check will be done if generators can back off Mvar limits (i.e. PQ goes back to PV bus) but a check will not be done for generators hitting limits (i.e. PV goes to PQ bus).
  - Mvar adjustment of individual generators at buses with multiple generators will now obey the regulation percentage instead of adjusting to the same point in their min/max range.
  - Now allow the user to specified a ZBR Threshold. Previously the ZBR Threshold was 0.0002 per unit, but can now be changed by the user. The ZBR threshold is used to build groups of buses connected by low impedance branches. Any generator that regulates a bus within these groups will coordinate with other generators when performing voltage control. In addition multiple switched shunts that control buses in the same group automatically coordinate their control. Finally, these groupings are used to find parallel transformers whose tap ratios are then balanced.
  - New object Voltage Control Group to control switched shunts. Used to model Centralized Grid Capacitor Control algorithm.
  - Made a correction to SVSMO2 SVC model to use a look-up table with all of the possible combinations of B MVARS to determine the B output to the closest step.
  - Improved DC line tap calculations to avoid controller oscillations in the power flow solution.
  - When reading in an EPC or RAW file which contained multiple slack bus designation for one electrical island, Simulator picks on of these as the slack and removes the other. An appropriate message is then written to the message log alerting the user of this. This message was then being repeated every time a power flow solution was done. The ongoing annoying messages were removed and only the first message will be shown now.
  - Added option with a VSC DC Line to specify whether the DC MW Setpoint is interpreted as the MW flow on the "AC side" or "DC Side" of the converter. If there are not any converter losses modeled then this does not matter. Modified reading VSC DC Lines from a RAW file so that the DC MW Setpoint is interpreted as the "AC side" MW. When writing out to the RAW format, if the option in Simulator is set to "DC Side", then the appropriate AC flow will be calculated and written out to the RAW file instead.
  - Changed the way the 2-terminal DC line firing angle and tap control are handled when GammaMin = GammaMax. Under other situations once the maximum tap value is reached and the DC voltage is still above the desired setpoint, then Simulator will calculate a firing angle that exceeds GammaMax. This has been changed now so that if GammaMin=GammaMax, then the firing angle will remain constant and instead the DC voltage setpoint enforcement is abandoned and the DC voltage will be higher than the setpoint. When this occurs a prominently highlighted message will be written to the log. This change in control feature was added primarily to match the treatment in several ERAG/MMWG, PJM, and MISO cases we have seen recently which have some erroneous input data.
  - [PV and QV Curve](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)
  - Options to Show Gridlines on both the Horizontal Axis and Vertical Axis of a PV plot
  - Added option to track high voltage limits during PV analysis.
  - With the QV Curve Tool added an option to allow specification of QV Make-Up Power. Previously, any MW changes during the QV curve tracing were made up at the system slack bus. Now can choose to use the system slack bus or the same option that is set as the Contingency Analysis Make-Up Power option. The default is to use the same setting as used with the Contingency Analysis Make-Up Power.
  - Added a new button with PV plots to save plot images to file.
  - Added option with PV plotting to specify how the objects on the plots are identified, i.e. number, name\_kv, or label.
  - Added new option with PV plots to only save a specified number of critical scenario plots to file. This is done on a plot-by-plot basis. When plotting critical scenarios, the options with contingencies that determine if scenarios should be plotted are ignored.
  - Added options to allow saving PV plots to file at the end of a PV run.
  - When using Injection Group Ramping option for Merit Order Dispatch, loads will now be included in the dispatch. Previously, any loads in the injection group were ignored. Loads will move towards either their minimum or maximum MW limit as appropriate. If both the minimum and maximum limits are 0, loads will only be allowed to decrease to 0 MW. Mvar load will be adjusted by keeping a constant power factor. \*\*\* You may need to modify your injection groups if you have been using Merit Order with injection groups containing both loads and generators and you want to maintain the same functionality. \*\*\*
  - Sensitivity Calculations
  - Interfaces can now be monitored with the LODF Matrix tool.
  - Added the ability to store the display/column option settings for the grids on the Flows and Voltages Sensitivities dialog under the "Self Sensitivity" and the "Multiple Meters, Single Control Change" tabs. Previously these could be modified but after closing the dialog and reopening it, Simulator would not maintain display/column options on those.
  - For TLR calculations, determine the island in which the calculations occur based on the island of the TLR element. If the element's terminals are in different islands, no calculation is done. When doing the calculations, only the buses in the transactor object that are in the same island as the TLR element will be used. Previously, we would not do the calculation and notify the user that the transactor spanned multiple islands. When doing the weighted calculations for areas and injection groups, we also only include the buses that are in the same island as the TLR element.
  - Added option when doing TLR calculations for injection groups that will allow offline devices to be included in the calculation.
  - Provide access to the Loss Increase % value found on the PTDF dialog through the PWCaseInformation objecttype and LinePTDFLosses variablename.
  - Added sensitivity calculations for dAmp/dControl and dMVA/dControl for the Multiple Meters, Single Control Change calculations.
  - Added new option to calculate sensitivities due to a change in generator MW injection for the Multiple Meters, Single Control Change and Multiple Meters, Multiple Control Change calculations.
  - Added calculations for ETLR and WTLR on injection groups.
  - Added access to the dV/dControl values for each terminal of a branch for use with the multiple sensitivities to a control change calculations.
  - When opening the PTDF dialog, the type is automatically set to Multiple if any directions are defined. When calculating PTDF values added a new MWAtZero:1 field for an interface which is similar to MWAtZero, but it assumes each transfer direction containing an injection group is configured to represent an area and as a result the "net injection" of each injection group in the MWAtZero:1 calculation is assumed to be equal to the export of the most common area in the injection group.
  - Added LODF Screening tool to screen single line contingencies by LODF magnitude or loading. Pairs of contingencies can be created from contingencies that are deemed to be significant based on screening thresholds. Purpose is to create a more manageable list of contingencies rather than run all pairs of single contingencies.
  - [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation)
  - When changing the injection of an Injection Group and using Merit Order Dispatch, loads will now be included in the dispatch. Previously, any loads in the injection group were ignored. Loads will move towards either their minimum or maximum MW limit as appropriate. If both the minimum and maximum limits are 0, loads will only be allowed to decrease to 0 MW. Mvar load will be adjusted by keeping a constant power factor.
  - [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)
  - Transient Stability Options
  - When choosing a generator as the Angle Reference in the Result Options which is presently out-of-service and choosing to use an angle reference which uses that generator, Simulator will now create a validation warning alerting you of this problem. The simulation will still run, but the angle reference will be the synchronous reference frame (no shift) instead of your choice.
  - Transient Stability Solution
  - Added hard-coded minimum values of the following for use in a transient stability simulation:
  - 0.3 for Minimum Per Unit Voltage for Constant Power Loads
  - 0.2 for Minimum Per Unit Voltage for Constant Current Loads
  - If input values are below these thresholds, Simulator will include a validation warning indicating that we will assume values equal to these threshold.
  - When using the option to only include generic limit monitors for synchronous generators without relay models, relay models will not be considered unless they are active. GP2 relays will always be ignored in this check.
  - Modified the treatment of the LD1PAC model in the algebraic network boundary equations when LD1PAC is not stalled. It was possible for the LD1PAC model to cause a voltage collapse when operating in the "running state 2" portion of the curve. We have modified the algebraic equations to relax this equation to make it less likely for this to occur.
  - Modified the network boundary equation treatment of the svsmo3 switched shunt model for modeling SVCs. All other switched shunt models (including svsmo1 and svsmo2) are modeled as an impedance in the network equations. The svsmo3 however is now handled internally in PowerWorld Simulator as a constant current injection instead. This matches the treatment used for various generator machine models such as wt3g, wt4g, regc\_a, pvd1, etc.
  - Changed the DC line algebraic equation solution in transient stability. Previously when using algebraic models of the DC network (no model, EPCDC, CDC6, etc...) during the network boundary equation solution, after each Newton iteration, the firing angles would be recalculated to attempt to exactly set the desired Current (or Power) of the DC converters. For algebraic solutions near points where firing angle limits were either hit or backed off, this could make the network boundary solution oscillate and fail. Attempting to get the current/power setting exact is unnecessary though. Instead, we now only modify the firing angle at the beginning of each time step in the simulation and then leave the firing angle constant. This is the same process that is done when actually modeling the dynamics of the DC network and using a transient stability model for the DC converters. Essentially the new algebraic solution is assuming that the firing angle is calculated based on the last time step's AC voltage profile and thus essentially the firing angle control has a 1 time-step delay. This is perfectly appropriate and makes the network boundary solution much more robust and the current/power control is still met exactly withing a couple time steps.
  - Transient Models
  - Added Area Automatic Generation Control (AGC) which also added MWRef control to various models
  - Added SVCALS Switched Shunt model
  - Added FRQDCAT/FRQTPAT and VTGDCAT/VTGTPAT transient models and the entire support for allowing multiple instances of the same relay in the gens others models.
  - Started work on including input data for stability models in the Difference Flows
  - Added REPC\_B plant controller model.
  - Added DIRECLEN line relay model
  - Added RELODEN line relay model.
  - Added UEL1 under excitation limiter model
  - Added MSLR1 Line Shunt model.
  - Added MSR1 Switched Shunt model.
  - Added MEXS Exciter model.
  - Added Generator Relay GVPHZIT (Volts per Hertz Relay Inverse Time).
  - Added Generator Relay LHSRT (Overspeed Relay). This relay is largely identical to the LHFRT relay, but monitors generator rotor speed instead of bus frequency.
  - Added Generator Relay GVPHZFT (Volts per hertz Fixed Time Relay).
  - Added ATRRELAY model.
  - Added OOSMHO Line Relay Model.
  - Added generator over frequency relay model called GENOF\_PW. This allows monitoring of frequency at a specified bus or generator. When monitoring a generator only the generator will be opened when over frequency is detected. If monitoring a bus, generators, loads, and shunts connected at that bus will be opened when over frequency is detected. The relay can also be used for monitoring without actually tripping any devices.
  - Added a new REEC\_C model that permits modeling of a battery storage device allowing a negative Ipmin (to represent charging) and providing a charging state which can result in a modification of the limits of the Ip.
  - Added support for the LSDT3 load relay models
  - Added support for the LSDT7 load relay models
  - Added support for GP2 relay model.
  - Added support for PV1G machine model and the PV1E electrical model.
  - Added support for the PVD1 Photo-Voltaic Distributed Generation model.
  - Added cross-current compensation model CCOMP which is an equivalent model to the COMPCC but with slightly different algebraic expressions. CCOMP specifies a Zc and Zt value instead of Z1 and Z2. The can be converted as follows however:
  - When Flag=1 in CCOMP, then
  - Z1 = (-2\*Zc) \* System Base/Machine Base
  - Z2 = (-2\*Zc - Zcomp) \* System Base/Machine Base
  - Where Zcomp = Rcomp+jXcomp specified in the generator data record
  - When Flag=0 in CCOMP, then
  - Z1 = -2\*(Zt - Zc) \* System Base/Machine Base
  - Z2 = (-2\*Zc) \* System Base/Machine Base
  - Added simplified line OC model.
  - Added support for PTIST3 stabilizer
  - Added default parameters for model WEHGOV
  - Added new stability model HYGOVRU which is really the same as HYGOVR
  - Added EPCDC, CDC4T, CDC6T, and CDC6 DC line models.
  - Implemented LDELEC load model.
  - Added WPIDHY governor model.
  - Added SIMPLEOC1 line relay model
  - Transient Model Modifications
  - When using the Scaled Quadratic Saturation Model for an exciter model, if a value of E1=0 we now automatically ignore the saturation function. The saturation function is B\*(E-A)^2/E so if E=0 this function is undefined so this input data does not make sense.
  - Can assign Criteria to a transient model that defines the conditions (advanced filter or advanced filter condition) under which the model will be used. This will allow multiple models of the same class (i.e. two different machine models) to be active at the same time as long as their Criteria are all not true at the same time.
  - Modified REGC\_A to contain Khv and Qlim parameters. These parameters are NOT used by PowerWorld Simulator, but they are part of the DYD file so we read and maintain them for users with DYD files to avoid confusion.
  - Modified the REGC\_A to contain an Xe parameter to represent generator effective reactance in per unit. If this value is zero then we will divide the value Iq by this amount and also model an impedance of (jXe) at the bus in the network boundary equations. This mimics what is done for WT3G type 3 wind turbines.
  - Modified EXAC1 that have derivative feedback and very small time constant (Tf) so that the subinterval integrations would start at 32 subintervals instead of 16. This helps ensure numerical stability of the algorithms.
  - Added option for CSVGN5 to change limit on Bmax/Bmin for initial limit violations.
  - Made a correction to SVSMO2 SVC model to use a look-up table with all of the possible combinations of B MVARS to determine the B output to the closest step.
  - Modified the REEC\_A, REEC\_B, and REEC\_C models so that when pfflag = 1 (constant power factor), then we initialize Qext to 0.0. It really doesn't matter in this particular situation because Qext isn't used if pfflag = 1, but it is less confusing when connected to an REPC\_A model if it defaults to zero in this situation.
  - Made changes to LHFRT way of handling the user input data. They frequency deviation are given in Hz but were previously being interpreted as per unit.
  - Added option with LOCTI Relay to trip the entire three-winding transformer or only the monitored winding.
  - Modified TLIN1 model so that multiple TLIN1 can be assigned to the same end of a branch. The Device ID must then be unique.
  - Added more parameters to WNDTGE governor model.
  - For LD1PAC, when fuvr=0 we were still reporting transient stability events related to the pickup of the under voltage relay even though it would never actually open anything. This has been fixed to no longer report these events if fuvr=0.
  - Changed the CONV\_IntMtnPP and CONV\_Adelanto converter models to use a CosMinAngle equal to 0.95630476 instead of 0.956. It's a very minor change but using 0.956 signifies an minimum firing angle of 17.059 degrees which doesn't match the initial condition of 17.000 often seen in cases.
  - Modified to not model motors which are less than 0.01 MW and added appropriate warning message to indicate this.
  - Modified the WT1G1, WT2G1, WT3G1, WT3G2, and WT4G1 wind turbine models so that they ignore any implicit step-up transformers.
  - Added an additional "Other Field" for induction motors to report the presently used Device MVABase used internally by Simulator. This can change throughout the simulation by load relays or by models such as CMPLDW.
  - Added other field for CMPLDW to show the "Fraction not tripped on under voltage" for the Type 3 motors.
  - Transient Plots
  - New feature for easy creation of a time series of images using the Transient Contour Toolbar
  - Options to Show Gridlines on both the Horizontal Axis and Vertical Axis of a plot
  - Added option with a SubPlot regarding whether to show the legend. "YES" means always show legend. "No" means never show legend. "Default" means show the legend if the number of plot series is below the global threshold specified on the plot tab of the Plot Designer. The default behavior is "Default" which matches the previous hardcoded feature.
  - Added ability on Transient Stability Plot titles and axis titles to use the special string "@CTGMemo" to include the memo of the transient contingency in the plot
  - [Transient Stability File Format Support](36-transient-stability-overview-and-data-part2.md#data-from-external-files)
  - Fixed error when writing out REGC\_A models to the DYD file format. The following values are now always written Khv = 0.7 and qmin = -1.3. These values are not used by PowerWorld Simulator and these represent typical used (nearly universally used) value in DYD files.
  - Modified loading of DYR files to look for particular user-written models commonly used in ERCOT and MMWG cases which represent wind turbine models.
  - USRMDLs W4G2U and SWTGU1 are both converted to WT4G1.
  - USRMDL VTGTPA is converted to VTGTPAT
  - USRMDL VTGDCA is converted to VTGDCAT
  - USRMDL FRQTPA is converted to FRQTPAT
  - USRMDL FRQDCA is converted to FRQDCAT
  - USRMDL which are part of the GEWTG1/GEWTE1/GEWTT/WGUSTC/GEWTA/GEWTP/GEWTPT suite of user-written models are automatically converted to WT3G2/WT3E1/WT3T1/WT3P1. (This suite of models is seen in ERCOT cases.)
  - USRMDL which are part of the GEWTG2/GEWTE2/GEWTT1/GEWTP2/GEWGD1/GEWTA2/GEWPLT2 suite of user-written models are automatically converted to WT3G2/WT3E1/WT3T1/WT3P1. (This suite of models is seen in MMWG cases.)
  - Improved messages written to the log when encountering user-written model in the DYR file.
  - When reading DYR files, added support for reading a USRMDL/GENROA model. This is a user-written model commonly used in NY-ISO in North America which simply copies the input parameters for GENROU from another GENROU model.
  - Added support for reading the REEC\_C model from a DYD file.
  - Added reading of the AMETA record from a DYD file to indicate storage of angle information to transient stability results.
  - Added ability to read DYD file containing devices identified by label.
  - Modified reading of the DYD file so that when the IFMON record is encountered we modify all our options regarding storing results to include the MW and Mvar flows on interfaces.
  - Added a check at the end of reading a DYD file to determine if there are loads which do not have any static/algebraic stability models assigned to them. If this is the case, then a dialog would previously appear asking the user to choose a default load model. This dialog caused more confusion than clarity, thus it has been modified so that instead messages are written to the log notifying the user that all loads that do not have static load models will default to a "Constant Current P, Impedance Q". Also checking is done to see if there are ALWSCC models assigned to some areas but not others, and if this is the case then log messages are written to notify the user that some areas do not have ALWSCC models and list those areas.
  - Added color to log text when loading in DYD files. "Missing" notes are written in gray. "Error" in red.
  - Modified reading of a GNET.idv file to allow multiple gnet sections in the same file to be read.
  - Added support for reading/writing the EPCDC, CDC4T, CDC6T, and CDC6 DC line models from DYD and DYR files.
  - Transient Stability Contingency Definitions
  - Cleaned up Fault Type specification and added diagrams to make it clear to the user how faults should be specified
  - Added new feature with a transient stability fault to "Apply Fault to achieve a desired voltage"
  - Added ability to clone transient contingencies
  - The Start Time and End Time for a transient contingency analysis can be negative
  - Made a slight modification so the SET Power command for transient contingencies will interpret an actual MW value and convert it to a delta MW value if necessary instead of treating everything like a delta MW value.
  - Added an option to auto-insert transient contingencies and name them by label.
  - Transient Stability User Dialogs and Auxiliary File Support
  - Modified to store and show generator Speed values in per unit instead of in Hz
  - In case information tables listing particular classes of transient models (i.e. Machine Models, Governors, etc.) an option has been added to Only Show Used Models
  - Islanded Load and Islanded Gen fields are now available with transient contingency results
  - Expanded on the "Solved" field for a transient contingency. Previously this field said "YES" if the transient contingency had been attempted at all regardless of whether it was successfully finished. There are now 3 fields:
  - 1\. Processed: This will say YES if the transient contingency solution was attempted
  - 2\. Solved: This will say YES only if the transient contingency solution was run and successfully finished
  - 3\. Reason Not Solved: When Solved = NO, this will be a string indicating why the solution was not finished
  - When saving transient stability settings to an auxiliary file, the dialog that allows you to select what to save has been modified. There is now an option that allows you to Save Transient Limit Monitors.
  - Added ability to open the Bus View from the Transient Limit Monitor Violation case information display.
  - Added ability to open the Bus View from case information displays of transient stability models.
  - Modified to bring the transient stability dialog back up in multiple contingency mode if it was in that mode the last time the user open the dialog.
  - On the Transient Stability Dialog, we were finding that the button on the Result Storage page called "Load from Hard Drive File into RAM results specified by Store to RAM Options" was causing confusion. Users were assuming that in order to plot results or use the Transient Contour Toolbar that results must first be loaded into RAM. This has never been the case as these features simply obtain data directly from the TSR file without requiring you to load results into RAM. The same button is available at the bottom of the "Results from RAMTime Values" and in practice the only place that you see these results from RAM is on this page. To avoid continued user confusion, we have removed the button from the Result Storage tab and it is now only available on the Time Values page.
  - When loading in transient stability data from an AUX, DYD, or DYR file, Simulator would prompt you asking "Do you want to clear the existing transient stability data first?". Feedback from many users was they would NEVER want to do this and it was a dangerous dialog to continually show users. We have removed this prompt and the clearing of stability data when loading a file.
  - In the Transient Stability dialog, modified the drop-down showing all of the transient contingencies so that the strings also show the categories of the contingency (if any categories have been assigned).
  - In the Transient Stability dialog, added a Find button next to the drop-down showing all the transient contingencies. The Find button allows you to find by either
  - 1\. Name of the Transient Contingency
  - 2\. Find the first transient contingency that has a transient contingency element that acts on a generator, load, bus, or switched shunt.
  - Added additional features to the "Insert Apply and Clear Fault" button on the transient stability dialog. Previously when doing this we did the following: Branch fault: create 3 events: Fault, OpenFrom, and OpenTo Bus Fault: create 2 events: Fault, ClearFault We have now modified it so that the user may choose whether to "Clear Fault" or "Open" for the extra events. Note: The auto-insert transient contingency tool will always do OPEN for all extra events.
  - Transient Stability Storage
  - Option to not monitor Min/Max results during simulation
  - Option to not store Events during simulation
  - Option to not store Solution Details during simulation
  - Transient Stability Results
  - When creating plots, option to only show results in RAM and ignore results stored in hard drive
  - Option to save Min/Max results stored in RAM in PWB file instead of just always saving them
  - Results for Line Shunts are now included
  - Results for Substations are now included
  - Results for Case Information (case-wide quantities) are now included
  - Fixed reporting of a limit violation on GPWSCC model when Ki = 0. It was reporting a limit violation even though the state was ignored.
  - When checking a limit against a min/max limit pair, sometimes Simulator would report a state violation even when the value was exactly at the limit. It will now only report limit violations to the user if they exceed the limit by more than 0.01% of the limit. Thus if the max limit is 1.0000 then it will only report a limit violation if it's 1.0001 or higher. Note, this ONLY effects the reporting of limit to the user. The value is still pegged at the limit, but we just don't report state limit violations that are likely due to numerical precision.
  - Modification were made when transferring results from transient stability for viewing inside Simulator.
  - 1\. The situation where one end of a transmission line is open is now handled by putting in a fictitious bus shunt so that mismatches which are viewed are meaningful.
  - 2\. We now show islands that exist in stability which would not be permitted to exist in the power flow, such as an island without any load or an island with only 1 bus.
  - Added an event in the Events table to indicate that the network solution failed during the simulation.
  - Min/Max, Events, and Summary information are now saved to a PWB file if not storing the Time Values to PWB.
  - Added Level designation to Transient Events. Options have been added to easily display Events by specific Levels: Error, Info, Skipped, User, Transition, Model Trip, and Relay Trip. Result Event Reporting options have been added to specify if events are reported to the Message Log in addition to the Event table. These new options are especially useful when using the CMPLDW composite load model which has many possible events associated with it.
  - Transient Data Validation
  - Many renewable energy machine models feed a commanded Ip and Iq through a small time delay with the output then feeding into the network boundary equations as the real and reactive current injections. We have added parameter checking to ensure that these time delays are no larger than 0.20 seconds. If the time delay is larger than 0.2 seconds then it will be treated as 0.2 seconds. In the 1000s of models like these we have seen, these time delay values are on the order of 0.02 seconds, but we were seeing a case with a value of 1.0 second which creates an unstable model. This affects the following models presently: WT3G, WT3G1, WT3G2, WT4G, WT4G1, REGC\_A, PVD1.
  - Modified the Validation message about treating generators with no machine model as negative load to make it clear that we treat the generator as constant current in this situation.
  - For a GENTPF/GENTPJ model when setting Tdopp or Tqopp to 0.0, this indicates that a transient model should be used for the generation model. The model should then be configured such that Xdpp=Xdp and Xqpp=Xqp=Xq to function appropriately. If the model was not setup this way from the start, then Simulator will change the parameter inside the simulation automatically to be treated in this manner. There was a bug however such that this wasn't properly handled which could cause generation to initialize incorrectly. This was occurring at the LITFAL generation in a WECC case. Simulator will now properly handle this without user-intervention.
  - For GENTPF/GENTPJ models which had Tqop=0 to indicate special handling of a salient pole machine with a single amortisseur winding, we were not performing any validation checks on the magnitude of Xqpp relative to Xdpp. As a result, invalid data such as Xqpp=0 was not being flagged as an error and was not being auto-corrected. We now perform the same check on Xqpp as we do for all other GENTPF/GENTPJ model and thus if the value is very small (Xqpp\<0.01\*Xdpp, basically zero) then we set Xqpp=Xdpp.
  - Modified the validation check on synchronous machines to ensure that Xqpp is not too big. Previously we enforced (Xqpp \<= 1.1Xdpp), but have changed this to (Xqpp \<= 1.5\*Xdpp).
  - Added error checking for WT3G2, WT3G, WT4G, WT4G1 and REGC\_A so that if LVPL=0 then it ignores the low voltage power logic
  - Added error checking for using a distribution equivalent which could not support the load specified. This was caused because the distribution equivalent impedances are given on an MVABase that is proportional to the MW of the load. In a situation which had a load of 2.0 MW and 120 Mvar, the load would exceed the maximum power transfer of the distribution system because the Mvar values was so huge relative to the MW. An appropriate error message will now be shown.
  - Added error checking for WT3E and WT3E1 model to disallow Kpp=0 AND Kip=0. That doesn't make any sense and is showing up in the MMWG cases at a generator.
  - Modified the validation check for GEWTG machine so that if the electrical model is EWTGFC or EXWTGE, but the fcflag does not match the expected value (0 for EXWTGE and 1 for EWTGFC), then the auto-correction routine will change the fcflag to match the expected value. The assumption is that the user specification of an electrical model is more reliable than setting of fcflag to 0 or 1.
  - Modified the synchronous generator (GENROU, GENSAL, GENTPF, GENTPJ, etc.) validation so that we allow Xl=Xdpp or Xl=Xqpp. We also added a check to enforce that Xl \< Xdp and Xl \< Xqp.
  - Changed validation for REEC\_A, REEC\_B, and REEC\_C so that when Pfflag = 1 we no longer report as an error if Qflag = 1. This is now simply reported as a warning indicating that this is a possible configuration, though not a typical one.
  - User Interface Dialogs
  - When using the Save Case As option from the file menu, the directory will default to the location where the present case was opened.
  - Modified the Recent Cases list so that the file extension is included. Also now include the file path in situations that duplicate entries are shown in the Recent Cases List (This can occur with the same file name, but different file path).
  - Added menu options for Append Case to directly access the different file types from the dropdown menu.
  - Added a Populate button on the LODF Screening dialog to populate Branch custom fields from the summary results after the analysis is complete. This is useful if you forget to set the options ahead of time or want to change the key fields used to identify branches in the summary.
  - When using the Test button on the custom expression (or string expression) dialog, added additional error message when no object has been selected for one of the variables.
  - Modified the Set Selected Field Inside a Network Cut dialog so that the check box "Require paths to be energized" is checked by default.
  - On the Injection Group Auto Insert dialog added option to specify participation factor by Field or Model Expression. Also, added option to include Bus participation points.
  - In Set Selected from Network Cut tool, added option to prompt user asking if they would like to initialize the Selected field.
  - Added Line length information on Branch Information dialog while in Run mode.

---

<a id="whats-new-2"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New_v22.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New_v22.htm)*

Simulator Version 22 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

To see a list of what was new in previous Simulator Versions choose links for [Simulator 21](#whats-new-3), [Simulator 20](#whats-new), and [Simulator 19](#whats-new-1).

  - Installation and Simulator Executable

      - Only the 64-bit version is installed.

  - [Automation Server](33-simauto-overview-and-setup.md#automation-server)

      - Added RunScriptCommand2, which is a more usable version of RunScriptCommand. It returns a Boolean for success or failure and a status string that contains information about what just happened (such as an error message, warning, etc.).

      - Added a property called ProgramInformation, which provides version, addon and the currently running SimAuto executable in an array of arrays. The first dimension selects the record desired, and the second dimension chooses fields from the record. Each record starts with an identifier (such as "version", "addons", or "executable") in the first field, followed by all the fields containing data for that kind of information.

  - [Auxiliary Files, Display Auxiliary Files and Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux)

      - For syntax and usage details, please refer to the latest Auxiliary File Format PDF, available at:

        [https://www.powerworld.com/knowledge-base/auxiliary-file-format-10](https://www.powerworld.com/WebHelp/knowledge-base/auxiliary-file-format-10)

      - When reading an AUX file, modified to support the ConditionType field of "\!=" to mean "not equal" in a Condition or ModelConditionCondition object. PowerWorld will still always write out "\<\>" for this ConditionType but we now support reading "\!=".

      - Added an optional parameter at the end of the special PROMPT section when specifying a filename in a SCRIPT command. That value can either be Continue or Abort. If not specified, it this will be Abort (present behavior). If Continue is used, then we will simply skip the script command and continue reading the AUX file. If that is omitted or anything else is in that location, we will Abort the entire read of the AUX file as is done now. Example syntax is as follows: LoadAux("\<PROMPT 'Choose an AUX file' 'Auxiliary Files (\*.aux)|\*.aux|All Files (\*.\*)|\*.\*' 'c:\\temp' 'Continue'\>", YES);

      - Added support for reading future [concise variable names](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names) that will be used in Version 22 for the following objects. These only impacts reading AUX files as Version 21 will continue to write the legacy variable names.

        CTGResultStorage, QVCurve, PVInterfaceResult, PWQVResultListContainer, PWPVResultListContainer, CTG\_AutoInsert\_Options, Equiv\_Options, Fault\_Options, IG\_AutoInsert\_Options, Limit\_Monitoring\_Options, LODF\_Options, MessLog\_Options, PTDF\_Options, Scale\_Options, Sim\_Environment\_Options, Sim\_Simulation\_Options, TLR\_Options. Also, all the difference case tool objects representing Removed\*\*\* objects.

      - The following special keywords were added for use with Script Commands. Typical uses could be to assign meaningful names while saving out CSV or AUX files, for example.

          - @CASEFILENAME

          - @CASEFILEPATH

      - The following Script Commands were added:

          - ATCDeleteAllResults;

          - ATCDeleteScenarioChangeIndexRange(ScenarioChangeType, \[IndexRange\]);

          - ATCDetermineMultipleDirections(DoDistributed, DoMultipleScenarios);

          - ATCDetermineMultipleDirectionsATCFor(RL, G, I);

          - ATCWriteAllOptions("filename", AppendFile, KeyField);

          - CTGProcessRemedialActionsAndDependencies(DoDelete, filter);

          - EstimateVoltages(filter);

          - InsertConnectedBuses("BusIdentifier");

          - InterfaceFlatten("InterfaceName");

          - LoadPTISEQData (filename, version);

          - LogShow(DoShow);

          - FaultMultiple(UseDummyBus);

          - TSClearResultsFromRAM(ALL/SELECTED/”ContingencyName”, ClearSummary, ClearEvents, ClearStatistics, ClearTimeValues, ClearSolutionDetails);

          - TSSaveDynamicModels("FileName", FileType, ObjectType, Filter, Append);

          - TSSetSelectedForTransientReferences(SetWhat, SetHow, \[ObjectType List\], \[ModelType List\]);

          - WriteLimitMonitoringSettings("filename");

      - The following Script Commands were enhanced with additional input arguments:

          - ATCDetermine(…, DoMultipleScenarios);

          - ATCWriteToExcel(…, \[fieldlist\]);

          - ATCWriteToText(…, \[fieldlist\]);

          - CalculateLODFScreening(…, CustomFieldOrigCTGName);

          - DiffCaseWriteCompleteModel (…, IncludeClearPowerFlowSolutionAidValues, DeleteBranchesThatFlipBusOrder);

          - OpenCase(…, PTI, \[…, HowToKeepDuplicates\]);

          - SaveData(…, Append);

          - SaveDataWithExtra(…, Append);

          - TapTransmissionLine(…, UpdateOnelines);

          - TSGetResults(…, SINGLE/SEPARATE/JSIS/INTEGRATED, …);

      - The following Script Commands were renamed:

        (For backward compatibility, the older names will continue to be recognized)

          - CalculateShiftFactors (previously CalculateTLR)

          - CalculateShiftFactorsMultipleElement (previously CalculateTLRMultipleElement)

          - DiffCaseSetAsBase (previously DiffFlowSetAsBase)

          - DiffCaseClearBase (previously DiffFlowClearBase)

          - DiffCaseMode (previously DiffFlowMode)

          - DiffCaseShowPresentAndBase (previously DiffFlowShowPresentAndBase)

          - DiffCaseKeyType (previously DiffFlowKeyType)

          - DiffCaseRefresh (previously DiffFlowRefresh)

          - DiffCaseWriteRemovedEPC (previously DiffFlowWriteRemovedEPC)

          - DiffCaseWriteNewEPC (previously DiffFlowWriteNewEPC)

          - DiffCaseWriteBothEPC (previously DiffFlowWriteBothEPC)

          - DiffCaseWriteCompleteModel (previously DiffFlowWriteCompleteModel)

          - FaultClear (previously ClearFault)

          - FaultMultiple (previously MultipleFault)

      - The following Display-related Script Commands were enhanced with additional input arguments:

          - AutoInsertBuses(…, InsertSelected);

          - AutoInsertSubStations(…, InsertSelected);

  - [Available Transfer Capability](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)

      - Multiple directions can now be specified with the ATC tool so that they can be run in sequence rather than having to launch tool separately for each direction to be studied. Distributed ATC computing available for calculating ATC on a list of directions.

      - ATC calculations can now be distributed by multiple directions, multiple scenarios, or multiple directions and multiple scenarios combined.

      - Added concise variable names for ATC related objects: TransferLimiter, ATCScenario, ATCExtraMonitor, ATCFlowValue, ATCGeneratorChange, ATCLineChange, ATCLineChangeB, ATCInterfaceChange, ATCZoneChange. Also added these to Version 21 so they can READ files written with new names in Version 22. However, Version 21 will NEVER write these new variable names.

      - Added option "Use Concise" on the GUI dialog that allows the saving of ATC options and results. This will save using the concise format for object fields and headers and does not save using Subdata.

      - More complete validation of transfer directions is done before running various ATC functionality.

      - Solution options and results for ATC are now stored with the PWB file. An option exists to enable or disable storing results.

  - [Bus View](08-view-case-data-tools.md#bus-view-display) and [Substation View](08-view-case-data-tools.md#substation-view-display) Onelines

      - Name of the currently chosen "Custom View" is now stored in the system registry for Bus View settings. This is retained when Simulator is closed and applied when reopened. It is used with any PWB, if the custom view is saved with the PWB.

      - The Bus View option to "Show Only Breaker for Consolidate Branch" will only be checked by default if opening an EMS case. This will no longer be checked by default if simply opening a case that contains breakers.

  - [Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)

      - Added new fields for Branches to show loading percentages based on Limit Monitoring Settings using Contingency Ratings. These new fields are:

          - Used % at From Bus CTG

          - Used % at To Bus CTG

          - Used % CTG

          - Used Limit CTG

          - Violated using CTG Limits

      - Changed the positioning of Quick Fill in cells of a grid. If text is right-aligned, then both the drop-down button and quick-fill handle are to the left, and vice versa.

      - Added new Row Metrics and string-grid Column Metrics. This can be accessed through a right-click on the grids, and then navigating to Set/Toggle/Columns. Added an option to "Use Excluded Values to Limit Range", and buttons to Pan to Maximum and Minimum Row, Column.

      - Added an option to "Save As Auxiliary with Options". This provides more flexibility to save using DATA instead of SUBDATA sections and choosing which contained objects to save. It will also include options to save using Auxiliary Export Format Description. The default option in version 22 will be to save using the DATA section, and the default in version 21 will be to save using the SUBDATA section.

      - Changed searching in the Model Explorer to allow pattern matching when the "Find entire cells only" option is selected. Also changed searching in chooser dialogs so that if a wildcard is used within the search string, searching will still find partial matches.

      - Remedial Actions can now be filtered using advanced filters defined for Remedial Action Elements.

      - Injection groups can now be filtered using advanced filters defined for the PartPoint object type.

      - Added a new field "CountLoadDistGen" for Area, Load, and Substation objects. These values return a count of the number of load record in the respective grouping which has a non-zero DistMW OR a non-zero DistMvar value assigned.

      - Pasting from Excel is now allowed for User Defined Case Information Displays.

  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)

      - Contingency Combination Analysis is now available for studying what is known as N-1-1 contingencies. Previously, this analysis was already possible in Simulator, but required the upfront creation of a list containing all contingencies in a combinatorial fashion, which was memory intensive. The new tool maintains an additional list of "Primary Contingencies", and each N-1-1 contingency is internally managed by combining one primary contingency and one item from the normal Contingencies list. This significantly reduces memory requirements. Improvements have also been made to the user interface for user friendly viewing, filtering, or saving results produced by Contingency Combination Analysis.

      - Contingency Element Dialog now allows multiple elements to be added to the same contingency without closing the dialog.

      - Model Plane object as another tool to use with defining remedial actions along with Model Conditions and Model Filters.

      - Disconnected buses are now be reported as violations when using a linear calculation method or in DC power flow mode when also choosing the option to report these types of violations.

      - Loads are now included as objects for which contingencies can be auto inserted.

      - Added options is three different places that will allow Remedial Actions and any Model Conditions, Model Filters, Model Expressions, and Model Planes being used by Remedial Actions to be deleted. Model Conditions, Model Filters, Model Expressions, and Model Planes that are being used by other objects or not being used by a Remedial Action will not be deleted. These are the three places that options have been added:

      - Added "Delete Remedial Actions and Dependencies" option on the Contingency Analysis dialog under Other \> Manage Contingency Definitions.

      - Added "Delete Remedial Actions and Dependencies" and "Delete Remedial Actions and Dependencies (only selected records)" on the local menu of Remedial Actions case information displays.

      - Added CTGProcessRemedialActionsAndDependencies(DoDelete, Filter) script command. If DoDelete is YES, objects will be deleted. If DoDelete is NO, the Selected field will be set to YES instead of deleting objects for all object types described above. Filter is optional, and if not specified or left blank, all Remedial Actions will be deleted or selected along with dependencies. Filter is applied to RemedialAction object type. AREAZONE is not a valid filter option.

      - When using the contingency tool to Convert to Device Contingencies it is now assumed that new energized islands cannot be created due to the actions of a contingency. Previously, the power flow solution option of "Dynamically add/remove slack buses as topology is changed" would be used, but now this option is always assumed false. This means that generators and loads that could form an energized island will now appear as devices in the resulting contingency element conversion.

      - Added options on the local menu of the contingency case information display under the Save As menu entry for "PTI Contingency File..." and "PTI Contingency File (only selected records)...".

      - The Summary table on the LODF Screening dialog now shows the "Original Contingency Name" field. If processing lines based on Defined Contingencies, this field will show the name of the contingency from which the single line outage originated. Otherwise, this field will be blank.

      - Added branch field called Status Change Order. This field can be used during contingency analysis with conditional actions to check the order in which branches changed status. The order is dependent on the contingency element Status group (CHECK, TOPOLOGYCHECK, POSTCHECK, etc.) in which the action is applied. This value is 0 by default, which indicates that a branch did not change status during a contingency. Branches that change status during the same group will have the same order value. Once a contingency has finished processing this field will be reset to the default of 0 for all branches.

      - Dynamic Relay Models DistRelay and DistRelayITR are now supported in Power Flow Contingency Analysis. Only tripping is supported based on the operating time (pick up time) of zones; reclosing is not supported. Dynamic Load Encroachment Models (that are helper models for relays), like RELODEN, are also supported in Power Flow Contingency Analysis.

  - [Difference Case](08-view-case-data-tools.md#difference-case)

      - When saving the Complete Model from the Preset Topological Differences from Base Case dialog, there is now an option to "Include ClearPowerFlowSolutionAidValues Script Command" that is checked by default. When checked this script command is included in the auxiliary file saved from the case differences. This script command was always included prior to this option being added.

      - Added another default parameter to the DiffCaseWriteCompleteModel script command called IncludeClearPowerFlowSolutionAidValues. By default, this is YES. When set to YES, the ClearPowerFlowSolutionAidValues script command is included in the auxiliary file saved from the case differences.

      - Added an option to "Show Only Changed", which can be applied in Difference Mode or Change Mode. When enabled, this will hide any rows that do not contain any changed values. This is currently only available for user-defined grids.

      - Modified the Section field of a Branch to properly show a Section difference treating the Section as an identifying string. Thus, if a section changed from 3 to 4 then previously it would have displayed a "1" (because it increased by 1). Now it will show "4|3" instead which is more useful.

      - When using an Aux Export Format to save Difference Case changes to file for objects that have at least one field that has changed, all objects were being saved if certain fields were included in the list of fields to save. Now only fields that are enterable and included in the difference case comparison will be considered fields that can change. These fields will still be written to the file but will not be included in the filtering.

      - Added an option to Add/delete branches that flip the from/to bus number using difference case tool. The option is on the dialog where the Key Field can be selected. Also modified the script command DiffCaseWriteCompleteModel to include the option AddDeleteBranchesthatFlipFromToBusNumber as an option to the inputs of the script command.

      - Added ability to allow Aux Export Format to be used when saving a difference case to EPC format.

  - [Distributed Computing](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)

      - Updated the Distributed Computation Configuration tool, which now allows a user or a security group. Command line tool has also been added to aid in scripting the automatic configuration of multiple machines across a network.

  - [Fault Analysis](27-fault-analysis.md#fault-analysis)

      - A new column has also been added to the multiple fault results table to indicate if the location of branch faults occurred at the specified percent location, or at one of the two terminal buses of the branch.

  - File Formats

      - When using "PTI RAW Files Open file with options". This now has an additional option to handle duplicate devices – either to keep duplicate devices by changing them to a unique ID, or to keep only the last read item from a RAW file.

      - Improved support for reading of Transient Stability Contingency Events from PSLF OTG files.

      - Added support to read interfaces specified in this format from PTI MON files:

        "MONITOR flowgate 3 'My Flowgate ' biratings 10000 10000"

      - Improved support for loading status of Transient Stability models from PTI IDV files.

      - When writing out an EPC file, no longer check to see if there is a generator with a closed status at a bus to identify it as type 2 or -2.

      - When writing out buses to an EPC file and specific voltage ratings for a bus have not been specified, write 1.1 as the default for max ratings and 0.9 for min ratings.

      - When loading a PWB the second line now also tells the patch date. As in:

        Opening Case AGL37\_HW5.PWB

        Reading PWB File, Version 22 BETA (build 527, patch date 2020\_12\_18)

  - [Geomagnetically Induced Currents](47-geomagnetically-induced-currents.md#gic-analysis)

      - Simulator can now read a 3D E field input time series represented in the GeoJSON format (file extension \*.json)

      - Simulator can now read and write the supplemental PSLF GMD file that has data sections for: Substations, Branches, Transformers and Shunts. For now, Constant\_Efield, Efield sections are ignored.

      - Added "Spatial Data" Object to Contour Type. This allows contouring of spatial data without explicit one-line objects. This is useful for visualizing GIC Electric Fields.

  - General

      - Added a new "File Browser" which bring up a list of all the PWB, PWD, RAW, EPC, AUX, and TSR in a user defined search path.

      - Added the ability to search the Case Description using the Search Bar that can be added to the dialog.

      - In a [Model Expression](04-model-explorer-and-case-information-part2.md#model-expressions) Dialog, there is now a dropdown menu to choose the key field identifier to use while viewing each expression in its definition – Primary, Secondary, or Label. Option only affects the key field identifier used in this dialog and does not impact the setting used with Case Information Display options.

      - The right-click menu of a Dialog’s caption bar now has options for "Export" and "Copy to Clipboard", which export or copy images of any specific dialog with Simulator.

      - Added "CustomFieldToggleChoice" objects for CustomSingle, CustomFloat, CustomString fields.

      - Added options to track loads in Quantities to Track with the PV and QV tools. MW, SMW, IMW, ZMW, Mvar, SMvar, IMvar, and ZMvar can now all be tracked and plotted.

      - Calculated fields now have an Extra Identification Option. This is available for Min and Max operations and allows displaying any field associated with the chosen object. This is useful for using calculated fields with a combination of filtering to return specific results.

      - Added data maintainer to Area/Zone/Substation section of the Bus, Shunt, Gen, Line, and Load dialogs.

      - Added tool to flatten interfaces. This modifies an interface by bringing all the elements from any included interfaces into the interface that has been selected to be flattened. The tool is available in the right click menu. This was added to work around the limitation of not being able to calculate Shift Factors (TLRs) on nested interfaces.

      - Adding ability to remove an Area Slack Bus designation by deleting the Slack Bus number from the field. If AGC is enabled in the area, designating an empty slack bus will also turn of AGC.

      - Enhanced the log so that objects can be associated with the messages, and then links to the object dialogs are available from the log.

      - Added an option to the Auto Tap Transmission Line dialog and TapTransmissionLine script command to allow the user to choose to replace the original line object with the tapped line objects on all open oneline diagrams.

      - Added a new column for a Branch called "Transformer\\Tap Ratio Change to Balance". When parallel taps are balanced properly, this field is blank. If this entry is not blank, then it shows the tap ratio which will balance parallel transformers. This is the same calculation done when solving a power flow and having the "Tap Balancing" enabled in the power flow solution options. Regardless of that solution option though, this field will show you the troublesome transformers.

  - [Oneline Diagrams](15-using-onelines-tools-and-options.md#oneline-diagram-overview)

      - Added another contouring method called Delaunay Triangulation, which provides faster contour rendering. This is particularly useful when animating wide-area frequency or voltage contours from a Transient Stability run.

      - Added an option to navigate to the object from Contouring Data Points \> Right Click\> Show Dialog in the Contour Options Dialog.

      - The GIS Shapefile Data Dialog can now Button to "Convert X/Y to Latitude and Longitude". This converts projected X/Y values (specified in the shapefile) to degrees latitude and longitude using the WGS 1984 Web Mercator Auxiliary Sphere projection. Conversion is required before projecting to PowerWorld's X/Y coordinates.

      - Add GeodataviewStyle field to allow "area" scaling to proportionally scale the dimensions (like size) rather than their product (area). This is needed for 1D object like arrows.

      - Modified the GDV style so the GDVs object display lines can show any type of field value for the object. Previously they were restricted to just numeric values.

  - [Powerflow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-theory)

      - When checking switched shunts in the voltage control loop of the power flow solution, a tolerance is now included so that shunts will only move if the voltage at the regulated bus is different than the target voltage by this tolerance. This will help prevent switched shunt oscillations especially in situations where generators are regulating the same bus as switched shunts.

      - Added ability to specify as input the RegBus with a VoltageDroopControl object. If the value is specified, then all generators assigned to that VoltageDroopControl will automatically use this regulated bus. If the value is unspecified, Simulator will continue to create a unique Voltage Drop Control equation for each set of generators within the voltage droop control which share a regulated bus (or buses connected by low impedance branches).

  - [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)

      - Added new form to Save GE Transient Stability Data with Options.

      - "Show/Save Selected Plot Data \> Show in Case Information Display" in the Transient Stability Plots tab, is now able to show signals from multiple plots. If duplicate signals are found, then they will be added only once to the grid.

      - Added Generic Branch Limit Monitors to monitor the Apparent Impedance at both ends of branches, by using a simple impedance relay within a reach circle. This can be applied to all AC branches in the case, or to only those branches that meet a filter. This is known as an Out of Step Monitor in other software.

      - Added the ability to plot the Apparent Impedance X vs. R at the same end of an AC line. This will automatically show an impedance circle at 100% of the branch series impedance. If impedance relay models are present, then their specific impedance zones will be shown, instead.

      - Added new fields for TSContingency objects to show totals for "Relay Tripped" and "Model Tripped" Load MW values.

      - In the Transient Contingency Element Dialog, added options for Switched Shunts that allow Set Values To and Change Values By (Mvar or Percent) as Percent of Start Nominal Mvar.

      - All Exciter Models and Excitation Limiter (OEL/UEL/SCL) Models now have compatibility checks.

          - Errors will be shown during Validation before running Transient Stability, along with Auto-Correction that will disable the ill-configured OEL/UEL/SCL instances.

          - The Compatibility information can also be viewed in a table by viewing Exciter fields - "OEL Input Used", "UEL Input Used" and "SCL Input Used", and OEL/UEL/SCL fields - "Output Used".

          - If an OEL/UEL/SCL output signal feeds into a Summation Point of the Active Exciter, the min/max parameters of the OEL/UEL/SCL are validated, along with Auto-Correction to ensure an output signal of zero when operating within the bounds of the OEL/UEL/SCL.

      - For Remedial Action Elements, Switched Shunt actions for Set To and Change By (Mvar or Percent) are now translated for use in Transient Stability Remedial Actions.

      - Added a "Show Valid Remedial Action Fields" button in Transient Stability \> Options \> Remedial Actions, which will display a case information display with all fields that can be evaluated at each time step. Support continues to grow with more fields and objects types. Model Expression allow time derivatives and filter times to be specified for expression variables.

      - Redesigned the Auto-Insert Distance Relay Tool. Now Supports inserting either DISTR1 or DistRelay, and to specify whether to Monitor or Trip.

      - Added a button to "Save Plot Images for Auto-Save Options". For the plots that are marked to AutoSave, this option will now allow plots to be batch-saved at a time after the simulation has been run, if results are available in RAM or Hard Drive.

      - Plots can now also be saved directly to a PDF file – one file per Transient Contingency, plus one additional file if plotting for multiple contingencies.

      - Added a button to "Re-evaluate to Get Limit Monitor Violations" to go through the stored results and get the Transient Limit Monitor Violations. First it will look at the results stored in RAM and then, if no results are found, look in the Hard Drive \*.tsr file. If the button is pressed under Multiple Contingencies mode it will re-evaluate all the contingencies results.

      - A new tool called Result Analyzer has been added. This can calculate statistics, modes and damping information from Transient Stability time-series values. Multiple user-specified time windows can be added. These calculations can be integrated directly into a Transient Stability run so that they are completed after each Transient Contingency, or calculations can be initiated manually as a post-processing step.

      - Frequency Analysis has a new Signal Summary tab. The start and end times can be adjusted to get metrics on just subset of time duration.

      - Changed the "Rotor Angle No Shift" to "Rotor Angle Shift" for the Angle Deviation generic limit monitor.

      - Improved initialization of all Over Excitation Limiter (OEL), Under Excitation Limiter (UEL) and Stator Current Limiter (SCL) models across a variety of possible initial conditions.

      - Distribution Equivalent Models can now be made "Active" or "Not Active", depending on whether to include or exclude from a transient simulation. When they are set to "Not Active", then they are not used, and a particular load model will move up the object hierarchy to find an active Dist Equiv Model. For instance, if LoadModelGroups were assigned to a Dist Equiv as well as assigning a Dist Equiv model to areas. If a load's LoadModelGroup had a Dist Equiv set Not Active, then it would move up to the Area Dist Equiv model instead.

      - Added more descriptive messages to Transient Events for LHVRT, LHFRT, LHSRT models configured to be in Alarm Mode. They will now show the MW of the generator from the initial condition to provide information about how much generation would have tripped if a model were not in alarm mode.

      - Added a new field that can be added as a column to the Transient Stability Events for "MVA Base". This field will show the generator MVA Base, load MVA, Branch Limit MVA Normal, and Switched Shunt maximum Mvar value. Events for other object types will return a blank.

      - Added ability for a TSResultEvent object to show the custom fields for the object to which the result event refers. Under the folder Object Fields\\Custom, there will be 5 custom integer, 5 custom floating points, 5 custom strings, and the memo field. In addition, we have exposed under the folder Custom, the Custom Expressions, Custom Strings Expressions, and Selected field for the TSResultEvent itself.

      - Added a right click option to a list of multiple transient contingencies to "Set into One Contingency at a Time". This switches the dialog back to the process one contingency at a time and choose the contingency that had been right clicked on.

      - Added a new option to specify whether "Non-user events split integration timesteps". This was always done previously. Regardless of this option, non-user events will not force the storage of time value results during the simulation. Again, previously results were stored for the time of any event occurring.

      - Added @CTGEVENTSUSER keyword that can be used in transient stability plot title block to display the transient events that are user defined, i.e., the Transient Contingency Elements. Events with other event levels will not be displayed.

      - The following models were added:

          - Machines: GENQEC, REGC\_C

          - Governors: WTGT\_B

          - Generator Relays: VPERHZ1

          - Load Relays: LDS4

          - Switched Shunts: CHSVCT

          - DC Lines: CDC1T, CHATGY, RSPDC3, CHIGATT, CMDWS2T, CEEL2T, CDCMC

          - DC Line Auxiliary signals: CHAAUT, PAUX1T, PAUX2T, PAUX12T, FCWDPT, CFCAUT, SQBAUT

          - VSC DC Lines: VSCDCT, VHVDC1

          - PAux Controllers: WTGIBFFR\_A, PROBOOST

          - These are a new category of controllers that allow for inertial-based fast frequency response (IBFFR). The PAux signal feeds into augment the effect of a Pref signal.

          - Plant Controllers: PF1, PF2, VAR1, VAR2

          - The output of these controllers is an incremental value that feeds forward into the voltage reference of an excitation system or electrical controls model.

          - Exciters: AC1C, AC2C, AC3C, AC4C, AC5C, AC6C, AC7C, AC8C, AC9C, AC10C, AC11C

  - [PV QV Curves](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)

      - During the QV solution process, the solution options for QV curve power flow are now loaded AFTER the contingency solution, so that they are used when tracing the QV curve after a contingency. Previously they were always loaded at the beginning of the QV curve run BEFORE the contingency solution. Because of that, the Contingency solution options would always overwrite the QV curve options when PowerWorld went to trace the QV curve after a contingency. There is now an option called "SolutionOptionWhen" that can be set to either "Before" or "After". The default option is "After" in version 22 and will remain as "Before" in version 21.

      - Solution options and results for both PV and QV are now stored within the PWB file. Options exist to enable or disable storing results.

---

<a id="whats-new-3"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New_v21.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New_v21.htm)*

Simulator Version 21 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

To see a list of what was new in previous Simulator Versions choose links for [Simulator 20](#whats-new) and [Simulator 19](#whats-new-1).

  - Installation and Simulator Executable
  - 64-bit version of the software is the only version available
  - [Auxiliary Files and Display Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux)
  - Aux File Browser allows quick access to auxiliary files contained in directories specified by the user
  - When loading a complete case in the auxiliary file format, only certain script commands that create or edit data or commands that do not directly affect data, such as log file manipulation, are allowed
  - *Show Container Object Create* option for Message Log. There are several ObjectTypes that are contained inside other ObjectTypes. For instance a ModelFilterCondition is contained by a ModelFilter. For many of these ObjectTypes it is convenient when loading an AUX file, to create the container object if it does not already exist, so Simulator automatically does this. However, it was not clear this was occurring to the user, so red warning messages have been added to the log to alert the user this is occurring when using this option. Examples of this include the following listed by "ContainerType"\\"subtype" Filter\\Condition ModelCondition\\ModelConditionCondition ModelFilter\\ModelFilterCondition Interface\\InterfaceElement Contingency\\ContingencyElement CTGElementBlock\\CTGElementBlockElement RemedialAction\\RemedialActionElement InjectionGroup\\PartPoint TSContingency\\TSContingencyElement TSPlayIn\\TSPlayInSignal TSPlayIn\\TSPlayInInfo
  - An interface element will meet the area/zone filter if its interface meets the area/zone filter. Previously, an interface element would meet the area/zone filter if its individual device met the area/zone filter. This could cause situations that could re-define an interface if interface elements are missing when this information was loaded from an aux file. It makes more sense to keep all of the interface elements as long as at least one of the elements meets the area/zone filter. An interface will meet the area/zone filter if at least one of its elements meets the area/zone filter. This is the way that area/zone filtering has always worked for interfaces.
  - Added ability for Data Maintainer objects to work as a filter on case information displays in a manner similar to Area/Zone/Owner filters. There is a now a global option that indicates if Data Maintainers should be used as a filter, and if this is set then their is a Filter field on each Data Maintainer.
  - Added the ability to use @MODELFIELD syntax for the following options: Transient\_Options: ExpDirectory PVCurve\_Options: PVCOutFile, PVCQVOptionsFile, PVCStoreStatesWhere QVCurve\_Options: QVOutputDir CTG\_Options: CTGPostSolAuxFile, PostPostAuxFile, CTGResultStorageFile:1 Sim\_Environment\_Options: SEOSpecifiedAUXFile:0, SEOSpecifiedAUXFile:1, SEOSpecifiedAUXFile:2 MessLog\_Options: LogAutoFileName
  - Remove FilterPre from the list of required fields for a Filter object. Assume a value of NO if not present.
  - Added concise variable names for DynamicFormatting objects
  - Added option *Use Defined Names in Variable Name Locations* to the Case Information Display options. This will display certain fields that are able to be named (CustomFloat, CustomInteger, CustomString, CustomExpression, CustomExpressionStr, DataCheck, DataCheckAggr, and CalcField) to be shown with the name replacing the location number when the fields are shown as their variable names. As an example, CustomFloat:1 will appear as CustomFloat:The name I gave this float.
  - Added ability to compare DateTime values to fields in Advanced Filter conditions
  - Added a new field on an InterfaceElement object called “NearBus”. This field will be processed to specify the near end for an element that references a Branch, MSLine, or DCLine. Normally using an AUX file by specifying bus numbers or bus name\_kV strings, the NearBus is part of the Element field as the first bus listed is the NearBus. When creating an AUX file using labels however, then the Element Syntax is only "Branch 'My label'" which does not indicate a NearBus. The assumption when using labels is that the NearBus is always the FromBus as specified in the network model for the Branch, MSLine, or DCLine. To add more flexibility, a new optional field NearBus has been added. When shown in Simulator this field will show the number, Name\_kV, or the primary label of the NearBus, but when data is entered in this field it is processed as follows.
  - When reading WECC RAS AUX formats written by old versions of PSLF, some incorrect syntax has been appearing in the file with the objecttype SECDD and TRAN appearing incorrectly. Changes were made to the parsing so that if the string SECDD or TRAN appears in a location where BRANCH would be expected, we reinterpret the syntax as showing BRANCH instead. These AUX files really should still be fixed by the user, but PowerWorld will read them regardless. When writing back out an AUX file from Simulator the correct syntax using BRANCH will be used. For the ModelCondition object this impacts reading the Object and FilterObjectType fields For the ContingencyElement and RemedialActionElement this impacts reading of the Object and ObjectAction fields, as well as reading the CTGElement SUBDATA sections.
  - When creating a new Case Comment through script or aux file, a blank User and Time can be specified. This will default to the current user and time.
  - [Auxiliary File SCRIPT](03-cases-files-and-formats.md#auxiliary-file-format-aux) and [SimAuto](33-simauto-overview-and-setup.md#automation-server) 
  - New Script Commands and SimAuto Functions
  - Added a new script command DiffFlowWriteCompleteModel() which will perform the save done of the Present Topological Differences from Base Case dialog when choose to "Save To\>Complete Model". The new script command has the format DiffFlowWriteCompleteModel("filename", AppendFile, SaveAdded, SaveRemoved, SaveBoth, KeyFields, "ExportFormat", UseAreaZone, UseDataMain, AssumeBaseMeet)
  - Added new script command DiffFlowShowPresentAndBase(How); Use this to set the parameter "Show Present|Base in Difference and Change modes".
  - Added script commands DiffFlowWriteNewEPC and DiffFlowWriteBothEPC which have identical parameters as DiffFlowWriteRemovedEPC, but they write out any determined by the Difference Case Tool to either be NEW objects or objects in BOTH the base case and present case.
  - Added new script commands which will save transient stability dynamic models to 4 file formats. This commands have a parameter to specify the filename and then a second optional parameter called "DiffCaseModfiedOnly". When omitted, the second parameter is assumed to be NO. Set to YES and it will only save models that are either new or models which have had a parameter modified as compared to the difference case tool base case. TSSaveBPA("FileName", DiffCaseModifiedOnly); TSSaveGE("FileName", DiffCaseModifiedOnly); TSSavePTI("FileName", DiffCaseModifiedOnly); TSWriteModels("FileName", DiffCaseModifiedOnly);
  - Added new script command TSClearAllModels; which will delete all transient stability dynamic models from the case.
  - Added new script command: InterfaceCreate( NewName, DeleteExisting, FilterType, FilterName)
  - Added ClearSmallIslands script command to identify the largest island, and de-energize all others.
  - Added script command VerifyDistributedComputersAvailable which allows distributed computer status to be verified via script action.
  - Added the ability to delete named system states, both through the GUI and with a new script command DeleteState which takes the same parameters as RestoreState. If the name All is provided for the named state to delete, all named states will be cleared.
  - Added script command GICLoad3DEField
  - Added script command PanAndZoomToObject
  - Added script command ScheduledActionSetReference
  - Changes to Existing Script Commands and SimAuto Functions
  - Made a commonly used feature much more memory efficient. The feature to Send To Excel by either right-clicking on the case information display, or when using the related SCRIPT command, could cause Simulator to run out of memory when used on extremely large data sets.
  - Added three additional optional parameters to the end of SendToExcel ClearExisting: Optional with default = YES. Set to NO to indicate that the existing worksheet should not be cleared before pasting in the information being sent RowShift: Optional with default = 0. Set to a positive integer to indicate a shift downwards by a number of rows ColShift: Optional with default = 0. Set to a positive integer to indicate a shift rightward by a number of columns
  - Added new optional parameter to ZeroOutMismatches script command. Specify ZeroOutMisatches(Load); to indicate that fake loads should be created to zero out the mismatches. The default behavior is that ShuntG and ShuntB will be changed. Added right-click option to the mismatch table to do the same.
  - The SaveJacobian script command will now allow DC to be specified for the JacForm parameter. This will save the B' matrix for the dc power flow.
  - Added new optional parameter to CalculateLODFAdvanced, IncludeIslandingCTG. The default is YES to retain original functionality. This behaves in the same manner as the new option on the dialog.
  - Modified the OpenCase scripts command for EPC files to have an extra parameter (MSDummyBus). The options are FROM, MAX or the range (ex. 99960-99975, 99980). Example script command would be OpenCase("filename", GE, \[MAINTAIN,2.0,YES,"99960-99975, 99990-99994"\]); OpenCase("filename", GE, \[MAINTAIN,2.0,YES,FROM\]); OpenCase("filename", GE, \[MAINTAIN,2.0,YES,MAX\]);
  - Adding script support for named system states. StoreState now takes an optional "StateName" parameter, and RestoreState has an optional second parameter for the State Name to be restored (which is ignored if the first parameter is not USER).
  - Streamlined the operation of three script commands to improve performance speed -- MergeLineTerminals, MergeBuses, and Delete
  - Made a fix so that OPENNETEMS file types can be loaded using the OpenCase script command.
  - When writing files from Auxiliary Script commands, we will now keep retrying to write them pause for a moment if the file being written to is in use by another program and thus locked, and then attempt to write the file again. This will be attempted 100 times with a 0.1 second delay between each attempt.
  - Added parameter Script to OpenOneline script command that will specify a script command to be executed on the newly opened oneline
  - When loading or saving a file through a script command, a special PROMPT syntax can be used to prompt the user for the file through a dialog. An additional parameter can be included with this syntax to specify the initial directory in which the dialog will open. The format of the this command is now \< PROMPT 'Caption' 'FileTypes' 'InitialDirectory'\>. Clicking Cancel on the file selection dialog will cancel the command and skip any remaining commands in the auxiliary file.
  - The & syntax can be used to reference a Model String Expression to specify the value of a field in a script command
  - [Aux Export Format Description](09-auxiliary-files-and-script-commands.md#auxiliary-file-export-format-description-for-both-display-and-power-system)
  - On the Auxiliary File Export Format Description dialog, when choosing to Create Format for Complete Case and choosing "Complete Model", the dialog that appears allows you to choose which parts of the model to export. There is now a new check box on this dialog that allows you to specify for the Network Model portion to "(Split commonly changed fields)". Checking this new box will split up fields for some objects into 2 data sections: a section with fields that normally do not change and a second section with fields that commonly do change. This mimics what occurs when exporting data from the Present Topological Differences from Base Case tool.
  - Modified the Auxiliary File Export Format Description dialog so that you can manually drag the fields listed to change the order in which they appear. Also modified so that a selected list of entries can be deleted by hitting the Delete key on the keyboard (after selecting using mouse clicks in combination of Ctrl or Shift keys).
  - [Available Transfer Capability (ATC)](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)
  - Added the contingency option to Iterate on Action Status to the ATC dialog. This option has always been used with linear ATC calculations, but it had previously only been found on the contingency dialog. When both dialogs are open at the same time, clicking on this option on either dialog will change the option on the other dialog.
  - Added more fields as valid fields to be used when using the option to Iterate on Action Status with linear contingency analysis. These fields include: Branch Max MVA, 3-winding transformer Status of primary, secondary, and tertiary windings, All Branch MVA Limits, and All Branch Amp Limits.
  - When using option to Create Contingent Interface For Selection, support has been added for generator open and load open contingencies
  - Added two new Iteratively Found values when using the (IL) then Full CTG Solution method and iterating on an individual limiter: FULL\_CTG\_SELLER\_LOST and FULL\_CTG\_BUYER\_LOST. These indicate that either the Seller or Buyer has been completely disconnected when the contingency is implemented. The transfer limit that is reported is the total amount that could be ramped before the contingency caused the loss of either the Seller or Buyer.
  - Bus View and Substation View Onelines
  - When using the Bus View option to "Show Serial Buses" on a Full Topology Mode, Simulator previously would bias a series of branches to show the non-switching devices most prominently. This was so that Transmission Lines, Transformers, Series Caps/Reactors, and such would appear larger and more prominent. If such a device was not in the series of buses then the first device was always shown. This has been modified so that within a series of switching devices we also bias to show either Breakers or Load Break Disconnects as the prominent device. This makes the breakers and load break disconnects appear more prominently than the plain disconnect switches.
  - Modified the Bus View fields shown for Multi-terminal DC lines and VSC DC Lines so that they are linked to the object using the generic Model Field display object. Previously they were just background text fields and thus the MW, Mvar and MVA shown were calculated only when the bus view was redrawn at a bus. As a result as the system state changed and the bus view was open the fields for these DC devices were not changing. With this change they will now change matching the expected behavior of all the other fields on the bus view.
  - On the Bus View, added ability to bring up the dialog for VSC DC Line or a Multi-terminal DC line when right-clicking on the background lines that are drawn to represent them.
  - [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays)
  - Added new expression functions for converting floats representing a date time into strings and also converting strings formatted as date/times into floating point numbers. These function all follow similar syntax as used in Excel functions of the same name. (1) Text(floatvalue, "formatstring") --\> returns a string with the floating point number converted to a data time string using the formatting specified in the format string. (2) DateValue("datetimestring") --\> returns a floating point number representing only the integer part for the date/time floating point (3) TimeValue("datetimestring") --\> returns a floating point number representing only the fractional part for the date/time floating point (4) DateTimeValue("datetimestring") --\> returns a floating point number representing the date/time floating point See the PowerWorld help documentation for more information on the format string. Search "Formatting String" in the help.
  - Cleaned up the Owner filtering for objects. When using the find dialog on a table if the object found was not presently visible on the case information display because Area/Zone filters were not met, Simulator would automatically change the area/zone filtering to make the object visible. This has now also been done for Owner filtering and the new Data Maintainer filtering.
  - Added ability for Data Maintainer objects to work as a filter on case information displays in a manner similar to Area/Zone/Owner filters. There is a now a global option that indicates if Data Maintainers should be used as a filter, and if this is set then their is a Filter field on each Data Maintainer.
  - The list of secondary filter classes available for objects has continued to grow to provide flexibility. However this has made the Filter drop-down menu on the case information toolbar extremely long as a result. We have organized this drop down menu so that object types are grouped by type such as "Network", "Aggregations", etc... Secondary filter classes that are in the same grouping will continue to appear directly under the filter submenu, but those in a different grouping have been moved inside an additional sub menu.
  - In Version 20 we added the Quick Filter drop-down directly on the Filter toolbar. As part of doing this we changed the caption of the button for opening the quick filter dialog to "Dialog". This also changed the caption of the button under the Filter drop-down the the Case Information Toolbar to "Dialog" which caused confusion. We have changed the caption under the Filter drop-down back to "Quick Filter..." to be consistent with previous versions.
  - When dynamic formatting was defined for a bus object's case information displays, it was always inherited by the area, zone, and substation objects. These objects would automatically apply the formatting if any bus in the aggregation met the conditions of the dynamic formatting. Previously this inheritance could not be prevented which was reported as a problem by some users. This inheritance has been removed as it is easy enough to define dynamic formatting for area, zone, or substation objects using advanced filtering that applies to a bus object type now.
  - On the Multi-Terminal DC Line and Two-Terminal DC line case information displays, add the ability to right-click on a selection of devices and choose "Remove Device and Converter to Equivalent Loads". This will add in new load objects which replace the MW and Mvar injections coming from these devices and then delete the DC system device.
  - Modified how CalculatedField objects work in the user interface dialog when they are very simple and refer to another Advanced Filter by reference.
  - Added an explicit field for the Island records for *Number*. This show the internally assigned Number of each island shown in the user interface. This number is automatically recalculated every time the topology of the system is evaluated. This number matches the number shown on various other tables such as Bus, Gen, etc. which show the island in which a device is contained.
  - When specifying variables in the Custom Expression dialog, there are now variable type choices of Field, Model Field, Model Expression, and Model String Expression. Model Expressions and Model String Expressions are special entries in an attempt to support older functionality of the dialog when only Model Expressions were available. Specifying Model Fields and Model String Expression as a variable type will not be supported in previous patch releases in Simulator and will become unlinked Model Expressions when loaded into earlier patch releases.
  - Custom Expressions can now reference any model field. Previously only Model Expressions could be accessed in addition to fields for the particular expression object type.
  - Added concise variable names for Superbus and Subnet objects
  - Added a new field to a DataMaintainer called *AllowEdit*. Setting this field to NO will mean that for objects that are maintained by this DataMaintainer, case information display editing will not be allowed nor will modifying an fields of those objects using AUX files or script commands.
  - Added several Short-Cut keyboard keys for use on case information displays Ctrl + Q = Quick Filter Dialog, Shift + Alt + A = Save Auxiliary File for Selected Records All Columns, Ctrl + Shift + A = Save Auxiliary File for Selected Records Selected Columns, and Ctrl + Alt + A = Save Auxiliary File for All Records All Columns
  - Added Case Info Customization for MW Transactions case information display. This will allow the same customizations such as the fields that are shown and the applied Quick filter to be stored when the display is closed and then used as set when the display is open again.
  - Made BusPair and VSCDCLine objects available for use in Model Expressions.
  - Added *Solution Detail* field with PWCaseInformation object that indicates whether or not the last power flow solution was successful.
  - Added *% of Amp Limit (Max)*, *% of Amp Limit at From Bus*, and *% of Amp Limit at To Bus* fields to show the flow based on the presently selected limit set with the Limit Monitoring Settings.
  - There are two new folders with Branch fields: Limit Monitoring\\Amp Limits Percent and Limit Monitoring\\MVA Limits Percent. These contain fields showing flow as a percent of the respective limits for all limits that are available.
  - Added new field for a Bus *IsAreaSlack*. This field returns YES if a bus has been designated as an area slack bus and NO otherwise.
  - Made the field *Selected* available for the ModelFilter object.
  - Modified to make an Interface Name and Number fields which can be entered in the case information display and via an AUX file.
  - Added a new field *Lockout* to a Branch in Simulator. When this is YES you can not open or close the branch. This is intended for operator training uses of the software.
  - Added support for secondary filtering for Case Information object using Bus, Generator, Load, Switched Shunt, or Branch advanced filters.
  - Added support for Calculated Fields with Case Information object. This will allow calculations on all objects in a case. Buses, Generators, Loads, Switched Shunts, and Branch calculated fields are available for the Case Information object.
  - Added new fields to Case Information object: *Max Branch %*, *Max Branch % Branch*, *Max Voltage*, *Max Voltage Bus*, *Min Voltage*, *Min Voltage Bus*, *Max Mvar Mismatch*, *Max Mvar Mismatch Bus*, *Max MW Mismatch*, and *Max MW Mismatch Bus*.
  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - Modified saving contingency analysis settings using DataMaintainers so that they make use of the new "Filter" field for a DataMaintainer instead of using the Selected Field. This is more consistent anyway.
  - Added support for several new VSCDCLine contingency actions that mimic the features available with the two-terminal DC line: OPEN, CLOSE 20 MW, SETTO 40 %, SETTO 20 MW, CHANGEBY -60 %, CHANGEBY -30 MW, and SETTO 5 OHMS
  - Updated the column headings and descriptions of several CTG\_Options fields so that when these options are shown in the CTG\_Options\_Value tables in a case information display more descriptive headings and descriptions are shown. This effects 3 options related to Island Limit Monitoring and 3 options related to storing contingency results to the hard drive.
  - While the contingency dialog was open, when loading an AUX file from somewhere other than the Load button on that dialog, the various edit boxes and check boxes on the contingency dialog the show the contingency options would not always update. This has been fixed so that regardless of how the AUX file is loaded the edit boxes and check boxes will update immediately.
  - OPENCBS and CLOSECBS contingency actions that are not able to identify breakers will now open or close the device meant to be acted upon by breakers. This will allow the same contingency definitions to be used in full topology cases containing all breakers and hybrid or planning models that do not contain breakers for all devices.
  - The ContingencyElement field WhoAmi Description shows a pretty version of the contingency element description. Various options allow that descriptions format to be changed to show various file format versions of the element description instead. If the element was unlinked however, the file format versions would just show a blank indicating that the unlinked objects wouldn't be written to file by default. This has been changed so that now we just show the normal unlinked information prepended with the word "Unlinked". It's still clear to the user that the element is unlinked.
  - Added more fields as valid fields to be used when using the option to Iterate on Action Status with linear contingency analysis. These fields include: Branch Max MVA, 3-winding transformer Status of primary, secondary, and tertiary windings, All Branch MVA Limits, and All Branch Amp Limits.
  - Added Arming Criteria to the list of dependencies for Remedial Actions and Remedial Action Elements.
  - Added a two new buttons to the Tools Ribbon tab under RAS + CTG Case Info\>Contingency Reference\>Set As Reference and RAS + CTG Case Info\>Contingency Reference\>Restore Reference
  - Modified the way that Contingency Violations (ViolationCTG) for an island choose the bus used as the identifier for the island. Previously, we would always take the slack bus of the island to identify it. Now we will instead choose the bus from the island that is the first in the list of buses sorted alphabetically by the name of the bus. This will help make the choice of the bus more consistent because sometimes the slack bus would change for the same set of buses depending on the state of the system (generator hitting Mvar limit for instance).
  - Added the wind control mode and wind control mode power factor for generators to the system state so that this can be changed during contingencies and then restored to what it was in the base case.
  - When reporting contingency analysis violations related to islands, if an island is split into pieces then whichever island has the original slack bus is considered the "old island" and all others are considered "new". The island reporting then only reports "new" islands. This however meant that if the original slack bus island had only a few buses and the other pieces have 1000s, then the piece with 1000s would still be reported as the "new" solved island. This has been modified so that if an island is split into 2 or more pieces, then whatever island piece has the largest amount of Load MW is not considered a "new island" while all others are considered "new".
  - On the local menu of the Contingencies case information display there is a new option under Insert Special called *Merge Contingencies That Result in Identical Breaker Actions*. This will examine existing contingencies that contain either an Open With Breakers or Close With Breakers actions and determine the breakers that will actually operate. If another contingency with Open With Breakers or Close With Breakers actions exists that would cause the same breakers to operate, both contingencies will be merged into a single contingency.
  - When auto inserting contingencies and using the Open Breakers action, a new option has been added called *Prevent Identical Breaker Actions*. Based on the current topology, this will determine the breakers that will operate for a given contingency. If another contingency is found that will cause the same breakers to operate, the actions from both contingencies will be merged so that only a single contingency is inserted.
  - On the contingency analysis dialog, using the Other \> Restore Reference option will put a message in the Status box on the dialog, "Reference State Restored", that better indicates the system state currently in memory.
  - Added an option with contingency voltage screening called *Max Iterations* that will allow the maximum number of inner power flow loop iterations to be specified. The default is 2, which was the hardcoded value prior to this option being added.
  - Added an option with contingency voltage screening called *Store Voltage Violations* that will allow limit violations to be stored from the voltage screening. The default is to not store limit violations during the voltage screening because the estimate of voltages at this point might not be very realistic because they are determined without a full power flow solution.
  - When using the option to *Join Active Contingencies* and creating a large number of contingencies the creation of the contingencies could be very slow. Made some changes to speed up the creation of the contingencies but showing them in the GUI is still slow.
  - When monitoring custom monitors with contingency analysis and using a percentage change, if the original value is 0 do not report anything.
  - For Remedial Actions and Remedial Action Elements, unlinked Arming Criteria will be retained when setting the Arming Criteria from an auxiliary file. If setting the Arming Criteria by directly editing the field in a case information display, a prompt will ask if unlinked criteria should be retained.
  - For Contingency Elements, unlinked Model Criteria will be retained when setting the Model Criteria from an auxiliary file. If setting the Model Criteria by directly editing the field in a case information display, a prompt will ask if unlinked criteria should be retained.
  - Added fields with contingency elements to show the *Nom kV* of the buses associated with the element without looking into injection groups and interfaces and *Nom kV (recurse)* that will show the voltages including looking into injection groups and interfaces.
  - Added *Normal Rating No Action* field with a contingency that will allow base case (reference state) violations to be recorded in the same format (LimitViol and ViolationCTG objects) as contingency violations. Violations will only be recorded if the contingency has no elements defined. Violations will be determined using the Normal Rating Set specified with the Limit Monitoring Settings.
  - Violation CTG Injection Sensitivities can be calculated for violated elements for each contingency.
  - [Difference Case](08-view-case-data-tools.md#difference-case)
  - Added the *GE Long ID* field for loads
  - In the Present Topological Differences from base case tool, the removed objects did not support the case information display filtering by owner, but only display filtering by Area/Zone. This has been modified to also support Owner filtering.
  - Added the Area/Zone/Owner filter menu/case info toolbar option to the Removed object tables in the Topological Differences from Base Case dialog. The functionality to filter these tables by area/zone filters had just recently been added so there had previously been no reason to care about them from these tables.
  - Modified the Base Case Topological Comparisons dialog so that user may use Data Maintainer filters to specify which objects to write out to a file.
  - Added ability for the list of Removed Substations in the Present Topological Differences from Base Case tool to properly use the Area/Zone/Owner filters.
  - Added Case Info Customizations for all case information displays used with the Difference Case tool dialog.
  - Added a button to remove field customizations for all of the difference grids on the topological differences dialog.
  - When showing some values in difference flows we show the Present Value followed by a | character followed by the Base Value such as " 103.45| 206.45". Depending on how wide the column is on the display however the text may have the portion of the string with the | character truncated. If the user can not see the | character it makes is confusing as to whether the value has changed or not. To avoid this confusion, we will now show the background color of cells shown in difference flows that contain a | character with a slightly different background color to indicate the value has changed.
  - Modified the Present Topological Differences from Base Case tool so that when choose to Save the differences of the Complete Model to an AUX file, the user may now define an AUX Export Format Description object indicating which objects and field lists to use for the export. This appears on the confirmation dialog for exporting the AUX file with the differences. The format will determine the objects that are saved for NEW, BOTH, and REMOVED types of objects. The format will determine the fields for NEW and BOTH types of objects, but any required fields will also be included with NEW objects.
  - Added support for branch fields *RegBus* and *RegBusNumUsed*
  - Added support for generator fields *CTGPreventAGC*, *CTGPartFact*, *CTGMaxResp*, *CTGMaxRespPerc*, and *Online*
  - Added a new object called DiffChangeTolerance which allows you to specify the tolerance used during the Change mode to determine if a floating point number has changed enough to be considered different. The default for all fields is a change of more than 0.0001% (6 significant digits), although defaults for Bus Voltage and Angle as well as Bus/Substation Latitude/Longitude are included that require slightly more precision.
  - Added many new fields related to Transient Stability input to the Difference Case tool. This includes the following fields for respective objects Gen: TSMachine, TSExciter, TSGovernor, TSStabilizer, and TSOther; Load: TSDistEquivMVABase, TSDistGenMVABase, TSDistEquiv, TSDistGen, TSDistEquivMVABaseUsed, TSDistGenMVABaseUsed, TSDistEquivUsed, TSAlgebraic, TSDynamic, and TSRelay; Shunt: TSModelName; Branch: TSRelayName; Bus: TSDistEquivMVABase, TSDistGenMVABase, TSDistEquiv, and TSDistGen; Area: TSDistEquivMVABase, TSDistGenMVABase, TSDistEquiv, and TSDistGen; Zone: TSDistEquivMVABase, TSDistGenMVABase, TSDistEquiv, and TSDistGen; Owner: TSDistEquivMVABase, TSDistGenMVABase, TSDistEquiv, and TSDistGen
  - Modified the Present Topological Differences From Base Case dialog so that there is a new check box called *For summary table statistics, show counts using Area/Zone/Owner/DataMaintainer filtering*. This box is not checked when the dialog is first opened, but if you check this box, then the summary statistical counts will be based on objects that meet the Area/Zone/Owner/DataMaintainer filtering in the case.
  - Added features to the Present Topological Differences tool to write out EPC files for Both and New objects lists. Previously you could only do this for the Removed objects.
  - Added ability to use the Difference Case tool to save ONLY the changes in transient stability models to either an AUX, DYD, DYR, or SWI file.
  - *Diff Modified* field added with all transient stability models to indicate if a model parameter, Device Status, Criteria, or the reference to another object have changed between the Present and Base case. This field will be blank if a model exists in the Present case that was not in the Base case.
  - When in the Difference Case Mode of either Change or Difference, all case information displays showing transient stability models will only show stability models that have been modified (*Diff Modified* = YES or blank)
  - [Fault Analysis](27-fault-analysis.md#fault-analysis)
  - Added faulted bus nominal voltage to the multiple fault results table
  - Added a log message for FaultAna when the user selects a pre-fault profile of Solved Power Flow, but the power flow solution fails before applying the fault. An abort message is added to the log, and the attempted fault calculation is cleared.
  - [File Formats](03-cases-files-and-formats.md#case-formats) 
  - EPC
  - When loading an EPC file, if a generator is set to cont\_mode = 3, but the power factor given is 0.0, then this is impossible data (would result in infinite Mvar output). In this situation, Simulator will now change the cont\_mode to 1 which is equivalent to setting AVR = NO in Simulator. A warning will also be written to the message log.
  - When loading an EPC file, if a generator is set to cont\_mode = 2, but the power factor given is 0.0, then this is inconsistent data. In this situation, Simulator will now set pf = 0.01 and write a warning to the message log.
  - Removed the log message when reading an EPC about bypassed branches that had a positive X value. This is perfectly fine for a bypassed series reactor, so the log message was causing confusion.
  - When reading the EPC generator cont\_mode for the voltage control mode, the integer values -2, 2, and 3 indicating types of either constant power factor or boundary power factor control. These were added several years ago originally for wind turbine generators and when first introduced it was reliable to assume that these always indicating a wind turbine. At the time, the turbine type field was not reliably populated so PowerWorld automatically changed the unit type when these values were seen. This is no longer appropriate so we no longer populate the unit type based on these values.
  - When writing out to the EPC file, any UnitType values for nuclear steam generators NB, NG, NH, and NP will be written as turbine type 1 indicating a steam turbine. Previously these were written as 99 indicating other. Customers pointed out that steam was an appropriate mapping.
  - When reading an EPC file, if any generator turbine type integers are read which are not specified in the WECC Data Preparation Manual, then a warning message will be written to the log indicating that this integer value is being interpreted as "OT (Other)"
  - When reading an EPC file, added the translation of new EPC turbine type integers to the UnitCode as spelled out in recent updates to the WECC Data Preparation Manual. 3 --\> XC (Cross Compound Steam), 19 --\> BT (Turbines Used in a Binary Cycle, including those used for geothermal applications), 25 --\> WS (Wind Turbine, Offshore), 29 --\> CT (Combined Cycle Combustion Turbine Part), 42 --\> BA (Energy Storage, Battery), 43 --\> FW (Energy Storage, Flywheel), 44 --\> ES (Energy Storage, Other), 46 --\> CE (Compressed Air Storage), 47 --\> CP (Energy Storage, Concentrated Solar Power), 51 --\> HA (Hydrokinetic, Axial Flow Turbine), 52 --\> HB (Hydrokinetic, Wave Buoy), 53 --\> HK (Hydrokinetic, Other), and 54 --\> PS (Hydro Pumped Storage)
  - Modified the options for numbering dummy buses of multi-section lines when loading an EPC file. The options can now be to the dummy bus from the FROM bus (as before), from the Max number of bus available or from a range.
  - Updated the options dialog when saving an EPC file with options to better explain how the generator base load flag is being written.
  - Modified writing out line shunts for EPC format so that line shunts that are part of an MS line determine which end of the MS line terminal the shunt is closest to, and fixes the shunt ID to correspond to the correct end of the MS line when writing it to the EPC format.
  - When reading an EPC file with a generator set to cont\_mode = 2 (boundary power factor control in Simulator's options), but the power factor is zero (pf=0), previously we were just setting the power factor to 0.01 instead resulting in a very large Mvar range. It is not clear what we should do with this bad input data, so we are modifying to instead just read this as cont\_mode=1 (fix Mvar or AVR = 0).
  - Added the ability to read the clzone from the EPC file and create LoadModelGroup objects from this designation.
  - Added the ability to read from a DYD file the "\_cmp\_der\_a" model and then reference it from a cmpldwg or cmpldw2 dynamic model assigned to a load. It creates in Simualtor a DGDER\_A model assigned to the corresponding load record.
  - RAW
  - Can now read version 34 files for planning models. Working on support for full topology models.
  - Fixed another issue with multi-terminal dc line names when writing to a RAW file. When the name is blank the number of the MTDC will be written instead. In this instance, the name was not being enclosed in single quotes, but his has now been fixed.
  - When loading in a PTI RAW files that have been exported from other software such as an EMS system, we have found exported voltages around three-winding transformer can be highly suspicious resulting in very large initial mismatches. This occurs when one or more terminals of a three-winding transformer is radial and not connected to anything that is online. In these situations the star bus and the radial terminal can have per unit voltage magnitudes and angles in the RAW file that are not consistent with the rest of the RAW file. This has been fixed by detecting these situations and assigning a more reasonable voltage and angle for these buses based on the impedances and voltages around them.
  - When reading a RAW file, PowerWorld parses the comments at the end of object records to create a label for the object. We look for the a string inside brackets \[\], while skipping over spaces, forward slashes and astericks. This has been modified to also skip over comma characters when looking for the special brackets.
  - Modified to write out the line length field to a RAW file out to 2 decimal places instead of 1.
  - Modified how comments at the end of RAW file records are parsed to more loosely assign labels if the comments contains label inside brackets
  - When loading a RAW file, the Mvar ouptut is estimated for FACTS which are converted into Continuous Switched Shunt objects in Simulator. This is because the RAW file does not specify the present operating point. To estimate this, the Mvar mismatch at the terminal of the FACTS is used. This has been modified so it sums up the Mvar at buses connected by low impedance branches to the FACTs terminal as well. Mvar are then shared by all FACTS that are connected to the same group of buses connected by low impedance branches.
  - When reading in a RAW file, the shunt-connected FACTs devices are now translated to a SwitchedShunt with "ShuntMode=SVC" and "SVC=SVSMO3". In addition when writing back out to a RAW file these SwitchedShunt objects are written to the FACTS device section as well. Previously these FACTs models were read in as "ShuntMode=Continuous"
  - Modified reading the RAW file bus records so the ONLY required entries now are number and name. If omitted the NomVolt, IDE, Area, Zone, and Owner will now all default to 1. For version 24 - 30, G and B will be 0.0.
  - SEQ
  - When loading a \*.seq file, the connection codes 4 and 14 represent a configuration where there is no series path in the zero-sequence network and there is no ground path in the zero-sequence network. PowerWorld was reading this in and setting the winding configuration to Wye-Wye which is a valid assumption, however it is equally valid to set the winding configuration to Delta-Delta. Both of the configuration result in no series path and no ground path. Customer were expecting this to be Delta-Delta and reported that other software reads this code in as Delta-Delta. This patch is modifying reading the \*.seq file so that the codes of 4 and 14 are read in as a configuration of Delta-Delta.
  - hdbexport CSV
  - Added message to the log when reading these files and the option to translate the DC system into multi-terminal DC systems is set to Always or Prompt and no DCLN records exist in the file. DC lines cannot be created if DCLN records do no exist.
  - When reading an hdbexport CSV file and performing a translation of the DC system into PowerWorld Simulator's data structures, Simulator will now search for generation (UN records) inside the DC system and translate those generators directly to the AC system terminal bus that is kept after performing the translation. This helps translate some VSC DC lines that are being modeled approximately in the hdbexport file by customers who add a synchronous condenser (UN record) inside the DC system.
  - When loading an Areva hdbexport CSV file, Simulator reads the BS record fields MMINJMW and MMINJMR and places those as GShunt and BShunt values at one of the Simulator Bus records. The Simulator Bus records correspond to the ND records in the hdbexport CSV file. These mismatches represent the mismatch from the optimal state estimation solution. Previously Simulator would arbitrarily assign the BShunt and GShunt values to the Bus with the lowest bus number. This has been changed now with the goal of keeping these injections connected to the system as much as possible even as devices are opened and closed from this base model. To achieve this, Simulator has a preference that the mismatch be assigned to a bus that has the highest number of in-service branches and DC devices dconnected to it. As a tie-breaker after that device count, the preference is for the following type of devices (in order) to be connected to the bus: (1)DC, VSC, Multiterminal DC, (2)Series Caps, (3)Transformers, (4)Lines, (5)ZBR, (6)Breaker, (7)Load Break Disconnect, (8)Fuse, (9)Ground Disconnect. Overriding all these preferences however, Simulator will also discourage buses connected to (1)Switched Shunts, (2)Generators or (3)Loads The goal here is to not assign the MW/Mvar mismatch to a bus that could be commonly taken out of service when isolating another device in the system.
  - When reading the RAS file for the Areva EMS system, added the ability to read a MWS field from the IPIN record to indicate that the MW field should be used but evaluated in the reference state for contingency analysis.
  - When loading an Areva hdbexport file, the Bus.MMINJMW and Bus.MMINJMR are assigned to PowerWorld's bus records as the BShunt and GShunt impedance values. This was conflicting with PowerWorld's expected structure for a three-winding transformer however when there was a BShunt/GShunt assigned to the star bus of a three-winding transformer. All would be fine inside Simulator, however when you then saved to an AUX file, and then tried to read that AUX file back in it could cause trouble. The 3WXFormer records would not permit the creation of three-winding transformers if the star bus was an existing bus which had any devices attached. The BShunt and GShunt were enough of a device for us to not permit this. We have fixed this by now so that we allow you to create the three-winding record but then take the BShunt and GShunt and move that impedance out to the terminals of the three-winding transformer
  - OTG Contingency
  - Modified reading of the OTG contingency text file format so that the header row for a Contingency can contain a second string such as "\#B2\_26" which will be ignored and then the third string kept and read as the contingency description. Previously anything after the first \# character was completely ignored.
  - When reading the OTG file format for contingencies, the header row for each contingency was expected to contain 2 strings. The second string however is only read as the "memo", so if it's missing we can just assume it's blank. The parser has been modified so that if it's missing we still read the file, where as previously it would cause the reading to fail.
  - When reading the \*.otg file format for contingencies, added ability to look for the keyword DEFAULT at the top of the file. If this is found then all lines are skipped until the keyword END is found. This is an indication of options in other software tools which PowerWorld does not parse, but adding this code at least properly skips this information and reads the remainder of the file.
  - Modified the reading of the OTG Contingency Format. Recent versions of this format have changed the file syntax. PowerWorld Simulator will automatically figure out which format the file is and read it appropriately.
  - WECC Switch File
  - Updated reading in of the WECC Switch File Format. Now accepts \* and \# at the beginning of a line as comments. If TITLE record is not found inside \*.swt file, then the file name is used as the Transient Contingency Name. Change start time of contingencies to -1 second, so that it is consistent with the Switch File Format to have a 60 seconds of flat start.
  - ASPEN RAT
  - Relay models can be created from this format
  - OSI OpenNet
  - When reading the OpenNet EMS csv file,s, added code to read transformer tap settings off of XFORMER records.
  - GCAP
  - When writing out a GCAP file, now write all the capability curve points instead of only the first 10. Newer versions of this file support up to 20 points now. Messages are written the message log indicating if more than 10 points are being written however.
  - UTCE
  - When reading the UCTE file, set all generator to AGC = YES.
  - Greatly sped up the time for reading a UCTE file in.
  - PTI CON
  - Added ability to write out two additional Contingency action types to a PTI CON file 1. BLOCK TWOTERMDC 'name' // Opens the DC line 2. SET TWOTERMDC 'name' to 12.34 MW 3. SET TWOTERMDC 'name' to 12.34 Amps
  - Added translation of the VSC DC Line OPEN contingency actions to a BLOCK VSCDC in the \*.con file.
  - Comtrade
  - Added ability to save results shown in the Results from RAM case information displays for transient stability directly to this format
  - KML
  - Updated the parser to parse PJM lines. This required fixing some things not handled when parsing the lines for coordinates. The PJM files have x,y,z coordinates instead of just x,y. The files do no contain identifiers that can be linked with the case, but at least unlinked lines are now read in.
  - PSLF DRW
  - This file type is now supported for opening oneline diagrams
  - Filtering
  - NumTrue logic added along with the number of conditions that must be true for the logic to be true. This is available with Advanced Filters, Model Conditions, and Model Filters.
  - General 
  - Optimized the closing of a power system case for cases that included a very large number of of model conditions, model filters, model expression, and/or contingencies. The case will now close much more quickly.
  - Model String Expressions can now reference other Model String Expressions.
  - Added the ability in an interface to include a Generator OPEN or a Load OPEN element. This has been integrated in the calculation of the AC Power Flow Solution, Linearized DC Power Flow Solution, the PTDF calculation, and the sensitivities and flows needed to perform an OPF solution.
  - Added a new column for generators to translate the generator UnitType field into the integer turbine type documented in the WECC Data Preparation Manual.
  - Added a new generator field UnitType choice of "XC (Cross Compound Steam)". When reading an EPC file this will be set if the turbine type = 3.
  - Added ability to save named system states.
  - Modified the caption of the *Single Solution* button to say *Solve Power Flow* instead.
  - Added *Memory* field to Distributed Computer object, so the amount of physical memory installed on the specified machine can be displayed along with the number of cores.
  - Added item to "Other Tools" menu to allow the user to clear islands prior to solving. This feature will open all generators in the case which do not belong to the island which has the largest number of buses.
  - Geographic Data View
  - Added Geographic Data View arrow objects for showing vectors.
  - Added pseudo-geographic mosaic display option with Geographic Data Views
  - [GIC Analysis](47-geomagnetically-induced-currents.md#gic-analysis)
  - Adding ability to show GIC results in time step simulation.
  - GIC Hotspot can now be modeled as a rectangle (as compared to a square earlier)
  - GIC geographic earth resistivity regions now have an additional field called HotSpotScalar, in addition to the Scalar. This is to model the supplemental event beta\_s, as per NERC documents
  - Added option to choose between HotSpotScalar vs. Scalar for points inside a hotspot.
  - Added GICGeographicRegionScalarCustom:1 for substations, which overrides looking up the region's hotspot scalar. Similar to GICGeographicRegionScalarCustom:0
  - Added support for the TPL-007.1 geomagnetic scaling function
  - Clarified GIC miles vs. km field values, particularly with aux files.
  - Added GIC field to show minimum ohms/phase on line for calculation of induced voltage.
  - Implemented giving precedence to user entered earth region.
  - DC Lines, Multi-terminal DC lines, and VSC DC Lines included in the calculations
  - Integrated Topology Processing
  - When using the close with breakers algorithm on a branch, breakers will be closed even if the branch is only open at one end. The branch is energized, but the goal should be to have it closed completely. Previously, no breakers would be closed if the branch was considered energized. Now if the branch has Derived Status \<\> Closed we will search for breakers to close. This is done anywhere that the close with breakers algorithm is used.
  - When looking for breakers to open to disconnect devices or close to connect devices, breakers that were connected strictly in series with a switched shunt were excluded. This effectively looks for switched shunts that are connected radially to the system. This was to prevent switched shunts from being connected/disconnected incorrectly if they were connected to a tap point on a line. If a switched shunt itself was to be connected/disconnected the breakers in series with that shunt would still be switched. Changes have been made to how this works: (1) This check is now done for generators and loads in addition to switched shunts. (2) There are options that allow disconnects that are normally closed to be closed when closing breakers to energize a device or disconnects that are normally open to be opened when opening breakers to disconnect a device. These disconnects are now checked and if they are in series with shunt devices that are not the specific device to be closed they will not switch.
  - Made a change that should help prevent numerical stability problems with full topology cases with generators on AVR that are connected to breakers that have not been consolidated.
  - When using the options to *Use Topology Processing* and *Close Breakers to Energize Switched Shunts*, breakers will be opened to isolate shunts at 0 Mvar output when the power flow is solved
  - [Limit Monitoring](18-general-tools.md#limit-monitoring-settings)
  - Added storage in the Window Registry for the user interface options on the Limit Monitoring Dialog. Previously the following was maintained during a session of PowerWorld Simulator, but after you closed Simulator and reopened it, it was not retained. The options include 1. The check box status of “Only show the primary bus for each superbus” 2. The choice under the “Elements to Show” 3. Which tab you are on the dialog
  - Oneline Diagrams
  - Adding the ability to be able to open Areva path overview onelines.
  - *Delta Per Mouse Click* value can now be specified for generator *Cost Multiplier* field
  - Added a new field to a Branch object called the *BranchCloseAngleThreshold*. Specifying a non-zero value for this field will impact how oneline diagrams behave for this branch. When clicking on the circuit breaker objects on a oneline diagram that represent the status of a particular branch, if the branch is presently OPEN and the angle difference across the branch is greater than the threshold specified, then the oneline diagram will not permit you to close in this branch. This was added to help users perform operating training simulations.
  - Added color map for showing integer values.
  - Oneline Link object can specify a left-click option and up to two right-click options
  - Oneline menu accessed by right clicking in the background of a oneline has option to *Open oneline script command dialog* that will allow script commands to be performed on the oneline
  - Adding the ability to pan to display objects via the Areva "find" command when loading in a oneline via a oneline link.
  - Adding the ability to open Areva substation onelines from the right click menu on string grid displays. Also can search for onelines in the Oneline Viewer.
  - Adding the ability to open Areva substation onelines from MTDC bus, converter and line lists; three-winding transformers; interface elements; substations; superbuses; subnets and scheduled actions lists.
  - Modified the oneline hints for branch objects to identify the BranchDeviceType in the Object Identifier string shown when popping up oneline hints.
  - Added a new GIS option to move bus and substation oneline display objects so that they match the latitude/longitude stored with the underlying bus and substation data object information.
  - New marker objects are now added to a 'Marker' layer by default.
  - Added option on the right-click menu for bus display objects to *Open Connected AC Branches* if a bus has *Status* = Connected. If the bus has *Status* = Disconnected the option will be *Close Connected AC Branches*. When closing branches only branches where the other terminal bus is connected will be closed. If there are any dc lines connected to the bus, their status will remain the same regardless of which option is being used.
  - Added hotkey 'R' to Oneline diagrams to toggle the orientation of selected buses, gens, loads, and shunts.
  - A new dialog will prompt the user when pasting objects to a oneline diagram (if they have chosen to copy objects and records). The prompt will ask the user if they would like to create new objects or link to existing objects, which is the previous behavior. Creating new objects will create new objects, including buses, which was not done before. Previously the bus oneline object would still link to the existing bus in the model ("link to existing"). With the new option, a new bus will be created and the oneline object will be linked to the new bus.
  - Added options to create new topology sections - both the oneline and case will be modified  
  - OPF
  - Added check boxes to the OPF tab of the Area dialog for specify whether to Enforce Branch Limits, Enforce Bus Angles, Enforce Interface Limits, Allow DC Line Control, or Include Marginal Losses.
  - Updated column headers for OPFSolutionSummary object type.
  - Power Flow Solution
  - Voltage Droop Control allows specification of renewable plant Q-V characteristic at the point of interconnection
  - Voltage Setpoint Tolerance allows generator voltage control closer to reality
  - Sped up routine related to calculating island information. This speed up will be especially noticeable in full topology cases when validating the case, solving the power flow, and deconsolidation because during these processes information about the state of the islands is stored for the power flow solution.
  - When on island based AGC control and an island does not have any controllable generators, the message in the log will now indicate which island by showing the number of the island slack bus.
  - When using the option to *Check Generator Mvar Limits Immediately*, generators are allowed to hit limits only for the first two voltage control loop iterations. After that they will only be allowed to back off limits. Limits will only be enforced if the Mvar output goes outside of a Mvar limit PLUS a deadband of 10% of the total Mvar Range.
  - [PV and QV Curve](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)
  - Added a new field to a load for *ScaleMvar*. This field defaults to YES. Set to NO to prevent changing the Mvar of this load when shifting power using an injection group (such as in ATC, PVQV, and System Scaling tools)
  - Choosing to archive system states to file will now work when using the Reverse Transfer option with the PV tool and a scenario requires a reverse transfer in order to solve. The states that are stored behave a little differently than when doing the normal forward transfer. Keep in mind that only the contingencies that failed during the 0 transfer will be studied using a reverse transfer. (1) When choosing to "save only the base case for each critical contingency" the base case state will be saved at any reverse transfer level at which a contingency solved. This is different than how the states are saved during the forward transfer because then the base case state will only be saved at the critical transfer level, i.e. the highest transfer level at which a contingency will solve. (2) When choosing to "save all states" both the base case state and the contingency state will be saved at any reverse transfer level at which a contingency solved. This is the same as how the states are saved during the forward transfer.
  - Added Maximum Transfer as a critical reason with PV results. This can only appear with the base case scenario. This will appear if the *Stop when transfer exceeds* transfer level is met. This option would always cause the PV analysis to stop, but there was no indication with the PV results object that this has occurred. A message appears on the dialog, but this couldn't be determined by just looking at the results.
  - Added concise variable names for *PVPlotSeries*, *PVSubPlot*, *PVPlotVertAxisGroup*, and *PVPlot* objects
  - Added ability to specify the Font Size on the plot definition as follows: Vertical Axis Group Labels, SubPlot Horizontal Axis Labels, and SubPlot Legend Labels
  - Added ability with the PWPVResultListContainer object to see many of the custom fields for the Contingency object to which these results refer. This includes the Custom Integers, Floats, and Strings, and the Custom Memo.
  - On the PV Curve dialog the *Present Nominal Shift* box shows the transfer that is in the current system state and the caption for the *Restore Last Solved State* option shows the transfer amount in that state
  - Branch and Interface Violations can now be treated as critical scenarios. Violations can also be logged and viewed at each studied transfer level if choosing not to stop the simulation when a violation occurs.
  - Scheduled Actions
  - When closing disconnects that are in series with breakers when using the Use Normal Status option, also close disconnects that are in series with Load Break Disconnects. This makes sense because we are treating breakers and load break disconnects the same when we are identifying breakers to open or close devices.
  - Added another check when the Use Normal Status option is in use to return disconnects that are in series with the branch that is being returned to service. If a branch is an Open Breaker action, any disconnects that are in series with it and are normally closed will be closed.
  - Added Scheduled Actions tab to dialogs for Gens, Loads, Lines, Switched Shunts, and Interfaces containing a case information display listing the Scheduled Actions that target the selected object. The tab is hidden if there are no Scheduled Actions defined in the case.
  - Added options to the Scheduled Action grid local menu allowing the user to isolate or energize the target device with breakers.
  - Disabled mouse-wheel scrolling over the Scheduled Actions active time window.
  - We now allow Scheduled Actions with a Mapping Status of Unmapped to be loaded from a CROW file regardless of uniqueness. Note that these non-unique actions will only be accessible in the GUI after loading from a CROW file; they cannot be read in from an AUX file or PWB.
  - Security Constrained OPF (SCOPF)
  - Added a column on the LPVariables grid to show the contingency name that corresponds to the variable. Previously it was possible to have variables with the same ID, making it impossible to uniquely identify a variable.
  - Added the contingency name to the 'Bus Marginal Controls' header to allow correlation between the controls and 'LP Basic Variables'
  - Added fields (i) Violated Primary-Element Label, and (ii) Violated Secondary-Element Label for SCOPF. These show the label of the line or interface that is violated.
  - Sensitivity Calculations
  - Added option with Advanced LODF Calculation to *Include Contingencies Creating Islands*. This option is true by default because that is what we had been doing before adding this option. If a contingency creates a new island, we report the LODF as a very big number to indicate that this value cannot be calculated. This option can be used to exclude these types of contingencies from the results.
  - [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation)
  - Updated time step summary to show load/gen/shunt results as opposed to input.
  - Modified TimeDomainOPF so it sets the GIC time value to be the offset time from the start of the time domain simulation.
  - [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)
  - Transient Stability Options
  - New filtering options have been added with the Store to Hard Drive Options that make it possible to be very specific about the information stored
  - Transient Stability Solution
  - The swing equation for synchronous machines is 0.5/H\*\[(Pmech - Dw)/(1+w) - Telec\]. In the result reporting for Simulator, the the accelerating power was being reported as Pmech - (1+w)\*Telec and thus did not include the impact of the damping term D. For the vast majority of model the D term should be zero, however if D is not zero, then we will now report the accelerating power as Pmech - Dw - (1+w)\*Telec instead.
  - Added the ability to specify the TSDistGenMVABase with a Load, LoadModelGroup, Bus, Owner, Zone or Area. The MVABase then assumed for the Load Distributed Generation model will be the TSDistGenMVABase associated with the object from which the Load is inheriting it's model. Thus if the Owner object has a Load Distributed Gen model, the Owner object's TSDistGenMVABase will be used. The exception to this is that any Load object that has a TSDistGenMVABase specified will automatically use that MVABase regardless of where the model is inherited from.
  - When counting the number of consecutive algebraic network solutions using the option "Abort after number of failed solution", Simulator will no longer increment the counter for failed solutions while a fault has been applied in the system.
  - Transient Limit Monitor
  - *Time to Begin Checking* options added with individual transient limit monitors. By default the global options that had previously existed will be used.
  - *Time to Stop Checking* options added with individual transient limit monitors. By default there will be no stop in checking. There is no global option for this.
  - *Limit Logic* that allows the logical combination using AND, OR, and NOT of Transient Limit Monitors
  - Transient Remedial Actions
  - Remedial Actions defined for steady state contingency analysis can be used with transient stability
  - Transient Models
  - Breaker delays can be specified with branches, generators, loads, and switched shunts. Various rules apply for branch relays to use these breaker delays as part of the relay model. Breaker delays are also used with transient remedial action scheme implementation when opening or closing devices.
  - Machine Model
  - Modified new DER\_A model to add parameter Trf and Vpr
  - Added storage of result of the Vmin and Vmax values to the DER\_A model
  - Modified DER\_A model by adding two new parameters Iqh1 and Iql1 as limits on the extra reactive current injection path.
  - Modified WT3G, WT4G, REG\_A, PVD1 type model that have "reactive current management" that prevent high voltages on voltage source converter machine models. Previously if the initial terminal voltage was above the high voltage limit, we would ignore this limit completely. This has been modified so that instead the high voltage limit is set equal to the initial terminal voltage. Indication that this is occuring will appear in the Validation Warnings.
  - Modifications in DER\_A model and DGDER\_A model to modify the feedback of Pord to the power and reactive power control blocks. This must be the feedback for this model because the fractional tripping means that the terminal power is not an appropriate feedback.
  - Also modified how the rrpwr rate limit on the Ip power block works. It will not rate limit based on the absolute value. Thus if Ip\>=0 then it will be a rate limit in the positive direction and if Ip\<=0 then it will be a rate limit in the negative direction. This way it will always permit the device to quickly move toward zero power, but then limit how quickly it moves away from zero. This is needed in case the DER\_A is used to represent a storage device.
  - Added a way to modify the REGC\_A and REGC\_B MW Set Point (Exciter Pref input) from the contingency element when there is only an Exciter REEC\_A among similar variations of the REEC model in the generator.
  - Modified the REGC\_B model to include a Imax current limit and DQFlag. This impacts the network interface equation for higher currents for the REGC\_B model and for the DER\_A model (and thus DGDER\_A as well).
  - Exciter
  - Added DC1C, DC2C, DC4C
  - Added AC1C, AC2C, AC3C, AC4C, AC5C, AC6C, AC7C, AC8C, AC9C, AC10C, AC11C
  - Added ST1C, ST2C, ST3C, ST4C, ST5C, ST6C, ST7C, ST8C, ST9C, ST10C
  - Added CELIN
  - Modified the AC7C exciter model to add a switch SW3. SW3 = 0 then feedback of Efd through the KR block is used (as in the IEEE 421.5 spec) SW3 \<\> 0 then feedback of Ve through the KR block is used
  - Modified the AC7C exciter model to add a switch spdmult spdmult = 0 means that the output is not multiplied by speed (as in the IEEE 421.5 spec) Spdmult \<\> 0 mean that the output is multiplied by speed
  - Governor
  - Added support for the newer Bradley Governor for Chugach (HGBLEM)
  - Added model h6e that represents a Hydro Turbine with an American Governor Company Controller.
  - Added transient stability validation checks to UCCPSS, UCBGT, and UHRSG
  - Added GGOV1DU governor model which is identical to GGOV1 but has up and down deadband limits on the input frequency signal.
  - Added TURCZT
  - Added BBGOV1
  - Stabilizer
  - Added PSS2C, PSS3C, PSS4C, PSS4B, PSS5C, PSS6C, PSS7C
  - Overexcitation Limiter
  - Added OEL1B, OEL2C, OEL3C, OEL5C
  - Under Excitation Limiter
  - UEL2C, UEL
  - Stator Current Limiter
  - SCL1C, SCL2C
  - Plant Controller
  - Made more descriptive validation error messages for REPC\_A and REPC\_B when the model does not have a measurement branch specified. Unless this model is only controlling voltage, then a branch must be specified at which the Qbranch, Pbranch, and/or Ibranch is measured. If the branch is not specified when it is needed an error message will appear indicating why the measurement is needed.
  - Added a new plant controller named REPC\_B100 which is the same as REPC\_B but instead of allowing 50 generators to be referenced, you can have 100 generators.
  - REPC\_A and REPC\_B models would spit out validation errors when they were configured to measure a branch P, Q, or I and no branch was specified on which to perform this measurement. PowerWorld's hope was that by making this an error which prevented the running of transient stability, this would force the input data to be updated over time, however after a few years it has become clear that this error just confuses folks and the input data has not been updated. We have modified it so that this is now a warning and indicates to the user that all input of IBranch, QBranch, and PBranch will be assumed to be zero until the data is updated.
  - Added some error messages to the log when loading the REPC\_B models which reference either bus numbers that do not exist or generator/shunt objects by ID which do not exist in the case.
  - Added a warning message in Validation of transient stability if a REPC\_B model exists but has no Control Devices specified
  - Added transient stability validation checks on REPC\_A and REPC\_B about having PMax \>= Pmin and Qmax \>= Qmin.
  - Modified the default parameters for the REPC\_B model. Previously Pmin=0; Pmax=2.0; femax=1.0; femin=-1.0. This made sense for the REPC\_A model on which this is based where the output represented the Pref of a single generator. However, for REPC\_B, the value Pext represents the DEVIATION of power from the initial starting point and thus using Pmin=0 was inappropriate as a default. Devalut values have been changed to Pmin=-99; Pmax=99.0; femax=99.0; femin=-99.0.
  - Load Characteristics
  - Fields added to prevent using the models for loads that do not meet specified criteria: Filter Pmin, Filter Qmin, and Filter Vmin
  - Load Distribution Equivalent
  - *XFMinkV* field added to indicate the minimum nominal kV at which a distribution equivalent will include the transformer. If set to 0 the global option will be used.
  - Load Distributed Generation
  - Added support for a new Load Distributed Generation model DGDER\_A. This is the same model as the machine model DER\_A, however it is instead applied to the Distributed Generation portion of the load record.
  - Load Relay
  - Added the ability to read and implement the LSDT3A model which uses a separate PickupValue as compared to the Setpoint value.
  - Line Relay
  - Modified the interpretation of Direct parameter of the LOCTI, TIOCR1, and TIOCRS over-current models. Previously it only had options 0 and 1 below. Option 2 has been added. 0 - means no directional element 1 - means directional element AND Direction will be based upon current leaving the FROM end of the branch 2 - means directional element AND Direction will be based upon current leaving the TO end of the branch
  - Generator Relay
  - Modified the LHFRT model so that when obtaining the frequency measurement at the bus, if the voltage is below the "Minimum PU voltage for relay frequency measurement", then the frequency is treated as at nominal
  - Added a new generator relay model called GP3 which was developed in the NERC SAMS committee.
  - DC Line Model
  - Added support to CHVDC2 to use the parameters which attempt to emulate commutation failure.
  - Switched Shunt
  - Added ABBSVC1
  - Added MSS2
  - Added MSS1
  - Added the check for the Xc value on svsmo1,2 and 3 to give a warning during validation if the value on the transient model is different from the power flow.
  - Transient Plots
  - Added the requested ability to add the case name into the plot name when in auto save. If the option is checked then the name will have the following format: *ContingencyName\_PlotName\_CaseName.jpg*. Otherwise it will be naming the plot as before.
  - Modified the Plot Designer portion of the Transient Stability and PV Curve tool dialogs so that list of plots, subplots, and vertical axis groups will show more meaningful captions for Subplots and Vertical Axis Groups. Previously they were identified only by number. Now, Subplots and Vertical Axis Groups will show captions based on the following priority. 1. TitleCaption if specified 2. FooterCaption if specified (applies only to Subplot) 3. If it contains only one plot series, it will show the same header as that plot series 4. If all plot series it contains have the same field then it will show the field 5. If all plot series it contains have the same object then it will show the object identifier 6. If all else fails it will revert back to the number
  - Added ability to specify the Font Size on the plot definition as follows Vertical Axis Group Labels SubPlot Horizontal Axis Labels SubPlot Legend Labels
  - If choosing to *Auto-Save an Image File of the Plot* and the data is not selected to be stored to either the RAM or hard drive, after the plot file is generated the data will be deleted.
  - Transient Results
  - Added the ability to filter transient result events table from Object type.
  - Added VFE of ESAC8b\_PTI into the State Other Fields.
  - Added substation field for average ROCOF.
  - Added new Branch field for storing results called *Minimum Profile Vpu*. This field calculates the minimum voltage along the length of the series R and X of a branch. Typically this value is at one of the terminal buses, but it can sometimes end up between the two buses. It is possible for that voltage to approach zero even when both terminals are not zero. This is an indication of the system going out of step. One can monitor this branch field for an indication of the system going out of step.
  - Added VFE of ESAC8B\_GE into the State Other Fields.
  - Added result storage of Area ACE value
  - [Transient Stability File Format Support](36-transient-stability-overview-and-data-part2.md#data-from-external-files)
  - Added ability to load a OTGD file that represent transient stability contingencies.
  - When reading a REEC\_B record from a DYD file we expect to see 30 input parameters after the colon. This record does not support the mva=12.34 syntax as other records sometimes do, however sometimes we see DYD records which start with the mva=12.34 syntax followed by 29 parameters. In this situation it is reasonable to assume that this first parameter should have instead just been 12.34. We have added special processing of the REEC\_B record to support this with a warning message written to the log to indicate this has been assumed. Previously we would have just ignored this record completely and reported an error.
  - When reading a DYD file, modified parsing of the LSDT2 model to allow as few as 5 input parameters to be specified with all subsequent parameters assumed as 0.
  - When reading a DYD file, modified parsing of the EWTGFC model so that the last 7 parameters are optional and if omitted will assume the following values: Xc=0, Kqd-0, Tlpqd=0, Xdq=0, Vermn=-0.1, Vermx=0.1, Vfrz=0.7.
  - Added ability to read/write the CHVDC2 model to and from the DYD file.
  - Modified reading the TIOCRS record from DYD file so that any paramter after A can be omitted and a value of zero will be assumed for the parameter
  - Modified reading of LOCTI record from DYD file so that any parameter after Tm1 can be omitted and a value of zero will be assumed for the parameter
  - When reading and writing a DYD file added ability to translate the distrel/zonedef/blindef models into a DistRelay model.
  - Added new right-click option under Save As on a case information displays for Generator, Shunt, LineShunt, and Branch objects, as well as any transient stability dynamic model object for one of these 4 objects. The new option says "DYD Format (only models of selected records)" and will store a DYD file snippet for the objects and models selected. Also include support for some Load objects and models as appropriate.
  - Added support when reading the REPC\_B model from a DYD file so that we interpret 2 character ID strings in the parameter list as the IDs of generators or SVCs appropriatly and also write them out as 2 character IDs. Previously these values were required to be numbers which were rounded to the neared integer. Also added special support when reading these values so that number strings such as 2.0 and 34.0 will be interpreted as the ID string 2 and 34.
  - Modified Simulator to read and write CMPLDWG records from and to a DYD file. These are read into Simulator and the final 15 parameters for the DGPV model are striped off and handled separately. The first 4 of these parameters are used to populate the DistMW and DistMvar parameters of the load record in Simulator, but only if the existing load record has zeros for both those values. Then the final 11 parameters are used to create (or modify) a Load Distributed Generation model (DGPV) at the particular load record. When writing out a DYD file, if a CMPLDW model is being written to the DYD, Simulator will check to see if there is an active DGPV Load Distributed Generation model being used by the load. If there is, then the model will be written as a CMPLDWG instead and the appropriate final 15 parameters will be written.
  - While loading in a DYR file, GGOV1DU governor user-model is converted to GGOV1, and the last two parameters are ignored.
  - When loading in WECC SWT files, the case will be started off with 1.0 second of no disturbance. ALL time values you input will have 60 cycles added to them.
  - When reading a DYR file, the USRMDL REPCTAU1 is now mapped to REPCTA1
  - Added ability to save transient results shown in the Results from RAM case information displays directly to the Comtrade formats.
  - Added the ability to read and write for GE PSLF for up to 4 generators for the TS model CCOMP4.
  - When reading a DYR file and finding several USRMDL govenor models that are identical to an existing governor model except for the addition of a deadband, modified to simply read this governor as the existing governor model ignoring the deadband. In Version 21, we will read and translate to new governors, but for now simply convert to a governor without a deadband. This includes the following GASTWDDU --\> GASTWD HYGOVDU --\> HYGOV IEESGODU --\> IEESGO IEEEG1SDU --\> IEEEG1 WPIDHYDU --\> WPIDHY
  - When reading a DYR file and finding a USAC6AU as a USRMDL exciter, modified to translate to the existing ESAC6A. This model is idential to the ESAC6A, except for the implementation of the non-windup limit on the Lead-Lag block of the (1+sTc)/(1+sTb). Simulator Version 21 will include a new AC6A model that implements the lead-lag block non-windup limit using the method described in the IEEE 421.5 standard, but for now in Version 20 we will just translate this model to the existings ESAC6A.
  - When reading a DYR file and finding a HYGOV4 as a USRMDL, modified to translate this to the existing HYGOV4 model.
  - When reading a DYR file and finding several USRMDL govenor models that are identical to an existing governor model except for the addition of a deadband and Trate, modified to simply read this governor as the existing governor model ignoring the deadband. In Version 21, we will read and translate to new governors that include the deadband and Trate, but for now simply convert to a governor without a deadband. This includes the following: GGOV1DU --\> GGOV1D, GASTWDDU --\> GASTWDD, HYGOVDU --\> HYGOVD, IEESGODU --\> IEESGOD, IEEEG1SDU --\> IEEEG1D, IEEEG1CDU --\> IEEEG1D, WPIDHYDU --\> WPIDHYD, DEGOV1DU --\> DEGOV1D, GAST2ADU --\> GAST2AD, GASTDU --\> GASTD, HYGOV2DU --\> HYGOV2D, IEEEG3DU --\> IEEEG3D, PIDGOVDU --\> PIDGOVD, TGOV1DU --\> TGOV1D, TGOV3DU --\> TGOV3D, and WESGOVDU --\> WESGOVD
  - Transient Stability Contingency Definitions
  - Added support when auto-inserting transient stability fault definitions to use the new SelfClear feature of a fault.
  - Added a flag SELFCLEAR at the end of a TSContingencyElement Action String for a fault. Normally when a fault point is isolated by opening branches in the system, the fault will NOT automatically clear itself and thus if lines are closed back in the fault will remain in place. When specifying SELFCLEAR, then when a fault point becomes isolated it will automatically clear itself at the same moment.
  - Transient Stability User Dialogs and Auxiliary File Support
  - Modified the Transient Stability tab on Load dialog to always show the "Terminal and State Values" tab so that the user knows it's available. Previously this tab would be hidden on the load dialog if the transient stability simulation had not been initialized. Now it will always appear, but if the simulation is not initialized then it will show all empty values.
  - Added the ability to rename the Device ID from a relay GUI dialog. It will only rename the Device ID if the new Device ID does not exists. If the Device ID already exists then the following message will appear: A Device ID already exists at from/to end (Line Name). Please Modify that particular (Relay Name)relay.
  - Added ability to delete all jpgs in the TS contour toolbar subdirectory. This is just a button on the dialog used to specify saving the TS contour images.
  - Added ability to right-click on the transient stability event case information display and show the dialog associated with the power system object refered to by this action.
  - Added additional concise variable names for transient stability models. Added concise variable names for following objecttypes TSPlotSeries, TSSubPlot, TSPlotVertAxisGroup, TSPlot, TSLimitMonitor, and Transient\_Options.
  - Added fields on a Bus, Area, Zone and Owner object to show the presently assigned Load Distributed Generation model name.
  - Added a new Gen object field called *TSGovMWCap* which returns the MW Base of the active dynamic governor model if available. If either no governer is active or the active governor does not have a MW Base parameter, then this field will appear as blank.
  - Modified how the list of available transient stability model types is displayed when choosing to only "Show Models Supported By" a particular software tool. Starting in Version 20 we would also show models that can be translated to that software tool. This patch changes it so it only shows models natively supported in that tool.
  - Added a new option to Clear Time Values from RAM for ALL the contingencies. Now there is a drop down menu in the Clear Time Values from RAM button with two options: -Clear Time Values from RAM for Active Contingency -Clear Time Values from RAM for ALL Contingencies
  - When in Difference Case Mode of either "Change" or "Diff", then all string grids showing transient stability models will only show stability models which have a modified parameter (Modified = YES or blank).
  - On the Result from RAM section of the Transient Stability Dialog, modified the "Clear Min/Max Values, Summary, Evenst, and/or Solution Details from RAM" button so that the dialog which appears gives you the option to either clear results for the Active Contingency, or for ALL Contingencies.  
  - User Interface Dialogs
  - Added two new buttons under the Restore\> dropdown on the Tools ribbon tab called *Store User State* and *Restore User State*. These provide button access to same functionality as available in the script commands StoreState; and RestoreState(USER);
  - Separating *Save* and *Save To Aux* button on the bus, branch, load, gen, shunt, and lineshunt dialogs. Clicking the Save to AUX will now store the fields specified as part of the built-in *Network Model* Auxiliary File Export Format Description.
  - Changed the hints that appear for the MVA Convergence Tolerance and the AGC tolerance to reference the fields that are in the unit of MVA (instead of the old fields which were in units of per unit)
  - When using the *Save to Aux* button on bus, switched shunt, generator, branch, line shunt, and load dialogs save using fields that are the same as default Network Model fields with the Aux Export Description. When saving switched shunts use appropriate fields if the shunt is allowed to be on control, i.e. control mode \<\> Bus Shunt. When saving transformers save using appropriate transformer control fields.
  - Added a button to the Geography tab of the Substation dialog which copies the Lat/Long information to the system clipboard. Also added this feature to the menu when right-clicking on a substation object on a oneline diagram.
  - Modified the Model Expression dialog so that the edit boxes that show the information about the variables show more concise text descriptions. They will now show information about what object each variable involves by showing either the primary, secondary, or label identifier depending on the user preference in the Simulator Options under Case Information. In addition they will show a hover hint that gives information on labels, primary, and secondary keys, along with the complete field description for the variable.
  - Modified the Generator Information dialog so that if the check-box *Use Capability Curve* is checked then the Min Mvar and Max Mvar edit boxes can not be edited. This is the same treatment as those fields on the case information displays which do not allow editing of those fields if they are calculated from the capability curves.
  - Added the bus label as an informational field on the Renumber Buses dialog.
  - Added scrollbars to the Memo that can be entered on object dialogs.

---

<a id="whats-new-4"></a>

## What's New

*Source: [`Content/MainDocumentation_HTML/Whats_New_v23.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Whats_New_v23.htm)*

PowerWorld Simulator Version 23 contains a number of major new features and hundreds of smaller enhancements designed to improve the performance and convenience of the package.

The following is a list of the most noticeable changes in Simulator Version 23.

  - Incorporation of [Weather-Related](28-weather.md#weather-related-features) Data
      - [Weather-dependent limits](28-weather.md#weather-dependent-limits) for branches and generators
      - Time Step Simulation using historic weather data
      - [Power Flow Weather (PFW) generator models](28-weather.md#weather-related-models-and-information-dialog)
  - Transient Stability
      - Automatically create plots that have a violation based on Transient Limit Monitor or Transient Limit Logic
      - Continued expansion of models
  - [Voltage Conditioning Tool](10-power-flow-solution-and-options-part3.md#voltage-conditioning-dialog) allows modifying power flow case to meet voltage schedules at buses or substations
  - [Spatial View Onelines](08-view-case-data-tools.md#spatial-view-oneline) to automatically draw bus and substation onelines using geographic information
  - Continued support for reading and writing [case data formats](03-cases-files-and-formats.md#case-formats)

To see a list of what was new in previous Simulator Versions choose links for [Simulator 22](#whats-new-2), [Simulator 21](#whats-new-3), [Simulator 20](#whats-new), and [Simulator 19](#whats-new-1).

What follows is a more detailed list of the changes in Simulator Version 23.

  - [Auxiliary Files, Display Auxiliary Files and Script Commands](03-cases-files-and-formats.md#auxiliary-file-format-aux)

      - For syntax and usage details, please refer to the latest Auxiliary File Format PDF, available at:

        [https://www.powerworld.com/knowledge-base/auxiliary-file-format-10](https://www.powerworld.com/WebHelp/knowledge-base/auxiliary-file-format-10)

      - In an aux file when using the special string "\&objecttype 'key fields' variablename" the key fields and variablename can now be specified using the '@variablename' syntax that will lookup the value to use from the specified field. An example: SetData(Load, \[CustomFloat\], \["\&Zone '@ZoneNumber' LoadMW"\], All). This will set the CustomFloat field for every load to the MW value of that field’s zone.

      - SetData and CreateData script commands now support referencing a model field using the "\&Objecttype 'key fields' concisename:digits:decimals" syntax when specifying the values of key fields used for identifying objects. Previously this syntax was only supported when specifying the values of non-key fields. This could be used for functionality that opens the branch with the highest percent loading in the case. Create a calculated field that returns the maximum loading and then apply this to the PWCaseInformationObject. Use the ObjectID field for identification and the CalcFieldExtra to return this string. Example: SetData(Branch, \[ObjectID, Status\], \["\&PWCaseInformation 'CalcFieldExtra:HighestLoading'", "Open"\]);

      - Added ability to write ContourPixel objects out to an AXD file.

      - Added support for writing ContourDataPoint objects to AXD files.

      - The following Script Commands were added:

          - TSRunResultAnalyzer(ContingencyName);

          - TSDisableMachineModelNonZeroDerivative(DerivativeThreshold);

          - TemperatureLimitsBranchUpdate(RatingSetPrecedence, NormalRatingSet, CTGRatingSet);

          - WeatherLimitsGenUpdate(UpdateMax, UpdateMin);

          - VoltageConditioning;

          - CTGVerifyIteratedLinearActions("filename");

          - RotateBusAnglesInIsland(\[BUS num\], Value);

          - SaveDataUsingBuiltInAUXFormat("filename", filetype, \[List\_of\_built\_ins\], ModelToUse);

          - CreateNewAreasFromIslands;

          - ATCWriteScenarioMinMax(...);

          - TSInitialize(CheckAlreadyInitialized);

          - TSValidate;

          - GICTimeVaryingElectricFieldsDeleteAllTimes;

          - CTGPrimaryAutoInsert;

          - TSTransferStateToPowerFlow;

          - ExportBusView("filename", "bus key", ImageType, Width, Height, \[ExportOptions\]);

          - CTGSort(\[SortFieldList\]);

      - The following Script Commands were modified:

          - Allow multiple injection groups to be selected for injection changes in the LineLoadingReplicatorCalculate script command. To specify more than one injection group, just include a comma delimited list of the injection group names instead of a single injection group within the bracketed injection group parameter.

          - Modified CalculateLossSense to include the new loss references options for AreaSALossReference and IslandLossReference: CalculateLossSense(FunctionType,AreaSALossReference,IslandLossReference).

          - Modified the script command GICLoad3DEfield to include an option to setup the Time-VaryingSeries on Load. The script now looks like this: GICLoad3DEfield(FileType, CoarseFile, SetupTVSOnLoad); SetupTVSOnLoad is optional and is a YES/NO option and default is false.

          - TSClearAllModels script command will now delete Load Distribution Equivalents.

          - The filter for ATCCreateContingentInterfaces is now optional, and by default all transfer limiters will be used.

  - [Available Transfer Capability](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)

      - On the ATC Dialog allow using an aux file to set the option to "Analyze Multiple Scenarios" rather than always forcing the option to be checked if multiple scenarios are defined.

      - At end of ATC run, TransferLimiters will be sorted from low to high transfer limit, contingency with any base case limiters coming first, and then limiting element. Previously the limiters were not sorted at the end of the calculations, which could result in the limiters being out of order if using the iterated methods. Limiters were being sorted when loading from an AUX or PWB, and this will make the result order consistent immediately after a run and when loading from file.

      - In ATC when iterating on all limiters to determine the individual limiters to iterate on when using one of the iterated methods, the analysis will stop if a reserve limit is found because there are no available participation points for calculating the linear step size. Previously the analysis would continue on to iterating on individual limiters, but the results would be the same for all limiters because no additional stepsize could be found because no available participation points would exist for any individual limiters.

      - Added button on ATC dialog to Store Initial State.

      - Added new feature on ATC dialog to report the minimum or maximum limiter based on either the Transfer Limit or one of the ATC Extra Monitor fields and to group the results by particular ATC Scenarios and include particular scenarios in the calculation.

      - Added ATCWriteScenarioMinMax script command that will save a file to report the minimum or maximum limiter based on either the Transfer Limit or one of the ATC Extra Monitor fields and to group the results by particular ATC Scenarios and include particular scenarios in the calculation.

      - Prior to running any ATC related functionality any islands created because of the option to "dynamically add/remove slack buses as topology is changed" will become permanent islands. This is to prevent the islands from being removed if a full contingency solution is done and the "dynamically add/remove..." option is not used. It is assumed that the topology that exists prior to any ATC analysis is the desired topology.

      - Added new field with TransferLimiter objects called RemedialActionApplied. This field will indicate if at least one remedial action element was applied for the contingency. This field is only valid for IterativelyFound results of YES, NO, or blank.

      - When creating contingent interfaces from transfer limiters, base case limiters will now be included, which will create interfaces without contingencies.

  - [Case Information Displays](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays)

      - Many more options to Plot Columns to quickly make great looking graphs for reports, presentations, and papers

      - Improved row and column metrics including metrics for strings

      - Added generator fields for MWRange, MWRangeUp, and MWRangeDown

      - Added CasePath as a field with PWCaseInformation

      - Added Bus and Bus Group (Area, Zone, Substation, Super Area, and Balancing Authority) fields to show the generator MW range (total, up, down). There are three options: either 1) the AGCable generators that are online, 2) all online generators, 3) all generators.

      - Added new fields for objects related to labels as follows. LabelCount = integer showing the number of labels specified for the object LabelsNotPrimary = a comma-delimited list of labels excluding the primary label.

      - Added fields to show switched shunt values aggregated at the bus and bus group level (Area, Zone, Substation, Super Area, and Balancing Authority).

      - IsLikelyStarBus field for bus to indicate if the bus is set to be the star bus of a three-winding transformer or if its topology makes it likely to be a star bus.

      - Added generator Step-Up Transformer Topology fields to show information about any explicitly modeled generator step-up transformers

      - Added special right-click option at the top of the case information local menu to "Follow link in browser". This will only be an option if the first 7 characters of the cell clicked on are http:// or if the first 8 characters are https://. If those are not the first 7 or 8 characters then the option is not visible. This will work on any cell on a case information display.

      - Added bus group (Area, Zone, Substation, Super Area, and Balancing Authority) fields to show the generator MW output by fuel type, max MW output for all fuel types, and max MW output for online generators by fuel type.

      - Added a new field for Tieline objects to show the bus number of the metered bus.

      - Added new to show Latitude, Longitude, Latitude String, and Longitude String for several objects including: Area, Zone, Owner, InjectionGroup, Contingency, RemedialAction, and Interface. Fields will return the average latitude/longitude of the objects contained inside them.

      - Modified how the Column Plot works with respect to columns with bad data (i.e., not enough data to plot). Previously the user was prompted about each column, which was overkill if there were more than a few columns. Now the user has an option to ignore the columns, just getting a summary of the total at the end. Having bad data is actually quite common with weather information.

      - Added several new fields for showing geographic information for result objects such as ViolationCTG, LimitViol, TSResultEvent, TSLimitViolation, TSResultAnalysisSignal, TSResultAnalysisViolation Fields will show values for Geography-related fields such as Branch LineLength, and various Latitude/Longitude fields for objects for which results are being reported.

      - With PWCaseInformation object type added CountContingency field to show the total number of defined contingencies.

      - Added PowerFactor as a generator field.

      - Added generator fields to provide information about the reactive capability curve for a generator: Maximum of Mvar Max, Maximum of Mvar Min, Minimum of Mvar Max, Minimum of Mvar Min, MW Max, and MW Min.

      - Changes to the plot columns functionality to implement 1) so the first selected column always starts with the black color \[this avoids the annoying issue of getting a yellow initial curve\], and 2) provide an option to only plot every nth point to make it easier to get a quick plot if there are lots of values.

      - User choices about hiding/showing Case Info Toolbar, Searchbar, and Filterbar are stored as part of the Windows registry settings.

  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)

      - Auto Insert option for Primary Contingencies was added to the CTG Combo Analysis tool

      - When reading a ContingencyElement from AUX files and the Object referred to by the ContingencyElement is not found, a special "Unlinked" ContingencyElement is created and can be viewed in the user interface. For users not familiar with this feature however a warning message in the log is a helpful reminder to go look for these unlinked elements. These log messages have been added.

      - Added log message when a ContingencyElement becomes unlinked because the object to which it was referencing was deleted.

      - Advanced filtering of rows is now supported for Contingency Violation Matrices.

      - When sorting the Contingency object type by the count of any type of violation, any contingencies that have been processed and are Unsolved will be treated as the highest value in the sort order so that when sorting in descending order they will always appear at the top. They will always appear at the bottom when sorting in ascending order.

      - The contingency element identifier for a branch that is part of a multi-section line will no longer contain the section number for OPEN or CLOSE actions. This section number with OPEN and CLOSE actions has always been ignored when loading an aux file and this resulted in the actions appearing different if comparing based on the identifying string. For OPEN and CLOSE actions, the section number does not matter because the action is applied to all sections in the multi-section line.

      - When using the auto-insert contingencies to insert by "bus groupings", we will now name the new contingencies created by the buses that remained connected but are on the edge of the grouping of buses being isolated. Previously we named the contigency after the buses that were on the edge but inside the group being isolated.

      - Prior to running any contingency analysis or combo contingency analysis related functionality any islands created because of the option to "dynamically add/remove slack buses as topology is changed" will become permanent islands. This is to prevent the islands from being removed if a full contingency solution is done and the "dynamically add/remove..." option is not used. It is assumed that the topology that exists prior to any contingency analysis is the desired topology.

      - Added CriteriaCheckOnce field with RemedialActionElements. Set this to YES if the Model Criteria should only be checked once during the process of applying Remedial Action Elements in response to contingency actions (model criteria is evaluated with TOPOLOGYCHECK, POSTCHECK, or SOLUTIONFAIL status). If the criteria is not met, this action will not be implemented and the criteria will not be evaluated again. The Persistent field is ignored when this is set to YES. The action will not be implemented and the Model Criteria will not be evaluated again for a Model Criteria that is met but the Time Delay is greater than the Time Delays of other actions whose Model Criterias are also met. This option has no impact if the Model Criteria is not defined.

      - Added a "Selected" filtering option to the result objects in the Contingency Combination Analysis dialog.

      - Added new field with Contingency object type called RemedialActionApplied that indicates if at least one remedial action element was implemented for the contingency. Valid entries are Yes, No, and Blank. If left blank then no information is known about whether or not a remedial action element was implemented.

      - Added new field with ContingencyPrimary and CTGComboResults objects called RemedialActionApplied. This field will indicate if at least one remedial action element was applied for a Primary contingency for the ContingencyPrimary object. With the CTGComboResults object this field indicates if at least one remedial action element was applied after the secondary contingency was applied when reported with the CTGComboResults object.

      - Added local menu options on Custom Monitor case information display found on the Contingency Analysis dialog to Save As \> Auxiliary File (all related info) and Save As \> Auxiliary File (all related/only selected records). These options will save the custom monitors along with any Advanced Filters and other dependent objects needed to define the monitors.

      - Added a new option on the Other menu in Contingency Analysis dialog under Other\\Manage Contingency Definitions\\Delete Contingencies with Identical Actions. This will delete a Contingency object if it contains the identical list of ContingencyElements as another contingency. The contingency with a Name that is first in an alphabetic sort will be maintained.

      - Added script command CTGSort(\[SortFieldList\]) that will sort the list of contingencies in the data structure that stores the contingencies internally in Simulator. This is different than sorting the contingencies in a case information display. Using this command is useful when using the options to Join Active Contingencies and a sorted ordered is desired when forming new contingencies. The \[SortFieldList\] parameter is optional and if not specified the list will be sorted in ascending order by contingency name. The SortFieldList parameter is in the format \[variablename1:+:0, variablename2:-:1\] that is a list of fields by which the list should be sorted, the sort order, and the case sensitivity (ABS for numbers).

      - Added new option to the CTG\_AutoInsert\_Options called FilterOnlyLineXFSeries. Choosing this option will cause the auto-insert contingencies tool to only insert branches that have BranchDeviceType = Line, Transformer, or Series Cap. This option also exists as a checkbox on the Auto Insert Contingencies dialog.

  - [Difference Case](08-view-case-data-tools.md#difference-case)

      - Added Difference Case support for GICXFormers.

      - Added Difference Case support for WeatherStation.

      - Modified to remove trailing zeros when showing comparisons of Present|Base on Transient Stability Models.

      - Added support in the Difference Case tool for the DistributionEquivalent transient models.

  - [Distributed Computing](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)

      - Added Verify Computers button on dialogs for tools that use distributed computing.

      - When running Distributed TS, if a contingency does not solve, the ReasonNotSolved is added to the Simulator log.

  - [Fault Analysis](27-fault-analysis.md#fault-analysis)

      - Greatly increased the speed of calculating bus faults on a long list of faults.

  - File Formats

      - PSS/E RAW file generator records will be written out with WMOD = 1 when the FuelType =SUN (Solar) OR Unit Type = PV (Photovoltaic) within Simulator

      - PSS/E RAW file version 35 support

      - PSLF EPC version 23 support

      - When reading an EPC file, the ID field for Breaker data will be used as the circuit ID for the breaker if the length of this field is 1 or 2. If the ID field is blank or greater than two characters, the circuit ID will be dynamically assigned. The ID field will always populate the EMS ID field in Simulator. When writing an EPC file, the ID field for Breaker data will be written using the EMS ID field if this is not blank. If this is blank the circuit ID field will populate the ID field in the EPC.

      - When writing an EPC file, the brktype field will be written based on the Branch Device Type specified in Simulator. When writing a Disconnect the EMS CBTyp field in Simulator will be used if it is not blank. The brktype field in an EPC file has more options for different types of disconnects that are only identfied as Disconnects within Simulator and the EMS CBTyp field might contain a more specific type.

      - When reading a contingency OTG file, if there was a BUS or a SECDD command it was adding a contingency element that was skipped because it was added incorrectly. Now the bus command is going to be added as an unlinked element event so the user will know that we do not support that command. The SECDD command will add the correct branch contingency element event and will be solved (not skipped) during the contingency analysis run.

      - Added Primary field to specify which label specification should be used as the primary label with the custom Areva label definitions used with hdbexport files. This will be assigned when loading hdbexport files.

      - Modified the feature to "Save Known Fields in HDB Pattern File" so that it now write 4 files c:\\FilePath\\FileName.txt : list of object/fields for exporting a solved case c:\\FilePath\\FileNameCTG.txt : list of object/fields for exporting contingency definitions c:\\FilePath\\FileNameRAS.txt : list of object/fields for exporting the RAS definitions c:\\FilePath\\FileNameHdbexport.txt : Text file describing how to call the hdbexport command

      - Modified reading of RAW file records for Bus, Gen, Load, Line and Transformer so that if an extra field is at the end of a record which is not expected, then we will try to read this in as a memo or label.

      - Added ability to read/write the FuelType from the EPC file format. The integer codes in the EPC format are based on the WECC Data Preparation manual.

      - Added AREVAHDB CSV files to the file types that can be opened from the command line

      - Modified to write out EPC files with up to 32 characters for the substation names. An older version of PSLF only supported 12 characters.

      - Various modifications when loading an Areva hdbexport file and how fields are interpreted.

      - When reading a RAW file set the 'Default' Limit Set for contingency voltage rating set to B to match how bus specific limits are loaded; the Normal bus ratings are put in rating set A and the Contingency bus ratings are put in rating set B.

      - When writing out Zone data to RAW files, PowerWorld was truncating the zone names to 8 characters. PowerWorld will now truncate to 12 characters instead to match the limitation in the RAW file format.

      - Modified reading of CP records from hdbexport CSV files when VTARGET is not defined. We now set the RegHigh/RegLow = 1.4/0.6 for shunts and also set AutoControl = NO.

      - Added 'Load Contingencies Complete' and 'Load RAS Complete' log messages at the end of the hdbexport contingency and RAS import routines.

      - Can load GMD data that is part of an EPC file.

      - Added ability to read ND outages from the CTGL records of the Areva HDBEXPORT CSV files for contingency definitions.

      - When reading transformer records in the EPC file will now recognize a negative "type" as an indication that control on this device is disabled.

      - When writing out transformers to an EPC file, if transformer is Fixed we will now always write type = 1. PowerWorld has a separate field indicating if a transformer's control is enabled and if it's disabled we write a negative sign on the type. However in EPC file type=1 means there is no control at all, so writing a -1 is strange as it means the transformer's control is disabled, but it has no control anyway. To avoid confusion, we just write a 1 instead.

  - General

      - Areas and zones for Area/Zone/Owner/DataMaintainer filters now allow a nominal kV range to be specified. The nominal kV of objects must be in this range to meet the filter.

      - Voltage Conditioning tool allows modifying power flow case to meet voltage schedules at buses or substations

      - Weather-dependent limits for branches and generators

      - Added to the Quick Power Flow list local menu support for bus and substation views, and bus and substation spatial views.

      - Added Length function that can be used with Custom Expressions and Model Expressions. This function takes a string as a parameter and returns an integer.

      - Added a new dialog to allow loading supplemental data from an external CSV. The new dialog allows the user to choose which values to read from the CSV, and what supplemental data fields to assign them to.

      - Modified the Long Line Voltage Profile tool to also show the Current \[Amp\] profile across the length of the line as well.

      - Added saving the shortcut definitions to the registry when the shortcuts dialog is closed

      - Modified option objects in the list of ObjectTypes so that they appear under the Options and Options By Value folder and then also under the respective tool if appropriate. For example the Contingency Options will appear under the folder Contingency\\Options.

      - Modified the LimitSet object so that it can have CustomFloat, CustomInteger, CustomString field specified with it. Also modified so that it can support labels

      - Added to the General File Browser the newer \*.docx, \*.xlsx and \*.pptx formats. Group these together with similar types: DOC|DOCX, XLS|XLSX, and PPT|PPTX. Allow the pipe symbol, |, to be used to group a list of extensions together. This can be used when defining custom file extensions.

  - [GIC](47-geomagnetically-induced-currents.md#gic-analysis)

      - Added support for EMP E1 load impact modeling.

      - Added Bus GIC field to show the GIC related losses allocated to the bus. These include the losses from the implicit GSUs and the other transformers. To avoid double counting the explicit transformer losses, the losses are allocated to the transformer's from bus only.

      - GIC electric field magnitude and angle are now shown on the substation information dialog.

      - GIC related support in system states so that the state restores correctly when GIC changes have been made.

      - On GICs added the ability to stretch the b3d data points.

      - The code that calculates the substation and line electric field values for the non-uniform fields is more efficient. This should make the Setup Time Varying Series function faster (which is called whenever a b3d file is loaded).

      - For B3D files the comments can now be edited and saved in a new b3d file.

      - GIC ribbon group on the Add Ons ribbon tab now has option to Load and Save GMD even if the user does not have the GIC add-on.

      - Modified the script command GICLoad3DEfield to include an option to setup the Time-VaryingSeries on Load. The script now looks like this: GICLoad3DEfield(FileType, CoarseFile, SetupTVSOnLoad); SetupTVSOnLoad is not optional and is a YES/NO option and default is false.

      - Added script command to clear time varying electric field inputs: GICTimeVaryingElectricFieldsDeleteAllTimes. This is equivalent to clicking 'Clear All Time Points' on the time varying electric field input tab.

  - [Oneline Diagrams](15-using-onelines-tools-and-options.md#oneline-diagram-overview)

      - Spatial View Onelines for automatically creating geographic onelines for buses and substations

      - KML Import now reads lines and points that are not in the PowerWorld format. Made the option when importing a KML file to add the Points as Ellipse, Squares, or Triangles. This option is only used when loading a KML file that is not in the PowerWorld format.

      - Added GIC field to Geographic Data View Line Summary Objects.

      - Added support for Geographic Data View two field rectangle objects. These are similar to the kites, except using rectangles. The objection are either top and bottom values, or left and right values.

      - Added fields to the Case Information Memo Field oneline object to allow for a prefix and/or a suffix.

      - Added Geographic Data View support for weather objects.

      - Increased the number of decimal places to 6 when showing the x,y values in the zoom dialog in lon, lat values.

      - Added direct support for GIC flow visualization with Animated Flows options. Dual display of MWs and GICs is also supported.

      - Added support for additional Geographic Data View display lines.

      - When right-clicking on multiple display objects that are on top of each other, the user will be given the choice of which object is selected. Added Oneline Visualization option "Edit Mode Right-Click Prompt for Objects at Same Location" that will allow you to disable the prompt that allows you to choose from a list of multiple objects if right-clicking on a oneline where there are multiple display objects on top of each other. This option only works in edit mode and in run mode you will always be prompted to choose from a list. This option is only stored in the registry and cannot be modified through an aux file.

      - Added a fix to the issue of contours bleeding into the background (usually water) of a oneline. The contour option to "Do Not Show Contour on Background and Borders" prevents the bleeding. This option is stored with the Oneline Display Options but is also available on the contour dialog.

      - Added new features under the Auto Insert drop-down on the Draw tab to automatically insert Area, Zone, Owner, and InjectionGroup display objects on a oneline diagram. The locations will be determined by look at the new Latitude/Longitude values for these objects now available on the case information displays.

      - Added a new right-click option, Open Model Explorer, on oneline display objects to bring up the model explorer and navigate to the object.

      - Added a right-click option, Show Data View, on oneline display objects to open the data view for the object.

      - Added new contouring color maps.

      - Modified the Select By Criteria feature for oneline objects so it can use the Area/Zone/Owner/DataMaintainer filtering.

      - Added an option in the Edit Mode right Click menu for display object to move objects to Geographical Coordinates. The option works with Buses, Gens, Loads, Switched Shunts and Substations. The Gen, Loads and Switched Shunts will look for the terminal Bus Geographical Information. If the Bus, Terminal Gen Bus, Terminal Load Bus or Terminal Switched Shunt Bus do not have Geographical coordinates then it will look for the Substation Geographical Information (if the objects belongs to a Substation).

      - On the contour dialog, replaced the ComboBox dropdown for choosing a color map with a much nicer drop-down that open a foldered view of color maps along with a preview as you choose the color map.

      - Added a new contour method based on the nearest data point.

      - When defining filters for display objects, a device filter in the syntax of "\<DEVICE\>objecttype 'key1' 'key2' 'key3'" will now work when filtering the display object type by data objects of supported types. This means that a DisplayBus can be filtered by a particular Bus object as well as the other types of objects that are supported. This syntax was already supported by filtering a display object by its own type, i.e., DisplayBus by DisplayBus.

      - Cursor Contour Value on contour color key shows the value currently under the cursor.

      - Contour Value Metrics have been added to the contour color key.

      - Contour color key dialog has fields to update the size and position of the dialog.

      - Saved oneline views can store the contour color key location and size.

      - Background lines can optionally have arrows at either end of the line.

      - Added Geographic Data View option for Pruning to Only Contour Pruned Values.

      - Added option to Case Information Memo Field to show the simulation time with seconds

  - [Optimal Power Flow (OPF)](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview)

      - When choosing whether to enforce limits on an interface in the OPF solution, we ensure that at least one element of the interface is configured to be enforce limits and that at least one device belongs to an area which is on OPF control. This check was also considering the status on branches that were assigned as a BRANCHOPEN or BRANCHCLOSE event. We have modified so that the checking of status on BRANCHOPEN and BRANCHCLOSE devices is no longer considered.

  - [Powerflow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-theory)

      - PowerFlow Weather (PFW) generator models

      - When determining the Setpoint Voltage Tolerance to use with generators regulating voltage, only generators with an available AVR range can be used for selecting the tolerance. If no range is available the tolerance will be 0.

      - For cases with bad input data such that generators at the same bus have different voltage setpoints, PowerWorld would just take the last generator's setpoint value. This has been modified so it will take the setpoint of the generator with the largest (MvarMax - MvarMin) value instead.

  - [PV QV Curves](29-pv-and-qv-curves.md#powerworld-simulator-pvqv-overview)

      - When running a QV curve at a bus, SVCs that are remotely regulating that bus are now turned off control. SVCs should be treated the same as generators that are remotely regulating the curve bus and need to be turned off control to not conflict with the fictitious generator. When a contingency or base case cannot solve and the fictitious generator is used to try to make them solve, switched shunts and SVCs at the curve bus are now turned off control and SVCs that are remotely regulating the curve bus are turned off control. These need to be turned off so that they do not conflict with the voltage setpoint of the fictitious generator.

      - PV tool options are now stored with the PWB file so it no longer makes sense to initialize the tool with options based on the power flow solution. This was only being done with the option to enforce generator MW limits during injection group ramping, but it was causing confusion because it was overriding the option as it was set with the PVCurve\_Options object.

      - With plot definition, added feature when automatically determining the vertical axis scale to force the Minimum value to be greater than the Minimum specified. This allows the automatic scaling to ignore values that are zero for example. Also added similar feature to force the Maximum value to be less than the Maximum specified.

      - For a PlotSeries add two new options for a "Scale" and "Offset". When using these the Actual Value on the plot will be (y-Offset)\*Scale.

      - Prior to running PV or QV analysis any islands created because of the option to "dynamically add/remove slack buses as topology is changed" will become permanent islands. This is to prevent the islands from being removed if the "dynamically add/remove..." option is not used with different sets of options. It is assumed that the topology that exists prior to any PV or QV analysis is the desired topology.

      - Added new field with QVCurve objects called RemedialActionApplied. This field will indicate if at least one remedial action element was applied for the contingency.

      - Added new field with PWPVResultListContainer objects called RemedialActionApplied. This field will indicate if at least one remedial action element was applied for the contingency.

      - Added a readonly edit box on the Auto-Save Plot portion settings on the Plot Designer to show the folder location to which these files will be stored.

  - [Scheduled Actions](48-scheduled-actions.md#scheduled-actions-tool)

      - New format for reading outages called the "PowerWorld Outage CSV File"

  - Sensitivity Analysis

      - Loss Sensitivity calculation now has options for which Loss Reference to use when the Loss Function is Island, Area, or Super Area.

      - Modified the bus fields shown by default of the Self-Sensitivity tab of the Sensitivities\\Flows and Voltage dialog. Negative Reactance Lines: this will now return NO if a neighbor branch has a negative X but this branch connects to the internal star bus of the equivalent of a three-winding transformer. The Star bus itself will still say YES, but the terminals of the three-winding transformer will return NO. Likely Alternative Solution Fields: These fields will now return YES if a terminal of a three-winding transformer has a negative dV/dQ even if the connection to the star bus has a negative X.

  - [Time Step Simulation](26-time-step-simulation-part1.md#time-step-simulation)

      - Greatly improved including aux file support

      - Ability to store and restore the full power system "state" making it easier to see results, resolve time points, and make visualizations including movies

      - Integrated support with weather modeling

      - There is now an option to change (shift) all the time points. This is an enhancement to the previous functionality that only allowed changing the time at a single timepoint. The old and new functionality is still available in the Time Step right-click menu by selecting Time Point Records, Change Timepoint Time.

      - In the time domain simulation added new feature to allow time to run backwards. This is useful in the common situation in which a time series is initialized from a time that does not correspond to the starting time. For example, a peak case might be used to initialize at say 4pm, then time can be run backward.

      - Added a new Interpolate Timepoints Options page to make it easy to create new interpolated time points based on an original set of time points.

      - Added option to just apply the data. This allows users to quickly see the results of applying weather to various models. Also added Bus Group Gen Max MW fields by generic fuel types to provide quick summaries of weather impacts over longer time periods.

      - Added options when entering time points to specify the time/date using UTC. This will probably be most useful for weather.

      - Added Substations and DC Lines to time domain saved fields.

      - Added option to Show Result Analysis form with time step simulation results.

  - [Topology Processing](35-integrated-topology-processing.md#topology-processing-overview)

      - Added a new field to a bus called "PriorityDefault" that shows the default priority used for topology processing when choosing the primary node.

  - [Transient Stability](36-transient-stability-overview-and-data-part1.md#transient-stability-overview)

      - Automatically create plots that have a violation based on Transient Limit Monitor or Transient Limit Logic

      - "MW Nominal Tripped" field for loads. This value will also be recorded for Areas and Zones as a field.

      - Option to Auto Insert Loads (only opening loads) for Transient Contingencies

      - Option to "Include Category in Plot Name" as a prefix for plot names when auto-saving plots. If Category is blank and the option is selected, an underscore, "\_", will appear in the plot name.

      - TSRunResultAnalyzer(ContingencyName) script command that runs the Transient Result Analyzer. If the ContingencyName is not specified the analysis will be run for all contingencies.

      - Limit Monitors now have an option to use Cumulative Time to determine when a violation occurs. When this option is used, the cumulative time for which the monitored value exceeds the limit value will be used to determine if the limit time duration is met for considering this to be a violation. When this option is not used, the timer for determining if the limit duration is met is reset when the monitored value is no longer exceeding the limit value.

      - TSDisableMachineModelNonZeroDerivative(DerivativeThreshold) script command that will look for the derivatives of all transient stability models for generators. If the absolute value of any of the state variables for a particular generator is greater than the DerivativeThreshold, the machine model for the generator is disabled. If the DerivativeThreshold is not specified, 0.001 is used.

      - Transformers are a separate entry in Object Types to Include in the Save to Hard Drive Options

      - Weighted Average Rotor Speed result field for injection groups. This is the sum of generator speed multiplied by Weight divided by the sum of Weights. The intention is to set the Weights to be H (inertia) of the generators. The Weights/inertia are set in the Participation Factors of the injection group.

      - Added a button on the Model Explorer when showing transient stability models called "Parameter Descriptions". This button is adjacent to the "Show Block Diagram" button that was already there. When clicking on Parameter Descriptions button a dialog will appear listing all the dynamic model input parameters for the class of model being shown, along with the description of those fields. This is the same description that appears in the hover hints when moving the mouse over the column headers as well as the string that appears in the Export Case Object Fields option from the Window Tab in Simulator.

      - Made TS Power Flow States Playback Dialog non-modal so the user can modify the oneline when it is open.

      - Added injection group contingency action to open or close all devices in the injection group.

      - Added Interface Open and Close commands contingency actions. These commands open or close all the branches in the interface.

      - Added option "For Radial Generators Trips Also Open the GSU".

      - Added the ability to make plots from Result Analyzer Signal Violations. See "Make New Plot..." in the right-click local menu.

      - Increased number of states that can be plotted for a VSC DC Line model

      - For Transient Contingency Element added three fields to show action parameters.

      - When selecting a Transient Contingency to Skip, all fields in the entire row will gray out. This will help the user visually identify the skipped contingencies.

      - Added frequency test signals that can be applied as events either to 1) individual generators, 2) all generators in an area, 3) all generators in an injection group, or 4) all the case generators. The test signal just modifies the generator speed value. This change can either be discrete or sinusoidal.

      - When performing a validation check for most values in transient stability against a minimum limit PowerWorld had a 0.000001 tolerance we checked against. For some situation this tolerance was too small. For example a user may run auto-correction against time constants the are required to be 4 times the 0.25 cycle times timestep which we would calculated as 1/240 \* 4 = 0.0166666667 seconds. If a time constant was smaller than this we would round it up to exactly that time constant. However if the user then changed the contingency to use a timestep of 0.004167 seconds (we store timestep in second out to microsecond precision), then the required minimum timestep was 4\*0.004167 = 0.016668 seconds. That means that the previously auto-corrected timestep was no "too small" because 0.0166666667 \< 0.016668. Thus the value is too low by 0.0000013333 seconds which is just slighly above the old tolerance we have. This has been changed so the tolerance is now 0.05% of the limit, so in this case the tolerance if 0.0166666667\*0.0005 = 0.0000083333 (so just over 8 microseconds). This slightly larger tolerance will scale appropriately for all situations.

      - When saving Transient Contingencies as an Aux file it will also save the Transient Contingency Elements. This was not done before when saving from the Multiple Contingency table.

      - Added an Event message for DISTRELAY models to say which Zone number activated the relay.

      - With plot definition, added feature when automatically determining the vertical axis scale to force the Minimum value to be greater than the Minimum specified. This allows the automatic scaling to ignore values that are zero for example. Also added similar feature to force the Maximum value to be less than the Maximum specified.

      - Added "Include In Tripped Amount" field with transient contingency element to indicate whether generation or load MW that gets opened should be included in the Summary Results for Tripped Generation and Load.

      - Generation and load MW that gets tripped due to an injection group transient contingency can now be included in the Summary Results for Tripped Generation and Load.

      - Modified documentation of Vramp and Cramp parameters of the CDC4 and CDC6 type DC Line models in case information displays to reflect that they are in the units of pu/sec.

      - TSValidation object type is now available to return all validation messages. The Category field indicates if a message is an Error, Warning, or Info. This object type can be filtered and saved to file but nothing can be loaded back in.

      - TSState object type is now available to return all transient stability states. This object type can be filtered and saved to file but nothing can be loaded back in.

      - Added TSInitialize script command that will initialize the transeint stability solution. This can take one optional parameter CheckAlreadyInitialized that is NO by default. If YES the initialization will not be done if it has already been done. This script command is necessary if using the new TSState object type to return initial states through scripting.

      - Added TSValidate script command that will run transient stability validation.

      - For a PlotSeries add two new options for a "Scale" and "Offset". When using these the Actual Value on the plot will be (y-Offset)\*Scale.

      - TSClearAllModels script command will now delete Load Distribution Equivalents.

      - Added new "psuedo-energy" calculation for the Transient Result Analyzer to calculate an Energy for each TSResultAnalyzerModeMagAng and then the summation of this across all signals for the TSResultAnalyzerMode.

      - In the Transient Stability Plot tool, the names of the plots and plot series was modified to eliminate the use of "\\" character. In the "\\" character which is considered an escape character, hence it was eliminated and substitute with a "\_" character. Example: "Gen\_App Imp\\R" will now look like this "Gen\_App Imp\_R"

      - Added Negative Load Models for Generators without Models options of Constant Current and Constant Impedance.

      - For truly bad input data on synchronous machine models, checks on (Xqpp \> Xqp) could conflict with checks on the ratio of (Xqpp/Xdpp). Modified the auto-correction routines in these situations to just leave the Xqpp value alone and return an error to force the user to go correct these models.

      - The option to "Save Transient Stability Data -\> Only Records Modified in Difference Case" will now use the Area/Zone filters.

      - Added TSTransferStateToPowerFlow script command.

      - Allow the generic object types that show the listing of all transient stability models of a particular type to be accessed through auxiliary and script commands for listing, filtering, and deleting objects. Objects cannot be modified through these generic object types.

      - Added ability to use Custom Expressions and Custom String Expressions with transient stability model object types.

      - Added a readonly edit box on the Auto-Save Plot portion settings on the Plot Designer to show the folder location to which these files will be stored.

      - Modified TSValidation object so they can show the DataMaintainer of the underlying model object.

      - Added a new field to a TSLimitMonitor called SeveritySort. Set to either ValueTime, ValueStartTime, ValueExtremeTime, ValueExtreme, or ValueExtremeConv. These refer to fields of a TSLimitMonitorViolation. When deciding which TSLimitMonitorViolation objects to keep once the MaxViolStore count is reached, this sort field determines which violations to keep. Default value is ValueTime which means that the first violation encountered are kept. Setting to ValueExtreme for example if you're tracking low voltages would give the buses that experienced the lowest voltage during the simulation (as long as they met the criteria for a violation).

      - TSModalAnalysisSignal object type can update fields through pasting from Excel or aux files. The signal itself must already exist and cannot be created this way.

      - Added ability to scale a mode's, TSGlobalModeResult object type, average value by a term, that tells how the signal decays, Damping Scalar.

      - With Modal Analysis, improved mode visualization by allowing angles to be shifted based on a specified signal value. Also added signal numbers for a quick way to identify signals.

      - Added transient contingency elements to change all generator angles and speeds in an area or injection group by a specified amount.

      - Changed so when inserting a new TS event by right-clicking on an existing event and choosing Insert, the new event will default to the same object (and hence object type) of the existing event. Other fields will be defaults in an attempt to distinguish this as a new event and not an edit of the existing event.

      - Modified the PlayIn signals so that when they are initialized, if OffSet\*Scale \> 10 then we automatically calculate an offset to match the initial condition for the respective signal. This was done previously but was done only looking at Offset \> 10, so if Scale was a very small number it could cause a problem.

      - Added the BusView option in the All States table. The bus view will only open if the selected object is a Generator, Switched Shunt, Load, or a Branch.

      - The following models were added:

          - Added new CompLoadMon measurement model

      - The following models were modified:

          - Modified the CMLD and CMLPDW model so that if a loading factor for a motor is set as 0.0, then we simply interpret as 1.0 instead. 0.0 causes divide by zero errors which don't make sense.

          - Changed the voltage delay default for the CMPLDW on the single phase motor to avoid getting validation errors with the defaults.

          - Modified the hydro governor models HYGOV, HYGOVD, HYGOVR, HYPID, HYG3, and HYGOV4 models when initial limit violations occur because the Pmech output is higher than the combination of the inputs of Hdam (or H0), qnl, At, and the nonlinear Gate to Pgv block are able to achieve. When using the initial limit violation option to "Modify Limits and Run", PowerWorld will now calculate a the higher value of Hdam necessary to achieve the Pmech output. Previously PowerWorld would change the At (turbine gain), but discussions with customers indicate it is more appropriate to modify Hdam instead.

          - Modified the WTGAR\_A and WTARA1 models so that they can initialize to an initial pitch that is negative. This is an unusual configuration for models but should be allowed.

          - Modified the REGC\_C machine model to include a new parameter Vpllfrz. The model will now freeze the PLL integrator state when the filtered terminal voltage is below Vdip.

          - Modified the new REGC\_C model so that the network equations use the PLL angle for the network to model reference transformation. Previously the PLL angle was used for doing the transformation for modeling the current controls, but not the network equations.

          - The Q/P ratio reference input for REEC\_A/B/C/D models can now be changed by using the setting the exciter setpoint during a dynamic simulation.

          - Modified the initialization of the H6E governor models to ensure they initialize to a flat start. Limitation in the gate position prevent the Pmech from being achieved are now handled by modifying the Hdam value instead for H6E. In addition, the initialization for the gate position was improved.

          - Default value of Trate for the H6E governor was 163 which was silly. The default is now 0.0 and means to use the generator MVABase which is what all other governors default to.

          - Modified PSS2C, PSS3C, PSS6C, and PSS7C stabilizers to include Tpgfilt parameter as a time constant for measuring Pgen for use in the PSS Output logic decisions. Added reading and writing this parameter from the DYD format.

          - For now, this change is affects only the UEL2 model. When a TS simulation is allowed to modify limits for initial limit violations, and if a UEL/OEL/SCL has Activation Status which is not equal to Idle (i.e 0) during Initialization, then it will NOT send a signal to exciter for the entire simulation. This will allow the exciter to initialize in steady state.

          - For the UCBGT and UCCPSS governor models, fixed the treatment of non-windup limits for the 3 states feeding into the Low Value Select block when the proportional gain is zero so that the integrator state would not windup. When Kp\<\>0 this was already handled.

          - Added LogModifiedStatusNotIdle to UEL2C

          - State 7 of PIIntegrator of UEL2C now reports PI output value instead of the internal state.

          - Modified the PSS2C, PSS3C, PSS6C, and PSS7C stabilizers to allow a "Compensated Frequency" calculation.

          - Modified the CDC1, CDC4T, CDC6, and CDC6T DC line models so that the Voltage-Dependent Current Order Limit (VDCOL) always uses the inverter DC voltage in kV.

          - Modified REGC\_C so that the PLL integrator state from the Kipll/s block has non-windup limits of wmax/wmin. These were already limits on the output of the PI block, so this uses the same values as non-windup limit on the integrator state.

          - Added the ability to specify zone forward reach and angle with a percentage value for the following distance relay models: ZLIN1, ZQLIN1, OOSLEN, OOSLNQ

      - File formats

          - Added support to read and write GENQEC, PSS2C, OEL3C, and UEL1 transient models from a dyd file. The model were already available in PowerWorld.

          - Added support to read and write ESDC2C transient model from a dyd file.

          - Previously PowerWorld would write cmpldw model defined in PowerWorld at an aggregation level such as Bus, Load Model Group, Area, Zone, or Owner, we would always write out cmpldw models for individual load objects because this is the only thing that the DYD file supported. The DYD file now supports writing out a special "\_cmpldw" model for load model groups, areas, zones, and owners, so we will write out these special "\_cmpldw" models to DYD files.

          - Added the ability to read from a DYR file a PLNTBU1, REAX3BU1, REAX4BU1, SYNAXBU1, FCTAXBU1, and SWSAXBU1 models and convert them into an REPC\_B plant controller model which controls multiple generators. PowerWorld Simulator will also write these models back out to a DYR file as this was added.

          - Cleaned up the look of how DYR files are written to remove unnecessary trailing 0s from numbers and remove lots of extra spaces in them. Each record is also written on a single line of text now instead of multiple lines.

          - Added support to read/write PSS2C Stabilizer for PSSE dyr files.

          - Added ability to read from DYR files the REPCC, REECD1, and WTGWGOA models.

          - Added ability to read from DYD files the REPC\_C, REEC\_D, and WTGWGO\_A models.

          - Added support to read and write from a PSLF dyd and PSSE dyr file for Transient Stability Stabilizer models PSS6C and PSS7C.

          - Added support to read and write from a PSLF dyd and PSSE dyr file for Transient Stability models OEL2c and UEL2C.

          - Added support to read and write from a PSLF dyd file for Transient Stability models ESAC1C (AC1C in PW) and ESAC2C (AC2C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability models ESAC3C (AC3C in PW), ESAC4C (AC4C in PW), ESAC5C (AC5C in PW) and ESAC6C (AC6C in PW).

          - Added support for read/write from the DYD file for the ESDC1C exciter model. This maps to the DC1C exciter.

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESAC7C (AC7C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESAC9C (AC9C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESAC10C (AC10C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESST2C (ST2C in PW) and ESST3C (ST3C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESST7C (ST7C in PW).

          - Added support to read and write from a PSSE dyr file for Transient Stability model ST7C (ST7C in PW).

          - Added support to read and write from a PSLF dyd file for Transient Stability model ESST8C (ST8C in PW) and ESST9C (ST9C in PW).

          - Customers have reported that renewable dynamic machine models do not function when read from DYR models in other software if the power flow generator model flag WMOD do not set to a 1. When writing out a RAW file, if the WindControlMode in PowerWorld is set to none, then the generator WMOD field in the RAW file will be determined by the type of dynamic machine model used for the generator. For machine models that are for renewable machines (WT1G, WT2G, WT3G, WT4G, REGC\*, PVD1, PV1G, and so on), the WMOD will be written as a 1 and for other generators the value will be a 0.

  - User Interface Dialogs

      - On the Super Area dialog a checkbox was added for the OPF option to Include Marginal Losses.

      - When pressing the Save To Aux button in the generator dialog, now it will also save the Reactive Capability curve in the aux file.

      - Added buttons to the Substation and Bus dialogs in both Edit and Run mode on the Geography tab to "Open Google Maps". This button will automatically launch the default browser on the computer and open the Google maps website to the latitude/longitude coordinate on the respective dialog.

      - When choosing to Save to AUX on the Simulator Options Dialog, added a dialog that has check-boxes on it so you may choose which types of options to save. The choices are Solution, Environment, Simulation, Case Inof, Custom Colors, Areva Import Label Specs, and Oneline Browser Custom Menu.

      - Modified the General File Browser to allow searching for PDF, PPT, DOC, and XLS files as well. When right-clicking on these files to open them a standard Window call is made to open the file with whatever program is registered with Windows.

      - Modified the edit boxes showing the Branch MVA limits on the Branch dialogs to only show at most 7 significant digits for the MVA limits.

      - Save Filter button on Advanced Filters dialog will now save a separate data section for Condition rather than a SUBDATA section.

      - Added a caption in the Display/Column Options to include the name of the DataGrid. Now the Display/Column Options dialog caption will be like this: "Display/Column Options: 'Name of DataGrid'"

      - In various places, such as the Advanced Filter dialog, the combo box that would show the list of available fields has been replaced with a drop-down treeview.

      - On Super Area dialog added summary information to show generation by fuel type.

      - Added new options to the right-click menu of a the Message Log to "For AUX load, add Log Message for Existing Objects Edited" and "For AUX load, add Log Message for New Objects Created". These 2 options are NOT checked each time PowerWorld is opened, but can be checked to generate log messages for every edited object or for every created object as AUX files are loaded. Normally this is not wanted but can be useful to ensure you are not editing existing objects when you were not expecting to.

      - Added PowerFactor value to the Load Run Mode dialog.

      - On the Bus Voltage Regulating Devices dialog, added field to show if switched shunt is using the RegTargetVoltHigh value.

      - Added an indication on the About box if the license being used is a software or hardware license.

  - Weather

      - Weather Station object containing various weather related measurements

      - [Weather-dependent limits](28-weather.md#weather-dependent-limits) for branches and generators

      - Time Step Simulation using historic weather data

      - [Power Flow Weather (PFW) generator models](28-weather.md#weather-related-models-and-information-dialog)

---

<a id="writeauxfile-function-version-9"></a>

## WriteAuxFile Function (version 9)

*Source: [`Content/MainDocumentation_HTML/WriteAuxFile_Function_v9.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/WriteAuxFile_Function_v9.htm)*

The WriteAuxFile function can be used to write data from the case in the [Simulator Automation Server](52-additional-linked-topics-part1.md#simulator-automation-server-version-9) to a PowerWorldâ Auxiliary file. The function is flexible in that you can specify the type of object data you want to export, an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) name for a filter you want to use, and as many or as few field types as desired that are supported by the type of object. In addition, you can specify a new file name for each call to WriteAuxFile, or you can specify the same file name and append the data to the file. If an error occurs while trying to write the auxiliary file, an error message is returned through EString.

**WriteAuxFile(fileName, filterName, tObjectType, EString, {tAppend}, {tFieldList})**

Parameter Definitions

**FileName : String **The name of the PowerWorldâ Auxiliary file you wish to save. No default.

**filterName : String **The name of an [advanced filter](04-model-explorer-and-case-information-part2.md#advanced-filtering) which was previously defined in the case before being loaded in the Simulator Automation Server. If no filter is desired, then simply pass an empty string. If a filter name is passed but the filter cannot be found in the loaded case, no filter is used. Default is an empty string.

**tObjectType : String **A string describing the type of object for which your are requesting data. No Default.

**EString : Variant **This parameter must be assigned a variable declared as a Variant. This parameter is for a return value only, and will assign the passed variable a string representing an error that may have occurred in the Simulator Automation Server. If no error occurred, the EString variable will return an empty string.

**TAppend : Boolean **This parameter is optional. If you have given a file name of an auxiliary file that already exists, then the file will either be appended to or overwritten according to the setting of this parameter. If the parameter is not passed, the Simulator Automation Server assumes false.

**TFieldList : Variant **This parameter is optional. A variant array of strings, where each string represents an object field variable, as defined in the section on [PowerWorld Object Variables](52-additional-linked-topics-part1.md#powerworld-object-variables-version-9). If no array is passed, the Simulator Automation Server will use predefined default fields when exporting the data.

Example

**WriteAuxFile("c:\\my files\\myauxfile.aux", "", "gen", EString, False, \[pwBusNum, pwGenID, pwGenAGCAble\])**

This function call will send the values of the fields in tFieldList to a PowerWorld Auxiliary file for all the generators in the load flow case. If a filter name had been passed instead of an empty string, Simulator would have located and used a pre-defined advanced filter and applied it to the information if it was found. By specifying the fields in the optional parameter tFieldList, only the three field values for each generator will be returned. If the optional parameter tFieldList had been omitted, Simulator would have returned internally defined default information for the generators. Since the tFieldList optional parameter was included, the tAppend optional parameter also had to be included, even though it's default value is already False.
