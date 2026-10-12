---
title: "TS Models — Buses, AGC and Measurement"
part: "Transient Models"
chapter_file: "46-ts-models-other.md"
topics: 9
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Buses, AGC and Measurement

Bus models, area AGC, play-in configuration and measurement objects.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (9)**

- [Transient Models](#transient-models)
- [Area AGC](#area-agc)
- [AreaAGC](#areaagc)
- [Bus](#bus)
- [Playin Configuration](#playin-configuration)
- [Playin](#playin)
- [Measurement Object](#measurement-object)
- [Measurement Object CMPLDWDemo](#measurement-object-cmpldwdemo)
- [Measurement Object LDTPRMON](#measurement-object-ldtprmon)

---

<a id="transient-models"></a>

## Transient Models

*Source: [`Content/TransientModels_HTML/Transient Models.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Transient Models.htm)*

As part of the help documentation, this website provides a detailed explanation of the various transient models that are available in the Transient Stability add-on in PowerWorld Simulator. Each topic corresponds to a particular model implementation/feature, and contains information of its block diagrams and/or equations. In general, input parameters, dynamic states, limits, and autocorrection properties are presented, along with a list of the dynamic states which exist for each model. These states are numerically labeled with a circled number. In addition, a comment is included in each model's documentation regarding whether another software product supports it.

---

<a id="area-agc"></a>

## Area AGC

*Source: [`Content/TransientModels_HTML/Area AGC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Area AGC.htm)*

_This topic has no body text in the source help file._

---

<a id="areaagc"></a>

## AreaAGC

*Source: [`Content/TransientModels_HTML/Area AGC AreaAGC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Area AGC AreaAGC.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Measurement Bus: You must specify a bus for the frequency measurement

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

Here is the link on how to set up the [AGC in Transient Stability](36-transient-stability-overview-and-data-part2.md#available-generation-control-agc-modeling).

---

<a id="bus"></a>

## Bus

*Source: [`Content/TransientModels_HTML/Bus.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Bus.htm)*

_This topic has no body text in the source help file._

---

<a id="playin-configuration"></a>

## Playin Configuration

*Source: [`Content/TransientModels_HTML/Playin Configuration.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Playin Configuration.htm)*

_This topic has no body text in the source help file._

---

<a id="playin"></a>

## Playin

*Source: [`Content/TransientModels_HTML/Playin Configuration Playin.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Playin Configuration Playin.htm)*

[Play In Modeling](36-transient-stability-overview-and-data-part2.md#playin-modeling).

---

<a id="measurement-object"></a>

## Measurement Object

*Source: [`Content/TransientModels_HTML/Measurement Object.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Measurement Object.htm)*

In many cases, load characteristic model open and close loads during a simulation. This cause loads to disconnect and connect MW or MVArs during a transient stability run. In order to keep track of the quantities of load been connected or disconnected a measurement object model was created in PowerWorld.

To handle this, Simulator's Transient Stability tool has always allowed you to assign load models to objects such as the entire system, an Area, a Zone, an Owner, or a Bus. In order to keep track of specific load models inside a load model stability model such as the CMPLDW the measurement object was created. It will assign a measurement object to an object or aggregation object. The measurement object will be in charge of a particular load model in the object and will keep track of specific quantities or models inside the load model.

The measurement Objects will be located in the Transient Stability under Measurement Object Models.

There are two ways to create a new Measurement Object:

**Dialog:**

In the Transient Stability folder under Measurement Object Models in the Model Explorer, right click and hit Insert. This will open a dialog:

![Measurement Object Dialog](images/Measurement_Object_Dialog.gif)

To add a new model just click the Insert button. A dialog will appear prompting you to choose which measurement object model to add for the object. To attached the measurement object to a particular object the measurement object will have a Measurement Object parameter. This is a link to the object the measurement object will be attached to perform the measurement. By clicking Choose a dialog will pop up that will have the available object types and objects the measurement object can perform measurements:

![Measurement Object Choose Dialog](images/Measurement_Object_Choose_Dialog.gif)

After the object is selected the measurement object is ready to be used during the Transient Stability simulation

**Aux File:**

A new Measuremetn object can be added by using an aux file. For example, the measurement object CMPLDWDemo measured the Delta MW change of the Motor X (Mtypa). To assign the measurement object CMPLDWDemo to the load model at bus number 5 the user will have to use the following script section in an aux file:

DATA (MeasurementObjectModel\_CMPLDWDemo, \[WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals\])

{

"Load '5' '1'" "LDTRPMON" "Default" "Active" ""

}

The WhoAmIMeasuring is the Object ID of the Load object. If the measurement object need to be assigned to an aggregation object like Area, Zone or Owner the Object ID will be the Object ID of the aggregation object. The Object Type here means the type of measurement object that particular object is attached to be performing measurements.

New measurement objects can be added as user requests. Please contact PowerWorld for more information.

---

<a id="measurement-object-cmpldwdemo"></a>

## Measurement Object CMPLDWDemo

*Source: [`Content/TransientModels_HTML/Measurement Object CMPLDWDemo.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Measurement Object CMPLDWDemo.htm)*

**AutoCorrection Properties**

To be documented.

The measurement object CMPLDWDemo is measuring the Delta MW change of the Motor X (Mtypa). For Example, to assign the measurement object CMPLDWDemo to the load model at bus number 5 the user will have to use the following script section in an aux file:

DATA (MeasurementObjectModel\_CMPLDWDemo, \[WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals\])

{

"Load '5' '1'" "CMPLDWDemo" "Default" "Active" ""

}

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="measurement-object-ldtprmon"></a>

## Measurement Object LDTPRMON

*Source: [`Content/TransientModels_HTML/Measurement Object LDTRPMON.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Measurement Object LDTRPMON.htm)*

**AutoCorrection Properties**

None

The measurement object LDTRPMON is measuring the amount of load tripped or shed by the different loads models inside the CMPLDW and CMPLDWNF load characteristic model.

Explanation on how to insert the model with the Model Explorer is presented [here](#measurement-object).

Example of adding the LDTRPMON with an aux file:

DATA (MeasurementObjectModel\_LDTRPMON, \[WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified\])

{

"Load '5' '1'" "LDTRPMON" "Default" "Active" "" ""

}

DATA (MeasurementObjectModel\_LDTRPMON, \[WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified\])

{

"Area '1'" "LDTRPMON" "Default" "Active" "" ""

}

DATA (MeasurementObjectModel\_LDTRPMON, \[WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified\])

{

"Zone '1'" "LDTRPMON" "Default" "Active" "" ""

}

In the Concise Variables Names and Headers format:

MeasurementObjectModel\_LDTRPMON (WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified)

{

"Load '5' '1'" "LDTRPMON" "Default" "Active" "" ""

}

MeasurementObjectModel\_LDTRPMON (WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified)

{

"Area '1'" "LDTRPMON" "Default" "Active" "" ""

}

MeasurementObjectModel\_LDTRPMON (WhoAmIMeasuring,ObjectType,DefaultData,Status,SubIntervals,DiffModified)

{

"Zone '1'" "LDTRPMON" "Default" "Active" "" ""

}

The model have the following measurement outputs:

**Pld**-Total load active power at high side bus, MW

**xshn**-Nominal value of load shed, MW

**xton**-Nominal value of load tripped, MW

**xtoi**-Instantaneous value of load tripped and shed, MW

**Pdg**-Distributed Generation P, MW

**xdgn**-Nominal value of distributed generation tripped, MW

**xdgi**-Inst. value of distributed generation tripped and shed ,MW

**Pst**-Static load P, MW

**Pel**-Electronic load P, MW

**Pma**-Motor A P, MW

**Pmb**-Motor B P, MW

**Pmc**-Motor C P, MW

**Pmd**-Motor D P, MW

**xeln**-Nominal electronic load tripped, MW

**xman**-Nominal motor A load tripped, MW

**xmbn**-Nominal motor B load tripped, MW

**xmcn**-Nominal motor C load tripped, MW

**xmdn**-Nominal motor D load tripped, MW

**xeli**-Instantaneous electronic load tripped and shed, MW

**xmai**-Instantaneous motor A load tripped and shed, MW

**xmb**-Instantaneous motor B load tripped and shed, MW

**xmci**-Instantaneous motor C load tripped and shed, MW

**xmdi**-Instantaneous motor D load tripped and shed, MW

**xst** - Instantaneous static load tripped and shed, MW

where:

**Instantaneous** means the Initial MW value minus present MW value.

**Nominal** means the fraction tripped times initial MW value.

This model is supported in PSLF.
