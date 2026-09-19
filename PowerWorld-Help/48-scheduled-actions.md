---
title: "Scheduled Actions"
part: "Add-Ons"
chapter_file: "48-scheduled-actions.md"
topics: 5
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Scheduled Actions

The Scheduled Actions tool and its dialogs.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (5)**

- [Scheduled Actions Tool](#scheduled-actions-tool)
- [Scheduled Actions Dialog](#scheduled-actions-dialog)
- [Scheduled Action Group Dialog](#scheduled-action-group-dialog)
- [Scheduled Action Dialog](#scheduled-action-dialog)
- [Scheduled Action Status Dialog](#scheduled-action-status-dialog)

---

<a id="scheduled-actions-tool"></a>

## Scheduled Actions Tool

*Source: [`Content/MainDocumentation_HTML/Scheduled_Actions_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scheduled_Actions_Analysis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**The Scheduled Actions tools is only available if you have purchased the Schedule add-on to the base Simulator package. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information) for details about ordering the Schedule Add-on of Simulator.**

The Scheduled Actions Analysis tools provide the ability to visualize the combined effects of planned equipment outages. Actions (such as Open, Close, or manipulating object field values) can be scheduled, visualized, and applied to the system, allowing their compounded effects to be analyzed. Users can manually scroll over a specified time period or automatically animate the actions being applied over that window, and view a Gantt chart overview of all Scheduled Action Groups.

For more information on using the Scheduled Actions Tools, please refer to the [Scheduled Actions Dialog](#scheduled-actions-dialog) help page, or the pages for the related objects:

  - [Scheduled Action](#scheduled-action-dialog)
  - [Scheduled Action Group](#scheduled-action-group-dialog)
  - [Scheduled Action Status](#scheduled-action-status-dialog)

CROW CSV file import

PowerWorld can import CSV files exported from Control Room Operations Window (CROW) outage coordination software. Due to different device identification conventions, however, some specific labels must be created for applicable devices in the PowerWorld case to link them to the devices referenced in the CSV file. If you are interested in interfacing with CROW software, please contact PowerWorld for labeling instructions.

---

<a id="scheduled-actions-dialog"></a>

## Scheduled Actions Dialog

*Source: [`Content/MainDocumentation_HTML/Scheduled_Actions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scheduled_Actions_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Scheduled Actions Dialog is accessible from the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) Ribbon Tab: select **Scheduled Actions** from the **Schedule** Ribbon Group.

![ScheduledActionsDialog](images/ScheduledActionsDialog.png)

The upper portion of the dialog provides time controls, and the lower portion has tabbed case info displays giving access to relevant system objects and a Gantt chart display of configured action groups.

Time Controls

The top controls in the dialog relate to time. This includes the configuration of the timeframe of interest, the specific time to view, and system animation over the specified timeframe.

Start Time, End Time

These calendar controls define the timeframe of consideration. They defined the endpoints of the slider bar below them, and the bounds of the Gantt chart display.

View Time

This calendar control specifies the precise time to display. **View Time** can also be set by moving the slider below the calendar controls, or by moving single increments with the arrow buttons to the right of the slider.

Resolution

This defines the resolution of both the time slider and the Gantt chart display.

Animation

Configured actions can be animated automatically. Hitting the **Play** button animates the scheduled actions from the current **View Time** using the specified resolution, up until the set **End Time**. Each increment is displayed for the amount of time set in the **Animation** group here. The animation can be stopped at any time with the **Stop** button.

Save Snapshot

This button saves a copy of the case at the current **View Time**. This can be useful if further analysis is needed over a potentially problematic system state brought on by the scheduled actions.

Case Information Displays

Below the time controls is a tabbed panel with case information displays showing data for schedule-related system objects: [Scheduled Action Groups](#scheduled-action-group-dialog), [Scheduled Actions](#scheduled-action-dialog), and [Scheduled Action Statuses](#scheduled-action-status-dialog).

Gantt Chart

The **Gantt Chart** is a specialized case information display showing the overlap of **Scheduled Action Groups** over time. The display includes a column for each time increment defined by the **Start Time**, **End Time**, and **Resolution** settings. Each row corresponds to a Scheduled Action Group, with cells colored in if the group is active during the corresponding time increment. Inactive groups are displayed as well, but in red instead of blue.

Options

The Options tab provides a number of controls to customize Action application to the case

Apply Actions

If this box is checked, any actions which are currently active are applied to the case. Immediately after checking this option system state is stored for use in restoring at beginning of a time step; immediately after unchecking the stored system state is restored.

Use Normal Status

Restore normal status for any scheduled action that is not in the active range.

Apply All Within Resolution

**Resolution** defines how forward in time you are going to go. All actions within window from the current **View Time** to the **View Time** plus one **Resolution** step are considered active.

Evaluate Time Manually

Rather than automatically applying active Actions whenever the **View Time** changes, this option allows the user to selectively apply time points as they chose.

Load/Save

Load options from or Save options to an auxiliary file for easy consistent setup.

Check Conflicts

Check Conflicts button populates Conflicts field for a Scheduled Action with a string indicating that there is another action for the same device applying a different action.

Switch Disconnects to Normal Status in Open and Close Breakers Actions

This attempts to handle power flow cases that might have Disconnects at a status other than their normal status and Disconnects are not explicitly defined as part of the scheduled actions. Typically only Breakers are opened or closed when using the breaker actions, which could cause the final topology to be incorrect if disconnects are not in their normal status.

Identify Breakers

This tool allows the user to convert an Open or Close Breakers action into a set of individual Open/Close actions. These new actions can be identifies with the Origin field -- if the field has a value of "User", the action was user generated; if "Added", it is a breaker action added by the identification process; if "Extra", the object was identified as also being isolated/connected by breaker actions (these actions by default have their Allow Active field set to No, so they are present only for informational purposes)

---

<a id="scheduled-action-group-dialog"></a>

## Scheduled Action Group Dialog

*Source: [`Content/MainDocumentation_HTML/Scheduled_Action_Group_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scheduled_Action_Group_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Scheduled Action Groups allow collections of actions to be applied to the system over a specified time frame.

The following fields can be configured in the Scheduled Action Group Dialog:

Name

A unique identifier for the group.

Description

A human-readable description of this set of actions.

Start Time/End Time

Determines at what points this group of actions are applied and removed. These controls set the end-points of this group's bar on the Scheduled Action Gantt chart.

Status

[Scheduled Action Statuses](#scheduled-action-status-dialog) are organizational tags which can be classified as Active or Inactive. Action Groups with an Active status can be applied to the system, whereas groups with an Inactive status will only be displayed on the Scheduled Action Gantt chart.

![ScheduledActionGroupDialog](images/ScheduledActionGroupDialog.gif)

---

<a id="scheduled-action-dialog"></a>

## Scheduled Action Dialog

*Source: [`Content/MainDocumentation_HTML/Scheduled_Action_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scheduled_Action_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Scheduled Actions** are similar to the actions used in Contingency Analysis: they define a specific action that can be applied to a particular device.

Scheduled Action Group

The dropdown in the top-left corner sets which Scheduled Action Group owns this action. Start and End times are set through a Scheduled Action Group.

Device

Currently, four types of elements can be affected by Scheduled Actions: Branches, Shunts, Loads, and Generators. The type of element being targeted is set in the Element Type radio group, which populates the element chooser with all relevant system elements.

Action Type

Scheduled Actions are similar to actions in Contingency Analysis. Devices can be **Opened**, **Closed**, **Opened with Breakers**, or **Closed with Breakers**, and Generators can have a particular field **Set To** a value or **Changed By** a value.

![ScheduledActionDialog](images/ScheduledActionDialog.gif)

---

<a id="scheduled-action-status-dialog"></a>

## Scheduled Action Status Dialog

*Source: [`Content/MainDocumentation_HTML/Scheduled_Action_Status_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Scheduled_Action_Status_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

**Scheduled Action Statuses** are organizational tags to classify **Scheduled Action Groups**. A Scheduled Action Group with an **Active** status can be applied to the system with the [Scheduled Actions Dialog](#scheduled-actions-dialog); groups with **Inactive** statuses can be viewed in the Gantt Chart display in that dialog, but have no effect on the system at any time. The following Statuses are defined by default:

![ScheduledActionStatusesDefaults](images/ScheduledActionStatusesDefaults.gif)

Scheduled Action Status Dialog

The Scheduled Action Status dialog allows the name and active state of a Status to be set.

![ScheduledActionStatusDialog](images/ScheduledActionStatusDialog.gif)
