---
title: "PowerWorld Cruncher"
part: "Cruncher"
chapter_file: "50-cruncher.md"
topics: 18
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# PowerWorld Cruncher

PowerWorld Cruncher: processing phases, structures, alarms, snapshots and settings.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (18)**

- [Introduction](#introduction)
- [Cruncher Processing](#cruncher-processing)
- [SimAuto Manager](#simauto-manager)
- [Seed Cases](#seed-cases)
- [Snapshots](#snapshots)
- [Studies](#studies)
- [Schedules](#schedules)
- [Processing Phases](#processing-phases)
- [Outages Phase](#outages-phase)
- [Weather Phase](#weather-phase)
- [Forecasts Phase](#forecasts-phase)
- [Voltage Conditioning Phase](#voltage-conditioning-phase)
- [Optimal Power Flow (OPF) Phase](#optimal-power-flow-opf-phase)
- [Analysis Phases](#analysis-phases)
- [Time-Varying CSV File Format](#time-varying-csv-file-format)
- [Alarms](#alarms)
- [Dynamic Snapshot Analysis](#dynamic-snapshot-analysis)
- [User Settings](#user-settings)

---

<a id="introduction"></a>

## Introduction

*Source: [`Content/MainDocumentation_HTML/Cruncher Introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Cruncher Introduction.htm)*

**PowerWorld Cruncher** is an application that uses **PowerWorld Simulator** as an engine for integrating data from various input files to configure power flow cases. It combines seed cases, forecasts, outages, and voltage schedules to generate consistent *Snapshots* of the system state at specific times or time ranges. These Snapshots can be analyzed, compared, and used to produce detailed reports for planning, operations support, and recurring studies.

Cruncher is designed for repeatable, large-scale workflows. By orchestrating automated processing, flexible scheduling, and parallel/distributed execution, it enables rapid, consistent evaluation of many operating scenarios that would be impractical to perform manually.

### Key Concepts

  - **Seed Cases** – The foundation of every study. A Seed Case defines the starting state and can include pre/post configuration files to standardize setup.
  - **Snapshots** – Points or ranges in time relative to a user-defined *Target Time*. Each Snapshot applies relevant inputs (forecasts, outages, schedules) to a Seed Case to create a case ready for analysis.
  - **Studies** – The central structure that brings Seed Cases, Snapshots, forecasts, outages, voltage schedules, and analysis settings into a repeatable workflow.
  - **Schedules** – Automation that runs a Study on a cadence (e.g., hourly or daily), generating and optionally analyzing snapshots at predefined intervals.
  - **Results** – Each run can produce output cases, reports, plots, and optional archives for review, sharing, and reproducibility.

### Why Use Cruncher?

  - Automates repetitive simulation tasks and multi-scenario studies.
  - Ensures consistent configuration across runs for reliable comparisons.
  - Scales via parallel SimAuto processes and distributed computing resources.
  - Generates comprehensive snapshot and analysis reports and visualizations.
  - Supports flexible scheduling for recurring operational or planning studies.

---

<a id="cruncher-processing"></a>

## Cruncher Processing

*Source: [`Content/MainDocumentation_HTML/Cruncher Processing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Cruncher Processing.htm)*

### Cruncher Processing

Cruncher processing can be roughly divided into three stages:

### Seed Case Processing

Perform any user-configured case sanitation, validation, or normalization using AUX scripts to prepare initial cases for the application of time-varying data

  - If a valid Cache case exists with an ID reflecting the current configuration, use that and do not re-process
  - Otherwise, load all AUX/HDBExport files in the optional “pre” subdirectory
  - Load a source case (PWB, AUX, or HDBExport). More recently modified source cases are used first
  - Load all AUX/HDBExport files in the optional “post” subdirectory
  - Attempt to solve the resulting case.
      - If the case does not solve, start over using the next most recently modified source case in the directory
  - If the case solves, save a Cache Case with a name reflecting the source case used, and a hash-based ID generated from the current configuration

### Snapshot Processing

Use time-varying data inputs to apply specific modifications to a Seed Case and generate a solved power flow representing the case stat at a given time, saved as a Snapshot Case

  - Snapshot processing begins with a Seed Case. The same Seed Case may be used for any number of Snapshots
  - Cruncher loads specified Time Inputs to map relevant data to each Snapshot
  - Processing Phases performed in sequence
      - [Outages](#outages-phase)
      - [Weather](#weather-phase)
      - [Load/Gen Forecasts](#forecasts-phase)
      - [Voltage Conditioning](#voltage-conditioning-phase)
      - [OPF](#optimal-power-flow-opf-phase)
  - The resulting power flow states are solved and saved as Snapshot Case PWBs
  - If configured to do so, an xlsx Snapshot Report is generated and saved

### Analysis

Perform Contingency or other analysis on one or more Snapshot Cases

  - Analysis of a given Snapshot begins by loading the Snapshot Case. If the Snapshot itself failed to solve, Analysis will not be performed

  - [Analysis](#analysis-phases) currently supports two phases

      - Analysis AUX phase runs a user-specified AUX script

      - Contingency Analysis phase runs Contingency Analysis on the case

  - Resulting state is saved as an Analysis Case PWB

  - If configured to do so, an XLSX Analysis Report is generated and saved

---

<a id="simauto-manager"></a>

## SimAuto Manager

*Source: [`Content/MainDocumentation_HTML/SimAuto Manager.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SimAuto Manager.htm)*

- All of the important processing Cruncher performs is done through Simulator using SimAuto connections handled by the SimAuto Manager
  - Settings for the SimAuto Manager can be found in the User Settings Dialog
      - **Processing Cores** defines the number of SimAuto processes the SimAuto Manager will maintain when connected, with an option to use the maximum number supported by the machine. Updates to this setting are applied the next time the SimAuto Manager connects (if updates are applied while connected, reconnect to apply the new values)
      - **Auto-start SimAuto**instructs Cruncher to start the SimAuto Manager automatically on application startup.
  - The SimAuto Manager handles SimAuto usage within one instance of Cruncher when processing multiple Studies concurrently – running multiple instances of Cruncher concurrently instead can lead to inefficient usage of local resources
  - The SimAuto Manager currently only runs local connections for Cruncher processing. Simulator Distributed Computing for Contingency Analysis, ATC, TS, and QV can make use of remote resources
  - The SimAuto Manager display in the main Cruncher Ribbon Tab has a number of indicators and controls
      - Connection Toggle button to connect/disconnect
      - Idle Connection bar to indicate SimAuto connections available for processing tasks
      - Active Connections bar to indicate SimAuto connections currently performing tasks
      - SimAuto Service indicator shows if the SimAuto Service is currently running and if it is limiting the number of SimAuto connections the SimAuto Manager can maintain
      - Distributed Computing Resources Lock indicator indicates if the Distributed Computer List on this machine is locked or not

![SimAutoManager](images/SimAutoManager.jpg)

---

<a id="seed-cases"></a>

## Seed Cases

*Source: [`Content/MainDocumentation_HTML/seedCases.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/seedCases.htm)*

A **Seed Case** provides the foundation for all Cruncher processing. It represents a solved base case, along with optional configuration files, that define the initial system state before forecasts, outages, or other study inputs are applied. All Snapshots and downstream results are built from one or more Seed Cases.

### Structure of a Seed Case

A Seed Case is organized as a folder on disk. This folder typically contains:

  - **Source Cases** – One or more case files (PWB, AUX, or HDBExport). Cruncher will select the most recent valid case by modification timestamp, using reverse alphabetical order as a tiebreaker.
  - **pre subdirectory** – Optional. Contains AUX or HDBExport files that should be applied *before* the source case is loaded. These often define Simulator configuration settings that affect case loading.
  - **post subdirectory** – Optional. Contains AUX or HDBExport files that should be applied *after* the source case is loaded. These often provide standardization or additional initialization.
  - **logs subdirectory** – Created automatically by Cruncher during the build process. Includes a summary log and a copy of the Simulator log for detailed troubleshooting.

### Build Process

When Cruncher processes a Seed Case directory:

1.  Runs any AUX files in the *pre* subdirectory in alphabetical order.
2.  Opens the selected source case file.
3.  Runs any AUX files in the *post* subdirectory in alphabetical order.
4.  Attempts to solve the case. If it does not solve, restart the process using the next Source Case in order.
5.  Saves a cached solved version of the case in the Seed Case folder.

On subsequent runs, Cruncher uses this cached solved case if it is still valid; otherwise, it rebuilds the cache. This caching ensures consistent results while reducing overhead.

### Configuration in Cruncher

  - **Name** – Defaults to the Seed Case directory name. Can be overridden for clarity.
  - **Directory** – Path to the Seed Case folder.
  - **Description** – Optional notes to provide context or versioning details about the case.
  - **Pre Case AUX / Post Case AUX** – Lists automatically populated based on the presence of `pre` and `post` subdirectories.

---

<a id="snapshots"></a>

## Snapshots

*Source: [`Content/MainDocumentation_HTML/snapshots.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/snapshots.htm)*

A **Snapshot** represents a point or range in time that Cruncher uses to transform a Seed Case into a case ready for analysis. Each Snapshot applies the study’s configured inputs (e.g., outages, weather, forecasts, voltage schedules, OPF) relative to a common *Target Time* chosen when the Study runs.

### Time Model

Snapshots are defined relative to a Study run’s **Target Time**:

  - **Offset** — The time difference from the Target Time. Offsets must be unique within a study’s Snapshot set (e.g., `+01:00`, `+02:00`).
  - **Duration** — The time window around the Snapshot time that determines which time-varying data points are considered. By default this is `0:00` (instantaneous, “at the time”). A positive duration looks *after* the time, and a negative duration looks *before* the time (e.g., `-01:00` means the hour preceding the Snapshot time).

#### Examples

  - *Offset = +03:00, Duration = 0:00*: Apply only data active exactly at Target Time + 3 hours.
  - *Offset = +12:00, Duration = -01:00*: Apply data active during the hour leading up to Target Time + 12 hours (i.e., an “hour ending” convention).

### Snapshot Configuration

Each Snapshot includes the following key settings:

  - **Seed Case** — Select which Seed Case to use as the base. In scheduled runs, Seed Case mapping can also be determined dynamically by day/time.
  - **Offset** — Required; must be unique in the set.
  - **Duration** — Optional; default is `0:00`. Positive looks after the time; negative looks before.
  - **Skip Analysis** — Exclude this Snapshot when the *Analysis* phase runs.
  - **Skip Voltage Conditioning** — Exclude this Snapshot from Voltage Conditioning even if enabled for the Study.

### Duration Aggregation

When **Duration** is non-zero, multiple data points may fall inside the window. Cruncher aggregates those values using the study’s duration settings:

  - **Aggregation methods**: *Average*, *Median*, *Maximum*, *Minimum*, *First*, *Last*.
  - **Per-type control**: Independent aggregation choices can be set for *Loads* and *Generators*, with a *Default* for other object types.

### Managing Snapshots

From the Snapshots tab you can:

  - **Add New** — Create a single Snapshot.
  - **Add Multiple** — Create a series with patterned offsets.
  - **Edit Last Selected** — Modify the highlighted Snapshot.
  - **Select All / Delete All Selected** — Bulk operations.
  - **Apply Preset Snapshot List** — Replace the current set with a preset:
      - *Future Hour Ahead*: three offsets `+01:00`–`+03:00`, duration `0:00`.
      - *Next Day Study*: 24 offsets `+01:00`–`+24:00`, each duration `-01:00` (hour ending).
      - *Week Ahead Study*: two blocks, `+06:00`–`+10:00` and `+15:00`–`+19:00`, duration `0:00`.

---

<a id="studies"></a>

## Studies

*Source: [`Content/MainDocumentation_HTML/studies.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/studies.htm)*

A **Study** in Cruncher is the primary container that brings together Seed Cases, Snapshots, processing phases, analysis options, and output settings into a single repeatable workflow. Running a Study creates one or more Snapshot cases relative to a chosen *Target Time*, applies configured inputs, and optionally performs Analysis and generates reports.

### Components of a Study

  - **Seed Cases** — Solved base cases that serve as the foundation for Snapshots.
  - **Snapshots** — Defined points or ranges in time, each applying time‑varying data to a Seed Case.
  - **Processing Phases** — Outages, Weather, Forecasts, Voltage Conditioning, and OPF.
  - **Analysis** — Optional Analysis AUX scripts or Contingency Analysis.
  - **Results** — Outputs including Snapshot/Analysis cases, reports, plots, AUX exports, and archives.
  - **Alarms** — JSON notifications signaling start, warnings, errors, and completion.

### Study Presets

Presets provide ready‑made Snapshot sets for common planning scenarios:

  - **Future Hour Ahead** — Three Snapshots at `+01:00`, `+02:00`, and `+03:00` with duration 0:00.
  - **Next Day Study** — Twenty‑four Snapshots (`+01:00` through `+24:00`) with `Duration = -01:00` (hour‑ending).
  - **Week Ahead Study** — Ten Snapshots in two blocks (`+06:00`–`+10:00` and `+15:00`–`+19:00`) with duration 0:00.

### Study Settings

  - **Name** — Human‑readable identifier.
  - **Status** — Informational flag such as TESTING, PENDING, VERIFIED, ERROR, ACTIVE, or PAUSED.
  - **Custom AUX** — Path to AUX files or folders for general configuration applied to every Snapshot.
  - **Solution Options AUX** — Export of Simulator solution options for consistent solves.
  - **Snapshot Solution Method** — Choice of power flow solution algorithm (e.g., Newton‑Raphson).
  - **Results Directory** — Folder where all outputs for this Study are saved.

### Validation

  - **Quick Validation** — Checks Study configuration and file paths without running Simulator.
  - **Full Validation** — Performs Simulator checks and saves an Excel report of issues found.

### Toolbar Actions

  - **Edit Study** — Open the Study Configuration dialog for editing.
  - **Delete Study** — Remove the Study from Cruncher.
  - **Export Study** — Save the Study configuration as JSON.
  - **Create Duplicate Study** — Clone the Study with a unique identifier.
  - **Run Validation** — Trigger Quick or Full Validation.
  - **Run On Demand** — Launch the Study immediately with a user‑specified Target Time.

---

<a id="schedules"></a>

## Schedules

*Source: [`Content/MainDocumentation_HTML/schedules.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/schedules.htm)*

A **Schedule** automates the execution of a Study by specifying when and how often it should run. Instead of manually launching an On Demand run, you can configure a Schedule to kick off hourly or daily, with Snapshot cases built relative to a dynamically determined Target Time.

### Schedule Types

Cruncher provides three preset schedule types that correspond to common study workflows:

  - **Hourly (Future Hour Ahead)** — Runs a Study multiple times per day, beginning at a user‑specified start hour and repeating at hourly intervals.
  - **Daily (Next Day Study)** — Runs once per day at a fixed time, targeting midnight of the next day (so Snapshot offsets align with hours of the day).
  - **Daily (Week Ahead Study)** — Similar to Next Day, but focuses on a smaller set of hours at predefined offsets for forward planning.

### Schedule Configuration

Each Schedule is defined in a JSON file that points to a Study configuration and adds scheduling metadata. Within the Schedule Configuration dialog, the following options are available:

  - **Name** — A human‑readable identifier for the Schedule (does not need to match the Study name).
  - **Description** — Freeform notes about purpose or scope of the Schedule.
  - **Maximum Threads** — Caps the number of SimAuto instances claimed when the Schedule runs, allowing resource sharing between multiple concurrent schedules.
  - **Quick Validation** — Option to automatically run Quick Validation a few minutes before the scheduled start.
  - **Perform Analysis** — Enables automatic Analysis after all Snapshots finish; if unchecked, only Snapshot cases are generated and Analysis must be launched manually later.
  - **Disable HUD** — Suppresses automatic launch of the Heads Up Display after completion.
  - **CTG Results Filter** — Overrides the Study’s Contingency Analysis filter if needed.
  - **Max Dist Procs** — Overrides distributed computing limits from the Study.

### Run Times

Run times determine when the Schedule will kick off. You can specify:

  - **Hourly schedules** — Start time of first run each day and number of hourly repeats.
  - **Daily schedules** — Specific clock time each day for the run to begin.

Schedules can be enabled or disabled for particular days of the week. If a day has no defined Seed Case mapping, the configuration falls back to a default Seed Case or the Study’s baseline configuration.

### Seed Case Overrides

A Schedule may assign different Seed Cases depending on day of week and time of day. Cruncher supports a naming convention where subdirectories are labeled with `<DAY>_HE<HH>` or `<DAY>_HB<HH>` (e.g., `MON_HE08` for Monday Hour Ending 08). Cruncher scans these folders to automatically map the correct Seed Case for each run.

### Snapshot Overrides

If desired, a Schedule can override the Snapshot list defined in the Study. By enabling *Override Study Snapshots*, you can provide an alternate set of Snapshots specific to the scheduled run.

### Alarms

Schedules can be configured with their own alarm settings to signal start, warning, error, or completion events. These alarms override alarm settings defined in the base Study.

### Schedule Management

  - **Add New** — Create a new Schedule from a preset or custom JSON.
  - **Edit** — Open a Schedule in the Schedule Configuration dialog.
  - **Manage** — View all loaded Schedules in a consolidated management dialog.
  - **Import / Export** — Load or save one or more Schedules as JSON configuration files.
  - **Quick Validate Study** — Run validation against the Study file associated with the Schedule.
  - **Toggle Pause** — Pause or unpause a Schedule; paused Schedules skip their runs.
  - **Run On Demand** — Launch the Study immediately using either the next or previous scheduled Target Time.

---

<a id="processing-phases"></a>

## Processing Phases

*Source: [`Content/MainDocumentation_HTML/processingPhases.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/processingPhases.htm)*

After a Seed Case is loaded to create a Snapshot, Cruncher applies a sequence of **Processing Phases**. Each phase introduces data or configuration that modifies the case before results are saved. Phases can be enabled or disabled individually, and each has its own configuration dialog in the Study settings.

### Common Elements

Most processing phases share a few common controls:

  - **Enable** — Determines whether the phase runs for the current Study or Snapshot.
  - **Set-up** — File or folder of AUX scripts applied before the phase logic executes.
  - **Clean-up** — File or folder of AUX scripts applied after the phase completes (if supported).

### Available Phases

The following processing phases are supported in Cruncher. Each is described in detail on its own page. When enabled, they proceed in the following order:

  - [Outages](#outages-phase) — Apply scheduled outages active at the Snapshot time and/or Revert scheduled outages active in the Seed Case.
  - [Weather](#weather-phase) — Import temperature forecasts and adjust limits accordingly.
  - [Forecasts](#forecasts-phase) — Apply generator and/or load forecasts from Time-varying CSV files.
  - [Voltage Conditioning](#voltage-conditioning-phase) — Apply scheduled voltage targets across regions, seasons, and holidays.
  - [Optimal Power Flow (OPF)](#optimal-power-flow-opf-phase) — Run an OPF step using default or custom configuration to target specific Interface flows.

After all enabled phases have been applied, the Snapshot case is saved to the results directory and becomes available for later Analysis.

---

<a id="outages-phase"></a>

## Outages Phase

*Source: [`Content/MainDocumentation_HTML/phaseoutages.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phaseoutages.htm)*

The **Outages** phase applies or reverts scheduled outages to a Snapshot case based on its time or duration window. Outage data can be supplied through AUX files or PowerWorld Outage CSV files. This phase is typically the first modification step after the Seed Case is loaded.

### Configuration Options

  - **Set-up** — File or folder of AUX scripts to run at the start of the phase.
  - **Clean-up** — File or folder of AUX scripts to run at the end of the phase.
  - **Definitions** — Path to AUX or CSV files containing outage definitions.

### Actions

The Outages phase can perform several different actions, which can be enabled or disabled independently:

  - **Revert Outages** — Uses the Seed Case timestamp to identify any outages that were active at that time and reverses them.
  - **Apply Outages** — Inserts outages active at the Snapshot time or within its duration window.
  - **Try Hard** — Iteratively applies outages in groups (e.g., by substation) and solves at each step to move the case toward a solved state with all outages applied.
  - **Require Outages** — If enabled, the Snapshot will fail if the case cannot solve with outages applied.

### Filters

Filters allow finer control over which outages are processed:

  - **Filter Buffer** — If enabled, retains only outages within a buffer window around the Snapshot time (user-specified hours before and after).
  - **Remove Filter** — Deletes any outages matching the filter immediately after definitions are loaded.
  - **Revert Filter** — Restricts which outages are reverted if Revert Outages is enabled.
  - **Outage Filter** — Restricts which outages are applied if Apply Outages is enabled.

### Phase Operation

1.  Run any *Set-up* AUX files.
2.  Load outage definitions from AUX or CSV.
3.  Apply *Remove Filter* (if specified) to prune the list of Scheduled Actions.
4.  Perform *Revert Outages* (if enabled) to clean up any outages that may have been active in the Seed Case.
5.  Apply *Filter Buffer* (if enabled) to leave only Scheduled Actions active during or near the specific Snapshot being generated.
6.  Perform *Apply Outages* (if enabled).
    1.  If the case solves with Outages applied, proceed.
    2.  Otherwise, if "Try Hard" is enabled, attempt to get a solved state through iterative batch application of Outages.
    3.  If the case still does not solve, "Require Outages" determines if processing proceeds without Outages applied, or halts.
7.  Run any *Clean-up* AUX files.

---

<a id="weather-phase"></a>

## Weather Phase

*Source: [`Content/MainDocumentation_HTML/phaseweather.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phaseweather.htm)*

The **Weather** phase introduces temperature forecast data into a Snapshot case. Weather data can be used by Simulator to adjust system parameters such as branch limits based on thermal ratings. This phase ensures that each Snapshot reflects the expected environmental conditions at its target time.

### Configuration Options

  - **Enable** — Toggles whether the Weather phase runs for the Study or Snapshot.
  - **Set-up** — File or folder of AUX scripts to be run before weather data is applied. This may be used to configure `WEATHERSTATION` objects and create mappings to them for relevant system devices.
  - **Clean-up** — File or folder of AUX scripts to be run after weather data is applied.
  - **Weather Forecast** — Path to a [Time Varying CSV](#time-varying-csv-file-format) file containing forecast data for `WEATHERSTATION` objects.

### Phase Operation

1.  Run any *Set-up* AUX files.
2.  Read forecast values from the specified CSV file.
3.  Apply values to `WEATHERSTATION` objects for the Snapshot time or duration window.
4.  Instruct Simulator to update dependent system parameters such as branch limits and renewable generation limits. For more details, refer to AUX Script documentation for TemperatureLimitsBranchUpdate and WeatherPFWModelsSetInputsAndApply.
5.  Run any *Clean-up* AUX files.

---

<a id="forecasts-phase"></a>

## Forecasts Phase

*Source: [`Content/MainDocumentation_HTML/phaseforecasts.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phaseforecasts.htm)*

The **Forecasts** phase applies time-varying data for loads, generators, areas, zones, or injection groups to a Snapshot case. This allows studies to reflect expected system behavior based on forecasted operating conditions. Forecasts are supplied through Time-Varying CSV files and can include both unit-level and aggregate adjustments.

### Configuration Options

  - **Enable** — Toggles whether the Forecasts phase runs for the Study or Snapshot.
  - **Set-up** — File or folder of AUX scripts to run before forecasts are applied.
  - **Clean-up** — File or folder of AUX scripts to run after forecasts are applied.
  - **Troubleshooting Depth** — Defines how aggressively Cruncher attempts to solve cases when applying forecast values prevents convergence. Options are *Low*, *Medium*, *High*, or *None*.
  - **Forecast File List** — Ordered list of Time-Varying CSV files to be applied, with higher-priority files overriding lower-priority ones.

### Supported Objects and Fields

  - **GEN** — `MW`
  - **LOAD** — `MW`
  - **AREA** — `GenMW`, `LoadMW`
  - **ZONE** — `GenMW`, `LoadMW`
  - **INJECTIONGROUP** — `GenMW`, `LoadMW`, `MW`

### Troubleshooting Depth

  - **Low** — Minimal iterations; stops quickly if case fails to solve.
  - **Medium** — Balanced approach between iteration count and run time.
  - **High** — Many iterations with small adjustments, maximizes chance of convergence.
  - **None** — Disables iterative troubleshooting; case must solve immediately.

### Phase Operation

1.  Run any *Set-up* AUX files.
2.  Apply forecast values from all listed CSV files, respecting file order and precedence rules.
3.  Attempt to solve the case.
4.  If unsolved and *Troubleshooting Depth* is enabled, iteratively adjust forecasted values between known solved states and forecast values until convergence is reached or depth limit is exceeded.
5.  Run any *Clean-up* AUX files.

---

<a id="voltage-conditioning-phase"></a>

## Voltage Conditioning Phase

*Source: [`Content/MainDocumentation_HTML/phasevoltageConditioning.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phasevoltageConditioning.htm)*

The **Voltage Conditioning** phase applies scheduled voltage profiles to a Snapshot case. It allows Cruncher to adjust voltage setpoints dynamically, reflecting seasonal, regional, or holiday-based operating targets. This ensures Snapshot cases more closely match expected system conditions at their Target Time.

### Configuration Options

  - **Enable** — Toggles whether the Voltage Conditioning phase runs.
  - **Set-up** — File or folder of AUX scripts run before applying schedules, typically to configure case parameters or custom objects.
  - **Clean-up** — File or folder of AUX scripts run after applying schedules.
  - **Voltage Schedule** — Defines which regions, seasons, and holidays apply different voltage target sets. This schedule is stored in the Study, but can be exported/imported as a JSON file for reuse.

### Schedule Structure

A voltage schedule contains the following elements:

  - **Regions** — Groupings of elements (e.g., buses or substations) that share a common schedule.
  - **Seasons** — Defined time periods with unique voltage target sets.
  - **Holidays** — Special exceptions that override the normal daily schedule (e.g., treating a weekday like a Sunday).

### Phase Operation

1.  Run any *Set-up* AUX files.
2.  Identify the applicable voltage targets for each Region at the Snapshot Time.
3.  Apply the defined voltage target sets to the Snapshot case and run the Voltage Conditioning tool.
4.  Run any *Clean-up* AUX files.

---

<a id="optimal-power-flow-opf-phase"></a>

## Optimal Power Flow (OPF) Phase

*Source: [`Content/MainDocumentation_HTML/phaseoPF.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phaseoPF.htm)*

The **Optimal Power Flow (OPF)** phase allows Cruncher to run OPF solutions on Snapshot cases. OPF adjusts dispatch and controls to meet objectives such as minimizing control changes or enforcing interface limits, providing a more realistic system state for subsequent analysis. OPF can be configured with default options for simple studies or with detailed custom AUX scripts for complex systems.

### Configuration Options

  - **Enable** — Toggles whether the OPF phase runs on the Snapshot case.
  - **Set-up** — File or folder of AUX scripts to run before the OPF solution, typically to configure case-specific OPF options.
  - **Set-up Defaults** — Checkbox that auto-configures basic OPF options suitable for simple studies. Defaults include:
      - All Areas added to a single SuperArea under OPF control.
      - Line enforcement disabled.
      - Interface enforcement enabled.
      - Objective function set to minimize control changes.
  - **Interface Targets** — Path to a Time-Varying CSV file specifying `LimitUsed` values for Interfaces over time. When applied to an Interface, the Interface's `OPFEnforceEquality` field is automatically set to YES.

### Phase Operation

1.  Run any *Set-up* AUX files.
2.  If *Set-up Defaults* is enabled, apply the default OPF configuration.
3.  Apply Interface Target values if a CSV file is specified.
4.  Attempt the OPF solution.
5.  Run any *Clean-up* AUX files.

### Default Setup (AUX Equivalent)

``` 
            SuperArea (Name, AGC)
            {
            "CRUNCHER_OPF" OPF
            }

            SCRIPT
            {
            SetData(AREA, [SuperArea], [CRUNCHER_OPF], ALL);
            }

            OPF_Options_Value (Option, Value)
            {
            OPF_DisLineEnforce YES
            OPF_DisIntEnforce NO
            OPF_ObjFunc 1
            }
```

---

<a id="analysis-phases"></a>

## Analysis Phases

*Source: [`Content/MainDocumentation_HTML/phaseAnalysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/phaseAnalysis.htm)*

After Snapshot processing is complete, Cruncher can run additional **Analysis phases** to evaluate system performance and identify potential violations. Two key phases are supported: *Analysis AUX* and *Contingency Analysis*. These phases provide flexibility to run custom scripts or detailed contingency studies on each Snapshot case.

### Analysis AUX Phase

The **Analysis AUX** phase allows Cruncher to execute custom AUX scripts after Snapshot creation but before Contingency Analysis. This enables users to apply additional configuration, calculations, or specialized study routines at the analysis stage.

#### Configuration Options

  - **Enable** — Toggles whether the Analysis AUX phase is run.
  - **Analysis AUX** — File or folder path pointing to one or more AUX scripts to execute during this phase.

### Contingency Analysis Phase

The **Contingency Analysis** phase allows Cruncher to run automated contingency studies on Snapshot cases, applying user-defined Contingency (CTG) and Remedial Action Scheme (RAS) lists. Results are collected across Snapshots to provide a comprehensive view of system performance under stressed conditions.

#### Configuration Options

  - **Enable** — Toggles whether Contingency Analysis runs.
  - **CTG List** — File or folder path to AUX or CSV files defining contingency specifications.
  - **RAS List** — File or folder path to AUX or CSV files defining RAS specifications.
  - **Use Dist** — Enables the use of distributed computing resources during contingency runs.
  - **Max Dist Procs** — Caps the number of distributed processes Cruncher will use. A value of 0 removes the cap and allows use of all available resources.

#### Phase Operation

1.  Load contingency and RAS definitions from specified input files.
2.  For each Snapshot case, run contingency analysis using Simulator’s CTG engine.
3.  If *Use Dist* is enabled, distribute computations across available resources up to the configured *Max Dist Procs*.
4.  Collect and save results, including solved/unresolved contingencies and any violations detected.

---

<a id="time-varying-csv-file-format"></a>

## Time-Varying CSV File Format

*Source: [`Content/MainDocumentation_HTML/timevaryingCSV.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/timevaryingCSV.htm)*

Many inputs to Cruncher use **Time-Varying CSV** files to describe values that change over time. This format provides a flexible and lightweight way to pass forecasts, weather data, or scheduled interface targets into Simulator. Each row in the file specifies a value for a particular object at a specific time.

### Core Structure

Each file must include the following elements:

  - **Object Header** — Column name in the form `<OBJECTTYPE>` (e.g. `<GEN>`, `<LOAD>`, `<AREA>`, `<ZONE>`, `<INTERFACE>`, or `<WEATHERSTATION>`). Identifies the device or aggregate object. The cells below should contain either the Simulator ObjectID or a valid Label identifying objects of the given type.
  - **DateTime** column — Timestamp for the row. Required in each file. Alternatively, use of either **DateTimeBegin** or **DateTimeEnd** explicitly tells Cruncher if the timestamps given should be interpreted as Interval Beginning or Interval Ending. Time zone can be explicitly specified by attaching a zone tag in angle brackets to this header (e.g. `DateTimeEnd<UTC>`). Current values explicitly supported include *UTC*, *US/Pacific*, *US/Mountain*, *US/Central*, and *US/Eastern*. Other time zones may be supported depending on your system.
  - **Value Fields** — One or more fields appropriate to the object type (e.g. `MW` for generators and loads, `GenMW`/`LoadMW` for areas, `TempC` for weather stations).

### Optional Columns

  - **Disable** — Marks a row to be ignored (`YES` disables; `NO` or blank keeps active).
  - **Any Other Header** — Any additional headers may be used for informational purposes; Cruncher will ignore them.

### Interval Convention

Cruncher must know whether a timestamp represents the *beginning* or *end* of the interval:

  - **Interval Beginning** — Value applies at this time and forward.
  - **Interval Ending** — Value applies up to this time.

This can be defined in the Cruncher configuration, or specified by the column header (`DateTimeBegin` or `DateTimeEnd`).

### Supported Fields

The following object types and fields are currently supported:

  - **Forecast Phase**
      - **GEN** — MW
      - **LOAD** — MW
      - **AREA** — GenMW, LoadMW
      - **ZONE** — GenMW, LoadMW
      - **INJECTIONGROUP** — GenMW, LoadMW, MW
  - **Weather Phase**
      - **WEATHERSTATION** — TempF, TempC, CloudCoverPerc, WindDirection, WindSpeedkmph, WindSpeedmph
  - **OPF Phase**
      - **INTERFACE** — LimitUsed

      - NOTE: any Interfaces with a LimitUsed value applied in a given Snapshot will also have its OPFEnforceEquality field set to YES

### Precedence Rules

When multiple files are applied, Cruncher follows a consistent order:

  - Individual object data (e.g. `<GEN>`, `<LOAD>`) are processed first.
  - Aggregate object data (e.g. `<AREA>`, `<ZONE>`, `<INJECTIONGROUP>`) are processed after.
  - If multiple files provide values for the same object, the file with higher priority in the Study or Snapshot configuration overrides lower-priority files.

### Example: Generator Forecast

``` 
            <GEN>,DateTime,MW
            GEN1,2025-09-09 06:00,150
            GEN1,2025-09-09 07:00,160
            GEN2,2025-09-09 06:00,200
            GEN2,2025-09-09 07:00,210

```

### Example: Area Load/Gen

``` 
            <AREA>,DateTime,GenMW,LoadMW
            1,2025-09-09 06:00,500,450
            1,2025-09-09 07:00,520,470

```

### Best Practices

  - Keep timestamp formatting consistent (ISO format `%Y-%m-%d %H:%M` is recommended).
  - If possible, use consistent time zones across all forecast files in a Study.
  - Group related files into directories for simpler configuration and re-use.

### See Also

  - [Weather Phase](#weather-phase)
  - [Forecasts Phase](#forecasts-phase)
  - [Optimal Power Flow Phase](#optimal-power-flow-opf-phase)
  - [Processing Phases](#processing-phases)

---

<a id="alarms"></a>

## Alarms

*Source: [`Content/MainDocumentation_HTML/Alarms.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Alarms.htm)*

The **Alarms** system in Cruncher provides automatic notifications and status tracking for running Studies and Schedules. When enabled, Cruncher writes JSON alarm files to a designated folder, allowing other applications or monitoring systems to detect study progress, warnings, or errors in near real time.

### Purpose

Alarms provide a lightweight way to monitor Cruncher activity without using the user interface. Each alarm file records the current state of a Study or Schedule and is updated as processing progresses. They can be consumed by external systems for status dashboards, workflow triggers, or automated reporting.

### Configuration

  - **Enable Alarms** — Global toggle that activates or deactivates the alarm system.
  - **Alarms Folder** — Directory where JSON alarm files are written. Each active Study or Schedule writes a separate file.
  - **Heartbeat Interval** — Defines how often Cruncher updates a small “heartbeat” file in the alarms folder. This allows external programs to detect if Cruncher has stopped or crashed unexpectedly.

### Alarm Files

Each alarm file is a JSON document describing the current execution state. The file name is derived from a hash of its contents ensuring uniqueness. The contents are a dictionary structure with the following values.

  - **TIMESTAMP** — Records when the Alarming event was triggered
  - **ALARM\_TYPE** — Denotes the specific type of Alarm
  - **MACHINE** — Gives the machine name the Alarming event occurred on
  - **SOURCE** — Gives the Study or Schedule name related to the Alarming event
  - **MESSAGE** — Contains any associated log message (if applicable)

#### Example Alarm File Structure

``` 
            {
            "TIMESTAMP": 1725898168.2709,
            "ALARM_TYPE": "STUDY_WARNING",
            "MACHINE": "my_workstation",
            "SOURCE": "Future Hour Ahead 0043",
            "MESSAGE": "load_forecast may contain stale data",
            }

```

### Alarm Types

Alarm Types can be enabled/disabled for individual Schedules/Studies based on a few general categories.

  - **Start**
      - **SCHEDULE\_STARTED** — Notification sent on a successful kick-off of a Scheduled run.
      - **SCHEDULE\_FAILED\_TO\_START** — An error occurred preventing a Scheduled run from starting.
  - **Warning**
      - **VALIDATION\_WARNING** — Validation Warning from automatic quick validation of a Schedule in advance of a run.
      - **STUDY\_WARNING** — Warning thrown during the execution of a Study.
  - **Error**
      - **VALIDATION\_ERROR** — Validation Error from automatic quick validation of a Schedule in advance of a run.
      - **STUDY\_CRUNCHER\_ERROR/STUDY\_SIMULATOR\_ERROR** — Error thrown during the execution of a Study; different types indicate if the error originated from a Cruncher process, or was passed back from Simulator during its processing.
  - **Completion**
      - **STUDY\_SNAPSHOTS\_COMPLETE** — Indication that Snapshot processing has completed.
      - **STUDY\_COMPLETE** — Indication that all processing has completed for a Study run (which may or may not have included Analysis).
  - **SIMAUTO\_ERROR** — SimAuto is critical to all of the processing Cruncher performs; errors related to SimAuto connections are critical to deal with quickly. If Alarms are enabled for a Schedule/Study, SimAuto errors are automatically reported.

### Heartbeat File

In addition to the individual alarm files, Cruncher can maintain a small “heartbeat” file named `.heartbeat` in the same directory. This file has not contents, but its Modification timestamp is updated at the interval specified by the Heartbeat setting confirming that Cruncher is still active. External monitors can use this file to detect unexpected shutdowns or stalled processes.

### Integration

Alarm and heartbeat files are designed to be easily parsed by other systems. They can be used to trigger automation scripts, send email alerts, update dashboards, or integrate with enterprise scheduling systems. Because they use standard JSON, they can be read by Python, PowerShell, or any language with a JSON parser.

---

<a id="dynamic-snapshot-analysis"></a>

## Dynamic Snapshot Analysis

*Source: [`Content/MainDocumentation_HTML/dynamicsnapshotAnalysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/dynamicsnapshotAnalysis.htm)*

**Dynamic Snapshot Analysis** is an experimental feature in Cruncher that helps users to prioritize which Snapshots should undergo full Contingency Analysis when computational resources are limited. By ranking and clustering Snapshot cases according to preconfigured or user-defined criteria, Dynamic Snapshot Analysis aims to identify those most likely to reveal system issues and groups similar Snapshots so that representative cases can be analyzed instead of the full set. Trial and error may be necessary to develop user-defined criteria that accurately identifies cases of particular interest.

### Purpose

Running full Contingency Analysis on every Snapshot can be computationally expensive. Dynamic Snapshot Analysis provides a decision-support layer, allowing users to focus processing effort where it matters most. This reduces study time while still capturing meaningful risk coverage.

### Methods

  - **TOPSIS Ranking** — Technique for Order Preference by Similarity to Ideal Solution. Produces a numerical index ranking Snapshots relative to ideal and worst-case conditions.
  - **OPTICS Clustering** — Ordering Points to Identify the Clustering Structure. Groups Snapshots by similarity so representative cases can be chosen for deeper analysis.

### Criteria

Dynamic Snapshot Analysis evaluates Snapshots based on three preset criteria and any user-specified custom criteria:

  - **High Voltage Risk** — Evaluates likelihood of bus voltages exceeding defined upper limits.
  - **Low Voltage Risk** — Evaluates likelihood of bus voltages falling below defined lower limits.
  - **Branch Limit Risk** — Evaluates likelihood of monitored branches nearing or exceeding their contingency limits.
  - **User-Specified Model Filters** — Apply filters to flag Snapshots with case characteristics of interest.
  - **User-Defined Criteria** — Defined by object type, field, and optional filter, allowing flexible customization of ranking and grouping.

### Outputs

Results from Dynamic Snapshot Analysis are included in both the Snapshot Report and the Analysis Report:

  - **Snapshot Report** — Displays criteria values, TOPSIS rankings, and OPTICS groupings for each Snapshot.
  - **Analysis Report** — Adds Contingency Analysis results to the above, enabling users to validate and refine the criteria’s predictive accuracy.

---

<a id="user-settings"></a>

## User Settings

*Source: [`Content/MainDocumentation_HTML/userSettings.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/userSettings.htm)*

The **User Settings** dialog provides application-wide configuration options that control how Cruncher behaves, where it stores outputs, and how information is displayed. These settings are stored in the user’s registry and persist across sessions.

### Processing

  - **Processing Cores**  
    Specifies how many SimAuto instances are started when the SimAuto manager connects. Click the CPU icon to select the maximum available on the machine. Changes only take effect after disconnecting and reconnecting the manager.
  - **Auto-start SimAuto**  
    When enabled, automatically connects the SimAuto manager at application startup .

### Timezones

  - **Use Timezone**  
    Overrides the machine’s system timezone with a user-specified timezone for the application .
  - **Default Input Timezone**  
    Sets a default timezone for reading Inputs when no timezone is specified in the Input configuration .

### Defaults Directory Locations

  - **Default Results**  
    Folder path to use as the Results location for newly created Studies .
  - **Default Archive**  
    Folder path to use as the Archive location for newly created Studies .
  - **Default Schedules**  
    File path pointing to a JSON file containing a set of Schedules. If specified, the schedules are automatically loaded on startup .

### Alarms

  - **Enable Alarms**  
    Top-level checkbox to enable or disable alarm generation for Studies and Schedules .
  - **Alarms**  
    Folder path specifying where alarm JSON files are exported .
  - **Heartbeat Interval**  
    Controls how often Cruncher updates a heartbeat file in the alarms location. External programs can use this file to detect if Cruncher has shut down improperly .

### Logging

  - **Log Window**  
    Sets how long logs remain in the application’s log window during extended runs .
  - **Text Log Directory**  
    Folder path where Cruncher writes plain text copies of log activity, including errors not handled by the GUI .

### Other

  - **Enable Save Checks**  
    When this setting is enabled, Cruncher will note to the user if they are closing a Study or Schedule dialog with unsaved changes.

### Display

Settings under this tab take effect the next time Cruncher starts up .

  - **Theme Scale**  
    Adjusts text scaling throughout the application .
  - **Default Color**  
    Sets the application’s accent color .
  - **Processing Color**  
    Color used to indicate an active process .
  - **Success Color**  
    Color used to indicate successful completion of a process .
  - **Warning Color**  
    Color used to indicate a warning during a process .
  - **Error Color**  
    Color used to indicate an error in a process .
  - **Restore Default Colors**  
    Resets all user-customized colors to the application defaults .
