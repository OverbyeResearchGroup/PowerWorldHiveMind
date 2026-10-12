---
title: "Weather Modelling"
part: "Analysis"
chapter_file: "28-weather.md"
topics: 13
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# Weather Modelling

Weather-related features, weather dependent limits and power flow weather models.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (13)**

- [Weather Related Features](#weather-related-features)
- [Weather Dependent Limits](#weather-dependent-limits)
- [Weather Dependent Limits Dialog](#weather-dependent-limits-dialog)
- [XYCurve, XYCurvePoint, XYCurveX Objects](#xycurve-xycurvepoint-xycurvex-objects)
- [WeatherStation Objects](#weatherstation-objects)
- [Substation assignments to WeatherStation](#substation-assignments-to-weatherstation)
- [Branches assignments to WeatherStation and XYCurve](#branches-assignments-to-weatherstation-and-xycurve)
- [Generator assignments to WeatherStation and XYCurve](#generator-assignments-to-weatherstation-and-xycurve)
- [Load Areva Dynamic Line Ratings (DLR) (*.csv) as Weather Dependent LImits](#load-areva-dynamic-line-ratings-dlr-csv-as-weather-dependent-limits)
- [Weather Related Models and Information Dialog](#weather-related-models-and-information-dialog)
- [WindClass1, WindClass2, WindClass3, WindClass4, WindBasic](#windclass1-windclass2-windclass3-windclass4-windbasic)
- [SolarPVBasic1, SolarPVBasic2](#solarpvbasic1-solarpvbasic2)
- [GenMWMaxMinXYCurve](#genmwmaxminxycurve)

---

<a id="weather-related-features"></a>

## Weather Related Features

*Source: [`Content/MainDocumentation_HTML/Weather_Related_Features.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Related_Features.htm)*

Weather-related features are available in PowerWorld Simulator.

Weather Dependent Limits

The ability add weather-dependent limits was added in Version 23.

The first is more simple feature that can be used to model weather-dependent limits. This feature is enabled for both Branch MVA limits and for generator MWMax and MWMin limits. These are described in detail in the following help topics.

[WeatherStation Objects](#weatherstation-objects)

[Weather Dependent Limits](#weather-dependent-limits)

[Weather Dependent Limits Dialog](#weather-dependent-limits-dialog)

Weather Related Models and Information

Additional features incorporate time-varying weather information more generically with support in the Time-Step Simulation added in Version 23.

These features build on the [WeatherStation object](#weatherstation-objects) concept and then expands to allows you to create Power Flow Weather Models. A "power flow model" will allow you to update something like the maximum MW output of a generator as a function of wind speed.

These features are organized on the [Weather Related Models and Information Dialog](#weather-related-models-and-information-dialog). See that help topic for more information.

---

<a id="weather-dependent-limits"></a>

## Weather Dependent Limits

*Source: [`Content/MainDocumentation_HTML/Weather_Dependent_Limits.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Dependent_Limits.htm)*

The ability add weather-dependent limits was added in Version 23. The [Weather Dependent Limits Dialog](#weather-dependent-limits-dialog) contains tabs for defining the various objects and references between objects making it easy to apply Weather Dependent Limits to the power system model. The relationship between the weather-related objects is described in the image below and this structure is generally described below. For more details follow the links below.

[Load Areva Dynamic Line Ratings (DLR) (\*.csv)](#load-areva-dynamic-line-ratings-dlr-csv-as-weather-dependent-limits)

Ability to load these files was adding starting in the September 15, 2023 patch of Version 23

On the Tools Ribbon Tab in Simulator under the Other Tools, Weather drop-down there is an option to Load Areva Dynamic Line Rating (DLR) (\*.csv). Choose this option to read a CSV file containing DYNELE, SEG, SEGWST, RATING, and WST objects from the CSV. The help topic explains how these objects will create XYCurve, XYCurvePoint, XYCurveX and WeatherStation objects.

[WeatherStation](#weatherstation-objects)

The object [WeatherStation](#weatherstation-objects) is the object that contains information about weather at a particular location. The [WeatherStation](#weatherstation-objects) has a Name to uniquely define it, a latitude and longitude, and various weather input information such as Temperature, DewPoint, CloudCoverPerc, WindSpeed, and Wind Direction. For more information see the [WeatherStation](#weatherstation-objects) help topic.

[XYCurve, XYCurvePoint, and XYCurveX](#xycurve-xycurvepoint-xycurvex-objects)

The objects [XYCurve, XYCurvePoint, and XYCurveX](#xycurve-xycurvepoint-xycurvex-objects) define an XY curve (X being the input value and Y being the output a function of x). The XYCurvePoints are points on a particular XYCurve and the XYCurve is the object that is referenced by Generator and Branch objects. The Branch objects can specify temperature dependent MVA limits (both Normal and Contingency limits), while the Generator objects can specify weather dependent MWMax and MWMin limits (for example wind speed or solar insolation percent). See the following topics for more information on these. The temperature is normally provided to the XYCurve by the WeatherStations objects associated with substation, branch or generator objects, but the temperature can also be provided directly using the XYCurveX objects.

[Substation assignments to WeatherStation](#substation-assignments-to-weatherstation)

[Branches assignments to WeatherStation and XYCurve](#branches-assignments-to-weatherstation-and-xycurve)

[Generator assignments to WeatherStation and XYCurve](#generator-assignments-to-weatherstation-and-xycurve)

These topics explain how to determine limits based on the XYCurve objects and the WeatherStation objects. The Branch and Generator object can show a column which performs a lookup of the present weather-dependent limit. The Branch first must determine which WeatherStation is associated with it to determine the present temperature. This is done either by assigning a WeatherStation to a branch, or the branch will determine will get WeatherStation assigned to the substation. Alternatively, separate XYCurveX objects can be assigned to an XYCurve and the temperature will come from those instead. This temperature is used as the X value applied to the XYCurve and the new limit in MVA is shown as the result of the XYCurve calculation.

![WeatherDependentLimits](images/WeatherDependentLimits.png)

Example Use of Temperature-Dependent MVA Limits for Branch objects

PowerWorld Corporation expects that Temperature-Dependent limits will be used by users as follows. There is more flexibility that this as will be seen below, but our expected use easier to understand. There are 15 limits available with each branch in PowerWorld's data structure. These limits are labels A, B, C, ..., M, N, O (the first 15 characters of the alphabet). With these 15 limits, we expect users will configure All Limit Monitoring settings for branches with temperature-dependent limits will be configured to use the same Rating Set. We expect that will be either A for Normal and B for Contingency, or maybe M for Normal and N for Contingency. The temperature dependent limits will then be copied right into these rating sets directly.

Example Procedure

  - User configures rating sets for branches they are interested in as follows.

      - Rating Sets D, E, F = Spring Seasonal Limits

      - Rating Sets G, H, I = Summer Seasonal Limits

      - Rating Sets J, K, L = Fall Seasonal Limits

      - Rating Sets M, N, O = Winter Seasonal Limits

  - User configures Limit Monitoring Settings to use the remaining unused 3 limits (A, B, C) as the "presently active limits"

      - A = Normal Limits

      - B = Contingency Limit

  - Assume that [WeatherStation](#weatherstation-objects) objects have been configured and populated with the present temperature at each one defined in the field *TempC*.

    These [WeatherStation](#weatherstation-objects) objects have then either been [assigned to a Substation](#substation-assignments-to-weatherstation) or [assigned to Branches](#branches-assignments-to-weatherstation-and-xycurve).

    In addition the Branch objects have had their *[*TemperatureLimitNormalName* and *TemperatureLimitCTGName*](#branches-assignments-to-weatherstation-and-xycurve)* populated with references to [XYCurve objects](#xycurve-xycurvepoint-xycurvex-objects) that represent the MVA limit of the branch as a function of the temperature in Celsius.

      - This means that the branch objects of interest now have a data field called *TemperatureLimitNormal* and *TemperatureLimitCTG* which will perform the lookup of the temperature-dependent MVA limit

  - With this configured, the case can be set to "Use Summer Limits" by doing the following either by using the [**Set All Values to Field** feature of the case information displays](04-model-explorer-and-case-information-part1.md#set-toggle-and-columns-menus) by or via an AUX file script listed below.

      - Push Summer Seasonal Limits into active limits by copying the G and H limits onto the A and B limits. (We are assuming above the G and H represent the Summer Normal and Summer Contingency ratings)

        `SetData(Branch, [LimitMVAA,LimitMVAB],                ["@LimitMVAG","@LimitMVAH"], "FilterNameforMyBranches");`

      - Now branches that have a [WeatherStation](#weatherstation-objects) and [XYCurves](#xycurve-xycurvepoint-xycurvex-objects) appropriately defined can overwrite the A and B limits with these values. This AUX file script or the Set All Values to Field feature is safe to use even for branches that do not have associated WeatherStation and XYCurve objects because for those branches the TemperatureLImitNormal and TemperatureLImitCTG fields <span class="underline">will be blank</span>. Pasting or typing a blank entry into the *LimitMVAA* and *LImitMVAB* fields will just leave those fields as their present numerical value which will be the entries copied from the G and H limits in the previous step.

        `SetData(Branch, [LimitMVAA,LimitMVAB],                ["@TemperatureLimitNormal","@TemperatureLimitCTG"], "FilterNameforMyBranches");`

---

<a id="weather-dependent-limits-dialog"></a>

## Weather Dependent Limits Dialog

*Source: [`Content/MainDocumentation_HTML/Weather_Dependent_Limits_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Dependent_Limits_Dialog.htm)*

The ability add weather-dependent limits was added in Version 23. The Weather Dependent LImits Dialog is available under on the [Tools Ribbon Tab](02-simulator-ribbon.md#tools-tab-overview), on the [Other Tools Ribbon Group](02-simulator-ribbon.md#other-tools-ribbon-group)

The Weather Dependent Limits Dialog groups together the features related to entering [Weather-Dependent Limits](#weather-dependent-limits) and the objects associated with these features. The dialog has the follow tabs.

  - **Weather Station**: This tab provides a place to define [WeatherStations](#weatherstation-objects) objects. A WeatherStation object represents any location at which weather measurements are specified. See the [WeatherStation Objects](#weatherstation-objects) help topic for more information.

  - **XY Curve**: This tab provides a place to define [XYCurve, XYCurvePoints, and XYCurveX](#xycurve-xycurvepoint-xycurvex-objects) which are used to represent the weather-dependent lookup functions such as a temperature-dependent MVA limit of a branch. See the[XYCurve, XYCurvePoints, and XYCurveX](#xycurve-xycurvepoint-xycurvex-objects) for more information

  - **Substation**: This tab provides a list of all substations with [substation weather-related fields](#substation-assignments-to-weatherstation) as default columns

  - **Branch**: This tab provides a list of all substations with [branch weather-related fields](#branches-assignments-to-weatherstation-and-xycurve) as default columns

  - **Generator**: This tab provides a list of all substations with [generator weather-related fields](#generator-assignments-to-weatherstation-and-xycurve) as default columns

Update Branch Limits

See the [Branches assignments to WeatherStation and XYCurve](#branches-assignments-to-weatherstation-and-xycurve) options for more information about important branch fields associated with weather such as the *TemperatureLimitNormal* and *TemperatureLimitCTG* fields and how a branch determines weather values such as temperature from the WeatherStation and Substation objects associated with the branch.

There are 3 options which impact that function of the **Update Branch Limits** button.

**Normal**: Specify which of the 15 MVA limits (A, B, C, ... , M, N, O ) to overwrite with the *TemperatureLimitNormal* value when clicking the **Update Branch Limits** button. A value of "Default" may also be specified which signifies that Simulator will overwrite the rating set (A, B, ... O) that is being used for Normal ratings based on each branch's [limit monitoring setting](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog)s.

**Contingency**: Same as for Normal, but determines which rating set to overwrite with the *TemperatureLImitCTG* value instead

**Precedence**: It is possible based on the **Normal** and **Contingency** options along with the [limit monitoring settings](18-general-tools.md#limit-monitoring-settings-and-limit-violations-dialog) choices that the same rating set (A, B, ... O) will be overwritten by both the *TemperatureLimitNormal* and the *TemperatureLimitCTG*. The precedence says which one is applied second (and thus overwrites the first one).

There is also a script command which performs this update with the following syntax.

`TemperatureLimitsBranchUpdate(RatingSetPrecedence, NormalRatingSet, CTGRatingSet);`

RatingSetPrecedence: is either Normal or CTG. If not specified then Normal is assumed.

NormatRatingSet: If nothing is specified, then Default is assumed. Parameter is specified as either A, B, C, ..., M, N, O or Default as described above. In addition it may be set as "No" to indicate that the normal rating set should not be updated.

CTGRatingset: same as for the NormalRating Set.

Filtering features on the Branch tab

There are some special filtering features available on the Branch tab that allow you to show Branches as follows

**Only Curves Assigned**: Shows only branches for which XYCurves have been assigned and are marked as InUse = YES

**Only Changes**: Shows only branches that will update limits based on the **Update Branch Limits** options

**Only Conflicts**: shows only branches that have a conflict with either the Normal or CTG curve based on the **Update Branch Limits** options

**All**: show all branches

Update Generator Limits

See the [Generator assignments to WeatherStation and XYCurve](#generator-assignments-to-weatherstation-and-xycurve) options for more information about important generator fields associated with weather such as the *WeatherMWMin* and *WeatherMWMax* fields and how a generator determines weather values such as temperature from the WeatherStation and Substation objects associated with the branch.

There are 2 options which impact that function of the **Update Generator Limits** button.

**MW Max**: check this box and when clicking the Update Generator Limits button the value for *WeatherMWMax* will overwrite the generator's MWMax field.

**MW Min**: check this box and when clicking the Update Generator Limits button the value for *WeatherMWMin* will overwrite the generator's MWMin field.

![WeatherDependentLimitsDialog](images/WeatherDependentLimitsDialog.png)

---

<a id="xycurve-xycurvepoint-xycurvex-objects"></a>

## XYCurve, XYCurvePoint, XYCurveX Objects

*Source: [`Content/MainDocumentation_HTML/XYCurveAndXYCurvePoint.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/XYCurveAndXYCurvePoint.htm)*

The ability add XYCurve and XYCurvePoint objects was added in Version 23.

The ability to define XYCurveX objects was added beginning in the September 15, 2023 patch of Version 23.

XYCurve and XYCurvePoint objects are used as part of the [Weather-Dependent Limits](#weather-dependent-limits) which are accessed on the [Weather-Dependent Limits dialog](#weather-dependent-limits-dialog).

A XYCurve and XYCurvePoint objects represents any a generic XYCurve. They represent a function that takes **one** input and provides **one** output.

Normally we expect that objects using an XYCurve will provide the X-axis value to use with the XYCurve and XYCurvePoint objects to perform the lookup function based on the provided X. For example a Branch using weather-dependent MVA limits will provide the temperature in Celsisus as the X-Value itself. The temperature will come from the WeatherStation assigned to branch for example. This normal behavior can be overridden by creating XYCurveX objects and assigning them to the XYCurve. The XYCurveX object will then refer to an Object and ObjectField which provides the X-Value to the XYCurve. For the purposes of weather-related limit we would expect that Object to be a [WeatherStation](#weatherstation-objects) and the ObjectField to be a temperature, wind speed, or other weather-related value.

XYCurve Objects

XYCurve objects have the following 3 fields, and then also store a list of XYCurvePoint objects associated with them which are also described below.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Input</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Name of the curve. This is the unique identifier (Key Field) for the XYCurve.</p></td>
</tr>
<tr class="odd">
<td><p>Information</p></td>
<td><p>String</p></td>
<td><p>User Input</p></td>
<td><p>Informational string about equipment that results in this curve being used. It is possible that one device in the power system model will have multiple curves associated with it. For example: a line may also have current transformer associated with it that has a different lower rating than the line.</p></td>
</tr>
<tr class="even">
<td><p>Enabled</p></td>
<td><p>String</p></td>
<td><p>User</p>
<p>Input</p></td>
<td><p>Set to either YES or NO. If set to NO then any calls to this XYCurve by other objects will not be used and thus ignored. For example, a Branch that is configured to us an XYCurve with Enabled=NO will not use the weather-dependent limit.</p></td>
</tr>
<tr class="odd">
<td><p>XType</p>
<p> </p>
<p>Option added beginning in the September 15, 2023 patch of Version 23.</p></td>
<td><p>Discrete Options</p>
<p>Ignore</p>
<p>Max</p>
<p>Min</p>
<p>EvalMax</p>
<p>EvalMin</p></td>
<td><p>User</p>
<p>Input</p></td>
<td><p>Specifies how to interpret multiple XYCurveX objects associated with this XYCurve.</p>
<p><em>Ignore</em> means that XYCurveX objects are ignored and the XYCurve will use whatever XValue is provided from the calling object (such as a Branch providing a temperature).</p>
<p><em>Max or Min</em> will take the maximum or minimum of all the XCurveX values.</p>
<p><em>EvalMax or EvalMin</em> will evalute the XYCurve for all XCurveX values and then return either the maximum or minimum of those evaluations</p></td>
</tr>
<tr class="even">
<td><p>IntermediateType</p></td>
<td><p>Discrete Options</p>
<p>AtOrAbove</p>
<p>AtOrBelow</p>
<p>Closest</p>
<p>Interpolate</p></td>
<td><p>User Input</p></td>
<td><p>Specifies how to handle any lookup when the temperature falls between X values. See the image below for</p>
<p><em>AtOrAbove</em> means the limits are at or above the specified temperature</p>
<p><em>AtOrBelow</em> means the limits are at or below the specified temperature</p>
<p><em>Closest</em> means use the limit based on the closest temperature</p>
<p><em>Interpolate</em> means we will linearly interpolate between points</p>
<p>These options are depicted in the next image. The XYCurvePoints are represented by the black dots in the image below.</p>
<p><img src="images/XYCurve_IntermediateType.png" alt="XYCurve IntermediateType" /></p></td>
</tr>
</tbody>
</table>

XYCurvePoint Objects

Each XYCurvePoint object represents one point on the XYCurve. The XYCurvePoint object has the following fields.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Input</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Name of the XYCurve to which this point belongs.</p></td>
</tr>
<tr class="odd">
<td><p>X</p></td>
<td><p>Single Float</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Single float storing temperature (tolerance would be 0.01. Thus 10.223 and 10.218 are both considered to be 10.22 degrees). The unit of this field will depend on what object is using the curve, so the curve itself does not know the units. This is assumed to be Celsius for temperature dependent curves.</p></td>
</tr>
<tr class="even">
<td><p>Info1, Info2, Info3</p>
<p>Info4, Info5</p></td>
<td><p>String</p></td>
<td><p>User Input</p></td>
<td><p>Informational strings about device that results in this value being used. There may be processing done outside of PowerWorld that creates a curve where each point in the curve represents a different piece of equipment. This may be done instead of defining a separate curve for each piece of equipment</p></td>
</tr>
<tr class="odd">
<td><p>Y</p></td>
<td><p>Single Float</p></td>
<td><p>User Input</p></td>
<td><p>Function Output at this temperature. The unit will depend on what object is using this curve, so the curve itself does not know the units. This is assumed to be MVA for temperature dependent Branch rating curves.</p></td>
</tr>
</tbody>
</table>

XYCurveX Objects added beginning in the September 15, 2023 patch of Version 23.

Each XYCurveX object represents one possible X-Value that would be provided to its XYCurve to perform a lookup.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Input</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Name of the XYCurve to which this point belongs.</p></td>
</tr>
<tr class="odd">
<td><p>Object</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Object from which the XYCurveX obtains its XValue. The string is of the same format as the ObjectID field used in AUX files starting with an ObjectType following by either primary key fields, secondary key fields or a label identifier.</p></td>
</tr>
<tr class="even">
<td><p>ObjectField</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Key Field Identifier</p></td>
<td><p>Variablename from which the XYCurve obtains its XValue from its Object.</p></td>
</tr>
</tbody>
</table>

---

<a id="weatherstation-objects"></a>

## WeatherStation Objects

*Source: [`Content/MainDocumentation_HTML/Weather_Station_Objects.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Station_Objects.htm)*

The ability add weather-dependent limits was added in Version 23

WeatherStation objects are used as part of the [Weather-Dependent Limits](#weather-dependent-limits) which are accessed on the [Weather-Dependent Limits dialog](#weather-dependent-limits-dialog).

They are also used as part of the [Weather Related Models and Information Dialog](#weather-related-models-and-information-dialog) which can be used in conjunction with the Time Step Simulation Tool.

A WeatherStation object represents any location at which weather measurements are specified. The following are examples of concepts that the WeatherStation object may represent.

1.  A weather recording station

2.  The output of some special weather forecast software that you are using

3.  A National Oceanic and Atmospheric Administration (NOAA) weather station location in North America

4.  An airport where you have weather measurements

WeatherStation objects have the following input fields

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Name</p></td>
<td><p>String</p>
<p>(KEY field)</p></td>
<td><p>Name of the WeatherStation. This is the unique identifier (Key Field) for the WeatherStation</p></td>
</tr>
<tr class="odd">
<td><p>Enabled</p></td>
<td><p>Boolean</p></td>
<td><p>Set to YES to indicate that the WeatherStation should be used. When this is set to NO, all numeric fields for the WeatherStation will be disabled and no limit calculations can be based on this WeatherStation.</p></td>
</tr>
<tr class="even">
<td><p>ObservationTime</p></td>
<td><p>String</p></td>
<td><p>This is the date time of when the latest observations were recorded. It is optional and when blank indicates no time is known.</p></td>
</tr>
<tr class="odd">
<td><p>Longitude</p></td>
<td><p>Double Float</p></td>
<td><p>Longitude Coordinate. An entry of blank may be given in which case there is not a valid value for this quantity. This value is stored as a double-precision floating point number and thus has about 15 significant digits instead of 7 digits for the single-precision values.</p></td>
</tr>
<tr class="even">
<td><p>Latitude</p></td>
<td><p>Double Float</p></td>
<td><p>Latitude Coordinate. An entry of blank may be given in which case there is not a valid value for this quantity. This value is stored as a double-precision floating point number and thus has about 15 significant digits instead of 7 digits for the single-precision values.</p></td>
</tr>
<tr class="odd">
<td><p>ElevationM</p>
<p>ElevationFt</p></td>
<td><p>Single Float</p></td>
<td><p>Elevation of WeatherStation in meters or feet. We only store a single value internally and so the final one read will be kept. An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
<tr class="even">
<td><p>TempF</p>
<p>TempC</p></td>
<td><p>Single Float</p></td>
<td><p>Temperature in Fahrenheit or Celsius. We only store a single value internally and so the final one read will be kept. An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
<tr class="odd">
<td><p>DewPointF</p>
<p>DewPointC</p></td>
<td><p>Single Float</p></td>
<td><p>DewPoint in Fahrenheit or Celsius. We only store a single value internally and so the final one read will be kept. An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
<tr class="even">
<td><p>CloudCoverPerc</p></td>
<td><p>Single Float</p></td>
<td><p>Cloud Cover Percentage (between 0 and 100). An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
<tr class="odd">
<td><p>WindSpeedmph</p>
<p>WindSpeedKnots</p>
<p>WindSpeedMsec</p>
<p>WindSpeedkmph</p></td>
<td><p>Single Float</p></td>
<td><p>Wind Speed in miles per hour, knots, meters per second, or kilometers per hour. We only store a single value internally and so the final one read will be kept. An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
<tr class="even">
<td><p>WindDirection</p></td>
<td><p>Single Float</p></td>
<td><p>Wind Direction in degrees. (90 = From East; 180 = From South; 270 = From West; 360 = From North. Only show 0 if wind speed also 0.)</p>
<p>An entry of blank means there is not a valid value for this quantity.</p></td>
</tr>
</tbody>
</table>

Additional fields that are calculated from other Weather Values (so they can not be edited)

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>Humidity</p></td>
<td><p>Single Float</p></td>
<td><p>Humidity is calculated as ratio of exponential function of DewPoint and Temperature</p></td>
</tr>
<tr class="odd">
<td><p>WindChillF</p>
<p>WindChillC</p></td>
<td><p>Single Float</p></td>
<td><p>Wind Chill is calculated as a function of temperature and wind speed.</p></td>
</tr>
<tr class="even">
<td><p>HeatIndexF</p>
<p>HeatIndexC</p>
<p> </p></td>
<td><p>Single Float</p></td>
<td><p>Heat Index is calculated as a function of temperature and humidity</p></td>
</tr>
</tbody>
</table>

Additional fields that are calculated from latitude, longitude, time of day and other fields

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>SolarElevation</p></td>
<td><p>Single Float</p></td>
<td><p>Sun Elevation (Deg). Depends on the time of day and the Latitude and Longitude of the WeatherStation</p></td>
</tr>
<tr class="odd">
<td><p>SolarAzimuth</p></td>
<td><p>Single Float</p></td>
<td><p>Sun Azimuth in compass degrees with zero due north, 90 due east, 180 due south and 270 due west. This depends on the time of day, latitude and longitude.</p></td>
</tr>
<tr class="even">
<td><p>AtmosphericTransmittance</p></td>
<td><p>Single Float</p></td>
<td><p>Atmospheric transmittance with 1 for the sun directly overhead, and lower values as the sun goes through more of the atmosphere. This depends on the time of day, latitude and longitude.</p></td>
</tr>
<tr class="odd">
<td><p>InsolationPerc</p></td>
<td><p>Single Float</p></td>
<td><p>Estimate insolation percentage</p>
<p>(100-CloudCoverPerc)*AtmosphericTransmittance</p></td>
</tr>
</tbody>
</table>

More Optional Identifying Information for the WeatherStation

|             |         |                                                                                                                                     |
| ----------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Field       | Type    | Type                                                                                                                                |
| ICAO        | String  | This is 4-character code assigned by the International Civil Aviation Administration. The last 3 digits are often the airport code. |
| GHCN        | String  | Global Historical Climatology Network identifier                                                                                    |
| WMO         | Integer | This is 5-digit numeric code to identify a weather station assigned by the World Meteorological Organization                        |
| CountryCode | String  | Two character country code; e.g., US, CA, etc.                                                                                      |
| Region      | String  | For the US and Canada this is the two character state or providence code                                                            |
| Subregion   | String  | County name for some US states                                                                                                      |
| PlaceName   | String  | Extra identifier in various weather resources                                                                                       |
| StationName | String  | Extra identifier in various weather resources                                                                                       |

---

<a id="substation-assignments-to-weatherstation"></a>

## Substation assignments to WeatherStation

*Source: [`Content/MainDocumentation_HTML/Weather_AssignSubstationToWeather.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_AssignSubstationToWeather.htm)*

The ability add weather-dependent limits was added in Version 23

Substation objects have various field associated with them which are used as part of the [Weather-Dependent Limits](#weather-dependent-limits) which are accessed on the [Weather-Dependent Limits dialog](#weather-dependent-limits-dialog).

There also similar weather-related fields for [Generator](#generator-assignments-to-weatherstation-and-xycurve) and [Branch](#) objects.

Substation Weather-Related Fields

Each Substation can be assigned to a [WeatherStation objec](#weatherstation-objects)t directly by entering the Name of a [WeatherStation object](#weatherstation-objects) in the substation field with the name **WeatherStation**. This designation will then be used when Branch and Generator objects are not assigned to their own WeatherStation. The default behavior will be that the link between weather and the power system occurs at the substation object in the data structure. The substation object then has a large number of fields that perform lookups into the assigned WeatherStation object to show the associated weather information for the substation. These are described in the following table.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>WeatherStation</p></td>
<td><p>String</p></td>
<td><p>WeatherStation object to which the user has assigned the substation</p></td>
</tr>
<tr class="odd">
<td><p>WeatherStationClosestName</p></td>
<td><p>String</p></td>
<td><p>This field is calculated by doing a Delaunay Triangulation of the WeatherStations objects with latitude/longitude coordinates in the case. This then shows the name of the closest WeatherStation based on this calculation. A user could choose to copy this designation into the user-assigned WeatherStation field.</p></td>
</tr>
<tr class="even">
<td><p>WeatherStationDistanceMILE</p></td>
<td><p>Single Float</p></td>
<td><p>Distance in miles from substation to the WeatherStationClosestName</p></td>
</tr>
<tr class="odd">
<td><p>WeatherStationDistanceKM</p></td>
<td><p>Single Float</p></td>
<td><p>Distance in km from substation to the WeatherStationClosestName</p></td>
</tr>
<tr class="even">
<td><p>AtmosphericTransmittance</p></td>
<td><p>Single Float</p></td>
<td><p>Gives an estimate of the atmospheric transmittance with 1.000 for the sun directly overhead, decreasing as it approaches the horizon; 0.000 if below the horizon. This is calculated from the latitude, longitude, date, and time of day.</p></td>
</tr>
<tr class="odd">
<td><p>SolarAzimuth</p></td>
<td><p>Single Float</p></td>
<td><p>Gives the sun's azimuth using the compass, with 0 due north, 90 degrees due east, 180 due south and 270 due west. This is calculated from the latitude, longitude, date, and time of day.</p></td>
</tr>
<tr class="even">
<td><p>SolarElevation</p></td>
<td><p>Single Float</p></td>
<td><p>Gives the sun's elevation about the horizon, with 90 degrees straight overhead. This is calculated from the latitude, longitude, date, and time of day.</p></td>
</tr>
<tr class="odd">
<td><p>WS_TempF</p>
<p>WS_TempC</p>
<p>WS_DewPointF</p>
<p>WS_DewPointC</p>
<p>WS_CloudCoverPerc</p>
<p>WS_WindSpeedmph</p>
<p>WS_WindSpeedKnots</p>
<p>WS_WindSpeedMsec</p>
<p>WS_WindSpeedkmph</p>
<p>WS_WindDirection</p>
<p>WS_InsolationPerc</p></td>
<td><p>Single Float</p></td>
<td><p>See the fields available for the <a href="#weatherstation-objects">WeatherStation object</a> for more information.</p>
<p> </p>
<p><em>Special feature ONLY for Substation objects: The various numeric fields with the substation such as WM_TempF, WM_CloudCoverPerc etc. can be edited in the substation case information displays. When editing these values the WeatherStation specified in the WeatherStation field will have the respective weather value changed. If the substation is not presently assigned to a WeatherStation, then the WM_* value will be blank, but a value can still be assigned to the substation. When editing the numeric value that is blank, Simulator will automatically create a new WeatherStation with a name equal to the name of the substation, and the value of the WeatherStation will be set to the entered value.</em></p></td>
</tr>
<tr class="even">
<td><p>WS_Humidity</p>
<p>WS_WindChillF</p>
<p>WS_WindChillC</p>
<p>WS_HeatIndexF</p>
<p>WS_HeatIndexC</p></td>
<td><p>Single Float</p></td>
<td><p>See the fields available for the <a href="#weatherstation-objects">WeatherStation object</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p>WS_Enabled</p>
<p>WS_ObservationTime</p></td>
<td><p>String</p></td>
<td><p>See the fields available for the <a href="#weatherstation-objects">WeatherStation object</a> for more information.</p></td>
</tr>
</tbody>
</table>

---

<a id="branches-assignments-to-weatherstation-and-xycurve"></a>

## Branches assignments to WeatherStation and XYCurve

*Source: [`Content/MainDocumentation_HTML/Weather_AssignBranchToWeather.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_AssignBranchToWeather.htm)*

The ability add weather-dependent limits was added in Version 23.

Branch objects have various field associated with them which are used as part of the [Weather-Dependent Limits](#weather-dependent-limits) which are accessed on the [Weather-Dependent Limits dialog](#weather-dependent-limits-dialog).

There also similar weather-related fields for [Substation](#substation-assignments-to-weatherstation) and [Generator](#generator-assignments-to-weatherstation-and-xycurve) objects.

Branch Weather-Related Fields

Each Branch can be assigned to a [WeatherStation objec](#weatherstation-objects)t directly by the user by entering the Name of a [WeatherStation object](#weatherstation-objects) in the branch field WeatherStation. This WeatherStation will then be used for all weather related values for the Branch. If the WeatherStation is not specified for a branch, then the branch will look at the terminal bus substations and make appropriate calculations of an average, max, or vector sum average. The branch object has a fields that perform lookups into the assigned WeatherStation object (or terminal substations WeatherStation objects) to show the associated weather information for the branch.

The branch object also has fields for specifying a list of [XYCurves](#xycurve-xycurvepoint-xycurvex-objects) that describe the temperature-dependent MVA limits for the branch. See the topic [XYCurve, XYCurvePoint, XYCurveX Objects](#xycurve-xycurvepoint-xycurvex-objects) for more details on how to define XYCurves. There are entries for specifying XYCurves for use for normal limits and also an entry for a list of XYCurves for post-contingency limits. Finally there are YES/NO fields to designate whether these XYCurves should even be used.

These fields are described in the following table.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>WeatherStation</p></td>
<td><p>String</p>
<p><em>Enterable</em></p></td>
<td><p>WeatherStation object to which the user has assigned the substation</p></td>
</tr>
<tr class="odd">
<td><p>TemperatureLimitNormalUse</p>
<p>TemperatureLimitCTGUse</p></td>
<td><p>String</p>
<p><em>Enterable</em></p></td>
<td><p>YES or NO. Specify YES to use the TemperatureLimitNormal XYCurves</p>
<p>(or TemperatureLImitCTG XYCurves)</p></td>
</tr>
<tr class="even">
<td><p>TemperatureLimitNormalName</p>
<p>TemperatureLimitCTGName</p></td>
<td><p>String</p>
<p><em>Enterable</em></p></td>
<td><p>A comma-delimited list of names of XYCurves that will impact this Branch. Multiple curves are allowed because there may be multiple devices that impact the limit of this branch. For example, a Current Transformer (CT) may be on a particular branch that imposes a different limit on the line as compared to the conductor limit.</p>
<p>The limit that is calculated by PowerWorld Simulator will be the minimum limit across all these curves. The x value of the curves is assumed to be temperature WS_TempC (Celsius temperature).</p>
<p>The TemperatureLimitNormalName refers to XYCurves that will be used to determine the TemperatureLImitNormal result, while the TermperatureLimitCTG are XYCurves for the TemperatureLImitCTG result.</p></td>
</tr>
<tr class="odd">
<td><p>TemperatureLimitNormal</p></td>
<td><p>Single Float</p></td>
<td><p>Uses the WS_TempC value and looks up the MVA limits based on the list of Limit XYCurves specified in TemperatureLimitNormalName field.</p>
<p>If no curves are specified, then value is blank</p>
<p>If 1 curve is specified, then value returns the lookup for that curve using WS_TempC</p>
<p>If multiple curves, then value performs the lookup on all curves using WS_TempC and then returns the <strong>minimum</strong> value across all curves.</p></td>
</tr>
<tr class="even">
<td><p>TemperatureLimitCTG</p></td>
<td><p>Single Float</p></td>
<td><p>Same as TemperatureLimitNormal, but uses the TemperatureLimitCTGName XYCurves instead.</p></td>
</tr>
<tr class="odd">
<td><p>WS_TempF</p>
<p>WS_TempC</p>
<p>WS_DewPointF</p>
<p>WS_DewPointC</p>
<p>WS_Humidity</p>
<p>WS_WindChillF</p>
<p>WS_WindChillC</p>
<p>WS_HeatIndexF</p>
<p>WS_HeatIndexC</p>
<p>WS_InsolationPerc</p></td>
<td><p>Single Float</p></td>
<td><p>Various values taken from a WeatherStation</p>
<p>If a WeatherStation is specified then this weather station's value is used. If a WeatherStation is not specified, then the terminal bus substations will be checked and if both values are valid then the <strong>maximum</strong> value is returned, otherwise if only one is valid then this valid value is returned.</p></td>
</tr>
<tr class="even">
<td><p>WS_CloudCoverPerc</p></td>
<td><p>Single Float</p></td>
<td><p>Cloud Cover Percentage (between 0 and 100). An entry of blank means there is not a valid value for this quantity.</p>
<p>If a WeatherStation is specified then this weather station's value is used. If a WeatherStation is not specified, then the terminal bus substations will be checked and if both values are valid then the <strong>average</strong> value is returned, otherwise if only one is valid then this valid value is returned.</p></td>
</tr>
<tr class="odd">
<td><p>WS_WindSpeedmph</p>
<p>WS_WindSpeedKnots</p>
<p>WS_WindSpeedMsec</p>
<p>WS_WindSpeedkmph</p></td>
<td><p>Single Float</p></td>
<td><p>Wind Speed in miles per hour, knots, meters per second, or kilometers per hour. We only store a single value internally and so the final one read will be kept. An entry of blank means there is not a valid value for this quantity.</p>
<p>If a WeatherStation is specified for the branch then this weather station's value is used. If a WeatherStation is not specified, then the terminal bus substations will be checked and if both values are valid then the <strong>vector summation</strong> of values is done and the resulting magnitude divided by 2 is returned, otherwise if only one is valid then this valid value is returned.</p></td>
</tr>
<tr class="even">
<td><p>WS_WindDirection</p></td>
<td><p>Single Float</p></td>
<td><p>Wind Direction in degrees. (90 = From East; 180 = From South; 270 = From West; 360 = From North. Only show 0 if wind speed also 0.) An entry of blank means there is not a valid value for this quantity.</p>
<p>If a WeatherStation is specified for the branch then this weather station's value is used. If a WeatherStation is not specified, then the terminal bus substations will be checked and if both values are valid then the <strong>vector summation</strong> of values is done and the resulting vector direction is returned, otherwise if only one is valid then this valid value is returned.</p></td>
</tr>
</tbody>
</table>

---

<a id="generator-assignments-to-weatherstation-and-xycurve"></a>

## Generator assignments to WeatherStation and XYCurve

*Source: [`Content/MainDocumentation_HTML/Weather_AssignGeneratorToWeather.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_AssignGeneratorToWeather.htm)*

The ability add weather-dependent limits was added in Version 23.

Generator objects have various field associated with them which are used as part of the [Weather-Dependent Limits](#weather-dependent-limits) which are accessed on the [Weather-Dependent Limits dialog](#weather-dependent-limits-dialog).

There also similar weather-related fields for [Substation](#substation-assignments-to-weatherstation) and [Branch](#) objects.

Generator Weather-Related Fields

Each Generator can be assigned to a [WeatherStation objec](#weatherstation-objects)t directly by entering the Name of a [WeatherStation object](#weatherstation-objects) in the branch field WeatherStation. Setting the WeatherStation field to a blank string will remove any existing WeatherStation designation. This WeatherStation will be used for all weather related values for the Generator. If the WeatherStation is not specified for a generator, then the generator will look at the terminal bus substations WeatherStation instead.

The generator object also has fields to specify a list of [XYCurves](#xycurve-xycurvepoint-xycurvex-objects) that describe the temperature-dependent MW limits. See the topic [XYCurve, XYCurvePoint, XYCurveX Objects](#xycurve-xycurvepoint-xycurvex-objects) for more details on how to define XYCurves. There are entries for specifying XYCurves for use for MWMax limits and also an entry for a list of XYCurves for MWMin limits. There are YES/NO fields to designate whether these XYCurves should be used. Finally, for generators there is also a field to specify which field to use as the x-value when performing lookups using the XYCurves. For example, for a wind power plant, using WindSpeedMsec (meters per second) may make the most sense, while for a solar power plant the InsolationPerc may be more useful.

These fields are described in the following table.

<table>
<tbody>
<tr class="odd">
<td><p>Field</p></td>
<td><p>Type</p></td>
<td><p>Type</p></td>
</tr>
<tr class="even">
<td><p>WeatherStation</p></td>
<td><p>String</p></td>
<td><p>WeatherStation object to which the user has assigned the substation</p></td>
</tr>
<tr class="odd">
<td><p>WeatherMWMaxUse</p></td>
<td><p>String</p></td>
<td><p>YES or NO. Specify YES to use the TemperatureLimitNormal values</p></td>
</tr>
<tr class="even">
<td><p>WeatherMWMinUse</p></td>
<td><p>String</p></td>
<td><p>YES or NO. Specify YES to use the TemperatureLimitCTG values</p></td>
</tr>
<tr class="odd">
<td><p>WeatherMWMaxName</p>
<p>WeatherMWMinName</p></td>
<td><p>String</p></td>
<td><p>A comma-delimited list of names of XYCurves that will impact this Generator. Multiple curves are allowed because there may be multiple devices that impact the limit.</p>
<p>The limit that is calculated by PowerWorld Simulator will be the minimum limit across all these curves. The x value of the curves is used is determined by the field WeatherMWMaxField and WeatherMWMinField</p></td>
</tr>
<tr class="even">
<td><p>WeatherMWMaxField</p>
<p>WeatherMWMinField</p></td>
<td><p>String</p></td>
<td><p>Field indicating what X value is represented in the XYCurves and which weather Station value should be used to determine the MWMax limit. Options are: TempF, TempC, DewPointF, DewPointC, CloudCoverPerc, WindSpeedmph, WindDirection, WindSpeedKnots, WindSpeedMsec, WindSpeedkmph, and InsolationPerc.</p></td>
</tr>
<tr class="odd">
<td><p>WeatherMWMax</p>
<p>WeatherMWMin</p></td>
<td><p>Single Float</p></td>
<td><p>Uses the specified WeatherMWMaxField or WeatherMWMinField value to determine the X-value to use as a lookup into the XYCurves of WeatherMWMaxName and WeatherMWMinName. Looks up the MW limits based on the list of Limit XYCurves specified.</p>
<p>If no curves are specified, then value is blank</p>
<p>If 1 curve is specified, then value returns the lookup for that curve</p>
<p>If multiple curves, then value performs the lookup on all curves and then returns the <strong>minimum</strong> value across all the MAX curves. (For the WeatherMWMin it would return the <strong>maximum</strong> value across all the MIN curves.</p></td>
</tr>
<tr class="even">
<td><p>WS_TempF</p>
<p>WS_TempC</p>
<p>WS_DewPointF</p>
<p>WS_DewPointC</p>
<p>WS_CloudCoverPerc</p>
<p>WS_WindSpeedmph</p>
<p>WS_WindSpeedKnots</p>
<p>WS_WindSpeedMsec</p>
<p>WS_WindSpeedkmph</p>
<p>WS_WindDirection</p>
<p>WS_InsolationPerc</p>
<p>WS_Humidity</p>
<p>WS_WindChillF</p>
<p>WS_WindChillC</p>
<p>WS_HeatIndexF</p>
<p>WS_HeatIndexC</p></td>
<td><p>Single Float</p></td>
<td><p>The various Weather Measurement values stored with a WeatherStation.</p>
<p>If a WeatherStation is specified then this weather station's value is used. If a WeatherStation is not specified, then the terminal bus substation WeatherStation is used.</p></td>
</tr>
</tbody>
</table>

---

<a id="load-areva-dynamic-line-ratings-dlr-csv-as-weather-dependent-limits"></a>

## Load Areva Dynamic Line Ratings (DLR) (*.csv) as Weather Dependent LImits

*Source: [`Content/MainDocumentation_HTML/Weather_Dependent_Limits_LoadArevaDLR.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Dependent_Limits_LoadArevaDLR.htm)*

Ability to load these files was adding starting in the September 15, 2023 patch of Version 23

On the Tools Ribbon Tab in Simulator under the Other Tools, Weather drop-down there is an option to **Load Areva Dynamic Line Rating (DLR) (\*.csv)**. Choose this option to read a CSV file containing DYNELE, SEG, SEGWST, RATING, and WST objects from the CSV. This help topic explains how these objects will create XYCurve, XYCurvePoint, XYCurveX and WeatherStation objects and how the DYNELE object will describe the mapping to PowerWorld Branch objects.

As of September 2023, the Areva patten file needed to export a CSV file using hdbexport from the Dynamic Line Ratings database in Areva was as follows.

> DYNELE,%SUBSCRIPT,LN,ZBR,XF,NAME1,NAME2,FRST,TOST,ACTRTGI1,ACTRTGI2,ACTRTGI3
> 
> SEG,%SUBSCRIPT,P\_\_DYNELE,ENTMP
> 
> RATING,%SUBSCRIPT,P\_\_SEG,ID,RTG1,RTG2,RTG3,I\_\_TEMPPT
> 
> SEGWST,%SUBSCRIPT,P\_\_SEG,I\_\_WST
> 
> WST,%SUBSCRIPT,ID,TELTEMP,MANUAL,MANTEMP

RATING and WST records have fields that specify a temperature (RATING.ID and WST.ID) . There is a global setting that must be set before reading the CSV to specify whether these values are in Fahrenheit or Celsius. This can be set in the [Simulator Options](10-power-flow-solution-and-options-part1.md#simulator-options) under File Management\\hdbexport Files on the [File Management Options](10-power-flow-solution-and-options-part2.md#file-management-options). The option can also be set using the following AUX file using either SCRIPT or DATA section as follows.

> SCRIPT
> 
> {
> 
> SetData(Sim\_Environment\_Options\_Value, \[Option,Value\], \[HDBExportTempUnits, Fahrenheit\]);
> 
> }
> 
>  
> 
> Sim\_Environment\_Options\_Value (Option,Value)
> 
> {
> 
> "HDBExportTempUnits" "Fahrenheit"
> 
> }

The relationship of DLR records to PowerWorld Simulator object data structures is depicted in the image below and a detailed description of each object follows. In general the objects in the EMS DLR Database represent objects in Simulator as follows.

  - DYNELE records provide information which is used to map the SEG records to the LN, XF, and ZBR records in the NETMOM database . Thus the DYNELE will map to a particular Branch object in PowerWorld Simulator

  - SEG records represent a temperature dependent rating curve (XYCurve in PowerWorld)

  - RATING records represent a particular point on the rating curve (XYCurvePoint in PowerWorld)

  - WST records represent weather stations which contain the temperature values (WeatherStation in PowerWorld)

  - SEGWST records map the SEG to WST (XYCurveX in PowerWorld)

![WeatherDependentLimitsArevaDLR](images/WeatherDependentLimitsArevaDLR.png)

DYNELE Records provide mapping to PowerWorld Branch Objects

DYNELE objects provide a mapping to the Branch objects (or the LN, XF, and ZBR records in the EMS NETMOM database). The mapping of DYNELE objects is done differently depending on the Booleans LN, ZB, and XF.

If LN=T then Simulator will find the PowerWorld Branch that was read as a LN record (EMSType = 'LN') and find the branch for which EMSLineID =NAME1 and EMSID=NAME2

If ZB=T then Simulator will find the PowerWorld Branch that was read as a ZBR record (EMSType = 'ZBR') and find the branch for which EMSLineID=NAME1 and EMSID=NAME2

If XF=T then Simulator will find the PowerWorld Branch that was read as a XF record (EMSType = 'XF') and find the branch for which SubNameFrom=FRST and EMSID=NAME1

When reading the file, PowerWorld will keep track of SEG records that actually have some RATING records which refer to the SEG record. We will then keep track of DYNELE records that have at least one SEG object with RATING records. If the DYNELE doesn’t have any viable SEG records then no error message is written to the message log when loading the CSV file (because we weren’t getting any XYCurve to associated with a Branch anyway). If however we can not find the object associated above then a warning is written to the message log.

The fields which PowerWorld recognizes in the DLR database for the DYNELE record are as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Field Header</p></td>
<td><p>Field Type</p></td>
<td><p>Description of Field</p></td>
</tr>
<tr class="even">
<td><p>%SUBSCRIPT</p></td>
<td><p>Integer</p></td>
<td><p>Integer used to lookup DYNELE from the SEG object</p></td>
</tr>
<tr class="odd">
<td><p>LN</p></td>
<td><p>T or F</p></td>
<td><p>T if it represents a LN record, else F</p></td>
</tr>
<tr class="even">
<td><p>ZB</p></td>
<td><p>T or F</p></td>
<td><p>T if it represents a ZBR record, else F</p></td>
</tr>
<tr class="odd">
<td><p>XF</p></td>
<td><p>T or F</p></td>
<td><p>T if it represents a XF record, else F</p></td>
</tr>
<tr class="even">
<td><p>NAME1</p></td>
<td><p>String</p></td>
<td><p>If LN=T OR ZB=T, then this represents the LINE record ID field. This is stored in PowerWorld’s Branch object as the EMSLINEID field</p>
<p>If XF=T, this is the XF record ID field which is stored in PowerWorld’s Branch object as the EMSID field</p></td>
</tr>
<tr class="odd">
<td><p>NAME2</p></td>
<td><p>String</p></td>
<td><p>If LN=T OR ZB=T, then this represents the LN or ZBR record ID field. This is stored in PowerWorld’s Branch object as the EMSID field</p>
<p>If XF=T we do not used this field for mapping, but it stores the XFMR record ID field which would also be stored in PowerWorld’s Branch object as the EMSLINEID field.</p></td>
</tr>
<tr class="even">
<td><p>FRST</p></td>
<td><p>String</p></td>
<td><p>This is the From side substation of the object. This will be used for mapping XF records.</p></td>
</tr>
<tr class="odd">
<td><p>TOST</p></td>
<td><p>String</p></td>
<td><p>This is the To side substation of the object. This is not used for anything in PowerWorld but just included for convenience.</p></td>
</tr>
<tr class="even">
<td><p>ACTRTGI1</p></td>
<td><p>Float</p></td>
<td><p>When reading this DYNELE, if we successfully map to a Branch in Simulator as described above we will set the LimitMVAA value to this</p></td>
</tr>
<tr class="odd">
<td><p>ACTRTGI2</p></td>
<td><p>Float</p></td>
<td><p>When reading this DYNELE, if we successfully map to a Branch in Simulator as described above we will set the LimitMVAB value to this</p></td>
</tr>
<tr class="even">
<td><p>ACTRTGI3</p></td>
<td><p>Float</p></td>
<td><p>When reading this DYNELE, if we successfully map to a Branch in Simulator as described above we will set the LimitMVAC value to this</p></td>
</tr>
</tbody>
</table>

SEG Records provide mapping to PowerWorld XYCurve

When reading the file, PowerWorld will keep track of SEG records that actually have some RATING records which refer to the SEG record. If a SEG record does not have any RATING records then the SEG record is ignored and a count of the number of SEG records skipped because of this is written to the message log. If the SEG record does have RATING records, but the SEG record P\_\_DYNELE integer references the %SUBSRIPT of DYDNELE for which the associated Branch object could not be found, then we skip the SEG records and do not write a warning to the log (the DYNELE would have already written a warning message).

If all these things are good however, then for each SEG record, PowerWorld Simulator will create 2 XYCurve objects whose name will depend on the the XF, ZB, and LN booleans.

If LN=T, names will be “LN NAME1 NAME2 NORMAL” and “LN NAME1 NAME2 CTG”

If ZB=T, names will be “ZBR NAME1 NAME2 NORMAL” and “ZBR NAME1 NAME2 CTG”

If XF=T, names will be “XF FRST NAME1 NORMAL” and “ZBR FRST NAME1 CTG”

When reading the file, PowerWorld will keep track of SEG records that actually have some RATING records which refer to the SEG record. We will then keep track of DYNELE records that have at least one SEG object with RATING records. If the DYNELE doesn’t have any viable SEG records then no error message is written to the message log when loading the CSV file (because we weren’t getting any XYCurve to associated with a Branch anyway). If however we can not find the object associated above then a warning is written to the message log.

The fields which PowerWorld recognizes in the DLR database for the SEG record are as follows.

|              |            |                                                                  |
| ------------ | ---------- | ---------------------------------------------------------------- |
| Field Header | Field Type | Description of Field                                             |
| %SUBSCRIPT   | Integer    | Integer used to lookup SEG record from RATING and SEGWST records |
| P\_\_DYNELE  | Integer    | Integer that points at the DYNELE record %SUBSCRIPT              |
| ENTMP        | T or F     | Set the PowerWorld XYCurve.Enabled field Boolean                 |

The other fields of the XYCurve are always set as follows

XYCurve.IntermediateType = Interpolate

XYCurve.PointTol = 0.05

XYCurve.XType = Max for XYCurves. This means that if the SEG record has multiple SEGWST records associated with it representing multiple WeatherStation temperatures associated with the same SEG we will take the maximum temperature of those available.

RATING Records provide mapping to PowerWorld XYCurvePoint

Each RATING record points at the SEG record to which it belongs using the P\_\_SEG integer (references the %SUBSCRIPT of the SEG object).

The fields which PowerWorld recognizes in the DLR database for the RATING record are as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Field Header</p></td>
<td><p>Field Type</p></td>
<td><p>Description of Field</p></td>
</tr>
<tr class="even">
<td><p>%SUBSCRIPT</p></td>
<td><p>Integer</p></td>
<td><p>Integer ID for the RATING record</p></td>
</tr>
<tr class="odd">
<td><p>P__SEG</p></td>
<td><p>Integer</p></td>
<td><p>Integer that points at the SEG record %SUBSCRIPT</p></td>
</tr>
<tr class="even">
<td><p>ID</p></td>
<td><p>Float</p></td>
<td><p>This is the temperature of this point. There is a global option in PowerWorld Simulator which we use to designate if this temperature is in Fahrenheit or Celsius in <a href="10-power-flow-solution-and-options-part2.md#file-management-options" class="MCXref xref">File Management Options</a> of the <a href="10-power-flow-solution-and-options-part1.md#simulator-options" class="MCXref xref">Simulator Options</a>.</p>
<p>PowerWorld requires that temperature-dependent Branch LimitMVA curves are in Celsius always. If this global setting specifies Fahrenheit, we will convert this floating point value as (ID-32)*5/9 (to convert to Celsius)</p></td>
</tr>
<tr class="odd">
<td><p>RTG1</p></td>
<td><p>Float</p></td>
<td><p>This is the Normal rating in MVA. An XYCurvePoint will be created with X based on the ID and Y=RTG1. This point will be assigned to the XYCurve with a name that ends in “NORMAL”</p></td>
</tr>
<tr class="even">
<td><p>RTG2</p></td>
<td><p>Float</p></td>
<td><p>This is the Emergency rating in MVA. An XYCurvePoint will be created with X based on the ID and Y=RTG2. This point will be assigned to the XYCurve with a name that ends in “CTG”</p></td>
</tr>
<tr class="odd">
<td><p>RTG3</p></td>
<td><p>Float</p></td>
<td><p>This is the Load-Shed rating in MVA and PowerWorld Simulator ignores this.</p></td>
</tr>
<tr class="even">
<td><p>I__TEMPPT</p></td>
<td><p>Integer</p></td>
<td><p>The RATING records in the DLR database have 2 uses: temperature-dependents limits and also seasonal limits. This is handled by 2 fields with the RATING object called I__TEMPPT and I__COSESN. If I__TEMPPT &gt; 0 then this means it represents a temperature-dependent limit. If I__COSESN &gt; 0 then it means it represents a company’s seasonal limit. We are only trying to read the temperature dependent limit, so we have written PowerWorld’s CSV reader so we read the I__TEMPPT field. If it is not given at all then we assume it’s a temperature-dependent limit. If I__TEMPPT is provided and the value is &lt;= 0 then we ignore the RATING record.</p></td>
</tr>
</tbody>
</table>

WST Records provide mapping to PowerWorld WeatherStation

WST records represent a WeatherStation which contains the telemetered or manual temperature values.

The fields which PowerWorld recognizes in the DLR database for the WST record are as follows.

|              |            |                                                                                                                                                                                                       |
| ------------ | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Field Header | Field Type | Description of Field                                                                                                                                                                                  |
| %SUBSCRIPT   | Integer    | Integer ID for the WST record                                                                                                                                                                         |
| ID           | String     | This is used to as the name of the WeatherStation that is created from the WST records.                                                                                                               |
| TELTEMP      | Float      | If is a number, then we will set PowerWorld’s WeatherStation field TempF or TempC depending on the global setting indicating what units the Temperatures in the CSV file are in.                      |
| MANUAL       | T or F     | If T, then we will consider using the MANTEMP                                                                                                                                                         |
| MANTEMP      | Float      | If MANUAL=T and MANTEMP is a number, then we will set PowerWorld’s WeatherStation field TempF or TempC depending on the global setting indicating what units the Temperatures in the CSV file are in. |

SEGWST Records provide mapping to PowerWorld XYCurveX

SETWST Records represent the specification of which temperature (or multiple temperatures) the SEG should use. In PowerWorld Simulator we had assumed that a Branch would normally obtain a temperature from the terminal substations. This provides another location to specify the temperature at. In PowerWorld Simulator the SEGWST become an XYCurveX object. This means that it provide the X coordinate to the XYCurve lookup. We allow multiply XYCurveX objects to be assigned to the same XYCurve to support the multiple SEGWST records assigned to a single SEG record. When reading SEGWST records, an XYCurveX object will be created which points at the appropriate XYCurve (based on P\_\_SEG) and then points at the appropriate WeatherStation (based on I\_\_WST).

The fields which PowerWorld recognizes in the DLR database for the WST record are as follows.

<table>
<tbody>
<tr class="odd">
<td><p>Field Header</p></td>
<td><p>Field Type</p></td>
<td><p>Description of Field</p></td>
</tr>
<tr class="even">
<td><p>%SUBSCRIPT</p></td>
<td><p>Integer</p></td>
<td><p>Integer ID for the SEGWST record</p></td>
</tr>
<tr class="odd">
<td><p>P__SEG</p></td>
<td><p>Integer</p></td>
<td><p>Integer that points at the SEG record %SUBSCRIPT. The XYCurveX.Name will point to the XYCurve created for the respective SEG record</p></td>
</tr>
<tr class="even">
<td><p>I__WST</p></td>
<td><p>Integer</p></td>
<td><p>Integer that points at the WST record %SUBSCRIPT. The XYCurveX.Object will point to the WeatherStation created for the respective WST record.</p>
<p>Also, the XYCurveX.ObjectField will always be set to TempC to indicate the lookup is done with Celsius. Not that the global option can be specified that values on RATING and WST are given in Fahrenheit in which case the RATING and WST values are converted to Celsisus for PowerWorld’s use. Thus PowerWorld will always set this ObjectField to TempC.</p></td>
</tr>
</tbody>
</table>

---

<a id="weather-related-models-and-information-dialog"></a>

## Weather Related Models and Information Dialog

*Source: [`Content/MainDocumentation_HTML/Weather_Related_Models_Info_Dialog.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Related_Models_Info_Dialog.htm)*

Weather Related Models were added in Version 23.

The Weather Related Models and Information dialog contains two tabs

Weather Stations

This tabs contains a list of the [WeatherStation objects](#weatherstation-objects) defined in the case. This objects define locations where weather measurements such as temperature, wind speed, and cloud cover percent can be assigned. See the help topic on [WeatherStation Objects](#weatherstation-objects) for more information.

Power Flow Weather (PFW) Models

This tab provides a location to define power flow weather models, which can be used by the Time Step Simulation Tool.

As of the initial release of PowerWorld Simulator Version 23, the following list of generator-based power flow weather models we available.

[GenMWMaxMinXYCurve](#genmwmaxminxycurve)

[SolarPVBasic1, SolarPVBasic2](#solarpvbasic1-solarpvbasic2)

[WindClass1, WindClass2, WindClass3, WindClass4, WindBasic](#windclass1-windclass2-windclass3-windclass4-windbasic)

[TemperatureBasic1](52-additional-linked-topics-part2.md#temperaturebasic1)

PFW Model Summary Tab

This table is a summary of the presently defined Power Flow Weather Models in the case. It will list each model along with a count of the "Active and Online", "Active", and "Inactive"

Available Power Flow Weather Models

This will be a list of all PFW Models defined in the case.

Generator PFW Models

This is a case information display showing all generators in the case along with some helpful fields associated with weather models showing information on the Active PFW Models and the Weather Stations objects associated with the generators.

---

<a id="windclass1-windclass2-windclass3-windclass4-windbasic"></a>

## WindClass1, WindClass2, WindClass3, WindClass4, WindBasic

*Source: [`Content/MainDocumentation_HTML/Weather_Model_WindMWMax.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Model_WindMWMax.htm)*

Weather Related Models were added in Version 23

There are several Power Flow Weather Models that use the wind speed to calculate a weather-dependent MWMax for the generator. The wind speed in meters per second is obtained from generator field **WS\_WindSpeedMsec** as described in the help topic [Generator assignments to WeatherStation and XYCurve](#generator-assignments-to-weatherstation-and-xycurve). If the generator can not obtain a valid wind speed there is a model parameter called **DefaultWindMS** which will be used instead . Either the **WS\_WindSpeedMsec** or the **DefaultWindMS** is then multiplied by a model parameter called **HubScalar**. The **HubScalar** represents the conversion from the measured wind speed, which may be on the ground, to the wind speed at the height at which the wind turbine sits (this is often called the "hub height"). The wind turbines can be very tall, so multiplying the measured wind speed by a factor between 1.0 and 2.0 is typically done and this factor is called the **HubScalar**. The value *UsedSpeed* is then run through a **Normalized Power Curve** which is different for each of these models. The **Normalized Power Curve** output is a value between 0.0 and 1.0. This normalized value is then multiplied by the model parameter **MWMax** to create the output of the Wind Model which represents the weather-dependent MWMax value that should be used by the generator. Finally depending on the input parameters **AllowTurnOff** and **AllowTurnOn** the model may also either open or close the generator described in the logic below.

![WeatherWindNormalizedPowercurve](images/WeatherWindNormalizedPowercurve.png)

![weatherAllowTurnOffOn](images/weatherAllowTurnOffOn.png)

Parameters common to all Wind-based power flow weather models.

|               |                                                                                                                                                                                                                                                                                         |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Parameter     | Description                                                                                                                                                                                                                                                                             |
| AllowTurnOff  | Set to 1 to indicate that if the wind speed results in a curve output = 0, then the generator can be turned off (status set to OPEN). For any value other than 1, then the generator will not be opened automatically by this model.                                                    |
| AllowTurnOn   | Set to 1 to indicate that if the windspeed results in a curve output \> 0, then the generator can be turned on (status set to CLOSED). For any value other than 1, then the generator will not be closed automatically by this model.                                                   |
| MWMax         | The largest MWMax allowed for this generator. The Output of this model will be equal to the result of the normalized curve multiplied by this value.                                                                                                                                    |
| HubScalar     | The WindSpeed (in meters per second) at the location of the generator is mulltiplied by this number to represent the scalar in the wind speed being measured and the wind at the height of the wind turbine. This is often called the "Hub Height Scalar". Typical values are 1.0 - 2.0 |
| DefaultWindMS | If a generator does not have access to a WeatherStation to determine the Wind Speed in meters per second, then this wind speed will be used instead.                                                                                                                                    |

With this general setup, the difference between the models is in how the Normalized Power Curve is defined. The International Electrotechnical Commission (IEC) defines a standard IEC 61400. This standard defines 4 different wind turbine classes which represent 4 different wind speed environments for High, Medium, Low, and Very Low wind speeds. PowerWorld has defined 4 models with hard-coded Normalized Output Curves with one for each class of wind defined in IEC 61400 with guidance to defines these curves obtained from the paper: C. Draxl, A. Clifton, B. Hodge, J. McCaa, “The Wind Integration National Dataset (WIND) Toolkit,” Applied Energy, vol. 151, pp. 355-366, 2015. There is also a simple generic model we call WindBasic. The Normalized Output Curves are documented below.

WindClass1 Normalized Output Curve (High Wind)

Class 1 are for High Winds defined as an annual average wind speed at the hub height of 10 m/s (36 km/h; 22 mph) with 70 m/s extreme gusts (250 km/h; 160 mph).

A hard-coded piece-wise linear curve as described next is used for the WindClass1 curve.

> 
> 
>     If      UsedSpeed >  26 Then Output = 0.000
>     Else If UsedSpeed >= 17 Then Output = 1.000
>     Else If UsedSpeed >= 16 Then Output = 0.999 + (UsedSpeed - 16) * 0.001
>     Else If UsedSpeed >= 15 Then Output = 0.999 + (UsedSpeed - 15) * 0.000
>     Else If UsedSpeed >= 14 Then Output = 0.995 + (UsedSpeed - 14) * 0.004
>     Else If UsedSpeed >= 13 Then Output = 0.977 + (UsedSpeed - 13) * 0.018
>     Else If UsedSpeed >= 12 Then Output = 0.926 + (UsedSpeed - 12) * 0.051
>     Else If UsedSpeed >= 11 Then Output = 0.829 + (UsedSpeed - 11) * 0.097
>     Else If UsedSpeed >= 10 Then Output = 0.673 + (UsedSpeed - 10) * 0.156
>     Else If UsedSpeed >=  9 Then Output = 0.502 + (UsedSpeed -  9) * 0.171
>     Else If UsedSpeed >=  8 Then Output = 0.353 + (UsedSpeed -  8) * 0.149
>     Else If UsedSpeed >=  7 Then Output = 0.233 + (UsedSpeed -  7) * 0.120
>     Else If UsedSpeed >=  6 Then Output = 0.143 + (UsedSpeed -  6) * 0.090
>     Else If UsedSpeed >=  5 Then Output = 0.077 + (UsedSpeed -  5) * 0.066
>     Else If UsedSpeed >=  4 Then Output = 0.032 + (UsedSpeed -  4) * 0.045
>     Else If UsedSpeed >=  3 Then Output = 0.004 + (UsedSpeed -  3) * 0.028
>     Else If UsedSpeed >=  2 Then Output = 0.000 + (UsedSpeed -  2) * 0.004
>     Else                         Output = 0.000

WindClass2 Normalized Output Curve (Medium Wind)

Class 2 are for Medium Winds defined as an annual average wind speed at the hub height of 8.5 m/s (31 km/h; 19 mph) with 59.5 m/s extreme gusts (214 km/h; 133 mph).

A hard-coded piece-wise linear curve as described next is used for the WindClass2 curve.

> 
> 
>     If      UsedSpeed >  26 Then Output = 0.000
>     Else If UsedSpeed >= 14 Then Output = 1.000
>     Else If UsedSpeed >= 13 Then Output = 0.999 + (UsedSpeed - 13) * 0.001
>     Else If UsedSpeed >= 12 Then Output = 0.994 + (UsedSpeed - 12) * 0.005
>     Else If UsedSpeed >= 11 Then Output = 0.964 + (UsedSpeed - 11) * 0.030
>     Else If UsedSpeed >= 10 Then Output = 0.855 + (UsedSpeed - 10) * 0.109
>     Else If UsedSpeed >=  9 Then Output = 0.669 + (UsedSpeed -  9) * 0.186
>     Else If UsedSpeed >=  8 Then Output = 0.473 + (UsedSpeed -  8) * 0.196
>     Else If UsedSpeed >=  7 Then Output = 0.313 + (UsedSpeed -  7) * 0.160
>     Else If UsedSpeed >=  6 Then Output = 0.190 + (UsedSpeed -  6) * 0.123
>     Else If UsedSpeed >=  5 Then Output = 0.103 + (UsedSpeed -  5) * 0.087
>     Else If UsedSpeed >=  4 Then Output = 0.042 + (UsedSpeed -  4) * 0.061
>     Else If UsedSpeed >=  3 Then Output = 0.005 + (UsedSpeed -  3) * 0.037
>     Else If UsedSpeed >=  2 Then Output = 0.000 + (UsedSpeed -  2) * 0.005
>     Else                         Output = 0.000

WindClass3 Normalized Output Curve (Low Wind)

Class 3 are for Low Winds defined as an annual average wind speed at the hub height of 7.5 m/s (27 km/h; 17 mph) with 52.5 m/s extreme gusts (189 km/h; 117 mph).

A hard-coded piece-wise linear curve as described next is used for the WindClass3 curve.

> 
> 
>     If      UsedSpeed >  23 Then Output = 0.000
>     Else If UsedSpeed >= 12 Then Output = 1.000
>     Else If UsedSpeed >= 11 Then Output = 0.980 + (UsedSpeed - 11) * 0.020
>     Else If UsedSpeed >= 10 Then Output = 0.918 + (UsedSpeed - 10) * 0.062
>     Else If UsedSpeed >=  9 Then Output = 0.785 + (UsedSpeed -  9) * 0.133
>     Else If UsedSpeed >=  8 Then Output = 0.595 + (UsedSpeed -  8) * 0.190
>     Else If UsedSpeed >=  7 Then Output = 0.403 + (UsedSpeed -  7) * 0.192
>     Else If UsedSpeed >=  6 Then Output = 0.251 + (UsedSpeed -  6) * 0.152
>     Else If UsedSpeed >=  5 Then Output = 0.135 + (UsedSpeed -  5) * 0.116
>     Else If UsedSpeed >=  4 Then Output = 0.053 + (UsedSpeed -  4) * 0.082
>     Else If UsedSpeed >=  3 Then Output = 0.005 + (UsedSpeed -  3) * 0.048
>     Else If UsedSpeed >=  2 Then Output = 0.000 + (UsedSpeed -  2) * 0.005
>     Else                         Output = 0.000

WindClass4 Normalized Output Curve (Very Low Wind)

Class 4 are for Very Low Winds defined as an annual average wind speed at the hub height of 6.0 m/s (22 km/h; 13 mph) with 42 m/s extreme gusts (150 km/h; 94 mph).

A hard-coded piece-wise linear curve as described next is used for the WindClass4 curve.

> 
> 
>     If      UsedSpeed >  20 Then Output = 0.000
>     Else If UsedSpeed >= 11 Then Output = 1.000
>     Else If UsedSpeed >= 10 Then Output = 0.980 + (UsedSpeed - 11) * 0.020
>     Else If UsedSpeed >=  9 Then Output = 0.918 + (UsedSpeed - 10) * 0.062
>     Else If UsedSpeed >=  8 Then Output = 0.785 + (UsedSpeed -  9) * 0.133
>     Else If UsedSpeed >=  7 Then Output = 0.595 + (UsedSpeed -  8) * 0.190
>     Else If UsedSpeed >=  6 Then Output = 0.403 + (UsedSpeed -  7) * 0.192
>     Else If UsedSpeed >=  5 Then Output = 0.251 + (UsedSpeed -  6) * 0.152
>     Else If UsedSpeed >=  4 Then Output = 0.135 + (UsedSpeed -  5) * 0.116
>     Else If UsedSpeed >=  3 Then Output = 0.053 + (UsedSpeed -  4) * 0.082
>     Else If UsedSpeed >=  2 Then Output = 0.000 + (UsedSpeed -  3) * 0.053
>     Else                         Output = 0.000

WindBasic

The WindBasic model is a simple model providing linear segments where the Normalized Output Curve transitions from 0.0 up to 1.0 and then from 1.0 back to 0.0. There are 4 input parameters to describe this as follows.

> 
> 
> |           |                                                                                                                                                                    |
> | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
> | Parameter | Description                                                                                                                                                        |
> | CutInMS   | Between CutInMS and RatedMS the normalized output will vary linearly between 0.0 and 1.0.                                                                          |
> | RatedMS   | Lowest wind speed in Meters per Second at which the normalized output reaches a value of 1.0.                                                                      |
> | CutOut1MS | Higher wind speed at which the normalized output starts decreasing. Between CutOut1MS and CutOut2MS, the normalized output will vary linearly between 1.0 and 0.0. |
> | CutOut2MS | Highest wind speed in Meters per Second at which the normalized output still has a value and thus above this value the normalized output is 1.0.                   |
> 

This gives a the following pseudo code.

> 
> 
>     If      (UsedSpeed >= RatedMS  ) AND (UsedSpeed <= CutOut1MS) Then 
>        Output = 1.000
>     Else If (UsedSpeed <  RatedMS  )     Then 
>        Output = (UsedSpeed - CutInMS  )/(RatedMS - CutInMS)
>     Else If (CutOut2MS >  CutOut1MS) AND (UsedSpeed >  CutoutMS ) Then 
>        Output = (CutOut2MS - UsedSpeed)/(CustOut2MS - CutOut1MS)
>     Else
>        Output = 0.000

---

<a id="solarpvbasic1-solarpvbasic2"></a>

## SolarPVBasic1, SolarPVBasic2

*Source: [`Content/MainDocumentation_HTML/Weather_Model_SolarMWMax.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Model_SolarMWMax.htm)*

Weather Related Models were added in Version 23

There are several Power Flow Weather Models that can be used to make a weather/time/location dependent MWMax for a solar PV generator.

The concepts for this model are discussed in detail in Chapter 4 of the book “Renewable and Efficient Electric Power Systems, 2nd Edition”, Gilbert M. Masters, ISBN: 978-1-118-63350-2, May 2013 Wiley-IEEE Press, 720 Pages

Model Inputs

<table>
<tbody>
<tr class="odd">
<td><p>Inputs</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>DateTime</p></td>
<td><p>The date and time of a simulation is important for solar PV plants. When using the <a href="26-time-step-simulation-part1.md#time-step-simulation">time-step simulation tool</a> this will manage this. Otherwise a global case time can is specified at the top of the <a href="05-case-information-displays-by-object-part1.md#case-description">Case Description dialog</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Latitude and Longitude</p></td>
<td><p>Latitude and Longitude location is obtained from the generator object. The latitude and longitude are specified either with the terminal bus of the generator or with the Substation object to which the terminal bus is assigned.</p></td>
</tr>
<tr class="even">
<td><p>CloudCoverPerc</p></td>
<td><p>The CloudCoverPerc will be obtained from the generator field <strong>WS_CloudCoverPerc</strong> as described in the help topic <a href="#generator-assignments-to-weatherstation-and-xycurve" class="MCXref xref">Generator assignments to WeatherStation and XYCurve</a>.</p>
<p>If this is not available there will be an input parameter with the model for DefaultCloudCoverPerc.</p></td>
</tr>
</tbody>
</table>

Parameters for SolarPVBasic1 and SolarPVBasic2.

<table>
<tbody>
<tr class="odd">
<td><p>Parameter</p></td>
<td><p>Description</p></td>
</tr>
<tr class="even">
<td><p>AllowTurnOff</p></td>
<td><p>Set to 1 to indicate that if a software tool results in an output = 0, then the generator can be turned off (status set to OPEN). For any value other than 1, then the generator will not be opened automatically by this model.</p></td>
</tr>
<tr class="odd">
<td><p>AllowTurnOn</p></td>
<td><p>Set to 1 to indicate that if a software tool results in an output &gt; 0, then the generator can be turned on (status set to CLOSED). For any value other than 1, then the generator will not be closed automatically by this model.</p></td>
</tr>
<tr class="even">
<td><p>Tracking</p></td>
<td><p>Integer code indicating if any solar tracking is used.</p>
<p>0 = None</p>
<p>1 = Single Axis with Fixed Tilt Angle</p>
<p>2 = Single Axis with Fixed Azimuth</p>
<p>3 = Dual Axis</p></td>
</tr>
<tr class="odd">
<td><p>MWMax</p></td>
<td><p>The MW output of the solar panels at the Latitude of the generator when operating on the summer solstice (June 21 in Northern hemisphere) at solar noon and also assuming that the panels are facing directly at the sun. This means that for this model, MWMax will only be reached if the Dual Axis Tracking available.</p></td>
</tr>
<tr class="even">
<td><p>AzimuthDeg</p></td>
<td><p>AzimuthDeg is only used if operating at a fixed Azimuth. (Tracking = 0 or 2). Azimuth is the angle between compass South and the direction normal to the plane of the solar panel)</p></td>
</tr>
<tr class="odd">
<td><p>TiltOffsetDeg or</p>
<p>TiltAngleDeg</p>
<p> </p>
<p>TiltAngleUsed</p></td>
<td><p>Tilt parameters are only used if operating at a fixed Tilt Angle (Tracking = 0 or 1). The solar panel tilt is the angle between the vertical and a vector normal to the plane of the solar panel. For SolarPVBasic1, the input parameter is TiltOffsetDeg and it represent the offset from the latitude.</p>
<p>For SolarPVBasic1: TiltAngleUsed = Latitude + TiltOffsetDeg</p>
<p>For SolarPVBasic2: TiltAngleUsed = TiltAngleDeg</p>
<p>For purposes of Diffuse Energy, if Tracking=0 or 1 then TiltAngleUsed = ElevationSolar</p></td>
</tr>
<tr class="even">
<td><p>DiffuseFactor</p></td>
<td><p>A fraction between 0.0 and 1.00 representing the fraction of the solar energy reaching the earth that does not come from direct sunlight. It’s the energy that is scattered (or diffused) by the atmosphere but still reaches the surface of the earth. This portion of the energy reaching the surface of the earth is not impacted by cloud cover and all the various angles and factors.</p></td>
</tr>
<tr class="odd">
<td><p>DefaultCloud</p></td>
<td><p>Normally, this model obtains the value of CloudCoverPerc from the value WM_CloudCoverPerc of the generator object which obtains it from the associated WeatherStation object. If there is no valid WeatherStation associated with the generator, then the model parameter DefaultCloud is used instead.</p></td>
</tr>
</tbody>
</table>

The Solar PV models also make an assumption that the angle between the Earth's rotational axis and the orbital axis is 23.45 degrees. The tropic of Cancer is defined at Latitude = +23.45 degrees and the Tropic of Capricorn is defined at Latitude -23.45 degrees.

To calculate the normalized MW output of the Solar PV Panel, the following calculations must be done

Declination Angle (DeclinationSolar)

Declination angle is the angle between the rays of the Sun and the plane of the Earth's equator. We define the angle as -23.45 degrees on December 21. We then define the N to represent the day of the year with N=0 representing January 1 at 12:00 AM and N=365 representing December 31 at midnight. The declanation angle is then defined as

**DeclinationSolar = -23.45\*cos( 360/365 \* (N+10) )**

All angles are expressed in degrees. The "+10" exists because the winter solstice occurs 10 days before January 1.

Solar Hour Angle (HRA)

The solar hour angle represents the time of day at the present location as an angle in degrees. The angle 0.0 degrees is defined as the moment when the sun is highest in the sky at that latitude and longitude. This is "solar time" and will not match the local clock time which is defined by local time zones. Each hour of the day then represents 15 degrees (15\*24 = 360) . The Hour Angle is going to be impacted by the Longitude of the location.

Solar Elevation Angle (ElevationSolar)

Solar Elevation Angle is also called the Solar Altitude Angle. It is the angle between the horizontal and the sun representing how high in the sky the sun is. It is calculated using the following equation.

ElevationSolar= arcsin( sin(DeclinationSolar)\*sin(Latitude) + cos(DeclinationSolar)\*cos(Latitude)\*cos(HRA) )

The maximum solar elevation will occur when HRA = 0 (at noon), so cos(HRA) = 1. Using the trigonometric identities that cos(A-B) = sin(A)sin(B) + cos(A)cos(B) and cos(A) = sin(A+90) will give that ElevationMax = Declination - Latitude+ 90. There are some differences when LAT is negative so the actual equation becomes

If Latitude\>= 0 then ElevationSolarMax = DeclinationSolar - Latitude+ 90 Else ElevationSolarMax = -DeclinationSolar + Latitude+ 90

Finally, we don't want ElevationMax \> 90 (which can occur inside the tropics), so if

If ElevationSolarMax \> 90 then ElevationSolarMax = 180 - ElevationSolarMax

Solar Azimuth Angle (AzimuthSolar)

Solar azimuth angle is defined as the angle between the projection of sun’s center onto the horizontal plane and the due South direction. If DeclinationSolar \< 90, then we calculate the azimuth angle as

AzimuthSolar=arctan2\[-cos(DeclinationSolar)\* sin(HRA), sin(DeclinationSolar)\*cos(Latitude) - cos(HRA)\*cos(DeclinationSolar)\*sin(Latitude) \]

Finally, we define Solar Azimuth as an angle between 0 and 360 degrees, so also check

If AzimuthSolar\<0 then AzimuthSolar=AzimuthSolar+360

Atmospheric Transmittance (Transmittance)

Atmospheric transmittance is a measure of what fraction of the energy survives a trip through the atmosphere. This is discussed on pages 213 – 215 of the Master's book. Atmospheric transmittance is a function of the distance of the atmosphere that the solar energy must travel though and thus is a function of the solar elevation angle (α\_s). It is also a function of many factors that are very hard to quantify such as dust, air pollution, water vapor, and turbidity. For our simple solar models for use in power system studies, we will make no attempt to quantify these and will us an exponential decay function: T=Ae^(-km)

The parameter A is a value in W/m^2 and represents the apparent solar energy in outer space. The parameters k is called the optical depth. For our basic model the value of A is not important because it will cancel out in our approximation and for the value of k we will use 0.197. The parameter m represents the air mass ratio which represents the total amount of air the solar energy traverses to get from outer space to the solar panel, relative to the amount that traverses to the solar panel if the sun was directly overhead (ElevationSolar=90 degrees). The empirically determined Equation (4.21) on page 215 of the Master’s book is m=((708 sin(ElevationSolar) )^2+1417)^0.5 - 708 sin(ElevationSolar).

This gives a value of Atmospheric Transmittance of

![WeatherSolarTransmittance](images/WeatherSolarTransmittance.png)

For a given latitude, we then calculate the maximum value of Solar Transmittance possible. This will occur on the summer solstice at noon and the value of ElevationSolar = 90+23.45 - abs(LAT) at that time for latitudes outside of the tropics. For latitudes inside the tropics use ElevationSolar = 90 instead which will make the entire term in square brackets equal to 1.0. This will give a normalized Atmospheric Transmittance of the following withe the A terms canceling out because of the division.

![WeatherSolarTransmittanceNormalized](images/WeatherSolarTransmittanceNormalized.png)

PV Tracking and Direct Solar Energy

The final amount of direct beam energy reaching the solar panel is effected by the type of solar panel tracking available. We assume the solar panels are a flat surface.

If the solar panel has a fixed Azimuth Angle (the angle between South and the compass direction normal to the plane of the solar panel), then the factor Kaz will be applied

Kaz=cos(AzimuthDeg - AzimuthSolar)

Where AzimuthDeg is a model parameter and AzimuthSolar is the angle calculated as described above.

If the solar panel tilt angle (angle between the vertical and vector normal to the plane of the solar panel), the factor Ktilt will be applied.

Ktilt=cos(90-TiltAngleUsed-ElevationSolar)

Where ElevationSolar is the angle between the horizontal plane and the direction of the sun calculated as described above.

Solar PV Tracking can be applied to track the East to West movement of the sun (Azimuth tracking) and/or to track the up and down movement of the sun (Tilt Tracking). The user input code Tracking is an integer 0, 1, 2 or 3 to signify this and the treatment is as follows

Tracking = 0 means there is no PV Tracking and thus Kaz=cos(AzimuthDeg - AzimuthSolar) and Ktilt=cos(90-TiltAngleUsed-ElevationSolar)

Tracking = 1 means there is single axis PV Tracking with a Fixed Tilt Angle thus Kaz=1.0 and Ktilt=cos(90-TiltAngleUsed-ElevationSolar)

Tracking = 2 means there is single axis PV Tracking with a Fixed Azimuth thus Kaz=cos(AzimuthDeg - AzimuthSolar) and Ktilt=1.0

Tracking = 3 means there is dual axis PV Tracking so Kaz=1.0 and Ktilt=1.0

Diffuse Solar Energy

The equations above have all discussed the geometry around direct beam radiation from the sun to the panel. Not all the energy from the sun arrives this way however. Diffused radiation is the energy that is scattered (or diffused) by the atmosphere but reaches the surface of the earth in a randomized way from all angles. This portion of the energy reaching the surface of the earth is not impacted by the various angles and factors discussed above. The portion of the diffuse energy that reaches the solar panel however is a function of what proportion of the sky that the panel sees. If the panel is pointed directly upwards then it sees "all of the sky", however if it is tiled vertically then it only sees 50% of the sky. In the extreme if it were oriented downward (pointing at the ground) it would see none of this diffuse energy. The Diffuse Energy reaching the panel will be proportional to the function (1 + sin(TiltAngleUsed))/2

Reflected Solar Energy

The Master's book also discusses solar energy that is reflected off other surfaces on page 220. The simple models we are showing here ignore this source of energy.

Normalized Power Reaching the Solar Panel

The model input parameter DiffuseFactor represents the fraction of the solar energy reaching the earth as Diffuse Energy. Another input to this model will be CloudCoverPerc equal to the generator's field [WM\_CloudCoverPerc](#generator-assignments-to-weatherstation-and-xycurve) which obtains it from the associated [WeatherStation object](#weatherstation-objects). If there is no valid [WeatherStation](#weatherstation-objects) associated with the generator, then the model parameter DefaultCloud is used instead. The final model Normalized Output Scalar is then calculated as follows.

![WeatherSolarNormalizedOutput](images/WeatherSolarNormalizedOutput.png)

This normalized value is then multiplied by the model parameter MWMax to create the output of the solar PV model which represents the weather-dependent MWMax value that should be used by the generator. Finally depending on the input parameters **AllowTurnOff** and **AllowTurnOn** the model may also either open or close the generator described in the logic below.

**Output (new MWMax)**=**OutScalar**\*MWMax

![weatherAllowTurnOffOn](images/weatherAllowTurnOffOn.png)

---

<a id="genmwmaxminxycurve"></a>

## GenMWMaxMinXYCurve

*Source: [`Content/MainDocumentation_HTML/Weather_Model_GenMWMaxMinXYCurve.htm`](https://www.powerworld.com/WebHelp/Content/MainDocumentation_HTML/Weather_Model_GenMWMaxMinXYCurve.htm)*

Weather Related Models were added in Version 23

This model has only two user parameters: **MWMaxCurve** and **MWMinCurve**. These are [references to an XY Curve](#xycurve-xycurvepoint-xycurvex-objects) to specifies how the MWMax and MWMin of the generator vary as a function of the Temperature in Celsius of at the generator. The Temperature in Celsius is obtained from the generator field **WS\_TempC** which is obtained from the [WeatherStation associated with the generator](#generator-assignments-to-weatherstation-and-xycurve). If there is no valid WeatherStation associated with the generator or if the WeatherStation does not have a valid TempC value then the model does not change anything.
