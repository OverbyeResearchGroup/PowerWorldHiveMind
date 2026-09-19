---
title: "Security Constrained OPF and OPF Reserves"
part: "Add-Ons"
chapter_file: "31-scopf-and-opf-reserves.md"
topics: 29
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Security Constrained OPF and OPF Reserves

Security Constrained OPF and OPF Reserves.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (29)**

- [Security Constrained OPF Overview](#security-constrained-opf-overview)
- [SCOPF Objective Function](#scopf-objective-function)
- [SCOPF Dialog](#scopf-dialog)
- [SCOPF Solution Process](#scopf-solution-process)
- [SCOPF Results](#scopf-results)
- [SCOPF Equality and Inequality Constraints](#scopf-equality-and-inequality-constraints)
- [SCOPF Equality Constraints](#scopf-equality-constraints)
- [SCOPF Inequality Constraints](#scopf-inequality-constraints)
- [SCOPF Control](#scopf-control)
- [SCOPF CTG Violations](#scopf-ctg-violations)
- [SCOPF LP Solution Details](#scopf-lp-solution-details)
- [SCOPF All LP Variables](#scopf-all-lp-variables)
- [SCOPF LP Basic Variables](#scopf-lp-basic-variables)
- [SCOPF LP Basis Matrix](#scopf-lp-basis-matrix)
- [SCOPF Bus Marginal Price Details](#scopf-bus-marginal-price-details)
- [SCOPF Bus Marginal Controls](#scopf-bus-marginal-controls)
- [SCOPF Example: Introduction](#scopf-example-introduction)
- [SCOPF Example: Marginal Prices](#scopf-example-marginal-prices)
- [SCOPF Example: Unenforceable Constraints](#scopf-example-unenforceable-constraints)
- [Optimal Power Flow Reserves Overview](#optimal-power-flow-reserves-overview)
- [OPF Reserves Topics](#opf-reserves-topics)
- [OPF Reserves Controls](#opf-reserves-controls)
- [Generator and Load OPF Reserves Bids](#generator-and-load-opf-reserves-bids)
- [OPF Reserves Constraints](#opf-reserves-constraints)
- [Area and Zone OPF Reserve Requirement Curves](#area-and-zone-opf-reserve-requirement-curves)
- [OPF Reserves Objective Function](#opf-reserves-objective-function)
- [OPF Reserves Results and Pricing](#opf-reserves-results-and-pricing)
- [OPF Reserves Case Information Display](#opf-reserves-case-information-display)
- [OPF Reserves Example](#opf-reserves-example)

---

<a id="security-constrained-opf-overview"></a>

## Security Constrained OPF Overview

*Source: [`Content/MainDocumentation_HTML/Security_Constrained_OPF_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Security_Constrained_OPF_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Note: The SCOPF option in PowerWorld Simulator is only available if you have purchased the SCOPF and OPF add-ons to the base package. To learn more about the SCOPF, please read through the information contained in these help files. Contact PowerWorld Corporation for details about ordering the SCOPF and OPF versions of Simulator.

The [optimal power flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) (OPF) algorithm has the purpose of minimizing an objective function (usually total operation cost) by changing different system controls while meeting power balance constraints and enforcing base case operating limits. Normally however, the secure operation of a power system requires that there be no unmanageable contingency violations. Thus, the minimization of the objective function requires considering contingencies. This is achieved using a security constrained optimal power flow (SCOPF) algorithm.

While the [optimal power flow](30-optimal-power-flow-part1.md#powerworld-simulator-optimal-power-flow-overview) (OPF) algorithm determines the optimal state of the system by iterating between solving a power flow and solving a linear program that changes the system controls, during the [SCOPF solution process](#scopf-solution-process) in addition to solving the base case power flow, all contingencies must also be solved. The linear program which then runs changes the system controls to remove contingency violations as well as base case operating violations.

The SCOPF algorithm makes control adjustments to the base case (pre-contingency condition) to prevent violations in the post-contingency conditions. If enough controls are available in the system, the solution minimizes the [objective function](#scopf-objective-function) and the system enforces contingency violations. If the system does not have enough controls, then some violations may be persistent under certain contingencies. Those represent unenforceable constraints, which result in high bus marginal costs.

The commands and options for the SCOPF are accessed by selecting the **SCOPF** option from the **OPF** ribbon group on the [Add Ons](02-simulator-ribbon.md#add-ons-tab-overview) ribbon tab. The SCOPF function uses the OPF options defined in the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options) and the contingency settings specified in the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog). Please read through the OPF and the contingency analysis help for more information about these settings. We encourage you to become familiar with Simulator OPF and the contingency analysis tool before running SCOPF simulations. Other commands in the [SCOPF dialog](#scopf-dialog) are used to specify the base case solution process and for accessing the SCOPF results.

---

<a id="scopf-objective-function"></a>

## SCOPF Objective Function

*Source: [`Content/MainDocumentation_HTML/SCOPF_Objective_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Objective_Function.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SCOPF objective function uses the function defined in the OPF settings. There are two objective functions in Simulator: Minimum Cost and Minimum Control Change. Minimum Cost attempts to minimize the sum of the total generation costs in specified areas or super areas. Minimum Control Change attempts to minimize the sum of the absolute value of the change in the generation in the specified areas or super areas. The objective function is set up in the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options).

The result of the SCOPF will be different from the OPF solution because the SCOPF meets additional [inequality constraints](#scopf-inequality-constraints) associated with the contingency violations.

---

<a id="scopf-dialog"></a>

## SCOPF Dialog

*Source: [`Content/MainDocumentation_HTML/SCOPF_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SCOPF dialog allows the user to control options of Security Constrained OPF, as well as to access the optimization results.

The SCOPF can be run from this dialog using the **Run Full Security Constrained OPF** button at the top of the form.

There are three pages of information included in this form:

[Options](#scopf-control)

[Results](#scopf-results)

[LP Solution Details](#scopf-lp-solution-details)

---

<a id="scopf-solution-process"></a>

## SCOPF Solution Process

*Source: [`Content/MainDocumentation_HTML/SCOPF_Solution_Process.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Solution_Process.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SCOPF involves three major steps that can be solved either automatically or manually from the SCOPF control dialog:

  - Initialization to setup the SCOPF LP tableau and the control structures
  - Contingency analysis calculation and storage of control sensitivities associated with each contingency violation
  - SCOPF iterations, which include an LP solution and a power flow solution. During each LP step in the LP routine, the algorithm enforces the newest most severe contingency violation. After each violation is processed, all of the unprocessed violations are updated. This step is crucial since often resolving the most severe violation resolves numerous other violations. For instance, a single line might be overloaded in a number of contingencies: fixing the worst contingency fixes the others as well. On the other hand, processing some violations may result in new violations. In order to verify that no new violations have been created by the control changes made, the SCOPF will go back to step two and reprocess all the contingencies and the new base solution. The number of times this iteration occurs is determined by the Maximum Number of Outer Loop Iterations.

The SCOPF terminates when all the contingency violations have been processed. Note that the user can rerun the SCOPF by repeating the solution process if they want to verify the contingency violation enforcement at the new optimal operating point.

---

<a id="scopf-results"></a>

## SCOPF Results

*Source: [`Content/MainDocumentation_HTML/SCOPF_Results.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Results.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Results page of the [Security Constrained Optimal Power Flow](#scopf-dialog) form provides information on the results of the latest SCOPF solution, including the [contingency violations](#scopf-ctg-violations) included, the [marginal price details](#scopf-bus-marginal-price-details), and the [marginal control details](#scopf-bus-marginal-controls).

---

<a id="scopf-equality-and-inequality-constraints"></a>

## SCOPF Equality and Inequality Constraints

*Source: [`Content/MainDocumentation_HTML/SCOPF_Equality_and_Inequality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Equality_and_Inequality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Two general types of constraints are involved in the SCOPF solution: equality and inequality constraints. Equality constraints are constraints that have to be enforced. That is, they are always "binding". For example in the SCOPF, as well as in the OPF and in the power flow, the real and reactive power balance equations at system buses must always be satisfied (at least to within a user specified tolerance). In contrast, inequality constraints may or may not be binding. For example, a line MVA flow under a certain contingency may or may not be at its limit.

The SCOPF problem is solved by iterating between a power flow solution and a contingency constrained LP solution, some of the constraints are enforced during the power flow solution and some constraints are enforced during the LP solution. The constraints enforced during the power flow are, for the most part, the constraints that are enforced during any power flow solution. These include the bus power balance equations, the generator voltage set point constraints, and the reactive power limits on the generators. What differentiates the SCOPF from a standard power flow and from the OPF are the constraints that are explicitly enforced by the LP solver. These include the following constraints:

[Equality Constraints](#scopf-equality-constraints)

[Inequality Constraints](#scopf-inequality-constraints)

---

<a id="scopf-equality-constraints"></a>

## SCOPF Equality Constraints

*Source: [`Content/MainDocumentation_HTML/SCOPF_Equality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Equality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SCOPF equality constraints are the same as the [OPF equality constraints](30-optimal-power-flow-part1.md#opf-equality-constraints): Area MW interchange, bus MW and Mvar power balance, Generator voltage setpoint and super area MW interchange.

---

<a id="scopf-inequality-constraints"></a>

## SCOPF Inequality Constraints

*Source: [`Content/MainDocumentation_HTML/SCOPF_Inequality_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Inequality_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following classes of inequality constraints are enforced during the SCOPF solution.

Generator real power limits

Generator real power limits are enforced during the SCOPF LP solution.

Generator reactive power limits

Generator reactive power limits are enforced during the SCOPF LP solution.

Interface MW Limits

Interface MW limits are enforced during the SCOPF solution. [Interfaces](07-object-properties-run-mode-and-general-part2.md#interface-information) are used to represent the aggregate flow through a number of different devices. During the SCOPF the MW post-contingency flow through the interface is constrained to be less than or equal to a user specified percentage of its limit, provided the interface is active for enforcement. For an interface to be active for enforcement the following three conditions must be met:

  - Interface enforcement must not be disabled for the case. This field can be set from either the [OPF Constraints Dailog](30-optimal-power-flow-part1.md#opf-options---constraint-options) or the [OPF interfaces records](30-optimal-power-flow-part2.md#opf-interface-records). As default, the interface enforcement is not disabled. Note that interface flow is limited to a percent of its limit as specified by the interface's [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).
  - Interface enforcement must be active for at least one of the interface's areas. Note, an interface is assumed to be in each area that contains at least one of its components. This field can be set from the [OPF Area Records display](30-optimal-power-flow-part1.md#opf-area-records). Note: the default is that interface enforcement is not active, so be sure to activate this if you want these constraints enforced.
  - Enforcement must be active for each individual interface. This field can be specified from the OPF interfaces records display or in the [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings) dialog. The default is active.

Each interface that is active for enforcement is modeled as an inequality constraint, which may be either binding or not binding. If the constraint is not binding then it does not impact the solution. If a constraint is binding then it has an associated marginal cost of contingency enforcement. When manually solving the SCOPF one can skip a contingency violation associated to the interface by setting the Include field of the [SCOPF CTG Violations](#scopf-ctg-violations) dialog to **No**.

Transmission Line and Transformer (Branch) MVA Limits

Transmission line and transformer (branch) MVA limits are enforced during the SCOPF solution. During the LP the post-contingency branch line flow is constrained to be less than or equal to a user specified percentage of its limit, provided the branch is active for enforcement. For a branch to be active for enforcement the following three conditions must be met:

  - Line/Transformer enforcement must not be disabled for the case. This field can be set from either the [OPF constraints dialog](30-optimal-power-flow-part1.md#opf-options---constraint-options) or the [OPF Line/Transformer Records](30-optimal-power-flow-part2.md#opf-linetransformer-records) display. The default is that case line/transformer enforcement is not disabled. Also note that the branch flow is limited to a percent of its limit as specified by the branch's [Limit Monitoring Settings](18-general-tools.md#limit-monitoring-settings).
  - Branch enforcement must be active for the branch's area. Enforcement for tie-lines must be active for either area. This field can be set from the [OPF Line/Transformer Records](30-optimal-power-flow-part2.md#opf-linetransformer-records) display. The default is that branch enforcement is not active, so be sure to activate this if you want these constraints enforced.
  - Enforcement must be active for each individual branch. This field can be set from the [OPF Line/Transformer Records](30-optimal-power-flow-part2.md#opf-linetransformer-records) display or in the [Limit Monitoring Settings Dialog](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog). The default is active.

Each branch that is active for enforcement is modeled as an inequality constraint, which may be either binding or not binding under contingency conditions. If the constraint is not binding then it does not impact the solution. If a constraint is binding then it has an associated marginal cost of enforcing the contingency constraint, which is shown on the [SCOPF Bus Marginal Price Details](#scopf-bus-marginal-price-details) dialog. When manually solving the SCOPF one can skip a contingency violation associated to the branch by setting the Include field of the [SCOPF CTG Violations](#scopf-ctg-violations) dialog to **No**.

---

<a id="scopf-control"></a>

## SCOPF Control

*Source: [`Content/MainDocumentation_HTML/SCOPF_Control.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Control.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The control dialog allows the user to manually or automatically run a SCOPF simulation and visualize the execution of the simulation. The [SCOPF solution process](#scopf-solution-process) involves three steps: base case solution and initialization, contingency analysis, and SCOPF iterations.

Run Full Security Constrained OPF

Press this button to run the three steps of the SCOPF solution automatically. The SCOPF will solve the base case using the selected method, will use the currently stored list of contingencies during the contingency analysis step, and will take the CA results and sensitivities to iterate in order to obtain the optimal solution that minimizes cost and enforces contingency violations.

Options

Maximum Number of Outer Loop Iterations

Indicates the number of maximum outer loop iterations. The outer loop iterations determines how many times the contingency analysis will be re-run following a successful SCOPF dispatch. In this manner, Simulator will look for new violations that may occur due to the new generation dispatch.

Consider Binding Contingent Violations from Last SCOPF Solution

When checked, this option ensures that the contingent violations from the last SCOPF solution are included in the current SCOPF solution. This option is helpful in preventing the SCOPF from hunting between having a constraint binding in one solution, and resolving with it not binding in a later solution because it was previously remedied. This option should generally always be checked, unless the user is sure that the previous solution has no bearing on the current solution, such as having made major changes to the system since the previous solution.

Initialize SCOPF with Previously Binding Constraints

When checked, this option results in the SCOPF solution process starts with the exact same LP tableau from the last solution. This can make for fairly fast solutions (recognizing that the contingency analysis needs to be resolved) when the changes to the system are small. Simulator automatically uses this option when doing multiple outer loops of the SCOPF. This option allows the user to solve the outer loops (set the outer loop counter to 1) by repeatedly solving the SCOPF manually, potentially making modifications between solutions if desired.

Set Solution as Contingency Analysis Reference Case

Check this field to set the solution of the SCOPF as the contingency analysis reference. If the system has enough controls to remove all the contingency violations, a rerun of the contingency [analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview) using the SCOPF solution as the reference should report no branch violations.

Maximum Number of Contingency Violations Allow Per Element

Specify the maximum number of contingency violations that the SCOPF analysis should allow per element. After completing the power flow solutions for the base case and the contingencies, only this number of contingency violations per element are then passed to the linear programming algorithm. The assumption is that if you fix the 10 worst contingency violations for an element then the others will also be fixed.

Basecase Solution Method

Specifies whether the solution of the base case is performed using the power flow algorithm or the optimal power flow algorithm. The selection will affect the initial conditions of the system and consequently the contingency analysis results and the sensitivities used by the LP solver. Currently the SCOPF does not resolve the contingency analysis during the optimization since this is computationally expensive. See the [SCOPF solution process](#scopf-solution-process) for details.

Handling of Contingent Violations Due to Radial Load

It is often common when computing a security constrained OPF to have violations occur on branches due to radial load. In these instances, there is no way to adjust controls to continue to serve the load, without overloading the serving element. Therefore you can choose how contingent violations of this type should be handled by the SCOPF. You can choose to flag them but not include them in the SCOPF, ignore them completely, or include the violations in the SCOPF. Note that if you include the violations in the SCOPF, the SCOPF algorithm will not be able to remove the violation on the element via generation dispatch. However, it may be able to do so if the load in question has a load benefit curve defined and is available for load shed dispatch in the SCOPF routine.

DC SCOPF Options

The DC options given for the SCOPF revolve around the treatment of Line Outage Distribution Factors (LODF) during the DC SCOPF solution. You can choose to discard the LODFs when the SCOPF is finished or store them in memory (lost when Simulator is closed).

If the LODFs have been stored and you wish to clear them (they can require quite a bit of RAM depending on the number of contingencies and size of the case,) you can press the button labeled **Clear Stored Contingency Analysis LODFs**.

SCOPF Results Summary

Number of Outer Loop Iterations

The number of outer loop iterations required to solve the SCOPF.

Number of Contingent Violations

Number of violations from the contingency analysis portion of the solution, which are used to attempt to determine the security constrained dispatch.

SCOPF Start Time, SCOPF End Time

Physical time when the SCOPF solution process started and finished.

Total Solution Time (Seconds)

Length of time needed to determine the SCOPF solution.

Total LP Iterations

Total number of Linear Programming iterations necessary to determine the SCOPF solution.

Contingency Analysis Input

Number of Active Contingencies

The number of contingencies included in the SCOPF simulation. Specific contingencies may be excluded from the simulation in the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) by changing the skip field of a contingency to YES. The contingency analysis dialog can be conveniently accessed from the SCOPF control dialog.

View Contingency Analysis Form

Clicking this button shows the [contingency analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog).

Contingency Analysis Results

This window allows the user to monitor the details of the contingency analysis step. During contingencies, the outage actions, the solution of each contingency, and the solution of the CA run are reported.

---

<a id="scopf-ctg-violations"></a>

## SCOPF CTG Violations

*Source: [`Content/MainDocumentation_HTML/SCOPF_CTG_Violations.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_CTG_Violations.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The contingency violations page is available from the Results tab of the [Security Constrained Optimal Power Flow](#scopf-dialog) form. The display lists the results from the latest contingency analysis run including the violations that were included in the SCOPF and the final error for each violation. This dialog may change if the user reruns the SCOPF by solving the contingency analysis using the SCOPF solution as contingency analysis reference. Right click any where in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display shows the following fields:

Contingency Name

This is the contingency label. By default single line contingencies start with an "L", single generator outages with a "G", and single transformer outages start with an "X".

Category

Currently, the SCOPF considers only branch and interface violations. Thus, the category of the contingencies should be branch MVA or Interface.

Element

Shows information about the specific element that presented the violation. When the violation occurs in a branch, this column includes the identifiers of the sending and receiving ends of the branch, the circuit, and the direction of the violating flow. Since Interfaces are directed, this field will present only the interface name in the case of violating interfaces.

Value

The percentage flow that appears in the branch during the contingency prior to optimization. If this number is larger than the scaled limit, the violation needs to be removed.

Scaled Limit

The scaled limit corresponds to the Line/Transformer Percentage specified in the [limit monitoring settings](18-general-tools.md#limit-monitoring-settings) dialog. By specifying this limit to be higher than 100% some of the contingency violations might be effectively relaxed. Sometimes this helps the OPF and the SCOPF obtain a feasible solution. On the other hand, it is often required to analyze the performance of the system if branches would have higher ratings.

New Value

The percentage flow that appears in the branch during the contingency after SCOPF optimization. If this number is larger than the scaled limit, the contingency violation has not been removed and it is therefore unenforceable. If the value is equal to the scaled limit, then the contingency violation constraint would be binding. If the value is smaller than the scaled limit, the contingency violation has been removed.

Error

The difference between the new value and the scaled limit. If the error is positive, the line is unenforceable. If the error is zero, the constraint has been corrected.

Included

Indicates if the contingency violation was included as a constraint in the SCOPF solution.

Marginal Cost

Indicates the cost associated with the contingency violation. If the constraint is unenforceable, the marginal cost is assigned arbitrarily as a high value in the [OPF constraint options](30-optimal-power-flow-part1.md#opf-options---constraint-options) dialog.

Unenforceable

Indicates whether the contingency violations is unenforceable, i.e., the system has not enough controls to relieve the branch overload when the contingency occurs.

Skip Violation?

Change this field to NO if the contingency violations should not be included as a SCOPF constraint. This is sometimes useful in order to analyze the effect of the contingency violation in the SCOPF solution. This field may be toggled when doing a manual SCOPF solution.

---

<a id="scopf-lp-solution-details"></a>

## SCOPF LP Solution Details

*Source: [`Content/MainDocumentation_HTML/SCOPF_LP_Solution_Details.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_LP_Solution_Details.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The LP Solution Details page of the [Security Constrained Optimal Power Flow](#scopf-dialog) form provides information on the linear program solution of the SCOPF, including a list of [All LP Variables](#scopf-all-lp-variables), [LP Basic Variables](#scopf-lp-basic-variables), and [LP Basis Matrix](#scopf-lp-basis-matrix). This information applies to the linear programming tableau solution method.

---

<a id="scopf-all-lp-variables"></a>

## SCOPF All LP Variables

*Source: [`Content/MainDocumentation_HTML/SCOPF_All_LP_Variables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_All_LP_Variables.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The SCOPF All LP Variables dialog displays the basic and non-basic variables associated with the final LP SCOPF solution. Users interested in the specifics of the LP SCOPF can access this page to obtain internal information about the SCOPF solution. To see the display, open the [Security Constrained Optimal Power Flow](#scopf-dialog) form, click on the LP Solution Details tab, and access the All LP Variables page.

Right click any where in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display lists each of the LP variables with the following fields:

ID

Variable identifier.

Org. Value

The initial value of the LP variable before SCOPF optimization.

Value

The final value of the LP variable after SCOPF optimization.

Delta Value

The difference between the original value field and the value field.

Basic Var

Shows the index of the basic variables in the LP basis. If the value is zero, the variable is non-basic. These values are set up after the SCOPF calculates the contingency violation sensitivities.

NonBasicVar

Shows the index of the non-basic variable. If the value is zero, the variable is basic.

Cost(Down)

The cost associated with decreasing the LP variable. The field will show if the variable is at its max or min limit.

Cost(Up)

The cost associated with increasing the LP variable. The field will show if the variable is at its max or min limit.

Down Range

The available range to decrease the basic variable before a new constraint is hit under a contingency condition.

Up Range

The available range to increase the basic variable before a new constraint is hit under a contingency condition.

Reduced Cost Up

The cost reduction that would be experimented if a LP variable increases. If a constraint is at the limit, the field shows the change in cost of constraint enforcement.

Reduced Cost Down

The cost reduction that would be experimented if a LP variable decreases. If a constraint is at the limit, the field shows the change in cost of constraint enforcement.

At Breakpoint

Yes, if the LP variable is at a break point.

---

<a id="scopf-lp-basic-variables"></a>

## SCOPF LP Basic Variables

*Source: [`Content/MainDocumentation_HTML/SCOPF_LP_Basic_Variables.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_LP_Basic_Variables.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The LP Basic Variables (from the SCOPF [LP Solution Details](#scopf-lp-solution-details) page) displays the basic variables of the final LP solution. The basic variables may correspond to controls that can be altered to minimize the objective function, or slack variables associated with unenforceable constraints. Users interested in the specifics of the LP SCOPF can access this page to obtain internal information about the SCOPF solution. Right click any where in the display to copy a portion or all of the display to the Window's clipboard, or to print the results.

The display lists each LP variable with the following fields:

ID

Basic variable identifier.

Org. Value

The initial value of the basic LP variable before the SCOPF optimization.

Value

The final value of the basic LP variable after the SCOPF optimization.

Delta Value

The difference between the original value field and the value of the basic variable.

Basic Var

Shows the indices of the basic variables in the LP basis.

Cost(Up)

The cost associated with increasing the basic variable.

Down Range

The available range to decrease the basic variable before a new constraint is hit under a contingency condition.

Up Range

The available range to increase the basic variable before a new constraint is hit under a contingency condition.

---

<a id="scopf-lp-basis-matrix"></a>

## SCOPF LP Basis Matrix

*Source: [`Content/MainDocumentation_HTML/SCOPF_LP_Basis_Matrix.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_LP_Basis_Matrix.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The LP Basis Matrix page of the SCOPF [LP Solution Details](#scopf-lp-solution-details) tab displays the basis matrix associated with the final SCOPF LP solution. There is one row per constraint and one column per basic variable. Additional columns summarize information associated with each constraint. This page is usually only of interest to users interested in knowing the specifics of the SCOPF solution. Knowing the basis matrix can be helpful in figuring out why a particular SCOPF solution exhibits a certain behavior. The entries in the basis matrix give the sensitivity of each constraint to each of the basic variables.

As any case info display in simulator, right click to see options to copy information to the clipboard and to perform standard windows actions, such as printing.

---

<a id="scopf-bus-marginal-price-details"></a>

## SCOPF Bus Marginal Price Details

*Source: [`Content/MainDocumentation_HTML/SCOPF_Bus_Marginal_Price_Details.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Bus_Marginal_Price_Details.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This display (from the SCOPF [Results](#scopf-results) page) shows information about the components of the marginal cost at each bus. The display is relevant to see how the bus marginal cost depends on the cost of enforcing system constraints such as branch limits and area equality constraints. This display is useful for indicating which constraints are contributing towards the determination of the marginal price at each bus.

As any case info display in Simulator this display can be customized and the information copied, printed, and saved by accessing the local menu option with the mouse right click.

One key feature of this display is the breakdown in the bus MW marginal cost into three components: the cost of energy, the cost of congestion, and the cost of losses. Also, while the bus MW marginal cost does not change based on the reference, the costs of energy, congestion, and losses are reference dependent. This reference is set on a per-area (or per-super area) basis in the [Area information dialog OPF tab](07-object-properties-run-mode-and-general-part2.md#opf) (or the [Super Area information dialog OPF tab](07-object-properties-run-mode-and-general-part2.md#super-area-information)).

---

<a id="scopf-bus-marginal-controls"></a>

## SCOPF Bus Marginal Controls

*Source: [`Content/MainDocumentation_HTML/SCOPF_Bus_Marginal_Controls.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Bus_Marginal_Controls.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This display (from the SCOPF [Results](#scopf-results) page) shows the sensitivities of the controls with respect to the cost at each bus. A change in a system control will have the indicated effect in the marginal cost at the system buses. Vice-versa, the marginal cost at a bus is affected by changes in the value of the basic variables.

The Marginal Controls page can be accessed by opening the [Security Constrained Optimal Power Flow](#scopf-dialog) form, and clicking on the Results tab.

---

<a id="scopf-example-introduction"></a>

## SCOPF Example: Introduction

*Source: [`Content/MainDocumentation_HTML/SCOPF_Example_Introduction.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Example_Introduction.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In this section we introduce an example of using the SCOPF. Consider the seven bus, three area system contained in the file B7SCOPF (included with the PowerWorld Simulator). This case is the same case used in the OPF example, except that the line from bus 2 to 3 has now a 100MVA rating, lines 1 to 2, 1 to 3 and 2 to 5 have a 120MVA rating, and all three areas are initially on OPF control. To initially solve the case using the optimal power flow, select **Primal LP** in the **OPF** ribbon group on the **[Add Ons](02-simulator-ribbon.md#add-ons-tab-overview)** ribbon tab. The solution obtained is shown below. The total case hourly cost is $16,011 / hr.

![image\\ebx\_-339818613.gif](images/ebx_-339818613_498x374.gif)

B7SCOPF Case Solved using OPF

We are interested in determining an optimal solution that meets security constraints under contingency conditions. In order to show that the current OPF solution does not enforce contingency violations, take line 1 to 2 out of service by clicking in a circuit breaker. Then solve the power flow by pressing the **Solve Power Flow**button. The result indicates that line 1 to 2 is overloaded 32%. The SCOPF algorithm will attempt to move the operating solution such that no contingency violation occurs in the system. Close line 1 to 2 back in service.

![image\\ebx\_-21905691.gif](images/ebx_-21905691_498x374.gif)

B7SCOPF Power Flow Solution with line 1-2 open

The next step is to specify the contingency conditions that the system should withstand. In order to do that, we access the [Contingency Analysis dialog](23-contingency-analysis-running-and-results.md#contingency-analysis-dialog) under **Tools**. Note that we can also access this dialog from the [SCOPF control dialog](#scopf-control) by selecting **Add Ons \> Security Constrained OPF** and pressing the **View Contingency Analysis Form** button on the **Options** page. The B7SCOPF case does not have contingencies associated with it. Insert single line contingencies in the contingency list by pressing the **Auto Insert**button located at the bottom left of the Contingency Analysis dialog. in the [Auto Insert Dialog](21-contingency-analysis-overview-and-records.md#automatically-generating-a-contingency-list) select the option for **Single Transmission Line** **or Transformer**and select **Numbers** under the *Identify buses by* field. Select **Do Insert Contingencies.** This will prompt to insert 11 single line contingencies corresponding to all the lines in the system. Select **Yes**. **** You can now close the Contingency Analysis dialog.

Return to the **Security Constrained Optimal Power Flow Form**. **** You can set the SCOPF to use the OPF solution as the base by selecting **Solve base case using optimal power flow**.

You can now solve the SCOPF by pressing the **Run Full Security Constrained OPF**. This will process the contingency violations and iteratively solve the LP program and the power flow equations to minimize the objective function and enforce equality and inequality constraints. The solution is shown below. The total operating cost is now $16,048 /hr. The increase in operating cost is due to enforcing security constraints. If a new contingency analysis is performed using the optimal solution as the reference, it will be found that no contingency violations occur for the contingencies in the list, i.e., branch flows are less than (or equal to) 100% in the post contingency condition. Thus, the system meets all the specified constraints. You can analyze the SCOPF results by browsing the information in the SCOPF tabs. Note that the **CTG Constraints** dialog does not show unenforceable constraints, but the branch violation of line 2 to 5 due to the contingency 5 to 7 is now binding.

![image\\ebx\_1530608614.gif](images/ebx_1530608614_498x374.gif)

B7SCOPF Case Solved using SCOPF: The system now meets the contingency constraints.

---

<a id="scopf-example-marginal-prices"></a>

## SCOPF Example: Marginal Prices

*Source: [`Content/MainDocumentation_HTML/SCOPF_Example_Marginal_Prices.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Example_Marginal_Prices.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Using the SCOPF solution from the previous page, select the **Bus Marginal Price Details** from the **Results** page of the **SCOPF Dialog** to view the detail of the marginal price components. Note in the following Figure that each area constraint contributes equally to the marginal cost of the buses in that area. The binding inequality constraint from bus 2 to 5 makes further contribution to the bus marginal price of buses in area Top.

![SCOPF Example Marginal Prices 932x301](images/SCOPF_Example_Marginal_Prices_932x301.gif)

Seven Bus Case SCOPF Bus Marginal Price Details

---

<a id="scopf-example-unenforceable-constraints"></a>

## SCOPF Example: Unenforceable Constraints

*Source: [`Content/MainDocumentation_HTML/SCOPF_Example_Unenforceable_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/SCOPF_Example_Unenforceable_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Using the same example as above, reduce the MVA rating of line 2 to 5 to 90 MVA. The initial base case LP OPF solution is the same as in the previous example. Consider the same contingency list. When the contingencies are solved using the initial OPF solution as the reference, seven contingency violations need to be removed. The CTG dialog after simulation is presented in the following figure.

![SCOPF Example Unenforceable Constraints 901x290](images/SCOPF_Example_Unenforceable_Constraints_901x290.gif)

CTG Dialog after SCOPF Solution

We note that the constraint from bus 2 to 5 under a contingency from 5 to 7 is unenforceable. There are not enough system controls to enforce the contingency constraint. A $ 1,000 / hr cost is assigned to unenforceable constraints in this case. The cost of not enforcing constraints can be specified in the [OPF Constraint Options](30-optimal-power-flow-part1.md#opf-options---constraint-options) **** Dialog.

---

<a id="optimal-power-flow-reserves-overview"></a>

## Optimal Power Flow Reserves Overview

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Overview.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Overview.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The OPF Reserves tool in PowerWorld Simulator is only available if you have purchased the OPF Reserves and OPF add-ons to the base package. To learn more about the OPF Reserves, please read through the information contained in these help files. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information) for details about ordering the OPF and OPF Reserves version of Simulator.

In order to prevent load disconnections and loss of stability during normal operation or in the case of unexpected events, power systems should operate with an adequate level of Reserve. Reserve is an ancillary service needed for the successful operation of the system and the electricity market. This service can be obtained in a regulated, mandatory manner, or it can be provided by an Ancillary Services Reserves Market. Simulator OPF Reserves is the tool used to simulate Ancillary Services Reserve Markets.

In the Reserves Market, the generators (and sometimes loads) supply bids to sell the ability to take demand (increase their output) in a fast manner if called to do so. While an energy-only market has only one product, active energy, the Reserves Market includes the energy product and several reserve services: regulating, spinning and supplemental reserve. Similar to electricity markets for energy, which deal with active power, the reserve market focuses only on active power reserves.

The optimal power flow (OPF) algorithm by itself is able to simulate energy-only electricity markets by determining the minimum cost or minimum control change dispatch subject to normal operation constraints. The OPF Reserves considers special OPF Reserve Constraints at the area and zone level, and OPF Reserve Controls provided by generators or loads. OPF Reserves will thus simultaneously co-optimize energy and reserve and maximize total social surplus producing both energy (LMP) and Reserve Marginal Clearing Prices (RMCP).

The commands and options for the [OPF Reserves](#opf-reserves-topics) are integrated with the [OPF tool](30-optimal-power-flow-part1.md#opf-options).

---

<a id="opf-reserves-topics"></a>

## OPF Reserves Topics

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Topics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Topics.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The commands and options for the OPF Reserves are integrated with the [OPF tool](30-optimal-power-flow-part1.md#opf-options). The OPF Reserves option is activated from the [Common Options tab](30-optimal-power-flow-part1.md#opf-options---common-options) of the OPF Options and Results dialog by checking the **Include OPF Reserve Requirements** box.

The following topics provide details about how the OPF Reserves are integrated into the OPF tool and options and input data can be set:

  - [OPF Reserves Controls](#opf-reserves-controls)
  - [OPF Reserves Constraints](#opf-reserves-constraints)
  - [OPF Reserves Objective Function](#opf-reserves-objective-function)
  - [OPF Reserves Results and Pricing](#opf-reserves-results-and-pricing)
  - [OPF Reserves Case Information Display](#opf-reserves-case-information-display)
  - [Area and Zone Reserve Requirements Curves](#area-and-zone-opf-reserve-requirement-curves)
  - [Generator and Load OPF Reserve Bids](#generator-and-load-opf-reserves-bids)
  - [OPF Reserves Example](#opf-reserves-example)

---

<a id="opf-reserves-controls"></a>

## OPF Reserves Controls

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Controls.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Controls.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generators can provide the following types of reserve:

  - Regulation Reserve (RR) is provided by online fast units, usually tied to AGC primary control, and capable to regulate the small positive or negative imbalances caused by the random nature of loads.
  - Spinning Reserve (SR) is provided by online units and is used to take larger variations of load and losses and unexpected events.
  - Supplemental Reserve (XR) is provided by online or offline fast-start units. This type of reserve is used to correct large imbalances caused by contingencies.

Spinning and supplemental reserve are positive quantities. Regulation reserve is a bidirectional control. There are two ways to model regulation controls: As two independent controls: regulation reserve up (RR<sup>+</sup>) and regulation reserve down (RR<sup>-</sup>). As a single control: in this case the unit provides the same amount of regulating reserve in both directions. In order to tell Simulator whether to use a single bidirectional control for regulating reserve up or down, go to the [OPF Options and Results Dialog](30-optimal-power-flow-part1.md#opf-options---common-options) and check the **Use a Single Control for Up/Down Regulation** box.

Spinning and supplemental reserves combined together provide Contingency Reserve (CR)

Contingency reserve plus regulating reserve up is called Operating Reserve (OR)

The following relations are then established:

RR<sup>+</sup> + SR + XR = OR

RR<sup>+</sup> +           CR = OR

Data for the reserve controls can be specified from the [Generator Information dialog](06-object-properties-edit-mode-part1.md#costs), the [Load Information dialog](06-object-properties-edit-mode-part1.md#opf-load-dispatch), or from the corresponding case information displays accessible from the **Model Explorer \> Optimal Power Flow \> Results \> Reserve Results**.

![OPF Reserves Constraints Controls](images/OPF_Reserves_Constraints_Controls.jpg)

---

<a id="generator-and-load-opf-reserves-bids"></a>

## Generator and Load OPF Reserves Bids

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Gen_and_Load_Reserve_Bids.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Gen_and_Load_Reserve_Bids.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Generators and loads can both be providers of reserve services. Similar options exist for both in setting the OPF Reserve Bids parameters. These options can be set for generators on the [Cost tab](06-object-properties-edit-mode-part1.md#costs) of the Generator Information dialog and for loads on the [OPF Load Dispatch tab](06-object-properties-edit-mode-part1.md#opf-load-dispatch) of the Load Information dialog.

OPF Regulating Reserves

These options are only available for generators.

**Up Reserve MW** - Value in MW of the cleared regulating reserve up. This value is determined by the OPF Reserves solution and is non-enterable by the user.

**Down Reserve MW** - Value in MW of the cleared regulating reserve down. This value is determined by the OPF Reserves solution and is non-enterable by the user. When a single bidirectional control is used for up and down reserve, the MW value of the cleared Up Reserve and Down Reserve will be the same.

**Available for Regulating Reserves** - Check this box to declare this unit as a provider of regulating reserves service.

**Price \[$/MWh\]** - This is the bid submitted for the block of regulating up and down reserves.

**Maximum MW Increase** - This is the size in MW of the block of the regulating reserve up bid submitted to the market. The cleared regulating reserve up cannot be larger than this value.

**Maximum MW Decrease** - This is the size in MW of the block of regulating reserve down bid submitted to the market. The cleared regulating reserve down cannot be larger than this value.

OPF Contingency Reserves

These options are available for both generators and loads.

**Spinning Available** - Check this box to declare this unit/load as a provider of spinning reserve service.

**Supplemental Available** - Check this box to declare this unit/load as a provider of supplemental reserve service.

**Reserve MW** - Value in MW of the cleared spinning and supplemental reserves. These values are determined by the OPF solution and are non-enterable by the user.

**Price \[$/MWh\]** - This is the bid submitted for the corresponding blocks of spinning and supplemental reserve.

**Max MW Increase** - For spinning and supplemental reserve this is the size of the reserves block submitted to the market. The cleared reserves cannot be larger that these values.

---

<a id="opf-reserves-constraints"></a>

## OPF Reserves Constraints

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Constraints.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Constraints.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Reserve constraints in the OPF Reserves tool are specified at the area and zone level. Overlapping constraints are handled if an area contains several zones or if a zone spans several areas. For each type of reserve specified, the total reserve of the area or zone must be equal or greater than a certain level of reserve requirement in MW:

  - Operating Reserve: OR ≥ OR<sub>REQ</sub>
  - Regulating Reserve: RR ≥ RR<sub>REQ</sub>
  - Contingency Reserve: CR ≥ CR<sub>REQ</sub>
  - Some systems require that a percentage of the contingency reserve be spinning: SR ≥ %CR

Reserve requirements are input as incremental demand curves. These can be defined for both areas and zones and are described in more detail in the [Area and Zone Reserve Requirement Curves topic](#area-and-zone-opf-reserve-requirement-curves).

The reserve requirement demand curves are specified by pairs of (MW,$/MWh) values that form a stair function. The demand curve should be monotonically decreasing, i.e., while the MW values increase, the $/MWH values should decrease.

Sometimes, ancillary services markets rules specify a single reserve requirement value and price. For instance, 300MW at $500/MWh. This requirement can be modeled by a demand curve that contains two points: 0.0 MW at 300 $/MWh, and 300 MW at 0.0 $/MWh.

![OPF Reserves Constraints Controls](images/OPF_Reserves_Constraints_Controls.jpg)

---

<a id="area-and-zone-opf-reserve-requirement-curves"></a>

## Area and Zone OPF Reserve Requirement Curves

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Area_and_Zone_Reserve_Requirement_Curves.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Area_and_Zone_Reserve_Requirement_Curves.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator OPF Reserves requires the user to specify area or zone reserve constraints as reserve demand curves for different types of requirements: operating, regulating and contingency.

Simulator OPF Reserves allows reserve constraints to be specified at the area and zone level or both, including overlapping regions. The data needed to specify reserve constraints at the zone level is identical to that needed for area reserve constraints.

Reserves Requirement Curves are found on the OPF tab of the [Area Information dialog](07-object-properties-run-mode-and-general-part2.md#opf) and the OPF tab of either the [edit](06-object-properties-edit-mode-part3.md#zone-information) or [run](07-object-properties-run-mode-and-general-part1.md#zone-information) mode Zone Information dialog.

The reserve requirement incremental demand curves are specified by a set of pairs of (MW,$/MWh) values that form a stair function. The incremental demand curve should be monotonically decreasing, i.e., while MW values increase, $/MWH values should decrease.

Sometimes, ancillary services markets rules specify a single reserve requirement and its price. For instance 300MW at $500/MWh. This requirement would be modeled by a demand curve that contains two points: 0.0 MW at 300 $/MWh, and 300 MW at 0.0 $/MWh.

**Enforce Operating Reserve Requirement in OPF** - Check this box to make the specified operating reserve demand curve be enforced by the OPF Reserves tool.

**Enforce Regulating Reserve Requirement in OPF** - Check this box to make the specified regulating reserve demand curve be enforced by the OPF Reserves tool.

**Enforce Contingency Reserve Requirement in OPF** - Check this box to make the specified contingency reserve demand curve be enforced by the OPF Reserves tool.

**Results Page** - This page shows total results at the area level for different types of reserve quantities: regulating reserve up, regulating reserve down, spinning reserve, supplemental reserve, contingency reserve and operation reserve.

**Enforce** - Whether a specific type of reserve is enforced for the area. Only regulating, contingency and operation reserve can be enforce at the area or zone level.

**Cleared MW** - Total reserve cleared in the area, for each reserve type.

**Max Reserve MW** - Total available reserve in the area for each reserve type.

**Hourly Cost $/hr** - Total cost of providing the reserve service in the area for each reserve type.

**Price $/MWh** - Reserve Marginal Clearing Price (RMCP) for each reserve type. This price is a result of enforcing the reserve constraints, and thus it is only available for regulation, contingency and operation reserves.

**Hourly Benefit $/Hr** - Benefit provided by enforcing reserve constraints at the area level. This benefit is derived from the enforced reserve demand requirements, and it is only available for regulation, contingency and operation reserves.

---

<a id="opf-reserves-objective-function"></a>

## OPF Reserves Objective Function

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Objective_Function.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Objective_Function.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The power system should operate exceeding level of the different types of reserves. The benefit associated with a reserve type is equal to the reserve consumer surplus (area below the reserve demand curve and above the equilibrium RMCP). In order to provide reserve, some generators will need to reduce their output to make room for the assigned reserve level. Thus in general, meeting the reserve requirements will result in increased energy prices. In Simulator, the OPF reserves problem is solved using an application of sequential linear programming embedded in the OPF solver. The LP problem consists in maximizing total surplus:

Total Surplus = Benefit - Costs

Where the benefits include:

  - Up Regulation Reserve Surplus
  - Down Regulation Reserve Surplus
  - Contingency Reserve Surplus
  - Operating Reserve Surplus

And the costs include:

  - Up Regulation Reserve Cost
  - Down Regulation Reserve Cost
  - Spinning Reserve Cost
  - Supplemental Reserve Cost

---

<a id="opf-reserves-results-and-pricing"></a>

## OPF Reserves Results and Pricing

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Results_and_Pricing.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Results_and_Pricing.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The results of co-optimization of energy and reserves as implemented in Reserve Markets are:

  - Optimal generation dispatch MW set-points and reserve assignments
  - Energy locational marginal prices (LMP)
  - Reserve market clearing prices (RMCP)

The energy locational marginal prices are different than the prices that would be obtained if reserve requirements are not consider. Usually, LMPs are higher in simultaneous energy and reserve optimization. This is due to some generators having to back-off their output to meet reserve control assignments.

As the bus LMP values correspond to the change in operating cost when an additional MW of active power load is served at that bus, the RMCP correspond to the change in operating surplus when an additional MW of a certain type of reserve is required to be provided at that bus. Each area or zone that specifies reserve requirements will have a RMCP. If particular, the RMCP of buses in overlapping zones and areas will be the result of adding the corresponding RMCP associated with each constraint. The bus components of the RMCP can be accessed from the [Bus MW Marginal Prices Details page](30-optimal-power-flow-part1.md#opf-options---bus-mw-marginal-price-details) in the OPF Options and Results Dialog. RMCP fields will show up automatically for each constraint type that is binding.

---

<a id="opf-reserves-case-information-display"></a>

## OPF Reserves Case Information Display

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Case_Information_Display.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Case_Information_Display.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

A special category of [case information display](04-model-explorer-and-case-information-part1.md#case-information-displays) is available from the [Model Explorer](04-model-explorer-and-case-information-part1.md#model-explorer) to access common OPF reserves data. From the Model Explorer select the **Optimal Power Flow \> Results \> Reserve Results**. The same set of reserve case information displays can be accessed from the [Add Ons ribbon tab](02-simulator-ribbon.md#add-ons-tab-overview) under the **Optimal Power Flow ribbon group \> OPF Case Info \> OPF Reserves**.

These case information displays include input and output data for the Reserves Markets, such as areas, zones, generator and loads. They have been customized with fields relevant to OPF Reserves. For instance, generator and loads include:

  - Availability of each reserve type: regulating, spinning, supplemental
  - Maximum reserve available for each reserve type
  - Single value bid price for the reserve bid block, for each reserve type
  - Resulting RMCP for each reserve type

The area and zone information displays include:

  - Enforcement of reserve constraints: regulating, contingency, and operation
  - Total cleared reserve for each type
  - Total reserve cost and benefit for each type

---

<a id="opf-reserves-example"></a>

## OPF Reserves Example

*Source: [`Content/MainDocumentation_HTML/OPF_Reserves_Example.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/OPF_Reserves_Example.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In this section, we present an example of the OPF Reserves in action. Consider the 10 bus, 7 generator case contained in the B10Reserve.pwb case (included with PowerWorld Simulator). This case has 2 areas and 3 zones.

![OPF Reserves Example Case Diagram](images/OPF_Reserves_Example_Case_Diagram.jpg)

First solve the LP OPF without reserves by clicking LP Primal from the [Add Ons ribbon group](02-simulator-ribbon.md#add-ons-tab-overview). Check the log to confirm a successful OPF solution. The initial LP OPF solution without reserves presents a binding transmission line as shown in the Figure.

The first step to solving the OPF with reserves is to set up the reserve control availability and reserve bids from the **Add Ons ribbon group \> OPF Case Info \> OPF Reserves \> Generators case information display**. The following parameters, which in this example will be set up in a tabular manner, can also be set in the individual [Generator Information dialog](06-object-properties-edit-mode-part1.md#costs). Let us set regulation, spinning and supplemental generator reserve availability as follows:

| Gen | Reg. Avail | SPN Avail | SUP Avail |
| :-: | :--------: | :-------: | :-------: |
|  1  |    YES     |    NO     |    NO     |
|  2  |    YES     |    YES    |    NO     |
|  4  |     NO     |    YES    |    YES    |
|  7  |    YES     |    NO     |    YES    |
|  8  |    YES     |    YES    |    NO     |
|  9  |     NO     |    YES    |    YES    |
| 10  |     NO     |    NO     |    YES    |

Then, let us set up the following reserve blocks and prices (reserve bids) in the same case information diagram.

![OPF Reserves Example Gen Reserve Bids](images/OPF_Reserves_Example_Gen_Reserve_Bids.jpg)

Once the generator and/or load reserve controls have been specified, the second step is to set up the reserve constraints for the control areas and/or zones. Let us set up the following data by accessing each individual [Area Information dialog](07-object-properties-run-mode-and-general-part2.md#opf) or [Zone Information dialog](06-object-properties-edit-mode-part3.md#zone-information). Recall, that a single level reserve requirement such as 150 MW @ 400 $/MWh is set by entering two points in the reserve demand curve: 0.0 MW at 400 $/MWh and 150 MW at 0.0 $/MWh.

![OPF Reserves Example Area Zone Constraints](images/OPF_Reserves_Example_Area_Zone_Constraints.jpg)

Let us now solve the OPF enforcing reserve requirements. Go to the [Add Ons ribbon tab](02-simulator-ribbon.md#add-ons-tab-overview) and choose [OPF Options and Results](30-optimal-power-flow-part1.md#opf-options---common-options) in the Optimal Power Flow ribbon group. Check the box **Include OPF Reserve Requirements**. Click the Solve LP OPF button from the dialog or the Primal LP button from the Add Ons ribbon tab.

The OPF Reserves, will enforce reserve constraints for each reserve type and for each area and zone whose Enforce Field is set to *YES*. In addition, OPF Reserve will observe the following constraints:

  - Transmission line limits
  - Generator MW Max and Min limits for the total energy plus reserve controls
  - Area scheduled interchange. For this case, there is a 100 MW export from Area A to Area B.

To explore the results, go to the Generators page in [OPF Reserve Results](#opf-reserves-case-information-display) in the Model Explorer. The results include generator MW dispatch and assignment of all the reserve services. Note that in this example, some of the generators have reached their reserve bid limits for certain units and types of reserve.

![OPF Reserves Example Gen Results](images/OPF_Reserves_Example_Gen_Results.jpg)

Results can be explored at the area or zone level by accessing the individual Area Information dialog or Zone Information dialog, going to the OPF tab, and the Results subtab of the [Reserve Requirement Curves](#area-and-zone-opf-reserve-requirement-curves). For instance, the Results for Area A are as shown in the next Figure. For each area, the results page shows the enforcement of different types of regulation, the total cleared reserve, the total available reserve, the reserve cost per hour, the reserve price, and the hourly benefit, which corresponds to the area below the demand curve and above the equilibrium RMCP level.

![OPF Reserves Example Area Results](images/OPF_Reserves_Example_Area_Results.jpg)

The Results tab of the [OPF Options and Results dialog](30-optimal-power-flow-part1.md#opf-options) shows the details of Bus MW marginal prices, including energy, congestion and losses, and the reserve prices associated with the area or zone reserve constraints. The corresponding linear programming details will list among the LP variables the reserve controls specified by the user. The LP tableau will include specific rows for the enforced reserve constraints at the area and zone level, etc. Reserve results can be visualized as any other generator, load or bus object field in Simulator.

![OPF Reserves Example 3D Diagram](images/OPF_Reserves_Example_3D_Diagram.jpg)

It should be mentioned that OPF Reserves is fully incorporated with the [Time Step Simulation (TSS) tool](26-time-step-simulation-part1.md#time-step-simulation), so hourly OPF runs including reserves can be performed and results versus time stored. However, currently OPF Reserves cannot be used simultaneously with the SCOPF tool.
