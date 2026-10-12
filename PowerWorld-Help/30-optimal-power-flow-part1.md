---
title: "Optimal Power Flow (OPF) (Part 1 of 2)"
part: "Add-Ons"
chapter_file: "30-optimal-power-flow-part1.md"
topics: 25
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Optimal Power Flow (OPF) (Part 1 of 2)

Optimal Power Flow: formulation, dialogs, controls, constraints and results.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (25)**

- [PowerWorld Simulator Optimal Power Flow  Overview](#powerworld-simulator-optimal-power-flow-overview)
- [OPF Objective Function](#opf-objective-function)
- [OPF Equality and Inequality Constraints](#opf-equality-and-inequality-constraints)
- [OPF Equality Constraints](#opf-equality-constraints)
- [OPF Inequality Constraints](#opf-inequality-constraints)
- [Determining Set of Active Inequality Constraints](#determining-set-of-active-inequality-constraints)
- [OPF Unenforceable Constraints](#opf-unenforceable-constraints)
- [OPF Marginal Costs](#opf-marginal-costs)
- [OPF Primal LP](#opf-primal-lp)
- [OPF Future Enhancements](#opf-future-enhancements)
- [OPF Options](#opf-options)
- [OPF Options - Common Options](#opf-options---common-options)
- [OPF Options - Constraint Options](#opf-options---constraint-options)
- [OPF Options - Control Options](#opf-options---control-options)
- [OPF Options - Advanced Options](#opf-options---advanced-options)
- [OPF Options - Solution Results](#opf-options---solution-results)
- [OPF Options - All LP Variables](#opf-options---all-lp-variables)
- [OPF Options - LP Basic Variables](#opf-options---lp-basic-variables)
- [OPF Options - LP Basis Matrix](#opf-options---lp-basis-matrix)
- [OPF Options - Bus MW Marginal Price Details](#opf-options---bus-mw-marginal-price-details)
- [OPF Options - Bus MVAR Marginal Price Details](#opf-options---bus-mvar-marginal-price-details)
- [OPF Options - Bus Marginal Controls](#opf-options---bus-marginal-controls)
- [OPF Options - Inverse of LP Basis](#opf-options---inverse-of-lp-basis)
- [OPF Options - Trace Solution](#opf-options---trace-solution)
- [OPF Area Records](#opf-area-records)

---

<a id="powerworld-simulator-optimal-power-flow-overview"></a>

## PowerWorld Simulator Optimal Power Flow  Overview

*Source: [`Content/MainDocumentation_HTML/Powerworld_Simulator_Optimal_Power_Flow_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Powerworld_Simulator_Optimal_Power_Flow_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Note: The OPF option in PowerWorld Simulator is only available if you have purchased the OPF add-on to the base package. To learn more about the OPF, please read through the information contained in these help files. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information) for details about ordering the OPF version of Simulator.

The PowerWorld Simulator (Simulator) is an interactive power system simulation package designed to simulate high voltage power system operation. In the standard mode Simulator solves the power flow equations using a Newton-Raphson power flow algorithm. However with the optimal power flow (OPF) enhancement, Simulator OPF can also solve these equations using an OPF. In particular, Simulator OPF uses a linear programming (LP) OPF implementation.

All of the OPF commands and options are accessed using the LP OPF main menu item. Other commands in this menu are used to specify input options, see results, and store/retrieve OPF specific data into auxiliary files.

The purpose of an OPF is to minimize an [objective (or cost) function](#opf-objective-function) by changing different [system controls](30-optimal-power-flow-part2.md#opf-controls) taking into account both [equality and inequality constraints](#opf-equality-and-inequality-constraints) which are used to model the power balance constraints and various operating limits.

In Simulator OPF the LP OPF determines the optimal solution by iterating between solving a standard power and then solving a linear program to change the system controls to remove any limit violations. See [OPF Primal LP](#opf-primal-lp) for more details.

---

<a id="opf-objective-function"></a>

## OPF Objective Function

*Source: [`Content/MainDocumentation_HTML/OPF_Objective_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Objective_Function.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The objective of the OPF algorithm is to minimize the OPF objective function, subject to various equality and inequality constraints. Since the objective of the OPF is to minimize an objective function, what objective function is used has a significant impact on the final solution.

Currently two objective functions are available in Simulator OPF: Minimum Cost and Minimum Control Change. Minimum Cost attempts to minimize the sum of the total control (generation, load, phase shifters, transactions, dc lines, and island slack bus angles) costs in specified areas or super areas. Minimum Control Change attempts to minimize the sum of the absolute values of the changes in the controls (generation, load, phase shifters, transactions, dc lines, and island slack bus angles) in the specified areas or super areas.

To include an area or super area in the OPF objective function, simply change the Area AGC Status field to "OPF" on the [OPF Area Records Display](#opf-area-records) or the Super Area AGC Status field to "OPF" on [the OPF Super Area Records Display](30-optimal-power-flow-part2.md#opf-super-area-records). This gives you great flexibility in defining the OPF study. For example you can set the OPF to minimize costs for the entire system, or just selected areas or super areas.

---

<a id="opf-equality-and-inequality-constraints"></a>

## OPF Equality and Inequality Constraints

*Source: [`Content/MainDocumentation_HTML/OPF_Equality_and_Inequality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Equality_and_Inequality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In solving a constrained optimization problem, such as the OPF, there are two general classes of constraints, equality and inequality. Equality constraints are constraints that always have to be enforced. That is, they are always "binding". For example in the OPF the real and reactive power balance equations at system buses must always be satisfied (at least to within a user specified tolerance); likewise the area MW interchange constraints. In contrast, inequality constraints may or may not be binding. For example, a line MVA flow may or may not be at its limit, or a generator real power output may or may not be at its maximum limit.

An important point to note is because the OPF is solved by iterating between a power flow solution and an LP solution, some of the constraints are enforced during the power flow solution and some constraints are enforced during the LP solution. The constraints enforced during the power flow are, for the most part, the constraints that are enforced during any power flow solution. These include the bus power balance equations, the generator voltage set point constraints, and the reactive power limits on the generators. What differentiate the LP OPF from a standard power flow are the constraints that are explicitly enforced by the LP. These include the following constraints:

[Equality Constraints](#opf-equality-constraints)

[Inequality Constraints](#opf-inequality-constraints)

---

<a id="opf-equality-constraints"></a>

## OPF Equality Constraints

*Source: [`Content/MainDocumentation_HTML/OPF_Equality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Equality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Area MW Interchange

The area MW interchange constraints are enforced during the LP for those areas that have an **AGC Status** equal to *OPF* provided the area is not part of a super area that is also set on AGC. The **AGC Status** field for an area can be set using the [OPF Area Records display](#opf-area-records), while the **AGC Status** field for the super area (if any) is set using the [OPF Super Area Records display](30-optimal-power-flow-part2.md#opf-super-area-records). Areas whose interchange is enforced during the LP do not have their interchange enforced during the power flow solution that is done as part of the LP process; during the power flow these areas are treated as though they were off of AGC (and hence the output of generators in that area is not varied during the power flow).

It is perfectly acceptable to have some areas on *OPF* AGC control and to have other areas on the more traditional power flow area AGC such as *ED* or *Part. AGC.* The interchange for such areas is controlled during the power flow solution.

Following a successful solution, marginal costs are calculated for the area interchange constraints; these values are displayed on the [OPF Area Records display](#opf-area-records) and can be contoured. See [OPF Marginal Costs](#opf-marginal-costs) for details.

Bus MW and Mvar power balance

Enforced during the power flow solution. Following a successful solution, marginal costs are calculated for the bus MW (real power) balance constraint; these values are displayed on the [OPF Bus Records display](30-optimal-power-flow-part2.md#opf-bus-records) and can be contoured.

Generator Voltage Setpoint

Enforced during the power flow solution. Following a successful solution, marginal costs are calculated for the voltage setpoint constraint; these values are displayed on the [OPF Bus Records display](30-optimal-power-flow-part2.md#opf-bus-records) .

Super Area MW Interchange

Super area interchange constraints are enforced similar to the area constraints. That is, super area interchange constraints are enforced during the LP only for those super areas that have an **AGC Status** equal to *OPF*. The **AGC Status** field can be set using [the OPF Super Area Records display](30-optimal-power-flow-part2.md#opf-super-area-records). During the power flow solution that is part of the LP process, such super areas are treated as though they were off of AGC.

Interface MW limits when treated as Equality

Interface MW limits are enforced during the LP solution. Interface MW limits are normally treated as inequality constraints (see [Inequality Constraints](#opf-inequality-constraints) ), however they can optionally be treated as equality constraints. See the [Interface Dialog](07-object-properties-run-mode-and-general-part2.md#interface-information) for information on how to treat the limit as an equality constraint.

Transmission Line and Transformer (Branch) MVA limits

Branch MVA limits are enforced during the LP solution. Branch MVA limits are normally treated as inequality constraints (see [Inequality Constraints](#opf-inequality-constraints) ), however they can optionally be treated as equality constraints. See the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information) for information on how to treat the limit as an equality constraint.

---

<a id="opf-inequality-constraints"></a>

## OPF Inequality Constraints

*Source: [`Content/MainDocumentation_HTML/OPF_Inequality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Inequality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following classes of inequality constraints are enforced during the OPF solution.

Generator real power limits

Generator real power limits are enforced during the LP solution.

Generator reactive power limits

Generator reactive power limits are enforced during the power flow solution.

Interface MW limits

Interface MW limits are enforced during the LP solution. In short, interface records are used to represent the aggregate flow through a number of different devices (see [Interface Records](05-case-information-displays-by-object-part3.md#interface-display) for details). During the LP the MW flow through the interface is constrained to be less than or equal to a user specified percentage of its limit, provided the interface is active for enforcement. For an interface to be active for enforcement the following three conditions must be met:

  - Interface enforcement must not be disabled for the case. This field can be set from either the [OPF Options and Results dialog](#opf-options---constraint-options) or the [OPF Interface Records display](30-optimal-power-flow-part2.md#opf-interface-records). The default is that case interface enforcement is not disabled. Also note that interface flow is limited to a percent of its limit as specified by the interface's [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).
  - Interface enforcement must be active for at least one of the interface's areas. Note, an interface is assumed to be in each area that contains at least one of its components. This field can be set from the [OPF Area Records display](#opf-area-records). The default is that interface enforcement is **not active**.
  - Enforcement must be active for each individual interface. This field can be set from [the OPF Interface Records display](30-optimal-power-flow-part2.md#opf-interface-records) or in the [Limit Monitoring Settings Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). The default is active.

Each interface that is active for enforcement is modeled as an inequality constraint, which may be either binding or not binding. If the constraint is not binding then it does not impact the solution. If a constraint is binding then it has an associated marginal cost of enforcement, which is shown on the [OPF Interface Records display](30-optimal-power-flow-part2.md#opf-interface-records).

Transmission Line and Transformer (Branch) MVA Limits

Transmission line and transformer (branch) MVA limits are enforced during the LP solution. During the LP the branch line flow is constrained to be less than or equal to a user specified percentage of its limit, provided the branch is active for enforcement. For a branch to be active for enforcement the following three conditions must be met:

  - Line/Transformer enforcement must not be disabled for the case. This field can be set from either the [OPF Options and Results dialog](#opf-options) or the [OPF Line/Transformer Records display](30-optimal-power-flow-part2.md#opf-linetransformer-records). The default is that case line/transformer enforcement is not disabled. Also note that the branch flow is limited to a percent of its limit as specified by the branche's [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).
  - Branch enforcement must be active for the branch's area. For tie-lines enforcement must be active for either area. This field can be set from the [OPF Area Records](#opf-area-records) display. The default is that branch enforcement is **not active**.
  - Enforcement must be active for each individual branch. This field can be set from the [OPF Line/Transformer Records display](30-optimal-power-flow-part2.md#opf-linetransformer-records) or in the [Limit Monitoring Settings Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). The default is active.

Each branch that is active for enforcement is modeled as an inequality constraint, which may be either binding or not binding. If the constraint is not binding then it does not impact the solution. If a constraint is binding then it has an associated marginal cost of enforcement, which is shown on the [OPF Line/Transformer Records display](30-optimal-power-flow-part2.md#opf-linetransformer-records).

Bus Angle

Specified bus angle values can be enforced during the LP solution. During the solution, the angle is constrained to be within a specified tolerance of this specified angle, provided the bus angle is active for enforcement. For a bus angle to be enforced, the following three conditions must be met:

  - Bus angle enforcement must not be disabled for the case. This field can be set from the [OPF Options and Results dialog](#opf-options). The default is that the case bus angle enforcement is disabled.
  - Bus angle enforcement must be active for the bus' area. This field can be set from the [OPF Area Records](#opf-area-records) display. The default is that bus angle enforcement is **not active**for an area.
  - Enforcement must be active for each individual bus. This is done by setting the Angle Tolerance to a large enough value. This field can be set from the [OPF Bus Records display](30-optimal-power-flow-part2.md#opf-bus-records). The default is the angles are not enforced.

---

<a id="determining-set-of-active-inequality-constraints"></a>

## Determining Set of Active Inequality Constraints

*Source: [`Content/MainDocumentation_HTML/Determining_Set_of_Active_Inequality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Determining_Set_of_Active_Inequality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A key issue in quickly solving the OPF is for the LP to effectively determine the set of active inequality constraints. Currently this includes the line MVA limits and the interface MW limits. Because the speed of the LP varies as the cube of the number of constraints active in the LP basis, it is extremely important to keep this number as small as possible. Therefore it would be very computationally prohibitive to setup an inequality constraint for each transmission line and interface (except in very small systems.)

The solution of setting up constraints **only** for those inequality constraints that are actually violating their limits is a step in the right direction, but suffers from the problem that during a solution a line may initially be violating its limit and then after the first iteration it is no longer violating. However if it is not subsequently included as a constraint during the next iteration the solution may simply oscillate between enforcing/unenforcing this constraint. This problem can be resolved by keeping that constraint in the basis even though it is no longer binding.

However this raises a question about how to handle these constraints during future OPF solutions. For example what would happen if a user solved the OPF, and then immediately resolved the OPF. Following the first solution the constraint would be enforced so that it may actually be less than its limit. However if this constraint is not included in the LP basis during the next solution the constraint may immediately violate during the first iteration, requiring a number of iterations just to return to the original initial solution.

Simulator solves this issue by keeping track of the enforced constraints from one solution to the next. Constraints are only removed from the basis if they the fall below a specified percentage of their limit. This percentage is enterable on the [Constraint Options page](#opf-options---constraint-options) of the [OPF Options and Results Dialog](#opf-options). This prevents the set of constraints in the basis from building up over time as a number of different system conditions (and hence constraints) are studied. Also, at any time this set of constraints can be cleared using the **Initialize OPF Button** on the [OPF Options and Results Dialog](#opf-options).

Also, the user is free to specify that a particular constraint **always** be included in the basis. This is done by toggling the **Constraint** field to "Always" on the [OPF Line/Transformer Records](30-optimal-power-flow-part2.md#opf-linetransformer-records) or [OPF Interface Records](30-optimal-power-flow-part2.md#opf-interface-records) displays.

---

<a id="opf-unenforceable-constraints"></a>

## OPF Unenforceable Constraints

*Source: [`Content/MainDocumentation_HTML/OPF_Unenforceable_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Unenforceable_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The goal of the LP OPF is to minimize the objective function subject to the user specified constraints. However there is no guarantee that it is even possible to simultaneously satisfy all of the specified constraints. In fact, it is quite easy to create a system in which all of the constraints **cannot** be enforced. A simple example is a two bus system consisting of a single generator supplying a single load through a transmission line. If the transmission line MVA rating is below the MVA of the load then it is impossible to supply this load while simultaneously satisfying the transmission line constraint. In Simulator OPF such a situation is known as an unenforceable constraint. In studying large systems, such as the U.S FERC 715 cases, such situations actually appear to be quite common. Seemingly unenforceable constraints are often due to a lack of controls available to the LP OPF or due to faulty limits entered in the case. In such cases unenforceable constraints can be corrected by making more controls available to the LP OPF or correcting the limits.

Simulator OPF allows you to solve systems with unenforceable constraints by only enforcing those constraints that have a marginal cost below a user specified tolerance. These tolerances are specified on the [OPF Options Constraint Options Page](#opf-options---constraint-options). Any constraints that have marginal costs above these values are not enforced, including any unenforceable constraints. This functionality is implemented in Simulator OPF through the use of slack variables. Slack variables are artificial variables introduced during the LP solution in order to satisfy the constraints with the slack variable costs equal to the user specified values. Then, during the LP solution the slack variables are usually removed from the LP basis. The only time this does not occur is if the constraint can not be enforced with a marginal cost less than the specified value. The number of unenforceable constraints are shown on the [OPF Option Solution Results Page](#opf-options---solution-results).

---

<a id="opf-marginal-costs"></a>

## OPF Marginal Costs

*Source: [`Content/MainDocumentation_HTML/OPF_Marginal_Costs.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Marginal_Costs.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

During any constrained minimization there is a cost associated with enforcing the equality constraints and the binding inequality constraints. These costs are known as the marginal costs.

In Simulator OPF marginal costs are calculated for the following record types:

Bus MW Equality Constraints

The Bus MW marginal costs tell the incremental cost to supply one additional MW of load at the specified bus. These values can be viewed on the [OPF Bus Records display](30-optimal-power-flow-part2.md#opf-bus-records); they can also be contoured or viewed on the one-lines using [bus fields](11-building-onelines-network-objects.md#bus-fields-on-onelines).

In the absence of any binding inequality constraints (such was Line MVA constraints) all of the bus marginal costs in an area should be identical. Bus marginal costs can only be determined for buses that are in areas or super areas on OPF control.

Bus Angle Constraints

The Angle Marginal Cost is the incremental cost to keep the angle at a bus within the specified enforcement tolerance. These values can be viewed on the [OPF Bus Records display](30-optimal-power-flow-part2.md#opf-bus-records).

Area MW Equality Constraints

The Area MW marginal costs tell the incremental cost for the specified area to import one additional MW of load **from the system slack bus.** These values can be viewed on [the OPF Area Records display](#opf-area-records); they can also be contoured or viewed on the one-lines [using area fields](11-building-onelines-network-objects.md#area-fields-on-onelines). In the absence of any binding inequality constraints the area MW marginal cost is identical to the bus MW marginal costs for all the buses in the area. When there are binding inequality constraints this is no longer the case.

Super Area MW Equality Constraints

The Super Area MW marginal costs are identical to the area marginal costs except they apply to super areas rather than areas.

Interface MW Constraints

The Interface MW marginal costs tell the incremental cost of enforcing the interface MW constraints. These values are only nonzero if the interface constraint is actually active (binding); they can be viewed using the [OPF Interface Records display](30-optimal-power-flow-part2.md#opf-interface-records).

Line/Transformer MVA Constraints

The Line/Transformer marginal costs tell the incremental cost of enforcing the line or transformer MVA constraint. These values are only nonzero if the line or transformer constraint is actually active; they can be viewed using the [OPF Line/Transformer Records display](30-optimal-power-flow-part2.md#opf-linetransformer-records).

---

<a id="opf-primal-lp"></a>

## OPF Primal LP

*Source: [`Content/MainDocumentation_HTML/OPF_Primal_LP.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Primal_LP.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **Primal LP** from the **OPF** ribbon group to solve the OPF using the primal LP algorithm.

In Simulator OPF the LP OPF determines the optimal solution by iterating between solving a standard power flow and then solving a linear program to change the system controls to remove any limit violations. The basic steps in the LP OPF algorithm are

1.  Solve the power flow
2.  Linearize the power system about the current power flow solution. Both constraints and controls are linearized.
3.  Solve the linearly-constrained OPF problem using a primal LP algorithm, computing the incremental change in the control variables. Slack variables are introduced to make the problem initially feasible. That is, the slack variables are used to satisfy the equality and inequality constraints. The slack variables typically have high costs so that during the iteration the slack variables change to satisfy the constraints. The LP then determines the optimal, feasible solution for the linear problem.
4.  Update the control variables and resolve the power flow.
5.  If the changes in the control variables are below a tolerance then the solution has been reached; otherwise go to step 2.
6.  Finish by resolving the power flow.

---

<a id="opf-future-enhancements"></a>

## OPF Future Enhancements

*Source: [`Content/MainDocumentation_HTML/OPF_Future_Enhancements.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Future_Enhancements.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

While we certainly plan on introducing additional functionality in future releases, we do want to be as clear as possible about what functionality is not currently provided.

The current version of Simulator OPF allows users to calculate the optimal solution to a power system using generator real power MW outputs and phase shifters as controls, while enforcing area, super area, interface MW and line/transformer MVA constraints. Marginal losses can also be included in the OPF calculation.

Some functionality that is **not** included in the current version of Simulator OPF, and which we hope to include in future versions, include the following:

  - Enforcing bus low/high voltage magnitudes as limits
  - Including additional devices as controls, such as generator voltage setpoints, LTC transformers, switched shunts.
  - Allowing the optimization of different cost functions.
  - Additional functionality as suggested by customers.

---

<a id="opf-options"></a>

## OPF Options

*Source: [`Content/MainDocumentation_HTML/OPF_Options_and_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_and_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Options and Results dialog allows you to customize the OPF solution. To display this dialog, go to the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab and select **Options and Results** from the **OPF** ribbon group. The dialog consists of three general pages; Options, Results and LP Solution Details.

The Options page has four tabs as well, [Common Options](#opf-options---common-options), [Constraint Options](#opf-options---constraint-options), [Control Options](#opf-options---control-options), and [Advanced Options](#opf-options---advanced-options)

The Results page has four tabs, [Bus MW Marginal Price Details](#opf-options---bus-mw-marginal-price-details), [Bus Mvar Marginal Price Details](#opf-options---bus-mvar-marginal-price-details), [Bus Marginal Controls](#opf-options---bus-marginal-controls), and [Solution Summary](#opf-options---solution-results).

The LP Solutions Page has five tabs, [All LP Variables](#opf-options---all-lp-variables), [LP Basic Variables](#opf-options---lp-basic-variables), [LP Basis Matrix](#opf-options---lp-basis-matrix), [Inverse of LP Basis](#opf-options---inverse-of-lp-basis), and [Trace Solution](#opf-options---trace-solution).

The dialog also has several buttons at the bottom of the display:

OK, Cancel

Select to close the dialog. Selecting **OK** saves your changes while **Cancel** does not. Note that changes are also saved anytime you select **Solve LP OPF** or **Single Outer Loop**.

Solve LP OPF

Solves the OPF using the Primal LP algorithm. Equivalent to selecting **** [Primal LP](#opf-primal-lp) from the **Optimal Power Flow** ribbon group on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab.

Single Outer Loop

Does a single outer loop of the Primal LP algorithm.

Initialize LP OPF

Returns the LP OPF variables to their original states.

Print

Prints the selected page of the dialog.

Help

Displays this help page. To view help for a particular page place the cursor on the page and press the F1 key.

---

<a id="opf-options---common-options"></a>

## OPF Options - Common Options

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Common_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Common_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The [OPF Dialog](#opf-options), Common Options page displays general options associated with the OPF solution. The display contains the following fields:

[Objective Function](#opf-objective-function)

Allows a choice of solving the LP using either a minimum cost or a minimum control change objective function.

OPF Reserves Options

These options are only available with the [OPF Reserves add-on](31-scopf-and-opf-reserves.md#optimal-power-flow-reserves-overview).

Include OPF Reserve Requirements

Check this box to include OPF reserve constraints in the OPF calculation.

Use a Single Control for Up/Down Regulation

Check this box to use a single bidirectional control for regulating reserve up or down. A unit will provide the same amount of regulating reserve up or down.

LP Control Variables

Disable All Phase Shifter Controls

Prevents phase shifters from attempting to control devices during the OPF solution.

Disable All Generator MW Controls

Prevents generators from shifting MW output during the OPF solution.

Disable All Load MW Controls

Prevents loads from shifting MW demand during the OPF solution.

Disable Area-to Area MW Transaction Controls

Prevents MW transactions between areas from being dispatched during the OPF solution.

Disable DC Transmission Line MW Controls

Prevents shifting of DC Transmission Line MW transfers during the OPF solution.

Disable D-FACTS Controls

Prevents adjusting D-FACTS devices during the OPF solution.

LP Options

Maximum Number of LP Iterations

Maximum number of allowable iterations for the LP portion of the LP OPF. How many iterations are required to obtain a solution depends, among other things, upon the number of breakpoints in the control cost models. Since each LP iteration can only move from one breakpoint to the next, the finer the model the more iterations required. However the LP is quite fast so a large number of iterations can be performed quite quickly. Default = 1000. Select *Treat Maximum LP Iterations Solutions as Valid* will treat the maximum number of iteration as a valid solution in the LP OPF.

Phase Shifter Cost ($ / Degree)

Specifies the assumed cost for moving phase shifting transformer taps away from their initial values. The purpose for this fictitious cost is approximate the cost of actually changing the angle of a phase shifting transformer, and to avoid large changes in phase shifter angles that have very little impact on the system. This field may be zero. Default = $ 0.10 / Degree.

Calculate Bus Marginal Cost of Reactive Power

When this option is checked, the OPF algorithm will also calculate the marginal cost of reactive power at each bus. Typically the result of interest from the OPF algorithm is the MW marginal cost of each bus (the LMP), but the MVAR marginal cost can be determined as well.

Save Full OPF Results in PWB File

When checked, Simulator will store the full set of results, including the LP matrix, in the PowerWorld Binary case file.

Do Detailed LP Logging

When checked, Simulator will write details on the LP algorithm solution during each pivot of the LP matrix. This is useful for debugging LP solution issues when running a LP OPF solution.

Start with Last Valid OPF Solution

When checked, Simulator will start the LP OPF solution process using the most recent OPF solution as the initial conditions.

Include only online devices in Injection Group calculation

When checked, the determination of the MW marginal costs for an injection group that are weighted by participation factors will only include those devices that are online. The MW marginal cost is associated with a bus, which means that it is possible for the bus to which a generator or load is attached to have a non-zero marginal cost even if the generator or load itself is open.

D-FACTS Cost ($/per unit X)

Specifies the assumed cost for adjusting the reactance of a D-FACTS device away from its initial value.

---

<a id="opf-options---constraint-options"></a>

## OPF Options - Constraint Options

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Constraint_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Constraint_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, Constraint Options page displays options associated with the enforcement of the constraints by the OPF. The display contains the following fields:

Line/Transformer Constraints

Disable Line/Transformer MVA Limit Enforcement

Select to disable enforcement of Line/Transformer MVA constraints for the entire case.

Percent Correction Tolerance

Specifies a tolerance for the enforcement of line/transformer MVA flows. The tolerance is necessary to prevent solution oscillations due to the non-linear nature of the actual constraints.

Violated elements are always enforced to their limits multiplied by the MVA Enforcement Percentage. If power systems were completely linear then following the LP solution the constraint would actually be equal to this value. However because of nonlinearities, the constraint is close to this value but usually not identical to the value. The Percent Correction Tolerance is used to tell the OPF how close is close enough. Provided all the constraints are violating their limits by less than the correction tolerance percentage the optimal solution is assumed to have been found. You may set this value as low as you like, but setting it too close to zero may result in convergence difficulties. The default is 2 percent.

MVA Auto Release Percentage

Specifies a MVA level at which transmission lines can be released as an OPF constraint equation if the branch MVA flow falls below the level specified.

Maximum Violation Cost ($/MWhr)

If a branch MVA limit cannot be enforced during an OPF solution, the branch will be assigned a fictitious cost of enforcement equal to this value. This value is usually rather large in order to easily determine where the unenforceable constraint is occurring. The default value is 1000 $/MWhr.

Enforce Line/Transformer MW Flow Limits (Not MVA)

Checking this box will cause Simulator to treat the limits of the transmission elements as MW limits instead of MVA limits. Thus Simulator will report violations on these elements in the OPF based on the MW flow of the element versus the element’s MVA rating.

Interface Constraints

Disable Interface MW Limit Enforcement

Select to disable enforcement of Interface MW constraints for the entire case.

Percent Correction Tolerance, MW Auto Release Percentage, Maximum Violation Cost ($/MWhr)

These fields are equivalent to the entries described above for Line/Transformer MVA Constraints except that they apply to Interface MW constraints.

Phase Shifting Transformer Regulation Limits

Disable Phase Shifter Regulation Limit Enforcement

Select to disable enforcement of Phase Shifter regulation limit constraints for the entire case.

For a phase shifter, there are two limits which can be enforced during the OPF—the MVA branch rating, and the regulation minimum and maximum MW flow. Checking this option will globally disable the enforcement of the regulation minimum and maximum MW flow for all phase shifters.

In Range Cost ($/degreehr)

The cost of changing a phase shifter angle away from zero degrees in $/degreehr, when the angle is within the allowable range of the phase shifter.

Maximum Violation Cost ($/MWhr)

If a phase shifter regulation limit cannot be enforced during an OPF solution, it will be assigned a fictitious cost of enforcement equal to this value. This value is usually rather large in order to easily determine where the unenforceable constraint is occurring. The default value is 1000 $/MWhr.

Bus Constraints

Disable Bus Angle Enforcement

Select to disable enforcement of Bus Angle limit constraints for the entire case.

Maximum Violation Cost ($/deg-h)

This field is equivalent to the entries described above for Line/Transformer MVA Constraints except that they apply to Bus Angle constraint. The default value is 1000 $/deg-h.

D-FACTS Constraints

Please contact PowerWorld for more information about these options.

Limit Monitoring Settings…

This button opens the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) dialog, which allows you to change the enforcement percentages for monitored elements.

Monitor/Enforce Contingent Interface Elements

This option cannot actually be set from this dialog, but it is important when including interfaces in the OPF solution. This option can be set on the Simulator Options dialog on the Power Flow Solution page under the [General tab](10-power-flow-solution-and-options-part2.md#power-flow-solution-general).

This option allows you to specify how contingency elements in an interface should be treated in Simulator. You can choose to never include the impact of contingent elements on interface flow, to only include contingent element impacts in the standard power flow or optimal power flow routines, or in all solution routines including contingency analysis and security constrained OPF.

It is not uncommon to ignore the impact of contingent elements when using the contingency analysis or security constrained OPF tools, as they are already processing lists of contingencies and evaluating flows on interfaces. Ignoring contingent elements within interface definitions allows for a determination of the impact of other contingencies on the flows of the non-contingent elements forming the interface, without impact from additional contingent element considerations.

---

<a id="opf-options---control-options"></a>

## OPF Options - Control Options

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Control_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Control_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The LP OPF Dialog, Control Options page displays options for generator control and power flow solution. The display contains the following options:

Generator Control Options

**Allow Commitment of Fast Start Generators**

If this option is checked, then generators designated as Fast Start generators can be turned on or "committed" if the OPF routine determines that doing so would reduce the overall generating costs of the system.

See the Fast Start description in the help on [OPF Generator Records](30-optimal-power-flow-part2.md#opf-generator-records) for a more detailed description of the Fast Start option of generators.

Allow Decommitment of Fast Start Generators

If this option is checked, then generators designated as Fast Start generators can be turned off or "de-committed" if the OPF routine determines that doing so would reduce the overall generating costs of the system.

See the Fast Start description in the help on [OPF Generator Records](30-optimal-power-flow-part2.md#opf-generator-records) for a more detailed description of the Fast Start option of generators.

Round to On Percentage if Min Limit

Generators designated as Fast Start generators will be turned On when the generator output is at the value specified by this option.

Modeling Generators without Piecewise Linear Cost Curves

The following fields specify how the OPF should handle generators that are specified as having a cubic cost model. Because the OPF is based upon an LP implementation, all control costs must be modeled using piecewise linear cost curves. These options permit an automatic conversion of cubic models to piecewise linear models. Alternatively, you can very easily convert the cubic models manually using the **\# Cost Curve Points** field on [the OPF Generator Records display](30-optimal-power-flow-part2.md#opf-generator-records) or using the [generator dialog](07-object-properties-run-mode-and-general-part1.md#generator-information).

Generators Cost Models

This field specifies how generators with cubic cost models should be handled in the OPF. The field has three values

**Ignore Them** -  Generators with cubic cost models are Ignored during the OPF solution. That is, they are considered as though their AGC status was off.

**Change to Specified Points per Curve** - A piecewise linear cost model is automatically inserted for the generator with a fixed number of points specified in the **Total Points Per Cost Curve** field described below. This curve will approximate the generator's cubic cost model as closely as possible; the existing cubic model is not modified. This is the default value.

**Change to Specified MWs per Segment -** A piecewise linear cost model is automatically inserted for the generator such that each segment in the cost model covers the amount of MWs specified in the **MWs per Cost Curve Segment** field described below. This curve will approximate the generator's cubic cost model as closely as possible; the existing cubic model is not modified.

Total Points Per Cost Curve

Specifies the total number of segments that should be automatically inserted into the piecewise linear cost models for those generators that are modeled using cubic cost functions. This is only done if the **Generator Cost Modeling** field is **Change to Specified Points per Curve.** Default = 5.

MWs per Cost Curve Segment

Specifies the number of MWs for each segment of the piecewise linear cost models that are automatically inserted for those generators that are modeled using cubic cost functions. This is only done if the **Generator Cost Modeling** field is **Change to Specified MWs per Segment**. Default = 10 MW.

Save Existing Piecewise Linear Cost Curves

Generators that are modeled with cubic cost curves may have existing piecewise linear cost curves which may have been manually entered by the user. These curves may or may not resemble the cubic cost function. During the OPF solution the existing piecewise linear cost curves are replaced with the auto-created cost curves. If this option is checked then the existing piecewise linear cost curves are restored at the end of the OPF. The default and recommended option is false since this allows one to view the actual cost curves used by the OPF.

If you would like to use a particular piecewise linear cost function simply make sure that the generator is modeled using the piecewise linear model, which can be set on the [OPF Generator Records](30-optimal-power-flow-part2.md#opf-generator-records) display.

Modeling of OPF Areas/Superareas

During the Initial OPF Power Flow Solution

Choose what manner of generation control you wish to be employed in the FIRST power flow solution the OPF will perform, which will establish the base case load flow condition for performing the subsequent OPF generation dispatch.

During Stand-Alone Power Flow Solutions

Choose what manner of generation control you wish to be employed in all load flow solutions FOLLOWING the initial load flow solution. In other words, after the LP OPF routine has determined the new generation dispatch, what type generation dispatch should be used during the normal load flow solution.

NOTE: it is NOT recommended that you use Economic Dispatch in this case, although it is an available option. The reason it is not recommended is that you will remove the optimal dispatch (including constraints) just determined by the OPF in favor of lowest cost economic dispatch, which will likely result in the re-introduction of overloaded elements that were corrected by the OPF dispatch in the first place.

Treat Area/Superarea MW Constraints as unenforceable even when the ACE is less than the AGC Tolerance (default is checked)

This option by default is checked, which means that if Simulator solves an OPF and the generators in an area or super area are all either at their minimum or maximum outputs, and the area control error is still not 0, then the area MW constraint is considered unenforceable and Simulator will assign a large penalty cost (usually $5,000/MWhr) to the LMP's of the area. However, if you deselect this option, you give Simulator the additional control of checking the ACE mismatch against the AGC tolerance for the area, and if the ACE mismatch is less than the AGC tolerance, Simulator will "acquire" the mismatch amount from the system slack bus for the area, and the area will not be considered unenforceable in the OPF solution. The AGC tolerance is usually small, and therefore the amount of power taken from the system slack bus will also be small. The purpose of this option is to allow for valid LMP solutions in an area that is meant to reach its full minimum or maximum generator capability, but that losses and numerical rounding results in the ACE mismatch deviating slightly from 0. It is not advised to uncheck this option if you have areas with large AGC tolerances.

---

<a id="opf-options---advanced-options"></a>

## OPF Options - Advanced Options

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Advanced_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Advanced_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Detection of LP Cycling

This option allows for advanced tweaking of when cycling is detected in the LP. It is recommended that users leave the default settings in place.

Minimum Number of Degenerate Iterations to Assume Cycling

To prevent inaccurate identification of cycling in the LP solution, the minimum number of degenerate iterations before cycling is identified can be specified manually in this box.

Minimum Number of Degenerate Iterations Multiplied by Number of Tableau Rows

To prevent inaccurate identification of cycling in the LP solution, the minimum number of degenerate iterations as a multiple of the number of tableau rows can be specified manually in this box.

Number of Sequential Degenerate Iterations for Last Case

This displays the number of degenerate iterations detected when performing the most recent OPF solution.

Power Flow Recalculation 

Choose one of the options to determine how often the power flow is resolved. The three options are, "When total generator MW change \> than tolerance"; "After each LP solution"; and "Only at end of LP OPF". If the power flow is not resolved, linear sensitivities are used to determine which constraints enter the LP tableau.

Total Generator Change Tolerance (MW)

Specifies the total generator change tolerance. The default is 500 MW.

After each LP solution

Resolves the power flow upon completion of each LP solution

Only at end of LP OPF

Resolves the power flow only after the LP OPF has completed.

---

<a id="opf-options---solution-results"></a>

## OPF Options - Solution Results

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Solution_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Solution_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, Solution Summary page displays general results from the last OPF solution. Click the **Save as Aux** button to save these results to a Simulator Auxiliary file.

The display contains the following fields, none of which can be directly changed:

General Results

Solution Start Time, Solution End Time

The starting time and ending time of the OPF solution algorithm.

Total Solution Time, Last Solution Status

Time and status of the last OPF solution.

Number of LP Iterations

Total number of LP iterations used during the last OPF solution. The maximum number of iterations is specified in the [Maximum Number of Iterations](#opf-options---common-options) field of the General Options page.

Initial Cost Function Value

Initial value of the [OPF cost function](#opf-objective-function). During the OPF the solution algorithm seeks to minimize the cost function, subject to the equality and inequality constraints.

Final Cost Function Value

Final value of the OPF cost function.

Final Slack Cost Value

The slack cost value is an artificial cost that is only non-zero when there are one or more unenforceable constraints.

Final Total Cost Value

The addition of the final cost function value and the final slack cost value.

Number of Buses in OPF

This field contains the total number of buses that are in areas or super areas that are on OPF control. Thus this field need not be equal to the total number of buses in the case. Marginal costs are only calculated for buses in OPF controlled areas or super areas.

Highest Bus Marginal Cost, Lowest Bus Marginal Cost, Average Bus Marginal Cost

Highest, lowest and average marginal cost for the buses that are in OPF controlled areas or super areas.

Bus MC Standard Deviation

The standard deviation of the Bus Marginal Cost.

Area and Superarea Constraints 

Unenforceable Area Constraints

Number of unenforceable area constraints.

Unenforceable Superarea Constraints

Number of unenforceable superarea constraints.

Line MVA Constraints

The **Line MVA Constraints** fields present results associated with the enforcement of the line MVA constraints.

Number of Initial Violations, MVA Sum of Initial Violations

Total number of lines that initially exceeded their MVA limits and were eligible for enforcement by the OPF. For these lines only, the **MVA Sum of Initial Violations** field contains sum of the absolute values of the line's actual MVA flow minus the line's MVA limit.

Number of Binding Lines

Total number of lines that are constrained to their limit value.

Highest Line MVA Marginal Cost

The highest Marginal Cost for an MVA change on a line.

Number of Unenforceable Violations

Total number of lines whose MVA flows can not be enforced by the OPF using the available controls.

MVA Sum of Unenforceable Violations

For all the unenforceable lines, this field contains the sum of the absolute values of the line's actual MVA flow minus the line's MVA limit.

Interface MW Constraints

The **Interface MW Constraints** field present results associated with the enforcement of the interface MW constraints.

Number of Initial Violations, MW Sum of Initial Violations

Total number of interfaces that initially exceeded their MW limits and were eligible for enforcement by the OPF. For these interfaces only, the **MW Sum of Initial Violations** field contains the sum of the absolute values of the interface's actual MW flow minus the interface's MW limit.

Number of Binding Interfaces

Total number of interfaces that are constrained to their limit value.

Highest Interface MW Marginal Cost

The highest Marginal Cost for an MVA change on an interface.

Number of Unenforceable Violations

Total number of interfaces whose MW flows can not be enforced by the OPF using the available controls.

MW Sum of Unenforceable Violations

For all the unenforceable interfaces, this field contains the sum of the absolute values of the interface's actual MW flow minus the interface's MW limit.

Generator MW Control Limit Violations

The **Generator MW Control Limit Violations** fields present results associated with the enforcement of the generator MW limit constraints.

Number of Initial Violations, MW Sum of Initial Violations

Total number of generators that initially exceeded their MW limits and were eligible for enforcement by the OPF. For these generators only, the **MW Sum of Initial Violations** field contains the sum of the absolute values of the generators’ actual MW output minus the generators’ MW limits.

Number of Unenforceable Violations

Total number of generators whose MW limits can not be enforced by the OPF using the available controls.

MW Sum of Unenforceable Violations

For all the generators with unenforceable limits, this field contains the sum of the absolute values of the generators’ actual MW output minus the generators MW limits.

Transformer Regulation Constraints

The **Transformer Regulation Constraints** fields present results associated with the enforcement of phase shifting transformer regulation.

Number of Initial Violations

Total number of phase shifting transformers that initially exceeded their MW set point limits and were eligible for enforcement by the OPF.

Number of Binding Constraints

Total number of phase shifting transformers that are set at their minimum or maximum regulation value.

Number of Unenforceable Violations

Total number of phase shifting transformers whose MW regulation limits can not be enforced by the OPF using the available controls.

Fast Start Generators

The **Fast Start Generators** fields present results associated with the commitment/decommitment of fast start generators.

Number of Generators Turned On

Total number of fast start generators turned on during the OPF solution

Number of Generators Turned Off

Total number of fast start generators turned off during the OPF solution

---

<a id="opf-options---all-lp-variables"></a>

## OPF Options - All LP Variables

*Source: [`Content/MainDocumentation_HTML/OPF_Options_All_LP_Variables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_All_LP_Variables.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, All LP Basic Variables page displays the basic and non-basic variables associated with the final LP solution. This page is usually only of interest to users interested in the specifics of the LP solution. Right click anywhere in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display lists each of the LP variables, showing the following fields for each:

ID

Variable identifier.

Original Value

The initial value of the LP variable before OPF optimization.

Value

The final value of the LP variable after OPF optimization.

Delta Value

The difference between the original value field and the value field.

BasicVar

Shows the index of the basic variables in the LP basis. If the value is zero, the variable is non-basic.

NonBasicVar

Shows the index of the non-basic variable. If the value is zero, the variable is basic.

Cost(Down)

The cost associated with decreasing the LP variable. The field will also show if the variable is at its max or min limit.

Cost(Up)

The cost associated with increasing the LP variable. The field will also show if the variable is at its max or min limit.

Down Range

The available range to decrease the basic variable before a new constraint is hit.

Up Range

The available range to increase the basic variable before a new constraint is hit.

Reduced Cost Up

The cost reduction that would be experienced if an LP variable increases. If a constraint is at the limit, the field shows the change in cost of constraint enforcement.

Reduced Cost Down

The cost reduction that would be experienced if an LP variable decreases. If a constraint is at the limit, the field shows the change in cost of constraint enforcement.

At Breakpoint?

Yes, if the LP variable is at a break point.

---

<a id="opf-options---lp-basic-variables"></a>

## OPF Options - LP Basic Variables

*Source: [`Content/MainDocumentation_HTML/OPF_Options_LP_Basic_Variables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_LP_Basic_Variables.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, LP Basic Variables page displays the basic variables associated with the final LP solution. This page is usually only of interest to users interested in the specifics of the LP solution. Right click anywhere in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display lists each of the basic variables, showing the following fields for each:

ID

Basic variable identifier.

Original Value

The initial value of the basic LP variable before the OPF optimization.

Value

The final value of the basic LP variable after the OPF optimization.

Delta Value

The difference between the original value field and the value of the basic variable.

Basic Var

Shows the indices of the basic variables in the LP basis.

Cost(Up)

The cost associated with increasing the basic variable.

Down Range

The available range to decrease the basic variable before a new constraint is hit.

Up Range

The available range to increase the basic variable before a new constraint is hit.

---

<a id="opf-options---lp-basis-matrix"></a>

## OPF Options - LP Basis Matrix

*Source: [`Content/MainDocumentation_HTML/OPF_Options_LP_Basis_Matrix.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_LP_Basis_Matrix.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, LP Basis Matrix page displays the basis matrix associated with the final LP solution. This page is usually only of interest to users interested in knowing the specifics of the LP solution. Knowing the basis matrix can be helpful in figuring out why a particular power system is exhibiting a particular behavior. The rows of the basis matrix are the binding constraints, while the columns of the basis matrix are the basic variables. The entries in the basis matrix then give the sensitivity of each constraint to each of the basic variables. The width of the columns in the matrix can also be adjusted using the **Column Widths** field. Finally, you can right-click anywhere in the matrix to copy the matrix to the Window's clipboard or to print the matrix.

---

<a id="opf-options---bus-mw-marginal-price-details"></a>

## OPF Options - Bus MW Marginal Price Details

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Bus_Marginal_Price_Details.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Bus_Marginal_Price_Details.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus MW Marginal Price Details page displays a grid containing the MW marginal prices computed for an OPF solution. If no OPF solution has been run, the values will all be zero. The grid used for displaying the information is a Case Information Display, which can be modified, sorted, printed, etc., as described in the discussion of [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays).

One key feature of this display is the breakdown in the bus MW marginal cost into three components: the cost of energy, the cost of congestion, and the cost of losses. Also, while the bus MW marginal cost does not change based on the reference, the costs of energy, congestion, and losses are reference dependent. This reference is set on a per-area (or per-super area) basis in the [Area information dialog OPF tab](07-object-properties-run-mode-and-general-part2.md#opf) (or the [Super Area information dialog OPF tab](07-object-properties-run-mode-and-general-part2.md#super-area-information)).

---

<a id="opf-options---bus-mvar-marginal-price-details"></a>

## OPF Options - Bus MVAR Marginal Price Details

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Bus_MVAR_Marginal_Price_Details.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Bus_MVAR_Marginal_Price_Details.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Bus MVAR Marginal Price Details page displays a grid containing the MVAR marginal prices computed for an OPF solution. If no OPF solution has been run, or if the option to compute MVAR marginal prices has not been selected, the values will all be zero. The grid used for displaying the information is a Case Information Display, which can be modified, sorted, printed, etc., as described in the discussion of [Case Information Displays](04-model-explorer-and-case-information-part1.md#case-information-displays).

---

<a id="opf-options---bus-marginal-controls"></a>

## OPF Options - Bus Marginal Controls

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Bus_Marginal_Controls.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Bus_Marginal_Controls.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This display shows the sensitivities of the controls with respect to the cost at each bus. A change in a system control will have the indicated effect in the marginal cost at the system buses. Vice-versa, the marginal cost at a bus is affected by changes in the value of the basic variables.

---

<a id="opf-options---inverse-of-lp-basis"></a>

## OPF Options - Inverse of LP Basis

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Inverse_of_LP_Basis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Inverse_of_LP_Basis.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, LP Basis Matrix page displays the inverse of the basis matrix. The width of the columns in the matrix can also be adjusted using the **Column Widths** field. Finally, right-click somewhere in the matrix to copy the matrix to the Window's clipboard or to print the matrix.

---

<a id="opf-options---trace-solution"></a>

## OPF Options - Trace Solution

*Source: [`Content/MainDocumentation_HTML/OPF_Options_Trace_Solution.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Options_Trace_Solution.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Dialog, Trace Solution page will trace the LP OPF of the Solution of either the basic variables values or all the store variable values. This page is usually only of interest to users interested in the specifics of the LP solution during the OPF run. By selecting *Do not trace solution*, no LP OPF solution will be tracked when performing an OPF. Right click anywhere in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display lists each of the basic variables, showing the following fields for each:

ID

Basic variable identifier.

---

<a id="opf-area-records"></a>

## OPF Area Records

*Source: [`Content/MainDocumentation_HTML/OPF_Area_Records.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Area_Records.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Displays OPF specific information about each area record in the case. To show this display select **Optimal Power Flow \> Results \> Areas** in the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) or **OPF Areas** from the **OPF Case Info** menu found in the **Optimal Power Flow (OPF)** ribbon group on the [Add Ons ribbon tab](02-simulator-ribbon.md#add-ons-tab-overview) while in Run mode. The OPF Area Records Display is a class of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and therefore can be used in a manner consistent with the other case information displays. Specific formatting options are available from the local menu, which can be accessed by right-clicking on any field in the display.

By default the display contains the following fields:

Number, Name

Area’s integer number and its alphanumeric identifier, 255 characters maximum.

AGC Status

Area's automatic generation control status. This is the same field shown on the [Area Records Display](05-case-information-displays-by-object-part1.md#area-display). The field indicates whether or not the area's generation is changing automatically to control the area interchange.

To be included in the OPF, this field MUST be *OPF*. The generation costs for areas that are on *OPF* control are included in the [OPF objective function](#opf-objective-function); otherwise they are not. Note that if the area is part of a super area that is on AGC control, this field value is ignored.

Double-click on the field to toggle its value.

XF Phase

Specifies whether phase shifting transformers in the area are available as controls. If *Yes* then all transformers in the area which have their Automatic Control Active are available for control; the Automatic Control status for a transformer is set on the [Branch Information Dialog](07-object-properties-run-mode-and-general-part1.md#linetransformer-information). If *No* then no transformers in the area are available for control.

Branch MVA

Specifies whether or not the MVA limits should be enforced for transmission lines and transformers that have at least one terminal in this area. For a transmission line or transformer to be included, Line/Transformer MVA Limit Enforcement must not be disabled on the [OPF Options and Results Dialog](#opf-options---constraint-options), and the individual line/transformer must be enabled for enforcement on the [OPF Line/Transformer display](30-optimal-power-flow-part2.md#opf-linetransformer-records).

Interface MW

Specifies whether or not the MW limits should be enforced for interfaces that have at least one element in this area. For an interface to be included, Interface MW Limit Enforcement must not be disabled on the [OPF Options and Results Dialog](#opf-options---constraint-options), and the individual interfaces must be enabled for enforcement on the [OPF Interface display](30-optimal-power-flow-part2.md#opf-interface-records).

Bus Angle

Specifies whether or not the specified bus angles should be enforced for buses in this area. For a bus to be included, Bus Angle Enforcement must not be disabled on the [OPF Options and Results Dialog](#opf-options---constraint-options), and the individual buses must be enabled for enforcement on the [OPF Buses display](30-optimal-power-flow-part2.md#opf-bus-records).

Load MW Dispatch

Specifies whether or not the MW load demand in an area should be included as available for re-dispatch during an OPF solution. In order for loads to be included in OPF re-dispatch, each individual load within the area must be available for control, and have either a fixed cost benefit or a piecewise-linear cost benefit curve provided. The option to Disable All Load MW Controls must also not be selected on the [OPF Options and Results Dialog](#opf-options---common-options).

DC Line MW Control

Specifies whether or not DC line MW setpoints can be modified for DC lines that have at least one terminal in this area. For a DC line to be included, DC Transmission Line MW Controls must not be disabled on the [OPF Options and Results Dialog](#opf-options---common-options).

Include Marg. Losses

Specifies whether or not marginal losses should be included for the area during the OPF solution.

MW Marg. Cost Ave

For an OPF solved case this field shows the average of the bus MW marginal costs for all the buses in the area. If there is no congestion then all of the marginal costs should be equal.

MW Marg. Cost St.Dev., Min., Max.

For an OPF solved case these fields show the standard deviation of the bus MW marginal costs for all the buses in the area, the minimum and the maximum bus MW marginal costs.

Report Limits

Specifies whether or not the kV limits should be reported. If this is set to *NO*, all of the other area options described above will be ignored because the area will not be included in any monitoring during the OPF.

Report Min kV, Report Max kV

Specifies the values for minimum and maximum kV levels to report. Defaults are 0 and 9999. This allows further determination of what elements that belong to the area will be included in the OPF enforcement. Only elements with nominal voltages in the specified Min/Max kV range will be included.
