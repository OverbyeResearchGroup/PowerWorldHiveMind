---
title: "Power Flow Solution and Simulator Options (Part 2 of 3)"
part: "Solving"
chapter_file: "10-power-flow-solution-and-options-part2.md"
topics: 16
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Power Flow Solution and Simulator Options (Part 2 of 3)

Power flow solution theory, simulator options, and solution and control settings.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (16)**

- [Power Flow Solution: Common Options](#power-flow-solution-common-options)
- [Power Flow Solution: Advanced Options](#power-flow-solution-advanced-options)
- [Power Flow Solution: Island Creation](#power-flow-solution-island-creation)
- [Post Power Flow Solution Actions Dialog](#post-power-flow-solution-actions-dialog)
- [Power Flow Solution: Island-Based AGC](#power-flow-solution-island-based-agc)
- [Power Flow Solution: DC Options](#power-flow-solution-dc-options)
- [DC Power Flow Loss Setup](#dc-power-flow-loss-setup)
- [Power Flow Solution: General](#power-flow-solution-general)
- [Power Flow Solution: Storage](#power-flow-solution-storage)
- [Environment Options](#environment-options)
- [Oneline Options](#oneline-options)
- [File Management Options](#file-management-options)
- [Case Information Display Options](#case-information-display-options)
- [Message Log Options](#message-log-options)
- [Distributed Computing Add-Ons](#distributed-computing-add-ons)
- [Solving the Power Flow](#solving-the-power-flow)

---

<a id="power-flow-solution-common-options"></a>

## Power Flow Solution: Common Options

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_Common_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_Common_Options.htm)*

The following options are all contained on the Common Options tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Power Flow (Inner) Loop Options (see [Solving the Power Flow](#solving-the-power-flow) for information on solution loops)

MVA Convergence Tolerance

The MVA convergence tolerance serves as a measure for determining when the inner power flow loop of the Power Flow Solution process has reached an acceptable solution. The MVA mismatch is computed as the maximum real or reactive mismatch at any bus in the system. Usually, this value should be around 0.1 MVA. If you are having difficulty solving a particular case, it may be helpful to temporarily increase the MVA Convergence Tolerance to drive the solution closer to the actual solution, and then re-solve from this solution using the smaller MVA tolerance.

Maximum Number of Iterations

This option defines the maximum number of iterations Simulator will perform during the Power Flow Solution process in an effort to converge to a solution. If Simulator must exceed this number of iterations, it assumes that the power flow case is not converging and will terminate the solution process. If Simulator is configured to represent non-converging power flow cases as blackouts, the screen will turn gray and the blackout warning message will appear.

Do Only One Iteration

If checked, Simulator will only perform one iteration of the load flow solution process when **Solve Power Flow** is clicked, regardless of the Maximum Number of Iterations setting. This is useful to more closely examine a case with which you are experiencing difficulty.

MW Control (Outer) Loop Options (see [Solving the Power Flow](#solving-the-power-flow) for information on solution loops)

Disable Automatic Generation Control (AGC)

If checked, the enforcement of the generation re-dispatch to account for MW interchange constraints for all areas is disabled. By default, this option is not checked.

Enforce Generator MW Limits

If checked, generator minimum and maximum MW limits are enforced for all generators whose *Enforce MW Limits* field is set to true. See [Generator Information Dialog](07-object-properties-run-mode-and-general-part1.md#generator-information) for more information. Otherwise, generator MW limits are not enforced. When using the economic dispatch or the Optimal Power Flow, the generator MW limits are always enforced regardless of user-settings.

Topology Processing Options (These options are only available with the [Topology Processing](35-integrated-topology-processing.md#topology-processing-overview) add-on)

Use Topology Processing

This option is used for all Simulator applications: power flow, contingency analysis, sensitivity calculations, etc. This option should ALWAYS be checked for real-time cases, while it should be unchecked for planning cases. If a full-topology model was read and this option is not checked, the power flow will try to solve the model without removing the switching devices resulting in a very large [ill-conditioned Jacobian](35-integrated-topology-processing.md#ill-conditioned-jacobian). This option is also found on the [Topology Processing Dialog](35-integrated-topology-processing.md#integrated-topology-processing-dialog).

Close Breakers to Energize Switched Shunts

If checked, an attempt will be made to close breakers in order to energize a [Switched Shunt](06-object-properties-edit-mode-part3.md#switched-shunt-information) that is on either Discrete or Continuous control and is needed to meet its regulated value. This option is applied as part of the [switched shunt control](05-case-information-displays-by-object-part3.md#switched-shunt-control) any time that the power flow is solved.

This option will be checked by default if loading an EMS case from Areva CSV or ABB Spider file types.

Controller (Middle) Loop Options (see [Solving the Power Flow](#solving-the-power-flow) for information on solution loops)

Disable Checking Gen VAR Limits

If checked, the Mvar limits are ignored for all the generators in the case during a power flow solution. By default, this option is not selected.

Check Immediately (option is not recommended)  
Check Back Off Immediate( option is recommended)

Before entering the inner power flow loop to solve the power flow equations, a decision is made about each generator in the case as to whether it will be treated as a PV or a PQ bus. It is assumed that a PV bus will maintain its setpoint voltage, while a PQ bus will maintain a constant reactive power output (for instance when the generator is at a Mvar min or max limit). Normally, the power flow equations are completely solved in an inner power flow loop using this assumption. After completing the solution, generator Mvar limits are checked to see if they have been reached (must change from PV to PQ), or if at a limit if the limit may be backed off of (must change from PQ to PV). If any generators change PQ/PV status, the inner power flow loop is resolved.

When the **Check Immediately** option is checked, the generator Mvar limits are checked after *every* inner power flow loop iteration instead to see if generator limits have been reached, or if a generator limit may be backed off. When this option is not checked then it will not check the generator limits inside the inner power flow loop. In *some* situations performing this check inside the inner power flow loop can help with convergence, however in *most* situations performing this check makes convergence to undesirable low or high voltages solution more likely and also slows down the solution process. By default, this option is not selected and the use of <span class="underline">this option is not recommended</span>.

**Check Back Off Immediately** was Added in Version 19 and is a partial implementation of the **Check Immediately** option. It will only check whether generator limits should be backed off during the inner power flow loop iteration, but will not check if generators are outside their Mvar limits. When this is checked, generators being outside their Mvar limits will continue to occur in the controller control loop. In Version 20 This option is checked by default. and is <span class="underline">the recommended option</span>.

Starting in the Version 23 patch on July 12, 2024, when  
(**Check Immediately** is not chosen) AND (**Check Back Off Immediately** is chosen)  
then behavior is modified slightly. We will always look to back off limits in the inner power flow loop, but will also (1) look to hit a high Mvar limit if the terminal per unit voltage is very high and (2) look to hit a low Mvar limit if the terminal per unit voltage is very low.

Disable Switched Shunt (SS) Control

If checked, automatic control of switched shunts is disabled in all areas. By default, this option is not selected.

Disable SVC Control

If checked, SVC type switched shunts are disabled. By default, this option is not selected. Note: The area option for shunt control only applies to non-SVCs.

Disable LTC Transformer Control

If checked, automatic control of LTC transformers is disabled in all areas. By default, this option is not checked.

Disable Phase Shifter Transformer Control

If checked, automatic control of phase shifting transformers is disabled in all areas. By default, this option is not checked.

Disable DC Line Transformer Tap Control

If checked, automatic control of DC transmission line transformer tap control is disabled in the entire case. By default, this option is not checked.

Disable D-FACTS Control

If checked, automatic control of D-FACTS devices is disabled for all devices. By default, this option is checked.

Transformer Stepping Methodology

Choose either *Coordinated Sensitivities* or *Self-Sensitivity Only*. The default value is *Coordinated Sensitivities*.

When the regulated value of tap-changing or phase-shifting transformers move outside of their regulation range, then Simulator attempts to bring those transformers back inside their range. By default Simulator determines all the tap-changing and phase-shifter transformers which are out-of-range and coordinates the movement of these transformers in an attempt to bring all the regulated values back into range. This is what is called *Coordinated Sensitivities*. Generally this results in a better convergence, however it also can be slower when a large number of transformers are out-of-range together. Because it gets slower with a large number of transforms, if more than 50 transformers are involved in the switching, Simulator will always use the *Self-Sensitivity Only* option. As the solution process continues however, the number of transformers moving will reduce and eventually the *Coordinated Sensitivities* will be used again.

Choosing *Self-Sensitivity Only* will modify this methodology so that each transformer only looks at the sensitivity of its regulated value with respect to changing its own tap or phase. This calculation is faster, but may result in convergence problems due to transformers that interact with one another.

Prevent Controller Oscillations

Sometimes, a power flow will fail to converge because certain automatic controls such as Mvar limit enforcement at generators, transformer tap switching, and shunt switching oscillate between their control bounds. These oscillations very often are due to modeling inaccuracies. If this option is checked, Simulator will automatically detect such oscillating controls and fix them at their current value so that they no longer oscillate. You may find this option helpful if you feel that the modeling of automatic controls in your system is inaccurate.

Maximum Number Controller Loop Iterations

As part of the solution process, the outer loop of the solution algorithm is a check of any necessary controller changes due to changes in controlled values from the last iteration of the Newton-Raphson load flow solution. The maximum number of loops through the control change algorithm can be set here. This is not the same as the Maximum Number of Iterations, which applies to the actual Newton-Raphson inner loop algorithm and solves the actual power flow.

---

<a id="power-flow-solution-advanced-options"></a>

## Power Flow Solution: Advanced Options

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_Advanced_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_Advanced_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the Advanced Options tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Dynamically add/remove slack buses as topology is changed

If checked, Simulator dynamically chooses a new slack bus for the islands if the user-input does not adequately define slack buses. If a slack bus can not be determined for an island, the island cannot be solved and will be isolated and ignored during the load flow solution. Also if there are multiple slack buses specified in the same island, Simulator will choose only one of them as the slack bus.

When allowing dynamic slack bus assignment, the choice of the island slack bus is managed in Simulator by internally maintaining a list of buses the user has identified as slack buses while in Edit Mode. Electrical islands are then dynamically determined from the system topology. As branch statuses are changed, this list of islands (and slack buses) will automatically change. For more information about how the islands are created see the help topic on [Island Creation](#power-flow-solution-island-creation). This was made a separate topic in the help documentation in Version 19, build on January 9, 2017

Evaluate Power Flow Solution for Each Island Added in Version 20

Prior to Version 20, Simulator would report a solution as unsolved if any island in the case did not successfully converge to a power flow solution. This meant that if you had a large system with multiple electrical island, then if even one island did not converge the power flow solution would abort. When checking this option, Simulator will abandon solving an island, but continue solving other islands as long as at least one island continues to converge. When choosing this option you will notice messages written to the log about the maximum mismatch in each island as well instead of only the maximum mismatch across the entire case.

Post Power Flow Solution Actions

Clicking this option will open the [Post Power Flow Solution Actions dialog](#post-power-flow-solution-actions-dialog), where the user can specify a list of actions to be executed at the end of every full AC power flow solution.

Power Flow (Inner) Loop Options (see [Solving the Power Flow](#solving-the-power-flow) for information on solution loops)

Disable Power Flow Optimal Multiplier

If checked, the Newton solution process will not use the optimal multiplier. The optimal multiplier is a mathematically calculated step size for the Newton's Method iteration that prevents the mismatch equations from increasing between iterations. A small value indicates that moving in the direction of the Newton step will increase the mismatch equations. When the optimal multiplier becomes too small, this is an indication that the power flow is not going to solve successfully and Simulator will stop instead of creating extremely large mismatches. If this happens at a point where the solution is not within the allowed tolerance for the Newton process, the Newton process will result in a failed convergence to a valid solution.

Initialize From Flat Start Values

This option only applies to stand alone power flow solutions. Stand alone means a power flow solution initiated by clicking on the Solve Power Flow button on the [Power Flow Tools group](02-simulator-ribbon.md#simulation-control) in the [Tools Ribbon Tab](02-simulator-ribbon.md#tools-tab-overview). This option does not apply to power flow solution initiated by the contingency analysis, PV Curve, QV Curve, or ATC tools.

When checked, each Power Flow Solution is started assuming that all voltage magnitudes at buses that are not being regulated by a generator or have attached generators are set to unity. If a bus is regulated by a generator or is a generator bus, the voltage magnitude is set to the voltage setpoint of the generator. Voltage angles are set to the voltage angle of the system slack bus. By default, this option is not selected. Some power flow problems can be very difficult to solve from flat start assumptions. Therefore, use this option sparingly.

When the flat start routine is applied to a system which contains many 30 degree phase shifts related to Delta-Wye transformer connections, the flat start routine will set voltage angles in a manner that will handle these phase shifts.

Minimum Per Unit Voltage for Constant Current Loads

This option is used to model the impact that falling voltage has on loads throughout the system. The default value is 0.5.

For constant current loads with a terminal bus below this per unit voltage, the value of the load will fall off using a sine function so that the load is zero at zero terminal voltage, and so that the derivative is continuous at the minimum per unit voltage for constant current loads.

Minimum Per Unit Voltage for Constant Power Loads

This option is used to model the impact that falling voltage has on loads throughout the system. The default value is 0.7.

For constant power loads with a terminal bus below this per unit voltage, the value of the load will fall off using a cosine function so that the load is zero at zero terminal voltage, and so that the derivative is continuous at the minimum per unit voltage for constant current loads.

Control (Middle) Loop Options (see [Solving the Power Flow](#solving-the-power-flow) for information on solution loops)

Disable Treating Continuous Switched Shunts (SSs) as PV Buses

Continuous switched shunts are normally treated the same as a generator bus inside the inner power flow loop (they are treated as buses with fixed power and voltage). Checking this option will cause the continuous switched shunt to be treated as a constant impedance in the inner power flow loop with all switch occurring in conjunction with other switched shunts in the voltage control loop instead.

Disable Balancing of Parallel LTC Taps

Simulator has the capability to attempt to balance tap positions of parallel transformers, in an attempt to avoid parallel transformers from going to opposite tap settings, inducing loop flow through the parallel transformers. Checking this option disables the automatic balancing of parallel transformers. The only transformers that will be balanced are those in parallel between the same terminal buses, or those in parallel between terminal buses that are connected with very-low impedance branches.

If enabled, when parallel transformers do not regulate the same bus (actually ZBR Bus group), the transformer will be turned off control automatically and an appropriate message will be written to the log.

When automatically detecting parallel transformers to ensure taps ratios and regulated buses are consistent, the **ZBR Threshold** user-input parameter is used to determine groupings of buses considered the same electrical point. This **ZBR Threshold** is also used with generator voltage regulation and making the **ZBR Threshold** too large can cause numerical problems. Testing has shown that transformer taps and regulated buses for parallel transformers are not as sensitive to this threshold, so a larger threshold is useful so that more parallel transformers can be auto-detected. The impedance threshold used for balancing transformer taps and choosing common regulated buses is 4 times the **ZBR Threshold**. For example, if ZBR Threshold = 0.00029, then for transformers tap tests we will use a value of 0.00116 instead.

Transformers have an available field called **Tap Ratio Change to Balance** that provides information about whether or not parallel taps are balanced. When parallel taps are properly balanced, this field is blank. If this field is not blank, the value is the tap ratio that will balance parallel transformers.

Model Phase Shifters as Discrete Controls

If checked, then phase shifters will switch tap positions discretely based on the tap step size of the phase shifting transformer. By default, this option is not checked, which means the phase shifters will switch continuously, independent of the tap step size.

Disabled Transformer Tap Control if Tap Sens. is the Wrong Sign (Normally Check This)

By default if a transformer controls one of its terminal buses, then when performing transformer tap switching calculations, a validation check is done on the sign of the voltage-to-tap sensitivity. If this sensitivity is the incorrect sign, then this indicates that the transformer is operating in an unusual system condition and switching of this transformer is disabled. To disable this default behavior, check this box.

Minimum Sensitivity for LTC Control

This option specifies the minimum-voltage-to-tap sensitivity for LTC transformers. All transformers having an absolute value of voltage-to-tap sensitivity below this value are automatically disabled from automatic control. This prevents Simulator from changing transformer taps that have little effect on their controlling voltage. The [Transformer AVR Dialog](06-object-properties-edit-mode-part2.md#transformer-avr-dialog) shows the voltage-to-tap sensitivity for each voltage-controlling transformer.

Disable Angle Smoothing

When a transmission branch status is changed from OPEN to CLOSED across a branch that has a large voltage angle difference, this can introduce a very large initial power flow mismatch and cause the inner power flow loop to diverge. Angle Smoothing will alleviate this large angle difference by smoothing the angles in the system around the newly closed in branch resulting in much better power flow convergence. Angle smoothing will also work if a series of branches are all closed in together. Angle smoothing should be enabled by default, but checking this option will disable this. Angle smoothing works best for individual branches or a series of branches that have been closed that are not electrically near other branches that have been closed. If modifying a case and adding in new transmission lines that are electrically near each other, it might be better for solution convergence to disable angle smoothing.

Disable Angle Rotation Processing

At the end of a power flow solution, by Simulator looks at the bus voltage angles in the case to see if any are near +/- 180 degrees. If the angles fall outside of +/- 160 degrees, then all angles in the island will be rotated by the same amount so that the angle range in the islands is equally spaced around zero degrees. Check this option to disable this feature.

Sharing of generator Vars across groups of buses during remote regulation

When several buses have generators that control the voltage at single bus, this option determines the method used to determine each buses "share" of the MVar support. There are three options

1.  Allocate across buses using the user-specified remote regulation percentages. This option most closely matches the sharing seen in RAW files. The allocation of Mvars to a bus will be proportional to the <span class="underline">average value</span> of the RegFactor for all generators at the bus.
2.  Allocate so all generators are at same relative point in their \[min .. max\] var range. This option most closely matches the sharing seen in a few EMS solutions PowerWorld has seen. The RegFactor values are not used with this option, but the MvarMax and MvarMin values will impact the allocation.
3.  Allocate across buses using the SUM OF user-specified remote regulation percentages. This option most closely matches the sharing seen in EPC files. The allocation of Mvars to a bus will be proportional to the <span class="underline">summation</span> of the RegFactor for all generators at the bus.

ZBR Threshold

Added in Version 19

Before Version 19 the ZBR Threshold was 0.0002 per unit always, but can now be changed by the user. The ZBR threshold is used internally in solution algorithms to build groups of buses connected by low impedance branches. Any generator that regulates a bus within these groups will coordinate with other generators when performing voltage control. In addition multiple switched shunts that control buses in the same group automatically coordinate their control. Finally, these groupings are used to find parallel transformers whose tap ratios are then balanced.

PSLF DC Converter Equation Compatibility Options

Use Approximate DC Converter Power Factor Equations (not recommended)Added in Version 22 build on August 20, 2021

The line-commutated DC Converter equations involve the calculation of the reactive power consumption at a converter using an equation that calculates the tangent of the power factor angle (and thus Q/P ratio) as a function of the firing angle and the overlap angle. There most accurate equation to use for this is shown on the left-hand side of the following image. Testing to obtain the exact same power flow results as PSLF however have shown that an approximate equation as shown on the right below must be used instead (when using this, solutions match exactly). Check the box **Use Approximate DC Converter Power Factor Equations (not recommended)** in order to use this calculation instead. While not generally recommended, when loading a power flow case from an EPC file, this box is checked to match the treatment in the EPC file.

![SolutionOptionsPSLFDCConverter](images/SolutionOptionsPSLFDCConverter.png)

Use PSLF treatment of Fixed Tap in DC Converters (not recommended)Added in Version 22 build on August 20, 2021

The line commutated DC Converter equations involve the calculation of a TotalTap from VariableTap and a FixedTap. The equations to calculated TotalTap should be {TotalTap = VariableTap + FixedTap - 1}, and all software tools use this equation with AC transformers. However with AC transformers embedded inside the DC converter model only, testing to obtain the exact same power flow results as PSLF have shown that a value of VariableTap\*FixedTap must be used instead (when using this, solutions match exactly ). Check the box **Use PSLF treatment of Fixed Tap in DC Converters (not recommended)** in order to multiply taps in this manner. While not generally recommended, when loading a power flow case from an EPC file, this box is checked to match the treatment in the EPC file.

Include Loss Penalty Factors in ED

If checked, the economic dispatch calculation will consider losses in determining the most economic generation dispatch. Otherwise, the generation dispatch calculation will disregard system losses.

Enforce Convex Cost Curves in ED

The economic dispatch algorithm attempts to set the output of all generators that are set to be automatically controlled so that the system’s load, losses, and interchange are met as economically as possible. The algorithm is guaranteed to reach a unique solution only when all generator cost curves, which model the variation of the cost of operating a unit with its output, are convex. If this option is checked, Simulator will identify units whose operating point is outside the convex portion of the cost curve and set them off automatic control.

---

<a id="power-flow-solution-island-creation"></a>

## Power Flow Solution: Island Creation

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_IslandCreation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_IslandCreation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When allowing dynamic slack bus assignment, the choice of the island slack bus is managed in Simulator by internally maintaining a list of buses the user has identified as slack buses while in Edit Mode. Electrical islands are then dynamically determined from the system topology. As branch statuses are changed, this list of islands (and slack buses) will automatically change .

The process used to build islands and choose the island slack buses is described as follows.

Step 1: Build the Islands

Islands are determined by going through the topology of the power system and building groups of buses that are connected by closed AC branches in the system (DC branches don’t count here). Each group of buses all connected by AC branches will be considered an Island by PowerWorld Simulator. The [case information display in the Model Explorer showing the of islands.](05-case-information-displays-by-object-part3.md#island-display) This list of islands however will only show islands that are energized or islands with more than 1 bus. Note there are also fields that can be added to the list of Islands which show the number of generators, loads or switched shunts in the island which can be useful information to know.

Step 2 : Choose Slack Bus for each Island

After these island bus groups are determined simulator will then determine which bus to choose as a slack bus. Part of the user-input for a bus is a field called Slack which can be set to YES or NO via an AUX file. You can also change this parameter of the Bus Edit Mode Dialog by checking the appropriate check box. If an island has exactly one user-identified slack bus, then that is used as the slack. If an island has greater than one user-identified slack bus, then the user-identified slack bus which has the largest maximum generator MW output is used as the slack bus. If an island has no user-identified slack buses, then Simulator will attempt to pick one of the buses in the island as the slack bus.

When picking a slack at this point we then look at another user-input integer field for a bus called SlackPriority (SlackPriority was added in Version 19, build on March. 17, 2016). Normally SlackPriorityare all zero, so this doesn’t matter, but if a user enters positive integer values, then we choose the buses within the island that have the highest positive integer only and consider them using the following rules.

From the list of candidate buses, the five criteria listed below are used. If buses are found that meets all five criteria, then of those buses the one with the largest maximum generator MW limit will be used. If no bus is found which meets these criteria, then of the buses that meet the first three criteria, the one with the largest maximum generator MW limit will be used. Again, if no bus is found, the first two criteria are used and so on. Under no circumstance will a generator set to any kind of wind power control mode be selected as an island slack bus.

> 1.  Generator regulates a bus in this island
> 
> 2.  At least one generator at the bus is set to AVR = YES
> 
> 3.  The sum of the Maximum MW limits for generators at the bus is less than 5,000 MW (if there is more, these are probably a fictitious MW limits)
> 
> 4.  Generators at the bus regulate their terminal bus (this will be required by the slack bus anyway). However, if another bus with generation that does not regulate its terminal bus is available and this other bus has a maximum MW output that is 5 times higher, it will be chosen.
> 
> 5.  There is only one generator at the bus (it is just easier for the user to keep track of then). However, if another bus with multiple generators is available and this other bus has a maximum MW output that is 5 times higher, it will be chosen.

As a last resort, if no generator is picked as a slack but the island has a generator that is regulating a bus outside the island, then that generator is set to regulate its own terminal.

Step 3 : Ensure that the island is considered viable

If the slack chosen in Step 2 was not user-specified (Slack = YES), then we do some checks to ensure the island is viable. We do not do these checks if Slack was chosen because the user has already indicated that these are good slack buses so we don’t restrict their choice as a slack as much.

> 1.  (Has at least one bus with closed load of nominal MW in per unit \> 0.001)
>     
>     OR (Has at least one bus with closed load of nominal Mvar in per unit \> 0.001)
>     
>     OR (Has a DC tie to another island).
> 
> 2.  (Has more than 1 bus)  
>     OR \[Has a DC tie to another island\]

If the island does not pass these tests then the slack choice is discarded and the island is considered not viable.

Step 4 : Ensure that the island has enough controllable generation (Note: This step is only done during Contingency Analysis when the option "[Prevent new island without enough controllable generation](22-contingency-analysis-options.md#basics)" is chosen. See the help on [Contingency Options Basics](22-contingency-analysis-options.md#basics) for more information)

This new step that can be optionally used in contingency analysis was added in Version 19, Build on January 9, 2017

This step is only done during a contingency analysis solution when the option "Prevent new island without enough controllable generation" is chosen. The goal of this option is to ensure that the MW controls specified for generators in the island have a reasonable chance of actually meeting the load and losses in the island. If the estimate shows that the slack bus chosen for the island in Step 2 above will likely end up operating well outside of its Minimum and Maximum MW output then the slack choice is discarded and the island is considered not viable. Also note that this is only done if the estimate load MW in the island is less than 50% of the total load in the case. This check on load MW is done to ensure that this additional check is only done on smaller islands created by the contingency and is not applied to the largest island in the case.

To perform this, the following calculation across all buses in the Island are done.

>   - GenControllableMWMax = sum of generator MWMax of generators which are both Online=YES and (AGC=YES or it is slack bus)
>   - GenControllableMWMin = sum of generator MWMin of generators which are both Online=YES and (AGC=YES or it is slack bus)
>   - GenNotControllabeMW = sum of generator MW of generators which are both Online=YES and (AGC=NO and it is not slack bus)
>   - LoadMW = sum of load MW of online loads (see \*\*note below)
>   - ShuntMW = sum of bus, switched, and line shunt actual online MWs (see \*\*note below)
>   - LossMW = sum of loss on devices inside the island (see \*\*note below)

In addition we calculate a value across all loads in the case

>   - LoadMWCase = sum of load MW of all online loads in the entire case

From these values we do the following calculations

>   - MaxDeviation = 0.01\*LoadMW, but bound MaxDeviation so that it must be between 10% and 100% of the Contingency Options Make-up Power Tolerance (AGCToleranceMVA)
>   - ControlNeeded = LoadMW + ShuntMW + LossMW – GenNotControllableMW
>   - If (ControllNeeded – GenControllableMWMax) then Deviation = ControllNeeded – GenControllableMWMax  
>     Else if (ControllNeeded \< GenControllableMWMin) then Deviation = ControllNeeded – GenControllableMWMin  
>     Else Deviation := 0
>   - If (abs(Deviation) \> MaxDeviation)  
>     AND  
>     (LoadMW \< 0.1\*LoadMWCase)  
>     Then consider the island to not be viable and discard the slack bus choice from Step 2.

\*\*Note: the calculation of LoadMW, ShuntMW and most importantly LossMW assume that the existing system bus voltage and angle values represent a reasonable power flow solution. Remember that these island checks are being done before a power flow solution is attempted so we cannot rely on reasonable bus voltages and angles always. This works in the contingency analysis tool because we can relay on the pre-contingency reference state having reasonable voltage and angles. This would not work well in other situations where a reasonable guess at Loss MW could not be made. This is why this option is limited to use in the contingency analysis tool.

---

<a id="post-power-flow-solution-actions-dialog"></a>

## Post Power Flow Solution Actions Dialog

*Source: [`Content/MainDocumentation_HTML/Post_Power_Flow_Solution_Actions_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Post_Power_Flow_Solution_Actions_Dialog.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Post Power Flow Solution Actions dialog describes a list of actions that are executed at the end of every Full AC power flow solution, which means they are not performed for DC solutions. Normally, these actions would all have Model criteria specified.

To open this dialog, select **Simulator Options** from the **Case Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab. Next, go to the **Power Flow Solution** category. Then click on the **Advanced Options**. Finally click the button labeled **Define Post Power Flow Solution Actions.**

Check the **Do Not Used Post Power Flow Solution Action List** check-box to disable using any actions defined in the list.

The action list display identifies the actions that comprise the post power flow solution action list. Actions can be inserted or deleted by using the local menu on the dialog. Right-click on the display and select **Insert** or **Delete**. Actions are inserted via the [Contingency Element Dialog](24-contingency-element-dialog.md#contingency-element-dialog).

The action display is a type of [Case Information Display](04-model-explorer-and-case-information-part1.md#case-information-displays) and thus shares many [characteristics and controls](https://www.powerworld.com/WebHelpvoid\(0\);) common to all other case information displays.

The Action List Display always contains the following fields:

Actions

This shows a string which describes the action. You may customize the format of the string that describes the actions by right-clicking on the Action List Display and choosing **Display Descriptions By**, and then choosing either Name, Num, Name/Num, PW File Format by Numbers, PW File Format by Name/kV or PTI File Format.

Model Criteria

Simulator allows you to define Model Criteria, which consist of both [Model Conditions](04-model-explorer-and-case-information-part3.md#model-conditions-display-and-dialog) and [Model Filters](04-model-explorer-and-case-information-part3.md#model-filters-display-and-dialog). These specify a criteria under which a contingency action would occur. For example, you could specify that a generation outage only occur if the pre-contingency flow on a line is higher than a specified amount. Normally, no Model Criteria will be specified, and this field will be blank. Also, note that Model Criteria can be overridden by the Model Condition and Filter option on the [Contingency Options Tab](22-contingency-analysis-options.md#options-tab). You can open a dialog to define Model Filters or Conditions by right-clicking on the Action List Display and choosing **Define Model Criteria**.

Status

The following options are available for this field:

  - CHECK : The action will be executed only if the Model Criteria is true. It will also be executed if no model criteria is specified. This is the default setting
  - ALWAYS: The action will always be executed, regardless of the Model Criteria.
  - NEVER: The action will never by executed, regardless of the Model Criteria.
  - POSTCHECK: This action is checked AFTER the other Check and Always actions have been performed and the load flow solution solved. If the criteria specified for the Postcheck action are met in the resulting load flow solution, then this action is taken and the load flow is again resolved. This will recursively occur for all Postcheck actions until either all postcheck actions have been taken, or the criteria for all remaining postcheck actions have not been met.

Note that the Never action allows you to disable a particular action without deleting it.

Comment

A user-specified comment string that can be associated with this action. While this comment is not used by Simulator in any way, these comments can be saved to be loaded at a later time. This is provided for the user to add comments regarding the action. For example, for an action with a Model Criteria you may could add a sentence explaining why the action is only performed under the specified criteria.

---

<a id="power-flow-solution-island-based-agc"></a>

## Power Flow Solution: Island-Based AGC

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_Island_Based_AGC.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_Island_Based_AGC.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the Island-Based AGC tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

The Island Based AGC options allow the user to choose to dispatch generation by island instead of by area or super area. The options available for dispatch here are:

Enable Island-based Automatic Generation Control (AGC)

When this option is selected, Island-Based AGC is being used, and area and super area dispatch options are ignored.

Island AGC Tolerance 

This sets the AGC tolerance in MW for the real power balance of each island. Generation must equal load plus losses plus DC line exports in each island. If necessary, each island slack bus output will vary during the [Power Flow (Inner) Loop](#solving-the-power-flow) solution to maintain the real power balance for the island. If it varies more than the specified tolerance and if a form of Island-based AGC is specified, then adjustments to AGCable units will be made in the [MW Control (Outer) Loop](#solving-the-power-flow) according to the selected Island-based AGC option.

Use Participation Factors of individual generators

When selected, the island-based AGC is used, based on the individual participation factors of each generator within the island. Area and super area ACE requirements will be ignored, and all generators in the island will be dispatched to serve load, losses, and any DC transfers to other islands.

If all generators with AGC = YES have participation factors also equal to 0.0, then all make-up power will come from the island slack bus.

Calculate Participation Factors from Area Make Up Power Values

The AGC will dispatch generation by using area make up power values, instead of by individual participation factor. What this means is that each area will be assigned a make up power value, similar to assigning a participation factor to a generator. Based on the make up power value of each area in the island, the amount of the generation dispatch needed will be divided amongst each area based on its value. Higher values will account for more of the generation dispatch than areas with smaller values. Then within each area, the generation dispatch is handled on an individual generator participation factor basis, where each generator will account for a portion of the dispatch that was assigned to its area.

To specify the make up power values for each area, click on the **Specify Area Make Up Power Values** button. Note that these settings are the same as those used by [Contingency Analysis Options Make Up Power](22-contingency-analysis-options.md#basics), therefore changing these values will affect the contingency analysis.

For example, three areas have participation factors of 2, 1 and 1, respectively. If the total generation redispatch in the island is 100 MW, then area 1 will account for 2 / (2+1+1), or 50%, of the total. Therefore area 1 is expected to redispatch by 50 MW. If area 1 then has two generators with participation factors of 4 and 1, they will account for the 50 MW by picking up 4 / (4+1) and 1 / (4+1), or 80% and 20%, respectively, of the 50 MW needed from the area.

If all areas have **CTG Make Up Gen** equal to 0.0, then all make-up power will come from the island slack bus.

Dispatch using an Injection Group (Loads and Generators will respond)

Checking this option will allow for the island dispatch to be covered by change in generation and/or load defined in an [injection group](07-object-properties-run-mode-and-general-part2.md#injection-groups-overview).

Additional options are available when dispatching based on an injection group:

Allow only AGC Units to Vary

If this option is checked, only units whose AGC status is turned on will be allowed to participate in the injection group dispatch.

Enforce unit MW limits

If checked, then each generator’s defined MW limits will be strictly adhered to during the redispatch.

Do not allow negative loads

When checked, loads included in the injection group are not allowed to drop below zero MW or MVAR load demand.

How should reactive power load change as real power load is ramped?

You can choose to keep the ratio of real and reactive power constant for each load that is included in the injection group, or you can specify a constant power factor that the MVAR value will be determined from when the MW value is changed.

Injection groups have their own set of options that can override the default options on this dialog if they are in use. See the [Injection Group Specific Scaling Options](05-case-information-displays-by-object-part3.md#injection-group-display) topic for more information.

---

<a id="power-flow-solution-dc-options"></a>

## Power Flow Solution: DC Options

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_DC_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_DC_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the DC Options tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Use DC Approximation in Power Flow

When this box is checked, Simulator will solve the load flow using the DC approximation method. When not checked, Simulator performs the Full Newton AC load flow algorithm. Once a case, especially a large one, has been solved using a DC approximation, it tends to be quite difficult to revert back to the Full Newton AC load flow from a solved DC approximation.

DC Power Flow Model

These choices also affect the calculation of sensitivities on the [PTDF](20-sensitivities.md#power-transfer-distribution-factors), [LODF](20-sensitivities.md#line-outage-distribution-factors-lodfs), and [TLR](20-sensitivities.md#shift-factor-sensitivities-dialog) dialogs and [ATC Tool](32-available-transfer-capability.md#solution-methods) calculations.

Generally, the *only* inputs that affect the DC power flow equations are line impedances and line status (open/closed). However there are three possible modeling choices (for which there is not general agreement in the industry) that will affect the DC equations in small ways. These choices are made here on the DC Power Flow Model options:

**Ignore Series Resistance (r)** or **Ignore Series Conductance (g)**

The series term of a transmission line consists of an r and x value which represent a complex number impedance. In the DC power flow approximation, the value that used is the imaginary part of the inverse of impedance (called admittance)

g + jb = 1 / (r + jx) = r / (r^2 + x^2) – j x / (r^2 + x^2)

Thus

g = r / (r^2 + x^2)

b = – x / (r^2 + x^2) \*\*\* This term is used in the DC power flow equations

The only term that is used in the DC power flow equations is the b term. Some say that a DC power flow means that r = 0 which means that b = -1/x and g = 0. Others say that a DC power flow only means assuming that g = 0, which means that b = - x / (r^2 + x^2). There is not a good consensus in the industry as to what is correct regarding this, so Simulator offers an option as to whether you ignore r or ignore g. The default option in PowerWorld is to ignore the resistance.

**Ignore Transformer Impedance Correction Tables**

These are both ignored by default.

When a transformer impedance correction table is specified for a transformer, the series impedance of the transformer will vary by a multiplier with the tap or phase of the transformer. The tap ratio is not generally relevant to a DC power flow, however the phase-shifter angle could vary when using the DC approximation. This option specifies whether to ignore the impact of this impedance correction. For phase shifters the multiplier is normally between 1.00 and 1.50 and thus tends to *increase* the impedances as you move away from zero degrees.

The issue with not ignoring this is it creates a situation where the equations for the DC approximation are dependent on the system state. In other words, the matrix equations become a function of the phase-shift angle. This results in a situation in which the matrices must be recalculated and re-inverted each time a phase angle is moved. This removes some of the advantages of the DC approximation. This can be especially problematic when using the OPF or SCOPF.

Compensate for Losses by Adjusting the Load

Traditionally a DC load flow is treated as lossless. However, you can approximate the loss in the load flow by artificially adjusting the load in the case to include estimated losses. To do so, click on the **DC Loss Setup** button to open the [DC Power Flow Loss Setup](#dc-power-flow-loss-setup) dialog for setting the DC Loss Multipliers.

Compensate for Dispatch Sensitivities with User-Specified Values

This option allows for the bus MW loss sensitivities to be used in the OPF and ED dispatch algorithms, if the type of loss sensitivity on the [General](#power-flow-solution-general) tab is set to User-Specified.

---

<a id="dc-power-flow-loss-setup"></a>

## DC Power Flow Loss Setup

*Source: [`Content/MainDocumentation_HTML/DC_Power_Flow_Loss_Setup.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/DC_Power_Flow_Loss_Setup.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

To open the DC Power Flow Loss Setup dialog, select **Simulator Options** from the **Case Options** ribbon group on the [Options](02-simulator-ribbon.md#options-tab-overview) ribbon tab. On the Power Flow Solution page, click on the tab labeled **DC Options**. Next, click the button labeled **DC Loss Setup**. This button will only be enabled when you check the box to **Use DC Approximation in Power Flow/OPF/SCOPF**.

The DC Power Flow Loss Setup dialog gives you a location to apply approximate losses during a DC load flow solution. The losses can be approximated by scaling the loads in the case to include an approximation of losses. Loss multiplication factors can be applied individually by bus, or as a group by area or by zone. Note that loss multipliers by area or by zone are just quick ways for setting the bus multiplication factors for all buses in the group. You will see the value reflected for all buses in the Buses page. If you wish to apply the same multiplication factor to the entire case, you can simply set the Case DC Loss Multiplier at the bottom of the dialog. This will automatically set all buses in the case to have the same DC Loss Multiplier specified.

Once the DC Loss Multipliers have been set, click OK to save the multipliers.

---

<a id="power-flow-solution-general"></a>

## Power Flow Solution: General

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_General.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_General.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the General tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Assumed MVA Per-Unit Base

This option allows the user to specify the MVA base to be used for the entire case. By default, this value is set to 100 MVA. Click on the **Change System Base** button to change this value. Changing this value will update all of the internal structures to store the proper values on the new base.

Bus Loss Sensitivity Function

Bus loss sensitivities indicate how island or area losses change with power injection at the bus. Here you may choose to forego the calculation of bus loss sensitivities or to base them on island losses or area losses. If the case consists of only one island, which, by definition, corresponds to the entire system, then the bus loss sensitivities are measured with respect to total system losses. If the bus sensitivities are set to *User-Specified*, the sensitivities will remain at their last calculated values, according to the loss function type previously specified when the [loss sensitivities](20-sensitivities.md#loss-sensitivities) were calculated.

Monitor/Enforce Contingent Interface Elements

This global location allows you to determine how contingency elements in an interface should be treated in Simulator. You can choose to never include the impact of contingent elements on interface flow, to only include contingent element impacts in the standard power flow or optimal power flow routines, or in all solution routines including contingency analysis and security constrained OPF.

It is not uncommon to ignore the impact of contingent elements when using the contingency analysis or security constrained OPF tools, as they are already processing lists of contingencies and evaluating flows on interfaces. Ignoring contingent elements within interface definitions allows for a determination of the impact of other contingencies on the flows of the non-contingent elements forming the interface, without impact from additional contingent element considerations.

There are some tools in which contingency elements in an interface are <span class="underline">always</span> ignored regardless of how this option is set. These include the following:

  - [Line Outage Distribution Factors (LODFs) Sensitivity Tool](20-sensitivities.md#line-outage-distribution-factors-dialog)
  - LODFs for interfaces containing contingency elements will be calculated based on the monitored branches only and the contingency elements will be completely ignored
  - [Contingency Analysis](21-contingency-analysis-overview-and-records.md#contingency-analysis-overview)
  - When using a linear calculation method or the case is in DC power flow mode an interface containing contingency elements will be completely ignored as a monitored element
  - [ATC Analysis](32-available-transfer-capability.md#available-transfer-capability-atc-analysis)
  - Interfaces containing contingency elements will be monitored for base case limits, but will be completely ignored during monitoring for contingency limits

Power Units for Display

Shows which power units, Mega- units or Kilo- units, are used for displaying values. The units cannot actually be changed with this option, but this option can be changed through an auxiliary file.

---

<a id="power-flow-solution-storage"></a>

## Power Flow Solution: Storage

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_Storage.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_Storage.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the Storage tab after choosing the [Power Flow Solution](10-power-flow-solution-and-options-part1.md#power-flow-solution-options) page of the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options).

Simulator offers the ability to restore either the last power flow solution state or the state of the system immediately before the last solution attempt. If your system has insufficient memory and you are working with large systems, you may wish to disable one or both of these options.

Disable "Restore last solution"

Restoring the last solution will undo any changes made to the data that were made after the last successful solution and return the case to the last valid solution. For large cases, the amount of memory required to store the last solution can be significant. If this option is checked, Simulator will not store this information in memory, and the last solution cannot be restored if a solution fails.

Disable "Restore state before failed solution attempt"

Restoring the state before failed solution attempt will undo only the attempted solution, but will retain any changes to data that were made before the solution process. This allows the user to return to the point just before the solution in order to add or remove changes in an effort to obtain a valid solution. For large cases, the amount of memory required to store the state before a solution attempt can be significant. If checked, Simulator will not store the state information in memory, and the state before the failed solution cannot be restored.

Even if you are not disabling these options, these system states might not be available for restoration under a couple of situations: switching to Edit Mode or adding or deleting a MW Transaction between areas will destroy these system states. The system states will be created again once a power flow solution is attempted, but the system states from any previous solutions will be destroyed.

---

<a id="environment-options"></a>

## Environment Options

*Source: [`Content/MainDocumentation_HTML/Environment_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Environment_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The Environment page provides you control over a number of display and simulation options. The first section of the page contains a list of check boxes that you can use to designate the content of the oneline displays.

These options include:

Do Not Solve While Animating (Display Only)

If checked, Simulator only displays the case; it does not solve the power flow equations. System flows are determined by the initial values in the case file. This option should be checked if you simply want to use Simulator to visualize a case that has already been solved. The advantage of the display-only mode is that animation is significantly faster, particularly for large cases. The drawback to the display-only mode is that the power flow equations are not automatically solved at each time step; you must explicitly call for a Power Flow Solution using either the **Solve Power Flow** button in the **Power Flow Tools** ribbon group on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab or choose one of the solution options under the **Solve** menu in the **[Power Flow Tools](02-simulator-ribbon.md#simulation-control)** ribbon group.

Play/Animation Solution Method

This option is available only for OPF releases of Simulator. Use it to indicate whether Simulator’s repetitive power flow should perform a normal power flow solution or an optimal power flow (OPF) solution.

Solution Animation

Check Auto Start Solution Animation to automatically start the animation after loading the case.

Check Auto Solve On Load to automatically solve the power flow solution when the case is loaded.

Show Log

If checked, the message log is displayed. The message log shows detailed results of each Power Flow Solution. Usually this log is NOT shown. However, if you are running into problems with a simulation case, it can prove useful for debugging the case.

Disable Showing Blackouts

You can dramatize a power flow case’s failure to converge by representing it as a blackout. The background of the oneline diagram will become a dark shade of gray, and a message box will appear to announce that the system has experienced a blackout. To disable this behavior, select the Disable Showing Blackouts box. Representing the failure to converge as a blackout can be very helpful for presentation purposes. Very often, the power flow’s failure to converge can be traced to the system’s inability to serve the load demand, a situation that requires that load be "blacked out," or shed, to restore the system to a viable operating state. Thus, displaying the failure to converge as a blackout has physical significance.

Disable AGC When Manually Changing Generator MW

When this option is checked, changing the MW output of a generator manually will automatically remove a generator from [Automatic Generation Control](10-power-flow-solution-and-options-part3.md#area-control). If you wish for generators to maintain their automatic generation control settings following a manual change of MW output, you must uncheck this option.

Open Associated Oneline Diagrams

By default, Simulator has always attempted to open any diagrams that were open with a case file when the case file was last closed. However, now you may uncheck this option and Simulator will not attempt to open any oneline diagrams when a case is loaded.

Auto Open Bus Records if No Oneline

If a case is opened in Simulator which does not have an associated oneline diagram, then Simulator will automatically open the [Bus Records](05-case-information-displays-by-object-part1.md#bus-display) case information display if this option is checked.

Allow to Prompt for comment when saving case

If checked it will force saving the case with comments by popping a [dialog](05-case-information-displays-by-object-part1.md#case-description) every time a case is saved.

Auto Set Present as Base for Difference Case Tool when Loaded

This option allows the present case to be set as a base automatically after being loaded. This can be done always or never, or only if the base case has not been set before opening the case.

Reset Default Positions and Styles for all Dialogs

Click this button to reset the default position, size and Free-Floating/Contained style of the dialogs. See [Window Basics](01-getting-started.md#windows-basics) for more information.

Custom Colors

This option allows the user to edit the custom colors used throughout all Simulator color dialogs.

Clock Style

The clock serves as a timer for timed simulations by showing the current time, the start time, and the end time of the simulation. You can choose to hide the simulation clock by specifying a clock style of *None*. Otherwise, to display the clock in its own window, choose *Dialog*, and to display the clock on the program’s status bar, select *Status Bar*.

Measurement System

This option allows the user to choose English (Imperial) or Metric (SI) units for system measurements. By default, this option is set to English units.

Recently Used File List Entries

The maximum number of file names and locations stored in the History List of the File menu.

Undo Memory Limit Per Oneline

The approximate maximum number of Megabytes allowed to be used in storing actions carried out when editing a oneline diagram, which can be undone at any time.

Use Touchscreen Menu

Check this box to enabled the [Touchscreen Menu](01-getting-started.md#touchscreen-interaction), available on fullscreen oneline diagrams.

Tap Correction

Tap correction adjusts for imprecise interactions with small display objects on a oneline in a touchscreen interface. If a tap misses the intended target and hits the oneline background instead, the Tap Correction slider sets a radius within which Simulator will intelligently search for the intended display object. High Tap Correction searches a wider area; the lowest Tap Correction setting turns it off entirely.

---

<a id="oneline-options"></a>

## Oneline Options

*Source: [`Content/MainDocumentation_HTML/Oneline_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Oneline_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

These options are available on the Oneline tab of the [PowerWorld Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) dialog. It is important to note that the options on this dialog apply to *all* oneline diagrams. There are also a large number of options which apply only to an individual oneline diagram. The diagram-specific options are specified on the [Oneline Display Options Dialog](15-using-onelines-tools-and-options.md#oneline-display-options-dialog).

There are two sub-categories on the Oneline Options tab: Visualization and File.

**Visualization**

Visualizing out-of-service elements

These three options allow you to choose how objects on the diagram should appear when they are representing a power system device that is currently "open" or "out-of-service." The three options are Blink, Use dashed lines, and Draw and X through off-line generators. The first two options apply to any oneline object, while the third option is specific to generator objects only.

Set gen MW to min when closed from oneline

This option allows the generator MW value to be set to its minimum MW output after a circuit breaker is clicked in the oneline display. Normally the generator's status is set to closed and the MW value is reset to its previous value.

Show Oneline Hints

If checked, pop-up hints will appear when you drag the mouse over an object in the oneline. These give information about the object; for example, for a generator the pop-up hint displays the bus number, generator ID, the MW output and the MVAR output. You may also customize the pop-up hints for each kind of display object by choosing [Options \> Custom Hint Values](15-using-onelines-tools-and-options.md#custom-hint-values) from the menu.

Show X,Y Coordinates

If checked, the (x,y) location of the cursor is monitored in the status bar at the bottom of the screen. The (x,y) location of the cursor is only shown in Edit Mode. By default, this option is selected.

Save Contour Image with Oneline File

If checked, and if a contour is being displayed on the oneline diagram, Simulator will store the contour with the oneline diagram when you save the case or save the oneline. It will store the contour as a bitmap.

Display Unlinked Elements in Run Mode

Typically, unlinked graphical objects are not visible in Run Mode. Checking this option will allow the display of unlinked elements during Run Mode.

Enable Mouse Wheel Zooming

This option allow the use of the mouse wheel to zoom in and out in the currently selected oneline diagram.

Maximum number of open onelines

Option to specify the maximum number of onelines that can be open simultaneously (this option defaults to 10). If this maximum threshold is exceeded than PowerWorld will automatically close the oneline whose most recent access is the oldest. By default a oneline can be closed in this manner, but an additional oneline-specific option has been added that can be changed to prevent this closure. This feature is useful for users who make extensive use of oneline links or substation display object links which can make opening dozens of onelines very easy. Opening dozens of onelines can slow down the program substantially. If you have a main oneline from which other onelines are automatically opened, then you may want to prevent the main oneline from closing.

Minimum Screen Font Size

The minimum font size at which text is visible on the screen. When text is rendered to the screen, any text which is smaller than this font size will not be rendered. This is useful when zooming out on a oneline diagram where a lot of text might become cluttered or hard to read on the screen.

Minimum Print/Copy Font Size

The minimum font size at which text can be printed or copied. This is useful if the application or printer you are sending to can or cannot display smaller fonts. When text is printed, any text which is smaller than this font size will not be printed. Normally the Minimum Print/Copy Font Size is smaller than the Minimum Screen Font Size because the resolution of the printed document is much higher than the screen resolution.

Transformer Symbol

Since transformer representation varies in different countries, this option allows the user to represent transformers as coils or circles. By default, transformers are represented as coils.

Line Navigation Arrows

These settings control whether the Pixel Size of the arrows, how long in seconds it should take to pan to the line end locations, and whether to show navigation hints as your mouse hovers over the arrow. See [Oneline Zoom and Panning](17-oneline-view-printing-and-contouring.md#oneline-zooming-and-panning) for more information.

**File**

Automatic Loading of Display Auxiliary File

This option is used options to automatically load a Display Auxiliary File (AXD) with one specific oneline. This setting is stored in the case (PWB) so that it only applies to onelines opened with the specific case.The file full path location has to be specified in the **Display Auxiliary File** box.

Automatic Loading of Display Auxiliary File with ANY oneline (Only saved to the Registry)

This option is used options to automatically load a Display Auxiliary File (AXD) with each oneline that is opened. This setting is stored in the windows registry so this applies to all onelines opened on the computer. The file full path location has to be specified in the **Display Auxiliary File** box.

Main Oneline File

This option is used to identify the primary oneline diagram to use with the case. The main oneline is the file that is displayed when you first open the case. The dropdown box lists all the oneline files that reside in the same directory as the case. Select one of these files, or enter the full path of the oneline you want to use if it does not appear in the dropdown box.

Use Default Oneline File

You can command Simulator to open a particular oneline diagram file if it cannot find a oneline diagram file for the case you are trying to open. For example, there is no oneline diagram associated with a PSS/E raw data file when you first read it into Simulator. However, if your application is such that you will always use the same oneline file whenever you open a PSS/E raw file, check the **Use Default Oneline File** to have Simulator open the oneline identified in the **Default Oneline File** box whenever it encounters a case that has no associated oneline. The default oneline must exist in the same directory as the case you are trying to open.

Automatically Show Full when opening any oneline

This option is used to show the oneline diagram completely when opening any oneline. If the oneline was previously saved in a particular location in the diagram, if at the moment of opening a oneline this option is selected then the oneline will open showing the full oneline.

Edit Oneline Browsing Path

This option applies when you have [Oneline Links](12-building-onelines-branches-and-devices.md#links-to-onelines-and-auxiliary-files) included on a oneline diagram. Rather than specify the full path and name of a oneline diagram as a oneline link, you can specify the file name only. When the link is clicked in Run Mode, Simulator will check all directories listed here, in order, to try and find the oneline file name stored with the link. This browsing path is also used when looking up [Shapefile Database Rcords](16-oneline-gis-tools.md#shapefile-database-record-dialog) and when finding the substation layout, URL, or command specified on the [Substation Information Dialog](06-object-properties-edit-mode-part1.md#substation-information).

Save Onelines when Saving Case

By default, Simulator always saves any oneline diagrams that are open when the user chooses to save the case (pwb) file. This option allows you to choose to be prompted to save oneline diagrams when a case file is saved, or to never save onelines when the case file is saved.

Open Oneline Links By

Open Oneline Links specifying if oneline links are to be opened by Number, Name\_kV, or Label.

---

<a id="file-management-options"></a>

## File Management Options

*Source: [`Content/MainDocumentation_HTML/File_Management_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/File_Management_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are useful when loading, storing, and configuring data in different file formats supported by PowerWorld.

**PowerWorld Files**

Automatic Loading of Auxiliary File

A default auxiliary file can be loaded when the present case is opened by checking the **Automatically load an auxiliary file when the present case is opened** check box. The auxiliary file given under **Auxiliary File** will then be loaded with the present case. The full path needs to be included with the file name. This option is stored when the case is saved in the PWB format.

Automatic Loading of Auxiliary File with ANY Case 

A default auxiliary file can be loaded when each case is opened by checking the **Automatically load an auxiliary file when ANY case is opened** check box. The auxiliary file given under **Auxiliary File** will then be loaded with each case. The full path needs to be included with the file name. This option is stored in the system registry.

Automatic Archiving of PWB Files

This option allows you to effectively make backup copies of your working case every time you save the PWB file. For example, assume you have a case named *Test Case.pwb*. With the Automatic Archiving turned on, saving the case will first create a copy of the original file and rename it *Test Case\_1.pwb*. The character used as a delimiter can be chosen optionally. The case with any changes you have just made will then be saved as the new *Test Case.pwb* file. Each time you save the case, the latest version is named *Test Case.pwb*, the last *Test Case.pwb* is renamed with the delimiter and 1 appended, and all other archived versions will be renamed with their number incremented by 1. The number of archive versions to maintain can also be chosen by setting the maximum number of archive files property.

Autosave Every … Minutes

This option allows the user to specify how often (in minutes) the case is automatically saved. A value of zero means that this option will not be used. A case will only be autosaved while in Edit Mode. The case will be autosaved in the same directory from which the last case was opened unless a specific **File Location** is specified. Cases will be saved with the name *autosave.pwb*.

The autosave and automatic archive options can be used simultaneously. If both are in use, the autosave.pwb file will be saved with incremented versions as described in the **Automatic Archiving of PWB Files section**.

File Location

Specifies where the autosaved PWB files are saved. If this is left blank, the files will be saved in the same directory from which the last case was opened.

Save Unlinked Elements of contingency, interface and injection group records in the PWB file

Checking this box allows saving any unlinked contingency, interface, and injection group records in the PWB case. The unlinked elements are only created when read from an auxiliary file containing unlinked records.

**EPC and RAW Files**

GE Additional Data Options

Load Additional Data from ECF

Older versions of Simulator did not read all the extra data from the GE EPC file and instead stored it in files with the ECF extension. If you would like to read in one of these old ECF files, click this button.

Remove Additional Data from Case

Because all of the extra data in the EPC can take up a lot of space (approximately doubles the PWB file size and increases the memory foot-print of Simulator itself too), you may want to just delete all this information. Click this button to permanently remove this data from your case.

GE EPC Motor Data Table

Part of the extra data read from the EPC file is Motor Data which does not map to an object used inside PowerWorld. To see this information, click on this button.

PTI RAW Transactions due to tie-line loads

Loads may be assigned to a different area than the load’s terminal bus. PTI offers an option that allows the user to ignore this assignment when calculating the tie-line flow for an area.

(AREA INT CODE = 1 FOR LINES ONLY)

(AREA INT CODE = 2 FOR LINES AND LOADS)

Simulator does not allow you to define a load this way and then choose to ignore it. Most RAW files that PowerWorld has seen seem to be solved ignoring the loads that are in different areas than their terminal bus by using the "lines only" option. To overcome this, when PowerWorld reads a RAW file, [MW Transactions](05-case-information-displays-by-object-part3.md#mw-transactions-display) are automatically created with the ID "RAW\_LOAD". (You can optionally choose to load the RAW file "with options". This will allow you to choose whether or not the transactions should be added. See [Case Formats](03-cases-files-and-formats.md#case-formats) for more information.) These transactions are between the load’s area and its terminal bus and are created so that the export from each area correctly matches a case solved using "lines only". If you know that your case was solved using "lines and loads", then click the button **Remove transaction due to tie-line loads**. Clicking this will delete all the MW Transactions with an ID of "RAW\_LOAD". You may also click the button **Add transactions due to tie-line loads** to recreate a list of transaction which represent flows between loads with different areas than their terminal bus.

PTI RAW Three-Winding XF Star Bus Numbering

In RAW format data, three-winding transformer star buses are not explicitly defined. Within Simulator these buses are explicitly created and assigned as one terminal of the three two-winding transformers that comprise the three-winding transformer. These options specify how the star buses are numbered:

**Use numbers near primary bus number**

A star bus number will be chosen from unused bus numbers that are near the number of the primary bus number of the three-winding transformer.

**Start numbering above the maximum bus number**

The maximum bus number is determined by the buses that are explicitly defined in the RAW file, i.e. none of these are star buses. Star buses are number sequentially starting at the next highest bus number and assigned in the order in which three-winding transformers are defined in the RAW file.

**Start number at specified bus number**

The star buses of three-winding transformers are numbered in the order in which they are read from the RAW file starting with the specified bus number. The star buses are ordered sequentially starting from the specified number. Any bus numbers that have already been used will be skipped and the next unused number will be asigned.

Transformer Regulated Bus Side

EPC and RAW files require the storage of which side of the transformer the regulated bus is on to determine which direction to move the tap in order to regulate voltage. In PowerWorld the tap sensitivity is always calculated when a transformer needs to move so this is not relavent. The buttons are provided to determine this side. If you have a solved power flow solution, then using tap sensitivities is good. If you do not have a solved power flow, then Recalculate using Closest Bus will also work (this just determines how far away the regulated bus is from the FROM and TO bus by summing up the total impedance that must be crossed to reach the regulated bus.)

**hdbexport Files**

All of the following options are stored in the system registry.

Mapping of CBTyp to Branch Device Type

When loading an hdbexport CSV file, a Branch record in Simulator is created for each CB record. The Branch Device Type for these branches is defined based on the CB's CBTyp using the following rules:

*if CBTyp contains* "CB" --\> Breaker

*Else if contains* "LBD" --\> Load Breaker Disconnect

*Else if contains* "GND" --\> Ground Disconnect

*Else if contains* "FUSE" --\> Fuse

*Else utilize user*-**Defined rules specified below**

*Else* -- Disconnect

The **Defined rules specified below** can be defined in the table in this section. The Priority can be set here for the CBTyp and the Branch Device Type can be specified with the following options: *Breaker, Disconnect, Fuse, Ground Disconnect, or Load Break Disconnect*.

Also after loading an hdbexport CSV file, if any CBTyp values were encountered that were not recognized a dialog box similar to the **Defined rules specified below** will appear prompting the user to designate the Branch Device Type rules for each CBTyp.

The **Clear Mappings** button will clear this table. Any subsequent file loads where an unrecognized type is encountered will prompt the user.

Default Label Delimiter

The default label delimiter is a dollar sign, $. The delimiter must be changed prior to loading in an hdbexport file. No changes will be made to the delimiter in existing labels.

Custom Label Generation

The specification of custom labels is done with these options. Labels are generated in these custom formats when loading an hdbexport file. No changes will be made to existing labels.

Examples of custom labels in the auxiliary file format is given below. Loading this auxiliary file will populate the table for this option.

DATA (AREVALABELIMPORTSPEC, \[ObjectType,LabelFormat,ArevaType\])

{

"Bus" "%ID\_ST%+'\_'+%ID\_KV%+'\_'+%ID%" "ND"

"Gen" "%ID\_ST%+'\_'+%ID\_KV%+'\_'+%ID%" "UN"

"Branch" "%ID\_LINE%+'\_'+%I\_\_ND.ID\_ST%+'\_'+%Z\_\_ND.ID\_ST%+'\_LN\_'+%ID\_LN%" "LN"

}

The following rules apply when defining custom labels:

1.  The label format uses the same syntax as PowerWorld's custom expression parser, which means that generating labels is very flexible.
2.  *%field%* means that you want to substitute the value in *field* for *%field%* within the string.
3.  The case database is hierarchical, which means it understands that some objects contain references to others. If you specify *%field\_type%,* Simulator will find the parent record of the current record that is being used to generate the label. If that parent record's type matches type, it will find *field* within that record and substitute it for *%field\_type%*. If the parent record's type doesn't match type, it will go up to the parent's parent and conduct the same test and so on until it finds the ancestor record whose type matches type. The generator example above of %ID\_ST% on a UN record makes sense because it will first go to the parent ND record, then its parent KV record and then finally its parent ST record to find the ID\_ST value. Note that this is technically a shorthand for item 4 below as all parents of records have pointers to their parent.
4.  The case database also contains pointers to other records that aren't parents. If you specify *%field1\_\_type.field2%*, Simulator will look at *field1\_type* and look at the record that it points to and then return the value of *field2*. Note that this can go as far as you'd like, so it can be something like *%field1\_type1.field2\_type2.field3%* and so on. The branch example above is instructive here as well with %I\_\_ND.ID\_ST%. It will get the ND record that I\_\_ND points to in the LINE record and then based on that conduct the search as in item 3 above for ID\_ST on the ND record. Note that %I\_\_ND.ID\_ST% can also be represented as %I\_\_ND.P\_\_KV.P\_\_ST.ID%. It's just shorthand.

Do Not Create Default Labels For Any Objects

Check this box to not create default labels for any objects. If no custom labels are defined for an object type and this option is checked, no labels will be created for that object type.

Translate the DC System

POLE, DCCNV, VSC, DCND, and DCLN records within an hdbexport file can be translated into mult-terminal dc line and VSC DC line objects within PowerWorld. If not translated these objects will instead be modeled as load and transformer objects. This option determines if the translation is attempted or not. Using the **Prompt each time a case is loaded** will prompt the user each time the appropriate record types are identified in a file. Upon prompting the user can select **Yes to All** which will set the **Always translate if possible option**. Selecting **No to All** at the prompt will set the **Never translate** option. If not choosing to prompt each time and one of the permanent options has been set, the option can always be changed here for future file loads.

Save Known Fields in HDB Pattern File

Pattern files are used by the hdbexport process to determine which record types and fields are included in the export file. Click this button to create a pattern file for the record types and fields that PowerWorld recognizes. A recognized field is one that PowerWorld actually uses upon loading the export file. Even though a field is not recognized by PowerWorld that will not create an error upon loading. That field will simply be ignored.

---

<a id="case-information-display-options"></a>

## Case Information Display Options

*Source: [`Content/MainDocumentation_HTML/Case_Information_Display_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Case_Information_Display_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

PowerWorld uses numerous [case information displays](04-model-explorer-and-case-information-part1.md#case-information-displays) to show power system data in tabular format. The options presented on the Case Information Display page of the [PowerWorld Simulator Options dialog](10-power-flow-solution-and-options-part1.md#simulator-options) control some of the general features of the case information displays.

Enterable Field Color

Fields whose values can be directly entered on the case information displays are colored navy blue by default. Click on the color field to change the color of enterable fields, or click the **Change** button.

Toggleable Field Color

Fields whose values can be toggled (changed) by left-clicking on them are colored green by default. Click on the color field to change the color of toggleable fields, or click the **Change** button.

At or Exceeding Limit Field Color

Fields whose values are at or exceeding a limit, are colored red by default. Click on the color field to change the color of such fields, or click the **Change** button.

Normal Field

Fields that cannot be modified directly from the case information display are colored black by default. Click on the color field to change the color of such fields, or click the **Change** button.

Special External Field

Fields that can be modified through an auxiliary file or by pasting data into a sheet from a spreadsheet, but cannot be changed in a case information display, are colored purple by default. Click on the color field to change the color of such fields, or click the **Change** button.

Field not presently used

Fields whose values are ignored because of various option or other field settings are colored gray by default. Click on the color field to change the color of such fields, or click the **Change** button.

Background

Background of cells is colored white by default. Click on the color field to change the color of the background, or click the **Change** button.

Use Alternating Background Color and the Color Added in Version 23, build on June 1, 2023

Add this for a slightly different background color to apply to alternating rows in the tables. Click on the color field to change the color of the background, or click the **Change** button.

Heading Background

Background of column and row headings is colored light gray by default. Click on the color field to change the color of the heading background, or click the **Change** button.

Data Fill Background Color

Background of selected cells when propagating values is colored yellow by default. Click on the color field to change the color of the heading background, or click the **Change** button.

Set Case Info Factory Default Colors

Clicking the **Dark Colors** button will reset the field and background colors to the defaults mentioned above, which comprise dark colors for fields, and light colors for backgrounds. Clicking the **Light Colors** button will set field and background colors to a specified set of light colors for fields and dark colors for backgrounds.

Highlight Objects with Selected? = YES

Check this option to automatically highlight all case information rows that represent a model object that has its *Selected* field set to YES. The row will then be highlighted using the color specified on this dialog. This option will apply to all case information displays representing all types of objects.

Use Concise Variable Names and Headers

Added in Version 19

Variable names within Simulator have been overhauled starting Version 19. This is described in more detail in the [PowerWorld Object Variables help topic](09-auxiliary-files-and-script-commands.md#powerworld-object-field-variable-names). This option must be chosen to use the more concise variable names when looking at field variable names in the user interface or when writing out to an Auxiliary File. If this option is not chosen then the legacy variable names will be used.

In addition, a new [Concise Auxiliary File (AUX) header](03-cases-files-and-formats.md#auxiliary-file-format-aux) is available when writing out AUX files. This option must be chosen to write out Auxiliary Files using the new concise format.

Disable Auto Refresh

This option prevents Simulator from automatically updating the contents of open case information displays with each solution. If this option is not checked, the data in all open case information displays will be updated automatically to reflect the system state calculated from each power flow solution.

Set Factory Defaults

Clicking on this button will reset the options to their defaults.

View/Modify Default Font

Clicking this button brings up a font dialog from which you can choose the font in which case information displays should show their data. Selecting a new font, font size, style, or color and pressing **OK** will change the default font, so that all case information displays will then employ a font having the selected properties. An individual case information display can override this setting by choosing a custom row height or font on the [Display Options tab of the Display/Column Options dialog](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays).

Default Row Height

This option sets the default height of the rows in the case information displays. This field may need to be changed depending on the screen size and font size of the computer. By default, the height is set to 13. An individual case information display can override this setting by choosing a custom row height or font on the [Display Options tab of the Display/Column Options dialog](04-model-explorer-and-case-information-part1.md#configuring-the-case-information-displays).

Show Grid Lines

Grid lines are shown by default in case information displays. Unchecking this box will remove the grid lines from the displays.

Column Headings

This option allows you to choose whether the column headings of the case information displays are the *Normal* column headings or are the *Variable Names* of the type of data stored in each column. Variable names are the strings used when writing data out to an [Auxiliary File](03-cases-files-and-formats.md#auxiliary-file-format-aux). Changing the headings to variable names can be helpful when looking at or creating auxiliary files.

When viewing the heading by *Variable Names* there are special characters that are included in parentheses after the variable names. More than one special character can be included with each heading.

  - **1**,**2**, or **3** - this is a primary key field
  - **A**, **B**, or **C** - this is a secondary key field
  - **\*** - this is a required field
  - **\<** - this is a field that is included in the [Difference Case](08-view-case-data-tools.md#difference-case) tool comparison

Use Word Wrap

Check this box to wrap the heading column text, breaking it in several rows to fit the current column width. If unchecked, the column heading text will be displayed in only one row.

Show Header Hints

This option allows the hints for the current field to be displayed when moving the cursor over the column heading.

Copy/Send Options

Typically when you copy information to the clipboard or send data to Excel from a case information display, the first two rows of the copied information contain the type of object the data represents (object name) and the column headings for each column of data. These rows are necessary if you intend to [paste the information back into Simulator](04-model-explorer-and-case-information-part3.md#copying-simulator-data-to-and-from-other-applications), but they are unnecessary if you are only exporting data to another program with no intention of pasting the information back into Simulator. Thus, these two options allow you to choose which of the two rows, if either, you wish to have copied along with the actual data from a case information display when pasting in another application.

Key Fields to Use in Subdata Sections

This option allows the user to decide whether to use primary or secondary key fields or labels for the objects saved in the subdata section of an auxiliary file. In addition to being applied to the subdata section of auxiliary files, this option is also used in some special cases to dictate how elements are identified when writing out [Auxiliary Files](03-cases-files-and-formats.md#auxiliary-file-format-aux) or displaying objects within certain fields in a case information display. The [Labels](07-object-properties-run-mode-and-general-part2.md#labels) topic contains additional information about this.

Show Column Metrics as Hints

Check this box to show the column metrics as hints that pop up over a selection instead of having to open the [grid metrics dialog](04-model-explorer-and-case-information-part3.md#grid-metrics-dialog). If this option is checked and more than two cells are selected in a case information display, the metrics hint will pop up.

Use Absolute Values

Check this box to use the absolute values of field values for the metrics computation.

Treatment of blank cells

If the option *Treat as zero* is checked, any blank cells will be considered as zero when computing the metrics. Instead, if the option *Ignore for calculation* is checked, any blank cell will be taken out of the metrics calculation.

---

<a id="message-log-options"></a>

## Message Log Options

*Source: [`Content/MainDocumentation_HTML/Message_Log_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Message_Log_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

![MessageLogOptions](images/MessageLogOptions.gif)

Show Log

If checked, the message log is displayed. The message log shows detailed results of each Power Flow Solution. Usually this log is NOT shown. However, if you are running into problems with a simulation case, it can prove useful for debugging the case.

Show Time Stamps

Checking this option will display the date and time at which each message is posted in the message log.

In log Messages, Identify buses by

This option allows the user to specify how to identify the buses in log messages. The options are by numbers, by names, or by both numbers and names.

Include Nominal Voltages in Log

If checked, this option will make the buses to be displayed with their nominal voltages after their name.

Suppress the following messages in the log

Checking the check-boxes in this option will remove the corresponding message writing to the log, thus speeding up the computation process. The boxes to the right of the messages indicate the color with which the messages will be displayed in the log.

An example of how these colors are reflected in the message log is shown in the following image.

![PowerFlow Message Log Example](images/PowerFlow_Message_Log_Example.gif)

---

<a id="distributed-computing-add-ons"></a>

## Distributed Computing Add-Ons

*Source: [`Content/MainDocumentation_HTML/Distributed_Computing_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Distributed_Computing_Options.htm)*

**The Distributed tools are available as an add-on to the base Simulator package. **[Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information)** **for more details. The use of Distributed tools in Simulator requires the use of the SimAuto add-on as well.****

Some tools in Simulator have been enabled to use Simulator's Distributed Computing capabilities. In order to use Distributed Computing a list of computers is provided to Simulator which are available for distributed computing. This list is managed in one place in Simulator and applies to all tools in Simulator that can be enabled for distributed computing. Tools which can use Distributed Computing are as follows:

  - [Contingency Analysis](22-contingency-analysis-options.md#distributed-computing) : can distribute groups of contingencies
  - [Available Transfer Capability](32-available-transfer-capability.md#distributed-computing) : can distribute multiple-scenario and multiple direction ATC calculations
  - [Transient Stability](37-transient-stability-analysis-dialog-part1.md#distributed-computing) : can distribute transient contingencies
  - [QV Curves](29-pv-and-qv-curves.md#distributed-computing) : can distribute groups of buses and contingencies for QV analysis Added in version 24

Along with this list of computers, appropriate login authentication must be provided for each remote computer to ensure that the Windows operating system security allows the remote processes to be started and results to be passed back to Simulator. These passwords are then encrypted and decrypted by Simulator using a Master Password as described below. For more technical details about password security please contact PowerWorld.

Buttons commonly available for distributed computing are described as follows.

> Insert Computer
> 
> Inserts a new computer into the list of computers available for distributed computing.
> 
> Verify Computers Available
> 
> Checks each computer in the list of distributed computing machines for availability, and sets the Enabled, Available, and Cores fields accordingly.
> 
> Enter Master Password
> 
> Allows the user to enter the password used to decrypt all of the distributed machine login credentials. If the master password has not been defined, then the user is asked to provide a new master password.
> 
> Forget Master Password
> 
> Tells Simulator to forget the already entered master password. The user will not be able to perform a distributed analysis until the master password has been re-entered.
> 
> Change Master Password
> 
> Tells Simulator to re-encrypt all credentials using a new master password.
> 
> Reset all authentication
> 
> Clears all authentication information including the master password and all distributed machine login credentials.

To add login authentication information for a particular Distributed Computer, go to the **Records Menu** or the right-click local menu under **Distributed Computer records** and choose the following options.

> Add or change authentication info...
> 
> Adds or changes login credentials for all currently selected distributed machines. If a master password has not been defined, the user will be prompted to provide a new master password. If the master password has been defined but not entered, the user will be prompted to enter the current master password.
> 
> Note: Adding authentication for the local machine is not needed and should not be provided. If authentication information is added for the local machine it will result in an "Access is denied" error from Windows.
> 
> Remove authentication info
> 
> Removes login credentials for all currently selected distributed machines.

The columns with the Distributed Computer List are as follows

> Computer Name
> 
> Name of the computer on the local network. If you wish to use cores on the local machine, you can enter the name "localhost".
> 
> Auth Info Stored?
> 
> Column will say YES if login authentication information is stored with this computer.
> 
> Processes
> 
> Specifies the number of processes which will be started on this when performing distributed computer. For computers with multiple cores and/or multiple processors it may be advantageous to execute multiple processes.
> 
> Enabled
> 
> Set this to NO to disable the use of this computer when using distributed computing. Set to YES to use the computer.
> 
> Available
> 
> When the **Verify Computers Available** button is clicked, Simulator will determine this field automatically. It shows whether the remote computer is available for use in distributed computing.
> 
> Cores
> 
> Shows the number cores available on the computer.
> 
> \# Errors
> 
> Shows the number of errors encountered when trying to use the computer for distributed computing.
> 
> Max \# Errors
> 
> Enter a number for the maximum number of errors which can be encountered with a computer before the distributed computing will stop attempting to use the computer for computation. By default this value is set to 1 because it is assumed that a failure will
> 
> Domain, Password, Username
> 
> Shows the domain, username, and password of the login information in an encrypted form. These values can be saved and loaded from an AUX file in encrypted form but you must not attempt to edit them directly. They must be encrypted and decrypted through the Master Password at all times, thus to make changes to these you must use the **Add or change authentication info** and **Remove authentication** info local menu buttons only. If authentication fails then Simulator will not use the computer for distributed computing.

---

<a id="solving-the-power-flow"></a>

## Solving the Power Flow

*Source: [`Content/MainDocumentation_HTML/Solving_the_Power_Flow.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Solving_the_Power_Flow.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

At its heart, Simulator is a Power Flow Solution engine. Power flow is a traditional power engineering calculation that is performed to determine the flows on all lines and the voltages at all buses in the system given the power injections at all buses and the voltage magnitudes at some of them.

The power flow problem entails solving a system of nonlinear equations. Solving a nonlinear system requires the use of an iterative algorithm to hone in on the correct solution. Many nonlinear system solvers have been developed, and PowerWorld provides access to the full Newton-Raphson method with an optimal multiplier and the fast decoupled method.

Usually, the power flow computation converges quickly. However, it is certainly possible to model conditions for which no Power Flow Solution exists, or for which the algorithm cannot converge to the solution within the [maximum number of iterations specified](10-power-flow-solution-and-options-part1.md#simulator-options). For such situations, the [message log](01-getting-started.md#message-log) will provide a message indicating that the computation failed to converge. Furthermore, unless [blackouts are disabled](#environment-options), the screen is grayed, and a message indicating a blackout has occurred is shown.

In order to calculate the power flow solution, simply press the Solve Power Flow button on the main Program Toolbar. Clicking Solve Power Flow actually performs several pre-processing activities and then runs three nested loops which solve the power flow: MW Control (Outer) Loop, Controller (Middle) Loop, and Power Flow (Inner) Loop.

Pre-Processing Activities

The Power Flow Loop is where the traditional power flow matrix equations are solved.

Angle Smoothing

When a transmission branch status is changed from OPEN to CLOSED across a branch that has a large voltage angle difference, this can introduce a very large initial power flow mismatch and cause the inner power flow loop to diverge. Angle Smoothing will alleviate this large angle difference by smoothing the angles in the system around the newly closed in branch resulting in much better power flow convergence. Angle smoothing will also work if a series of branches are all closed in together. A message will be written to the [message log](01-getting-started.md#message-log) to indicate this is occurring. Angle smoothing should be enabled by default, but an option exists with the [Advanced Power Flow Solution Options](#power-flow-solution-advanced-options) to disable this. Angle smoothing works best for individual branches or a series of branches that have been closed that are not electrically near other branches that have been closed. If modifying a case and adding in new transmission lines that are electrically near each other, it might be better for solution convergence to disable angle smoothing.

Generator Remote Regulation Viability

Generators are allowed to remotely regulate any bus in the system. However, if there is no transmission path between the generator terminal bus and the remotely regulated bus which does not pass over any other PV buses, then the generator will not be able to regulate this bus remotely. Additionally this will introduce a numerical condition that makes the inner power flow loop not converge. This pre-processing activity ensures catches this condition and prevents these generators from performing voltage regulation. A message will be written to the [message log](01-getting-started.md#message-log) to indicate this is occurring.

Estimate MW Change Needed

When large changes in generation or load are made to the system, then ultimately this entire mismatch will show up at the island slack buses during the first inner power flow loop. This can cause the inner power flow loop to not converge. When automatic generation control is enabled for this system, then this pre-processing activity will automatically try to initialize generator outputs throughout the system to prevent the entire mismatch from appearing at the slack bus. Eventually the MW Control (Outer) Loop will be executed to bring generators to their proper outputs as specified by the Area or Island AGC choices.

Low Impedances Lines Voltage Profile

When pre-processing the voltage profile, Simulator will look at groupings of buses connected by very low impedances lines. If a bus in a grouping of energized buses has a zero voltage while other buses in the group do not, the zero voltage will be changed to the first non-zero voltage found in the grouping. This provides a much more reliable solution.

Estimate Voltages at Buses that Have Just Been Connected

As part of the pre-processing of voltages, voltages and angles at buses that have just had their status changed from *Disconnected* to *Connected* will be estimated assuming that the voltages and angles at buses that have not just changed status remain fixed. This will better facilitate power flow convergence. A message will be written to the [message log](01-getting-started.md#message-log) to indicate this is occurring.

Three Nested Loops

Power Flow (Inner) Loop : Red Loop

The Power Flow Loop is where the traditional power flow matrix equations are solved. There are several [Common](#power-flow-solution-common-options) and [Advanced](#power-flow-solution-advanced-options) Solution options which affect this loop. In the [message log](01-getting-started.md#message-log), a **RED** outline will be drawn around the inner power flow loop. Additionally, a **PURPLE** outline will be drawn around any generator Mvar limit checking which occurs inside this loop. For details on the equations used to solve the power flow loop see the topic on [Equation Basics](10-power-flow-solution-and-options-part1.md#power-flow-bus-equation-basics).

Controller (Middle) Loop : Green Loop

Once the Power Flow Loop is solved, control devices check if their control requirements are being met. Control devices are checked in the following order or precedence.

> 1.  Generator Mvar Limit Checking
> 2.  DC Line Solution
> 3.  Switched Shunt Controls (each switched shunt or switched shunt control group is examined individually)
> 4.  Load-Tap-Changing (LTC) transformers, Phase Shifting transformers, and D-FACTS devices (can be coordinated switching or examined individually)

If any control devices requiring changes, then these changes are made and the power flow loop is re-solved. This continues until no more control loop changes are made. There are several [Common](#power-flow-solution-common-options) and [Advanced](#power-flow-solution-advanced-options) Solution options which affect this loop. In the [message log](01-getting-started.md#message-log), a **GREEN** outline will be drawn around this loop.

MW Control (Outer) Loop : Blue Loop

After the Control Loop has completed, the MW Control loop is entered and generation (and possibly load) is moved to meet the MW control options set in the case. Normally, MW control is done by [area control](10-power-flow-solution-and-options-part3.md#area-control) with each area varying generation to meet its own load, losses and interchange. However, you may also use [island-based control](#power-flow-solution-island-based-agc) to dispatch MWs by island. If any MW control is needed, then the Control Loop and Power Flow Loop interaction must be repeated and so on. In the [message log](01-getting-started.md#message-log), a **BLUE** outline will be drawn around this loop.

A depiction of these loops and how you will see them represented in the message log is shown in the following figure.

![PowerFlow Message Log Example](images/PowerFlow_Message_Log_Example.gif)

>
