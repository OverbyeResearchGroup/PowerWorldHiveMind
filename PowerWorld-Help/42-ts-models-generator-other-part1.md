---
title: "TS Models — Other Generator Models (Part 1 of 2)"
part: "Transient Models"
chapter_file: "42-ts-models-generator-other-part1.md"
topics: 32
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Other Generator Models (Part 1 of 2)

Remaining generator-attached models: plant controllers, relays, limiters and auxiliary devices.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (32)**

- [Generator](#generator)
- [Other](#other)
- [Aerodynamic](#aerodynamic)
- [WTGAR_A](#wtgar-a)
- [AGC Controller](#agc-controller)
- [AGCBradley](#agcbradley)
- [AGCPulseRate](#agcpulserate)
- [AGCSetPoint](#agcsetpoint)
- [Over Excitation Limiter](#over-excitation-limiter)
- [BASOEL2](#basoel2)
- [MAXEX1](#maxex1)
- [MAXEX2](#maxex2)
- [OEL1](#oel1)
- [OEL1B](#oel1b)
- [OEL2C](#oel2c)
- [OEL3C](#oel3c)
- [OEL4C](#oel4c)
- [OEL5C](#oel5c)
- [Parameter Container](#parameter-container)
- [H6BD](#h6bd)
- [Plant Controller](#plant-controller)
- [PF1](#pf1)
- [PF2](#pf2)
- [PLAYINREF](#playinref)
- [REPC_A](#repc-a)
- [REPC_B](#repc-b)
- [REPC_C](#repc-c)
- [REPC_D (Bus)](#repc-d-bus)
- [REPCGFM_C1](#repcgfm-c1)
- [VAR1](#var1)
- [VAR2](#var2)
- [Paux Controller](#paux-controller)

---

<a id="generator"></a>

## Generator

*Source: [`Content/TransientModels_HTML/Generator.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Generator.htm)*

_This topic has no body text in the source help file._

---

<a id="other"></a>

## Other

*Source: [`Content/TransientModels_HTML/Generator Other.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Generator Other.htm)*

_This topic has no body text in the source help file._

---

<a id="aerodynamic"></a>

## Aerodynamic

*Source: [`Content/TransientModels_HTML/Aerodynamic.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Aerodynamic.htm)*

_This topic has no body text in the source help file._

---

<a id="wtgar-a"></a>

## WTGAR_A

*Source: [`Content/TransientModels_HTML/Aerodynamic Model WTGAR_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Aerodynamic Model WTGAR_A.htm)*

In PTI: **WTARA1** is the same as **WTGAR\_A** model.

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Ka = 0 then Error is created because Ka \> 0.
  - If Theta \< 0 then Error is created because That \>= 0.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Aerodynamic Model WTGAR A 0001](images/Aerodynamic_Model_WTGAR_A_0001.svg)

**Parameters for WTGAR\_A:**

|         |                          |
| ------- | ------------------------ |
| Ka      | Aero-dynamic gain factor |
| Theta   | Initial Pitch Angle      |
| MVABase | MVA Base                 |

**Parameters for WTARA1:**

|       |                          |
| ----- | ------------------------ |
| Ka    | Aero-dynamic gain factor |
| Theta | Initial Pitch Angle      |

---

<a id="agc-controller"></a>

## AGC Controller

*Source: [`Content/TransientModels_HTML/AGC Controller.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/AGC Controller.htm)*

_This topic has no body text in the source help file._

---

<a id="agcbradley"></a>

## AGCBradley

*Source: [`Content/TransientModels_HTML/AGC Controller AGCBradley.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/AGC Controller AGCBradley.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

Here is the link on how to set up the [AGC in Transient Stability](36-transient-stability-overview-and-data-part2.md#available-generation-control-agc-modeling).

---

<a id="agcpulserate"></a>

## AGCPulseRate

*Source: [`Content/TransientModels_HTML/AGC Controller AGCPulseRate.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/AGC Controller AGCPulseRate.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

Here is the link on how to set up the [AGC in Transient Stability](36-transient-stability-overview-and-data-part2.md#available-generation-control-agc-modeling).

---

<a id="agcsetpoint"></a>

## AGCSetPoint

*Source: [`Content/TransientModels_HTML/AGC Controller AGCSetPoint.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/AGC Controller AGCSetPoint.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

Here is the link on how to set up the [AGC in Transient Stability](36-transient-stability-overview-and-data-part2.md#available-generation-control-agc-modeling).

---

<a id="over-excitation-limiter"></a>

## Over Excitation Limiter

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter.htm)*

_This topic has no body text in the source help file._

---

<a id="basoel2"></a>

## BASOEL2

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter BASOEL2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter BASOEL2.htm)*

Added in Version 24, build on August 5, 2025

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Over Excitation Limiter BASOEL2 0001](images/Over_Excitation_Limiter_BASOEL2_0001.svg)

![Over Excitation Limiter BASOEL2 0002](images/Over_Excitation_Limiter_BASOEL2_0002.svg)

**Parameters:**

|         |                                                               |
| ------- | ------------------------------------------------------------- |
| OELFlag | OEL Status. 0=disable; \<\>0=enable                           |
| VHzFlag | V/Hz Status. 0=disable; \<\>0=enable                          |
| OELIn   | OEL input. 0=Efd; 1=Ifd; 2=Vfe                                |
| TRoel   | \[seconds\] OEL regulator input filter time constant          |
| Kp      | \[pu\] OEL regulator proportional gain                        |
| Ki      | \[pu\] OEL regulator integral gain                            |
| OEL1    | \[pu\] Short-time allowed overload                            |
| OET1    | \[seconds\] Short-time overload time (normally zero)          |
| OEL2    | \[pu\] Medium-time allowed overload                           |
| OET2    | \[seconds\] Medium-time overload time                         |
| OEL3    | \[pu\] Continuous limit                                       |
| OET3    | \[seconds\] Continuous limit time                             |
| TRVHz   | \[seconds\] V/Hz limiter regulator input filter time constant |
| KVHz    | \[pu\] V/Hz limiter gain                                      |
| VHzmin  | \[pu\] V/Hz limiter minimum input                             |

---

<a id="maxex1"></a>

## MAXEX1

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter MAXEX1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter MAXEX1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Over Excitation Limiter MAXEX1 0001](images/Over_Excitation_Limiter_MAXEX1_0001.svg)

**Parameters:**

|          |                    |
| -------- | ------------------ |
| EfdRated | Efd,rated          |
| Efd1     | Efd point 1        |
| Time1    | Time1              |
| Efd2     | Efd point 2        |
| Time2    | Time2              |
| Efd3     | Efd point 3        |
| Time3    | Time3              |
| EfdDes   | EfdDes input value |
| Kmx      | Gain               |
| Vlow     | Low limit          |

---

<a id="maxex2"></a>

## MAXEX2

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter MAXEX2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter MAXEX2.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Over Excitation Limiter MAXEX2 0001](images/Over_Excitation_Limiter_MAXEX2_0001.svg)

**Parameters:**

|            |                                     |
| ---------- | ----------------------------------- |
| EorIField  | Set to 0 for Efd or 1 for Ifd Input |
| FieldRated | EfdRated or IfdRated                |
| Field1     | Efd or Ifd point 1                  |
| Time1      | Time1                               |
| Field2     | Efd or Ifd point 2                  |
| Time2      | Time2                               |
| Field3     | Efd or Ifd point 3                  |
| Time3      | Time3                               |
| FieldDes   | EfdDes or IfdDes input value        |
| Kmx        | Gain                                |
| Vlow       | Low limit                           |

---

<a id="oel1"></a>

## OEL1

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL1.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL1 0001](images/Over_Excitation_Limiter_OEL1_0001.svg)

**Parameters:**

|         |                                                                               |
| ------- | ----------------------------------------------------------------------------- |
| Vfdflag | 0 for field current; 1 for field voltage                                      |
| Ifdset  | Pickup level of time dependent excitation limit, per unit                     |
| Ifdmax  | Level of hard excitation limit, per unit                                      |
| Tpickup | Timer setting for time dependent limit                                        |
| RunBack | Parameter of voltage regulator reference adjustment                           |
| Tmax    | Definite time delay for generator trip if field current exceeds Ifdmax        |
| Tset    | Definite time delay for generator trip if field current exceeds Ifdset        |
| Ifcont  | Maximum continuous field current, per unit                                    |
| Alarm   | If 0 take action, if \> 0 only alarm with no action except generator tripping |

1\) **Tpickup Parameter:**

The OEL1 limiter Runback is set based on the limiter timer set by the **Tpickup** parameter:

a) **If** Tpickup \> 0 **then** the field current limiter timer will have an inverse characteristic behavior. The Tpickup will be the delay in operation and will be activated when the field current exceeds Ifdset by 1 per unit.

b) **If** Tpickup \< 0 **then** the field current limiter will have a definite time characteristic and will be the time the field current must remain above the Ifdset to be activated.

2\) Runback Parameter:

The Runback parameter set the behavior of the current or voltage limiter when the time dependent element operates (limiter timer set by Tpickup):

a) **If** Runback \> 0 **then** the voltage regulator reference is biased by the negative direction ramping at the rate if 1/Runback per unit per second as long as the field current or field voltage (as selected by Vfdflag) exceeds Ifcont.

If the selected value falls under Ifcont then ramping is stopped and the voltage regulator reference remains frozen at the biased value.

b) **If** Runback \< 0 **then** the voltage regulator reference is biased and set to Runback per unit.

c) **If** Runback = 0 **then** the generator Exciter is set to the Hard Limit of Ifcont.

3\) The Hard Limiter:

The Hard limiter is set when the generator field current \>= Ifdmax

The Hard Limiter acts immediately to limit the excitation system output voltage and is set the following way by the Ifdmax parameter

a) **When** Ifdmax \> 0 **then** the Hard Limiter is set to Ifdmax.

b) **When** Ifdmax \< 0 **then** the Hard Limiter is set to Ifcont

4\) Generator Trip:

a) **If** Generator Current \> Ifdmax for Tmax seconds or,

b) **If** Generator Current \> Tfdset for Tset seconds.

Notes: The implementation of the Hard Limiters are only allowed in the following exciters:

**esdc1a esdc2a esdc4b esst1a\_ge esst1a\_ge exac1 exac1a exac2 exac8b exbbc exdc1 exdc2\_ge exdc2a exst1\_ge rexs rexsys**

**Pseudo Code of OEL1 algorithm:**

HardLimit = Ifcont **if** Ifdmax \<=0 **else** HardLimit = Ifdmax

**If** fVfdflag = 0 **Then** InputSignal := FieldCurrent

**Else** InputSignal:= EField

Function Local\_DetermineVOEL(SetRunbackSeconds)

**If** Runback \< 0 then begin

VOEL = Runback

FrozenLimitToRunBack := true

**End**

**Else Begin**

**If** SetRunbackSeconds \>= 0 **then begin**

VOEL := -1/(fRunBack)\* SetRunbackSeconds + oldVOEL

FrozenLimitToRunBack := true

**End**

**End**

`End function`

Function LOCAL\_GetRunBackSeconds

**If** (TPickup \< 0) and (AboveIfdInputSignalSetTime \>= Abs(TPickup)) **Then Begin**

result := Present Time - AboveIfdInputSignalSetTime- - Abs(TPickup)

**End**

**Else If** (fTPickUp \> 0) **Then Begin** // Inverse time

InverseCharacteristic TripReset(IO,local\_NewTime);

**If** InverseCharacteristic Tripped **Then Begin** // Meaning it got to one second

result := InverseCharacteristic.TripTime

**End**

**End**

End function

**If** IfieldCurrent \> Ifdmax **then**

OEL1 is at HardLimit.

**If** IfieldCurrent \> Ifdmax for TMax time **then** Trip the Unit.

**End**

**If** (IfieldCurrent \> fIfdSet) **Then Begin**

**If** IfieldCurrent \> fIfdSet for TMax time **then** Trip the Unit.

**End**

**If** InputSignal \> fIfdSet Then Begin

AlreadyReset = false;

**If** AboveIfdInputSignalSetTime = 0 **then** AboveIfdInputSignalSetTime = PresentTime

SetRunbackSeconds := PresentTime

**If** LOCAL\_GetRunBackSeconds \>= 0 **then** begin

**If** (Runback = 0) and (Alarm = 0) **then begin**

OEL1 set at HardLimit = Ifcont

**End**

**End**

**If** Runback \<\> 0 **then begin**

Local\_DetermineVOEL(LOCAL\_GetRunBackSeconds)

**If** (fRunback \<\> 0) and (FrozenLimitToRunBack) and (Alarm = 0) **then begin**

VOEL SendingSignal := true;

**End**

**End**

**Else Begin**

**If** (fRunback \<\> 0) and (FrozenLimitToRunBack) and (Alarm = 0) **then begin**

VOEL SendingSignal := true;

**End**

**If** (fRunback \<\> 0) and (InputSignal \> fIfcont) and (not AlreadyReset) and (Alarm = 0) **then begin**

**If** LOCAL\_GetRunBackSeconds \>= 0 **then begin**

LOCAL\_DetermineVOEL(LOCAL\_GetRunBackSeconds)

**End**

**End**

**Else begin**

**If** (Runback \<\> 0) and (FrozenLimitToRunBack) **then begin**

oldVOEL := fVOEL

**If** (not AlreadyReset) **then begin**

VOEL Frozen

**End**

**End**

AboveIfdInputSignalSetTime := Set to Zero;

InverseCharacteristic(Reset to Zero) // Reset to zero

**If** (not fAlreadyReset) **then begin**

Reset

**End**

AlreadyReset := true

RunbackisZeroActivated := false

**End**

**End**

---

<a id="oel1b"></a>

## OEL1B

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL1B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL1B.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL1B 0001](images/Over_Excitation_Limiter_OEL1B_0001.svg)

**Parameters:**

|          |                                                    |
| -------- | -------------------------------------------------- |
| ITFpu    | OEL timed field current limiter pick up level (pu) |
| IFDmax   | OEL instantaneous field current limit (pu)         |
| IFDlim   | OEL timed field current limit (pu)                 |
| HYST     | OEL pick up/drop out hysteresis (pu)               |
| KCD      | OEL cool down gain (pu)                            |
| Kramp    | Low band central frequency (pu/s)                  |
| IFDrated | Rated field current                                |

---

<a id="oel2c"></a>

## OEL2C

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Kscalse \<= 0.0001 then Kscalse = 0.0001

  - If TFCL \<= 0.0001 then TFCL = 0.0001

  - If ITFpu \<= 0.0001 then ITFpu = 0.0001

  - If 0.0 \< TB1oel \< 0.25\*Mult\*TimeStep then TB1oel = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TB1oel \< 0.5\*Mult\*TimeStep then TB1oel = 0.5\*Mult\*TimeStep

  - If 0.0 \< Tb2oel \< 0.25\*Mult\*TimeStep then Tb2oel = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tb2oel \< 0.5\*Mult\*TimeStep then Tb2oel = 0.5\*Mult\*TimeStep

  - If 0.0 \< TDoel \< 0.25\*Mult\*TimeStep then TDoel = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TDoel \< 0.5\*Mult\*TimeStep then TDoel = 0.5\*Mult\*TimeStep

  - If 0.0 \< TRoel \< 0.25\*Mult\*TimeStep then TRoel = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TRoel \< 0.5\*Mult\*TimeStep then TRoel = 0.5\*Mult\*TimeStep

  - If 0.0 \< TAoel \< 0.25\*Mult\*TimeStep then TAoel = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TAoel \< 0.5\*Mult\*TimeStep then TAoel = 0.5\*Mult\*TimeStep

  - If VOELmax1 \< VOELmin1 then swap the values. If VOELmax1 \< 0 then VOELmax1 change sign to positive. If VOELmin1 \> 0 then change sign to negative.

  - If VOELmax2 \< VOELmin2 then swap the values. If VOELmax2 \< 0 then VOELmax2 change sign to positive. If VOELmin2 \> 0 then change sign to negative.

  - If VOELmax3 \< VOELmin3 then swap the values. If VOELmax3 \< 0 then VOELmax3 change sign to positive. If VOELmin3 \> 0 then change sign to negative.

  - If VINVmax \< VINVmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If LeadLagC1B1 \> VOELmax1, then VOELmax1 = LeadLagC1B1 limits or if LeadLagC1B1 \< VOELmin1, then VOELmin1 = LeadLagC1B1
  - If LeadLagC1B2 \> VOELmax2, then VOELmax2 = LeadLagC1B2 limits or if LeadLagC1B2 \< VOELmin2, then VOELmin2 = LeadLagC1B2
  - If VOELPID \> VOELmax3, then VOELmax3 = VOELPID limits or if VOELPID \< VOELmin3, then VOELmin3 = VOELPID
  - if IERRinv2 \> VINVmax , then VINVmax = IERRinv2 limits or if IERRinv2 \< VINVmin, then VINVmin = IERRinv2

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL2C 0001](images/Over_Excitation_Limiter_OEL2C_0001.svg)

**Parameters:**

|          |                                                                                                           |
| -------- | --------------------------------------------------------------------------------------------------------- |
| OELInput | OELInput: OEL Input, 0=Ifd, 1=Efd, 2=VFE                                                                  |
| TC1oel   | TC1oel: OEL regulator denominator (lag) time constant 1 (s)                                               |
| TB1oel   | TB1oel: OEL regulator numerator (lead) time constant 1 (s)                                                |
| TC2oel   | TC2oel: OEL regulator denominator (lag) time constant 2 (s)                                               |
| Tb2oel   | Tb2oel: OEL regulator numerator (lead) time constant 2 (s)                                                |
| KPoel    | KPoel: OEL PID regulator proportional gain (pu)                                                           |
| KIoel    | KIoel: OEL PID regulator integral gain (pu/s)                                                             |
| KDoel    | KDoel: OEL PID regulator differential gain (pu)                                                           |
| TDoel    | TDoel: OEL PID regulator differential time constant (s)                                                   |
| VOELmax3 | VOELmax3: Maximum OEL PID output limit (pu)                                                               |
| VOELmin3 | VOELmin3: Minimum OEL PID output limit (pu)                                                               |
| VOELmax2 | VOELmax2: Maximum OEL lead-lag 1 output limit (pu)                                                        |
| VOELmin2 | VOELmin2: Minimum OEL lead-lag 1 output limit (pu)                                                        |
| VOELmax1 | VOELmax1: Maximum OEL output limit (pu)                                                                   |
| VOELmin1 | VOELmin1: Minimum OEL output limit (pu)                                                                   |
| Ireset   | Ireset: OEL reset reference, if OEL is inactive (pu)                                                      |
| Ten      | Ten: OEL activation delay time (s)                                                                        |
| Toff     | Toff: OEL reset delay time (s)                                                                            |
| ITHoff   | ITHoff: OEL reset threshold value (pu)                                                                    |
| Kscale   | Kscale: OEL input signal scaling factor (pu)                                                              |
| TRoel    | TRoel: OEL input signal filter time constant (s)                                                          |
| Kact     | Kact: OEL actual value scaling factor (pu)                                                                |
| ITFpu    | ITFpu: OEL reference for inverse time calculations (pu)                                                   |
| Iinst    | Iinst: OEL instantaneous field current limit (pu)                                                         |
| Ilim     | Ilim: OEL thermal field current limit (pu)                                                                |
| TAoel    | TAoel: OEL reference filter time constant (s)                                                             |
| c1       | c1: OEL exponent for calculation of IERRinv1                                                              |
| K1       | K1: OEL gain for calculation of IERRinv1 (pu/pu)                                                          |
| c2       | c2: OEL exponent for calculation of IERRinv2                                                              |
| K2       | K2: OEL gain for calculation of IERRinv2 (pu/pu)                                                          |
| VINVmax  | VINVmax: OEL maximum inverse time output (pu)                                                             |
| VINVmin  | VINVmin: OEL minimum inverse time output (pu)                                                             |
| Fixedru  | Fixedru: OEL fixed delay time output (pu)                                                                 |
| Fixedrd  | Fixedrd: OEL fixed cooling down time output (pu)                                                          |
| TFCL     | TFCL: OEL timer reference (pu)                                                                            |
| Tmax     | Tmax: OEL timer maximum level (pu)                                                                        |
| Tmin     | Tmin: OEL timer minimum level (pu)                                                                        |
| KFB      | KFB: OEL timer feedback gain (pu)                                                                         |
| Krd      | Krd: OEL reference ramp down rate (pu/s)                                                                  |
| Kru      | Kru: OEL reference ramp up rate (pu/s)                                                                    |
| KZRU     | KZRU: OEL thermal reference release threshold                                                             |
| IFDrated | IFDrated: Rated field current (pu)                                                                        |
| SW1      | SW1: User selected logic, which will select fixed ramp rates or a ramp rate function of the field current |

---

<a id="oel3c"></a>

## OEL3C

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL3C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL3C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Kscalse \<= 0.0001 then Kscalse = 0.0001

  - If Koel \<= 0.0001 then Koel = 0.0001

  - If Toel \<= 0 then Toel = Mult\*TimeStep

  - If 0.0 \< TF \< 0.25\*Mult\*TimeStep then TF = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TF \< 0.5\*Mult\*TimeStep then TF = 0.5\*Mult\*TimeStep

  - If VOELmax1 \< VOELmin1 then swap the values. If VOELmax1 \< 0 then VOELmax1 change sign to positive. If VOELmin1 \> 0 then change sign to negative.

  - If VOELmax2 \< VOELmin2 then swap the values. If VOELmax2 \< 0 then VOELmax2 change sign to positive. If VOELmin2 \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VIOEL \> VOELmax1, then VOELmax1 = VIOEL limits or if VIOEL \< VOELmin1, then VOELmin1 = VIOEL
  - If VOEL \> VOELmax2, then VOELmax2 = VOEL limits or if VOEL \< VOELmin2, then VOELmin2 = VOEL

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL3C 0001](images/Over_Excitation_Limiter_OEL3C_0001.svg)

**Parameters:**

|          |                                                          |
| -------- | -------------------------------------------------------- |
| OELInput | OELInput: OEL Input, 0=Ifd, 1=Efd, 2=VFE                 |
| ITFpu    | ITFpu: OEL time field current limiter pick up level (pu) |
| Kscale   | Kscale: OEL input signal scaling factor (pu)             |
| TF       | TF: OEL field current measurement time constant(s)       |
| K1       | K1: Exponent for OEL error calculation                   |
| Koel     | Koel: OEL gain(pu)                                       |
| Toel     | Toel: OEL integral time constant (s)                     |
| KPoel    | KPoel: OEL proportional gain (pu)                        |
| VOELmax1 | VOELmax1: OEL integrator maximum output (pu)             |
| VOELmin1 | VOELmin1: OEL integrator minimum output (pu)             |
| VOELmax2 | VOELmax2: OEL maximum output (pu)                        |
| VOELmin2 | VOELmin2: OEL minimum output (pu)                        |

---

<a id="oel4c"></a>

## OEL4C

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL4C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL4C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Kp and Ki: Kp can't be 0 if Ki = 0, if true then Kp changed to 40.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL4C 0001](images/Over_Excitation_Limiter_OEL4C_0001.svg)

**Parameters:**

|        |                                                                                                      |
| ------ | ---------------------------------------------------------------------------------------------------- |
| Qref   | Reactive power limit, per unit on machine base; the default of zero means to use the power flow Qmax |
| TDelay | Time delay to begin enforcement, seconds                                                             |
| Kp     | PI proportional gain                                                                                 |
| Ki     | PI integral gain                                                                                     |
| Vmin   | Maximum value to change voltage reference, must be always \<= 0                                      |

---

<a id="oel5c"></a>

## OEL5C

*Source: [`Content/TransientModels_HTML/Over Excitation Limiter OEL5C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Over Excitation Limiter OEL5C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If Toel \<= 0 then Toel = Mult\*TimeStep
  - If 0.0 \< TF1 \< 0.25\*Mult\*TimeStep then TF1 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TF1 \< 0.5\*Mult\*TimeStep then TF1 = 0.5\*Mult\*TimeStep
  - If 0.0 \< TF2 \< 0.25\*Mult\*TimeStep then TF2 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< TF2 \< 0.5\*Mult\*TimeStep then TF2 = 0.5\*Mult\*TimeStep
  - If VOELmax \< VOELmin then swap the values. If VOELmax \< 0 then VOELmax change sign to positive. If VOELmin \> 0 then change sign to negative.
  - If VVFEmax \< VVFEmin then swap the values. If VVFEmax \< 0 then VVFEmax change sign to positive. If VVFEmin \> 0 then change sign to negative.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If IntegratorPIKPvKIv \> VVFEmax, then VVFEmax = IntegratorPIKPvKIv limits or if IntegratorPIKPvKIv \< VVFEmin, then VVFEmin = IntegratorPIKPvKIv
  - If IntegratorPIKPKI \> VOELmax, then VOELmax = IntegratorPIKPKI limits or if IntegratorPIKPKI \< VOELmin, then VOELmin = IntegratorPIKPKI

Model Equations and/or Block Diagrams

![Over Excitation Limiter OEL5C 0001](images/Over_Excitation_Limiter_OEL5C_0001.svg)

**Parameters:**

|          |                                                                      |
| -------- | -------------------------------------------------------------------- |
| OELInput | OELInput: OEL Input, 0=Ifd, 1=Efd, 2=VFE                             |
| IFDpu    | IFDpu: OEL inverse time integrator pick up level (pu)                |
| IFDlim   | IFDlim: OEL inverse time limit active level (pu.s)                   |
| VOELmax1 | VOELmax1: OEL inverse time upper limit (pu.s)                        |
| Toel     | Toel: OEL inverse time integrator time constant (s)                  |
| KIFDT    | KIFDT: OEL inverse time leak gain (pu)                               |
| K        | K: OEL lead lag gain (pu)                                            |
| TCoel    | TCoel: OEL lead time constant (s)                                    |
| TBoel    | TBoel: OEL lag time constant (s)                                     |
| IFDpulev | IFDpulev: OEL activation logic pick up level (pu)                    |
| TIFDlev  | TIFDlev: OEL activation logic timer setpoint (s)                     |
| TFDref1  | TFDref1: OEL reference 1 (pu)                                        |
| TFDref2  | TFDref2: OEL reference 2 (pu)                                        |
| KPoel    | KPoel: OEL proportional gain (pu)                                    |
| KIoel    | KIoel: OEL integral gain (pu/s)                                      |
| VOELmax  | VOELmax: OEL PI control upper limit (pu)                             |
| VOELmin  | VOELmin: OEL PI control lower limit (pu)                             |
| KPvfe    | KPvfe: Exciter field current regulator proportional gain (pu)        |
| KIvfe    | KIvfe: Exciter field current regulator integral gain (pu/s)          |
| VVFEmax  | VVFEmax: Exciter field current regulator upper limit (pu)            |
| VVFEmin  | VVFEmin: Exciter field current regulator lower limit (pu)            |
| Kscale1  | Kscale1: Scale factor for OEL input                                  |
| TF1      | TF1: OEL input transducer time constant (s)                          |
| Kscale2  | Kscale2: Scale factor IFEbase/IFErated                               |
| TF2      | TF2: Exciter field current transducer time constant (s)              |
| VFEref   | VFEref: Exciter field current reference setpoint (pu)                |
| SW1      | SW1: OEL reference logical switch 1 (1 = Position A, 2 = Position B) |
| Ibias    | Ibias: OEL reference bias (pu)                                       |
| K1       | K1: Exponent for inverse time function                               |

---

<a id="parameter-container"></a>

## Parameter Container

*Source: [`Content/TransientModels_HTML/Parameter Container.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Parameter Container.htm)*

_This topic has no body text in the source help file._

---

<a id="h6bd"></a>

## H6BD

*Source: [`Content/TransientModels_HTML/Parameter Container H6BD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Parameter Container H6BD.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

This model is a sub model of [Governor Model H6B](40-ts-models-governors-part1.md#h6b-and-h6bd).

PDF file to be added, please contact us.

---

<a id="plant-controller"></a>

## Plant Controller

*Source: [`Content/TransientModels_HTML/Plant Controller.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller.htm)*

_This topic has no body text in the source help file._

---

<a id="pf1"></a>

## PF1

*Source: [`Content/TransientModels_HTML/Plant Controller PF1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller PF1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If VREFmax \< VREFmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VADJ \> VREFmax, then VREFmax = VADJ limits or if VADJ \< VREFmin, then VREFmin = VADJ

Model Equations and/or Block Diagrams

![Plant Controller PF1 0001](images/Plant_Controller_PF1_0001.svg)

**Parameters:**

|           |                                                                  |
| --------- | ---------------------------------------------------------------- |
| VADJF     | Voltage adjuster bypass of pulse generator, 0 inactive, 1 active |
| Tslew     | Voltage adjuster travel time, sec.                               |
| VREFmax   | Voltage adjuster maximum output, pu                              |
| VREFmin   | Voltage adjuster minimum output, pu                              |
| Ton       | Voltage adjuster pulse generator time on, sec.                   |
| Toff      | Voltage adjuster pulse generator time off, sec.                  |
| PFREFnorm | Power factor controller normalized reference setpoint, pu        |
| VITmin    | Power factor controller minimum terminal current limit, pu       |
| VVTmin    | Power factor controller minimum terminal voltage limit, pu       |
| VVTmax    | Power factor controller maximum terminal voltage limit, pu       |
| VPFC\_BW  | Power factor controller deadband magnitude, pu                   |
| TPFC      | Power factor controller delay time, sec.                         |

---

<a id="pf2"></a>

## PF2

*Source: [`Content/TransientModels_HTML/Plant Controller PF2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller PF2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KPpf and KIpf: KPpf can't be 0 if KIpf = 0, if true then KPpf changed to 1.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Plant Controller PF2 0001](images/Plant_Controller_PF2_0001.svg)

**Parameters:**

|           |                                                            |
| --------- | ---------------------------------------------------------- |
| PFREFnorm | Power factor controller normalized reference setpoint, pu  |
| VITmin    | Power factor controller minimum terminal current limit, pu |
| VVTmin    | Power factor controller minimum terminal voltage limit, pu |
| VVTmax    | Power factor controller maximum terminal voltage limit, pu |
| KPpf      | Power factor controller proportional gain, pu              |
| KIpf      | Power factor controller integral gain, pu/sec.             |
| VPFLMT    | Power factor controller output limit, pu                   |

---

<a id="playinref"></a>

## PLAYINREF

*Source: [`Content/TransientModels_HTML/Plant Controller PLAYINREF.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller PLAYINREF.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="repc-a"></a>

## REPC_A

*Source: [`Content/TransientModels_HTML/Plant Controller REPC_A.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller REPC_A.htm)*

In PTI:

\- When used for modeling of **Type 3** wind machine, the model is named **REPCTA1**, and the is used along with REGCA1, REECA1, WTDTA1, WTPTA1, WTARA1 and WTTQA1

\-When used for modeling of **Type 4** machines, the model is named **REPCA1**, and is uses along with are REGCA1, REECA1 and WTDTA1.

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Ddn \< Mult\*TimeStep then Ddn = Mult\*TimeStep
  - If 0 \< Dup \< Mult\*TimeStep then Dup = Mult\*TimeStep
  - If 0.0 \< Tflr \< 0.5\*Mult\*TimeStep then Tflr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tflr \< Mult\*TimeStep then Tflr = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tlag \< 0.5\*Mult\*TimeStep then Tlag = 0, ElseIf 0.5\*Mult\*TimeStep \< Tlag \< Mult\*TimeStep then Tlag = Mult\*TimeStep
  - If Femax \< Femin then swap the values. If Femax \< 0 then Femax change sign to positive. If Femin \> 0 then change sign to negative.
  - If Emax \< Emin then swap the values. If Emax \< 0 then Emax change sign to positive. If Emin \> 0 then change sign to negative.
  - Dbd, dbd1 and dbd2:
      - If Branch is not specified: If RefFlag = 1, and Vcomp = 1 and FreqFlag = 0 do nothing else Must specify a branch on which P, Q, and I measurements are taken.
      - If Branch is specified: Measurement Bus must be one of the terminals of the Measurement Branch.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Reactive PI \> Qmax, then Qmax = Reactive PI or if Reactive Pi \< Qmin, then Qmin = Reactive Pi
  - If PI Power limits \> Pmax, then Pmax = PI Power limits or if PI Power limits \< Pmin, then Pmin = PI Power limits

Model Equations and/or Block Diagrams

![Plant Controller REPC A 0001](images/Plant_Controller_REPC_A_0001.svg)

**Parameters for REPC\_A:**

|           |                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------ |
| RefFlag   | Reference Flag: 1 = voltage control; 0 = reactive power control                                                          |
| VcompFlag | Selection of droop (0) or line drop compensation (1)                                                                     |
| Freqflag  | Flag to turn on (1) or off (0) the active power control loop within the plant controller                                 |
| Tfltr     | Voltage or reactive power measurement filter time constant                                                               |
| Kp        | Proportional gain                                                                                                        |
| Ki        | Integral gain                                                                                                            |
| Tft       | Lead time constant                                                                                                       |
| Tfv       | Lag time constant                                                                                                        |
| Vfrz      | Voltage below which plant control integrator state is frozen                                                             |
| Rc        | Line drop compensation resistance                                                                                        |
| Xc        | Current compensation constant (to emulate droop or line drop compensation)                                               |
| Kc        | Gain on reactive current compensation                                                                                    |
| emax      | Maximum error limit                                                                                                      |
| emin      | Minimum error limit                                                                                                      |
| dbd       | Deadband in control                                                                                                      |
| Qmax      | Maximum Q control output                                                                                                 |
| Qmin      | Minimum Q control output                                                                                                 |
| Kpg       | Proportional gain for power control                                                                                      |
| Kig       | Integral gain for power control                                                                                          |
| Tp        | Lag time constant on Pgen measurement                                                                                    |
| fdbd1     | Deadband downside                                                                                                        |
| fdbd2     | Deadband upside                                                                                                          |
| femax     | Maximum error limit                                                                                                      |
| femin     | Minimum error limit                                                                                                      |
| Pmax      | Maximum Power                                                                                                            |
| Pmin      | Minimum Power                                                                                                            |
| Tlag      | Lag time constant on Pref feedback                                                                                       |
| Ddn       | Downside droop                                                                                                           |
| Dup       | Upside droop                                                                                                             |
| MVABase   | Model MVA base                                                                                                           |
| PUflag    | PUFlag: 0 means that inputs Pbranch, Qbranch and Ibranch are on the system MVABase, otherwise they are the model MVABase |

**Parameters for REPCA1:**

|           |                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------ |
| RefFlag   | Reference Flag: 1 = voltage control; 0 = reactive power control                                                          |
| VcompFlag | Selection of droop (0) or line drop compensation (1)                                                                     |
| Freqflag  | Flag to turn on (1) or off (0) the active power control loop within the plant controller                                 |
| Tfltr     | Voltage or reactive power measurement filter time constant                                                               |
| Kp        | Proportional gain                                                                                                        |
| Ki        | Integral gain                                                                                                            |
| Tft       | Lead time constant                                                                                                       |
| Tfv       | Lag time constant                                                                                                        |
| Vfrz      | Voltage below which plant control integrator state is frozen                                                             |
| Rc        | Line drop compensation resistance                                                                                        |
| Xc        | Current compensation constant (to emulate droop or line drop compensation)                                               |
| Kc        | Gain on reactive current compensation                                                                                    |
| emax      | Maximum error limit                                                                                                      |
| emin      | Minimum error limit                                                                                                      |
| dbdlow    | Deadband low in control                                                                                                  |
| Qmax      | Maximum Q control output                                                                                                 |
| Qmin      | Minimum Q control output                                                                                                 |
| Kpg       | Proportional gain for power control                                                                                      |
| Kig       | Integral gain for power control                                                                                          |
| Tp        | Lag time constant on Pgen measurement                                                                                    |
| fdbd1     | Deadband downside                                                                                                        |
| fdbd2     | Deadband upside                                                                                                          |
| femax     | Maximum error limit                                                                                                      |
| femin     | Minimum error limit                                                                                                      |
| Pmax      | Maximum Power                                                                                                            |
| Pmin      | Minimum Power                                                                                                            |
| Tlag      | Lag time constant on Pref feedback                                                                                       |
| Ddn       | Downside droop                                                                                                           |
| Dup       | Upside droop                                                                                                             |
| dbdupper  | Deadband upper in control                                                                                                |
| PUflag    | PUFlag: 0 means that inputs Pbranch, Qbranch and Ibranch are on the system MVABase, otherwise they are the model MVABase |

**Parameters for REPCTA1:**

|           |                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------ |
| RefFlag   | Reference Flag: 1 = voltage control; 0 = reactive power control                                                          |
| VcompFlag | Selection of droop (0) or line drop compensation (1)                                                                     |
| Freqflag  | Flag to turn on (1) or off (0) the active power control loop within the plant controller                                 |
| Tfltr     | Voltage or reactive power measurement filter time constant                                                               |
| Kp        | Proportional gain                                                                                                        |
| Ki        | Integral gain                                                                                                            |
| Tft       | Lead time constant                                                                                                       |
| Tfv       | Lag time constant                                                                                                        |
| Vfrz      | Voltage below which plant control integrator state is frozen                                                             |
| Rc        | Line drop compensation resistance                                                                                        |
| Xc        | Current compensation constant (to emulate droop or line drop compensation)                                               |
| Kc        | Gain on reactive current compensation                                                                                    |
| emax      | Maximum error limit                                                                                                      |
| emin      | Minimum error limit                                                                                                      |
| dbdlow    | Deadband low in control                                                                                                  |
| Qmax      | Maximum Q control output                                                                                                 |
| Qmin      | Minimum Q control output                                                                                                 |
| Kpg       | Proportional gain for power control                                                                                      |
| Kig       | Integral gain for power control                                                                                          |
| Tp        | Lag time constant on Pgen measurement                                                                                    |
| fdbd1     | Deadband downside                                                                                                        |
| fdbd2     | Deadband upside                                                                                                          |
| femax     | Maximum error limit                                                                                                      |
| femin     | Minimum error limit                                                                                                      |
| Pmax      | Maximum Power                                                                                                            |
| Pmin      | Minimum Power                                                                                                            |
| Tlag      | Lag time constant on Pref feedback                                                                                       |
| Ddn       | Downside droop                                                                                                           |
| Dup       | Upside droop                                                                                                             |
| dbdupper  | Deadband upper in control                                                                                                |
| PUflag    | PUFlag: 0 means that inputs Pbranch, Qbranch and Ibranch are on the system MVABase, otherwise they are the model MVABase |

---

<a id="repc-b"></a>

## REPC_B

*Source: [`Content/TransientModels_HTML/Plant Controller REPC_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller REPC_B.htm)*

REPCB100 is the same as REPC\_B but instead of allowing 50 generators to be referenced, you can have 100 generators.

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Ddn \< Mult\*TimeStep then Ddn = Mult\*TimeStep
  - If 0 \< Dup \< Mult\*TimeStep then Dup = Mult\*TimeStep
  - If 0.0 \< Tflr \< 0.5\*Mult\*TimeStep then Tflr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tflr \< Mult\*TimeStep then Tflr = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tlag \< 0.5\*Mult\*TimeStep then Tlag = 0, ElseIf 0.5\*Mult\*TimeStep \< Tlag \< Mult\*TimeStep then Tlag = Mult\*TimeStep
  - For Tw1 to Tw50 :
      - If 0.0 \< Tw \< 0.5\*Mult\*TimeStep then Tw = 0, ElseIf 0.5\*Mult\*TimeStep \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Femax \< Femin then swap the values. If Femax \< 0 then Femax change sign to positive. If Femin \> 0 then change sign to negative.
  - If Emax \< Emin then swap the values. If Emax \< 0 then Emax change sign to positive. If Emin \> 0 then change sign to negative.
  - Dbd, dbd1 and dbd2:
      - If Branch is not specified: If RefFlag = 1, and Vcomp = 1 and FreqFlag = 0 do nothing else Must specify a branch on which P, Q, and I measurements are taken.
      - If Branch is specified: Measurement Bus must be one of the terminals of the Measurement Branch.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Reactive PI \> Qmax, then Qmax = Reactive PI or if Reactive Pi \< Qmin, then Qmin = Reactive Pi
  - If PI Power limits \> Pmax, then Pmax = PI Power limits or if PI Power limits \< Pmin, then Pmin = PI Power limits

Model Equations and/or Block Diagrams

![Plant Controller REPC B 0001](images/Plant_Controller_REPC_B_0001.svg)

**Parameters for REPC\_B:**

|           |                                                                                          |
| --------- | ---------------------------------------------------------------------------------------- |
| MVABase   | Model MVA base                                                                           |
| RefFlag   | Reference Flag: 1 = voltage control; 0 = reactive power control                          |
| VcompFlag | Selection of droop (0) or line drop compensation (1)                                     |
| Freqflag  | Flag to turn on (1) or off (0) the active power control loop within the plant controller |
| Tfltr     | Voltage or reactive power measurement filter time constant                               |
| Kp        | Proportional gain                                                                        |
| Ki        | Integral gain                                                                            |
| Tft       | Lead time constant                                                                       |
| Tfv       | Lag time constant                                                                        |
| Vfrz      | Voltage below which plant control integrator state is frozen                             |
| Rc        | Line drop compensation resistance                                                        |
| Xc        | Current compensation constant (to emulate droop or line drop compensation)               |
| Kc        | Gain on reactive current compensation                                                    |
| emax      | Maximum error limit                                                                      |
| emin      | Minimum error limit                                                                      |
| dbd       | Deadband in control                                                                      |
| Qmax      | Maximum Q control output                                                                 |
| Qmin      | Minimum Q control output                                                                 |
| Kpg       | Proportional gain for power control                                                      |
| Kig       | Integral gain for power control                                                          |
| Tp        | Lag time constant on Pgen measurement                                                    |
| fdbd1     | Deadband downside                                                                        |
| fdbd2     | Deadband upside                                                                          |
| femax     | Maximum error limit                                                                      |
| femin     | Minimum error limit                                                                      |
| Pmax      | Maximum Power                                                                            |
| Pmin      | Minimum Power                                                                            |
| Tlag      | Lag time constant on Pref feedback                                                       |
| Ddn       | Downside droop                                                                           |
| Dup       | Upside droop                                                                             |
| Kw1       | Kw1: Reactive path weight for control device 1                                           |
| Kz1       | Kz1: Real path weight for control device 1                                               |
| Tw1       | Tw1: Time Delay for control device 1                                                     |
| Kw2       | Kw2: Reactive path weight for control device 2                                           |
| Kz2       | Kz2: Real path weight for control device 2                                               |
| Tw2       | Tw2: Time Delay for control device 2                                                     |
| Kw\*      |                                                                                          |
| Kz\*      |                                                                                          |
| Tw\*      |                                                                                          |
| Kw50      | Kw50: Reactive path weight for control device 50                                         |
| Kz50      | Kz50: Real path weight for control device 50                                             |
| Tw50      | Tw50: Time Delay for control device 50                                                   |

**Parameters for REPC\_B100:**

|           |                                                                                          |
| --------- | ---------------------------------------------------------------------------------------- |
| RefFlag   | Reference Flag: 1 = voltage control; 0 = reactive power control                          |
| VcompFlag | Selection of droop (0) or line drop compensation (1)                                     |
| Freqflag  | Flag to turn on (1) or off (0) the active power control loop within the plant controller |
| Tfltr     | Voltage or reactive power measurement filter time constant                               |
| Kp        | Proportional gain                                                                        |
| Ki        | Integral gain                                                                            |
| Tft       | Lead time constant                                                                       |
| Tfv       | Lag time constant                                                                        |
| Vfrz      | Voltage below which plant control integrator state is frozen                             |
| Rc        | Line drop compensation resistance                                                        |
| Xc        | Current compensation constant (to emulate droop or line drop compensation)               |
| Kc        | Gain on reactive current compensation                                                    |
| emax      | Maximum error limit                                                                      |
| emin      | Minimum error limit                                                                      |
| dbd       | Deadband in control                                                                      |
| Qmax      | Maximum Q control output                                                                 |
| Qmin      | Minimum Q control output                                                                 |
| Kpg       | Proportional gain for power control                                                      |
| Kig       | Integral gain for power control                                                          |
| Tp        | Lag time constant on Pgen measurement                                                    |
| fdbd1     | Deadband downside                                                                        |
| fdbd2     | Deadband upside                                                                          |
| femax     | Maximum error limit                                                                      |
| femin     | Minimum error limit                                                                      |
| Pmax      | Maximum Power                                                                            |
| Pmin      | Minimum Power                                                                            |
| Tlag      | Lag time constant on Pref feedback                                                       |
| Ddn       | Downside droop                                                                           |
| Dup       | Upside droop                                                                             |
| Kw1       | Kw1: Reactive path weight for control device 1                                           |
| Kz1       | Kz1: Real path weight for control device 1                                               |
| Tw1       | Tw1: Time Delay for control device 1                                                     |
| Kw2       | Kw2: Reactive path weight for control device 2                                           |
| Kz2       | Kz2: Real path weight for control device 2                                               |
| Tw2       | Tw2: Time Delay for control device 2                                                     |
| Kw\*      |                                                                                          |
| Kz\*      |                                                                                          |
| Tw\*      |                                                                                          |
| Kw100     | Kw100: Reactive path weight for control device 100                                       |
| Kz100     | Kz100: Real path weight for control device 100                                           |
| Tw100     | Tw100: Time Delay for control device 100                                                 |
| MVABase   | Model MVA base                                                                           |

---

<a id="repc-c"></a>

## REPC_C

*Source: [`Content/TransientModels_HTML/Plant Controller REPC_C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller REPC_C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - The following parameter pairs should have a maximum value that is positive and a minimum value that is negative:  
    Femax/Femin, Emax/Emin, and frmax/frmin  
    If both values are positive, then we will assume the minimum value should have had a negative sign.  
    If both values are negative, then we will assume the maximum value should have had a positive sign.  
    If the Max \< 0 AND Min \> 0, then we will assume the numbers have been entered backwards and we will swap the values.
  - The following parameter pairs should have a maximum value that is greater or equal to than the minimum value:  
    Qvmax/Qvmin, Pmax/Pmin, vrefmax/vrefmin, Qrefmax/Qrefmin, dprefmax/dprefmin, qvrmax/qvrmin, dprmax/dprmin, pfmax/pfmin, Prmax/Prmin, PImax/PImin  
    If the Max \< Min then the values will be swapped by the Auto Correction.  
  - dbd1 and fdbd1 represent low side deadbands which should always be negative. We will assume a parameter equal to the negative of the absolute value entered.
  - dbd2 and fdbd2 represent high side deadbands which should always be positive. We will assume a parameter equal to the positive of the absolute value entered.
  - For Tfltr, Tp, Tlag, Tc, and Tfrq  
    If 0.0 \< X \< 0.5\*Mult\*TimeStep then X = 0, ElseIf 0.5\*Mult\*TimeStep \< x \< Mult\*TimeStep then X = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   

![Plant Controller REPC C 0001](images/Plant_Controller_REPC_C_0001.svg)

**Parameters:**

|             |                                                                                                                                                                                                          |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MeasFlag    | MeasFlag: 0 indicate that positive flow for MeasBranch is leaving MeasBus going out to the line. 1 indicate that positive flow for MeasBranch is arriving at MeasBus coming in from the line.            |
| MeasQFlag   | MeasQFlag: 0 indicate that positive flow for MeasQBranch2 is leaving MeasQBus2 going out to the line. 1 indicate that positive flow for MeasQBranch2 is arriving at MeasQBus2 coming in from the line.   |
| Pefd\_Flag  | Pefd\_Flag: Enable (1) or disable (0) electrical power feedback                                                                                                                                          |
| Ffwrd\_Flag | Ffwrd\_Flag: Feedforward flaf (1) include feedforward and (0) disable                                                                                                                                    |
| RefFlag     | RefFlag: Reference Flag: 0 = reactive power control; 1 = voltage control; 2 = constant power factor                                                                                                      |
| VcompFlag   | VcompFlag: Selection of droop (0) or line drop compensation (1)                                                                                                                                          |
| Freqflag    | Freqflag: Flag to turn on (1) or off (0) the active power control loop within the plant controller                                                                                                       |
| Tfltr       | Tfltr: Voltage or reactive power measurement filter time constant                                                                                                                                        |
| Kp          | Kp: Proportional gain                                                                                                                                                                                    |
| Ki          | Ki: Integral gain                                                                                                                                                                                        |
| Tft         | Tft: Lead time constant                                                                                                                                                                                  |
| Tfv         | Tfv: Lag time constant                                                                                                                                                                                   |
| Vfrz        | Vfrz: Voltage below which plant control integrator state is frozen                                                                                                                                       |
| Rc          | Rc: Line drop compensation resistance                                                                                                                                                                    |
| Xc          | Xc: Current compensation constant (to emulate droop or line drop compensation)                                                                                                                           |
| Kc          | Kc: Gain on reactive current compensation                                                                                                                                                                |
| emax        | emax: Maximum error limit                                                                                                                                                                                |
| emin        | emin: Minimum error limit                                                                                                                                                                                |
| dbd         | dbd: Deadband in control                                                                                                                                                                                 |
| Qvmax       | Qvmax: Maximum Q control output                                                                                                                                                                          |
| Qvmin       | Qvmin: Minimum Q control output                                                                                                                                                                          |
| Kpg         | Kpg: Proportional gain for power control                                                                                                                                                                 |
| Kig         | Kig: Integral gain for power control                                                                                                                                                                     |
| Tp          | Tp: Lag time constant on Pgen measurement                                                                                                                                                                |
| fdbd1       | fdbd1: Deadband downside                                                                                                                                                                                 |
| fdbd2       | fdbd2: Deadband upside                                                                                                                                                                                   |
| femax       | femax: Maximum error limit                                                                                                                                                                               |
| femin       | femin: Minimum error limit                                                                                                                                                                               |
| Pmax        | Pmax: Maximum Power                                                                                                                                                                                      |
| Pmin        | Pmin: Minimum Power                                                                                                                                                                                      |
| Tlag        | Tlag: Lag time constant on Pref feedback                                                                                                                                                                 |
| Ddn         | Ddn: Downside droop                                                                                                                                                                                      |
| Dup         | Dup: Upside droop                                                                                                                                                                                        |
| MVABase     | MVABase: Model MVA base                                                                                                                                                                                  |
| Vrefmax     | Vrefmax: Maximum voltage reference, pu                                                                                                                                                                   |
| Vrefmin     | Vrefmin: Minimum voltage reference, pu                                                                                                                                                                   |
| Qrefmax     | Qrefmax: Maximum Q-reference, pu                                                                                                                                                                         |
| Qrefmin     | Qrefmin: Minimum Q-reference, pu                                                                                                                                                                         |
| dqrefmax    | dqrefmax: Maximum rate if increase of Q-reference, pu/s                                                                                                                                                  |
| dqrefmin    | dqrefmin: Maximum rate if decrease of Q-reference, pu/s                                                                                                                                                  |
| qvrmax      | qvrmax: Maximum rate if increase of Qext (Vext), pu/s                                                                                                                                                    |
| qvrmin      | qvrmin: Maximum rate if decrease of Qext (Vext), pu/s                                                                                                                                                    |
| dprmax      | dprmax: Maximum rate if increase of Plant Pref, pu/s                                                                                                                                                     |
| dprmin      | dprmin: Maximum rate if decrease of Plant Pref, pu/s                                                                                                                                                     |
| pfmax       | pfmax: For positive Mvar, the minimum power factor setpoint allowed                                                                                                                                      |
| pfmin       | pfmin: For negative Mvar, the minimum power factor setpoint allowed                                                                                                                                      |
| Prmax       | Prmax: Maximum rate if increase of Pref, pu/s                                                                                                                                                            |
| Prmin       | Prmin: Maximum rate if decrease of Pref, pu/s                                                                                                                                                            |
| PImax       | PImax: Maximum output of the active power PI controller, pu                                                                                                                                              |
| PImin       | PImin: Minimum output of the active power PI controller, pu                                                                                                                                              |
| Tc          | Tc: Reactive-current compensation time-constant, sec                                                                                                                                                     |
| Qdn1        | Qdn1: First stage of capacitor (reactor) switching out (in), pu                                                                                                                                          |
| Qdn2        | Qdn2: Second stage of capacitor (reactor) switching out (in), pu                                                                                                                                         |
| Qup1        | Qup1: First stage of capacitor (reactor) switching in (out), pu                                                                                                                                          |
| Qup2        | Qup2: Second stage of capacitor (reactor) switching in (out), pu                                                                                                                                         |
| Tdelay1     | Tdelay1: Time delay after which if Q \< Qdn1 (or Q \> Qup1) a capacitor (reactor) is switched, sec                                                                                                       |
| Tdelay2     | Tdelay2: Time delay after which if Q \< Qdn2 (or Q \> Qup2) a capacitor (reactor) is switched, sec                                                                                                       |
| Tmssbrk     | Tmssbrk: Time it takes to switch in (out) a mechanically switched shunt, sec                                                                                                                             |
| TOUT        | TOUT: Time for discharging of a capacitor that has just beed switched out; the same capacitor cannot be switched back in until Tout (sec) has elapsed                                                    |
| Tfrz        | Tfrz: A time delay during which the states are kept frozeen even after the filtered voltage recovers above Vfrz. This can be used to ensure the plant controller does not iteract with the inverter LVRT |
| Tfrq        | Tfrq: Frequency time constant, sec                                                                                                                                                                       |
| dfmax       | dfmax: Maximum frequency error, pu                                                                                                                                                                       |
| dfmin       | dfmin: Minimum frequency error, pu                                                                                                                                                                       |
| MSSFlag     | MSSFlag: 0 means shunt switching is disabled; \<\> 0 means shunt switching is enabled.                                                                                                                   |
| QVFlag      | QVFlag: 0 means Q/V control is a fixed output; \<\> 0 means QV control is enabled.                                                                                                                       |
| Vfreq       | Vfreq: Voltage in pu below which measured frequency is set to 1 pu.                                                                                                                                      |
| frmax       | frmax: Maximum rate limit on measured frequency, pu/s                                                                                                                                                    |
| frmin       | frmin: Minimum rate limit on measured frequency, pu/s                                                                                                                                                    |

---

<a id="repc-d-bus"></a>

## REPC_D (Bus)

*Source: [`Content/TransientModels_HTML/Bus REPC_D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Bus REPC_D.htm)*

**NOTE: REPC\_D is in the same family of controller as the Generator Plant Controllers such as REPC\_A, however the REPC\_D model is assign to a Bus object instead of a Generator object.**

**Thus to create the object you must go to Stability tab on the Bus dialog or look in the Model Explorer under Transient Stability\\Bus Models**

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - The following parameter pairs should have a maximum value that is positive and a minimum value that is negative:  
    Femax/Femin, Emax/Emin, and frmax/frmin  
    If both values are positive, then we will assume the minimum value should have had a negative sign.  
    If both values are negative, then we will assume the maximum value should have had a positive sign.  
    If the Max \< 0 AND Min \> 0, then we will assume the numbers have been entered backwards and we will swap the values.
  - The following parameter pairs should have a maximum value that is greater or equal to than the minimum value:  
    Qvmax/Qvmin, Pmax/Pmin, vrefmax/vrefmin, Qrefmax/Qrefmin, dprefmax/dprefmin, qvrmax/qvrmin, dprmax/dprmin, pfmax/pfmin, Prmax/Prmin, PImax/PImin  
    If the Max \< Min then the values will be swapped by the Auto Correction.  
  - dbd1 and fdbd1 represent low side deadbands which should always be negative. We will assume a parameter equal to the negative of the absolute value entered.
  - dbd2 and fdbd2 represent high side deadbands which should always be positive. We will assume a parameter equal to the positive of the absolute value entered.
  - For Tfltr, Tp, Tlag, Tc, and Tfrq  
    If 0.0 \< X \< 0.5\*Mult\*TimeStep then X = 0, ElseIf 0.5\*Mult\*TimeStep \< x \< Mult\*TimeStep then X = Mult\*TimeStep
  - When (RefFlag=1) AND (VcompFlag=0) AND (Kc\<\>0), a branch should be specified on which to measure Qbranch to perform voltage control with reactive droop. If none is specified then the output of the generator

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   

![Bus Controller REPC D 0001](images/Bus_Controller_REPC_D_0001.svg)

![Bus Controller REPC D 0002](images/Bus_Controller_REPC_D_0002.svg)

![Bus Controller REPC D 0003](images/Bus_Controller_REPC_D_0003.svg)

**Object Parameters:**

|                         |                |                                                                                                                                                                                                                             |
| ----------------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MeasVBus                | OtherObject:0  | Measurement VBus. Bus at which voltage is measured. If not specified then the bus at which the REPC\_D model is defined is used.                                                                                            |
| MeasFreqBus             | OtherObject:1  | Measurement Freq Bus. Bus at which frequency is measured. If not specified, then it will use the same bus as the voltage measurement.                                                                                       |
| MeasBranch              | OtherObject:2  | Measurement Branch. Branch on at which Qbranch, Pbranch, and Ibranch is measured.                                                                                                                                           |
| MeasBus                 | OtherObject:3  | Measurement Bus. This is the terminal bus of the Measurement Branch at which Qbranch, Pbranch and Ibranch are measured. Note that the parameter MeasFlag determines whether the flow is measured into or out of the branch. |
| MeasQBranch2            | OtherObject:4  | Measurement Q Branch 2. Branch on which Qbranch2 is measured.                                                                                                                                                               |
| MeasQBus2               | OtherObject:5  | Measurement Q Bus. This is the terminal bus of the Measure Q Branch 2 at which Qbranch2 is measured. Note that the parameter MeasQFlag determines whether the flow is measured into or out of the branch.                   |
| Control Shunt Device 1  | OtherObject:6  | Switched Shunt controlled by REPC\_D (up to 12 can be specified)                                                                                                                                                            |
| Control Shunt Device 2  | OtherObject:7  | Switched Shunt controlled by REPC\_D (up to 12 can be specified)                                                                                                                                                            |
| ...                     | ...            | ...                                                                                                                                                                                                                         |
| Control Shunt Device 12 | OtherObject:17 | Switched Shunt controlled by REPC\_D (up to 12 can be specified)                                                                                                                                                            |
| Control Device 1        | OtherObject:18 | Generator 1 which receives output Po1 and Qo1 from the REPC\_D model                                                                                                                                                        |
| Control Device 2        | OtherObject:19 | Generator 2 which receives output Po2 and Qo2 from the REPC\_D model                                                                                                                                                        |
| ...                     | ...            | ...                                                                                                                                                                                                                         |
| Control Device 50       | OtherObject:67 | Generator 50 which receives output Po50 and Qo50 from the REPC\_D model                                                                                                                                                     |

**Parameters:**

|             |                                                                                                                                                                                                          |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MeasFlag    | MeasFlag: 0 indicate that positive flow for MeasBranch is leaving MeasBus going out to the line. 1 indicate that positive flow for MeasBranch is arriving at MeasBus coming in from the line.            |
| MeasQFlag   | MeasQFlag: 0 indicate that positive flow for MeasQBranch2 is leaving MeasQBus2 going out to the line. 1 indicate that positive flow for MeasQBranch2 is arriving at MeasQBus2 coming in from the line.   |
| VcompFlag   | VcompFlag: Selection of droop (0) or line drop compensation (1)                                                                                                                                          |
| RefFlag     | RefFlag: Reference Flag: 0 = reactive power control; 1 = voltage control; 2 = constant power factor                                                                                                      |
| Freqflag    | Freqflag: Flag to turn on (1) or off (0) the active power control loop within the plant controller                                                                                                       |
| Pefd\_Flag  | Pefd\_Flag: Enable (1) or disable (0) electrical power feedback                                                                                                                                          |
| Ffwrd\_Flag | Ffwrd\_Flag: Feedforward flaf (1) include feedforward and (0) disable                                                                                                                                    |
| MSSFlag     | MSSFlag: 0 means shunt switching is disabled; \<\> 0 means shunt switching is enabled.                                                                                                                   |
| QVFlag      | QVFlag: 0 means Q/V control is a fixed output; \<\> 0 means QV control is enabled.                                                                                                                       |
| Tfltr       | Tfltr: Voltage or reactive power measurement filter time constant                                                                                                                                        |
| Kp          | Kp: Proportional gain                                                                                                                                                                                    |
| Ki          | Ki: Integral gain                                                                                                                                                                                        |
| Tft         | Tft: Lead time constant                                                                                                                                                                                  |
| Tfv         | Tfv: Lag time constant                                                                                                                                                                                   |
| Vfrz        | Vfrz: Voltage below which plant control integrator state is frozen                                                                                                                                       |
| Rc          | Rc: Line drop compensation resistance                                                                                                                                                                    |
| Xc          | Xc: Current compensation constant (to emulate droop or line drop compensation)                                                                                                                           |
| Kc          | Kc: Gain on reactive current compensation                                                                                                                                                                |
| emax        | emax: Maximum error limit                                                                                                                                                                                |
| emin        | emin: Minimum error limit                                                                                                                                                                                |
| dbd1        | QV Deadband lower threshold \<= 0                                                                                                                                                                        |
| dbd2        | QV Deadband upper threshold \>= 0                                                                                                                                                                        |
| Qvmax       | Qvmax: Maximum Q control output                                                                                                                                                                          |
| Qvmin       | Qvmin: Minimum Q control output                                                                                                                                                                          |
| Kpg         | Kpg: Proportional gain for power control                                                                                                                                                                 |
| Kig         | Kig: Integral gain for power control                                                                                                                                                                     |
| Tp          | Tp: Lag time constant on Pgen measurement                                                                                                                                                                |
| fdbd1       | fdbd1: Deadband downside                                                                                                                                                                                 |
| fdbd2       | fdbd2: Deadband upside                                                                                                                                                                                   |
| femax       | femax: Maximum error limit                                                                                                                                                                               |
| femin       | femin: Minimum error limit                                                                                                                                                                               |
| Pmax        | Pmax: Maximum Power                                                                                                                                                                                      |
| Pmin        | Pmin: Minimum Power                                                                                                                                                                                      |
| Tlag        | Tlag: Lag time constant on Pref feedback                                                                                                                                                                 |
| Ddn         | Ddn: Downside droop (\>= 0)                                                                                                                                                                              |
| Dup         | Dup: Upside droop (\>= 0)                                                                                                                                                                                |
| Vrefmax     | Vrefmax: Maximum voltage reference, pu                                                                                                                                                                   |
| Vrefmin     | Vrefmin: Minimum voltage reference, pu                                                                                                                                                                   |
| Qrefmax     | Qrefmax: Maximum Q-reference, pu                                                                                                                                                                         |
| Qrefmin     | Qrefmin: Minimum Q-reference, pu                                                                                                                                                                         |
| dqrefmax    | dqrefmax: Maximum rate if increase of Q-reference, pu/s                                                                                                                                                  |
| dqrefmin    | dqrefmin: Maximum rate if decrease of Q-reference, pu/s                                                                                                                                                  |
| qvrmax      | qvrmax: Maximum rate if increase of Qext (Vext), pu/s                                                                                                                                                    |
| qvrmin      | qvrmin: Maximum rate if decrease of Qext (Vext), pu/s                                                                                                                                                    |
| dprmax      | dprmax: Maximum rate if increase of Plant Pref, pu/s                                                                                                                                                     |
| dprmin      | dprmin: Maximum rate if decrease of Plant Pref, pu/s                                                                                                                                                     |
| pfmax       | pfmax: For positive Mvar, the minimum power factor setpoint allowed                                                                                                                                      |
| pfmin       | pfmin: For negative Mvar, the minimum power factor setpoint allowed                                                                                                                                      |
| Prmax       | Prmax: Maximum rate if increase of Pref, pu/s                                                                                                                                                            |
| Prmin       | Prmin: Maximum rate if decrease of Pref, pu/s                                                                                                                                                            |
| PImax       | PImax: Maximum output of the active power PI controller, pu                                                                                                                                              |
| PImin       | PImin: Minimum output of the active power PI controller, pu                                                                                                                                              |
| Tc          | Tc: Reactive-current compensation time-constant, sec                                                                                                                                                     |
| Qdn1        | Qdn1: First stage of capacitor (reactor) switching out (in), pu                                                                                                                                          |
| Qdn2        | Qdn2: Second stage of capacitor (reactor) switching out (in), pu                                                                                                                                         |
| Qup1        | Qup1: First stage of capacitor (reactor) switching in (out), pu                                                                                                                                          |
| Qup2        | Qup2: Second stage of capacitor (reactor) switching in (out), pu                                                                                                                                         |
| Tdelay1     | Tdelay1: Time delay after which if Q \< Qdn1 (or Q \> Qup1) a capacitor (reactor) is switched, sec                                                                                                       |
| Tdelay2     | Tdelay2: Time delay after which if Q \< Qdn2 (or Q \> Qup2) a capacitor (reactor) is switched, sec                                                                                                       |
| Tmssbrk     | Tmssbrk: Time it takes to switch in (out) a mechanically switched shunt, sec                                                                                                                             |
| TOUT        | TOUT: Time for discharging of a capacitor that has just beed switched out; the same capacitor cannot be switched back in until Tout (sec) has elapsed                                                    |
| Tfrz        | Tfrz: A time delay during which the states are kept frozeen even after the filtered voltage recovers above Vfrz. This can be used to ensure the plant controller does not iteract with the inverter LVRT |
| Tfrq        | Tfrq: Frequency time constant, sec                                                                                                                                                                       |
| Vfreq       | Vfreq: Voltage in pu below which measured frequency is set to 1 pu.                                                                                                                                      |
| dfmax       | dfmax: Maximum frequency error, pu                                                                                                                                                                       |
| dfmin       | dfmin: Minimum frequency error, pu                                                                                                                                                                       |
| MVABase     | MVABase: Model MVA base                                                                                                                                                                                  |
| frmax       | frmax: Maximum rate limit on measured frequency, pu/s                                                                                                                                                    |
| frmin       | frmin: Minimum rate limit on measured frequency, pu/s                                                                                                                                                    |
| Vfrzhigh    | Vfrz: Voltage above which plant control integrator state is frozen                                                                                                                                       |
| Kz1         | Real path weight for control device 1                                                                                                                                                                    |
| Tz1         | Time Delay for real power 1                                                                                                                                                                              |
| Pmax1       | Real Power Maximum (pu) 1                                                                                                                                                                                |
| Pmin1       | Real Power Minimum (pu) 1                                                                                                                                                                                |
| Kw1         | Reactive path weight for control device 1                                                                                                                                                                |
| Tw1         | Time Delay for reactive power 1                                                                                                                                                                          |
| Qmax1       | Reactive Power Maximum (pu) 1                                                                                                                                                                            |
| Qmin1       | Reactive Power Minimum (pu) 1                                                                                                                                                                            |
| ...         |                                                                                                                                                                                                          |
| ...         | repeat parameters Kz\*, Tz\*, Pmax\*, Pmin\*, Kw\*, Tw\*, Qmax\*, Qmin\* for up to 50 generators                                                                                                         |
| ...         |                                                                                                                                                                                                          |
| Kz50        | Real path weight for control device 50                                                                                                                                                                   |
| Tz50        | Time Delay for real power 50                                                                                                                                                                             |
| Pmax50      | Real Power Maximum (pu) 50                                                                                                                                                                               |
| Pmin50      | Real Power Minimum (pu) 50                                                                                                                                                                               |
| Kw50        | Reactive path weight for control device 50                                                                                                                                                               |
| Tw50        | Time Delay for reactive power 50                                                                                                                                                                         |
| Qmax50      | Reactive Power Maximum (pu) 50                                                                                                                                                                           |
| Qmin50      | Reactive Power Minimum (pu) 50                                                                                                                                                                           |

---

<a id="repcgfm-c1"></a>

## REPCGFM_C1

*Source: [`Content/TransientModels_HTML/Plant Controller REPCGFM_C1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller REPCGFM_C1.htm)*

Model was added in Version 24, build on May 1, 2025

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - The following parameter pairs should have a maximum value that is positive and a minimum value that is negative:  
    FRmax/FRmin, Pfreqmax/Pfreqmin, Prefmax/Prefmin, PerrRmax/PerrRmin, Perrmax/Perrmin, QerrRmax/QerrRmin, Qerrmax/Qerrmin, Verrmax/Verrmin, Qvcmax/Qvcmin  
    If both values are positive, then we will assume the minimum value should have had a negative sign.  
    If both values are negative, then we will assume the maximum value should have had a positive sign.  
    If the Max \< 0 AND Min \> 0, then we will assume the numbers have been entered backwards and we will swap the values.
  - The following parameter pairs should have a maximum value that is greater or equal to than the minimum value:  
    Frefmax/Frefmin, Vrefmax/Vrefmin, FFFRhigh, FFFRlow, Qrefmax, Qrefmin  
    If the Max \< Min then the values will be swapped by the Auto Correction.  
  - dbfL1 and dbVSL1 represent low side deadbands which should always be negative. We will assume a parameter equal to the negative of the absolute value entered.
  - dbfH1 and dbVSH1 represent high side deadbands which should always be positive. We will assume a parameter equal to the positive of the absolute value entered.
  - PFFRhigh \<= 0 expected, so we will assume a value of zero if a positive value specified.
  - PFFRlow \>= 0 expected, so we will assume a value of zero if a negative value specified.
  - Tfrq much be at least Mult\*TimeStep and will be increased to that if less than this
  - Ddn, Dup, DFFR, Kip, Kiq, Kivc, and Kpvc not be negative and will be treated as 0.0 if a negative value is specified.
  - Rloss and Xloss should be positive values. Negative or zero values will be treated as an indication that Rloss and Xloss should be auto-calculated as described below.
  - For Tfref, TVmeas, TVlag, TVref, TPmeas, TPlag, TQmeas, TQlag, Tvc time constant, any value less than Mult\*TimeStep will be modified. If less than 0.5\*Mult\*TimeStep will be set to 0.0, otherwise it will be increased to Mult\*TimeStep.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   

![Plant Controller REPCGFM C1 0001](images/Plant_Controller_REPCGFM_C1_0001.svg)

![Plant Controller REPCGFM C1 0002](images/Plant_Controller_REPCGFM_C1_0002.svg)

![Plant Controller REPCGFM C1 0003](images/Plant_Controller_REPCGFM_C1_0003.svg)

**Parameters:**

|               |                                                                                                                                                                                      |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OtherObject:0 | Measurement Bus                                                                                                                                                                      |
| OtherObject:1 | Measurement Branch                                                                                                                                                                   |
| OtherObject:2 | Measurement Freq Bus                                                                                                                                                                 |
| MeasFlag      | 0 indicates that positive flow for MeasBranch is leaving MeasBus going out to the line. 1 indicate that positive flow for MeasBranch is arriving at MeasBus coming in from the line. |
| VFlag         | A flag to determine if the voltage control for the GFL branch is enabled (\<\>0) or disabled (0)                                                                                     |
| VrefFlag      | A flag to select whether the plant voltage measurement (\<\>0) or the inverter voltage measurement (0) is used to generate the voltage reference of the GFM branch                   |
| FFRFlag       | A flag to select whether the FFR function is enabled (\<\>0) or disabled (0)                                                                                                         |
| FRmax         | Upper rate limiter for the plant frequency measurement \[pu/s\]                                                                                                                      |
| FRmin         | Lower rate limiter for the plant frequency measurement \[pu/s\]                                                                                                                      |
| Tfrq          | Time constant of the low-pass filter for site frequency measurement \[s\]                                                                                                            |
| Vfth          | Voltage threshold for the plant frequency measurement \[pu\]                                                                                                                         |
| Frefmax       | Upper limit of the frequency reference generator of the GFM branch \[pu\]                                                                                                            |
| Frefmin       | Lower limit of the frequency reference generator of the GFM branch \[pu\]                                                                                                            |
| Tfref         | Time constant of the low-pass filter for frequency reference output \[s\]                                                                                                            |
| TVmeas        | Time constant of the low-pass filter for voltage measurement \[s\]                                                                                                                   |
| TVlag         | Emulate the time delay of sending the inverter terminal voltage to the plant controller \[s\]                                                                                        |
| Rloss         | Resistance used to estimate the active power loss of the plant ( If Rloss=0, it will be auto-calculated at initialization so that integrator state for Kip is zero) \[pu\]           |
| Xloss         | Reactance used to estimate the reactive power loss of the plant (If Xloss=0, it will be auto-calculated at initialization so that integrator state for Kiq is zero) \[pu\]           |
| Vrefmax       | Upper limit of the voltage reference generator of the GFM branch \[pu\]                                                                                                              |
| Vrefmin       | Lower limit of the voltage reference generator of the GFM branch \[pu\]                                                                                                              |
| TVref         | Time constant of the low-pass filter for voltage reference output \[s\]                                                                                                              |
| dbfL1         | Lower threshold of the frequency deadband \[pu\]                                                                                                                                     |
| dbfH1         | Upper threshold of the frequency deadband \[pu\]                                                                                                                                     |
| Ddn           | Downside of frequency versus power droop gain \[pu\]                                                                                                                                 |
| Dup           | Upside of frequency versus power droop gain \[pu\]                                                                                                                                   |
| Pfreqmax      | Upper limit of the frequency versus active power droop reference \[pu\]                                                                                                              |
| Pfreqmin      | Lower limit of the frequency versus active power droop reference \[pu\]                                                                                                              |
| Prefmax       | Upper limit of the active power reference \[pu\]                                                                                                                                     |
| Prefmin       | Lower limit of the active power reference \[pu\]                                                                                                                                     |
| FFFRhigh      | Upper threshold of the Fast Frequency Response function \[pu\]                                                                                                                       |
| FFFRlow       | Lower threshold of the Fast Frequency Response function \[pu\]                                                                                                                       |
| PFFRhigh      | Power command of Fast Frequency Response when frequency is higher than fFFR\_high \[pu\]                                                                                             |
| PFFRlow       | Power command of Fast Frequency Response when frequency is lower than fFFR\_low \[pu\]                                                                                               |
| TFFR          | Time duration of the Fast Frequency Response \[s\]                                                                                                                                   |
| DFFR          | Ramp rate for the Fast Frequency Response to quit operation \[pu/s\]                                                                                                                 |
| TPmeas        | Time constant of the low-pass filter for P measurement. \[s\]                                                                                                                        |
| Kip           | Controller gain for the active power path \[pu\]                                                                                                                                     |
| PerrRmax      | Upper limit of the input for the active power path \[pu\]                                                                                                                            |
| PerrRmin      | Lower limit of the input for the active power path \[pu\]                                                                                                                            |
| Perrmax       | Upper limit of the integrator for the active power path \[pu\]                                                                                                                       |
| Perrmin       | Lower limit of the integrator for the active power path \[pu\]                                                                                                                       |
| TPlag         | Emulate the time delay of sending the P command from the plant controller to the inverter controller \[s\]                                                                           |
| Qrefmax       | Upper limit of the reactive power reference \[pu\]                                                                                                                                   |
| Qrefmin       | Lower limit of the reactive power reference \[pu\]                                                                                                                                   |
| TQmeas        | Time constant of the low-pass filter for Q measurement \[s\]                                                                                                                         |
| Kiq           | Controller gain for the reactive power path \[pu\]                                                                                                                                   |
| QerrRmax      | Upper limit of the input for the reactive power path \[pu\]                                                                                                                          |
| QerrRmin      | Lower limit of the input for the reactive power path \[pu\]                                                                                                                          |
| Qerrmax       | Upper limit of the integrator for the reactive power path \[pu\]                                                                                                                     |
| Qerrmin       | Lower limit of the integrator for the reactive power path \[pu\]                                                                                                                     |
| TQlag         | Emulate the time delay of sending the Q command from the plant controller to the inverter controller \[s\]                                                                           |
| Verrmax       | Upper limit of the voltage reference \[pu\]                                                                                                                                          |
| Verrmin       | Lower limit of the voltage reference \[pu\]                                                                                                                                          |
| dbVSL1        | Lower threshold of the plant voltage controller deadband \[pu\]                                                                                                                      |
| dbVSH1        | Upper threshold of the plant voltage controller deadband \[pu\]                                                                                                                      |
| Kpvc          | Controller gain of the plant voltage controller \[pu\]                                                                                                                               |
| Kivc          | Controller gain of the plant voltage control \[pu\]                                                                                                                                  |
| Qvcmax        | Upper limit of the reactive power of the plant controller \[pu\]                                                                                                                     |
| Qvcmin        | Lower limit of the reactive power of the plant controller \[pu\]                                                                                                                     |
| Tvc           | Time constant of the low-pass filter \[s\]                                                                                                                                           |
| MVABase       | Model MVA base (enter 0 to use the machine MVABase) \[MVA\]                                                                                                                          |

---

<a id="var1"></a>

## VAR1

*Source: [`Content/TransientModels_HTML/Plant Controller VAR1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller VAR1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If VREFmax \< VREFmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If VADJ \> VREFmax, then VREFmax = VADJ limits or if VADJ \< VREFmin, then VREFmin = VADJ

Model Equations and/or Block Diagrams

![Plant Controller VAR1 0001](images/Plant_Controller_VAR1_0001.svg)

**Parameters:**

|           |                                                                  |
| --------- | ---------------------------------------------------------------- |
| VADJF     | Voltage adjuster bypass of pulse generator, 0 inactive, 1 active |
| Tslew     | Voltage adjuster travel time, sec.                               |
| VREFmax   | Voltage adjuster maximum output, pu                              |
| VREFmin   | Voltage adjuster minimum output, pu                              |
| Ton       | Voltage adjuster pulse generator time on, sec.                   |
| Toff      | Voltage adjuster pulse generator time off, sec.                  |
| QREF      | VAR controller reference setpoint, pu                            |
| VITmin    | VAR controller minimum terminal current limit, pu                |
| VVTmin    | VAR controller minimum terminal voltage limit, pu                |
| VVTmax    | VAR controller maximum terminal voltage limit, pu                |
| VVARC\_BW | VAR controller deadband magnitude, pu                            |
| TVARC     | VAR controller delay time, sec.                                  |

---

<a id="var2"></a>

## VAR2

*Source: [`Content/TransientModels_HTML/Plant Controller VAR2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Plant Controller VAR2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KPvar and KIvar: KPvar can't be 0 if KIvar= 0, if true then KPvar changed to 1.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Plant Controller VAR2 0001](images/Plant_Controller_VAR2_0001.svg)

**Parameters:**

|         |                                                   |
| ------- | ------------------------------------------------- |
| QREF    | VAR controller reference setpoint, pu             |
| VITmin  | VAR controller minimum terminal current limit, pu |
| VVTmin  | VAR controller minimum terminal voltage limit, pu |
| VVTmax  | VAR controller maximum terminal voltage limit, pu |
| KPvar   | VAR controller proportional gain, pu              |
| KIvar   | VAR controller integral gain, pu/sec.             |
| VVARLMT | VAR controller output limit, pu                   |

---

<a id="paux-controller"></a>

## Paux Controller

*Source: [`Content/TransientModels_HTML/Paux Controller.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Paux Controller.htm)*

_This topic has no body text in the source help file._
