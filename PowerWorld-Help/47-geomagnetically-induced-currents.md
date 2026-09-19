---
title: "Geomagnetically Induced Currents (GIC)"
part: "Add-Ons"
chapter_file: "47-geomagnetically-induced-currents.md"
topics: 5
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Geomagnetically Induced Currents (GIC)

GIC analysis, time-varying inputs, electric field inputs and GIC results.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (5)**

- [GIC Analysis](#gic-analysis)
- [GIC Analysis Dialog](#gic-analysis-dialog)
- [GIC Analysis Time Varying Input](#gic-analysis-time-varying-input)
- [GIC Analysis Time Varying Electric Field Inputs ](#gic-analysis-time-varying-electric-field-inputs)
- [GIC Analysis Tables and Results](#gic-analysis-tables-and-results)

---

<a id="gic-analysis"></a>

## GIC Analysis

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis.htm)*

**The GIC Analysis tool is only available if you have purchased the GIC add-on to the base Simulator package. [Contact PowerWorld Corporation](52-additional-linked-topics-part1.md#contact-information) for details about ordering the GIC version of Simulator.**

GICs are induced in the electric power grid when coronal mass ejections (CMEs) on the sun send charged particles towards the earth. These particles interact with the Earth’s magnetic field causing what is known as a geomagnetic disturbance (GMD). So changes in the earth’s magnetic field, usually expressed in nT/minute variation, produce electric field variations. These in turn give rise to quasi-dc (frequencies much below 1 Hz) currents in long conducting paths such as pipelines, railways and the high voltage transmission grid.

In PowerWorld Simulator the impact of the magnetic field variation is represented by series dc voltage sources in series with each of the transmission lines. The details of the determination of these voltages in PowerWorld Simulator is discussed later.

How the GICs flow in the electric transmission system depends upon the induced dc voltage in the transmission lines and the resistance of the various system elements. Since the GICs are essentially dc, device reactance plays no role in there determination. Values that impact the GICs include the resistance of the transmission lines, the resistance of the coils of grounded transformers, the resistance of the series windings of auto-transformers (and their common winding if grounded), and the substation grounding resistance. This is illustrated for a simple two bus network in Figure 1. Note that from a GIC perspective the three phases are in parallel. Since the concept of per unit plays no role in GIC determination, resistance values are expressed in Ohms (Ω), conductance in Siemens (S), current is in amps (A), and the dc voltages are given in volts (V).

![GIC Anaysis Two Generator Example](images/GIC_Anaysis_Two_Generator_Example.gif)

Figure 1: Simple GIC Flow in a Two Generator Example

GIC Analysis

In PowerWorld Simulator the primary means for setting the GIC specific fields and viewing the results is through the GIC Analysis Form. This form can be displayed by selecting the Tools ribbon, then clicking on Other (located towards the right side of the ribbon), and on GIC Calculations. Note, for quicker access to this form right click on the GIC Calculations and select Add to Quick Access Toolbar to place it in the Quick Access Toolbar.More info on [GIC Analysis Form here](#gic-analysis-dialog).

---

<a id="gic-analysis-dialog"></a>

## GIC Analysis Dialog

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_Form.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_Form.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

In PowerWorld Simulator the primary means for setting the GIC specific fields and viewing the results is through the GIC Analysis Form. This form can be displayed by selecting the Tools ribbon, then clicking on Other (located towards the right side of the ribbon), and on GIC Calculations. Note, for quicker access to this form right click on the GIC Calculations and select Add to Quick Access Toolbar to place it in the Quick Access Toolbar:

![GIC Analysis SnapShotInput 1000x444](images/GIC_Analysis_SnapShotInput_1000x444.gif)

PowerWorld Simulator allows the GIC calculations to be either directly integrated into the power flow solution, or done separately without solving the power flow. This allows you to calculate the DC GIC currents in a stand-alone environment which is a very fast calculation, without introducing the additional complexity of the impact on the AC system. To include the impact of GIC in the AC system, check the box **Include GIC in Power Flow and Transient Stability**. When checked, anytime the standard PowerWorld Simulator power flow is solved (for example by clicking on the [Solve Power Flow button](02-simulator-ribbon.md#tools-tab-overview) in the Quick Access Toolbar), the DC GIC currents are recalculated, with the corresponding transformer reactive power losses included in the power flow and transient stability solutions. If this box is not checked then any existing GIC solution results are cleared before the power flow is solved.

There are many options with specific objects such as generators, substations, transformers, etc... which must be specified before performing GIC calculations. Convenient tables are available on the [Tables and Results tab](#gic-analysis-tables-and-results) which provide default access to all these fields as well as access to fields showing the GIC calculation results.

Simulator also provides four different **Calculation Modes** which will be discussed shortly, however all modes share a common set of settings used to calculate the Series DC Voltages induced on the lines by the GMD Electric Fields. These Electric Field options are discussed first.

Calculating the Series DC Voltages from Electric Field

PowerWorld currently supports two different electric field models, with the type determined by the entry in the *Electric Field Model Type* radio group. The simplest is the *Uniform* field approach, in which a constant electric field is assumed, with the magnitude given in the *Maximum Electric Field* field in units of either volts/mile or volts/km (selectable in the *Units of Distance*e field). The direction of the field is then specified in a compass angle in degrees, with 0 degrees being north, 90 degree east, etc. the second field approach is the **Non-uniform** field that will be explained below in the *Time Varying Electric Field Inputs*

Additional options are available to restrict lines for which a DC series voltage is calculated. *Minimum Line Length segmentation* specifies the minimum transmission line length for which a DC voltage will be calculated. Any line shorter than this will not include a DC voltage. (Note: Line length is calculated assume a straight line between the from and to substation coordinates.) If you *Calculate Voltages for Equivalent Lines* is not checked, then any equivalent line does not have a DC series voltage calculated.

**Calculation Mode** = *Single Snapshot*

In this mode, user interface is very simple. Using the parameters as described above, the electric field is used to calculate an induced DC voltage in series with each transmission line. Network equations are then calculated for the resulting DC network to calculated DC GIC currents for the entire system.

The GIC values can be calculated separately from the power flow by selecting the **Calculate GIC Values** button. Since this just requires the solution of a linear system, it is quite fast even for large systems. Clicking the *Clear GIC Values* button clears out all the GIC specific results.

**Calculation Mode** = *Time Varying Series Voltage Inputs*

The DC Series Voltages used in the GIC Calculation must be created ahead of time for the Time Varying Inputs mode. This creation is described in the [Time Varying Inputs](#gic-analysis-time-varying-input) help topic.

The *Current Time (Seconds)* is used to determine which set of GMD-induced transmission dc voltage values should be used in the GIC calculations. PowerWorld Simulator models these values for each transmission line using a piecewise linear model, with each point assigned a time value (in seconds). For the power flow the units of time are irrelevant. When the *Calculate GIC on Time Change* box is checked, the GICs are automatically recalculated anytime the *Current Time* value is changed.

**Calculation Mode** = *Time Varying Electric Field Inputs*

This mode recognizes that a storm is unlikely to have a uniform electric field over an entire large scale interconnected grid. It allows specification of time-varying and spatially-varying northward and eastward electric fields. The specification of the electric field characteristics is described in the [Time Varying Electric Field Inputs](#gic-analysis-time-varying-electric-field-inputs) help topic.

**Calculation Mode** = *Spatially Uniform Time-Varying E-Field*

This mode is intended to be used with a reference electric field time series that does not include a spatial component, such as the NERC benchmark or supplemental events described in TPL-007-2.

Some options apply to all Calculation Modes.

**Options\\DC Current Calculation Tab**

> **Minimum Voltage Level to Include in Analysis (kV)**: Specify a voltage below which the DC voltages are not modeled in series with the transmission line regardless of the other input parameters.
> 
> **Automatic Determination of Autotransformer when status is Unknown**: When the Autotransformer status is *Unknown* the current functionality is to assume it is an autotransformer provided (1) it is not a phase shifter, (2) the From and To bus nominal voltage values differ, (3) the turns ratio is no greater than **Maximum Turns Ratio** to 1, and (4) the medium (secondary) nominal voltage is below **Minimum Medium Voltage** kV.
> 
> **If Low Medium, Minimum High Side Winding Voltage (kV) for always GSU**: When the Autotransformer status is *Unknown* and (1) the medium (secondary) nominal voltage is below **Minimum Medium Voltage** kV, (2) a generator is connected to the medium voltage bus, and the high winding bus nominal kV is above this value, then assume the transformer is a GSU. If a winding configuration is *Unknown* for a GSU, then it the high side is assumed Grounded Wye and the medium (generator) side is assumed Delta.
> 
> **Default Trans. Side Config** and **Default Dist. Side Config**: For transformers that serve load, are not autotransformers, are not GSUs, and whose device-level winding configuration is *Unknown* - the assumed winding configuration for the high side and medium side, respectively. These options may also be specified at the Area level. The Area level setting will overload this setting in Areas where it is not set to *Case Default*.
> 
> **Automatic Insertion of Substations for Buses without Substations**: Substations must be defined to properly model the common grounding of all bus neutrals at a substation. If substations do not exist they will be automatically created when performing the GIC DC current calculation according to these options.

**Options\\AC Power Flow Model Tab**

> After calculating the DC GIC currents, when choosing to **Include GIC AC Power Flow**, each transformer will model a constant current Mvar loss that is a determined by multiplying the effective GIC Current by a linear multiplier called the "K Value". The K Value may be user-specified directly by setting the **GIC Model Type** of a transformer to *Linear* and then specifying the transformer's *GIC Model Param* as the appropriate K Value. If the **GIC Model Type** is instead set to *Default*, then Simulator will automatically calculate a K value based on the **Core Type** of the transformer and the various settings on this tab. The values on this tab are expressed based on a 500 kV transformer. The value is then scaled up or down based on the maximum nominal kV value of the transformer. The actual K Value used for a transformer can be found by looking at the transformer table in the Tables and Results section. There is a column there called **GIC Model K Used**.
> 
> If the transformer's default scaling value based on its **Core Type** or voltage level is 0.80 and it is a 345/138 kV transformer, then the K Value used will be 0.8\*345/500 = 0.552. Thus if the transformer has an effective current of 100 Amps, the Mvar losses would be Ieffective \* KValue = 100\*0.552 = 55.2 Mvar.

.

The results are described in the [Table and Results](#gic-analysis-tables-and-results) help topic.

The calculation of sensitivities is described in the [Sensitivity Analysis](52-additional-linked-topics-part1.md#gic-analysis-sensitivity-analysis) help topic.

For the time points of the Non-uniform electric field is described in the [Non-Uniform Field Data](52-additional-linked-topics-part1.md#gic-analysis-non-uniform-field-data) help topic.

The **Validate Input Data for GIC** button will check if any of the lines is longer than 776.5 miles (1/4 wavelength).

>

---

<a id="gic-analysis-time-varying-input"></a>

## GIC Analysis Time Varying Input

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_TimeVaryingInput.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_TimeVaryingInput.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When using the GIC **Calculation mode**of *Time Varying Inputs*, you must first use the Field/Voltage Input tab and create the time points. The Field/Voltage tab is shown as follows.

![GIC Analysis TimeVaryingInput](images/GIC_Analysis_TimeVaryingInput.gif)

To enter a new time point, do the following

1.  Setup the **Voltage Input Parameters** the same as was described for the Single Snapshot in the [GIC Form Options](#gic-analysis-dialog).
2.  Enter a new time in the box **Input at Time (Seconds)**
3.  Click the **Add at Time** button

This will add a new column to the table above which lists each transmission line in the system and columns for each time point. The columns correspond to particular times and include a DC voltage induced in series with the line for the respective time point.

---

<a id="gic-analysis-time-varying-electric-field-inputs"></a>

## GIC Analysis Time Varying Electric Field Inputs 

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_TimeVaryingElectricField.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_TimeVaryingElectricField.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

When using the GIC **Calculation mode**of *Time Varying Electric Field Inputs*, you must first use the Field/Voltage Input tab and create the time points. The Field/Voltage tab is shown as follows.

![GIC Analysis TimeVaryingElectricFieldInput](images/GIC_Analysis_TimeVaryingElectricFieldInput.gif)

To select this option 4 csv files need to be for specified and loaded to create a *Non-uniform* electric field.:

**Coarse Grid File:** This file should contain an origin point (latitude and longitude), grid spacing in units of degrees longitude, and data points for e-field strength and orientation (possibly in rectangular east and north coordinates?)

For the *Fine Grid Files*:

**Location File:** This file should contain a list of latitude and longitude coordinates for which fine grid data is provided. The fine grid has a higher resolution than the coarse grid.

**East Direction Coordinate File:** This file should contain a list of the eastward rectangular component for the e-field at each point listed in the Location File

**North Direction Coordinate File:** This file should contain a list of the northward rectangular component for the e-field at each point listed in the Location File

After loading these files the data can be browse in the [Non-Uniform Field Data.](52-additional-linked-topics-part1.md#gic-analysis-non-uniform-field-data)

---

<a id="gic-analysis-tables-and-results"></a>

## GIC Analysis Tables and Results

*Source: [`Content/MainDocumentation_HTML/GIC_Analysis_TablesResults.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/GIC_Analysis_TablesResults.htm)*

[See Also](https://www.powerworld.com/WebHelpvoid\(0\);)

This section provides a reference explanation for each of the GIC specific fields on the GIC Analysis *Tables and Results:*

![GIC Analysis TableAndResults](images/GIC_Analysis_TableAndResults.gif)

**Areas Tab**

> The Areas page contains the following fields:

> **Area Num, Area Name**: Give the standard identifiers for each area.

> **Ignore GIC Losses**: Indicates whether or not GIC related losses are calculated for the transformers in the area. In large cases when solving the power flow it may be helpful to avoid calculating the GIC related losses for transformers in distant areas.

> **Mvar Losses**: Gives the total GIC related transformer Mvar losses for the area.

**Buses Tab**

> The Buses page contains the following fields:

> **Number, Name, Area Name and Nom kV**: Give the standard identifiers for each bus.

> **PU Volt**: The AC solution per unit voltage.

> **GIC DC Volt**: The GIC DC voltage for the bus.

> **GIC Neutral DC Volt**: The bus’s substation neutral bus voltage.

> **GIC Gen Step-up Conductance Per Phase**: Total of the per phase conductance for all the implicitly modeled generator step-up transformers at the bus. See the Generator Page for details.

> **GIC Gen Step-up Amps to Neutral**: Total of the amps flowing into the neutral for all the implicitly modeled generator step-up transformers at the bus. See the Generator Page for details.

**Generators Tab**

> The Generators page contains the following fields:

> **Number of Bus, Name of Bus, ID**: Give the standard identifiers for each generator.

> **Status, Gen MW**: Status and real power output of the generator.

> **Include Implicit GSU**: Often the generator step-up transformer (GSU) is modeled explicitly in the power flow. For this situation the transformer would appear on the Transformers page and this field should be No. However, sometimes the transformer is not explicitly modeled. This may be indicated by the generator being directly connected to a high voltage bus, or it may be indicated by non-zero entries for the R and X fields in the Generator Step-up Transformer group on the Generator Dialog, Faults page. If this is the cause then the field should be Yes. If unknown then the entry should be Default, in which case an implicit GSU is assumed if either 1) the R or X fields are non-zero, or 2) the generator is connected to a bus with a nominal voltage greater than 30 kV. This implicit generator is assumed to be y-connected on the transmission side, delta on the generator side. If the R value is non-zero the associated per phase conductance is calculated from this value. Otherwise a default value is used. Currently the default value cannot be changed.

> **GIC Step-up Amps to Neutral**: The total amps (all three phases) flowing from the implicitly modeled GSU into the substation neutral.

> **GIC Step-up Conductance Per Phase**: Per phase conductance for the implicitly modeled GSU; zero indicates no transformer.

> **Implicit GSU Mvar Losses**: Total of the Mvar losses associated with the implicitly modeled GSU. Currently this is not implemented, but will be added shortly.

> **Ignore Losses from Implicit GSU**: This field is always disabled to indicate it is not set here. It tells whether the GIC related losses from the implicitly modeled GSU are ignored for the generator’s area.

**GMatrix Tab**

> The GMatrix page shows the entries in the G (conductance) matrix. The entries are for the parallel combination of all three phases.

**Lines Tab**

> The Lines page contains entries for all the transmission lines and transformers in the model. It contains the following fields:

> **From Number, From Name**: Standard identifiers for the From end bus.

> **To Number, To Name**: Standard identifiers for the To end bus.

> **Circuit**: Line two character circuit ID.

> **GIC DC Volt Input**: The GIC DC voltage modeled for the line. This comes from the data on the Create GMD Electric Field Input page. The polarity is the positive terminal is towards the To end.

> **GIC DC Amps Per Phase From**: For a transmission line this is the per phase GIC current in amps flowing into the From end of the line. If this is a transformer then this is the per phase current flowing into the substation neutral unless it is an auto-transformer. For an auto-transformer it is either the series or common winding flow, depending upon whether the From or To bus has the higher nominal voltage.

> **GIC DC Amps Per Phase To**: For a transmission line this is the per phase GIC current in amps flowing into the To end of the line. If this is a transformer then this is the per phase current flowing into the substation neutral unless it is an auto-transformer. For an auto-transformer it is either the series or common winding flow, depending upon whether the From or To bus has the higher nominal voltage.

> **GIC DC Amps Per Phase Max Abs Value**: This is the absolute value of the maximum current flow in the previous two fields. The field is included to make it easy to sort by the maximum current.

> **GIC DC Volt From**: The GIC DC voltage for the From bus.

> **GIC DC Volt To**: The GIC DC voltage for the To bus.

> **GIC Conductance Per Phase**: The per phase conductance for all the transmission lines. The field value is determined from the per unit power flow data. This field is zero for transformers since the winding values are given/entered on the Transformers page.

> **GIC Mvar Losses**: The GIC related reactive power losses for the transformers. Field is blank for transmission lines.

> **Distance Between Substations**: Distance between the From and To bus substations in either km or miles, depending on the value of the Units of Distance field on the Create GMD Electric Field Input page.

> **Compass Angle Between Substations**: Compass angle in degrees pointing from the From bus substation to the To bus substation.

**Substations Tab**

> The Substations page contains entries for all the substations in the model. It contains the following fields:

> **Sub Num, Sub Name, Sub ID**: Standard identifiers for the substation

> **GIC DC Neutral Voltage**: DC voltage of the substation neutral

> **GIC Amps to Neutral**: Total amps flowing into the substation neutral; a negative number is used for current flow out of the neutral into the system.

> **Grounding Resistance**: Substation grounding resistance in Ohms. This is a user input field and should be set if known. If the value is left zero then an approximated value will be used in the computations (see the next field).

> **GIC Used Grounding Resistance**: This is the grounding resistance value in Ohms that was actually used in the GIC calculations. If the Grounding Resistance field is non-zero then that value is used. Otherwise the resistance is approximated, based upon the the voltage of the highest bus in the substation and the number of buses in the substation. The approximation assumes larger, higher voltage substations have a larger footprint and hence a lower resistance.

> **Latitude, Longitude**: Latitude and longitude for the substation. Latitude values in the Northern Hemisphere are entered as positive numbers and those in the Southern Hemisphere as negative values. Longitude values in the Eastern Hemisphere are entered as positive values and those in the Western Hemisphere as negative values.

**Transformers Tab**

> The Transformers page contains entries for all the transformers in the model. It contains the following fields:

> **From Number, From Name**: Standard identifiers for the From end bus of the transformer.

> **To Number, To Name**: Standard identifiers for the To end bus of the transformer.

> **Circuit**: Line two character circuit ID for the transformer.

> **Manually Enter Coil Resistance**: Toggle to allow the transformer’s coil resistance to be set manually (Yes) or estimated based upon the transformer’s series resistance in the power flow (No). Ideally these values should be set manually. However, in a large case this may be impractical. A reasonable approach could be to set the values for key transformers in the area of interest. When this field is set Yes the next two fields are enterable. Otherwise the next two fields are overwritten with the resistance value actually used in the GIC solution.

> **From Side Ohms per Phase**: If the Manually Enter Coil Resistance field is Yes then this field is enterable, and should be set to the per phase coil winding resistance for the From Bus winding. Otherwise the coil resistance is estimated, and this value is overwritten. The value need not be set for coils that are not connected to ground except is should be set for the series winding on an auto-transformer.

> **To Side Ohms per Phase**: If the Manually Enter Coil Resistance field is Yes then this field is enterable, and should be set to the per phase coil winding resistance for the To Bus winding. Otherwise the coil resistance is estimated, and this value is overwritten. The value need not be set for coils that are not connected to ground except is should be set for the series winding on an autotransformer.

> **Is AutoTransformer**: Indicates whether the transformer should be modeled as an autotransformer. Since this is not a standard power flow model parameter, the default value is Unknown. Set to Yes if it is an autotransformer and No if it is not. When the value is *Unknown* the current functionality is to assume it is an autotransformer provided (1) it is not a phase shifter, (2) the From and To bus nominal voltage values differ, (3) the turns ratio is no greater than 4 to 1, and (4) the highest nominal voltage is above 100 kV. Entries (3) and (4) can be modified under the DC Current Calculation Options

> **Assumed to be an AutoTransformer**: Indicates whether the GIC calculations treated the transformer as an autotransformer.

> **Transformer GIC Neutral Amps**: Total amps flowing from the transformer into the substation neutral.

> **GIC Mvar Losses**: Total GIC induced reactive power losses (in Mvar) for the transformer. The following fields describe how this value is calculated.

> **Ignore GIC Losses**: Indicates whether the GIC losses for the transformer are being ignored. Since this is currently set on an area by area basis, the field is disabled here; it is just for informational purposes.

> **Core Type**: Core type of the transformer. This value is only used if the next field, GIC Model Type, is Default. Since the core type is not a standard power flow field the default value is Unknown. Available core types are as follows.
> 
> 1.  Unknown
> 2.  Single Phase
> 3.  Three Phase Shell
> 4.  3-Legged, Three Phase,
> 5.  5-Legged, Three Phase
> 6.  7-Legged, Three Phase
> 7.  Core, Three Phase Generic

> **GIC Model Type**: The GIC Model Type field is used to relate the GIC currents flowing into the transformer coils into reactive power losses. Currently two values are available, either Default or Linear. When the value is set to Linear, the total GIC-related Mvar losses modeled in the power flow are this value times the GIC coil current in amps. A typical range for this field is between 0.3 to 1.5. When the value is Default, a linear model is used with the reactive power losses estimated based on the core type.

> **GIC Model Param**: When the GIC model type is linear, this field is used to determine the transformer reactive power losses based on the GIC current flowing in the transformer coils.

> **GIC Blocked for Transformer Neutral**: When set to Yes has a GIC blocking device which will blocked dc neutral current.
> 
> **GIC Model K Used**: Will show the K Value actually used by the transformer. This will potentially depend on the GIC Model Type, Core Type, GIC Model Param, and the settings on the Options\\AC Power Flow Model settings. See the Options description for more details.
