---
title: "Power Flow Solution and Simulator Options (Part 1 of 3)"
part: "Solving"
chapter_file: "10-power-flow-solution-and-options-part1.md"
topics: 10
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Power Flow Solution and Simulator Options (Part 1 of 3)

Power flow solution theory, simulator options, and solution and control settings.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (10)**

- [Power Flow Solution Theory](#power-flow-solution-theory)
- [Power Flow: Bus Equation Basics](#power-flow-bus-equation-basics)
- [Power Flow: Remote Voltage Regulation](#power-flow-remote-voltage-regulation)
- [Power Flow: Mvar Sharing between Generators](#power-flow-mvar-sharing-between-generators)
- [Power Flow: Line Drop Compensation](#power-flow-line-drop-compensation)
- [Power Flow: Voltage Setpoint Tolerance](#power-flow-voltage-setpoint-tolerance)
- [Power Flow: Voltage Droop Control with Deadband](#power-flow-voltage-droop-control-with-deadband)
- [Power Flow: Bus Category Possibilities](#power-flow-bus-category-possibilities)
- [Simulator Options](#simulator-options)
- [Power Flow Solution Options](#power-flow-solution-options)

---

<a id="power-flow-solution-theory"></a>

## Power Flow Solution Theory

*Source: [`Content/MainDocumentation_HTML/PowerFlow Solution Theory.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Solution Theory.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This help concentrates only on describing the basic set of equations that define the power flow solution. When you click Solve Power Flow in PowerWorld Simulator there is a lot more going on that solving these basic equations. [Solve Power Flow in PowerWorld](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) encompasses numerous voltage control algorithms such as tap changing transformers moving, phase shifters, switched shunts, generator MW control and so on. This is described in detail in the [Solving the Power Flow](10-power-flow-solution-and-options-part2.md#solving-the-power-flow) help topic which discusses the **Blue Loop** (MW control), **Green Loop** (Voltage control) and **Red Loop** (power flow inner loop). The topic you are reading now only relates to the **Red Loop** which solves the Inner Power Flow Equations.

The power flow equations can be very simple when considering only local voltage control on a generator, but variations on this theme make the topic more complex. The following topics walk through the basics and then successively add the variations that describe the complete voltage control features for generation (and switched shunt SVCs).

  - [Bus Equation Basics](#power-flow-bus-equation-basics)
  - [Remote Voltage Regulation](#power-flow-remote-voltage-regulation)
  - [Power Flow: Mvar Sharing between Generators](#power-flow-mvar-sharing-between-generators)
  - [Line Drop Compensation](#power-flow-line-drop-compensation)
  - [Voltage Setpoint Tolerance (added in Simulator Version 21)](#power-flow-voltage-setpoint-tolerance)
  - [Voltage Droop Control with Deadband (added in Simulator Version 21)](#power-flow-voltage-droop-control-with-deadband)
  - [Power Flow: Bus Category Possibilities](#power-flow-bus-category-possibilities)

---

<a id="power-flow-bus-equation-basics"></a>

## Power Flow: Bus Equation Basics

*Source: [`Content/MainDocumentation_HTML/PowerFlow Equation Basics.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Equation Basics.htm)*

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory)

Each bus in the power system model has 4 quantities associated with it that may not be know. These are

1.  V (Bus Voltage Magnitude)
2.  d Bus Voltage Angle
3.  P (Real Power Injection)
4.  Q (Reactive Power Injection)

In addition each bus may have various equations that can be used to describe it.

1.  Summation of Real Power Flows into the bus equal zero
2.  Summation of Reactive Power Flow into the bus equals zero
3.  Voltage equal to Voltage Setpoint
4.  Other (voltage tolerance has a special equation as does voltage droop control with deadband)

Typically at each bus there are then 2 unknown variables out of these 4 variables and 2 equations that are used at each bus. This makes an equal number of unknown variables as equations so the "inner power flow solution" is simply the calculation of the unknown variables from the set of equations. There are some exceptions to each bus having 2 equations that come up with remote regulation and voltage droop control, but we'll leave that for later (might have a bus with 1 equations and another with 3 equations).

PowerWorld Simulator automatically figures out which 2 equations to use and which unknown variables to solve for based on the user input parameters (mostly generator parameters). The buses are categorized into a Type or "BusCat" which is shown by default on the [Bus Mismatch case information display](05-case-information-displays-by-object-part1.md#bus-mismatches-display). BusCat is a string indication as to which two equations were used in the power flow solution. [BusCat has a lot of potential options described in another topic](#power-flow-bus-category-possibilities), but the most common are the following three.

  - **PQ**: buses that have no voltage control devices such as a generator at them and are also not remotely controlled by a generator will be called a PQ bus. We call them a **PQ** bus because we use the equations for summation of real power (P) and reactive power (Q) at these buses and the unknown variables are then voltage angle (V) and voltage angle (d).
  - **PV**: a bus that has a generator at it which is regulating the terminal voltage to a voltage setpoint will be called a PV bus. Again this is because the equations are the summation of real power (P) and an equation for Voltage = Setpoint (V). The unknown variables are then voltage angle (d) and the extra Q injection at the bus. The extra Q injection at the bus is then used to assign the reactive power output to the generators at the bus.
  - **Slack**: one bus in each electrical island is chosen as the island slack bus. This bus has a fixed voltage magnitude and voltage angle. Using our notation we might call it a **dV** bus. The unknown variables at this bus are then the real power (P) and reactive power (Q) which are then used to assign the real and reactive power at the slack generator.

PowerWorld Simulator will also frequently add modifiers to the Bus Type string to indicate why it is behaving in a particular way. Some examples are as follows

  - **PV (SVC)**: a bus that has a switched shunt with (ShuntMode = SVC) and (SVCType = SVSMO3 or SVSMO1) configured to regulate the voltage at the terminal bus. The voltage equation will be used just as for a generator.
  - **PQ (Gens at Var Limit)**: a bus that has a generator at it regulating the terminal voltage, however presently the generator is stuck at a maximum or minimum Mvar limit and is thus no longer able to regulate the voltage. Because we are stuck at a Mvar limit, the equations used is the reactive power (Q) equation. This is an indication that the bus type would have been **PV**, but is not because of the generators at Mvar limits
  - **PQ (SVC at Limit)**: similar to PQ (Gens at Limit), but a switched shunt that is an SVA
  - **PQ (Continuous Shunts at Var Limit):**: similar to PQ (Gens at Limit), but it's a continous switched shunt at limits.

This topic then gets more complex however as you add the following concepts.

  - [Remote Voltage Regulation](#power-flow-remote-voltage-regulation)
  - [Power Flow: Mvar Sharing between Generators](#power-flow-mvar-sharing-between-generators)
  - [Line Drop Compensation](#power-flow-line-drop-compensation)
  - [Voltage Setpoint Tolerance](#power-flow-voltage-setpoint-tolerance)
  - [Voltage Droop Control with Deadband](#power-flow-voltage-droop-control-with-deadband)
  - [Power Flow: Bus Category Possibilities](#power-flow-bus-category-possibilities)

---

<a id="power-flow-remote-voltage-regulation"></a>

## Power Flow: Remote Voltage Regulation

*Source: [`Content/MainDocumentation_HTML/PowerFlow Remote Regulation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Remote Regulation.htm)*

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory)

More complicated situations occur when generators are configured to regulate a bus that is not the terminal bus and when groups of generators coordinate their Mvar outputs to regulate a single remote bus together. This is depicted in the next image where there are three generators at buses A, B, and C which are working together to regulate the voltage at the regulated bus R.

![PowerFlow Remote Regulation](images/PowerFlow_Remote_Regulation.png)

The proportion of total Mvars output by each of these generators is impacted by the user-designed option Sharing of generator Vars across groups of buses during remote regulation which is available on the [Advanced Options tab of the Power Flow Solution Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) on the Simulator Options Dialog. Examples that use the regulation factors will make use of user-enterable remote regulation factor (RegFactor) that is defined for each generator. The RegFactor values are then normalized to determine what relative amount of Mvar output from each generator is expected. Thus if generator A RegFactor was 10, B was 6, and C was 4, then you would expect generator A to have 2.5 times as much Mvar output as generator C and generator B would have 1.5 times as much Mvar output as generator C. [A more complete description of how Mvars are shared between generators is available in another topic](#power-flow-mvar-sharing-between-generators).

In order to enforce this kind of control the equations solved for are modified. Out of the buses that are participating in remote generator voltage regulation, one bus is chosen as the <span class="underline">Primary</span> Bus. For our example, let's assume that Bus A is chosen as the Primary Bus. All buses will enforce the real power flow summation to zero at the bus, but the reactive or voltage equations are then implemented as follows

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td><p>Which Bus</p></td>
<td><p>Voltage or Reactive Equation Description</p></td>
<td><p>BusCat String</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Bus A</p></td>
<td><p>As the primary bus it will enforce the bus voltage equation <em>at the regulated Bus R</em></p></td>
<td><p><strong>PV (Remote Reg Primary)</strong></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Bus B</p>
<p>and</p>
<p>Bus C</p></td>
<td><p>As secondary buses they will enforce <a href="#power-flow-mvar-sharing-between-generators">an equation then ensures that the total Mvar output of generators at the respective bus is equal to the appropriate proportion of the summation of the Mvar outputs at Bus A, B and C (click link for more information on Mvar Sharing)</a></p></td>
<td><p><strong>PQ (Remote Reg Secondary)</strong></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Bus R</p></td>
<td><p>The regulated bus will just enforce the reactive power flow summation at its bus.</p></td>
<td><p><strong>PQ (Remotely Regulated)</strong></p></td>
</tr>
</tbody>
</table>

Notice that the regulated bus is denoted as "**PQ**" even though the <span class="underline">voltage</span> at the regulated bus is being controlled. The equation that is enforcing the regulated bus voltage is instead coming from the <span class="underline">primary</span> Bus A. In this set equations the primary bus A has only 1 equation (P) while the regulated bus R has 3 equations (P, Q, and V). The unknown variables at all the buses here remain the variables V and d. Thus there are still have an equal number equations and unknown variables to solve for.

There are also 2 other possible BusCat strings related to remote regulation which are as follows

  - **PV (Local/Remote Reg Primary)**: This is seen when there are a group of generators at different buses that all regulate the voltage at a regulated bus and that regulated bus also has generation participating in the regulation. Thus this bus is regulating its own voltage, but doing so in coordination with generators at other remote buses.
  - **PQ (Remotely Regulated at Var Limit)**: This is seen for a remotely regulated bus if all the generators which are regulating it are at MVar limits.

---

<a id="power-flow-mvar-sharing-between-generators"></a>

## Power Flow: Mvar Sharing between Generators

*Source: [`Content/MainDocumentation_HTML/PowerFlow Mvar Sharing between Generators.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Mvar Sharing between Generators.htm)*

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory)

On the [Simulator Options](#simulator-options) dialog under the [Power Flow Solution, Advanced Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options) tab there is an option called **Sharing of generator Vars across groups of buses during remote regulation**. When several buses have generators that control the voltage at single bus, this option determines the method used to determine each bus' share of the Mvar support. There are three options as follows.

  - **OPTION\#1**: Allocate across buses using the user-specified remote regulation percentages. This option most closely matches the sharing seen in RAW files. The allocation of Mvars to a bus will be proportional to the <span class="underline">average value</span> of the RegFactor for all generators at the bus.
  - **OPTION \#2**: Allocate so all generators are at same relative point in their \[min .. max\] var range. This option most closely matches the sharing seen in a few EMS solutions PowerWorld has seen. The RegFactor values are not used with this option, but the MvarMax and MvarMin values will impact the allocation.
  - **OPTION \#3**: Allocate across buses using the SUM OF user-specified remote regulation percentages. This option most closely matches the sharing seen in EPC files. The allocation of Mvars to a bus will be proportional to the <span class="underline">summation</span> of the RegFactor for all generators at the bus.

In an Auxiliary file, this option is part of the object **Sim\_Solution\_Options** and can be changed by change the field named *MvarSharingAllocation* which can set to either RegPerc, MinMaxRange, or SumRegPerc.

To demonstrate what these options mean consider the following system where there are 3 buses (A, B, and C) that have generators that are regulating a remote bus.

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td><p>Bus A has 2 generators (a1 and a2), Bus B has one generator (b1), and Bus C has 2 generators (c1 and c2). The RegFactors and generator Mvar limits are as shown in the following table.</p>
<p> </p>
<table>
<tbody>
<tr class="odd">
<td style="text-align: right;"><p>Generator</p></td>
<td style="text-align: right;"><p>RegFactor</p></td>
<td style="text-align: right;"><p>MvarMin</p></td>
<td style="text-align: right;"><p>MvarMax</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>a1</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-60.0</p></td>
<td style="text-align: right;"><p>+40.0</p></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>a2</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+30.0</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>b1</p></td>
<td style="text-align: right;"><p>6.0</p></td>
<td style="text-align: right;"><p>-100.0</p></td>
<td style="text-align: right;"><p>+100.0</p></td>
</tr>
<tr class="odd">
<td style="text-align: right;"><p>c1</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+50.0</p></td>
</tr>
<tr class="even">
<td style="text-align: right;"><p>c2</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-40.0</p></td>
<td style="text-align: right;"><p>+80.0</p></td>
</tr>
</tbody>
</table></td>
<td><p><img src="images/PowerFlow_Remote_Regulation_Mult.png" alt="PowerFlow Remote Regulation Mult" /></p></td>
</tr>
</tbody>
</table>

As an example assume that the summation of the Mvar from all 5 generators in a solution ends up being +180 Mvar. The relative Mvar outputs of the generators will be impacted by this option and will be described as follows.

  - **OPTION \#1** The first option means that the RegFactor is interpreted for each bus, and thus <span class="underline">buses</span> are assigned Mvar in proportion to the factors 2, 6, and 4. These factors are then normalized so that Bus A generators will provide 2/12 of the Mvars, Bus B will provide 6/12, and Bus C will provide 4/12. With a total of 180 Mvar that means Bus A provides 30 Mvar, Bus B provides 90 Mvar, and Bus C provides 60 Mvar. This then means that a1 and a2 provide 15 Mvar each, b1 provides 90 Mvar, and c1 and c2 provide 30 Mvar each.
      - ![PowerFlow Remote Regulation Option1Eq](images/PowerFlow_Remote_Regulation_Option1Eq.png)
      - Thus for generator c2 its output will be ![PowerFlow Remote Regulation Option1EqEx](images/PowerFlow_Remote_Regulation_Option1EqEx.png), but then this is split by using the RegFactor at bus C so that c1 gets half of this which is 30 Mvar
  - **OPTION \#2** The second option means that each generator will end up at the same relative point within its Min/Max Mvar range. The summation of minimum Mvars is -300 and the summation of maximum Mvar is +300. This gives a total range of 600 Mvar. The desired total of 180 Mvar, which is 480 Mvar above the minimum Mvar total. That means we want to be 480/600 and thus 80% of the way from the minimum to maximum value for each generator. Written in equation for each generator's output will then be set equal to  
      - ![PowerFlow Remote Regulation Option2Eq](images/PowerFlow_Remote_Regulation_Option2Eq.png)
      - Tthus for generator c2 its output will be ![PowerFlow Remote Regulation Option2EqEx](images/PowerFlow_Remote_Regulation_Option2EqEx.png)
  - **OPTION \#3** The third option means the RegFactor is interpreted for each bus as the summation of values assigned for each generator. This is the same as each individual generator providing Mvar in proportion to its own RegFactor. This means that generators a1 and a2 will each provide 2/18 of the Mvars, generator b1 will provide 6/18, and generators c1 and c2 will each provide 4/18. With a total of 180 Mvar this then means that a1 and a2 provide 20 Mvar each, b1 provides 60 Mvar, and c1 and c2 provide 40 Mvar each.
      - ![PowerFlow Remote Regulation Option3Eq](images/PowerFlow_Remote_Regulation_Option3Eq.png)
      - Thus for generator c2 its output will be ![PowerFlow Remote Regulation Option3EqEx](images/PowerFlow_Remote_Regulation_Option3EqEx.png), but then this is split by using the RegFactor at bus C so that c1 gets half of this which is 40 Mvar

**Generator Outputs if the summation of outputs is 180 Mvar**

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td style="text-align: right;"><p>Generator</p></td>
<td style="text-align: right;"><p>RegFactor</p></td>
<td style="text-align: right;"><p>MvarMin</p></td>
<td style="text-align: right;"><p>MvarMax</p></td>
<td><p>Option #1</p>
<p>Mvar</p></td>
<td><p>Option #2</p>
<p>Mvar</p></td>
<td><p>Option #3</p>
<p>Mvar</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>a1</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-60.0</p></td>
<td style="text-align: right;"><p>+40.0</p></td>
<td><p>+15</p></td>
<td><p>+20</p></td>
<td><p>+20</p></td>
</tr>
<tr class="odd">
<td> </td>
<td style="text-align: right;"><p>a2</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+30.0</p></td>
<td><p>+15</p></td>
<td><p>+14</p></td>
<td><p>+20</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>b1</p></td>
<td style="text-align: right;"><p>6.0</p></td>
<td style="text-align: right;"><p>-100.0</p></td>
<td style="text-align: right;"><p>+100.0</p></td>
<td><p>+90</p></td>
<td><p>+60</p></td>
<td><p>+60</p></td>
</tr>
<tr class="odd">
<td> </td>
<td style="text-align: right;"><p>c1</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+50.0</p></td>
<td><p>+30</p></td>
<td><p>+30</p></td>
<td><p>+40</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>c2</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-40.0</p></td>
<td style="text-align: right;"><p>+80.0</p></td>
<td><p>+30</p></td>
<td><p>+56</p></td>
<td><p>+40</p></td>
</tr>
</tbody>
</table>

PowerWorld Corporation has found that various software tools choose to do this Mvar allocation across generators in different ways. The three methods described here are the ones we have seen. Our recommendation would be to use the second option to keep generators within the same point of the MvarMin to MvarMax range as this has the advantage of not requiring the extra input parameter RegFactor and also means that all generators participating in remote regulation together will hit their limits at the same point. See discussion below which shows that hitting and backing off of generator limits using the other options can be quite complex.

One clarification when allocating with this recommended option however: it is possible for a solution to have a mixture of positive and negative Mvar outputs even when regulating together. As an example consider what happens when the summation of generator Mvar outputs is either 36.0 or 0.0 Mvar. The various options would yield those shown below where generators at Bus A are operating at a negative Mvar, while generators c2 is operating at a higher positive value. This is occurring because generators a1 and a2 have a larger negative Mvar range than positive, while generator c2 has a larger positive range than negative.

**Generator Outputs if the summation of outputs is 36.0 or 0.0 Mvar**

Mvar Outputs for total of 36.0

Mvar Outputs for total of 0.0

Generator

RegFactor

MvarMin

MvarMax

Option \#1

Mvar

Option \#2

Mvar

Option \#3

Mvar

Option \#1

Mvar

Option \#2

Mvar

Option \#3

Mvar

a1

2.0

\-60.0

\+40.0

\+3

\-4.0

\+4

0

\-10

0

a2

2.0

\-50.0

\+30.0

\+3

\-5.2

\+4

0

\-10

0

b1

6.0

\-100.0

\+100.0

\+18

\+12.0

\+12

0

0

0

c1

4.0

\-50.0

\+50.0

\+6

\+6.0

\+8

0

0

0

c2

4.0

\-40.0

\+80.0

\+6

\+27.2

\+8

0

\+20

0

Enforcement of Generator Mvar Limits

When using the OPTION\#2 (MinMaxRange), the hitting of minimum and maximum Mvar limits for the generators occurs simultaneously across all generators performing control together. This is the most straighforward of the options to understand.

For OPTION \#1 and OPTION \#3 however as you increase the total Mvar from all 5 generators then you will encounter solutions where within a group of generators regulating the same bus there is a mixture of generators at a limit and generators not at a Mvar limit. In PowerWorld Simulator we allocate the Mvars to <span class="underline">buses</span> using the algorithms described first. If the summation of Mvar limits of generators at <span class="underline">a bus</span> can handle the Mvar allocated to the bus then the Mvars will stay at that bus and be spread around ensuring no generator is outside its Mvar limits. This is done <span class="underline">before</span> pushing those Mvars to other buses in the remote regulation group.

As an example, consider OPTION\#1 in the previous system and what occurs if a total of 250 Mvar is spread across these generators. Initially, internally we would assign values of 20.833 Mvar to a1 and a2, 125.000 to b1, and 41.667 to c1 and c2. However, this would result in b1 exceeding its MvarMax limit of 100. Therefore we would allocate the 25 extra Mvar by renormalizing the Mvar allocation for the remaining generators at A and C and we would end up with the entries shown in the final column on the right below.

**Generator Outputs if the summation of outputs is 250 Mvar**

<table>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td style="text-align: right;"><p>Generator</p></td>
<td style="text-align: right;"><p>RegFactor</p></td>
<td style="text-align: right;"><p>MvarMin</p></td>
<td style="text-align: right;"><p>MvarMax</p></td>
<td><p>Option #1</p>
<p>Mvar</p></td>
<td><p>Move Mvars to Bus A and C</p></td>
<td><p>Option #1</p>
<p>Mvar FINAL</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>a1</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-60.0</p></td>
<td style="text-align: right;"><p>+40.0</p></td>
<td><p>+20.833</p></td>
<td><p>Add 4.167</p></td>
<td><p>+25</p></td>
</tr>
<tr class="odd">
<td> </td>
<td style="text-align: right;"><p>a2</p></td>
<td style="text-align: right;"><p>2.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+30.0</p></td>
<td><p>+20.833</p></td>
<td><p>Add 4.167</p></td>
<td><p>+25</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>b1</p></td>
<td style="text-align: right;"><p>6.0</p></td>
<td style="text-align: right;"><p>-100.0</p></td>
<td style="text-align: right;"><p>+100.0</p></td>
<td><p>+125.000</p></td>
<td><p>Set back to limit</p></td>
<td><p>+100</p></td>
</tr>
<tr class="odd">
<td> </td>
<td style="text-align: right;"><p>c1</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-50.0</p></td>
<td style="text-align: right;"><p>+50.0</p></td>
<td><p>+41.667</p></td>
<td><p>Add 8.333</p></td>
<td><p>+50</p></td>
</tr>
<tr class="even">
<td> </td>
<td style="text-align: right;"><p>c2</p></td>
<td style="text-align: right;"><p>4.0</p></td>
<td style="text-align: right;"><p>-40.0</p></td>
<td style="text-align: right;"><p>+80.0</p></td>
<td><p>+41.667</p></td>
<td><p>Add 8.333</p></td>
<td><p>+50</p></td>
</tr>
</tbody>
</table>

Take this a step further and let's go to 288 Mvar output. Initially we get the generator b1 allocated to 144 Mvar which is beyond its limit. Because there is only one generator at bus B, we must move Mvars from Bus B over to Buses A and C and we get generators at bus A at 31.333 and generators at bus C at 62.667. At this point however, generators a2 and c1 are now violating their MvarMax limits. We do not reallocate those Mvars across the entire group though because both Bus A and C have other generators at their respective buses which can take on those Mvars. Thus the extra Mvars at generator c1 are moved to c2 and the extra Mvars at a2 are moved to a1.

**Generator Outputs if the summation of outputs is 288 Mvar**

Generator

RegFactor

MvarMin

MvarMax

Option \#1

Mvar

Move Mvars to Bus A and C

Option \#1

Mvar

Shift at

Bus Only

Option \#1

Mvar FINAL

a1

2.0

\-60.0

\+40.0

\+24

Add 7.333

\+31.333

Reallocate at the Buses A and C to keep within limits

\+1.333

\+32.667

a2

2.0

\-50.0

\+30.0

\+24

Add 7.333

\+31.333

\-1.333

\+30

b1

6.0

\-100.0

\+100.0

\+144

Set back to limit

\+100

\+100

c1

4.0

\-50.0

\+50.0

\+48

Add 14.667

\+62.667

\-12.667

\+50

c2

4.0

\-40.0

\+80.0

\+48

Add 14.667

\+62.667

\+12.667

\+75.333

Finally as the most extreme example, consider the situation where 297 Mvar are needed. It proceeds along but in the second step the total allocated to Bus C becomes 131.333 which is above the summation of its MvarMax, so that then gets moved over to bus A.

**Generator Outputs if the summation of outputs is 297 Mvar**

Generator

RegFactor

MvarMin

MvarMax

Option \#1

Mvar

Move Mvars to Bus A and C

Option \#1

Mvar

Shift at Bus Only

Move C to A

Option \#1

Mvar FINAL

a1

2.0

\-60.0

\+40.0

\+24.75

Add 8.083

\+32.833

Bus C now has 131.333 MW which is above the summation of its Max Mvar. Also generator a2 at bus

\+2.833

\+1.333

\+37

a2

2.0

\-50.0

\+30.0

\+24.75

Add 8.083

\+32.833

\-2.833

\+30

b1

6.0

\-100.0

\+100.0

\+148.5

Set back to limit

\+100

\+100

c1

4.0

\-50.0

\+50.0

\+49.5

Add 16.167

\+65.667

\-15.667

\+50

c2

4.0

\-40.0

\+80.0

\+49.5

Add 16.167

\+65.667

\+15.667

\-1.333

\+80

---

<a id="power-flow-line-drop-compensation"></a>

## Power Flow: Line Drop Compensation

*Source: [`Content/MainDocumentation_HTML/PowerFlow Line Drop Compensation.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Line Drop Compensation.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory)

In power system cases, we often model the generator so that it controls a [remote bus](#power-flow-remote-voltage-regulation) located somewhere in the rest of the power system (presumably nearby of course). The remote regulation of a bus voltage however may represent a human controlling a bus voltage and not an automatic control system. Imagine the human operator at a generator being instructed to regulate the voltage at the high side of the generator step-up transformer. The operator may be given instruction to keep the voltage at the high side near a particular value. To achieve that they may only have the ability to instruct the exciter of the machine to move the voltage up or down. They may just manually do this until the voltage is close enough. This type of control may take minutes or tens of minutes to respond to an event depending on what other duties the human is responsible for. If you are studying a system response in the few minutes following a sudden event (such as in contingency analysis), it may not be appropriate to assume that the remote voltage regulation is met in the short time frame after the event.

Power system designers understand this limitation and sometimes build in special controls into the voltage regulation (part of the exciter of a generator) that ensure that some remote regulation can be done even without the human interaction and without the need for adding measurements that feed back the voltage at the high side of the transformer to the voltage regulator. Using only local measurements at the terminal of the generator for terminal voltage, power, and current, if we know the impedance between the terminal of the generator at the high side of the transformer we can using complex algebra to get an estimate of the remote voltage using only the local measurements. Generator often regulate a particular percentage of the way through the step-up transformer for instance. This concept is called Line Drop Compensation and is depicted in the following image.

![PowerFlow LineDrop](images/PowerFlow_LineDrop.png)

When using line drop compensation, a special equation is used to model the reactive power at the generator terminal bus. The BusCat will be denoted as **PQ (Line Drop Comp)** in this situation. There are also Switch Shunt Model modes that may result in a **PQ (SVC Line Drop Comp)** as well.

In PowerWorld Simulator you can configure a generator to use Line Drop Compensation and then specify the Rcomp and Xcomp impedance through which this is done. This is described in the [help topic on line drop compensation](22-contingency-analysis-options.md#generator-line-drop-and-reactive-current-compensation).

---

<a id="power-flow-voltage-setpoint-tolerance"></a>

## Power Flow: Voltage Setpoint Tolerance

*Source: [`Content/MainDocumentation_HTML/PowerFlow Voltage Setpoint Tolerance.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Voltage Setpoint Tolerance.htm)*

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory)

The ability to use a Voltage Setpoint Tolerance was added in Simulator Version 21

Engineers in charge of operating the entire power transmission system have a voltage schedule that they ask a generator to meet. However, that voltage schedule is not a hard target. Frequently the generator operator is instructed to keep the voltage within a specified tolerance of the given voltage setpoint. Thus the instructions given to a generator at to keep the generator between the Minimum and Maximum Mvar outputs of the generator and also to keep a particular voltage within a tolerance of a setpoint. In additional, this tolerance is often in the range of 0.5 - 2.0 % of nominal voltage. That translates to a tolerance of 0.005 to 0.02 per unit voltage which in the context of a power flow solution can actually be quite large.

This is 4 input parameters: MvarMax, MvarMin, VoltSet, and VoltSetTol. As an example consider the following

  - MvarMax = +500
  - MvarMin = - 400
  - VoltSet = 1.000
  - VoltSetTol = 0.010

In traditional power flow algorithm discussions and textbooks, the topic of a PQ and PV bus are introduced as shown in the far left figure below. The assumption is that the generator Mvar output will move to any value between the MvarMin and MvarMax value to achieve the voltage setpoint specified. Thus the generator will operated either at on of the Mvar limits on the red lines or on the voltage setpoint represented by the blue line. However, as we just discussed this is not really what a generator is asked to do in real life. Instead the generator is asked to keep the system voltage within a <span class="underline">tolerance</span> of the setpoint. Thus what a generator is actually instructed to do is "Stay inside the Yellow Box" in the middle image below. PowerWorld Simulator provides you the ability to specify a voltage setpoint tolerance with each generator (VoltSetTol) and when this is done the solution will follow the blue line in the far right image instead. This means that as the voltage at the regulated bus increases then the reactive power output is going to decrease. Similarly as the voltage at the regulated voltage decreases, then the output of the generator increases. It is important that this equation have this negative dV/dQ relationship to maintain the numerical stability of the power flow solution when using this. We could really use any function between these points, but it makes most sense and is simplest to move along the line from (MvarMax, VoltSet - VoltSetTol) to the point (MvarMin, VoltSet + VoltSetTol).

|  |                                              |                                                      |                                                                          |
|  | -------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------ |
|  | ![PowerFlow PVPQ](images/PowerFlow_PVPQ.png) | ![PowerFlow PVPQ Tol](images/PowerFlow_PVPQ_Tol.png) | ![PowerFlow PVPQ Tol with Line](images/PowerFlow_PVPQ_Tol_with_Line.png) |

When generators change the VoltSetTol to a non-zero value then Powerworld automatically changes the voltage equation enforced for either a locally regulating bus or the primary bus of a group of remotely regulating buses. The [BusCat string](#power-flow-bus-category-possibilities) that you will see in these situation are.

  - **PVTol**: Same as the PV, except the voltage equation for the bus is modified such that when the bus voltage is equal to (VoltSet - VoltSetTol), the generators at the bus will operate at their maximum Mvar Limit and when the bus voltage is equal to (VoltSet + VoltSetTol), the generators at the bus will operate at their minmum Mvar Limit
  - **PVTol (Remote Reg Primary)**: Same as the PV (Remote Reg Primary), except the voltage equation for the remote bus is modified such that when the regulated bus voltage is equal to (VoltSet - VoltSetTol), the generators participating in remote regulation will operate at their maximum Mvar Limit and when the regulated bus voltage is equal to (VoltSet + VoltSetTol), the generators participating in remote regulation will operate at their minmum Mvar Limit
  - **PVTol (Local/Remote Reg Primary)**: Same concept as PVl (Local/Remote Reg Primary), except this the voltage equation includes the Voltage Setpoint Tolerance again.

---

<a id="power-flow-voltage-droop-control-with-deadband"></a>

## Power Flow: Voltage Droop Control with Deadband

*Source: [`Content/MainDocumentation_HTML/PowerFlow Voltage Droop Control with Deadband.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow Voltage Droop Control with Deadband.htm)*

This is a subtopic of the [Power Flow Solution Theory Help.](#power-flow-solution-theory) Also see related topics on showing a list of [Voltage Droop Control object](05-case-information-displays-by-object-part3.md#voltage-droop-control-display)s or the [Voltage Droop Control Dialog](10-power-flow-solution-and-options-part3.md#voltage-droop-control-with-deadband-dialog).

The ability to use a Voltage Droop Control with Deadband was added in Simulator Version 21

Some generator voltage controls are configured such that the control signals sent to the generator are related to the measurements made at a remote bus instead of the terminal buses. An example of this is renewable generation plants such as a large solar farm or wind generation farm. In a common configuration the power system model for this situation will be as follows.

1.  All the wind generator or solar inverter are aggregated and modeled as a single generator in the power flow solution (shown at bus 2 in the image below).
2.  An equivalent transformer stepping up from the low voltage a single wind turbine or solar inverter to the local farm distribution voltage will be modeled (show between bus 2 and 3 in the image below)
3.  A transformer modeling the transition between the high voltage point of interconnection (bus 1) and the local farm distribution system is modeled (between bus 1 and 4 below)
4.  An equivalent feeder representing the impedance between the two transformers.

![PowerFlow VoltageDroop Simple](images/PowerFlow_VoltageDroop_Simple.png)

In this configuration, it is common for the renewable generation plant to operate so that at the *point of interconnection* (bus 1) when the voltage is between Vdblow and Vdbhigh the plant operates at a fixed reactive power output Qdb (often 0.0). Then below the Vdblow threshold the reactive power increases linearly until it is at a specified Qmax at a voltage of Vlow, and above the Vdbhigh threshold the reactive power decreases linearly until it is at a specified Qmin at a voltage of Vhigh. This is depicted in the next image.

![PowerFlow VoltageDroop Curve](images/PowerFlow_VoltageDroop_Curve.png)

This type of voltage control is distinctly different than features such as remote voltage regulation used in other features of the software. They are different because in all other voltage control features the reactive power flows used in the algorithms are the generator Mvar outputs directly. For Voltage Droop Control, the reactive power is the flow arriving at the point of interconnection bus and thus is the reactive flow on the AC branch arriving at Bus 1 and coming from bus 4 shown as Qbranch in the figure above.

When configuring this control in the power flow, the BusCat string will be the following for buses involved.

  - **PQ (Voltage Droop Reg Bus)**: this represents the remotely regulated bus of a group of generators that are assigned to the same Voltage Droop Control . The equation at this bus is a special reactive power flow equation ensuring that the droop control curve is enforced. (Bus 1 in picture above)
  - **PQ (Voltage Droop Remote Bus)**: this represents on of the remote buses in a group of buses performing voltage droop control. It will enforce [an equation then ensures that the total Mvar output of generators at the respective bus is equal to the appropriate proportion of the summation of the Mvar outputs at all generators in the group (click link for more information on Mvar Sharing)](#power-flow-mvar-sharing-between-generators). (Bus 2 in picture above)
  - **PQ (Voltage Droop Reg Bus at Var Limit)**: This is an indication that all the generators that are remotely regulating this bus using voltage droop control are at a Mvar limit. (This could occur at Bus 1 in the picture above).
  - **PQ (Voltage Droop Remote Bus at Var Limit)**: This is an indication that a remotely regulating bus in a voltage droop control is at a Mvar limit. (This could be shown at Bus 2 in the picture above).

Determining Grouping of Generators for Voltage Droop Control

If a regulated bus is specified with a **VoltageDroopControl** object then all generators the are assigned to the **VoltageDroopControl** will use this regulated bus. (The specification of the regulated bus was added in the Version 21 patch on February 5, 2021.) When a regulated bus is specified with the **VoltageDroopControl** then there will be one equation associated with the **VoltageDroopControl** object. Alternatively, if the regulated bus for the **VoltageDroopControl** is not specified, then Simulator will *automatically* group together generators that (1) share the same **VoltageDroopControl** AND (2) regulate the same bus (or buses connected by very low impedance branches that are below the ZBR Threshold and discussed in the [advanced power flow options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options)).

Also note that there can be multiple groups of generators using different **VoltageDroopControl** objects which regulate the same regulated bus. An example of this would two separate wind farms that ultimately connect to the same regulated bus. This is depicted in the more complex example shown in the following image.

![PowerFlow VoltageDroop Medium](images/PowerFlow_VoltageDroop_Medium.png)

In the example shown in this image, there are two separate **VoltageDroopControl** objects defined (**Green** and **Blue**), however all 6 generators shown regulate the same bus (**RegBus**). Software tools can easily automatically determine the list of "arriving branches" in this case so PowerWorld automatically determines that Qla1 and Qla2 go with VoltageDroopControl A and Qlb1 goes with VoltageDroopControl B. In addition, it is valid to have some generators in the **VoltageDroopControl** be located at the RegBus itself as well, so this is automatically detected for generator MVar outpus Qga1 and Qgb1.

The only extra information needed beyond more traditional power flow input data is the specification with each generator at to which **VoltageDroopControl** it belongs to. The example depicted above may represent two phases of a wind farm project. It is possible that the green generators representing **VoltageDroopControl A** were added several years ago and are configured under the control of one plant controller (that uses voltage control with a reactive droop). Now a second phase of the wind farm has been install representing **VoltageDroopControlB** and are controlled using a separate plant controller. Both of these phases connect to the same **RegBus** and these voltage droop control algorithms will not conflict with one another exactly because the QV characteristic has a negative slope (or "droop"). This is why control system engineers use droop control.

Specification of the QV Characteristic Curve

It may be convenient to express the values of *Vlow*, *Vdblow*, *Vdbhigh*, and *Vhigh* as deviations away from the voltage setpoints of the generators, so features are given to do this.

It may also be convenient to specify that the Qdb, Qmax, and Qmin values be automatically calculated based on the summation of generator *MvarMax* and *MvarMin*, and *Qdb* is assumed to be 0.0. (If both *Qmax* and *Qmin* are the same sign, then *Qdb* is assumed to be either *Qmax* or *Qmin* depending on which value is closer to 0.0. When automatically determine the reactive thresholds for this curve, there is no need to actually enforce those limits in the QV Characteristic curve. Instead we can just rely on the individual generators to enforce their Mvar limits. As a result the QV characteristic curve would change as depicted in the following image. When Qauto is chosen then the red line extrapolates out as shown in the green dashed line.

![PowerFlow VoltageDroop Curve Qauto](images/PowerFlow_VoltageDroop_Curve_Qauto.png)

Handling hitting Generator Mvar limits for Voltage Droop Control

Each generator within the Voltage Droop Control will enforce their own individual Mvar limits. In aggregate there is thus a limitation in the Mvar arriving at the regulated bus from the generators as a result. This is handles in a manner similar to the existing generator Mvar limit checking. The Qmax and Qmin may come into play during the simulation, but it is also possible that all generators in the control will hit a Mvar limit before the solution gets to the Qmax or Qmin level. For example, the following image shows a hypothetical system where the Qmax due to individual generators is shown by the red-dashed line and the Qmin is shown by the green dashed line. In this example, the individual generator MvarMax limits end up above the Qmax characteristic while the individuals MvarMin will end up being hit before reaching the QV characteristic. This is all handled by the software.

![PowerFlow VoltageDroop Curve Individual Limits](images/PowerFlow_VoltageDroop_Curve_Individual_Limits.png)

Detection of invalid Voltage Droop Control

When implementing Voltage Droop Control algorithms in software it is possible for the user input to present impossible situations. These include situations where there topology between two VoltageDroopControls have an overlapping network. It is not possible to distinguish the Mvars arriving at the regulated bus between the overlapping VoltageDroopControls in this situation, so this is not allowed and the VoltageDroop control would be reported as invalid due to "Overlapping Voltage Droop Networks). The red highlighted line in the following image would represent such an invalid topology.

![PowerFlow VoltageDroop Invalid Topology](images/PowerFlow_VoltageDroop_Invalid_Topology.png)

The user may also specify a topology where it is not possible to reach the regulated bus from the generators in the VoltageDroopControl. This will be reported as invalid due to "Can not reach RegBus".

It is acceptable for there to be generators encompassed by the topology of the VoltageDroopControl as long as those generators are set to AVR=NO. However, if a generator is found that does not belong to a VoltageDroopControl and is configured for either normal voltage control or for LineDrop compensation then this will be considered invalid due to "Conflicting Gen on Voltage Setpoint" or "UseLineDrop= YES for generator".

Topology may seem invalid but would not be due to the treatment of the ZBR Threshold

Because of how very low impedance branches are handled in a special manner, it is possible that a topology may appear to have overlapping topologies but will not. The following figure shows a topology that is valid and would be solved with no troubles.

![PowerFlow VoltageDroop Valid Topology](images/PowerFlow_VoltageDroop_Valid_Topology.png)

Comments about Detailed Software Implementation

The QV characteristic each user-defined point creates a discontinuous derivative in the QV characteristic. (dQ/dV will suddently change). That will cause a lot of trouble for any iterative solution techniques used to solve a power flow solution. To prevent this from occurring, PowerWorld implements various numerical approximations of the QV characteristic to smooth the transition at these corner points. In addition there are hard-coded restrictions that the voltage transition points must be at least 0.001 per unit (apart) and restrictions on steep the slopes can be on the QV characteristic. You will not notice any of this is going on unless you look very closely at the power flow solution when operating right near these transition points.

Consider the example below. The dashed green line shows what the QV characteristic that is actually being enforced by PowerWorld is, while the black line shows the user-input data. IN this example the Mvar arriving at the regulated bus is about -0.8 Mvar instead of at the user-specified 0.0 Mvar. [If you want the extreme details of how this implemented see the equation PDF describing how this is implemented in software.](https://www.powerworld.com/WebHelp/Content/Other_Documents/VoltageDroopControl_Software_Implementation.pdf)

![PowerFlow VoltageDroop Curve Corner](images/PowerFlow_VoltageDroop_Curve_Corner.png)

---

<a id="power-flow-bus-category-possibilities"></a>

## Power Flow: Bus Category Possibilities

*Source: [`Content/MainDocumentation_HTML/PowerFlow BusCat.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/PowerFlow BusCat.htm)*

The various topics on the [Power Flow Theory](#power-flow-solution-theory) all end up describing different possibilities for the field that appears in the mismatch table called "Type" or "BusCat". This is a comprehensive list of the potential string that will appear in this field and what they mean.

The following BusCat strings are the standard one seen for generators and switched shunts using local voltage control as described in the [Power Flow: Bus Equation Basics](#power-flow-bus-equation-basics) topic.

  - **PQ**: buses that have no voltage control devices such as a generator at them and are also not remotely controlled by a generator will be called a PQ bus. We call them a PQ bus because we use the equations for summation of real power (P) and reactive power (Q) at these buses and the unknown variables are then voltage angle (V) and voltage angle (d).
  - **PV**: a bus that has a generator at it which is regulating the terminal voltage to a voltage setpoint will be called a PV bus. Again this is because the equations are the summation of real power (P) and an equation for Voltage = Setpoint (V). The unknown variables are then voltage angle (d) and the extra Q injection at the bus. The extra Q injection at the bus is then used to assign the reactive power output to the generators at the bus.
  - **Slack**: one bus in each electrical island is chosen as the island slack bus. This bus has a fixed voltage magnitude and voltage angle. Using our notation we might call it a dV bus. The unknown variables at this bus are then the real power (P) and reactive power (Q) which are then used to assign the real and reactive power at the slack generator.
  - **PQ (Gens at Var Limit)**: a bus that has a generator at it regulating the terminal voltage, however presently the generator is stuck at a maximum or minimum Mvar limit and is thus no longer able to regulate the voltage. Because we are stuck at a Mvar limit, the equations used is the reactive power (Q) equation. This is an indication that the bus type would have been PV, but is not because of the generators at Mvar limits
  - **PV (SVC)**: a bus that has a switched shunt with (ShuntMode = SVC) and (SVCType = SVSMO3 or SVSMO1) configured to regulate the voltage at the terminal bus. The voltage equation will be used just as for a generator.
  - **PQ (SVC at Limit)**: similar to PQ (Gens at Limit)
  - **PQ (Continuous Shunts at Var Limit):**: similar to PQ (Gens at Limit), but it's a continous switched shunt at limits.

The following BusCat strings are the ones seen as a result of remote voltage regulation being used as described in the [Power Flow: Remote Voltage Regulation](#power-flow-remote-voltage-regulation) topic.

  - **PV (Remote Reg Primary)**: the primary bus in a group of buses performing remote regulation will enforce the bus voltage equation *at the regulated Bus R*
  - **PQ (Remote Reg Secondary)**: secondary buses in a group of buses performing remote regulation will enforce a rather complex equation then ensures that the total Mvar output of generators at the respective bus is equal to the appropriate proportion of the summation of the Mvar outputs at all generators in the group.
  - **PQ (Remotely Regulated)**: A bus that is regulated by a group of generators at remote bus will just enforce the real and reactive power flow summation at its bus.
  - **PV (Local/Remote Reg Primary)**: This is seen when there are a group of generators at different buses that all regulate the voltage at a regulated bus and that regulated bus also has generation participating in the regulation. Thus this bus is regulating its own voltage, but doing so in coordination with generators at other remote buses.
  - **PQ (Remotely Regulated at Var Limit)**: This is seen for a remotely regulated bus if all the generators which are regulating it are at MVar limits.

The following BusCat strings are the ones seen as a result of line drop compensation being used as described in the [Power Flow: Line Drop Compensation](#power-flow-line-drop-compensation) topic.

  - **PQ (Line Drop Comp)**: indicates that generation at this is configured to use Line Drop compensation so a special reactive equation is written to account for this.
  - **PQ (SVC Line Drop Comp)**: same as PQ (Line Drop Comp), but indicates a switched shunt configured as an SVC on line drop comp is present.

The following BusCat strings are the ones seen as a result of Voltage Setpoint Tolerance being used as described in the [Power Flow: Voltage Setpoint Tolerance](#power-flow-voltage-setpoint-tolerance) topic. The ability to use a Voltage Setpoint Tolerance was added in Simulator Version 21

  - **PVTol**: Same as the PV, except the voltage equation for the bus is modified such that when the bus voltage is equal to (VoltSet - VoltSetTol), the generators at the bus will operate at their maximum Mvar Limit and when the bus voltage is equal to (VoltSet + VoltSetTol), the generators at the bus will operate at their minmum Mvar Limit
  - **PVTol (Remote Reg Primary)**: Same as the PV (Remote Reg Primary), except the voltage equation for the remote bus is modified such that when the regulated bus voltage is equal to (VoltSet - VoltSetTol), the generators participating in remote regulation will operate at their maximum Mvar Limit and when the regulated bus voltage is equal to (VoltSet + VoltSetTol), the generators participating in remote regulation will operate at their minmum Mvar Limit
  - **PVTol (Local/Remote Reg Primary)**: Same concept as PVl (Local/Remote Reg Primary), except this the voltage equation includes the Voltage Setpoint Tolerance again.

The following BusCat strings are the ones seen as a result of Voltage Droop Control with Deadband as described in the [Power Flow: Voltage Droop Control with Deadband](#power-flow-voltage-droop-control-with-deadband) topic. The ability to use a Voltage Droop control with Deadband was added in Simulator Version 21

  - **PQ (Voltage Droop Reg Bus)**: this represents the remotely regulated bus of a group of generators that are assigned to the same Voltage Droop Control . The equation at this bus is a special reactive power flow equation ensuring that the droop control curve is enforced.
  - **PQ (Voltage Droop Remote Bus)**: this represents on of the remote buses in a group of buses performing voltage droop control. It will enforce a rather complex equation then ensures that the total Mvar output of generators at the respective bus is equal to the appropriate proportion of the summation of the Mvar outputs at all generators in the group.
  - **PQ (Voltage Droop Reg Bus at Var Limit)**: This is an indication that all the generators that are remotely regulating this bus using voltage droop control are at a Mvar limit.
  - **PQ (Voltage Droop Remote Bus at Var Limit)**: This is an indication that a remotely regulating bus in a voltage droop control is at a Mvar limit.

---

<a id="simulator-options"></a>

## Simulator Options

*Source: [`Content/MainDocumentation_HTML/Simulator_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Simulator_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

Simulator provides a flexible environment for simulating power system operation by offering you access to a number of customizable options. The **Simulator Options**dialog houses pages of options that you can customize to tailor the program to your needs.

To display the Simulator Options dialog go to the [Options](02-simulator-ribbon.md#case-information-tab-overview) ribbon tab, and choose **Simulator Options** from the Case Options ribbon group. The Simulator Options button is also available on the [Tools](02-simulator-ribbon.md#tools-tab-overview) ribbon tab on the [Power Flow Tools](02-simulator-ribbon.md#simulation-control) ribbon group.

There are several categories of options for the Simulator Options dialog:

[Power Flow Solution Options](#power-flow-solution-options)

[Environment Options](10-power-flow-solution-and-options-part2.md#environment-options)

[Oneline Options](10-power-flow-solution-and-options-part2.md#oneline-options)

[File Management Options](10-power-flow-solution-and-options-part2.md#file-management-options)

[Case Information Display Options](10-power-flow-solution-and-options-part2.md#case-information-display-options)

[Message Log Options](10-power-flow-solution-and-options-part2.md#message-log-options)

[Distributed Computing Options](10-power-flow-solution-and-options-part2.md#distributed-computing-add-ons)

---

<a id="power-flow-solution-options"></a>

## Power Flow Solution Options

*Source: [`Content/MainDocumentation_HTML/Power_Flow_Solution_Options.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Power_Flow_Solution_Options.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

The following options are all contained on the [Simulator Options](#simulator-options) dialog.

The Power Flow Solution Tab offers various options regarding how Simulator solves the power flow problem. There are six sub-categories on the Power Flow Solutions tab: [Common Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-common-options), [Advanced Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-advanced-options), [Island-Based AGC](10-power-flow-solution-and-options-part2.md#power-flow-solution-island-based-agc), [DC Options](10-power-flow-solution-and-options-part2.md#power-flow-solution-dc-options), [General](10-power-flow-solution-and-options-part2.md#power-flow-solution-general), and [Storage](10-power-flow-solution-and-options-part2.md#power-flow-solution-storage). Each of these categories is shown on tabs. Many of the options in the Power Flow Solution options will be of interest only to advanced users of the package.
