---
title: "TS Models — Loads (Part 3 of 3)"
part: "Transient Models"
chapter_file: "43-ts-models-load-part3.md"
topics: 38
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Loads (Part 3 of 3)

Load characteristic models, distributed generation, distribution equivalents and load relays.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (38)**

- [PERC2](#perc2)
- [PlayInLoad](#playinload)
- [PQWave](#pqwave)
- [WSCC](#wscc)
- [Algebraic V and F](#algebraic-v-and-f)
- [Composite](#composite)
- [Induction Motor 1 Phase](#induction-motor-1-phase)
- [Induction Motor 3 Phase](#induction-motor-3-phase)
- [Power Electronic](#power-electronic)
- [Other](#other)
- [PlayIn](#playin)
- [BPA Loads](#bpa-loads)
- [BPA_Induction_Motor_I](#bpa-induction-motor-i)
- [BPA_Induction_Motor_L](#bpa-induction-motor-l)
- [BPA_Type_LA](#bpa-type-la)
- [BPA_TYPE_LB](#bpa-type-lb)
- [Distributed Generation](#distributed-generation)
- [DGDER_A](#dgder-a)
- [DGPV](#dgpv)
- [Distribution Equivalent](#distribution-equivalent)
- [Load Model Group](#load-model-group)
- [Relay](#relay)
- [DLSH](#dlsh)
- [LDS3](#lds3)
- [LDS3_OF_AK](#lds3-of-ak)
- [LDS4](#lds4)
- [LDSH](#ldsh)
- [LDST](#ldst)
- [LSDT1](#lsdt1)
- [LSDT2](#lsdt2)
- [LSDT3](#lsdt3)
- [LSDT3A](#lsdt3a)
- [LSDT7](#lsdt7)
- [LSDT8](#lsdt8)
- [LSDT9](#lsdt9)
- [LRDT9](#lrdt9)
- [LVS3](#lvs3)
- [LVSH](#lvsh)

---

<a id="perc2"></a>

## PERC2

*Source: [`Content/TransientModels_HTML/Load Characteristic PERC2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic PERC2.htm)*

Available in July 28, 2026 path of Version 24

PERC2 is an acronym for the **Power Electronic Reconnecting and Ceasing** load model.

PERC2 is a modification of the [PERC1](43-ts-models-load-part2.md#perc1) model which itself is based on [LDEV1](43-ts-models-load-part2.md#ldev1) which was based on the model developed by EPRI summarized in the November 2022 report entitled

"A Positive Sequence Model for Aggregated Representation Electric Vehicle Chargers"

EPRI Project 1-116982

written by L. Sundaresh and P. Matra

The model expands the PERC1 model from 30 input parameters to 57 to provide additional features and complexity. If PERC1 is appropriate for modeling your load, we would recommend using PERC1 as it is less complex. As with PERC1, this model is appropriate to represent any aggregation of a large number of power electronic loads. Examples would be an electrical vehicle charging, a large number of computers such as a data center, a cryptocurrency mining facility, a large number of variable frequency drives, and so on.

The changes made to PERC1 to create the PERC2 are as follows.

1.  (Change of interpretation for Tramp values. )  
    After releasing the PERC1 model in 2025, it became clear that the Tramp value represents not a time, but instead a ramp rate used when devices come back from a cease event. Tramp was changed in PERC2 so that it now represents the time over which a ramp occurs when the portion of the model that reconnects goes from fully ceased to the fully reconnected <span class="underline">when operating at rated power</span>. Because the device limit is actually a ramp rate limit, if the device is operating at a fraction of its rated power, then the amount of time for the ramp should be scaled by this fraction. The parameter Lfm represents the Load factor of the device. Internally in the model, a value TrampUsed will be calculated as equal to Tramp\*Lfm. Thus if it takes 10 seconds to ramp when operating at rating power, then if Lfm = 0.30 it will instead only take 3 seconds to ramp. Same logic will be applied when using the TLrampL and TLrampH values as well.

2.  (Add 1 parameter)  
    **Imax** added a total current limit which is used in combination with the existing Ipmin, Ipmax, Iqmin, and Iqmax values. A value of 0 can be entered for Imax to indicate the parameter is not used.

3.  (Add 1 parameter)  
    The Reconnection Zone adds a high voltage threshold (VLrecon \<= Vfilt \<= **VHrecon**). Previous Vrecon is now called VLrecon.

4.  (Add 1 parameter)  
    The Cease zone adds a high voltage threshold (VLcease \<= Vfilt \<= **VHcease**). Previous Vcease is now called VLcease.

5.  (Add 10 parameters)  
    Four Long Cease Low Voltage threshold/timer pairs (**VLC1/TVLC1** ... **VLC4/TVLC4**) for a low voltage cease zone. When entering this zone the time for reconnection is **TLreconL** and the time for ramping is **TLrampL\*Lfm**) (These represent a Long reconnection and ramp time for a Low voltage excursion). As indicated by the names, the expectation is that this times will be longer than for the original Cease Zone.

6.  (Add 10 parameters)  
    Four Long Cease High Voltage threshold/timer pairs (**VHC1/TVHC1** ... **VHC4/TVHC4**) for a high voltage cease zone. When entering this zone the time of reconnection is (**TLreconH** and the time for ramping is **TLrampH\*Lfm**) (These represent the Long reconnection and ramp time for a High voltage excursion). As indicated by the names, the expectation is that this times will be longer than for the original Cease Zone.

7.  (Add 4 parameters)  
    Both Low and High Frequency threshold/timer pairs **(FLC1/TFLC1** and **FHC1/TFHC1**) for a frequency cease zone. When entering this zone, then no reconnection will occur.

Description of the PERC2

This model can be used to represent any aggregation of a large number of power electronic loads. Examples would be an electrical vehicle charging station, a large number of computers such as a data center, a crypto-currency mining facility, a large number of variable frequency drives, and so on.

The values MWinit and Mvarinit on the left of the block diagram below are calculated as part of the stability simulation initialization routine. MWInit is set equal to the initial MW of the load. When this model is used inside the [CompLoad component-based load structure](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic), then the parameter QPRatio is used to calculate the Mvarinit value and any extra Mvars are assigned as done with the [CompLoad](36-transient-stability-overview-and-data-part1.md#load-component-and-compload-characteristic). When this model is used as a stand-alone model as part of a LoadModelGroup, Load, Bus, Area, etc. then the QPRatio is ignored and the Mvarinit is set equal to the load's initial Mvar. If a simple event occurs in the simulation and the final voltage returns to the initial voltage and the cease and reconnect logic is never engaged during the simulation, then this model will bring the MW and Mvar back to the same as the initial condition. The top half of the block diagram below represents the real power (MW) response of the load while the bottom half of the block diagram represents the reactive power (Mvar) response.

The dynamic portion of this model is described in the left side of the block diagram by the dynamic states 1 - 6 . The washout blocks (Kvp/Tvp and Kvq/Tvq parameters) model a response where the model load will decrease when a decreasing voltage is encountered (such as after and during a fault) and the load will then increase when the voltage is increasing (during fault recovery). This is meant to model a device such as a variable frequency drive which may reduce the electrical power during a fault, but then after the fault clears an additional amount of load will be seen to re-accelerate the mechanical load that the VFD is driving. This model is not simulating any characteristics of the mechanical load or the control system that causes this behavior, but is using the simple washout blocks to approximation the behavior. The MW control path also includes a simple frequency droop with deadband response that the load may have. After this the lead lag blocks are used to model any other transient response of the real and reactive loads. This leads to States 1 and 2 in the block diagram below which represent the model's request for a per unit power based on the initial voltage Vinit.

After this, both the real power and reactive portions of this model have a user input which is the exponent of the voltage relationship relative to the initial voltage. Any value of nP and nQ is allowed, but it is useful to realize that nP = 0 indicates a constant power at steady state, nP = 1 indicates constant current, and nP = 2 indicates constant impedance. After the exponent, it then divides by per unit voltage to convert to a current signal. The limits Ipmax/Ipmin or Iqmax/Iqmin are then used in conjunction with Imax to calculated IpmaxUsed/IpminUsed and IqmaxUsed/IqminUsed. Please see the detailed pseudo-code at the bottom of this help topic for details of how these current limits are enforced.

Next the current is multiplied by a value FracOn which represents the fraction of the load that remains connected to the system. The FracOn models the Cease and Reconnect logic.

PERC1 logic was relatively simple: if the filtered voltage is less than Vcease for more than Tcease seconds, then a decision to cease a portion of the load is made. Then, after an additional delay of Tdelay seconds, the FracOn is reduced to a value of (1 - Fcease). Then the system will wait to see if the filtered voltage goes above Vrecon for more than Trecon seconds at which time it will begin ramping the FracOn value back up over a time of Tramp seconds to a value of (1 - Fcease + Fcease\*Frecon).

PERC2 expands on this logic a lot by including 4 different zones in which ceasing may occur along with 4 different Reconnection and Ramping times as described in the following table.

<table>
<tbody>
<tr class="odd">
<td> </td>
<td><p>Zone</p></td>
<td><p>Logic to Enter Zone</p></td>
<td><p>TreconUsed and TrampUsed</p></td>
<td><p>After the Zone is reached , what other zones continue to be checked</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Cease Zone (Blue Zone)</p></td>
<td><p>(Vfilt &lt; VLcease ) for Tcease seconds</p>
<p>OR (Vfilt &gt; VHcease) for Tcease seconds</p></td>
<td><p>TreconUsed = Trecon</p>
<p>TrampUsed = Tramp*Lfm</p></td>
<td><p>Long Cease High Zone</p>
<p>Long Cease Low Zone</p>
<p>Frequency Zone</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>Long Cease Low Voltage Zone (Red Zone)</p></td>
<td><p>4 low voltage threshold/timer pairs</p>
<p>(VLC1/TVLC1, etc.)</p></td>
<td><p>TreconUsed = TLreconL</p>
<p>TrampUsed= TLrmapL</p></td>
<td><p>Frequency Zone</p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>Long Cease High Voltage Zone (Purple Zone)</p></td>
<td><p>4 high voltage threshold/timer pairs</p>
<p>(VHC1/TVHC1, etc.)</p></td>
<td><p>TreconUsed = TLreconH</p>
<p>TrampUsed= TLrmapH</p></td>
<td><p>Frequency Zone</p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>High or Low Frequency Zone</p></td>
<td><p>1 low and 1 high frequency threshold/timer</p>
<p>(VHC1/TVHC1 OR VLC1/TVLC1)</p></td>
<td><p>TrecondUsed = Infinite</p>
<p>TrampUsed = Infinite</p></td>
<td><p>Nothing is checked</p>
<p>Reconnection will never occur</p></td>
</tr>
</tbody>
</table>

Additional detail is included below to describe how these timers are reset and how a voltage drops after the model begins ramping is handled. See the pseudo-code and diagrams below for more details.

Finally, the output goes through another delay block using the Tt time constant to result a final desired current for each path. The treatment of this model in the algebraic network boundary equations is then a constant current.

Model Equations and/or Block Diagrams![Load Characteristic PERC2 0001](images/Load_Characteristic_PERC2_0001.svg)

Model Parameters

<table>
<tbody>
<tr class="odd">
<td><p>Index</p></td>
<td><p>Parameter</p></td>
<td><p>Description</p></td>
<td><p>Default</p></td>
</tr>
<tr class="even">
<td><p>0</p></td>
<td><p>Lfm</p></td>
<td><p>Loading factor used to calculate MVAbase of model as MWinit/Lfm.</p>
<p>If Lfm &lt; 0.001 then software will use a value of 1.000</p></td>
<td><p>0.80</p></td>
</tr>
<tr class="odd">
<td><p>1</p></td>
<td><p>QPratio</p></td>
<td><p>Q/P ratio for Q0 computation from P0 when used as a component of a CompLoad.</p>
<p>When used as a stand-alone load model, Q0 = Qinit always.</p></td>
<td><p>0.66</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Tt</p></td>
<td><p>Time delay for outputs [seconds] (If &lt; 4*TimeStep will be treated as 4*TimeStep)</p></td>
<td><p>0.02</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Tv</p></td>
<td><p>Voltage measurement time constant [s]</p></td>
<td><p>0.02</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Tf</p></td>
<td><p>Frequency measurement time constant [s]</p></td>
<td><p>0.02</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>Dbdl</p></td>
<td><p>Deadband on frequency response low (&lt;=0) [pu]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>Dbdh</p></td>
<td><p>Deadband on frequency response high (&gt;=0) [pu]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>Kdroop</p></td>
<td><p>Frequency droop [per unit]</p></td>
<td><p>10.00</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>Kvp</p></td>
<td><p>Proportional constant for active power washout</p></td>
<td><p>0.02</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>Tvp</p></td>
<td><p>Time constant for active power washout [seconds]</p></td>
<td><p>0.02</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>Kvq</p></td>
<td><p>Proportional constant for reactive power washout</p></td>
<td><p>0.50</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>Tvq</p></td>
<td><p>Time constant for reactive power washout [seconds]</p></td>
<td><p>0.10</p></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p>Tap</p></td>
<td><p>Lead time constant for real power path [seconds]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p>Tbp</p></td>
<td><p>Lag time constant for real power path [seconds]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>Taq</p></td>
<td><p>Lead time constant for reactive power path [seconds]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p>Tbq</p></td>
<td><p>Lag time constant for reactive power path [seconds]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="even">
<td><p>16</p></td>
<td><p>nP</p></td>
<td><p>Active Power Exponential</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="odd">
<td><p>17</p></td>
<td><p>nQ</p></td>
<td><p>Reactive Power Exponential</p></td>
<td><p>1.00</p></td>
</tr>
<tr class="even">
<td><p>18</p></td>
<td><p>Ipmax</p></td>
<td><p>Maximum Ip [per unit]</p></td>
<td><p>1.00</p></td>
</tr>
<tr class="odd">
<td><p>19</p></td>
<td><p>Ipmin</p></td>
<td><p>Minimum Ip [per unit]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="even">
<td><p>20</p></td>
<td><p>Iqmax</p></td>
<td><p>Maximum Iq [per unit]</p></td>
<td><p>0.66</p></td>
</tr>
<tr class="odd">
<td><p>21</p></td>
<td><p>Iqmin</p></td>
<td><p>Minimum Iq [per unit]</p></td>
<td><p>-0.66</p></td>
</tr>
<tr class="even">
<td><p>22</p></td>
<td><p>Imax</p></td>
<td><p>Maximum total current [per unit]</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="odd">
<td><p>23</p></td>
<td><p>Fcease</p></td>
<td><p>Fraction that will cease (between 0 and 1)</p></td>
<td><p>1.00</p></td>
</tr>
<tr class="even">
<td><p>24</p></td>
<td><p>Frecon</p></td>
<td><p>Of the fraction that ceases, this is the fraction that then reconnects (&gt;=0).<br />
Frecon &gt; 1.0 allowed for a load that comes back above the initial value after reconnecting.</p></td>
<td><p>1.00</p></td>
</tr>
<tr class="odd">
<td><p>25</p></td>
<td><p>Tdelay</p></td>
<td><p>Time delay to cease after detection. Same for delay for all cease zones (&gt;= 0) [seconds]</p></td>
<td><p>0.00</p></td>
</tr>
<tr class="even">
<td><p>26</p></td>
<td><p>VLrecon</p></td>
<td><p>Low Voltage threshold to initiate power ramp reconnection logic [per unit]</p></td>
<td><p>0.80</p></td>
</tr>
<tr class="odd">
<td><p>27</p></td>
<td><p>VHrecon</p></td>
<td><p>High Voltage threshold to initiate power ramp reconnection logic [per unit]</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="even">
<td><p>28</p></td>
<td><p>Tramp</p></td>
<td><p>Cease logic Ramp up time for portion of load that reconnects to ramp from<br />
0 to 100% at full Mbase (&gt;= 0) [seconds]. TrampUsed = Tramp*Lfm</p></td>
<td><p>0.15</p></td>
</tr>
<tr class="odd">
<td><p>29</p></td>
<td><p>Trecon</p></td>
<td><p>Reconnection time delay for ramp up logic to be initiated for cease logic [per unit]</p></td>
<td><p>0.05</p></td>
</tr>
<tr class="even">
<td><p>30</p></td>
<td><p>VLcease</p></td>
<td><p>Low Voltage threshold for the Cease logic [per unit]</p></td>
<td><p>0.80</p></td>
</tr>
<tr class="odd">
<td><p>31</p></td>
<td><p>VHcease</p></td>
<td><p>High Voltage threshold for the Cease logic [per unit]<br />
(Negative or Zero value indicates that this threshold should be ignored)</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="even">
<td><p>32</p></td>
<td><p>Tcease</p></td>
<td><p>Low Time delay for Cease logic to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.01</p></td>
</tr>
<tr class="odd">
<td><p>33</p></td>
<td><p>TLrampL</p></td>
<td><p>Long Low Cease logic Ramp up time. (&gt;= 0) [seconds]. TrampUsed = TrampLL*Lfm</p></td>
<td><p>5.00</p></td>
</tr>
<tr class="even">
<td><p>34</p></td>
<td><p>TLreconL</p></td>
<td><p>Long Low Cease Time delay for ramp up logic to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.05</p></td>
</tr>
<tr class="odd">
<td><p>35</p></td>
<td><p>VLC1</p></td>
<td><p>First Low Voltage threshold for Long Cease [per unit]</p></td>
<td><p>0.90</p></td>
</tr>
<tr class="even">
<td><p>36</p></td>
<td><p>TVLC1</p></td>
<td><p>First Low Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="odd">
<td><p>37</p></td>
<td><p>VLC2</p></td>
<td><p>Second Low Voltage threshold for Long Cease [per unit]</p></td>
<td><p>0.80</p></td>
</tr>
<tr class="even">
<td><p>38</p></td>
<td><p>TVLC2</p></td>
<td><p>Second Low Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.50</p></td>
</tr>
<tr class="odd">
<td><p>39</p></td>
<td><p>VLC3</p></td>
<td><p>Third Low Voltage threshold for Long Cease [per unit]</p></td>
<td><p>0.50</p></td>
</tr>
<tr class="even">
<td><p>40</p></td>
<td><p>TVLC3</p></td>
<td><p>Third Low Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.25</p></td>
</tr>
<tr class="odd">
<td><p>41</p></td>
<td><p>VLC4</p></td>
<td><p>Fourth Low Voltage threshold for Long Cease [per unit]</p></td>
<td><p>0.35</p></td>
</tr>
<tr class="even">
<td><p>42</p></td>
<td><p>TVLC4</p></td>
<td><p>Fourth Low Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.15</p></td>
</tr>
<tr class="odd">
<td><p>43</p></td>
<td><p>TLrampH</p></td>
<td><p>Long High Cease logic Ramp up time. (&gt;= 0) [seconds]. TrampUsed = TrampLL*Lfm</p></td>
<td><p>5.00</p></td>
</tr>
<tr class="even">
<td><p>44</p></td>
<td><p>TLreconH</p></td>
<td><p>Long High Cease Time delay for ramp up logic to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>0.05</p></td>
</tr>
<tr class="odd">
<td><p>45</p></td>
<td><p>VHC1</p></td>
<td><p>First High Voltage threshold for Long Cease [per unit]<br />
(Negative or Zero value indicates that this threshold should be ignored)</p></td>
<td><p>1.10</p></td>
</tr>
<tr class="even">
<td><p>46</p></td>
<td><p>TVHC1</p></td>
<td><p>First High Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>1.00</p></td>
</tr>
<tr class="odd">
<td><p>47</p></td>
<td><p>VHC2</p></td>
<td><p>Second High Voltage threshold for Long Cease [per unit]<br />
(Negative or Zero value indicates that this threshold should be ignored)</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="even">
<td><p>48</p></td>
<td><p>TVHC2</p></td>
<td><p>Second High Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>99.00</p></td>
</tr>
<tr class="odd">
<td><p>49</p></td>
<td><p>VHC3</p></td>
<td><p>Third High Voltage threshold for Long Cease [per unit]<br />
(Negative or Zero value indicates that this threshold should be ignored)</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="even">
<td><p>50</p></td>
<td><p>TVHC3</p></td>
<td><p>Third High Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>99.00</p></td>
</tr>
<tr class="odd">
<td><p>51</p></td>
<td><p>VHC4</p></td>
<td><p>Fourth High Voltage threshold for Long Cease [per unit]<br />
(Negative or Zero value indicates that this threshold should be ignored)</p></td>
<td><p>2.00</p></td>
</tr>
<tr class="even">
<td><p>52</p></td>
<td><p>TVHC4</p></td>
<td><p>Fourth High Time delay for Long Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>99.00</p></td>
</tr>
<tr class="odd">
<td><p>53</p></td>
<td><p>FLC1</p></td>
<td><p>Low Frequency Threshold for Forever Cease [Hz]</p></td>
<td><p>57.00</p></td>
</tr>
<tr class="even">
<td><p>54</p></td>
<td><p>TFLC1</p></td>
<td><p>Low Frequency Time Delay for Forever Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>999.00</p></td>
</tr>
<tr class="odd">
<td><p>55</p></td>
<td><p>FHC1</p></td>
<td><p>High Frequency Threshold for Forever Cease [Hz]</p></td>
<td><p>63.00</p></td>
</tr>
<tr class="even">
<td><p>56</p></td>
<td><p>TFHC1</p></td>
<td><p>High Frequency Time Delay for Forever Cease to be initiated (&gt;= 0) [seconds]</p></td>
<td><p>999.00</p></td>
</tr>
</tbody>
</table>

![Load Characteristic PERC1 CeaseReconnect3 784x327](images/Load_Characteristic_PERC1_CeaseReconnect3_784x327.png)

![Load Characteristic PERC1 CeaseReconnect2 784x286](images/Load_Characteristic_PERC1_CeaseReconnect2_784x286.png)

![Load Characteristic PERC1 CeaseReconnect1 787x512](images/Load_Characteristic_PERC1_CeaseReconnect1_787x512.png)

![Load Characteristic PERC2 0004](images/Load_Characteristic_PERC2_0004.svg)

![Load Characteristic PERC2 0005](images/Load_Characteristic_PERC2_0005.svg)

![Load Characteristic PERC2 0006](images/Load_Characteristic_PERC2_0006.svg)

![Load Characteristic PERC2 0007](images/Load_Characteristic_PERC2_0007.svg)

![Load Characteristic PERC2 0008](images/Load_Characteristic_PERC2_0008.svg)

![Load Characteristic PERC2 0009](images/Load_Characteristic_PERC2_0009.svg)

---

<a id="playinload"></a>

## PlayInLoad

*Source: [`Content/TransientModels_HTML/Load Characteristic PlayInLoad.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic PlayInLoad.htm)*

Model Equations and/or Block Diagrams

Added in Version 24, build on April 22, 2026

![Load Characteristic PlayInLoad 0001](images/Load_Characteristic_PlayInLoad_0001.svg)

---

<a id="pqwave"></a>

## PQWave

*Source: [`Content/TransientModels_HTML/Load Characteristic PQWave.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic PQWave.htm)*

Model Equations and/or Block Diagrams

Added in Version 24, build on April 22, 2026

![Load Characteristic PQWave 0001](images/Load_Characteristic_PQWave_0001.svg)

---

<a id="wscc"></a>

## WSCC

*Source: [`Content/TransientModels_HTML/Load Characteristic WSCC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic WSCC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Model supported by PSLF

**Parameters:**

|     |                                            |
| --- | ------------------------------------------ |
| p1  | Constant impedance fraction in p.u.        |
| q1  | Constant impedance fraction in p.u.        |
| p2  | Constant current fraction in p.u.          |
| q2  | Constant current fraction in p.u.          |
| p3  | Constant power fraction in p.u.            |
| q3  | Constant power fraction in p.u.            |
| p4  | Frequency dependent power fraction in p.u. |
| q4  | Frequency dependent power fraction in p.u. |
| lpd | Real power frequency index in p.u.         |
| lqd | Reactive power frequency index in p.u.     |

If p4 OR q4 are non-zero then

P=P\_o \[p\_1 V^2+p\_2 V+p\_3+p\_4 (1+lpd(freqpu-1))\]

Q=Q\_o \[q\_1 V^2+q\_2 V+q\_3+q\_4 (1+lpq(freqpu-1))\]

else

P=P\_o \[p\_1 V^2+p\_2 V+p\_3 \]\[1+lpd(freqpu-1)\]

Q=Q\_o \[q\_1 V^2+q\_2 V+q\_3 \]\[1+lpq(freqpu-1)\]

V= per unit voltage magnitude at the terminal bus

freqpu = per unit bus frequency at the terminal bus

P\_o and Q\_o are calculated during initialization to match the initial conditions

---

<a id="algebraic-v-and-f"></a>

## Algebraic V and F

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder AlgebraicVF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder AlgebraicVF.htm)*

_This topic has no body text in the source help file._

---

<a id="composite"></a>

## Composite

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder Composite.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder Composite.htm)*

_This topic has no body text in the source help file._

---

<a id="induction-motor-1-phase"></a>

## Induction Motor 1 Phase

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder InductionMotor1P.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder InductionMotor1P.htm)*

_This topic has no body text in the source help file._

---

<a id="induction-motor-3-phase"></a>

## Induction Motor 3 Phase

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder InductionMotor3P.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder InductionMotor3P.htm)*

_This topic has no body text in the source help file._

---

<a id="power-electronic"></a>

## Power Electronic

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder Power Electronic.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder Power Electronic.htm)*

_This topic has no body text in the source help file._

---

<a id="other"></a>

## Other

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder Other.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder Other.htm)*

_This topic has no body text in the source help file._

---

<a id="playin"></a>

## PlayIn

*Source: [`Content/TransientModels_HTML/Load CharacteristicFolder PlayIn.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load CharacteristicFolder PlayIn.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-loads"></a>

## BPA Loads

*Source: [`Content/TransientModels_HTML/BPA Loads.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/BPA Loads.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-induction-motor-i"></a>

## BPA_Induction_Motor_I

*Source: [`Content/TransientModels_HTML/Load Characteristic BPA INDUCTION MOTOR I.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic BPA INDUCTION MOTOR I.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-induction-motor-l"></a>

## BPA_Induction_Motor_L

*Source: [`Content/TransientModels_HTML/Load Characteristic BPA INDUCTION MOTOR L.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic BPA INDUCTION MOTOR L.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

---

<a id="bpa-type-la"></a>

## BPA_Type_LA

*Source: [`Content/TransientModels_HTML/Load Characteristic BPA TYPE LA.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic BPA TYPE LA.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="bpa-type-lb"></a>

## BPA_TYPE_LB

*Source: [`Content/TransientModels_HTML/Load Characteristic BPA TYPE LB.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic BPA TYPE LB.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="distributed-generation"></a>

## Distributed Generation

*Source: [`Content/TransientModels_HTML/Load Distributed Generation.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Distributed Generation.htm)*

_This topic has no body text in the source help file._

---

<a id="dgder-a"></a>

## DGDER_A

*Source: [`Content/TransientModels_HTML/Distributed Generation DGDER_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Distributed Generation DGDER_A.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

The DGDER\_A Load Distributed Generation model is identical to the machine model DER\_A. See the help documentation on DER\_A for more information.

**Parameters:**

|           |                                                                                                                                                                                                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PfFlag    | PfFlag: 0 means for constant Q control; 1 means constant power factor control (any number which is not 0 is treated as 1)                                                                                                                                                       |
| FreqFlag  | FreqFlag: 0 means frequency control disabled; 1 means frequency control enabled (any number which is not 0 is treated as 1)                                                                                                                                                     |
| PQFlag    | PQFlag: 0 means Q priority; 1 means P priority for current limit (any number which is not 0 is treated as 1)                                                                                                                                                                    |
| TypeFlag  | TypeFlag: 0 means the unit is a storage device and Ipmin = - Ipmax; 1 means the unit is a generator Ipmin = 0 (any number which is not 0 is treated as 1)                                                                                                                       |
| VtripFlag | VtripFlag: 0 means disable the voltage trip logic; 1 means enable the voltage trip logic (any number which is not 0 is treated as 1)                                                                                                                                            |
| FtripFlag | FtripFlag: 0 means disable the frequency trip logic; 1 means enable the frequency trip logic (any number which is not 0 is treated as 1)                                                                                                                                        |
| Trv       | Trv: transducer time constant (seconds) for voltage measurement (can be zero)                                                                                                                                                                                                   |
| Trf       | Trf: transducer time constant (seconds) for frequency measurement (\> 0)                                                                                                                                                                                                        |
| dbd1      | dbd1: lower voltage deadband \<= 0 (pu)                                                                                                                                                                                                                                         |
| dbd2      | dbd2: upper voltage deadband \>= 0 (pu)                                                                                                                                                                                                                                         |
| Kqv       | Kqv: proportional voltage control gain (pu/pu)                                                                                                                                                                                                                                  |
| Vref0     | Vref0: voltage reference set-point (pu)                                                                                                                                                                                                                                         |
| Tp        | Tp: transducer time constant (seconds)                                                                                                                                                                                                                                          |
| Tiq       | Tiq: Q control time constant (seconds)                                                                                                                                                                                                                                          |
| Ddn       | Ddn: frequency control droop gain \>= 0 (down-side)                                                                                                                                                                                                                             |
| Dup       | Dup: frequency control droop gain \>= 0 (up-side)                                                                                                                                                                                                                               |
| fdbd1     | fdbd1: lower frequency control deadband \<= 0 (pu)                                                                                                                                                                                                                              |
| fdbd2     | fdbd2: upper frequency control deadband \>= 0 (pu)                                                                                                                                                                                                                              |
| femax     | femax: frequency control maximum error (pu) \>= 0                                                                                                                                                                                                                               |
| femin     | femin: frequency control minimum error (pu) \<= 0                                                                                                                                                                                                                               |
| Pmax      | Pmax: Maximum power (pu)                                                                                                                                                                                                                                                        |
| Pmin      | Pmin: Minimum power (pu)                                                                                                                                                                                                                                                        |
| dPmax     | dPmax: Power ramp rate up \>= 0 (pu/s)                                                                                                                                                                                                                                          |
| dPmin     | dPmin: Power ramp rate down \<= 0 (pu/s)                                                                                                                                                                                                                                        |
| Tpord     | Tpord: Power order time constant (seconds)                                                                                                                                                                                                                                      |
| Kpg       | Kpg: active power control proportional gain                                                                                                                                                                                                                                     |
| Kig       | Kig: active power control integral gain                                                                                                                                                                                                                                         |
| Imax      | Imax: Maximum converter current (pu)                                                                                                                                                                                                                                            |
| Vl0       | Vl0: voltage break-point for low voltage cut-out of the inverter (Multiplier = 0.0 at this voltage)                                                                                                                                                                             |
| Vl1       | Vl1: voltage break-point for low voltage cut-out of the inverter (Multiplier = 1.0 at this voltage)                                                                                                                                                                             |
| Vh0       | Vh0: voltage break-point for high voltage cut-out of the inverter (Multiplier = 0.0 at this voltage)                                                                                                                                                                            |
| Vh1       | Vh1: voltage break-point for high voltage cut-out of the inverter (Multiplier = 1.0 at this voltage)                                                                                                                                                                            |
| Tvl0      | Tvl0: voltage break-point for low voltage cut-out timer (If voltage stays below vl0 for more than tvl0 seconds, then the multiplier will remain zero for the simulation)                                                                                                        |
| Tvl1      | Tvl1: voltage break-point for low voltage cut-out timer (If voltage stays below vl1 for more than tvl1 seconds, then the multiplier will track a depressed curve according to Vrfrac and an internally tracked value of the minimum voltage experienced during the simulation)  |
| Tvh0      | Tvh0: voltage break-point for high voltage cut-out timer (If voltage stays above vl0 for more than tvl0 seconds, then the multiplier will remain zero for the simulation)                                                                                                       |
| Tvh1      | Tvh1: voltage break-point for high voltage cut-out timer (If voltage stays above vl1 for more than tvl1 seconds, then the multiplier will track a depressed curve according to Vrfrac and an internally tracked value of the maximum voltage experienced during the simulation) |
| Vrfrac    | Vrfrac: fraction of device that recovers after voltage comes back to within vl1 \< V \< vh1 (Note that the timers Tvl1 and Tvh1 also impact when this fraction is used)                                                                                                         |
| Tv        | Tv: time constant on the output of the voltage cut-out                                                                                                                                                                                                                          |
| fl        | fl: frequency break-point for low frequency cut-out of the inverter (Hertz)                                                                                                                                                                                                     |
| fh        | fh: frequency break-point for high frequency cut-out of the inverter (Hertz)                                                                                                                                                                                                    |
| Tfl       | Tfl: frequency break-point for low frequency cut-out timer (seconds) (highly recommend that Tfl \> Trf)                                                                                                                                                                         |
| Tfh       | Tfh: frequency break-point for high frequency cut-out timer (seconds) (highly recommend that Tfh \> Trf)                                                                                                                                                                        |
| Vpr       | Vpr: voltage below which frequency tripping is disabled (pu)                                                                                                                                                                                                                    |
| Tg        | Tg: Current control time constant                                                                                                                                                                                                                                               |
| rrpwr     | rrpwr: Power rise ramp rate following a fault \>= 0 (pu/s)                                                                                                                                                                                                                      |
| Xe        | Xe: Generator effective reactive (pu) \> 0                                                                                                                                                                                                                                      |
| Iqh1      | Iqh1: Maximum limit of reactive current injection, p.u.                                                                                                                                                                                                                         |
| Iql1      | Iql1: Minimum limit of reactive current injection, p.u.                                                                                                                                                                                                                         |
| MBase     | Mbase: Mbase=0 means MVABase=InitialMW; Mbase\<0 means MVABase=InitialMW/abs(Mbase); Mbase\>0 means MVABase=MBase                                                                                                                                                               |

---

<a id="dgpv"></a>

## DGPV

*Source: [`Content/TransientModels_HTML/Distributed Generation DGPV.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Distributed Generation DGPV.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load DistGen DGPV 0001](images/Load_DistGen_DGPV_0001.svg)

**Parameters:**

|        |                                                                                                                                                                                                                         |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Imax   | Imax: Apparent current limit (pu)                                                                                                                                                                                       |
| Vt0    | Vt0: Voltage below which all generation is tripped (pu)                                                                                                                                                                 |
| Vt1    | Vt1: Voltage below which generation starts to trip (pu)                                                                                                                                                                 |
| Vt2    | Vt2: Voltage above which generation starts to trip (pu)                                                                                                                                                                 |
| Vt3    | Vt3: Voltage above which all generation is tripped (pu)                                                                                                                                                                 |
| Vrflag | Vrflag: Fraction of generation that can reconnect after low or high voltage tripping. 0.0 means voltage tripping is permanent; 1.0 means all generation can reconnect; Between 0 and 1 for partially self-resetting     |
| Ft0    | Ft0: Frequency below which all generation is tripped (pu)                                                                                                                                                               |
| Ft1    | Ft1: Frequency below which generation starts to trip (pu)                                                                                                                                                               |
| Ft2    | Ft2: Frequency above which generation starts to trip (pu)                                                                                                                                                               |
| Ft3    | Ft3: Frequency above which all generation is tripped (pu)                                                                                                                                                               |
| Frflag | Frflag: Fraction of generation that can reconnect after low or high frequency tripping. 0.0 means frequency tripping is permanent; 1.0 means all generation can reconnect; Between 0 and 1 for partially self-resetting |

---

<a id="distribution-equivalent"></a>

## Distribution Equivalent

*Source: [`Content/TransientModels_HTML/Load Characteristic DISTRIBUTION EQUIVALENT TYPES.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Characteristic DISTRIBUTION EQUIVALENT TYPES.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

This equivalent model and the parameters used for the Load Distribution Equivalent Types are the same as the first 17 parameters of the CMPLDW load characteristic model, along with an MVA base parameter.

Model supported by PowerWorld

**Parameters:**

|                                         |                                                                                                                                                                                                                                                                                               |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Number                                  | Number: field not used inside Simulator. This is an identifier which is used to maintain compatibility with the negative numbers used within the DYD syntax. When writing out to a DYD file, we will automatically ensure uniqueness across all load components and distribution equivalents. |
| XFMinkV                                 | XFMinkV: when a load has a terminal bus nominal kV below this value, then the transformer of the distribution equivalent will be ignored during the transient stability simulation                                                                                                            |
| Mbase                                   | Mbase: Determines how the distribution equivalent MVABase is calculated for loads.                                                                                                                                                                                                            |
| Mbase\>0 means DistMVABase = Mbase;     | Mbase\<0 means DistMVABase = LoadMW/abs(Mbase);                                                                                                                                                                                                                                               |
| Mbase=0 means DistMVABase = LoadMW/0.8. | Each load record can override this by specifying the TSDistEquivMVABase directly as well.                                                                                                                                                                                                     |
| Bss                                     | Bss: Substation shunt capacitor susceptance, p.u.                                                                                                                                                                                                                                             |
| Rfdr                                    | Rfdr: Feeder equivalent resistance, p.u.                                                                                                                                                                                                                                                      |
| Xfdr                                    | Xfdr: Feeder equivalent reactance, p.u.                                                                                                                                                                                                                                                       |
| Fb                                      | Fb: Fraction of feeder shunt capacitance at substation bus end                                                                                                                                                                                                                                |
| Xxf                                     | Xxf: Substation transformer reactance, p.u.                                                                                                                                                                                                                                                   |
| Tfixhs                                  | Tfixhs: Transformer high side fixed tap, p.u.                                                                                                                                                                                                                                                 |
| Tfixls                                  | Tfixls: Transformer low side fixed tap, p.u.                                                                                                                                                                                                                                                  |
| LTC                                     | LTC: 1 for automatic tap adjustment (low side variable tap)                                                                                                                                                                                                                                   |
| Tmin                                    | Tmin: Minimum variable tap, p.u.                                                                                                                                                                                                                                                              |
| Tmax                                    | Tmax: Maximum variable tap, p.u.                                                                                                                                                                                                                                                              |
| step                                    | step: Variable tap step size, p.u.                                                                                                                                                                                                                                                            |
| Vmin                                    | Vmin: Minimum low-side voltage, p.u.                                                                                                                                                                                                                                                          |
| Vmax                                    | Vmax: Maximum low-side voltage, p.u.                                                                                                                                                                                                                                                          |
| Tdel                                    | Tdel: Time delay to initiate tap adjustment, sec.                                                                                                                                                                                                                                             |
| Tdelstep                                | Tdelstep: Time delay between tap steps, sec.                                                                                                                                                                                                                                                  |
| Rcmp                                    | Rcmp: Transformer LTC compensating resistance, p.u.                                                                                                                                                                                                                                           |
| Xcmp                                    | Xcmp: Transformer LTC compensating reactance, p.u.                                                                                                                                                                                                                                            |

---

<a id="load-model-group"></a>

## Load Model Group

*Source: [`Content/TransientModels_HTML/Load Group.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Group.htm)*

In many cases, load characteristic model are created to allocate the behavior of a load between various components (static model and or dynamic models) by percentage. For example, the model MOTORW model allocates a percentage of various loads to a dynamic motor model while the remaining portion of the load remain a static model. In many cases, there may be 100s or 1000s of loads for which you want to use the same load model.

To handle this, Simulator's Transient Stability tool has always allowed you to assign load models to an aggregation object such as the entire system, an Area, a Zone, an Owner, or a Bus to make this data management easier. However, frequently the load behavior does not break down in the system based on the definitions of Areas, Zones, Owners, or Buses. In order to make the assignment of load model easier to manage, a new aggregation object called a Load Model Group may be created.

A Load Model Group is a very simple object which essentially has only a Name and then a list of various Load Characteristic Models (such as MOTORW, WSCC, IEEL, CMPLDW\_NF, etc.) assigned to it in the same way that load characteristics are assign to an Area, Zone, etc. A Load Model Group may represent the behavior of "High Desert" loads or "Coastal Loads" for example.

![AssignLoadsToGroupsEquivs](images/AssignLoadsToGroupsEquivs.png)

Once Load Model Groups are created, then each Load Record may optionally be assigned to a specific Load Model Group. When determining which Transient Stability Model to use for a particular load, the following logic is applied. This general hierarchy has always existed in Simulator, with only the Load Model Group part newly added.

  - If a load-specific model exist, this will be used
  - Else if the Load is assigned to a Load Model Group which has a model, this will be used
  - Else if a bus-specific model exists at the terminal bus, this will be used
  - Else if an owner-specific model exists for the load's owner, this will be used
  - Else if an zone-specific model exists for the load's zone, this will be used
  - Else if an area-specific model exists for the area's zone, this will be used
  - Else if an system-specific model exists for the power system, this will be used
  - Else the Load Modeling option specified on the Transient Stability Dialog's Option\\Power System Model section will be used. (For relays the default will be to not use a relay model at all)

Load Model Groups are now included in the hierarchy of Load Characteristics in the Model Explorer as depicted in the following image.

![LoadModelGroups](images/LoadModelGroups.png)

---

<a id="relay"></a>

## Relay

*Source: [`Content/TransientModels_HTML/Load Relay.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relay.htm)*

_This topic has no body text in the source help file._

---

<a id="dlsh"></a>

## DLSH

*Source: [`Content/TransientModels_HTML/Load Relays DLSH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays DLSH.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams 

Rate of Frequency Load Shedding Model DLSH

Model supported by PSSE

**Parameters:**

|                |                                  |
| -------------- | -------------------------------- |
| f1 to f3       | Frequency load shedding point    |
| t1 to t3       | Pickup time                      |
| Frac1 to frac3 | Fraction of load to shed         |
| tb             | Breaker time                     |
| df1 to df3     | Rate of frequency shedding point |

---

<a id="lds3"></a>

## LDS3

*Source: [`Content/TransientModels_HTML/Load Relays LDS3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LDS3.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Underfrequency Load Shedding Model with Transfer Trip LDS3

Model supported by PSSE

**Parameters:**

|                      |                               |
| -------------------- | ----------------------------- |
| Transfer Trip Object | Transfer Trip Object          |
| SC                   | Shed Shunts                   |
| f1 to f5             | Frequency load shedding point |
| t1 to t5             | Pickup time                   |
| tb1 to tb5           | Breaker time                  |
| frac1 to frac5       | Fraction of load to shed      |
| ttb                  | Transfer trip breaker time    |

---

<a id="lds3-of-ak"></a>

## LDS3_OF_AK

*Source: [`Content/TransientModels_HTML/Load Relay LDS3_OF_AK.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relay LDS3_OF_AK.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Over frequency Frequency Relay Model

**Parameters:**

|                      |                               |
| -------------------- | ----------------------------- |
| Transfer Trip Object | Transfer Trip Object          |
| SC                   | Shed Shunts                   |
| f1 to f5             | Frequency Load Shedding Point |
| t1 to t5             | Pickup Time                   |
| tb1 to tb5           | Breaker Time                  |
| frac1 to frac5       | Fraction of Load to Shed      |

---

<a id="lds4"></a>

## LDS4

*Source: [`Content/TransientModels_HTML/Load Relays LDS4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LDS4.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Underfrequency Load Shedding Model with Transfer Trip LDS4 and Inhibitor

Model supported by PowerWorld

**Parameters:**

ObjectFieldSummary

Field Name Description

|                      |                                                              |
| -------------------- | ------------------------------------------------------------ |
| Transfer Trip Object | Transfer Trip Object                                         |
| SC                   | Shed Shunts                                                  |
| f1 to f5             | Frequency Load Shedding Point                                |
| t1 to t5             | Pickup Time                                                  |
| tb1 to tb5           | Breaker Time                                                 |
| frac1 to frac5       | Fraction of Load to Shed                                     |
| ttb                  | Breaker Time                                                 |
| Vthresh              | Voltage Threshold to inhibit relay behavior by Tv time delay |
| Tv                   | Inhibit relay behavior time delay                            |

---

<a id="ldsh"></a>

## LDSH

*Source: [`Content/TransientModels_HTML/Load Relays LDSH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LDSH.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Underfrequency Load Shedding Model LDSH

Model supported by PSSE

**Parameters:**

|                |                               |
| -------------- | ----------------------------- |
| f1 to f3       | Frequency load shedding point |
| t1 to t3       | Pickup time                   |
| frac1 to frac3 | Fraction of load to shed      |
| tb             | Breaker time                  |

---

<a id="ldst"></a>

## LDST

*Source: [`Content/TransientModels_HTML/Load Relays LDST.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LDST.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Time Underfrequency Load Shedding Model LDST

Model supported by PSSE

**Parameters:**

|          |                               |
| -------- | ----------------------------- |
| f1 to f4 | Frequency load shedding point |
| z1 to z4 | Nominal operating time        |
| tb       | Breaker time                  |
| frac     | Fraction of load to shed      |
| freset   | Reset frequency               |
| tres     | Resetting time                |

---

<a id="lsdt1"></a>

## LSDT1

*Source: [`Content/TransientModels_HTML/Load Relays LSDT1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LSDT1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT1 0001](images/Load_Relays_LSDT1_0001.svg)

**Parameters:**

|                |                                |
| -------------- | ------------------------------ |
| Tfilter        | Input transducer time constant |
| tres           | Resetting time                 |
| f1 to f3       | Frequency load shedding point  |
| t1 to t3       | Pickup time                    |
| tb1 to tb3     | Breaker time                   |
| frac1 to frac3 | Fraction of load to shed       |

---

<a id="lsdt2"></a>

## LSDT2

*Source: [`Content/TransientModels_HTML/Load Relays LSDT2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LSDT2.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT2 0001](images/Load_Relays_LSDT2_0001.svg)

**Parameters:**

|                |                                               |
| -------------- | --------------------------------------------- |
| Rem Bus        | Remote Bus                                    |
| Voltage Mode   | Voltage mode: 0 for deviation; 1 for absolute |
| Tfilter        | Input transducer time constant                |
| tres           | Resetting time                                |
| v1 to v3       | Voltage load shedding point                   |
| t1 to t3       | Pickup time                                   |
| tb1 to tb3     | Breaker time                                  |
| frac1 to frac3 | Fraction of load to shed                      |

---

<a id="lsdt3"></a>

## LSDT3

*Source: [`Content/TransientModels_HTML/Load Relay LSDT3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relay LSDT3.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT3 0001](images/Load_Relays_LSDT3_0001.svg)

**Parameters:**

|                        |                                               |
| ---------------------- | --------------------------------------------- |
| Rem Bus                | Remote Bus                                    |
| Mode                   | Voltage mode: 0 for deviation; 1 for absolute |
| Tfilter                | Input transducer time constant                |
| V1 to V3               | Voltage load shedding point (p.u.)            |
| T1 to T3               | Pickup time (sec.)                            |
| Tcb1 to Tcb3           | Breaker time (sec.)                           |
| sv1 to sv3             | Fraction of load to shed                      |
| vreset1a to vreset\_3a | First reset voltage (p.u.)                    |
| treset1a to treset\_3a | First reset time delay (sec.)                 |
| vreset1b to vreset\_3b | Second reset voltage(p.u.)                    |
| treset1b to treset\_3b | Second reset time delay (sec.)                |

---

<a id="lsdt3a"></a>

## LSDT3A

*Source: [`Content/TransientModels_HTML/Load Relay LSDT3A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relay LSDT3A.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT3A 0001](images/Load_Relays_LSDT3A_0001.svg)

**Parameters:**

|                        |                                               |
| ---------------------- | --------------------------------------------- |
| Rem Bus                | Remote Bus                                    |
| Mode                   | Voltage mode: 0 for deviation; 1 for absolute |
| Tfilter                | Input transducer time constant                |
| V1pickup               | Voltage pickup value which timer start        |
| V1 to V3               | Voltage setpoint value(p.u.)                  |
| T1 to T3               | Pickup time (sec.)                            |
| Tcb1 to Tcb3           | Breaker time (sec.)                           |
| sv1 to sv3             | Fraction of load to shed                      |
| vreset1a to vreset\_3a | First reset voltage (p.u.)                    |
| treset1a to treset\_3a | First reset time delay (sec.)                 |
| vreset1b to vreset\_3b | Second reset voltage(p.u.)                    |
| treset1b to treset\_3b | Second reset time delay (sec.)                |

---

<a id="lsdt7"></a>

## LSDT7

*Source: [`Content/TransientModels_HTML/Load Relay LSDT7.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relay LSDT7.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Definite-time Underfrequency Load Shedding Relay Model LSDT7

Have similar parameters as [LSDT8](#lsdt8) relay.

**Parameters:**

|                               |                                  |
| ----------------------------- | -------------------------------- |
| Tfilter                       | Input transducer time constant   |
| Tres; or Treset               | Resetting time                   |
| f1 to f3                      | Frequency load shedding point    |
| t1 to t3                      | Pickup time                      |
| tcb1 to tcb3                  | Breaker time                     |
| frac1 to frac3; or sf1 to sf3 | Fraction of load to shed         |
| df1 to df3                    | Rate of frequency shedding point |

---

<a id="lsdt8"></a>

## LSDT8

*Source: [`Content/TransientModels_HTML/Load Relays LSDT8.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LSDT8.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT8 0001](images/Load_Relays_LSDT8_0001.svg)

**Parameters:**

|                               |                                  |
| ----------------------------- | -------------------------------- |
| Tfilter                       | Input transducer time constant   |
| Tres; or Treset               | Resetting time                   |
| f1 to f3                      | Frequency load shedding point    |
| t1 to t3                      | Pickup time                      |
| tcb1 to tcb3                  | Breaker time                     |
| frac1 to frac3; or sf1 to sf3 | Fraction of load to shed         |
| df1 to df3                    | Rate of frequency shedding point |

---

<a id="lsdt9"></a>

## LSDT9

*Source: [`Content/TransientModels_HTML/Load Relays LSDT9.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LSDT9.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LSDT9 0001](images/Load_Relays_LSDT9_0001.svg)

**Parameters:**

|                |                                |
| -------------- | ------------------------------ |
| Tfilter        | Input transducer time constant |
| tres           | Resetting time                 |
| f1 to f9       | Frequency load shedding point  |
| t1 to t9       | Pickup time                    |
| tcb1 to tcb9   | Breaker time                   |
| frac1 to frac9 | Fraction of load to shed       |

---

<a id="lrdt9"></a>

## LRDT9

*Source: [`Content/TransientModels_HTML/Load Relays LRDT9.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LRDT9.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Load Relays LRDT9 0001](images/Load_Relays_LRDT9_0001.svg)

**Parameters:**

|                |                                |
| -------------- | ------------------------------ |
| Tfilter        | Input transducer time constant |
| tres           | Resetting time                 |
| f1 to f9       | Frequency load restoring point |
| t1 to t9       | Pickup time                    |
| tcb1 to tcb9   | Breaker time                   |
| frac1 to frac9 | Fraction of load to restore    |

---

<a id="lvs3"></a>

## LVS3

*Source: [`Content/TransientModels_HTML/Load Relays LVS3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LVS3.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Undervoltage Load Shedding Model with Transfer Trip LVS3

**Parameters:**

|                     |                             |
| ------------------- | --------------------------- |
| FirstTran Trip Obj  | First Transfer Trip Object  |
| SecondTran Trip Obj | First Transfer Trip Object  |
| SC                  | Shed Shunts                 |
| v1 to v5            | Voltage load shedding point |
| t1 to t5            | Pickup time                 |
| tb1 to tb5          | Breaker time                |
| Frac1 to frac5      | Fraction of load to shed    |
| ttb1 to ttb2        | Transfer trip breaker time  |

---

<a id="lvsh"></a>

## LVSH

*Source: [`Content/TransientModels_HTML/Load Relays LVSH.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Load Relays LVSH.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

Undervoltage Load Shedding Model LVSH

**Parameters:**

|                |                             |
| -------------- | --------------------------- |
| v1 to v3       | Voltage load shedding point |
| t1 to t3       | Pickup time                 |
| frac1 to frac3 | Fraction of load to shed    |
| tb             | Breaker time                |
