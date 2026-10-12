---
title: "TS Models — Exciters (Part 4 of 5)"
part: "Transient Models"
chapter_file: "39-ts-models-exciters-part4.md"
topics: 15
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Exciters (Part 4 of 5)

Excitation system models (IEEE types, ESST/ESAC/EXST families, REEC*, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (15)**

- [REEC_B](#reec-b)
- [REEC_C](#reec-c)
- [REEC_D](#reec-d)
- [REEC_E](#reec-e)
- [REXS](#rexs)
- [REXSY1](#rexsy1)
- [REXSYS](#rexsys)
- [SCRX](#scrx)
- [SEXS_GE](#sexs-ge)
- [SEXS_PTI](#sexs-pti)
- [ST1C](#st1c)
- [ST2C](#st2c)
- [ST3C](#st3c)
- [ST4C](#st4c)
- [ST5C](#st5c)

---

<a id="reec-b"></a>

## REEC_B

*Source: [`Content/TransientModels_HTML/Exciter REEC_B.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REEC_B.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Iqh \< Iql then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Q limits \> Qmax , then Qmax = Q limits or if Q limits \< Qmin , then Qmin = Q limits
  - If PIq limits \> Vmax , then Vmax = PIq limits or if PIq limits \< Vmin, then Vmin = PIq limits
  - If Pord \> Pmax , then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Model Equations and/or Block Diagrams

![Exciter REEC B 0001](images/Exciter_REEC_B_0001.svg)

**Parameters:**

|         |                                                                                                                                                                                                          |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PfFlag  | Power factor flag (1 – power factor control, 0 – Q control, which can be commanded by an external signal)                                                                                                |
| VFlag   | Voltage control flag (1 – Q control, 0 – voltage control)                                                                                                                                                |
| QFlag   | Reactive power control flag ( 1 – voltage/Q control, 0 – constant pf or Q control)                                                                                                                       |
| Pqflag  | P/Q priority selection on current limit flag. 0 = Q priority; 1 = P priority                                                                                                                             |
| Vdip    | The voltage below which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                |
| Vup     | The voltage above which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                |
| Trv     | Filter time constant for voltage measurement                                                                                                                                                             |
| dbd1    | Deadband in voltage error when voltage dip logic is activated (for overvoltage – thus overvoltage response can be disabled by setting this to a large number e.g. 999)                                   |
| dbd2    | Deadband in voltage error when voltage dip logic is activated (for undervoltage)                                                                                                                         |
| kqv     | Gain for reactive current injection during voltage dip (and overvoltage) conditions                                                                                                                      |
| Iqh1    | Maximum limit of reactive current injection (Iqinj)                                                                                                                                                      |
| Iql1    | Minimum limit of reactive current injection (Iqinj)                                                                                                                                                      |
| Vref0   | The reference voltage from which the voltage error is calculated. This is set by the user. If the user does not specify a value it is initialized by the model to equal to the initial terminal voltage. |
| Tp      | Filter time constant for electrical power measurement                                                                                                                                                    |
| Qmax    | Reactive power limit maximum                                                                                                                                                                             |
| Qmin    | Reactive power limit minimum                                                                                                                                                                             |
| Vmax    | Voltage control maximum                                                                                                                                                                                  |
| Vmin    | Voltage control minimum                                                                                                                                                                                  |
| Kqp     | Proportional gain on Q control                                                                                                                                                                           |
| Kqi     | Integral gain on Q control                                                                                                                                                                               |
| Kvp     | Proportional gain on V control                                                                                                                                                                           |
| Kvi     | Integral gain on V control                                                                                                                                                                               |
| Tiq     | Time constant on lag delay                                                                                                                                                                               |
| dPmax   | Positive Ramp rate on power reference                                                                                                                                                                    |
| dPmin   | Negative Ramp rate on power reference                                                                                                                                                                    |
| Pmax    | Maximum power reference                                                                                                                                                                                  |
| Pmin    | Minimum power reference                                                                                                                                                                                  |
| Tpord   | Filter time constant on Pord                                                                                                                                                                             |
| Imax    | Maximum allowable total converter current limit                                                                                                                                                          |
| MVABase | MVABase                                                                                                                                                                                                  |

**Current Limit Logic Psuedo Code**

The following pseudo-code describes how the values for Ipmax, Ipmin, Iqmax, and Iqmin are updated.

  local\_V = StateVtfilter // Vt State 1

  Iqmax = Imax

  Ipmax = Imax

  **if** PQFlag = **0** **then begin** // Q priority \[default\]

    Iqmin = -Iqmax

    local\_I = Sqr(Imax) - Sqr(Iqcmd)

    **if** local\_I \< **0** **then** local\_I = **0**

    **else** local\_I = sqrt( local\_I )

    **if** local\_I \< Ipmax **Then** Ipmax = local\_I

    Ipmin = **0**

  **end**

  **else Begin**// P priority

    Ipmin = **0**

    local\_I = Sqr(Imax) - Sqr(Ipcmd)

    **if** local\_I \< **0** **then** local\_I = **0**

    **else** local\_I = sqrt( local\_I )

    **if** local\_I \< Iqmax **Then** Iqmax = local\_I

    Iqmin = -Iqmax

  **end**

---

<a id="reec-c"></a>

## REEC_C

*Source: [`Content/TransientModels_HTML/Exciter REEC_C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REEC_C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - If 0 \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If Qmax \< Qmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Iqh \< Iql then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Q limits \> Qmax, then Qmax = Q limits or if Q limits \< Qmin, then Qmin = Q limits
  - If PIq limits \> Vmax, then Vmax = PIq limits or if PIq limits \< Vmin, then Vmin = PIq limits
  - If Pord \> Pmax, then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Model Equations and/or Block Diagrams

![Exciter REEC C 0001](images/Exciter_REEC_C_0001.svg)

**Note:** Vref1 is set to 0 during initialization and is not used in this model.

**Parameters:**

|         |                                                                                                                                                                                                                                                              |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| PfFlag  | Power factor flag (1 – power factor control, 0 – Q control, which can be commanded by an external signal)                                                                                                                                                    |
| VFlag   | Voltage control flag (1 – Q control, 0 – voltage control)                                                                                                                                                                                                    |
| QFlag   | Reactive power control flag ( 1 – voltage/Q control, 0 – constant pf or Q control)                                                                                                                                                                           |
| Pqflag  | P/Q priority selection on current limit flag. 0 = Q priority; 1 = P priority                                                                                                                                                                                 |
| Vdip    | The voltage below which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                                                                    |
| Vup     | The voltage above which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                                                                    |
| Trv     | Filter time constant for voltage measurement                                                                                                                                                                                                                 |
| dbd1    | Deadband in voltage error when voltage dip logic is activated (for overvoltage – thus overvoltage response can be disabled by setting this to a large number e.g. 999)                                                                                       |
| dbd2    | Deadband in voltage error when voltage dip logic is activated (for undervoltage)                                                                                                                                                                             |
| kqv     | Gain for reactive current injection during voltage dip (and overvoltage) conditions                                                                                                                                                                          |
| Iqh1    | Maximum limit of reactive current injection (Iqinj)                                                                                                                                                                                                          |
| Iql1    | Minimum limit of reactive current injection (Iqinj)                                                                                                                                                                                                          |
| Vref0   | The reference voltage from which the voltage error is calculated. This is set by the user. If the user does not specify a value it is initialized by the model to equal to the initial terminal voltage.                                                     |
| Tp      | Filter time constant for electrical power measurement                                                                                                                                                                                                        |
| Qmax    | Reactive power limit maximum                                                                                                                                                                                                                                 |
| Qmin    | Reactive power limit minimum                                                                                                                                                                                                                                 |
| Vmax    | Voltage control maximum                                                                                                                                                                                                                                      |
| Vmin    | Voltage control minimum                                                                                                                                                                                                                                      |
| Kqp     | Proportional gain on Q control                                                                                                                                                                                                                               |
| Kqi     | Integral gain on Q control                                                                                                                                                                                                                                   |
| Kvp     | Proportional gain on V control                                                                                                                                                                                                                               |
| Kvi     | Integral gain on V control                                                                                                                                                                                                                                   |
| Tiq     | Time constant on lag delay                                                                                                                                                                                                                                   |
| dPmax   | Positive Ramp rate on power reference                                                                                                                                                                                                                        |
| dPmin   | Negative Ramp rate on power reference                                                                                                                                                                                                                        |
| Pmax    | Maximum power reference                                                                                                                                                                                                                                      |
| Pmin    | Minimum power reference                                                                                                                                                                                                                                      |
| Tpord   | Filter time constant on Pord                                                                                                                                                                                                                                 |
| Imax    | Maximum allowable total converter current limit                                                                                                                                                                                                              |
| T       | The discharge time in units of seconds. That is, the time (in seconds) that it takes for the unit to go from 0% state of charge to 100% state of charge.                                                                                                     |
| SOCini  | The initial state of charge on the battery and is a user entered value. It should be in per unit; 1.0 per unit means fully charged and 0.0 per unit means fully discharged.                                                                                  |
| SOCmax  | The maximum allowable state of charge. By definition the maximum value would be 1.0, however, it may be set to smaller values (e.g. 0.8) to represent manufacturer requirements that the BESS always remain at or below a certain charging level (e.g. 80%). |
| SOCmin  | The minimum allowable state of charge. By definition the minimum value would be 0.0, however, it may be set to larger values (e.g. 0.2) to represent manufacturer requirements that the BESS always remain at or above a certain charging level (e.g. 20%).  |
| vq1     | VDL1: Voltage Point1                                                                                                                                                                                                                                         |
| lq1     | VDL1: Iqmax Point1                                                                                                                                                                                                                                           |
| vq2     | VDL1: Voltage Point2                                                                                                                                                                                                                                         |
| lq2     | VDL1: Iqmax Point2                                                                                                                                                                                                                                           |
| vq3     | VDL1: Voltage Point3                                                                                                                                                                                                                                         |
| lq3     | VDL1: Iqmax Point3                                                                                                                                                                                                                                           |
| vq4     | VDL1: Voltage Point4                                                                                                                                                                                                                                         |
| lq4     | VDL1: Iqmax Point4                                                                                                                                                                                                                                           |
| vp1     | VDL2: Voltage Point1                                                                                                                                                                                                                                         |
| lp1     | VDL2: Ipmax Point1                                                                                                                                                                                                                                           |
| vp2     | VDL2: Voltage Point2                                                                                                                                                                                                                                         |
| lp2     | VDL2: Ipmax Point2                                                                                                                                                                                                                                           |
| vp3     | VDL2: Voltage Point3                                                                                                                                                                                                                                         |
| lp3     | VDL2: Ipmax Point3                                                                                                                                                                                                                                           |
| vp4     | VDL2: Voltage Point4                                                                                                                                                                                                                                         |
| lp4     | VDL2: Ipmax Point4                                                                                                                                                                                                                                           |
| MVABase | MVABase                                                                                                                                                                                                                                                      |

**Current Limit Logic Psuedo Code**

The following pseudo-code describes how the values for Ipmax, Ipmin, Iqmax, and Iqmin are updated.

  Voltage\_Thld2TimerActive = special boolean related to timer

  local\_V = StateVtfilter // Vt State 1

  **if** VDL1 table is empty **then** Iqmax = **1E10**

  **else** Iqmax = lookup from VL1 table using local\_V

  **if** not Voltage\_Thld2TimerActive **then begin**

    **if** VDL2 table is empty **then** Ipmax = **1E10**

    **else** Ipmax = lookup from VDL2 table using local\_V

  **end**

  **if** PQFlag = **0** **then begin** // Q priority \[default\]

    **If** Imax \< Iqmax **Then** Iqmax = IMax

    Iqmin = -Iqmax

    **if** not Voltage\_Thld2TimerActive **then begin**

      local\_I = Sqr(Imax) - Sqr(Iqcmd)

      **if** local\_I \< **0** **then** local\_I = **0**

      **else** local\_I = sqrt( local\_I )

      **if** local\_I \< Ipmax **Then** Ipmax = local\_I

    **end**

    Ipmin = -Ipmax

  **end**

  **else Begin** // P priority

    **if** not Voltage\_Thld2TimerActive **then begin**

      **if** IMax \< Ipmax **Then** Ipmax = Imax

    **end**

    Ipmin = -Ipmax

    local\_I = Sqr(Imax) - Sqr(Ipcmd)

    **if** local\_I \< **0** **then** local\_I = **0**

    **else** local\_I = sqrt( local\_I )

    **if** local\_I \< Iqmax **Then** Iqmax = local\_I

    Iqmin = -Iqmax// LOCAL\_UpdateIqmin

  **end**

---

<a id="reec-d"></a>

## REEC_D

*Source: [`Content/TransientModels_HTML/Exciter REEC_D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REEC_D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - If 0 \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If QVmax \< QVmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Iqh \< Iql then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Q limits \> QVmax, then QVmax = Q limits or if Q limits \< QVmin, then QVmin = Q limits
  - If PIq limits \> Vmax, then Vmax = PIq limits or if PIq limits \< Vmin, then Vmin = PIq limits
  - If Pord \> Pmax, then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Model Equations and/or Block Diagrams

**Parameters:**

![Exciter REEC D 0001](images/Exciter_REEC_D_0001.svg)

|           |                                                                                                                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vcmpflag  | Vcmpflag: Vcomp Flag (\<\>0 means use current compensation, 0 means use reactive droop                                                                                                                          |
| PfFlag    | PfFlag: Power factor flag (\<\>0 means power factor control, 0 means Q control, which can be commanded by an external signal)                                                                                   |
| VFlag     | VFlag: Voltage control flag (\<\>0 means Q control, 0 mean voltage control)                                                                                                                                     |
| QFlag     | QFlag: Reactive power control flag (\<\>0 means voltage/Q control, 0 means constant pf or Q control)                                                                                                            |
| Pflag     | Pflag: Power Flag (\<\>0 means multiply Pref signal by gen speed wg, 0 means do not multiply)                                                                                                                   |
| Pqflag    | Pqflag: P/Q priority selection on current limit flag. (0 means Q priority, \<\>0 means P priority                                                                                                               |
| MVABase   | MVABase: MVABase for model                                                                                                                                                                                      |
| Vdip      | Vdip: The voltage below which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                 |
| Vup       | Vup: The voltage above which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                  |
| Trv       | Trv: Filter time constant for voltage measurement                                                                                                                                                               |
| dbd1      | dbd1: Deadband in voltage error when voltage dip logic is activated (for overvoltage – thus overvoltage response can be disabled by setting this to a large number e.g. 999)                                    |
| dbd2      | dbd2: Deadband in voltage error when voltage dip logic is activated (for undervoltage)                                                                                                                          |
| kqv       | kqv: Gain for reactive current injection during voltage dip (and overvoltage) conditions                                                                                                                        |
| Iqh1      | Iqh1: Maximum limit of reactive current injection (Iqinj)                                                                                                                                                       |
| Iql1      | Iql1: Minimum limit of reactive current injection (Iqinj)                                                                                                                                                       |
| Vref0     | Vref0: The reference voltage from which the voltage error is calculated. This is set by the user. If the user does not specify a value it is initialized by the model to equal to the initial terminal voltage. |
| Iqfrz     | Iqfrz: Value to which reactive-current command is frozen after a voltage-dip \[pu\]                                                                                                                             |
| Thld      | Thld: Time for which reactive-current command is frozen after a voltage-dip \[s\]; if positive then Iqcmd is frozen to its final value during the voltage-dip; if negative then Iqcmd is frozen to Iqfrz        |
| Thld2     | Thld2: Time delay for which the active current limit (Ipmax) is held after voltage\_dip returns to zero for Thld2 seconds at its value during the voltage dip.                                                  |
| Tp        | Tp: Filter time constant for electrical power measurement                                                                                                                                                       |
| QVmax     | QVmax: The maximum value of the incoming Qext or Vext \[pu\]                                                                                                                                                    |
| QVmin     | QVmin: The minimum value of the incoming Qext or Vext \[pu\]                                                                                                                                                    |
| Vmax      | Vmax: Voltage control maximum                                                                                                                                                                                   |
| Vmin      | Vmin: Voltage control minimum                                                                                                                                                                                   |
| Kqp       | Kqp: Proportional gain on Q control                                                                                                                                                                             |
| Kqi       | Kqi: Integral gain on Q control                                                                                                                                                                                 |
| Kvp       | Kvp: Proportional gain on V control                                                                                                                                                                             |
| Kvi       | Kvi: Integral gain on V control                                                                                                                                                                                 |
| Vref1     | Vref1: User-define reference/bias on the inner-loop voltage control (default value is zero)                                                                                                                     |
| Tiq       | Tiq: Time constant on lag delay                                                                                                                                                                                 |
| dPmax     | dPmax: Positive Ramp rate on power reference                                                                                                                                                                    |
| dPmin     | dPmin: Negative Ramp rate on power reference                                                                                                                                                                    |
| Pmax      | Pmax: Maximum power reference                                                                                                                                                                                   |
| Pmin      | Pmin: Minimum power reference                                                                                                                                                                                   |
| Imax      | Imax: Maximum allowable total converter current limit                                                                                                                                                           |
| Tpord     | Tpord: Filter time constant on Pord                                                                                                                                                                             |
| Rc        | Rc: Current-compensation resistance \[pu\]                                                                                                                                                                      |
| Xc        | Xc: Current-compensation reactance \[pu\]                                                                                                                                                                       |
| Tr1       | Tr1: Filter time constant for voltage measurement. Can be set to zero. \[s\]                                                                                                                                    |
| Kc        | Kc: Reactive-current compensation gain                                                                                                                                                                          |
| Ke        | Ke: Scaling on Ipmin; set to 0 for a generator, set to a value between 0 and 1 for a storage device, as appropriate                                                                                             |
| Vblkh     | Vblkh: Voltage above which the converter is blocked (i.e. Iq = Ip = 0)                                                                                                                                          |
| Vblkl     | Vblkl: Voltage below which the converter is blocked (i.e. Iq = Ip = 0)                                                                                                                                          |
| Tblkdelay | Tblkdelay: The time delay following blocking of the converter after which the converter is released from being blocked                                                                                          |
| Vq1       | Vq1: VDLq: Voltage Point1                                                                                                                                                                                       |
| Iq1       | Iq1: VDLq: Iqmax Point1                                                                                                                                                                                         |
| Vq2       | Vq2: VDLq: Voltage Point2                                                                                                                                                                                       |
| Iq2       | Iq2: VDLq: Iqmax Point2                                                                                                                                                                                         |
| Vq3       | Vq3: VDLq: Voltage Point3                                                                                                                                                                                       |
| Iq3       | Iq3: VDLq: Iqmax Point3                                                                                                                                                                                         |
| Vq4       | Vq4: VDLq: Voltage Point4                                                                                                                                                                                       |
| Iq4       | Iq4: VDLq: Iqmax Point4                                                                                                                                                                                         |
| Vq5       | Vq5: VDLq: Voltage Point5                                                                                                                                                                                       |
| Iq5       | Iq5: VDLq: Iqmax Point5                                                                                                                                                                                         |
| Vq6       | Vq6: VDLq: Voltage Point6                                                                                                                                                                                       |
| Iq6       | Iq6: VDLq: Iqmax Point6                                                                                                                                                                                         |
| Vq7       | Vq7: VDLq: Voltage Point7                                                                                                                                                                                       |
| Iq7       | Iq7: VDLq: Iqmax Point7                                                                                                                                                                                         |
| Vq8       | Vq8: VDLq: Voltage Point8                                                                                                                                                                                       |
| Iq8       | Iq8: VDLq: Iqmax Point8                                                                                                                                                                                         |
| Vq9       | Vq9: VDLq: Voltage Point9                                                                                                                                                                                       |
| Iq9       | Iq9: VDLq: Iqmax Point9                                                                                                                                                                                         |
| Vq10      | Vq10: VDLq: Voltage Point10                                                                                                                                                                                     |
| Iq10      | Iq10: VDLq: Iqmax Point10                                                                                                                                                                                       |
| Vp1       | Vp1: VDLp: Voltage Point1                                                                                                                                                                                       |
| Ip1       | Ip1: VDLp: Ipmax Point1                                                                                                                                                                                         |
| Vp2       | Vp2: VDLp: Voltage Point2                                                                                                                                                                                       |
| Ip2       | Ip2: VDLp: Ipmax Point2                                                                                                                                                                                         |
| Vp3       | Vp3: VDLp: Voltage Point3                                                                                                                                                                                       |
| Ip3       | Ip3: VDLp: Ipmax Point3                                                                                                                                                                                         |
| Vp4       | Vp4: VDLp: Voltage Point4                                                                                                                                                                                       |
| Ip4       | Ip4: VDLp: Ipmax Point4                                                                                                                                                                                         |
| Vp5       | Vp5: VDLp: Voltage Point5                                                                                                                                                                                       |
| Ip5       | Ip5: VDLp: Ipmax Point5                                                                                                                                                                                         |
| Vp6       | Vp6: VDLp: Voltage Point6                                                                                                                                                                                       |
| Ip6       | Ip6: VDLp: Ipmax Point6                                                                                                                                                                                         |
| Vp7       | Vp7: VDLp: Voltage Point7                                                                                                                                                                                       |
| Ip7       | Ip7: VDLp: Ipmax Point7                                                                                                                                                                                         |
| Vp8       | Vp8: VDLp: Voltage Point8                                                                                                                                                                                       |
| Ip8       | Ip8: VDLp: Ipmax Point8                                                                                                                                                                                         |
| Vp9       | Vp9: VDLp: Voltage Point9                                                                                                                                                                                       |
| Ip9       | Ip9: VDLp: Ipmax Point9                                                                                                                                                                                         |
| Vp10      | Vp10: VDLp: Voltage Point10                                                                                                                                                                                     |
| Ip10      | Ip10: VDLp: Ipmax Point10                                                                                                                                                                                       |

![Exciter REEC D 0002](images/Exciter_REEC_D_0002.svg)

**Current Limit Logic Psuedo Code**

The following pseudo-code describes how the values for Ipmax, Ipmin, Iqmax, and Iqmin are updated. This is done independently of blocking logic described previously.

  **If** Blocked **then begin** // see logic above for when blocking is implemented

    Ipmax = **0**

    Ipmin = **0**

    Iqmax = **0**

    Iqmin = **0**

  **End**

  **Else begin**

    Voltage\_Thld2TimerActive = special boolean related to timer

    local\_V = StateVtfilter // Vt State 1

    **if** VDL1 table is empty **then** Iqmax = **1E10**

    **else** Iqmax = lookup from VL1 table using local\_V

    **if** not Voltage\_Thld2TimerActive **then begin**

      **if** VDL2 table is empty **then** Ipmax = **1E10**

      **else** Ipmax = lookup from VDL2 table using local\_V

    **end**

    **if** PQFlag = **0** **then begin** // Q priority \[default\]

      **If** Imax \< Iqmax **Then** Iqmax = IMax

      **if** Iqmax \< **0** **then** Iqmin = Iqmax // special handling

      **Else** Iqmin = -Iqmax

      **if** not Voltage\_Thld2TimerActive **then begin**

        local\_I = Sqr(Imax) - Sqr(Iqcmd)

        **if** local\_I \< **0** **then** local\_I = **0**

        **else** local\_I = sqrt( local\_I )

        **if** local\_I \< Ipmax **Then** Ipmax = local\_I

      **end**

      Ipmin = -Ke\*Ipmax

    **end**

    **else** **Begin**// P priority

      **if** not Voltage\_Thld2TimerActive **then begin**

        **if** IMax \< Ipmax **Then** Ipmax = Imax

      **end**

      Ipmin = -Ke\*Ipmax

      local\_I = Sqr(Imax) - Sqr(Ipcmd)

      **if** local\_I \< **0** **then** local\_I = **0**

      **else** local\_I = sqrt( local\_I )

      **if** local\_I \< Iqmax **Then** Iqmax = local\_I

      **if** Iqmax \< **0** **then** Iqmin = Iqmax // special handling

      **Else** Iqmin = -Iqmax

    **end**

  **end**

---

<a id="reec-e"></a>

## REEC_E

*Source: [`Content/TransientModels_HTML/Exciter REEC_E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REEC_E.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tv \< 0.5\*Mult\*TimeStep then Tv = 0, ElseIf 0.5\*Mult\*TimeStep \< Tv \< Mult\*TimeStep then Tv = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tiq \< 0.5\*Mult\*TimeStep then Tiq = 0, ElseIf 0.5\*Mult\*TimeStep \< Tiq \< Mult\*TimeStep then Tiq = Mult\*TimeStep
  - If 0.0 \< Tpord \< 0.5\*Mult\*TimeStep then Tpord = 0, ElseIf 0.5\*Mult\*TimeStep \< Tpord \< Mult\*TimeStep then Tpord = Mult\*TimeStep
  - If 0 \< T \< Mult\*TimeStep then T = Mult\*TimeStep
  - Kpp and Kip can't be both zero. Must be corrected by user.
  - If Vmax \< Vmin then swap the values
  - If QVmax \< QVmin then swap the values
  - If Pmax \< Pmin then swap the values
  - If RPmax \< RPmin then swap the values
  - If Iqh \< Iql then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Q limits \> QVmax, then QVmax = Q limits or if Q limits \< QVmin, then QVmin = Q limits
  - If PIq limits \> Vmax, then Vmax = PIq limits or if PIq limits \< Vmin, then Vmin = PIq limits
  - If Pord \> Pmax, then Pmax = Pord or if Pord \< Pmin, then Pmin = Pord

Model Equations and/or Block Diagrams

**Parameters:**

![Exciter REEC E 0001](images/Exciter_REEC_E_0001.svg)

![Exciter REEC E 0002](images/Exciter_REEC_E_0002.svg)

![Exciter REEC E 0003](images/Exciter_REEC_E_0003.svg)

|           |                                                                                                                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vcmpflag  | Vcmpflag: Vcomp Flag (\<\>0 means use current compensation, 0 means use reactive droop                                                                                                                          |
| PfFlag    | PfFlag: Power factor flag (\<\>0 means power factor control, 0 means Q control, which can be commanded by an external signal)                                                                                   |
| VFlag     | VFlag: Voltage control flag (\<\>0 means Q control, 0 mean voltage control)                                                                                                                                     |
| QFlag     | QFlag: Reactive power control flag (2 means means constant pf or Q control and use limits Iqmax/Iqmin for PIQ, 1 means voltage/Q control, 0 means constant pf or Q control)                                     |
| PEflag    | PEflag: Power Flag (\<\>0 means to allow for local PI for active power (PIP), 0 means no PI for active power (PIP))                                                                                             |
| Pflag     | Pflag: Power Flag (\<\>0 means multiply Pref signal by gen speed wg, 0 means do not multiply)                                                                                                                   |
| Pqflag    | Pqflag: P/Q priority selection on current limit flag. (0 means Q priority, \<\>0 means P priority                                                                                                               |
| PqflagFRT | PqflagFRT: P/Q priority selection on current limit flag when Voltage\_dip=1. (0 means Q priority, \<\>0 means P priority                                                                                        |
| MVABase   | MVABase: MVABase for model                                                                                                                                                                                      |
| Vdip      | Vdip: The voltage below which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                 |
| Vup       | Vup: The voltage above which the reactive current injection (Iqinj) logic is activated (i.e. voltage\_dip = 1)                                                                                                  |
| Trv       | Trv: Filter time constant for voltage measurement                                                                                                                                                               |
| dbd1      | dbd1: Deadband in voltage error when voltage dip logic is activated (for overvoltage – thus overvoltage response can be disabled by setting this to a large number e.g. 999)                                    |
| dbd2      | dbd2: Deadband in voltage error when voltage dip logic is activated (for undervoltage)                                                                                                                          |
| kqv       | kqv: Gain for reactive current injection during voltage dip (and overvoltage) conditions                                                                                                                        |
| Iqh1      | Iqh1: Maximum limit of reactive current injection (Iqinj)                                                                                                                                                       |
| Iql1      | Iql1: Minimum limit of reactive current injection (Iqinj)                                                                                                                                                       |
| Vref0     | Vref0: The reference voltage from which the voltage error is calculated. This is set by the user. If the user does not specify a value it is initialized by the model to equal to the initial terminal voltage. |
| Iqfrz     | Iqfrz: Value to which reactive-current command is frozen after a voltage-dip \[pu\]                                                                                                                             |
| Thld      | Thld: Time for which reactive-current command is frozen after a voltage-dip \[s\]; if positive then Iqcmd is frozen to its final value during the voltage-dip; if negative then Iqcmd is frozen to Iqfrz        |
| Thld2     | Thld2: Time delay for which the active current limit (Ipmax) is held after voltage\_dip returns to zero for Thld2 seconds at its value during the voltage dip.                                                  |
| Tp        | Tp: Filter time constant for electrical power measurement                                                                                                                                                       |
| QVmax     | QVmax: The maximum value of the incoming Qext or Vext \[pu\]                                                                                                                                                    |
| QVmin     | QVmin: The minimum value of the incoming Qext or Vext \[pu\]                                                                                                                                                    |
| Vmax      | Vmax: Voltage control maximum                                                                                                                                                                                   |
| Vmin      | Vmin: Voltage control minimum                                                                                                                                                                                   |
| Kqp       | Kqp: Proportional gain on Q control                                                                                                                                                                             |
| Kqi       | Kqi: Integral gain on Q control                                                                                                                                                                                 |
| Kpp       | Kpp: Proportional gain on P control                                                                                                                                                                             |
| Kpi       | Kpi: Integral gain on P control                                                                                                                                                                                 |
| Kvp       | Kvp: Proportional gain on V control                                                                                                                                                                             |
| Kvi       | Kvi: Integral gain on V control                                                                                                                                                                                 |
| Vref1     | Vref1: User-define reference/bias on the inner-loop voltage control (default value is zero)                                                                                                                     |
| Tiq       | Tiq: Time constant on lag delay                                                                                                                                                                                 |
| dPmax     | dPmax: Positive Ramp rate on power reference                                                                                                                                                                    |
| dPmin     | dPmin: Negative Ramp rate on power reference                                                                                                                                                                    |
| Pmax      | Pmax: Maximum power reference                                                                                                                                                                                   |
| Pmin      | Pmin: Minimum power reference                                                                                                                                                                                   |
| Imax      | Imax: Maximum allowable total converter current limit                                                                                                                                                           |
| Tpord     | Tpord: Filter time constant on Pord                                                                                                                                                                             |
| Rc        | Rc: Current-compensation resistance \[pu\]                                                                                                                                                                      |
| Xc        | Xc: Current-compensation reactance \[pu\]                                                                                                                                                                       |
| Tr1       | Tr1: Filter time constant for voltage measurement. Can be set to zero. \[s\]                                                                                                                                    |
| Kc        | Kc: Reactive-current compensation gain                                                                                                                                                                          |
| Ke        | Ke: Scaling on Ipmin; set to 0 for a generator, set to a value between 0 and 1 for a storage device, as appropriate                                                                                             |
| Vblkh     | Vblkh: Voltage above which the converter is blocked (i.e. Iq = Ip = 0)                                                                                                                                          |
| Vblkl     | Vblkl: Voltage below which the converter is blocked (i.e. Iq = Ip = 0)                                                                                                                                          |
| Tblkdelay | Tblkdelay: The time delay following blocking of the converter after which the converter is released from being blocked                                                                                          |
| Vq1       | Vq1: VDLq: Voltage Point1                                                                                                                                                                                       |
| Iq1       | Iq1: VDLq: Iqmax Point1                                                                                                                                                                                         |
| Vq2       | Vq2: VDLq: Voltage Point2                                                                                                                                                                                       |
| Iq2       | Iq2: VDLq: Iqmax Point2                                                                                                                                                                                         |
| Vq3       | Vq3: VDLq: Voltage Point3                                                                                                                                                                                       |
| Iq3       | Iq3: VDLq: Iqmax Point3                                                                                                                                                                                         |
| Vq4       | Vq4: VDLq: Voltage Point4                                                                                                                                                                                       |
| Iq4       | Iq4: VDLq: Iqmax Point4                                                                                                                                                                                         |
| Vq5       | Vq5: VDLq: Voltage Point5                                                                                                                                                                                       |
| Iq5       | Iq5: VDLq: Iqmax Point5                                                                                                                                                                                         |
| Vq6       | Vq6: VDLq: Voltage Point6                                                                                                                                                                                       |
| Iq6       | Iq6: VDLq: Iqmax Point6                                                                                                                                                                                         |
| Vq7       | Vq7: VDLq: Voltage Point7                                                                                                                                                                                       |
| Iq7       | Iq7: VDLq: Iqmax Point7                                                                                                                                                                                         |
| Vq8       | Vq8: VDLq: Voltage Point8                                                                                                                                                                                       |
| Iq8       | Iq8: VDLq: Iqmax Point8                                                                                                                                                                                         |
| Vq9       | Vq9: VDLq: Voltage Point9                                                                                                                                                                                       |
| Iq9       | Iq9: VDLq: Iqmax Point9                                                                                                                                                                                         |
| Vq10      | Vq10: VDLq: Voltage Point10                                                                                                                                                                                     |
| Iq10      | Iq10: VDLq: Iqmax Point10                                                                                                                                                                                       |
| Vp1       | Vp1: VDLp: Voltage Point1                                                                                                                                                                                       |
| Ip1       | Ip1: VDLp: Ipmax Point1                                                                                                                                                                                         |
| Vp2       | Vp2: VDLp: Voltage Point2                                                                                                                                                                                       |
| Ip2       | Ip2: VDLp: Ipmax Point2                                                                                                                                                                                         |
| Vp3       | Vp3: VDLp: Voltage Point3                                                                                                                                                                                       |
| Ip3       | Ip3: VDLp: Ipmax Point3                                                                                                                                                                                         |
| Vp4       | Vp4: VDLp: Voltage Point4                                                                                                                                                                                       |
| Ip4       | Ip4: VDLp: Ipmax Point4                                                                                                                                                                                         |
| Vp5       | Vp5: VDLp: Voltage Point5                                                                                                                                                                                       |
| Ip5       | Ip5: VDLp: Ipmax Point5                                                                                                                                                                                         |
| Vp6       | Vp6: VDLp: Voltage Point6                                                                                                                                                                                       |
| Ip6       | Ip6: VDLp: Ipmax Point6                                                                                                                                                                                         |
| Vp7       | Vp7: VDLp: Voltage Point7                                                                                                                                                                                       |
| Ip7       | Ip7: VDLp: Ipmax Point7                                                                                                                                                                                         |
| Vp8       | Vp8: VDLp: Voltage Point8                                                                                                                                                                                       |
| Ip8       | Ip8: VDLp: Ipmax Point8                                                                                                                                                                                         |
| Vp9       | Vp9: VDLp: Voltage Point9                                                                                                                                                                                       |
| Ip9       | Ip9: VDLp: Ipmax Point9                                                                                                                                                                                         |
| Vp10      | Vp10: VDLp: Voltage Point10                                                                                                                                                                                     |
| Ip10      | Ip10: VDLp: Ipmax Point10                                                                                                                                                                                       |

![Exciter REEC D 0002](images/Exciter_REEC_D_0002.svg)

**Current Limit Logic Psuedo Code**

The following pseudo-code describes how the values for Ipmax, Ipmin, Iqmax, and Iqmin are updated. This is done independently of blocking logic described previously.

  **If** Blocked **then begin** // see logic above for when blocking is implemented

    Ipmax = **0**

    Ipmin = **0**

    Iqmax = **0**

    Iqmin = **0**

  **End**

  **Else begin**

    Voltage\_Thld2TimerActive = special boolean related to timer

    local\_V = StateVtfilter // Vt State 1

    **if** VDL1 table is empty **then** Iqmax = **1E10**

    **else** Iqmax = lookup from VL1 table using local\_V

    **if** not Voltage\_Thld2TimerActive **then begin**

      **if** VDL2 table is empty **then** Ipmax = **1E10**

      **else** Ipmax = lookup from VDL2 table using local\_V

    **end**

    **if** PQFlag = **0** **then begin** // Q priority \[default\]

      **If** Imax \< Iqmax **Then** Iqmax = IMax

      **if** Iqmax \< **0** **then** Iqmin = Iqmax // special handling

      **Else** Iqmin = -Iqmax

      **if** not Voltage\_Thld2TimerActive **then begin**

        local\_I = Sqr(Imax) - Sqr(Iqcmd)

        **if** local\_I \< **0** **then** local\_I = **0**

        **else** local\_I = sqrt( local\_I )

        **if** local\_I \< Ipmax **Then** Ipmax = local\_I

      **end**

      Ipmin = -Ke\*Ipmax

    **end**

    **else** **Begin**// P priority

      **if** not Voltage\_Thld2TimerActive **then begin**

        **if** IMax \< Ipmax **Then** Ipmax = Imax

      **end**

      Ipmin = -Ke\*Ipmax

      local\_I = Sqr(Imax) - Sqr(Ipcmd)

      **if** local\_I \< **0** **then** local\_I = **0**

      **else** local\_I = sqrt( local\_I )

      **if** local\_I \< Iqmax **Then** Iqmax = local\_I

      **if** Iqmax \< **0** **then** Iqmin = Iqmax // special handling

      **Else** Iqmin = -Iqmax

    **end**

  **end**

---

<a id="rexs"></a>

## REXS

*Source: [`Content/TransientModels_HTML/Exciter REXS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REXS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.125\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.25\*Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.125\*Mult\*TimeStep then Tp = 0.0  
    ElseIf 0.125\*Mult\*TimeStep \< Tp \< 0.25\*Mult\*TimeStep then Tp = 0.25\*Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.25\*Mult\*TimeStep then Tb1 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0.5\*Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.25\*Mult\*TimeStep then Tb2 = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0.5\*Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vfmax \< Vfmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vf \> Vfmax, then Vfmax = Vf or if Vf \< Vfmin, then Vfmin = Vf
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< -Vimax, then -Vimax = Vi

Model Equations and/or Block Diagrams

![Exciter REXS 0001](images/Exciter_REXS_0001.svg)

**Parameters:**

|        |                                           |
| ------ | ----------------------------------------- |
| Tr     | Transducer time constant, sec             |
| Kvp    | Voltage regulator proportional gain       |
| Kvi    | Voltage regulator integral gain           |
| ViMax  | Voltage regulator input limit, pu         |
| Ta     | Voltage regulator time constant, sec      |
| Tb1    | Lag time constant, sec                    |
| Tc1    | Lead time constant, sec                   |
| Tb2    | Lag time constant, sec                    |
| Tc2    | Lead time constant, sec                   |
| Vrmax  | Maximum control element output, pu        |
| Vrmin  | Minimum control element output, pu        |
| Kf     | Rate feedback gain, pu                    |
| Tf     | Rate feedback constant, sec               |
| Tf1    | Feedback lead time constant, sec          |
| Tf2    | Feedback lag time constant, sec           |
| Fbf    | Rate feedback signal flag                 |
| Kip    | Field current regulator proportional gain |
| Kii    | Field current regulator integral gain     |
| Tp     | Field current bridge time constant, sec   |
| VfMax  | Maximum exciter field current, pu         |
| VfMin  | Minimum exciter field current, pu         |
| Kh     | Field voltage controller feedback gain    |
| Ke     | Exciter field proportional constant       |
| Te     | Exciter field time constant, sec          |
| Kc     | Rectifier regulation factor, pu           |
| Kd     | Exciter regulation factor, pu             |
| E1     | Exciter flux at knee of curve, pu         |
| SE1    | Saturation factor at E1                   |
| E2     | Maximum exciter, pu                       |
| SE2    | Saturation factor at E2                   |
| Rcomp  | Not Used                                  |
| Xcomp  | Not Used                                  |
| Nvphz  | Pickup speed of v/Hz limiter, pu          |
| Kvphz  | v/Hz limiter gain                         |
| Flimf  | Limit type flag                           |
| Xc     | Exciter compounding reactance, pu         |
| VcMax  | Maximum compounding voltage, pu           |
| Kefd   | Field voltage feedback gain               |
| Limflg | Limit flag                                |

---

<a id="rexsy1"></a>

## REXSY1

*Source: [`Content/TransientModels_HTML/Exciter REXSY1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REXSY1.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vfmax \< Vfmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vf \> Vfmax, then Vfmax = Vf or if Vf \< Vfmin, then Vfmin = Vf
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< -Vimax, then -Vimax = Vi

Model Equations and/or Block Diagrams

![Exciter REXSY1 0001](images/Exciter_REXSY1_0001.svg)

**Parameters:**

|       |                                           |
| ----- | ----------------------------------------- |
| Tr    | Transducer time constant, sec             |
| Kvp   | Voltage regulator proportional gain       |
| Kvi   | Voltage regulator integral gain           |
| ViMax | Voltage regulator input limit, pu         |
| Ta    | Voltage regulator time constant, sec      |
| Tb1   | Lag time constant, sec                    |
| Tc1   | Lead time constant, sec                   |
| Tb2   | Lag time constant, sec                    |
| Tc2   | Lead time constant, sec                   |
| Vrmax | Maximum control element output, pu        |
| Vrmin | Minimum control element output, pu        |
| Kf    | Rate feedback gain, pu                    |
| Tf    | Rate feedback constant, sec               |
| Tf1   | Feedback lead time constant, sec          |
| Tf2   | Feedback lag time constant, sec           |
| Fbf   | Rate feedback signal flag                 |
| Kip   | Field current regulator proportional gain |
| Kii   | Field current regulator integral gain     |
| Tp    | Field current bridge time constant, sec   |
| VfMax | Maximum exciter field current, pu         |
| VfMin | Minimum exciter field current, pu         |
| Kh    | Field voltage controller feedback gain    |
| Ke    | Exciter field proportional constant       |
| Te    | Exciter field time constant, sec          |
| Kc    | Rectifier regulation factor, pu           |
| Kd    | Exciter regulation factor, pu             |
| E1    | Exciter flux at knee of curve, pu         |
| SE1   | Saturation factor at E1                   |
| E2    | Maximum exciter, pu                       |
| SE2   | Saturation factor at E2                   |
| Flimf | Limit type flag                           |
| Xc    | Exciter compounding reactance, pu         |
| VcMax | Maximum compounding voltage, pu           |

---

<a id="rexsys"></a>

## REXSYS

*Source: [`Content/TransientModels_HTML/Exciter REXSYS.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter REXSYS.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tf2 \< 0.5\*Mult\*TimeStep then Tf2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf2 \< Mult\*TimeStep then Tf2 = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vfmax \< Vfmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vf \> Vfmax, then Vfmax = Vf or if Vf \< Vfmin, then Vfmin = Vf
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< -Vimax, then -Vimax = Vi

Model Equations and/or Block Diagrams

![Exciter REXSYS 0001](images/Exciter_REXSYS_0001.svg)

**Parameters:**

|       |                                           |
| ----- | ----------------------------------------- |
| Tr    | Transducer time constant, sec             |
| Kvp   | Voltage regulator proportional gain       |
| Kvi   | Voltage regulator integral gain           |
| ViMax | Voltage regulator input limit, pu         |
| Ta    | Voltage regulator time constant, sec      |
| Tb1   | Lag time constant, sec                    |
| Tc1   | Lead time constant, sec                   |
| Tb2   | Lag time constant, sec                    |
| Tc2   | Lead time constant, sec                   |
| Vrmax | Maximum control element output, pu        |
| Vrmin | Minimum control element output, pu        |
| Kf    | Rate feedback gain, pu                    |
| Tf    | Rate feedback constant, sec               |
| Tf1   | Feedback lead time constant, sec          |
| Tf2   | Feedback lag time constant, sec           |
| Fbf   | Rate feedback signal flag                 |
| Kip   | Field current regulator proportional gain |
| Kii   | Field current regulator integral gain     |
| Tp    | Field current bridge time constant, sec   |
| VfMax | Maximum exciter field current, pu         |
| VfMin | Minimum exciter field current, pu         |
| Kh    | Field voltage controller feedback gain    |
| Ke    | Exciter field proportional constant       |
| Te    | Exciter field time constant, sec          |
| Kc    | Rectifier regulation factor, pu           |
| Kd    | Exciter regulation factor, pu             |
| E1    | Exciter flux at knee of curve, pu         |
| SE1   | Saturation factor at E1                   |
| E2    | Maximum exciter, pu                       |
| SE2   | Saturation factor at E2                   |
| Flimf | Limit type flag                           |

---

<a id="scrx"></a>

## SCRX

*Source: [`Content/TransientModels_HTML/Exciter SCRX.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter SCRX.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0 \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep, elseif Te \<= 0 then Te = 0
  - If Kc \< 1 then Kc = 1
  - If Efdmax \< Efdmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> Efdmax, then Efdmax = Efd or if Efd \< Efdmin, then Efdmin = Efd

Model Equations and/or Block Diagrams

![Exciter SCRX 0001](images/Exciter_SCRX_0001.svg)

**Parameters:**

|         |                                                               |
| ------- | ------------------------------------------------------------- |
| Ta\_Tb  | Ta /Tb - gain reduction ratio of lag-lead element             |
| Tb      | Denominator time constant of lag-lead block, sec              |
| K       | Voltage regulator gain                                        |
| Te      | Exciter field time constant, sec                              |
| Efdmin  | Minimum excitation output, pu                                 |
| Efdmax  | Maximum excitation output, pu                                 |
| Cswitch | 0=bus fed, 1=solid fed                                        |
| Rc\_Rfd | Equal 0 for exciter negative field capability, otherwise \> 0 |

---

<a id="sexs-ge"></a>

## SEXS_GE

*Source: [`Content/TransientModels_HTML/Exciter SEXS_GE.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter SEXS_GE.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Exciter SEXS GE 0001](images/Exciter_SEXS_GE_0001.svg)

**Parameters:**

|        |                                                  |
| ------ | ------------------------------------------------ |
| Ta\_Tb | Ta/Tb gain- reduction ratio of lag-lead element  |
| Tb     | Denominator time constant of lag-lead block, sec |
| K      | Voltage regulator gain                           |
| Te     | Exciter field time constant, sec                 |
| Emin   | Minimum excitation output, pu                    |
| Emax   | Maximum excitation output, pu                    |
| Kc     | Rectifier regulation factor, pu                  |
| Tc     | Time constant, sec                               |
| Efdmin | Minimum excitation output, pu                    |
| Efdmax | Maximum excitation output, pu                    |
| Tr     | Transducer time constant, sec                    |

---

<a id="sexs-pti"></a>

## SEXS_PTI

*Source: [`Content/TransientModels_HTML/Exciter SEXS_PTI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter SEXS_PTI.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![Exciter SEXS PTI 0001](images/Exciter_SEXS_PTI_0001.svg)

**Parameters:**

|        |                                                  |
| ------ | ------------------------------------------------ |
| Ta\_Tb | Ta/Tb gain- reduction ratio of lag-lead element  |
| Tb     | Denominator time constant of lag-lead block, sec |
| K      | Voltage regulator gain                           |
| Te     | Exciter field time constant, sec                 |
| Efdmin | Minimum excitation output, pu                    |
| Efdmax | Maximum excitation output, pu                    |

---

<a id="st1c"></a>

## ST1C

*Source: [`Content/TransientModels_HTML/Exciter ST1C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST1C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.25\*Mult\*TimeStep then Tr = 0.0  
    ElseIf 0.25\*Mult\*TimeStep \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0.5\*Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If Vamax \< Vamin then swap the values
  - If Vimax \< Vimin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Efd \> (VT\*Vrmax- Kc\*Ifd), then Efd = (Vrmax- Kc\*Ifd) limits or if Efd\< (VT\*Vrmin), then Vrmin = Efd
  - If Va \> Vamax, then Vamax = Va or if Va\< Vamin, then Vamin = Va
  - If Vi \> Vimax, then Vimax = Vi or if Vi \< Vimin, then Vimin = Vi

Model Equations and/or Block Diagrams

![Exciter ST1C 0001](images/Exciter_ST1C_0001.svg)

**Parameters:**

|       |                                                                               |
| ----- | ----------------------------------------------------------------------------- |
| OEL   | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| UEL   | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| VOS   | PSS input: if = 1, add to error signal; if = 2, add after HV gate 1           |
| Tr    | Filter time constant, sec                                                     |
| ViMax | Maximum error, pu                                                             |
| ViMin | Minimum error, pu                                                             |
| Tc    | Lag time constant, sec                                                        |
| Tb    | Lead time constant, sec                                                       |
| Tc1   | Lag time constant, sec                                                        |
| Tb1   | Lead time constant, sec                                                       |
| Ka    | Gain, pu                                                                      |
| Ta    | Voltage regulator time constant, sec                                          |
| VaMax | Maximum control element output, pu                                            |
| VaMin | Minimum control element output, pu                                            |
| Vrmax | Maximum control element output, pu                                            |
| Vrmin | Minimum control element output, pu                                            |
| Kc    | Rectifier regulation factor, pu                                               |
| Kf    | Rate feedback gain, pu                                                        |
| Tf    | Rate feedback constant, sec                                                   |
| Klr   | Gain on field current limit                                                   |
| Ilr   | Maximum field current, pu                                                     |

---

<a id="st2c"></a>

## ST2C

*Source: [`Content/TransientModels_HTML/Exciter ST2C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST2C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tf \< 0.5\*Mult\*TimeStep then Tf = 0, ElseIf 0.5\*Mult\*TimeStep \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Te \< 0.5\*Mult\*TimeStep then Te = 0, ElseIf 0.5\*Mult\*TimeStep \< Te \< Mult\*TimeStep then Te = Mult\*TimeStep
  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If Ka = 0 then Ka = Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values
  - If VPImax \< VPImin then swap the values
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If VPI \> VPImax, then VPImax = VPI or if VPI \< VPImin, then VPImin = VPI
  - If Efd \> Efdmax, then Efdmax= Efd

Model Equations and/or Block Diagrams

![Exciter ST2C 0001](images/Exciter_ST2C_0001.svg)

**Parameters:**

|           |                                                                               |
| --------- | ----------------------------------------------------------------------------- |
| OEL       | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| UEL       | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| Tr        | Filter time constant, sec                                                     |
| Ka        | Gain, pu                                                                      |
| Ta        | Voltage regulator time constant, sec                                          |
| Vrmax     | Maximum control element output, pu                                            |
| Vrmin     | Minimum control element output, pu                                            |
| Ke        | Exciter field resistance time constant, pu                                    |
| Te        | Exciter field time constant, sec                                              |
| Kf        | Rate feedback gain, pu                                                        |
| Tf        | Rate feedback constant, sec                                                   |
| Kp        | Potential source gain, pu                                                     |
| ThetaPDeg | Phase angle of potential source, degrees                                      |
| Ki        | Current source gain, pu                                                       |
| Xl        | P-bar leakage reactance, pu                                                   |
| Kc        | Rectifier regulation factor, pu                                               |
| Efdmax    | Maximum excitation output, pu                                                 |
| VbMax     | Maximum excitation voltage, pu                                                |
| Kpr       | Proportional gain, pu                                                         |
| Kir       | Integral gain, pu                                                             |
| Vpidmax   | PID maximum limit                                                             |
| Vpidmin   | PID minimum limit                                                             |

---

<a id="st3c"></a>

## ST3C

*Source: [`Content/TransientModels_HTML/Exciter ST3C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST3C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tb \< 0.5\*Mult\*TimeStep then Tb = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb \< Mult\*TimeStep then Tb = Mult\*TimeStep

  - If 0.0 \< Tm \< 0.5\*Mult\*TimeStep then Tm = 0, ElseIf 0.5\*Mult\*TimeStep \< Tm \< Mult\*TimeStep then Tm = Mult\*TimeStep

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep

  - If Ka = 0 then Ka = Mult\*TimeStep

  - If Km = 0 then Km = Mult\*TimeStep

  - If Vrmax \< Vrmin then swap the values

  - If Vmmax \< Vmmin then swap the values

  - If VPImax \< VPImin then swap the values

  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If VPI \> VPImax, then VPImax = VPI or if VPI \< VPImin, then VPImin = VPI
  - If Vm \> Vmmax, then Vmmax = Vm or if Vm \< Vmmin, then Vmmin = Vm

Model Equations and/or Block Diagrams

![Exciter ST3C 0001](images/Exciter_ST3C_0001.svg)

**Parameters:**

|           |                                                                               |
| --------- | ----------------------------------------------------------------------------- |
| OEL       | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| UEL       | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| Tr        | Filter time constant, sec                                                     |
| ViMax     | Maximum error, pu                                                             |
| ViMin     | Minimum error, pu                                                             |
| Km        | DC converter gain                                                             |
| Tc        | Lag time constant, sec                                                        |
| Tb        | Lead time constant, sec                                                       |
| Ka        | Gain, pu                                                                      |
| Ta        | Voltage regulator time constant, sec                                          |
| Vrmax     | Maximum control element output, pu                                            |
| Vrmin     | Minimum control element output, pu                                            |
| Kg        | Excitation limiter gain, pu                                                   |
| Kp        | Potential source gain, pu                                                     |
| Ki        | Current source gain, pu                                                       |
| VbMax     | Maximum excitation voltage, pu                                                |
| Kc        | Rectifier regulation factor, pu                                               |
| Xl        | P-bar leakage reactance, pu                                                   |
| VgMax     | Maximum excitation voltage                                                    |
| ThetaPDeg | Phase angle of potential source, degrees                                      |
| Tm        | Time constant, sec                                                            |
| VmMax     | Model Parameters\\VmMax                                                       |
| VmMin     | Model Parameters\\VmMin                                                       |
| Kpr       | Proportional gain, pu                                                         |
| Kir       | Integral gain, pu                                                             |
| Vpidmax   | PID maximum limit                                                             |
| Vpidmin   | PID minimum limit                                                             |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)                             |

---

<a id="st4c"></a>

## ST4C

*Source: [`Content/TransientModels_HTML/Exciter ST4C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST4C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Ta \< 0.5\*Mult\*TimeStep then Ta = 0, ElseIf 0.5\*Mult\*TimeStep \< Ta \< Mult\*TimeStep then Ta = Mult\*TimeStep
  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tg \< 0.5\*Mult\*TimeStep then Tg = 0, ElseIf 0.5\*Mult\*TimeStep \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - Kpm and Kim: Kpm can't be 0 if Kim = 0, if true then Kpm changed to 1.
  - Kpr and Kir: Kpr can't be 0 if Kir = 0, if true then Kpr changed to 40.
  - If Vrmax \< Vrmin then swap the values
  - If Vmmax \< Vmmin then swap the values
  - If Vamax \< Vamin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr
  - If Vm \> Vmmax, then Vmmax = Vm or if Vm \< Vmmin, then Vmmin = Vm
  - If Va \> Vamax, then Vamax = Va or if Va \< Vamin, then Vamin = Va

Model Equations and/or Block Diagrams

![Exciter ST4C 0001](images/Exciter_ST4C_0001.svg)

![Exciter ST4C 0002](images/Exciter_ST4C_0002.svg)

**Parameters:**

|           |                                                                                     |
| --------- | ----------------------------------------------------------------------------------- |
| VOS       | PSS input: if = 1, add to error signal; if = 2, add after HV gate 1                 |
| OEL       | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2       |
| UEL       | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2       |
| SCL       | SCL input: if \< 2, add to error signal; if = 2, Take Over 2 1; if = 3, Take Over 3 |
| SW1       | Logical switch 1 (1 = Position A, 2 = Position B)                                   |
| Tr        | Filter time constant, sec                                                           |
| Kpr       | Proportional gain, pu                                                               |
| Kir       | Integral gain, pu                                                                   |
| Vrmax     | Maximum control element output, pu                                                  |
| Vrmin     | Minimum control element output, pu                                                  |
| Kpm       | Proportional gain of field voltage regulator, pu                                    |
| Kim       | Integral gain of field voltage regulator, pu                                        |
| VmMax     | Model Parameters\\VmMax                                                             |
| VmMin     | Model Parameters\\VmMin                                                             |
| Ta        | Voltage regulator time constant, sec                                                |
| VaMax     | Maximum exciter output, p.u.                                                        |
| VaMin     | Minimum exciter output, p.u.                                                        |
| Kg        | Excitation limiter gain, pu                                                         |
| Tg        | Feedback time constant of field current regulator, sec.                             |
| VgMax     | Maximum excitation voltage                                                          |
| Kp        | Potential source gain, pu                                                           |
| Ki        | Current source gain, pu                                                             |
| Xl        | P-bar leakage reactance, pu                                                         |
| ThetaPDeg | Phase angle of potential source, degrees                                            |
| Kc        | Rectifier regulation factor, pu                                                     |
| VbMax     | Maximum excitation voltage, pu                                                      |

---

<a id="st5c"></a>

## ST5C

*Source: [`Content/TransientModels_HTML/Exciter ST5C.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Exciter ST5C.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Tr = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tb1 \< 0.5\*Mult\*TimeStep then Tb1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb1 \< Mult\*TimeStep then Tb1 = Mult\*TimeStep
  - If 0.0 \< Tb2 \< 0.5\*Mult\*TimeStep then Tb2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tb2 \< Mult\*TimeStep then Tb2 = Mult\*TimeStep
  - If 0.0 \< Tob1 \< 0.5\*Mult\*TimeStep then Tob1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tob1 \< Mult\*TimeStep then Tob1 = Mult\*TimeStep
  - If 0.0 \< Tob2 \< 0.5\*Mult\*TimeStep then Tob2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tob2 \< Mult\*TimeStep then Tob2 = Mult\*TimeStep
  - If 0.0 \< Tub2 \< 0.5\*Mult\*TimeStep then Tob2 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tub2 \< Mult\*TimeStep then Tub2 = Mult\*TimeStep
  - If 0.0 \< Tub1 \< 0.5\*Mult\*TimeStep then Tub1 = 0, ElseIf 0.5\*Mult\*TimeStep \< Tub1 \< Mult\*TimeStep then Tub1 = Mult\*TimeStep
  - T1: If Mult\*TimeStep \> 4 then T1 = 0.25\*Mult\*TimeStep, else 1 \< T1 \< Mult\*TimeStep
  - If Vrmax \< Vrmin then swap the values

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Vr \> Vrmax, then Vrmax = Vr or if Vr \< Vrmin, then Vrmin = Vr

Model Equations and/or Block Diagrams

![Exciter ST5C 0001](images/Exciter_ST5C_0001.svg)

**Parameters:**

|       |                                                                               |
| ----- | ----------------------------------------------------------------------------- |
| OEL   | OEL input: if \< 2, add to error signal; if = 2, LV gate 1; if = 3, LV gate 2 |
| UEL   | UEL input: if \< 2, add to error signal; if = 2, HV gate 1; if = 3, HV gate 2 |
| Tr    | Filter time constant, sec                                                     |
| Tc1   | Lead time constant 1, sec                                                     |
| Tb1   | Lag time constant 1, sec                                                      |
| Tc2   | Lead time constant 2, sec                                                     |
| Tb2   | Lag time constant 2, sec                                                      |
| Kr    | Gain, pu                                                                      |
| Vrmax | Maximum control element output, pu                                            |
| Vrmin | Minimum control element output, pu                                            |
| T1    | Inverse timing current constant, sec                                          |
| Kc    | Rectifier regulation factor, pu                                               |
| Tuc1  | UEL lead time constant 1, sec.                                                |
| Tub1  | UEL lag time constant 1, sec.                                                 |
| Tuc2  | UEL lead time constant 2, sec.                                                |
| Tub2  | UEL lag time constant 2, sec.                                                 |
| Toc1  | OEL lead time constant 1, sec.                                                |
| Tob1  | OEL lag time constant 1, sec.                                                 |
| Toc2  | OEL lead time constant 2, sec.                                                |
| Tob2  | OEL lag time constant 2, sec.                                                 |
